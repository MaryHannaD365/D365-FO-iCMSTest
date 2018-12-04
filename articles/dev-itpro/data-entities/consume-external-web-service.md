---
# required metadata

title: Consume external web services in Finance and Operations
description: This topic describes how to consume external web services in Microsoft Dynamics 365 for Finance and Operations.
author: Sunil-Garg
manager: AnnBe
ms.date: 11/10/2017
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
ms.custom: 21311
ms.assetid: 5ff7fd93-1bb8-4883-9cca-c8c42ddc1746
ms.search.region: Global
# ms.search.industry: 
ms.author: sunilg
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Consume external web services in Finance and Operations

[!include [banner](../includes/banner.md)]

You can consume web services by adding new class libraries to Microsoft Dynamics 365 for Finance and Operations. In Microsoft Dynamics AX 2012, you could consume web services from X++ code by adding Microsoft Visual Studio projects as a reference and by using **Aif::CreateServiceClient**. This scenario is supported, but the steps have changed. Application Integration Framework (AIF) is no longer supported.

The following steps show how to consume an external StockQuote service from X++.

1. Create a new Class Library project in Visual Studio, and name it **ExternalServiceLibrary.csproj**.
2. In the Visual Studio project, add a service reference to the external web service: `http://www.webservicex.net/stockquote.asmx`.
3. Create a new static class, and wrap the StockQuote service operation as shown in the following example.

    ```
    public static string GetQuote(string s)
    {
        var binding = new System.ServiceModel.BasicHttpBinding();
        var endpointAddress = new EndpointAddress("http://www.webservicex.net/stockquote.asmx");
        ServiceLibrary.QuoteReference.StockQuoteSoapClient client = new ServiceLibrary.QuoteReference.StockQuoteSoapClient(binding, endpointAddress);

        //GetQuote is the operation on the StockQuote service
        return client.GetQuote("MSFT");
    }
    ```

4. Build the project. The binary ExternalServiceLibrary.dll is created.
5. Create a new Dynamics project in Visual Studio.
6. Add **ExternalServiceLibrary.dll** as a reference.
7. In the X++ class, you can use the external web services that were referenced in ExternalesrviceLibrary.dll.

    ```
    public static void main(Args _args)
    {
        info(ServiceLibrary.StockQuoteClass::GetQuote("MSFT"));
    }
    ```
