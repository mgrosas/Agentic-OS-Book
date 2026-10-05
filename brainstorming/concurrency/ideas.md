# Concurrency — Ideas

## Unpredictable access patterns

- What makes the Agentic OS more interesting is that an agent can interact with the outside world easily and **in no predetermined order**.
- Opening a file is not necessarily part of a fixed sequence of instructions. It may happen as the agent works out its own control flow at run time.
- So reasoning about concurrency is harder than in classic parallel programming, where the access patterns are visible in the code.
- **There are many points of contention that will need to be curated.**

## What the Agentic OS needs

- Clearly defined concurrency models.
- Orchestration of schedulable resources.
- Shared environments for events (see `../io/`).

## Open questions (Claude's prompts)

- Where are the contention points? Shared files, databases, APIs with rate limits, human attention, physical machines.
- Do we need agent-level locks or transactions, or optimistic approaches like version checks and merges?
- Relevant classics: Dijkstra (1965) on mutual exclusion and semaphores; Lee (2006) on why threads make non-determinism hard to reason about.
