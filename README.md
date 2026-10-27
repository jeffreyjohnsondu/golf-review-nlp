# Golf Course Review Operational Diagnostic & Aspect Analysis

## Overview
An NLP and text-extraction pipeline designed to analyze public golf course reviews, extract structured operational issue flags and aspect-based sentiment, and quantify the exact drivers of customer dissatisfaction to inform management decision-making.

## Stakeholder & Business Problem
* **Stakeholder:** Public Golf Course General Managers, Head Superintendents, and Regional Directors of Golf.
* **Problem:** Numerical star ratings (1–5) and aggregate sentiment scores indicate overall satisfaction levels but fail to explain the root operational causes behind low scores. Predicting whether a review is positive or negative provides little new information since the rating is already known.
* **Impact:** Moving from prediction to explanation. This project quantifies the precise operational bottlenecks (e.g., slow pace of play, poor green conditions, clubhouse service issues) and measures their specific magnitude on customer ratings, giving management clear directives on where to allocate staff and capital.

## Dataset & Scope
* **Source:** Scraped Google Maps reviews across regional public courses (e.g., Kennedy Golf Course)
* **Key Columns:** `review_text`, `star_rating`, `course_name`, `review_date`, `location`
* **Segment & Temporal Analysis:** Leverages timestamps and course groupings to evaluate whether complaints (such as pace of play or turf maintenance) spike seasonally or during peak operating hours.

## Methodology & Tooling
* **Structured Information Extraction (Path B):** Uses the Claude API to process review texts offline, extracting aspect-based sentiment and binary issue flags (e.g., `pace_of_play_issue`, `course_condition_issue`, `service_issue`)
* **Explanatory Regression Analysis:** Regresses star ratings against extracted aspect flags—controlling for course and time—to calculate the exact rating penalty associated with each specific operational failure.
* **Comparative Modeling:** Evaluates multiple feature spaces (Baseline TF-IDF/n-grams vs. Claude-extracted operational topics vs. aspect-based sentiment) to maximize business interpretability.

## Actionable Outcomes (Moving Past Weak Recommendations)
Instead of vague suggestions like *"improve pace of play,"* this pipeline generates quantified, time-bound findings for management:
* *Example Target Output:* Quantifying that negative sentiment tied to pace-of-play issues increases by a measurable percentage during Q3 weekend morning tee times, driving a specific star-rating penalty.
* *Who Acts & What They Do Differently:* General Managers and Superintendents use these insights to dynamically adjust tee-time spacing intervals or reschedule heavy maintenance windows to off-peak days.

## Repository Layout
* `data/` — Contains structured CSV datasets (e.g., `kennedy_golf_reviews.csv`)
* `notebooks/` — Sequential Jupyter notebooks covering data acquisition, text preprocessing, feature extraction, and explanatory regression analysis.
* `src/` — Reusable modular Python code for data loading and preprocessing.
