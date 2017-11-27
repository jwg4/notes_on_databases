# Postgres

## Indexes
- B-tree indexes are designed for >, ==, >=, etc.
- BRIN indexes can work with ordered data, record min max element of each disk block. Details about how they work?
- Hash indexes: equality only. Could be used for filtering by channel etc, if we don't have timestamp filters, or in a multi-level index

## Timestamp type?
- 64 bit integer with microseconds

## JSONB
### does not preserve
- Whitespace
- Repeated keys
- Order of keys

### Structure on disk
- Struct can have pointer to both string and binary format
- Parse tree in binary format?
- Not mutable

## Source
- ADT: Abstract Data Type
