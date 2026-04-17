# One-Shot-Signature-Verification-Siamese-Networks-with-Grad-CAM-Explainability

## 📌 Overview

This project implements a **one-shot signature verification system** using a **Siamese Neural Network (SNN)**.
The model compares two signatures and predicts whether they are **genuine (same person)** or **forged (different person)**.

Instead of traditional classification, the model learns a **similarity function** using **contrastive loss and Euclidean distance**.

---

## 🚀 Key Features

* One-shot learning (no need for per-person training)
* Siamese Neural Network with shared weights
* Contrastive loss for similarity learning
* Memory-efficient pair generation (avoids RAM crash)
* Grad-CAM for model explainability
* End-to-end pipeline implementation

---

## 🗂️ Dataset Structure

```
train_data/
validation_data/
test_data/
```

Each folder contains:

* Genuine signatures
* Forged signatures (identified using 'forg' in folder name)

---

## 🧹 Preprocessing

* Converted all images to grayscale
* Resized images to **650 × 268**
* Normalized pixel values to **[0,1]**
* Final input shape: `(268, 650, 1)`

---

## 🔗 Pair Generation Strategy

To avoid memory overflow from generating all combinations, a controlled pairing strategy was used:

### Genuine pairs (label = 0)

(orig[i], orig[i+1])

### Forged pairs (label = 1)

(orig[i], forg[i])

---

## 📊 Dataset Size

| Dataset    | Number of Pairs |
| ---------- | --------------- |
| Train      | 559             |
| Validation | 111             |
| Test       | 127             |

---

## 🧠 Model Architecture

* Base CNN (shared weights):

  * Convolution + MaxPooling layers
  * Dense embedding (128-dimension)

* Distance Layer:

  * Euclidean distance between embeddings

* Loss Function:

  * Contrastive Loss

---

## ⚙️ Training Details

* Optimizer: Adam
* Batch size: 32
* Epochs: 10

---

## 📈 Results

| Metric              | Value     |
| ------------------- | --------- |
| Training Accuracy   | ~100%     |
| Validation Accuracy | ~85–88%   |
| Test Accuracy       | **85.8%** |

---

## 🔍 Grad-CAM Explainability

Grad-CAM was used to visualize model attention:

* Highlights important regions in signatures
* Shows where the model focuses during prediction
* Helps interpret decisions (genuine vs forged)

### Insight:

* Genuine signatures → consistent stroke attention
* Forged signatures → inconsistent or scattered focus

---

## 💡 Future Improvements
* Data augmentation
* Threshold tuning
* Deployment as web/app

---

## 🛠️ Tech Stack

* Python
* TensorFlow / Keras
* OpenCV
* NumPy
* Matplotlib

---
:

📘 Note

This project was developed for learning and educational purposes to understand:

Siamese Neural Networks
One-shot learning
Contrastive loss
Computer vision techniques
Explainable AI using Grad-CAM

The primary goal was to gain hands-on experience in building an end-to-end deep learning pipeline
## 🎯 Conclusion

This project demonstrates how Siamese Neural Networks can be used for **one-shot learning problems**, achieving **~85.8% accuracy** on unseen signature pairs with a computationally efficient approach and added explainability using Grad-CAM.



If you want, I can next:

✔ Add **images section for Grad-CAM outputs (looks very impressive on GitHub)**
✔ OR create a **perfect GitHub repo structure (folders + files naming)**
