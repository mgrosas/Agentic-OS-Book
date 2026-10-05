# Protection — Ideas

## Scope and escalation

- Agents have a limited reach into the outside world, set by their current workspace.
- Some interactions need no escalation, like a process opening its own file. Others should require explicit permission.
- Traditional OSs provide clear interfaces to the outside world (OS libraries, POSIX). Agents need an equivalent.

## Agents should not modify their own souls

- Program data needs permissions, and so does the program itself.
- Agents should not be able to modify their "souls" (their instructions and identity), or at least not directly.
- Example: Karpathy's **autoresearch**. The agent may edit only one file (`train.py`); the human-owned instructions (`program.md`) are off limits to it.
- This is like a process that cannot write to its own code segment (read-only text pages).
- There is a relationship here to memory (episodic, long-term, etc.): which memories can an agent write, and which are read-only? See `../memory/`.

## Recovering what traditional OSs gave us

- One objective of the Agentic OS is to recover what traditional OSs already provide: isolation, permissions, etc.
- The harder new problem is interaction with humans, with the outside world, and the extremely distributed execution that happens inside a company. See `../introduction/ideas.md`.
- What we need back: a well-defined separation between kernel space and user space, i.e. between the process definition and the agent's execution.
