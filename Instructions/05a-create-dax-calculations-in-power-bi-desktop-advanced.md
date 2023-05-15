---
lab:
    title: 'Create Advanced DAX Calculations in Power BI Desktop (challenge version)'
    module: '5 - Create Model Calculations using DAX in Power BI'
---


# Create Advanced DAX Calculations in Power BI Desktop (challenge version)

**The estimated time to complete the lab is 45 minutes.**

In this lab, you'll create measures with DAX expressions involving filter context manipulation.

In this lab you learn how to:

- Use the CALCULATE() function to manipulate filter context

- Use Time Intelligence functions

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. Load Data in Power BI Desktop
1. Design a Data Model in Power BI
1. Create DAX Calculations in Power BI Desktop
1. **Create Advanced DAX Calculations in Power BI Desktop**
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Exercise 1: Work with Filter Context**

In this exercise, you'll create measures with DAX expressions involving filter context manipulation.

### **Task 1: Get started**

In this task, you'll set up the environment for the lab.

*Important: If you're continuing on from the previous lab (and you completed that lab successfully), don't complete this task; instead, continue from the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\05-create-dax-calculations-in-power-bi-desktop-advanced\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Create a matrix visual**

In this task, you'll create a matrix visual to support testing your new measures.

1. In Report view, create a new report page and add a matrix visual.

2. Add the following elements to the **Matrix** visual:

    - **Region \| Regions** hierarchy (*You may recall that the **Regions** hierarchy has the levels **Group**, **Country**, and **Region**.*)
    - **Sales \| Sales** field

3. Resize the matrix visual to fill the entire page.

4. Expand the entire hierarchy

5. Format the visual, to that **Stepped Layout** is set to **Off**.

6.  Verify that the matrix visual now has four column headers.

    ![Picture 50](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image15.png)

    *At Adventure Works, the sales regions are organized into groups, countries, and regions. All countries—except the United States—have just one region, which is named after the country. As the United States is such a large sales territory, it’s divided into five sales regions.*

    *You’ll create several measures in this exercise, and then test them by adding them to the matrix visual.*

### **Task 3: Manipulate filter context**

In this task, you'll create several measures with DAX expressions that use the CALCULATE() function to manipulate filter context.

1. Add a measure to the **Sales** table, named **Sales All Region**. The measure should evaluate the sum of the **Sales** column while removing any filters applied to the columns of the **Region** table.

    *For your convenience, all DAX definitions in this lab can be copied from the **D:\PL300\Labs\05-create-dax-calculations-in-power-bi-desktop-advanced\Assets\Snippets.txt** file.*

2. Add the **Sales All Region** measure to the matrix visual.

    ![Picture 52](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image16.png)

3. Notice that the **Sales All Region** measure computes the total of all region sales for each region, country (subtotal) and group (subtotal).

    *The new measure is yet to deliver a useful result. When the sales for a group, country, or region is divided by this value it will produce a useful ratio known as “percent of grand total”.*

4. Create a new measure **Sales % All Region**. The measure should divide the **Sales** measure (not modified by filter context) by the **Sales** measure in a modified context, which removes any filters applied to the **Region** table.

5. Format the **Sales % All Region** measure as a percentage with two decimal places.

6. In the matrix visual, review the **Sales % All Region** measure values.

    ![Picture 53](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image17.png)

7. Add another measure to the **Sales** table, named **Sales % Country**. It should achieve a result that represents the sales as a percentage of country. Tip: you should modify the filter context by removing filters on the **Region** column of the **Region** table, not all columns of the **Region** table.

8. Add the **Sales % Country** measure to the matrix visual.

9. Notice that only the United States’ regions produce a value that isn't 100%.
    
	*You may recall that only the United States has multiple regions. All other countries comprise a single region, which explains why they're all 100%.*

    ![Picture 54](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image18.png)


10. To improve the readability of this visual, modify the **Sales % Country** measure. You should use the ISINSCOPE() function to test whether the region column is the level in a hierarchy of levels. When true, the DIVIDE() function is evaluated. When false, a blank value is returned because the region column isn't in scope.*

