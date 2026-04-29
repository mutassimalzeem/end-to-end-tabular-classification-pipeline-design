# Model Card

## Project

Spaceship Titanic — End-to-End Tabular Classification Pipeline Design

## Task

Binary classification.

Predict whether a passenger was transported to an alternate dimension.

## Models Explored

| Model | Role |
|---|---|
| Random Forest | Baseline tree model |
| XGBoost | Boosting benchmark |
| LightGBM | Tuned gradient boosting experiment |
| CatBoost | Strong tabular model comparison |

## Validation Results Observed in Notebook

| Experiment | Result |
|---|---:|
| Random Forest pipeline | ~0.794 validation accuracy |
| XGBoost experiment | ~0.918 accuracy on transformed split |
| CatBoost experiment | ~0.872 accuracy |

## Important Caveat

The notebook contains multiple experimental cells. Some cells use different training/evaluation setups.

For a production-quality version, all models should be compared using one consistent validation protocol.

## Intended Use

This project is intended as a portfolio case study for tabular ML pipeline design.

## Not Intended For

- Real passenger risk prediction
- Production deployment without additional validation
- Leaderboard-only comparison without understanding validation setup

## Recommended Next Step

Convert the notebook workflow into a modular training pipeline with:

- `src/features.py`
- `src/train.py`
- `src/evaluate.py`
- saved model artifacts
- reproducible experiment tracking
