# Production Notes

This project is currently notebook-first, but the workflow can be moved toward production.

## What Is Already Strong

- Clear classification objective
- Multiple model comparisons
- Preprocessing pipeline usage
- Feature extraction mindset
- Strong portfolio framing

## What Should Be Improved Before Production

### 1. Validation Discipline

Use one consistent validation strategy across every model.

Recommended:

- fixed train/validation split
- stratified split
- cross-validation for final comparison
- untouched final test/inference path

### 2. Artifact Saving

Save:

- preprocessing pipeline
- trained model
- feature list
- experiment metadata

### 3. Modularization

Future production-style structure:

```text
src/
├── config.py
├── data.py
├── features.py
├── train.py
├── evaluate.py
└── predict.py
```

This was intentionally not added as executable code because the notebook code is preserved.

### 4. Explainability

Add:

- permutation importance
- SHAP summary
- feature importance comparison

### 5. Data Quality Checks

Add checks for:

- missing required columns
- unexpected categories
- invalid numerical ranges
- train/test schema mismatch

## Portfolio Message

This project is strong because it shows the transition from notebook experimentation to ML engineering thinking.
