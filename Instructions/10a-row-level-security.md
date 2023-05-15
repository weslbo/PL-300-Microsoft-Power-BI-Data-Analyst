---
lab:
    title: 'Enforce Row-Level Security (challenge version)'
    module: '12 - Row-Level Security'
---


# **Enforce Row-Level Security** (challenge version)

**The estimated time to complete the lab is 45 minutes**

In this lab, you'll enforce row-level security to ensure that a salesperson can only analyze sales data for their assigned region(s).

In this lab you learn how to:

- Enforce row-level security

### **Lab story**

This lab is one of many in a series of labs that was designed as a complete story from data preparation to publication as reports and dashboards. You can complete the labs in any order. However, if you intend to work through multiple labs, we suggest you do them in the following order:

1. Prepare Data in Power BI Desktop
1. Load Data in Power BI Desktop
1. Design a Data Model in Power BI
1. Create DAX Calculations in Power BI Desktop
1. Create Advanced DAX Calculations in Power BI Desktop
1. Design a Report in Power BI Desktop
1. Enhance a Report in Power BI Desktop
1. Perform Data Analysis in Power BI Desktop
1. Create a Power BI Dashboard
1. **Enforce Row-Level Security**

## **Exercise 1: Enforce row-level security**

In this exercise, you'll enforce row-level security to ensure a salesperson can only ever see sales made in their assigned region(s).

### **Task 1: Get started**

In this task, you'll set up the environment for the lab.

*Important: If you completed the previous lab in the same VM, **skip** to the next task.*

1. Open the following Power BI Desktop file: **D:\PL300\Labs\10-row-level-security\Starter\Sales Analysis.pbix**

2. Save the report to the **D:\PL300\MySolution** folder.

### **Task 2: Enforce row-level security**

In this task, you'll enforce row-level security to ensure a salesperson can only see sales made in their assigned region(s).

1. Switch to Data view.

1. Select the **Salesperson (Performance)** table.

1. Review the data, noticing that Michael Blythe (EmployeeKey 281) has a UPN value of: **michael-blythe@adventureworks.com**
    
	*You may recall that Michael Blythe is assigned to three sales regions: US Northeast, US Central, and US Southeast.*

2. Create a role named **Salespeople**.

3. Assign a filter, for the **Salesperson (Performance)** table, based on the **[UPN]** field.

4. In the **Table Filter DAX Expression** box, modify the expression by replacing **“Value”** with **USERPRINCIPALNAME()**, and then **Save**.
    
	*USERPRINCIPALNAME() is a Data Analysis Expressions (DAX) function that returns the name of the authenticated user. It means that the **Salesperson (Performance)** table will filter by the User Principal Name (UPN) of the user querying the model.*

   ![Picture 11](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image25.png)

5. Test the security role, by selecting **View As**.

   ![Picture 5708](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image27.png)

6. In the **View as Roles** window, check the **Other User** item, and then in the corresponding box, enter: **michael-blythe@adventureworks.com**

7. Check the **Salespeople** role, and then **OK**.
    
	*This configuration results in using the **Salespeople** role and impersonating the user with your Michael Blythe’s name.*

   ![Picture 5709](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image28.png)

8. Notice the yellow banner above the report page, describing the test security context.

   ![Picture 13](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image30.png)

9.  In the table visual, notice that only the salesperson **Michael Blythe** is listed.

   ![Picture 5713](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image31.png)

10. To stop testing, at the right side of the yellow banner, select **Stop Viewing**.

   ![Picture 5712](Linked_image_Files/04-configure-data-model-in-power-bi-desktop-advanced_image32.png)

11. Delete the **Salespeople** role.
    
12. Select **Save**, then save the Power BI Desktop file to end the lab.

*Note: When the Power BI Desktop file is published to the Power BI service, you’ll need to complete a post-publication task to map security principals to the **Salespeople** role. You won’t do that in this lab.*
