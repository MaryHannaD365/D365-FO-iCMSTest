---
# required metadata

title: Develop and customize 
description: This topic provides links to topics about development.
author: RobinARH
manager: AnnBe
ms.date: 04/27/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.assetid: 06e26767-6056-4755-b47e-0bda71833581
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Develop and customize 

[!include [banner](../includes/banner.md)]

This topic provides links to topics about development.

## Overview

Microsoft Dynamics 365 for Finance and Operations represents the next-generation enterprise resource planning (ERP) offering from Microsoft. It is designed to enable the entire ERP application suite as a cloud-based solution, for both public and private clouds, as well as on-premises. It leverages the speed, simplicity, and cost-effectiveness of working in the cloud, while building on the latest technology from Microsoft. This release introduces significant changes to the development experience. These changes include:

- Development tools that are decoupled from any running environment. You develop against local, XML-based files, not the online database.
- Microsoft Visual Studio is the development environment. The Visual Studio environment is customized to provide you with a smooth and familiar experience.
- The X++ compiler generates Common Intermediate Language (CIL) for all features. CIL is the same intermediate language used by other .NET-based (managed) languages, such as the C\# programming language.
- You can leverage the browser-based client and the design patterns for forms to provide an improved end-user experience.
- The Application Lifecycle Model (ALM) supports build automation, test automation, and deployment of models to the cloud.

## Architecture
-   [Application stack and server architecture](application-stack-server-architecture.md)

