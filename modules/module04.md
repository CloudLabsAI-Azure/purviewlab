# Module 04 - Glossary

## Introduction

A [Glossary](https://docs.microsoft.com/azure/purview/concept-business-glossary), sometimes called Data Glossary or Business Glossary, is a list of business terms with their definitions. A Glossary is an important tool for maintaining and organizing information about your data. It is used for capturing domain knowledge of information that is commonly used, communicated, and shared in organizations as they are conducting business.

There aren’t any rules for the size and representation of glossaries. They can stay abstract or high-level, but also are allowed to be detailed, describing carefully attributes, dependencies, relationships and definitions. A glossary isn't limited to only a single database, in fact it can cover many applications or multiple databases. Multiple applications can work together to accomplish a specific business need. This means that the relation between a glossary and data attributes is a one-to-many relationship. The glossary can also include and capture more concepts than the concepts representing the application or database itself. It can include concepts, which are used to make the context clearer, but don’t play a direct role (yet) in the application or database design. It can also include concepts, that represents future requirements, but didn’t find their way yet into the actual design of the application or database yet.

When implementing your Glossary it is important to think about how you will structure your business terms and definitions. For example, you could use hierarchies and align these with business domains such as: Finance, Marketing, Sales, HR, etc. You could think of naming standards or introduce term templates for capturing additional information about your business metadata. You could also use relationships for linking business terms, such as Acronyms, Related terms and Synonyms. These relationships could help to avoid creating terms with duplicated names and lower the overhead of management.

In this lab you learn how to create terms using a system and custom term template. You'll also learn how to import and export terms. Lastly, you learn about linking terms to data assets, which helps to relate technical metadata to business metadata.

## Objectives

* Create a Term in the Glossary using the System Default Term Template.
* Create a Term in the Glossary using a Custom Term Template.
* Bulk Import Terms into the Glossary via a CSV file.
* Bulk Export Terms from the Glossary into a CSV file.
* Assign a Term to an Asset in the Data Catalog.
* Update an existing Term with Related Terms and Contacts.

## Table of Contents

1. [Create a Term (System Default Term Template)](#1-create-a-term-system-default-term-template)
2. [Create a Term (Custom Term Template)](#2-create-a-term-custom-term-template)
3. [Bulk Import Terms](#3-bulk-import-terms)
4. [Bulk Export Terms](#4-bulk-export-terms)
5. [Assign a Term to an Asset](#5-assign-a-term-to-an-asset)
6. [Update an Existing Term](#6-update-an-existing-term)

## 1. Create a Term (System Default Term Template)

1. Open the **Microsoft Purview Governance Portal** and from the **Data catalog**, click **Glossary**.

    ![](../images/module04/m4-t1-step1.png)

2. Click on **New term** to create a new **Glossary** item.

    ![New Glossary Term](../images/module04/m4-t1-step2.png)

3. Select the **System default** term template and click **Continue**.

    > **Did you know?**
    >
    > A **Term Template** determines the attributes for a term. The **System default** term template has basic fields only (e.g. Name, Definition, Status, etc). **Custom** term templates on the other hand, can be used to capture additional custom attributes. For more information, check out [How to manage term templates for business glossary](https://docs.microsoft.com/en-us/azure/purview/how-to-manage-term-templates).

    ![System default term template](../images/module04/m4-t1-step3-1.png)

4. In the New term tab, provide the following details and click on **Create**.

    **Status**
    ```
    Approved
    ```
    **Name**
    ```
    Contoso Parent
    ```
    **Definition**
    ```
    This will be the parent term.
    ```
    **Acronym**
    ```
    CP
    ```
    > **Info**: Click on **+ Add a resource** to add the resource.

    **Resource Name**
    ```
    Microsoft Purview
    ```
    **Resource Link**
    ```
    https://aka.ms/Azure-Purview
    ```
    
    ![New Term](../images/module04/m4-t1-step4.png)

## 2. Create a Term (Custom Term Template)

1. Open the **Microsoft Purview Studio** and from the **Data catalog**, click **Glossary** and click **Glossary**.

    ![](../images/module04/m4-img1.png)

2. Click **New term**.

    ![New Term](../images/module04/M4-Update3.png)

3. Click **New term template**.

    ![New term template](../images/module04/M4T2S3.png)

4. Provide the Term Template a **Name** as `Contoso Template` and click **New attribute**.

    ![Term template](../images/module04/m4-img2.1.png)

5. Populate the attribute fields as per the examples below and click **Apply**.

    | Field  | Example Value |
    | --- | --- |
    | Attribute name | `Business Unit` |
    | Field type | `Single choice` |
    | Choices | `Sales`, `Marketing`, `Finance`, `Human Resources`, `IT` |

    > **Info**: Click on **Choices** to add a choice.

    ![Attribute](../images/module04/04.07-attribute-properties1.png)

6. Click on **Create** to create the template.

    ![Create term template](../images/module04/04.08-template-create.png)

7. Select the **Contoso Template** and click on **Continue**.
    
    ![Custom Term Template](../images/module04/04.09-term-custom1.png)

8. Change the **Status** of the term to `Approved` and then **copy** and **paste** the values below into the appropriate field, then click **Create**.

    **Name**
    ```
    Contoso Child
    ```
   **Parent**
    ```
    Contoso Parent
    ```   
   **Definition**
    ```
    This will be the long description for the child glossary term.
    ```
    **Business Unit**
    ```
    Marketing
    ```
    
    ![](../images/module04/M4-T2-S8.1.png)


9. Navigate back to **Glossary** screen, change the view to **Hierarchical view** to see the hierarchical glossary.

    ![](../images/module04/M4T2S9.png)
    
## 3. Bulk Import Terms

1. Download a copy of **[import-terms-sample.csv](https://github.com/tayganr/purviewlab/raw/main/assets/import-terms-sample.csv)** to your **labvm** by opening the link in a new tab, right-click within the body of the content, click **Save as** .

    ![Import terms](../images/module04/04.29-sample.1-saveas.png)
    
2. Select **All files** under **Save as type** and click on **Save**.

   ![Svae](../images/module04/saveas.png)

3. From the **Glossary** screen, click **Import terms**.

    ![Import terms](../images/module04/M4-T3-S3.1.png)

4. Select the **System default** term template and click **Continue**.

    ![Term Template](../images/module04/04.13-import-default.1.png)

5. Click **Browse** and open the local copy of **import-terms-sample.csv**.

    ![Browse](../images/module04/04.14.1-import-browse.png)

6. Click **OK**.

    ![Upload CSV file](../images/module04/04.15-import-ok.1.png)

7. Once complete, you should see 50 additional terms beneath the parent (Workplace Analytics). **Tip**: You can quickly find specific types of terms using the filters at the top (e.g. Status = Approved).

    ![Filter Terms](../images/module04/M4-T3-S7.1.png)

## 4. Bulk Export Terms

1. From the **Glossary** screen, we want to select ALL terms (top check box) and then de-select terms that do not belong to Workplace Analytics (i.e. Contoso Parent, Contoso Child). **All Workplace Analytics terms** should be selected. Click **Export terms**. 

   
   ![Export Terms](../images/module04/M4-T4-S1.1.png)

2. If the export was successful, you should find a **CSV** file has been copied to your **labvm** in the **Downloads** folder.

    ![Downloads](../images/module04/04.18.1-export-downloads.png)

## 5. Assign a Term to an Asset

1. Perform a wildcard search by typing asterisk (**\***) into the search bar and hitting the Enter key to submit the query. Click on the asset title `QueriesByState` to view the details.

    ![Wildcard Search](../images/module04/M4-Update4.1.1.png)

2. Click on **Edit** to edit the dataset.

    ![Edit Asset](../images/module04/M4-Update5.1.1.png)

3. Open the **Glossary terms** drop-down menu and select a glossary term named `Contoso Child`. Click **Save**.

    ![Assign Term](../images/module04/M4-Update6.1.png)

4. Click on the **Contoso Child** hyperlinked term name to view the glossary term details.

    ![Assigned Terms](../images/module04/M4-Update7.1.png)

5. Click **Refresh** to view the **Catalog assets** that the term is assigned to.

    ![Catalog assets](../images/module04/M4-Update8.1.png)
    
## 6. Update an Existing Term

1. From the **Glossary** screen, open an existing term `Aggregation`.

   ![Term Details](../images/module04/04.24-term-view.png)

2. Navigate to the **Related** tab and click **Edit**.

    ![Related](../images/module04/04.25-term-related.png)

3. Use the drop-down menu to assign two glossary terms as **Synonyms** i.e **Workspace Analytics> Attended** and **Workspace Analytics> Attendee**.

    > **Did you know?**
    >
    > **Synonyms** are other terms with the same or similar definitions. Where as **Related terms** are other terms that are related but have different definitions.

    ![Synonyms](../images/module04/04.26-term-synonym.png)

4. Use the drop-down menu to assign two glossary terms as **Related terms** i.e  **Workspace Analytics> Collaborator group** and **Workspace Analytics> Collaborators** .

    ![Related Terms](../images/module04/04.27-term-related.png)

5. Navigate to the **Contacts** tab and assign an **Expert** and a **Steward** to the user named **ODL_User [DID]**. Click **Save**.

    > **Did you know?**
    >
    > Glossary terms can be related to two different types of contacts. **Experts** are typically a business process or subject matter experts. Where as **Stewards** define the standards for a data object or business term. They drive quality standards, nomenclature, rules.

    ![Term Contacts](../images/module04/M4-Update10.1.png)

## Knowledge Check

[http://aka.ms/purviewlab/q04](http://aka.ms/purviewlab/q04)

1. Glossary terms with the same name but different descriptions can exist under the same parent term?

    A ) True  
    B ) False 

2. Glossary terms can be related to other terms in the glossary. Which of the following is **not** a valid glossary term relationship type?

    A ) Synonyms  
    B ) Antonyms  
    C ) Related terms  

3. Glossary terms created using different term templates can be exported together using the Microsoft Purview Governance Portal (UI) glossary "Export terms" functionality?

    A ) True  
    B ) False  
    
## Summary

This module provided an overview of how to create, export, and import terms into the Microsoft Purview glossary.
