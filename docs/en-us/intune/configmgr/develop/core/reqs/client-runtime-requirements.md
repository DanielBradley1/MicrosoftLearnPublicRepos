<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-runtime-requirements -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Client Runtime Requirements

Applications that run on Microsoft Configuration Manager clients have the following runtime requirements.

## Managed Code

- Configuration Manager client
- Microsoft .NET Framework version 4

## VBScript

- Configuration Manager client
- Windows Script Host

## Windows 64-Bit Support

A 32-bit compiled application that uses Configuration Manager SDK interfaces to access Configuration Manager client or Configuration Manager server functionality works when it runs in 32-bit emulation on a 64-bit Windows operating system. However, a 64-bit compiled application that uses Configuration Manager SDK interfaces that access 32-bit Configuration Manager client or Configuration Manager server functionality does not work. Similarly, Configuration Manager SDK scripts do not work when the scripting host is a native 64-bit application. A Configuration Manager SDK script does work if it is called from within a 32-bit scripting host.

The Configuration Manager client has a native 64-bit version that is installed automatically on Windows 64-bit operating systems. Applications that relied on the 32-bit interfaces to be present may need to be re-compiled in a native 64-bit environment to interact with the Configuration Manager client APIs.

## General Requirements

For more information about Configuration Manager client requirements, see [Supported configurations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/supported-configurations).

## See Also

[Configuration Manager Client Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/client-development-requirements) [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements) [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements)
