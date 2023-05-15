---
lab:
    title: 'Prepare Data in Power BI Desktop (challenge version)'
    module: '2 - Get Data in Power BI'
---

# Prepare Data in Power BI Desktop (challenge version)

**The estimated time to complete the lab is 45 minutes.**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. **Prepare Data in Power BI Desktop**
1. Load Data in Power BI Desktop
1. Design a Data Model in Power BI
1. Create DAX Calculations in Power BI Desktop
1. Create Advanced DAX Calculations in Power BI Desktop
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Lab story**

This lab is designed to introduce you to Power BI Desktop application and how to connect to data and how to use data preview techniques to understand the characteristics and quality of the source data. The learning objectives are:

- Open Power BI Desktop
- Connect to source data
- Preview source data
- Use data preview techniques to better understand the data

## **Exercise 1: Prepare Data**

In this exercise, you'll create eight Power BI Desktop queries. Six queries will source data from SQL Server, and two from CSV files.

### **Task 1: Get started with Power BI Desktop**

In this task, create a new Power BI file and configure the following **report-level** settings:

- Data Load > Import relationships from data sources on first load: **Disabled**
- Data Load > Autodetect new relationships after data is loaded: **Disabled**

*Note: While having these two options enabled can be helpful when developing a data model, you disabled them earlier to support the lab experience. When you create relationships in the **Load Data in Power BI Desktop** lab, you’ll learn why you're adding each one.*

Save the file as **Sales Analysis.pbix** to the following **D:\PL300\MySolution** folder.

### **Task 2: Get data from SQL Server**

Import the following tables from SQL Server database **AdventureWorksDW2020**. Connect to the SQL Server database by using **localhost**.

    - DimEmployee
    - DimEmployeeSalesTerritory
    - DimProduct
    - DimReseller
    - DimSalesTerritory
    - FactResellerSales

### **Task 3: Preview Data in Power Query Editor**

This task introduces the Power Query Editor and allows you to review and profile the data. This helps you determine how to clean and transform the data later.

1. Select the first query—**DimEmployee**. The **DimEmployee** table in the SQL Server database stores one row for each employee. A subset of the rows from this table represents the salespeople, which will be relevant to the model you’ll develop. At the bottom left corner of the status bar, some table statistics are provided—the table has 33 columns, and 296 rows.

     ![Count of 33 columns, 296 rows](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image22.png)

2. Notice that the last five columns contain **Table** or **Value** links. These five columns represent relationships to other tables in the database. They can be used to join tables together. You’ll join tables in the **Load Data in Power BI Desktop** lab.

3. Assess the **Column Quality** for the **Position** column. What's the percentage of empty (null) values?

     ![Column quality showing 94% empty rows](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image24.png)

4. Assess the **Column Distribution** for the **Position** column again, and notice that there are four distinct values, and one unique value.

5. Review the column distribution for the **EmployeeKey** column—there are 296 distinct values, and 296 unique values.
    
    *When the distinct and unique counts are the same, it means the column contains unique values. When modeling, it’s important that some model tables have unique columns. These unique columns can be used to create one-to-many relationships, which you'll do later in the **Model Data in Power BI Desktop** lab.*

     ![Column distribution showing 296 distinct, 296 unique values](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image26.png)

6.  Examine the **DimEmployeeSalesTerritory** table, which stores one row for each employee and the sales territory regions they manage. The table supports relating many regions to a single employee. Some employees manage one, two, or possibly more regions. When you model this data, you’ll need to define a many-to-many relationship.

7.  Examine the **DimProduct** table, which contains one row per product sold by the company.

8.  Notice the **DimProductSubcategory** column. When you add transformations to this query in the **Load Data in Power BI Desktop** lab, you’ll use the **DimProductSubcategory** column to join tables.

9.  Examine the **DimReseller** table, which contains one row per reseller. Resellers sell, distribute, or value add to the Adventure Works products.*

10. Check the **Column Profile** for the **BusinessType** column header, and notice the the data quality issue: there are two labels for warehouse (**Warehouse**, and the misspelled **Ware House**).

     ![Value distribution for the BusinessType column](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image31.png)

11. Hover the cursor over the **Ware House** bar, and notice that there are five rows with this value.
    
    *You’ll apply a transformation to relabel these five rows in the **Load Data in Power BI Desktop** lab.*

12. Examine the **DimSalesTerritory** table, which contains one row per sales region, including **Corporate HQ** (headquarters). Regions are assigned to a country, and countries are assigned to groups. In the **Model Data in Power BI Desktop** lab, you’ll create a hierarchy to support analysis at region, country, or group level.*

14. Examine the **FactResellerSales** table, which contains one row per sales order line—a sales order contains one or more line items.*

15. Review the column quality for the **TotalProductCost** column, and notice that 8% of the rows are empty.
    
    *Missing **TotalProductCost** column values is a data quality issue. To address the issue, in the **Load Data in Power BI Desktop** lab, you’ll apply transformations to fill in missing values by using the product standard cost, which is stored in the related **DimProduct** table.*

### **Task 4: Get data from a CSV file**

In this task, you'll create a new query based on CSV files.

1. Import the following CSV file: **D:\PL300\Resources\ResellerSalesTargets.csv**

    *The **ResellerSalesTargets** CSV file contains one row per salesperson, per year. Each row records 12 monthly sales targets (expressed in thousands). The business year for the Adventure Works company commences on July 1.*

2. Notice that no column contains empty values.  When there isn’t a monthly sales target, a hyphen character is stored instead.

3. Review the icons in each column header, to the left of the column name. The icons represent the column data type. **123** is whole number, and **ABC** is text.

     ![Picture 74](Linked_image_Files/01-prepare-data-with-power-query-in-power-bi-desktop_image38.png)

4. Create another query based on the **D:\PL300\Resources\ColorFormats.csv** file.
    
    *The **ColorFormats** CSV file contains one row per product color. Each row records the HEX codes to format background and font colors.*

*You should now have two new queries, **ResellerSalesTargets** and **ColorFormats**.*

![Queries list](Linked_image_Files/01-all-queries-loaded.png)

### **Task 5: Finish up**

In this task, you'll complete the lab.

1. **Save** the Power BI Desktop file. When prompted to apply the pending changes, select **Apply Later**.
    
    *Tip: Applying the queries will load their data to the data model. You’re not ready to do that, as there are many transformations that must be applied first.*
