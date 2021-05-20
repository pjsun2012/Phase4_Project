# Chest X-rays Pneumonia Detection using Convolutional Neural Network
### Author: Pengju Sun
## Context
### What is Pneumonia?
Pneumonia is a severe lung infection, where it causes the tiny air sacs in the lungs to be inflamed and filled with fluids or pus[1]. This inflammation makes the patient unable to breathe enough oxygen to reach the bloodstream.
Facts about Pneumonia
Over 150 million people get infected with Pneumonia on an annual basis. It is the world's leading cause of death for children under the age of 5. In the US, Pneumonia is the most common cause of hospital admissions for adults and is the most common reason for children to be hospitalized[2].
### The Challenges
We know that Pneumonia is a common illness that affects many people in the US and worldwide. How do we detect this disease? Chest X-rays have long been considered the best tool to detect any form of Pneumonia. However, studies have shown that even experienced radiologists have a hard time correctly identify whether something is an infiltrate (a substance denser than air, such as pus or fluid) on the X-Ray[3]. This causes delays in diagnosis, which increases the disease severity. The risk of Pneumonia is immense for many, especially in developing countries with severe pollution and inadequate medical resources and personnel. For example, in Africa's 57 countries, a gap of 2.3 million doctors and nurses exists. The lack of doctors and nurses makes diagnosis and treatment of Pneumonia more difficult.
## Goal
Our goal is to build a deep learning model to automatically identify whether a patient is suffering from Pneumonia or not by checking check X-ray images. The model needs to be highly accurate because life really matters.
## Dataset
The data used for this project can be found at https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia. The dataset includes two classes which are normal and Pneumonia.
## Methodology
### 1. Data Exploring
As the validation dataset from Kaggle is too small, I re-split the ent dataset into the ratio of 70% train, 20% validation, and 10% test. All the above three datasets have the same ratios of Normal and Pneumonia, which is 73% of Pneumonia X-ray images and 27% of Normal X-ray images.
### 2. Image Preprocessing
Since the chest X-ray shows the part of the chest in different shades of black and white-based on the amount of radiation and tissue can absorb, it makes sense to decrease the complexity of the model by converting the images to grayscale (one color channel). The pixels were normalized to values from 0 to 1 to ensure efficient computation.
### 3. Models
The architecture of a CNN model consists of CNN layers, followed by a pooling layer and an optional dropout, and then fully connected layers with activations and output layers. I tried different combinations of activations, dropout, batch normalization, dense layers, and epochs numbers. My final best performance model has three convolutional 2D layers, with each followed by a max-pooling layer. After being flattened, it is fed into a fully-connected layer with ReLU activation. In the end, since this is a binary classification, I used the sigmoid activation function to predict the output probability.
## Results
Through each epoch during the learning process, validation loss and training loss approach each other, which means our model doesn't have much overfitting or underfitting. Moreover, the traning and validation accuracy score also converges to some points where they are almost equal in the end.
The model has an accuracy score of 96.24%, which indicates that our CNN model performs really well to classify 96.24% of the images in the test set.
For the case of detecting Pneumonia, we will aim to have high recall as any delayed diagnosis means that someone may get sick and potentially lose their life. The model has a recall score of 98.36% with 2.56% false positives and 1.20% false negatives, which are impressively good and exactly what we are aiming for.
## Conclusion
Our CNN model can effectively detect pneumonia disease with extremely high accuracy.
## Future Work
To make the model more robust, increase the number and diversity in the dataset. For example, include X-ray images from patients in different countries and at different ages.
Our current model is a binary classification model, identifying whether the patient has Pneumonia or not. In reality, patients could be suffering from different types of lung disease. In the future, I would love to collect different types of lung X-ray images and build a model to automatically diagnosis the type of lung disease.
## Reference
[1]: American Lung Association. (May 27, 2020). Learn About Pneumonia. https://www.lung.org/lung-health-diseases/lung-disease-lookup/pneumonia/learn-about-pneumonia
[2]: American Thoracic Society. Top 20 Pneumonia Facts — 2019. https://www.thoracic.org/patients/patient-resources/resources/top-pneumonia-facts.pdf
[3]: GE Healthcare. (February 25, 2019). AI Could Hold the Key to Identifying Pneumonia Via X-Ray. https://www.gehealthcare.com/feature-article/ai-could-hold-the-key-to-identifying-pneumonia-via-x-ray#:~:text=Chest%20X%2Drays%20have%20long,via%20X%2Dray%20a%20challenge.