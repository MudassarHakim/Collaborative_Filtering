# Collaborative Filtering – User & Item Based Recommendation

**Repository:** `Collaborative_Filtering`
**Notebook:** [collaborative_user_based.ipynb](collaborative_user_based.ipynb)

## Overview

This repository contains an implementation of a **user-based collaborative filtering** recommendation system (in the notebook `collaborative_user_based.ipynb`). The goal is to show how to use collaborative filtering techniques to predict user preferences based on past interactions of similar users & similar movies.

## Features

* Builds a user–item interaction matrix from a dataset of users, items and ratings.
* Computes user-user similarity (e.g., via cosine similarity or Pearson correlation) to identify “neighbour” users.
* Predicts ratings for items not yet consumed by a given user, using ratings of similar users.
* Generates top-N recommended items for each user based on predicted ratings.
* Evaluates performance (e.g., via RMSE, MAE, precision/recall of top-N).

## Tech Stack & Dependencies

* Python (3.x)
* Common libraries: `pandas`, `numpy`, `scikit-learn` (if used for similarity), `matplotlib`/`seaborn` (for visuals)
* Jupyter Notebook (`.ipynb`) format

## Folder / File Structure

```
/Collaborative_Filtering
│  collaborative_user_based.ipynb
│  README.md
│  ratings.csv, movie_genres_final.csv
└─ …
```

## Usage

1. Clone the repository:

   ```
   git clone https://github.com/MudassarHakim/Collaborative_Filtering.git
   cd Collaborative_Filtering
   ```
2. Install dependencies (for example via pip):

   ```
   pip install pandas numpy scikit-learn matplotlib seaborn
   ```
3. Open and run the notebook `collaborative_user_based.ipynb` using Jupyter:

   ```
   jupyter notebook
   ```

   Then navigate to the notebook and execute the cells step by step.
4. Follow the notebook structure:

   * Data loading & preprocessing
   * Creation of user–item matrix
   * Similarity calculation
   * Rating prediction & recommendation generation
   * Evaluation & visualization

## Approach Explained

* **User–Item Matrix**: Each row corresponds to a user, each column to an item; cell values represent the rating given by the user to the item (or NaN if not rated).
* **Similarity Computation**: For each pair of users, compute a similarity score (e.g., cosine similarity) based on their rating vectors (only on co-rated items).
* **Prediction**: For a target user and an item they haven’t rated, predict the rating by taking a weighted average of ratings from similar users (neighbours) who have rated that item.
* **Top-N Recommendation**: For each user, list items with highest predicted ratings (that the user hasn’t yet seen/rated).
* **Evaluation**: Use metrics such as Root Mean Square Error (RMSE) or Mean Absolute Error (MAE) on held-out test ratings; for top-N, use precision/recall measures.

## Why This Is Useful

User-based collaborative filtering is intuitive and easy to implement. It leverages the wisdom of similar users to make recommendations, and can work well when you have many users with overlapping interests and sufficient rating data. The notebook provides a clear, educational demonstration of the core idea, and can be extended or adapted for more advanced real-world systems (e.g., item-based, matrix factorization, hybrid methods).

## Limitations & Considerations

* Cold-start problem: New users (or users with few ratings) may not get good recommendations.
* Scalability: Computing similarity among all user pairs can be expensive for large datasets.
* Sparsity: Many users may only rate a few items, leading to very sparse user–item matrices which can degrade performance.
* Popularity bias: Users similar in ratings may still diverge in tastes beyond the rated items; simple similarity may not capture full nuance.
* Data leakage / evaluation: When splitting data into train/test, make sure that test items truly reflect “future” unseen ratings by the user, to avoid overly optimistic estimates.

## Possible Extensions

* Implement **item-based collaborative filtering** (compute similarity among items instead of users).
* Incorporate **matrix factorization** (e.g., SVD, ALS) for latent-factor modeling.
* Add **hybrid approaches** combining collaborative filtering + content-based filtering.
* Improve evaluation to include **Top-N ranking metrics** (Precision@K, Recall@K, NDCG).
* Handle **implicit feedback** (clicks, views) instead of explicit ratings.
* Optimize performance for large-scale datasets (approximate nearest-neighbours, dimension reduction).

## License

Specify here your license (e.g., MIT License).

```
MIT License
Copyright (c) 2025 [Your Name]
```

## Contributing

Contributions are welcome! If you find bugs, have ideas for new features or want to improve the evaluation/reporting, feel free to open an issue or submit a pull request.

## Acknowledgements

Thanks to the open-source community for tools and libraries used. Data may be inspired by publicly available datasets (e.g., MovieLens)

