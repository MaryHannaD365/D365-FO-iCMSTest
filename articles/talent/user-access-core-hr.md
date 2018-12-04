---
# required metadata

title: User can access Core HR but not the Onboard or Attract app
description: This topic explains how to resolve the issue where a user can access Microsoft Dynamics 365 for Talent Core HR, but can't access the Attract or Onboard app.
author: Darinkramer
manager: AnnBe
ms.date: 11/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: dkrame
ms.search.validFrom: 2018-11-02
ms.dyn365.ops.version: Talent

---

# User can access Core HR but not the Onboard or Attract app

[!include [banner](includes/banner.md)]

**Environment details**

- The Microsoft Dynamics Lifecycle Services (LCS) deployment was done by user A.
- User A added user B as a user to Microsoft Dynamics 365 for Talent Core HR.

**Issue**

User B can access Core HR, but can't access the Talent: Attract or Talent: Onboard app. When the user tries to go to **Experience apps**, he or she is taken to a trial environment instead.

**Solution**

User B must be assigned the rights to view the Microsoft PowerApps environment that user A created during the provisioning process.

For information, see the "Granting access to the environment" section in [Provision Talent](https://docs.microsoft.com/en-us/dynamics365/unified-operations/talent/provisioning-talent).

**Long-term solution**

Microsoft is considering automatically assigning the appropriate rights to Onboard and Attract when a user is added to Core HR.
