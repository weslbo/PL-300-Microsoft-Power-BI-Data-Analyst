---
lab:
    title: 'Model Data in Power BI Desktop'
    module: 'Module 4 - Design a Data Model in Power BI'
---


# **Model Data in Power BI Desktop**

**The estimated time to complete the lab is 45 minutes**

In this lab you will commence developing the data model. It will involve creating relationships between tables, and then configuring table and column properties to improve the friendliness and usability of the data model. You will also create hierarchies and create quick measures.

In this lab you learn how to:

- Create model relationships

- Configure table and column properties

- Create hierarchies


### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop

2. Load Data in Power BI Desktop

3. **Model Data in Power BI Desktop**

5. Create DAX Calculations in Power BI Desktop, Part 1

6. Create DAX Calculations in Power BI Desktop, Part 2

7. Design a Report in Power BI Desktop, Part 1

8. Design a Report in Power BI Desktop, Part 2

9. Create a Power BI Dashboard

10. Perform Data Analysis in Power BI Desktop

11. Enforce Row-Level Security

## **Exercise 1: Create Model Relationships**

In this exercise you will create model relationships.

### **Task 1: Get started**

*Important: If you are continuing on from the previous lab (and you completed that lab successfully), do not complete this task; instead, continue from the next task.*

1. Open the **D:\PL300\Labs\03-configure-data-model-in-power-bi-desktop\Starter\Sales Analysis.pbix** file.

2. Save it immediately in the **D:\PL300\MySolution** folder.

3. Open **Power Query Editor** window again. *Tip: click the **Transform Data** icon.*

### **Task 2: Create model relationships**

In this task you will create model relationships.

1. In Power BI Desktop, navigate to the **Model** view.

	*In Model view, it’s possible to view each table and relationships (connectors between tables). Presently, there are no relationships because in the **Prepare Data in Power BI Desktop** lab, you disabled the data load relationship options.*

2. Return back to the Report view, and create a table visual with the **Product \| Category** and **Sales \| Sales** fields. It should look like this:

	![Picture 330](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image13.png)

	*The labs use a shorthand notation to reference a field. It will look like this: **Product \| Category**. In this example, **Product** is the table name and **Category** is the field name.*

3. Notice that the table visual lists four product categories, and that the sales value is the same for each, and the same for the total. The issue is that the table is based on fields from different tables. The expectation is that each product category displays the sales for that category. However, because there isn’t a model relationship between these tables, the **Sales** table is not filtered. You’ll now add a relationship to propagate filters between the tables.

3. Create a new relationship between the **Product** table and the **Sales** table. The **ProductKey** column can be used to join the two tables.

4. In the **Cardinality** dropdown list, notice that **One To Many (1:*)** is selected.

	*The cardinality was automatically detected, because Power BI understands that the **ProductKey** column from the **Product** table contains unique values. One-to-many relationships are the most common cardinality, and all relationship you create in this lab will be this type.*

5. In the **Cross Filter Direction** dropdown list, notice that **Single** is selected.

	*Single filter direction means that filters propagate from the “one side” to the “many side”. In this case, it means filters applied to the **Product** table will propagate to the **Sales** table, but not in the opposite direction.*

6. Notice that the **Mark This Relationship Active** is checked.

	*Active relationships propagate filters. It’s possible to mark a relationship as inactive so filters don’t propagate. Inactive relationships can exist when there are multiple relationship paths between tables. In this case, model calculations can use special functions to activate them.*

7. In the report, notice that the table visual updated to display different values for each product category.

	![Picture 337](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image20.png)

	*Filters applied to the **Product** table now propagate to the **Sales** table.*

8. In the model, on the diagram, notice that you can interpret the cardinality on the relationship which is represented by the **1** and ***** indicators.

	*Filter direction is represented by the arrow head. A solid line represents an active relationship; a dashed line represents an inactive relationship.*

9. Create the following three model relationships:

	- **Reseller \| ResellerKey** to **Sales \| ResellerKey**

	- **Region \| SalesTerritoryKey** to **Sales \| SalesTerritoryKey**

	- **Salesperson \| EmployeeKey** to **Sales \| EmployeeKey**

10. In the diagram, arrange the tables so that the **Sales** table is positioned in the center of the diagram, and the related tables are arranged about it. Position the disconnected tables to the side.

	![Picture 340](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image23.png)

11. Save the Power BI Desktop file.

## **Exercise 2: Configure Tables**

In this exercise you will configure each table by creating hierarchies, and hiding, formatting, and categorizing columns.

### **Task 1: Configure the Product table**

In this task you will configure the **Product** table.

1. Create a hierarchy, starting from the **Products \| Category** column. Add the **Subcategory** and **Product** columns to it. Name the hierarchy **Products** and do not forget to click **Apply Level Changes**.

	![Picture 343](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image26.png)

2. In the **Fields** pane, notice the **Products** hierarchy.

	![Picture 346](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image28.png)

3. Add the **Background Color Format** and **Font Color Format** columns into a new display folder named **Formatting**.

	![Picture 349](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image30.png)

	*Display folders are a great way to declutter tables—especially for tables that comprise many fields.*

