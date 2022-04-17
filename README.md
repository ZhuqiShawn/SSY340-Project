# Animal Detection Project
This repo is for SSY340 Deep Machine Learning Course Project, building a network for detecting animals in [Universeum](https://www.universeum.se/en/). 

## Labeling Software

### Labeling Tool
Link to [labelImg](https://github.com/tzutalin/labelImg.git) on github.

Step to install:
```
git clone https://github.com/tzutalin/labelImg.git
cd labelImg
pip3 install pyqt5 lxml
make qt5py3
python3 labelImg.py
python3 labelImg.py [IMAGE_PATH] [PRE-DEFINED CLASS FILE]
```

To initiate a label, type `w`, and draw the intended label. Then, type ctrl (or command) `S` to save the label. Type `d` to go to the next image (and `a` to go back an image).`

Export your labels to YOLO format, with one `*.txt` file per image (if no objects in image, no `*.txt` file is required). The `*.txt` file specifications are:

+ One row per object
+ Each row is `class x_center y_center width height` format.
+ Box coordinates must be in **normalized xywh** format (from 0 - 1). If your boxes are in pixels, divide `x_center` and `width` by image width, and `y_center` and `height` by image height.
+ Class numbers are zero-indexed (start from 0).

### Create dataset.yaml

The file format is shown as below:
```
# Example format for the dataset.yaml file
# Example usage: python train.py --data coco128.yaml
# parent
# ├── yolov5
# └── datasets
#     └── your dataset


# Train/val/test sets as 
# 1) dir: path/to/imgs, 
# 2) file: path/to/imgs.txt, or 
# 3) list: [path/to/imgs1, path/to/imgs2, ..]

path: ../datasets/data  # dataset root dir
train: images/train  # train images (relative to 'path') 128 images
val: images/val  # val images (relative to 'path') 128 images
test: images/test

# Classes
nc: 20  # number of classes
names: ['person', 'bicycle', 'car', 'motorcycle', 'airplane']  # class names
```

## Transfer learning

### YOLOv5
[YOLOv5 Link](https://github.com/ultralytics/yolov5)
#### Create a new virtual conda environment
```
$ conda create --name yolov5 # create a new virtual env
$ conda activate yolov5 # activate the new created env
$ conda install pip # install pip for later use
```

#### Get pre-trained YOLOv5 model

```
$ git clone https://github.com/ultralytics/yolov5  # clone repo
$ cd yolov5
$ pip install -r requirements.txt  # install
```
