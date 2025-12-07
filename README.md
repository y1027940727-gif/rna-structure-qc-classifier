# RNA Structural-Type QC Classifier

This project builds a lightweight and interpretable machine learning model to classify RNA structural types — especially distinguishing **Protein–RNA complexes** from **solo RNA** — using structural and sequence-based features from the open-source gRNAde dataset.

The goal is to provide a **QC / pre-filtering tool** that can help screen RNA entries before running more expensive geometric deep learning or inverse design models.

---

## 🔬 Dataset

Dataset source: gRNAde (open-source)  
https://github.com/chaitjo/geometric-rna-design

File used: `data/processed_df.csv`

> The dataset is **not included** in this repository.  
> To reproduce the results, please download the original repo and copy the file into this folder.

---

## 🛠 Methods

### 1. Label Cleaning
- Normalize raw labels into:
  - Protein–RNA Complex  
  - Solo RNA  
  - unknown  
- Remove classes with fewer than 30 samples.

### 2. Feature Engineering
**Structural features**
- length, mean_rmsd, median_rmsd  
- num_structures  
- cluster_seqid0.8  
- cluster_structsim0.45  

**Sequence features**
- A/U/G/C fractions  
- GC_content, AU_content  
- Longest homopolymer run  

### 3. Modeling
- Baseline RandomForest  
- Hyperparameter tuning  
- 3-class and binary classification tasks

---

## 📊 Results

| Task | Test Accuracy |
|------|---------------|
| 3-class classification | ~0.68 |
| Binary classification (Protein–RNA vs Solo RNA) | **~0.84** |

---

## 📁 Files

- `rna_structure_classification.ipynb` – main notebook (cleaning → features → modeling)

---

## 🙏 Acknowledgements

Dataset and project inspiration from:  
https://github.com/chaitjo/geometric-rna-design
