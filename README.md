# 🐶🐱 Dog vs Cat Classification using ResNet50 (Transfer Learning) 

## Project Overview  
This project focuses on binary image classification to distinguish between dogs and cats using ResNet50 with transfer learning. The model was trained with advanced augmentation, regularization, and class weight adjustments to achieve high accuracy and robust generalization. The final model was deployed using Streamlit for real-time predictions.

---

## Dataset  
- **Source:** [Kaggle - Dogs vs. Cats](https://www.kaggle.com/competitions/dogs-vs-cats)
- **Dataset Split:**
  -  **Training:**  17,500 images
  -  **Validation:** 7,500 images
  -  **Testing:** 12,500 images
- Labels extracted from filenames using os.path.basename()[0]. 
- **Encoded:**
  -  Dog -> 1
  -  Cat -> 0
---

## Data Preprocessing  
- Used **ImageDataGenerator** for
  -  Rescaling pixel values
  -  Data Augmentation (rotation,flips)
- Computed Class weights.  

---

## Model Architechure  
- Base Model: ResNet50 (ImageNet pre-trained, input shape = (112,112,3)  
- Trainable layers: last 25 layers (out of 175 total)
- Custom layers 
  - GlobalAveragePooling2D()  
  - Dropout(0.5)
  - Dense layer with 1 neuron with "sigmoid" activation  
- Regularization
  -  Early stopping
  -  ReduceLROnPlateau
  -  Class weights
## Training
  -  Epochs: 50
  -  Batch size: based on GPU memory
  -  Optimizer: Adam
  -  Loss: Binary Crossentropy

---

## Results 

**Classification Report:**  

| Class | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| 0 (Cat) | 0.98 | 0.97 | 0.97 | 3812 |
| 1 (Dog)    | 0.97 | 0.98 | 0.97 | 3688 |

- **Accuracy:** 0.97  
- **ROC-AUC:** 0.996  
---

## Deployment (Streamlit)
- Built a Streamlit app (app.py) for image-classification
- User can upload an image -> model predicts whether it’s a Dog 🐶 or Cat 🐱.
- Run locally using
 `streamlit run app.py`
---
## Author  
**Abhinay Kalavakuri**

