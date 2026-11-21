<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/disable-xl4-xlm-macros?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Disable Excel 4.0 \(XL4/XLM\) macros

Excel 4.0 \(XLM/XL4\) macros are a legacy automation technology retained for backward compatibility. Microsoft advises organizations to migrate remaining XLM automation to Visual Basic for Applications \(VBA\), which offers a modern object model and stronger security controls. Microsoft added new VBA objects/methods to help replace the few remaining XLM only functions and recommends avoiding permissive macro states.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

- **Legacy risk surface**: XLM predates VBA and lacks modern safeguards; Microsoft encourages migration to VBA for better security and maintainability.
- **Independent control**: The newer Trust Center option lets you disable only XLM without affecting VBA policies, reducing attack paths that specifically abuse legacy macro sheets. Unchecking the XLM checkbox is the recommended hardened posture.

## How this setting works

When you enable Disable Excel 4.0 \(XLM\) macros in Baseline security mode:

- Excel blocks XLM macro execution so users can't run legacy macro sheets.
- Users are prevented from reenabling XLM via the Excel UI unless your organization's macro policy explicitly permits it.
- This overrides the Trust Center control that lets orgs manage XLM behavior separately from VBA using the checkbox **Enable Excel 4.0 macros when VBA macros are enabled**. Microsoft's recommended secure posture is to uncheck this box so XLM macros remain disabled even if VBA is allowed.

## Additional information for administrators

- **Trust Center \(per device/per user\)**: Users/admins can configure XLM behavior at **File** > **Options** > **Trust Center** > **Trust Center Settings** > **Macro Settings** using **Enable Excel 4.0 macros when VBA macros are enabled**. For a more secure configuration, leave this setting unchecked so XLM stays disabled regardless of VBA.
- **Group Policy / cloud policy**: Admins can centrally enforce XLM restrictions with policy controls referenced in this [TechCommunity post](https://techcommunity.microsoft.com/blog/excelblog/restrict-usage-of-excel-4-0-xlm-macros-with-new-macro-settings-control/2528450). For example, using Macro Notification Settings and the option to prevent Excel from running XLM macros, so end users can't weaken settings locally.
- **Migration guidance**: Microsoft's support article explains that Excel still supports XLM but recommends migrating to VBA. It documents the added VBA coverage for formerly XLM only functions and reiterates avoiding permissive macro modes. [Use this guidance when planning remediation of legacy files](https://techcommunity.microsoft.com/blog/excelblog/excel-4-0-xlm-macros-now-restricted-by-default-for-customer-protection/3057905).

## Use Cloud Policy service

You can also make changes to the policy settings directly using the [Cloud Policy service](https://config.office.com/). Set the **Prevent Excel from running XLM macros** policy as not configured to revert to the default behavior.
