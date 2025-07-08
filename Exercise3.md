
## Exercise 3: Building an AI-Powered Chatbot with Microsoft Fabric and Azure AI Studio

Contoso encountered a major issue with customer churn, especially among millennials. The executives at Contoso struggled to understand this customer segment and figure out how to earn their loyalty. Despite having extensive data from customer interactions, surveys, and market research, Contoso found it difficult to pinpoint the root cause of the churn and determine effective solutions. 

The main problem was the lack of integration in their existing systems. This prevented Contoso's executives from utilizing their data for root cause analysis and strategic insights, which in turn, hampered their ability to improve marketing strategies, product offerings, and customer experiences. 

To solve the data silos issue, Contoso implemented an advanced AI solution using Azure OpenAI, Azure AI Search, and Microsoft Fabric. Once the team discovered that millennials were leaving because they couldn't find products, they developed an Azure OpenAI-powered shopping assistant to help with product search and recommendations. 

In this exercise, we will learn how they achieved this! 

### Task 3.1: Integrate Fabric data with Azure AI Studio using Azure AI Search

Let's step into the shoes of Eva, the Data Engineer, as she launches Azure AI Studio and leverages data stored in Microsoft OneLake as knowledge base.

1. Navigate back to the Microsoft Fabric tab on your browser (https://app.fabric.microsoft.com).
 
2. Click on **Workspaces** and select **<inject key= "WorkspaceName" enableCopy="false"/>**.
 
   ![task-1.3.02.png](media/l14.png)

3. Click **Manage access**.

   ![th07.png](media/th07.png)

4. Click **+ Add people or groups**.

   ![th08.png](media/th08.png)

5. Type **<inject key= "Search_service" enableCopy="true"/>**, select **Contributor** from the permission dropdown, and then click **Add**.

   ![th09.png](media/th09.png)

6. Click on **<inject key= "WorkspaceName" enableCopy="false"/>** from the left-hand side menu, then select **Lakehouse**.

   ![th03.png](media/th03.png)

7. Copy the **browser URL** as shown in the screenshot, and paste it into your notepad for later use.

   ![th04.png](media/th04.png)

8. Open the following Search service in the VM browser new window: **<inject key= "searchservice" enableCopy="true"/>** 

9. In the Search service, click on the **Import data** option to begin setting up the data source.

   ![th05.png](media/th05.png)

10. In the **Existing data source** dropdown, select the **OneLake files (preview)** option.

      ![th06.png](media/th06.png)

11. In the Connect to your data section, configure the following fields:

- **Data Source**: **OneLake files (preview)**.

- **Data source name**: **onelake**.

- **Data to extract**: **All metadata**.

- **Parsing mode**: **JSON array**.

- **Connect by**: **Lakehouse URL**.

- **Lakehouse URL**: Paste the Lakehouse URL you copied in the **Step 7**.

- **Lakehouse folder/shortcut**: **products**.

- **Managed identity authentication**: **System-assigned**.

12. Click on **Next: Add cognitive skills (Optional)** to proceed.

      ![th20.png](media/th20.png)

13. Click on **Skip to: Customize target index** to proceed.

      ![th10.png](media/th10.png)

14. Provide in the **Index name** field as **onelake-index**.

15. Provide in the **Key** field as **id**.

      ![th11.png](media/th11.png)

16. Ensure all fields have **Retrievable**, **Filterable**, **Sortable**, **Facetable**, and **Searchable** options checked as shown in the screenshot.


17. Once the field settings are configured, click on **Next: Create an indexer** to proceed.

      ![st05.png](media/createindexer.png)

18. Enter the name of the indexer as **onelake-indexer** and click on the **Submit** button.

      ![th13.png](media/th13.png)


---

### Task 3.2: Establish Azure OpenAI, Azure AI Content Safety, and AI Search Connections in Azure AI Studio

Contoso integrated all of their data sources using Microsoft Fabric, including customer feedback, sales records, social media interactions, and encompassing internal company policy documents such as SOPs and research articles on customer behavior into Azure AI Search. 
This created a unified, searchable knowledge base. 

Let's step into Data Engineer, Eva's shoes to see how.


1. In Azure portal Search for the **prj-build-<inject key= "DeploymentID" enableCopy="false"/>**, and select **prj-build-<inject key= "DeploymentID" enableCopy="false"/>** service from the results.

   ![st04.png](media/prj.png)
    
3. Click on the **Studio web URL**.

   ![st04.png](media/std.png)

   >**Note:** Close any pop-up that appears on the screen throught the lab.

   ![st04.png](media/st04.png)

   >**Note:** Click on the **Expand** icon, if the left navigation is hidden.

   ![prjexpand.png](media/prjexpand.png)

2. Scroll down and click on the **Management center** from the bottom of the navigation menu.

   ![th14.png](media/th14.png)

3. Click **Connected resources** and select **New connection**.

   ![th15.png](media/th15.png)

4. Select **Azure OpenAI**.

   ![ai_4.png](media/ai_4.png)

5. You will find an Azure OpenAI resource with gpt-4o and text-embedding-ada-002 model deployment. Create a connection by clicking on the **Add connection** button.

   ![st07.png](media/E31.png)

6. Once the **OpenAI services are connected**, click on **Back to select an asset type**.

   ![st08.png](media/deopenai2.png)

7. Click on **Azure AI Search**.

   ![st008.png](media/st008.png)

8. Click on **Add connection**.

   ![st009.png](media/st009.png)

9. Once the **AI Search is connected**, click on the **Close** button.

   ![st09.png](media/st09.png)

   > **Note:** If you're unable to see the Close option, try adjusting your screen resolution to 80% or 90%.

   ![st09.png](media/resolution.png)

10. Notice that **Azure Open AI** and **Azure AI Search** connections are established successfully.

      ![st10.png](media/st10.png)

---

### Task 3.3: Setup and use Prompt Flow in Azure AI Studio

Prompt flow in Azure AI Studio offers a comprehensive, streamlined environment for creating AI applications. It provides a visual interface for orchestrating flows, and enables iterative prompt engineering. Azure AI Studio includes built-in evaluation tools, seamless deployment options, and integration with Azure's ecosystem. It also offers enterprise-level security and scalability, making it ideal for developing, testing, and deploying sophisticated AI solutions efficiently. Let's explore how Contoso deployed and tested a Prompt flow.

1. In the left navigation pane, click on **Go to Project** button.

   ![st06.png](media/st06.png)

2. Click on **Prompt flow** from the left navigation pane and then click on the **+ Create** button.

   ![st11.png](media/st11.png)

3. Scroll down and click on the **Upload** button in the Upload from local section.

   ![31.png](media/31.png)

4. Click on the **Zip file** radio button and then click on **Browse**.

   ![32.1.png](media/32.1.png)

5. Copy the path **C:\LabFiles\artifacts\artifacts\aistudio**, paste it in the **File name** textbox and then click on the **Open** button.

   ![32.1.1.png](media/32.1.1.png)

6. Click on **shopping-assistant-prompt-flow** and then click on the **Open** button.

   ![promptziploc.png](media/promptziploc.png)

7. In the Select flow type dropdown, select **Chat flow** and then click on the **Upload** button.

   ![st12.png](media/st12.png)

   >**Note:** If clicking on the Upload button doesn't redirect you to the Prompt Flow screen, click the Upload button again. If it still doesn't work, refresh the page and try uploading again.

8. Once the prompt flow is uploaded, you'll see a **graph** view with connected nodes representing each step in the flow.

   ![st12.png](media/newuu.png)

9. Open a new tab, click on browser address bar, and copy paste the following web app link ``https://app-shopping-copilot-d1hz4ew.azurewebsites.net/`` and then press Enter.

    ```
    https://app-shopping-copilot-d1hz4ew.azurewebsites.net/
    ```
      ![Contosoterms.1.png](media/Contosoterms.1.png)

10. Click on the **terms and conditions checkbox** and then click on the **Login** button.

      ![Contosoterms.png](media/Contosoterms.png)
 
11. Click on the **Copilot icon** at the bottom right of the page.
 
      ![Copiloticonwebapp.png](media/Copiloticonwebapp.png)

12. Click on any of the **pre-populated questions**.
 
      ![question1webapp.png](media/question1webapp.png)
 
13. Observe the **response**.
  
      ![Answer1webapp.png](media/Answer1webapp.png)
 
With their new Shopping Copilot, Contoso was able to provide their customers with an online shopping experience that has an in-store feel. This simulates a personalized shopping experience that helps increase customers' engagement with enhanced data insights.
