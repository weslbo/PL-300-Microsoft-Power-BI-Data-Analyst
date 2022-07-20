---
lab:
    title: 'Load Data in Power BI Desktop'
    module: 'Module 3 - Clean, Transform, and Load Data in Power BI'
---

# **Load Data in Power BI Desktop**

**The estimated time to complete the lab is 45 minutes**

In this lab you will commence apply transformations to each of the queries created in the previous lab. You will then apply the queries to load each as a table to the data model.

In this lab you learn how to:

- Apply various transformations

- Apply queries to load them to the data model

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop

2. **Load Data in Power BI Desktop**

3. Model Data in Power BI Desktop


5. Create DAX Calculations in Power BI Desktop, Part 1

6. Create DAX Calculations in Power BI Desktop, Part 2

7. Design a Report in Power BI Desktop, Part 1

8. Design a Report in Power BI Desktop, Part 2

9. Create a Power BI Dashboard

10. Perform Data Analysis in Power BI Desktop

11. Enforce Row-Level Security

## **Exercise 1: Load Data**

In this exercise you will apply transformations to each of the queries created in the previous lab.

### **Task 1: Get started**

*Important: If you are continuing on from the previous lab (and you completed that lab successfully), do not complete this task; instead, continue from the next task.*

1. Open the **D:\PL300\Labs\02-load-data-with-power-query-in-power-bi-desktop\Starter\Sales Analysis.pbix** file.

2. Save it immediately in the **D:\PL300\MySolution** folder.

3. Open **Power Query Editor** window again. *Tip: click the **Transform Data** icon.*

### **Task 2: Configure the Salesperson query**

1. Rename the **DimEmployee** query to **Salesperson**.

	*The query name will determine the model table name. It’s recommended to define concise, yet friendly, names.*

2. Filter the query rows to retrieve only employees who are salespeople. The **SalesPersonFlag** column can be used for this.

3. In the **Query Settings** pane, in the **Applied Steps** list, notice the addition of the **Filtered Rows** step.

	![Picture 98](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image17.png)

	*Each transformation you create results in additional step logic. It’s possible to edit or delete steps. It’s also possible to select a step to preview the query results at that stage of the query transformation.*

4. Remove all columns, except the following six columns:

	- EmployeeKey

	- EmployeeNationalIDAlternateKey

	- FirstName

	- LastName

	- Title

	- EmailAddress

5. Merge the **FirstName** and **LastName** column. Use a **Space** as the **Separator**. The new column should be named **Salesperson**.

6. Rename the **EmployeeNationalIDAlternateKey** column to **EmployeeID**.

	*Important: When instructed to rename columns, it’s important that you rename them exactly as described.*

7. Rename the **EmailAddress** column to **UPN**.

	*UPN is an acronym for User Principal Name.*

8. At the bottom-left, in the status bar, verify that the query has five columns and 18 rows.

	*Important: It’s important that you do not proceed if your query does not produce the correct result—it won’t be possible to complete later labs. If the query columns or rows don’t match, refer back to the steps in this task to fix any problems.*

### **Task 3: Configure the SalespersonRegion query**

In this task you will configure the **SalespersonRegion** query.

1. Rename the **DimEmployeeSalesTerritory** query to **SalespersonRegion**.

2. Remove the last two columns

3. In the status bar, verify that the query has two columns and 39 rows.

### **Task 4: Configure the Product query**

In this task you will configure the **Product** query.

1. Rename the **DimProduct** query to **Product**.

2. Locate the **FinishedGoodsFlag** column, and then filter the column to retrieve products that are finished goods (i.e. TRUE).

3. Remove all columns, except the following:

	- ProductKey

	- EnglishProductName

	- StandardCost

	- Color

	- DimProductSubcategory

4. Notice that the **DimProductSubcategory** column represents a related table (it contains **Value** links).

5. Expand the **DimProductSubcategory** column and check the **EnglishProductSubcategoryName** and **DimProductCategory** columns. Uncheck the **Use Original Column Name as Prefix** checkbox.

	![Picture 5646](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image32.png)

	*By selecting these two columns, a transformation will be applied to join to the **DimProductSubcategory** table, and then include these columns. The **DimProductCategory** column is, in fact, another related table in the data source.*

