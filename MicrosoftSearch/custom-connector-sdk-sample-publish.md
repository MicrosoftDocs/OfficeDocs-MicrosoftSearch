---
title: "Graph connectors SDK sample publish"
ms.author: rchanda
author: rchanda1392
manager: harshkum
ms.audience: Admin
ms.topic: article
ms.service: mssearch
ms.date: 06/29/2022
description: "Graph connectors SDK sample publish"
---

# Publish your first custom connection on M365 Admin Center

1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com/)

2. Navigate to **Search & intelligence** > **Data Sources** and click on “**Add**”.

3. Choose "**Custom Connector**" option and paste the following manifest details for your sample connector implementation with your updated **connectorId**:

    ```json
     {
      // This is the unique connector id/provider id
      "connectorId": "<ConnectorGuid>",
    
      // This is list of all supported auth types. Remove the ones that the connector does not support.
      "authTypes": [ "Anonymous" ]   
    }

    ```

    >[!Note]
    >You can also find the manifest file auto generated in the output directory of your project.

4. Provide connection name, connection ID, description (optional) select the checkbox and click Next.

5. Provide URL of the location where you've downloaded the CSV file to be indexed and choose the Graph connector Agent installed. Click **Test connection** to validate the information provided. Click Next on successful validation.

6. Click Next on the **Additional parameters** screen

7. Click Next on the **Assign property labels** screen

8. Click Next on the **Manage schema** screen

9. Select **Everyone** on **Manage search permissions** screen

10. Select the **Full refresh frequency** as 15 minutes

11. Review the details provided and click Finish
