# Beyond Access - Google Maps Reviews (Healthcare Services)

**Which complaints get missed?** A sentiment audit of Bay Area healthcare reviews for the 8th Annual Datathon for Social Good, Advanced Track.

One reviewer (paraphrased) called the doctor great, found the front desk unhelpful, and left one star. Our classifier read the text and filed it as fine. This project asks how often that happens, and where.

**Start with [the notebook](analysis.ipynb)** · [View slides](https://docs.google.com/presentation/d/1AZ6jwSll1UV7ZIjFEZeli3BjL_2Ik4XE/edit) · [Download PowerPoint](presentation.pptx) · [Video Walkthrough](https://drive.google.com/file/d/1kM62s8GBE6vYaenJ1Qi0zr96S19Ei-Ja/view)

## What we studied

68,007 written reviews from 18,416 Google place listings in 9 Bay Area counties and 7 healthcare service groups. Low-star means 1–2 stars.

## Methods

- **Sampling.** We compared the share of 1–2-star ratings in the available review texts with the share among all ratings at the same listings, including ratings without text. Each listing carried the same weight in both comparisons.

- **TF-IDF** turns each review into a vector of words and two-word phrases, so “helpful” and “not helpful” are separate features. A term’s weight is $\mathrm{count}(t,d)\,[1+\ln((N+1)/(df_t+1))]$, where $N$ is the number of training reviews and $df_t$ is the number containing term $t$. This gives less weight to terms that appear almost everywhere. Each review vector is then scaled to unit length.

- **Logistic regression** learns which features point toward a 1–2-star rating. Given a review vector $x$, it estimates $P(\text{low-star}\mid x)=1/(1+e^{-(w^\top x+b)})$, where $w$ contains the learned feature weights and $b$ is the intercept. We trained on general Google Maps reviews and tested on Bay Area healthcare reviews, with no shared listings or identical texts between the two sets.

## Findings

- **Sampling gap.** At pharmacies, 39.9% of the review texts we could read were low-star, against 30.3% of all ratings at the same listings.
- **Model.** TF-IDF + logistic regression, trained on general reviews. Its healthcare flags were right 94.7% of the time (precision), and it caught 81.9% of low-star reviews (recall). Macro-F1: 0.927, against 0.449 for a majority baseline.
- **Misses.** Mental health had the highest observed miss rate (385 of 1,743 low-star reviews). Outpatient and primary care had the most misses (898 of 4,716).
- **Errors we read.** In 20 hand-read errors, some missed reviews mixed a complaint with praise for someone else.

Star ratings report experience. They do not measure clinical quality.

## Run it

1. `pip install -r requirements.txt`
2. Put `google_maps_reviews.csv` and `google_maps.csv` in a `data/` folder at the repository root.
3. Open `analysis.ipynb` in Jupyter and run all cells.

County boundaries download from U.S. Census TIGERweb if missing and are checked against a pinned hash.

## Tested environment

Release run: Python 3.10.12 on Linux with the versions pinned in `requirements.txt`. A local rerun on macOS with Python 3.12.3 matched. One independent run elsewhere reported 2,136 missed reviews and 605 false positives, against 2,278 and 583 here.

## Data

Google Maps Places and Reviews were supplied by Bright Data through The Bright Initiative. They are not included here.
