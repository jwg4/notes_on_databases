1. Postgres has microseconds in a 64-bit integer (4713 BCE - 294000 CE)
2. MongoDB has milliseconds in a 64-bit integer. (CE + 270 million years)
3. APFS filesystem has 64 bit nanosecond timestamps (Unix epoch to ~2550 CE) https://blog.cugu.eu/post/apfs/
4. https://github.com/jbenet/nanotime
5. InfluxDB has signed 64 bit timestamps counting nanoseconds (1677 CE to ~2270 CE) https://www.influxdata.com/blog/tldr-influxdb-tech-tips-december-08-2016/

A 64 bit integer counting nanoseconds would cover 584 years.
