---
layout: learning
title: "Notes from \"What Every Programmer Should Know About Memory\""
status: "Finished"
description: "Here I put all the notes I made and that helped me with understanding all of the topics... I used ChatGPT for learning purposes, that's the only reason you should ever use it TBH."

---

# 🧠 CPU Cache Hierarchy & Memory Latency

*📘 Overview* 

Modern CPUs use multiple levels of cache — small, ultra-fast memory units — to bridge the huge speed gap between the CPU and main memory (RAM).

> ⚙️ Problem: Each cell in the large main memory could be accessed by the CPU,
> but the cache is tiny — so cache implementers must decide which memory parts to store for best performance.

*🧩 Cache Levels Explained*

| Level   | Name                      | Typical Size  | Speed          | Shared Between Cores | Purpose                                 |
| ------- | ------------------------- | ------------- | -------------- | -------------------- | --------------------------------------- |
| **L1d** | Level 1 Data Cache        | 32 KB         | Fastest        | No                   | Stores **data** used by the CPU         |
| **L1i** | Level 1 Instruction Cache | 32 KB         | Fastest        | No                   | Stores **instructions (code)**          |
| **L2**  | Level 2 Cache             | 256 KB – 1 MB | Slower than L1 | Usually No           | Backup for L1; holds both data and code |
| **L3**  | Level 3 Cache             | 4–64 MB       | Slowest cache  | **Yes**              | Shared by all cores; reduces RAM access |

*⚡ Memory Access Speed Comparison*

| Memory Type           | Approx. Access Time | Relative Speed (vs. CPU) | Typical Size   | Notes                                 |
| --------------------- | ------------------- | ------------------------ | -------------- | ------------------------------------- |
| **CPU Registers**     | ~0.3 ns             | 💨 1× (fastest)          | Few KB         | Used directly for active computations |
| **L1 Cache**          | ~1 ns               | ⚡ ~3× slower             | 32–64 KB       | Closest cache to the CPU              |
| **L2 Cache**          | ~3–5 ns             | ⚙️ ~10× slower           | 256 KB – 1 MB  | Per-core cache                        |
| **L3 Cache**          | ~10–20 ns           | 🌀 ~30–60× slower        | 4–64 MB        | Shared across cores                   |
| **Main Memory (RAM)** | ~60–100 ns          | 🐢 ~200–300× slower      | GBs            | Much slower than caches               |
| **SSD Storage**       | ~100 µs             | 🪨 ~300,000× slower      | Hundreds of GB | Used for files and paging             |
| **HDD Storage**       | ~5 ms               | 🐌 ~10,000,000× slower   | TBs            | Mechanical, extremely slow            |

*🕒 Memory Latency Timeline*
```
Registers     : |█| 0.3 ns
L1 Cache      : |█────| 1 ns
L2 Cache      : |█─────────| 4 ns
L3 Cache      : |█──────────────────| 15 ns
Main Memory   : |█────────────────────────────| 80 ns
SSD (NVMe)    : |█──────────────────────────────────────────────────────────────| 100 µs (100,000 ns)
HDD (Disk)    : |█────────────────────────────────────────────────────────────────────────────────────────────────────────────| 5 ms (5,000,000 ns)
```

🧩 Each bar represents access delay — the farther the memory is from the CPU, the longer it takes to reach it.

# 🧠 Cache Size Formula & Concepts

*Memory Address Breakdown*

> Each memory address is split into three parts: `[ TAG 🏷️ | Set Index 🗂️ | Block Offset 📦 ]`
- TAG 🏷️ → Identifies which memory block is stored in a line.
- Set Index 🗂️ → Determines which set the block maps to.
- Block Offset 📦 → Identifies the byte within the cache line.

*Cache Structure*


    CACHE 💾 (Total Size)
    +---------------------------------------------+
    | Set 0 🗂️                                    |
    |  +------------+  +------------+ ...         |
    |  | Line 0 📦  |  | Line 1 📦  | ...         |
    |  | TAG 🏷️     |  | TAG 🏷️     |             |
    |  +------------+  +------------+             |
    | Set 1 🗂️                                    |
    |  +------------+  +------------+ ...         |
    |  | Line 0 📦  |  | Line 1 📦  | ...         |
    |  | TAG 🏷️     |  | TAG 🏷️     |             |
    |  +------------+  +------------+             |
    | Set 2 🗂️                                    |
    |  +------------+  +------------+ ...         |
    |  | Line 0 📦  |  | Line 1 📦  | ...         |
    |  | TAG 🏷️     |  | TAG 🏷️     |             |
    |  +------------+  +------------+             |
    | ...                                         |
    | Set N 🗂️                                    |
    +---------------------------------------------+


Formula:

`Cache size` = `Cache line size` × `Associativity` × `Number of sets`

1️⃣ *Cache Line Size* 📦

- Smallest unit of memory transfer between RAM ↔ CPU cache.
- Typical: 64 bytes.
- Exploits spatial locality: accessing nearby memory is faster.
- Analogy: like buying a pack of apples 🍎; even if you need 1, you get the whole pack.

2️⃣ *Associativity* 🔗

