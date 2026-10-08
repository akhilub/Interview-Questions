





To perform API authentication using HMAC, ==the client and the server must first securely share a private secret key==.

Instead of sending this secret key over the network (like a standard password or API key), the client uses it to generate a unique digital signature for each request. The server then recalculates the signature to verify it.

---

## 🔄 The HMAC Authentication Workflow

```unset
[ Client ]                                                       [ Server ]
    │                                                                │
    ├── 1. Prepares Request Data (Method, URL, Body, Timestamp)      │
    ├── 2. Signs data with Shared Secret -> Generates Signature     │
    │                                                                │
    ├── 3. Sends Request + Signature + Timestamp ───────────────────>│
    │                                                                │
    │                                                                ├── 4. Checks Timestamp (Prevents Replay Attacks)
    │                                                                ├── 5. Re-signs incoming data with Shared Secret
    │                                                                ├── 6. Compares recalculated signature with sent signature
    │                                                                │
    │                                                                └── 7. If Match: Process Request (200 OK)
    │                                                                        If Mismatch: Reject (401 Unauthorized)
```

---

## 🛠️ Step-by-Step Implementation

## 1. The Client Prepares and Signs the Request

Before sending a request, the client bundles specific parts of the request together into a single string. This is called the Canonical String.

- Step A: Create the string to sign.
    
    ```text
    StringToSign = HTTP_Method + "\n" + Request_URI + "\n" + Timestamp + "\n" + Request_Body
    ```
    
    _(Adding a Timestamp is crucial. It prevents "replay attacks" where a hacker steals a valid signature and tries to reuse it hours later. The server will reject requests if the timestamp is older than, say, 5 minutes)._
- Step B: Generate the HMAC.  
    The client hashes the `StringToSign` using a hashing algorithm (like SHA-256) and the shared secret key.
    
    ```text
    Signature = HMAC_SHA256(StringToSign, Shared_Secret_Key)
    ```
    
- Step C: Send the request.  
    The client sends the actual data, the timestamp, and the generated signature in the HTTP headers.
    
    ```http
    POST /api/v1/payments
    X-API-Key: client_public_identifier
    X-Signature: 9b741g8... (The generated HMAC)
    X-Timestamp: 1791497940
    Content-Type: application/json
    
    {"amount": 100, "currency": "INR"}
    ```
    

## 2. The Server Verifies the Request

When the server receives the request:

1. Lookup: It uses the `X-API-Key` to look up the client's `Shared_Secret_Key` in its database.
2. Time Check: It verifies that the `X-Timestamp` is close to the server's current time.
3. Reconstruct: It builds the exact same `StringToSign` using the incoming method, URI, timestamp, and body.
4. Recalculate: It runs the HMAC function on that string using the retrieved secret key.
5. Compare: It compares its freshly generated signature with the `X-Signature` header sent by the client. If they match perfectly, the request is authenticated.

---

## ⚖️ Why use this instead of a standard Bearer Token?

|Feature|Standard API Key / Bearer Token|HMAC Authentication|
|---|---|---|
|Exposure Risk|High. If intercepted, an attacker can use it indefinitely.|Low. The secret key is never sent over the internet.|
|Tamper Proof|No. A hacker can change the request body (e.g., changing a price from ₹10,000 to ₹1) while keeping the token valid.|Yes. If the request body changes even by one character, the signatures will not match.|
|Complexity|Very easy to implement.|Moderate. Requires cryptographic libraries on both sides.|

To provide a ready-to-use code example for this authentication flow, let me know:

- What backend language or framework you are building the server with? (e.g., Node.js/Express, Python/FastAPI, Java, C#)
- Do you need both the client-side generation and server-side verification code?