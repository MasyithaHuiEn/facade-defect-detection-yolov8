# facade-defect-detection-yolov8
Context: Singapore’s Periodic Facade Inspection requirement, and manually going through millions of drone images would be tedious, slow and prone to human error.
My role: Baseline model (Model 1) and Colab training setup. The wider project compared six configurations as a team of 6.

Setup: YOLOv8n, 25 epochs, 640px, standard augmentation, 2,000 images split 68/12/20.

Results: a small table with mAP50 0.655, mAP50-95 ~0.47, precision 0.651 and recall 0.661. Embed the confusion matrix and the sample predictions as images.

Findings: crack and hole AP (0.48) lagged far behind “normal” (0.995) despite crack having the most instances. 

Link to dataset used in this project > https://www.kaggle.com/datasets/erkandevvecii/wall-crack-hole-normal-dataset/data - no images were modified in anyway. 

How to run: install ultralytics, point data.yaml at the dataset, run the notebook.

Credits: My groupmates, and the author of the dataset.
