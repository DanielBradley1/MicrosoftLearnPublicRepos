<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Server Development Requirements

In Configuration Manager, the SMS Provider and associated technologies can be programmed by using the following programming languages.

## Managed Code

The Configuration Manager SDK provides Microsoft .NET Framework libraries for accessing the SMS Provider and also for extending the Configuration Manager console.

Note

You can also use the System.Management namespace for accessing the SMS Provider, but this approach is not documented in the Configuration Manager SDK.

Programming the SMS Provider with managed code has the following requirements:

- Installed Configuration Manager site server
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly.
- Microsoft Visual Studio
- Microsoft .NET Framework version 4

### NET Framework

You should have version 4 of the .NET Framework installed on the development computer and on the computers you want to deploy your .NET Framework application to. To download the .NET Framework redistributable package, see [Download .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework). It is also installed as part of Visual Studio.

## Configuration Manager Console User Interface Extension

Programming Configuration Manager console extensions has the following requirements:

- Installed Configuration Manager site server
- Installed Configuration Manager console
- Microsoft Visual Studio
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly.
- Microsoft .NET Framework 4

  For more information, see [About console extensions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension).

  For specific information about deploying Configuration Manager console extensions, see [Configuration Manager Console Extension Deployment](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-extension-deployment)

## VBScript

You can use Windows Management Instrumentation \(WMI\) to access the SMS Provider.

The scripting samples are provided in VBScript and use WMI to access Configuration Manager. For more information, see [Objects overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-objects-overview).

Programming the SMS Provider with VBScript has the following requirements:

- Installed Configuration Manager site server
- Windows Script Host

  For more information about scripting with WMI, see [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page).

## C++

C++ examples are provided for some Configuration Manager technologies where C++ is the most appropriate development language. In most cases, C++ developers should use the VBScript samples as a guide. For more information about using WMI with C++, see [Creating a WMI Application Using C++](https://learn.microsoft.com/en-us/windows/win32/wmisdk/creating-a-wmi-application-using-c-).

## Other Languages

For languages that are not based on the .NET Framework, use the VBScript samples as a starting point for accessing Configuration Manager through WMI.

Important

For more information about general Configuration Manager requirements, see [Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).

## See Also

[Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements) [Configuration Manager SDK Libraries and Header Files](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files)
