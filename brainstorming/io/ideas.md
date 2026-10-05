# I/O — Ideas

## I/O is event-driven

- I/O is a big part of what an OS does.
- By nature, I/O is event-driven. It reacts to signals and produces signals that go to handlers the OS has registered for a process (in user space or kernel space).
- The kernel needs a common OS bus to route the different signals to the right callback mechanisms.

## Organizations are event-driven too

- Where an OS defines events and buses that bring external events into the system, an organization is already event-driven: a sale happens, a machine dies, a purchase arrives.
- Where an OS has a clear GUI, an organization has a distributed I/O layer in many shapes and forms.
- See the OS ↔ organization table in `../introduction/ideas.md`.

## Reference to read

- Saltzer (1966) treats I/O control as a special case of inter-process communication. That fits the event-driven, signal-routing view above. See `Notes/reading-list.md`.

## Relationship to memory

- The boundary between I/O and memory (memory-mapped I/O, `/dev/mem`, single-level stores) is covered in `../memory/ideas.md`.

## Open questions for the agent analogy (Claude's prompts)

- Are tool calls and MCP servers the agent's I/O devices? What plays the role of the "common bus" (e.g. MCP)? Related: the agent protocols survey and MCP-Zero in `Related Papers/`.
- What are an agent's interrupts and signals: user messages, webhooks, tool results?
