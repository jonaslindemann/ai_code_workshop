# Hands-on 2: Debugging with AI

!!! abstract "Overview"

    **Time:** 25 minutes · **Workflow:** describe → diagnose → fix → verify

    A scientific program that **runs without errors but gives the wrong
    answer**. Use an AI assistant to find the cause, make the smallest
    possible fix, and use tests and physical reasoning to confirm it.

    > **AI proposes. Tests and physical reasoning determine correctness.**

## Material

Directory: [`python/debugging/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/debugging)

| File | Description |
| ---- | ----------- |
| [`debug_temperature.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/debug_temperature.py) | **Starting point:** 2D steady-state heat conduction in a square plate. Contains a bug. |
| [`tests/test_debug_temperature.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/tests/test_debug_temperature.py) | Tests that check the result against the physical problem |
| [`prompts.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/prompts.md) | Suggested prompts for this exercise |
| [`run_tests.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/run_tests.md) | How to run the tests |

!!! warning "No peeking"

    The directory also contains `debug_temperature_fixed.py` and
    `instructor_solution.md`. Leave them until you have finished the exercise.

## The physical problem

The program is supposed to model steady-state heat conduction in a square plate:

- plate dimensions: 1 × 1
- constant isotropic conductivity
- left edge: **T = 0**
- right edge: **T = 100**
- top and bottom edges: insulated
- no internal heat source

The program runs, but its result does not match this problem. Your task is
to find out why and make the **smallest possible fix**.

## Prerequisites

In addition to CALFEM (see [Setup](../setup.md)), you need `pytest` and `matplotlib`:

```bash
pip install pytest matplotlib
```

## Instructions

### Step 1: Observe the symptom (≈ 5 min)

```bash
cd python/debugging
python debug_temperature.py --plot
pytest -q
```

Before you ask the AI anything, answer for yourself:

- What **should** the temperature field look like for this problem?
- Which features of the plot contradict that?
- Which tests fail?

### Step 2: Describe the problem to the AI (≈ 5 min)

Give the LLM `debug_temperature.py` and start from the symptom, **not** from
a guess about the cause:

> This Python program runs without an exception, but I suspect that the
> temperature field does not represent the physical problem described in the
> module docstring. Diagnose possible causes. Do not change the code yet.

Then show it the result. Paste a screenshot of the plot or describe it,
together with the test output:

> Here is the temperature field produced by the program. Before looking at
> the code again: what should the field look like for the problem described
> in the module docstring (T=0 on the left, T=100 on the right, insulated top
> and bottom)? Which features of the plot contradict that expectation?

### Step 3: Diagnose (≈ 5 min)

Ask the AI to connect the physical model to the code:

> Trace the boundary-condition information from the geometry definition to
> the calls to `applybc`. Explain which physical edge each marker refers to.
> Be precise and quote the relevant code locations.

Challenge the diagnosis:

> What evidence would distinguish a boundary-condition error from a numerical
> solver error? Suggest concrete checks I can perform without rewriting the
> whole program.

??? tip "Hint: stuck? (only if you have formed a hypothesis)"

    Ask the AI to visualise the model definition itself:

    > Add a plot of the geometry that shows which boundary marker is attached
    > to each edge. Do not change the solver.

### Step 4: Fix and verify (≈ 10 min)

> Propose the smallest code change that makes the implementation match the
> stated physical problem. Do not introduce unrelated refactoring.

Review the proposed change (`git diff`), apply it and verify it:

```bash
pytest -q                           # expected: 3 passed
python debug_temperature.py --plot
```

> After the fix, what numerical properties should hold for the solution?
> Suggest tests that check the physical boundary conditions and the expected
> qualitative behaviour of the temperature field.

!!! note "Rule for this exercise"

    Do not accept a fix just because the code runs. Connect:

    **code → physical model → numerical result → verification**

## Checklist

- [ ] All three tests pass.
- [ ] The plot matches what you expected in Step 1.
- [ ] The fix is minimal. The solver and assembly are unchanged.
- [ ] You can explain *why* the original code gave the result it did.

## Discussion

1. What did the LLM suspect at first? Solver, assembly, element type, something else?
2. Did it find the actual cause? How many prompts did that take?
3. Did it propose changing more code than necessary?
4. What evidence convinced you that the fix was correct?
5. Would a generic unit test have found this bug without knowing the
   physical boundary conditions?

Afterwards, compare your fix with
[`debug_temperature_fixed.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/debug_temperature_fixed.py)
and read
[`instructor_solution.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/debugging/instructor_solution.md).
