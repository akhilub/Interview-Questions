
when I use msw framework to mock api response in browser for dev environment how will I test we backend endpoint have real data



To test your frontend application against a live backend with real data while using [Mock Service Worker (MSW)](https://mswjs.io/), you must prevent the service worker from intercepting your requests. [[1](https://www.edstem.com/blog/mock-service-worker-development-testing), [2](https://medium.com/@msmechatronics/stop-waiting-for-apis-a-developers-guide-to-mock-service-worker-a05d7a58ff39), [3](https://medium.com/@biplavmazumdar5/mswjs-mock-service-worker-8c3354a757bf)]

The most common ways to toggle or bypass MSW in your local browser environment to see real backend data include: [[1](https://mswjs.io/docs/)]

1. Toggle via Browser URL Query Parameters

You can conditionally start the worker based on a URL flag. This lets you view real data simply by adding `?mock=false` to your browser's address bar. [[1](https://dev.to/kevin-uehara/mocking-your-apis-calls-using-mocking-service-worker-msw-7k6), [2](https://cathalmacdonnacha.com/mocking-error-empty-and-loading-states-with-msw)]

Update your application initialization logic (e.g., `main.ts` or `index.js`):

typescript

```
// Check if MSW should be skipped based on URL parameters
const urlParams = new URLSearchParams(window.location.search);
const shouldMock = urlParams.get('mock') !== 'false';

if (process.env.NODE_ENV === 'development' && shouldMock) {
  const { worker } = await import('./mocks/browser');
  await worker.start();
}
```

Use code with caution.

2. Control with Custom Environment Variables

If you want to boot the entire development build configured to target the live backend rather than toggling it manually in the browser, use a custom flag in your `.env` files.

- **For MSW (Mocked Dev Mode):** Create or use a default `.env.development` file:
    
    env
    
    ```
    VITE_USE_MSW=true
    VITE_API_URL=http://localhost:3000 # Or your local server path
    ```
    
    
    
- **For Real Data Mode:** Create a `.env.local` or `.env.real` file (which overrides default variables):
    
    env
    
    ```
    VITE_USE_MSW=false
    VITE_API_URL=https://yourbackend.com
    ```
    
    
    
    [[1](https://symfonycasts.com/screencast/mailer/functional-test)]

In your application code, wrap your initialization block with this environment variable:

typescript

```
if (import.meta.env.VITE_USE_MSW === 'true') {
  const { worker } = await import('./mocks/browser');
  await worker.start();
}
```



3. Fallthrough to Real Endpoints via MSW Strategies

If you want MSW to intercept _some_ endpoints but want to let others point directly to your real backend, you can specify unhandled request behaviours or bypass specific routes. [[1](https://dev.to/andrewchaa/simplifying-api-mocking-with-mock-service-worker-msw-4o4j)]

- **Allow All Unhandled Requests:** By default, you can configure MSW to let any request that doesn't match an explicit mock handler fall through to the actual network:
    
    typescript
    
    ```
    // in browser.ts
    worker.start({
      onUnhandledRequest: 'bypass', // Passes unhandled requests to the live server
    });
    ```
    
    
    
- **Manually Forward via `passthrough()`:** Within a specific handler file, you can explicitly tell MSW to step out of the way for a particular route:
    
    
    
    ```typescript
    import { http, passthrough } from 'msw';
    
    export const handlers = [
      http.get('/api/users', () => {
        // Temporarily bypass this handler to hit the live backend
        return passthrough(); 
      }),
    ];
    ```
    
    [[1](https://dev.to/andrewchaa/simplifying-api-mocking-with-mock-service-worker-msw-4o4j), [2](https://stevekinney.com/courses/enterprise-ui/mock-service-worker)]

4. Direct Terminal Commands (The Quickest Toggle)

If you do not want to change your code logic, you can temporarily stop MSW directly from your browser's developer tools. Open your browser console (`F12`) and call the global worker control options exposed by MSW:

- **Turn off mocking temporarily:** `window.msw.worker.stop()` (Note: You may need to assign the `worker`reference to `window.msw` during your setup script to call this cleanly).
    
- **Verify in Network Tab:** Look at your **Network Tab**. When MSW is running, requests show a `Gear` icon or say `from ServiceWorker`. When bypassed, you will see your actual server IP/Domain under the "Remote Address" column. [[1](https://impacttrial.coresecurity.com/docs/doc/onprem/walkthrough/webapps/), [2](https://ultimatecourses.com/blog/ultimate-guide-pwa-workbox)]

Would you like help setting up a **specific script in your package.json** to automate launching your dev environment with or without mocks?



Here is how to set up dedicated scripts in your `package.json` to effortlessly launch your development environment with or without MSW.

This approach uses environment variables to control whether the mock worker initializes.

1. Update your `package.json`

Add separate scripts for your mocked environment and your live data environment.

Here is an example using **Vite** (if you use Webpack/CRA, substitute `VITE_` with `REACT_APP_`):

json

```
{
  "scripts": {
    "dev": "vite",
    "dev:mock": "cross-env VITE_USE_MSW=true vite",
    "dev:real": "cross-env VITE_USE_MSW=false vite"
  },
  "devDependencies": {
    "cross-env": "^7.0.3"
  }
}
```



_(Note: `cross-env` ensures the environment variables work seamlessly across Mac, Linux, and Windows machines.)_

2. Install `cross-env`

Run this command in your terminal to install the utility dependency:



```bash
npm install --save-dev cross-env
```

Use code with caution.

3. Update your App Initialization Code

Ensure your code checks for this specific environment variable before starting the service worker:

typescript

```
// main.ts / index.js
async function enableMocking() {
  // Check the environment variable set by your package.json script
  if (import.meta.env.VITE_USE_MSW !== 'true') {
    return;
  }

  const { worker } = await import('./mocks/browser');
  
  // Return the worker start promise
  return worker.start({
    onUnhandledRequest: 'bypass', // Lets unmocked routes hit the real backend
  });
}

enableMocking().then(() => {
  // Render your React / Vue / Angular application here
  // ReactDOM.createRoot(document.getElementById('root')).render(<App />)
});
```

Use code with caution.

4. How to run it

- **To build/test using your MSW mock data:**
    
    bash
    
    ```
    npm run dev:mock
    ```
    
    Use code with caution.
    
- **To bypass MSW completely and test against live backend data:**
    
    bash
    
    ```
    npm run dev:real
    ```
    
    Use code with caution.
    

If you want, I can:

- Show you how to configure this for **Next.js or Webpack** instead of Vite
- Show how to automatically **swap the API Target URL** when running the real data script
- Help you write a script that toggles mocks using **`.env` files** instead of inline command variables



Show how to automatically swap the API Target URL when running the real data script


To automatically change your API target URL depending on whether you are using mocks or live data, you can define different target URLs directly inside your `package.json` scripts or utilize standard environmental variables.

Here is how to implement this for **Vite** (for Webpack/Create React App, use `REACT_APP_` instead of `VITE_`). [[1](https://kuberns.com/blogs/deploy-react-on-render/)]

1. Update your `package.json` Scripts

Add a second environment variable (e.g., `VITE_API_URL`) to your scripts. This assigns a local proxy or mock URL for your mock script, and your live server URL for your real data script. [[1](https://requestly.com/blog/academy-understanding-insert-inject-script-rule/)]

json

```
{
  "scripts": {
    "dev:mock": "cross-env VITE_USE_MSW=true VITE_API_URL=/api vite",
    "dev:real": "cross-env VITE_USE_MSW=false VITE_API_URL=https://yourbackend.com vite"
  }
}
```

Use code with caution.

2. Use the Environment Variable in your API Client

Instead of hardcoding your base URL in your Fetch, Axios, or RTC Query configuration, reference the dynamic environment variable.

typescript

```
// apiClient.ts or apiService.js
import axios from 'axios';

export const apiClient = axios.create({
  // Automatically resolves to '/api' or 'https://yourbackend.com'
  baseURL: import.meta.env.VITE_API_URL, 
  headers: {
    'Content-Type': 'application/json',
  },
});
```

Use code with caution.

3. Update your MSW Handlers (If necessary)

If your `VITE_API_URL` uses an absolute path (like `https://yourbackend.com`), your MSW handlers must match that specific domain to intercept the requests correctly.

You can dynamically import the same environment variable inside your MSW handlers:

typescript

```
// src/mocks/handlers.ts
import { http, HttpResponse } from 'msw';

// Read the same API URL configuration
const API_URL = import.meta.env.VITE_API_URL || '';

export const handlers = [
  // Intercepts path cleanly whether it is '/api/users' or 'https://.../api/users'
  http.get(`${API_URL}/users`, () => {
    return HttpResponse.json([
      { id: 1, name: 'Mocked User' }
    ]);
  }),
];
```

Use code with caution.

Alternative: Using `.env` Files (Cleaner Codebase)

If your paths are long or complex, you can move these configurations out of `package.json` into specialized environment files:

1. Create a `.env.development` file (used for `npm run dev:mock`):
    
    env
    
    ```
    VITE_USE_MSW=true
    VITE_API_URL=/api
    ```
    
    Use code with caution.
    
2. Create a `.env.local` file (this overrides development configurations locally and is ignored by git). Use this when you want to switch to real data:
    
    env
    
    ```
    VITE_USE_MSW=false
    VITE_API_URL=https://yourbackend.com
    ```
    
    Use code with caution.
    
    [[1](https://nextnative.dev/blog/secure-api-key)]

Would you like help configuring a **Vite proxy (`vite.config.ts`)** to fix any CORS issues when hitting the real backend URL directly?