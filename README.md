# Market-Basket Analysis on the IMDB Top 1000 Dataset

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/SamueleSamonini/Market-basket-analysis/blob/main/main.ipynb)

University project for the **Algorithms for Massive Data** module, Master in Data Science
for Economics, Università degli Studi di Milano — A.Y. 2025/26.

## Overview

This project implements **market-basket analysis** on the
[IMDB Top 1000 dataset](https://www.kaggle.com/datasets/harshitshankhdhar/imdb-dataset-of-top-1000-movies-and-tv-shows).
Each movie is treated as a *basket* and its four leading actors (`Star1`–`Star4`) as the
*items*. The goal is to find groups of actors who frequently appear together.

Two algorithms are implemented and compared:

- **A-Priori** — the classic level-wise algorithm for frequent itemsets.
- **PCY (Park–Chen–Yu)** — an optimization of A-Priori that uses a hash table during the
  first pass to filter candidate pairs.

## Contents

- `main.ipynb` — the Jupyter notebook with the full analysis (data loading,
  preprocessing, both algorithms, and the scalability experiments).
- `Report.pdf` — the project report describing the methodology, experiments and results.
- `imdb_top_1000.csv` — the dataset (also downloaded automatically by the notebook).

## How to run

The notebook is designed to run on **Google Colab** (click the badge above) or locally
with Jupyter.

It downloads the dataset through the Kaggle API. Before running, insert your Kaggle
credentials in the dedicated cell:

```python
os.environ["KAGGLE_USERNAME"] = "your_username"
os.environ["KAGGLE_KEY"] = "your_key"
```

See the [Kaggle API documentation](https://github.com/Kaggle/kaggle-api) for how to
obtain your credentials.

## Main results

- A-Priori and PCY return identical frequent itemsets, confirming correctness.
- The frequent itemsets correspond to meaningful patterns: film sagas (Harry Potter, The
  Lord of the Rings, Star Wars), director–actor collaborations (e.g. Mifune–Kurosawa,
  Coen–Turturro) and shared cinematic universes (Marvel).
- Both algorithms scale linearly with the number of baskets.
- On this dataset A-Priori is faster than PCY: the small fixed-size baskets (four actors)
  do not provide the conditions under which the PCY bucket filter pays off. The report
  discusses this result in detail.

## Author

Samuele Samonini — Student ID 73427A