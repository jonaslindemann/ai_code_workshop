# Hands-on 3: Profiling & performance reasoning

!!! abstract "Overview"

    **Time:** 35 minutes · **Workflow:** profile → interpret → ask AI → form hypotheses

    Measure where a CALFEM stress analysis spends its time, and use an AI
    assistant to interpret the profile and form hypotheses about what to
    optimise. **Do not change the code yet.** You will do that in
    [Hands-on 4](04-optimisation.md).

## Material

Directory: [`python/calfem/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/calfem)

| File | Description |
| ---- | ----------- |
| [`ex2_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_original.py) | **Starting point:** 2D plane stress analysis with two materials, timed in four phases: mesh, assembly, solve and post-processing |
| [`prompt_ai_opt.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/prompt_ai_opt.md) | Prompts for this exercise |

## Instructions

### Step 1: Get a baseline (≈ 5 min)

```bash
cd python/calfem
python ex2_original.py
```

The script prints the number of elements and DOFs and the average time for
each phase. Write down the timings.

The problem size is set at the top of the file:

```python
MESH_SIZES = [0.025]   # smaller value = finer mesh
PROFILE_REPEATS = 3
```

If it runs too slowly or too quickly on your laptop, adjust `MESH_SIZES`.
Try e.g. `[0.05, 0.025, 0.0125]` to see how each phase **scales** with
problem size.

### Step 2: Profile (≈ 10 min)

Run the script under the Python profiler:

```bash
python -m cProfile -o output.prof ex2_original.py
```

Print the 20 most expensive functions:

```bash
python -c "import pstats; pstats.Stats('output.prof').sort_stats('cumtime').print_stats(20)"
```

Or explore the profile interactively (optional):

```bash
pip install snakeviz
snakeviz output.prof
```

### Step 3: Interpret with AI (≈ 10 min)

Give the LLM the code, your timings **and** the profiler output:

> Based on this profiler output, suggest the three most promising optimisation opportunities.

> Which changes are likely to matter most: meshing, assembly, solver, or postprocessing?

> Explain why the assembly phase takes the time it does. What is happening inside the loop?

### Step 4: Form hypotheses (≈ 10 min)

Before you change anything, write down **one or two hypotheses**, for example:

> *"Assembly is slow because of X. If we change it to Y, assembly time should
> drop by roughly Z, and the results should be unchanged."*

Ask the AI to challenge your hypotheses:

> Here is my hypothesis about the performance bottleneck: \[...\]. What evidence
> supports or contradicts it? How could I test it?

## Checklist

- [ ] Which phase dominates the runtime? Does this change with mesh size?
- [ ] Did the AI's explanation match what the profiler actually shows?
- [ ] Did the AI suggest optimisations for parts of the code that barely matter?
- [ ] Do you have a concrete, testable hypothesis to take into Hands-on 4?
