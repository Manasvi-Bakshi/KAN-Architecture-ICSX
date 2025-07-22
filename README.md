# KAN-Architecture-ICSX
## ICSX Network Traffic Classification with Machine Learning & KAN

This project focuses on classifying encrypted network traffic data using traditional machine learning models and a Kolmogorov-Arnold Network (KAN). It is based on the ICSX Dataset (Time-Based Features) and aims to identify darkweb traffic types in a controlled environments with high accuracy and interpretability.

###  Dataset

- Source: [ISCX 2016 VPN-nonVPN dataset](https://www.unb.ca/cic/datasets/vpn.html)
- File Used: `TimeBasedFeatures-Dataset-15s-AllinOne.arff`

I have tested the code with other respective files as well it should work fine, just need to change the file path names. The file is present in Scenario-B ARFF zip. The dataset consists of time-based network flow features extracted every 15 seconds which captures sessions across 14 traffic categories including normal and VPN variants. The Traffic is generated using real applications like Skype, Facebook, Hangouts, FileZilla, uTorrent, and more. Each sample includes time-based features extracted using ISCXFlowMeter

| Feature Type     | Description                            |
|------------------|----------------------------------------|
| Statistical      | Mean, Std, Max, Min of flow timings    |
| Flow Metadata    | Packet counts, durations, idle times   |
| Target Column    | `class1` (categorical traffic type)    |


## KAN Architecture

[KAN (Kolmogorov-Arnold Network)](https://github.com/KindXiaoming/pykan) is a novel architecture designed to learn nonlinear mappings with high interpretability. In this project, KAN was trained using `LBFGS` optimizer and outperformed many classical models in generalization on the ICSX dataset.

### Machine Learning Models Used

- Logistic Regression
- Random Forest
- Support Vector Machine (SVM)
- XGBoost
- K-Nearest Neighbors (KNN)

Each model was trained on the same preprocessed dataset, with performance evaluated on both training and testing splits using accuracy.

### Model Evaluation

| Model                  | Training Acc | Testing Acc | Overfitting Gap |
|------------------------|--------------|-------------|------------------|
| XGBoost                | 0.9922       | 0.9280      | 0.0642           |
| Random Forest          | 0.9981       | 0.9106      | 0.0875           |
| K-Nearest Neighbors    | 0.8901       | 0.8402      | 0.0499           |
| Logistic Regression    | 0.6166       | 0.6140      | 0.0027           |
| SVM                    | 0.5880       | 0.5868      | 0.0012           |
| KAN                    | 0.9007       | 0.8421      | 0.0586           |



#### How to Run This Project On Google Colab:
1. Upload the dataset `.arff` file to your Colab environment.
2. Run the notebook cells in order.
3. Install KAN via:
   ```bash
   !pip install git+https://github.com/KindXiaoming/pykan.git

