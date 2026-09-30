# 🥔 Project: Potato Leaf Disease Classification using Deep Learning

## 📑 Project Overview
Early and accurate detection of crop diseases is critical for maximizing agricultural yield and ensuring food security. This project leverages advanced deep learning techniques to build an automated image classification system capable of identifying common potato leaf diseases. By analyzing leaf images, the system supports farmers and agronomists in early disease detection, enabling timely intervention and reducing crop loss.

---

## 🎯 Project Objectives
The primary goals of this project are to:
* **Develop a Robust Classification Pipeline:** Accurately classify potato leaf images into three distinct categories: **Healthy**, **Early Blight**, and **Late Blight**.
* **Architect a Baseline Model:** Build and train a custom Convolutional Neural Network (CNN) from scratch to learn visual features directly from the raw image data.
* **Implement Transfer Learning:** Leverage pre-trained architectures (VGG16 and MobileNetV2) to improve feature extraction and reduce training time.
* **Benchmark Model Performance:** Rigorously evaluate and compare the accuracy, precision, and computational efficiency of the custom CNN versus the transfer learning models.
* **Deploy for Inference:** Create a streamlined pipeline capable of predicting the disease category from a single, unseen leaf image in real-time.

---

## 🧩 Dataset & Preprocessing
The project utilizes a comprehensive potato leaf image dataset categorized into three classes:
* **Healthy:** Leaves with no visible signs of disease.
* **Early Blight:** Leaves exhibiting characteristic concentric rings of *Alternaria solani*.
* **Late Blight:** Leaves showing water-soaked lesions characteristic of *Phytophthora infestans*.

**Data Engineering & Augmentation:**
To ensure model robustness and prevent overfitting, the following preprocessing steps were implemented:
* **Resizing & Normalization:** Images were uniformly resized and pixel values were normalized to accelerate gradient descent convergence.
* **Data Augmentation:** Applied transformations (rotation, zoom, shear, and horizontal flips) to artificially expand the training dataset and improve the model's ability to generalize to real-world field conditions.

> *Note: The complete raw dataset is not included in this repository due to its large file size, but the data loading and preprocessing pipelines are fully documented.*

---

## ⚙️ Models Architected & Trained

### 1. Custom Convolutional Neural Network (CNN)
A baseline deep learning model was designed from scratch. This architecture utilizes multiple convolutional layers for hierarchical feature extraction, followed by max-pooling layers for spatial dimensionality reduction, and fully connected dense layers for final classification.

### 2. VGG16 (Transfer Learning)
The VGG16 architecture, pre-trained on the massive ImageNet dataset, was utilized to leverage its powerful, deeply learned feature extractors. The final classification head was replaced and fine-tuned specifically for the three potato disease classes.

### 3. MobileNetV2 (Lightweight Transfer Learning)
MobileNetV2 was implemented to explore the trade-off between computational efficiency and accuracy. Utilizing depthwise separable convolutions, this lightweight architecture is highly optimized for deployment on edge devices or mobile applications used directly in the field by farmers.

---

## 📊 Model Evaluation & Comparison

| Model Architecture | Test Accuracy | Key Characteristic |
| :--- | :--- | :--- |
| **Custom CNN** | 89.43% | Baseline performance; trained entirely from scratch. |
| **VGG16** | 87.13% | High parameter count; deeper feature extraction but prone to overfitting on this specific dataset. |
| **MobileNetV2** | **94.94%** | **Highest Accuracy**; optimal balance of performance and computational efficiency. |

**Key Takeaway:** 
**MobileNetV2** emerged as the superior model, achieving the highest test accuracy (94.94%). Its advanced architectural design (inverted residuals and linear bottlenecks) allowed it to capture complex leaf textures more effectively than the heavier VGG16 model, while remaining highly efficient for potential mobile deployment.

---

## 🛠 Tools & Technical Stack
* **Core Language:** Python
* **Deep Learning Frameworks:** TensorFlow, Keras
* **Data Manipulation:** NumPy, Pandas
* **Image Processing:** OpenCV
* **Data Visualization:** Matplotlib, Seaborn
* **Environment:** Google Colab (for GPU-accelerated training)

---

## 🔄 Project Workflow

```text
[ Raw Potato Leaf Images ]
          ↓
[ Data Preprocessing & Cleaning ]
          ↓
[ Image Resizing & Normalization ]
          ↓
[ Data Augmentation (Train Set) ]
          ↓
[ Model Architecture Design ]
   ├── Custom CNN
   ├── VGG16 (Transfer Learning)
   └── MobileNetV2 (Transfer Learning)
          ↓
[ Model Training & Hyperparameter Tuning ]
          ↓
[ Model Evaluation (Accuracy, Loss, Confusion Matrix) ]
          ↓
[ Final Model Selection (MobileNetV2) ]
          ↓
[ Inference: Disease Prediction on New Images ]
```

---

## 🚀 Future Roadmap & Enhancements
* **Edge Deployment:** Package the optimized MobileNetV2 model using TensorFlow Lite to deploy on a mobile app for offline, in-field disease detection.
* **Object Detection & Localization:** Transition from image classification to object detection (using YOLO or Faster R-CNN) to pinpoint the exact location of lesions on the leaf.
* **Drone Integration:** Adapt the pipeline to process aerial/drone imagery for large-scale, field-level crop health monitoring.
* **Explainable AI (XAI):** Implement Grad-CAM to generate heatmaps showing exactly which parts of the leaf the model is focusing on, increasing trust among agronomists.

---

## 📌 Conclusion
This project successfully demonstrates the application of deep learning and transfer learning in precision agriculture. By achieving nearly 95% accuracy with a lightweight model (MobileNetV2), this solution proves that highly accurate, automated crop disease detection is not only possible but also computationally feasible for real-world, on-the-ground deployment.
