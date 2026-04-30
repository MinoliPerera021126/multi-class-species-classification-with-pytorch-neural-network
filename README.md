# 🌸 PyTorch Flower Classification

A beginner-friendly Convolutional Neural Network (CNN) built with PyTorch to classify images of flowers into five distinct categories. 

This project is designed to be easily runnable in **Google Colab** and demonstrates fundamental deep learning concepts, including custom CNN architectures, data transformations, and model evaluation.

## 📊 Dataset
This project uses the [Flowers Recognition dataset](https://www.kaggle.com/datasets/alxmamaev/flowers-recognition) by Alexander Mamaev, available on Kaggle. 

The dataset contains images of five types of flowers:
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
   * Run the remaining cells sequentially to train and test the model!

## 🧠 Model Architecture
The model uses a custom Convolutional Neural Network (CNN) built from scratch using `torch.nn`. 

**Architecture summary:**
* 3 Convolutional blocks (Conv2d -> ReLU -> MaxPool2d) for feature extraction.
* 1 Flatten layer.
* 2 Fully Connected (Linear) layers for final classification.
* Optimizer: Adam (`lr=0.001`)
* Loss Function: Cross-Entropy Loss

## 🛠️ Technologies Used
* **Python**
* **PyTorch** (`torch`, `torchvision`)
* **Matplotlib** (for visualizing predictions)
* **Kaggle API** (for seamless data downloading)
