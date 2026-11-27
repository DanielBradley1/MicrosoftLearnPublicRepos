<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-com-addins-not-on-admin-allow-list?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block COM add-ins that aren't on the admin allow list

This setting blocks COM add-ins that aren't explicitly included in an administrator managed allow list from running in Microsoft 365 apps. Microsoft 365 apps rely on user level policy settings to determine which COM add-ins can load. When this setting is enabled, only approved COM add-ins are allowed to run, while all other unmanaged or untrusted COM add-ins are blocked. By enforcing an allow list model, this setting helps reduce the risk of malicious or unreviewed add-ins executing in Office applications and provides centralized administrative control over which COM add-ins users can load.

Note

The COM add-ins setting is currently not available for government clouds.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

COM add-ins are legacy Office extensibility components that run inside the Office client on Windows and execute with the full permissions of the signed in user. Unlike modern Office web add-ins, COM add-ins don't benefit from the same sandboxing and isolation model.

This setting helps mitigate security risks by:

- **Preventing execution of untrusted COM add-ins** Only COM add-ins that are explicitly approved by administrators are allowed to run, reducing exposure to unknown or potentially malicious components.
- **Reducing a common attack vector** Because COM add-ins can access local files, the Windows registry, and network resources, they're a frequent target for persistence and initial access attacks when left unrestricted.
- **Enforcing centralized governance** Administrators control which add-ins are permitted, rather than relying on individual user decisions or local configuration.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk, reinforcing Microsoft guidance to tightly control add-ins that run with elevated trust in Office clients.

## How this setting works

When this setting is enabled:

- **Microsoft 365 apps evaluate COM add-ins against an admin managed allow list** defined through policy.
- **COM add-ins that aren't on the allow list are blocked** from loading in Office applications.
- **Approved add-ins continue to run normally**, without user intervention.
- **Users can't override the restriction**, ensuring consistent enforcement across the organization.

This allow list approach ensures that only reviewed and trusted COM add-ins can execute, while all others are prevented from running by default.

## Additional considerations for administrators

The admin center experience and Microsoft Learn guidance highlight several important points for assessment and rollout:

- This setting is labeled **At risk**, emphasizing that unrestricted COM add-ins significantly increase exposure to malicious code execution.
- The admin center surfaces who is loading COM add-ins and which add-ins are in use, helping administrators understand the impact before enforcement.
- A **Download detailed report \(CSV\)** option allows admins to:

  - Identify COM add-ins currently in use
  - Review affected users
  - Build or refine the allow list before enabling the policy

- COM add-ins are distinct from modern Office web add-ins, which use a sandboxed runtime and are centrally managed through the Microsoft 365 admin center. This setting specifically targets **legacy** COM add-ins, which require stricter controls.

## Use Cloud Policy service

You can also make changes to the policy settings directly using the [Cloud Policy service](https://config.office.com/). Set the **Block loading of COM/VSTO add-ins registered in HKCU** policy as not configured to revert to the default behavior.
