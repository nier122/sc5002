# sc5002
# SC5002 Lab Assignment – Search Algorithms & Regularised Regression

**Course:** SC5002 Artificial Intelligence Fundamentals & Applications (NTU)
**Group members:** [Name 1], [Name 2], [Name 3]

## Overview
This repository contains our work for the SC5002 lab assignment:
- **Part 1 – Classical Search:** BFS and A* search on a weighted directed graph, and A* on the 8-puzzle (hand calculations are in the report).
- **Part 2 – Applied Machine Learning:** Linear Regression vs. Ridge Regression on the California Housing dataset, evaluated with 5-fold cross-validation.

## Files
| File | Description |
|---|---|
| `SC5002_Lab.ipynb` | Completed Google Colab notebook for Part 2 |
| `README.md` | This file |

## How to Run
1. Open `SC5002_Lab.ipynb` in Google Colab (File → Upload notebook).
2. Click **Runtime → Run all**.
3. No downloads are needed: the dataset loads automatically with `fetch_california_housing()` from scikit-learn.

**Libraries:** numpy, pandas, matplotlib, scikit-learn (all pre-installed in Colab).

## Dataset
California Housing dataset (scikit-learn). 1,000 rows were sampled with `random_state=42`.
- **Target:** `MedHouseVal` (median house value, in $100,000s)
- **Features (8):** MedInc, HouseAge, AveRooms, AveBedrms, Population, AveOccup, Latitude, Longitude
- Features were standardised with `StandardScaler`, and an 80/20 train/test split was used.

## Results
| Model | Alpha | Mean 5-Fold CV R² |
|---|---|---|
| Linear Regression | – | 0.6457 |
| Ridge Regression | 0.1 | 0.6457 |
| Ridge Regression | 10.0 | 0.6443 |
| Ridge Regression | 1000.0 | 0.3574 |

## Key Findings
- Linear Regression and Ridge (alpha 0.1–10) performed almost identically. With 800 training rows and only 8 features, the model was not overfitting, so regularisation had little to fix.
- At alpha = 1000, R² dropped sharply to 0.357. The penalty shrinks the weights so much that the model **underfits**.
- 5-fold cross-validation gives a more reliable score than a single train/test split because it averages performance over five different test folds.

## Use of Generative AI
We used Claude as a learning partner to explain concepts (admissible heuristics, feature scaling, regularisation), to check our hand calculations, and to debug code. Bugs fixed:
1. **SyntaxError:** the f-string in the Ridge `print()` statement was split across two lines. We joined it into one line.
2. **Missing bar labels:** `plt.show()` was indented inside the `for` loop, so only the first bar was labelled. We moved it outside the loop.

Full AI prompt logs are included in our PDF report.

