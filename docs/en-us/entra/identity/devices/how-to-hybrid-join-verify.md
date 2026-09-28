<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/how-to-hybrid-join-verify -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Verify Microsoft Entra hybrid join

This article describes three ways to locate and verify the Microsoft Entra hybrid joined device state.

## Prerequisites

None

## Locally on the device

Follow these steps:

1. Open Windows PowerShell.
2. Enter `dsregcmd /status`.
3. Verify that both **AzureAdJoined** and **DomainJoined** are set to **YES**.
4. You can use the **DeviceId** and compare the status on the service using either the Microsoft Entra admin center or PowerShell.

## Using the Microsoft Entra admin center

Follow these steps:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Device Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-device-administrator).
2. Browse to **Entra ID** > **Devices** > **All devices**.
3. If the **Registered** column says **Pending**, then Microsoft Entra hybrid join hasn't completed. In federated environments, this state happens only if it failed to register and Microsoft Entra Connect is configured to sync the devices. Wait for Microsoft Entra Connect to complete a sync cycle.
4. If the **Registered** column contains a **date/time**, then Microsoft Entra hybrid join has completed.

## Using PowerShell

Verify the device registration state in your Azure tenant by using [Get-MgDevice](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.directorymanagement/get-mgdevice). This cmdlet is in the [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/overview).

When you use the **Get-MgDevice** cmdlet to check the service details:

- An object with the **device ID** that matches the ID on the Windows client must exist.
- The value for **DeviceTrustType** is **Domain Joined**. This setting is equivalent to the **Microsoft Entra hybrid joined** state on the **Devices** page in the Microsoft Entra admin center.
- For devices that are used in Conditional Access, the value for **Enabled** is **True** and **DeviceTrustLevel** is **Managed**.

1. Open Windows PowerShell as an administrator.
2. Enter [Connect-MgGraph](https://learn.microsoft.com/en-us/powershell/microsoftgraph/authentication-commands#using-connect-mggraph) to connect to your Azure tenant.

   ### Count all Microsoft Entra hybrid joined devices \(excluding **Pending** state\)


   ```powershell
   (Get-MgDevice -All | where {($_.TrustType -eq 'ServerAd') -and ($_.ProfileType -eq 'RegisteredDevice')}).count
   ```


   ### Count all Microsoft Entra hybrid joined devices with **Pending** state


   ```powershell
   (Get-MgDevice -All | where {($_.TrustType -eq 'ServerAd') -and ($_.ProfileType -ne 'RegisteredDevice')}).count
   ```


   ### List all Microsoft Entra hybrid joined devices


   ```powershell
   Get-MgDevice -All | where {($_.TrustType -eq 'ServerAd') -and ($_.ProfileType -eq 'RegisteredDevice')}
   ```


   ### List all Microsoft Entra hybrid joined devices with **Pending** state


   ```powershell
   Get-MgDevice -All | where {($_.TrustType -eq 'ServerAd') -and ($_.ProfileType -ne 'RegisteredDevice')}
   ```


   ### List details of a single device:


   1. Enter the following command. Obtain the device ID locally on the device.


   ```powershell
   $Device = Get-MgDevice -DeviceId <ObjectId>
   ```


   1. Verify that `AccountEnabled` is set to `True`.


   ```powershell
   $Device.AccountEnabled
   ```

## Related content

- [Configure Microsoft Entra hybrid join](https://learn.microsoft.com/en-us/entra/identity/devices/how-to-hybrid-join)
- [Troubleshoot pending device state](https://learn.microsoft.com/en-us/troubleshoot/azure/active-directory/pending-devices)
