## Dataset

* **Dataset:** [Caltech-101](http://www.vision.caltech.edu/Image_Datasets/Caltech101/)
* **Classes:** 102 (101 object categories + background class)
* **Total Images:** 9,145
* Images are split into **train, validation, and test sets** while preserving class distribution.

  * Example: If splitting 10%, each class contributes 10% of its images.

---

## Data Splitting

Two approaches are implemented for splitting the dataset:

1. **Copy Method** – Images are physically copied into separate `train/`, `val/`, and `test/` folders.
2. **DataFrame Method** – Image paths and labels are stored in a DataFrame, avoiding duplication and saving memory.

---

## Data Loader

The data loader generates **pairs of images**:

* **Same class → Label = 0**
* **Different class → Label = 1**

### Data Imbalance Issue

Naively sampling results in too many **label = 1 (dissimilar pairs)**.
To address this:

* Balanced batches are created with an equal number of similar and dissimilar pairs.
* Number of pairs: **750 – 1500** (configurable).
* Implemented using **PyTorch’s Dataset and DataLoader** utilities.

---

## Data Preprocessing

* **Resizing & Augmentations** – Applied during preprocessing.
* **Normalization** – Standard ImageNet normalization applied:

  * Mean = `[0.485, 0.456, 0.406]`
  * Std = `[0.229, 0.224, 0.225]`

---

Developed by **\[Your Name]** as part of an assignment project on image similarity learning with PyTorch.

---

👉 Would you like me to also add a **diagram of how pairs are generated (same vs different class)** to make the README more visual and beginner-friendly?
