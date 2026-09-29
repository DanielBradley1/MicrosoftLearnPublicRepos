<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-manage-cases -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# View and manage cases across multiple tenants in the Microsoft Defender multitenant portal

Case management in the [**Microsoft Defender multitenant portal**](https://mto.security.microsoft.com) allows you to view and manage security operations \(SecOps\) cases from multiple tenants in a single view. Case management supports multiple case types, including incident cases and generic cases.

Note

Incident cases are in preview and are the recommended experience for managing incidents across tenants in Microsoft Defender multitenant management. The legacy incident experience remains available during preview. For the legacy experience, see [View and manage incidents and alerts in Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-incidents-alerts).

Use the multitenant cases experience to:

- View and manage cases across multiple tenants
- Triage and prioritize incident cases from multiple tenants
- Define your own case workflow with custom status values for generic cases
- Assign tasks to collaborators and configure due dates
- Manage access to your cases using RBAC
- Open a case in the tenant-specific Microsoft Defender portal for deeper investigation or response

## View cases in the multitenant portal

The cases experience in the multitenant portal is similar to [the cases experience in the single-tenant Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management), but with a few extra features:

- The **Cases** list contains columns for **Tenant** and **Tenant ID**, so you can see which tenant each case belongs to.
- If you're managing many tenants, you can search, sort, or filter the cases list by tenant. Existing sort, filter, and search capabilities also work across multiple tenants in one combined view.
- Role-based access control \(RBAC\) settings are applied at the tenant level, so you only see cases from the tenants you have access to.

![Screenshot of the cases list in the Microsoft Defender multitenant portal.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-manage-cases/mto-cases-queue.png)

For more information, see [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management).

## Manage cases in the multitenant portal

Manage cases from multiple tenants from the multitenant cases list.

To manage a case:

1. Go to the [Microsoft Defender multitenant portal](https://mto.security.microsoft.com).
2. Select **Cases**.
3. Select the case you want to review.
4. Review the case details in the preview pane.
5. To open the full case details page, select the case name.

When you open the full case details page, the case opens in the tenant-specific Microsoft Defender portal. You can continue investigation or response in the context of that tenant.

Available actions depend on the case type, your permissions, and the tenant where the case is located.

For more information, see [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management).

## Manage incident cases across tenants

Use the multitenant cases list to triage and prioritize incident cases across tenants. Incident cases help analysts investigate and respond to related alerts, impacted assets, evidence, activities, and tasks.

To manage incident cases across tenants:

1. Go to the [Microsoft Defender multitenant portal](https://mto.security.microsoft.com).
2. Select **Cases**.
3. Filter or search the cases list to find the incident cases that need attention.
4. Select an incident case to review its details.
5. Open the incident case for deeper investigation or response.

For more information, see:

- [Prioritize incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/prioritize-incident-cases)
- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Investigate incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases)

## Create a generic case in the multitenant portal

You can create generic cases from the multitenant portal.

To create a generic case:

1. On the **Cases** page in the multitenant portal, select **+ Create**.
2. In the **Create case** pane, select the tenant where you want to create the case.
3. Enter the case details, and then save the case.

![Screenshot of creating a case in the Microsoft Defender multitenant portal.](https://learn.microsoft.com/en-us/defender-xdr/media/mto-manage-cases/mto-create-case.png)

The maximum allowed per tenant is 100,000 cases.

## Related content

- [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management)
- [Prioritize incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/prioritize-incident-cases)
- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Investigate incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases)
- [Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-overview)
- [Microsoft Sentinel in the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-defender-portal)
