# Data Contract

This document describes the expected shape of the raw Kaggle input data.

## Expected Raw Files

Place the files in:

```text
data/raw/train.csv
data/raw/test.csv
```

## Target Column

| Column | Meaning |
|---|---|
| `Transported` | Binary target indicating whether a passenger was transported |

## Important Input Columns

| Column | Type | Notes |
|---|---|---|
| `PassengerId` | string | Can be used to derive group-level signals |
| `HomePlanet` | categorical | Passenger origin |
| `CryoSleep` | boolean/categorical | Strong behavioral signal |
| `Cabin` | string | Can be split into deck, number, and side |
| `Destination` | categorical | Travel destination |
| `Age` | numerical | Requires imputation |
| `VIP` | boolean/categorical | Passenger status |
| `RoomService` | numerical | Spending behavior |
| `FoodCourt` | numerical | Spending behavior |
| `ShoppingMall` | numerical | Spending behavior |
| `Spa` | numerical | Spending behavior |
| `VRDeck` | numerical | Spending behavior |
| `Name` | string | Can support family/group signals |

## Contract Assumptions

- The training set contains `Transported`.
- The test set does not contain `Transported`.
- Missing values are expected.
- `Cabin` may need parsing before modeling.
- Numerical spending columns should be treated consistently.
- Categorical columns should be encoded through a repeatable preprocessing pipeline.
