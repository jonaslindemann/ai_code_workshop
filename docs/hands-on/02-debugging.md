# Hands-on 2: Debugging with AI (TBD)

!!! abstract "Overview"

    **Time:** 25 minutes · **Workflow:** describe → diagnose → fix → verify

    Use an AI assistant to find and fix a bug in a scientific example. The
    focus is on *how* you describe the problem to the AI and how you
    **verify** its proposed fix.

## Material

Directory: [`python/calfem/`](https://github.com/jonaslindemann/ai_coding_example/tree/main/python/calfem)

## Instructions

### Step 1: Observe the symptom (≈ 5 min)

Run the broken example and compare the results with what you would expect
physically. Do **not** look for the bug in the code yet. Write down:

- what you expected to see,
- what you actually see,
- any error messages or warnings (copy them exactly).

### Step 2: Describe the problem to the AI (≈ 5 min)

Give the LLM the code **and** your description of the symptom. Try at
least two ways of describing it and compare the answers:

1. A vague description:

    > This code gives the wrong answer. Can you fix it?

2. A precise description:

    > This code solves \[problem\]. I expect \[expected behaviour\], but I get
    > \[observed behaviour\]. Here is the output: \[...\]. What could cause this?

### Step 3: Diagnose (≈ 5 min)

Ask the LLM to explain its reasoning *before* changing any code:

> List the possible causes of this behaviour, ordered by likelihood. For each,
> explain how I could confirm or rule it out.

> What would you print or plot to confirm the cause?

Check the most likely cause yourself, e.g. by adding print statements or
plots.

### Step 4: Fix and verify (≈ 10 min)

> Propose a minimal fix for this bug. Explain why it fixes the problem.

Apply the fix, then verify it:

- [ ] Does the result now match the physical expectation?
- [ ] Is the fix minimal, or did the AI also change unrelated code? (`git diff`)
- [ ] Does the fix treat the cause or only hide the symptom?

> How could we write a test that would have caught this bug?

## Discussion

- Did the precise description give a better diagnosis than the vague one?
- Did the AI find the bug straight away, or did it suggest plausible but wrong causes?
- Would you have found the bug faster without the AI?
