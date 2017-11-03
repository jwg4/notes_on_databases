We want to choose whether to persist to disk or not. This is so that we can have a server which doesn't and a slave which does, but doesn't have any other load.

The following case might be worth considering in detail. 
1. Server A is the master, which receives events from a bunch of places.
2. Servers B1, B2, B3 each receive a slice of server A's stream, filtered by channel, between them they get all of it.
3. Servers B1/2/3 persist to disk. 
4. They have access to timestamp, id, hash from A. But neither id nor hash can be independently generated.
5. To re-create the whole event stream, server A' reads from B1/2/3.
6. A needs to get the original timestamps. It needs to process the events in the order of these timestamps.
7. If it does this, it can recreate the hash and id from A.

Step 6 could be quite complicated. It involves
a) huge resources at A' to hold onto, say, messages from B1 where it hasn't yet retrieved an earlier message from B2.
b) cleverness at A' to keep deciding where it should get messages from and asking for a range (PULL model)
c) the ability for the streams from B1/2/3 to be 'paused' or throttled and unthrottled continually.

Whichever one of these is chosen should be able to carry on without problems, if it reaches the end of the persisted data, and starts getting data which is passed straight through from A.

It seems like every event will have both original and local id, timestamp and hash. It will be configurable 
a) which one of these gets passed through (at stream level, ie. you could subscribe to one or the other?)
b) whether we check id and timestamp against our own or not (at subscriber level)
