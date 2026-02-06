# Deepfake Detection using VGG16 and MTCNN

![Python](https://img.shields.io/badge/Python-3.8+-blue)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.10+-orange)
![License](https://img.shields.io/badge/License-MIT-green)


**Topics:** computer-vision • deep-learning • transfer-learning • mtcnn-face-detection • vgg16-model • deepfake-detection • ai-ml

This repository presents a complete deepfake detection pipeline based on face detection using **MTCNN** and binary classification using a **VGG16 (transfer learning)** model. The project is designed with a clear, modular structure to ensure reproducibility, clarity, and professional presentation.

---

## Project Overview

Deepfake media poses a serious challenge in digital forensics and misinformation detection. This project focuses on identifying manipulated facial images by following a face-centric deep learning pipeline:

- Detecting faces from images using MTCNN  
- Cropping and preprocessing facial regions  
- Extracting deep features using a pretrained VGG16 network  
- Classifying images as **Real** or **Fake**

---

## Directory Structure



```
deepfake-detection-vgg16/
├── project/
│ ├── Epics.ipynb # Training, evaluation & inference notebook
│ ├── confusion_matrix.png # Test set confusion matrix
│ └── training_curves.png # Accuracy & loss curves
│
├── README.md # Project documentation
└── .gitignore # Ignored files (models, datasets, envs)
```
---


---

## Methodology / Pipeline

### 1. Face Detection (MTCNN)
Each input image is first processed using the MTCNN face detector to localize and extract the facial region. This ensures the model focuses only on relevant facial features and ignores background noise.

### 2. Face Cropping and Preprocessing
- Detected face regions are cropped  
- Images are resized to **224 × 224** pixels  
- Pixel values are normalized to the range **[0, 1]**

### 3. Feature Extraction (VGG16 – Transfer Learning)
A pretrained **VGG16** network (trained on ImageNet) is used as a feature extractor. The convolutional layers are frozen to preserve learned visual representations.

### 4. Classification Head
Extracted features are passed through:
- Fully connected layers  
- Batch normalization and dropout for regularization  
- A sigmoid output neuron for binary classification (**Real / Fake**)

### 5. Evaluation and Visualization
Model performance is analyzed using:
- Training and validation accuracy/loss curves  
- Confusion matrix on the test dataset  

---

## Dataset Description

The dataset consists of facial images divided into two classes:

- **Real:** Authentic, non-manipulated facial images  
- **Fake:** AI-generated or manipulated facial images  

### Dataset Organization
- Training data is used to learn model parameters  
- Validation data is used during training for monitoring performance  
- A held-out test dataset is used for final evaluation  

Each class is stored in a separate directory following a standard folder-based structure.

---

## Training Details

- **Backbone Model:** VGG16 (ImageNet pretrained)  
- **Input Size:** 224 × 224 × 3  
- **Optimizer:** Adam  
- **Loss Function:** Binary Cross-Entropy  
- **Batch Size:** 32  
- **Epochs:** 20  
- **Learning Rate:** 1e-4  

Dropout and batch normalization are applied in the classification head to reduce overfitting.

---

## Results and Performance

The trained VGG16-based deepfake detection model shows strong and stable performance on the test dataset.
![Training Curves](project/training_curves.png)

![Confusion Matrix](project/confusion_matrix.png)

![Sample Prediction](project/sample_prediction.png)


### Quantitative Results
- **Test Accuracy**: 99.37%
- **Loss Convergence**: Smooth convergence without signs of overfitting

### Confusion Matrix Summary
- Real images correctly classified: 199 / 200
- Fake images correctly classified: 198 / 200
- Very low false positive and false negative rates

### Observations
- The model generalizes well to unseen facial images
- Face-based preprocessing using MTCNN significantly improves classification accuracy
- Transfer learning with VGG16 provides robust feature representations for deepfake detection

---

## Future Work

- Extend the system to video-level deepfake detection
- Train and evaluate on larger benchmark datasets such as DFDC or FaceForensics++
- Experiment with more advanced architectures like EfficientNet or Vision Transformers
- Improve robustness against low-resolution and compressed images

---

## Conclusion

This project demonstrates that combining face-based preprocessing using MTCNN with transfer learning using VGG16 can achieve high accuracy for image-level deepfake detection. The results show strong generalization on unseen data, highlighting the effectiveness of deep feature extraction for detecting manipulated facial images.

---

## How to Run the Project

```

How to Run the Project
Step 1: Clone the repository
├── git clone https://github.com/MAYANK479/deepfake-detection-vgg16.git

└── cd deepfake-detection-vgg16

Step 2: Install required dependencies
└── pip install -r requirements.txt

Step 3: Open the notebook
└── project/Epics.ipynb

Step 4: Run the notebook cells sequentially
├── Model training
├── Evaluation on validation dataset
├── Evaluation on test dataset
└── Inference on unseen images
```
---

---

## Author

**Mayank Pandey**  
B.Tech Computer Science Engineering (AI/ML)  

This project demonstrates the application of face-based preprocessing with **MTCNN** and transfer learning using **VGG16** for high-accuracy deepfake detection.
