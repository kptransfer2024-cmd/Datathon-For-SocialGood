# Beyond Access

**Which Complaints Get Missed? A Sentiment Audit of Bay Area Healthcare Reviews**

Project for the Advanced Track of the 8th Annual Datathon for Social Good.

## Research question

Among Google Maps reviews of healthcare services in the nine Bay Area counties, which feedback reaches the review sample we can read, and which low-star reviews does a general-purpose text classifier miss? Low-star means 1–2 stars. Star ratings are a proxy for expressed dissatisfaction, not a measure of clinical quality.

## Data

Both files were supplied by Bright Data through The Bright Initiative. They are not included in this repository.

- `google_maps_reviews.csv`: reviews of many business types. Training source for the classifier.
- `google_maps.csv`: place listings with coordinates, categories, a sample of reviews and full rating distributions. Source for the healthcare cohort and the evaluation set.

## Run

1. `pip install -r requirements.txt`
2. Put the two CSV files in a `data/` folder at the repository root.
3. Open `analysis.ipynb` in Jupyter and run all cells. The first run downloads county boundaries from U.S. Census TIGERweb into `data/`.

## Status

The notebook currently holds the project outline, an executed input and data-quality check, and the audited nine-county healthcare review cohort. The representation comparison and the model are not built yet, so there are no model results.
