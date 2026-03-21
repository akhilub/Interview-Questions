Redis and Memcached are both used to make applications faster.

They work as a cache layer between your app and the database.

Instead of hitting the database every time, your app can fetch frequently used data directly from memory. Since RAM is much faster than disk, responses come back in microseconds.

So what's the difference?

Memcached

- A simple distributed key value cache
- Stores data in memory
- Great for fast and lightweight caching
- No persistence so data disappears if the server restarts

Redis

- An in memory data structure store
- Supports lists, sets, hashes and sorted sets Can be used for queues rate limiting leaderboards and pub sub messaging
- Supports persistence so data can survive restarts

The core idea is simple.

Memcached is a pure cache.

Redis is a cache that can also act like a lightweight data store.