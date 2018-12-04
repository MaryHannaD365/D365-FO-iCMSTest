---
# required metadata

title: Deployment guidelines for cash registers for India
description: This topic is a deployment guide for the Retail localization for India.
author: 
manager: ralin
ms.date: 03/29/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: shylaw
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
ms.search.industry: Retail
ms.author: jiaqia
ms.search.scope: Retail
ms.search.validFrom: 2018-1-31
ms.dyn365.ops.version: 7.3.1

---
# Deployment guidelines for cash registers for India

[!include [banner](../includes/banner.md)]

This topic is a deployment guide that shows how to enable the requirements for Goods and Services Tax (GST) in the Microsoft Dynamics 365 for Retail localization for India. For more information about the Retail localization for India, see [GST integration for cash registers for India](./apac-ind-cash-registers.md).

This sample is part of the Retail software development kit (SDK). For information about how to install and use the Retail SDK, see the [Retail SDK documentation](../dev-itpro/retail-sdk/retail-sdk-overview.md).

This sample consists of extensions for the Commerce runtime (CRT). To run this sample, you must modify and build the CRT projects. We recommend that use you an unmodified Retail SDK to make the changes that are described in this topic. We also recommend that you use a source control system, such as Microsoft Visual Studio Online (VSO), where no files have been changed yet.

> [!NOTE] 
> Some steps in the procedures in this topic differ, depending on the version of Microsoft Dynamics 365 for Retail that you're using. For more information, see [What's new or changed in Dynamics 365 for Retail](../get-started/whats-new.md).

## Prerequisites

Make sure that the Visual C++ Redistributable Packages are present on the machine you are running Goods and Services Tax (GST) calculations on. It's Retail server for Cloud POS and MPOS online mode, MPOS machine itself for offline mode. You can get the packages from the following location: [Download the Visual C++ Redistributable Packages](https://www.microsoft.com/download/details.aspx?id=30679).

## Development environment

Follow these steps to set up a development environment so that you can test and extend the sample.

### The CRT extension components

The CRT extension components are included in the CRT samples. To complete the following procedures, open the CRT solution, **CommerceRuntimeSamples.sln**. You can find this solution under **RetailSdk\\SampleExtensions\\CommerceRuntime**.

#### Generic Tax Engine component

1. Find the **Runtime.Extensions.GenericTaxEngine** project, and build it.
2. Find the following files:

   - In the **Extensions.GenericTaxEngine\\bin\\Debug** folder:
    
       - Contoso.Commerce.Runtime.Extensions.GenericTaxEngine.dll
    
   - In the **Reference\\Newtonsoft.Json\\9.0.0.0** folder:

       - Newtonsoft.Json.dll

     # [Retail 7.3.1](#tab/retail-7-3-1)

     In the **Reference\\TaxEngine** folder:

     - Microsoft.Dynamics365.Tax.Core.dll
     - Microsoft.Dynamics365.Tax.DataAccessor.dll
     - Microsoft.Dynamics365.Tax.DataAccessFramework.dll
     - Microsoft.Dynamics365.Tax.DataModel.dll
     - Microsoft.Dynamics365.Tax.Metadata.dll
     - Microsoft.Dynamics365.LocalizationFramework.dll
     - Microsoft.Dynamics365.LocalizationFrameworkCore.dll
     - Microsoft.Dynamics365.ElectronicReportingMapping.dll
     - Microsoft.Dynamics365.XppSupportLayer.dll

     Find the following folders in the **Reference\\Z3** folder:

     - x86
     - x64

     # [Retail 7.3.2 and later](#tab/retail-7-3-2)

     In the **References\\Microsoft.Dynamics.AX.TaxEngine.7.3.42\\XppModule\\TaxEngine\\bin** folder:

     - Microsoft.Dynamics365.LocalizationFramework.dll
     - Microsoft.Dynamics365.Tax.Core.dll
     - Microsoft.Dynamics365.Tax.DataAccessFramework.dll
     - Microsoft.Dynamics365.Tax.DataAccessor.dll
     - Microsoft.Dynamics365.Tax.DataModel.dll
     - Microsoft.Dynamics365.Tax.Metadata.dll

     In the **References\\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\\XppModule\\ElectronicReporting\\bin** folder:

     - Microsoft.Dynamics365.ElectronicReportingMapping.dll
     - Microsoft.Dynamics365.LocalizationFrameworkCore.dll
     - Microsoft.Dynamics365.XppSupportLayer.dll

     Find the following folders in the **Reference\\Z3.4.5.0\\lib\\net40** folder:

     - x86
     - x64

    ---

3. Copy the 11 assembly files, and both x64 and x86 folders to the CRT extensions folder:

    - **Retail Server:** Copy the assemblies to the **\\bin\\ext** folder under the Microsoft Internet Information Services (IIS) Retail server site location.
    - **Local CRT on Modern POS:** Copy the assemblies to the **\\ext** folder under the local CRT client broker location.

