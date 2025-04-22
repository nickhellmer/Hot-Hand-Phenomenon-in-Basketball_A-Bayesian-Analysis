# Hot Hand Phenomenon in BasketballA A Bayesian Hierarchical Analysis
 The "hot hand" phenomenon in basketball is the belief that a player is more likely to make a shot after making previous shots. This project aims to determine if this phenomenon truly exists or if it occurs only due to pure chance (e.g., law of large numbers). Shot level data from the 2015-16 NBA season was analyzed and player-specific probabilities of making a shot when "hot" (defined as making the last n shots) versus "not hot" (making less than the last \( n \) shots). The models in this project were created using PyMC, and the posterior distributions were assessed to understand the credibility of the hot-hand effect.

## Objective

To determine whether the hot hand is a real statistical effect or merely a perceived one — and whether it varies meaningfully between players.

## Dataset

- **Source**: [2015–2016 NBA Shot Logs (Kaggle)](https://www.kaggle.com/code/benhamner/quick-exploration-of-the-nba-shot-logs-data/input)
- Each record includes player name, shot outcome, game context, distance, defender proximity, time remaining, and more.

## Methodology

- **Preprocessing**: Custom filtering using domain knowledge and modified Z-score outlier detection (e.g., removing layups, buzzer beaters, wide-open shots).
- **"Hot" Definition**: A shot is labeled hot if the player made their previous \( n \) shots within \( t \) seconds, in the same game and quarter.
- **Modeling**:
  - **Model 1**: A single-player Beta-Binomial model for Stephen Curry.
  - **Model 2**: Hierarchical Beta-Binomial model across all players (with \( n = 3 \), \( t = 45 \)).
  - **Model 3**: Alternative model using a relaxed hot definition (\( n = 2 \), \( t = 60 \)) for sensitivity analysis.

## Key Findings

- The hot-hand effect is not consistent across the league.
- **Some players**, such as James Harden, show moderate-to-strong posterior evidence of improved performance when “hot”.
- Others (e.g., Russell Westbrook) perform slightly worse in the hot state.
- League-wide averages are nearly identical between hot and not-hot conditions — the effect is **player-specific**, not universal.

## Tools & Technologies

- Python (Pandas, NumPy, Matplotlib, ArviZ, PyMC)
- Jupyter Notebook
- Bayesian modeling via PyMC (NUTS sampler, hierarchical priors)

## Project Structure

├── Hot_Hand_python_code.ipynb              # Main analysis notebook
├── Hot_Hand_python_code.html               # Rendered notebook for viewing
├── Hot-Hand-Shooting_A-Bayesian-Analysis   # Analysis detailed write-up (LaTeX)
└── README.md                               # You’re here!
