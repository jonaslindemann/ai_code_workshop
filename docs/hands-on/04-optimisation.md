# Hands-on 4: Optimisation

!!! abstract "Overview"

    **Time:** 25 minutes · **Workflow:** implement one change → verify → benchmark → compare

    Take one hypothesis from [Hands-on 3](03-profiling.md), implement it with
    the help of the AI, and show that the code is **faster** and **still
    correct**.

## Material

Directory: [`python/calfem/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/calfem)

| File | Description |
| ---- | ----------- |
| [`ex2_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_original.py) | **Starting point** |
| [`prompt_ai_opt.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/prompt_ai_opt.md) | Prompts for this exercise |
| [`ex2_opt1.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_opt1.py) … [`ex2_opt4.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_opt4.py) | Example solutions: a sequence of optimisation steps (look at them afterwards) |

## Instructions

### Step 1: Make results checkable (≈ 5 min)

`ex2_original.py` only prints **timings**, not results. Without a result
to compare, you cannot tell whether an optimisation broke the computation.

Make a copy of the script and ask the AI to add a result summary:

```bash
cp ex2_original.py ex2_mine.py
```

> Modify `run_case` so that it also returns the maximum absolute displacement
> and the maximum von Mises stress, and print them in the summary. Do not
> change anything else.

Run **both** versions and check that the timings match and that you now have
reference values for the results.

### Step 2: Implement one change (≈ 10 min)

Pick **one** hypothesis from Hands-on 3 and ask for a focused change:

> How could this element loop be rewritten to reduce runtime?

> Suggest improvements that preserve correctness and readability.

> Implement only \[your chosen change\]. Keep the rest of the code unchanged.

Review the diff before running it (`git diff`, or compare the files side by side).

### Step 3: Verify (≈ 5 min)

- [ ] Do the maximum displacement and von Mises stress match the reference
      (to within a sensible tolerance, e.g. `1e-10` relative)?
- [ ] Are the number of elements and DOFs unchanged?

If the results differ, ask the AI why and decide whether the difference is
acceptable (floating-point rounding) or a bug.

### Step 4: Benchmark and compare (≈ 5 min)

Run the original and optimised versions with the same `MESH_SIZES` and
`PROFILE_REPEATS` and record the timings:

| Phase       | Original (s) | Optimised (s) | Speed-up |
| ----------- | ------------ | ------------- | -------- |
| mesh        |              |               |          |
| assembly    |              |               |          |
| solve       |              |               |          |
| postprocess |              |               |          |

Then compare your approach with the example solutions
[`ex2_opt1.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_opt1.py) →
[`ex2_opt4.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex2_opt4.py).

## Discussion

- Was your hypothesis from Hands-on 3 confirmed?
- How much faster did it get? Is the speed-up the same for all mesh sizes?
- Did any AI suggestion make the code slower, less readable or wrong?
- Share your best speed-up (and how you verified it) with the room.
