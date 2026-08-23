# Malaria Parasite Detection Using CNN and Transfer Learning

## 📌 Overview

This project uses Deep Learning to classify malaria blood smear cell images into:

* **Parasitized**
* **Uninfected**

### Models Used

1. **CNN From Scratch**
2. **MobileNetV2 using Transfer Learning and Fine-Tuning**

---

## 🎯 Objectives

* Detect malaria parasites from cell images.
* Implement and compare CNN and MobileNetV2.
* Evaluate Accuracy, Precision, Recall, and F1-Score.

---

## 📊 Dataset

**NIH/NLM Malaria Cell Images Dataset**

* Total dataset: **27,558 images**
* Project subset: **4,000 balanced images**
* 2,000 Parasitized
* 2,000 Uninfected

Dataset:
https://data.lhncbc.nlm.nih.gov/public/Malaria/cell_images.zip

---

## ⚙️ Methodology

```text
Dataset
   ↓
Preprocessing
   ↓
Image Resizing (128 × 128)
   ↓
Normalization + Augmentation
   ↓
70% Training / 15% Validation / 15% Testing
   ↓
CNN From Scratch + MobileNetV2
   ↓
Fine-Tuning
   ↓
Performance Evaluation
```

---

## 🧠 Models

### CNN From Scratch

A custom CNN that learns features directly from the malaria cell images.

### MobileNetV2

A pretrained MobileNetV2 model using ImageNet weights, followed by transfer learning and fine-tuning.

---

## 📈 Results

| Model                |   Accuracy |  Precision |     Recall |   F1-Score |
| -------------------- | ---------: | ---------: | ---------: | ---------: |
| **CNN From Scratch** | **95.83%** | **95.08%** |     96.67% | **95.87%** |
| MobileNetV2          |     84.50% |     77.45% | **97.33%** |     86.26% |

**CNN From Scratch achieved the best overall performance**, while **MobileNetV2 achieved the highest recall**.

---

## 📚 Research Paper

**Rajaraman et al. (2018)**
*Pre-trained convolutional neural networks as feature extractors toward improved malaria parasite detection in thin blood smear images.*

DOI: https://doi.org/10.7717/peerj.4568

This project is inspired by the research paper but is not an exact reproduction because it uses a 4,000-image subset and MobileNetV2.

---

## 🛠️ Technologies Used

* Python
* TensorFlow / Keras
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Seaborn
* Google Colab

---

## 🚀 How to Run

1. Open the `.ipynb` file in Google Colab.
2. Enable GPU runtime if available.
3. Run all cells sequentially.
4. Train and evaluate both models.

---

## ⚠️ Limitations

* Only 4,000 images were used.
* Results may vary with different training settings.
* This is an educational implementation, not an exact research paper reproduction.

---

## ✅ Conclusion

This project demonstrates the use of CNN and Transfer Learning for automated malaria parasite detection. The **CNN From Scratch performed better overall with 95.83% accuracy**, while **MobileNetV2 achieved the highest recall of 97.33%**.
