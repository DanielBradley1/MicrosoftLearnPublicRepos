<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/prerequisites-for-power-management -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Prerequisites for power management in Configuration Manager

*Applies to: Configuration Manager \(current branch\)*

Power management in Configuration Manager has external dependencies and dependencies within the product.

## Dependencies external to Configuration Manager

The following table lists the dependencies external to Configuration Manager for using power management.

| Dependency | More information |
| --- | --- |
| Client computers must be able to support the required power states | To use all features of power management, client computers must be able to support the sleep, hibernate, wake from sleep, and wake from hibernate actions. You can use the **Power Capabilities** report to determine if computers can support these actions. For more information, see [Power Capabilities report](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/monitor-and-plan-for-power-management#BKMK_Capabilites) in the topic [How to monitor and plan for power management](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/monitor-and-plan-for-power-management). |

## Configuration Manager dependencies

The following table lists the dependencies within Configuration Manager for using power management.

| Dependency | More Information |
| --- | --- |
| Power management must be enabled before you can create and monitor power plans. | For information about how to enable and configure power management, see [Configuring power management](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/power/configuring-power-management). |
| Reporting services point | You must configure a reporting services point before you can view power management reports. For more information, see [Introduction to reporting](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-reporting). |
