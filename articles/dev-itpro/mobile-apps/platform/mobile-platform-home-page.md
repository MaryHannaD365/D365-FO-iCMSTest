---
# required metadata

title: Mobile platform home page
description: The mobile platform lets you create mobile apps for your workspaces.
author: RobinARH
manager: AnnBe
ms.date: 08/30/2018
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
ms.custom: 255544
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9

---

# Mobile platform home page

[!include [banner](../../includes/banner.md)]

By using mobile apps, you can reuse business logic and modeling from Microsoft Dynamics 365 for Finance and Operations. Mobile apps enable rich offline and mobile interactions, and provide an easy-to-use designer experience. Developers can create simplified forms in Microsoft Visual Studio and then design mobile apps that expose this functionality. The mobile platform makes it easy to change the forms and mobile app definitions to include customizations that are made to Finance and Operations. 

## Get started

+ [Getting started](mobile-platform-getting-started.md) 
+ [Architecture](mobile-platform-architecture.md) 
+ [Page design guidelines](page-design-guidelines.md)
+ [Action design guidelines](action-design-guidelines.md)
+ [Form design requirements](form-design-requirements.md)

Check out the following series of how-to videos that show how to create a mobile app.

+ [Tutorial 1: Building the sales order page](https://youtu.be/PdegfBxifl8)
+ [Tutorial 2: Building the sales order details page](https://youtu.be/mF-vlbnRte0)
+ [Tutorial 3: Building the create new sales order action](https://youtu.be/VYw9oTv9t3o)
+ [Tutorial 4: Adding a lookup to the create new sales order action](https://youtu.be/eNJKd0IYmZk)
+ [Tutorial 5: Adding a lookup and hiding pages using mobile business logic](https://youtu.be/kIJKk9J8FvI)

## Common configurations
These topics describe some common customizations that you can add to your mobile app.

+ [Localize mobile workspaces](scenarios/localize-workspaces-on-server.md)
+ [Help secure mobile workspaces](scenarios/secure-mobile-workspace.md)
+ [Set up clickable fields](scenarios/make-workspace-field-clickable.md)
+ [Set up mandatory fields through workspace classes](scenarios/make-field-mandatory.md)
+ [Display item counts in a field](scenarios/display-count-workspace.md)

## Client-side development

Client-side APIs are used in the business logic file, which provides an extensibility layer to the mobile workspace that allows for customization. Some things that you can access and influence through the client-side APIs include:
+ Metadata
+ Runtime control/page instances
+ Business data
+ Offline-first business behaviors
+ Layout and style

The process for client-side development is described in these topics:
+ [Client-side design APIs overview](scenarios/client-api-design-overview.md)
+ [Business logic events overview](business-logic-events-overview.md)
+ [Client APIs](client-apis/client-apis-reference.md)

You can download a sample business logic file (with a .js file name extension) for the Reservation management workspace. Go to [Dynamics365-for-Operations-mobile-FleetManagementSamples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples), open the **business_logic folder**, and locate the FM.js file

## Server-side development

Workspace attributes and classes are used to create, configure, and publish workspaces on the server. These server-side X++ APIs can be used instead of using the task recorder-based mechanism to build a workspace. Workspaces created using either mechanism can then be styled and augmented using the client-side APIs.

Server-side development is described in these topics:
+ [Workspace class overview](scenarios/mobile-workspace-configuration.md)
+ [Server APIs (X++)](mobile-workspace-server-apis.md)

You can download the sample project (with an .axpp file name extension) for the Fleet Management mobile app. Go to [Dynamics365-for-Operations-mobile-FleetManagementSamples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) and download the **FMMobileApp.axpp** file.

## Debugging during development

During development it can be useful to attach a debugger to get more detailed information and insight into what is happening in the background. A web debugger can be used with the client-side JavaScript logic and styling and the Visual Studio debugger can be used with the server-side X++ business logic.

### Debugging the client side 

#### Prerequisites
- Android device plus PC
- Azure-hosted development machine (so the mobile device can point to it)

#### Steps to debug the client side
1. On the web client that is exposed by the Azure-hosted development machine, ensure that there are mobile workspaces published for the Unified Operations app. For information about publishing a mobile workspace, see [Publish a mobile workspace](../publish-mobile-workspace.md).

2. Install the Android debug apk for the Unified Operations app on an Android device:
    - One time only, allow the installation of apk files -  Go to **Menu** > **Settings** > **Security** and then check **Unknown Sources** to allow the phone to install apps from sources other than the Google Play Store.
    - Uninstall the Unified Operations app - Ensure that any previous version of the Unified Operations app has been uninstalled.
    - Download the apk file - From the device’s browser, navigate to the latest [Unified Operations Android debug apk on Github](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples/blob/master/android-debug.apk) and click **Download** (or use [this direct link to the file](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples/raw/master/android-debug.apk)).
    - Install the Unified Operations apk file - Confirm install of the Unified Operations app via the apk file.
    - Run the debug Unified Operations app on the device and sign in.

3. Connect to the device from the debugging machine.

    - On the Azure-hosted development machine or a separate PC, follow Android developer instructions to [Get Started with Remote Debugging Android Devices](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/). You can also find a wide selection of instructional videos on YouTube by searching for [Chrome for Android remote debugging](https://www.youtube.com/results?search_query=chrome+for+android+remote+debugging). 
    
4. After you connect the debugger, find the active tab on your device. You may need to click **View more tabs** on Android. One of the tabs should look similar to `/www.index.html#/app/appList` or `/www.index.html#/app/app_landing`. 

    Expand the nodes to find the workspace JavaScript, such as **File** > (no domain) > **ExpenseMobile.js**. Click the JavaScript file to view it and add breakpoints.
    
    ![Expense management mobile workspace](./media/expense-management-mobile-workspace.png)
    
5. Reflect the mobile device on your desktop so that you can interact with it on the desktop screen. 

6. Go to through the desired workspace and forms.

7. If breakpoints are encountered, then the browser developer tools will allow you to control the flow of execution and see the values and parameters being passed. 

8. To change styling at runtime, use the elements tab to alter the styling. This will help you determine what elements JavaScript should target and how those elements should be styled.

9. If a needed change is identified, make those changes in JavaScript, and then push those changes into the environment.

10. If more changes or validation is needed, repeat the process.

### Debugging the server side

#### Prerequisites
- Azure-hosted development machine (so the mobile device can point to it)

#### Steps to debug the serverside
1. On the web client exposed by the Azure-hosted development machine, ensure that there are mobile workspaces published for the Unified Operations app. For information about publishing a mobile workspace, see [Publish a mobile workspace](../publish-mobile-workspace.md).

2. Open the Unified Operations app on your device, point to the Azure-hosted development machine, and sign in.

3. Open Visual Studio on the Azure-hosted development machine and attach the debugger to the w3wp process.

4. After you connect the debugger, find the desired business logic, and insert breakpoints as needed.

5. Either use the app on your device as usual, or reflect the mobile device on your desktop so you can interact with it on the desktop screen.

6. Navigate through the desired workspace and forms.

7. If breakpoints are encountered, then Visual Studio will allow you to control the flow of execution and see the values and parameters being passed. 

8. If a needed change is identified, make those changes in X++, and push those changes into the environment.

9. If more changes or validation is needed, repeat the process.

## Change needed for ADFS to support Mobile Client in on-premises environments 
If ADFS is in use on the domain and the environment is on-premises, then **ADFS must be configured to provide a regular forms-based authentication screen** instead of using Windows Integrated Authentication (WIA). The Microsoft Dynamics Unified Operations apps for iOS and Android require the regular forms-based authentication screen. ADFS should be configured to only provide WIA for browser clients (use cases). For more information, see [Configure intranet forms based authentication for devices that do not support wia](https://docs.microsoft.com/en-us/windows-server/identity/ad-fs/operations/configure-intranet-forms-based-authentication-for-devices-that-do-not-support-wia)

## Troubleshooting
### The Mobile Client app is not working correctly on particular devices
Sometimes the cache associated with the Unified Operations app becomes corrupt or obsolete and needs to be cleared. Unfortunately, the only way to clear the data associated with the app is to uninstall the app.
To completely uninstall the app, don't use the "long-press wiggle and x on the app icon" method. Instead, completely uninstall the app by navigating to **Settings** > **General** > **iPhone Storage** > **Dynamics 365 Unified Operations**, and then click **Delete App**. After 10-15 seconds, the app can be reinstalled.

### I can't figure out how to build or change something in my Mobile Client content
There are many resources that you can leverage to figure out how to build or change content for the Mobile Client.
- Review the documentation provided in the Dynamics 365 for Finance and Operations Help system.
- Review the [Fleet Management Samples](https://github.com/Microsoft/Dynamics365-for-Operations-mobile-FleetManagementSamples) for examples.
- Publish and review the Expense Management workspace, and other standard workspaces, for examples. Demo data for the USSI company is useful when using the Expense Management workspace. The forms and X++ code that make up the Expense Management workspace can be found in the Application Explorer by searching for the "ExpenseMobile" prefix.
- Leverage the [Dynamics Community forums for Finance and Operations (AX)](https://community.dynamics.com/ax/f/33) by searching for answers and asking questions when needed.
