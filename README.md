# Chest-X-ray-Classification
Elimelech Berlin  
September 2023

## Overview
This report aims to construct an image classification model capable of accurately diagnosing pneumonia in pediatric patients, from chest X-ray images. Utilizing an iterative aproach, a convolutional neural network capable of identifying 91% of pneumonial scans present in the test group of the images, emerges as the most performant model.

## Context
A model capable of classifying chest X-rays as either normal or displaying evidence of pneumonia would enable medical professionals to delegate reading such scans to an automated system thereby attaining greater efficiency in healthcare. Additionaly, such a tool may prove useful in detecting disease in patients whose scan abnormality is slight enough to be overlooked by even trained medical technicians.

## Data
*** 
The images used for this report come from Kaggle's [Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia) dataset. The images are chest X-ray scans of pediatric patients between ages 1 and 5 years old obtained from routine patient scans at Guangzhou Women and Children’s Medical Center, Guangzhou (China).  
The nearly 6K images are classified into two categories: Normal or Pneumonia.  
As provided by Kaggle, the images are divided into three subsets:
* train - 5,216 images
* validate - 16 images
* test - 631 images
***
### For More Information
Please review the full analysis in the [Jupyter Notebook](https://github.com/terminalcoder/Churn-in-Telecom/blob/main/notebook.ipynb) or the [presentation](https://github.com/terminalcoder/Churn-in-Telecom/blob/main/presentation.pdf).  
For any additional questions, please contact Elimelech Berlin, melech.berlin@gmail.com.

***
## Repository Structure
```
├── README.md                                 <- the top-level README for reviewers of this project
├── notebook.ipynb                            <- narrative documentation of analysis in Jupyter notebook
├── presentation.pdf                          <- PDF version of project presentation
├── data                                      <- sourced externally
├── .gitignore                                <- files to ignore
└── images                                    <- sourced from code
```
