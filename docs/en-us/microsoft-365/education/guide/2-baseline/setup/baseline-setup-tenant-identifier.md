<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-tenant-identifier -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Step 8: Education Tenant Identifier

## Overview

Classify Microsoft Education tenants as either K-12 or Higher Education by using the new Microsoft Education Tenant Identifier. This identifier determines how students are treated by default and how they're granted or denied access to tools and products like Microsoft Copilot. Microsoft recommends every IT admin for a Microsoft 365 Education tenant set and verify their Tenant Identifier correctly.

## Tenant Identifier settings

The Education Tenant Identifier offers four settings. IT admins should pick the setting that best applies to their institution, to ensure appropriate student access to Microsoft Copilot in alignment with Microsoft policy.

![Screenshot showing options for the Tenant Identifier.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/setup/tenant-identifier.png)

- **K-12:** If you're a K-12 school, district, or ministry of education, this setting is for you. When selected, students are treated as minors by default unless or until you set their ageGroup attribute in Microsoft Entra ID to notAdult or adult. Students with ageGroup set to minor aren't allowed to access Microsoft Copilot, regardless of their license assignment.
- **Higher Education:** If you're a college, university, technical school, or any post-secondary institution of higher learning, this setting is for you. When selected, students are treated as adults, unless or until you set their ageGroup attribute in Microsoft Entra ID to state otherwise. Students with ageGroup set to adult are allowed to access Microsoft Copilot, assuming they also have the required license assignment.
- **Other:** If you're a Research Institution, Academic Library, or other educational organization, this setting is for you. When selected, students are treated as adults, unless or until you set their ageGroup attribute in Microsoft Entra ID to notAdult or minor. Students with ageGroup set to adult are allowed to access Microsoft Copilot, if they also have the required license assignment.

## How to set the Education Tenant Identifier

To access the Tenant Identifier, follow these steps:

1. Sign in to the Microsoft 365 Admin Center as a Global Administrator.
2. Go to **Settings** > **Org Settings**.
3. Under the **Services** tab, find **Microsoft Education Tenant Identifier**.
4. On the flyout, select the appropriate setting and select **Save**.
