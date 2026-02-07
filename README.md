# RISC-V Architectural Certification (ACT4)

Initial setup and exploration.
# RISC-V Architectural Certification (ACT4) – Setup & Learning

## Background
This repository documents my initial hands-on exploration of the RISC-V Architectural Certification Tests (ACT4).  
As a beginner to RISC-V and an aspiring Design Verification (DV) engineer, the goal was to understand how architectural certification is structured, how cores are described to the framework, and what is required before running certification tests.

---

## Step 1: Environment Verification

### What I Did
I verified that my Ubuntu Linux system had the basic tools required to work with the ACT framework:
- Git
- Python 3
- GNU Make

### Why I Did It
ACT4 relies on Git for source management, Python for orchestration, and Make for build automation. Verifying these tools ensures the system is ready before proceeding further.

### Evidence
Screenshots show tool versions checked using:
- `git --version`
- `python3 --version`
- `make --version`

---

## Step 2: Cloning the Certification Repository

### What I Did
I cloned the official `riscv-arch-test` repository and inspected available branches.

### What Broke
The documentation referenced a branch name that did not exist locally.

### How I Fixed It
I listed all remote branches using `git branch -a` and identified `act4` as the correct branch for architectural certification. I then checked out the `act4` branch.

### Why This Matters
Certification work must be done on the correct branch, as ACT4 introduces a new framework compared to older versions.

---

## Step 3: Understanding Core Configuration (UDB)

### What I Did
I explored the directory:

and inspected the following files:
- `cvw-rv32imc.yaml` – architecture and ISA extensions
- `model_test.h` – trickbox macros
- `link.ld` – linker script defining memory layout
- test configuration files

### Why I Did It
ACT tests are not generic binaries; they must be adapted to each core.  
The Unified Database (UDB) file describes what the core supports so the framework can select appropriate tests.

### Key Learning
I learned how a RISC-V core’s capabilities (XLEN, extensions, CSRs) are formally described for certification.

---

## Step 4: Tooling Friction and Dependency Resolution

### What Broke
While exploring the build flow:
- `make help` was not a valid target
- A warning indicated that the `uv` Python dependency manager was missing

### How I Fixed It
I installed `uv`, added it to the PATH, and verified its installation.

### Key Insight
ACT4 is **Python-driven**, not Makefile-driven.  
The Makefile is used internally, while Python scripts control test generation and execution.

---

## Step 5: Identifying the Correct Execution Interface

### What I Did
I examined the available Python entry points and invoked:

### Why I Did It
This confirmed how certification ELF files are intended to be executed and clarified the expected workflow of the ACT framework.

---

## What Is Ready Now
- All essential tools are installed
- ACT4 framework is checked out correctly
- Core configuration files are understood
- The correct execution interface has been identified

The environment is now ready to begin **core-specific architectural certification testing**.

---

## What Remains / Next Steps
- Integrate a runnable RISC-V core model
- Execute Phase 0 ACT tests
- Compare results against the Sail reference model
- Incrementally expand test coverage

---

## Evidence
The `screenshots/` directory contains screenshots documenting:
- Tool verification
- Branch discovery and checkout
- Core configuration exploration
- Dependency installation and resolution
