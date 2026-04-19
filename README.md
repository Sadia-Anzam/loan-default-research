# Interpretable Modeling of Rare Loan Default Events Using Behavioral Features from Noisy Transactional Data

> **Confidentiality note:** This repository uses synthetic data and abstracted business logic inspired by real loan transaction systems. No proprietary company data, exact production schema, or confidential internal rules are included.

## Overview

This project investigates how behavioral and temporal features derived from transactional loan data can improve the **interpretable prediction of future loan default**. It is designed as a research-oriented portfolio project at the intersection of **credit risk modeling, applied machine learning, and operational decision-making**.

The central idea is simple: in real lending environments, predictive performance alone is not enough. Risk teams also need models that are **transparent, traceable at the individual-loan level, and operationally usable**. This project therefore prioritizes both **predictive usefulness** and **interpretability**.

Rather than presenting loan default prediction as a generic machine learning task, this repository frames it as a **real-world rare-event modeling problem** shaped by noisy transactional histories, inconsistent records, repayment schedule differences, and business constraints.

---

## Research Question

**How can behavioral and temporal features derived from transactional loan data improve interpretable prediction of loan default?**

### Supporting Questions

1. Which early-stage delinquency indicators are most predictive of eventual default?
2. How does normalization of overdue duration across different repayment schedules affect model performance?
3. What is the trade-off between interpretability and predictive performance in loan default modeling?

---

## Why This Project Matters

Loan default prediction matters because it affects:

- early identification of high-risk accounts
- collection strategy and prioritization
- portfolio stability and product evaluation
- responsible lending and financial inclusion

This project is especially relevant for **microfinance and retail lending contexts**, where repayment behavior evolves over time and operational constraints often require models that are explainable, not just accurate.

---

## Project Goals

This repository aims to:

- build an interpretable loan default prediction pipeline
- reflect realistic data cleaning and preprocessing challenges
- engineer behavior-driven features from transaction history
- evaluate model performance under class imbalance
- connect modeling outputs to business interpretation

---

## Data

This repository does **not** include real company data.

Instead, it uses a **synthetic dataset** designed to preserve the structural characteristics of real loan transaction systems without exposing confidential information. The synthetic data is intended to mimic realistic lending behavior while remaining safe to share publicly.

### Synthetic data is designed to reflect:

- heterogeneous installment frequencies
- varying loan sizes
- early missed-payment behavior
- consecutive missed collections
- overdue carrying duration
- prior borrowing history
- default labels with realistic class imbalance

---

## Data Challenges

A major focus of this project is that real-world loan transaction data is messy.

The modeling pipeline is designed around challenges such as:

- incomplete or incorrect transaction entries
- transferred loans
- modified loan rules or repayment schedules
- inconsistent collection timelines
- exceptional operational cases that distort modeling
- rare-event class imbalance

These challenges are not treated as side issues. They are part of the core problem definition.

---

## Data Preparation

The data preparation process is intended to reflect the realities of large-scale transactional credit data.

Key preprocessing themes include:

- rule-based cleaning of invalid states
- reconstruction of loan timelines from daily transaction records
- exclusion or re-encoding of exceptional loan cases
- transformation of raw records into loan-level modeling features
- consistency checks across repayment schedules and collection behavior

This project treats **data preparation as a modeling contribution**, not just a preprocessing step.

---

## Behavioral Feature Engineering

A central contribution of this project is the design of **behavioral and temporal risk features** based on observed repayment patterns.

### Feature groups

#### 1. Early Delinquency Indicators
- missed collections in early lifecycle stages
- missed installments by lifecycle checkpoints
- first signs of repayment deterioration

#### 2. Payment Behavior Features
- consecutive missed payments
- repayment recovery after missed cycles
- collection achieved relative to target

#### 3. Temporal Risk Features
- maximum overdue carrying duration
- overdue duration normalized by installment frequency
- timing-based repayment irregularity measures

#### 4. Historical Exposure Features
- previous loan count
- repeat borrowing behavior
- prior exposure to lending cycles

#### 5. Financial Normalization Features
- disbursement-based normalization
- loan-size-adjusted risk signals

### Feature design philosophy

Features in this project are not based only on automatic selection. They are designed from a combination of:

- exploratory data analysis
- observed behavioral patterns
- domain reasoning
- operational interpretability

This is important because default risk is not only a statistical signal. It is also a behavioral process.

---

## Modeling Approach

The primary model used in this project is **logistic regression**.

### Why logistic regression?

Logistic regression is chosen because it supports:

- interpretability
- traceability at the individual-loan level
- easier business explanation
- operational usability in risk workflows

In practical credit-risk settings, a slightly more accurate black-box model is not always preferable if it cannot be clearly explained or audited. For that reason, this project treats model choice as a **deployment-aware decision**, not only a leaderboard decision.

### Possible benchmark models
Where useful, future iterations may compare logistic regression with:

- tree-based models
- gradient boosting methods
- hierarchical or mixed-effects approaches

However, the main objective remains **interpretable default prediction under realistic constraints**.

---

## Class Imbalance Strategy

Loan default is treated here as a **rare-event prediction problem**.

Because of class imbalance, accuracy alone is not considered an appropriate evaluation metric. The project instead focuses on methods that better reflect operational performance.

### Planned handling includes:

- class weighting
- decision-threshold tuning
- precision-recall focused evaluation
- error analysis across false positives and false negatives

---

## Evaluation

Model evaluation will focus on both predictive quality and practical usefulness.

### Planned metrics and analyses

- ROC-AUC
- PR-AUC
- precision and recall at selected thresholds
- confusion matrix
- coefficient interpretation
- segment-level performance analysis
- business-facing error interpretation

The goal is not just to say whether the model performs well, but to understand **why**, **where**, and **under what constraints** it performs well.

---

## Repository Structure

```text
loan-default-research/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── raw/
│   ├── processed/
│   └── README.md
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_feature_engineering.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_evaluation.ipynb
├── src/
│   ├── data_cleaning.py
│   ├── feature_engineering.py
│   ├── model.py
│   └── utils.py
├── reports/
│   ├── final_report.pdf
│   └── figures/
└── docs/
    ├── methodology.md
    └── assumptions.md
