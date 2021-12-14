# Kneron_YOLOv4
## Custom model
Kneron doesn't support a lot of operations and new activation functions as mish, so we had to change mish to leaky ReLU in Scaled-YOLOv4-CSP and trained this model from scratch. Our custom model achieves with 448x448 image size **43.1% mAP @IoU=0.5:0.95**  and **61.6% mAP @IoU=0.5** on COCO val 2017.
Scaled-YOLOv4 repository: https://github.com/WongKinYiu/ScaledYOLOv4/tree/yolov4-csp

You can see difference between our model and suggested one in the table below. Fps calculated without postprocessing on the host side.
|                model               | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |   FPS on KL-720   |
| :------------------------------:   | :--------------------: | :----------------: |:----------------: |
| Scaled-YOLOv4-CSP-leaky-448(ours)  | 0.432                  | 0.615              | 10.08             |
|      pjreddie's YOLOv3-416         | 0.31                   | 0.553              | 10.01             |

## Convertation to nef
Model's accuracy after convertation and quantization significantly drops due to quantization. Different preprocessing pipelines yields slightly different model performance. Our Scaled-YOLOv4-CSP-leaky-448 converted to nef(int8) format is given in the table.
| our model                      | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |
| :--------------------------:   | :--------------------: | :----------------: |
| YOLOv3-416                  | 0.252                     |     0.489          |
| YOLOv4-scaled-448           | 0.395                     |     0.577          |

YOLOv4 preprocessing is slightly changed preprocessing function from Scaled-YOLOv4 repository. We changed dynamic resolution to fixed, because nef model can take only fixed input size. Also padding from both biggest sides was removed. 
YOLOv3 preprocessing we took from: https://github.com/qqwweee/keras-yolo3

## Conclusion
Convertation to nef decreased mAP50 on 36.7% and showed that our model not supposed to be used in int8 quantization due to differences between Darknet(YOLOv3) and CSP-Darknet53(YOLOv4) backbones. YOLOv3 preprocessing showed to be better option for our Kneron model. 






