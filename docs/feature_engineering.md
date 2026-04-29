# Feature Engineering Notes

The main feature-engineering goal is to turn raw Kaggle columns into stable modeling signals.

## Passenger-Level Features

`PassengerId` can be used to infer passenger grouping. In tabular classification tasks, group-level information can sometimes capture shared travel behavior.

## Cabin Features

`Cabin` is a semi-structured column. Instead of using it directly, it can be split into:

- deck
- cabin number
- side

This creates cleaner categorical/numerical signals for the model.

## Spending Behavior

The spending columns represent passenger activity:

- RoomService
- FoodCourt
- ShoppingMall
- Spa
- VRDeck

These can be analyzed individually or combined into total spending-style features.

## CryoSleep Logic

`CryoSleep` is especially important because passengers in cryosleep often show different spending behavior. This is a good example of domain-guided feature logic.

## Portfolio Lesson

Feature engineering should not look like random column manipulation.  
It should show a clear reason why a feature may help the model.
