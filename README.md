# GTSRB-Traffic-Sign-CNN
GTSRB Traffic Sign Recognition Using CNN

Overview

This project implements a Convolutional Neural Network (CNN) for
multi-class traffic sign recognition using the German Traffic Sign
Recognition Benchmark (GTSRB) dataset.

The notebook covers the complete workflow from dataset setup and
preprocessing to CNN training, model evaluation, confusion-matrix
analysis, test-image prediction, and visualization of learned filters
and feature maps.

Dataset

The project uses the preprocessed GTSRB dataset published on Kaggle by
Valentyn Sichkar:

Dataset: Traffic Signs Preprocessed

Source: Kaggle

Classes: 43 traffic sign categories

Training samples: 34,799

Validation samples: 4,410

Test samples: 12,630

The dataset is loaded from train.pickle, valid.pickle, and
test.pickle, with class names provided by label_names.csv.

Data Preprocessing

The notebook performs the following preprocessing steps:

Sets random seeds to support reproducibility.

Loads the training, validation, and test data from pickle files.

Normalizes image pixel values from 0--255 to the range 0--1.

Resizes images to 48 × 48 pixels.

Converts class labels to one-hot encoded vectors.

Maps class IDs to readable traffic sign names.

Examines the test-set class distribution.

Dataset Shapes

Dataset                      Images        Labels

Training       34,799 × 48 × 48 × 3   34,799 × 43
Validation      4,410 × 48 × 48 × 3    4,410 × 43
Test           12,630 × 48 × 48 × 3   12,630 × 43

CNN Architecture

The CNN consists of three convolutional blocks followed by fully
connected layers:

Conv2D --- 32 filters, 3 × 3 kernel, ReLU

MaxPooling2D --- 2 × 2

Conv2D --- 64 filters, 3 × 3 kernel, ReLU

MaxPooling2D --- 2 × 2

Conv2D --- 128 filters, 3 × 3 kernel, ReLU

MaxPooling2D --- 2 × 2

Flatten

Dense --- 128 units, ReLU

Dropout --- 0.5

Dense --- 43 units, Softmax

The model contains 361,067 trainable parameters.

Compilation

Optimizer: Adam

Loss: Categorical Cross-Entropy

Metric: Accuracy

Training

The model is trained with:

Epochs: Up to 20

Batch size: 64

Shuffle: Enabled

Early stopping: Enabled

Early stopping monitor: Validation loss

Patience: 5 epochs

Restore best weights: Enabled

The training process records both training and validation accuracy/loss
for analysis.

Results

The trained CNN achieved:

Test Accuracy: 95.82%

Test Loss: 0.2137

The notebook also generates:

Training vs. validation accuracy curves

Training vs. validation loss curves

A 43-class confusion matrix

A misclassification-only confusion matrix

Per-class misclassification counts

A classification report containing precision, recall, and F1-score

Random test-image predictions

CNN filter visualizations

CNN feature-map visualizations

Model Files

The notebook saves the trained model in two formats:

traffic_sign_cnn.keras

traffic_sign_cnn.h5

The native .keras format is the preferred format in current Keras
versions, while the .h5 file is also generated for compatibility.

Project Workflow

GTSRB Dataset
      ↓
Dataset Setup
      ↓
Load Pickle Files
      ↓
Normalize Images
      ↓
Resize to 48 × 48
      ↓
One-Hot Encode Labels
      ↓
CNN Training
      ↓
Early Stopping
      ↓
Test Evaluation
      ↓
Confusion Matrix & Classification Report
      ↓
Prediction & Feature Visualization

Notebook

The complete implementation is provided in:

Project2_GTSRB_CNN.ipynb

The notebook is designed to run in Google Colab and includes the
dataset download/setup, preprocessing, model training, evaluation, and
visualization steps.

Technologies Used

Python

TensorFlow / Keras

NumPy

Pandas

Matplotlib

Seaborn

Scikit-learn

Google Colab

Kaggle API
