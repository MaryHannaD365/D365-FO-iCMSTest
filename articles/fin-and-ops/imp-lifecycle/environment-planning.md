---
# required metadata

title: Environment planning
description: This topic provides an overview of various aspects that you must consider while you plan for your project's environment.
author: ClaudiaBetz-Haubold
manager: AnnBe
ms.date: 08/13/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:  
# ROBOTS:
audience: IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: chaubold
ms.search.validFrom: 2018-08-01
ms.dyn365.ops.version: Finance and Operations

---

# Environment planning

[!include[banner](../includes/banner.md)]

This topic provides an overview of various aspects that you must consider while you plan for your project's environment. To help guarantee a successful cloud implementation of Microsoft Dynamics 365 for Finance and Operations, it's important that you discuss and plan your environment early in the project.

## Environment planning overview

To begin, here are a few important concepts:

- **Environment purpose** – The reasons why the environment exists. Examples include development, system testing, user acceptance testing (UAT), and operations.
- **Environment topology** – The composition of the environment and the purpose. Examples include **Develop** and **Build and Test** for Tier-1 environments.
- **Environment tier** – The type or category of the environment. Examples include Tier-1 environments and Tier-2 environments.

For more information, about the various environments and tiers, download the latest *Microsoft Dynamics 365 Licensing Guide* from [Dynamics 365 pricing](https://dynamics.microsoft.com/en-us/pricing/).

### Environment types
You can use the following environment types for your project:

- **Standard** – This environment is included in the standard offer and is managed by Microsoft in a Microsoft subscription. Standard environments include the production environment, a Tier-2 Standard Acceptance Test environment, and one Tier-1 develop and test environment.
- **Add-on** – The add-on environments are in a Microsoft-managed subscription that the customer has purchased in addition to the standard offer. For example, an add-on environment might be an additional Tier-4 environment for performance testing.
- **Cloud-hosted** – Cloud-hosted environments are additional environments that are managed by the customer or partner in a customer or partner Microsoft Azure subscription. A cloud-hosted environment can include a Tier-1 demo environment.
- **Environment image (VHD)** – These additional Tier-1 environments are hosted on-premises by using a virtual hard disk (VHD) that can be downloaded from [Microsoft Dynamics Lifecycle Services (LCS)](https://lcs.dynamics.com/v2).

> [!IMPORTANT]
> In a *customer or partner Azure subscription*, the customer or partner brings its own Azure subscription, and deploys Finance and Operations environments to that subscription for evaluation and development purposes only. The customer or partner pays for the resources that are deployed to its Azure subscription. The amount that the customer or partner pays is based on the Azure price list. By contrast, in a *Microsoft subscription*, the customer purchases Finance and Operations licenses. These licenses then allow the customer to deploy environments to an Azure subscription that is managed by Microsoft. Therefore, the customer has no separate Azure billing.

### Tier-1 vs. Tier-2 and higher
| Tier-1 | Tier-2 and higher |
|--------|-------------------|
| Single-box environment | Multi-box environment |
| All components are installed on the same server. These components include Application Object Server (AOS), the database, Microsoft Dynamics 365 for Retail, and Management Reporter. | Components are installed on multiple servers. |
| Microsoft SQL Server is used. | [Azure SQL Database](https://docs.microsoft.com/en-us/azure/sql-database/) is used. |
| The architecture differs from the architecture of the production environment to maximize the efficiency of the development team. | The architecture is the same as the architecture of the production environment, even though this type of environment has a different sizing and isn't enabled for disaster recovery. |
| The environment can be deployed in various ways. For example, it can be deployed as an add-on, it can be cloud-hosted, or it can be deployed as an environment image (VHD). | The environment can be deployed only as a standard environment or an add-on environment. It can't be cloud-hosted. |
| The environment isn't suitable for UAT or performance testing. | The environment is suitable for UAT and performance testing. |

## Finance and Operations standard cloud offer

Each Finance and Operations standard cloud offer includes three environments:

- **Tier-1 environment: Develop and test** – One develop/test instance is provided for the duration of the subscription. This instance is a non-production single-box instance that the customer can use as an automated build environment, or to customize Finance and Operations and do unit testing for the changes. Additional develop/test instances can be purchased separately as an optional add-on.
- **Tier-2 environment: Standard Acceptance Testing** – One Standard Acceptance Testing (UAT) instance is provided for the duration of the subscription. This instance is a non-production multi-box instance that customers can use for UAT, integration testing, and training. Additional sandbox/staging instances can be purchased separately as an optional add-on.
- **Production environment** – One production instance is provided per tenant. The production multi-box instance includes disaster recovery and high availability. It will be provisioned when the implementation approaches the Operate phase, after the required activities in the Microsoft Dynamics Lifecycle Services (LCS) methodology and a successful go-live assessment are completed. Additionally, some file storage and database storage are included in the offer:

    - **File storage:** Every customer receives 100 gigabytes (GB) of file/Azure blob cloud storage for files and binary data. Additional file/blob storage can be purchased.
    - **Database storage:** Every Finance and Operations subscription includes 10 GB of Azure SQL Database storage per customer at no additional charge. Additional storage capacity is provided at no charge as an organization increases the number of user and device service licenses. For more information about the various environments and the various types of storage, download the latest *Microsoft Dynamics 365 Licensing Guide* from [Dynamics 365 pricing](https://dynamics.microsoft.com/en-us/pricing/).

### Provisioning of standard environments

The various Finance and Operations environments are provisioned at different times. The following table shows the suggested timing for the environments in the Finance and Operations standard cloud offer.

| Environment                     | When does provisioning occur? | Is it self-service? |
|---------------------------------|-------------------------------|---------------------|
| Tier-2 Standard Acceptance Test | During onboarding with the Microsoft FastTrack team | Yes |
| Tier-1 develop/build and test   | When the Design phase starts. The provisioning process requires that Microsoft Azure DevOps be configured. | Yes |
| Production                      | At production system readiness | A production deployment request must be submitted in LCS. Deployment is done through the Dynamics Service Engineering (DSE) team within two business days. |

> [!IMPORTANT]
> Always deploy environments by using an **unnamed** account, such as `dynadmin@customer.com`. Use the build topology to deploy and use the develop and test environment, because this topology simplifies build management and automatically initializes the Azure DevOps source repository.

### Production system readiness

The production environment can be deployed when the project is ready for the initial go-live. For more information, see [Prepare for go-live](prepare-go-live.md).

Production system readiness includes, but isn't limited to, the following conditions:

- An up-to-date subscription estimate is activated, as described in [Subscription estimator](../../dev-itpro/lifecycle-services/subscription-estimator.md).
- Code, configuration, and data are ready for cutover.
- An engineering process is in place to manage critical fixes.
- The customer has signed off on the solution and UAT.
- A cutover plan is in place.

Customers should use the production environment to **operate** the solution, not build it. The production environment is sized to run your business. The sizing is based on the subscription estimate and diagnostic data from performance testing. After deployment, customers can and should do a mock cutover and a final round of validation on the production environment. Before the final cutover, customers can request a Point in time restore to restore the production environment to a clean snapshot (up to 35 days in the past).

To select the appropriate data center for the production environment, consider the latency from the geographic locations where the business operates. Use tools such as [PsPing](https://docs.microsoft.com/en-us/sysinternals/downloads/psping) and [azurespeed.com](http://azurespeed.com/) to test latency to Azure data centers.

The following illustrations shows the environment planning process.

![Environment planning process flow](./media/environment-planning-1-process-flow.png)

## Additional environments

Additional environments can be purchased as add-ons, or they can be deployed as cloud-hosted environments. The following illustration shows a *sample* overview of standard and additional environments, based on the complexity of the Finance and Operations implementation.

![Environment purpose and complexity](./media/environment-planning-2-purpose-complexity-matrix.png)

> [!IMPORTANT]
> Always deploy environments by using an **unnamed** account, such as `dynadmin@customer.com`. Assign the environments an owner who will be responsible for their status and maintenance. After go-live, if you plan to work on new releases, get an additional Tier-2 or higher environment to support production.

### Deployment considerations for development environments

For development environments, there are three deployment options:

- **Standard or add-on** – The environments are managed by Microsoft in a Microsoft subscription.
- **Cloud-hosted** – The environments are managed by the customer/partner in a customer/partner Azure subscription.
- **Environment image (downloadable VHD)** – The environments are hosted on-premises.

> [!NOTE]
> You must allocate one development environment per developer.

The following table compares the deployment options.

| Capability                            | Standard/add-on | Cloud-hosted | Environment image |
|---------------------------------------|-----------------|--------------|-------------------|
| Public URL                            | ✓ | ✓ | Not supported |
| Integration development               | ✓ | ✓ | Extra setup is required. (For example, run the admin user provisioning tool.) |
| Azure DevOps                                  | ✓ | ✓ | Extra setup is required. (For example, rename the computer.) |
| Applying deployable packages from LCS | Automated | Automated | Manual through runbooks |
| Deploying data packages from LCS      | ✓ | ✓ | Not supported |
| Maintenance                           | Managed by Microsoft | Managed by the customer/partner | Managed by the customer/partner |
| Cost model                            | Fixed flat rate (The price is the same if the environment is on 24/7.) | Pay as you go (If the environment is on for eight hours, you pay for eight hours.) | Hardware-related |
| Limitations                           | Administrator access is disabled (admin lockdown). | None | None |

> [!IMPORTANT]
> Admin lockdown for Tier-1 environments is effective in Platform update 12 and later. Actions that require local administrator access can no longer be performed. These actions include installation of third-party tools and development of Microsoft Power BI reports. If administrator permissions are required, use cloud-hosted environments or an environment image (downloadable VHD) instead. For more information, see [Development and build VMs that don't allow admin access FAQ](../../dev-itpro/sysadmin/vms-no-admin-access.md).

### Selecting the correct Tier-2 or higher environment

It's important that you select the correct Tier-2 or higher environment, depending on the purpose of the environment. The guidance that is provided in the following illustration is a *baseline*. You must work with your implementation partner to adjust this guidance, based on your specific business scenarios and factors such as type of users, complexity, and volumes.

![Environment tiers](./media/environment-planning-3-environment-tiers.png)

After a subscription estimate is activated, you can view transaction lines per hour in LCS, as shown in the following illustration.

![Subscription estimate](./media/environment-planning-4-subscription-estimate.png)

> [!IMPORTANT]
> The upcoming admin lockdown for Tier-2 or higher environments will no longer allow Remote Desktop Protocol (RDP) connections to the servers. As part of the Microsoft roadmap, the most common actions where RDP access is required are being replaced by self-service tasks in LCS. For example, the procedure that is currently described in [Copy a Finance and Operations database from SQL Server to a production Azure SQL Database environment](../../dev-itpro/database/copy-database-from-sql-server-to-azure-sql.md) will be available as a service from Microsoft. Therefore, to copy a Finance and Operations database from SQL Server to a production Azure SQL Database environment, you will have to create a service request in LCS. More information will be available through the [LCS Blog](https://blogs.msdn.microsoft.com/lcs/2018/02/27/notice-of-upcoming-change-removing-rdp-access-to-tiers-2-3-4-and-5-standard-acceptance-test-or-sandbox-environments-deployed-in-microsoft-subscription/) and on [Docs](https://docs.microsoft.com/en-us/dynamics365/unified-operations/fin-and-ops/).

### Purchasing add-on environments

If you want to purchase add-on environments, we recommend that you work closely with your Cloud Solution Provider or License Service Reseller. Consider the potential lead time that occurs between the time when the order is placed and the time when the environment is deployed.

The following illustration shows the process for purchasing add-on environments.

![Procuring add-ons](./media/environment-planning-5-procuring-add-on.png)

> [!IMPORTANT]
> If you have a Microsoft Volume Licensing agreement, you can subscribe to add-on environments on a monthly basis through the Microsoft Products and Services Agreement (MPSA) licensing program. Alternatively, you can subscribe to them through the Microsoft Cloud Solution Provider (CSP) program. For more information about the various environments and tiers, download the latest *Microsoft Dynamics 365 Licensing Guide* from [Dynamics 365 pricing](https://dynamics.microsoft.com/en-us/pricing/).

## Environments plan

Create the environments plan early in your implementation.

1. Identify the project activities that require an environment. These activities include, but aren't limited to, development of customizations and maintenance of golden configuration data.
2. Determine the *activities lifecycle* to determine the *environments lifecycle*. Here are some examples of the questions that you should ask during this step:

    - When and for how long do you require the environment?
    - Do you require the environment before or after go-live?

3. Determine the type and topology of the required environments.
4. Summarize the list of required environments in a matrix.

After you've identified the environments, the environments plan can be used to structure the Application Lifecycle Management (ALM) flows. For example, after you finalize your environments plan, you can define the flows for building and moving the code and the data across environments.

We strongly recommend that you watch the [Environment Planning TechTalk](https://infopedia.eventbuilder.com/event?eventid=o8a5q2&source=Dynamics_365_for_Operations_-_FastTrack_Tech_Talks). From the linked page, you can also download the *Sample Environment Planning exercise* spreadsheet to get a head start on your environment planning exercise.
