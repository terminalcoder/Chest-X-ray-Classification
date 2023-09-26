# Chest-X-ray-Classification
Elimelech Berlin  
September 2023

## Overview
This report aims to construct an image classification model capable of accurately diagnosing pneumonia in pediatric patients, from chest X-ray images. Utilizing an iterative aproach, a convolutional neural network capable of identifying 91% of pneumonial scans present in the test group of the images, emerges as the most performant model.

## Context
Pneumonia can be detected by visual inspection of chest X-ray scans - scans of those with the disease exhibit abnormal opacification in the lung cavity, while imagery of healthy lungs is clear:

![X-ray_samples](https://github.com/terminalcoder/Chest-X-ray-Classification/blob/master/images/scan_samples_small.png)

A model capable of classifying chest X-rays as either normal or displaying evidence of pneumonia would enable medical professionals to delegate reading such scans to an automated system thereby attaining greater efficiency in healthcare. Additionaly, such a tool may prove useful in detecting disease in patients whose scan abnormality is slight enough to be overlooked by even trained medical technicians.

## Data
The images used for this report come from Kaggle's [Chest X-Ray Images (Pneumonia)](https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia) dataset. The images are chest X-ray scans of pediatric patients between ages 1 and 5 years old obtained from routine patient scans at Guangzhou Women and Children’s Medical Center, Guangzhou (China).  
The nearly 6K images are classified into two categories: Normal or Pneumonia.  
As provided by Kaggle, the images are divided into three subsets:
* train - 5,216 images
* validate - 16 images
* test - 631 images

-To correct for the overly small validation set (just 16 images), enough images were moved from the training set to the validation set to make the split equal to aproximately 80/20, before training the model.

-Note, that there is significant class imbalance present in the training data as seen in the following plot (this can be address by setting the `class_weights` hyperparameter while training the model):

![class_imbalance_plot](https://github.com/terminalcoder/Chest-X-ray-Classification/blob/master/images/train_class_dist.png)

## Modeling
The iterative process followed to build a model capable of classifying chest X-ray images as Normal or Pneumonia, employed Convolutional Neural Networking (CNN).
The following process was followed:
* Begin with a basic CNN
* Build a 2nd such model with additional layers (more complexity)
* Build a 3rd model with even more layers (even more complexity)
* Identify most performant model & seek to improve it further by adding dropout layers to the model, implementing regularization, & setting the `class_weights` hyperparameter during training

Predictions were made on the test set with each model for assessing & comparing model performance.

## Model Results/Evaluation
Each model's performance was assessed based on its __recall__ score (percent of true positives identified as such). This is the metric of choice for a model to be used in a system intended to assist medical professionals in identifying patients whose condition warrants further intervention. (Need to maximize the number of sick patients who will get treatment.)

The above process revealed that the 3rd model iteration (without the additional adjustments), is the best model to classify the given images, with a recall score of 91%.

Shown is a plot of the model's performance:

![model_3_confusion matrix](https://github.com/terminalcoder/Chest-X-ray-Classification/blob/master/images/model_3_conf_mat.png)

## Limitations/Next Steps
Several points should be taken into account when considering the findings of this report:
* The performance metrics of the best model vary drastically (e.g. recall for negative predictions is 10%). In this process, the model's recall for identifying positive cases of pneumonia is the metric by which performance is assessed. Certain use cases may indicate that a different metric be used. (e.g. If a given treatment is only warranted in the absence of pneumonia, a metric that is focused on negative predictions makes more sense.)
* The performance of CNN models is greatly improved with the use of more data (images) in the training process. Although the available data used for this project is limited, an attempt to generate more training data by creating augmented images from the given image collection may provide sufficient to achieve improved results.
* In an effort to reduce training times, only a limited number of models were attempted. Running additional models with greater levels of complexity & a greater number of hyperparameters adjusted, may have eventually yielded a more precise model.

### For More Information
Please review the full analysis in the [Jupyter Notebook](https://github.com/terminalcoder/Chest-X-ray-Classification/blob/main/notebook.ipynb) or the [presentation](https://github.com/terminalcoder/Chest-X-ray-Classification/blob/main/presentation.pdf).  
For any additional questions, please contact Elimelech Berlin, melech.berlin@gmail.com.

***
## Repository Structure
```
├── data                                      <- sourced externally
├── images                                    <- sourced from code
├── .gitignore                                <- files to ignore
├── README.md                                 <- the top-level README for reviewers of this project
├── notebook.ipynb                            <- narrative documentation of analysis in Jupyter notebook
└── presentation.pdf                          <- PDF version of project presentation
```
