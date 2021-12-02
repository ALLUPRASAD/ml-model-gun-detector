# ml-model-gun-detector
# yolov5s for detecting guns in images

### Description

_Purpose_: Detecting guns present in the image; 

_Input_: Normal image containing Gun.

_Output_: Valid classes: 'Gun'

_Sample inputs:_ with augmentations 'hsv_h': 0.015, 'hsv_s': 0.7, 'hsv_v': 0.4,'translate': 0.3, 'scale': 0.1 

<img src="./assets/sample.jpg" width="300" height="300"/> <img src="./assets/sample3.jpg" width="300" height="300"/> <img src="./assets/sample2.jpg" width="300" height="300"/>

All these augmentations are applied on letter box resizing due to variation in the size of object class "Gun"
