### Exercise 2: Azure Databricks integration with Fabric: DLT Pipelines, Unity Catalog (Data governance), Mirrored Azure Databricks Catalog

This exercise shows how Microsoft Fabric with Databricks enabled Contoso to solve their integration challenges. The acquired company, Litware Inc., was already using Databricks heavily and they stored their churn and sales data in ADLS Gen2. We’ll see how Unity Catalog benefited Contoso’s data architects so they could quickly get up to speed on all Litware Inc.’s data.

### Task 2.1: Create Delta Live Table pipeline for Data Transformation

1. Please use the following link to navigate to the Azure Databricks workspace:**<inject key= "NewdatabricksWorkspaceUrl" enableCopy="True"/>** and click on the **Sign in with Microsoft Entra ID** that appears.

```
<inject key= "NewdatabricksWorkspaceUrl" enableCopy="True"/>
```

![databrickssign.png](media/labMedia/databrickssign.png)

2. Scroll down in the left navigation pane and click on **Pipelines**.

![task-2.2.2new.png](media/labMedia/l9.png)

3. Select the **Create pipeline** and then click on the **ETL Pipeline** button.

![task-2.2.3.1new.png](media/labMedia/l10.png)

4. Enter the name of the pipeline as **DLT_Pipeline** , scroll down to **Paths** given in the **Source code** section and click on the **file icon** to browse the notebook.

```BASH
DLT_Pipeline
```

![task-2.2.3new.png](media/labMedia/task-2.2.3new.png)

5. Click on **Shared**, click on **Analytics with ADB**, click on the **01 DLT Notebook** and then click on the **Select** button.

![task-2.2.4new.png](media/labMedia/f13.png)

6. Type **dbo** in **Default schema** field and click on the **Create** button.

![f45.png](media/labMedia/f45.png)

7. Click on the **Start** button.

![task-2.2.5new.png](media/labMedia/f14.png)

>**Note**: The pipeline will take 5-7 minutes to complete. In the meantime, you can move on to the next section and return to this one afterward.

8. Once the execution is completed, we will see a result similar to the one in the following screenshot.

![task-2.2.7.png](media/labMedia/task-2.2.7.png)

This beautiful lineage view showing the Medallion Architecture is a data design pattern commonly used in Databricks to organize and optimize data processing workflows in a lakehouse architecture. It structures data into three logical layers—Bronze, Silver, and Gold—ensuring data quality, accessibility, and scalability for analytics and machine learning.

---

### Task 2.2: Explore the data in the Azure Databricks environment with Unity Catalog (unified governance solution for data and AI).

We saw how Contoso utilized DLT pipelines to create a Medallion architecture on their data. Now let’s look at how data governance was managed on this curated data across the organization and made easy with Unity Catalog.

With the acquisition of Litware Inc., Contoso had a lot of data integration and interoperability challenges. They wanted to make sure that the transition was smooth, and their data engineers and data scientists could easily assimilate the data processed by Databricks. Thankfully, they were able to leverage Gen AI features right within Azure Databricks to understand and derive insights from this data.

>**Note**: Due to time constraints, the following steps will be completed via an online Click-by-Click exercise.

>Please follow the green beacons for this exercise.
- This exercise will be performed outside the VM browser.
- Please return back to the VM browser once you see the **End of Task 2.2** screen.
- Once you press the **Agree** button, press the **A** key on your keyboard if you do not see the annotations.
	
1. Click on the [**hyperlink**](https://regale.cloud/Microsoft/viewer/3066/task-22-explore-the-data-in-azure-databricks-environment-with-unity-catalog/index.html#/0/1)

2. Continue with next excercise.


### Task 2.3: Create a Mirrored Azure Databricks Catalog in Microsoft Fabric and analyze data using T-SQL

Mirroring the Azure Databricks Catalog structure in Microsoft Fabric allows seamless access to the underlying catalog data through shortcuts. This means that any changes made to the data are instantly reflected in Microsoft Fabric, without the need for data movement or replication. Let’s step into Data Engineer, Eva’s shoes to create a Mirrored Azure Databricks Catalog and analyze the data using T-SQL. 

1. Navigate back to the Microsoft Fabric tab on your browser (https://app.fabric.microsoft.com).

2. Click on the **<inject key= "WorkspaceName" enableCopy="true"/>** and select **New item** from menu bar.

![Task-2.3_1.png](media/labMedia/Task-2.3_1.png)

3. In the **New item** window, scroll down and click on **Mirrored Azure Databricks catalog (preview)**.

![Task-2.3_2.png](media/labMedia/Task-2.3_2.png)

4. When the **New source** window pops up, click on the **New connection** radio button.

![Task-2.3_3.png](media/labMedia/l11.png)

5. In the URL field enter **<inject key= "databricksurl" enableCopy="true"/>**

6. Now, select **Service principal** from 'Authentication kind' dropdown box, and enter the following details.

- Tenant ID: **<inject key= "catalogTenantID" enableCopy="true"/>**
- Service principal client ID: **<inject key= "ClientID" enableCopy="true"/>**
- Service principal Key: **<inject key= "Secret" enableCopy="true"/>**

7. click on the **Connect** button.

![Task-2.3_7.png](media/labMedia/l12.png)

8. Click on the **Next** button.

![Task-2.3_7.1.png](media/labMedia/l13.png)

9. In the **Choose data** screen, select the Catalog name as **litware_unity_catalog** from the dropdown box, and ensure **default** and **rag** schema is selected.

10. Click on **Next** button.

![Task-2.3_8.png](media/labMedia/Task-2.3_8u.png)

11. In the **Name** field enter **litware_unity_catalog1** for your mirrored Databricks Catalog and click on the **Create** button.

```BASH
litware_unity_catalog1
```

![Task-2.3_9.png](media/labMedia/Task-2.3_9.png)

12. Click on the **Monitor catalog** button to track the mirroring **Status** and then close it.

![Task-2.3_10.1.png](media/labMedia/Task-2.3_10.1.png)

13. Click on the **View SQL endpoint** button. You can also select the tables to preview data.

![Task-2.3_10.png](media/labMedia/Task-2.3_10.png)

14. Click on the **Refresh button**, then expand **rag**, and further expand **Tables** to view replicated tables.

![Task-2.3_10.png](media/labMedia/f79.png)

>**Note:** If you are unable to view replicated tables, refresh the page by pressing **Ctrl + Shift + R**.
 
15. Click on **New SQL Query**, then copy and paste the following **SQL query** in query editor and click on **Run** button.
 
![Task-2.3_10.png](media/labMedia/f80.png)
 
```BASH
SELECT 
    [Campaign_Name],
    AVG([ROI]) AS Avg_ROI,
    SUM([Profit]) AS Total_Profit,
    SUM([Cost]) AS Total_Cost,
    AVG([Cost]) AS Avg_Cost
FROM 
    [litware_unity_catalog].[rag].[campaigndata]
GROUP BY 
    [Campaign_Name]
ORDER BY 
    Avg_ROI DESC; 
```

Fabric Mirrored Databricks has been successfully created and configured. It's now ready for seamless integration and data collaboration across platforms.