6. Notice that the transformation resulted in the addition of two columns, and that the **DimProductSubcategory** column has been removed.

7. Expand the **DimProductCategory** column, and then introduce only the **EnglishProductCategoryName** column.

8. Rename the following four columns:

	- **EnglishProductName** to **Product**

	- **StandardCost** to **Standard Cost** (include a space)

	- **EnglishProductSubcategoryName** to **Subcategory**

	- **EnglishProductCategoryName** to **Category**

9. In the status bar, verify that the query has six columns and 397 rows.

### **Task 5: Configure the Reseller query**

In this task you will configure the **Reseller** query.

1. Rename the **DimReseller** query to **Reseller**.

2. Remove all columns, except the following:

	- ResellerKey

	- BusinessType

	- ResellerName

	- DimGeography

3. Expand the **DimGeography** column, to include only the following three columns:

	- City

	- StateProvinceName

	- EnglishCountryRegionName

4. In the **Business Type** column header, review the distinct column values, and notice the incorrect spelling of **Ware House**.

	![Picture 2](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image38.png)

5. Replace **Ware House** to **Warehouse**.

6. Rename the following four columns:

	- **BusinessType** to **Business Type** (include a space)

	- **ResellerName** to **Reseller**

	- **StateProvinceName** to **State-Province**

	- **EnglishCountryRegionName** to **Country-Region**

7. In the status bar, verify that the query has six columns and 701 rows.

### **Task 6: Configure the Region query**

In this task you will configure the **Region** query.

1. Rename the **DimSalesTerritory** query to **Region**.

2. Apply a filter to the **SalesTerritoryAlternateKey** column to remove the value 0 (zero).

3. Remove all columns, except the following:

	- SalesTerritoryKey

	- SalesTerritoryRegion

	- SalesTerritoryCountry

	- SalesTerritoryGroup

4. Rename the following three columns:

	- **SalesTerritoryRegion** to **Region**

	- **SalesTerritoryCountry** to **Country**

	- **SalesTerritoryGroup** to **Group**

5. In the status bar, verify that the query has four columns and 10 rows.

### **Task 7: Configure the Sales query**

In this task you will configure the **Sales** query.

1. Rename the **FactResellerSales** query to **Sales**.

2. Remove all columns, except the following:

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

	*You may recall in the **Prepare Data in Power BI Desktop** lab that a small percentage of **FactResellerSales** rows had missing **TotalProductCost** values. The **DimProduct** column has been included to retrieve the product standard cost column to assist fixing the missing values.*

3. Expand the **DimProduct** column, and then include only the **StandardCost** column.

4. Create a custom column named **Cost**, with the following expression (after the equals symbol):

   **Power Query**
   ```
   if [TotalProductCost] = null then [OrderQuantity] * [StandardCost] else [TotalProductCost]
   ```

*This expression tests if the **TotalProductCost** value is missing. If it is, produces a value by multiplying the **OrderQuantity** value by the **StandardCost** value; otherwise, it uses the existing **TotalProductCost** value.*

5. Remove the following two columns:

	- TotalProductCost

	- StandardCost

6. Rename the following three columns:

	- **OrderQuantity** to **Quantity**

	- **UnitPrice** to **Unit Price** (include a space)

	- **SalesAmount** to **Sales**

7. Modify the column data type of the **Quantity** column to a **Whole Number**.

	*Configuring the correct data type is important. When the column contains numeric value, it’s also important to choose the correct type if you expect to perform mathematic calculations.*

8. Modify the following three column data types to **Fixed Decimal Number**.

	- Unit Price

	- Sales

	- Cost

	*The fixed decimal number data type stores values with full precision, and so requires more storage space that decimal number. It’s important to use the fixed decimal number type for financial values, or rates (like exchange rates).*

9. In the status bar, verify that the query has 10 columns and 999+ rows.

	*A maximum of 1000 rows will be loaded as preview data for each query.*

### **Task 8: Configure the Targets query**

