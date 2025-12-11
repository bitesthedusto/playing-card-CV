# Project: Playing Card Detection and Recognition

Private repo for Playing Card Detection and Recognition project for CS4337 Computer Vision

**Objective:** 

## 1. Introdution

This project was to create a computer vision model that was able to detect and identify playing cards (suits and ranks) within images. To achieve this, I used a pretrained YOLO model, yolov8, and ran it on a dataset I found on Roboflow using the A100 GPU on Google Colab for faster computation.

Once training was finished, I ran the model on validation and testing set images to verify how well the model performed on non-training images to make sure the model wasn't over or under fitted.

## 2. Setup and Workflow

- Python 3.11.13


**Download the project files containing the image datasets and the YOLO model**

**Install Dependencies:**
```bash pip install -r requirements.txt```

## Data

Dataset sourced from Roboflow: https://universe.roboflow.com/augmented-startups/playing-cards-ow27d

## Config

The dataset configuration is the standard yolov8 yaml format. 

Modify path or add config with format .yaml in data_config

sample: [data.yaml](Playing-Cards-1/data.yaml)



## 3. Test Model

In the .ipynb file, there is a cell at the bottom. Simply download an image you would like to test, and change the first string in results = model('IMAGE PATH', save=True, conf=0.5) to the path of the image you would like to test. After that, the model should output the resulting image and save it.
