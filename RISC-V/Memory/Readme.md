<details>
<summary>Table of Contents</summary>
<ol>
  <li>
    <a href='#hierarchical-memory-organization'>Hierarchical Memory Organization</a>
  </li>
  <li>
    <a href='#cache-memory'>Cache Memory</a>
  </li>
  <li>
    <a href='#direct-mapped-cache-practice'>Direct Mapped Cache Practice</a>
  </li>
  <li>
    <a href='#virtual-memory'>Virtual Memory</a>
  </li>
</ol>
</details>

## Hierarchical Memory Organization
The primary reason for having a memory hierarchy in modern computer systems is to balance cost, speed, and storage capacity

### Types of Memory
There are two types of main memory:

<ul>
  <li><strong>Read-only-memory (ROM)</strong> which does not need to be refreshed and is used to store permanent, or semi-permanent data that persists even while the system is turned off</li>
  <li><strong>Random access memory (RAM)</strong>
    <ul>
      <Li>Static RAM (SRAM) is very fast memory and it does not need to be refreshed like DRAM does. It is used to build cache memory</li>
      <li>Dynamic RAM (DRAM) consists of capacitors that slowly leak their charge over time. Thus they must be refreshed every few milliseconds to prevent data loss. DRAM is cheap memory owing to its simple design</li>
    </ul>
  </li>
</ul>

Random access memory are large arrays of storage cells. The memory is volatile meaning the memory stores the data as long as it is powered on

There are two control signals associated with RAM: the output enable (OE) control signal which specifies read operation and write enable (WE) control signal which specifies write operation

#### SRAM
Static RAM (SRAM) for cache memory
<ul>
  <li>Fast but expensive RAM</li>
  <li>Requires six to eight transistors per bit</li>
  <li>Provides fast access time</li>
  <li>Typically used for cache memories</li>
</ul>

#### DRAM
Dynamic RAM (DRAM) for main memory
<ul>
  <li>Slow, cheap, and dense memory</li>
  <li>One transistor + capacitor per bit</li>
  <li>Bit is stored as a charge on capacitor</li>
  <li>Must be re-written after being read</li>
  <li>Must also be periodically refreshed. Reading each row and writing it back to restore the charge</li>
  <li>Typical choice for main memory</li>
</ul>

DRAM's refresh cycle is about tens of milliseconds. Refreshing is done for the entire memory and some of the memory bandwidth is lost to refresh cycles

### Processor-Memory Performance Gap
There is a widening speed gap between CPU and main memory performance. Processor operations take much less time compared to main memory operations

Cache memory can help bridge the CPU-memory gap since cache memory is small in size but fast

### Typical Memory Hierarchy
<ul>
  <li>Registers are at the top of the hierarchy
    <ul>
      <li>Typical size is less than 1 KB</li>
      <li>Access time is less than 0.5 ns</li>
    </ul>
  <li>Level 1 Cache (8 - 64 KB)
    <ul>
      <li>Access time is 1 ns</li>
    </ul>
  </li>
  <li>Level 2 Cache (512KB - 8MB)
    <ul>
      <li>Access time is 3 - 10 ns</li>
    </ul>
  </li>
  <li>Main Memory (4 - 16 GB)
    <ul>
      <li>Access time is 50 - 100 ns</li>
    </ul>
  </li>
  <li>Disk Storage (greater than 200 GB)
    <ul>
      <li>Access time is 5 - 10 ms</li>
    </ul>
  </li>
</ul>

#### Principle of Locality of Reference
<ul>
  <li>Program access small portion of their address space. At any time, only a small set of instructions and data is needed</li>
  <li>Temporal locality
    <ul>
      <li>If an item is accessed, probably it will be accessed again soon</li>
      <li>Same loop instructions are fetched each iteration</li>
      <li>Same procedure may be called and executed many times</li>
    </ul>
  </li>
  <li>Spatial locality
    <ul>
      <li>Tendency to access contiguous instructions/data in memory<li>
      <li>Sequential execution of instructions</li>
      <li>Traversing arrays element by element</li>
    </ul>
  </li>
</ul>

### Cache Memory
Cache memory is small and fast (SRAM) memory technology that stores the subset of instructions and data currently being accessed. It is used to reduce the average access time to memory

<ul>
  <li>Caches exploit temporal locality by keeping recently accessed data closer to the processor</li>
  <li>Caches exploit spatial locality by moving blocks consisting of multiple contiguous words</li>
</ul>

The goals of cache memory are to utilize its fast speeds and balance the cost of the memory system

Almost everything in computer architecture is cache

<ul>
  <li>Registers are a cache on variables</li>
  <li>First-level cache is a cache on second-level cache</li>
  <li>Second-level cache is a cache on memory</li>
  <li>Memory is a cache on a hard disk. A hard disk stores recent programs and their data. Hard disks can be viewed as an extension to main memory</li>
</ul>

A <strong>hit</strong> is when data is found at a given memory level

A <strong>miss</strong> is when it is not found

The <strong>hit rate</strong> is the percentage of time data is found at a given memory level

The <strong>miss rate</strong> is the percentage of time it is not. The miss rate is equal to 1 minus the hit rate

The <strong>hit time</strong> is the time required to access data at a given memory level

The <strong>miss penalty</strong> is the time required to process a miss, including the time that it takes to replace a block of memory plus the time it takes to deliver the data to the processor

### Effective Access Time (EAT)
<div align="center">
EAT = (Hit rate) * (Cache hit time) + (Miss rate) * (Miss penalty)
</div>

