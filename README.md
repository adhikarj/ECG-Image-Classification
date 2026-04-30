# ECG-Image-Classification
Extended materials for Myocardial Infarction detection from ECG images using multimodal LLMs.

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

---

###  Zero-Shot Prompt

- **System Instruction:**
  - You are an expert cardiologist specializing in ECG interpretation.

- **Task:**
  - Classify the ECG image into exactly one of the following categories:

- **MI (Myocardial Infarction):**
  - ST elevation in leads II, III, and aVF (inferior MI) with possible reciprocal ST depression
  - ST elevation in V1–V6, I, and aVL (anterior MI) with reciprocal depression
  - Mirror-image changes in V1–V3 showing tall R waves and upright T waves (posterior MI)
  - ST changes in the same direction as the QRS complex in the presence of LBBB, or ST elevation > 5 mm in V1–V3, or Q waves in consecutive lateral leads (Sgarbossa criteria)

- **Non-MI (Non-Myocardial Infarction):**
  - Old inferior MI pattern without acute injury:
    - Q wave in lead III > 1 mm (1 small square)
    - Q wave in aVF > 0.5 mm
    - Q wave of any size in lead II
    - No ST-segment elevation
  - Normal sinus rhythm or any arrhythmia without acute ischemic changes

- **Output:**
  - Respond only with one label:
    - MI
    - Non-MI

- **Rules:**
  - Do not explain your reasoning or provide probabilities
  - Choose the closest match even if uncertain
  - Use the uploaded ECG image for interpretation

---

###  Few-Shot Prompt

- **System Instruction:**
  - You are an expert cardiologist specializing in ECG interpretation.

- **Few-Shot Context:**
  - [Use the cached ECG images as reference examples.]

- **Task:**
  - Classify the ECG image into exactly one of the following categories:

- **MI (Myocardial Infarction):**
  - ST elevation in leads II, III, and aVF (inferior MI) with possible reciprocal ST depression
  - ST elevation in V1–V6, I, and aVL (anterior MI) with reciprocal depression
  - Mirror-image changes in V1–V3 showing tall R waves and upright T waves (posterior MI)
  - ST changes in the same direction as the QRS complex in the presence of LBBB, or ST elevation > 5 mm in V1–V3, or Q waves in consecutive lateral leads (Sgarbossa criteria)

- **Non-MI (Non-Myocardial Infarction):**
  - Old inferior MI pattern without acute injury:
    - Q wave in lead III > 1 mm (1 small square)
    - Q wave in aVF > 0.5 mm
    - Q wave of any size in lead II
    - No ST-segment elevation
  - Normal sinus rhythm or any arrhythmia without acute ischemic changes

- **Output:**
  - Respond only with one label:
    - MI
    - Non-MI

- **Rules:**
  - Do not explain your reasoning or provide probabilities
  - Choose the closest match even if uncertain
  - Use the uploaded ECG image and reference examples for interpretation



## Summary Results

| Model | Scenario | Accuracy | F1 | Sensitivity | Specificity |
|------|----------|---------:|---:|------------:|------------:|
| Gemini 2.5 Pro | 0-shot | 72.63 | 66.23 | 56.49 | 78.23 |
| Gemini 2.5 Pro | 30-shot | 76.08 | 66.07 | 42.26 | 87.81 |
| GPT-4o | 0-shot | 68.86 | 63.73 | 60.67 | 71.70 |
| GPT-4o | 30-shot | 81.57 | 76.97 | 71.55 | 85.05 |


## Confusion Matrices

**Zero-Shot**:

Gemini 2.5 Pro:

<img width="486" height="406" alt="image" src="https://github.com/user-attachments/assets/7b198e4d-087b-465c-83f7-5ced807e85e3" />

GPT 4o:
<img width="492" height="405" alt="image" src="https://github.com/user-attachments/assets/8accb77d-a892-4b38-8c51-79688273ad85" />

---
**Few-Shot**:

Gemini 2.5 pro: 

<img width="492" height="408" alt="image" src="https://github.com/user-attachments/assets/6a622c19-e6c7-4c2b-b784-baf88bad57d0" />

GPT-4o:

<img width="493" height="408" alt="image" src="https://github.com/user-attachments/assets/4afcfffd-6ba8-47ea-8a85-3bf8227c9ffe" />

---
