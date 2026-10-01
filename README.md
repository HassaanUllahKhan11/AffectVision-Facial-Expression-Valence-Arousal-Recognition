# AffectVision: Facial Expression & Valence-Arousal Recognition

A deep learning project for **facial affect recognition** using transfer learning with **ResNet50** and **MobileNetV2**.

The project focuses on **8-class facial expression classification** and explores **continuous Valence-Arousal prediction** for affective computing applications.

**Author:** Hassaan Ullah Khan
**Student ID:** 21i-1695

---

## Overview

AffectVision compares two CNN architectures for facial affect recognition:

* **ResNet50** — a deep, high-capacity CNN used as the primary baseline.
* **MobileNetV2** — a lightweight CNN designed with computational efficiency and deployment in mind.

The project uses **ImageNet-pretrained models** and evaluates their performance using multiple classification and continuous affect metrics.

### Main Objectives

* Perform facial expression classification across **8 expression categories**
* Compare ResNet50 and MobileNetV2
* Apply transfer learning using ImageNet pretrained weights
* Evaluate classification performance using Accuracy, F1, Cohen's Kappa, and ROC-AUC
* Evaluate continuous affect prediction using RMSE, CORR, SAGR, and CCC
* Analyze training behavior and qualitative failure cases
* Examine the trade-off between model accuracy and computational efficiency

---

## Models

### ResNet50

ResNet50 is used as the high-capacity CNN baseline.

**Characteristics:**

* Deep residual architecture
* ImageNet pretrained weights
* Strong image classification capability
* Higher computational requirements
* Higher classification accuracy in the experiment

### MobileNetV2

MobileNetV2 is used as a lightweight alternative.

**Characteristics:**

* Lightweight CNN architecture
* ImageNet pretrained weights
* Faster training
* Lower computational requirements
* More suitable for constrained or real-time applications

---

## Transfer Learning

Both ResNet50 and MobileNetV2 are initialized using **pretrained ImageNet weights**.

Their original classification layers are adapted for the project's facial affect recognition task.

Transfer learning allows the models to take advantage of previously learned visual features and helps accelerate convergence when working with limited training data.

---

## Dataset

The project uses a facial affect dataset containing approximately **3,999 face images** with corresponding NumPy annotations.

The annotations contain:

* Expression labels
* Valence values
* Arousal values

Samples with uncertain Valence/Arousal annotations are excluded during dataset preparation.

The dataset itself is **not included in this GitHub repository**.

---

## Model Configuration

| Parameter              | Value                |
| ---------------------- | -------------------- |
| Input Size             | **160 × 160 RGB**    |
| Expression Classes     | **8**                |
| Epochs                 | **15**               |
| Batch Size             | **12**               |
| Optimizer              | **Adam**             |
| Learning Rate          | **3 × 10⁻⁴**         |
| Loss                   | **CrossEntropyLoss** |
| Train/Validation Split | **90% / 10%**        |
| Pretrained Weights     | **ImageNet**         |

---

## Data Preprocessing

The input images are resized to:

```text
160 × 160 RGB
```

Training preprocessing includes:

* Random horizontal flipping
* Brightness adjustment
* Contrast adjustment
* Tensor conversion
* ImageNet normalization

Validation images are resized and normalized without random augmentation.

---

## Evaluation Metrics

### Classification Metrics

The project evaluates facial expression classification using:

* **Accuracy**
* **F1-Score**
* **Cohen's Kappa**
* **ROC-AUC**

These metrics provide different perspectives on classification performance.

### Continuous Affect Metrics

For Valence-Arousal prediction, the project considers:

* **RMSE** — Root Mean Squared Error
* **CORR** — Correlation
* **SAGR** — Sign Agreement Rate
* **CCC** — Concordance Correlation Coefficient

CCC is particularly relevant for continuous affect prediction because it considers both correlation and agreement between predicted and ground-truth values.

---

## Results

The baseline experiments produced the following approximate classification results:

| Model           | Accuracy | Training Time | Characteristics                        |
| --------------- | -------: | ------------- | -------------------------------------- |
| **ResNet50**    | **~82%** | Slower        | More accurate, computationally heavier |
| **MobileNetV2** | **~79%** | Faster        | Lightweight and efficient              |

### ResNet50

ResNet50 achieved approximately **82% accuracy**.

It provided the stronger classification performance but required more computational resources.

### MobileNetV2

MobileNetV2 achieved approximately **79% accuracy**.

Although its accuracy was slightly lower, it trained faster and offered a more lightweight architecture.

### Overall Observation

The experiment demonstrates a practical trade-off between:

**Classification Performance ↔ Computational Efficiency**

ResNet50 favors higher classification performance, while MobileNetV2 favors efficiency and deployment suitability.

---

## Training Analysis

The project includes training visualizations showing:

* Training Loss vs. Epochs
* Validation Accuracy vs. Epochs
* Comparison between ResNet50 and MobileNetV2

The observed training behavior shows decreasing loss and improving validation performance across training.

MobileNetV2 converges faster, while ResNet50 achieves higher final classification accuracy.

---

## Qualitative Analysis

The project also examines correctly and incorrectly classified facial expressions.

### Correct Predictions

The models perform well when facial expressions are clear and visually distinctive.

Examples include expressions such as:

* Happiness
* Surprise
* Other clearly expressed emotions

### Incorrect Predictions

Classification becomes more difficult in cases involving:

* Ambiguous expressions
* Low-light conditions
* Occluded faces
* Noisy or uncertain images

These failure cases demonstrate the challenges of facial affect recognition in uncontrolled real-world conditions.

---

## Technologies

* **Python**
* **PyTorch**
* **Torchvision**
* **NumPy**
* **Scikit-learn**
* **Matplotlib**
* **Pillow**
* **tqdm**

---

## Repository Contents

The repository intentionally contains only the project files required to present the implementation and results.

```text
AffectVision/
│
├── AffectVision.ipynb
└── README.md
```

> **Note:** The original dataset is not included in the repository due to its size/data distribution considerations. The notebook contains the implementation and configuration used for the experiments.

---

## How to View the Project

The easiest way to explore the project is to open:

```text
AffectVision.ipynb
```

The notebook contains the implementation covering:

1. Environment and library setup
2. Configuration
3. Dataset loading and preprocessing
4. Evaluation metrics
5. ResNet50 and MobileNetV2 architectures
6. Training
7. Model evaluation
8. Training visualizations
9. Final results

---

## Limitations

* The experiments were conducted using the available facial affect dataset.
* Facial expressions can be ambiguous and difficult to classify consistently.
* Poor lighting and occlusion can negatively affect predictions.
* Real-world facial images contain substantial visual variation.
* The reported results correspond to this specific experimental setup.

---

## Future Improvements

Potential extensions include:

* GPU-based training
* Hyperparameter optimization
* More extensive data augmentation
* Confusion matrix analysis
* Per-class performance analysis
* Improved continuous Valence-Arousal evaluation
* Real-time webcam-based facial expression recognition
* MobileNetV2 deployment for edge devices
* Further optimization for real-world affect recognition

---

## Author

**Hassaan Ullah Khan**
**21i-1695**

**AffectVision — Multi-Task Facial Expression & Valence-Arousal Recognition**
