# CIFAR-10 ResNet50 Classifier

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)

A small image-classification example that fine-tunes a ResNet50 model on the CIFAR-10 dataset using TensorFlow. The script trains the model, evaluates it on the test split, and reports classification metrics.

## Run locally

Install the dependencies and start the training script:

```bash
pip install tensorflow numpy matplotlib seaborn scikit-learn
python main.py
```

TensorFlow downloads CIFAR-10 when the dataset is first requested. The model uses ImageNet weights as its starting point.
