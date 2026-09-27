<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/configuration-manager-sdk-libraries-and-header-files -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager SDK libraries

In Configuration Manager, when you write unmanaged applications, you might have to include one or more of the following libraries. Use COM Interoperability to access COM objects from .NET Framework applications.

| Library | Description |
| --- | --- |
| ismifcom.dll | Contains a class wrapper for the install status MIF functions. Visual Basic and scripting programmers use this ActiveX control to create a status MIF file.  <br>  <br>Visual Basic users must select the ISMIFCOM 1.0 Type Library project reference. Scripting users create this object by using "ISMIFCOM.InstallStatusMIF". |
| Microsoft.ConfigurationManager.Messaging.dll | Contains A .NET assembly encapsulating the client SDK that has an object model and transport for communicating with Configuration Manager site server roles such as the management point. |
| smsmsgapi.dll | Contains management point interface libraries. |
| smsrsgen.dll | Contains the Discovery Data Record functions. This DLL must exist in the directory from where you start your application. |
| smsrsgenctl.dll | Contains a class wrapper for the Discovery Data Record Functions. Visual Basic and scripting programmers use this control to create discovery data records. |

Note

The library files are available as [NuGet packages](https://www.nuget.org/profiles/ConfigurationManagerTeam).

For more information about general Configuration Manager requirements, see [Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).
