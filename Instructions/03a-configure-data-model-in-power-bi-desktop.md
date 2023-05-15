---
lab:
    title: 'Design a Data Model in Power BI (challenge version)'
    module: '4 - Design a Data Model in Power BI'
---


# Design a Data Model in Power BI (challenge version)

**The estimated time to complete the lab is 45 minutes.**

In this lab, you'll commence developing the data model. It will involve creating relationships between tables, and then configuring table and column properties to improve the friendliness and usability of the data model. You'll also create hierarchies and create quick measures.

In this lab you learn how to:

- Create model relationships
- Configure table and column properties
- Create hierarchies

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. Load Data in Power BI Desktop
1. **Design a Data Model in Power BI**
1. Create DAX Calculations in Power BI Desktop
1. Create Advanced DAX Calculations in Power BI Desktop
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Exercise 1: Create Model Relationships**

In this exercise, you'll create model relationships.

### **Task 1: Get started**

In this task, you'll set up the environment for the lab.

*Important: If you completed the previous lab in the same VM, **skip** to the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\03-configure-data-model-in-power-bi-desktop\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Create model relationships**

In this task, you'll create model relationships. The file was configured to not identify relationships between tables in the previous labs. This isn't the default setting, but is recommended to prevent extra work creating the correct relationships for your model.

*Important: The labs use a shorthand notation to reference a field. It will look like this: **Product \| Category**. In this example, **Product** is the table name and **Category** is the field name.*

1. Select the **Model** view icon and arrange the tables more closely together so they can all be seen at the same time.

     *Tip: You can also use the zoom control located at the bottom of the window.*

2. Return to the Report view and expand all fields from the the **Fields** pane.

3. Create a table visual, using the **Product \| Category** and **Sales \| Sales** fields.

4. Notice that the table visual lists four product categories, and that the sales value is the same for each, and the same for the total.
    
	*The issue is that the table is based on fields from different tables. The expectation is that each product category displays the sales for that category. However, because there isn’t a model relationship between these tables, the **Sales** table isn't filtered. You’ll now add a relationship to propagate filters between the tables.*

     ![Picture 330](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image13.png)

5. Create a relationship between the **Product** and **Sales** tables, based on the **ProductKey** column. The **Cardinality** should be **One To Many (1:*)**.
    
	*The cardinality was automatically detected, because Power BI understands that the **ProductKey** column from the **Product** table contains unique values. One-to-many relationships are the most common cardinality, and all relationship you create in this lab will be this type.*

6.  Set the **Cross Filter Direction** to **Single**.
    
	*Single filter direction means that filters propagate from the “one side” to the “many side”. In this case, it means filters applied to the **Product** table will propagate to the **Sales** table, but not in the opposite direction.*

7.  Make sure that **Mark This Relationship Active** is checked.
    
	*Active relationships propagate filters. It’s possible to mark a relationship as inactive so filters don’t propagate. Inactive relationships can exist when there are multiple relationship paths between tables. In this case, model calculations can use special functions to activate them.*

8.  Notice there's now a connector between the two tables (it doesn't matter if the tables are positioned next to each other).
    1. You can interpret the cardinality that is represented by the **1** and **(*)** indicators.
    2. Filter direction is represented by the arrow head.
    3. A solid line represents an active relationship; a dashed line represents an inactive relationship.
    4. Hover the cursor over the relationship to highlight the related columns.

     ![Picture 338](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image21.png)

9.  Create the following model relationships:

     - **Reseller \| ResellerKey** to **Sales \| ResellerKey**
     - **Region \| SalesTerritoryKey** to **Sales \| SalesTerritoryKey**
     - **Salesperson \| EmployeeKey** to **Sales \| EmployeeKey**

10. In the diagram, arrange the tables so that the **Sales** table is positioned in the center of the diagram, and the related tables are arranged about it. Position the disconnected tables to the side.

     ![Star schema design in Model view](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image23.png)

11. In the report view, notice that the table visual updated to display different values for each product category.
    
	*Filters applied to the **Product** table now propagate to the **Sales** table.*

     ![Updated category and sales numbers with new relationships.](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image20.png)

12. Save the Power BI Desktop file.

## **Exercise 2: Configure Tables**

In this exercise you'll configure each table by creating hierarchies, and hiding, formatting, and categorizing columns.

### **Task 1: Configure the Product table**

In this task, you'll configure the **Product** table.

1. In the **Product** table, create a hierarchy named **Products**, with the following three levels:

     - Category
     - Subcategory
     - Product
  
 	*Tip: Don’t forget to select **Apply Level Changes**—it’s a common mistake to overlook this step.*

     ![Picture 346](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image28.png)

2. Add the **Background Color Format** and **Font Color Format** columns into a **Display Folder** named **Formatting**.
    
	*Display folders are a great way to declutter tables—especially for tables that comprise many fields. They're logical presentation only.*

     ![Picture 349](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image30.png)

### **Task 2: Configure the Region table**

In this task, you'll configure the **Region** table.

