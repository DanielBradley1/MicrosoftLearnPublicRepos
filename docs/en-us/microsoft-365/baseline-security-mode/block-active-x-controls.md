<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-active-x-controls?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block ActiveX controls in Microsoft 365 apps

As a Microsoft 365 admin, you want to protect and secure your business environment. **Baseline security mode** helps you protect and secure your organization.

ActiveX controls are small programs used to add interactive features to Microsoft 365 documents and web pages. Due to their history of security vulnerabilities, ActiveX controls are highly susceptible to exploitation by malicious actors. These controls can be used to run harmful code, install malware, or take control of a system when users open compromised files or visit unsafe websites. Consequently, ActiveX is now blocked by default in Microsoft 365 apps.

When this setting is turned on, users in your environment won't be able to override the default configuration using **Trust Center**.

If you have turned on this setting but need to return to the default behavior \(allow users to override ActiveX blocking using Trust Center\), you can turn this setting off directly in the Microsoft 365 admin center.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## ActiveX settings behavior

- If no configuration is set by the user or administrator, ActiveX defaults to **Disable all controls without notification**. Users can change this setting in Trust Center.
- In baseline security mode, the setting is enforced by policy as **Disable all controls without notification**. In this case, the option is locked in Trust Center and appears greyed out.

## Scope summary

This setting applies across the organization to supported Microsoft 365 apps. When enabled, Microsoft 365 apps block ActiveX controls from running, and users can’t override the setting.

Baseline Security Mode doesn’t provide direct user-level or app-level scoping for this setting. If specific users or workflows still depend on files that contain ActiveX controls, review the available exclusion guidance.

## Turn off setting in the Microsoft 365 admin center

1. Go to the Microsoft 365 admin center at [https://admin.cloud.microsoft](https://go.microsoft.com/fwlink/p/?linkid=2024339) and select **Org settings**.
2. Select Baseline Security Mode, find the **Block ActiveX controls in the Microsoft 365 apps** setting, and switch the toggle to **Off**.

## Use Office Cloud Policy service

**You can use Office Cloud Policy service to exclude certain users or groups from this setting**. Follow the steps in the [Steps for creating a policy configuration](https://learn.microsoft.com/en-us/microsoft-365-apps/admin-center/overview-cloud-policy) topic to create a new policy configuration.

- In **Step 4**, select the users or group\(s\) to exclude from this setting. Only individuals and Microsoft Entra groups can be excluded. For more information on groups, see [Microsoft Entra groups requirements](https://learn.microsoft.com/en-us/microsoft-365-apps/admin-center/overview-cloud-policy).
- In **Step 7**, find the **Disable All ActiveX** policy and set it to **Enabled**. Make sure this new policy configuration is a **higher** priority than the **Tenant** policy configuration to make sure it takes precedence. You can verify and update this in the main [Policy configurations](https://config.office.com/officeSettings/officePolicies) page.

Tip

You can download a detailed report under the Baseline Security Mode **Block ActiveX controls in the Microsoft 365 apps** setting to identify users who are opening files which contain ActiveX controls and have ActiveX controls currently enabled.

If you have turned on this setting but need to return to the default behavior, you can set the **Disable All ActiveX** policy to **Not configured**.