### **Task 2: Configure the Region table**

In this task you will configure the **Region** table.

1. In the **Region** table, create a hierarchy named **Regions**, with the following three levels:

	- Group

	- Country

	- Region

2. Select the **Country** column (not the **Country** hierarchy level) and configure the **Data Category** for this column to be a **Country/Region**.

	![Picture 352](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image32.png)

	*Data categorization can provide hints to the report designer. In this case, categorizing the column as country or region provides more accurate information to Power BI when it renders a map visualization.*

### **Task 3: Configure the Reseller table**

In this task you will configure the **Reseller** table.

1. In the **Reseller** table, create a hierarchy named **Resellers**, with the following two levels:

	- Business Type

	- Reseller

2. Create a second hierarchy named **Geography**, with the following four levels:

	- Country-Region

	- State-Province

	- City

	- Reseller

3. Set the **Data Category** for the **Country-Region**, **State-Province**, and **City** columns (not the hierarchy level) to **Country/Region**, **State or Province**, and **City**, respectively. 

### **Task 4: Configure the Sales table**

In this task you will configure the **Sales** table.

1. In the **Sales** table, set the description of the **Cost** column to: **Based on standard cost**

	*Descriptions can be applied to tables, columns, hierarchies, or measures. In the **Fields** pane, description text is revealed in a tooltip when a report author hovers their cursor over the field.*

2. Enable the **Thousands Separator** for the **Quantity** column.

3. Set the **Decimal Places** property to **2** for the **Unit Price** column and set the default summarization to **Average**.

	*By default, numeric columns will summarize by summing values together. This default behavior is not suitable for a column like **Unit Price**, which represents a rate. Setting the default summarization to average will produce a meaningful result.*

### **Task 5: Bulk update properties**

In this task you will update multiple columns using single bulk updates. You will use this approach to hide columns, and format column values.

1. Hide the following fields (tip: use the **Ctrl** key to select multiple columns at once)

	- Product \| ProductKey

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

	*You’ll use the **SalesOrderNumber** in a calculation in the **Create DAX Calculations in Power BI Desktop, Part 1** lab.*

4. Set the **Decimal Places** to **0** (zero) for the following three columns:

	- Product \| Standard Cost

	- Sales \| Cost

	- Sales \| Sales

## **Exercise 3: Review the Model Interface**

### **Task 1: Review the model interface**

In this task you will switch to Report view, and review the model interface.

1. Switch to Report view.

2. In the **Fields** pane, notice the following:

	- Columns, hierarchies and their levels are fields, which can be used to configure report visuals

	- Only fields relevant to report authoring are visible

	- The **SalespersonRegion** table is not visible—because all of its fields are hidden

	- Spatial fields in the **Region** and **Reseller** table are adorned with a spatial icon

	- Fields adorned with the sigma symbol (Ʃ) will summarize, by default

	- A tooltip appears when hovering the cursor over the **Sales \| Cost** field

3. Expand the **Sales \| OrderDate** field, and then notice that it reveals a date hierarchy.

	![Picture 359](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image40.png)

	*The **Targets \| TargetMonth** field delivers a similar hierarchy. These hierarchies were not created by you. They were created automatically. There is a problem, however. The Adventure Works financial year commences on July 1 of each year. But, in these automatically created date hierarchies, the date hierarchy year commences on January 1 of each year.*

	*You’ll now turn this automatic behavior off. In the **Create DAX Calculations in Power BI Desktop, Part 1** lab, you’ll use DAX to create a date table, and configure it define the Adventure Works’ calendar.*

4. Turn off auto/date time. You can do this from **Options and Settings** in the **Current File / Data Load** group.

	![Picture 362](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image43.png)

5. In the **Fields** pane, notice that the date hierarchies are no longer available.

	![Picture 363](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image45.png)

## **Exercise 4: Create Quick Measures**

In this exercise you will create two quick measures.

### **Task 1: Create quick measures**

In this task you will create two quick measures to calculate profit and profit margin.

1. Create a **New Quick Measure** from the **Sales** table that calculates the sales minus the cost.

	![Picture 368](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image48.png)

	*A quick measure creates the calculation formula for you. They’re easy and fast to create for simple and common calculations. You’ll create measures without using this tool in the **Create DAX Calculations in Power BI Desktop, Part 1** lab.*

2. In the **Fields** pane, inside the **Sales** table, notice that new measure.

	![Picture 370](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image50.png)

	*Measures are adorned with the calculator icon.*

3. Rename the measure to **Profit**, and then press **Enter**.

4. In the **Sales** table, add a second quick measure named **Profit Margin**.

	- Use the **Division** mathematical operation

	- Set the **Numerator** to the **Sales \| Profit** field

	- Set the **Denominator** to **Sales \| Sales** field

	![Picture 372](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image52.png)

5. For the **Profit Margin** measure, set the format to **Percentage**, with two decimal places.

