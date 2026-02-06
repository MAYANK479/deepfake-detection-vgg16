# Deepfake Detection using VGG16 and MTCNN

This repository contains a complete deepfake detection pipeline based on
face detection using **MTCNN** and binary classification using a
**VGG16 (transfer learning)** model.

The project is structured in a modular and professional manner, separating
training, evaluation, inference, and visualization components for clarity,
reproducibility, and scalability.

---

## Project Overview

Deepfake media poses a serious threat in terms of misinformation and digital
forensics. This project focuses on detecting manipulated facial images by:

1. Detecting faces from images using MTCNN
2. Cropping and preprocessing facial regions
3. Extracting deep features using a pretrained VGG16 network
4. Classifying images as **Real** or **Fake**

---

## Directory Structure


## Directory Structure

```
deepfake-detection-vgg16/
├── project/
│   ├── Epics.ipynb                # Training, evaluation & inference notebook
│   ├── confusion_matrix.png       # Test set confusion matrix
│   └── training_curves.png        # Accuracy & loss curves
│
├── README.md                      # Project documentation
└── .gitignore                     # Ignored files (models, datasets, envs)
```
---

## Methodology / Pipeline

The complete deepfake detection pipeline followed in this project is described below:

1. **Face Detection (MTCNN)**  
   Each input image is first processed using the MTCNN face detector to locate and extract the facial region.  
   This step ensures that the model focuses only on relevant facial features rather than background noise.

2. **Face Cropping and Preprocessing**  
   - Detected face regions are cropped  
   - Images are resized to **224 × 224** pixels  
   - Pixel values are normalized to the range **[0, 1]**

3. **Feature Extraction (VGG16 – Transfer Learning)**  
   A pretrained **VGG16** network (trained on ImageNet) is used as a feature extractor.  
   The convolutional layers are frozen to retain learned visual representations.

4. **Classification Head**  
   The extracted features are passed through:
   - Fully connected layers  
   - Batch normalization and dropout for regularization  
   - A sigmoid output neuron for binary classification (**Real / Fake**)

5. **Evaluation and Visualization**  
   Model performance is evaluated using:
   - Accuracy and loss curves  
   - Confusion matrix on the test dataset
  ---

## Dataset Description

The dataset used in this project consists of facial images categorized into two classes:

- **Real**: Authentic, non-manipulated facial images  
- **Fake**: AI-generated or manipulated facial images

### Dataset Organization

- Training data is used to learn model parameters  
- Training data is used to learn model parameters  
- A held-out test dataset is used for validation during training and final performance evaluation


All datasets follow a directory-based structure where each class is stored in a separate folder.
---

## Training Details

- **Backbone Model**: VGG16 (ImageNet pretrained)  
- **Input Size**: 224 × 224 × 3  
- **Optimizer**: Adam  
- **Loss Function**: Binary Cross-Entropy  
- **Batch Size**: 32  
- The model was trained for 20 epochs using the Adam optimizer with a learning rate of 1e-4.


To prevent overfitting, dropout and batch normalization layers are used in the classification head.
---

## Results and Performance

The trained model demonstrates strong performance on the test dataset.

### Key Results
- High classification accuracy on unseen data  
- Stable convergence during training  
- Clear separation between real and fake classes

### Visual Results
- **Training Curves**: Show accuracy and loss trends across epochs  
- **Confusion Matrix**: Illustrates correct and incorrect classifications for both classes

These results indicate that transfer learning with VGG16 combined with face-based preprocessing is effective for deepfake detection.
---

## How to Run the Project

1. Clone the repository
   ```bash
   git clone https://github.com/MAYANK479/deepfake-detection-vgg16.git
   cd deepfake-detection-vgg16
2. Install required dependencies

pip install -r requirements.txt


3. Open the notebook

project/Epics.ipynb


4. Run the cells sequentially for:

Model training

Evaluation on validation and test sets

Inference on unseen images

## Author

**Mayank Pandey**  
B.Tech Computer Science Engineering (AI/ML)  
Project: Deepfake Detection using Deep Learning
