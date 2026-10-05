# Memory — Ideas

## Virtual memory

Virtual memory has two purposes:

1. **For the process:** each process can assume full control of its address space. A program, in whatever language and running in its own process, does not need to pre-define exact memory addresses to sit alongside other processes (special programs aside).
2. **For the OS:** the OS is free to decide where data really lives in physical memory, which enables tricks like swap, page migration, etc.

## The file system as an extension of memory

- The file system deserves special attention because it is an extension of memory.
- Modern operating systems keep I/O strictly separate from (virtual) memory.
- There are still techniques that expose I/O space as memory (e.g. `/dev/mem`).
- Other systems took a more generic approach, a **single-level store**, in which files and I/O were almost plain pointers into virtual memory. Examples: **MULTICS** (segments) and **IBM System/38** (later AS/400).
- Modern caching mechanisms rely on these techniques.

## Context as memory, and the organizational parallel

- The context is the agent's current execution memory (data). See `../agent-processes/ideas.md`.
- In an organization, the equivalent of a shared file system is a shared database.
- Agent memory types (episodic, long-term, etc.) have a permission side: which memories can an agent modify, and which are part of its read-only "soul"? See `../protection/ideas.md`.

## Open questions for the agent analogy (Claude's prompts)

- What is an agent's "address space"? Can an agent assume full control of it the way a process does?
- What are the equivalents of swap and page migration for agent context (summarization, offloading to external memory)? Related: MemoryOS, A-Mem, Mem0 in `Related Papers/`.

## To verify

- *Origin of virtual memory*: usually credited to the **Atlas** computer (Manchester, 1962).
