# Text-to-Image Generation with Conditional VAE and CLIP Embeddings

This repository contains the final project for ECE 685D: Introduction to Deep Learning at Duke University. Our project explores **text-to-image generation** using Conditional Variational Autoencoders (CVAEs) conditioned on **CLIP embeddings**. We investigate both short-label (FashionMNIST) and long-description (MS-COCO) scenarios.

## 🚀 Overview

The project is implemented in two stages:

1. **Short Text CVAE**: A simple Conditional VAE trained on FashionMNIST using one-hot labels to generate digit-specific clothing images.
2. **Long Text CVAE**: A more advanced Conditional VAE trained on the MS-COCO dataset, using CLIP text embeddings as conditioning input for image generation from descriptive captions.

We explore how integrating CLIP and CVAE can bridge the semantic gap between language and vision.

---

## 📁 Project Structure

