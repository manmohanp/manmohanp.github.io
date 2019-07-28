---
layout: post
title: Deep Learning-based Real Time object detection with YOLO and OpenCV
subtitle: 4 min read
category: technology
hide: true

---

<img src="/Users/manamohanpanda/git/manmohanp/manmohanp.github.io/assets/img/opencv.png" alt="OpenCV" width="150" height="150"/> <img src="https://manmohanp.github.io/assets/img/yolo.png" alt="OpenCV" width="150" height="150"/>

**You only look once** ([YOLO](https://pjreddie.com/darknet/yolo/)) is a state-of-the-art, real-time object detection system.

As per official Yolo site:

"Our model has several advantages over classifier-based systems. It looks at the whole image at test time so its predictions are informed by global context in the image. It also makes predictions with a single network evaluation unlike systems like [R-CNN](https://github.com/rbgirshick/rcnn) which require thousands for a single image. This makes it extremely fast, more than 1000x faster than R-CNN and 100x faster than [Fast R-CNN](https://github.com/rbgirshick/fast-rcnn). See our [paper](https://pjreddie.com/media/files/papers/YOLOv3.pdf) for more details on the full system."

Object detector is a combination of **object locator** and **object recognizer** and Yolo does this by runing forward the whole image only once through the deep nural network ([DNN](https://papers.nips.cc/paper/5207-deep-neural-networks-for-object-detection.pdf)).

## Realtime Object Detection

We will use OpenCV for this, especially DNN, Yolo3, [Darknet](https://pjreddie.com/darknet/). And since we are going to Python OpenCV provides a good port for Darknet.

## Preparation/Setup

### OpenCV

While there are other official document