1. In the **Region** table, create a hierarchy named **Regions**, with the following three levels:

     - Group
     - Country
     - Region

1. Set the **Data Category** of the **Country** column (not the **Country** hierarchy level) to **Country/Region**.

	*Data categorization can provide hints to the report designer. In this case, categorizing the column as country or region provides more accurate information to Power BI when it renders a map visualization.*

### **Task 3: Configure the Reseller table**

In this task, you'll configure the **Reseller** table.

1. In the **Reseller** table, create a hierarchy named **Resellers**, with the following two levels:

     - Business Type
     - Reseller

1. Create a second hierarchy named **Geography**, with the following four levels:

     - Country-Region
     - State-Province
     - City
     - Reseller

1. Set the **Data Category** for the **Country-Region**, **State-Province**, and **City** columns (not the hierarchy level) to **Country/Region**, **State or Province**, and **City**, respectively.

### **Task 4: Configure the Sales table**

In this task, you'll configure the **Sales** table.

1. In the **Sales** table, set the **Description** of the **Cost** column to: *Based on standard cost*.
    
	*Descriptions can be applied to tables, columns, hierarchies, or measures. In the **Fields** pane, description text is revealed in a tooltip when a report author hovers their cursor over the field.*

2. Set the formatting of the **Quantity** column to include a **thousands separator**.

3. Set the formatting of the **Unit Price** column include **2 Decimal Places**.

4. Set the default summarization for the **Unit Price** column to **average**.
    
	*By default, numeric columns will summarize by summing values together. This default behavior isn't suitable for a column like **Unit Price**, which represents a rate. Setting the default summarization to average will produce a meaningful result.*

### **Task 5: Bulk update properties**

In this task, you'll update multiple columns using single bulk updates. You'll use this approach to hide columns, and format column values.

1. Set the following columns to **Hidden**:

     - Produt \| ProductKey
     - Region \| SalesTerritoryKey
     - Reseller \| ResellerKey
     - Sales \| EmployeeKey
     - Sales \| ProductKey
     - Sales \| ResellerKey
     - Sales \| SalesOrderNumber
     - Sales \| SalesTerritoryKey
     - Salesperson \| EmployeeID
     - Salesperson \| EmployeeKey
     - Salesperson \| UPN
     - SalespersonRegion \| EmployeeKey
     - SalespersonRegion \| SalesTerritoryKey
     - Targets \| EmployeeID
    
	*The columns were hidden because they’re either used by relationships or will be used in row-level security configuration or calculation logic.*

 	*You’ll use the **SalesOrderNumber** in a calculation in the **Create DAX Calculations in Power BI Desktop** lab.*

2. Configure 0 **Decimal Places** for the following fields:

     - Product \| Standard Cost
     - Sales \| Cost
     - Sales \| Sales

## **Exercise 3: Review the Model Interface**

In this exercise you'll switch to Report view, and review the model interface.

### **Task 1: Review the model interface**

In this task you'll switch to Report view, and review the model interface.

1. Switch to Report view.

1. In the **Fields** pane, notice the following:

     - Columns, hierarchies and their levels are fields, which can be used to configure report visuals
     - Only fields relevant to report authoring are visible
     - The **SalespersonRegion** table isn't visible—because all of its fields are hidden
     - Spatial fields in the **Region** and **Reseller** table are adorned with a spatial icon
     - Fields adorned with the sigma symbol (Ʃ) will summarize, by default
     - A tooltip appears when hovering the cursor over the **Sales \| Cost** field

1. Expand the **Sales \| OrderDate** field, and then notice that it reveals a date hierarchy.
    
	*The **Targets \| TargetMonth** field delivers a similar hierarchy. These hierarchies weren't created by you. They were created automatically. There's a problem, however. The Adventure Works financial year commences on July 1 of each year. But, in these automatically created date hierarchies, the date hierarchy year commences on January 1 of each year.*

     ![Picture 359](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image40.png)

 You’ll now turn off this automatic behavior. In the **Create DAX Calculations in Power BI Desktop** lab, you’ll use DAX to create a date table, and configure it define the Adventure Works’ calendar.

1. To turn off auto/date time, Navigate to **File > Options and Settings > Options > Current File** group, and select **Data Load**.
    1. In the **Time Intelligence** section, uncheck **Auto Date/Time**.

     ![Picture 362](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image43.png)

1. In the **Fields** pane, notice that the date hierarchies are no longer available.

     ![Picture 363](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image45.png)

## **Exercise 4: Create Quick Measures**

In this exercise, you'll create two quick measures.

### **Task 1: Create quick measures**

In this task, you'll create two quick measures to calculate profit and profit margin.

*A quick measure creates the calculation formula for you. They’re easy and fast to create for simple and common calculations. You’ll create measures without using this tool in the **Create DAX Calculations in Power BI Desktop** lab.*

1. Create a **New Quick Measure** on the **Sales** table. Name the measure **Profit**. Configure the measure to calculate the difference between **Sales** and **Cost**.

