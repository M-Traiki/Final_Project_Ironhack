# 📘 Expected Goals (xG) Modelling Project

This repository contains an end-to-end workflow for building and evaluating Expected Goals (xG) models using event-level shot data from major international tournaments.  
The project compares multiple modelling approaches and evaluates how well they predict goal-scoring probability across tournaments such as **World Cup 2018**, **Euro 2020**, and **World Cup 2022**.

---

## 📂 Project Overview

The aim of the project is to:

- Build several xG models (Logistic Regression and XGBoost)
- Engineer geometric, contextual, and categorical features for shot prediction
- Evaluate models using **AUC**, **Brier Score**, and aggregate predicted xG
- Compare model performance across tournaments
- Benchmark model predictions against **actual goals** and **StatsBomb xG**

StatsBomb xG is **not used for training** — only for evaluation and comparison.

---

## 🧠 Models Included

### Logistic Regression (LR)
- `lr_raw` — minimal geometric + contextual features  
- `lr_featured` — engineered features  
- `lr_scaled` — scaled feature representation  
- `lr_tuned` (FF + OHE) — tuned model using feature-filtered, one-hot encoded inputs  

### XGBoost (XGB)
- `xgb_raw`  
- `xgb_featured`  

Each model outputs a **probability of a shot being classified as a goal**, used as the model’s xG value.

---

## 📁 Data

Datasets used:

- `shots_featured` — core engineered-feature shot dataset  
- Splits for:
  - World Cup 2018  
  - Euro 2020  
  - World Cup 2022  

Common fields include:

- Shot coordinates (`x`, `y`)
- Shot technique
- Shot type
- Body part
- Shot characteristics
- **Target:** `goal` (binary outcome)
- **Benchmark:** `shot_statsbomb_xg` (for evaluation only)

---

## 📊 Evaluation Metrics

Models are assessed using:

- **AUC (Area Under ROC Curve)**
- **Brier Score**
- **Total predicted xG**, compared with:
  - Actual goals
  - StatsBomb xG totals

Each tournament is evaluated independently.

---

## 📐 Project Purpose

This project provides a complete modelling pipeline for:

1. Preprocessing shot event data  
2. Engineering predictive shot features  
3. Training baseline and enhanced xG models  
4. Benchmarking against established metrics  
5. Understanding the effect of feature engineering on predictive performance  

---

## 📜 License

### **Data License**

The event and shot data used in this project is sourced from **StatsBomb**.  
All rights to the data belong exclusively to **StatsBomb Services Limited**.

StatsBomb Open Data License & Terms:  
https://github.com/statsbomb/open-data

Users of this repository **must comply with StatsBomb’s data license** when redistributing, modifying, or using the data.

The models, analyses, and derived outputs included here are based on this data but do **not** transfer ownership of the underlying data.

---

## 🚀 Future Enhancements

- Calibration curves  
- Sequence/possession-level features  
- Player & team-level xG summaries  
- Interactive dashboards  
