# Related Papers

Initial literature collection for the agent-system topics in the four table-of-contents images supplied on 2026-09-27. Chapter numbers below refer to those images, including the visible beginning of Chapter 9; they do not define our manuscript outline.

This collection is restricted to **2025 and 2026**. It currently contains **8 papers and surveys, all from 2025**; no 2026 papers were included in the original selection. The cutoff uses the verified publication year, or the first preprint year when no publication venue was verified. AIOS, LongMemEval, and RouteLLM qualify by their 2025 publications even though their first preprints appeared earlier.

Discovery used Google Scholar; bibliographic details and relevance were checked against primary paper pages, proceedings, and author-hosted PDFs. This is a curated starting collection, not an exhaustive literature review or a claim to cover the latest 2026 work.

## Contents

- [BibTeX bibliography](references.bib): one entry per reference, using citation keys that match the PDF filenames.
- [PDFs](pdfs/): unmodified reading copies, named by citation key.

Extended reading notes and critiques can be added to [Notes](../Notes/) using the same citation keys.

## Start here

The order below is a suggested reading sequence, not a ranking of research quality.

1. [AIOS](pdfs/mei2025aios.pdf) — Study a concrete agent runtime with kernel services and scheduling.
2. [MemoryOS](pdfs/kang2025memoryos.pdf) — Examine a three-tier memory architecture.
3. [MCP-Zero](pdfs/fei2025mcpzero.pdf) — Study dynamic tool discovery and hierarchical retrieval.
4. [A Survey of AI Agent Protocols](pdfs/yang2025agentprotocols.pdf) — Compare the purposes and boundaries of agent protocols.

## Map to the photographed topics

| Chapter | Topic | Suggested references |
| --- | --- | --- |
| 1 | Agent OS definitions and boundaries | [AIOS](pdfs/mei2025aios.pdf) |
| 2 | Control, coordination, and memory | [AIOS](pdfs/mei2025aios.pdf) |
| 3 | RPA, single agents, and broader systems | [AIOS](pdfs/mei2025aios.pdf) |
| 4 | Connections, tools, agents, orchestration, memory, governance | [AIOS](pdfs/mei2025aios.pdf) |
| 5 | Memory tiers, retrieval, updates, and context budget | [MemoryOS](pdfs/kang2025memoryos.pdf), [A-Mem](pdfs/xu2025amem.pdf), [LongMemEval](pdfs/wu2025longmemeval.pdf) |
| 6 | Router, planner-executor, blackboard, event bus | [RouteLLM](pdfs/ong2025routellm.pdf) |
| 7 | Agent communication and protocol boundaries | [Protocol survey](pdfs/yang2025agentprotocols.pdf) |
| 8 | Tool routing and capability discovery | [MCP-Zero](pdfs/fei2025mcpzero.pdf) |
| 9 | Task state, shared state, retries, and recovery | Further 2025–2026 references needed for state correctness, retries, and recovery. |

## Reading boundaries

- The photographs supply an organizing framework. Their three-pillar and six-layer descriptions are not assumed to be a standardized research taxonomy.
- Chapter mappings and suggested uses are our synthesis. Screening primarily covered abstracts, bibliographic records, and selected sections; the list does not claim a complete critical reading of every paper.
- Conversational memory, retrieved knowledge, and durable workflow state are different objects. Memory benchmark results do not establish transaction or concurrency guarantees.
- RouteLLM selects models. MCP-Zero addresses tool discovery. These routing problems should be distinguished.
- The retained set needs additional 2025–2026 sources for RPA comparisons, planner-executor and blackboard/event-bus designs, governance, and durable state, idempotent retries, and recovery. The chapter map does not imply complete coverage of those topics.

## Protocol specifications (supplementary, not research papers)

- [Model Context Protocol, revision 2025-11-25](https://modelcontextprotocol.io/specification/2025-11-25): a versioned reference for client/server tool and context integration.
- [Agent2Agent Protocol, version 0.3.0](https://a2a-protocol.org/v0.3.0/specification/): a versioned reference for agent discovery, messages, tasks, and artifacts.

These are deliberately pinned versions, not claims about the latest release. MCP and A2A have different roles; their specifications should not be treated as interchangeable. The 2025 protocol survey is a historical snapshot rather than the authority for later wire formats.
