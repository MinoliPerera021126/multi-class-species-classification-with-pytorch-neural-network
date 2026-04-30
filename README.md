# 🌸 PyTorch Flower Classification

A comprehensive PyTorch project for classifying images of flowers into five distinct categories. 

This project is designed to be easily runnable in **Google Colab** and demonstrates fundamental deep learning concepts, including custom CNN architectures, data augmentation, transfer learning, and model evaluation.

## 📊 Dataset
This project uses the [Flowers Recognition dataset](https://www.kaggle.com/datasets/alxmamaev/flowers-recognition) by Alexander Mamaev, available on Kaggle. 

The dataset contains approximately 4,300 images across five types of flowers:
* 🌼 Daisy
* 🌾 Dandelion
* 🌹 Rose
* 🌻 Sunflower
* 🌷 Tulip

*Note: The dataset is downloaded dynamically during runtime via the Kaggle API and is not included in this repository to keep it lightweight.*

## 🚀 How to Run

The easiest way to run this project is using Google Colab.

1. **Get your Kaggle API Key:**
   * Go to your [Kaggle Account settings](https://www.kaggle.com/settings).
   * Scroll down to the **API** section and click **Create New Token**.
   * This will download a `kaggle.json` file to your computer.

2. **Run in Google Colab:**
   * Open the `.ipynb` notebook in Google Colab.
   * Make sure you are using a GPU for faster training: Go to `Runtime` > `Change runtime type` > Select `T4 GPU`.
   * Run the first cell. When prompted, upload the `kaggle.json` file you downloaded in Step 1.
   * Run the remaining cells sequentially to train the models, visualize evaluations, and test inference on new images.

## 🧠 Model Architectures
This project implements and compares two different approaches to image classification:

### 1. Custom CNN (From Scratch)
A Convolutional Neural Network built entirely from scratch using `torch.nn`.
* **Feature Extractor:** 4 Convolutional blocks, where each block consists of `Conv2d` -> `BatchNorm2d` -> `ReLU` -> `MaxPool2d`.
* **Pooling:** Global Average Pooling (`AdaptiveAvgPool2d`) to collapse spatial dimensions.
* **Classifier:** 3 Fully Connected (`Linear`) layers with Dropout (`p=0.4` and `p=0.3`) to prevent overfitting.

### 2. Transfer Learning (ResNet-18)
A pre-trained ResNet-18 model adapted for our 5-class problem.
* Uses weights pre-trained on ImageNet (`IMAGENET1K_V1`).
* Replaces the final fully connected layer (`fc`) with a custom sequence: `Linear` -> `ReLU` -> `Dropout` -> `Linear` to output 5 classes.
* The entire backbone is fine-tuned for optimal accuracy.

## ⚙️ Training Details & Data Augmentation
To prevent overfitting on a relatively small dataset, the training pipeline applies extensive data augmentation:
* Random resized cropping, horizontal/vertical flipping, color jitter (brightness, contrast, saturation, hue), and random rotation up to ±30 degrees.
* Inputs are normalized using standard ImageNet statistics.

**Hyperparameters:**
* **Optimizer:** Adam with weight decay (1e-4) for L2 regularization.
* **Learning Rate:** 3e-4 for the Custom CNN and 1e-4 for fine-tuning ResNet-18.
* **Scheduler:** `ReduceLROnPlateau` halves the learning rate if validation loss plateaus for 3 epochs.
* **Loss Function:** Cross-Entropy Loss.

## 🛠️ Technologies Used
* **Python**
* **PyTorch** (`torch`, `torch.nn`, `torch.optim`)
* **Torchvision** (`datasets`, `transforms`, `models`, `utils`)
* **Matplotlib & Seaborn** (for visualizing data distributions, augmented images, and confusion matrices)
* **Scikit-learn** (for generating classification reports and confusion matrices)
* **PIL (Pillow)** (for image loading and processing)
* **Kaggle API** (for seamless data downloading)
