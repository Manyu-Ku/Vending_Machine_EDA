# Vending Machine Sales Exploratory Data Analysis

![vm](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/751c8aec-8f74-4f1c-92ca-0b3343c266e0)

Photo by <a href="https://unsplash.com/@nicsandman20?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Nicholas Ng</a> on <a href="https://unsplash.com/photos/jhM6SfHOlFs?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText">Unsplash</a>

## Data Source: 
[kaggle_datasets-vending-machine-sales](https://www.kaggle.com/datasets/awesomeasingh/vending-machine-sales)

2022 vending machine sales data from 4 different locations in Central New Jersey

## 1. Business Problem:
The business wants to optimize product placement in vending machines to enhance customer satisfaction, increase sales, and improve overall profitability.

## 2. Objectives:
The objective of this exploratory data analysis (EDA) is to gain insights into consumer behavior, preferences, and trends in different vending machine locations across Central New Jersey. 

## 3. Methodology:
The analysis in this report was conducted using Jupyter Notebook and implemented in Python.
- Libraries used: `Pandas`, `NumPy`, `Matplotlib`, `Seaborn`
- Techniques/Models applied: `Exploratory Data Analysis`, `Frequency Analysis`, `Time Series Analysis`, `Comparative Analysis`, `Data Visualization`

## 4. Constraints and Data Augmentation Suggestions:
The current dataset lacks inventory and item profitability information. Including these details would enhance supply optimization, reducing stockouts and excess inventory costs. Profitability data would prioritize items benefiting revenue.
> With the provided data, we assume that the company restocks when needed and conducts an analysis of sales and quantity rather than profit analysis.

## 5. Data Analysis
The following outline provides a concise summary of the analysis, highlighting the essential steps and key findings. To view the complete code, please click [here for ipynb file]().

### 5-1 Data Preprocessing
- Import libraries
- Read and view the first 5 of the dataset
- Check the size of the data and the data types of all columns
- Convert 'TransDate' and 'Prcd Date' to DateTime format
- Check if there is any duplicates
- Check & handle NA values
  ![na1](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/b611cd29-b4e6-43ec-84d9-518e2248bc18)
  > Given that both 'Product' and 'Category' columns contain missing values, and considering their interrelation, we will drop rows where both columns have missing values. Furthermore, if one of these columns has a valid value while the other is missing, we will assign the missing value based on a relevant and logical relationship.
 
  ![na2](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/c6de188b-ce65-4f21-9bf6-dab7f07730c2)
  ![na3](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/e6c88eab-f3e9-4343-9b7c-7d3690fd8d05)
  > Most missing Category entries are for products in the 'Food' category, with exceptions like 'Canada Dry' in 'Carbonated' and 'Starbucks Coffee' in 'Non-Carbonated'. We will address beverages and assign the rest to 'Food'.
 
  ![na4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/6a503ba3-3b41-4aad-92a9-2c90cdf100ee)
- Summary statistics of numeric variables
  ![describe](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/3f35b883-e19b-4ac8-80e5-f7150e3032aa)
  > The descriptive summaries of the real columns (Coil, Price, Qty) closely resemble those of the corresponding mapping columns. To verify, we will compare the values in the real columns to those in the mapping columns for identicalness.

   ![rm](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/a9eee0b0-b6f8-4699-9fbc-e3c60a94401f)
- Explore categorical variables
- Create 'month' and 'weekday' columns to facilitate time series analysis

### 5-2 Vending Machine Sales Overview
- The sales overview (LineTotal = Total Sales)

  ![overview](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/001b0a82-2d37-4c62-97a0-344ebf5e66b5)
- Find out the sales trend

  ![monthly](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/944c8479-abe2-450a-a030-fe961a35b02e)
  > :point_right: Total sales peaked in July. Given that we only have one year of records, it is challenging to ascertain whether there is a seasonal reason for this peak.
- Find out the total sales by machine

  ![machines](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/86e60a94-9c9f-410c-bd03-94df67853c3c)
- Find out the total sales by location

  ![locations](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/3ed548d3-e7b0-4370-9bb5-2dbcdc964c73)
- Find out the monthly sales by location

  ![msloc](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/a61520d1-5482-4348-a8ea-195971b48dc5)
  > :point_right: The sales trends in GuttenPlans and Brunswick Sq Mall align with the overall sales trend, both of which peaked in July.
- Find out the traffic trends in each location

  ![weekday](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/dfe3b767-2d1a-48b7-ad6d-0b50a8792109)
  > :point_right: Brunswick Sq Mall experiences its highest traffic during weekends, particularly on Saturdays. In contrast, EB Public Library observes higher traffic on weekdays compared to weekends. Earle Asphalt, a construction engineering firm operating five days a week, exhibits nearly equivalent weekday traffic. As for Gutten Plans, a frozen dough specialist company, its traffic follows a normal distribution from Monday to Saturday.

### 5-3 Transaction Overview
- Transaction overview by location

  ![trans](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/1dfbce32-defd-4fd1-af07-57d84b23494a)
- Find out the product count per transaction

  ![pc](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/45582c75-c6e1-4b1e-9301-c9f82ec6ddf9)
  > :point_right: The majority of individuals only bought a single product per transaction.
- Find out the distribution of payment type

  ![paytype](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/0c68463b-5055-4f8c-978e-c6d944131b82)

  ![pay4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/d302f0d5-4f7c-4a05-abd0-7ca83eb69bd3)

### 5-4 Category Analysis
- Find out the sales and quantity sold trends by category

  ![cat](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/3a9f7218-104e-4271-9961-31eb3906347e)

  ![catq](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/1544d5b0-9a72-42ad-b3f7-b84e26ace24f)
  > :point_right: Among all categories, food appears to be more popular across all locations. EB Public Library, in particular, exhibits a notably high demand for food compared to the other locations. GuttenPlans experiences high demand in both the food and carbonated drink categories, while there is no demand for water (which might be indicating that this location does not offer water).
- Identify the range of products within each category and location

  ![range](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/848f7025-200b-455f-94d5-1d60fcab6575)
- Find out the distributions of sales in each location

  ![sales](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/1699afe8-8f7f-4947-9f14-61c2ae724ee0)

  ![sales4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/ec6af24d-6fe5-4095-b88a-a403070c09fe)
- Find out the distributions of quantity sold in each location

  ![qty](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/21470411-bc98-42f6-a81d-8ccdb01a2d36)

  ![qty4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/b95a419a-e05f-468a-9642-da421bd76deb)
- Identify the price range in each category

  ![pd](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/7ef11dfa-b12b-42b5-8497-a746e43ef48f)
  ![pmm](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/5834c171-0d89-421a-ada3-88a7d6798d15)

### 5-5 Product Analysis
- Find the top 10 products

  ![101](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/df8947e8-0cf8-4fda-921c-edaafc711489)
  ![102](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/9c9936a0-fd64-4838-9e97-650d77e12ec0)
- Find the top 10 products' trends in each location
