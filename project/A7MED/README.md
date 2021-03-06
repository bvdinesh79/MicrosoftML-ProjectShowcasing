# Deep learning model for COVID-19 diagnosis using chest X-ray images
Microsoft Azure Machine Learning Scholarship Project Showcasing Challenge

## Team:
@A7MED, @Jhonatan Tirado, @Radha Revathi G, @Lourdes Lizbeth Luna Rodríguez

## Guidelines: [https://github.com/mhmohona/MicrosoftML-ProjectShowcasing/blob/master/README.md](https://github.com/mhmohona/MicrosoftML-ProjectShowcasing/blob/master/README.md)

## Introduction
Nowadays, the world is suffering a health crisis, where it is essential to detect the problem in time and be able to do something about it. In December 2019, in Wuhan, China started an infectious disease called COVID-19, broadly speaking, this disease causes respiratory infections that can range from the common cold to more serious diseases that affect the lungs. 

It has been observed that around 80% of those who suffer from the disease recover without the need for hospital treatment, however, 1 in 5 people who contract COVID-19 end up presenting a serious condition and experiencing breathing difficulties, to such an extent that death can happen.

This disease has been alarming because of the speed with which it spreads, in addition to the complications that occur in the health of the person, as well as in the social context. An important factor to stop this disease, in addition to preventing it by taking hygiene and social distancing measures, for those who suffer from it, is early detection in order to take action in time. Therefore, in this project, a classifier for X-ray images of the rib cage is implemented on a web server, where the objective is to discriminate between healthy lungs, lungs with regular pneumonia or lungs with COVID-19 pneumonia.

As already mentioned, the project seeks to classify between three types of lung condition, since it has been seen that COVID-19 pneumonia is very similar to regular pneumonia, which has made it difficult to give diagnoses. Many investigations are being developed in order to differentiate between COVID-19 pneumonia and other types of pneumonia, since this type of information can be very useful for diagnoses and the simple understanding of how it is that COVID-19 affects the lungs. 

In order to be able to help the area of ​​medicine, the implementation of an intelligent model available to everyone is innovative, practical and useful to provide the appropriate service to the patient. 

For the project, the steps to follow were: 1) obtaining, preparing and exploring the data, 2) design, training and validation of a deep neural network, 3) testing of the deep neural network, 4) deployment for real time inferencing and, 5) evaluation of the implementation in a web server.

## Evaluation criteria:
1. Using Azure for Implementation based on Course Material (30%) = 
   1. The labs in the course did not show how to train or deploy a model for image classification.
   2. We deployed the model, as a REST API endpoint for real time inferencing, to a virtual machine in the cloud
2. Innovation & Creativity (20%) = Evaluation of the novelty, innovation and creativity introduced in the project such that it is appealing.
   1. The model can predict if an X-ray image shows normal lungs, lungs infected with common pneumonia, or lungs infected with COVID-19. This is important to make a difference between common pneumonia and the one caused by COVID-19.
3. Project Implementation (20%) = Evaluation of how much the planned idea was implemented in this project and how well the results are presented.
   1. To improve accuracy of the model, we planned to train 3 binary classifiers and use ensemble learning to determine the final result by a voting mechanism
      * First model would have two classes: "normal" and "not normal"
      * Second model would have two classes: "pneumonia" and "not pneumonia"
      * Third model would have two classes: "covid-19" and "not covid-19"
   2. Thus, when we want to predict if an X-ray is normal, pneumonia or covid-19, we would feed the same image to the three different models. Then, we would use a voting mechanism to determine the final result.
   3. For instance, if the input image is "covid-19", the expected results are:
      * First model: "not normal"
      * Second model: "not pneumonia"
      * Third model: "covid-19"
4. Impact & Potential (15%) =
   1. The model could be a tool to aid physicians to diagnose COVID-19. There’s a shortage of PCR testing kits, the gold standard to diagnose COVID-19, in countries like Peru, where a blood test to detect coronavirus antibodies is used instead.
5. Responsible AI (15%) = Evaluation of the potentiality of the project which is fair, inclusive to everyone, preserves data privacy and is secure.
   1. The model preserves data privacy because no PII (Personal Identifiable Information) is used. The input is a chest X-ray, and the output is a label (normal, pneumonia or COVID-19) and a probability (0 to 1).
   2. The model could be secured if access restrictions are added to the endpoint, to prevent unauthorized use
   3. The model is as inclusive as its dataset. If most of the chest X-ray images belong to asian patients, then the model can better predict COVID-19 for asian patients than for african people. That’s why it is important to collect data from all races, age and gender.

## Dataset
Chest radiography images were used in this project. Two different sub-databases were used to create one database.

Images of healthy lungs and regular pneumonia were acquired from Kaggle databases which are publicly available and it’s found in the next link: [https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia?](https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia?)

While lungs with COVID-19 pneumonia were extracted from a publicly available GitHub database, which is found on the below link: 
[https://github.com/lindawangg/COVID-Net/blob/master/docs/COVIDx.md](https://github.com/lindawangg/COVID-Net/blob/master/docs/COVIDx.md)

The images used in this project of the three types of lungs were used in .jpeg format, therefore it is considered as a requirement of the application.

The final dataset used had a total of ## images of X-ray, which have been divided into three groups and each one has three classes of X-ray images that belong to normal lungs, regular pneumonia lungs and COVID-19 pneumonia lungs. Below, the number of images used for each group is mentioned:
1. Training set: 
   1. Normal - ## images
   2. Regular pneumonia - ## images
   3. COVID-19 pneumonia - ## images
   4. Total of images: ##
2. Validation set:
   1. Normal - ## images
   2. Regular pneumonia - ## images
   3. COVID-19 pneumonia - ## images
   4. Total of images: ##
3. Testing set:
   1. Normal - ## images
   2. Regular pneumonia - ## images
   3. COVID-19 pneumonia - ## images
   4. Total of images: ##

## Data Preprocessing
Image resizing and conversion to RGB

## Model Architecture
Type and structure of the model selected (convolutional neural network), number and type of layers, input, output

## Model Training and Validation
Hyperparameters: learning rate, training epochs, batch size
Algorithms: SGD
Overfitting

## Model Testing
Metrics: overall accuracy, accuracy for each class, confusion matrix

## Deployment for Real Time Inferencing 

The code is available on GitHub at: [https://github.com/jhonatantirado/covid-azure-ml/blob/master/serve_rest_api.py](https://github.com/jhonatantirado/covid-azure-ml/blob/master/serve_rest_api.py)

The deep learning classification model was trained and generated by pytorch as a ".pt" file, which includes the calculated weights and biases of the model, but not the structure.

The trained model was then deployed as a REST API endpoint that can be consumed by a mobile or web application.

It’s important to load the model only once on startup to avoid loading the model everytime a request is sent to the REST API endpoint and to curb memory consumption

Fig 1 Code snippet where the pytorch model is loaded as a global variable

![Load model](https://github.com/waqasne/MicrosoftML-ProjectShowcasing/blob/master/project/A7MED/LoadModel-CodeSnippet.png)