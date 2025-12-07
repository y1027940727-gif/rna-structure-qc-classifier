[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/y1027940727-gif/rna-structure-qc-classifier/blob/main/rna-structure-qc-classifier.ipynb)



# RNA Structural-Type QC Classifier

[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/y1027940727-gif/rna-structure-qc-classifier/blob/main/rna_structure_classification.ipynb)

![Python](https://img.shields.io/badge/Python-3.10-blue)
![ML Task](https://img.shields.io/badge/Task-RNA%20Classification-green)
![Model](https://img.shields.io/badge/Model-RandomForest-yellow)

---

## 🔬 Project Overview

This project implements a lightweight and interpretable machine-learning classifier to predict RNA structural types — especially distinguishing **Protein–RNA complexes** from **solo RNA molecules**. The main purpose is to serve as a **QC / pre-filtering tool**: before applying computationally expensive geometric deep learning or inverse design models, this classifier can screen and tag RNA entries to ensure data quality and consistency.

---

## 📁 Data Source

- Source: **gRNAde** open-source repository  
  https://github.com/chaitjo/geometric-rna-design  
- File used: `data/processed_df.csv`  
- ⚠️ Data file **not included** in this repo (due to license/data size).  
  To reproduce: clone the original gRNAde repo and copy `processed_df.csv` into this folder.

---

## 🛠 Methods

### 1. Label Cleaning  
- Raw `type_list` entries normalized into: **Protein–RNA Complex**, **Solo RNA**, **unknown**.  
- Removed classes with fewer than 30 samples to reduce noise and class imbalance.  

### 2. Feature Engineering  
- **Structural features**: length, mean_rmsd, median_rmsd, num_structures, cluster_seqid0.8, cluster_structsim0.45  
- **Sequence features**: base composition (A/U/G/C fractions), GC_content, AU_content, longest homopolymer run  

### 3. Modeling  
- Stratified train/test split  
- Baseline model: Random Forest  
- Hyper-parameter tuning (n_estimators, max_depth, etc.) with cross-validation  
- Two classification tasks:  
  - 3-class (Complex / Solo / unknown)  
  - Binary (Protein–RNA complex vs solo RNA)

---

## 📊 Results

| Task                             | Test Accuracy |
|----------------------------------|---------------|
| 3-class classification           | ~0.68         |
| Binary classification (Complex vs Solo) | **~0.84**     |

**Binary classifier performs robustly and can effectively act as a QC / pre-filtering step for downstream bioinformatics or design pipelines.**

---

## 📂 Repository Files

- `rna_structure_classification.ipynb` — Full notebook: data loading, cleaning, feature engineering, modeling, results  
- `README.md` — This documentation  

---

## 🤝 Acknowledgements

This work uses data and inspiration from the open-source **gRNAde** repository:  
https://github.com/chaitjo/geometric-rna-design  


---

## 🙏 Acknowledgements

Dataset and project inspiration from:  
https://github.com/chaitjo/geometric-rna-design
