# ml-model-gun-detector
# yolov5s for detecting guns in images

### Description

_Purpose_: Detecting guns present in the image; 

_Input_: Normal image containing Gun.

_Output_: Valid classes: 'Gun'

_Sample inputs:_ with augmentations 'hsv_h': 0.015, 'hsv_s': 0.7, 'hsv_v': 0.4,'translate': 0.3, 'scale': 0.1 

|<img src="./assets/sample.jpg" width="240" height="240"/> | <img src="./assets/sample3.jpg" width="240" height="240"/> | <img src="./assets/sample2.jpg" width="240" height="240"/>|

All these augmentations are applied on letter box resizing due to variation in the size of object class "Gun"

## Data Preparation
  1. Removed the images which don't have annotations 
  2. Converted annotations into standard yolo format
   follow the steps provide in the data_preprocessing data_preparation (./data_preparation/notebook data_preprocessing (2).ipynb)
  Data Extraction: data is extracted along with labels from https://www.kaggle.com/issaisasank/guns-object-detection
    
## Training data 

In current dataset contains 330 training images and trained with 512*512 dimensions 

 Train Dataset | Validation dataset| Test | Epochs|
| --- | --- |  --- |--- |
| 330| 30| 30 |50 |

## Training instructions 

  1.Change directory to dev/yolov5/
  
  2.install dependencies using !pip install -r requirments.txt
  
  3.Create data.yaml file which containes train,val and test training images and labels  
  
      train : data/data/train/images
      
      val : data/data/val/images
      
      test : data/data/test/images
      
      nc : 1
      
      names: ["Gun"] 
   
  4.Check defaults parameters in train.py and specify any parameters you want to it be different.

  5.Run $ python train.py --img 512 --batch 8 --epochs 40 --data data.yaml --weights yolov5s.pt



### Current performance metrics v0.0

 
Following are the results on test data with confidence score>0.4

| _Per class_ |precision    |recall  |map@0.5  |map@0.95 | total no of images |
| --- | --- | --- | --- | --- | ---
| 'Gun' | 0.85 | 0.9 | 0.91 |0.552 | 28 |

### Testing instructions 

1.Change directory to dev/yolov5/

2.Mention the required parameters in test.py and keep the test images and annotations as specified in data.yaml 

3.Run the below command 

    python3 test.py --task test 


### Prediction results
_Sample result:_

| <img src = "assets/a.jpg" height="240" width="260"/>  | <img src = "assets/b.jpg" height="240" width="260"/> | <img src = "assets/c.jpg" height="240" width="260"/> |

| <img src = "assets/d.jpg" height="240" width="260"/>  | <img src = "assets/e.jpg" height="240" width="260"/> | <img src = "assets/f.jpg" height="240" width="260"/> |

## Inference instructions 

  1.Change directory to dev/yolov5/
  
  2.Mention the required parameters in detect.py with following details along with best.pt params file which is there in model_params folder 
  
      weights='best.pt', source='images', img_size=512, conf_thres=0.4, iou_thres=0.2, device='', view_img=False, save_txt=False, save_conf=False,  classes=None,   agnostic_nms=False, augment=False, update=False, project='runs/detect', name='exp', exist_ok=False
      
  3.Run the following command 
  
      python3 detect.py --weights best.pt --img_size 512 --source images
