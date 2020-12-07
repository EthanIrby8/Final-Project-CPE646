# Natural Image Classification - DNN
Improving model learning to accurately predict respiratory illness

## Table of Contents 
- Motivation
- Technologies
- Model Architecture(s)
- Compile and Run

### Motivation
This project aims to develop and test different machine learning models to enhance natural image classification performance. The project aims to improve performance of model prediciton likelihood of pneumonia using chest x-ray images. Minimal preprocessing was applied with the hope of reducing computational complexity. 

The notebook was created for submission as a Final Project to a Pattern Recognition & Classification course. All data was assembled from kaggle.com. For more than a small introduction to the overview of the project, please read (pages document). Links to the data repositories and journal articles will be attached at the end of this document. 

### Technologies
- Python 3.7
- Tensorflow 1.14.0
- Keras 2.4.3

### Model Architecture(s)
Analyzing the available data did not take much effort as inferring the potential distractions/noise nested within each image was straightforward. The decision as to whether or not to apply image preprocessing algorithms to improve classification performance was carefully examined. One article that contributed to the decision to not use several preprocessing techniques for this project was written by Heidari et al.. In it, the researchers discussed some drawbacks of leaving diaphragm regions as part of chest x-ray images to train models. Their discussions positively impacted this project as a whole, and their article can be found towards the end of this document as well. 

insert image of pneumonia image

Once all of the data had been loaded and processed to satisfy Keras API requirements (see https://keras.io/api/models/model/), model development begun. The first model aligned with a convolutional neural network (CNN) structure. The goal here was to devise a traditional CNN that boasted several layers without too much overfitting reduction algorithms applied. Many studies typically use convolutional neural networks for detecting and classifying lung disease cases using chest x-ray images. Since this is the case, a CNN was constructed as a base-model to which a smaller and fully connected model can be compared against based upon accuracy and loss metrics.  

"Model 1" (CNN)
insert image of model summary

"Model 1" achieved a training accuracy ~99.5% and a validation accuracy of ~76%. The major difference in accuracies is an indicator that the model overfitted the training data. 

In order to achieve a robust model with less layers and proneness to overfitting, a dense neural network is constructed. A few changes to note first. To improve model performance with some hyper-parameter tuning, l2 regularization is added to two dense layers. This should help with penalizing the large number of weights being passed through the network, subsequently taming the amount of computational power.  

"Model 2" (DNN)
insert image of model summary

