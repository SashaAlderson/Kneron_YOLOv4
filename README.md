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
Model's accuracy after convertation and quantization slightly drops due to quantization. YOLOv3 showed here is the model that was converted in previous example https://github.com/SashaAlderson/Kneron_yolov3_inference.
| our model                   | mAP @<br>IoU=0.5:0.95  |  mAP @<br>IoU=0.5  |
| :-----------------------:   | :--------------------: | :----------------: |
| YOLOv3-416                  | 0.252                  |     0.489          |
| Scaled-YOLOv4-CSP-leaky-448          | 0.395                  |     0.577          |


## Conclusion
YOLOv4 is more optimal choise for Kneron KL-720 than YOLOv3. Also we used 500 images for quantization instead of suggested 10 in example, so our model loses significantly less accuracy(≈9%) comparing with YOLOv3(≈19%).






