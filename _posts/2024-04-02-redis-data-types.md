---
layout: post
title: "Understand Redis data types"
category: redis
---

Overview of data types supported by Redis

Redis is a data structure server. At its core, Redis provides a collection of native data types that help you solve a wide variety of problems, from [caching](https://redis.io/docs/manual/client-side-caching/) to [queuing](https://redis.io/docs/data-types/lists/) to [event processing](https://redis.io/docs/data-types/streams/). Below is a short description of each data type, with links to broader overviews and command references.

If you'd like to try a comprehensive tutorial for each data structure, see their overview pages below.

## Core

### Strings

[Redis strings](https://redis.io/docs/data-types/strings) are the most basic Redis data type, representing a sequence of bytes. For more information, see:

- [Overview of Redis strings](https://redis.io/docs/data-types/strings/)
- [Redis string command reference](https://redis.io/commands/?group=string)

### Lists

[Redis lists](https://redis.io/docs/data-types/lists) are lists of strings sorted by insertion order. For more information, see:

- [Overview of Redis lists](https://redis.io/docs/data-types/lists/)
- [Redis list command reference](https://redis.io/commands/?group=list)

### Sets

[Redis sets](https://redis.io/docs/data-types/sets) are unordered collections of unique strings that act like the sets from your favorite programming language (for example, [Java HashSets](https://docs.oracle.com/javase/7/docs/api/java/util/HashSet.html), [Python sets](https://docs.python.org/3.10/library/stdtypes.html#set-types-set-frozenset), and so on). With a Redis set, you can add, remove, and test for existence in O(1) time (in other words, regardless of the number of set elements). For more information, see:

- [Overview of Redis sets](https://redis.io/docs/data-types/sets/)
- [Redis set command reference](https://redis.io/commands/?group=set)

### Hashes

[Redis hashes](https://redis.io/docs/data-types/hashes) are record types modeled as collections of field-value pairs. As such, Redis hashes resemble [Python dictionaries](https://docs.python.org/3/tutorial/datastructures.html#dictionaries), [Java HashMaps](https://docs.oracle.com/javase/8/docs/api/java/util/HashMap.html), and [Ruby hashes](https://ruby-doc.org/core-3.1.2/Hash.html). For more information, see:

- [Overview of Redis hashes](https://redis.io/docs/data-types/hashes/)
- [Redis hashes command reference](https://redis.io/commands/?group=hash)

### Sorted sets

[Redis sorted sets](https://redis.io/docs/data-types/sorted-sets) are collections of unique strings that maintain order by each string's associated score. For more information, see:

- [Overview of Redis sorted sets](https://redis.io/docs/data-types/sorted-sets)
- [Redis sorted set command reference](https://redis.io/commands/?group=sorted-set)

### Streams

A [Redis stream](https://redis.io/docs/data-types/streams) is a data structure that acts like an append-only log. Streams help record events in the order they occur and then syndicate them for processing. For more information, see:

- [Overview of Redis Streams](https://redis.io/docs/data-types/streams)
- [Redis Streams command reference](https://redis.io/commands/?group=stream)

### Geospatial indexes

[Redis geospatial indexes](https://redis.io/docs/data-types/geospatial) are useful for finding locations within a given geographic radius or bounding box. For more information, see:

- [Overview of Redis geospatial indexes](https://redis.io/docs/data-types/geospatial/)
- [Redis geospatial indexes command reference](https://redis.io/commands/?group=geo)

### Bitmaps

[Redis bitmaps](https://redis.io/docs/data-types/bitmaps/) let you perform bitwise operations on strings. For more information, see:

- [Overview of Redis bitmaps](https://redis.io/docs/data-types/bitmaps/)
- [Redis bitmap command reference](https://redis.io/commands/?group=bitmap)

### Bitfields

[Redis bitfields](https://redis.io/docs/data-types/bitfields/) efficiently encode multiple counters in a string value. Bitfields provide atomic get, set, and increment operations and support different overflow policies. For more information, see:

- [Overview of Redis bitfields](https://redis.io/docs/data-types/bitfields/)
- The [`BITFIELD`](https://redis.io/commands/bitfield) command.

### HyperLogLog

The [Redis HyperLogLog](https://redis.io/docs/data-types/hyperloglogs) data structures provide probabilistic estimates of the cardinality (i.e., number of elements) of large sets. For more information, see:

- [Overview of Redis HyperLogLog](https://redis.io/docs/data-types/hyperloglogs)
- [Redis HyperLogLog command reference](https://redis.io/commands/?group=hyperloglog)

## Extensions

To extend the features provided by the included data types, use one of these options:

1. Write your own custom [server-side functions in Lua](https://redis.io/docs/manual/programmability/).
2. Write your own Redis module using the [modules API](https://redis.io/docs/reference/modules/) or check out the [community-supported modules](https://redis.io/docs/modules/).
3. Use [JSON](https://redis.io/docs/stack/json/), [querying](https://redis.io/docs/stack/search/), [time series](https://redis.io/docs/stack/timeseries/), and other capabilities provided by [Redis Stack](https://redis.io/docs/stack/).
