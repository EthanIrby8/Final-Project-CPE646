# Natural Image Classification - DNN
Improving model learning to accurately predict respiratory illness

## Table of Contents 
- Motivation
- Technologies
- Model Architecture(s)
- Compile and Run

### Motivation
This project aims to develop and test different machine learning models to enhance natural image classification performance. The project aims to improve performance of model prediciton likelihood of pneumonia using chest x-ray images. Minimal preprocessing was applied with the hope of reducing computational complexity. 

The notebook was created for submission as a Final Project to a Pattern Recognition & Classification course. All data was assembled from kaggle.com. Links to the data repositories and journal articles will be attached at the end of this document. 

### Technologies
- Python 3.7
- Tensorflow 1.14.0
- Keras 2.4.3

### Model Architecture(s)
Analyzing the available data did not take much effort when picking out the potential distractions/noise nested within each image. The decision as to whether or not to apply image preprocessing algorithms to improve classification performance was carefully examined. One article that contributed to the decision to not use several preprocessing techniques for this project was written by Heidari et al.. In it, the researchers discussed some drawbacks of leaving diaphragm regions as part of chest x-ray images to train models. Their discussions positively impacted this project as a whole, and their article can be found towards the end of this document as well. 



Once all of the data had been loaded and processed to satisfy Keras API requirements (see https://keras.io/api/models/model/), model development begun. 
