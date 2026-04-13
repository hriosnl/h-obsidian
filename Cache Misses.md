Happen when the CPU looks for data in the cache but cannot find it there.

Main cases:

1. **Cold miss (first access)**  
    Happens when data is accessed for the first time. It has never been loaded into cache before.

2. **Capacity miss**  
    Happens when the cache is too small to hold all the data being used. Older data gets evicted, and when it is needed again, it is no longer there.

3. **Conflict miss**  
    Happens when multiple pieces of data map to the same cache location. Even if there is free space elsewhere, they replace each other due to how the cache is structured.

4. **Coherence miss (multi-core systems)**  
    Happens when another core modifies or invalidates a cached value, forcing a reload from main memory.

In short: cache misses occur when required data is not currently stored in the cache due to first-time access, limited size, mapping collisions, or multi-core updates.

> (All that code is C) but it's optimized at the level where I worry about single instruction (kind of thing and especially single cache misses)
> - Linus Torvalds

