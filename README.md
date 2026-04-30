# ECG-Image-Classification
Extended materials for Myocardial Infarction detection from ECG images using multimodal LLMs.

**Dataset**
ECG Image Dataset

**Source:
**Kaggle ECG Dataset
https://www.kaggle.com/datasets/evilspirit05/ecg-analysis/data

**Reference**: Adhikari, J., Jiang, K., & Bernard, G. R. (2026).
Same Models, Better Results: Improving Multimodal LLMs’ Accuracy in Identifying Myocardial Infarction from ECG Images.
Accepted at the International Conference on Artificial Intelligence in Medicine (AIME 2026), Ottawa, Canada.

# Dataset Description

## Overview
This study utilizes a publicly available dataset of 12-lead ECG images to evaluate multimodal large language models (MLLMs) for myocardial infarction (MI) classification.

---

## Original Classes
The dataset consists of four diagnostic categories:

- **MI**: Myocardial Infarction  
- **PMI**: Prior Myocardial Infarction  
- **HB**: Abnormal Heartbeat  
- **N**: Normal ECG  

---

## Dataset Composition

| Subset | MI | PMI | HB | Normal | Total |
|:------|---:|----:|---:|-------:|------:|
| Train | 956 | 516 | 699 | 852 | 3023 |
| Test  | 239 | 172 | 233 | 284 | 928  |
| **Total** | 1195 | 688 | 932 | 1136 | 3948 |

---

## Binary Classification Setup
To align with prior work, the task was reformulated into a binary classification problem:

- **MI**
- **Non-MI** (PMI + HB + Normal)

| Subset   | MI | Non-MI (PMI, N, HB) | Total |
|:---------|---:|--------------------:|------:|
| Test     | 239 | 689 | 928 |
| Examples | 15  | 15 (5 + 5 + 5) | 30 |

---

## Few-Shot Example Selection
For the few-shot prompting setup:

- Total examples: **30 ECG images**
- **15 MI samples**
- **15 Non-MI samples**, composed of:
  - 5 PMI  
  - 5 HB  
  - 5 Normal  

These annotated examples were included in the prompt to guide model predictions.

---

## Data Usage
- The training set was **not used for model training**  
- A small subset of training images was used only for **few-shot prompting**  
- The test set was used exclusively for **evaluation**

---

## Data Source
The dataset is publicly available on Kaggle:  
https://www.kaggle.com/datasets/evilspirit05/ecg-analysis/data

---

## Notes
- All ECG images are anonymized  
- The dataset consists of **12-lead ECG recordings**  
- ECG images represent electrical activity of the heart rather than anatomical structures  

