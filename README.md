# ⚽ Football Prediction & Betting Analytics System

An automated football analytics pipeline that turns historical match and market data into probability estimates, backtests, and daily model-based betting signals across 34 leagues.

> **Portfolio note:** The production implementation and operational data are private. This repository documents the system’s architecture, methodology, and development process without exposing proprietary source code, credentials, or live betting signals.

## Overview

The project combines data collection, quality controls, statistical modelling, market comparison, and performance evaluation in one repeatable workflow. It is designed to support disciplined, evidence-led decision-making rather than intuition-led betting.

The current release is the third major model iteration. It broadens the evaluation framework to 34 leagues and supports league-aware parameter optimisation, out-of-sample testing, and automated daily prediction generation.

## What the system does

- Collects and standardises historical football results, fixture, and odds data.
- Cleans data and validates inputs before modelling.
- Builds team, league, form, table-position, and corner-related features.
- Estimates expected goals and match probabilities using a Negative Binomial modelling framework.
- Produces probabilities for relevant match and goals markets.
- Compares model probabilities with available market odds to identify qualifying value signals.
- Applies configurable staking constraints, including fractional Kelly sizing.
- Backtests historical performance and evaluates calibration, error, and closing-line movement.
- Refreshes the data and generates updated daily predictions through automated R and Python scripts.

## System architecture

```text
Data sources
    ↓
Data collection
    ↓
Cleaning & validation
    ↓
Feature engineering
    ↓
Model training & optimisation
    ↓
Probability estimation
    ↓
Market comparison & staking rules
    ↓
Backtesting & evaluation
    ↓
Daily predictions
```

## Modelling approach

The core model uses a Negative Binomial distribution to account for the dispersion commonly observed in football scores. Expected home and away goals are derived from league context and team-strength estimates, then converted into match and totals probabilities.

Key inputs and controls include:

| Area | Examples |
| --- | --- |
| Goal environment | League-average scoring and expected home/away goals |
| Team strength | Attacking and defensive ratings for each team |
| Recency | Exponential time decay using a configurable half-life |
| Match context | Points per game, recent five-match form, and corner-generation difference |
| Market calibration | Favourite/underdog adjustments, totals bias, and Platt scaling where applicable |
| Selection rules | Minimum and maximum value thresholds |
| Bankroll management | Minimum/maximum stake bounds and fractional Kelly sizing |

League-specific parameter optimisation recognises that scoring distributions and market behaviour differ across competitions. The 34 leagues are also grouped into high-, mid-, and low-scoring environments for analysis and model configuration.

## Evaluation framework

Performance is assessed with a focus on generalisation and probability quality, not headline return alone:

- **Out-of-sample testing** to separate model selection from performance evaluation.
- **Brier Score** to measure probabilistic accuracy.
- **Historical backtesting** across markets, leagues, and time periods.
- **Value buckets** to inspect how results vary by estimated edge.
- **Calibration analysis** to compare predicted probabilities with observed outcomes.
- **Closing-line comparison** to assess whether selections move in the expected market direction.

## Tech stack

- **R:** modelling, feature engineering, backtesting, and orchestration.
- **Python:** odds collection, closing-line retrieval, and supporting automation.
- **tidyverse** and **pandas:** data transformation and analysis.
- **Git / GitHub:** version control and workflow automation.

## Development

The system has progressed through three major iterations:

1. **Foundation:** historical data pipeline, initial team-strength model, and baseline backtests.
2. **Refinement:** expanded feature set, market comparison, calibration work, and improved automation.
3. **Current version:** 34-league evaluation, league-specific optimisation, out-of-sample testing, closing-line analysis, and daily prediction generation.

## What I built

I designed and developed the end-to-end workflow, including:

- Data architecture and automated ingestion.
- Statistical modelling and probability estimation.
- Feature engineering and parameter optimisation.
- Historical backtesting and performance evaluation.
- Automated R/Python operational pipeline.
- Daily prediction and staking-signal generation.

## Responsible use

This project is an analytical and research tool. Model outputs are probabilistic estimates, not guarantees or financial advice. Historical performance does not ensure future results; always use sensible limits and comply with applicable laws and bookmaker terms.

## Source code

The production source code is maintained privately. This public repository serves as technical documentation and a portfolio demonstration of the system’s architecture, development process, and evaluation methodology.
