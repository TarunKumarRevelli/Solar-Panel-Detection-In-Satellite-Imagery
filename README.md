# Solar Panel Detection using YOLOv8n

## Overview
This project focuses on detecting solar panels from aerial imagery using deep learning. The dataset consists of high-resolution images annotated with solar panel locations in the MS-COCO format. The objective is to train an object detection model using Ultralytics YOLO and evaluate its performance using standard metrics like IoU, mAP, and precision-recall curves.

## Dataset
The dataset is publicly available and contains high-resolution aerial images with labeled solar panels:

- **Images (15 cm HD and 31 cm native resolution, resized to 416x416)**: [Download Link](https://resources.maxar.com/product-samples/15-cm-hd-and-30-cm-view-ready-solar-panels-germany)
- **Labels and README**: [Google Drive Link](https://drive.google.com/drive/folders/13QfMQ-7OdWKw-LR8DmypKwSHtI0Hk2wh?usp=sharing)
- **Label Description**: [Figshare](https://figshare.com/articles/dataset/Solar_Panel_Object_Labels/22081091)
- **Annotation Format**: MS-COCO with Horizontal Bounding Boxes (HBB)

## Data Exploration and Understanding

### Dataset Statistics
- Total number of solar panel instances in the dataset.
- Distribution of labels per image (e.g., how many images contain 0, 1, 2, or more labels).
- Area statistics of solar panels in meters (computed based on label documentation).
  - Mean and standard deviation of the area.
  - Histogram of solar panel areas with observations.

## Implementing Key Functions

### Intersection over Union (IoU)
A function is implemented to compute IoU between two axis-aligned bounding boxes in the Ultralytics YOLO format. The function uses the `shapely` library and is compared with `supervision`'s IoU implementation.

### Average Precision (AP) Computation
Three methods are implemented to compute AP:
1. **Pascal VOC 11-point interpolation method**
2. **COCO 101-point interpolation method**
3. **Area under Precision-Recall Curve method**

These methods are tested on randomly generated data:
- 10 images of size 100x100.
- 10 randomly generated ground truth boxes (20x20) per image.
- 10 predicted bounding boxes (20x20) per image.
- AP50 (Average Precision at IoU 0.5) is computed and compared across methods.

## Model Building and Evaluation

### Data Splitting
- **Train-Test Split**: 80-20 split with 10% of the training data reserved for validation.

### Model Training
- YOLO (Ultralytics) is used for model training.
- The validation loss is monitored to ensure convergence.

### Model Evaluation
- **Visualization**: Ground truth and predicted bounding boxes are visualized on random test images.
- **Metrics Computation**:
  - Mean Average Precision (mAP50) is computed using `supervision.metrics` and compared with our custom implementation.
  - Precision, Recall, and F1-score are computed for different IoU and confidence thresholds:

#### Precision, Recall, and F1-score Table
| IoU \ Confidence | 0.1 | 0.3 | 0.5 | 0.7 | 0.9 |
|----------------|-----|-----|-----|-----|-----|
| **0.1**       | 0.7802 / 0.7905 / 0.7853 | 0.7802 / 0.7905 / 0.7853 | 0.7011 / 0.8790 / 0.7800 | 0.5610 / 0.9504 / 0.7056 | 0.0946 / 1.0000 / 0.1729 |
| **0.3**       | 0.7752 / 0.7855 / 0.7803 | 0.7752 / 0.7855 / 0.7803 | 0.6993 / 0.8767 / 0.7780 | 0.5604 / 0.9494 / 0.7048 | 0.0946 / 1.0000 / 0.1729 |
| **0.5**       | 0.7360 / 0.7457 / 0.7408 | 0.7360 / 0.7457 / 0.7408 | 0.6675 / 0.8368 / 0.7426 | 0.5374 / 0.9103 / 0.6758 | 0.0946 / 1.0000 / 0.1729 |
| **0.7**       | 0.6339 / 0.6423 / 0.6380 | 0.6339 / 0.6423 / 0.6380 | 0.5940 / 0.7447 / 0.6609 | 0.5000 / 0.8470 / 0.6288 | 0.0909 / 0.9605 / 0.1661 |
| **0.9**       | 0.1438 / 0.1457 / 0.1448 | 0.1438 / 0.1457 / 0.1448 | 0.1426 / 0.1788 / 0.1586 | 0.1364 / 0.2310 / 0.1715 | 0.0535 / 0.5658 / 0.0978 |

(Values computed using `supervision.metrics.ConfusionMatrix` for TP, FP, and FN.)

## Conclusion
This project demonstrates a robust approach to solar panel detection using deep learning. The dataset was explored, custom evaluation metrics were implemented, and a YOLO model was trained and assessed. The results provide insights into solar panel detection performance across different IoU and confidence thresholds.

