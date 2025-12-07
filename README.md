# Unet
the difference dataset in Unet 

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
