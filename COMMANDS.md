# Commands Used – ACT4 Setup & Exploration

This document lists the key commands used during the setup and exploration of the
RISC-V Architectural Certification Tests (ACT4). The commands are grouped by
purpose to improve clarity and reproducibility.

---

## Environment Verification

```bash
git --version
python3 --version
make --version
git clone https://github.com/riscv-non-isa/riscv-arch-test.git
cd riscv-arch-test
git branch -a
git checkout act4
ls config/cores/cvw/cvw-rv32imc
less config/cores/cvw/cvw-rv32imc/cvw-rv32imc.yaml
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.local/bin/env
uv --version
make help
python3 run_tests.py --help
