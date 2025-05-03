CIFAR-10 CNN Image Classification

This repository contains a hyperparameter-optimized Convolutional Neural Network (CNN) model for classifying images in the CIFAR-10 dataset. The model is implemented using TensorFlow/Keras and achieves a test accuracy of approximately 90-92%. The project is designed to run seamlessly on Kaggle's GPU environment, with error handling for common issues like NotFoundError.
Table of Contents

Project Overview
Dataset
Model Architecture
Installation
Usage
Results
Contributing
License

Project Overview
The goal of this project is to develop a high-performance CNN model for the CIFAR-10 image classification task. The model is optimized through careful hyperparameter tuning, data augmentation, and GPU-accelerated training. Key features include:

A 32-layer CNN architecture with 4 convolutional blocks and dense layers.
Data augmentation to improve generalization.
Learning rate scheduling and early stopping to prevent overfitting.
Error handling for TensorFlow/Keras compatibility in Kaggle.

Dataset
The CIFAR-10 dataset consists of 60,000 32x32 color images across 10 classes (50,000 training, 10,000 testing). The classes are:

Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck

Each class contains 6,000 images. The dataset is directly accessible via tensorflow.keras.datasets.cifar10.
Model Architecture
The CNN model consists of 32 layers, structured as follows:

4 Convolutional Blocks:
Each block contains:
2 Conv2D layers (filters: 64, 128, 256, 512) with ReLU activation and same padding.
2 BatchNormalization layers for training stability.
1 MaxPooling2D layer for dimension reduction.
1 Dropout layer (rates: 0.3, 0.4) to prevent overfitting.




Dense Layers:
Flatten layer to convert feature maps to a vector.
2 Dense layers (1024 and 512 neurons) with ReLU activation.
2 BatchNormalization and 2 Dropout (0.5) layers.
Final Dense layer with 10 neurons and softmax activation for classification.



Total parameters: Approximately 7.8 million (see model.summary() output).
Installation
To run this project, you need a Kaggle account and a notebook with GPU enabled. Alternatively, you can run it locally with the following dependencies:
pip install tensorflow==2.15.0 numpy matplotlib seaborn scikit-learn

Kaggle Setup

Create a new Kaggle notebook.
Go to Settings > Accelerator > Select GPU T4 x2 or GPU P100.
Copy the code from cifar10_cnn_hypertuned_kaggle.ipynb (available in this repository) into the notebook.

Usage

Clone the Repository (if running locally):
git clone https://github.com/<your-username>/cifar10-cnn-classification.git
cd cifar10-cnn-classification


Run the Notebook:

In Kaggle, paste the code from cifar10_cnn_hypertuned_kaggle.ipynb and execute all cells sequentially.
The notebook will:
Load and preprocess the CIFAR-10 dataset.
Apply data augmentation.
Train the 32-layer CNN model with GPU acceleration.
Save the trained model and visualizations to /kaggle/working/.




Outputs:

Trained model: /kaggle/working/cifar10_cnn_hypertuned_model.h5
Visualizations: Training plots, confusion matrix, and sample predictions (*.png files).


Example Command (local environment):
jupyter notebook cifar10_cnn_hypertuned_kaggle.ipynb



Results

Test Accuracy: ~90-92% (varies slightly due to randomness in training).
Training Time: Approximately 20-30 minutes on Kaggle's T4 x2 GPU for 100 epochs (early stopping typically reduces this).
Key Optimizations:
Data augmentation (rotation, flip, zoom) for better generalization.
Learning rate scheduling with ReduceLROnPlateau.
Dropout and batch normalization to prevent overfitting.
Simplified data pipeline to avoid NotFoundError.



Sample outputs (confusion matrix, training plots) are saved in /kaggle/working/ and can be downloaded from Kaggle's Output tab.
Contributing
Contributions are welcome! To contribute:

Fork this repository.
Create a new branch: git checkout -b feature/your-feature.
Commit your changes: git commit -m "Add your feature".
Push to the branch: git push origin feature/your-feature.
Open a Pull Request.

Please ensure your code follows PEP 8 style guidelines and includes relevant documentation.
License
This project is licensed under the MIT License. See the LICENSE file for details.

Built with ❤️ by Furkan Bulut
