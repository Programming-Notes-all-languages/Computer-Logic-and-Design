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
Miss penalty = Catch hit time + memory access time = 2 + 50 ns = 52 ns<br />
EAT = 0.95 * 2 + 0.05 * 52 = 4.5 ns
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A non-overlapping data access direct-mapped cache has an access time of 2ns, while main memory access takes 50ns<br />

If the cache hit rate is 90%, what is the effective memory access time (EMAT)?

<ul>  
  <details>
    <summary>Solution</summary>

Miss rate = 1 - 0.9 = 0.1<br />
Miss penalty = Catch hit time + memory access time = 2 + 50 ns = 52 ns
EAT = 0.9 * 2 + 0.1 * 52 = 7 ns
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A system has a non-overlapping data access direct-mapped cache with a 90% hit rate<br />

If the cache access time is 2 ns and the main memory access time is 100 ns, what is the effective memory access time (EMAT)?

<ul>  
  <details>
    <summary>Solution</summary>

Miss rate = 1 - 0.9 = 0.1<br />
Miss penalty = Catch hit time + memory access time = 2 + 100 ns = 102 ns
EAT = 0.9 * 2 + 0.1 * 102 = 12 ns
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
  <li>0x9F8 = 1111 1111 1111 1111 1111 1001 1111 1000<br />
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

A 2 MB direct-mapped cache has a block size of 128 bytes. If a memory address of 0x1A3F58 is accessed, which cache line in hex will it map to?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (2 * 1024 * 1024) / 128 = 16384 = 2<sup>14</sup><br />
Index = 14 bits
Byte offset = 128 = 2<sup>7</sup><br />
Byte offset = 7 bits<br />
Tag bits = 32 - 14 - 7 = 11 bits<br />

0x1A3F58 = 0001 1010 0011 1111 0101 1000<br />
Offset: 101 1000<br />
Index: 11 0100 0111 1110 = 11010001111110<br />
Tag: 000<br />

Index in hex: 0x347E
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

<details>
    <summary>Example problem</summary>

A system has a 64KB direct-mapped cache with a block size of 32 bytes. If a 32-bit address is used, how many bits are needed for the tag field?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (64 * 1024) / 32 = 2048 = 2<sup>11</sup><br />
Index = 11 bits
Byte offset = 32 = 2<sup>5</sup><br />
Byte offset = 5 bits<br />
Tag bits = 32 - 11 - 5 = 16 bits
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 128KB direct-mapped cache with a block size of 32 bytes. How many index bits are required?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (128 * 1024) / 32 = 8192 = 2<sup>12</sup><br />
Index = 12 bits
</details>
</ul>  
</details>

### Fully Associative Cache
A block can be placed anywhere in cache, meaning no indexing

If $m$ blocks exist, then $m$ comparators are needed to match tag and the cache data size = $m$ * 2<sub>b</sub> bytes

#### Replacement Policy
<ul>
  <li><strong>Least Recently Used (LRU)</strong> is the most common replacement policy for fully associative cache. It replaces the block that has been unused for the longest time</li>
  <li><strong>First in First Out (FIFO)</strong> is where the oldest block in the set gets replaced</li>
  <li><strong>Random</strong> is where a random block is evicted</li>
</ul>

<details>
    <summary>Example problem</summary>

A fully associative cache has a size of 64 KB and a block size of 32 bytes. If the system uses 320bit addresses, how many bits are required for the tag field?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks: cache size / block size = (64 * 1024) / 32 = 2048<br />
There is no indexing in fully associative cache<br />
Offset: 32 = 2<sup>5</sup> = 5 bits<br />
Tag: 32 - 5 = 27 bits
</details>
</ul>  
</details>

### Set-Associative Cache
A <strong>set</strong> is a group of blocks that can be indexed

If there are $m$ blocks in a set (<strong>m-way set associative</strong>) then $m$ tags are checked in parallel using $m$ comparators

If 2<sup>n</sup> sets exist then <strong>set index</strong> consists of $n$ bits. The cache data size = $m$ * 2<sup>n + b</sup> bytes

<details>
    <summary>Example problem</summary>

A non-overlapping 4-way set-associative cache has a hit rate of 92%, a cache access time of 4 ns, and a memory access time of 80ns. What is the effective memory access time (EMAT) in ns?

<ul>  
  <details>
    <summary>Solution</summary>

Miss rate = 1 - 0.92 = 0.08<br />
Miss penalty = Catch hit time + memory access time = 4 + 80 ns = 84 ns
EAT = 0.92 * 4 + 0.08 * 84 = 10.4 ns
</details>
</ul>  
</details>

#### Replacement Policy
<ul>
  <li><strong>Least Recently Used (LRU)</strong> is the most common replacement policy for set-associative cache. It replaces the block that has been unused for the longest time</li>
  <li><strong>First in First Out (FIFO)</strong> is where the oldest block in the set gets replaced</li>
  <li><strong>Random</strong> is where a random block is evicted</li>
</ul>

<details>
    <summary>Example problem</summary>

