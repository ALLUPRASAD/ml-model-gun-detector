# ml-model-gun-detector
# yolov5s for detecting guns in images

### Description

_Purpose_: Detecting guns present in the image; 

_Input_: Normal image containing Gun.

_Output_: Valid classes: 'Gun'

_Sample inputs:_ with augmentations 'hsv_h': 0.015, 'hsv_s': 0.7, 'hsv_v': 0.4,'translate': 0.3, 'scale': 0.1 

<img src="./assets/sample.jpg" width="300" height="300"/> <img src="./assets/sample3.jpg" width="300" height="300"/> <img src="./assets/sample2.jpg" width="300" height="300"/>

All these augmentations are applied on letter box resizing due to variation in the size of object class "Gun"

### Data Preparation
    
    1.Removed the images which don't have annotations 
    2.Converted annotations into standard yolo yolo formate 
    
    Data Extraction:(https://www.kaggle.com/issaisasank/guns-object-detection)
    
## Training data 

 Train Dataset | Validation dataset| Test | Epochs|
| --- | --- |  --- |--- |
| 330| 30| 30 |50 |



### Current performance metrics v0.0

After filtering detections which have confidence score which are less than 0.4. 
Following are the results

| _Per class_ |precision    |recall  |map@0.5  |map@0.95 | total no of images |
| --- | --- | --- | --- | --- | ---
| 'Gun' | 0.85 | 0.9 | 0.91 |0.552 | 28 |

