# 🛣️ Self-Driving Car using Deep Learning  

## 📖 Project Overview  
This project implements a **behavioral cloning** model for self-driving cars.  
The goal is to train a deep learning model that predicts the **steering angle** of a car based on input images from the car’s front camera.  

The pipeline involves:  
- Collecting and preprocessing driving images.  
- Applying data augmentation (zoom, pan, flip, brightness).  
- Training a CNN model (inspired by NVIDIA’s Self Driving Car architecture).  
- Running the trained model in a simulator using **SocketIO + Flask** to control the car in real-time.  

---

## 🚀 Tech Stack  
- **Programming Language**: Python  
- **Deep Learning Framework**: TensorFlow / Keras  
- **Server**: Flask + SocketIO  
- **Other Libraries**: OpenCV, NumPy, Pandas, Matplotlib, imgaug  

---

## 📂 Dataset  
- Dataset is collected from a **driving simulator** (Udacity Self Driving Car Simulator).  
- For each frame, 3 images are captured:  
  - **Center Camera**  
  - **Left Camera** (with steering correction `+0.15`)  
  - **Right Camera** (with steering correction `-0.15`)  

Steering angles are recorded in a CSV file.  

---

## ⚙️ Data Preprocessing  
1. **Cropping** images to remove sky & dashboard.  
2. **Resizing** to (200x66) as per NVIDIA architecture.  
3. **Normalization** (`pixel / 255.0`).  
4. **Augmentations** applied randomly:
   - Zoom  
   - Pan (Shift)  
   - Brightness Adjustment  
   - Horizontal Flip  

---

## 🏗️ Model Architecture  
Implemented a CNN based on **NVIDIA’s End-to-End Self Driving Car model**:  
- 5 Convolutional layers (feature extraction)  
- Flatten + Fully Connected Layers  
- Output: **Single Neuron** (predicting steering angle)  

---

## 🏋️ Training  
- **Loss Function**: Mean Squared Error (MSE)  
- **Optimizer**: Adam  
- **Batch Size**: 32  
- **Epochs**: 10–30 (tunable)  
- **Data Generators** used for efficient training.  

---

## 🎮 Testing in Simulator  
- A Flask + SocketIO server receives images from the simulator.  
- Images are preprocessed and passed into the trained model.  
- Predicted steering angle + throttle is sent back to the simulator in real-time.  

Run the server:
```bash
python testing_5.py
