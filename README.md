<img src="https://img.shields.io/badge/Python-white?logo=python&logoColor=3776AB" style="height: 25px; width: auto;">  <img src="images/logos--gradio-icon.png" alt="Gradio logo" style="height: 15px; background-color: #D3D3D3; padding: 4px; border-radius: 5px;">  <img src="https://img.shields.io/badge/Gradio-white?" style="height: 25px; width: auto;">  <img src="https://img.shields.io/badge/FastAI-white?logo=python&logoColor=3776AB" style="height: 25px; width: auto;">  <img src="https://img.shields.io/badge/Pydicom-white?logo=python&logoColor=3776AB" style="height: 25px; width: auto;">


# 🚀 Diagnostic Assistant for Idiopathic Pulmonary Fibrosis

This is a **project demo** developed in **48 hours** for a **BOEHRINGER INGELHEIM Hackathon**.

Click on the image below to watch a **demonstration** of the application on YouTube:

[![Watch the demonstration on YouTube](https://img.youtube.com/vi/kS4T7r7cydg/0.jpg)](https://www.youtube.com/watch?v=kS4T7r7cydg)

## 📜 **Project Description**
Clinicians face a significant workload when identifying and managing patients with potential lung diseases such as **Idiopathic Pulmonary Fibrosis (IPF)**. This project aims to provide a tool based on **data-driven decision-making** to help them make faster and more informed decisions. The tool can analyze clinical data and imaging to determine if a patient should:

- Be closely monitored.
- Be referred to a specialist.
- Continue with routine follow-up.

By using this solution, the goal is to optimize diagnostic time, prioritize the most urgent cases, and improve clinical patient management.

## 🎯 **Project Objectives**
- Assist clinicians in prioritizing patients through clinical and imaging data analysis.
- Identify subtle patterns indicating a higher risk of IPF.
- Generate risk-based recommendations to support clinical decision-making.
- Improve efficiency and accuracy in identifying patients needing intensive follow-up or referral.

## 🛠️ **Approach and Solution**
The implemented solution is a web application built with **Gradio** that integrates deep learning and machine learning models to analyze patient imaging and clinical data.

### 🧩 **Key Components**
- **Pre-trained Computer Vision Models**: Models like ResNet34, SqueezeNet, and DenseNet121 were trained on **Kaggle**, leveraging GPUs, and later incorporated into the Gradio app for feature extraction from CT scan images.
- **LightGBM Model**: A LightGBM model was trained using the probabilities from vision models and clinical features to predict the likelihood of IPF.
- **Llama 3 Model**: An LLM model is used to consolidate all outputs into natural language messages for clear communication between patients and clinicians.
- **Animation Generation**: The `AnimateScans` class was created to generate GIF animations of CT scans, enabling dynamic visualization of the images.

## 📂 **Project Structure**
- `gradio_app.py`: Main script that runs the Gradio application.
- `utils.py`: Module containing the `AnimateScans` class for processing DICOM images and generating animations.
- `models/`: Folder containing pre-trained models and the LightGBM model.
- `data/`: Folder with sample patient data.
- `dicom/`: Directory with patient DICOM images, organized by patient ID.
- `animations/`: Folder where generated GIF animations are saved.

## ⚙️ **Installation and Usage Instructions**

### 📋 **Prerequisites**
- Python 3.8 or later.
- Conda or Miniconda installed on your system.

### 📥 **Installation**
Clone the repository:
```bash
git clone https://github.com/jordisc97/team9_boehringer.git
cd team9_boehringer
```
Create and activate the conda environment:
```bash
conda env create -f environment.yml
conda activate fibrosis_pulmonar_env
```
### **Verify the Models**
- The pre-trained models are already included in the `models/` folder of the repository. Ensure the following files are available:
  - `resnet34_model.pkl`
  - `squeezenet1_0_model.pkl`
  - `densenet121_model.pkl`
  - `lgbm_model.txt`

### **Download DICOM Files and Data**
1. Download the necessary folders from Google Drive using this link:  
   [Sample DICOM Files](https://drive.google.com/drive/folders/1ZXwMteDDFa1I9ihyeYkD70Urql4fUho5?usp=sharing)
2. Place the downloaded folders in the specified structure:
   - DICOM images should be stored in the `dicom/` folder, with a subdirectory for each patient based on their ID (e.g., `dicom/ID000123456789/`).
   - The data file `sample_patient_data.csv` should be placed in the `data/` folder.

### ▶️ **Run the Application**
Run the following command from the project root to start the application:
```bash
python gradio_app.py
```
The application will run locally and be available at http://localhost:7860.

## 🖥️ **Using the Application**
1. **Select Patient ID**: Use the dropdown menu to select the ID of the patient whose images and data you want to analyze.
2. **Enter Clinical Data**: Provide the required information, such as age, FVC, gender, smoking status, and baseline week.
3. **Get Results**: Click the button to generate the prediction. The application will display:
   - The probability that the patient has IPF.
   - A risk message indicating if more frequent monitoring is recommended.
   - A GIF animation of the patient’s CT scans.

## 🧠 **Key Technical Decisions**
- **Integration of Vision Models and Clinical Data**: Combining computer vision models with clinical data in a LightGBM model leverages multiple data sources to enhance diagnostic accuracy.
- **Use of Gradio for the User Interface**: Gradio simplifies the creation of interactive web interfaces for machine learning models without needing to develop a web application from scratch.
- **Processing DICOM Images**: Implementing the `AnimateScans` class to handle DICOM images and generate animations improves radiologists' visual interpretation of CT scans.
- **Modular Code Structure**: Separating the code into modules (`app.py` and `utils.py`) enhances project clarity and maintainability.