# Semantic Segmentation of Tomato Fruits
Semantic segmentation is a pivotal task in computer vision that involves classifying each pixel in an image into specific categories. This enables detailed scene understanding by identifying and delineating the boundaries of various objects.

The goal of this project is to develop effective semantic segmentation techniques to accurately identify and segment components of tomato fruit images into categories such as **tomatoes and stalks**. A unique aspect of this project is the use of the **Segment Anything Model (SAM)** by Meta AI for annotating images, significantly reducing the time and effort required for manual annotation compared to traditional tools like LabelMe or VGG Image Annotator.

## Project Objectives
1. **Implementation of Segment Anything Model (SAM) as an Annotation Tool**: SAM was employed to generate segmentation masks for tomato and stalk images, serving as a semi-automated alternative to traditional manual annotation methods. 
2. **Implementation of Deep Learning Models (Mask R-CNN and YOLOv8-seg)**: This project involved developing and fine-tuning Mask R-CNN and YOLOv8 architectures to perform the semantic segmentation of tomato fruits. Both models were trained on the annotated dataset generated by SAM.
3. **Evaluation of Models Using Quantitative Metrics**: The performance of the segmentation models was evaluated using quantitative metrics such as precision, recall, and mean average precision (mAP). 

## Key steps taken to perform the segmentation Process
1.	**Dataset Preparation and splitting**: The dataset utilized for this project is an industrial tomato dataset with a subset of 356 images. The dataset was divided into training, validation, and test sets at 70% for training, 10% for validation, and 20% for testing
2.	**Generation of Segmentation Masks using Segment Anything Model (SAM)**: SAM was used to automatically generate binary masks for objects in the images
3.	**Manual Filtering of segmentation masks**: The manual filtering process involved carefully selecting masks corresponding to tomatoes and stalks from the entire generated masks of all objects found within the images 
4.	**Conversion of masks to COCO JSON format**: This process involves converting the manually filtered binary masks of tomatoes and stalks into the COCO JSON format. The COCO format is advantageous because it supports complex annotations, such as multiple objects per image and detailed segmentation masks, which is crucial for this task. This format facilitates the training of the Mask R-CNN model by providing a structured representation of images and their corresponding annotations.
5.	**Conversion of JSON format to Yolo-V8 Polygon Format**: YOLOv8 requires a specific annotation format—polygonal coordinates normalized to the image dimensions. This conversion ensures compatibility with YOLOv8 and allows the model to correctly interpret and process the training data for the segmentation task.
6.	**Model Training**
   - 	**Mask RCNN**: For this project, the Mask R-CNN model was implemented using a ResNet-101 backbone with a Feature Pyramid Network (FPN) using Pytorch as the deep learning framework. The model was trained on the custom dataset where tomatoes and stalks binary masks were converted into COCO JSON format and organized into training, validation, and test sets. The dataset was processed and loaded using the COCO format. During training, the model learned to classify and segment tomatoes and stalks by optimizing both the bounding box regression
   - 	**YOLO V8-seg**: To train this sophisticated model, the yolov8x-seg.pt variant, pre-trained on the COCO dataset, was fine-tuned on the custom dataset of tomato fruit images.

## Inference/Prediction
`Inference on some samples from the test dataset`
![Screenshot 2024-08-25 132918](https://github.com/user-attachments/assets/6ace552c-4fa3-4445-b351-6e862c601669)
![Screenshot 2024-11-30 082114](https://github.com/user-attachments/assets/088b8dbd-a393-4545-8ee9-a79cf4c8bb32)


