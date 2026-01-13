# The more, the merrier?! 🧠📡

> **Evaluating the impact of SMOTE and CTGAN data augmentation on hardware failure classification in Microwave Networks**

![Status](https://img.shields.io/badge/Status-Completed-success)
![Type](https://img.shields.io/badge/Type-Individual_Project-blue)
![Focus](https://img.shields.io/badge/Focus-Machine_Learning_|_XAI-orange)

## 📂 Repository Structure
This repository contains the full engineering workflow for Project 10 of the NMDA Lab:

* 📄 **[NMDA Lab - Project](NMDA%20Lab%20-%20Final%20Project.ipynb)**: The complete technical implementation of the project via Jupyter Notebook; it includes data cleaning, t-SNE visualization, synthetic data generation (CTGAN / SMOTE), model training and model evaluation.
*(Note that the notebook includes detailed explanations for each step and, therefore, this README just focuses on an high-level overview to avoid redundant information)*

* 📄 **[NMDA Lab - Presentation](NMDA%20Lab%20-%20Final%20Presentation.pdf)**: A visual explaination of the experimental setup, results and interpretability analysis. *(Recommended as a starting point for an high-level understanding of the project)*

* 📄 **[Projects](NMDA%20Lab%20-%20Final%20Presentation.pdf)**: The description of the all proposed projects for the A.Y. 2023–2024

## 📖 About The Project

This project addresses the challenge of predicting hardware failures in microwave networks using a dataset of **163 different alarms**. Each feature represents the duration (in seconds) an alarm was active during a 15-minute window.

The dataset is characterized by a small sample size (**1,669 instances**) and significant **class imbalance** across four failure types:

1. **Class 0: In-Door Unit (IDU) Failure**

2. **Class 1: Out-Door Unit (ODU) Failure**

3. **Class 2: Cable Failure**

4. **Class 3: Power Failure**

### Research Question
> **Does increasing dataset size through synthetic data generation genuinely improve classification performance or does it just introduce additional noise and reduce model reliability?**


## ⚡ Engineering Workflow

### 1. Data Refining & EDA
* **Preprocessing:** Identified and removed **534 duplicate rows** and **45 constant features** (alarms with zero variance) to reduce noise

* **Exploration:** Applied **t-SNE (3D)** to visualize class clusters and assess the separability of the four failure types

### 2. The Augmentation Pipeline
In order to address data scarcity and imbalance, two synthetic data generation techniques were implemented and compared:

- **SMOTE (Synthetic Minority Over-sampling Technique)**: It generates new minority-class samples via linear interpolation in the feature space

- **CTGAN (Conditional Tabular GAN)**: A generative adversarial network tailored for tabular data, designed to model complex, non-linear feature dependencies

Multiple **custom data generation strategies** were tested (Datagen 1, 2A, 2B), exploring different **real-to-synthetic ratios** to identify the optimal balance between data diversity and realism


### 3. Model Training & Evaluation
We benchmarked three different architectures:

* **Support Vector Machine (SVM)**

* **XGBoost (Extreme Gradient Boosting)**

* **Logistic Regression**

The performance was evaluated across original and augmented datasets to quantify the true impact of synthetic data.

### 4. Explainable AI (XAI)
In order to verify that models learned **physically meaningful network patterns** rather than artifacts introduced by augmentation, explainability techniques were applied:

* **SHAP (SHapley Additive exPlanations):** Global feature importance and individual "Waterfall" plots to see which alarms triggered a specific failure prediction

* **LIME:** Local interpretable explanations to validate the model's logic on a per-sample basis

---

<div align="center">

*This project was developed as part of the Network Measurement and Data Analysis Course (A.Y. 2023 - 2024) at Politecnico di Milano.*

</div>
