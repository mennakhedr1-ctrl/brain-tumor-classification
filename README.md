# brain-tumor-classification
Brain tumor classification from MRI scans using VGG19 transfer learning (98% accuracy).
## Overview
This project fine-tunes a pretrained VGG19 network to detect brain tumors in MRI images. Data augmentation and early stopping were used to reduce overfitting and stabilize training. Because false negatives are costly in a medical setting, the model was evaluated with precision, recall, F1-score, and AUC-ROC, not accuracy alone.

## Approach
1. Loaded the MRI dataset (train / validation / test splits)
2. Applied data augmentation to the training set only (flips, rotation, shifts, shear)
3. Stage 1: froze VGG19 and trained a custom classifier head
4. Stage 2: unfroze the last convolutional layers and fine-tuned
5. Trained with early stopping and learning-rate reduction on plateau
6. Evaluated on the held-out test set

## Results (test set)
| Class | Precision | Recall | F1-score | Support |
|-------|-----------|--------|----------|---------|
| Nontumorous | 0.99 | 0.99 | 0.99 | 900 |
| Tumorous | 0.99 | 0.99 | 0.99 | 900 |

| Metric | Score |
|--------|-------|
| Accuracy | 99.39% |
| AUC-ROC | 0.9996 |

## Tech Stack
Python, TensorFlow, Keras, Scikit-learn, NumPy, Matplotlib
