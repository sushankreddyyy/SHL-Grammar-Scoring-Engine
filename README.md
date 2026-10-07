# SHL Grammar Scoring Engine

A multimodal regression solution for the **SHL Hiring Assessment 2026** (Research Intern).

The objective is to predict a continuous English grammar score from spoken audio on a **0–5** scale.

## Approach

The pipeline combines:

1. **Speech transcription:** Faster-Whisper (`small.en`)
2. **Linguistic features:** vocabulary richness, sentence statistics, repetition, stopwords, pronouns, punctuation, dependency/syntax features, bigram diversity, and POS ratios
3. **Acoustic features:** duration, RMS energy, zero-crossing rate, spectral statistics, spectral contrast, MFCCs, chroma, and activity/silence ratios
4. **Regression models:** Random Forest, Gradient Boosting, Ridge
5. **Final ensemble:** 50% Random Forest + 50% Ridge

## Validation

The completed experiment used 5-fold shuffled cross-validation.

| Model | RMSE | Pearson |
|---|---:|---:|
| Random Forest | 0.733441 | 0.807596 |
| Gradient Boosting | 0.745761 | 0.798491 |
| Ridge | 0.747882 | 0.797986 |
| **RF 50% + Ridge 50%** | **0.714242** | **0.817797** |

## Kaggle Result

The first recorded Kaggle submission achieved a **0.7326 public score**.

The challenge notes that the public leaderboard uses approximately 60% of the test set, so the final score may differ.

## Repository Structure

```text
SHL-Grammar-Scoring-Engine/
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   └── SHL_Grammar_Scoring_Engine.ipynb
└── report/
    └── results.md
```

## Running the Project

The competition dataset is private and is **not included** in this repository.

To reproduce the workflow:

1. Open the notebook in Google Colab.
2. Authenticate to Kaggle using your own credentials.
3. Download the private competition data.
4. Run the notebook from top to bottom.

The notebook writes generated artifacts and the submission file under:

```text
/content/shl_artifacts/
```

## Dependencies

See [`requirements.txt`](requirements.txt).

## Data and Privacy

The original audio and competition files are not redistributed here.
Do not commit Kaggle credentials, private competition data, audio files, or access tokens.

## Author

**Sushank Reddy**
