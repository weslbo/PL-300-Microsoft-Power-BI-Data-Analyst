---
lab:
    title: 'Prepare Data in Power BI Desktop'
    module: 'Module 2 - Get Data in Power BI'
---

# **Prepare Data in Power BI Desktop**

**The estimated time to complete the lab is 45 minutes**

In this lab you commence the development of a Power BI Desktop solution for the Adventure Works company. It involves connecting to source data, previewing the data, and using data preview techniques to understand the characteristics and quality of the source data.

In this lab you learn how to:

- Open Power BI Desktop

- Set Power BI Desktop options

- Connect to source data

- Preview source data

- Use data preview techniques to better understand the data

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. **Prepare Data in Power BI Desktop**

2. Load Data in Power BI Desktop

3. Model Data in Power BI Desktop

5. Create DAX Calculations in Power BI Desktop, Part 1

6. Create DAX Calculations in Power BI Desktop, Part 2

7. Design a Report in Power BI Desktop, Part 1

8. Design a Report in Power BI Desktop, Part 2

9. Create a Power BI Dashboard

10. Perform Data Analysis in Power BI Desktop

11. Enforce Row-Level Security

## **Exercise 1: Prepare Data**

In this exercise you will create eight Power BI Desktop queries. Six queries will source data from SQL Server, and two from CSV files.

### **Task 1: Save the Power BI Desktop file**

First create a new Power BI Desktop report and save it immediatly as **D:\PL300\MySolution\Sales Analysis.pbix**.

### **Task 2: Set Power BI Desktop options**

In this task you will set Power BI Desktop options. Make sure that for the **current file**, you do not automatically import relationships from data sources on first load. Also, you do not want Power BI Desktop to autodetect new relationships after data is loaded.

Tip: check the **Data Load** settings for the current file:

![Picture 7](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image9.png)

While having these two options enabled can be helpful when developing a data model, you disabled them earlier to support the lab experience. When you create relationships in the **Load Data in Power BI Desktop** lab, you’ll learn why you are adding each one.

### **Task 3: Get data from SQL Server**

In this task you will create queries based on SQL Server tables. Connect to the SQL Server database by using **localhost**. ( This isn’t a recommended practice when creating your own solutions. It’s because gateway data sources cannot resolve **localhost**.) If prompted for credentials, select **Use my current credentials**. You have to use the **AdventureWorksDW2020** database.

The **AdventureWorksDW2020** database is based on the **AdventureWorksDW2017** sample database. It has been modified to support the learning objectives of the course labs.

Create queries, for the following six tables:

	- DimEmployee

	- DimEmployeeSalesTerritory

	- DimProduct

	- DimReseller

	- DimSalesTerritory

	- FactResellerSales

You won’t be transforming the data in this lab. The objectives of this lab focus on exploring and profiling the data in the **Power Query Editor** window.

### **Task 4: Preview SQL Server queries**

In this task you will preview the data of the SQL Server queries. First, you will learn relevant information about the data. You will also use column quality, column distribution, and column profile tools to understand the data and to assess data quality.

1. Select the first query—**DimEmployee**.

	![Picture 33](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image21.png)

	The **DimEmployee** table in the SQL Server database stores one row for each employee. A subset of the rows from this table represents the salespeople, which will be relevant to the model you’ll develop.

2. Notice the table statistics—the table has 33 columns, and 296 rows.

	![Picture 36](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image22.png)

3. Notice that the last five columns contain **Table** or **Value** links.

	These five columns represent relationships to other tables in the database. They can be used to join tables together. You’ll join tables in the **Load Data in Power BI Desktop** lab.

4. Check the **Column Quality** for the **Position** column (sixth last column) and notice that 94% of rows are empty (null).

	![Picture 38](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image24.png)

5. Check the **Column Distribution** for the **Position** column, and notice that there are four distinct values, and one unique value.

