---
lab:
    title: 'Design a Report in Power BI Desktop (challenge version)'
    module: '7 - Create Reports'
---


# Design a Report in Power BI Desktop (challenge version)

**The estimated time to complete the lab is 45 minutes.**

In this lab, you'll create a three-page report. You'll then publish it to Power BI, whereupon you'll open and interact with the report.

In this lab you learn how to:

- Design a report
- Configure visual fields and format properties

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. Load Data in Power BI Desktop
1. Design a Data Model in Power BI
1. Create DAX Calculations in Power BI Desktop
1. Create Advanced DAX Calculations in Power BI Desktop
1. **Design a Report in Power BI Desktop**
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI
1. Create a Power BI Dashboard
1. Enforce Row-Level Security

## **Exercise 1: Create a Report**

In this exercise, you'll create a three-page report named **Sales Report**.

### **Task 1: Get started – Open report**

In this task, you'll set up the environment for the lab.

*Important: If you're continuing on from the previous lab (and you completed that lab successfully), don't complete this task; instead, continue from the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\06-design-report-in-power-bi-desktop\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Design page 1**

In this task, you'll design the first report page. When you’ve completed the design, the page will look like the following:

![Image of page 1, comprising a logo, two slicers, and three visuals.](Linked_image_Files/06-finished-report-page.png)

1. Rename **Page 1** to **Overview**.

2. Add an image **D:\PL300\Resources\AdventureWorksLogo.jpg** to the top-left corner and resize it.

     ![Picture 12](Linked_image_Files/07-design-report-in-power-bi-desktop_image17.png)

3. Add a slicer, based on the **Date \| Year** field (not the **Year** level of the hierarchy) into the slicer **Field** in Visualizations pane.
    
	*The labs use a shorthand notation to reference a field. It will look like this: **Date \| Year**. In this example, **Date** is the table name and **Year** is the field name.*

4. Convert the slicer from a list to a dropdown.

5. Resize and position the slicer so it sits beneath the image and is the same width as the image.

     ![Picture 19](Linked_image_Files/07-design-report-in-power-bi-desktop_image20.png)

6.  Filter the report with the slicer by year **FY2020**.

7.  Create a second slicer, based on the **Region \| Region** field (not the **Region** level of the hierarch).

8.  Leave the slicer as a list, and then resize and position the slicer beneath the **Year** slicer.

     ![Picture 21](Linked_image_Files/07-design-report-in-power-bi-desktop_image22.png)

9.  Add a **Line and Stacked Column Chart** to the page

10. Resize and position the visual so it sits to the right of the logo, and so it fills the width of the report page.

     ![Picture 26](Linked_image_Files/07-design-report-in-power-bi-desktop_image27.png)

11. Drag and drop the following fields into the visual:

     - Date \| Month
     - Sales \| Sales

12. Add the **Sales \| Profit Margin** field into the **Line y-axis** well/area.

13. Notice that the visual has 11 months only. You'll need to configure the visual to show all months (including **2020 June**). *Tip: Show Items With No Data*
    
	*The last month of the year, 2020 June, doesn't have any sales (yet). By default, the visual has eliminated months with BLANK sales. 

14. Add a **Stacked Column Chart** to the page.

15. Resize and position the visual so it sits beneath the column/line chart, and so it fills half the width of the chart above.

     ![Picture 33](Linked_image_Files/07-design-report-in-power-bi-desktop_image32.png)

16. Add the following fields to the visual wells/areas:

     - X-axis: **Region \| Country**
     - Y-axis: **Sales \| Sales**
     - Legend: **Product \| Category**

17. Add a **Stacked Bar Chart** to the page.

18. Resize and position the visual so it fills the remaining report page space.

     ![Picture 35](Linked_image_Files/07-design-report-in-power-bi-desktop_image34.png)

19. Add the following fields to the visual wells/areas:

     - Y-axis: **Product \| Category**
     - X-axis: **Sales \| Quantity**


20. Set the **Default Color** of the **Bars** to a suitable color (to complement the column/line chart).

21. Make sure that **Data Labels** will be displayed.

22. Save the Power BI Desktop file.

*The design of the first page is now complete.*

### **Task 3: Design page 2**

In this task, you'll design the second report page. When you’ve completed the design, the page will look like the following:

 ![Image of page 2, comprising a slicer and matrix.](Linked_image_Files/07-design-report-in-power-bi-desktop_image37.png)

