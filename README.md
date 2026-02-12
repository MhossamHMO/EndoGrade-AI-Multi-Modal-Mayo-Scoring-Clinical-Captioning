# Multi-Modal Ulcerative Colitis Grading in Endoscopy

![Project Goal](https://img.shields.io/badge/Project%20Goal-Automated%20Mayo%20Grading-blue)
![Accuracy](https://img.shields.io/badge/MedSam%20Accuracy-78%25-green)
![Agreement](https://img.shields.io/badge/Kappa-87%25-brightgreen)

## 📌 Project Overview
This project addresses the challenges of manual grading in Ulcerative Colitis (UC), which is often time-consuming, subjective, and suffers from inter-observer variability. Our goal is to develop an automated **Mayo Endoscopic Score (MES)** classification system enhanced with clinical captioning to provide consistent, AI-powered diagnostic support.

**Project Team:** Mohamed Sherif, Mohamed Hossam, Ranim Hisham, Shahd Ayman, Jana El-Kordy.

---

## 📊 Dataset Overview
We utilized the **LIMUC Dataset**, a high-quality multi-centre dataset consisting of:
* **Total Images:** 11,276
* **Total Patients:** 564
* **Severity Distribution (MES Scores):**
  * Mayo 0 (Normal): 54%
  * Mayo 1 (Mild): 27%
  * Mayo 2 (Moderate): 11%
  * Mayo 3 (Severe): 8%

---

## 🛠️ Methodology & Approaches

Our solution employs a robust pipeline: **Input Image** → **Preprocessing (CLAHE & Sharpness)** → **Dual-Model Approach**.

### 1️⃣ Approach 1: MedSAM Classifier (Direct Pipeline)
This approach utilizes a dedicated medical segmentation and classification pipeline. 
* **Focus:** Binary masking and affected area metrics to determine severity.
* **Results:** * **Quadratic Weighted Kappa:** 87% (Excellent Agreement)
    * **Accuracy:** 78%
    * **Macro Recall:** 75%
* **Notebook:** `Approach_1_MedSAM_Classifier.ipynb`

### 2️⃣ Approach 2: Qwen VLM (Visual Language Model)
This approach leverages Contrastive Learning and Vision-Language Models to provide not just a score, but clinical context.
* **Focus:** Generating descriptive clinical captions alongside classification.
* **Components:** * Captions generated via **Qwen VLM**.
    * Segmentation metrics provided by **MedSAM**.
* **Notebook:** `Approach_2_Qwen_VLM_Captioning_and_Classification.ipynb`

---

## 🧬 Pipeline Architecture
1. **Preprocessing:** Applied **CLAHE** (Contrast Limited Adaptive Histogram Equalization) and **Gamma Correction** to improve image visibility and contrast (Average brightness increased from 39.9 to 42.2).
2. **Segmentation:** MedSAM identifies the affected mucosal area (e.g., Identifying healthy branching vascularity vs. ulcerations).
3. **Classification:** Models predict the class (Mayo 0-3).
4. **Clinical Summary:** The VLM generates a professional summary (e.g., *"The mucosal color appears uniform... vascular pattern is intact..."*).

---

## 📂 Repository Structure
* `Approach_1_MedSAM_Classifier.ipynb`: Implementation of the direct MedSAM classification pipeline.
* `Approach_2_Qwen_VLM_Captioning.ipynb`: Implementation of the VLM approach with contrastive learning and caption generation.
* `data/`: https://doi.org/10.5281/zenodo.5827695.

---

## 📈 Evaluation Results
The model demonstrates high reliability, particularly in identifying Mayo 0 (Normal) cases with 84.9% accuracy.

| Metric | Score |
| :--- | :--- |
| Accuracy | 78% |
| Weighted Kappa | 87% |
| Macro Recall | 75% |
| Balanced Accuracy | 74% |

---

## 🚀 Conclusion & Future Work
This project successfully integrates computer vision with clinical language processing to standardize UC grading. Future work will focus on expanding the multi-centre data variety and refining the VLM's clinical reasoning for rare lesions.

---
*Developed as part of Deep Learning research for medical diagnostic automation.*
