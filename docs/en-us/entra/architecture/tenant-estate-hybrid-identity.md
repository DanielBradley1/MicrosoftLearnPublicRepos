<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-hybrid-identity -->
<!-- Sitemap-Last-Modified: 2026-07-31 -->

# Microsoft Entra tenant estate guidance for hybrid identity and isolation

Designing your Microsoft Entra **tenant estate** — the set of tenants your organization operates — means balancing security, compliance, administrative complexity, and user experience. While a single production tenant is ideal for simplicity and user experience, your specific business and technical requirements might necessitate multiple production tenants.

This article series describes the following common tenant architecture patterns that Microsoft has observed across real-world deployments.

- [Microsoft Entra tenant estate guidance introduction](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-guide)
- [Primary production tenant](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-primary)
- [Collaborating production tenants](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-collaborating)
- [Nonproduction environments](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-nonproduction)
- [Isolated tenants for critical production systems](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-critical-production)
- [Isolated tenants for business partner access](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-business-partner)

This article describes hybrid identity and isolation. A multitenant architecture can provide strong isolation at the cloud layer. However, many organizations operate a hybrid identity model. Hybrid identity supports resource access and device management across on-premises and cloud environments. However, it increases attack surface and operational complexity. It requires a larger investment to deploy, monitor, and maintain.

Microsoft Entra ID tenants synchronize users, groups, and devices from on-premises Active Directory with tools like Microsoft Entra Connect, Cloud Sync or Microsoft Identity Manager.

When you design a multitenant architecture to meet isolation requirements, use segmentation controls in each Microsoft Entra tenant and in the underlying infrastructure. For example, if multiple tenants source identities from the same Active Directory forest \(or from interconnected forests that use trusts\), then shared identity sources can undermine tenant-level isolation. Plan for the following potential incidents.

- A compromised on-premises account might propagate to multiple tenants if that account synchronizes into each one.
- Group memberships managed on premises might inadvertently grant access across tenants if improperly scoped.
- Device compliance and Conditional Access policies can rely on signals from hybrid-joined devices that might share across tenants.

To achieve meaningful isolation in a hybrid scenario, consider the following recommendations.

- **Segment Active Directory forests or domains** to align with tenant boundaries. For example, use separate domains for each tenant and avoid cross-domain trusts unless explicitly required.
- **Scope synchronization connectors** to limit which identities synchronize into each tenant. Avoid overlapping sync scopes that could result in the same identity appearing in multiple tenants.
- **Review group management practices**, especially if groups synchronize from on premises. Ensure that group membership doesn't inadvertently span isolation boundaries.
- **Evaluate device management boundaries**, particularly if you use Intune or Configuration Manager in hybrid mode. Enroll and manage devices in alignment with the tenants that they support.
- **Apply least privilege principles** to on-premises administrators. Admins with rights in Active Directory might indirectly influence multiple tenants with improperly scoped synchronization.
- **Align cloud isolation with on-premises infrastructure isolation**. Without careful design, hybrid identity can become a bridge that bypasses tenant boundaries. If you implement multitenant architectures for security, compliance, or operational reasons, include Active Directory and device management architecture in your planning.

The preceding considerations highlight isolation risks specific to multitenant architectures that operate in hybrid identity models where shared on‑premises infrastructure can unintentionally weaken tenant boundaries. These recommendations are additive and not a substitute for established identity security best practices. Continue to apply well‑understood controls such as tiered Active Directory administration models, Privileged Access Workstations \(PAW\), and strict separation of Tier‑0 assets.

## Related content

- [Microsoft Entra tenant estate guidance introduction](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-guide)
- [Microsoft Entra tenant estate guidance: Primary production tenant](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-primary)
- [Microsoft Entra tenant estate guidance: Collaborating production tenants](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-collaborating)
- [Microsoft Entra tenant estate guidance: Nonproduction environments](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-nonproduction)
- [Microsoft Entra tenant estate guidance: Isolated tenants for critical production systems](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-critical-production)
- [Microsoft Entra tenant estate guidance: Isolated tenants for business partner access](https://learn.microsoft.com/en-us/entra/architecture/tenant-estate-business-partner)
