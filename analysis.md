### Comparison Between Mammography Calcification Segmentation and Lung Segmentation

# Project background

## This project compares two different datasets in Unet
- Mammography Calcification Segmentation
- Lung segmentation from Chest X-Ray dataset( from Nikhil Pandey)
## The goal of this project
- Why these two datasets behave differently
- How dataset characteristics affect segmentation difficulty
- Why UNet performs well in one task but struggles in the other
- How Dice score reflects task complexity
- What improvements can be made

# Dataset Description
## Mammography Calcification Dataset
- Image size: 512×512
- Objective: detect extremely small calcification regions
- Mask characteristics: small, low-contrast, irregular shapes
- Typical target area ratio: < 1% of the image
- Challenges:
  -Very small target → Dice is naturally low
  -High noise + low contrast
  -Hard for UNet to capture micro features

## Model Architecture(Unet)
- Input: 512 × 512 × 3
- Encoder: 4 downsampling blocks
  - Conv → BN → ReLU ×2
  - MaxPooling
- Filters: 64 → 128 → 256 → 512
- Bottleneck:
  - Conv(1024) ×2 with BN + ReLU
- Decoder: 4 upsampling blocks
  - ConvTranspose
  - Skip connections
  - Filters: 512 → 256 → 128 → 64
- Output: Conv(1, 1×1, sigmoid)
## Loss Function
- To handle extremely small lesions:
- Tversky Loss (β > α, FN-heavy)
- Focal Loss
- Final Loss:
  - Loss = 0.7 * Tversky + 0.3 * Focal

## Training Settings
- Optimizer: Adam (1e-4)
- Batch size: 4
- Metric: Dice coefficient

## Training Results Comparison
| Dataset                    | Train Dice | Val/Test Dice | Notes                                       |
| -------------------------- | ---------- | ------------- | ------------------------------------------- |
| Mammography Calcifications | ~0.20      | **0.15–0.18** | Small-object segmentation, very challenging |
| Lung Segmentation          | ~0.95      | **0.92–0.97** | Large region segmentation, easy for UNet    |
