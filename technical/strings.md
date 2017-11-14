How do postgres and SQLite store strings? Does it require a further lookup to the b-tree index? Is there an mbuf type data structure?

- SQLite stores strings inline in variable-length fields which encode their own length, and aren't null terminated.
