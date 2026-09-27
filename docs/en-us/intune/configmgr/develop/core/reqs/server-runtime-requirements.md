<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Server Runtime Requirements

Microsoft Configuration Manager server applications that are developed by using the Configuration Manager SDK, have the following runtime requirements.

## Managed Code

- A supported version of Windows Server as defined in [Supported operating systems for Configuration Manager site system servers](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers). For more information, see [General Requirements](#general-requirements).
- Installed Configuration Manager site server
- Microsoft.ConfigurationManagement.ManagementProvider .NET Framework assembly
- Microsoft .NET Framework version 4

## Configuration Manager Console User Interface Extension

Programming Configuration Manager console extensions has the following requirements:

- Installed Configuration Manager site server
- Installed Configuration Manager console
- .NET Framework 4.0

  For more information, see [About console extensions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension).

## VBScript

- Installed Configuration Manager site server
- Windows Script Host

## Windows 64-Bit Support

A 32-bit compiled application that uses Configuration Manager SDK interfaces to access Configuration Manager client or Configuration Manager server functionality works when it runs in 32-bit emulation on a 64-bit Windows operating system. However, a 64-bit compiled application that uses Configuration Manager SDK interfaces that access 32-bit Configuration Manager client or Configuration Manager server functionality does not work. Similarly, Configuration Manager SDK scripts do not work when the scripting host is a native 64-bit application. A Configuration Manager SDK script does work if it is called from within a 32-bit scripting host.

## General Requirements

Important

For more information about general Configuration Manager requirements, see [Supported configurations for Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).

## See Also

[About console extensions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension) [Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements) [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements)
