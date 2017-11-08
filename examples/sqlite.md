# SQLite

## Date/time
```
SQLite does not have a storage class set aside for storing dates and/or times. Instead, the built-in Date And Time Functions of SQLite are capable of storing dates and times as TEXT, REAL, or INTEGER values:

    TEXT as ISO8601 strings ("YYYY-MM-DD HH:MM:SS.SSS").
    REAL as Julian day numbers, the number of days since noon in Greenwich on November 24, 4714 B.C. according to the proleptic Gregorian calendar.
    INTEGER as Unix Time, the number of seconds since 1970-01-01 00:00:00 UTC. 

Applications can chose to store dates and times in any of these formats and freely convert between formats using the built-in date and time functions.
```

## Atomicity
This explains how atomic commits are done in SQLite. It's probably a pretty good reference to what should happen in any write-to-disc process for an ACID database. https://sqlite.org/atomiccommit.html

## Write-ahead log
A new mode of committing for SQLite. It writes blocks which are to be committed to an append-only log, and finally writes something which confirms that they are valid. Each read process checks the WAL before looking at the main database file. An index is maintained in RAM to find pages in the WAL quicker.

This might be a good reference implementation of append-only data with an index to the latest version of each thing.
