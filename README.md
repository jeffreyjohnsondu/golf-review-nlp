Markdown
# Golf Course Review Sentiment & Operational Driver Analysis

## Overview
An NLP text classification model built to analyze public golf course reviews, predict review sentiment (Binary: Positive 4–5 stars vs. Negative 1–3 stars), and extract key operational drivers behind player satisfaction.

## Stakeholder & Business Problem
* **Stakeholder:** Public Golf Course General Managers & Regional Directors of Golf.
* **Problem:** Numerical star ratings (1–5) indicate satisfaction levels but obscure the root operational causes behind low scores.
* **Impact:** Allows management to identify operational bottlenecks (e.g., slow pace of play, poor turf conditions, clubhouse service) and deploy targeted fixes before overall ratings drop.

## Dataset
* **Source:** Scraped Google Maps & GolfNow reviews across regional public courses.
* **Target Variable:** `is_positive` (Binary: 1 for 4–5 stars, 0 for 1–3 stars).
* **Sample Data:** Stored in `data/sample_reviews.csv`.

## Planned Use of Tools
* **Claude API:** Data labeling & feature enrichment (tagging reviews with operational sub-dimensions like `pace_of_play_issue` or `green_quality`).
* **Classical NLP:** TF-IDF n-gram tokenization + Logistic Regression/Naive Bayes to ensure interpretable feature weights and fast, cost-free inference on new reviews.

## Repository Layout
* `data/`: Sample datasets and feature maps.
* `notebooks/`: Exploratory data analysis, feature extraction, and model training.
* `src/`: Reusable Python modules for data collection and preprocessing.
