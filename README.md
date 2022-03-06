# Multi-object-Tracking
## Requirements
* Python 3.6
* [Pytorch](https://pytorch.org) >= 1.2.0 
* python-opencv
* [py-motmetrics](https://github.com/cheind/py-motmetrics) (`pip install motmetrics`)
* cython-bbox (`pip install cython_bbox`)
* (Optional) ffmpeg (used in the video demo)
* (Optional) [syncbn](https://github.com/ytoon/Synchronized-BatchNorm-PyTorch) (compile and place it under utils/syncbn, or simply replace with nn.BatchNorm [here](https://github.com/Zhongdao/Towards-Realtime-MOT/blob/master/models.py#L12))


Usage:
```
python predict_video.py --input-video path/to/your/input/video --weights path/to/model/weights
               --output-format video --output-root path/to/output/root
```
or 
```
python predict_webcam.py --weights path/to/model/weights --output-format video --output-root path/to/output/root
               
```

## Dataset zoo
Please see [DATASET_ZOO.md](https://github.com/Zhongdao/Towards-Realtime-MOT/blob/master/DATASET_ZOO.md) for detailed description of the training/evaluation datasets.
## Pretrained model and baseline models
Darknet-53 ImageNet pretrained model: [[DarkNet Official]](https://pjreddie.com/media/files/darknet53.conv.74)

Trained models with different input resolutions:

|Model| MOTA | IDF1 | IDS | FP | FN | FPS | Link |
|-----|------|------|-----|----|----|-----|------|
|JDE-1088x608| 73.1|	68.9|	1312|6593|	21788|	22.2| [[Google]](https://drive.google.com/open?id=1nlnuYfGNuHWZztQHXwVZSL_FvfE551pA) [[Baidu]](https://pan.baidu.com/s/1Ifgn0Y_JZE65_qSrQM2l-Q) |
|JDE-864x480| 70.8|	65.8|	1279|	5653|	25806|	30.3| [[Google]](https://drive.google.com/open?id=1UKgkYrsV-59kYaHgWeJ70p5Mij3QWuFr) [[Baidu]](https://pan.baidu.com/s/1rBQ7DFjhLQbEq6JTJRntKA) |
|JDE-576x320| 63.7|	63.3|	1307|	6657|	32794|	37.9|[[Google]](https://drive.google.com/file/d/1sca65sHMnxY7YJ89FJ6Dg3S3yAjbLdMz/view?usp=sharing) [[Baidu]](https://pan.baidu.com/s/1cCulbPNneIXOpRRjrTgJ4g) |


## Evaluation 
```
python evaluation.py --cfg ./cfg/yolov3_1088x608.cfg --weights /path/to/model/weights
```

## Training instruction
- Download the training datasets.  
- Edit `cfg/ccmcpe.json`, config the training/validation combinations. A dataset is represented by an image list, please see `data/*.train` for example. 
- Run the training script:
```
python train.py 
```
