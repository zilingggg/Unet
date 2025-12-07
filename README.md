# Unet
the difference dataset in Unet 
(This project received assistance from Chatgpt)

##  UNet for Mammogram Calcification Segmentation

### Model Setup
- Image size: **512×512**
- Input channels: **1 (Grayscale)**
- Loss function: **Dice Loss + Focal Loss**
- Metrics: **Dice Coefficient**
- Optimizer: **Adam (lr=1e-4)**
- Epochs: **20**
- Batch size: **4**
- Augmentation: horizontal flip, rotation, brightness shift

### Dataset
- Real mammography dataset  
- Ground truth masks are small area lesions  
- Image–mask ratio is extremely imbalanced → segmentation difficulty high

- ### Result
- Val/Test Loss : 0.9281
- Val/Test Dice : 0.1751

-----------------------------------------------------------------------------------------------
# Conclusion
 
  This comparsion helps me to understant how dataset characteristics heavily influence model performance and help me choose a more suitable model and loss function in the future.
I found a huge different in using the same dataset in Unet and Mask R-cnn and using different datasets in the same model.
From this experience( Mammogram Calcification Segmentation in Unet), I realized the special of Unet and understand that the low dice doesn't mean this model is bad. Comparing to the lung dataset, large-structure segmentation fits UNet’s strengths and a strong model cannot overcome poor contrast or tiny targets without preprocessing.

  That is, the upper limit of a model is determined by the load of the dataset, not by the architecture itself.
