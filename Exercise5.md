
### Exercise 5: Real-time Intelligence experience: Explore Streaming data using Copilot for KQL DB

Imagine, it is 6 am on the day of Contoso's big Thanksgiving sale. Customers are flocking to their stores in large numbers. We are about to witness the very culmination of Contoso's phenomenal transformation with Microsoft Fabric and Azure Databricks. Specifically, we will see how near real-time data is used to make decisions for the next moment in Contoso's stores to ensure optimal temperatures are maintained for their customers while they shop at the big sale!

### Task 5.1: Ingest real-time data into Eventhouse using Eventstream
In the exercise, we'll explore how Data Engineer, Eva, ingested real-time data from the event hub into the KQL Database to monitor in-store temperatures in real time. 

1.  Click on the **<inject key= "WorkspaceName" enableCopy="false"/>** workspace from the left navigation pane and select **New item**.

    ![st26.png](media/st26.png)

    >**Note:** If you see a pop-up like the one below, click on the **Don't save** button.

    ![donotsave.png](media/donotsave.png) 

2. In the new item window, search for the **Eventhouse** and click **Eventhouse**.

    ![st27.png](media/st27.png)

3. Enter the name **Contoso-Eventhouse**.

    ```
    Contoso-Eventhouse
    ```

4. Click on the **Create** button and wait for the database to be created.

    ![eventhouse2.png](media/eventhouse2.png)

    >**Note:** If you see a **pop-up** like the one in the screenshot below, ignore it and proceed with the next step.

    ![eventhouse16.png](media/eventhouse16.png)

5. Click on the **<inject key= "WorkspaceName" enableCopy="false"/>**  workspace from the left navigation pane and select **New item**.

    ![st26.png](media/st26.png)

6. In the new item window, search for the **Eventstream** and click **Eventstream**.

    ![st28.png](media/st28.png)

7. Enter the name as **RealtimeDataTo-KQL-DB** and click on the **Create** button.

    ```
    RealtimeDataTo-KQL-DB
    ```

    ![Eventst-name1.png](media/Eventst-name1.png)

8. Click on the **Connect data sources** button.

    ![](media/eventhouse12u.png)

9. Click on the **Connect** button for **Azure Event Hubs**.

    ![](media/eventhouseconnect.png)

10. Under the Connection field, click on **New connection**.

    ![eventhouse13.png](media/eventhouse13.png)

11. Enter the value for the **Event Hub namespace** as **<inject key= "namespaces_adx_thermostat" enableCopy="true"/>**  and enter the **Event Hub** value as **thermostat**.

    ```
    thermostat
    ```

    ![task-5.2.5-2.png](media/task-5.2.5-2.png)

12. Scroll down to the **Authentication kind** dropdown and select **Shared Access Key**. In the **Shared Access Key Name** field enter **thermostat** , in the **Shared Access Key** field enter **<inject key= "eventHubPolicyPrimaryKey" enableCopy="true"/>** and then click on the **Connect** button.

    ![eventhouse14.png](media/eventhouse14.png)

    >**Note:** Close any pop-up which appears on screen.

    ![pop-up3.png](media/pop-up3.png)

13. Select Data format as **JSON** and click on **Next** button.

    ![eventhouse15.png](media/eventhouse15.png)

    >**Note:** Wait for the connection to be established.

14. Click on the **Add** button.

    ![task-5.2.1new8.png](media/task-5.2.1new8.png)

15. In the Eventstream canvas, click on the **Add destination** dropdown and select **Eventhouse**.

    ![sel-kql-db.png](media/sel-kql-db.png)

16. Select the **Event processing before ingestion** radio button, enter **RealTimeData** as the Destination name.

17. In the **Workspace** field select **<inject key= "WorkspaceName" enableCopy="false"/>**. 

18. In the **Eventhouse** dropdown select **Contoso-Eventhouse**.

18. In the **KQL Database** dropdown select **Contoso-Eventhouse**.

19. In the **KQL Destination table** field, click on **Create new** button.

    ![eventhouse5.png](media/eventhouse5.png)

20. Enter the table name as **thermostat** and then click on the **Done** button.

    ![eventhouse6.png](media/eventhouse6.png)

21. Enter the Input data format as **Json**.

    >**Note:** Zoom-out on your screen if the **Input data format field** is not visible.

    ![eventhouse7.png](media/eventhouse7.png)

22. Drag Arrow from 'RealtimeDataTo-KQL' and connect it to 'RealTimeData'.

    ![eventhouse8.png](media/eventhouse8.png)

23. Click on the **Publish** button.

    ![task-5.2.15.png](media/task-5.2.15.png)

    >**Note:** Wait for the data ingestion from EventHub to KQL DB, In the RealTimeData canvas, the status will appear as **Active**, confirming that the streaming has started successfully.

24. Once you see that the streaming has started, click on **Refresh** and wait for the data to preview.

    ![eventhouse17.png](media/eventhouse17.png)

Real-time data from the event hub has been ingested successfully into the KQL Database. Next, as customers walk in aisles and the temperatures fluctuate, let us see how KQL queries proactively identify anomalies and help maintain an optimal shopping experience!

---

### Task 5.2: Analyze and discover patterns, identify anomalies and outliers using Copilot

Kusto Query Language (KQL) is a powerful tool. In this scenario KQL is used to explore Contoso's data, discover patterns, identify anomalies and outliers, create statistical modeling, and more.

We use KQL to query the thermostat data that's streaming in near real-time from the devices installed in Contoso's stores.

1. Click on the **<inject key= "WorkspaceName" enableCopy="false"/>** workspace from the left navigation pane and select **New item**.

    ![st26.png](media/st26.png)

2. In the new item window, search for the **KQL Queryset** and click **KQL Queryset**.

    ![st29.png](media/st29.png)

4. In the KQL Queryset name field, +++Query Thermostat Data in Near Real-time using KQL Script+++ and click on the **Create** button.

    ![task-5.3.3.png](media/task-5.3.3.png)

    >**Note:** Close any pop-up which appears on screen.

    ![st30.png](media/st30.png)

5. **Wait** for the query set creation and a new screen will display. In this screen, click on **Contoso-Eventhouse**, verify the workspace name and then click on the **Connect** button.

    ![eventhouse10.png](media/eventhouse10.png)

6. Place your cursor inside the **query** field, select all using **Ctrl + A** and **delete** the pre-written query.

    ![task-5.3.5.png](media/task-5.3.5.png)

7. Click on the **Copilot** button.

    ![st31.png](media/st31.png)

8. **Paste** the query provided below in the Copilot query section.

    ```
    Create a query to summarize average temperature every 1 min in line chart
    ```

9. Click on the **Send** icon.

    >**Note:** Note: If you receive a response from Copilot such as "I am not sure" please ask the question again.

    >**Note:** The responses from Copilot may not match the ones in the screenshot but will provide a similar response. 

10. Click on the **Insert** button.

    ![kqlqueyset1 - Copy.png](media/kqlqueyset1 - Copy.png)

11. Place your cursor in the **script field**, click on the **Run** button and you get the desired result.

    ![task-5.3.8 - Copy.png](media/task-5.3.8 - Copy.png)


Imagine one of the aisles had a sudden rise in temperature due to an anomaly. Customers start leaving that aisle and the wait times in the checkout lines start to increase but thanks to the KQL Queries, those anomalies would be tracked, and immediately notifications would be generated to bring the aisle temperature back to optimal levels! 
