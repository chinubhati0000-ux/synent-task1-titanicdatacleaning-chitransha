# Titanic Data Cleaning & Preprocessing (Synent Task 1)

## Problem Statement
Raw data is often messy. The Titanic passenger dataset has missing values, columns with the wrong data types, and unclear column names. The goal of this project is to clean and prepare the data so it is ready for analysis.

## Dataset Details
- **Source:** [Kaggle: Titanic - Machine Learning from Disaster](https://www.kaggle.com/c/titanic/data) (`train.csv`)
- **Size:** 891 passengers, 12 columns
- **Columns:** passenger ID, survived, passenger class, name, sex, age, siblings/spouses aboard, parents/children aboard, ticket, fare, cabin, port of embarkation

## Approach
Tools used: Python, pandas, Jupyter/Google Colab.

1. **Handle missing values**
   - `Age` (177 missing): filled with the median age of each passenger class and sex group. The median is not affected by extreme values.
   - `Embarked` (2 missing): filled with the most common port (Southampton).
   - `Cabin` (687 missing, about 77%): dropped because too much was missing. A new column `has_cabin` (1 or 0) was kept first.
2. **Remove duplicates:** checked for repeated rows and repeated passenger IDs. None were found.
3. **Convert data types:** `age` converted to whole numbers. `survived`, `passenger_class`, `sex` and `embarked_port` converted to categories.
4. **Rename columns:** all names made lowercase and readable, for example `SibSp` became `siblings_spouses` and `Parch` became `parents_children`.
5. **Make values readable:** `0/1` became `No/Yes`, and `C/Q/S` became the port names.

## Results
| | Before | After |
|---|---|---|
| Missing values | 866 | 0 |
| Duplicate rows | 0 | 0 |
| Rows | 891 | 891 |
| Columns | 12 | 12 (`Cabin` dropped, `has_cabin` added) |

The clean dataset is ready for analysis and is saved as `titanic_clean.csv`.

## Files in this repository
- `data_cleaning.ipynb`: the full cleaning notebook with explanations
- `train.csv`: original raw dataset
- `titanic_clean.csv`: cleaned dataset
