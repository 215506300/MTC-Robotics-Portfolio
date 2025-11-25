ITAI 2376 - Deep Learning
Course Overview
This repository contains my coursework and projects from ITAI 2376 - Deep Learning, part of the Associates in Artificial Intelligence program. The course focused on advanced neural network architectures, generative models, and practical implementations using PyTorch. Key topics included diffusion models for image generation, retrieval-augmented generation (RAG) systems, embeddings with Sentence Transformers, and dynamic learning through user feedback.
Skills and Technologies

Deep Learning Frameworks: PyTorch for building and training models like U-Nets and diffusion probabilistic models.
Generative AI: Implemented Denoising Diffusion Probabilistic Models (DDPM) for image synthesis on datasets like MNIST.
Natural Language Processing: Used Sentence Transformers (all-MiniLM-L12-v2) for semantic embeddings, cosine similarity for retrieval, and NLTK for text preprocessing.
Tools and Libraries: Torchvision for datasets, Einops for tensor manipulations, Pandas for data handling, Matplotlib for visualizations, Scikit-learn for metrics.
Concepts: Class-conditional generation, error handling in neural networks (e.g., dimension mismatches), RAG architectures, feedback loops for adaptive AI, hyperparameter tuning, and evaluation metrics like cosine similarity and CLIP scores.
Environment: Google Colab with GPU acceleration for training.

Featured Projects

Creating Images with Diffusion Models: Built a class-conditional DDPM using a U-Net to generate MNIST digits. Addressed dimension mismatches in embeddings and evaluated with qualitative visuals and potential FID scores. README.md
Creation of an AI Agent named ProgBot: Developed a programming tutor chatbot using RAG with Sentence Transformers for query matching. Incorporated dynamic learning via user feedback, achieving 85% retrieval accuracy. README.md
