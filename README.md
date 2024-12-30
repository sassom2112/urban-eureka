# Generating Realistic Flower Images with GANs

## Overview
This project leverages Generative Adversarial Networks (GANs) to generate realistic images of flowers using the **Oxford 102 Flowers Dataset**. GANs consist of two neural networks, the **Generator** and the **Discriminator**, which work adversarially. The Generator learns to create realistic images, while the Discriminator learns to distinguish real images from fake ones. Through this iterative process, the Generator becomes capable of producing high-quality, realistic images.

---

## Features
- **Dataset**:
  - Uses the **Oxford 102 Flowers Dataset**, a collection of flower images with diverse varieties.
- **Custom GAN Architecture**:
  - **Discriminator**:
    - A Convolutional Neural Network (CNN) with LeakyReLU activations and Sigmoid output.
    - Classifies images as real or fake.
  - **Generator**:
    - A CNN with Transpose Convolutions, ReLU activations, and Tanh output.
    - Generates realistic flower images from random noise.
- **Training Pipeline**:
  - Adversarial training with Binary Cross-Entropy Loss.
  - Adam optimizers with dynamic learning rates for stable convergence.
- **Visualization**:
  - Tracks and visualizes Generator and Discriminator losses during training.
  - Compares real images from the dataset with synthetic images generated by the model.

---

## Key Components
### 1. **Discriminator**
- A CNN designed to classify images as real or fake.
- Utilizes LeakyReLU activations for stability and Sigmoid for output probabilities.

### 2. **Generator**
- A CNN that generates realistic flower images from random latent vectors.
- Employs Batch Normalization for stability and Tanh activation for output normalization.

### 3. **Custom Weight Initialization**
- Implements custom initialization for Convolutional and BatchNorm layers to enhance stability during training.

### 4. **Training Configuration**
- **Loss Function**: Binary Cross-Entropy Loss for adversarial training.
- **Optimizers**: Adam optimizers with a learning rate of 0.0001 and momentum tuning (`beta1=0.5`).
- **Labels**: Real images labeled as `1.0`, fake images labeled as `0.0`.

---

## Training
### Steps
1. **Update Discriminator**:
   - Classifies real and fake images.
   - Learns to differentiate between real and synthetic images.
2. **Update Generator**:
   - Generates synthetic images and improves to fool the Discriminator.
3. **Repeat**:
   - Alternates updates for both networks over multiple epochs.

### Visualization
- Tracks Generator and Discriminator losses during training.
- Generates and saves synthetic flower images at the end of each epoch for qualitative evaluation.

---

## Outputs
1. **Trained Models**:
   - A Generator capable of producing realistic flower images.
   - A Discriminator trained to distinguish between real and fake images.
2. **Generated Images**:
   - High-quality flower images synthesized by the Generator.
   - Visual progress over epochs saved in the `generated_images` directory.
3. **Training Curves**:
   - Graphs of Generator and Discriminator losses for monitoring stability and performance.

---

## How to Run
### Prerequisites
- Python 3.x
- Required libraries: `torch`, `numpy`, `matplotlib`, `torchvision`

### Steps
1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-folder>
   ```
2. Install dependencies:
```bash
pip install torch matplotlib scikit-learn numpy
```
3. Run the script to preprocess data, train the model, and generate predictions:
```bash 
python lstm_text_prediction.py
```

## Future Enhancements
- Implement a conditional GAN (cGAN) to generate specific flower types based on labels.
- Add a Frechet Inception Distance (FID) metric to quantitatively evaluate the quality of generated images.
- Experiment with attention mechanisms for finer details in image generation.