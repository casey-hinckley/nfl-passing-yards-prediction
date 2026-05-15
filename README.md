# NFL Team Passing Yards Prediction Model

## Overview
Predicts NFL team passing yards for weeks 7–11 using only data available through week 6, 
built as part of STOR 538 (Sports Analytics) at UNC Chapel Hill.

## Methodology
- **Data**: Play-by-play and schedule data from the nflverse/nflreadr R package (2018–2025)
- **Features**: Decay-weighted rolling averages (geometric decay = 0.6) frozen at week 6, 
  shrunk toward multi-year league priors using 6 ghost games to reduce early-season noise
- **Target**: Net passing yards (gross passing yards minus sack yards lost) per game
- **Models compared**:
  - Baseline (frozen net YPA × attempts)
  - Compact Elastic Net
  - Transformed Elastic Net (log/sqrt features + interactions)
  - Polynomial Elastic Net degree 2 ✅ best performer

## Results
| Model | MAE |
|-------|-----|
| Poly_EN | 88.54 |
| Ridge_Game_Tx | 88.72 |
| Ridge_Game | 89.89 |
| Baseline | 90.78 |

## Tech Stack
R, glmnet, nflreadr, dplyr, tidyr

## Files
- `nfl_passing_yards_predictions.R` — full modeling pipeline
- `NFL Passing Yards Prediction Paper.pdf` — full methodology writeup
