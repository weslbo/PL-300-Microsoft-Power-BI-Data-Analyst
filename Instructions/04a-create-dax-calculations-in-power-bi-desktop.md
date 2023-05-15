---
lab:
    title: 'Create DAX Calculations in Power BI Desktop (challenge version)'
    module: '5 - Create Model Calculations using DAX in Power BI'
---


# Create DAX Calculations in Power BI Desktop (challenge version)

**The estimated time to complete the lab is 45 minutes.**

In this lab you'll create calculated tables, calculated columns, and simple measures using Data Analysis Expressions (DAX).

In this lab you learn how to:

 - Create calculated tables
 - Create calculated columns
 - Create measures

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. Load Data in Power BI Desktop
1. Design a Data Model in Power BI
1. **Create DAX Calculations in Power BI Desktop**
1. Create Advanced DAX Calculations in Power BI Desktop
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Exercise 1: Create Calculated Tables**

In this exercise, you'll create two calculated tables. The first will be the **Salesperson** table, to allow a direct relationship between it and the **Sales** table. The second will be the **Date** table.

### **Task 1: Get started**

In this task, you'll set up the environment for the lab.

*Important: If you're continuing on from the previous lab (and you completed that lab successfully), don't complete this task; instead, continue from the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Create the Salesperson table**

In this task, you'll create the **Salesperson** calculated table (direct relationship to **Sales**).

A calculated table is created by first entering the table name, followed by the equals symbol (=), followed by a DAX formula that returns a table. The table name can't already exist in the data model.

The formula bar supports entering a valid DAX formula. It includes features like auto-complete, Intellisense and color-coding, enabling you to quickly and accurately enter the formula.

1. In Power BI Desktop, in Report view, on the **Modeling** ribbon, from inside the **Calculations** group, select **New Table**.

     ![Picture 1](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image9.png)

2. In the formula bar (which opens directly beneath the ribbon when creating or editing calculations), type **Salesperson =**, press **Shift+Enter**, type **'Salesperson (Performance)'**, and then press **Enter**.
    
	*For your convenience, all DAX definitions in this lab can be copied from the snippets file, located in **D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt**.*

	 ![Picture 4](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image10.png)

	 *This table definition creates a copy of the **Salesperson (Performance)** table. It copies the data only, however model properties like visibility, formatting, etc. aren't copied.*

     *Tip: You’re encouraged to enter “white space” (that is, carriage returns and tabs) to write formulas in an intuitive and easy-to-read format—especially when formulas are long and complex. To enter a carriage return, press **Shift+Enter**. “White space” is optional.*

1. In the **Fields** pane, notice that the table icon is a shade of blue (denoting a calculated table).

	![Picture 10](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image11.png)

	*Note: Calculated tables are defined by using a DAX formula that returns a table. It’s important to understand that calculated tables increase the size of the data model because they materialize and store values. They’re recomputed whenever formula dependencies are refreshed, as will be the case for this data model when new (future) date values are loaded into tables.*

	*Unlike Power Query-sourced tables, calculated tables can’t be used to load data from external data sources. They can only transform data based on what has already been loaded into the data model.*

1. Switch to Model view, and notice that the **Salesperson** table is available (you may need to reset view to find table).

1. Create a relationship from the **Salesperson \| EmployeeKey** column to the **Sales \| EmployeeKey** column.

2. **Delete** the inactive relationship between the **Salesperson (Performance)** and **Sales** tables.

3. Hide the following columns from the **Salesperson** table:

	- EmployeeID
	- EmployeeKey
	- UPN

4. Set the description of the **Salesperson** table to **Salesperson related to Sales**
    
	*You may recall that descriptions appear as tooltips in the **Fields** pane when the user hovers their cursor over a table or field.*

5. For the **Salesperson (Performance)** table, set the description to: **Salesperson related to region(s)**

*The data model now provides two alternatives when analyzing salespeople. The **Salesperson** table allows analyzing sales made by a salesperson, while the **Salesperson (Performance)** table allows analyzing sales made in the sales region(s) assigned to the salesperson.*

### **Task 3: Create the Date table**

In this task, you'll create the **Date** table.

1. Switch to Data view. On the **Home** ribbon tab, from inside the **Calculations** group, select **New Table**.