A 32 KB 2-way set-associative cache has a block size of 64 bytes. Which cache set in hex will memory address 0xABC3D4 map to?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks: cache size / block size = (32 * 1024) / 64 = 512<br />
Number of sets = Number of blocks / $m$ = 512 / 2 = 256 sets
Index: 256 = 2<sup>8</sup><br />
Index: 8 bits<br />
Offset: 64 = 2<sup>6</sup><br />
Offset: 6 bits<br />
0xABC3D4 = 1010 1011 1100 0011 1101 0100<br />
Index = 0000 1111 = 0xF
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 32-bit memory address is divided into tag, index, and offset fields for a 4-way set-associative cache with:<br />

64 KB total cache size<br />
Block size = 32 bytes<br />

How many bits are allocated for the index field?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks: cache size / block size = (64 * 1024) / 32 = 2048<br />
Number of sets = Number of blocks / $m$ = 2048 / 4 = 512 sets
Index: 512 = 2<sup>9</sup><br />
Index: 9 bits
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 2 MB 2-way set-associative cache has a block size of 64 bytes. How many bits are required for the tag field in a 32-bit address system?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (2 * 1024 * 1024) / 64 = 32768<br />
Number of sets: Number of blocks / $m$ = 32768 / 2 = 16384 sets<br />
Index: 16384 = 2<sup>14</sup><br />
Index: 14 bits<br />
Offset: 64 = 2<sup>6</sup><br />
Offset: 6 bits<br />
Tag: 32 - 14 - 6 = 12 bits
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 128 KB 4-way set-associative cache has a block size of 64 bytes. How many sets does the cache contain?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks = cache size / block size = (128 * 1024) / 64 = 2048<br />
Number of sets: Number of blocks / $m$ = 2048 / 4 = 512 sets
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 32 KB 2-way set-associative cache has a block size of 64 bytes. Which cache set will memory address 0xABC3D4 map to in decimal?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks: cache size / block size = (32 * 1024) / 64 = 512<br />
Number of sets: Number of blocks / $m$ = 512 / 2 = 256 sets<br />
Index: 256 = 2<sup>8</sup> = 8 bits<br />
Offset: 64 = 2<sup>6</sup> = 6 bits<br />
Tag: 32 - 8 - 6 = 18 bits<br />
0xABC3D4: 1010 1011 1100 0011 1110 0100<br />
Offset = 10 0100<br />
Index = 0000 1111 = 15<br />
Tag: 101<br />
</details>
</ul>  
</details>

<details>
    <summary>Example problem</summary>

A 512 KB 4-way set-associative cache has a block size of 64 bytes. If a memory address 0xA67B34 is accessed, which set number will it map to?

<ul>  
  <details>
    <summary>Solution</summary>

Number of cache blocks: cache size / block size = (512 * 1024) / 64 = 8192<br />
Number of sets: Number of blocks / $m$ = 8192 / 4 = 2048 sets<br />
Index: 2048 = 2<sup>11</sup> = 11 bits<br />
Offset: 64 = 2<sup>6</sup> = 6 bits<br />
Tag: 32 - 11 - 6 = 15 bits<br />
0xABC3D4: 1010 0110 0111 1011 0011 0100<br />
Offset = 11 0100<br />
Index = 001 1110 1100 = 476<br />
Tag: 101<br />
</details>
</ul>  
</details>

The primary hardware disadvantage of a fully associative cache compared to set-associative or direct-mapped caches is the greater power consumption due to multiple parallel tag comparisons

### Handling Write
#### Write Through
<ul>
  <li>Writes update cache and lower-level memory</li>
  <li>For cache control bit, only a valid bit is needed</li>
  <li>Memory always has latest data</li>
  <li>Can always discard cached data when a block is replaced</li>
</ul>

#### Write Back
<ul>
  <li>Writes update cache only</li>
  <li>For cache control bits: valid and modified bits are required</li>
  <li>Modified cached data is written back to memory when replaced</li>
  <li>Multiple writes to a cache block require only one write to memory</li>
  <li>Uses less memory bandwidth than write-through and less power</li>
  <li>Is more complex to implement than write though</li>
  <li>Write-back may lead to data inconsistency if not properly managed</li>
</ul>

## Virtual Memory
The primary purpose of cache memory is to provide faster memory access speeds

The primary purpose of virtual memory is to provide greater memory capacity without the expense of adding main memory. This is done by extending main memory with a portion of a disk drive

### Virtual Memory Terminology
<ul>
  <li>Virtual addresses: the logical or program address that the process uses</li>
  <li>Physical address: the real address in physical memory</li>
  <li>Mapping: the mechanism by which virtual addresses are translated into physical ones</li>
  <li>Page frames: the equal-size chunks or blocks into which main memory (physical memory) is divided</li>
  <li>Pages: the chunks or blocks into which virtual memory (the logical address space) is divided, each equal in size to a page frame. Virtual pages are stored on disk until needed</li>
  <li>Paging: the process of copying a virtual page from disk to a page frame in main memory</li>
  <li>Fragmentation: memory that becomes unusable</li>
  <li>Page fault: an event that occurs when a requested page is not in main memory and must be copied into memory from disk</li>
