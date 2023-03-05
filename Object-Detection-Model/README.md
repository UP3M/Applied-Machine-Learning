## 1. Take photos of your environment of two or more objects. (at least 100 instances between all objects) 

## 2. Annotate them on roboflow (Preparing a custom dataset in Roboflow)
Building a custom dataset can be a painful process. It might take dozens or even hundreds of hours to collect images, label them, and export them in the proper format. Fortunately, Roboflow makes this process as straightforward and fast as possible. Let me show you how!

### Step 1: Creating project

Before you start, you need to create a Roboflow [account](https://app.roboflow.com/login). Once you do that, you can create a new project in the Roboflow [dashboard](https://app.roboflow.com/). Keep in mind to choose the right project type. In our case, Object Detection.

### Step 2: Uploading images

Next, add the data to your newly created project. You can do it via API or through our [web interface](https://docs.roboflow.com/adding-data/object-detection).

If you drag and drop a directory with a dataset in a supported format, the Roboflow dashboard will automatically read the images and annotations together. 

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/2.jpeg"
  >
</div>

### Step 3: Labeling

If you only have images, you can label them in [Roboflow Annotate](https://docs.roboflow.com/annotate).

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/3%20(2).jpeg"
  >
</div>

### Step 4: Generate new dataset version

Now that we have our images and annotations added, we can Generate a Dataset Version. When Generating a Version, you may elect to add preprocessing and augmentations. This step is completely optional, however, it can allow you to significantly improve the robustness of your model.

<div align="center">
  <img
    width="640"
    src="https://media.roboflow.com/preparing-custom-dataset-example/generate-new-version.gif?ik-sdk-version=javascript-1.4.3&updatedAt=1673003597834"
  >
</div>

### Step 5: Exporting dataset

Once the dataset version is generated, we have a hosted dataset we can load directly into our notebook for easy training. Click `Export` and select the `YOLO v8 PyTorch` dataset format.

## 3. Train a Faster RCNN model using detectron2

Link to Colab for Detectron 2: https://colab.research.google.com/drive/1f5boHc71qriQXU4A1KtGGl9dV6rAgnh9?usp=sharing

To train our detector we take the following steps:

### 1. Install Detectron2 dependencies
### 2. Download custom Detectron2 object detection data
### 3. Visualize Detectron2 training data
### 4. Write our Detectron2 Training configuration
### 5. Run Detectron2 training
### 6. Evaluate Detectron2 performance
### 7. Run Detectron2 inference on test images

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/detectron_h.jpeg"
  >
</div>

## 4. Train Yolo v8

Link to Colab for Yolo v8: https://colab.research.google.com/drive/11jAfrp_1mgF60d_V7Gp_n9xpLaMUHK9v#scrollTo=oe9vkEvFABbN

Before we start, to train our detector we take the following steps:

### 1. Install YOLOv8
### 2. CLI Basics
### 3. Inference with Pre-trained COCO Model
### 4. Roboflow Universe
### 5. Preparing a custom dataset
### 6. Custom Training
### 7. Validate Custom Model
### 8. Inference with Custom Model

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/yolo8_h.jpeg"
  >
</div>

## 5. Evaluation of both models based on mAP and speed.

Yolov8 and Detectron 2 are both popular object detection frameworks, but they differ in their approach and design.

In terms of Mean Average Precision (mAP), which is a commonly used metric to evaluate object detection models, the performance of Yolov8 and Detectron 2 can vary depending on the specific implementation and dataset used for evaluation. Generally speaking, Detectron 2 is considered to be a state-of-the-art framework that achieves high mAP scores on many benchmark datasets. In this case, Detectron 2 achieves a mask mAP of 60.89,

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/det_e_map.jpeg"
  >
</div>

while Yolov8 achieves a bbox mAP of 0.49.

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/yolo8_e.jpeg"
  >
</div>

In terms of speed, Yolov8 is known for its fast inference times. It is optimized for speed by using a single-stage architecture that performs detection directly on the image without region proposal networks. Yolov8 can achieve real-time performance with a high degree of accuracy, making it well-suited for applications that require fast object detection. 

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/yolo8_e.jpeg"
  >
</div>

On the other hand, Detectron 2 is a more complex framework that uses a two-stage architecture with region proposal networks, which can lead to longer inference times. However, recent versions of Detectron 2 have improved the speed and efficiency of the framework, making it more competitive with other state-of-the-art object detection frameworks.

<div align="center">
  <img
    width="640"
    src="https://github.com/UP3M/Applied-Machine-Learning/blob/master/src/det_e_time.jpeg"
  >
</div>

In summary, Yolov8 is faster but may not achieve the same level of mAP as Detectron 2. Detectron 2 is more accurate but may be slower. The choice between Yolov8 and Detectron 2 will depend on the specific needs and constraints of the application at hand.