2. In the formula bar, enter the following:

	**DAX**

	```
	Date =  
	CALENDARAUTO(6)
	```

	![Picture 6](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image16.png)

	
	*The CALENDARAUTO() function returns a single-column table consisting of date values. The “auto” behavior scans all data model date columns to determine the earliest and latest date values stored in the data model. It then creates one row for each date within this range, extending the range in either direction to ensure full years of data is stored.*

	*This function can take a single optional argument that is the last month number of a year. When omitted, the value is 12, meaning that December is the last month of the year. In this case, 6 is entered, meaning that June is the last month of the year.*

3. Notice the column of date values.

	![Picture 7](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image17.png)

	*The dates shown are formatted using US regional settings (that is, mm/dd/yyyy).*

4. At the bottom-left corner, in the status bar, notice the table statistics, confirming that 1826 rows of data have been generated, which represents five full years’ data.

	![Picture 9](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image18.png)

### **Task 4:** **Create calculated columns**

In this task, you'll add more columns to enable filtering and grouping by different time periods. You'll also create a calculated column to control the sort order of other columns.

*For your convenience, all DAX definitions in this lab can be copied from the snippets file, located in **D:\PL300\Labs\04-create-dax-calculations-in-power-bi-desktop\Assets\Snippets.txt**.*

1. Create a new calculated column **Year** with a DAX expression that returns the fiscal year. The formula should use the date’s year value but add one to the year value when the month is after June. It’s how fiscal years at Adventure Works are calculated.

	![Picture 12](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image20.png)

2. Create another two calculated columns for the **Date** table:

	- Quarter
	- Month

	![Picture 14](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image21.png)

3. To create a new report page.

4. Add a matrix visual to the new report page. It should include **Year** and **Month** in the **Rows** well/area.

5. Notice that the years expand to months, and that the months are sorted alphabetically rather than chronologically.

	![Picture 20](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image27.png)

	*By default, text values sort alphabetically, numbers sort from smallest to largest, and dates sort from earliest to latest.*

6.  To customize the **Month** field sort order, switch to Data view.

7.  Add the **MonthKey** column to the **Date** table. The formula should compute a numeric value for each year/month combination. For example, **201707** for July 2017, etc.

8. Switch back to Report view. In the **Fields** pane, ensure that the **Month** field is selected (when selected, it will have a dark gray background).

9.  On the **Column Tools** contextual ribbon, from inside the **Sort** group, select **Sort by Column**, and then select **MonthKey**.

	![Picture 22](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image29.png)

10. In the matrix visual, notice that the months are now chronologically sorted.

	![Picture 23](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image30.png)

### **Task 5:** **Complete the Date table**

In this task, you'll complete the design of the **Date** table by hiding a column and creating a hierarchy. You'll then create relationships to the **Sales** and **Targets** tables.

1. Switch to Model view. In the **Date** table, hide the **MonthKey** column.

2. Create a hierarchy in the **Date** table, named **Fiscal**. The hierarchy should include the following fields:

	- Year
	- Quarter
	- Month

	![Picture 24](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image31.png)

3. Create the following two model relationships:

	- **Date \| Date** to **Sales \| OrderDate**
	- **Date \| Date** to **Targets \| TargetMonth**

4. Hide the following two columns:

	- Sales \| OrderDate
	- Targets \| TargetMonth

### **Task 6: Mark the Date table**

In this task, you'll mark the **Date** table as a date table.

1. Mark the Date table as a **Date Table**. 
   
	![Picture 37](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image33.png)

2. Save the Power BI Desktop file.

	*Power BI Desktop now understands that this table defines date (time). It’s important when relying on time intelligence calculations. You’ll work with time intelligence calculations in the **Create Advanced DAX Calculations in Power BI Desktop** lab.*

	*This design approach for a date table is suitable when you don’t have a date table in your data source. If you have a data warehouse, it would be appropriate to load date data from its date dimension table rather than “redefining” date logic in your data model.*

## **Exercise 2: Create Measures**

In this exercise, you'll create and format several measures.

### **Task 1: Create simple measures**

In this task, you'll create simple measures. Simple measures aggregate values in a single column or count rows of a table.

1. In Report view, on **Page 2**, in the **Fields** pane, drag the **Sales \| Unit Price** field into the matrix visual.

	*The labs use a shorthand notation to reference a field. It will look like this: **Sales \| Unit Price**. In this example, **Sales** is the table name and **Unit Price** is the field name.*

	![Picture 27](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image35.png)

	*You may recall that in the **Model Data in Power BI Desktop** lab, you set the **Unit Price** column to summarize by **Average**. The result you see in the matrix visual is the monthly average unit price (sum of unit price values divided by the count of unit prices).*

