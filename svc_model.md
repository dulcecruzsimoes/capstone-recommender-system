# SVD Model for Recommender System

## Overview

This document provides a detailed explanation of the implementation, evaluation, and results of the Singular Value Decomposition (SVD) model for the recommendation system using the Retailrocket dataset.

## Detailed Explanation of Dataset Reduction, Splitting, and Evaluation Process

### Dataset Reduction for Performance

Given the large size of the original dataset, it was necessary to reduce its size to improve computational performance. We sampled a subset of 100,000 interactions from the original dataset. This reduction allows us to test and refine our recommendation model more efficiently. The reduced dataset retains the characteristics of the original dataset but is small enough to allow for quicker iterations during model development and evaluation.

### Splitting Data into Training and Test Sets

To evaluate the recommendation model effectively, we divided the reduced dataset into training and test sets based on a temporal split. This approach ensures that we evaluate the model on future interactions, simulating a real-world scenario where we predict future user behavior based on past interactions.

### Evaluation Methodology

#### User-Item Interaction Matrix

We transformed the training and test datasets into user-item interaction matrices. These matrices represent users' interactions with items, where rows correspond to users, columns correspond to items, and cell values indicate the number of interactions. For the purpose of training and testing the SVD model, we further mapped the event types ('view', 'addtocart', 'transaction') to numeric values (1, 2, 3 respectively).

#### SVD Recommendation Model

We used the Singular Value Decomposition (SVD) algorithm to recommend items to users. The SVD model was trained using the training set's interaction matrix. The `Surprise` library was utilized to implement the SVD model.

#### Evaluation Process

We evaluated the model's performance using precision, recall, and the number of hits. These metrics provide insights into how well the model recommends relevant items to users.

1. **Precision@K:** The fraction of recommended items that are relevant.
2. **Recall@K:** The fraction of relevant items that are recommended.
3. **Hits@K:** The total number of relevant items recommended across all users.

## Results

The model that achieved the following performance metrics:
- **Precision@5:** 5.9%
- **Recall@5:** 29.3%
- **Hits@5:** 121

### Acceptability of Results

These results indicate that the SVD model has room for improvement. The precision value suggests that only a small portion of the recommended items are relevant to the users. However, the recall value shows that the model is able to retrieve a significant portion of the relevant items.

### Reasons for SVD Performance

The performance of the SVD model can be attributed to its ability to capture latent factors in the user-item interaction matrix. However, the relatively low precision suggests that the model may benefit from further tuning and incorporating additional features.

## Future Improvements

To improve the model further, we could explore:
- **Tuning the hyperparameters**: Optimizing factors like the number of latent factors and regularization parameters.
- **Incorporating more features**: Including additional user and item features to capture more information.
- **Hybrid Models**: Combining SVD with other models like KNN or neural networks to leverage the strengths of different algorithms.