6. Review the column distribution for the **EmployeeKey** (first) column—there are 296 distinct values, and 296 unique values.

	![Picture 43](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image26.png)

	When the distinct and unique counts are the same, it means the column contains unique values. When modeling, it’s important that some model tables have unique columns. These unique columns can be used to create one-to-many relationships, which you will do in the **Model Data in Power BI Desktop** lab.

7. Select the **DimEmployeeSalesTerritory** query.

	The **DimEmployeeSalesTerritory** table stores one row for each employee and the sales territory regions they manage. The table supports relating many regions to a single employee. Some employees manage one, two, or possibly more regions. When you model this data, you’ll need to define a many-to-many relationship.

8. Select the **DimProduct** query.

	The **DimProduct** table contains one row per product sold by the company.

9. Notice the **DimProductSubcategory** column.

	When you add transformations to this query in the **Load Data in Power BI Desktop** lab, you’ll use the **DimProductSubcategory** column to join tables.

10. Select the **DimReseller** query.

	The **DimReseller** table contains one row per reseller. Resellers sell, distribute, or value add to the Adventure Works products.

11. Check the **Column Profile** for the **BusinessType** column. Notice a data quality issue: there are two labels for warehouse (**Warehouse**, and the misspelled **Ware House**).

	![Picture 51](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image31.png)

12. Hover the cursor over the **Ware House** bar, and notice that there are five rows with this value.

    You’ll apply a transformation to relabel these five rows in the **Load Data in Power BI Desktop** lab.

13. Select the **DimSalesTerritory** query.

	The **DimSalesTerritory** table contains one row per sales region, including **Corporate HQ** (headquarters). Regions are assigned to a country, and countries are assigned to groups. In the **Model Data in Power BI Desktop** lab, you’ll create a hierarchy to support analysis at region, country, or group level.

14. Select the **FactResellerSales** query.

	The **FactResellerSales** table contains one row per sales order line—a sales order contains one or more line items.

15. Review the column quality for the **TotalProductCost** column, and notice that 8% of the rows are empty.

	![Picture 63](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image34.png)

	Missing **TotalProductCost** column values is a data quality issue. To address the issue, in the **Load Data in Power BI Desktop** lab, you’ll apply transformations to fill in missing values by using the product standard cost, which is stored in the related **DimProduct** table.


### **Task 5: Get data from a CSV file**

In this task you will create a query based on a CSV file.

1. Import the **D:\PL300\Resources\ResellerSalesTargets.csv** file.

	The **ResellerSalesTargets** CSV file contains one row per salesperson, per year. Each row records 12 monthly sales targets (expressed in thousands). Note that the business year for the Adventure Works company commences on July 1.

2. Notice that no column contains empty values.

	When there isn’t a monthly sales target, a hyphen character is stored instead.

3. Review the icons in each column header, to the left of the column name.

	![Picture 74](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image38.png)

	The icons represent the column data type. **123** is whole number, and **ABC** is text.

	You’ll apply many transformations to achieve a different shaped result consisting of only three columns: **Date**, **EmployeeKey**, and **TargetAmount** in the **Load Data in Power BI Desktop** lab.

### **Task 6: Get additional data from a CSV file**

In this task you will create an additional query based on a different CSV file.

Use the steps in the previous task to create a query based on the **D:\PL300\Resources\ColorFormats.csv** file.

The **ColorFormats** CSV file contains one row per product color. Each row records the HEX codes to format background and font colors. You’ll integrate this data with the **DimProduct** query data in the **Load Data in Power BI Desktop** lab.

### **Task 7: Finish up**

In this task you will complete the lab.

Save the Power BI Desktop file. When prompted to apply the queries, click **Apply Later**.

Applying the queries will load their data to the data model. You’re not ready to do that, as there are many transformations that must be applied first.

You’ll apply various transformations to the queries and then apply the queries to load them to the data model in the **Load Data in Power BI Desktop** lab.
