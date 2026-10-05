# Agents as Executables and Processes — Ideas

## The process as a concept

- The introduction of the process was one of the major advances of operating systems, along with virtual memory.
- Where did the concept come from? Two key sources (see `Notes/reading-list.md`):
  - Saltzer's 1966 MIT thesis, written for Multics (`saltzer1966traffic`).
  - Dijkstra's *Cooperating Sequential Processes* (1965, `dijkstra1965cooperating`) and the THE system (1968, `dijkstra1968the`).

## The process as a virtual von Neumann machine

- A von Neumann architecture has three parts:
  1. memory
  2. compute
  3. I/O
- A process contains each of these in virtualized form:

  | von Neumann | Process |
  |---|---|
  | Memory | Virtual memory |
  | Compute | Threads |
  | I/O | OS-specific operations to talk to the outside world |

- **Key point:** the OS does not change this execution model. Its job is to make sure all the virtual von Neumann machines (the processes) get fair use of the system.

## Open questions for the agent analogy (Claude's prompts)

- What are an agent's memory, compute, and I/O? (Context window and external memory? Model inference? Tool calls?)
- If an agent process is a virtual von Neumann machine, what does "fair use of the system" mean for agents (tokens, GPU time, rate limits, money)?

## References to read

See `Notes/reading-list.md`: Saltzer (1966), Dijkstra (1965, 1968), Conway (1963).

---

## Agentic AI is just computation (with statistics)

- Agentic AI is not that different from regular computation. What sets it apart is its extraordinary ability to solve mathematical problems through statistics.

### Programs as functions over numbers

- Any program can be represented as a (very large) number. This idea goes back to the Turing machine. *The Problem with Threads* (Lee, 2006) describes it well and points to the original sources.
- **Example: an image is a number.**
  - A pixel is a tuple `(a, b, c)` of RGB values. With 8 bits per channel, each value is 0–255.
  - An image is a list of these tuples, `(a1,b1,c1)(a2,b2,c2)…`.
  - Read as one sequence in memory, the whole image is a single number, however that number is interpreted.
- A program that changes the image (for example, smoothing its colors) is a mathematical function `f`. Its input is the number that represents the image, and its output is the number that represents the result.

### An LLM call as a single instruction

- Programs break down into instructions. Some are simple arithmetic (add, sub); modern architectures also have complex ones (matrix multiply, trigonometric functions).
- It is hard to imagine breaking an LLM's output down into a set of instructions. But a single-shot prompt can also be seen as a mathematical function.
- Models are non-deterministic because of temperature. If you factor out temperature, quantization rounding errors, etc., the model becomes deterministic.
- **From the perspective of a single shot, the model is one instruction that computes a really large number (the number that represents the output text).**
- So an LLM by itself has no side effects.

### The agent loop: from instruction to execution

- What makes agentic AI different is that execution does not stop after a single shot.
- A loop decides which instruction to execute next and uses the context as the input to that function. (See A-PXM, Cárdenas, Herrera, Monsalve & Bermudez, EuroLLVM 2026 [`cardenas2026apxm`].)
- From the harness's perspective there are three kinds of operation:

  | Operation | What it does | OS analogue |
  |---|---|---|
  | **Compute** (LLM call) | Computes, and partly determines the control flow (call a tool or call an LLM next?) | Instruction execution |
  | **I/O** (tool call) | Moves data in and out of the outside world (write a file, connect to a server) | System calls / I/O |
  | **Control flow** | Usually decided by the LLM itself, but can also follow a plan | Program counter / branching |

### Execution traces as compute graphs

- Whatever the harness, at the end of an execution you can see a trace of the tasks it ran (tool calls, LLM calls).
- Analyzing that trace yields a compute graph.
- Other frameworks, such as LangGraph, have adopted stricter graphs defined ahead of time.
- **A-PXM goes further: the graph is the program.**
  - Skills are written in a DSL and compiled into an MLIR dialect (AIS), where every dependency is an edge.
  - Compiler passes then optimize the graph:
    - prove which LLM calls can run in parallel, using effect resources
    - fuse chains of ask operations
    - deduplicate shared prompt prefixes
    - mark the critical path
  - The compiler emits an artifact with hints (priority, KV-cache prefix pinning, downstream nodes) that a graph-aware backend (vLLM) can use and other backends ignore.
- So there is a spectrum:
  1. compute graph recovered from a trace (after the fact)
  2. explicit graph framework (LangGraph)
  3. compiled graph with static analysis (A-PXM)
- A-PXM's motivation, "the stack is disconnected", is itself an OS argument. The agent framework, the LLM API, and GPU inference each see only their own layer: function calls, one request, a token stream. No layer sees the whole workflow. An OS kernel exists precisely to be the layer with the full picture. *(Claude's framing.)*

## The agent as a process: the full parallel

Regardless of the framework, an agent's execution maps completely onto a process:

| Process | Agent |
|---|---|
| Program instructions (the executable) | The folder structure: `CLAUDE.md` / `AGENTS.md`, skills, tools |
| Execution memory (data) | The context |
| Thread | The loop that picks the next instruction (LLM call or tool) |
| Static control flow, compiled in | Fully generic control flow. Tools are functions called whenever the current context needs them. The control-flow logic lives inside one or more models. |
| Process permissions / scope | The current workspace |
| OS libraries, POSIX | The interfaces for interacting with the outside world (tool and protocol standards?) |

- **A thread is the agent's ability to execute by selecting instructions.**
- The control-flow logic lives in one or more models. Examples:
  - **Jev** (TypeSafe), a "System One Model" that outputs type-safe structured values (classify, route, score, extract, branch) with calibrated confidence instead of text. In effect, a model built to be a fuzzy branch instruction.
  - **OpenAI Decisions API** (powered by GPT-6 Luna, limited preview, Sept. 29, 2026). You define questions and possible answers to classify content, route requests, or **choose an agent's next action**. This is instruction selection offered as an API.
- Two vendors shipped "decision models" within weeks of each other. That suggests the control-flow role inside the agent loop is becoming its own kind of model, separate from the general LLM that does the compute. *(Claude's observation.)*

### Many instances, one program

- One agent can be instantiated many times, the same way you open several documents in Word.
- Each instance is the same program instructions loaded into its own independent memory space (context).
- Side effects happen through interaction with the shared space outside the agent.

## References to read (this batch)

See `Notes/reading-list.md`: Lee (2006), Turing (1936), A-PXM (Cárdenas et al.), LangGraph, Jev (TypeSafe), OpenAI Decisions API.

## To clarify

- *Determinism*: setting temperature to 0 is not enough on its own. Batch-size effects in inference kernels also cause non-determinism. See Thinking Machines Lab, *Defeating Nondeterminism in LLM Inference* (He, 2025). Worth citing next to "factor out temperature and rounding errors".
