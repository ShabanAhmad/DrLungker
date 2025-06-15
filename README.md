# DrLungker: Deep-Ensemble Learning for Predicting Compound Activity against Lung Cancer and Probing Multitarget Potency via WaterMap, DFT, MD Simulation, and MMGBSA Studies

The DrLungker model combines ResNet, Feedforward Neural Network (FNN), and RNN-LSTM architectures, and uses three ensemble techniques: Averaging, Majority Voting, and Stacking. It is trained on 5,883 molecular descriptors derived from lung cancer bioassay data obtained from PubChem and ChEMBL.
The model can predict whether a compound is active or inactive against lung cancer. If a compound is predicted to be active, the model further provides an activity score on a scale from 1 to 10, indicating the degree of activity.

---

## 📌 Key Features

* **Comprises Multiple Deep Learning Models**: Combines ResNet, FNN and LSTM to capture both local and long-range dependencies in molecular descriptor sequences of Lung Cancer BioAssays.
* **High Accuracy**: Achieved beyond 99% accuracy, precision, and recall on test data.
* **Generalisation**: Demonstrated strong generalisation through 5-fold and 10-fold cross-validation with average accuracies of 97%.
* **Prediction on Unlabelled Data**: Scores new compounds (0–10 scale) to identify high-potential drug candidates.
* **Output-Ready Results**: Generates CSV files with prediction probabilities, scaled activity scores, and interpretability rankings.
* **SDF extractor**: The code extracts the SDF file ready for structural validation, docking studies and other downstream analysis.

---

## 📂 Repository Structure

```
DeepEntXAI/
├── data/                        # Sample_Dataset.csv, SampleInput molecular descriptors (CSV format)
├── notebooks/                   # Enterobacteriaceae_Code.ipynb, Code with outputs (CNN-LSTM-XAI)
├── README.md                    # README.md, Project documentation
└── LICENSE                      # LICENSE.md, License file
```

---

## 📊 Dataset

* **Source**: PubChem and ChEMBL BioAssays relevant to Enterobacteriaceae.
* **Size**: From ChEMBL, we obtained 18,349 Active and 1,50,836 Inactive compounds; from PubChem, we obtained 17,455 Active and 2,99,607 Inactive compounds taken for the LigPrep. After LigPrep, we obtained 18172 ligands for the Active and 150109 Inactive from the ChEMBL library, whereas 16,566 Active and 2,86,269 Inactive compounds from the PubChem library. After removing the duplicates, 4,537 and 8661 unique compounds in Active libraries of ChEMBL and PubChem, respectively, the same number of compounds were taken from Inactive and merged together, making 26,396 unique compounds with the label Active (1) and Inactive (0) ready for Deep and Ensemble Learning.
* **Final Data Size for Training**: 26,396 unique compounds with 5883 descriptors each.
* **Descriptors**: Computed using **AlvaDesc** and **QikProp**.
* **Preprocessing**:

  * Structure standardisation
  * Duplicate removal
  * Descriptor curation
  * and many more, read the full paper. 

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ShabanAhmad/DrLungker.git 
cd DrLungker
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

Available in the manuscript. 
---

---

## 🧪 Applications

* Active compound screening
* Compound efficacy assessment
* Drug repurposing
* Prioritisation for **Lung Cancer**
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

**Author**: *\Dr Shaban Ahmad1,2, Prof Khalid Raza1*

**Email**: *\Shaban@sund.ku.dk, kraza@jmi.ac.in*

**Institutions**: *\
1 Department of Computer Science, Jamia Millia Islamia, New Delhi-110025, India.

2 Biomedicine Section, Department of Veterinary and Animal Sciences, Faculty of Health and Medical Sciences, University of Copenhagen, Frederiksberg, Denmark.*

---