<details>
    <summary>Example problem</summary>

A system has:<br /><br />
Cache hit time = 2 ns<br />
Cache hit rate = 95%<br />
Memory access time = 50 ns<br /><br />
What is the effective access time

<ul>  
  <details>
    <summary>Solution</summary>

Miss rate = 1 - 0.95 = 0.05<br />
Miss penalty = Catch hit time + memory access time = 2 + 50 ns = 52 ns
EAT = 0.95 * 2 + 0.05 * 52 = 4.5 ns
</details>
</ul>  
</details>

## Cache Memory
### Block Placement: Direct Mapped
A <strong>block</strong> is a unit of data transfer between cache and memory

A block can be placed in exactly one location in the cache

A memory addressed is divided into
<ul>
  <li><strong>Block address</strong> which identifies block in memory
    <ul>
      <li>A block address is further divided into
        <ul>
          <li>A <strong>block</strong> used for direct cache access</li>
          <li>A <strong>tag</strong> which are the most significant bits of a block address</li>
          <li><strong>Index</strong> = Block Address mod Cache Blocks</li>
        </ul>
      </li>
    </ul>
  </li>
  <li><strong>Block offset</strong> which accesses bytes within a block</li>
  <li>A tag must be stored also inside cache for block identification</li>
  <li>A <strong>valid bit</strong> is also required to indicate whether a cache block is valid or not</li>
</ul>

A <strong>cache hit</strong> is a block stored inside cache
<ul>
  <li>Index is used to access cache block</li>
  <li>Address tag is compared against stored tag</li>
  <li>If equal and cache block is valid then <strong>hit</strong>; otherwise, <strong>cache miss</strong></li>
</ul>

if the number of cache blocks is 2<sup>n</sup>, then n bits are used for the cache index

If the number of bytes in a block is 2<sup>b</sup>, then b bits are used for the block offset

If 32 bits are used for an address, 32 - n - b bits are used for the tag

The cache data size is equal to 2<sup>n + b</sup> bytes

<details>
    <summary>Example problem</summary>

Consider a small direct-mapped cache with 32 blocks. Cache is initially empty and block size is 16 bytes

The following memory addresses are referenced: 0x3E8, 0x3EC, 0x3F0, 0x9F4, 0x9F8, and 0x9FC. Map addresses to cache blocks and indicate whether hit or miss

<ul>  
  <details>
    <summary>Solution</summary>

Cache index is equal to 2^n = 32, n = 5<br />
Byte offset is equal to 2^n = 16, n = 4<br />
Tag is 23-bit<br />

<ol type="a">
  <li>0x3E8 = 0000 0000 0000 0000 0000 0011 1110 1000<br />
Offset: 1000<br />
Index: 11110<br />
Tag: 000<br />
The cache block at index 30 has a valid bit of 0 since it has not been filled with data yet, and therefore it will be a miss. After this miss, the data corresponding to the address 0x3E8 will be loaded into index 30
  </li>
  <li>0x3EC = 0000 0000 0000 0000 0000 0011 1110 1100<br />
  Offset: 1100<br />
Index: 11110<br />
Tag: 000<br />
The cache block at index 30 has a valid bit of 1 since it has been filled with data in the previous process. The previous tag and the current tag match, 000; therefore, this is a hit
  </li>
  <li>0x3F0 = 0000 0000 0000 0000 0000 0011 1111 0000<br />
Offset: 0000<br />
Index: 11111<br />
Tag: 000<br />
The cache block at index 31 has a valid bit of 0 since it has not been filled with data in the previous processes and therefore it will be a miss. After this miss, the data corresponding to the address 0x3F0 will be loaded into index 31</li>
  <li>0x9F4 = 1111 1111 1111 1111 1111 1001 1111 0100<br />
Offset: 0100<br />
Index: 11111<br />
Tag: 111<br />
The cache block at index 31 has a valid bit of 1 since it has been filled with data in the previous process. However, the previous tag, 000, and the current tag, 111, do not match; therefore, this is a miss. After the miss, the data corresponding to the address 0x9F4 will be loaded into index 31</li>
  <li>
</ol>0x9F8 = 1111 1111 1111 1111 1111 1001 1111 1000<br />
Offset: 1000<br />
Index: 11111<br />
Tag: 111<br />
The cache block at index 31 has a valid bit of 1 since it has been filled with data in the previous processes. The previous tag and the current tag match, 111; therefore, this is a hit</li>
</ol>
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A system has:<br />
32-bit memory addresses, direct-mapped cache, 64 KB cache size, block size = 16 bytes. How many bits are used for the tag field?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (64 * 1024) / 16 = 4096 = 2<sup>12</sup><br />
Index = 12 bits
Byte offset = 16 = 2<sup>4</sup><br />
Byte offset = 4 bits<br />
Tag bits = 32 - 12 - 4 = 16 bits
</details>
</ul>  
</details>

### Fully Associative Cache
A block can be placed anywhere in cache, meaning no indexing

If $m$ blocks exist, then $m$ comparators are needed to match tag and the cache data size = $m$ * 2<sub>b</sub> bytes

### Set-Associative Cache
A <strong>set</strong> is a group of blocks that can be indexed

## Virtual Memory
The primary purpose of cache memory is to provide faster memory access speeds

The primary purpose of virtual memory is to provide greater memory capacity without the expense of adding main memory. This is done by extending main memory with a portion of a disk drive
