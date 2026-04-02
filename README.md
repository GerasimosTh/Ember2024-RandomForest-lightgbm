# Malware Detection using Machine Learning — EMBER2024


## Overview

Evaluating static analysis feature groups for malware detection using machine learning.

Two classifiers — **LightGBM** and **Random Forest** — are trained and evaluated on
the [EMBER2024](https://github.com/FutureComputing4AI/EMBER2024) dataset across three file types:
Win64, .NET, and APK executables.

---

## Results

| File Type | Model | Accuracy | F1-Score | ROC-AUC |
|-----------|-------|----------|----------|---------|
| Win64 | LightGBM | 98.74% | 98.74% | 0.9990 |
| Win64 | Random Forest | 98.07% | 98.06% | 0.9972 |
| .NET | LightGBM | 97.99% | 98.00% | 0.9982 |
| .NET | Random Forest | 97.25% | 97.25% | 0.9968 |
| APK | LightGBM | 94.31% | 94.17% | 0.9884 |
| APK | Random Forest | 93.16% | 92.96% | 0.9843 |

---

## Feature Groups Evaluated

Static features from EMBER2024, evaluated individually and in combinations:

- **Byte Histogram & Byte Entropy Histogram** — byte-level distribution
- **String Extractor** — behavioral string patterns
- **Header & Section Info** — PE structural features
- **Imports / Exports** — library and function calls
- **Data Directories, Rich Header, Authenticode, PE Warnings** — new EMBER2024 features
- **GeneralFileInfo** — file size, entropy, metadata

Key finding: the combination of String + Header + Section features approaches
full-feature performance at significantly lower computational cost.

---

## Tech Stack

- Python 3.10.19
- scikit-learn
- LightGBM
- NumPy, pandas
- Jupyter Notebook

---

## Dataset

[EMBER2024](https://github.com/FutureComputing4AI/EMBER2024) — ~3.2M samples (Win64, .NET, APK, Win32, ELF, PDF)
collected Sep 2023 – Dec 2024 via VirusTotal with double-verification labeling.

Download the dataset separately and update the paths in the notebooks before running.

---

## Project Structure

```
├── notebooks/
│   ├── win64_lightgbm.ipynb
│   ├── win64_random_forest.ipynb
│   ├── net_lightgbm.ipynb
│   ├── net_random_forest.ipynb
│   ├── apk_lightgbm.ipynb
│   └── apk_random_forest.ipynb
├── README.md
└── requirements.txt
```

 **Note:** These notebooks contain the final, cleaned code used to produce 
 the results reported in the thesis. Exploratory and intermediate experiments 
 conducted during development are not included.
 
---

## Author

Gerasimos Theodosiadis  
Dept. of Electrical & Computer Engineering, University of Patras

## References

If you use this work or the EMBER2024 dataset, please cite:
```
@inproceedings{joyce2025ember,
    title={EMBER2024 - A Benchmark Dataset for Holistic Evaluation of Malware Classifiers},
    author={Robert J. Joyce and Gideon Miller and Phil Roth and Richard Zak and 
            Elliott Zaresky-Williams and Hyrum Anderson and Edward Raff and James Holt},
    year={2025},
    booktitle={Proceedings of the 31st ACM SIGKDD Conference on Knowledge Discovery and Data Mining},
}
```
