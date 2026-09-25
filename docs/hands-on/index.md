---
icon: lucide/flask-conical
---

# Hands-on

All hands-on exercises use the example repository
[**jonaslindemann/ai_coding_example**](https://github.com/jonaslindemann/ai_coding_example).
The core exercises use the CALFEM for Python examples in
[`python/calfem/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/calfem).

| Time        | Exercise                                                                     | Material |
| ----------- | ---------------------------------------------------------------------------- | -------- |
| 09:30–10:05 | [1. Understanding & improving scientific code](01-understanding.md)          | [`ex1_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_original.py) |
| 10:05–10:30 | [2. Debugging with AI](02-debugging.md)                                      | Broken scientific example |
| 10:45–11:20 | [3. Profiling & performance reasoning](03-profiling.md)                      | [`ex2_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_original.py) |
| 11:20–11:45 | [4. Optimisation](04-optimisation.md)                                        | [`ex2_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_original.py) |
| 11:45–11:55 | [Demo: from assistant to agent](demo-objsolver.md)                           | [`cpp/objsolver/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/cpp/objsolver) |

## Before you start

Make sure you have completed the [Setup](../setup.md): a working Python
environment with CALFEM installed, access to an AI/LLM service, and a local
copy of the example repository:

```bash
git clone https://github.com/jonaslindemann/ai_coding_example.git
cd ai_coding_example/python/calfem
```

## How to work

!!! tip "Guidelines for all exercises"

    - **Any LLM works.** A browser chat where you paste code is enough. If you
      use an assistant in your editor or terminal, that is fine too.
    - **Try it yourself first.** The repository contains example solutions
      (`ex1_oop.py`, `ex2_opt1.py`, …). Look at them *after* you have made your
      own attempt. Your LLM will give different answers, and comparing them is
      part of the exercise.
    - **Verify everything.** Run the code after every change. Treat AI output
      like a pull request from a colleague you have never worked with before.
    - **Commit often.** With Git, commit before each change
      (`git commit -am "before refactoring"`) so you can compare and roll back.
    - **Take notes.** Write down where the AI was helpful and where it was
      wrong. We will collect results from the room at the end.

## Prompt files in the repository

Each example directory contains the prompts used when the material was
developed:

- [`python/calfem/prompts_doc_refactor.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/prompts_doc_refactor.md): understanding, documenting and refactoring
- [`python/calfem/prompt_ai_opt.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/prompt_ai_opt.md): performance and optimisation

See [More examples](more-examples.md) for the other examples in the
repository (C++ porting, documentation, user interfaces, …) that you can
explore after the workshop.
