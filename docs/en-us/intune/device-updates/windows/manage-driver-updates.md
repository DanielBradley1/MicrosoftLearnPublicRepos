<!-- Source: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-driver-updates -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Manage Windows driver updates

Windows driver updates provide updated device drivers and firmware that help ensure hardware compatibility, stability, and performance. These updates are released by device manufacturers and can include fixes for reliability issues, security vulnerabilities, and support for new hardware capabilities. Because driver updates can vary by device model and hardware configuration, organizations often prefer a more controlled approval process.

In Microsoft Intune, Windows driver updates are managed through **driver update policies**, which provide a dedicated policy surface for reviewing, approving, and deploying driver updates to managed devices. This policy is built on cloud‑based update orchestration and works alongside other Windows update policies, such as feature updates and quality updates. Driver update policies can be used independently or as part of Windows Autopatch. Client‑side install behavior—such as restarts and user notifications—continues to be governed by standard Windows Update policy settings.

Driver update policies support **automatic or manual approval workflows**, allowing you to choose whether recommended drivers are deployed automatically or require administrator review before installation. This approach helps organizations balance hardware stability, risk management, and operational efficiency while maintaining visibility into which drivers are approved for deployment.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/network-connectivity.svg) **Network and connectivity requirements**

> Devices must have internet access and be able to reach required Microsoft endpoints:
> 
> - [Intune service endpoints](https://learn.microsoft.com/en-us/intune/fundamentals/endpoints#access-for-managed-devices)
> - [Windows Update endpoints](https://learn.microsoft.com/en-us/windows/privacy/manage-windows-1809-endpoints#windows-update)
> - [Windows Autopatch endpoints](https://learn.microsoft.com/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-configure-network)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/cloud.svg) **Cloud requirements**

> This feature is supported in the following cloud environments:
> 
> - Public cloud
> - Government Community Cloud \(GCC\)

![](https://learn.microsoft.com/en-us/intune/media/icons/16/tenant-administration.svg) **Tenant configuration requirements**

> To enable reporting for this feature, ensure your organization allows Intune to access Windows diagnostic data collected from enrolled devices.
> 
> For details, see [Enable use of Windows diagnostic data](https://learn.microsoft.com/en-us/intune/privacy/enable-windows-diagnostic-data).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> To use this feature, the following licenses are required:
> 
> - [Microsoft Intune Plan 1](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
> - A Windows license that includes the [Autopatch entitlement](https://learn.microsoft.com/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-prerequisites#licenses-and-entitlements).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following Windows editions:
> 
> - Pro
> - Pro Education
> - Enterprise
> - Education
> 
> Note
> 
> Windows Enterprise LTSC \(Long Term Service Channel\) isn't supported. Use update ring policies instead.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> This policy type supports devices that are:
> 
> - Managed by Intune
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 
> Devices must also meet the following requirements:
> 
> - Telemetry must be turned on, with a minimum setting of [**Required**](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows#reporting-and-telemetry).
> - The *Microsoft Account Sign-In Assistant* service \(`wlidsvc`\) must be enabled and running.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To manage this feature, use an account with at least one of the following roles:
> 
> - [Policy and Profile manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - The **Device configurations** permissions **Assign**,**Create**,**Delete**,**View Reports**,**Update**, and **Read**
>   - Permissions that provide visibility into and access to managed devices in Intune \(for example, Organization/Read, Managed devices/Read\)
> 
> To view the reports for this feature, use an account with at least one of the following roles:
> 
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager)
> - [Read Only Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator)
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator)
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) with the **Managed devices**/**View Reports** permission.

## Architecture

The following diagram illustrates the high‑level architecture for managing Windows driver updates by using Microsoft Intune and Windows Autopatch.

[![A conceptual diagram of Windows driver update management.](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/manage-driver-updates/update-management-architecture.png)](https://learn.microsoft.com/en-us/intune/device-updates/windows/media/manage-driver-updates/update-management-architecture.png#lightbox)

1. **Microsoft Intune** provides device identity, assignment, and driver update approval information. Intune sends policy settings, approved drivers, and pause commands to Windows Autopatch.
2. **Windows Autopatch** uses this information to configure Windows Update behavior for managed devices and to coordinate driver update deployment.
3. **Windows Update** evaluates device and hardware information to determine which driver updates are applicable, and installs only approved updates during regular update scans.
4. **Reporting data** collected during update operations is sent through Windows Autopatch and surfaced in Intune reporting.

This architecture allows administrators to approve and control driver updates centrally in Intune while relying on Windows Update and Autopatch to determine applicability and handle installation.

## Next steps

[Learn how to configure driver update policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-driver-update-policy)
