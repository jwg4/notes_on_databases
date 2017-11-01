# notes_on_databases

- How are JSON documents stored for searching into arbitrary fields?
- How do we build indexes for timestamp or similar data?
- Indexes for queries of arbitrary complexity.
- Timestamp types.
- PUB/SUB? PUB/SUB for complex queries.
- File formats?
- Managing concurrency?
- Responsiveness of servers, limited RAM per client.
- Which things can be realistically sharded?
- How can things be mirrored quickly and reliably?
- Structured/probabilistic types such as stream counters

- how does redid decide when to write to disc? How configurable? Does it free memory when doing so?
- how do we deal with disk blocks, mmap, in python?
- SQLite how is memory Fred when things are written to disc? How does it deal with limited memory?
- can rabbitmq queues be daisy chained?
- can redid only deal with data that fits in memory? It's it ok with pages being swapped out?
- how do databases fail when they run out of RAM or disk space?
