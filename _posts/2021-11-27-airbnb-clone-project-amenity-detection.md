---
layout: post
title: airbnb Clone Project - Amenity Detection
subtitle: Object Detection Project about Custom Dataset
cover-img: /assets/img/amenity_thumb.png
thumbnail-img: /assets/img/amenity_thumb.png
share-img: /assets/img/amenity_thumb.png
tags: [object detection, custom dataset, centernet]
---

# Amenity Detection - airbnb Clone Project

## Introduction for Object Detection Problem Areas

In the field of computer vision, Object Detection is a representative problem area that detects the location of objects present in an object and the type of object.. 

At this time, what is output as a prediction result of the object detection is in the form of **[the vertex coordinates of the bounding box (x_min, y_min, x_max, y_max), the label of the object, the degree of confidence in the detection result]**, which represents the locations of the objects present in one image.

![Untitled](../assets/img/Untitled.png)

Figure 1 - Prediction Results of Object Detection Model - (Location of Bounding Box, Type of Object, Degree of Confidence) [1]

Object Detection technology is actively used for real-world in various fields such as autonomous driving and unmanned store operation.

![Untitled 1](../assets/img/Untitled%201.png)

Figure 2 - Tesla Self-driving Using Object Detection Technology [2]

![Untitled 2](../assets/img/Untitled%202.png)

Figure 3 - AOperate unmanned stores using Amazon Go Object Detection technology [3]

## Airbnb Amenity Detection

**airbnb** is a world-class company that provides accommodation sharing services. The airbnb data science team is making various attempts to improve its service quality using the latest deep learning and machine learning technologies. 

Among their services, they have developed a feature that detects Amenities in photos uploaded by **hosts who want to rent rooms using Object Detection technology, and automatically allows customers who want to rent rooms to check what Amenities exist in their rooms without entering them one by one. [4]

For example, whether a microwave oven, one of the convenience items, exists in a room can be an important criterion for choosing a room.

The airbnb data science team carried out the Amenity Detection project using TensorFlow. [4] The airbnb team's Amenity Detection project was selected as a representative best case of solving real problems using TensorFlow and was also posted on the TensorFlow official website.

![Untitled 3](../assets/img/Untitled%203.png)

Figure 4 - Airbnb's Amenity Detection Project selected as a representative best case using TensorFlow.[3]

The airbnb team organized the project in detail on their blog and released it.[4] Therefore, based on the **blog post of the airbnb data science team, I proceeded with the Amenity Detection project as a clone project.

## TensorFlow Object Detection API

TensorFlow Object Detection API is an API that enables object detection using the latest deep learning model using TensorFlow released by Google.

It provides pre-trained parameters of the latest deep learning models for object detection, such as Fast-RCNN, SSD, EfficientDet, and CenterNet, and code and setup files for learning.

![Untitled 4](../assets/img/Untitled%204.png)

Figure 5 - Example of detection using the TensorFlow Object Detection API. [6]

The airbnb data science team reviewed Object Detection using Fast R-CNN and SSD models. However, this clone project has been trained and evaluated using the **more up-to-date model CenterNet[7] model proposed after airbnb's posting.

# Google Open Images Dataset

The Google Open Image Dataset is a dataset that contains a large amount of images released by Google and a bounding box for 600 labels. Based on Open Image Dataset V4, it has 1,743,042 Training Images and 14,610,229 Bounding Boxes. [8]

![Untitled 5](../assets/img/Untitled%205.png)

Figure 6 - Information on Google Open Images Dataset V4

Just like the airbnb data science team, I extracted only 30 Amenity labels from Google Open Images Dataset V4. The 30 amenity classes targeted for detection are as follows.

> ['Toilet', 'Swimming pool', 'Bed', 'Billiard table', 'Sink',
'Fountain', 'Oven', 'Ceiling fan', 'Television', 'Microwave oven',
'Gas stove', 'Refrigerator', 'Kitchen & dining room table', 'Washing machine', 'Bathtub',
'Stairs', 'Fireplace', 'Pillow', 'Mirror', 'Shower',
'Couch', 'Countertop', 'Coffeemaker', 'Dishwasher', 'Sofa bed',
'Tree house', 'Towel', 'Porch', 'Wine rack', 'Jacuzzi']

As a result of selecting images including the above 30 amenity classes from a total of 1,743,042 images, **a total of 34,835 images** were selected as images for learning. Among them, **90% was used as training data and 10% as test data for evaluation**.

# Training

Using the CenterNet model, I trained 140,000 steps using 31,351 images, or 90% of 34,835 images containing 30 Amenity classes.

![Untitled 6](../assets/img/Untitled%206.png)

Figure 7 - A screenshot of the TensorBoard training process for 140,000 steps.

# Evaluation

After 140,000 steps of training, the following evaluation results were obtained for 3,483 test images, or 10% of 34,835 images.

![Untitled 7](../assets/img/Untitled%207.png)

Figure 8 - A screenshot of the TensorBoard process.

For the entire test image, the mAP value of about **14.32 was obtained when IoU 0.5 or more was considered the correct answer.

When IOU 0.5 or higher was considered the correct answer for each class, a mAP value of 61.28 for the Swimming pool label, a mAP value of 5.33 for the Bathtub label, and a mAP value of 19.38 for the Oven label could be obtained.

# Future Work

As shown in the example above, you can see that the mAP value varies greatly by individual label. This may have several causes, but one of the main causes can be that the number of training images corresponding to each label varies greatly. Therefore, as the airbnb data science team did, I plan to collect additional images, label the correct answer, and train them using additional data to improve mAP in the future.

# My Work Code 

training - https://colab.research.google.com/drive/1jvDUqGYr6pvkffFtBFcElKJ09FCqPKPo?usp=sharing

evaluation - https://colab.research.google.com/drive/1-_g4ifyi61HFlIHLMhiE-Jk6_5HLTL2S?usp=sharing 

# References

[1] [https://www.inflearn.com/course/욜로-딥러닝-논문구현?inst=60c23368](https://www.inflearn.com/course/%EC%9A%9C%EB%A1%9C-%EB%94%A5%EB%9F%AC%EB%8B%9D-%EB%85%BC%EB%AC%B8%EA%B5%AC%ED%98%84?inst=60c23368)

[2] [https://www.tesla.com/ko_KR/autopilot](https://www.tesla.com/ko_KR/autopilot)

[3] [https://www.youtube.com/watch?v=NrmMk1Myrxc](https://www.youtube.com/watch?v=NrmMk1Myrxc)

[4] [https://medium.com/airbnb-engineering/amenity-detection-and-beyond-new-frontiers-of-computer-vision-at-airbnb-144a4441b72e](https://medium.com/airbnb-engineering/amenity-detection-and-beyond-new-frontiers-of-computer-vision-at-airbnb-144a4441b72e)

[5] [https://www.tensorflow.org/about/case-studies?hl=ko](https://www.tensorflow.org/about/case-studies?hl=ko)

[6] [https://github.com/tensorflow/models/tree/master/research/object_detection](https://github.com/tensorflow/models/tree/master/research/object_detection)

[7] [https://arxiv.org/abs/1904.07850](https://arxiv.org/abs/1904.07850)

[8] [https://storage.googleapis.com/openimages/web/factsfigures_v4.html](https://storage.googleapis.com/openimages/web/factsfigures_v4.html)
