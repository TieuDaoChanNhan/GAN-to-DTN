# 🎨 Generative Adversarial Networks \& Domain Transfer Network

## 📌 Giới thiệu

Repo này là hành trình từ reproduce paper GAN (Goodfellow et al., 2014) đến triển khai và nghiên cứu các biến thể nâng cao như DCGAN, WGAN-GP, và cuối cùng là Domain Transfer Network (DTN, Taigman et al., 2017).

Mục tiêu:

- Hiểu rõ cơ chế GAN và các vấn đề như vanishing gradient và mode collapse.
- Áp dụng cải tiến với DCGAN và WGAN-GP để cải thiện chất lượng sinh ảnh.
- Nghiên cứu paper Unsupervised Cross-Domain Image Generation (DTN) để giải quyết bài toán image-to-image translation mà không cần dữ liệu paired.
- Triển khai mô hình DTN trên Hugging Face Spaces với giao diện demo qua Gradio.

🔗 Demo Hugging Face: [DTN-Demo-v1](https://huggingface.co/spaces/TieuDaoChanNhan/DTN-Demo-v1)

## 📂 Cấu trúc Repo

- DCGAN with CelebA.ipynb → Triển khai DCGAN trên dataset CelebA để sinh ảnh khuôn mặt.
- WGAN GP with CelebA.ipynb → Thử nghiệm WGAN-GP với CelebA, cải thiện ổn định training và giảm mode collapse.
- DTN with Dataset.ipynb → Triển khai Domain Transfer Network từ CelebA-HQ (resize) → Bitmoji, huấn luyện và đóng gói demo Gradio.
- Slide Report.pdf → Báo cáo chi tiết:
    - Toán học đằng sau GAN và Jensen–Shannon Divergence.
    - Các vấn đề vanishing gradient và mode collapse.
    - Cách WGAN/WGAN-GP cải tiến.
    - Phân tích paper DTN và cách áp dụng.


## 📖 GAN \& Các biến thể

- GAN: Mô hình gồm Generator và Discriminator cạnh tranh, tối ưu hàm mục tiêu liên quan đến Jensen–Shannon Divergence.
- DCGAN: Sử dụng Conv/Deconv layers, BatchNorm để cải thiện training stability.
- WGAN-GP: Dùng Wasserstein Distance + Gradient Penalty, giúp:
    - Tránh vanishing gradient.
    - Giảm mode collapse.
- Target domain của các thí nghiệm GAN: CelebA dataset.


## 📖 Domain Transfer Network (DTN)

- Paper: Unsupervised Cross-Domain Image Generation (Taigman et al., 2017).
- Bài toán: Transfer ảnh từ domain nguồn (CelebA-HQ) → domain đích (Bitmoji), bảo toàn identity mà không cần dữ liệu paired.

Kiến trúc:

- f: Pre-trained feature extractor (FaceNet) để giữ đặc trưng.
- g: Generator mapping feature → target domain.
- D: Ternary Discriminator (phân biệt real target / fake source / fake target).

Loss Function:

- LGAN: đảm bảo ảnh sinh ra thuộc target domain.
- LCONST: bảo toàn identity (quan trọng nhất).
- LTID: giữ consistency trong target domain.
- LTV: regularization, làm ảnh mượt hơn.


## 🚀 Triển khai \& Demo

- Training với PyTorch + tracking bằng Weights \& Biases (wandb): theo dõi loss và ảnh sinh ra qua từng epoch.
- Gói demo bằng Gradio, triển khai trên Hugging Face Spaces:
    - 👉 [DTN-Demo-v1](https://huggingface.co/spaces/TieuDaoChanNhan/DTN-Demo-v1)


## 📚 Tham khảo

- Goodfellow et al. (2014), Generative Adversarial Nets.
- Radford et al. (2015), DCGAN.
- Gulrajani et al. (2017), WGAN-GP.
- Taigman et al. (2017), Unsupervised Cross-Domain Image Generation (DTN).

***

✍️ Repo được phát triển trong khuôn khổ nghiên cứu Toán học trong các Mô hình Tạo sinh (PiMA 2025).