4. Find the extensions configuration file for CRT:

    - **Retail Server:** The file is named **commerceruntime.ext.config**, and it's in the **bin\\ext** folder under the IIS Retail server site location.
    - **Local CRT on Modern POS:** The file is named **CommerceRuntime.MPOSOffline.Ext.config**, and it's under the local CRT client broker location.

5. Register the CRT change in the extensions configuration file.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.GenericTaxEngine" />
    ```

    > [!WARNING]
    > Do **not** edit the commerceruntime.config and CommerceRuntime.MPOSOffline.config files. These files aren't intended for any customizations.

### Set up required parameters in Retail headquarters

For more information, see [GST integration for cash registers for India](./apac-ind-cash-registers.md).

## Production environment

Follow these steps to create deployable packages that contain Retail components, and to apply the packages in a production environment.

1. In the **commerceruntime.ext.config** and **CommerceRuntime.MPOSOffline.Ext.config** configuration files under the **RetailSdk\\Assets** folder, add the following lines to the **composition** section.

    ``` xml
    <add source="assembly" value="Contoso.Commerce.Runtime.Extensions.GenericTaxEngine" />
    ```

2. In the **Customization.settings** package customization configuration file under the **RetailSdk\\BuildTools** folder, add the following lines to the **ItemGroup** section to include the CRT extensions in deployable packages.

    # [Retail 7.3.1](#tab/retail-7-3-1)

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.Extensions.GenericTaxEngine.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.Core.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.Metadata.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataAccessor.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataAccessFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.Tax.DataModel.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.LocalizationFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.LocalizationFrameworkCore.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.ElectronicReportingMapping.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\TaxEngine\Microsoft.Dynamics365.XppSupportLayer.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Newtonsoft.Json\9.0.0.0\Newtonsoft.Json.dll" />
    ```

    # [Retail 7.3.2 and later](#tab/retail-7-3-2)

    ``` xml
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Contoso.Commerce.Runtime.Extensions.GenericTaxEngine.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Core.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.Metadata.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessor.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataAccessFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.Tax.DataModel.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.TaxEngine.7.3.42\XppModule\TaxEngine\bin\Microsoft.Dynamics365.LocalizationFramework.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.LocalizationFrameworkCore.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.ElectronicReportingMapping.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Microsoft.Dynamics.AX.ElectronicReporting.7.3.42\XppModule\ElectronicReporting\bin\Microsoft.Dynamics365.XppSupportLayer.dll" />
    <ISV_CommerceRuntime_CustomizableFile Include="$(SdkReferencesPath)\Newtonsoft.Json\9.0.0.0\Newtonsoft.Json.dll" />
    ```

3. Modify the following files to include the Z3 libraries in deployable packages.:

   - Packages\\ModernPOS.Sdk\\Sdk.ModernPOSSetup.csproj
   - Packages\\ModernPOSOffline.Sdk\\Sdk.ModernPOSSetupOffline.csproj
   - Packages\\RetailServer\\Sdk.RetailServerSetup.proj

     # [Retail 7.3.1](#tab/retail-7-3-1)

     Add the following lines to the **ItemGroup** section

     ```xml
       <_bin_ext_Z3_x86_File Include="..\..\References\Z3\x86\*.*" />
       <_bin_ext_Z3_x64_File Include="..\..\References\Z3\x64\*.*" />
     ```

     # [Retail 7.3.2 and later](#tab/retail-7-3-2)

     ```xml
       <_bin_ext_Z3_x86_File Include="..\..\Reference\Z3.4.5.0\lib\net40\x86\*.*" />
       <_bin_ext_Z3_x64_File Include="..\..\Reference\Z3.4.5.0\lib\net40\x64\*.*" />
     ```

    ---

    For **Sdk.ModernPOSSetup.csproj** and **Sdk.ModernPOSSetupOffline.csproj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section

        ```xml
            <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x86" SkipUnchangedFiles="true" />
            <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\CustomizedFiles\ClientBroker\ext\x64" SkipUnchangedFiles="true" />
        ```

    For **Sdk.RetailServerSetup.proj** also add the following lines to the **\<Target Name="CopyPackageFiles"\>** section

        ```xml
            <Copy SourceFiles="@(_bin_ext_Z3_x86_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x86" SkipUnchangedFiles="true" />
            <Copy SourceFiles="@(_bin_ext_Z3_x64_File)" DestinationFolder="$(OutputPath)content.folder\RetailServer\Code\bin\ext\x64" SkipUnchangedFiles="true" />
        ```

4. Run **msbuild** for the whole Retail SDK to create deployable packages.

5. Apply the packages via Microsoft Dynamics Lifecycle Services (LCS) or manually. For more information, see [Retail SDK packaging](../dev-itpro/retail-sdk/retail-sdk-packaging.md).
