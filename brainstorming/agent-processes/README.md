# Agents as Executables and Processes

Brainstorming for the section on treating an agent like a program: the *executable* is the static definition (model, prompt, tools, configuration) and the *process* is a running instance with its own context, state, and lifecycle.

## Starting questions

- What exactly makes up an agent "executable"? What is the equivalent of the binary, the loader, and linked libraries?
- What state belongs to an agent "process" (context window, memory, open tool sessions, credentials)?
- Which OS process concepts carry over cleanly (fork, exec, scheduling, signals, IPC, isolation), and which break?
- How do existing systems (e.g. AIOS) model this, and where does our view differ?