In this task you will configure the **Targets** query.

1. Rename the **ResellerSalesTargets** query to **Targets**.

2. Unpivot the 12 month columns (**M01**-**M12**). Tip: first multi-select the **Year** and **EmployeeID** column headers and use **Unpivot Other Columns**.

3. Notice that the column names now appear in the **Attribute** column, and the values appear in the **Value** column.

4. Apply a filter to the **Value** column to remove hyphen (-) values.

	*You may recall that the hyphen character was used in the source CSV file to represent zero (0).*

5. Rename the following two columns:

	- **Attribute** to **MonthNumber** (there is no space between the two words—it will be removed later)

	- **Value** to **Target**

	*You’ll now apply transformations to produce a date column. The date will be derived from the **Year** and **MonthNumber** columns. You’ll create the column by using the **Columns From Examples** feature.*

6. Remove the "M" from the **MonthNumber** column and modify the column data type to **Whole Number**.

7. Use the **Column From Examples** feature and commence entering **7/1/2017**.

	*The virtual machine uses US regional settings, so this date is in fact July 1, 2017.*

8. Notice that the grid cells update with predicted values.

	*The feature has accurately predicted that you are combining values from the **Year** and **MonthNumber** columns.*

9. Notice also the formula presented above the query grid.

	![Picture 5679](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image60.png)

10. Rename the new column to **TargetMonth**.

11. Remove the following columns:

	- Year

	- MonthNumber

12. Modify the following column data types:

	- **Target** as fixed decimal number

	- **TargetMonth** as date

13. Multiply the **Target** values by 1000.

	*You may recall that the target values were stored as thousands.*

14. In the status bar, verify that the query has three columns and 809 rows.

### **Task 9: Configure the ColorFormats query**

In this task you will configure the **ColorFormats** query.

1. Select the **ColorFormats** query.

2. Promote the first row as the column names.

3. In the status bar, verify that the query has three columns and 10 rows.

### **Task 10: Update the Product query**

In this task you will update the **Product** query by merging the **ColorFormats** query.

1. Merge the **Product** query with the **ColorFormats** query, based on the matching **Color** column. Use the default **Join Kind** - maintaining the selection of Left Outer.

	*Merging queries allows integrating data, in this case from different data sources (SQL Server and a CSV file).*

2. When the **Privacy Levels** window opens, for each of the two data sources, in the corresponding dropdown list, select **Organizational**.

	![Picture 5691](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image74.png)

	*Privacy levels can be configured for data source to determine whether data can be shared between sources. Setting each data source as **Organizational** allows them to share data, if necessary. Note that Private data sources can never be shared with other data sources. It doesn’t mean that Private data cannot be shared; it means that the Power Query engine cannot share data between the sources.*

3. Expand the **ColorFormats** column to include the following two columns:

	- Background Color Format

	- Font Color Format

4. In the status bar, verify that the query now has eight columns and 397 rows.

### **Task 11: Update the ColorFormats query**

In this task you will update the **ColorFormats** to disable its load.

1. Uncheck the **Enable Load To Report** checkbox for the **ColorFormats** query.

	![Picture 323](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image81.png)

	Disabling the load means it will not load as a table to the data model. This is done because the query was merged with the **Product** query, which is enabled to load to the data model.

### **Task 12: Finish up**

In this task you will complete the lab.

1. Verify that you have eight queries, correctly named as follows:

	- Salesperson

	- SalespersonRegion

	- Product

	- Reseller

	- Region

	- Sales

	- Targets

	- ColorFormats (which will not load to the data model)

2. Load the data model by selecting **Close &amp; Apply**.

	*All load-enabled queries are now loaded to the data model.*

3. In the **Fields** pane (located at the right), notice the seven tables loaded to the data model.

	![Picture 3](Linked_image_Files/02-load-data-with-power-query-in-power-bi-desktop_image84.png)

4. Save the Power BI Desktop file.

5. If you intend to start the next lab, leave Power BI Desktop open.

	*You’ll configure data model tables and relationships in the **Model Data in Power BI Desktop** lab.*
