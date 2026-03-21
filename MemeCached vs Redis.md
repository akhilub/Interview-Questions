---
excalidraw-plugin: parsed
tags:
  - excalidraw
---
Redis and Memcached are both used to make applications faster.

They work as a cache layer between your app and the database.

Instead of hitting the database every time, your app can fetch frequently used data directly from memory. Since RAM is much faster than disk, responses come back in microseconds.

So what's the difference?

**Memcached**

- A simple distributed key value cache
- Stores data in memory
- Great for fast and lightweight caching
- No persistence so data disappears if the server restarts

**Redis**

- An in memory data structure store
- Supports lists, sets, hashes and sorted sets Can be used for queues rate limiting leaderboards and pub sub messaging
- Supports persistence so data can survive restarts

 _The core idea is simple._

_Memcached is a pure cache._

_Redis is a cache that can also act like a lightweight data store._

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
%%
## Drawing
```compressed-json
N4KAkARALgngDgUwgLgAQQQDwMYEMA2AlgCYBOuA7hADTgQBuCpAzoQPYB2KqATLZMzYBXUtiRoIACyhQ4zZAHoFAc0JRJQgEYA6bGwC2CgF7N6hbEcK4OCtptbErHALRY8RMpWdx8Q1TdIEfARcZgRmBShcZQUebR4ARniaOiCEfQQOKGZuAG1wMFAwYogSbggACQBHAGsAFgAhAGUAKQAtFOLIWERywOwojmVgzpLMbgBmAA5tAAZ5hcWFif4S

mG4EibiANl29/f3VyAoSdUmeHYOrgHY6o6kEQmVpblvtAE5Pr++v6/vrYbiVCze7MKCkNg1BAAYTY+DYpHKAGIEghUajRpBNLhsDVlBChBxiLD4YiJODrMw4LhAllMRAAGaEfD4JqwEYSQQeelgiFQgDqp0k3D4BQE4MhCDZMA56C5ZXuBOeHHCOTQCXubGp2DU63V83u+OEcAAksQ1ahcgBde4M8gZM3cDhCFn3QhErDlXCzekEokq5gWopdaDw

IETMUAX1BCAQxFe1wms22PFu73ujBY7C4aB4yYzTFYnAAcpwxBsJnUAKxV64JBKzDVi0rMAAiaSgce4DIIYXummERIAosEMlkLc7Xc2hHBiLhO/H1ddbvX3ts6u8plMmyGiBwak6Xfh7vDcV20D38GECpHwDa6Lg4HA2fOgcHoJJ0kCIERnlBRgwhAIBQDQ4nifrEnCCLIgysFwQB2AiLSUAmp2+hsnyMJQWS6Aomi+EIUhmQoWhoG4kahKQaS5Q

UhwVI0sRhGkMhqHpAAYsyrLst+8rxqsECIcxxGsehEoCkKIr8YJLFoRhkrSrKEC8UxMnpAASsIyqqhsUlEVkIkAPLarqGwGgUAl6SR7GcFAbG4PozJ6qgVa6UJ+loWxNlNIQRhAnmrmqfoAAqWBQAAgr+OboMEDL/gFwmyVEpDhcxbAUJ+uCLqgk7HuZ0kJekQ5EmFqXpSEWUQDSEJUPF7npCV1VBWGfSDnxeWWSJbH2ggGmyjl/HMNgEIsgAGtw

ILmYNw34AAmuN/FGGwBjcMGkD0AQQhAgkN61VZ+gaZRAYWhAEEAfiJDeb5IoTSU53EGyCBwNwLnmXdACybDEAgRW4JowRZZefavaQJAktBaCrRADRwhVpDKNiAAUiR/LwCQo8j1DAtoVYAJT0mpCDKC6NJ9PDuBI0mmM8JTvA07M2N4zt7VuVAclQkZUDZhOR78Xa9k9ZkX0g0MK3Npkv3/dw4Kbfc2BEE9aDSwg9wcPzUukDLzbCFAe5Akr9z6D

SUKkMWauKxryvNobpDGz9f3nqgStMyUdgAFYIAMzBNKrcAfV9duSxevaWyUOKc4wQVLfgoshj0PFpAM2b0ohYIGE1vRoP1zanlCAPB7aELoQnnOcN2+fZ6E4WJxHUeHiyzuQI4zAS1hWShW9mRCGXV4h1i7qOEMAAKgQMkwmTlhI4v221JSEMwDT9+6ygBw7+vmXPb0kHAbDuqzPtwEvK9ZU7YDRnQTLBEGt6RkAA===
```
%%