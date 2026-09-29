<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-dashboard -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Vulnerability management in multi-tenant management

**Applies to:**

- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

## Microsoft Defender Vulnerability Management dashboard

You can use the Defender Vulnerability Management dashboard in multi-tenant management to view aggregated and summarized information across all tenants, such as:

- Your exposure score and exposure level for devices across all tenants.
- Your most exposed tenants along with details of the number of weaknesses, exposed devices, and available recommendations for each tenant.

  [![Screenshot of the defender vulnerability management dashboard in multi-tenant management in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/media/mto-dashboard/mto-mdvm-dashboard.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-dashboard/mto-mdvm-dashboard.png#lightbox)

The Defender Vulnerability Management dashboard in multi-tenant management provides the following information across all the tenants you have access to:

| Area | Description |
| --- | --- |
| **Organization Exposure score** | See the current state of your organization's device exposure to threats and vulnerabilities across all tenants. |
| **Most exposed tenants** | Real time visibility into the tenants with the highest current exposure level. |
| **Tenants with the largest increase in exposure** | Identify tenants with the largest increase in exposure over the last 30 days. |
| **Device exposure distribution** | See how many devices are exposed based on their exposure level, across all tenants. Select a section in the doughnut chart to see the number of exposed devices at each level. |
| **Tenant exposure distribution** | View a summary of exposed tenants aggregated by exposure level. |

## Tenant vulnerability details

The **Tenants page** under **Vulnerability management** includes vulnerability information for all tenants, and at a tenant-specific level, such as exposed devices, security recommendations, weaknesses, and critical CVEs.

[![Screenshot of multi-tenant vulnerability management in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/media/mto-dashboard/mto-multi-tenant-view.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-dashboard/mto-multi-tenant-view.png#lightbox)

At the top of the page, you can view the number of tenants and the aggregate number of:

- Exposed devices
- Critical CVEs
- High severity CVEs
- Security recommendations

Select a tenant name to navigate to the Defender Vulnerability Management dashboard for that tenant in the [Microsoft Defender XDR](https://security.microsoft.com/machines) portal.

For more information, see [Microsoft Defender Vulnerability Management dashboard](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-dashboard-insights).

## Related articles

- [Exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score)
- [Security recommendations](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation)
