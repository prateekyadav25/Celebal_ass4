# 🧠 CIFAR-10 Image Classification: ANN vs. CNN

## 📌 Project Overview
This project focuses on building and comparing image classification models using the **CIFAR-10 dataset**. The primary objective is to evaluate the performance differences between an **Artificial Neural Network (ANN)** and a **Convolutional Neural Network (CNN)**, highlighting why CNNs are the preferred architecture for computer vision tasks. The project also explores the impact of various training strategies, including Dropout, Batch Normalization, and Data Augmentation.

## 📦 Dataset
We use the **CIFAR-10** dataset, which consists of **60,000 color images** (32x32 pixels, 3 channels). 
- **Training Set:** 50,000 images
- **Test Set:** 10,000 images
- **Classes (10):** Airplane, Automobile, Bird, Cat, Deer, Dog, Frog, Horse, Ship, Truck.

### Preprocessing
- Pixel values are normalized from the standard **0–255 range to 0–1** to ensure stable and faster training.
- For the ANN model, the 32x32x3 images are flattened into 1D vectors of size 3072.

## ⚙️ Models & Architecture

### 1. Artificial Neural Network (ANN)
The ANN treats images as flat vectors, inherently losing spatial features (edges, textures, shapes). 
- **Architecture:** Multiple `Dense` layers with `relu` activation and `Dropout` to prevent overfitting.
- **Limitation:** Increasing complexity (adding more dense layers) does not significantly improve performance because spatial relationships between pixels are ignored.

### 2. Convolutional Neural Network (CNN)
The CNN preserves spatial relationships by using convolution and pooling operations, allowing for hierarchical feature extraction.
- **Architecture:** 
  - Multiple `Conv2D` layers for feature extraction.
  - `MaxPooling2D` for downsampling.
  - `BatchNormalization` for training stability.
  - `Flatten` followed by `Dense` layers and `Dropout` for final classification.

### 3. CNN with Data Augmentation
To further improve generalization and reduce overfitting, a data augmentation pipeline was integrated.
- **Transformations:** `RandomFlip` (horizontal), `RandomRotation`, and `RandomZoom`.

## 📊 Results & Comparison

| Model | Test Accuracy |
| :--- | :--- |
| **ANN** | ~ 41.22% |
| **CNN** | ~ 69.64% |
| **Augmented CNN** | ~ 48.34% |

*(Note: Accuracies are based on the training run over 20 epochs with EarlyStopping)*

**Key Observations:**
- **CNN significantly outperformed the ANN** (approx. 30% higher validation/test accuracy).
- Convolution layers successfully extracted meaningful image features, proving that model architecture is more critical than simply increasing depth for image tasks.
- **Batch Normalization** and **Dropout** successfully stabilized training and reduced overfitting.
- **EarlyStopping** proved useful in preventing unnecessary training by restoring the best weights.

## ✅ Conclusion
- **ANN works** but fundamentally ignores the 2D structure of image data.
- **CNN is highly effective** because it extracts and learns spatial features.
- Implementing robust **training strategies** (dropout, batch norm, augmentation, early stopping) is crucial for building robust deep learning models.
- This project serves as a strong foundational exercise for understanding the mechanics of computer vision and deep learning.
