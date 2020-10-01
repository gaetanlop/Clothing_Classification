# Clothing_Classification Web app
* **Final Product Hosted On Heroku:** https://clothing-classification.herokuapp.com/

I created a tool that classify images of clothes. 
*   This project is done using the Fastai Library.
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
Before going to the EDA or the Model Building part, I needed to clean up the data so that it can be used by a model or for an Exploratory Data Analysis. I made the following changes and created the following variables:
* From Location I extracted the district.
* Parsed numeric data out of Price
* Parsed numeric data out of area
* Parsed numeric data out of number of rooms
* Parsed numeric data out of number of bedrooms
* Made columns for if different caracteristics of an apartment were listed in the apartment description:
  * Extracting the number of floor of the building
  * Extracting where the apartment is located in the building
  * Extracting the number of bathrooms
  * Cellar
  * Parking
  * Balcony
  * Heating type
  * Renovated
* Created a categorical feature 'Building Height' based on the number of floors of the building.
* Created two categoricals features 'Las floor' and 'Ground Floor' based on the number of floors of the building and the floor of the apartment.

## Exploratory Data Analysis
Before starting the EDA I made a few assumptions, I tried to find out if they were valid or not.
 * Obviously, the higher the area of a home, the higher the price of the apartment.
 * The higher the number of rooms,bedrooms,bathrooms, the higher the price of the apartment. The number of rooms/bedrooms/bathrooms must be correlated with the area.
 * The height of the building might be negatively correlated with the price.
 * The presence of a Parking, a Cellar or a balcony must increase the price.
 * I have not any assumptions regarding the type of Heating.
 * In Paris some districts are way more expensive than others.
 * I think that an apartment at the Last floor is more expensive. At the contrary, an apartment at the ground floor must be less expensive. An apartment that have been renovated recently must be more expensive too.
 
I made a univariate and bivariate analysis of the column SalePrice witht the features that I thought were most interesting.I looked at the distributions of the numerical features and I transformed the skewed numerical features using log trnasformation. I also looked at the value counts for the various categorical variables. I detected and removed outliers. I explored the colinearity between the different features. I made pivot_tables to undertand the relationship between SalePrice and the different categorical features.
Below are a few highlights from the things I looked at.

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
