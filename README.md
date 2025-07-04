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

   
