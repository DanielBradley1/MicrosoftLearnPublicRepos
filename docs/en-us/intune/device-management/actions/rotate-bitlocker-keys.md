<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/actions/rotate-bitlocker-keys -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# Device action: BitLocker key rotation

The *BitLocker key rotation* action in Microsoft Intune lets IT admins remotely refresh the recovery key for the operating system drive on BitLocker-encrypted Windows devices. This helps reduce the risk of unauthorized access if a recovery key has been used or potentially exposed.

Key rotation is especially useful in environments where devices are frequently serviced, reassigned, or exposed to support scenarios. For example, if a helpdesk technician shares a recovery key during a support call, you can rotate the key from Intune to ensure it can't be reused.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This action supports the following platforms:
> 
> - Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To run this action, use an account with at least one of the following roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The permission **Remote tasks/Rotate BitLockerKeys**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)

## How to rotate the BitLocker key from the Intune admin center

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview) > [**All devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/allDevices).
2. From the devices list, select a device.
3. At the top of the device overview pane, find the row of action icons. Select **Secure** > **BitLocker key rotation**.
4. Select **Yes** to confirm the action.

## Reference links

- Configuration service provider \(CSP\) used to initiate the action: [BitLocker CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/bitlocker-csp#rotaterecoverypasswords)
- Microsoft Graph API: [rotateBitLockerKeys action](https://learn.microsoft.com/en-us/graph/api/intune-devices-manageddevice-rotateBitLockerKeys)
- [BitLocker overview](https://learn.microsoft.com/en-us/windows/security/operating-system-security/data-protection/bitlocker/)
