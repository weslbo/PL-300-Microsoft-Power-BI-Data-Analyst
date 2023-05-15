---
lab:
    title: 'Load Data in Power BI Desktop (challenge version)'
    module: '3 - Clean, Transform, and Load Data in Power BI'
---

# Load Data in Power BI Desktop (challenge version)

**The estimated time to complete the lab is 45 minutes.**

In this lab, you'll apply transformations to each of the queries created in the previous lab. You'll then apply the queries to load each as a table to the data model.

In this lab you learn how to:

- Apply various transformations
- Apply queries to load them to the data model

## **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. **Load Data in Power BI Desktop**
1. Design a Data Model in Power BI
1. Create DAX Calculations in Power BI Desktop
1. Create Advanced DAX Calculations in Power BI Desktop
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Exercise 1: Load Data**

In this exercise, you'll apply transformations to each of the queries created in the previous lab.

### **Task 1: Get started**

In this task, you'll set up the environment for the lab.

*Important: If you completed the previous lab in the same VM, **skip** to the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\02-load-data-with-power-query-in-power-bi-desktop\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Configure the Salesperson query**

In this task, you'll use Power Query Editor to configure the **Salesperson** query.

*Important: When instructed to rename columns, it’s important that you rename them exactly as described.*

1. Rename the **DimEmployee** to **Salesperson**.
    
	*The query name determines the model table name. It’s recommended to define concise and user-friendly names.*

2. Locate the **SalesPersonFlag** column, by choosing the **Choose Columns** from the ribbon.

3. Filter the rows to retrieve only employees who are salespeople. Notice the addition of the **Filtered Rows** step.
    
	*Each transformation you create results in another step logic. It’s possible to edit or delete steps. It’s also possible to select a step to preview the query results at that stage of the query transformation.*

     ![Applied steps](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image17.png)

4. Keep only the following six columns:

    - EmployeeKey
    - EmployeeNationalIDAlternateKey
    - FirstName
    - LastName
    - Title
    - EmailAddress

5.  Merge the the **FirstName** and **LastName** column into a a single column, named **Salesperson**. Use **Space** as the **Separator**.

6.  Rename the **EmployeeNationalIDAlternateKey** column to **EmployeeID**.

7.  Rename the **EmailAddress** column to **UPN**.
    
	*UPN is an acronym for User Principal Name.*

8.  At the bottom-left, in the status bar, verify that the query has five columns and 18 rows.

### **Task 3: Configure the SalespersonRegion query**

In this task, you'll configure the **SalespersonRegion** query.

1. Rename the **DimEmployeeSalesTerritory** query to **SalespersonRegion**.

2. Remove the last two columns (**DimEmployee** and **DimSalesTerritory**)
   
3. In the status bar, verify that the query has two columns and 39 rows.

### **Task 4: Configure the Product query**

In this task, you'll configure the **Product** query.

1. Rename the **DimProduct** query to **Product**.

2. Locate the **FinishedGoodsFlag** column, and then filter the column to retrieve products that are finished goods (that is, TRUE).

3. Remove all columns, **except** the following:

    - ProductKey
    - EnglishProductName
    - StandardCost
    - Color
    - DimProductSubcategory

4. Notice that the **DimProductSubcategory** column represents a related table (it contains **Value** links).

5. Expand the **DimProductSubcategory** column. Do not **Use Original Column Name as Prefix**. Keep only the following columns:

	*By selecting these two columns, a transformation will be applied to join to the **DimProductSubcategory** table, and then include these columns. The **DimProductCategory** column is, in fact, another related table in the data source.*

6. Notice that the transformation resulted in the addition of two columns, and that the **DimProductSubcategory** column has been removed.

7. Expand the **DimProductCategory** column, and then introduce only the **EnglishProductCategoryName** column.

8.  Rename the following four columns:

    - **EnglishProductName** to **Product**
    - **StandardCost** to **Standard Cost** (include a space)
    - **EnglishProductSubcategoryName** to **Subcategory**
    - **EnglishProductCategoryName** to **Category**

9.  In the status bar, verify that the query has six columns and 397 rows.

### **Task 5: Configure the Reseller query**

In this task, you'll configure the **Reseller** query.

1. Select the **DimReseller** query and rename to **Reseller**.

1. Remove all columns, **except** the following:

    - ResellerKey
    - BusinessType
    - ResellerName
    - DimGeography

1. Expand the **DimGeography** column, to include **only** the following three columns:

    - City
    - StateProvinceName
    - EnglishCountryRegionName

2. Replace the value **Ware House** to **Warehouse** (notice the space) from the **Business Type** column.

3. Rename the following four columns:

    - **BusinessType** to **Business Type** (include a space)
    - **ResellerName** to **Reseller**
    - **StateProvinceName** to **State-Province**
    - **EnglishCountryRegionName** to **Country-Region**

4. In the status bar, verify that the query has six columns and 701 rows.

### **Task 6: Configure the Region query**

In this task, you'll configure the **Region** query.

1. Select the **DimSalesTerritory** query and rename the query to **Region**.

1. Apply a filter to the **SalesTerritoryAlternateKey** column to remove the value 0 (zero).
    
	*This will remove one row.*

1. Remove all columns, **except** the following:

    - SalesTerritoryKey
    - SalesTerritoryRegion
    - SalesTerritoryCountry
    - SalesTerritoryGroup