1. In the visual fields pane (located beneath the **Visualizations** pane), in the **Values** field well/area, notice that **Unit Price** is listed.

	![Picture 28](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image36.png)

1. Select the down-arrow for **Unit Price**, and then notice the available menu options.

	![Picture 30](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image37.png)

	*Visible numeric columns allow report authors at report design time to decide how column values will summarize (or not). It can result in inappropriate reporting. Some data modelers don’t like leaving things to chance, however, and choose to hide these columns and instead expose aggregation logic defined in measures. It’s the approach you'll now take in this lab.*

2. Create a new measure named **Avg Price** in the **Sales** table, based on the average of the unit price.

3. Notice that it produces the same result as the **Unit Price** column (but with different formatting).

4. In the **Values** well, open the context menu for the **Avg Price** field, and notice that it isn't possible to change the aggregation technique.

	![Picture 32](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image39.png)

	*It’s not possible to modify the aggregation behavior of a measure.*

5. Create the following five measures for the **Sales** table:

	- Median Price
	- Min Price
	- Max Price
	- Orders (tip: you should count orders only once (ignoring duplicate **SalesOrderNumber** values))
	- Order Lines (tip: the number of order lines is simply the number of table rows (each row is a line of an order).)

6. For the following measures, set the format to two decimal places and assign them to a display folder named **Pricing**: 

	- Avg Price
	- Max Price
	- Median Price
	- Min Price

7.  Hide the **Unit Price** column.

	*The **Unit Price** column is now not available to report authors. They must use the pricing measures you’ve added to the model. This design approach ensures that report authors won’t inappropriately aggregate prices, for example, by summing them.*

8.  Multi-select the **Order Lines** and **Orders** measures, and then configure the following requirements:

	- Set the format use the thousands separator

	- Assign to a display folder named **Counts**

9.  In Report view, remove the **Unit Price** from the matrix visual.
    
10. Add the following five measures to the matrix visual:

	- Median Price
	- Min Price
	- Max Price
	- Orders
	- Order Lines

11. Verify that the results look sensible and are correctly formatted.

	![Picture 39](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image43.png)

### **Task 2: Create additional measures**

In this task, you'll create more measures that use more complex formulas.

1. In Report view, select **Page 1** and review the table visual, noticing the total for the **Target** column.

	![Picture 41](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image45.png)

2. Remove the **Target** field from the table visual.

3. Rename the **Targets \| Target** column as **Targets \| TargetAmount**.

	*Tip: There are several ways to rename the column in Report view: In the **Fields** pane, you can right-click the column, and then select **Rename**—or, double-click the column, or press **F2**.*

	*You’re about to create a measure named **Target**. It’s not possible to have a column and measure in the same table with the same name.*

4. Create a measure named **Target** on the **Targets** table. It should use a function which tests whether a single value in the **Salesperson** column is filtered. When true, the expression should return the sum of target amounts (for just that salesperson). When false, BLANK is returned. Format it to display zero decimal places.

5. Hide the **TargetAmount** column.

6. Add the **Target** measure to the table visual. Notice that the **Target** column total is now BLANK.

	![Picture 43](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image47.png)

7. Create the following two measures for the **Targets** table:

	- Variance: sales minus target, but only for the sales person (zero decimal places)
	- Variance Margin: variance divided by target (percentage with two decimal places)

8.  Add the **Variance** and **Variance Margin** measures to the table visual.

	![Picture 44](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image48.png)

	*While it appears all salespeople aren't meeting target, remember that the table visual isn’t yet filtered by a specific time period. You’ll produce sales performance reports that filter by a user-selected time period in the **Design a Report in Power BI Desktop** lab.*

9.  At the top-right corner of the **Fields** pane, notice that the **Targets** table now appears at the top of the list.

	![Picture 46](Linked_image_Files/05-create-dax-calculations-in-power-bi-desktop_image50.png)

	*Tables that comprise only visible measures are automatically listed at the top of the list.*

### **Task 3: Finish up**

In this task, you'll complete the lab.

Save the Power BI Desktop file.

*You’ll enhance the data model with more advanced calculations using DAX in the **Create Advanced DAX Calculations in Power BI Desktop** lab.*
