# Buff
Buff is a just in time serialization layer for java structurally similar to binary json, implemented directly on top of java byte buffers. 
All the java primitives, as well as structs (maps) and arrays (lists) are supported.
Because objects are serialized natively at the bytebuffer level, they are fast and NIO friendly.

## How it works
Under the covers, buff lazily converts, waiting to perform the serialization task until records are actually accessed, or written. 
Because of this, large records utilizing sparse access patterns can be efficiently stored with logN serialization overhead.

## Why this is awesome
Because it stores records natively into/from byte buffers, this is efficient with respect to memory mapped storage utilizing both sparse and brute force access patterns. Serialization is bytebuffer level and generally requires no copying.
This makes its IO cost minimal and its extremely lightweight and fast.

## Why this was written
Mainly, because I needed a way to traverse a memory mapped dataset many times larger than physical ram efficiently without paying serialization or copy overhead. This operates as a core serialization layer for Proxamic, which is a dynamic proxy based
data layer built to leverage buff serialization.

