# Module 09 - Integrate with Azure Synapse Analytics

## Introduction

Azure Synapse Analytics, formerly known as Azure SQL Data Warehouse, is a big data analytics solution with enterprise data warehousing features. It provides different types of compute environments for different workloads. It is often used to process large volumes of data and can be used to design a data lake, data warehouse or big data analytics platform.

Registering a Microsoft Purview account to a Synapse workspace allows you to discover Microsoft Purview assets, interact with them through Synapse specific capabilities, and push lineage information to Microsoft Purview. This enables you to see what data is ingested, processed and consumed by what analytical processes.

## Objectives

* Register an Azure Purview account to a Synapse workspace.
* Query a dataset that exists in the Azure Purview catalog with Azure Synapse Analytics.

## Table of Contents

1. [Azure Data Lake Storage Gen2 Account Access](#1-azure-data-lake-storage-gen2-account-access)
2. [Connect to a Purview Account](#2-connect-to-a-purview-account)
3. [Search a Purview Account](#3-search-a-purview-account)

## 1. Azure Data Lake Storage Gen2 Account Access

>**Did you know?**
>
> One of the key benefits of integrating Azure Synapse Analytics with Azure Purview, is the ability to discover Azure Purview assets from within Synapse Studio (i.e. no need to swtich between user experiences), with added abilities using Synapse specific capabilities (e.g. SELECT TOP 100). 
>
> Note: Before we can demonstrate the ability to query external data sources from Azure Synapse Analytics, we need to ensure our account has the appropriate level of access (i.e. `Storage Blob Data Reader`).

1. Navigate to the **Azure Data Lake Storage Gen2 account** `pvlab{DID}adls`), select **Access Control (IAM)**, and then click **Add role assignment**.

    ![Storage Access Control](../images/module09/upd-M8-T1-S1.png)

2. Filter the list of roles available by searching for `Storage Blob Data Reader`, select the **Storage Blob Data Reader** role from the list, and click **Next**.

    ![Storage RBAC Assignment](../images/module09/09.02-storage-rbaca.png)

3. To add your account click **Select members**, search for the user named **ODL_User <inject key="DeploymentID" enableCopy="false" />** in your Azure Active Directory , select the account from the list, and click **Select**.

    ![Storage RBAC Assignment](../images/module09/09.16-rbac-members-1.png)

4. Click **Review + assign** to progress to the final confirmation screen and then click **Review + assign** once more.

    ![Storage RBAC Assignment](../images/module09/09.17-rbac-reviewa.png)

## 2. Connect to a Purview Account

1. Within the Azure portal, navigate to the **purviewlab-rg** and open the Synapse workspace named **pvlab-{randomId}-synapse** and click **Open Synapse Studio**.

    ![Open Synapse Studio](../images/module09/09.08-synapse-studioa.png)

2. Navigate to **Manage**(1)> **Microsoft Purview**(2) and click **Connect to a Purview account**(3).

    ![Connect to a Purview Account](../images/module09/09.09-synapse-connect-1.1.png)

3. Select your **Purview account** from the drop-down menu and click **Apply**.

    ![Select a Purview Account](../images/module09/09.10-synapse-purviewa.png)

4. Once the connection has been established, you will receive a notification that **Registration succeeded**. Switch to the **Purview account** tab to confirm that the Purview account is connected. On this page, you will also see a list of integration capabilities that are now available (e.g. Azure Purview search, Synapse Pipeline lineage, etc).

    >**Did you know?**
    >
    > When connecting a Synapse workspace to Purview, Synapse will attempt to add the necessary Purview role assignment (i.e. `Data Curator`) to the Synapse managed identity automatically. This operation will be successful if you belong to the **Collection admins** role on the Purview root collection and have access to the Azure Purview account. For more information, check out [Connect a Synapse workspace to an Azure Purview account](https://docs.microsoft.com/en-us/azure/synapse-analytics/catalog-and-governance/quickstart-connect-azure-purview).

    ![Purview Account Registered](../images/module09/09.11-synapse-success-1.1.png)

5. To validate that Synapse was able to successfully add the Synapse managed identity to the Data Curator role, navigate to the **Microsoft Purview Governance Portal**, **Data map**(1) > **Collections**(2) > **YOUR_ROOT_COLLECTION**(3), switch to the **Role assignments**(4) tab and expand **Data curators**(5). You should be able to see the **Synapse Service Principal**(6) listed as one of the Data curators. This will provide Synapse read/write access to the catalog.

    ![](../images/module09/09.18-synapsemi-curator.1.1.png)

## 3. Search a Purview Account

1. Within the **Synapse workspace**, navigate to the **Data** screen and perform a **keyword search** `parquet`. Notice that the search bar now defaults to searching the entire Purview catalog as opposed to the Synapse workspace only.

    ![Search Purview Account](../images/module09/09.12-synapse-search.png)

2. Click to open the **asset details** of the items `twitter_handles.parquet`.

    ![Open Asset Details](../images/module09/09.13-synapse-open.png)

3. Notice the special Synapse-specific menu items such as **Connect** and **Develop**. For supported file types such as parquet, you can quickly generate sample code to query the external source by navigating to **Develop** > **New SQL script** > **Select top 100**.

    ![Select Top 100](../images/module09/09.14-synapse-select.png)

4. To execute the query, click **Run**. 
    ![Run Query](../images/module09/09.15-synapse-run.png)

## Knowledge Check

[http://aka.ms/purviewlab/q09](http://aka.ms/purviewlab/q09)

1. Connecting a Synapse workspace to Azure Purview enables you to discover data assets that live **outside** of the Azure Synapse Analytics workspace?

    A ) True  
    B ) False  

2. A single Synapse Analytics workspace can connect to **multiple** Azure Purview accounts?

    A ) True  
    B ) False  

3. Once Synapse Analytics is connected to an Azure Purview account, users can quickly generate a new linked service or integration dataset via the action buttons (for supported file types)?

    A ) True    
    B ) False  

## Summary

This module provided an overview of how to register an Azure Purview account to an Azure Synapse Analytics Workspace, view the details of an asset that exists outside of the Synapse workspace, and how you can quickly query an external source.