6. To test the two measures, go back to the table visual on the report page. Add the **Profit** and **Profit Margin** to the table visual. Verify that the measures produce reasonable results that are correctly formatted.

	![Picture 378](Linked_image_Files/03-configure-data-model-in-power-bi-desktop_image57.png)

### **Task 2: Create a many-to-many relationship**

In this task you will create a many-to-many relationship between the **Salesperson** table and the **Sales** table.

1. In Power BI Desktop, in Report view, create another table visual with the following two fields:

	- Salesperson \| Salesperson

	- Sales \| Sales

	![Picture 1](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image9.png)

	*The table displays sales made by each salesperson. However, there’s another relationship between salespeople and sales. Some salespeople belong to one, two, or possibly more sales regions. In addition, sales regions can have multiple salespeople assigned to them.*

	*From a performance management perspective, a salesperson’s sales (based on their assigned territories) need to be analyzed and compared with sales targets. You’ll create relationships to support this analysis in the next exercise.*

2. Notice that Michael Blythe has sold almost $9 million.

3. Switch to Model view and create the following two model relationships:

	- **Salesperson \| EmployeeKey** to **SalespersonRegion \| EmployeeKey**

	- **Region \| SalesTerritoryKey** to **SalespersonRegion \| SalesTerritoryKey**

	*The **SalespersonRegion** table can be considered to be a bridging table.*

6. Switch to Report view, and then notice that the visual has not updated—the sales result for Michael Blythe has not changed.

7. Switch back to Model view, and then follow the relationship filter directions (arrowhead) from the **Salesperson** table.

	*Consider that the **Salesperson** table filters the **Sales** table. It also filters the **SalespersonRegion** table, but it does not continue by propagating filters to the **Region** table (the arrowhead is pointing the wrong direction).*

	![Picture 380](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image11.png)

8. Edit the relationship between the **Region** and **SalespersonRegion** tables and set the **Cross Filter Direction** to **Both**. Check the **Apply Security Filter in Both Directions** checkbox.

	![Picture 381](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image12.png)

12. Notice that the relationship has a double arrowhead.

	![Picture 382](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image14.png)

13. Switch to Report view, and then notice that the sales values have still not changed.

	*The issue now relates to the fact that there are two possible filter propagation paths between the **Salesperson** and **Sales** tables. This ambiguity is internally resolved, based on a “least number of tables” assessment. To be clear, you shouldn’t design models with this type of ambiguity—the issue will be addressed in part later in this lab, and by the completion of the **Create DAX Calculations in Power BI Desktop, Part 1** lab.*

14. Switch to Model view.

15. To force filter propagation via the bridging table, edit (double-click) the relationship between the **Salesperson** and **Sales** tables.

16. In the **Edit Relationship** window, uncheck the **Make This Relationship Active** checkbox.

	![Picture 383](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image15.png)

	*The filter propagation will now follow the only active path.*

18. In the diagram, notice that the inactive relationship is represented by a dashed line.

	![Picture 5697](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image17.png)

19. Switch to Report view, and then notice that the sales for Michael Blythe is now nearly $22 million.

	![Picture 5698](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image18.png)

20. Notice also, that the sales for each salesperson—if added—would exceed the table total.

	*It’s a common observation of a many-to-many relationship due to the double, triple, etc. counting of regional sales results. Consider Brian Welcker, the second salesperson listed. His sales amount equals the total sales amount. It’s the correct result simply due to the fact the he’s the Director of Sales; his sales are measured by the sales of all regions.*

	*While the many-to-many relationship is now working, it’s now not possible to analyze sales made by a salesperson (because the relationship is inactive). You’ll be able to reactivate the relationship when you introduce a calculated table that will allow analyzing sales made in the sales region(s) assigned to the salesperson (for performance analysis) in the **Create DAX Calculations in Power BI Desktop, Part 1** lab.*

21. Switch to Modeling view, and rename the **Salesperson** table to **Salesperson (Performance)**.

	*The renamed table now reflects its purpose: it’s used to report and analyze the performance of salespeople based on the sales of their assigned sales regions.*

### **Task 3: Relate the Targets table**

In this task you will create a relationship to the **Targets** table

1. Create a relationship from the **Salesperson (Performance) \| EmployeeID** column and the **Targets \| EmployeeID** column.

2. In Report view, add the **Targets \| Target** field to the table visual.

3. Resize the table visual so all columns are visible.

	![Picture 5699](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image19.png)

	*It’s now possible to visualize sales and targets—but take care for two reasons. First, there’s no filter on a time period, and so targets also include future target amounts. Second, targets are not additive, and so the total should not be displayed. They can either be disabled by formatting the visual or removed by using calculation logic. You’ll follow the second approach by creating a target measure in the **Create DAX Calculations in Power BI Desktop, Part 2** lab that’ll return BLANK when more than one salesperson is filtered.*

### **Task 4: Finish up**

In this task you will complete the lab.

1. Save the Power BI Desktop file.

2. If prompted to apply queries, click **Apply Later**.

3. If you intend to start the next lab, leave Power BI Desktop open.
