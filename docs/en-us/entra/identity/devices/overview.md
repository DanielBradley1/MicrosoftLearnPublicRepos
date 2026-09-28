<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/overview -->
<!-- Sitemap-Last-Modified: 2025-06-27 -->

# What is a device identity?

A [device identity](https://learn.microsoft.com/en-us/graph/api/resources/device) is an object in Microsoft Entra ID. This device object is similar to users, groups, or applications. A device identity gives administrators information they can use when making access or configuration decisions.

![Devices displayed in Microsoft Entra Devices blade](https://learn.microsoft.com/en-us/entra/identity/devices/media/overview/azure-entra-devices-all-devices.png)

There are three ways to get a device identity:

- Microsoft Entra registration
- Microsoft Entra join
- Microsoft Entra hybrid join

Device identities are a prerequisite for scenarios like [device-based Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant) and [Mobile Device Management with the Microsoft Intune family of products](https://learn.microsoft.com/en-us/mem/endpoint-manager-overview).

## Modern device scenario

The modern device scenario focuses on two of these methods:

- [Microsoft Entra registration](https://learn.microsoft.com/en-us/entra/identity/devices/concept-device-registration)

  - Bring your own device \(BYOD\)
  - Mobile device \(cell phone and tablet\)

- [Microsoft Entra join](https://learn.microsoft.com/en-us/entra/identity/devices/concept-directory-join)

  - Windows 11 and Windows 10 devices owned by your organization
  - [Windows Server 2019 and newer servers in your organization running as VMs in Azure](https://learn.microsoft.com/en-us/entra/identity/devices/howto-vm-sign-in-azure-ad-windows)

[Microsoft Entra hybrid join](https://learn.microsoft.com/en-us/entra/identity/devices/concept-hybrid-join) is seen as an interim step on the road to Microsoft Entra join. All three scenarios can coexist in a single organization.

## Resource access

Registering and joining devices to Microsoft Entra ID gives users Seamless Sign-on \(SSO\) to cloud-based resources.

Devices that are Microsoft Entra joined benefit from [SSO to your organization's on-premises resources](https://learn.microsoft.com/en-us/entra/identity/devices/device-sso-to-on-premises-resources).

## Provisioning

Getting devices in to Microsoft Entra ID can be done in a self-service manner or a controlled process managed by administrators.

## Related content

- To get an overview of how to manage device identities, see [Managing device identities](https://learn.microsoft.com/en-us/entra/identity/devices/manage-device-identities).
- To learn more about device-based Conditional Access, see [Configure Microsoft Entra device-based Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-conditional-access-grant).
