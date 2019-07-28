---
layout: post
title: Deep Learning-based Real Time object detection with YOLO and OpenCV
subtitle: 4 min read
category: technology
hide: true
tags: [AI, ArtificialIntelligence, OpenCV, Yolo, DNN, NeuralNetwork, ObjectDetection, ComputerVision]

---

<img src="https://manmohanp.github.io/assets/img/opencv.png" alt="OpenCV" width="150" height="150"/> <img src="https://manmohanp.github.io/assets/img/yolo.png" alt="OpenCV" width="150" height="150"/>

**You only look once** ([YOLO](https://pjreddie.com/darknet/yolo/)) is a state-of-the-art, real-time object detection system.

As per official Yolo site:

"Our model has several advantages over classifier-based systems. It looks at the whole image at test time so its predictions are informed by global context in the image. It also makes predictions with a single network evaluation unlike systems like [R-CNN](https://github.com/rbgirshick/rcnn) which require thousands for a single image. This makes it extremely fast, more than 1000x faster than R-CNN and 100x faster than [Fast R-CNN](https://github.com/rbgirshick/fast-rcnn). See our [paper](https://pjreddie.com/media/files/papers/YOLOv3.pdf) for more details on the full system."

Object detector is a combination of **object locator** and **object recognizer** and Yolo does this by runing forward the whole image only once through the deep nural network ([DNN](https://papers.nips.cc/paper/5207-deep-neural-networks-for-object-detection.pdf)).

## Realtime Object Detection

We will use OpenCV for this, especially DNN, Yolov3, [Darknet](https://pjreddie.com/darknet/). And since we are going to Python OpenCV provides a good port for Darknet.

I am using Python3 though have earlier have used OpenCV with Python2 versions.

## Preparation/Setup

### OpenCV

Good intro to OpenCV there on https://docs.opencv.org/master/d9/df8/tutorial_root.html

[Adrian Rosebrock](https://www.pyimagesearch.com/author/adrian/) put a good step by step guide on his blog [pip install opencv](https://www.pyimagesearch.com/2018/09/19/pip-install-opencv/)

Once you have installed Python and OpenCV, you should see below;

```python
$ workon
cv
dl4cv
$ workon cv
(cv) $ python
Python 3.7.4 (default, Jul  9 2019, 18:13:23) 
[Clang 10.0.1 (clang-1001.0.46.4)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import cv2
>>> cv2.__version__
'4.1.0'
>>> 
```

### Download Pre-trained Models

Create a project directory e.g. yolo-realtime-object-detection and download the following files to the directory.

- Pre-trained network’s weights (this is ~250mb in size)
  yolov3.weights - [https://pjreddie.com/media/files/yolov3.weights](https://pjreddie.com/media/files/yolov3.weights)

- Network configuration
  yolov3.cfg - [https://github.com/pjreddie/darknet/blob/master/cfg/yolov3.cfg?raw=true](https://github.com/pjreddie/darknet/blob/master/cfg/yolov3.cfg?raw=true)

- Names from COCO dataset
  coco.names - [https://github.com/pjreddie/darknet/blob/master/data/coco.names?raw=true](https://github.com/pjreddie/darknet/blob/master/data/coco.names?raw=true)

### Object detection

To be updated