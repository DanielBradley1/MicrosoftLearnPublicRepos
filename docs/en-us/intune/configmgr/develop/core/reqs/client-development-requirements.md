<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Client Development Requirements

The Configuration Manager client can be programmed by using the following programming languages.

## Managed Code

If you are programming the Configuration Manager client by using managed code, you use the System.Management namespace and, where applicable, you use COM Interoperability to access the Configuration Manager automation objects.

### NET Framework

You should have version 4.0 of the Microsoft .NET Framework installed on the development computer and on the computers you want to deploy your .NET Framework application to. To download the .NET Framework redistributable package, see [Download .NET Framework](https://dotnet.microsoft.com/download/dotnet-framework). It is also installed as part of Visual Studio.

## VBScript

You can use VBScript to access the Configuration Manager client WMI namespaces. The client also has a number of COM automation objects that you can use.

For more information about scripting with WMI, see [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page).

## C++

C++ examples are provided for some Configuration Manager technologies where C++ is the most appropriate development language. In most cases, C++ developers should use the VBScript samples as a guide. For more information about using WMI with C++, see [Creating a WMI Application Using C++](https://learn.microsoft.com/en-us/windows/win32/wmisdk/creating-a-wmi-application-using-c-).

## Other Languages

For languages that are not based on .NET Framework, use the VBScript samples as a starting point for accessing Configuration Manager through WMI.

Important

For more information about general Configuration Manager requirements, see [Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).

## See Also

[Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements) [Configuration Manager SDK Libraries and Header Files](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files)
