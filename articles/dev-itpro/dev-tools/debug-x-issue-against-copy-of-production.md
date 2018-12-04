---
# required metadata

title: Debug X++ against copies of production databases
description: This topic explains how to configure X++ debugging so that you can investigate issues in the production environment.
author: tariqbell
manager: AnnBe
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 199063
ms.assetid: 3c0551f3-6c96-4518-8acd-82d4638f9323
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2016-05-31
ms.dyn365.ops.version: AX 7.0.1

---

# Debug X++ against copies of production databases

[!include [banner](../includes/banner.md)]

This topic explains how to configure X++ debugging so that you can investigate issues in the production environment. For this procedure, you make a copy of the production database and then configure a developer environment to connect to the copy.

## Solution overview

When an issue that requires X++ debugging occurs in a production environment, the system administrator and developer work together to configure debugging and then debug the issue. The following illustration shows an overview of the process.

[![Debugging process](./media/debugxpp.jpg)](./media/debugxpp.jpg)

1. In Microsoft Dynamics Lifecycle Services (LCS), the system administrator requests that a copy of the database be connected to the sandbox user acceptance testing (UAT) environment. (In other words, request a database refresh.)
2. In Microsoft Azure DevOps, the developer synchronizes the local code to the same build that is running in the production environment.
3. In the sandbox instance of Microsoft Azure SQL Database, the system administrator creates a temporary SQL sign-in for the developer. The developer then configures the environment to connect to the sandbox database.
4. A firewall exception is added so that the developer environment can connect to the sandbox database.
5. The developer debugs the issue.

> [!NOTE]
> When debugging is completed, the system administrator can remove the temporary sign-in from the sandbox SQL database.

## Before you begin

Before you begin to configure X++ debugging in a production environment, note the following points:

- You can't debug directly against the production environment, because debugging might cause data corruption. However, developers can manipulate values at runtime. Alternatively, in their own instance, developers can make a code change that changes data.

    > [!NOTE] 
    > The developer environment that is used for debugging must exist in the same LCS project as the sandbox environment, and both of them must be Microsoft managed. This requirement helps strengthen the security of the sandbox database. By default, there is a firewall restriction on both the sandbox and production SQL databases. This restriction allows only servers in those environments to connect to the databases. To enable debugging, a firewall exception is added so that a developer environment can connect to the sandbox database.


- A one-time manual change to the developer environment is required, so that the IP address of the environment can connect to the sandbox database. Submit a request to the Microsoft Service Engineering Team (DSE) to allow the IP address.
- We recommend that you not use a build environment for debugging. Otherwise, there is a risk that the developer's activities on the computer might break the automated build process.

## Solution details

When an issue occurs in the production environment, the system administrator can sign in to LCS and request that a database copy be added to a sandbox environment. While the database copy is running, the system administrator can notify the developer of the issue. The developer can then synchronize to the correct build of the code to match the production environment.

1. In Microsoft Visual Studio, in Source Control Explorer, right-click the root node of the branch to synchronize, and then select **Advanced** &gt; **Get specific version**.
2. In the dialog box, select **Type=Label**, and then select the ellipsis (**...**).
3. In the dialog box, select **Find**. All the builds from the build server are listed.
4. Select the build that is currently deployed in the production environment, and then select to run a full build. When the database is copied, only the system administrator will be able to access the sandbox database. The system administrator must complete the following tasks:

    - Remove any data that you don't want in the sandbox database, such as employee salaries.
    - Enable or add the developer as a user.
    - Create a new SQL sign-in that the developer can use. This step lets the system administrator maintain the security of the sandbox environment. The developer will have access to one database for only a limited time. Use the following code to create the new SQL sign-in.

        ```
        CREATE USER devtempuser WITH PASSWORD = ''
        EXEC sp_addrolemember 'db_owner', 'devtempuser'
        ```

Next, the developer edits the web.config file for Application Object Server (AOS).

1. Go to **J:\\AosService\\WebRoot\\web.config**.
2. Save a copy of the original web.config file, so that you can switch back later.
3. Edit the following section in the web.config file.

    **Before your changes**

    ```
    <add key="DataAccess.Database" value="sandboxDatabaseName" />
    <add key="DataAccess.DbServer" value="sandboxDbServerName.database.windows.net" />
    <add key="DataAccess.SqlPwd" value="password" />
    <add key="DataAccess.SqlUser" value="devtempuser" />
    ```

    **After your changes**

    ```
    <add key="DataAccess.Database" value="TariqRTW_axdb_dd78f8aadbc6c481" />
    <add key="DataAccess.DbServer" value="vyxx2dflyo.database.windows.net" />
    <add key="DataAccess.SqlPwd" value="P@ssw0rd" />
    <add key="DataAccess.SqlUser" value="devtempuser" />
    ```

4. Debug the issue.

After the developer has finished, the system administrator can remove devtempuser from the sandbox database. This step prevents the developer from having permanent access to the sandbox database.
