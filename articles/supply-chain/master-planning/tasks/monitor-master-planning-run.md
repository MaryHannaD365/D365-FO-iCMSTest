--- 
# required metadata 
 
title: Monitor a master planning run
description: The production planner wants to see if a master planning run is in progress. 
author: ShylaThompson
manager: AnnBe 
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: DefaultDashboard, ReqCreatePlanWorkspace, ReqTransPlanCard, SysQueryForm, InventItemIdLookupSimple, ReqLog, ReqProcessTaskTrace   
audience: Application User 
# ms.devlang:  
ms.reviewer: shylaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Monitor a master planning run

[!include [task guide banner](../../includes/task-guide-banner.md)]

The production planner wants to see if a master planning run is in progress. Use the demo data company USMF to complete this procedure.


## Run master planning
1. Click Master planning.
    * You'll find this on the default dashboard.  
2. In the Plan field, enter or select a value.
    * Example: StaticPlan  
3. Click Run.
4. Select Yes in the Track processing time field.
    * If the field is already selected, skip this step.  
5. In the Number of threads field, enter a number.
6. Expand the Records to include section.
7. Click Filter.
8. In the list, mark the selected row.
    * Mark the row where Field = Item number.  
9. In the Criteria field, enter or select a value.
    * Example: T0001  
10. Click OK.
11. Click OK.

## Monitor the master planning run
1. Click History.
2. Click Inquiries.
3. Click Process task duration.
4. In the list, find and select the desired record.
    * For each item you can get an overview of how long it took to complete each planning step.  

