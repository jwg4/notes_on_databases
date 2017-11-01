# RethinkDB

## Basics
- Fast
- Sharded (eventually consistent)
- Document store (JSON)
- Has atomicity (over a single key)
- Not ACID: cannot write to multiple keys in one transaction
- Can subscribe to changes!

## Subscribe to changes
For example, here is how you query RethinkDB for a document:

```
r.table('users').get('coffeemug').run()
```

And here is how you subscribe to a stream of updates from RethinkDB any time the document changes:

```
r.table('users').get('coffeemug').changes().run()
```

## Scaling
From the FAQ:

The changefeeds architecture is designed to enable each client to open multiple realtime feeds. Since modern web and mobile applications often have tens of thousands of concurrent clients, RethinkDB’s feeds are designed to be extremely scalable. You should be able to open thousands of concurrent active feeds on a single RethinkDB node, and scale to tens or hundreds of thousands of feeds across a RethinkDB cluster.

## Questions
- What wire protocol for pub-sub?
- RethinkQL? Is this a query language which makes sense?
