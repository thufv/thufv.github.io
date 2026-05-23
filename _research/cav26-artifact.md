---
layout: default
title: Deadlock Verification via Ordering-Constrained Mutex Modeling
permalink: /research/cav26
---

## <center>Deadlock Verification via Ordering-Constrained Mutex Modeling</center>

#### <center>Pei Wang, Zhilei Han, Zhihang Sun and <a href="https://feihe.github.io/">Fei He</a></center>

## <center>Abstract</center>

Mutexes are fundamental synchronization primitives in concurrent programming, but their improper use can lead to deadlocks. Conventional assume-based modeling abstracts mutex semantics via assumptions, simplifying safety verification but hindering deadlock verification. Although prior efforts have aimed to address this limitation, we show that state-of-the-art methods remain inaccurate. In this paper, we propose a novel modeling approach that captures mutex semantics using ordering constraints, enabling accurate deadlock verification within partial-order-based concurrent verification frameworks. We formally prove the correctness of our method and implement it in a prototype tool, DEAGLE-DL. We evaluate DEAGLE-DL against a state-of-the-art bounded model checker ESBMC that employs the conventional modeling approach, and a state-of-the-art static analysis tool for deadlock detection. Our experiments show that DEAGLE-DL significantly outperforms both tools in terms of precision, while maintaining substantial efficiency.

## <center>Artifact</center>

The artifact for DEAGLE-DL is available <a href="https://doi.org/10.5281/zenodo.19696864">here</a>. It contains the complete source code of DEAGLE-DL, a prebuilt Docker image for direct execution, benchmark suites (classical benchmarks and SV-COMP benchmarks), and all scripts needed to reproduce the experimental results reported in the paper.

### Artifact Structure

The artifact is distributed as a compressed archive with the following top-level layout:

* **`DEAGLE-DL-src/`** — The complete source code of DEAGLE-DL (outside Docker, can be built on the host system).
* **`image.tar.gz`** — Prebuilt Docker image for direct execution.
* **`Readme.md`** — Overview and reproduction instructions.
* **`LICENSE`** — License file.

#### Docker Image Contents

The source code is not included in the Docker image. Inside the container, the precompiled binaries, benchmarks, scripts, and the Dockerfile are available under `/workspace` with the following layout:

* **`Dockerfile`** — The Dockerfile used to rebuild the Docker image.
* **`tools/`**
  * **`DEAGLE-DL/`** — Contains the precompiled binary of DEAGLE-DL (`deagle-dl-bin/`).
  * **`ESBMC/`** — Contains the official precompiled binary of the baseline bounded model checker ESBMC.
  * **`STATIC-ANALYZER/`** — Contains the official precompiled binary of the baseline static analyzer.
* **`benchmarks/`**
  * **`classical-benchmarks/`** — Benchmarks used in the first experiment (Table 1).
  * **`sv-benchmarks/`** — Benchmarks drawn from SV-COMP, used in the second experiment (Tables 2 & 3).
* **`scripts/`**
  * `run_smoke.sh` — Quick smoke-test script.
  * `run_all.sh` — One-command script to run all experiments and generate all three tables.
  * **`scripts_on_cl/`** — Scripts to run tools on classical benchmarks and generate Table 1.
  * **`scripts_on_sv/`** — Scripts to run tools on SV-COMP benchmarks and generate Tables 2 & 3.
* **`outputs/`**
  * `table1.csv`, `table2.csv`, `table3.csv` — Generated tables corresponding to those in the paper.
  * **`outputs_on_cl/`** — Raw results and statistics on classical benchmarks.
  * **`outputs_on_sv/`** — Raw results and statistics on SV-COMP benchmarks.

### Building from Source (Outside Docker)

The DEAGLE-DL source code can be built from the `DEAGLE-DL-src/` directory:

```bash
cd src && make
```

**Dependencies:** g++, flex, bison (≥ 3.5.2 recommended), gcc-multilib.

The build produces the executable binary `deagle_exe` in `src/cbmc/`.

### Usage

```
deagle_exe <input file> <unwind options> <specifications>
```

**Unwind options:**
- `--unwind n` — Unwind all loops for `n` times.
- `--unwindset loop_id0:n0,loop_id1:n1,...` — Set unwind limits per loop individually.
- If unwind options are omitted, DEAGLE-DL iteratively unwinds each loop until fully unwound.

**Specifications (selected):**
- `--no-assertions`: disable user-defined assertion.
- `--unwinding-assertions`: add assertions at each loop to check whether the loop has been fully unwound.
- `--no-self-loops-to-assumptions`: do not directly replace self-loops with assume statements.
- `--deadlock`: Enable deadlock detection. Should be used together with `--unwinding-assertions` and `--no-self-loops-to-assumptions` to ensure the unwinding requirement for loops inside critical sections is correctly enforced.

### Experimental Environment

All experiments in the paper were conducted on a server with two AMD EPYC 7H12 64-core processors and 1 TiB RAM, running Ubuntu 20.04.6 LTS (x86_64).

### Smoke Test

```bash
docker load < image.tar.gz
docker run -it deagle-dl-env
cd /workspace/scripts/
bash run_smoke.sh       # ~2 minutes
```

DEAGLE-DL should report `FAILED` on 15 deadlocking tasks and `SUCCESSFUL` on 15 deadlock-free tasks. The smoke test succeeds if the script outputs `Smoke test succeeded.`

### Full Reproduction

#### One-Command Execution

```bash
cd /workspace/scripts/
bash run_all.sh         # ~87 hours
```

This sequentially runs all tools on both benchmark suites and generates `outputs/table1.csv`, `outputs/table2.csv`, and `outputs/table3.csv`.

#### Step-by-Step

**1. Classical benchmarks (Table 1):**

```bash
cd /workspace/scripts/scripts_on_cl
python3 run_DEAGLE_on_cl.py            # ~2 min
python3 run_ESBMC_on_cl.py             # ~8 hours
sh run_STATIC-ANALYZER_on_cl.sh
python3 get_table1.py
```

**2. SV-COMP benchmarks (Tables 2 & 3):**

```bash
cd /workspace/scripts/scripts_on_sv
python3 run_DEAGLE_on_sv.py           # ~31 hours
python3 run_ESBMC_on_sv.py            # ~48 hours
sh run_STATIC-ANALYZER_on_sv.sh
python3 get_table2.py
python3 get_table3.py
```

### Reproduced Results

The CSV files in `outputs/outputs_on_cl` and `outputs/outputs_on_sv` contain both the raw experimental results and derived statistics. The files `outputs/table1.csv`, `outputs/table2.csv`, and `outputs/table3.csv` correspond directly to Table 1, Table 2, and Table 3 in the paper, respectively.

### License

The DEAGLE-DL artifact is distributed under the GNU General Public License, version 3 or, at the user's option, any later version. See the `LICENSE` file in the artifact root for the full license text.
