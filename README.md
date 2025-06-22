# Comparative Analysis of Representation Methods for Image Classification on MNIST

## 🧠 Project Overview

This project investigates the impact of different feature representation techniques on image classification performance using the **MNIST** dataset. We compare four approaches:

- Raw Pixel Data
- Principal Component Analysis (PCA)
- Kernel PCA (kPCA)
- Isomap

A consistent **Support Vector Machine (SVM)** with an **RBF kernel** is used as the classifier for all experiments to isolate the effect of data representation.

---

## 📁 Dataset

- **Source**: [MNIST Handwritten Digits](http://yann.lecun.com/exdb/mnist/)
- **Image size**: 28 × 28 pixels (flattened to 784 features)
- **Splits**:
  - Training: 16,000 samples
  - Validation: 4,000 samples
  - Test: 5,000 samples
- **Preprocessing**: Min-max normalization to scale pixel values to [0, 1]

---

## 🧮 Methods Compared

### 1. Raw Pixel Data
Used as the baseline without any transformation.  

### 2. Principal Component Analysis (PCA)
Linear dimensionality reduction.  
- Retained 95% variance → 153 components

### 3. Kernel PCA (kPCA)
Nonlinear dimensionality reduction using RBF kernel (γ = 0.04).  
- 100 components used  

### 4. Isomap
Manifold learning technique preserving geodesic distances.  
- 30 components, 10 neighbors

---

## 🧪 Classifier: Support Vector Machine (SVM)
- Kernel: RBF
- Metrics:
  - **Accuracy**
  - **Macro-averaged F1 Score**

---

## 📊 Results Summary

| Representation | Test Accuracy | Macro F1 Score |
|----------------|---------------|----------------|
| **PCA**        | **96.12%**    | **0.9615**     |
| Raw Pixels     | 96.00%        | 0.9601         |
| kPCA           | 95.03%        | 0.9512         |
| Isomap         | 94.04%        | 0.9413         |

---

## 📈 Performance Insights

- **PCA** offered the best performance, balancing dimensionality reduction and accuracy.
- **Raw data** was nearly as effective but computationally heavier.
- **kPCA** captured nonlinear patterns but may have overfit.
- **Isomap** underperformed due to its sensitivity to noise and neighborhood construction.

---

## 🖼 Visual Analysis

- **Explained variance plot**: PCA retained >95% variance in just 153 components.
- **Confusion matrices**: PCA yielded the most uniform performance across digits.
- **Performance charts**: PCA consistently leads in accuracy and F1 score.

---

## ✅ Conclusion

Dimensionality reduction can enhance classification efficiency without major accuracy trade-offs. PCA stands out as the most balanced method. Future work could explore other nonlinear techniques like t-SNE or UMAP for visualization and classification.

---

## 📚 References

- LeCun, Y. et al. *The MNIST Database*
- Scikit-learn Documentation: [`PCA`](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html), [`KernelPCA`](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.KernelPCA.html), [`Isomap`](https://scikit-learn.org/stable/modules/generated/sklearn.manifold.Isomap.html)
