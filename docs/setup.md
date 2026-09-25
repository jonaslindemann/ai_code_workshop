---
icon: lucide/wrench
---

# Workshop Setup

## AI-Assisted Large-Scale Scientific Software Development

This page describes how to prepare your computer for the hands-on parts of the workshop.

Please complete the setup **before the workshop**. We want to spend the workshop experimenting with AI-assisted development rather than installing software.

## What you need

Please bring your own laptop with:

* a modern web browser
* access to an AI/LLM service
* Git
* Python 3
* a text editor or development environment
* the workshop repository downloaded or cloned

The core hands-on exercises use **Python**. C++ examples may be demonstrated during the workshop, but a C++ development environment is not required for the main exercises.

## 1. AI/LLM access

You need access to at least one AI/LLM service capable of working with programming tasks.

Examples include:

* ChatGPT
* Claude
* Gemini
* Microsoft Copilot
* GitHub Copilot
* an AI service provided by your university or organisation
* a suitable locally hosted model

**No particular commercial AI service is required.**

A browser-based conversational LLM is sufficient for the core exercises. If you already use an AI coding assistant or coding agent integrated into your editor or terminal, you are welcome to use it as well.

### Check with your home university

Before the workshop, please check which AI/LLM services are available and approved for use by your home university or organisation.

Make sure that you can log in and use your chosen service **before arriving at the workshop**.

Different participants are encouraged to use different LLMs. Part of the workshop will be comparing how different tools approach the same scientific programming problems.

### Research code and sensitive information

The workshop uses public example code, so you do **not** need to provide your own research software.

Please do not submit confidential, sensitive, unpublished, security-sensitive, or otherwise restricted source code or information to an external AI service.

Always follow the policies of your home university or organisation when using AI services.

## 2. Get the workshop repository

The workshop material is available from:

https://github.com/jonaslindemann/ai_coding_example

If you have Git installed, clone the repository:

```bash
git clone https://github.com/jonaslindemann/ai_coding_example.git
cd ai_coding_example
```

Alternatively, use GitHub's **Code → Download ZIP** option and unpack the archive on your computer.

## 3. Python

The core exercises require a reasonably recent version of Python 3.

Check your installation with:

```bash
python --version
```

On some systems the command may instead be:

```bash
python3 --version
```

We recommend using a Python virtual environment for the workshop.

### Linux/macOS

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### Windows PowerShell

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
```

Once activated, update `pip`:

```bash
python -m pip install --upgrade pip
```

## 4. Python packages

The scientific examples use packages including:

* NumPy
* SciPy
* CALFEM for Python
* Gmsh

Install the required packages according to the instructions provided with the workshop repository.

Before the workshop, please verify that the CALFEM examples can be executed on your computer.

## 5. Editor or development environment

Use an editor or IDE that you are comfortable with.

Examples include:

* Visual Studio Code
* PyCharm
* Vim/Neovim
* Emacs
* another Python-capable editor or IDE

Visual Studio Code is a convenient choice if you do not already have a preferred development environment, but **it is not required**.

Participants who already have an AI assistant integrated into their editor are welcome to use it.

## 6. Git

Check that Git is available:

```bash
git --version
```

Git is strongly recommended because we will modify code during the exercises and may want to inspect or revert changes.

If Git is unavailable, downloading the repository as a ZIP file is sufficient for the core exercises.

## 7. C++ tools — optional

Some workshop material demonstrates AI-assisted development of larger C++ scientific applications.

You do **not** need a working C++ development environment for the core hands-on exercises.

If you would like to experiment with the C++ examples yourself, having the following available is useful:

* a modern C++ compiler
