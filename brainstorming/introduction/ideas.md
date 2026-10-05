# Introduction — Ideas

## Why operating systems exist

- The OS was born because computers lacked the ability to be multi-purpose. Today's operating systems are the result of slow, incremental changes.

## Early machines: the human as the OS

- The first computers were single-program machines. Programs had fixed addresses for both code and data; there were no linkers or loaders.
- Orchestrating work required a human operator who loaded one program at a time.
- **The scheduler was a person.** The operator kept a physical queue of program tapes and picked the next one for non-preemptive execution. (Reference: [*EDSAC 1951*](https://www.youtube.com/watch?v=6v4Juzn10gM), a film of **EDSAC** at Cambridge being operated [`edsac1951film`].)
- **Libraries were physical tape.** Reusable routines were pieces of tape copied by hand onto the program tape. This was manual linking with no real code reuse, since everything was inlined.

## Toward multiprogramming and multi-user systems

- Computers evolved to need better orchestration of programs running at the same time.
- MULTICS (1960s) was one of the first operating systems. It started as a project to let multiple users share the same machine.
- At the same time, programming was moving from monolithic code toward procedural programming with subroutines (FORTRAN II, 1958) and coroutines (Conway, 1958; published 1963 [`conway1963separable`]).

## The goals of an operating system

The ultimate goal of an OS is to:

1. Make each process believe and behave as if it were the only one running on the system.
2. Avoid conflicts whenever they arise from multiple processes working concurrently.
3. Isolate processes from the privileged runtime (the kernel) and from low-level hardware, for security.

Two of the major advances were **virtual memory** and **the process as a concept**. See `../agent-processes/` and `../memory/`.

## Thesis: an Agentic OS for the enterprise

- **This book is about enterprise AI and the Agentic OS.** We lay the groundwork for what an Agentic OS for the distributed, complex enterprise is.
- Opening hook: agentic AI is not that different from regular computation. See `../agent-processes/ideas.md`.
- The Agentic OS should recover what traditional OSs provide (isolation, permissions, etc.). The new, harder problem is interacting with humans, with the outside world, and with the extremely distributed execution of a company, where many agents run alongside humans and business infrastructure.

### A company is organized like an operating system

| Operating system | Organization |
|---|---|
| Shared file system | Shared database |
| Contention for shared devices (keyboard, mouse, printers) | Contention for shared resources, e.g. production machines driven by orders from sales |
| A clear GUI for interacting with the system | A distributed I/O layer in many shapes and forms |
| Events and buses that bring external events into the system | The event-driven nature of a business: a sale happens, a machine dies, a purchase arrives |

### What the enterprise Agentic OS must bring back

1. Separation between processes.
2. Clearly defined concurrency models (`../concurrency/`).
3. Shared environments for events (`../io/`).
4. Orchestration of schedulable resources.
5. A well-defined separation between kernel space and user space: the process definition vs. agent execution (`../protection/`).

## References to read

See `Notes/reading-list.md`: the EDSAC 1951 film, Conway (1963), Dijkstra (1965, 1968).

## To verify

- *MULTICS dates*: the project started around 1964–65 (MIT, GE, Bell Labs), with time-sharing as its goal.
- *EDSAC film*: the YouTube copy is a re-upload by the user *rthelen*. Before citing it in the book, find the canonical source (likely the University of Cambridge Computer Laboratory).
