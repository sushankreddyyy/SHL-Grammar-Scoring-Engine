# Results Summary

## Task

Predict a continuous grammar score (0–5) from spoken English audio.

## Training data

- 769 labeled training samples
- 216 test samples
- 91 final numeric features

## Feature groups

### Linguistic
- Word count
- Unique word count
- Type-token ratio
- Average word length
- Sentence count and sentence-length statistics
- Filler words
- Repetition
- Stopword usage
- Pronoun usage
- Punctuation counts
- Dependency/syntax statistics
- Subordinate and coordinating conjunctions
- Bigram diversity
- POS ratios

### Acoustic
- Duration
- RMS mean/std/min/max
- Zero-crossing rate
- Spectral centroid/bandwidth/rolloff
- Spectral contrast
- 13 MFCC mean/std pairs
- Chroma
- Active/silence ratios

## Cross-validation

5-fold shuffled cross-validation with `random_state=42`.

| Model / Blend | RMSE | Pearson |
|---|---:|---:|
| Random Forest | 0.733441 | 0.807596 |
| Gradient Boosting | 0.745761 | 0.798491 |
| Ridge | 0.747882 | 0.797986 |
| RF 50% + Ridge 50% | **0.714242** | **0.817797** |

## Final model

- Random Forest: 700 estimators, `min_samples_leaf=3`, `max_features=0.5`
- Ridge: `alpha=10`
- Ensemble weight: 50% RF + 50% Ridge
- Predictions clipped to the 0–5 task range

## Kaggle

Recorded public score from the first submission: **0.7326**.
