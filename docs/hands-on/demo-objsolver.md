# Demo: from assistant to agent

!!! abstract "Overview"

    **Time:** 10 minutes · **Format:** live demonstration

    A coding **agent** working on a larger, multi-library C++ finite element
    code: exploring the codebase, building it, adding a benchmark and
    optimising the solver while checking that the results stay the same.

## Material

| Directory | Description |
| --------- | ----------- |
| [`cpp/objsolver_original/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/cpp/objsolver_original) | Starting point: object-oriented 3D beam/frame FEM solver (`ofem`, `ofsolve`, `ofmath` and `util` libraries) |
| [`cpp/objsolver/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/cpp/objsolver) | After agent work: optimised build flags, `--benchmark` mode and faster solver |
| [`cpp/objsolver/benchmark_results.txt`](https://github.com/jonaslindemann/ai_coding_example/blob/main/cpp/objsolver/benchmark_results.txt) | Benchmark results from the optimisation steps |
| [`cpp/objsolver/.claude/settings.json`](https://github.com/jonaslindemann/ai_coding_example/blob/main/cpp/objsolver/.claude/settings.json) | The commands the agent was allowed to run |

The `bin/` directory contains test models (`*.df3`), from small bridges to a
large building with about 1000 nodes and 2500 elements.

## What to look for

- How does the agent build an understanding of a codebase it has not seen before?
- How is the agent's work checked? Look at the benchmark, the result comparison and the
  permissions the agent was given.
- What does the agent do on its own, and what decisions does the human still make?

## Try it yourself (optional)

Requires a C++20 compiler, CMake ≥ 3.20 and [vcpkg](https://vcpkg.io/)
(`eigen3`, `nlohmann-json`, `cpp-base64`, `fmt`). `CMakePresets.json` assumes
vcpkg in `C:/vcpkg`, so adjust `toolchainFile` if yours is elsewhere.

```bash
cd cpp/objsolver
cmake --preset windows-release
cmake --build --preset release
cd bin
./objsolver --benchmark . --repeat 30
./objsolver large_building.df3 --displacements --reactions
```

Suggested prompts for an agent started in `cpp/objsolver_original`:

> Give me an overview of this codebase: its libraries, main classes and how a
> model is read, solved and written.

> Add a --benchmark option that runs all .df3 files in a directory, repeats
> each run n times and prints a table with load time and min/avg/max solve time.

> Using the benchmark, identify the main bottlenecks and implement
> optimisations one at a time, verifying that displacements and reactions are
> unchanged after each.
