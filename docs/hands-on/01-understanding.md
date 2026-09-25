# Hands-on 1: Understanding & improving scientific code

!!! abstract "Overview"

    **Time:** 35 minutes · **Workflow:** understand → explain → document → refactor

    Use an AI assistant to understand an unfamiliar CALFEM finite element
    script, document it and refactor it without changing its results. Then
    critically evaluate what the assistant told you.

## Material

Directory: [`python/calfem/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/calfem)

| File | Description |
| ---- | ----------- |
| [`ex1_original.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_original.py) | **Starting point:** a 2D finite element problem written as a flat script |
| [`prompts_doc_refactor.md`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/prompts_doc_refactor.md) | All prompts for this exercise |
| [`ex1_modified_func.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_modified_func.py) | Example solution: refactored into functions |
| [`ex1_oop.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_oop.py) | Example solution: object-oriented version |

## Instructions

### Step 1: Run the original (≈ 5 min)

```bash
cd python/calfem
python ex1_original.py
```

Look at the plots and note the results. This is your **reference** for
checking later changes. Try to guess what the code does *before* asking the AI.

### Step 2: Understand (≈ 10 min)

Give `ex1_original.py` to your LLM and ask:

> Explain what this code does at a high level. What problem is it solving?

> Identify the main steps in the computation and describe them in simple terms.

> Explain the underlying numerical/engineering method used in this code.

> What assumptions does this implementation make about the physical or mathematical model?

Compare the explanation with your own guess. What physical problem is being
solved? What do the boundary conditions represent?

### Step 3: Document (≈ 5 min)

> Write clear docstrings for all functions in this code.

> Add inline comments explaining the most important parts of the code.

> Explain this code for a PhD student who is new to this method.

### Step 4: Refactor (≈ 10 min)

Refactor in small steps. **Run the code after each step** and check that
the results match Step 1.

> Refactor this code to improve readability without changing its functionality.

> Restructure the code in a cleaner structure. Use functions when appropriate.

If you have time:

> Convert this code to an OOP version. Use separation of concerns.

### Step 5: Critical evaluation (≈ 5 min)

This is the most important step. Ask:

> What parts of your explanation might be uncertain or incorrect?

> What assumptions did you make when interpreting this code?

> How could we verify that the AI-generated explanation is correct?

> Does the generated documentation match what the code actually does?

## Checklist

- [ ] Does the refactored code produce **the same results** as the original?
- [ ] Did the LLM invent physics, units or assumptions that are not in the code?
- [ ] Are there comments or docstrings that sound plausible but are wrong?
- [ ] How would you write an automated test that shows the refactoring is correct?
- [ ] Compare your result with [`ex1_modified_func.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_modified_func.py) and [`ex1_oop.py`](https://github.com/jonaslindemann/ai_coding_example/blob/main/python/calfem/ex1_oop.py).

!!! question "Extra: thinking at scale"

    > If this code were to be used in a large-scale HPC setting, what changes
    > would be needed in terms of structure, performance, or reproducibility?
