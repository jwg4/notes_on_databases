# Redis

## Questions
- How does Redis pub/sub work?
- How can a write to keystore/pubsub complete as quickly as possible?
- How does confirmation of write/transaction affect performance?
- How are timestamps stored, if at all?
- How are sorted sets stored?
- Multi-channel pubsub, or filtering quickly from sets or sorted sets?
- Fast slicing from sorted sets
- Preserving order when filtering
- Redis connection management, connection overhead
- Redis protocol, how does it compare to HTTP for fast connections, fast writes, low RAM usage?

## Types
- SDS strings: custom string which is compatible with null-terminated strings.

## Sorted set
```
/* ZSETs are ordered sets using two data structures to hold the same elements
 * in order to get O(log(N)) INSERT and REMOVE operations into a sorted
 * data structure.
 *
 * The elements are added to a hash table mapping Redis objects to scores.
 * At the same time the elements are added to a skip list mapping scores
 * to Redis objects (so objects are sorted by scores in this "view").
 *
 * Note that the SDS string representing the element is the same in both
 * the hash table and skiplist in order to save memory. What we do in order
 * to manage the shared SDS string more easily is to free the SDS string
 * only in zslFreeNode(). The dictionary has no value free method set.
 * So we should always remove an element from the dictionary, and later from
 * the skiplist.
 *
 * This skiplist implementation is almost a C translation of the original
 * algorithm described by William Pugh in "Skip Lists: A Probabilistic
 * Alternative to Balanced Trees", modified in three ways:
 * a) this implementation allows for repeated scores.
 * b) the comparison is not just by key (our 'score') but by satellite data.
 * c) there is a back pointer, so it's a doubly linked list with the back
 * pointers being only at "level 1". This allows to traverse the list
 * from tail to head, useful for ZREVRANGE. */
```

## Threading
Redis is single-threaded. How do waits for IO work? Pre-emption seems like it would break the Redis data model, or perhaps it's not the case because data processing always takes place without blocking.

## Saving to disk
BGSAVE is a command which forks the process. The new process writes everything in its memory to disk. SAVE pauses everything while it write to disk.

## Set operations
Redis does, apparently "lightning-fast set operations", eg UNION, INTER..

## Replication
The replication model is based on this - all commands must produce exactly the same effect if replayed on a slave machine. This means that some behavior involving keys which will expire is just excluded. You can retrieve data involving keys which have expiries set, but you can't set other keys using keys with expiry set. 
