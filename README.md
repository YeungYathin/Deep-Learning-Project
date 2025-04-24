# Text-to-Image Generation with Conditional VAE and CLIP Embeddings

This repository contains the final project for ECE 685D: Introduction to Deep Learning at Duke University. Our project explores **text-to-image generation** using Conditional Variational Autoencoders (CVAEs) conditioned on **CLIP embeddings**. We investigate both short-label (FashionMNIST) and long-description (MS-COCO) scenarios.

## Overview

The project is implemented in two stages:

1. **Short Text CVAE**: A simple Conditional VAE trained on FashionMNIST using one-hot labels to generate digit-specific clothing images.
2. **Long Text CVAE**: A more advanced Conditional VAE trained on the MS-COCO dataset, using CLIP text embeddings as conditioning input for image generation from descriptive captions.

We explore how integrating CLIP and CVAE can bridge the semantic gap between language and vision.

---

## Project Structure

. ├── clip_model/ # Pretrained CLIP model loader ├── short_text_model/ # MNIST model: one-hot label conditional CVAE ├── long_text_model/ # COCO model: CLIP-conditional CVAE ├── datasets/ # Dataset loaders and preprocessors ├── utils/ # Loss functions, training scripts, metrics ├── results/ # Generated and reconstructed images ├── report/ # Final project report (PDF) ├── requirements.txt └── README.md


---

## Model Architecture

### Short Text Model (FashionMNIST)

- Condition: One-hot label vector (10-dim)
- Encoder/Decoder: Fully connected MLPs
- Latent Dimension: 20
- Optimizer: Adam (lr=1e-3)

### Long Text Model (MS-COCO + CLIP)

- Condition: CLIP text embeddings (512-dim)
- Encoder: 5-layer ConvNet + MLP for `μ` and `log(σ²)`
- Decoder: Transposed ConvNet for image reconstruction
- Latent Dimension: 128
- Loss: BCE + KL Divergence
- Optimizer: Adam (lr=1e-4)
- Training Epochs: 250

---

## Results

### Short Text CVAE

- Successfully generates FashionMNIST digits based on label
- Generates diverse samples per class
- High visual fidelity and consistency

### Long Text CVAE (MS-COCO + CLIP)

- Coherent images generated from natural language descriptions
- Best CLIP Score: `0.2023` at epoch 250
- FID reduced from `326.7 → 295.4` during training
- Performance sensitive to latent dimension and overfitting after 250 epochs

---

## Installation

Clone the repo and install dependencies:
```bash
git clone https://github.com/your-username/conditional-vae-text2image.git
cd conditional-vae-text2image