11. Notice that the **Sales % Country** measure now only returns a value when a region is in scope.

    ![Picture 55](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image19.png)

12. Add another measure to the **Sales** table named **Sales % Group**. It should achieve a result that represents the sales as a percentage of group. Tip: you should modify the filter context by removing filters on the **Region** and **Country** columns of the **Region** table, not all columns of the **Region** table.

13. Add the **Sales % Group** measure to the matrix visual.

14. To improve the readability of this measure in visual, modify the **Sales % Group** measure so that it only returns a value when a region or country is in scope.

15. In Model view, place the three new measures into a display folder named **Ratios**.

    ![Picture 56](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image20.png)

16. Save the Power BI Desktop file.

*The measures added to the **Sales** table have modified filter context to achieve hierarchical navigation. Notice that the pattern to achieve the calculation of a subtotal requires removing some columns from the filter context, and to arrive at a grand total, all columns must be removed.*

## **Exercise 2: Work with Time Intelligence**

In this exercise, you'll create a sales year-to-date (YTD) measure and sales year-over-year (YoY) growth measure.

### **Task 1: Create a YTD measure**

In this task, you'll create a sales YTD measure.

1. In Report view, on **Page 2**, notice the matrix visual that displays various measures with years and months grouped on the rows.

2. Add a measure to the **Sales** table, named **Sales YTD**, and format it to zero decimal places:

    *Tip: the TOTALYTD() function evaluates an expression—in this case the sum of the **Sales** column—over a given date column. The date column must belong to a date table marked as a date table, as was done in the **Create DAX Calculations in Power BI Desktop** lab.*

    *The function can also take a third optional argument representing the last date of a year. The absence of this date means that December 31 is the last date of the year. For Adventure Works, June in the last month of their year, and so “6-30” is used.*

3. Add the **Sales** field and the **Sales YTD** measure to the matrix visual.

4. Notice the accumulation of sales values within the year.

    ![Picture 59](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image21.png)

    *The TOTALYTD() function performs filter manipulation, specifically time filter manipulation. For example, to compute YTD sales for September 2017 (the third month of the fiscal year), all filters on the **Date** table are removed and replaced with a new filter of dates commencing at the beginning of the year (July 1, 2017) and extending through to the last date of the in-context date period (September 30, 2017).*

    *Many Time Intelligence functions are available in DAX to support common time filter manipulations.*

### **Task 2: Create a YoY growth measure**

In this task, you'll create a sales YoY growth measure.

1. Add another measure to the **Sales** table, named **Sales YoY Growth**. It should calculate the sum of the **Sales** column in a modified context that uses the PARALLELPERIOD() function to shift 12 months back from each date in filter context

2. Add the **Sales YoY Growth** measure to the matrix visual.

3. Notice that the new measure returns BLANK for the first 12 months (because there were no sales recorded before fiscal year 2017).

4. Notice that the **Sales YoY Growth** measure value for **2018 Jul** is the **Sales** value for **2017 Jul**.

    ![Picture 61](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image22.png)

    *Now that the “difficult part” of the formula has been tested, you can overwrite the measure with the final formula that computes the growth result.*

5. Modify the **Sales YoY Growth** measure to display it as a percentage with two decimal places. 

6. Verify that the YoY growth for **2018 Jul** is **392.83%**.

    ![Picture 62](Linked_image_Files/06-create-dax-calculations-in-power-bi-desktop-advanced_image23.png)

    *The YoY growth measure identifies almost 400% (or 4x) increase of sales during the same period of the previous year.*

7. In Model view, place the two new measures into a display folder named **Time Intelligence**.

### **Task 3: Finish up**

In this task, you'll complete the lab.

1. To clean up the solution ready for report development, at the bottom-left, right-click the **Page 2** tab, and then select **Delete** page. When prompted to delete the page, select **Delete**.

1. Delete **Page 3** also.

1. On the remaining page, to clear the page, select the table visual, and the press the **Delete** key.

1. Save the Power BI Desktop file.

1. If you intend to start the next lab, leave Power BI Desktop open.

*You’ll create a report based on the data model in the **Design a Report in Power BI Desktop** lab.*
