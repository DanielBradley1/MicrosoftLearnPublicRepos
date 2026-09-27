<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/upgrade-readiness -->
<!-- Sitemap-Last-Modified: 2024-07-17 -->

# Integrate Upgrade Readiness with Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Important

The Windows Analytics service is retired as of January 31, 2020. For more information, see [KB 4521815: Windows Analytics retirement on January 31, 2020](https://support.microsoft.com/help/4521815/windows-analytics-retirement).

If your Configuration Manager site had a connection to Upgrade Readiness, you need to remove it and reconfigure clients.

## Remove Upgrade Readiness connection

1. Open the Configuration Manager console as a user with the **Full administrator** role.
2. Go to the **Administration** workspace, expand **Cloud Services**, and select the **Azure Services** node.
3. Delete the Windows Analytics service.

## Reconfigure clients

### Unenroll devices

First, review the site's default or any custom client device settings in the **Windows Analytics** group. For example, disable the following setting: **Manage Windows telemetry settings with Configuration Manager**.

On enrolled devices, remove the CommercialID value from the following Windows Registry keys:

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

### Windows diagnostic data configuration

If you don't want your devices to continue sending diagnostic data:

- Windows 10: set the diagnostic data level to **Security**
- Windows 7 SP1 or 8.1: disable the **Commercial Data Opt-in Key**

Set these values using one of the following methods:

- Group policy, in **Computer Configuration** > **Administrative Templates** > **Windows Components** > **Data Collection and Preview Builds**
- Mobile device management \(MDM\), such as [Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows)

For more information, see [Configure Windows diagnostic data in your organization](https://learn.microsoft.com/en-us/windows/privacy/configure-windows-diagnostic-data-in-your-organization).

Note

When you apply these changes, devices immediately stop sending diagnostic data. It may take 24-48 hours for Microsoft to stop processing insights for your workspace. Microsoft deletes this data from its cloud services within 30 days or less.
