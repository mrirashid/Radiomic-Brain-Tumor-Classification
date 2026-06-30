**Hybrid Deep Learning and Radiomic Shape Feature Fusion for Automated Brain Tumor Classification from MRI Images**

Published in: **2026 IEEE 2nd International Conference on Quantum Photonics, Artificial Intelligence, and Networking (QPAIN)**

Brain tumor diagnosis using Magnetic Resonance Imaging (MRI) is an important medical imaging task. Manual diagnosis can be time-consuming and challenging because brain tumors vary in shape, size, texture, location, and visual appearance. Automated classification systems can support radiologists by improving early diagnosis and clinical decision-making. This project proposes a hybrid deep learning framework for automated brain tumor classification using MRI images. The framework combines deep CNN-based image features with radiomic shape and texture-related features to improve classification performance.

The study evaluates the proposed framework on two tasks:

1. **Binary classification**
   - Tumor
   - No Tumor

2. **Multiclass classification**
   - Glioma
   - Meningioma
   - Pituitary Tumor
   - No Tumor

The proposed framework uses transfer learning, feature fusion, radiomic descriptors, data preprocessing, augmentation, and imbalance-aware training to improve robustness across both binary and multiclass MRI datasets.

## Dataset Links

### Binary Class Dataset

https://www.kaggle.com/datasets/navoneel/brain-mri-images-for-brain-tumor-detection

This dataset contains MRI images labeled as:

- Yes / Tumor
- No / No Tumor

### Multi Class Dataset

Brain Tumor MRI Dataset:

https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset

This dataset contains four classes:

- Glioma
- Meningioma
- Pituitary Tumor
- No Tumor

Paper Link: https://ieeexplore.ieee.org/abstract/document/11545798

## Main Contribution of the Paper

The main contribution of this paper is the development of a hybrid brain tumor classification framework that combines deep learning features with radiomic features for MRI-based tumor classification.

The key contributions are:

1. A unified hybrid deep learning framework for both binary and multiclass brain tumor classification.
2. Transfer learning-based feature extraction using EfficientNet and ResNet-based architectures.
3. Fusion of CNN image features with radiomic shape and texture-related features.
4. Adaptive gated feature fusion to combine deep features and handcrafted radiomic features more effectively.
5. Separate preprocessing strategies for binary and multiclass MRI datasets.
6. Data augmentation and class imbalance handling to improve generalization.
7. Two-phase training strategy using frozen-backbone training followed by fine-tuning.
8. Evaluation using accuracy, precision, recall, F1-score, confusion matrix, and training-validation curves.
9. Experimental comparison showing that feature fusion improves performance compared with baseline CNN models.

## My Contribution to This Paper

### Research Idea and Problem Formulation

I contributed to the idea of developing an automated MRI-based brain tumor classification system using hybrid feature fusion. The main research problem was to improve brain tumor classification by combining deep CNN features with radiomic features instead of relying only on standard CNN-based classification.

I helped define the two major classification tasks:

- Binary tumor detection
- Multiclass tumor classification

The objective was to design a framework that could work effectively on both simple tumor detection and more complex tumor-type classification.

### Model Design and Implementation

I contributed to designing and implementing the hybrid deep learning framework. The model used transfer learning-based CNN feature extraction and combined these features with radiomic feature representations.

For the binary classification task, the framework used deep features from a ResNet-based model and fused them with radiomic features through a gated fusion mechanism.

For the multiclass classification task, EfficientNet-based deep features were combined with auxiliary radiomic descriptors and passed through dense classification layers for four-class prediction.

The implementation included:

- CNN backbone integration
- Global average pooling
- Global max pooling
- Radiomic feature extraction
- Feature standardization
- Feature projection
- Gated fusion
- Dense classification head
- Binary and multiclass output layers

### Dataset Processing

I contributed to preparing and preprocessing both datasets.

For the binary dataset, the preprocessing steps included:

- Loading MRI images
- Converting grayscale images into RGB format
- Resizing images to 224 × 224 pixels
- Assigning binary labels
- Splitting the dataset into training, validation, and testing sets
- Applying EfficientNet-style normalization

For the multiclass dataset, the preprocessing steps included:

- Loading MRI images in RGB format
- Cropping unnecessary background regions
- Padding images to preserve square shape
- Resizing images to 224 × 224 pixels
- Normalizing image intensity
- Applying class weights to handle imbalance
- Preparing auxiliary radiomic feature vectors

### Data Augmentation

I contributed to applying augmentation strategies to improve model generalization.

For the binary dataset, test-time augmentation was used during evaluation, including:

- Rotation
- Horizontal flipping
- Averaging predictions

For the multiclass dataset, augmentation was applied only to training images, including:

- Random flipping
- Rotation
- Zoom
- Contrast adjustment

Validation and test data were kept unchanged to ensure fair evaluation.

### Radiomic Feature Fusion

I contributed to the radiomic feature fusion part of the study. Radiomic features were used to provide additional information beyond CNN image features.

The radiomic feature pipeline included:

- Image resizing
- Intensity normalization
- First-order statistical feature extraction
- Texture-related feature extraction
- Feature standardization using z-score normalization
- Projection into a compact embedding space
- Fusion with deep CNN features

The adaptive gated fusion mechanism helped the model learn how much importance should be given to CNN features and radiomic features during classification.

### Training and Experiments

I contributed to the model training and experimental setup.

The training strategy included two stages:

1. Frozen-backbone training
   - The pretrained CNN backbone was frozen.
   - Only the classification head was trained.

2. Fine-tuning
   - Upper layers of the backbone were unfrozen.
   - The model was trained using a lower learning rate.
   - Early stopping and learning rate scheduling were used.

For the multiclass task, class weights were used to reduce the effect of class imbalance.

### Result Analysis

I contributed to analyzing the experimental results for both binary and multiclass classification.

The binary classification model achieved:

- Accuracy: 94%
- Tumor recall: 1.00
- Strong tumor detection performance
- No false negatives in the confusion matrix

The multiclass classification model achieved:

- Accuracy: 84.5%
- Strong performance for no-tumor and pituitary tumor classes
- Balanced glioma classification
- Some confusion between glioma and meningioma due to visual similarity

The ablation study showed that adaptive gated fusion improved binary classification accuracy from 88% to 94%, confirming the importance of combining deep CNN features with radiomic features.


## Results Summary

| Task | Dataset | Model Type | Accuracy |
|---|---|---|---|
| Binary Classification | Brain MRI Tumor Detection Dataset | Hybrid ResNet + Radiomic Gated Fusion | 94% |
| Multiclass Classification | Brain Tumor MRI Dataset | Hybrid EfficientNet + Radiomic Fusion | 84.5% |

## Ablation Study

An ablation study was conducted to evaluate the effect of the proposed fusion strategy.

| Model Setting | Task | Accuracy |
|---|---|---|
| Baseline EfficientNetB0 with radiomic features | Binary Classification | 88% |
| Proposed adaptive gated fusion model | Binary Classification | 94% |
| Proposed hybrid EfficientNet model | Multiclass Classification | 84.5% |

The improvement from 88% to 94% in binary classification shows that adaptive feature fusion improves the model’s discriminative ability.

