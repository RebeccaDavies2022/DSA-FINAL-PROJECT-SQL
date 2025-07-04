# DSA-FINAL-PROJECT-SQL
This repository contains a complete SQL-based analysis project done as part of my data analysis training with DSA Incubator Hub. It focuses on solving real-world business intelligence questions for Kultra Mega Stores (KMS) , a retail company specializing in office supplies and furniture in Nigeria.

The objective was to analyze historical order data (2009–2012) using **SQL** to solve two case scenarios involving customer insights, sales performance, and operations.

## Data Cleaning
- I changed the decimal from *18,10* to *10,2* for the currency before uploading the csv file
- Changed Row ID, Order ID, Order Quantity to INT before uploading the csv file
- Created database as KML_db so the query will be on the right database folder.
  
  ```
  CREATE Database KML_db
  ```
  
```
SELECT * from [dbo].[KMS Sql Case Study]
```

```
SELECT * from [dbo].[Order_Status csv]
```

## Data Analytical Task And Solutions

### Data Manipulation

- I Joined the two tables (Order Status and KML SQL Case Study) together and created view with it for easier access.
    - Joining ;
      ```
      SELECT [dbo].[KMS Sql Case Study].ORDER_ID,
       [dbo].[KMS Sql Case Study].Order_Quantity,
	   [KMS Sql Case Study].Unit_Price,
	   [KMS Sql Case Study].Discount,
	   [KMS Sql Case Study].Product_Base_Margin,
        [KMS Sql Case Study].Order_Date,
		[KMS Sql Case Study].Ship_Date,
		[KMS Sql Case Study].Customer_Name,
		[KMS Sql Case Study].Customer_Segment,
		[KMS Sql Case Study].Province,
		[KMS Sql Case Study].Region,
		[KMS Sql Case Study].Order_Priority,
		[KMS Sql Case Study].Sales,
		[KMS Sql Case Study].Profit,
		[KMS Sql Case Study].Ship_Mode,
		[KMS Sql Case Study].Shipping_Cost,
	    [KMS Sql Case Study].Product_Container,
		[KMS Sql Case Study].Product_Category,
		[KMS Sql Case Study].Product_Sub_Category,
		[KMS Sql Case Study].Product_Name,
		[Order_Status csv].[Status]
		from [KMS Sql Case Study]
		JOIN [Order_Status csv]
		ON [Order_Status csv].Order_Id=[KMS Sql Case Study].Order_ID
      ```
      
     - Creating View

```
Create view Vw_KMSORDER
AS
SELECT [dbo].[KMS Sql Case Study].ORDER_ID,
    [dbo].[KMS Sql Case Study].Order_Quantity,
    [KMS Sql Case Study].Unit_Price,
    [KMS Sql Case Study].Discount,
    [KMS Sql Case Study].Product_Base_Margin,
    [KMS Sql Case Study].Order_Date,
		[KMS Sql Case Study].Ship_Date,
		[KMS Sql Case Study].Customer_Name,
		[KMS Sql Case Study].Customer_Segment,
		[KMS Sql Case Study].Province,
		[KMS Sql Case Study].Region,
		[KMS Sql Case Study].Order_Priority,
		[KMS Sql Case Study].Sales,
		[KMS Sql Case Study].Profit,
		[KMS Sql Case Study].Ship_Mode,
		[KMS Sql Case Study].Shipping_Cost,
    [KMS Sql Case Study].Product_Container,
		[KMS Sql Case Study].Product_Category,
		[KMS Sql Case Study].Product_Sub_Category,
		[KMS Sql Case Study].Product_Name,
		[Order_Status csv].[Status]
		from [KMS Sql Case Study]
		JOIN [Order_Status csv]
		ON [Order_Status csv].Order_Id=[KMS Sql Case Study].Order_ID
```

  - Update Null Cell
    

```    
		UPDATE [dbo].[Vw_KMSORDER]
SET [Product_Base_Margin] = COALESCE([Product_Base_Margin], 0.00)
WHERE [Product_Base_Margin] IS NULL
```

```
SELECT * FROM [dbo].[Vw_KMSORDER]
```

    
#### **Case Scenario I**
1. Which product category had the highest sales?
2. What are Top 3 and Bottom 3 regions in terms of sales?
3. What were the total sales of appliances in Ontario?
4. Advise the management of KMS on what to do to increase the revenue from the bottom 10 customers
5. KMS incurred the most shipping cost using which shipping method?

#### **Case Scenario II**
6.  Who are the most valuable customers, and what products or services do they typically purchase?
7.  Which small business customer had the highest sales? 
8.  Which Corporate Customer placed the most number of orders in 2009 – 2012? 
9.  Which consumer customer was the most profitable one? 
10. Which customer returned items, and what segment do they belong to?
11. Do you think the company appropriately spent shipping costs based on the Order Priority? Explain your answer

#### **Files Included**
All SQL queries that has been used to clean, join, analyze and generate insights from the dataset given is in this file below;

[KMS Analytical File](https://drive.google.com/file/d/1WHj5xxLNAdsG1Kq29lEzn2pncb61Iksf/view?usp=sharing)

#### **Preview Of The SQL Canvas**

![SQL SCREENSHOT](https://github.com/user-attachments/assets/de91f35e-8a4f-491e-8f16-86ab086cf9ce)


#### **Tools Used**
- SQL Server
- SSMS (SQL Server Management Studio 21)

## **Insights & Recommendations**

- **Insights**
   - There is high demand and potential for future investments in tech products, bundles, or promotions.
   - The bottom 3 regions by sales showed underperformance which could signal lack of market penetration, logistics limitations or product relevance issues in those areas.
   - High returns rates could indicate product dissatisfaction or quality issues. It can even warrant an audit by product line or supplier.

- **Recommendations**
   - Control delivery expenses by aligning each shipping method with the urgency level of the order.
   - Promote top-selling tech and premium furnitureproducts to your most valuable customer segments for increased revenue.
   - Use customer segmentation to create specialised offers, like business bundles or swifter delivery options tailored to each group.
   - Address challenges in low-performing regions, then apply focused marketing strategies to increase sales.






   
