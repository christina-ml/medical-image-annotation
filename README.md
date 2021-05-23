# Table of Contents

* [Project Description](#project-description)
	- [Project Overview](#project-overview)
	- [Tutorial](#tutorial)
* [The Different AI Models I Created (4 Total)](#the-differnt-ai-models)
	- [AI Model No.1 - Clean/Balanced Data](#ai-model-no2)
	- [AI Model No.2 - Clean/Unbalanced](#ai-model-no.2)
	- [AI Model No.3 - Dirty/Balanced](#ai-model-no.3)
	- [AI Model No.4 - 3-Class](#ai-model-no.4)
* [Project Submission](#project-submission)


# Project Description

## Project Overview

In the previous project, you created the instructions needed to build a labeled dataset that distinguishes between healthy and pneumonia x-ray images. This dataset would eventually be used to build a product that helps doctors quickly identify cases of pneumonia in children. Remember that the goals of this product are to:

* help flag serious cases,
* quickly identify healthy cases,
* and, generally, act as a diagnostic aid for doctors.

In this project, we are going to take the next step and build the classification model that would serve as the backbone of this product.

We are using Google AutoML, an automated machine learning tool that will allow us to build the model and host it in the cloud.

In order to appreciate how training data impact models, we will build models with 4 variants of the dataset. This project is designed to test your ability to

build a model using Google's AutoML Vision platform, and
understand how properties of data impact performance of models.

### The Data

We'll be using the same Kaggle chest x-ray dataset that we used in the previous project, except here, we'll skip the step of using Figure Eight's platform to label the data, and just use the original labels supplied with the data on Kaggle.

### The Four Parts of the Project

We will train four different models using four variants of the pneumonia dataset. Recall that the dataset contains childrens' chest x-ray images, and that they are classified into two classes, "normal" and "pneumonia". The following sections describe the steps you must take to create each model.

1. Create a binary classifier to detect pneumonia using chest x-rays
2. Create an unbalanced binary classifier
3. Create a binary classifier with dirty data
4. Create a three-class model with the classes “normal”, “bacterial pneumonia”, and “viral pneumonia”

## Tutorial

Google Cloud AutoML Vision
The following tutorial will guide you through the process of creating and training a model on Google Cloud's AutoML Vision platform. Go through the following steps to complete the project.

Steps:

Download Kaggle Chest X-Ray Images (Pneumonia) Dataset, if you haven't already: https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia#chest_xray.zip.
Go to Google AutoML: https://cloud.google.com/automl/.
Click “TRY AUTOML” and select “AutoML Vision”.
Sign in to Google Developer or create an account.
After you log in, head to the AutoML Vision Console: https://console.cloud.google.com/vision and Accept the terms of service.
Next create a project with any title.
Here is a link to the chest-xray.zip in case you are unable to download it from Kaggle.


7. Once on the dashboard click “Get Started” on AutoML Image Classification.

8. Accept all the screens then you will reach the last page where you have to set up billing and Vision API.

11. Once you have completed the billing you can go back to the project set up page and click “SET UP NOW” to enable the vision API. This will automatically set up the API and should redirect you select the Google Cloud Project.

12. In the dropdown you should see the project that you created. Select the project and continue.


13. Next, you should see the Datasets page. Click “NEW DATASET” at the top of the page.

14. Select “Single-Label Classification”.

15. Create your dataset.
Give the dataset a name.
Open the folder of Chest Xrays you downloaded from Kaggle and go into the train folder.
In a separate folder create a directory with the following structure:
AutoMLDataset/
normal/
pneumonia/
Then copy between 100-300 images of each type of each classification from the original train/ folder (normal, pneumonia) into the appropriate new folder (make sure to copy the same number of each type of image to have a balanced dataset) Once you have your images in the new folders then zip the whole AutoMLDataset/ folder to create automldataset.zip.


Christina says: I chose 200 photos for each category:
* 200 "normal" photos
* 200 "pneumonia" photos


16. Now back in the AutoML Console Dataset go ahead and upload the zip file with all the images. Again, make sure you zipped the top-level folder that contains two folders: normal/ and pneumonia/ with the associated sets of 100-300 images in each folder. This will allow AutoML to automatically detect the correct ground truth label for each image by looking at the name of the folder in which it is contained. Once the zip file is attached go ahead and “CREATE DATASET”. For our current labeling scheme, there is no need to select the button to "Enable multi-label classification" (this allows you to apply multiple labels to a single image). This step make take a few minutes to upload all the images and set up the dataset.

17. Once the data is ready you should see a screen with all the images you added as well as a label of “normal” or “pneumonia” under each image. These are the images and ground truth labels that will be used to train/test/validate your pneumonia detector model.

18. Next click on the “TRAIN” tab and here you will see the distribution of images as well as the splits for training, validation, and test images.


19. Click “START TRAINING” to begin training your pneumonia classification model. In the options keep all the defaults (Cloud-hosted, 8 node hour) and then start the training.

20. Now the model is in the training phase. Go grab a cup of coffee and stretch your legs. Once the model training is done you will be notified via email.

21. Once the training is complete you can click on the “EVALUATE” tab and you will see various metrics about the model such as precision, recall, and a confusion matrix. Try to understand what each of these metrics means and how they are calculated.

22. Optional: Next click on the “TEST&USE” tab and this is where you can test the model on new data that the model has never seen. If you click “UPLOAD IMAGES” and select an image from the Kaggle dataset that you did NOT use in the training set of images and watch the model predict whether or not the patient in the x-ray has pneumonia or not. Try to find images that produce both correct and wrong predictions.


23. That's it! You've built your first AI model! Now that you know how to upload data and train the model, follow the steps above for 3 additional variations on the dataset, for a total of 4 models. We recommend creating new folders, new zip files, and new datasets in AutoML so that you can keep track of which iteration you're on and retain the results of each trained model for reference:
	1. - Clean/Unbalanced: Create a model using 100 "normal" images and 300 "pneumonia" images.
	2. - Dirty/Balanced: Create a model with 100 "normal" images and 100 "pneumonia" images, but deliberately create a "dirty" dataset by putting 30 "normal" images in the pneumonia folder and 30 "pneumonia" images in the normal folder.
	3. - 3-Class: Note that the filenames of images in the "pneumonia" class have 2 standards; for example: person75_bacteria_366.jpeg and person80_virus_150.jpeg. The inclusion of the word "bacteria" indicates that this was a case of bacterial pneumonia, and the word "virus" means this was a case of viral pneumonia. Go back and create a dataset with 3 classes: "normal", "bacterial pneumonia" and "viral pneumonia".
Once you have completed the project, don't forget to disable the Google Cloud Platform billing for this project. You can find those instructions here.


# The Different AI Models I Created (4 Total)

## AI Model No.1 - Clean/Balanced Data

Binary Classifier with Clean/Balanced Data

* 200 Normal Images
* 200 Pneumonia Images


## AI Model No.2 - Clean/Unbalanced

Binary Classifier with Clean/Unbalanced Data

* 100 Normal Images
* 300 Pneumonia Images


## AI Model No.3 - Dirty/Balanced

Binary Classifier with Dirty/Balanced Data

* 100 Normal Images (this group contains 30 "pneumonia" images on purpose) - 100 total
* 100 Pneumonia Images (this group contains 30 "normal" images on purpose) - 100 total


## AI Model No.4 - 3-Class

3-Class Model

Go back and create a dataset with 3 classes: "normal", "bacterial pneumonia" and "viral pneumonia".
* Normal (I put in 100 each)
* Bacterial Pneumonia (I put in 100 each)
* Viral Pneumonia (I put in 100 each)


# Project Submission

## AutoML Modeling Report
Please refer to the AutoML Modeling Report pdf file to view this project, which goes into detail on each of the 4 models.

You'll find this data for each of the 4 models:
* Confusion Matrix
* Precision and Recall
* Score Threshold

For Clean/Balanced Data model (#1) & Clean/Unbalanced Data model (#2):
* Train/Test Split

For Clean/Unbalanced Data model (#2):
* Unbalanced Classes

For Dirty/Balanced Data model (#3):
* Dirty Data

For 3-Class Model model (#4):
* F1 Score
