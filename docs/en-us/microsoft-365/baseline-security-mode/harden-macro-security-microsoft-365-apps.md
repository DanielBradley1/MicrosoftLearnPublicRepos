<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/harden-macro-security-microsoft-365-apps?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Harden VBA macro security in Microsoft 365 apps

This setting hardens Visual Basic for Applications \(VBA\) macro security in Microsoft 365 apps by strengthening how macros are evaluated, trusted, and allowed to run. When enabled, it increases protection against malicious macros by expanding runtime scanning, enforcing stricter signing requirements for always loaded macros, and tightening trusted publisher criteria.

The policy also removes Trusted Documents and other trust exceptions for macros downloaded from the internet, and applies stricter macro evaluation to help prevent users from inadvertently enabling unsafe code. These controls reduce the risk of malware and ransomware delivered through Office documents while maintaining clearer guidance for legitimate macro usage.

For more information, see [Privacy and security for Office Add-ins](https://learn.microsoft.com/en-us/office/dev/add-ins/concepts/privacy-and-security).

Note

The VBA macro security setting is currently not available for government clouds.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

VBA macros are a well known and frequently exploited attack vector used by malicious actors to deliver malware and ransomware through Office documents. Macros are a common technique used in phishing campaigns and malicious attachments.

This setting helps mitigate those risks by:

- **Blocking unsafe macros from internet originated files** Macros in files downloaded from the internet are treated as high risk and are blocked by default, reducing the likelihood of successful phishing based attacks.
- **Reducing reliance on user trust decisions** Removing Trusted Documents and similar exceptions prevents attackers from convincing users to bypass security prompts to enable malicious macros.
- **Strengthening macro trust enforcement** Requiring stronger trust signals- such as trusted publishers- helps ensure that only vetted macros are allowed to run.
- **Aligning with Microsoft's recommended security posture** Microsoft recommends hardening macro execution as part of its security baseline because insufficient macro controls significantly increase exposure to malware and ransomware.

## How this setting works

When this setting is enabled:

- **Macros are evaluated using stricter security criteria**, including origin and trust signals.
- **Macros from internet downloaded files are blocked**, even if users attempt to enable them through trust prompts.
- **Trusted Documents and other trust exceptions are removed** for internet originated macros, preventing persistent trust abuse.
- **Stronger signing and trusted publisher requirements are enforced** for macros that are allowed to run.
- **Macro execution decisions are guided by stricter policy based controls**, rather than relying on token user prompts.

This configuration ensures macro execution reflects organizational security policy rather than individual user choices.

## Additional considerations for administrators

The admin center experience highlights several important points to consider before enforcement:

- This setting is labeled At risk, reflecting that VBA macros are a common malware delivery mechanism.
- Administrators can review users and existing macros impacted before enabling the policy, helping assess business impact.
- A Download detailed report \(CSV\) option is available to:

  - Identify macros currently in use
  - Understand which users may be affected
  - Plan remediation or signing of legitimate macros

- Hardening macro security may affect legacy workflows that rely on unsigned or loosely trusted macros and should be validated using the available reporting.

## Use Cloud Policy service

You can also make changes to the policy settings directly using the [Cloud Policy service](https://config.office.com/). Set the **Require trusted publisher signatures for macros that are always loaded** policy as not configured to revert to the default behavior.
