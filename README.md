# MobileNet-V2 S3FD in PyTorch

[![License](https://img.shields.io/badge/license-BSD-blue.svg)](LICENSE)

A [PyTorch](https://pytorch.org/) implementation of [S3FD: Single Shot Scale-invariant Face Detector](https://arxiv.org/abs/1708.05237). The official code in Caffe can be found [here](https://github.com/sfzhang15/SFD).

## WIDER Face Performance
| Subset | Original Caffe | PyTorch Implementation | MV2 Pytorch Implementation |
|:-|:-:|:-:|:-:|
| Easy | 93.7% | 94.1% | 91.5% |
| Medium | 92.4% | 92.9% | 89.0% |
| Hard | 85.2% | 85.4% | 76.5% |


## Component
* [√] Max-out background label
* [√] Scale compensation anchor matching strategy
* [√] Scale-equitable framework

### Contents
- [Installation](#installation)
- [Training](#training)
- [Evaluation](#evaluation)
- [Performance](#performance)
- [Test](#test)
- [References](#references)

## Installation
1. Install [PyTorch-1.0.0](https://pytorch.org/) according to your environment.

2. Clone this repository. We will call the cloned directory as `$S3FD_ROOT`.
```Shell
git clone https://github.com/luuuyi/S3FD.PyTorch.git
```

3. Compile the nms:
```Shell
./make.sh
```

_Note: We support PyTorch-1.0.0 and Python 3+._

## Training
1. Download [WIDER FACE](http://mmlab.ie.cuhk.edu.hk/projects/WIDERFace/index.html) dataset, place the images under this directory:
  ```Shell
  $S3FD_ROOT/data/WIDER_FACE/images
  ```
2. Convert WIDER FACE annotations to VOC format or download [our converted annotations](https://drive.google.com/open?id=1-s4QCu_v76yNwR-yXMfGqMGgHQ30WxV2), place them under this directory:
  ```Shell
  $S3FD_ROOT/data/WIDER_FACE/annotations
  ```

3. Download VGG Pretrained Model from [here](https://s3.amazonaws.com/amdegroot-models/vgg16_reducedfc.pth), place it under this directory:
  ```Shell
  $S3FD_ROOT/weights
  ```

4. Train the model using WIDER FACE(You should modify below file depend on your setting):
  ```Shell
  cd $S3FD_ROOT/
  ./train_s3fd.sh
  ```

## Evaluation(WIDER Face)

1. Evaluate the trained model using:(You should modify below file depend on your setting)
```Shell
./test_s3fd.sh
```

2. If you can use Matlab, downloading official eval tools to evaluate the performance. If you use Python, clone this repo [WiderFace-Evaluation](https://github.com/wondervictor/WiderFace-Evaluation) to evaluate the performance.


## Performance(FDDB)

1. Single-Scale : minside is 300 pixels aligned

![ROC](https://github.com/lippman1125/S3FD.PyTorch/blob/master/performance/fddb_DiscROC.png)<br>
![PR](https://github.com/lippman1125/S3FD.PyTorch/blob/master/performance/fddb_PR.png)

## Test

1. Single-Scale : minside is 1080 pixels aligned

![festival](https://github.com/lippman1125/S3FD.PyTorch/blob/master/demo/festival_out.jpg)<br>
![office](https://github.com/lippman1125/S3FD.PyTorch/blob/master/demo/office_out.jpg)<br>
![oscar](https://github.com/lippman1125/S3FD.PyTorch/blob/master/demo/oscar_out.jpg)

## References
- [Official release (Caffe)](https://github.com/sfzhang15/SFD)
- A huge thank you to FaceBoxes ports in PyTorch that have been helpful:
  * [FaceBoxes.PyTorch](https://github.com/zisianw/FaceBoxes.PyTorch)

  _Note: If you can not download the converted annotations, the provided images and the trained model through the above links, you can download them through [BaiduYun](https://pan.baidu.com/s/1HoW3wbldnbmgW2PS4i4Irw)._
