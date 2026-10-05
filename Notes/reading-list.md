# Reading List

Papers to read for the brainstorming sections. Citation keys are in `Related Papers/foundations.bib`.

## To read

- [ ] **Watch: *EDSAC 1951* (film)** (`edsac1951film`)
  - Why: shows the human operator acting as the scheduler, with a physical queue of program tapes and one program loaded at a time.
  - For: `brainstorming/introduction/`
  - [YouTube](https://www.youtube.com/watch?v=6v4Juzn10gM)

- [ ] **Saltzer (1966), *Traffic Control in a Multiplexed Computer System*** (`saltzer1966traffic`)
  - Why: an early definition of the *process* in the Multics context. It also treats I/O control as a special case of inter-process communication.
  - For: `brainstorming/agent-processes/`, `brainstorming/io/`
  - [PDF (MIT)](https://web.mit.edu/saltzer/www/publications/TRs+TMs/Multics/TR-030.pdf)
- [ ] **Dijkstra (1965), *Cooperating Sequential Processes*, EWD 123** (`dijkstra1965cooperating`)
  - Why: the founding text of concurrent programming. It covers sequential processes, mutual exclusion, and semaphores.
  - For: `brainstorming/agent-processes/`, `brainstorming/introduction/`
  - [EWD archive (UT Austin)](https://www.cs.utexas.edu/~EWD/index01xx.html)
- [ ] **Dijkstra (1968), *The Structure of the "THE"-Multiprogramming System*** (`dijkstra1968the`)
  - Why: an OS built as layers of cooperating processes, and an early example of layered kernel design.
  - For: `brainstorming/agent-processes/`, `brainstorming/introduction/`
- [ ] **Conway (1963), *Design of a Separable Transition-Diagram Compiler*** (`conway1963separable`)
  - Why: the first published description of coroutines. It is relevant to the shift toward procedural programming and to cooperative scheduling.
  - For: `brainstorming/introduction/`, `brainstorming/agent-processes/`
- [ ] **Lee (2006), *The Problem with Threads*** (`lee2006threads`)
  - Why: describes programs as functions over numbers (from Turing machines) and argues that threads make non-determinism hard to reason about.
  - For: `brainstorming/agent-processes/`, `brainstorming/concurrency/`
- [ ] **Turing (1936), *On Computable Numbers*** (`turing1936computable`)
  - Why: the original source for "any program is a number". Lee cites this lineage. *(Suggested by Claude.)*
  - For: `brainstorming/agent-processes/`
- [ ] **Cárdenas, Herrera, Monsalve & Bermudez (2026), *A-PXM: Multi-Agent Workflows Analysis and Optimizations via MLIR*** (`cardenas2026apxm`, EuroLLVM 2026 lightning talk)
  - Why: agent skills compiled into a graph (AIS MLIR dialect). Static analysis proves parallelism, and compiler hints flow to vLLM scheduling. "The graph is the program."
  - For: `brainstorming/agent-processes/`, `brainstorming/concurrency/`
  - [Slides](https://llvm.org/devmtg/2026-04/slides/lightning_talk/lightning_talk_cardenas.pdf) · [Code](https://github.com/randreshg/a-pxm)
  - **Full paper forthcoming.** Replace the slides citation and add the PDF once it is out.
- [ ] **Karpathy, *autoresearch*** (code repository, 2026)
  - Why: the agent may modify only one file (`train.py`); the human-owned `program.md` is off limits. An example of agents not modifying their own "soul".
  - For: `brainstorming/protection/`
- [ ] **LangGraph** (framework docs)
  - Why: makes agent execution an explicit graph defined ahead of time, in contrast to compute graphs recovered from traces.
  - For: `brainstorming/agent-processes/`
- [ ] **He / Thinking Machines Lab (2025), *Defeating Nondeterminism in LLM Inference*** (blog)
  - Why: non-determinism remains even at temperature 0 (batch invariance). Relevant to "an LLM call is a deterministic function". *(Suggested by Claude.)*
  - For: `brainstorming/agent-processes/`
- [ ] **Almeida / TypeSafe (2026), *Introducing System One Models & Jev*** (blog, Sept. 15, 2026)
  - Why: a model that emits type-safe structured decisions (classify, route, score, branch) with calibrated confidence. It is trained with "RL for Calibrated Decisions" and is said to be 40–200x faster than LLMs on comparable tasks. A concrete example of control flow embedded in a model.
  - For: `brainstorming/agent-processes/`
  - [Blog post](https://typesafe.ai/blog/introducing-system-one-models-and-jev)
- [ ] **OpenAI Developers (2026), *Decisions API*, powered by GPT-6 Luna** (announcement, Sept. 29, 2026, limited preview)
  - Why: you define questions and possible answers to classify content, route requests, or choose an agent's next action. The model as a control-flow / instruction-selection primitive, alongside Jev.
  - For: `brainstorming/agent-processes/`
  - [Announcement on X](https://x.com/OpenAIDevs/status/2105003318917697873). Find the official docs page before citing.