*Important: When detailed instructions have already been provided in the labs, the lab steps will provide more concise instructions. If you need the detailed instructions, you can refer back to other tasks in this lab.*

1. Create a new page, named **Profit**.

2. Add a slicer based on the **Region \| Region** field.

3. Make sure that the “Select All” option can be selected.

4. Resize and position the slicer so it sits at the left side of the report page, and so it is about half the page height.

     ![Picture 44](Linked_image_Files/07-design-report-in-power-bi-desktop_image40.png)

5. Add a matrix visual, and resize and position it so it fills the remaining space of the report page

     ![Picture 45](Linked_image_Files/07-design-report-in-power-bi-desktop_image41.png)

6. Add the **Date \| Fiscal** hierarchy to the matrix **Rows** well/area.

     ![Picture 46](Linked_image_Files/07-design-report-in-power-bi-desktop_image42.png)

7. Add the following five **Sales** table fields to the **Values** well/area:

     - Orders (from the **Counts** folder)
     - Sales
     - Cost
     - Profit
     - Profit Margin

     ![Picture 55](Linked_image_Files/07-design-report-in-power-bi-desktop_image43.png)

8. Add the following fields to the **Filter on This Page** well/area: 

     - **Product \| Category**
     - **Product \| Subcategory**
     - **Product \| Product**
     - **Product \| Color**

	*Fields added to the **Filters** pane can achieve the same result as a slicer. One difference is they don’t take up space on the report page. Another difference is that they can be configured to achieve more sophisticated filtering requirements.*

     ![Picture 60](Linked_image_Files/07-design-report-in-power-bi-desktop_image46.png)

9.  Save the Power BI Desktop file.

 *The design of the second page is now complete.*

### **Task 4: Design page 3**

In this task, you'll design the third—and final—report page. When you’ve completed the design, the page will look like the following:

 ![Image of page 3, comprising a slicer and three visuals.](Linked_image_Files/07-design-report-in-power-bi-desktop_image47.png)

1. Create a new page, and then rename it as **My Performance**.

1. To simulate the performance of row-level security filters, drag the **Salesperson (Performance) \| Salesperson** field to the page level filters in the filter pane.

     ![Image of Salesperson field in filter pane.](Linked_image_Files/07-design-report-in-power-bi-desktop_image999.png)

1. Select **Michael Blythe**. Data on the **My Performance** report page will now be filtered to display data for Michael Blythe only.

1. Add a dropdown slicer based on the **Date \| Year** field, and then resize and position it so it sits at the top-left corner of the page.

     ![Picture 70](Linked_image_Files/07-design-report-in-power-bi-desktop_image49.png)

1. In the slicer, set the page to filter by **FY2019**.

     ![Picture 71](Linked_image_Files/07-design-report-in-power-bi-desktop_image50.png)

1. Add a **Multi-row Card** visual, and then resize and reposition it so it sits to the right of the slicer and fills the remaining width of the page.

     ![Picture 74](Linked_image_Files/07-design-report-in-power-bi-desktop_image52.png)

2. Add the following four fields to the visual:

     - Sales \| Sales
     - Targets \| Target
     - Targets \| Variance
     - Targets \| Variance Margin

