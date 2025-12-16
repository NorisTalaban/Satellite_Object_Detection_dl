# Satellite Object Detection

Object detection on satellite imagery using Deep Learning (YOLOv8) and the xView dataset.

## Important Note

This project is **not focused on achieving maximum performance**. Its main goal is to present a **clear and complete end-to-end workflow** for object detection on satellite images: from data preparation and model training, to evaluation, error analysis, and inference on unseen data.

The project should be interpreted as a **case study and learning-oriented implementation**, demonstrating how modern object detection models can be applied to geospatial imagery.

> **Tip:** for a clearer and more interactive experience, it is recommended to open the notebooks using **Google Colab**.

---

## Project Structure

For simplicity and clarity, the project is divided into **two main notebooks**, each covering a specific phase of the workflow:

### 1. `Satellite_Object_Detection_dl.ipynb`

**Training and preliminary validation phase.**

This notebook includes:

* Dataset download and setup
* YOLOv8 configuration
* Model training for 20 epochs
* Monitoring of training and validation metrics
* Preliminary qualitative checks on predictions

The test set is **not used** in this phase.

---

### 2. `Test_and_Error_Analysis.ipynb`

**Final evaluation and error analysis phase.**

This notebook focuses exclusively on:

* Inference on a **hold-out test set** (never seen during training)
* Confidence analysis per class
* Ground Truth vs Prediction visual comparisons
* Analysis of prediction frequency and class imbalance
* Confidence score distributions
* Qualitative inspection of sample predictions
* Exploratory inference on external satellite images (Google Earth)

No training or fine-tuning is performed in this notebook.

---

## Model

For object detection, the project uses **YOLOv8 (Nano variant)**, an all-in-one object detection model that balances simplicity, efficiency, and robustness.

### Why YOLOv8

* **Efficient inference:** potentially suitable for fast inference on large-scale image datasets
* **Consolidated architecture:** optimized backbone and detection head for simultaneous localization and classification
* **Ease of use:** Ultralytics framework simplifies training, validation, and experimentation
* **Multi-scale robustness:** suitable for datasets with objects of very different sizes, such as xView
* **Built-in data augmentation:** native support for mosaic augmentation and image flipping
* **Good baseline choice:** well-suited for exploratory and research-oriented projects

---

## Training Configuration

| Parameter         | Value                                  |
| ----------------- | -------------------------------------- |
| Model             | YOLOv8n (Nano)                         |
| Epochs            | 20                                     |
| Image Size        | 640×640                                |
| Batch Size        | 16                                     |
| Data Augmentation | Mosaic, horizontal flip, vertical flip |
| Device            | GPU recommended                        |
| Training Strategy | Default Ultralytics YOLOv8 pipeline    |

---

## Dataset

The project uses the **xView dataset**, a large-scale satellite imagery dataset annotated with **60 object categories**, including vehicles, buildings, ships, aircraft, and infrastructure elements.

### Dataset Split

| Split      | Percentage | Purpose                                       |
| ---------- | ---------- | --------------------------------------------- |
| Training   | 70%        | Model training                                |
| Validation | 15%        | Training monitoring and model selection       |
| Test       | 15%        | Final evaluation (never used during training) |

### Image Characteristics

* **Format:** RGB images (JPG / PNG)
* **Resolution:** Variable (resized to 640×640 during training and inference)
* **Annotations:** YOLO format (normalized bounding boxes)

### Object Categories

The dataset includes 60 classes such as aircraft, vehicles, ships, buildings, cranes, storage tanks, pylons, and other infrastructure-related objects.

---

## Part 2: Test and Error Analysis

The second notebook is entirely dedicated to **model evaluation and interpretability**.

### Main Activities

* Inference on the test set with per-class confidence analysis
* Visualization of Ground Truth vs Predictions to inspect errors
* Analysis of prediction frequency and class imbalance
* Confidence score distribution analysis
* Visualization of sample predictions with confidence-based coloring
* Exploratory inference on external satellite images from Google Earth

This phase provides insight into **how the model behaves**, rather than how well it can be optimized.

---

## Conclusions and Implications

Using YOLO on a large-scale dataset proved to be an effective baseline approach, with clear room for improvement as training duration increases. Dataset quality plays a critical role: consistency in image source, viewing angle, illumination, and acquisition conditions has a strong impact on model performance.

Despite training for only 20 epochs, the exploratory test on Google Earth images showed a **reasonable degree of generalization**. While results are not perfect, they highlight the potential of the approach. With higher-quality data and longer training, significantly better performance could be achieved.

Overall, this project shows that **object detection models**, when properly adapted, can effectively address domain-specific geospatial and monitoring tasks, providing a solid foundation for more advanced and specialized applications.

---

## Future Work

* Training with a larger number of epochs to improve stability and accuracy
* Use of larger, higher-quality datasets with more consistent acquisition conditions
* Deeper analysis on external images to better assess real-world behavior
* Adaptation and specialization of the model for specific application domains (e.g., urban monitoring, infrastructure analysis, territorial surveillance)

---

**Status:** Completed  
**Last Updated:** December 16, 2025

