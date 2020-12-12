# Natural Image Classification - ConvNet
Deploying ConvNet models to accurately predict respiratory illness

## Table of Contents 
- Brief Introduction
- Technologies
- Model Architecture(s)
- Compile and Run

### Introduction
This project aims to develop and test a convolutional neural network architecture to enhance natural image classification performance. We aim to improve performance of model prediciton likelihood of pneumonia using chest x-ray images. Minimal image preprocessing algorithms were applied with the hope of reducing computational complexity. It was decided that binarizing the images would be the sole image preprocessing algorithm applied as pixel densities were well separated within the range of 0 to 1. 

The notebook was created for submission as a Final Project to a Pattern Recognition & Classification course. All data was assembled from kaggle.com. Links to the data repositories and journal articles will be attached at the end of this document. 

### Technologies
- Python 3.7
- Tensorflow 1.14.0
- Keras 2.4.3

### Model Architecture(s)
Analyzing the available data did not take much effort as searching for potential noise nested within each image was easy to find. The decision as to whether or not to apply image preprocessing algorithms to improve classification performance was carefully examined. One article that contributed to the decision to not use several preprocessing techniques for this project was written by Heidari et al.. In it, the researchers discussed some drawbacks of leaving diaphragm regions as part of chest x-ray images to train models. During their research Heidari et al. determined that completely removing and then smoothing out the diaphragm region had a positive impact on classification performance. Their article can be found towards the end of this file. 

![image](https://user-images.githubusercontent.com/63656931/101534242-b95ad400-394b-11eb-974a-2d5cb521a890.png)

This chest x-ray is of a patient labeled as having pneumonia. Notice the white fog that inhabits the middle of the chest. This feature is what we really want the network to detect. Notice the presence of the diaphragm occupying the bottom of the x-ray.  

Once all of the data had been loaded and processed to satisfy Keras API requirements (see https://keras.io/api/models/model/), model development went underway. The first model aligned with a convolutional neural network (CNN) structure. Many studies typically use convolutional neural networks for detecting and classifying lung disease cases using chest x-ray images. Since this is the case, a CNN was constructed as a base-model to which a smaller and fully connected model can be compared against based upon accuracy and loss metrics.  

"Mode 1"(ConvNet)

<img width="598" alt="Screen Shot 2020-12-10 at 2 39 26 PM" src="https://user-images.githubusercontent.com/63656931/101821177-77ad6300-3adc-11eb-90cc-570405e932bb.png">

After training for only 5 epochs, "Model 1" reached a training accuracy of ~95.02% and a validation accuracy of ~94.17%. 

<img width="185" alt="Screen Shot 2020-12-09 at 12 39 22 PM" src="https://user-images.githubusercontent.com/63656931/101949177-089d4080-3ba8-11eb-97fd-6b1cdbab7090.png">

Running a confusion matrix provided the necessary metrics needed to assess how the model learned our data. Almost all test images were being classified as belonging to a single class which is clearly a problem (refer to matrix above). Nearly 2,500 more images belonged to class 'PNEUMONIA' compared to its counterpart. Thus, we performed under-sampling to achieve an even distribution of data across both classes. Since the model trained for only 5 epochs, we were unable to observe a convergence towards a well-balanced 'true positive' score. However, the model was defintely trending in the right direction as the confusion matrix helps to understand the better class separability (confusion matrix below). 



### Compile and Run

The entire model is saved to a HDF5 file, thanks to Keras. HDF stands for Hierarchical Data Format. HDF5 uses a file directory to organize data within that file and ensure long-term access to the large amounts of data stored within the file. Loading a model on your own machine just requires you to have tensorflow and keras installed. Versions of tensorflow >= 1.14.0 will work just fine. 

The model has been saved using tensorflow's model.save method. The model's weights, architecture, and training configuration has all been stored in one file. The original source code to re-create the model is not required as loading the model using the below statements below is sufficient.  

Since the optimizer and its state are saved as well, training will restart from where training left off. Make predictions and evaluate the model on images of your choosing. Also, it is important to train for more than 20 epochs as convergence towards a higher test accuracy is right around the corner.   

Here are some links attached below to the data and journal articles referenced:
https://www.sciencedirect.com/science/article/pii/S138650562030959X

https://www.nature.com/articles/s41598-019-42557-4

https://www.kaggle.com/tolgadincer/labeled-chest-xray-images

https://www.kaggle.com/prashant268/chest-xray-covid19-pneumonia 