## Getting started
-   [Get an evaluation copy](get-evaluation-copy.md)
-   [LCS101 – Sign up for a subscription](sign-up-preview-subscription.md)
-   [Access development instances](../dev-tools/access-instances.md)
-   [Development system requirements](development-system-requirements.md)
-   [Deprecated features](../migration-upgrade/deprecated-features.md)
-   [Deprecated API’s](../migration-upgrade/deprecated-apis.md)
-   [Rename and reboot machines for Azure DevOps](../migration-upgrade/vso-machine-renaming.md)
-   [Introduction to Azure DevOps (Video)](http://channel9.msdn.com/Events/Build/2014/2-575)
<!-- [Learn about packages, models and Visual Studio (Office Mix)](https://mix.office.com/watch/ies6lyit6773)-->
<!-- [Development tools performance tips (Office Mix)](https://mix.office.com/watch/rnp6ng9wu8kx)-->
<!-- [Feedback and support (Office Mix)](https://mix.office.com/watch/92azzna59jj6)-->

## Fleet Management
-   [Fleet Management sample](introduction-fleet-management-sample.md)
-   [INT101: Introduction to Fleet Management](fleet-management-sample.md)

## Development tools
### Tutorials

-   [Introduction to Visual Studio development](introduction-visual-studio.md)
-   [Create a simple data model](create-data-model-elements.md)
-   [Building and debugging a project](build-debug-project.md)
-   [Version control, metadata search, navigation, and other features](version-control-metadata-navigation.md)

### Tools, models, and VMs

-   [Development tools](development-tools-overview.md)
<!-- [Introduction to the development environment (Office Mix)](https://mix.office.com/watch/1tz7194y62m3s)-->
-   [Application Explorer](application-explorer.md)
-   [Projects](projects.md)
-   [Element designers](element-designers.md)
-   [Element usage](element-usage.md)
-   [Models](models.md)
-   [Build operations](build-operations.md)
-   [Visual Studio code editor](code-editor.md)
-   [Developer tools add-ins](developer-tools-add-ins.md)
-   [Distribution of models: How to export and import a model](models-export-import.md)
-   [Metadata search in Visual Studio](metadata-search-visual-studio.md)
-   [Resolve conflicts using Visual Studio](https://mix.office.com/watch/1rl75ei2cs6d7)
-   [Enable a new user account to develop on a development VM](enable-development-machine.md)
-   [Updating the Visual Studio development tools](update-development-tools.md)
-   [Virtual machines that don't allow administrator access FAQ](../sysadmin/VMs-no-admin-access.md)
<!--  [Configure version control with Azure DevOps (Office Mix)](https://mix.office.com/watch/1ftubtqzp3xxl)-->

## X++ programming language
### Tutorials

-   [New X++ and debugger features](new-x-debugger-features.md)
-   [C\# and X++ interoperability and LINQ](write-business-logic.md)

### Language support

-   [Programming language support](programming-language-support.md)
-   [EventHandlerResult classes in request or response scenarios](event-handler-result-class.md)
-   [Debugging X++ code](debug-xpp.md)
-   [LINQ provider for use in C\#](linq-provider-c.md)
-   [Authoring best practice rules](author-best-practice-rules.md)

### Reference

-   [X++ language reference](../dev-ref/xpp-language-reference.md)

## Customize with extensions and overlayering
- [Extensibility home page](../extensibility/extensibility-home-page.md)
- [Customize App Suite reports using extensions](../analytics/customize-app-suite-reports-with-extensions.md)

## Code migration
- [Code migration and upgrade home page](../migration-upgrade/code-migration-home-page.md)

## Move packages between environments
- [Create and apply a deployable package](../deployment/create-apply-deployable-package.md)

## Performance
- [Take a trace with the Trace Parser and analyze it](../perf-test/trace-trace-tutorial.md)
- [Introduction to the PerfSDK and multiuser testing with Visual Studio Online](../perf-test/perfsdk-tutorial.md)
- [Using the desktop version of trace parser to diagnose problems and analyze performance issues](../perf-test/trace-parser.md)
- [Performance timer](../perf-test/performance-timer.md)
<!-- [Expanding data with the Data Expansion tool (Office Mix)](https://mix.office.com/watch/11cet1u4nmn64)
- [Analyzing performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw)
- [The performance timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3)
- [Using Task Recorder to create a single user performance test (Office Mix)](https://mix.office.com/watch/qtdlasy2rcf3)
- [The performance timer and other tools (Office Mix)](https://mix.office.com/watch/ij5cqidra5q3)
- [Analyzing performance Issues with Trace Parser (Office Mix)](https://mix.office.com/watch/17d76cll0npyw)-->

## User interface concepts
The client is an HTML web client that runs in all major browsers. For information about developing and customizing the user interface, see the [User interface development home page](../user-interface/user-interface-development-home-page.md).

## Analytics
- [Analytics](../analytics/analytics.md)

## Reporting services
- [Electronic reporting overview](../analytics/general-electronic-reporting.md)
<!-- [Introduction to Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/wdl1dquy2tve)
- [Demo of Advanced Reporting Solutions (Office Mix)](https://mix.office.com/watch/1hkvtnc8sc7l6)-->

## Data entities and OData
- [Data entities home page](../data-entities/data-entities.md)
- [OData](../data-entities/odata.md)

## Testing support in Visual Studio
- [Testing and validation](../perf-test/testing-validation.md)
- [Support for testing in Visual Studio](../perf-test/testing-support.md)
- [Developer topology deployment with continuous build and test automation](../perf-test/continuous-build-test-automation.md)
- [Task Recorder](../user-interface/task-recorder.md)

## Office integration
- [Office integration](../office-integration/office-integration.md)

## Intelligence
- [Intelligence](../analytics/bi-reporting-home-page.md)
<!-- [Overview of aggregate data (Office Mix)](https://mix.office.com/watch/16yvvnw45kzhf)-->

## Mobile platform
- [Mobile platform home page](../mobile-apps/platform/mobile-platform-home-page.md)

## Global finance management
- [Financials development home page](../financial/financial-dev-home-page.md)

## Licensing
- [ISV licensing](isv-licensing.md)

## Supply chain management
- [Gantt development guide](../user-interface/gantt-development-guide.md)
- [Create a new transportation management engine](../../supply-chain/transportation/create-new-transportation-management-engine.md)

## Additional resources
[Insider tips on development](https://community.dynamics.com/ax/b/newdynamicsax)



