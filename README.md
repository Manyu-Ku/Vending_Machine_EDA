# Vending Machine Sales Exploratory Data Analysis

![5925973](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/a4865fe2-e418-472d-b360-42cc0e994015)

<a href="https://www.freepik.com/free-vector/cartoon-vending-machines-collection_18575977.htm#query=vending%20machine&position=0&from_view=search&track=ais">Image by pikisuperstar</a> on Freepik

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
>  ![na1](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/b611cd29-b4e6-43ec-84d9-518e2248bc18)
> Given that both 'Product' and 'Category' columns contain missing values, and considering their interrelation, we will drop rows where both columns have missing values. Furthermore, if one of these columns has a valid value while the other is missing, we will assign the missing value based on a relevant and logical relationship.
>
> ![na2](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/c6de188b-ce65-4f21-9bf6-dab7f07730c2)
> ![na3](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/e6c88eab-f3e9-4343-9b7c-7d3690fd8d05)
> Most missing Category entries are for products in the 'Food' category, with exceptions like 'Canada Dry' in 'Carbonated' and 'Starbucks Coffee' in 'Non-Carbonated'. We will address beverages and assign the rest to 'Food'.
> 
> ![na4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/6a503ba3-3b41-4aad-92a9-2c90cdf100ee)
- Summary statistics of numeric variables
> ![describe](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/3f35b883-e19b-4ac8-80e5-f7150e3032aa)
> The descriptive summaries of the real columns (Coil, Price, Qty) closely resemble those of the corresponding mapping columns. To verify, we will compare the values in the real columns to those in the mapping columns for identicalness.
> ![rm](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/a9eee0b0-b6f8-4699-9fbc-e3c60a94401f)
- Explore categorical variables
- Create 'month' and 'weekday' columns to facilitate time series analysis
