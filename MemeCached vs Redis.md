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


## Drawing
```compressed-json
N4IgLgngDgpiBcIYA8DGBDANgSwCYCd0B3EAGhADcZ8BnbAewDsEAmcm+gV31TkQAswYKDXgB6MQHNsYfpwBGAOlT0AtmIBeNCtlQbs6RmPry6uA4wC0KDDgLFLUTJ2lH8MTDHQ0YNMWHRJMRZFFgBGULIkT1UYRjAaBABtAF1ydCgoAGUAsD5QSXw8LOwNPkZOTExyHRgiACF0VABrQq5GXABhekx6fAQQAGIAM1GxkABfCaA==
```
%%
