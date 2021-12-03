# ml-model-gun-detector
# yolov5s for detecting guns in images

### Description

_Purpose_: Detecting guns present in the image; 

_Input_: Normal image containing Gun.

_Output_: Valid classes: 'Gun'

_Sample inputs:_ with augmentations 'hsv_h': 0.015, 'hsv_s': 0.7, 'hsv_v': 0.4,'translate': 0.3, 'scale': 0.1 

<img src="./assets/sample.jpg" width="300" height="300"/> <img src="./assets/sample3.jpg" width="300" height="300"/> <img src="./assets/sample2.jpg" width="300" height="300"/>

All these augmentations are applied on letter box resizing due to variation in the size of object class "Gun"

## Data Preparation
  1. Removed the images which don't have annotations 
  2. Converted annotations into standard yolo format
    
  Data Extraction: data is extracted along with labels from https://www.kaggle.com/issaisasank/guns-object-detection
    
## Training data 

In current dataset contains 330 training images

 Train Dataset | Validation dataset| Test | Epochs|
| --- | --- |  --- |--- |
| 330| 30| 30 |50 |

## Training instructions 

  Change directory to dev/yolov5/
  install dependencies using !pip install -r requirments.txt 
  Create data.yaml file which containes train,val and test training images and labels  
    train : data/data/train/images
    val : data/data/val/images
    test : data/data/test/images
    nc : 1
    names: ["Gun"] 
   
  Check defaults parameters in train.py and specify any parameters you want to it be different.
Run train.py python train.py . Sample command: python train.py --num-gpus 1 --im-size 512 --epochs 100 --lr 0.001 --lr-decay 0.01 --lr-decay-epoch '40,80,120' --save-prefix 'ssd_mobilenet1.0' --save-interval 50 --batch-size 8 --model-dir './model_checkpoint/' --task-name 'wd-det-adjust-chain' --classes 'window,door' --save-model-s3 's3://ev-ml-data/satheesh/Window_Door_ObjDet/v.0.0/model/v0.0.params' > train_log.log



### Current performance metrics v0.0

After filtering detections which have confidence score which are less than 0.4. 
Following are the results

| _Per class_ |precision    |recall  |map@0.5  |map@0.95 | total no of images |
| --- | --- | --- | --- | --- | ---
| 'Gun' | 0.85 | 0.9 | 0.91 |0.552 | 28 |

