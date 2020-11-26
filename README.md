# clustercache

A file cache implementation designed for small-scale reliable caching solutions.

## Goals

There are many cache implementations, but none that exactly fit my need:

1. The cache must run as a fully replicated cluster.
2. Cache reads and writes must be able to occur on any node in the cluster.
3. Cache writes must only succeed once a specific number of other nodes have written the value.
4. Cache values must be persistable to disk.
5. There should be no concept of quorum, as different values are unlikely to be written to different hosts.
6. In the case where two nodes write a different value for a key ("split brain"), the write with the older timestamp must be discarded.
7. The system must support per-tenant quotas, with least recently used items being discarded.
8. It must be possible to limit which IP addresses can join the cluster.
9. It must be possible to store binary data.
10. It must be possible to store arbitrarily large files.
11. It must be possible to access random portions of values, as opposed to having to read the entire file.
12. It must be possible to stream read and write values.
13. It must be possible to encrypt communication.
