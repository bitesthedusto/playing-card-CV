# Project: Playing Card Detection and Recognition


<img src="https://github.com/user-attachments/assets/22b7913b-755a-4542-b8f8-e1389411d5fe" width="300" />

**Objective:** 

Create a model that can take an input image and detect any playing cards in the image and their corresponding suits and ranks

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

```
train: train/images
val: valid/images
test: test/images

names: 
  0: 10C
  1: 10D
  2: 10H
  3: 10S
  4: 2C
  5: 2D
  6: 2H
  7: 2S
  8: 3C
  9: 3D
  10: 3H
  11: 3S
  12: 4C
  13: 4D
```

## Train

```
model = YOLO('yolov8n.pt')

results = model.train(
    data=os.path.join(dataset.location, 'data.yaml'),
    epochs=50,
    imgsz=640,
    batch=16,
    device=None,
    pretrained=True,
    optimizer='AdamW',
    lr0=0.001
)
```


| Models | precision | recall | mAP50 | mAP50:95 |
| :--- | :---: | :---: | :---: | :---: |
| yolov8s |	1.000 | 1.000 | 0.995 |	0.951 |

## 3. Test Model

In the .ipynb file, there is a cell at the bottom. Simply download an image you would like to test, and change the first string in results = model('IMAGE PATH', save=True, conf=0.5) to the path of the image you would like to test. After that, the model should output the resulting image and save it.

| Input Image | Output Image |
| :---: | :---: |
| <img src="https://github.com/user-attachments/assets/b5aaaba4-95d3-435c-b733-b6462803f373" width="300" /> | <img src="https://github.com/user-attachments/assets/5690afb4-db24-44bd-8139-e901c772eca1" width="300" /> |




