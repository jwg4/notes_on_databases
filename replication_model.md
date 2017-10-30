1. Database A has an output stream, for ALL. 
2. Database B replicates A, by subscribing to A's ALL stream. 
3. B's configuration says that A's ALL becomes B's ALL.
4. This means that B's ids will just be A's ids?
5. B connects on startup to A, and subscribes using the last valid event it got as a starting point.
6. Database C also replicates A's ALL.
7. However, it has A's ALL at its /foo channel.
8. Channels /blah and /asdf on A appear on C as /foo/blah and /foo/asdf
9. C might also republish D's ALL stream (or a substream) with a configured prefix.
10. This means that C's ids aren't the same as A's, and C's hashes aren't the same as A's.

