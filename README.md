ITAI 1378 - Computer Vision
Course Overview
This repository contains my coursework and projects from ITAI 1378 - Computer Vision, part of the Associates in Artificial Intelligence program. The course emphasized object detection techniques, transfer learning with pre-trained models, and evaluation metrics like Intersection over Union (IoU). Key topics included dataset handling (e.g., Pascal VOC 2007, COCO 2017), model adaptation for resource-constrained environments, and analyzing detection accuracy in complex scenarios such as occlusions and cluttered backgrounds.
Skills and Technologies

Deep Learning Frameworks: TensorFlow and TensorFlow Hub for loading and fine-tuning models like SSD MobileNet V2.
Object Detection: Implemented detection pipelines with bounding box localization, class prediction, and IoU-based evaluation.
Data Processing: Used TensorFlow Datasets for loading and preprocessing (resizing, normalization); tf.data for efficient pipelines.
Tools and Libraries: Matplotlib for visualizations, NumPy for array operations.
Concepts: Transfer learning from COCO-pre-trained models to VOC/COCO subsets, fine-tuning strategies, threshold tuning for confidence scores, and qualitative/quantitative analysis of detections.
Environment: Google Colab with GPU acceleration for inference and limited training.

Featured Projects

Object Detection using Transfer Learning: Applied pre-trained SSD MobileNet V2 on Pascal VOC 2007 subset for object detection. Analyzed bounding box accuracy, threshold impacts, and limitations like occlusion handling. README.md
Object Detection Project: Used SSD MobileNet V2 on COCO MiniTrain subset, with optional fine-tuning. Evaluated IoU-based accuracy, comparing baseline (0.75) to fine-tuned (0.85) performance. README.md