- Number of cache lines per set.
- Determines how many blocks can fit in the same set.

> *Types:*
>
| Type              | Associativity | Description                                                       |
| ----------------- | ------------- | ----------------------------------------------------------------- |
| Direct-mapped     | 1             | Each address maps to **one line** only.                           |
| Set-associative   | 2,4,8…        | Each set can hold multiple lines → reduces **conflict misses ⚡**. |
| Fully associative | # of lines    | Any memory block can go anywhere in cache 🌐.                     |


3️⃣ *Number of Sets* 🗂️

- Number of distinct sets in the cache.

> - *Relationship:* `Number of sets` =  `Total cache lines`​ / `Associativity`

- Memory addresses use set bits to determine which set they map to.

💡 *Example*

- Cache line size = 64 bytes 📦
- 8-way associative 🔗
- 512 sets 🗂️

# 🧩 MESI Cache Coherence Protocol

MESI ensures that multiple CPU caches stay consistent when reading/writing the same memory.

1️⃣ *States of a Cache Line*

- `I` ❌  Invalid     → Data is not in cache or is stale
- `S` 🤝  Shared      → Data is in one or more caches, matches memory
- `E` 🏠  Exclusive   → Only this cache has it, matches memory
- `M` 🖊️  Modified    → Only this cache has it, differs from memory

2️⃣ *State Transitions (Simplified)*

*Read Miss*
>```
I ❌ (no data)  → fetch from memory
        ↘
         E 🏠  if no other cache has it
         S 🤝  if other caches have it
```

*Write Hit*
>```
S 🤝 (shared)  → invalidate others → M 🖊️
E 🏠 (exclusive) → modify locally → M 🖊️
M 🖊️ → modify locally → stay M 🖊️
```

*Write Miss*
>```
I ❌ → fetch line → invalidate other caches → M 🖊️
```

3️⃣ *Visual Cheat Sheet*

            +---------------------+
            |  CPU wants to read  |
            +---------------------+
                        |
                        v
        I ❌ → fetch line → E 🏠 or S 🤝
                        |
                        v
                CPU wants to write
                        |
     +------------------+------------------+
     |                                     |
     v                                     v
    S 🤝 → invalidate others → M 🖊️      E 🏠 → modify locally → M 🖊️
    M 🖊️ → modify locally → stay M 🖊️

4️⃣ *Example Scenario*

- Core 1 has a line in S 🤝
- Core 2 wants to write to it
- Core 1’s line becomes I ❌
- Core 2’s line becomes M 🖊️
- Memory is updated only when M 🖊️ is replaced or written back

✅ This is exactly how MESI prevents stale reads/writes in multi-core CPUs.


# 💾 Virtual Memory, Physical Memory & TLB

1️⃣ *Physical Memory (RAM)* 🧱

- Real hardware memory (RAM) used by the CPU.
- Each address here is a physical address.
- Accessing it directly would cause:
    - Fragmentation
    - Security issues
    - Process interference
- That’s why CPUs use virtual memory on top of it.

2️⃣ *Virtual Memory (VMEM)* 🧠

- Provides each process with its own address space (isolated).
- Virtual addresses are mapped to physical addresses by the MMU (Memory Management Unit).
- Enables:
    - Isolation 🛡️: one process can’t access another’s memory.
    - Paging 📄: divide memory into small equal-sized blocks.
    - Swapping 🔄: move inactive pages to disk when RAM is full.

3️⃣ *The MMU (Memory Management Unit)* ⚙️

- Hardware that performs address translation: `Virtual Address` → `Physical Address`.
- Uses the page table to find which frame corresponds to which page.
- This translation happens for every memory access, so speed matters ⚡.

4️⃣ *The TLB (Translation Lookaside Buffer)* ⚡

TLB = tiny cache inside the CPU for address translations.

| Concept      | Description                                         | Emoji |
| ------------ | --------------------------------------------------- | ----- |
| **TLB**      | Stores recently used **page → frame mappings**      | ⚡     |
| **TLB Hit**  | The mapping is found in the TLB → fast access 🚀    | ✅     |
| **TLB Miss** | Mapping not in TLB → must read page table (slow) 🐢 | ❌     |

TLB Process Overview
>```
CPU → Virtual Address 🧠
       |
       v
Check TLB ⚡
   |     \
 Hit ✅   Miss ❌
   |        |
Use frame   → Consult Page Table 🧾
             → Update TLB ⚡
             → Access memory 🧱
```

**TLB + Virtual Memory = Fast & Safe Memory Access**
| Step | Component                   | Action |
| ---- | --------------------------- | ------ |
| 1    | CPU issues virtual address  | 🧠     |
| 2    | TLB translates (if hit)     | ⚡      |
| 3    | If miss → Page table lookup | 🧾     |
| 4    | MMU uses physical address   | 🧱     |
| 5    | Cache/memory access happens | 🚀     |

5️⃣ *Putting It All Together*

```
Virtual Memory (per process) 🧠
       ↓  (translated by)
      MMU ⚙️  →  uses TLB ⚡ + Page Tables 🧾
       ↓
Physical Memory (RAM) 🧱
```