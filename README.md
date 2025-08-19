# 🎨 Generative Adversarial Networks \& Domain Transfer Network

## 📌 Introduction

This repository documents a journey from reproducing the original GAN paper (Goodfellow et al., 2014) to implementing and studying advanced variants such as DCGAN, WGAN-GP, and finally the Domain Transfer Network (DTN, Taigman et al., 2017).

Goals:

- Understand the mechanics of GANs and issues like vanishing gradient and mode collapse.
- Apply improvements with DCGAN and WGAN-GP to enhance image generation quality.
- Study the paper Unsupervised Cross-Domain Image Generation (DTN) to tackle image-to-image translation without paired data.
- Deploy the DTN model on Hugging Face Spaces with a Gradio demo interface.

🔗 Hugging Face Demo: DTN-Demo-v1

## 📂 Repository Structure

- DCGAN with CelebA.ipynb → Implement DCGAN on the CelebA dataset for face generation.
- WGAN GP with CelebA.ipynb → Experiment with WGAN-GP on CelebA to improve training stability and reduce mode collapse.
- DTN with Dataset.ipynb → Implement the Domain Transfer Network from CelebA-HQ (resized) → Bitmoji, train, and package a Gradio demo.
- Slide Report.pdf → Detailed report:
    - Mathematics behind GANs and the Jensen–Shannon Divergence.
    - Issues of vanishing gradient and mode collapse.
    - How WGAN/WGAN-GP improve training.
    - Analysis of the DTN paper and practical application.


## 📖 GANs \& Variants

- GAN: A framework with a Generator and a Discriminator in competition, optimizing an objective related to the Jensen–Shannon Divergence.
- DCGAN: Uses Conv/Deconv layers and BatchNorm to improve training stability.
- WGAN-GP: Uses the Wasserstein Distance with Gradient Penalty, which:
    - Avoids vanishing gradients.
    - Reduces mode collapse.
- Target domain in GAN experiments: CelebA dataset.


## 📖 Domain Transfer Network (DTN)

- Paper: Unsupervised Cross-Domain Image Generation (Taigman et al., 2017).
- Problem: Transfer images from a source domain (CelebA-HQ) to a target domain (Bitmoji), preserving identity without paired data.

Architecture:

- f: Pre-trained feature extractor (FaceNet) to preserve identity features.
- g: Generator that maps features to the target domain.
- D: Ternary Discriminator (distinguishes real target / fake source / fake target).

Loss Functions:

- LGAN: Ensures generated images belong to the target domain.
- LCONST: Preserves identity (the most important term).
- LTID: Maintains consistency within the target domain.
- LTV: Regularization for smoother images.


## 🚀 Implementation \& Demo

- Training with PyTorch + tracking via Weights \& Biases (wandb): monitor losses and generated images across epochs.
- Packaged as a Gradio demo and deployed on Hugging Face Spaces:
    - 👉 DTN-Demo-v1


## 📚 References

- Goodfellow et al. (2014), Generative Adversarial Nets.
- Radford et al. (2015), DCGAN.
- Gulrajani et al. (2017), WGAN-GP.
- Taigman et al. (2017), Unsupervised Cross-Domain Image Generation (DTN).

***

✍️ This repository was developed as part of the study Mathematics in Generative Models (PiMA 2025).