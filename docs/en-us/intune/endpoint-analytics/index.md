<!-- Source: https://learn.microsoft.com/en-us/intune/endpoint-analytics/ -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Endpoint analytics overview

Endpoint analytics helps IT professionals assess and improve the user experience across managed devices. It provides data-driven insights into device performance, startup times, app reliability, and battery health—empowering IT teams to proactively identify and remediate issues that impact productivity.

Endpoint analytics contributes to the technology experiences category within [Microsoft Adoption Score](https://learn.microsoft.com/en-us/microsoft-365/admin/productivity/productivity-score), offering device-level insights that complement broader organizational productivity metrics.

The service integrates with Microsoft Intune, enabling IT pros to:

- Enroll devices directly from Intune.
- Use Configuration Manager for co-managed environments.
- Manage data collection and configuration.
- View analytics in the Intune admin center.
- Apply remediations or adjust policies based on insights.

[![Screenshot of the endpoint analytics overview page](https://learn.microsoft.com/en-us/intune/endpoint-analytics/media/shared/overview.png)](https://learn.microsoft.com/en-us/intune/endpoint-analytics/media/shared/overview.png#lightbox)

## Available reports

Endpoint analytics organizes insights into reports that highlight performance and reliability issues across managed devices. These reports help IT teams identify trends, diagnose problems, and implement improvements to enhance the overall user experience. Endpoint analytics includes the following reports:

[Startup performance report](https://learn.microsoft.com/en-us/intune/endpoint-analytics/startup-performance)

> Identifies devices with slow boot times and factors that delay startup.

[Application reliability report](https://learn.microsoft.com/en-us/intune/endpoint-analytics/app-reliability)

> Monitors app crashes and stability trends to improve user experience.

[Work from anywhere report](https://learn.microsoft.com/en-us/intune/endpoint-analytics/work-from-anywhere)

> Evaluates device readiness for secure and efficient remote work.

[Advanced Analytics](https://learn.microsoft.com/en-us/intune/advanced-analytics/)

> Provides deeper insights and extended reporting capabilities \(**requires additional licensing**\).

## Prerequisites

To use endpoint analytics, ensure your environment meets the following prerequisites:

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> Endpoint analytics supports the following Windows editions:
> 
> - Pro
> - Pro Education
> - Enterprise
> - Education

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> Endpoint analytics supports devices that are:
> 
> - Managed by Intune
> - Co-managed \(Intune + Configuration Manager\)
> - Managed by Configuration Manager \(via tenant attach\)
> - Microsoft Entra joined
> - Microsoft Entra hybrid joined
> 
> Devices must also meet the following requirements:
> 
> - The **Connected User Experiences and Telemetry** service \(DiagTrack\) must be enabled and running.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/network-connectivity.svg) **Network and connectivity requirements**

> To enroll Intune-managed devices to endpoint analytics, they need to send required functional data to Microsoft public cloud. Ensure the following endpoints are accessible from Intune-managed devices:
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://*.events.data.microsoft.com` | Used by managed devices to send [required functional data](https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection#data-collection) to the Intune data collection endpoint. |
> 
> For more information and troubleshooting proxy configurations, see [Troubleshoot endpoint analytics](https://learn.microsoft.com/en-us/intune/endpoint-analytics/troubleshoot#proxy-server-authentication).

> Configuration Manager-managed devices send data to Intune via the connector on the Configuration Manager role and they don't need directly access to the Microsoft public cloud. If your environment uses a proxy server, configure the proxy server to allow the following endpoints:
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://graph.windows.net` | Used to automatically retrieve settings when attaching your hierarchy to endpoint analytics on Configuration Manager Server role. For more information, see \[Configure the proxy for a site system server\]\(../configmgr/> core/plan-design/network/proxy-server-support.md#configure-the-proxy-for-a-site-system-server\). |
> | `https://*.manage.microsoft.com` | Used to synch device collection and devices with endpoint analytics on Configuration Manager Server role only. For more information, see [Configure the proxy for a site system server](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server). |
> 
> If you have co-management enabled, enrolled devices send required functional data directly to Microsoft public cloud. In this case, ensure the following endpoints are accessible from co-managed devices:
> 
> | Endpoint | Function |
> | --- | --- |
> | `https://*.events.data.microsoft.com` | Used by managed devices to send [required functional data](https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection#data-collection) to the Intune data collection endpoint. |
> 
> For more information and troubleshooting proxy configurations, see [Troubleshoot endpoint analytics](https://learn.microsoft.com/en-us/intune/endpoint-analytics/troubleshoot#proxy-server-authentication).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> Devices enrolled in endpoint analytics need a valid license for the use of Microsoft Intune. For more information, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/fundamentals/licensing).

> Devices enrolled in endpoint analytics need a valid license for the use of Microsoft Intune. For more information, see [Microsoft Configuration Manager licensing](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/learn-more-editions).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Role requirements vary based on whether you're configuring endpoint analytics or reviewing the data.
> 
> \---
> 
> To [configure endpoint analytics](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure), you need an account with at least one of the following Intune roles:
> 
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator): Grants read/write permissions to endpoint analytics.
> - A [custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - **Endpoint Analytics/Read** — View scores and performance reports.
>   - **Endpoint Analytics/Create, Update, Delete** — Manage settings and baselines.
>   - **Organization/Read** and **Managed Devices/Read** — Required for device visibility.
>   - **Device configurations/Create, Read, Assign** — Required to create and assign the data collection policy
> 
> \---
> 
> To [access endpoint analytics reports](https://learn.microsoft.com/en-us/intune/endpoint-analytics/scores), you need an account with at least one of the following Intune roles:
> 
> - [Help Desk Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#help-desk-operator): Grants read permissions to endpoint analytics.
> - [Read Only Operator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator): Grants read permissions to endpoint analytics.
> - [Endpoint Security Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager): Grants read permissions to endpoint analytics.
> - [School Administrator](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#school-administrator): Grants read/write permissions to endpoint analytics.
> - [Custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/create-custom-role) that includes:
> 
>   - **Endpoint Analytics/Read** — View scores and performance reports.
>   - **Organization/Read** and **Managed Devices/Read** — Required for device visibility.
> 
> You can also use an account that has the following Microsoft Entra built-in roles:
> 
> - [Reports Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader): Grants read permissions to endpoint analytics.

## Configuration Manager requirements

To use endpoint analytics, your environment must have [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions) enabled. Tenant attach connects Configuration Manager to Intune, allowing you to manage devices from the Intune admin center and perform actions such as device sync and remote tasks.

Note

Using multiple Configuration Manager hierarchies with a single endpoint analytics instance isn't supported.

## Next Steps

Learn more about endpoint analytics:

- [Configure endpoint analytics](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure)
- [Scores, baselines, and insights](https://learn.microsoft.com/en-us/intune/endpoint-analytics/scores)
- [Understand data collection](https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection)
- [Microsoft Intune Advanced Analytics](https://learn.microsoft.com/en-us/intune/advanced-analytics/)
