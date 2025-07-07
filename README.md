# COGS 181 Final Project - AlexNet on CIFAR-10

## Overview

This project implements and evaluates the performance of **AlexNet**, a convolutional neural network, on the **CIFAR-10** dataset using **PyTorch**. It explores how different activation functions and hyperparameter tuning affect classification accuracy and loss.

---

## Objectives

- Implement AlexNet from scratch using PyTorch.
- Experiment with activation functions: `ReLU`, `Leaky ReLU`, `Sigmoid`.
- Tune key hyperparameters:
  - Learning rate
  - Batch size
  - Dropout rate
- Evaluate model performance using accuracy and cross-entropy loss.

---

## Dataset

- **CIFAR-10**:
  - 60,000 32×32 color images
  - 10 classes (6,000 images/class)
- **Preprocessing**:
  - Random horizontal flip
  - Random cropping (32x32 with padding=4)
  - Normalization (mean=0.5, std=0.5 per channel)

---

## Model Architecture

**AlexNet** consists of:
- 5 Convolutional Layers:
  - Each followed by an activation function and some followed by max pooling.
- 3 Fully Connected Layers:
  - Includes dropout for regularization.

**Activation Functions Tested**:
- `ReLU` ✅ (Best performance)
- `Leaky ReLU` 🔄 (Competitive but less consistent)
- `Sigmoid` ❌ (Poor performance)

---

## Hyperparameter Tuning

| Hyperparameter     | Values Tested            | Best Value     |
|--------------------|---------------------------|----------------|
| Learning Rate      | 0.001, 0.0001              | **0.0001**     |
| Batch Size         | 64, 128, 256               | **64**         |
| Dropout Rate       | 0.3 – 0.8                  | **0.8**        |
| Epochs             | 20 → 50                    | **50**         |

**Additional Tuning**:
- Learning rate scheduler: reduces LR by 0.1 after 3-epoch plateau
- Cross-entropy loss used as the primary evaluation metric

---

## Results

**Best Configuration**:
- Activation Function: `ReLU`
- Learning Rate: `0.0001`
- Batch Size: `64`
- Dropout Rate: `0.8`
- Epochs: `50`

**Performance**:
- Accuracy: ~**90%**
- Final Loss: **0.1174**

**Notes**:
- Leaky ReLU sometimes outperformed ReLU, but lacked consistency.
- Sigmoid consistently underperformed (loss ~2.0).
- ReLU provided reliable convergence and performance.

## References
- Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). ImageNet Classification with Deep Convolutional Neural Networks.
- CIFAR-10 Dataset
- PyTorch Documentation

