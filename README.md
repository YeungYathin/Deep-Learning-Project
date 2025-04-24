# Text-to-Image Generation with Conditional VAE and CLIP Embeddings

This repository contains the final project for ECE 685D: Introduction to Deep Learning at Duke University. Our project explores **text-to-image generation** using Conditional Variational Autoencoders (CVAEs) conditioned on **CLIP embeddings**. We investigate both short-label (FashionMNIST) and long-description (MS-COCO) scenarios.

## Overview

The project is implemented in two stages:

1. **Short Text CVAE**: A simple Conditional VAE trained on FashionMNIST using one-hot labels to generate digit-specific clothing images.
2. **Long Text CVAE**: A more advanced Conditional VAE trained on the MS-COCO dataset, using CLIP text embeddings as conditioning input for image generation from descriptive captions.

We explore how integrating CLIP and CVAE can bridge the semantic gap between language and vision.

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

## Citation
If you find this project helpful or inspiring for your work, feel free to cite our report or mention this GitHub:

```
@misc{yang2024cvaeclip,
  title={Text-to-Image Generation using Conditional VAEs and CLIP Embeddings},
  author={Yang, Yixuan and Yang, Chengkun and Yu, Qinmeng and Lu, Kechao},
  year={2024},
  note={ECE 685D Final Project},
  url={https://github.com/YeungYathin/Deep-Learning-Project}
}
```

## Acknowledgements
- CLIP by OpenAI
- FashionMNIST by Zalando
- COCO Dataset by Microsoft
- Implemented with PyTorch
