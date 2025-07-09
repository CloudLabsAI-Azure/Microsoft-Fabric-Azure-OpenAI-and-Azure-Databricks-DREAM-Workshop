
# Modernize you data estate MS Fabric Azure Databricks and AI Foundry


**DISCLAIMER**

This presentation, demonstration, and demonstration model are for informational purposes only and (1) are not subject to SOC 1 and SOC 2 compliance audits, and (2) are not designed, intended or made available as a medical device(s) or as a substitute for professional medical advice, diagnosis, treatment or judgment. Microsoft makes no warranties, express or implied, in this presentation, demonstration, and demonstration model. Nothing in this presentation, demonstration, or demonstration model modifies any of the terms and conditions of Microsoft's written and signed agreements. This is not an offer and applicable terms and the information provided are subject to revision and may be changed at any time by Microsoft.

This presentation, demonstration, and demonstration model do not give you or your organization any license to any patents, trademarks, copyrights, or other intellectual property covering the subject matter in this presentation, demonstration, and demonstration model.

The information contained in this presentation, demonstration and demonstration model represents the current view of Microsoft on the issues discussed as of the date of presentation and/or demonstration, for the duration of your access to the demonstration model. Because Microsoft must respond to changing market conditions, it should not be interpreted to be a commitment on the part of Microsoft, and Microsoft cannot guarantee the accuracy of any information presented after the date of presentation and/or demonstration and for the duration of your access to the demonstration model.

No Microsoft technology, nor any of its component technologies, including the demonstration model, is intended or made available as a substitute for the professional advice, opinion, or judgment of (1) a certified financial services professional, or (2) a certified medical professional. Partners or customers are responsible for ensuring the regulatory compliance of any solution they build using Microsoft technologies.

**Copyright**

© 2024 Microsoft Corporation. All rights reserved. 

By using this demo/lab, you agree to the following terms:

The technology/functionality described in this demo/lab is provided by Microsoft Corporation for purposes of obtaining your feedback and to provide you with a learning experience. You may only use the demo/lab to evaluate such technology features and functionality and provide feedback to Microsoft. You may not use it for any other purpose. You may not modify, copy, distribute, transmit, display, perform, reproduce, publish, license, create derivative works from, transfer, or sell this demo/lab or any portion thereof.

COPYING OR REPRODUCTION OF THE DEMO/LAB (OR ANY PORTION OF IT) TO ANY OTHER SERVER OR LOCATION FOR FURTHER REPRODUCTION OR REDISTRIBUTION IS EXPRESSLY PROHIBITED.

THIS DEMO/LAB PROVIDES CERTAIN SOFTWARE TECHNOLOGY/PRODUCT FEATURES AND FUNCTIONALITY, INCLUDING POTENTIAL NEW FEATURES AND CONCEPTS, IN A SIMULATED ENVIRONMENT WITHOUT COMPLEX SET-UP OR INSTALLATION FOR THE PURPOSE DESCRIBED ABOVE. THE TECHNOLOGY/CONCEPTS REPRESENTED IN THIS DEMO/LAB MAY NOT REPRESENT FULL FEATURE FUNCTIONALITY AND MAY NOT WORK THE WAY A FINAL VERSION MAY WORK. WE ALSO MAY NOT RELEASE A FINAL VERSION OF SUCH FEATURES OR CONCEPTS. YOUR EXPERIENCE WITH USING SUCH FEATURES AND FUNCITONALITY IN A PHYSICAL ENVIRONMENT MAY ALSO BE DIFFERENT.

## Overview

![arch.png](media/arch.png)

This lab showcases Microsoft Fabric with Copilot and Azure Databricks, featuring a cost-effective, performance-optimized, and cloud-native Analytics solution pattern. This architecture unifies our customers' data estate to accelerate data value creation. 
 
The visual illustrates the real-world example for Contoso, a fictitious company. 

Contoso is a retailer with thousands of brick-and-mortar stores across the world and an online store. Contoso is acquiring Litware Inc., which has curated marketing data and sales data processed by Azure Databricks and stored in the gold layer in ADLS Gen2. Contoso also has their customer churn data stored in the gold layer in ADLS Gen2. 
 
In the following exercises, you will see how the Contoso team leveraged the power of Microsoft Fabric to ingest data from a spectrum of sources, combine Litware's data with their existing data from ADLS Gen2, and derive meaningful insights. Explore how they used a shortcut to reference Litware's existing data from ADLS Gen2. Finally, you will see how Contoso's data architects utilized Unity Catalog to quickly get up to speed on the acquired company's data. After Constoso's data architects got upto speed, they chose which data to pick from the Unity catalog and include that in OneLake using Mirrored Azure Databricks Catalog. You will also see the power of creating LLM Chatbots with the Databricks Data Intelligence Platform to uncover an unprecedented market sentiment for Contoso.

The lab scenario begins on January 30th. The new CEO, April, has noticed some negative trends in the company's key metrics, including:

- A high number of their customers leaving

- Falling sales revenue

- High bounce rate on their website

- High operating costs

- Poor customer experience

- And most importantly, low market sentiment

To address the high customer churn, April and the Contoso team decided to acquire Litware Inc., which carries products popular with millennials. April asks Rupesh, the Chief Data Officer, how they could create a data-driven organization and reverse these adverse KPI trends. Rupesh talks to his technical team, including Eva, the data engineer; Miguel, the data scientist; and Wendy, the business analyst. He tasks them with designing and implementing a solution pattern to realize this vision of a data-driven organization. 

The team recognizes that the existence of data silos within Contoso's various departments presents a significant integration challenge, which is intensified by the need to combine subsidiary data with data from Litware Inc. To overcome these challenges, they plan to utilize Fast Copy for efficient data ingestion, Task Flow for streamlined workflows, Real-time Intelligence for immediate insights, and Azure SQL DB Mirroring in Fabric to ensure seamless access to relational data across the organization.

During this lab you will execute some of these steps as a part of this team to reverse these adverse KPI trends. First, you will ingest data from a spectrum of data sources into OneLake for Contoso. Let's get started.

## Table of Contents
 
Exercise 1: Data Engineering and Data Factory experience: Data ingestion from a spectrum of analytical data sources into OneLake
 
 - Task 1.1: Create a Microsoft Fabric enabled workspace
 - Task 1.2: Use the New Shortcut option from external data sources
 - Task 1.3: Create Delta tables using Spark Notebook

Exercise 2: Azure Databricks integration with Fabric: DLT Pipelines, Unity Catalog (Data governance), Mirrored Azure Databricks Catalog

 - Task 2.1: Create Delta Live Table pipeline for Data Transformation
 - Task 2.2: Explore the data in the Azure Databricks environment with Unity Catalog (unified governance solution for data and AI)
 - Task 2.3: Create a Mirrored Azure Databricks Catalog in Fabric and analyze data using T-SQL

Exercise 3: Building an AI-Powered Chatbot with Microsoft Fabric and Azure AI Studio

 - Task 3.1: Integrate Fabric data with Azure AI Studio using Azure AI Search
 - Task 3.2: Establish Azure OpenAI, Azure AI Content Safety, and AI Search Connections in Azure AI Studio
 - Task 3.3: Setup and use Prompt Flow in Azure AI Studio

**Optional exercises**

Exercise 4: Power BI Experience in Fabric (Optional)
 
 - Task 4.1: Create a Semantic model and generate insights using Copilot for Power BI

Exercise 5: Explorer Data Science experience in Microsoft Fabric
 
 - Task 5.1: Build ML models and experiments using Copilot in Fabric  

