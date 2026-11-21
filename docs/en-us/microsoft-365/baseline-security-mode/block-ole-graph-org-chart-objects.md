<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-ole-graph-org-chart-objects?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-16 -->

# Block OLE Graph and OrgChart objects

As a Microsoft 365 admin, you want to protect and secure your business environment. **Baseline security mode** helps you protect and secure your organization.

Although rarely used today, OLE Graph and OrgChart objects in Microsoft 365 files are legacy features that attackers often exploit to run malicious code when a document is opened.

When you enable this setting, Microsoft 365 apps will block loading OLE Graph and OrgChart objects to protect users from known exploitation techniques.

If you have enabled this setting but need to revert to the default behavior \(allow users to override the basic authentication blocking using Trust Center\), you can turn this setting off directly in the Microsoft 365 admin center.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Turn off setting in the Microsoft 365 admin center

1. Go to the Microsoft 365 admin center at [https://admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339) and select Org settings.
2. Select Baseline Security Mode, find the **Block OLE Graph and OrgChart objects** setting, and switch the toggle to **Off**.

## Use Office Cloud Policy service

Alternatively, you can make changes to the policy setting directly using the [Office Cloud Policy service](https://config.office.com/). Set the **Block OrgChart** policy and **Block OLE Graph** policy as not configured to revert to the default behavior.
