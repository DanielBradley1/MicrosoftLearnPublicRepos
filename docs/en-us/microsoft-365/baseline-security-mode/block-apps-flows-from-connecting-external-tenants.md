<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-apps-flows-from-connecting-external-tenants?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block apps and flows from connecting to external tenants

Blocking apps and flows from connecting to external tenants helps prevent unintended data sharing and unauthorized cross tenant access within your Dynamics 365 and Power Platform environment. Without tenant level restrictions, compromised accounts or misconfigured apps can establish connections to data sources in other tenants, increasing the risk of data leakage, privilege misuse, or exfiltration. Enforcing this setting ensures that apps and flows operate only within your tenant's trusted boundaries, reducing exposure to external data pipelines and strengthening overall authentication and governance controls across your environment.

For more information, see [Cross tenant inbound and outbound restrictions in Microsoft Power Platform](https://learn.microsoft.com/en-us/power-platform/admin/cross-tenant-restrictions).

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator), [Dynamics 365 administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#dynamics-365-administrator), or [Power Platform Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#power-platform-administrator) to be able to configure this setting.

## Why this setting matters

Power Platform apps and Power Automate flows commonly connect to business critical data using Microsoft Entra-based authentication. By default, valid credentials can be used to establish cross tenant connections, even when that behavior isn't intended or reviewed by administrators.

This setting helps mitigate those risks by:

- **Preventing unintended cross tenant data movement** Tenant isolation blocks apps and flows from establishing connections to data sources in external tenants, reducing the risk of data leakage or exfiltration across organizations.
- **Reducing the impact of compromised identities or apps** Even if a user account or app is compromised, tenant level restrictions prevent it from being used as a bridge to access data in other tenants.
- **Strengthening tenant trust boundaries** Apps and flows are constrained to operate only within the tenant unless an administrator explicitly configures trusted exceptions.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk because unrestricted cross tenant connections significantly increase exposure to unauthorized access and data loss.

## How this setting works

When this setting is enabled:

- **Cross tenant connections are blocked by default**, including:

  - **Inbound connections** \(external tenants attempting to connect to data in your tenant\)
  - **Outbound connections** \(apps or flows in your tenant connecting to external tenants\)

- **Only Microsoft Entra ID- based connectors are evaluated**, ensuring tenant isolation applies to commonly used enterprise data sources.
- **Administrators can define explicit allow list exceptions** for trusted tenants, permitting inbound, outbound, or bidirectional connections when there is a valid business requirement.
- **Existing apps and flows that violate the policy may stop running**, and affected flows surface failure details in run history until the policy is adjusted or exceptions are added.
- **Policy changes are not instantaneous** and may take up to about an hour to be fully evaluated against existing apps and flows.

This model ensures that cross tenant communication is intentional, auditable, and limited to explicitly trusted tenants.

## Additional considerations for administrators

The admin center experience provides visibility and controls to help assess impact before enforcement:

- This setting is labeled **At risk** and **Recommended**, highlighting that cross tenant connections are a high impact data exfiltration vector if left unrestricted.
- The admin center shows quantified impact metrics, including:

  - **Cross tenant connections blocked**
  - **Apps and flows with restricted inbound connectors**
  - **Apps and flows with restricted outbound connectors**

- **Inbound and outbound restrictions are evaluated separately**, helping administrators understand the direction of cross tenant access attempts.
- **A Download detailed report \(CSV\)** option is available, allowing admins to identify affected apps, flows, and connectors and plan remediation or allow list exceptions before enforcing the policy.
- Administrators can **customize the policy** to allow trusted tenant exceptions while keeping all other cross tenant connections blocked by default.
