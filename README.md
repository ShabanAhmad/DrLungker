# DrLungker
DrLungker combines ResNet, FNN, and RNN-LSTM with ensemble methods (Averaging, Voting, Stacking), trained on 5,886 lung cancer bioassay descriptors from PubChem and ChEMBL. It predicts compound activity (active/inactive), and scores active ones from 1 to 10.

# DeepEntXAI

**DeepEntXAI: A CNN-LSTM + Explainable AI Framework for Predicting Drug Activity Against Enterobacteriaceae**

DeepEntXAI is a hybrid deep learning framework developed to predict the biological activity of chemical compounds against **Enterobacteriaceae** pathogens (e.g., *E. coli*, *K. pneumoniae*, *S. enterica*) using molecular descriptors. The framework combines a **CNN-LSTM** architecture with **explainable AI (XAI)** techniques to achieve state-of-the-art prediction accuracy while ensuring model interpretability. It supports both labelled and unlabelled compound predictions and includes tools for compound prioritisation and descriptor relevance evaluation.

---

## 📌 Key Features

* **Hybrid Deep Learning Model**: Combines CNN and LSTM to capture both local and long-range dependencies in molecular descriptor sequences.
* **High Accuracy**: Achieved 99.80% accuracy, 99.63% precision, and 99.94% recall on test data.
* **Generalisation**: Demonstrated strong generalisation through 5-fold and 10-fold cross-validation with average accuracies of 99.09% ± 0.36% and 99.13% ± 0.27%, respectively.
* **Explainability**: Integrates both:

  * A **hybrid perturbation-based XAI** method (accuracy drop, flip ratio, log-loss increase)
  * **LIME** for local interpretability and compound-specific insights.
* **Prediction on Unlabelled Data**: Scores new compounds (0–10 scale) to identify high-potential drug candidates.
* **Output-Ready Results**: Generates CSV files with prediction probabilities, scaled activity scores, and interpretability rankings.

---

## 📂 Repository Structure

```
DeepEntXAI/
├── data/                        # Sample_Dataset.csv, SampleInput molecular descriptors (CSV format)
├── models/                      # 1_CNN_LSTM_XAI.pth, Trained models and saved weights
├── notebooks/                   # Enterobacteriaceae_Code.ipynb, Code with outputs (CNN-LSTM-XAI)
├── README.md                    # README.md, Project documentation
└── LICENSE                      # LICENSE.md, License file
```

---

## 📊 Dataset

* **Source**: PubChem and ChEMBL BioAssays relevant to Enterobacteriaceae.
* **Size**: 17,097 compounds with 2,997 descriptors each (selected 2000 with PCA).
* **Descriptors**: Computed using **RDKit**, **Mordred**, and **PaDEL**.
* **Preprocessing**:

  * Structure standardisation
  * Duplicate removal
  * Descriptor curation
  * and many more, read the full paper. 
  * Final active set: 8,097 ligands, 9000 Inactive compounds. 

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ShabanAhmad/DeepEntXAI.git 
cd DeepEntXAI
```

### 2. Set Up the Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
pip install -r requirements.txt
```

### 3. Run Training

```python
Directly use the saved weight file.
```

### 4. Predict on Unlabelled Data

```python
Pass any unlabelled data in CSV format. 
```

### 5. Run Explainability Analysis

```python
python src/explain_hybrid.py --input data/test.csv --model models/ _weights.h5
python src/explain_lime.py --input data/test.csv --model models/ _weights.h5
```

---

## 📈 Results Summary

| Metric                     | Score          |
| -------------------------- | -------------- |
| Accuracy                   | 99.80%         |
| Precision                  | 99.63%         |
| Recall (Sensitivity)       | 99.94%         |
| F1-Score                   | 99.78%         |
| Specificity                | 99.67%         |
| AUC-ROC                    | 0.998          |
| Cross-Validation (5-fold)  | 99.09% ± 0.36% |
| Cross-Validation (10-fold) | 99.13% ± 0.27% |

---

## 🧠 XAI Insights

* **Top Feature**: `minHsNH3p` – High perturbation sensitivity across accuracy, flip ratio, and log-loss.
* **Low-Importance Features**: `geomDiameter`, `nG12FRing`, `BCUTZ-1l`
* **Top Compounds (by confidence)**: `4615770`, `5309708`, `70556`, with scaled scores \~9.9999
* **Least Certain Compounds**: Predictions near 0.5 threshold, structurally ambiguous

---

## 🧪 Applications

* Active compound screening
* Compound efficacy assessment
* Drug repurposing
* Prioritisation for **Enterobacteriaceae** infections (e.g., UTIs, BSIs, sepsis)
* Feature-driven compound design

---

## 📜 License

This project is licensed under the MIT License (read full license file).

---

## 🤝 Contributions

We welcome contributions from the community. Please open issues or submit pull requests for improvements, bug fixes, or new features.

---

## 📧 Contact

For questions or collaboration inquiries, please contact:

**Author**: *\Nagmi Bano1, Dr Shaban Ahmad1,2, Prof Khalid Raza1*
**Email**: *\nagmi2300973@st.jmi.ac.in, Shaban@sund.ku.dk, kraza@jmi.ac.in*
**Institution**: *\
1 Department of Computer Science, Jamia Millia Islamia, New Delhi-110025, India.
2 Preclinical Disease Biology Section, Department of Veterinary and Animal Sciences, Faculty of Health and Medical Sciences, University of Copenhagen, Frederiksberg, Denmark.*

---
