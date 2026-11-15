# Beyond Access

**Which Complaints Get Missed? A Sentiment Audit of Bay Area Healthcare Reviews**

Project for the Advanced Track of the 8th Annual Datathon for Social Good.

## Research question

Among Google Maps reviews of healthcare services in the nine Bay Area counties, which feedback reaches the review sample we can read, and which low-star reviews does a general-purpose text classifier miss? Low-star means 1–2 stars. Star ratings are a proxy for expressed dissatisfaction, not a measure of clinical quality.

## Data

Both files were supplied by Bright Data through The Bright Initiative. They are not included in this repository.

- `google_maps_reviews.csv`: reviews of many business types. Training, validation and internal test data for the classifier.
- `google_maps.csv`: place listings with coordinates, categories, a sample of reviews and full rating distributions. Source for the healthcare cohort, which is the external test set.

## Findings

The healthcare cohort has 68,007 written reviews from 18,416 Google place listings in seven service groups.

- **Sample representation.** At the same listings and weights, 18.6% of sampled review texts were low-star against 15.6% of all ratings. The gap was largest for pharmacies (9.6 percentage points).
- **Classifier.** TF-IDF with logistic regression, trained only on general reviews, reached low-star precision 0.947 and recall 0.819 on the healthcare cohort (macro-F1 0.927). A majority baseline finds no low-star review (macro-F1 0.449).
- **Misses.** The model missed 2,278 of 12,617 low-star reviews. The miss rate ran from 14.1 per 100 in vision care to 22.1 per 100 in mental health, and outpatient and primary care had the most missed reviews (898).
- **Error reading.** In 20 hand-read errors, missed reviews often described a problem plainly or mixed it with praise for someone else.

These results describe the observed reviews. They do not measure clinical quality or demographic disparities.

## Run

1. `pip install -r requirements.txt`
2. Put the two CSV files in a `data/` folder at the repository root.
3. Open `analysis.ipynb` in Jupyter and run all cells. It takes a few minutes.

County boundaries are read from `data/tigerweb_bay_area_counties.geojson`. If that file is missing, the notebook requests it from U.S. Census TIGERweb and compares it with a pinned hash.
