# Neural Network Model for Recommender System

## Overview

This document provides a detailed explanation of the implementation, evaluation, and results of the Neural Network (NN) model for the recommendation system using the Retailrocket dataset.

## Detailed Explanation of Dataset Reduction, Splitting, and Evaluation Process

### Dataset Reduction for Performance

Given the large size of the original dataset, it was necessary to reduce its size to improve computational performance. We sampled a subset of 100,000 interactions from the original dataset. This reduction allows us to test and refine our recommendation model more efficiently. The reduced dataset retains the characteristics of the original dataset but is small enough to allow for quicker iterations during model development and evaluation.

### Steps for Dataset Reduction:
1. **Load the original dataset**: The dataset was loaded from the `events.csv` file.
2. **Convert timestamps to datetime format**: This conversion was necessary for better readability and to facilitate the temporal split of the dataset.
3. **Sample 100,000 interactions randomly**: A random sample of 100,000 interactions was selected from the original dataset to create a manageable subset for model training and evaluation.

### Splitting Data into Training and Test Sets

To evaluate the recommendation model effectively, we divided the reduced dataset into training and test sets based on a temporal split. This approach ensures that we evaluate the model on future interactions, simulating a real-world scenario where we predict future user behavior based on past interactions.

### Steps for Data Splitting:
1. **Define the split date**: The 80th percentile of the interaction dates in the sampled dataset was selected as the split date.
2. **Create the training set**: Interactions before the split date were used for training the model.
3. **Create the test set**: Interactions on or after the split date were used for testing the model. It was ensured that all users and items in the test set also existed in the training set to maintain consistency and relevance in the recommendations.

### Evaluation Methodology

#### Encoding User and Item IDs

To facilitate the use of user and item IDs in the neural network model, these IDs were encoded to continuous integer indices using label encoding. This transformation allows the model to efficiently process the IDs during training and evaluation.

#### Generating Samples for Training

To train the neural network model, we generated both positive and negative samples. Positive samples represented actual user-item interactions from the dataset, while negative samples were generated to represent non-interactions. This process involved ensuring that the negative samples did not overlap with the positive samples, thereby providing a clear distinction for the model to learn from.

#### Neural Network Model

The neural network model was implemented using PyTorch. The model architecture consisted of embedding layers for users and items, followed by fully connected layers. The embedding layers transformed the user and item IDs into dense vector representations, which were then concatenated and passed through the fully connected layers to predict interaction probabilities.

#### Training the Neural Network

The model was trained using binary cross-entropy loss, which is suitable for binary classification tasks like predicting whether a user will interact with an item. The Adam optimizer was used to update the model weights. The training process involved multiple epochs, where the model parameters were adjusted iteratively to minimize the loss. Due to computational constraints, the training was performed on the CPU.

#### Function to Get Recommendations

To generate recommendations, we created a function that predicted interaction scores for all items for a given user. The items with the highest predicted scores were selected as the top recommendations for the user. This approach ensures that the recommendations are tailored to the user's preferences as learned by the model.

#### Evaluation Process

The model's performance was evaluated using precision, recall, and the number of hits. These metrics provide insights into how well the model recommends relevant items to users.

1. **Precision@K**: The fraction of recommended items that are relevant.
2. **Recall@K**: The fraction of relevant items that are recommended.
3. **Hits@K**: The total number of relevant items recommended across all users.

## Results

The evaluation of the Neural Network model yielded the following metrics:
- **Precision@5**: 0.00%
- **Recall@5**: 0.00%
- **Hits@5**: 0

### Acceptability of Results

These results indicate that the Neural Network model did not perform well in recommending relevant items to users. Both the precision and recall values are zero, suggesting that the model was unable to capture the user's preferences effectively. This could be due to several factors such as insufficient training data, suboptimal model architecture, or inadequate training duration.

### Reasons for Neural Network Performance

The poor performance of the Neural Network model can be attributed to various reasons, including:
- **Insufficient Training Data**: Despite reducing the dataset size, the model might still require more interactions to learn meaningful patterns.
- **Model Complexity**: The chosen architecture might not be complex enough to capture the underlying patterns in the data.
- **Training Duration**: The number of epochs for training might not have been sufficient for the model to converge.

## Future Improvements

To improve the model further, we could explore:
- **Increasing the Training Data**: Using a larger subset of the dataset to provide more interactions for the model to learn from.
- **Tuning the Hyperparameters**: Optimizing the learning rate, batch size, and number of epochs to enhance model performance.
- **Enhancing Model Architecture**: Adding more layers or using advanced architectures like attention mechanisms to capture complex patterns.
- **Using GPU for Training**: Leveraging GPU acceleration to train the model faster and on larger datasets.
