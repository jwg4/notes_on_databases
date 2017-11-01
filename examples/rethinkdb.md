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



## Questions
- What wire protocol for pub-sub?
- RethinkQL? Is this a query language which makes sense?
