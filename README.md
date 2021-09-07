# Kneron_YOLOv4
Kneron doesn't support a lot of operations and new activation functions as mish, so we had to change mish to leaky ReLU in YOLOv4-CSP and trained this model from scratch. YOLOv4 repository: https://github.com/WongKinYiu/ScaledYOLOv4/tree/yolov4-csp
Our model achieves mAP @IoU=0.5:0.95 0.431 and mAP @IoU=0.5 0.616

| YOLOv4-csp-leaky-448 nef(int8) | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |
| :--------------------------:   | :--------------------: | :----------------: |
| Yolov4 preprocess              | 0.149                  | 0.339              |
| Yolov3 preprocess              | 0.169                  | 0.39               |
