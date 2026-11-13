<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/release-notes -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# Release notes for Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

With Configuration Manager, product release notes are limited to urgent issues. These issues aren't yet fixed in the product, or detailed in a [troubleshooting article](https://learn.microsoft.com/en-us/troubleshoot/mem/configmgr/welcome-configuration-manager).

Feature-specific documentation includes information about known issues that affect core scenarios.

This article contains release notes for the current branch of Configuration Manager. For information on the technical preview branch, see [Technical Preview](https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/technical-preview).

For information about the new features introduced with different versions, see the following articles:

- [What's new in version 2609](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-version-2609)
- [What's new in version 2603](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2603)
- [What's new in version 2509](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2509)

Tip

You can use RSS to be notified when this page is updated. For more information, see [How to use the docs](https://learn.microsoft.com/en-us/intune/fundamentals/use-docs#notifications).

## Set up and upgrade

### ODBC driver version 18.7.1.1 can block site configuration before updating to 2609

*Applies to: upgrades to version 2609*

Microsoft ODBC Driver for SQL Server version [18.7.1.1](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows#187) has a known issue with Configuration Manager version 2603 and earlier that can block site configuration.

To avoid this issue, don't install ODBC driver version 18.7.1.1 before updating Configuration Manager. Use ODBC driver version [18.6.2.1](https://learn.microsoft.com/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows#186), the validated version shipped with Configuration Manager 2609, for the update. Complete the Configuration Manager update to version 2609 before you install ODBC driver version 18.7.1.1.

For more information, see [ODBC driver for SQL Server](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Configuration Manager performance counters are missing on Windows Server 2025

*Applies to: primary site servers and management points running Windows Server 2025*

On Windows Server 2025, Configuration Manager performance counter registration can fail, leaving the counters unavailable in Performance Monitor. This issue can occur after a clean installation of Windows Server 2025 or an in-place upgrade from Windows Server 2022.

**Perfsetup.log** records errors similar to the following:

```text
Error: InstallSMSObjectAndCounterKeySettingsIntoRegistry() could not get the "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SMS_SOFTWARE_INVENTORY_PROCESSOR\Performance" registry key; error = 6 (0x6).
```

Perfsetup can also exit with code `1000`. The affected component name in the registry path can vary.

To resolve this issue, install the [update rollup for Configuration Manager version 2603 \(KB39169655\)](https://learn.microsoft.com/en-us/intune/configmgr/hotfix/2603/39169655) or update to Configuration Manager version 2609, which also includes this fix.

## Client authentication and registration

### Microsoft Entra token validation fails when the management point can't access the internet

*Applies to: version 2603 and later*

Starting in version 2603, the management point uses Microsoft Identity Service Essentials \(MISE\) for Microsoft Entra token validation and requires internet access. This requirement affects sites configured to support Microsoft Entra joined users and devices when clients authenticate using Microsoft Entra tokens, typically through a cloud management gateway \(CMG\). Environments that only use on-premises Active Directory authentication without Microsoft Entra integration aren't affected.

If the management point can't reach the required endpoints, **CCM\_STS\_ManagedBase.log** on the management point records a `MiseAuthenticationTicketProviderException` with an underlying network error, for example:

```text
Microsoft.Identity.ServiceEssentials.Exceptions.MiseAuthenticationTicketProviderException: MISE12034: AuthenticationTicketProvider Name:AuthenticationTicketProvider
System.Net.Sockets.SocketException: No connection could be made because the target machine actively refused it
```

Important

The `MISE12034` exception can also occur for other reasons. Before applying this resolution, verify that the underlying exception indicates a network connectivity problem, such as a `SocketException`, `HttpRequestException`, or connection timeout.

To resolve this issue, allow the management point server to access the following Microsoft Entra authentication endpoints through the proxy and firewall in the Local System context:

- `https://login.microsoftonline.com`
- `https://sts.windows.net`

If the management point uses a proxy, configure it in the Local System context. In version 2603, the proxy set in the site system properties and a WinHTTP-only proxy \(`netsh winhttp set proxy`\) aren't used for this validation path.

For configuration steps and the full list of required endpoints, see [Management point proxy configuration](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support#management-point) and [Management point internet access requirements](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/internet-endpoints#management-point).

### Bulk registration token verification fails after installing the version 2603 update rollup

*Applies to: version 2603 with update rollup KB39169655 installed*

After you install the [update rollup for Configuration Manager version 2603 \(KB39169655\)](https://learn.microsoft.com/en-us/intune/configmgr/hotfix/2603/39169655), bulk registration token verification fails on the management point for devices that aren't Microsoft Entra joined and connect through a cloud management gateway \(CMG\). Affected devices can't complete bulk registration through the CMG to obtain their individual Configuration Manager-issued client authentication tokens. Other CMG communication scenarios for these devices may also be affected.

This issue doesn't affect devices that use Microsoft Entra authentication or version 2603 sites that haven't installed KB39169655.

On the management point, errors similar to the following are recorded in `<MP_InstallDir>\Logs\CCM_STS.log`:

```text
ProcessRequest - Start
Incoming request URL: https://<management-point>/CCM_STS
Validated PreAuth SelfProve token. UniqueId: <client-id>. ClientKey: <public-key>
ProcessRequest - Exception: System.IO.FileLoadException:
Could not load file or assembly
'mpisapiclr, Version=5.0.9146.1045, Culture=neutral,
PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
The located assembly's manifest definition does not match the assembly reference.
(Exception from HRESULT: 0x80131040)
```

To resolve this issue, install [KB40345593](https://learn.microsoft.com/en-us/intune/configmgr/hotfix/2603/40345593), which is available in **Updates and Servicing** after you install KB39169655. This update requires a [site reset](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/modify-your-infrastructure#bkmk_reset) after installation, but doesn't require a computer restart.

## Collection management

### Collections based on Active Directory group membership lose members after upgrading to version 2609

*Applies to: version 2609*

After you upgrade to Configuration Manager version 2609, a full [Microsoft Entra user group discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-discovery-methods#bkmk_azuregroupdisco) cycle might remove Active Directory user-group relationships from the Configuration Manager database. User collections with query-based membership rules that depend on Active Directory group membership might lose some or all members after collection evaluation. Deployments targeted to these collections might no longer reach the intended users.

To prevent further occurrences, disable [Microsoft Entra user group discovery](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configure-discovery-methods#bkmk_azuregroupdisco). Disabling discovery doesn't restore user-group relationships that have already been removed.

## Software updates

### Devices continue scanning Windows Update after moving the update workload back to Configuration Manager

*Applies to: version 2503 with update rollup KB32851084 and KB36495448 installed, version 2509 with KB36495448 installed, and later releases that inherit this behavior*

After you move the **Windows Update policies** co-management workload from Intune back to Configuration Manager, devices might continue scanning Windows Update or Microsoft Update instead of WSUS, even after a machine policy cycle completes.

Starting with [KB36495448](https://learn.microsoft.com/en-us/intune/configmgr/hotfix/2509/36495448), the Configuration Manager client no longer sets or removes Windows Update scan source policies. Moving the workload slider doesn't automatically remove the Windows Update client policy state previously configured by Intune. This state can persist on the device after the Intune policy assignment is removed.

To address this issue, review the effective scan source for each update category and explicitly manage scan source policies through Group Policy or Intune. As a best practice, remove or reassign the device's Intune Windows Update client policy assignment before moving the workload back. For the cleanup procedure and alternative policy configuration, see [Moving the workload back to Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/integrate-windows-update-client-policies#moving-the-workload-back-to-configuration-manager).

### Reset default value of superseding age in months for software updates

*Applies to: version 2303*

Removing SUP role in Admin Console doesn't reset the superseding age property in WMI. As a result, while reconfiguring the role, the previously configured value is shown in the configuration window. This property needs to be reset to default value on role removal. For more information, see [supersedence rules for installing a software update point.](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/install-a-software-update-point)

## Cloud services

### CMG update to version 2609 fails when Azure permissions or resource provider registration are missing

*Applies to: version 2609 updates with an existing cloud management gateway*

Starting in version 2609, Configuration Manager automatically disables shared-key access for cloud management gateway \(CMG\) storage. Existing CMGs that previously used shared-key access also require Azure role-assignment permissions and resource provider registration for this transition. A successful deployment on an earlier version doesn't confirm that these prerequisites are met.

If the CMG server application's service principal can't create the required storage role assignments, the CMG deployment update can fail. **CloudMgr.log** can report HTTP `403`, `DeploymentFailed`, and a denied `Microsoft.Authorization/roleAssignments/write` action. Missing **Microsoft.Maintenance** resource provider registration can also cause the deployment update to fail.

Before updating, verify the CMG server application's effective permissions at each CMG resource group. The **Contributor** role alone doesn't grant storage role-assignment permissions, and the signed-in administrator's permissions don't establish that the CMG application has access. Use the constrained role-assignment configuration described in [Configure Azure RBAC permissions for the server app](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad#configure-azure-rbac-permissions-for-the-server-app), rather than granting unrestricted administrator permissions.

Also verify that **Microsoft.Maintenance** is registered in every Azure subscription that hosts a CMG. Registration in a staging subscription doesn't register the provider in a different production subscription. For instructions, see [Configure Azure resource providers](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-azure-ad#configure-azure-resource-providers).
