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
- Read and view the first 5 rows of the dataset
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
  > :point_right: Earle Asphalt has the lowest transaction amount, at $1.83, among the four locations, while EB Public Library has the highest, at $2.29.
- Find out product count per transaction

  ![pc](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/45582c75-c6e1-4b1e-9301-c9f82ec6ddf9)
  > :point_right: The majority of individuals only bought a single product per transaction.
- Find out the distribution of payment type

  ![paytype](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/0c68463b-5055-4f8c-978e-c6d944131b82)

  ![pay4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/d302f0d5-4f7c-4a05-abd0-7ca83eb69bd3)
  > :point_right: Overall, 65% of the transactions are paid by cash. GuttenPlans even has a higher proportion of customers paying by cash, at 78%. Therefore, changes to the vending machine should be planned carefully in order to meet the needs of this customer base.

### 5-4 Category Analysis
- Find out the sales and quantity sold trends by category

  ![cat](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/3a9f7218-104e-4271-9961-31eb3906347e)

  ![catq](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/1544d5b0-9a72-42ad-b3f7-b84e26ace24f)
  > :point_right: Among all categories, food appears to be more popular across all locations. EB Public Library, in particular, exhibits a notably high demand for food compared to the other locations. GuttenPlans experiences high demand in both the food and carbonated drink categories, while there is no demand for water (which might indicate that this location does not offer water).
- Identify the range of products within each category and location

  ![range](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/848f7025-200b-455f-94d5-1d60fcab6575)
   > :point_right: As GuttenPlans has the highest sales among all and has a lower variety of products in the transaction records, this suggests that consumers at GuttenPlans have more centralized demands. In contrast, Brunswick Sq Mall and EB Public Library have more diverse demands.

  ![sales](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/1699afe8-8f7f-4947-9f14-61c2ae724ee0)

  ![sales4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/ec6af24d-6fe5-4095-b88a-a403070c09fe)
- Find out the distributions of quantity sold in each location

  ![qty](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/21470411-bc98-42f6-a81d-8ccdb01a2d36)

  ![qty4](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/b95a419a-e05f-468a-9642-da421bd76deb)
  > :point_right: The compositions of demand categories are very different among the four locations. While most locations are dominated by the food category, GuttenPlans also has a significant competing demand for carbonated products. Additionally, Brunswick Sq Mall has a unique 20% demand for water, which is not common in other locations.
- Identify the price range in each category

  ![pd](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/7ef11dfa-b12b-42b5-8497-a746e43ef48f)
  ![pmm](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/5834c171-0d89-421a-ada3-88a7d6798d15)

### 5-5 Product Analysis
- Find the top 10 products

  ![101](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/df8947e8-0cf8-4fda-921c-edaafc711489)
  ![102](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/9c9936a0-fd64-4838-9e97-650d77e12ec0)
- Find the top 10 products' trends in each location

  ![bmall](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/d4e31b52-fdf7-421c-90e9-2a4a57a3bdb8)
  > :point_right: Poland Springs Water is clearly the top-demanding product at Brunswick Sq Mall and is the only product in the water category that made it into the top 10 demands.
  
  ![eli](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/f0b6e710-a442-44bc-af48-2c3e16945621)
  > :point_right: Poland Springs Water is the top demanding product at EB Public Library aside from Coca Cola-Zero Sugar. The observed 0 transactions in August might have been due to Poland Spring Water being out of stock. During the same month, there was an increased demand for Starbucks Refresher-Real Coconut Water. This suggests that Starbucks Refresher-Real Coconut Water is a substitute for Poland Springs Water.
  
  ![ea](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/2267b184-779d-4e2b-befe-9105da4bd7be)
  > :point_right: Aside from Robert Irvine's-Fit Crunch-Chocolate Pea and Wonderful Pistachinos-variety, there are many 0 transactions across the cross-tabulation. This may indicate diverse demand at Earle Asphalt or inconsistent allocation of the product mix. The peak demand for Pop Corners-Sea Salt in November should be investigated further to understand the cause of the sudden increase.
  
  ![gp](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/7e19d308-bae5-4b1c-9c1e-18df653342ea)
  > :point_right: The supply of Coca-Cola Regular and Coca-Cola Zero Sugar should be identified to determine whether they are substitutes or have their own separate demands.

### 5-6 Price Sensitivity Analysis
- Examine the relationship between price and quantity

  ![pq](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/7d578ebe-6079-474d-ae28-dd4e9ed3eeb9)
  > :point_right: Consumers at EB Public Library have the highest purchasing ability, with the highest product cost being $5, followed by Brunswick Sq Mall at $4, and then GuttenPlans and Earle Asphalt at $3.5 and $3, respectively.
  
- Examine the relationship between price and quantity in each category
  
  ![car](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/6d3e6290-c276-45f0-b4a4-668202d23859)
  
  ![foo](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/0c1076cf-4ae9-42b9-ac5f-c0f8fc7f6984)
  > :point_right: With the exception of EB Public Library, consumers at the other locations did not purchase food items priced over $3.

  ![non](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/c1500a07-512d-4260-a514-978972ec0102)
  > :point_right: EB Public Library has a high demand for a $3.5 non-carbonated product, specifically Starbucks Doubleshot Energy-Mocha, while demand for non-carbonated products at other locations is around $2.5.

  ![wat](https://github.com/Manyu-Ku/Ecomm_Customer_Segmentation_Analysis/assets/122411152/a08ed199-5565-4593-b381-eaba7bfb9866)

## 6. Insights & Recommendations
1. Brunswick Sq Mall ranked second in sales among the 4 locations. The top product at the mall is Poland Springs Water, and the Water category accounts for 20% of sales. However, **sales in the water category have dropped in Q4, and the root cause of the decrease needs to be investigated.**

2. EB Public Library possesses a sales record near the highest in all locations, and it also has the highest amount spent per transaction. This location offers a wider range of products with relatively low price sensitivity. **It is recommended to introduce more profitable or high-value products at this location to maximize profit.**

3. Earle Asphalt has the lowest sales and traffic, and it also offers the most limited products priced under $3, which might be the reason for the lower sales. **Introducing a greater variety of products to examine whether there is unmet demand in this area might help increase sales.**

4. GuttenPlans has the highest sales among all locations, with nearly 80% of transactions being paid in cash, and the demand is highly centralized. **Products in high demand should undergo inventory prediction to ensure that all demands are met. One thing to note is that there are no transactions in the water category. Further investigation is needed to determine whether there is no demand for water products or if there is a supply issue in this category.**

