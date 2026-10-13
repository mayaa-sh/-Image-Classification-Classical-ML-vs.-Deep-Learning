Fashion-MNIST Image Classification

Overview

This project explores image classification using the Fashion-MNIST dataset. It compares classical machine learning algorithms, a Multi-Layer Perceptron (MLP), and a Convolutional Neural Network (CNN) to identify which approach performs best on grayscale clothing images.

The project follows an end-to-end machine learning workflow, including data preprocessing, baseline modeling, hyperparameter tuning, model evaluation, and error analysis.

Objectives

- Build baseline image classification models using classical machine learning.
- Compare a default MLP with a hyperparameter-tuned MLP.
- Develop a CNN using TensorFlow/Keras.
- Evaluate model performance using accuracy and class-level classification metrics.
- Analyze misclassifications to identify challenging clothing categories.
- Compare predictive performance with training time.

Dataset

The project uses the Fashion-MNIST dataset, which contains 70,000 grayscale images of clothing items.

Each image has a resolution of 28 × 28 pixels and belongs to one of 10 classes.

Dataset Split| Number of Images
Training| 54,000
Validation| 6,000
Test| 10,000
Total| 70,000

The original training set of 60,000 images is split into training and validation subsets using stratified sampling. The official test set contains 10,000 images.

Classes

The dataset contains the following categories:

- T-shirt/top
- Trouser
- Pullover
- Dress
- Coat
- Sandal
- Shirt
- Sneaker
- Bag
- Ankle boot

Images are normalized to the range [0, 1]. Flattened images are used for the scikit-learn models, while the original image structure is preserved for the CNN.

Models

Five model configurations are evaluated:

1. Logistic Regression — a linear classification baseline.
2. Random Forest — an ensemble-based classical machine learning model.
3. MLP (Default) — a feed-forward neural network implemented with scikit-learn.
4. MLP (Tuned) — an MLP optimized using randomized hyperparameter search with three-fold cross-validation on a 15,000-sample subset.
5. CNN — a convolutional neural network built with TensorFlow/Keras.

The CNN uses two convolutional layers, max-pooling layers, dropout regularization, and a softmax output layer for ten-class classification.

The CNN is trained with the Adam optimizer and sparse categorical cross-entropy loss. Early stopping is configured to monitor validation loss.

Model Evaluation

Models are compared using validation accuracy, test accuracy, and training time. Classification reports and a normalized confusion matrix are used to examine class-level performance and common misclassifications.

Results

The following results were recorded in the current notebook execution.

Model| Validation Accuracy| Test Accuracy| Training Time (s)
CNN| 92.00%| 90.80%| 679.41
MLP (Tuned)| 90.43%| 89.20%| 69.71
MLP (Default)| 89.72%| 88.10%| 21.58
Random Forest| 88.67%| 87.68%| 121.38
Logistic Regression| 86.20%| 84.13%| 62.54

Training times are specific to the recorded execution environment and may vary across machines.

Important: For a strict evaluation protocol, select the final model using validation performance and evaluate the held-out test set only after model selection. The current notebook computes test accuracy for each scikit-learn model, so this evaluation step should be refactored before claiming that the test set was used exclusively for final evaluation.

Error Analysis

The CNN achieved a test accuracy of 90.80% and a macro-average F1-score of approximately 0.907.

Performance varied across clothing categories:

- Shirt was the most challenging class, with an F1-score of approximately 0.717.
- Shirt images were frequently misclassified as T-shirt/top, Pullover, and Coat.
- Trouser and Sandal achieved F1-scores of approximately 0.987 and 0.983, respectively.
- Bag and Ankle boot also achieved strong classification performance.

The confusion matrix and misclassified image visualizations help identify categories with similar visual characteristics and reveal where the model struggles.

Key Findings

- The CNN achieved the highest test accuracy among the evaluated models.
- It outperformed the tuned MLP by 1.60 percentage points in test accuracy.
- Convolutional layers can exploit spatial information that is not explicitly preserved when images are flattened for classical machine learning models.
- Visually similar upper-body garments remain a major source of classification errors.
- The CNN achieved better predictive performance at a higher training-time cost in the recorded experiment.

Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- scikit-learn
- TensorFlow/Keras
- Jupyter Notebook

The Fashion-MNIST dataset is loaded through the Keras dataset API.

Future Improvements

Potential extensions include:

- Applying data augmentation to improve generalization.
- Experimenting with batch normalization and alternative CNN architectures.
- Expanding the CNN training budget while monitoring validation loss.
- Performing a broader hyperparameter search.
- Comparing per-class precision, recall, and F1-score across models.
- Recording hardware specifications to make training-time comparisons more reproducible.
- Separating validation-based model selection from the final test-set evaluation.

Summary

This project demonstrates practical machine learning and deep learning skills through a comparative image classification study. It covers data preprocessing, baseline development, hyperparameter tuning, CNN training, model evaluation, and error analysis.

The results highlight the effectiveness of CNNs for image classification while identifying visually similar clothing categories as an important area for further improvement.
