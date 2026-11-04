# Facade Defect Detection with YOLOv8

Crack and hole detection on building surfaces, as a proof of concept for automating facade inspection in Singapore. Built for the C384 group project (team of 6).

## Context
Singapore's Periodic Facade Inspection (PFI) requirement means buildings over 13 m must be inspected every 7 years. Manual inspection is slow, costly and prone to human oversight. This project tests whether an object detection model could flag defects in inspection images so engineers know where to look first.

## My role
I trained and evaluated the **baseline model (Model 1)** and set up the shared Google Colab training pipeline. As a team we compared six configurations (epochs, model size, resolution, augmentation) on identical data splits. The other five models were trained by my teammates.

## Setup
- Model: YOLOv8n (Ultralytics), pretrained COCO weights
- 25 epochs, 640 px input, batch 16, standard augmentation
- Data: 2,000 images, split 68/12/20 (train/val/test)
- Classes: crack, hole, normal

## Results (validation split)

| Metric | Score |
|---|---|
| mAP50 | 0.655 |
| mAP50-95 | ~0.47 |
| Precision | 0.651 |
| Recall | 0.661 |

![Confusion matrix](results/confusion_matrix_normalized.png)
![Sample predictions](results/val_batch0_pred.jpg)
![Training curves](results/results.png)

## Findings
- "Normal" was detected almost perfectly (AP 0.995), but crack and hole lagged far behind (AP ~0.48), even though crack had the most training instances (1,104).
- Across the team's six runs, longer training (50 epochs) scored best at 0.679 mAP50, and heavy augmentation scored worst at 0.617.
- Next steps: lighter augmentation for grayscale images, longer training with proper scheduling, and instance segmentation for thin crack shapes.

## Dataset
[Wall Crack/Hole/Normal dataset](https://www.kaggle.com/datasets/erkandevvecii/wall-crack-hole-normal-dataset/data) on Kaggle. Images were not modified or re-uploaded here.

## How to run
1. Download the dataset and update the path in `data.yaml`.
2. Open the notebook in Google Colab (GPU runtime).
3. `pip install ultralytics`, then run all cells.

## Credits
Group 3, C384: Jeanett, Kai Jie, Yanisa, Luc and Emmanuel. Dataset by erkandevvecii on Kaggle.
