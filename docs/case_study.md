# Spaceship Titanic: End-to-End Tabular Classification Pipeline Design

## Project overview

This project uses Kaggle's **Spaceship Titanic** competition as a portfolio case study for building a clean end-to-end tabular classification pipeline.

The task is to predict whether passengers were transported to an alternate dimension using passenger profile, cabin, travel, and onboard spending information.

The goal of this repository is not just to submit another Kaggle notebook. The goal is to demonstrate practical machine learning engineering habits:

- problem framing,
- exploratory data analysis,
- feature engineering,
- preprocessing pipeline design,
- model comparison,
- validation,
- final submission generation.

## Why this project

The original Titanic competition is a strong first classification project. Spaceship Titanic is a better second classification project because it gives more room to show pipeline thinking.

This project demonstrates:

- better preprocessing structure,
- feature extraction from compound columns,
- feature-store style thinking,
- reusable transformations,
- model comparison across multiple algorithms,
- a cleaner workflow from raw data to submission file.

## Problem statement

Given passenger information from the Spaceship Titanic dataset, predict whether each passenger was transported.

### Target

`Transported` — binary label indicating whether the passenger was transported.

### Main feature groups

- Passenger identity: `PassengerId`, `Name`
- Travel information: `HomePlanet`, `Destination`, `Cabin`
- Passenger status: `CryoSleep`, `VIP`, `Age`
- Spending behavior: `RoomService`, `FoodCourt`, `ShoppingMall`, `Spa`, `VRDeck`

## Workflow

```text
Raw data
   ↓
EDA and missing-value analysis
   ↓
Feature engineering
   ↓
Numerical/categorical preprocessing
   ↓
Model training and validation
   ↓
Model comparison
   ↓
Final submission generation
```

## Feature engineering

Important engineered features include:

- `Deck`, `CabinNum`, `Side` from `Cabin`
- `GroupId`, `GroupPos` from `PassengerId`
- `GroupSize` from passenger groups
- `is_solo` from group size
- `total_spending` from spending columns
- `has_spending` from spending behavior

These features turn raw strings and individual spending columns into more useful predictive signals.

## Preprocessing design

The notebook separates features into three groups.

### Numerical features

Numerical columns are imputed with the median and scaled.

### Low-cardinality categorical features

Categorical columns with a small number of unique values are imputed and one-hot encoded.

### High-cardinality categorical features

Columns like `PassengerId`, `Cabin`, `Name`, and `GroupId` are not directly one-hot encoded because they create too many sparse features. Instead, useful information is extracted from them first.

## Models tested

The notebook compares several models:

- Random Forest
- XGBoost
- LightGBM with Optuna tuning
- CatBoost

In the notebook's validation setup, CatBoost achieved the strongest result and was selected for final submission generation.

## Reported result snapshot

| Model | Validation result |
|---|---:|
| CatBoost | 0.8719 |
| LightGBM with Optuna | 0.7885 |

## Key learning

The biggest lesson from this project is that strong tabular ML performance often comes from clean data logic, consistent preprocessing, and reusable feature engineering — not only from trying bigger models.

## What I would improve next

- Move feature engineering into reusable Python functions or custom transformers.
- Save the trained model and preprocessor with `joblib`.
- Add a `src/` structure for training, preprocessing, evaluation, and inference.
- Add experiment tracking with MLflow or a simple experiment log.
- Add SHAP or feature importance analysis.
- Add unit tests for feature engineering logic.

## Portfolio positioning

Recommended portfolio title:

**Spaceship Titanic: End-to-End Tabular Classification Pipeline Design**

This positions the project as a machine learning engineering case study instead of just another Kaggle notebook.
