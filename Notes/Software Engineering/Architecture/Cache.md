
Cache systems are in memory databases

Used for fast, temporary storage


## Invalidation
- Set time to live
- Remove with API call
- Remove oldest entity when space runs out


## Uses
- Store user sessions


## Patterns
- Lazy loading - all read data is cached
- Write through - all writes are cached


## Implementations
- [[Redis]]
- [[Memcached]]