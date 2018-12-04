---
# required metadata

title: Project Service Automation
description: This topic provides information about the Project Service Automation to Finance and Operations integration solution. This integration solution uses the Data Integration feature to synchronize data across instances of Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Project Service Automation via Common Data Service.
author: KimANelson
manager: AnnBe
ms.date: 06/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 87983
ms.assetid: b454ad57-2fd6-46c9-a77e-646de4153067
ms.search.region: Global
# ms.search.industry: 
ms.author: knelson
ms.search.validFrom: 2016-11-28
ms.dyn365.ops.version: AX 7.0.0

---

# Project Service Automation

[!include[banner](../includes/banner.md)]

The Project Service Automation to Finance and Operations integration solution uses the Data integration feature to synchronize data across instances of Microsoft Dynamics 365 for Finance and Operations and Microsoft Dynamics 365 for Project Service Automation via Common Data Service. The integration templates that are available with the Data integration feature enable the flow of projects, project contracts, project contract lines, project contract line milestones, project tasks, expense transaction categories, hour estimates, and expense estimates from Project Service Automation to Finance and Operations.

> [!NOTE]
> - If you're using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3.0, after you install KB 4132657 and KB 4132660, you will be able to use the templates to integrate project tasks, expense transaction categories, hour estimates, expense estimates, and actuals, and to configure functionality locking. If you must reset the accounting distributions, we recommend that you also install KB 4131710.
> - If you're using Finance and Operations 7.3.0, you must install KB 4074835. You will then be able to integrate fixed price projects.
> - If you're using Finance and Operations 7.3.0, and you are bringing fee transactions over from Project Service Automation, you must install KB 4345320 in order to include those fees in the project invoice.
> - If you're using Microsoft Dynamics 365 for Finance and Operations version 8.0, you will be able to use project task integration, expense transaction categories, hour estimates, expense estimates, and functionality locking.
> - If you're using Microsoft Dynamics 365 for Finance and Operations version 8.0.1, or later, you will be able to synchronize actuals.

Before you can integrate Project Service Automation with Finance and Operations, you must configure the Project Service Automation integration parameters. For more information, see [Project Service Automation integration parameters](PSA-parameters.md).

This integration solution enables direct synchronization in the following scenarios:

- Maintain project contracts in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Create projects in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain project contract lines in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain project contract line milestones in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain project tasks in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Maintain expense transaction categories in Finance and Operations, and synchronize them directly from Finance and Operations to Project Service Automation.
- Create project hour estimates in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Create project expense estimates in Project Service Automation, and synchronize them directly from Project Service Automation to Finance and Operations.
- Create project time, expense, and fee actuals in Project Service Automation, and create project transactions in the Project Service Automation integration journal so that they can be posted in Finance and Operations.

## Data synchronization

The following illustration shows how data is synchronized as part of the integration between Project Service Automation and Finance and Operations.

> [!NOTE]
> Not all templates are currently available. Templates will be released as they are completed.

[![Project Service Automation integration with Finance and Operations](./media/PSA-integration.png)](./media/PSA-integration.png)

## System requirements for Finance and Operations

To use the Project Service Automation to Finance and Operations integration solution, you must install Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3 with platform update 12 or later.

## System requirements for Project Service Automation

To use the Project Service Automation to Finance and Operations integration solution, you must install the following components:

- Microsoft Dynamics 365 for Project Service Automation version 9.0.0.0 or later
- Prospect to cash solution for Microsoft Dynamics 365 for Sales, version 1.14.0.0 (v14) or later
- Project Service Automation to Finance and Operations solution for Microsoft Dynamics 365 for Project Service Automation version 1.0.0.0 or later

## Install the Project Service Automation to Finance and Operations integration solution in your Project Service Automation instance

Download the Project Service Automation to Finance and Operations integration solution from [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57016), and follow the instructions that are included with the solution.
