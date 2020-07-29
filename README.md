# Predicting the sales for Big Mart

##Goal of the project

#### The goal of the project is to understand the factors impacting the sales of different products in different stores and build a predictive model to predict the sales.

## About the dataset

#### The dataset contains sales data at Big Mart for 2013 for 1559 products across 10 stores in different cities. Also, certain attributes of each product and store have been defined. The aim is to to understand the properties of products and outlets which play a key role in increasing sales and build a predictive model to predict the sales of each product at a particular outlet. The dataset contains 8523 data points, 11 features and one target variable. They are as follows:

Item_Identifier: Unique product ID
Item_Weight: Weight of product
Item_Fat_Content: Whether the product is low fat or not
Item_Visibility: The % of total display area of all products in a store allocated to the particular product
Item_Type: The category to which the product belongs
Item_MRP: Maximum Retail Price (list price) of the product
Outlet_Identifier: Unique store ID
Outlet_Establishment_Year: The year in which store was established
Outlet_Size: The size of the store in terms of ground area covered
Outlet_Location_Type: The type of city in which the store is located
Outlet_Type: Whether the outlet is just a grocery store or some sort of supermarket
Item_Outlet_Sales:Sales of the product in the particular store. This is the outcome variable to be predicted.

## Data Pre Processing

### Null value imputation:

#### 1) The Item_Size column has 4016 i.e 28.27% missing values.The imputation was done based on two factors: a. Looking at the mode of the outlet sizes in the different locations for the different types of outlets. b. Comparing the sales of the outlets in the different locations. An assumption was made that an outlet with particular size will have similar sales across different locations

#### 2) The Item_Weight column has 2439 i.e 17.17% missing values.The basis for imputation was on the the type of the item. The assumption made was items of one type will have the same weight.

### Removing Duplicacies in the Item_Fat_Content column:

#### The Item_Fat_Content had duplicacies like LF and reg which were converted to Low Fat and Regular. The items which fell under the category of Non Consumables were given a fat content value of Non Edible.

### Creating the Item Category from the Item_Identifier column:

#### The first two letters of the Item Identifier column were FD, DR and NC which were converted to Food, Drinks and Non Consumable for Item Category variable.

### Zero values in item_Visibility column:

#### It is not possible for an item to have zero visibility in a store. So, the zeros were replaced by the mean visibility of the particular product type. The assumption made was similar products will have similar visibility in a store.

### Findings from Exploratory Data Analysis:
#### 1. The distribution of sales right skewed which means mostly the sales figure was below 4000 but because of certain outlier sales above 10,000 the distribution mean has shifted towards the right.
#### 2. We have 3 Categories of Products Food, Non Consumable and Drinks.Under food we have 11 sub categories and 3 for each of Food and Non Consumable.
#### 3. Under Food we have 580 Low Fat items and 539 Regular Items. For Non Consumable there is only 295 Low Fat Items. For Drinks there are 133 Low Fat Items and 12 Regular Items.
#### 4. Food Category, Non Consumable and Drinks account for 73%, 18.5% and 8.5% of the total revenue generated
#### 5. Within Food, Fruits and Vegetables and Starchy Foods contributed 20% each. For Drinks, Soft Drinks and Hard Drinks contributed 55% and 28% respectively. For Non Consumables Household items and Health items contributed 59% and 30% resepectively.
#### 6. In terms of overall revenue Fruits and Vegetables, Snack Foods and Households contributes the highest with 15%, 14% and 11% of total revenu.
#### 7. Drinks with low fat are selling more compared to regular drinks.
#### 8. Tier 3 with 3350 stores contributes 41% of the total revenue. Tier 2 and 1 has 2785 and 2388 stores and contributes 35% and 24% respectively of the total profit.
#### 9. The number of items sold and revenue gained is high for low fat compared to regular items across all the three tiers
#### 10. Supermarket Type 1 has the highest number of stores across all the tiers. The number of stores of a particular type in a location is proportional to sales. This can be seen by looking at the sales of Supermarket Type 1 in Tier 1 and 2 which have the highest number of stores and also contributes 23% and 34% respectively.
#### 11. The tier 3 medium sized outlets are contributing 28% of total revenue which is more than the high sized outlets in the same tier. They are also generating more revenue compared to small or medium sized outlets in other tiers.
#### 12. Same supermarket type 1 is doing diffferently in two tiers 1 and 2. This can be attributed to the number of mid sized stores in the two tiers.
#### 13. Supermarket Type 3 having medium sized outlets is generating more revenue than a high sized outlets of Supermarket Type 1 in tier 3. One reason is the average MRP of the products is lower which incentivizes customers to buy more.
#### 14. The sales from outlets established in the year 1998 say a fall in the total sales. This can be attributed to the reduced number of stores established in that year

## Feature Engineering:

#### 1. Item Visibility Ratio was created by taking the ratio of the item visibility and the mean value of item visibility. This variable showed how one item was given more importance compared to others.

#### 2. The values of Item Fat Content, Outlet Location Type and Outlet Size were converted into categories.

#### 3. The numerical variables were scaled using MinMaxScaler.

## Model Building

#### The models built and their RMSE values are as follows:

#### XGBoost Regression: 1077
#### Polynomial Regression: 1084
#### Linear Regression: 1120
#### Ridge Regression: 1125
#### Random Forest Regression: 1139

#### The XGBoost Regressor was the predictor with the least RMSE value.
