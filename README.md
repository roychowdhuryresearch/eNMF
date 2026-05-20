This repository provides a clean Python implementation of several **Non-negative Matrix Factorization (NMF)** algorithms and their constrained variants (**NMFC**). It also includes scripts/notebooks for dataset preparation and experiment reproduction.

## ✨ Features

- **NMF algorithms:** `GRADMUL`, `HALS`, `MUL`, `ALS`, `AOADMM`, `ADMM`, `eNMF`
- **NMFC algorithms:** `ADM`, `SCD`, `MUL`, `eNMF` (constrained)
- **Datasets:** Verb, MovieLens, AudioMNIST, and synthetic datasets (exact factorization & noisy)
- **Config-driven experiments** with reproducible settings

---

## 📦 Installation

> Python 3.12 recommended (3.9+ supported)

```bash
# Create and activate a Python 3.12 env with Conda 
conda create -n nmf-312 python=3.12 -y
conda activate nmf-312

# dev install
pip install -U pip setuptools wheel
pip install -e .     
```
---
## 🧪 Experiments

### 1) Prepare Datasets

Create a top-level `Dataset/` folder and place files as described in `Dataset/README.md`.  


---

### 2) Run Experiments

Make sure the package is installed (editable install recommended during development):
```bash
pip install -e .            # or: pip install -e .[plot]
```

**A. Without proto-based config**

Quick demo:
```bash
python Experiments/run_experiment_demo.py
```

**B. proto-based pipeline** e.g.

Quick demo:
```bash
python Experiments/experiment_scripts_exacts.py
```

**Custom configs**  
You can add or modify configs under:
```
Experiments/configs/
```
Adjust dataset paths, algorithm names, ranks (`latent_dim`), and time/error budgets as needed.


---

## 🔕 Logging

By default, experiment scripts show progress messages through Python logging.

To reduce the output, set the logging level to `WARNING` in the experiment script:

```python
import logging

logging.basicConfig(
    level=logging.WARNING,
    format="%(asctime)s | %(levelname)s | %(message)s",
)
```
---

## 🛠️ Development

If you update your proto definitions (e.g., `src/nmf_algos/dataproto/data_config.proto`), regenerate the Python stubs.

**Recommended (uses bundled compiler via grpcio-tools):**
```bash
cd src/nmf_algos/dataproto
python -m pip install -U protobuf grpcio-tools
python -m grpc_tools.protoc -I . --python_out=. data_config.proto
```
---

## 📖 Citation

If you find this repository useful for your research, please cite our paper:

```bibtex
@article{enmf2026,
  title={An Exterior Method for Nonnegative Matrix Factorization},
  author={Qiujing Lu and Tonmoy Monsoor and Ehsan Ebrahimzadeh and Kartik Sharma and Vwani Roychowdhury},
  journal={arXiv preprint arXiv:2605.19325},
  year={2026},
  url={http://arxiv.org/abs/2605.19325}
}
```
