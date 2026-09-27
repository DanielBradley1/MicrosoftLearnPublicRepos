<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-troubleshoot -->
<!-- Sitemap-Last-Modified: 2023-11-16 -->

# Common issues when enabling TLS 1.2

This article provides advice for common issues that occur when you enable TLS 1.2 support in Configuration Manager.

## Unsupported platforms

The following client platforms are supported by Configuration Manager but aren't supported in a TLS 1.2 environment:

- Apple OS X
- Windows devices managed with on-premises MDM

## Reports don't show in the console

If reports don't show in the Configuration Manager console, make sure to update the computer on which you're running the console. [Update the .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client#bkmk_net), and enable strong cryptography.

## FIPS security policy enabled

If you enable the FIPS security policy setting for either the client or a server, Secure Channel \(Schannel\) negotiation can cause them to use TLS 1.0. This behavior happens even if you disable the protocol in the registry.

To investigate, enable Secure Channel event logging, and then review Schannel events in the system log. For more information, see [Restrict the use of certain cryptographic algorithms and protocols in Schannel.dll](https://learn.microsoft.com/en-us/troubleshoot/windows-server/windows-security/restrict-cryptographic-algorithms-protocols-schannel).

## SQL Server communication failure

If SQL Server communication fails and returns an **SslSecurityError** error, verify the following settings:

- [Update .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server#bkmk_net), and enable strong cryptography on each machine
- [Update SQL Server](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server#bkmk_sql) on the host server
- [Update SQL Server client components](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server#bkmk_sql-client) on all systems that communicate with SQL. For example, the site servers, SMS provider, and site role servers.

## Configuration Manager client communication failures

If the Configuration Manager client doesn't communicate with site roles, verify that you [updated Windows](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client#bkmk_winhttp) to support TLS 1.2 for client-server communication by using WinHTTP. Common site roles include distribution points, management points, and state migration points.

## Reporting services point fails and returns an expected error

If the reporting services point doesn't configure reports, check the **SRSRP.log** for the following error entry:

`The underlying connection was closed:` `An expected error occurred on a receive.`

To resolve this issue, follow these steps:

1. [Update .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client#bkmk_net), and enable strong cryptography on all relevant computers.
2. After you install any updates, restart the SMS\_Executive service.

## Service connection point upload failures

If the service connection point doesn't upload data to SCCMConnectedService, [update the .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server#bkmk_net), and enable strong cryptography on each computer. After you make the changes, remember to restart the computers.

## Configuration Manager console displays Intune onboarding dialog box

If the Intune onboarding dialog box appears when the console tries to connect to the Microsoft Intune admin center, [update the .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client#bkmk_net), and enable strong cryptography on each computer. After you make the changes, remember to restart the computers.

## Configuration Manager console displays failure to sign in to Azure

When you try to create applications in Microsoft Entra ID, if the Azure Services onboarding dialog box immediately fails after you select **Sign in**, [update the .NET Framework](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server#bkmk_net), and enable strong cryptography. After you make the changes, remember to restart the computers.

## Configuration Manager cloud services and TLS 1.2

The Azure virtual machines used by the cloud management gateway support TLS 1.2. Supported client versions automatically use TLS 1.2.

The **SMSAdminui.log** may contain an error similar to the following example:

```Log
Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationException
Service returned error. Check InnerException for more details
at Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationContext.GetAADAuthResultObject
...
Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException
Service returned error. Check InnerException for more details
at Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext.RunAsyncTask
...
System.Net.WebException
The underlying connection was closed: An unexpected error occurred on a receive.
at System.Net.HttpWebRequest.GetResponse
```

In the System EventLog, SChannel EventID 36874 may be logged with the following description: `An TLS 1.2 connection request was received from a remote client application, but none of the cipher suites supported by the client application are supported by the server. The TLS connection request has failed.`

## Additional resources

- [Transport layer security \(TLS\) best practices with the .NET Framework](https://learn.microsoft.com/en-us/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)
- [KB 3135244: TLS 1.2 support for Microsoft SQL Server](https://support.microsoft.com/topic/kb3135244-tls-1-2-support-for-microsoft-sql-server-e4472ef8-90a9-13c1-e4d8-44aad198cdbe)
- [Cryptographic controls technical reference](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/cryptographic-controls-technical-reference)

## Next steps

- [Enable TLS 1.2 on clients](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client)
- [Enable TLS 1.2 on the site servers and remote site systems](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server)
