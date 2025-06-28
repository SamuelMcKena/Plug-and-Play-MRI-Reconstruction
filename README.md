# MRI Reconstruction with Plug-and-Play Deep Learning

This repository contains code for reconstructing undersampled MRI images using a Plug-and-Play (PnP) approach with a deep learning denoiser (U-Net). The workflow includes data extraction, preprocessing, undersampling simulation, dataset preparation, model training, and evaluation.

## Features

- **Data Extraction:** Handles `.tar` archives of MRI k-space data and organizes them into training and validation folders.
- **Undersampling Simulation:** Applies variable-density undersampling masks to k-space data to simulate accelerated MRI acquisition.
- **Dataset Preparation:** Splits data into training and validation sets, and prepares paired original and undersampled samples.
- **Deep Learning Model:** Implements a U-Net denoiser using TensorFlow/Keras for image reconstruction.
- **Plug-and-Play Reconstruction:** Alternates between data consistency in k-space and learned denoising in image space.
- **Evaluation:** Computes quantitative metrics (MSE, MAE, SSIM) and visualizes reconstruction results and difference maps.
- **Experiment Tracking:** Integrates with [Weights & Biases](https://wandb.ai/) for experiment logging.

## Folder Structure

- `TestData/` and `ValData/`: Raw MRI data archives and extracted files.
- `split_data/`: Contains split training and validation sets, each with `original` and `undersampled` subfolders.
- Jupyter Notebook: Contains all code for data processing, model training, and evaluation.

## Main Steps

1. **Extract MRI Data:**  
    Extracts `.tar` files into specified directories.

2. **Simulate Undersampling:**  
    Applies a variable-density mask to k-space data to create undersampled datasets.

3. **Prepare Datasets:**  
    Splits data into training and validation sets, and prepares paired samples for model input.

4. **Model Training:**  
    Trains a U-Net model to map undersampled images to fully-sampled ground truth images.

5. **Plug-and-Play Reconstruction:**  
    Uses the trained model in an iterative PnP framework for MRI reconstruction.

6. **Evaluation & Visualization:**  
    Computes metrics and visualizes results, including difference maps.

## Requirements

- Python 3.7+
- numpy
- h5py
- matplotlib
- tensorflow
- keras
- opencv-python
- wandb
- scikit-image
- torch (for CUDA check, optional)