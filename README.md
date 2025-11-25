Object Detection using Transfer Learning
Problem
The goal of this project was to adapt an image classification task to object detection, which involves not only classifying objects in images but also localizing them with bounding boxes. Using a subset of the Pascal VOC 2007 dataset, the challenge was to detect and visualize objects like persons, cars, dogs, bottles, and chairs while addressing limitations from limited computational resources, such as lower accuracy in a lightweight model. Key issues included handling class mismatches between COCO (pre-training dataset) and VOC categories, occlusion, low contrast, and small object detection.
Approach

Model Selection: Utilized the pre-trained SSD MobileNet V2 model from TensorFlow Hub for its efficiency, fast inference, and low memory requirements, suitable for Google Colab's free GPU. The model was chosen over more accurate but resource-heavy alternatives like Faster R-CNN or EfficientDet.
Dataset Handling: Loaded a small subset of the Pascal VOC 2007 dataset using TensorFlow Datasets, with shuffling enabled. No retraining was performed; the focus was on inference with the pre-trained model.
Implementation: In the Jupyter notebook, imported necessary libraries (TensorFlow, TensorFlow Hub, Matplotlib). Defined a plot_detections function to visualize bounding boxes and confidence scores, filtering detections with a threshold of 0.5. Ran detection on multiple images to observe consistency.
Error Analysis and Modifications: Adjusted the confidence threshold (e.g., 0.3 to 0.7) to study its impact on false positives/negatives. Proposed code modifications for category-specific detection (e.g., filtering by VOC class IDs for animals or vehicles).

Results

Metrics: No quantitative metrics like mAP were computed due to the inference-only setup, but qualitative analysis showed high accuracy for large, prominent objects (e.g., "person", "car", "dog" with confidence >0.8). Smaller or occluded objects (e.g., "bottle", "chair") had lower scores (~0.4-0.6) or were missed/mislabeled (e.g., "chair" as "sofa").
Visuals: Bounding boxes were plotted on images, showing accurate localization for clear objects but inaccuracies in crowded scenes or low-contrast areas. Running multiple times yielded consistent outputs due to fixed shuffling. Compared to online Faster R-CNN demos, SSD was faster but less precise on small objects. (Refer to the notebook for visualization code; examples include partial "person" boxes or missed "cars" in occlusions.)
Observations: The model prioritized speed over accuracy, struggling with VOC complexities not fully aligned with COCO training. Threshold of 0.5 balanced noise and misses effectively.

How to Run
Requirements

Python 3.10+
Libraries: tensorflow, tensorflow-hub, tensorflow-datasets, matplotlib

Install dependencies:
textpip install tensorflow tensorflow-hub tensorflow-datasets matplotlib
Commands

Open Lab9VOC2007__Dataset_student_Notebook_LAB_Object_Detection_transfer_learning_(1) (1).ipynb in Google Colab or Jupyter Notebook.
Set runtime to GPU: In Colab, go to Runtime > Change runtime type > GPU.
Run all cells sequentially: Installs packages, loads the model and dataset, performs detection, and plots results.
To experiment: Modify the threshold in plot_detections (e.g., to 0.3 for more detections) and re-run the visualization cell.
For category filtering: Add the proposed code snippet (e.g., target_ids = [2, 7, 9, 11, 12, 16] for animals) to plot_detections.

Monitor GPU usage: If errors occur, reduce batch size or use a smaller dataset subset.
Data Access Notes

Dataset: Pascal VOC 2007 (subset for testing), loaded via tensorflow_datasets.load('voc/2007', split='test', shuffle_files=True). Contains images with annotated objects across 20 classes (e.g., aeroplane=0, bicycle=1, person=14).
Size: Full dataset has ~5,000 test images; notebook uses a small batch (e.g., take(10)) for efficiency.
Access: Automatically downloaded by TensorFlow Datasets; no manual download needed. For full dataset evaluation, remove the .take() limit, but expect longer runtime.

What I Learned / Next Steps

Learnings: Understood the key differences between image classification (whole-image labeling) and object detection (localization with boxes and confidences). Gained insights into model trade-offs: SSD MobileNet V2's speed suits resource-limited environments but sacrifices accuracy on complex scenes. Learned about factors affecting detection (occlusion, contrast, size) and the value of pre-trained models for transfer learning. Explored threshold impacts and class filtering for targeted applications.
Next Steps:
Train a custom model: Convert VOC to TFRecords, fine-tune SSD on full dataset, evaluate with mAP.
Address challenges: Use data augmentation for occlusion/low-contrast, or switch to heavier models like Faster R-CNN with paid Colab resources.
Extend functionality: Implement real-time detection for videos or mobile apps; compare with YOLOv5 for better speed-accuracy balance.
Improve evaluation: Compute quantitative metrics like precision/recall; test on diverse datasets beyond VOC.
