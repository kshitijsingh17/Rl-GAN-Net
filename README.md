# RL-GAN-Net: Reinforcement Learning Controlled GAN for Point Cloud Shape Completion

RL-GAN-Net is a novel framework combining Reinforcement Learning (RL) with Generative Adversarial Networks (GANs) to perform real-time 3D shape completion on partial and noisy point clouds. This method is designed to robustly complete 3D shapes from partial observations without relying on time-consuming optimization, enabling real-time performance suitable for integration into pipelines such as classification and reconstruction.

## 🧠 Key Features

- **RL-Controlled Latent GAN**: First architecture to use a deep RL agent to control a GAN’s input for 3D shape generation.
- **Real-Time Shape Completion**: Achieves shape reconstruction in ~1 ms per object by avoiding iterative optimization.
- **Hybrid Model Selection**: Combines outputs from AE and RL-GAN-Net using a trained discriminator to choose the most plausible result.
- **Improved Downstream Performance**: Enhances classification accuracy of partially observed shapes by completing them beforehand.

## 🏗️ Architecture Overview

RL-GAN-Net is composed of three main modules:
- **Autoencoder (AE)**: Learns to encode partial point clouds into latent vectors (Global Feature Vectors - GFVs).
- **Latent-Space GAN (l-GAN)**: Trained in GFV space to generate realistic latent representations of complete shapes.
- **Reinforcement Learning Agent**: Selects optimal latent seed vector `z` to feed the generator for producing plausible completions.

![Architecture Overview](docs/architecture_diagram.png)

## 🔍 Applications

- **3D Point Cloud Shape Completion**
- **Preprocessing for Classification**
- **Potential use in image inpainting and other generative tasks**

## 📊 Dataset

The framework is trained and tested on categories from the [ShapeNetCore](https://shapenet.org/) dataset:
- Airplane
- Car
- Chair
- Desk

### Input Format

- Raw 3D point clouds (2048 points per shape)
- Partial inputs simulated by removing random point clusters

## 📈 Performance

- **Real-Time Inference**: ~1ms per shape on a single GTX Titan Xp
- **Classification Accuracy** (with 70% missing points): 
  - Raw: 50.2%
  - AE + PointNet: 69.6%
  - RL-GAN-Net (hybrid) + PointNet: 83.8%
- **Chamfer Distance Improvement** over baseline AE models

## 🛠️ Installation

```bash
git clone https://github.com/your-username/rl-gan-net.git
cd rl-gan-net
pip install -r requirements.txt