</ul>

### Page Table 
<img src="Images/Diagrams/Page Table" alt="Page Table">

Page offset (bits) = log base 2(page size (bits))<br />

To compute the physical address, physical address = frame number * page size + offset<br />

In a virtual address, to top x bits are the virtual address' page number and the lower y bits are the virtual address' page offset

<details>
    <summary>Example problem</summary>

Suppose you have a byte-addressable virtual address memory system with 8 virtual pages of 64 bytes each, and 4 page frames. Assuming the following page table, answer the questions below:

<img src="Images/Example Problems/Problem 1.png" alt="Problem 1">

<ol type="a">
  <li>How many bits are in a virtual address?</li>
  <li>How many bits are in a physical address?</li>
  <li>How many bits are virtual page number?</li>
  <li>How many bits are page frame number?</li>
  <li>How many bits are page offset?</li>
  <li>What is the corresponding physical address for virtual address 0x00?</li>
  <li>What is the corresponding physical address for virtual address 0xC2?</li>
  <li>What is the corresponding physical address for virtual address 0x80?</li>
</ol>
<ul>  
  <details>
    <summary>Solution</summary>

<ol type="a">
  <li>Virtual address space = 8 pages * 64 bytes = 512 bytes<br />
  log <sub>2</sub> (512) = 9 bits</li>
  <li>Physical address space = 4 frames * 64 bytes = 256 bytes<br />
  log <sub>2</sub> (256) = 8 bits</li>
  <li>log <sub>2</sub> (8) = 3 bits</li>
  <li>log <sub>2</sub> (4) = 2 bits</li>
  <li>log <sub>2</sub> (64) = 6 bits</li>
  <li>Top 3 bits: 000 -> page number = 0<br />
  Bottom 6 bits: 000000 -> offset = 0<br />
  Physical address = 1 * 64 + 0 = 64</li>
  <li>Top 3 bits: 110 -> page number = 6<br />
  Bottom 6 bits: 00010 -> offset = 2<br />
  Page fault since valid bit at frame 6 is 0</li>
  <li>Top 3 bits: 100 -> page number = 4<br />
  Bottom 6 bits: 00000 -> offset = 0<br />
  Physical address = 2 * 64 + 0 = 128</li>
</ol>
</details>
</ul>  
</details> 

<details>
    <summary>Example problem</summary>

A system has 128 MB of physical memory and uses a 40-bit virtual address with a page size of 8 KB. How many bits are required for the page offset?

<ul>  
  <details>
    <summary>Solution</summary>

Page offset = log base 2(8 * 1024) = 13 bits
</details>
</ul>  
</details>

Number of physical frames = Physical memory size / Page size

<details>
    <summary>Example problem</summary>

In a system with a 4 KB page size and 1 GB of physical memory, how many physical frames are available

<ul>  
  <details>
    <summary>Solution</summary>

Number of physical frames = (1024 * 1024 * 1024) / (4 * 1024)
</details>
</ul>  
</details>

#### Virtual Address
There are two fields: a page field and an offset field
<ul>
  <li>The page field determines the page location of the virtual address</li>
  <li>Offset field indicates the location of the address within the page</li>
</ul>

Number of virtual pages = Virtual address space size / Page size

<details>
    <summary>Example problem</summary>

Given a system with a 32-bit virtual address space and 4 KiB (2 <sup>12</sup> bytes) page size, how many virtual pages are there?

<ul>  
  <details>
    <summary>Solution</summary>

Number of virtual pages = 2 <sup>32</sup> / 2 <sup>12</sup> = 2 <sup>20</sup>
</details>
</ul>  
</details>

#### Physical Address
There are two fields: a page frame field and an offset fields
<ul>
  <li>The page frame field determines the page frame location in main memory</li>
</ul>

### Translation Look-aside Buffer (TLB)
Since page tables are constantly read, they are stored in a special cache called the <strong>translation look-aside buffer</strong>

TLBs are a special associative cache that stores the mapping of virtual pages to physical pages. The primary purpose of the TLB in a virtual memory system is to accelerate virtual-to-physical address translation

If there is a TLB miss, go to the page table to get the necessary frame number

### Segmentation
<strong>Segmentation</strong> is where virtual address space is divided into variable-length segments

### Fragmentation
<ul>
  <li>Both paging and segmentation can cause fragmentation</li>
  <li><strong>Paging</strong> is subject to internal fragmentation because a process may not need the entire range of addresses contained within the page</li>
  <li><strong>Segmentation</strong>is subject to external fragmentation, which occurs when contiguous chunks of memory become broken up as segments are allocated and deallocated over time</li>
</ul>

#### Internal Fragmentation
Memory wasted due to internal fragmentation = Page size - (Processes needed mod Page size)

<details>
    <summary>Example problem</summary>

If a system has a page size of 8 KB, and a process needs 30 KB of memory, how much memory is wasted due to internal fragmentation?

<ul>  
  <details>
    <summary>Solution</summary>

Waste = 8 - (30 mod 8) = 8 - 6 = 2 KB
</details>
</ul>  
</details>
