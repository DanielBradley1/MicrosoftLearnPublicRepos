<!-- Source: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-quality-updates -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Manage Windows quality updates

Windows quality updates are the regular Windows servicing updates that keep devices secure, reliable, and supported. These updates are released frequently—typically monthly—and include security fixes, non‑security improvements, and reliability enhancements. Because quality updates are cumulative, installing the latest update brings a device fully up to date for its currently installed Windows version.

In Microsoft Intune, you manage Windows quality updates through **quality update policies**. These policies provide a dedicated policy surface for targeting specific quality updates, and use cloud‑based update orchestration to deploy those updates to devices. Quality update policies work alongside other Windows update policies—such as **feature updates policies** and **driver updates policies**—and can be managed directly in Intune or automatically through **Windows Autopatch**, depending on your deployment model.

Quality update policies support targeted deployment scenarios for Windows quality updates. You can use them to **expedite updates** and accelerate the installation of critical or security updates when standard deployment timelines aren't acceptable. For eligible Windows editions and device configurations, you can also enable **hotpatch**, which installs certain security updates without requiring an immediate device restart—helping balance rapid protection, deployment control, and end‑user experience.

Client‑side update behavior—such as restart settings, deadlines, notifications, and deferral periods—continues to be configured through **update rings** and **Windows Update client policies**, which together with quality update policies complete the end‑to‑end update experience on devices.

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

## How quality update policies support different deployment scenarios

Quality update policies provide a single management surface for deploying Windows quality updates across different operational scenarios:

- **Standard deployment**: Use quality update policies to enable cloud‑based orchestration of regular monthly quality updates, while update rings and Windows Update client settings continue to control restarts, deadlines, and notifications.
- **Expedited deployment**: Use expedite policies to accelerate the installation of a specific security or critical update when faster remediation is required.
- **Restart‑optimized deployments**: On supported devices, enable hotpatch through quality update policies to apply qualifying security updates without requiring an immediate device restart.

These scenarios use cloud‑based update orchestration to control how updates are approved, timed, and applied, depending on the deployment model.

### Do I need a Windows quality update policy?

You don't need to create a Windows quality update policy for devices to continue receiving monthly Windows quality updates. Devices without a quality update policy continue to receive quality updates through standard Windows Update behavior, using update rings and Windows Update client policies to control deferrals, deadlines, restarts, and notifications.

Create a Windows quality update policy if you want to:

- Enable **cloud‑based orchestration** of Windows quality updates
- Use **Windows Autopatch-managed quality update deployments**
- Enable **hotpatch** for eligible devices
- View **policy‑based quality update reporting**

If you only need to **accelerate the installation of a specific quality update** for a limited set of devices, you can use an **expedite policy** without creating a quality update policy.

In most environments, you create a Windows quality update policy only when you need advanced deployment scenarios such as hotpatch or Windows Autopatch-managed update workflows.

## Next steps

- [Learn how hotpatch works with quality update policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-hotpatch)
- [Learn how expedite policies work with quality update policies](https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-quality-updates)
