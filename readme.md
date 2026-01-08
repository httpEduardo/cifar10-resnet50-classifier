# Insonia - Image Classification with ResNet50

![Python](https://img.shields.io/badge/Python-3.6%2B-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)

A robust and efficient deep learning image classification system using TensorFlow and the ResNet50 neural network architecture, applied to the CIFAR-10 dataset.

## Overview

This project implements a Convolutional Neural Network (CNN) using the ResNet50 architecture to recognize and categorize images from the CIFAR-10 dataset. The model leverages transfer learning with pre-trained ImageNet weights and fine-tuning techniques to achieve high accuracy on the CIFAR-10 benchmark.

The CIFAR-10 dataset consists of 60,000 32x32 color images across 10 different classes:
- Airplane
- Automobile
- Bird
- Cat
- Deer
- Dog
- Frog
- Horse
- Ship
- Truck

## Features

- **Transfer Learning**: Utilizes pre-trained ResNet50 weights from ImageNet
- **Two-Stage Training**: Initial training with frozen base layers followed by fine-tuning
- **Regularization Techniques**: 
  - Dropout layers to prevent overfitting
  - L2 regularization for weight penalties
- **Comprehensive Evaluation**: 
  - Confusion matrix visualization
  - Detailed classification reports with precision, recall, and F1-score
- **Adaptive Learning**: Fine-tuning of the last 15 layers for domain-specific adaptation

## Requirements

- Python 3.6 or higher
- TensorFlow 2.x
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn

## Installation

Install all required dependencies using pip:

```bash
pip install tensorflow numpy matplotlib seaborn scikit-learn
```

## Usage

### Training the Model

Run the main script to train the model:

```bash
python main.py
```

The training process consists of two stages:

1. **Initial Training (5 epochs)**: The ResNet50 base layers are frozen, and only the custom top layers are trained
2. **Fine-Tuning (5 epochs)**: The last 15 layers of ResNet50 are unfrozen and trained with a lower learning rate

### Model Prediction

The model automatically evaluates on the test set after training and generates:
- Test accuracy and loss metrics
- Confusion matrix heatmap
- Classification report with per-class metrics

## Model Architecture

The model architecture consists of:

1. **Base Model**: ResNet50 (pre-trained on ImageNet)
   - Input shape: 32x32x3 (CIFAR-10 image dimensions)
   - Weights: ImageNet pre-trained
   - Top layers: Excluded

2. **Custom Top Layers**:
   - Global Average Pooling 2D
   - Dense layer (1024 units, ReLU activation, L2 regularization)
   - Dropout layer (50% dropout rate)
   - Output layer (10 units, Softmax activation)

3. **Training Configuration**:
   - Optimizer: Adam
     - Initial training: learning rate = 0.0001
     - Fine-tuning: learning rate = 0.00001
   - Loss function: Sparse Categorical Crossentropy
   - Metrics: Accuracy

### Code Structure

The `main.py` file implements the following pipeline:

- Data loading and preprocessing of CIFAR-10 dataset
- Model construction using ResNet50 architecture
- Model compilation and initial training
- Fine-tuning of selected ResNet50 layers
- Model evaluation on test set
- Generation of confusion matrix and classification reports

## Dataset

**CIFAR-10** is a widely-used benchmark dataset for image classification:

- **Total Images**: 60,000 (50,000 training + 10,000 testing)
- **Image Size**: 32x32 pixels
- **Color Channels**: 3 (RGB)
- **Classes**: 10 equally distributed categories
- **Preprocessing**: Pixel values normalized to [0, 1] range

## Results

The model evaluation includes:

- **Confusion Matrix**: Visual representation of model performance across all 10 classes
- **Classification Report**: Detailed metrics including:
  - Precision: Ratio of correctly predicted positive observations
  - Recall: Ratio of correctly predicted positive observations to all actual positives
  - F1-Score: Weighted average of Precision and Recall
  - Support: Number of actual occurrences of each class

### Performance Metrics

The two-stage training approach with transfer learning and fine-tuning enables the model to achieve competitive accuracy on the CIFAR-10 dataset while avoiding overfitting through regularization techniques.

## License

This project is licensed under the MIT License - see below for details:

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Acknowledgments

- ResNet50 architecture from [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385)
- CIFAR-10 dataset from the [Canadian Institute for Advanced Research](https://www.cs.toronto.edu/~kriz/cifar.html)
