# Clothing_Classification Web app: Project Overview
**Final Product Hosted On Heroku:** https://clothing-classification.herokuapp.com/
I created a tool that classify images of clothes into their corresponding categories (t-shirts,shirts,jeans...). 

*   Project done using the Fast.ai Library.
*   I created a tool that classify images of clothes. 
*   Scraped more than 1000  images of clothes from Google Image.
*   Cleaned Data based on the predictions of a simple convolutional neural net.  
*   Used transfer learning (pretrained resnet34). 
*   Used the learning rate finder to find the best learning rate to update the weights. At first trained with a freezed model (except the head) then unfreezed the model for better predictions.
*   Built a client facing API using Voila.
*   Deployed the model on Heroku.

## Code and Resources Used

**Python Version:** 3.7

**For Web Framework Requirements:** ```pip install -r requirements.txt```

**Fastai Course:** https://github.com/fastai/fastbook

## Web Scraping
Scraped more than 1200  images of clothes from Google Image. I scraped images of:
* shirts
* t-shirts
* jeans
* socks
* shoes
* polo-shirts

## Data Cleaning
As I scraped images from Google Image, there was some images that does not correspond to what I wanted my model to train on or images that were mislabeled. Therefore, I trained a neural net for only two epochs then plot the images with the highest losses. Thus, I could have a look at what images the model had difficulties to train on or to predict.
To display the images whith the highest loss, I used a python GUI called the ImageClassifierCleaner.

![alt text](https://github.com/gaetanlop/Clothing_Classification/blob/master/Data%20example.PNG)


## Data Augmentation Strategy
I simply Resized all the images to 224 by 224 pixels using Cropping. Then add aug_transforms: a fastai method to transforms images using the following trnasformations: mult=1.0, do_flip=True, flip_vert=False, max_rotate=10.0, min_zoom=1.0, max_zoom=1.1, max_lighting=0.2, max_warp=0.2, p_affine=0.75, p_lighting=0.75, xtra_tfms=None, size=None, mode='bilinear', pad_mode='reflection', align_corners=True, batch=False, min_scale=1.0.

![alt text](https://github.com/gaetanlop/Clothing_Classification/blob/master/Data%20augmentation%20example.PNG)

## Model Building
Used transfer learning (pretrained resnet34). Used the learning rate finder to find the best learning rate to update the weights. 

![alt text](https://github.com/gaetanlop/Clothing_Classification/blob/master/Lr%20finder.PNG)

## Model performance
At first trained with a freezed model (except the head) then unfreezed the model for better predictions.

![alt text](https://github.com/gaetanlop/Clothing_Classification/blob/master/results.PNG)
![alt text](https://github.com/gaetanlop/Clothing_Classification/blob/master/confusion%20matrix.PNG)

## Productionization and Deployment
I built a client facing API using Voila and deployed it using Heroku.
* **Final Product Hosted On Heroku:** https://clothing-classification.herokuapp.com/
