### Suitable_Crop_Area_Estimation_Using_Yolov12s
Implementing the latest Yolov12s version for the determination of detecting the crop and non-crop areas suitable for cultivation. This is the advanced application in the field of Artificial Intelligence and Deep Learning, making the use of the Yolov12s model because of its perks.

# 🌾 Crop Area Detection using YOLOv12s
This project implements the **YOLOv12s** model to accurately detect **crop** and **non-crop areas** from aerial or satellite imagery. It’s a cutting-edge application in **Artificial Intelligence** and **Deep Learning** aimed at enhancing agricultural planning and cultivation decisions.

# 🚀 Why YOLOv12s?
├── **Latest** state-of-the-art object detection model
├── Efficient with **FlashAttention**
├── Ideal for resource-constrained and real-time environments
├── Integrated with **Roboflow** for seamless dataset management

# 📁 Project Structure
├── train_yolov12_object_detection_model.ipynb   # Training + inference pipeline
├── README.md                                    # Project overview

# Yolo Ultralytics Documentation 
├── https://docs.ultralytics.com/modes/predict/#inference-arguments

# 🧠 Model Architecture
YOLOv12s brings significant improvements over previous YOLO versions:
├── Uses FlashAttention for faster attention computation.
├── Better performance on edge GPUs (Ampere or newer).
├── Enhanced detection accuracy for agricultural segmentation.

# 🔧 Environment Setup
## ├── 1. Configure Roboflow API Key (Get your key from Roboflow Settings and then store it in Colab)
import os
from google.colab import userdata
os.environ["ROBOFLOW_API_KEY"] = userdata.get("ROBOFLOW_API_KEY")  #your respective api key, you can get it by first logging in an activating account in -> https://app.roboflow.com/login

## ├── 2. Install Dependencies
!pip install roboflow supervision
!git clone https://github.com/YOLOv12/YOLOv12
%cd YOLOv12
!pip install -r requirements.txt

## ├── 3. GPU Check (Optional but Recommended)
!nvidia-smi

# 📊 Dataset
Dataset is fetched from Roboflow and consists of annotated images for:
Crop Areas (class 0)
Non-Crop Areas (class 1)

You can simply use the dataset by running the below code:
from roboflow import Roboflow
rf = Roboflow(api_key=ROBOFLOW_API_KEY)
project = rf.workspace("your-workspace").project("your-dataset")
dataset = project.version("x").download("yolov12")

# 🏋️‍♂️ Model Training
Training is done with the YOLOv12 CLI inside the cloned repo:
!python train.py --data data.yaml --epochs 100 --img 640 --batch 16 --weights yolov12s.pt

# 🔍 Inference
You can test on your own image or downloaded samples:
!python detect.py --weights runs/train/exp/weights/best.pt --img 640 --source test_image.jpg

# 📈 Results
The model achieves:
├── High accuracy in segmenting agriculturally viable land
├── Real-time inference on supported GPUs
├── Visualized output using the supervision package

# Applications
├── Smart Farming & Precision Agriculture
├── Crop Monitoring from Drones or Satellites
├── Land Suitability Analysis for Cultivation

# 🤝 Contributing
Got ideas for improvements or want to collaborate? Send me a message on my LinkedIn as I am super active there -> linkedin.com/in/om-subrato-dey/
