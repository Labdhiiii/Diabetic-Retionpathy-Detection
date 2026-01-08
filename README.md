# Diabetic Retinopathy Detection

## Objectives

* Detect important retinal features such as microaneurysms, hemorrhages, and exudates
* Use these features to classify DR into severity stages
* Build a structured and explainable deep learning pipeline
* Support early screening and reduce manual diagnostic workload

---

## Project Structure & File Description

```
Diabetic-Retionpathy-Detection/
│
├── Dataset/
│   ├── A. Segmentation Dataset
│   ├── B. Disease Grading Dataset
│
├── Model/
│   ├── itworksunet.pth          # Trained U-Net model for lesion detection
│   ├── dr_stage_model.pkl       # Final trained DR stage prediction model
│
├── correct_dataset.ipynb        # U-Net implementation & retinal feature detection - 1
├── lesion_features_from_seg.csv # Extracted lesion features from segmentation
├── dr_stage_training_data.csv   # Training data for disease grading
├── dr_stage.ipynb               # DR stage prediction - 3
├── unet_model_results.ipynb     # Sample testing & visualization of U-Net Model - 2
│
├── README.md
```

---
## About the Dataset

### **A. Segmentation Dataset**

**Purpose:** Retinal feature detection

* Used to detect retinal abnormalities such as: Microaneurysms, Hemorrhages, Soft and Hard Exudates.
* Answers: *“Where are the disease-related features present?”*
* Output:
  * Segmentation results
  * Extracted lesion-based numerical features

These features are later used for disease grading.

---

### **B. Disease Grading Dataset**

**Purpose:** Predict DR severity stage

* Contains:
  * Fundus images
  * Corresponding DR stage labels in csv file.
* Learns the relationship between:
  * Retinal features
  * Disease severity levels
 * Answers: *“How severe is the disease?”*

Stages predicted:

* No DR -0
* Mild DR -1
* Moderate DR -2
* Severe DR -3
* Proliferative DR -4

---

## Models Used

### 1. itworksunet.pth

* Trained **U-Net segmentation model**
* Used for:
  * Detecting retinal abnormalities
* Performs **feature localization**


### 2. dr_stage_model.pkl

* Trained **disease grading model**
* Uses:
  * Fundus image information
  * Extracted lesion features
* Outputs:
  * Final DR severity stage

---

## Sequential Flow

###  1.correct_dataset.ipynb

**Role:** Retinal feature detection

* Contains:

  * U-Net architecture
  * Segmentation logic
* Detects abnormal retinal regions
* Extracts lesion-based features
* Generates:

  * `itworksunet.pth`

###  2. unet_model_results.ipynb

**Role:** Demonstration & testing

* Displays sample segmentation outputs
* Used for:

  * Verifying U-Net performance

### lesion_features_from_seg.csv

* Stores numerical features extracted from segmentation
* Acts as a **bridge between segmentation and grading**
* Improves interpretability of the system

###  3. dr_stage.ipynb

**Role:** Disease severity prediction

* Trains the classification model
* Uses lesion features to predict DR stage
* Generates:

  * `dr_stage_model.pkl`

### dr_stage_training_data.csv

* Final dataset for DR stage prediction
* Combines:

  * Image references
  * Lesion features
  * DR stage labels

---

## Overall Workflow

> The system first identifies abnormal retinal features using segmentation.
> These detected features are then used to predict the severity stage of Diabetic Retinopathy.

---
