# Kneron_YOLOv4
## Custom model
Kneron doesn't support a lot of operations and new activation functions as mish, so we had to change mish to leaky ReLU in Scaled-YOLOv4-CSP and trained this model from scratch. Our custom model achieves with 448x448 image size **43.1% mAP @IoU=0.5:0.95**  and **61.6% mAP @IoU=0.5** on COCO val 2017.
Scaled-YOLOv4 repository: https://github.com/WongKinYiu/ScaledYOLOv4/tree/yolov4-csp
You can see difference between our model and suggested one in the table below. Fps calculated without postprocessing on the host side.
|              model             | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |   FPS on KL-720  |
| :--------------------------:   | :--------------------: | :----------------: |:----------------: |
| Scaled-YOLOv4-CSP-leaky(ours)  | 0.431                  | 0.616              | 9.8               |
|      pjreddie's YOLOv3         | 0.31                   | 0.553              | 8.7               |

## Convertation to nef
After convertation model's accuracy significantly drops due to quantization. We tried to use different preprocessing and this is what we got:
| YOLOv4-csp-leaky-448 nef(int8) | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |
| :--------------------------:   | :--------------------: | :----------------: |
| Yolov4 preprocessing           | 0.149                  | 0.339              |
| Yolov3 preprocessing           | 0.169                  | 0.39               |