2. Add another quick measure, named **Profit Margin**. Configure the measure to calculate the **Profit** divided by **Sales**. Set the format to **Percentage**, with two decimal places.

3. To test the two measures, add them to the **table** visual on the report page.

4. Verify that the measures produce reasonable results that are correctly formatted.

     ![Picture 378](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image57.png)

### **Task 2: Create a many-to-many relationship**

In this task, you'll create a many-to-many relationship between the **Salesperson** table and the **Sales** table.

 *The labs use a shorthand notation to reference a field. It will look like this: **Salesperson \| Salesperson** . In this example, **Salesperson**  is the table name and **Salesperson**  is the field name.*

1. In Power BI Desktop, in Report view, create a **table** visual based on the follow two fields:

     - Salesperson \| Salesperson
     - Sales \| Sales

     ![Picture 1](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image9.png)

     *The table displays sales made by each salesperson. However, there’s another relationship between salespeople and sales. Some salespeople belong to one, two, or possibly more sales regions. In addition, sales regions can have multiple salespeople assigned to them.*

     *From a performance management perspective, a salesperson’s sales (based on their assigned territories) need to be analyzed and compared with sales targets. You’ll create relationships to support this analysis in the next exercise.*

1. Notice that **Michael Blythe** has sold almost $9 million.

1. Switch to Model view and create the following two model relationships:

     - **Salesperson \| EmployeeKey** to **SalespersonRegion \| EmployeeKey**
     - **Region \| SalesTerritoryKey** to **SalespersonRegion \| SalesTerritoryKey**

    *The **SalespersonRegion** table can be considered to be a bridging table.*

1. Switch to Report view, and then notice that the visual hasn't updated—the sales result for Michael Blythe hasn't changed.

1. Switch back to Model view, and then follow the relationship filter directions (arrowhead) from the **Salesperson** table. 
    
	*Consider that the **Salesperson** table filters the **Sales** table. It also filters the **SalespersonRegion** table, but it doesn't continue by propagating filters to the **Region** table (the arrowhead is pointing the wrong direction).*

     ![Picture 380](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image11.png)

2. Modify the relationship between the **Region** and **SalespersonRegion** tables by setting the **Cross Filter Direction** to **Both**. Make sure to **Apply Security Filter in Both Directions**.

     *Notice that the relationship has a double arrowhead now.*

3. Switch to Report view, and then notice that the sales values have still not changed.
    
	*The issue now relates to the fact that there are two possible filter propagation paths between the **Salesperson** and **Sales** tables. This ambiguity is internally resolved, based on a “least number of tables” assessment. To be clear, you shouldn’t design models with this type of ambiguity—the issue will be addressed in part later in this lab, and by the completion of the **Create DAX Calculations in Power BI Desktop** lab.*

4. Switch to Model view to force filter propagation via the bridging table. You can do this by modifying the relationship between the **Salesperson** and **Sales** tables. It should become an inactive relationship.
    
	*The filter propagation will now follow the only active path. In the diagram, notice that the inactive relationship is represented by a dashed line.*

     ![Picture 5697](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image17.png)

6. Switch to Report view, and then notice that the sales for Michael Blythe are now nearly $22 million.

     ![Picture 5698](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image18.png)

7. Notice also, that the sales for each salesperson—if added—would exceed the table total.

     *It’s a common observation of a many-to-many relationship due to the double, triple, etc. counting of regional sales results. Consider Brian Welcker, the second salesperson listed. His sales amount equals the total sales amount. It’s the correct result due to the fact the he’s the Director of Sales; his sales are measured by the sales of all regions.*

     *While the many-to-many relationship is now working, it’s now not possible to analyze sales made by a salesperson (because the relationship is inactive). You’ll be able to reactivate the relationship when you introduce a calculated table that will allow analyzing sales made in the sales region(s) assigned to the salesperson (for performance analysis) in the **Create DAX Calculations in Power BI Desktop** lab.*

8.  In the model, rename the **Salesperson** table to **Salesperson (Performance)**.

*The renamed table now reflects its purpose: it’s used to report and analyze the performance of salespeople based on the sales of their assigned sales regions.*

### **Task 3: Relate the Targets table**

In this task, you'll create a relationship to the **Targets** table

1. Create a relationship from the **Salesperson (Performance) \| EmployeeID** column and the **Targets \| EmployeeID** column.

1. In Report view, add the **Targets \| Target** field to the table visual.

1. Resize the table visual so all columns are visible.

     ![Picture 5699](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image19.png)

 *It’s now possible to visualize sales and targets—but take care for two reasons. First, there’s no filter on a time period, and so targets also include future target amounts. Second, targets aren't additive, and so the total shouldn't be displayed. They can either be disabled by formatting the visual or removed by using calculation logic. You’ll follow the second approach by creating a target measure in the **Create Advanced DAX Calculations in Power BI Desktop** lab that will return BLANK when more than one salesperson is filtered.*

### **Task 4: Finish up**

In this task, you'll complete the lab.

Save the Power BI Desktop file.
