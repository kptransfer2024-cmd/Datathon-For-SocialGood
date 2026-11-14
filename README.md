# Beyond Access
Sentiment classification and subgroup error analysis for Bay Area essential-service reviews.

**Status: planning scaffold. Modeling cells and findings are pending implementation.**

## Files
- `analysis.ipynb`: the complete project outline and implementation cells, from raw inputs through evaluation and interpretation.
- `presentation.pptx`: editable seven-slide presentation framework. Results slides are explicitly pending.
- `requirements.txt`: minimal packages. Pin versions after a successful end-to-end run.
- `.gitignore`: excludes raw data and local environment files.

## Research question
Can review text identify low-star reviews of essential services, and does model performance vary across service types and locations? The practical output is a feedback audit for human review. Existing stars already identify low ratings; the classifier is a benchmark for text interpretation, not proof of a new operational capability.

## Data and method
Use organizer-supplied Google Maps Places and Reviews. Join on place_id, audit matches and keep supported essential-service categories. Predict 1–2 stars versus 3–5 stars with TF-IDF + Logistic Regression, compared with a majority-class baseline. Keep places disjoint across training, validation and test sets. Audit at least three sufficiently populated subgroup levels.

## Run after implementation
1. Install Python 3 and `pip install -r requirements.txt`.
2. Place `google_maps.csv` and `google_maps_reviews.csv` in a local `data/` folder.
3. Open `analysis.ipynb` in Jupyter or Colab. Implement the marked cells, then restart and run all.
4. Update slides using actual notebook outputs. Record tested versions and input checksums.

The current notebook is an outline, not an executable completed analysis. No metrics or findings have been generated.

## Interpretation and privacy
Ratings are subjective labels. Reviews are self-selected and cannot establish service quality or population-level inequity. Report aggregate patterns, remove identity fields, and paraphrase sensitive examples. Confirm redistribution permission before publishing raw records.

## Submission
Project URL: pending

Presentation: `presentation.pptx`

Video URL (maximum 5 minutes): pending

One teammate submits the project URL, slideshow and video through the organizer's form:
https://docs.google.com/forms/d/e/1FAIpQLSfWHAXrGLYZztTQ5lHI_GlY72-hW9zT1yps0FI2gxVkdRs7ag/viewform

Sources: organizer-provided Tracks & Guide and the Places/Reviews dataset READMEs. Data supplied by Bright Data through The Bright Initiative.
