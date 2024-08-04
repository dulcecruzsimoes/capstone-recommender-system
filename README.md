# Recommender System for Retailrocket Dataset

This Jupyter Notebook provides an end-to-end solution for building a recommendation system with implicit feedback using the Retailrocket dataset. It includes data loading, exploratory data analysis, data preprocessing using collaborative filtering, model training using various algorithms.

## Table of Contents

- [Recommender System for Retailrocket Dataset](#recommender-system-for-retailrocket-dataset)
  - [Table of Contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Setup and Installation](#setup-and-installation)
    - [Prerequisites](#prerequisites)
    - [Installation](#installation)
  - [Dataset](#dataset)
  - [Notebook Overview](#notebook-overview)
  - [Results](#results)
    - [Reasons for KNN Performance](#reasons-for-knn-performance)
  - [Model Card](#model-card)
  - [Contributing](#contributing)
  - [License](#license)

## Introduction

This project aims to create a recommendation system for an online retail marketplace. The recommendation system is built using collaborative filtering and various machine learning algorithms.

## Setup and Installation

### Prerequisites

- Python 3.6 or higher
- Jupyter Notebook

### Installation

1. Clone the repository
2. Install the required libraries
3. Open the Jupyter Notebook

## Dataset

The dataset used in this project is the Retailrocket dataset. It consists of three main files:
- `events.csv`

Make sure to download the file and place it in the same directory as the notebook.

## Notebook Overview

The project consists of four Jupyter notebooks, each serving a specific purpose:

1. **exploratory_data_analysis.ipynb**: This notebook performs an exploratory data analysis to understand the distribution and characteristics of the data.
2. **knn.ipynb**: This notebook implements the K-Nearest Neighbors (KNN) algorithm for the recommendation system.
3. **svd.ipynb**: This notebook implements the Singular Value Decomposition (SVD) algorithm for the recommendation system.
4. **nn.ipynb**: This notebook implements a Neural Network (NN) for the recommendation system.

Each algorithm has a corresponding `.md` file explaining the implementation details of the model used:
1. **KNN**: [KNN Model](knn_model.md).
2. **SVD**: [SVC Model](svc_model.md).
3. **NN**:  [NN Model](nn_model.md).

## Results

The model that achieved the best results was the KNN model with the following performance metrics:
- Precision@5: 0.546
- Recall@5: 0.569
- Hits@5: 237

These results are considered acceptable for a recommendation system. The Precision@5 and Recall@5 values indicate that the model is reasonably good at recommending relevant items to users, making it a useful tool for improving user engagement and satisfaction.

### Reasons for KNN Performance
KNN performed the best due to its simplicity and effectiveness in capturing the similarity between users and items based on historical interaction data. It leverages the local neighborhood information, which is particularly useful in sparse datasets like Retailrocket.

## Model Card

For detailed information about the model, performance, and other relevant details, please refer to the [Model Card](model_card.md).

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an issue.

## License

This project is licensed under the MIT License. See the LICENSE file for more details.