1. Rename the following three columns:

    - **SalesTerritoryRegion** to **Region**
    - **SalesTerritoryCountry** to **Country**
    - **SalesTerritoryGroup** to **Group**

1. In the status bar, verify that the query has four columns and 10 rows.

### **Task 7: Configure the Sales query**

In this task, you'll configure the **Sales** query.

1. Select the **FactResellerSales** query and rename it to **Sales**.

1. Remove all columns, **except** the following:

    - SalesOrderNumber
    - OrderDate
    - ProductKey
    - ResellerKey
    - EmployeeKey
    - SalesTerritoryKey
    - OrderQuantity
    - UnitPrice
    - TotalProductCost
    - SalesAmount
    - DimProduct
        
		*Note: You may recall in the **Prepare Data in Power BI Desktop** lab that a small percentage of **FactResellerSales** rows had missing **TotalProductCost** values. The **DimProduct** column has been included to retrieve the product standard cost column to assist fixing the missing values.*

2. Expand the **DimProduct** columnn and only include the **StandardCost** column.

3. Add a **Custom Column**, named **Cost**. The expression should calculate the **TotalProductCost** value by multiplying the **OrderQuantity** value by the **StandardCost** value, only if the **TotalProductCost** value is missing.

4. Remove the following two columns:

    - TotalProductCost
    - StandardCost

5. Rename the following three columns:

    - **OrderQuantity** to **Quantity**
    - **UnitPrice** to **Unit Price** (include a space)
    - **SalesAmount** to **Sales**

6. Set the data type of the **Quantity** column to **Whole Number**.
    
	*Configuring the correct data type is important. When the column contains numeric value, it’s also important to choose the correct type if you expect to perform mathematic calculations.*

7. Modify the following three column data types to **Fixed Decimal Number**.
    
	*The fixed decimal number data type allows for 19 digits, and allows for more precision to avoid rounding errors. It’s important to use the fixed decimal number type for financial values, or rates (like exchange rates).*

    - Unit Price
    - Sales
    - Cost

8. In the status bar, verify that the query has 10 columns and 999+ rows.
    
	*A maximum of 1000 rows will be loaded as preview data for each query.*

### **Task 8: Configure the Targets query**

In this task, you'll configure the **Targets** query.

1. Rename the **ResellerSalesTargets** query to **Targets**.

2. Unpivot the 12 month columns (**M01**-**M12**). (Tip:  multi-select the **Year** and **EmployeeID** columns.)

3. Apply a filter to the **Value** column to remove hyphen (-) values.

	*You may recall that the hyphen character was used in the source CSV file to represent zero (0).*

4. Rename the following two columns:

    - **Attribute** to **MonthNumber** (there's no space)
    - **Value** to **Target**

5. Remove the "M" value from the **MonthNumber** column.

6. Use the **Column From Examples** feature, to create a new column named **TargetMonth**. The first value should be **1/1/2017**.
    
	*The virtual machine uses US regional settings, so this date is in fact July 1, 2017. Other regional settings may require a **0** before the date.*

7.  Notice also the formula presented above the query grid.

     ![Picture 5679](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image60.png)

8.  Remove the following columns:

    - Year
    - MonthNumber

9.  Modify the following column data types:

    - **Target** as fixed decimal number
    - **TargetMonth** as date

10. Multiply the **Target** values by 1000.
    
	*You may recall that the target values were stored as thousands.*

     ![Picture 5682](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image63.png)

11. In the status bar, verify that the query has three columns and 809 rows.

### **Task 9: Configure the ColorFormats query**

In this task, you'll configure the **ColorFormats** query.

1. Promote the first Row as header.

2. In the status bar, verify that the query has three columns and 10 rows.

### **Task 10: Update the Product query**

In this task, you'll update the **Product** query by merging the **ColorFormats** query.

1. Merge the **Product** query with the **ColorFormats** query. Use the **Color** column as the matching column.
    
	*Merging queries allows integrating data, in this case from different data sources (SQL Server and a CSV file).*

2. When the **Privacy Levels** window opens, for each of the two data sources, in the corresponding dropdown list, select **Organizational**, then **Save**.
    
	*Privacy levels can be configured for data source to determine whether data can be shared between sources. Setting each data source as **Organizational** allows them to share data, if necessary. Private data sources can never be shared with other data sources. It doesn’t mean that Private data can't be shared; it means that the Power Query engine can't share data between the sources.*

     ![Picture 5691](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image74.png)


3. Include the following two columns:

    - Background Color Format
    - Font Color Format

4. In the status bar, verify that the query now has eight columns and 397 rows.

### **Task 11: Update the ColorFormats query**

In this task, you'll update the **ColorFormats** to disable its load.

1. Disable loading the **ColorFormats** query.
    
	*Disabling the load means it will not load as a table to the data model. This is done because the query was merged with the **Product** query, which is enabled to load to the data model.*

### **Task 12: Finish up**

In this task, you'll complete the lab.

1. Verify that you have eight queries, correctly named as follows:

    - Salesperson
    - SalespersonRegion
    - Product
    - Reseller
    - Region
    - Sales
    - Targets
    - ColorFormats (which won't load to the data model)

1. Load the data model.
    
2. In the **Fields** pane (located at the right), notice the seven tables loaded to the data model.

     ![Picture 3](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image84.png)

3. Save the Power BI Desktop file.

*You’ll configure data model tables and relationships in the **Model Data in Power BI Desktop** lab.*
