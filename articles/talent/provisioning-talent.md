---
# required metadata

title: Provision Talent
description: This topic walks you through the process of provisioning a new environment for Microsoft Dynamics 365 for Talent. 
author: rschloma
manager: AnnBe
ms.date: 09/27/2018
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
ms.search.scope: Talent
# ms.tgt_pltfrm: 
ms.custom: 17271
ms.assetid: ba1ad49d-8232-400e-b11f-525423506a3f
ms.search.region: Global
# ms.search.industry: 
ms.author: rschloma
ms.search.validFrom: 2017-11-20
ms.dyn365.ops.version: Talent July 2017 update

---
# Provision Talent

[!include [banner](includes/banner.md)]

This topic walks you through the process of provisioning a new production environment for Microsoft Dynamics 365 for Talent. This topic assumes that you've purchased Talent through a Cloud Solution Provider (CSP) or enterprise architecture (EA) agreement. If you have an existing Microsoft Dynamics 365 license that already includes the Talent service plan, and you can't complete the steps in this topic, contact Support.

To begin, the global administrator should sign in to [Microsoft Dynamics Lifecycle Services](https://lcs.dynamics.com) (LCS) and create a new Talent project. Unless a licensing issue prevents you from provisioning Talent, assistance from Support or Dynamics Service Engineering (DSE) representatives isn't required.

## Create an LCS project
To use LCS to manage your Talent environments, you must first create an LCS project.

1. Sign in to [LCS](https://lcs.dynamics.com/Logon/Index) by using the account that you used to subscribe to Talent.
2. Select the plus sign (**+**) to create a project.
3. Select **Microsoft Dynamics 365 for Talent** as the product name and product version.
4. Select the **Dynamics 365 for Talent** methodology.
5. Select **Create**.

For information about how to get started with Talent, see the **Talent** methodology that you created in your new project. After you've finished creating the project, complete the following procedure to provision your Talent environment.

## Provision a Talent project
After you've created an LCS project, you can provision Talent into an environment.

1. In your LCS project, select the **Talent App Management** tile.
2. Talent is always provisioned into a Microsoft PowerApps environment to enable PowerApps integration and extensibility. Read the “Selecting a PowerApps environment” section of this topic before you continue. If you don't already have a PowerApps environment, select Manage environments in LCS or navigateto the PowerApps Admin center. Then follow the steps to [Create a PowerApps environment](https://docs.microsoft.com/en-us/powerapps/administrator/create-environment).

    > [!NOTE]
    > To view existing environments or create new environments, the tenant admin who provisions Talent must be assigned to the PowerApps P2 license. If your organization doesn't have a PowerApps P2 license, you can get one from your CSP or from the [PowerApps pricing page](https://powerapps.microsoft.com/en-us/pricing/).

4. Select **Add**, and then select the environment to provision Talent into.
5. Select the ‘Include Demo Data’ option if you want your environment to include the same Demo data set used in the Talent Test Drive experience.  This is beneficial for long-term demo or training environments, and should never be used for production environments.  Note that you must choose this option upon initial deployment and can't update an existing deployment later.
6. Select **Yes** to agree to the terms and begin deployment.

    Your new environment appears in the list of environments in the navigation pane on the left. However, you can't start to use the environment until the deployment status is updated to **Deployed**. This process typically takes just a few minutes. If the provisioning process is unsuccessful, you must contact Support.

7. Select **Log on to Talent** to use your new environment.

> [!NOTE]
> If you haven't yet signed off on the final requirements, you can deploy a test instance of Talent in the project. You can then use this instance to test your solution until you sign off. If you use your new environment for testing, you must repeat this procedure to create a production environment.

> [!NOTE]
> Since only two LCS environments are allowed as part of the Talent subscription, you may also consider leveraging a free 60-day [Talent trial environment](https://dynamics.microsoft.com/en-us/talent/overview/). Although a trial environment is owned by the user who requested it, other users can be invited through the system administration experience for Core HR. Trial environments contain fictitious data that can be used to explore the program in a safe manner. They aren't intended to be used as production environments. Note that when a trial environment expires after 60 days, all the data that's in it is deleted and can't be recovered. You can sign up for a new trial environment after the existing environment expires.

## Select a PowerApps environment

The integration between Talent and the PowerApps environments lets you integrate and extend the use of Talent data using PowerApps tools. Understanding the purpose of PowerApps environments will not only help you build apps to extend Talent, but also can also help you select the correct environment when provisioning Talent. For information about PowerApps environments, including environment scope, environment access, and creating and choosing an environment, see [Announcing PowerApps environments](https://powerapps.microsoft.com/en-us/blog/powerapps-environments/). 

Use the following guidance when determining which PowerApps environment to deploy Talent into: 
1. In LCS, select Manage environments, or navigate directly to the PowerApps Admin center , where you can view existing environments and create new environments.
2. A single Talent environment is mapped to a single PowerApps environment.
3. A PowerApps environment “contains” the Talent application, along with the corresponding PowerApps, Flow, and CDS applications. If the PowerApps environment is deleted, so are the apps within it. When provisioning a Talent environment, either "Trial" or "Production" can be provisioned. Choose the type of environment based on how the environment will be used. 
4. Data integration and testing strategies should be considered, for example: Sandbox, UAT, Production. Therefore, we recommend that you consider the various implications for your deployment, because it isn't easy to change which Talent environment is mapped to a PowerApps environment later.
5. The following PowerApps environments cannot be used for Talent and will be filtered from the selection list within LCS:
 
   **Default Power Apps environments** Although each tenant is automatically provisioned with a default PowerApps environment, we don't recommend using them with Talent since all tenant users have access to the PowerApps environment and may unintentionally corrupt production data when testing and exploring with PowerApps or Flow integrations.
   
   <strong>Test Drive environments</strong> Environments with a name like ‘TestDrive – alias@domain’ are created with a 60-day expiration period and will expire after that time, causing your environment to be removed automatically.
   
   **Unsupported regions** Currently Talent is only supported in the following regions: United States, Europe, or Australia.
  
6. There is no specific action to take once you have determined the correct environment to use. Continue with the provisioning process. 
 
## Grant access to the environment
By default, the global administrator who created the environment has access to it. However, additional application users must be explicitly granted access. To grant access, you [add users](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/create-new-users) and [assign the appropriate roles to them](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/sysadmin/tasks/assign-users-security-roles) in the Core HR environment. The global administrator that deployed Talent must also launch both the Attract and Onboard applications to complete the initialization and enable access for other tenant users.  Until this happens, other users will not be able to access Attract and Onboard applications and will get access violation errors.