3. Format the visual:

     - Increase the **Text Size** for the callout values to **28pt**

     - Set the **Background Color** to a light gray color (such as "White, 20% Darker) to give contrast

         ![Picture 79](Linked_image_Files/07-design-report-in-power-bi-desktop_image53.png)

4. Add a **Clustered Bar Chart** visual, and then resize and position it so it sits beneath the multi-row card visual and fills the remaining height of the page, and half the width of the multi-row card visual.

     ![Picture 78](Linked_image_Files/07-design-report-in-power-bi-desktop_image55.png)

5. Add the following fields to the visual wells/areas:

     - Y-axis: **Date \| Month**
     - X-axis: **Sales \| Sales** and **Targets \| Target**

6. Copy and paste the visual, (**Ctrl+C**, **Ctrl+V**).

7. Position the new visual to the right of the original visual.

     ![Picture 82](Linked_image_Files/07-design-report-in-power-bi-desktop_image57.png)

8. Modify the visualization type to a **Clustered Column Chart**.

 *It’s now possible to see the same data expressed by two different visualization types. This isn’t a good use of the page layout, however, you’ll improve it in the **Enhance a Report in Power BI Desktop** lab by superimposing the visuals. By adding buttons to the page, you’ll allow the report user to determine which of the two visuals is visible.*

 *The design of the third—and final—page is now complete.*

## **Exercise 2: Explore the Report**

In this exercise, you'll publish the report to the Power BI service and explore the read-only consumer report.

### **Task 1: Publish the report**

In this task, you'll publish the report to the Power BI service.

1. Save the Power BI Desktop file.

2. **Publish** the report to the Power BI service **My Workspace**.
    
	*If you're not signed into Power BI Desktop already, you'll need to sign-in to publish.*
    
	*We won't go into detail about the different items within the Power BI service in this lab.*

3. When the publication has succeeded, select **Got It**.

### **Task 2: Explore the report**

In this task, you'll explore the report that was published to Power BI.

1. Open a Microsoft Edge browser, then sign-in at **https://app.powerbi.com**.

1. In the Microsoft Edge browser window, in the Power BI service, in the **Navigation** pane (located at the left, and it could be collapsed), expand **My Workspace**.

    ![Picture 93](Linked_image_Files/06-my-workspace-new.png)

1. Review the contents of the workspace. Notice the navigation options of All, Content, and Datasets + dataflows.
    1. *There are four types of items that can exist in a workspace, and we'll talk about **reports** and **datasets**.*
    1. *You may need to refresh your Microsoft Edge browser if the dataset is not visible.*
    1. *When you published the Power BI Desktop file, the data model was published as a dataset.*

1. To explore the report, select the **Sales Analysis** report.

1. At the left, in the **Pages** pane, select the **Overview** page.

1. In the **Regions** slicer, while pressing the **Ctrl** key, select multiple regions.

1. In the column/line chart, select any month column to cross filter the page.

1. While pressing the **Ctrl** key, select another month.

     *Note: By default, cross filtering filters all other visuals on the page.*

1. Notice that the bar chart is filtered and highlighted, with the bold portion of the bars representing the filtered months.

1. Hover the cursor over the bar chart visual, and then at the top-right, hover the cursor over the filter icon. 
    
	*The filter icon allows you to understand all filters that are applied to the visual, including slicers and cross filters from other visual.*

1. Hover the cursor over a bar, and then notice the tooltip information.

1. To undo the cross filter, in the column/line chart, select an empty area of the visual.

1. Hover the cursor over the stacked column chart visual, and then at the top-right, select the **Focus mode** icon.
    
	*Focus mode zooms the visual to full page size.*

     ![Picture 96](Linked_image_Files/07-published-report-visual-filter.png)

1. Hover the cursor over different segments of the bar charts to reveal tooltips.

1. To return to the report page, at the top-left, select **Back to Report**.

     ![Picture 86](Linked_image_Files/07-design-report-in-power-bi-desktop_image66.png)

1. Hover the cursor over one of the visuals again, then at the top-right, select the ellipsis (…), and then notice the menu options. Try out each of the options, except **Chat in Teams**.

     ![Picture 97](Linked_image_Files/07-design-report-in-power-bi-desktop_image67.png)

1. At the left, in the **Pages** pane, select the **Profit** page.

     ![Picture 84](Linked_image_Files/07-design-report-in-power-bi-desktop_image68.png)

1. Notice that the **Region** slicer has a different selection to the **Region** slicer on the **Overview** page.
    
	*The slicers aren't synchronized. You’ll modify the report design to ensure they sync between pages in the **Enhance a Report in Power BI Desktop** lab.*

1. In the **Filters** pane (located at the right), expand a filter card, and apply some filters.
    
	*The **Filters** pane allows you to define more filters than could possibly fit on a page as slicers.*

1. In the matrix visual, use the plus (+) button to drill into the **Fiscal** hierarchy.

1. Select the **My Performance** page.

     ![Picture 89](Linked_image_Files/07-design-report-in-power-bi-desktop_image69.png)

1. At the top-right on the menu bar, select **View**, and then select **Full Screen**.

     ![Picture 98](Linked_image_Files/07-design-report-in-power-bi-desktop_image70.png)

1. Interact with the page by modifying the slicer, and cross filtering the page.

1. At the bottom of the window, notice the commands to change page, navigate backwards or forwards between pages, or to exit full screen mode.

1. Select the right icon to exit full screen mode.

     ![Picture 91](Linked_image_Files/07-design-report-in-power-bi-desktop_image71.png)

### **Task 3: Finish up**

In this task, you'll complete the lab.

To return to "My Workspace", select **My Workspace** in the banner across the window web page.

 *You'll enhance the report design with advanced features in the **Enhance a Report in Power BI Desktop** lab.*
