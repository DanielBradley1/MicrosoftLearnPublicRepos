<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/run-remediation -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device action: run remediation

The *run remediation* action in Microsoft Intune allows IT administrators to proactively detect and resolve support issues on managed devices. This action triggers a remediation script that checks for specific conditions and applies a fix if needed—without requiring user interaction.

Use this action to address common problems such as configuration drift, missing settings, or compliance gaps. It's especially useful for maintaining device health across large environments.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Run Remediation**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to run a remediation from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Run remediation \(preview\)**.
4. In the **Run remediation \(preview\)** pane, select the Script package you want to run from the list.
5. To run the remediation, select **Run remediation**.

To learn more about remediations in Microsoft Intune—including what they are, along with prerequisites and licensing requirements—see [Use Remediations to detect and fix support issues](https://learn.microsoft.com/en-us/intune/device-management/tools/deploy-remediations).

## Reference links

- Microsoft Graph API: [initiateOnDemandProactiveRemediation action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-initiateondemandproactiveremediation)
