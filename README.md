# Clothing_Classification Web app
**Final Product Hosted On Heroku:** https://clothing-classification.herokuapp.com/

I created a tool that classify images of clothes. 
*   Project done using the Fastai Library.
*   I created a tool that classify images of clothes. 
*   Scraped more than 1200  images of clothes from Google Image.
*   Cleaned Data based on the predictions of a simple convolutional neural net.  
*   Used transfer learning (pretrained resnet34). 
*   Used the learning rate finder to find the best learning rate to update the weights. At first trained with a freezed model (except the head) then unfreezed the model for better predictions.
*   Built a client facing API using Voila.
*   Deployed the model on Heroku.

## Code and Resources Used

**Python Version:** 3.7

**For Web Framework Requirements:** ```pip install -r requirements.txt```

## Web Scraping
Scraped more than 1200  images of clothes from Google Image. I scraped images of:
* shirts
* t-shirts
* jeans
* k
* x
* y
* z

## Data Cleaning



## Exploratory Data Analysis


![alt text]
![alt text]
![alt text]

## Model Building
First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.
I tried three different models and evaluated them using Mean Absolute Error:
* **Linear Regression**: - Baseline for the model
* **Lasso**: - Because some independent variables were highly correlated and because of the sparse data, I thought that using a normalized regression like lasso would be a good idea.  
* **Ridge**: - Because some independent variables were highly correlated and because of the sparse data, I thought that using a normalized regression like ridge would be a good idea.  
* **Random Forest** 
* **XGBoost**
* **Stacked Model**: I wanted to implement what I learned recently on Model Stacking. It works well.

## Model performance
The Stack Model outperformed the other approaches on the validation set. Here are the results in K euros.
* **Linear Regression**: MAE= 82.6
* **Random Forest**: MAE=77.6
* **XGBoost**: MAE=80.5
* **Stacked Model**: MAE=74.9

## Productionization and Deployment
I built a client facing API using Voila and deployed it using Heroku.
* **Final Product Hosted On Heroku:** https://house-price-prediction-paris.herokuapp.com/
