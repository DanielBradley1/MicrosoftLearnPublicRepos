<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/custom-account-correlation-rules -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Manage account correlation rules in Microsoft Defender for Identity \(Preview\)

Custom account correlation rules are a Microsoft Defender for Identity setting for accounts that don't share strong identifiers. These identifiers include account ID, SID, object ID, or UPN. The rules are especially useful for privileged accounts with unique naming conventions. By defining custom rules, you get full visibility and better protection for all accounts.

[![Screenshot of the Account Correlation Rules settings page with rule management actions and configured rules.](https://learn.microsoft.com/en-us/defender-for-identity/media/account-correlation-rules-settings.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/account-correlation-rules-settings.png#lightbox)

Before you begin, review the license and role requirements in [Prerequisites](#prerequisites).

This article explains how to choose a correlation type, create custom account correlation rules, and edit or remove existing rules in the Microsoft Defender portal.

## Prerequisites

- An active Microsoft Defender for Identity license, or another license that includes Defender for Identity \(such as E5\). Without the required license, the policies page is read-only.
- At least one of the following roles to **view** policies:

  - **Microsoft Entra ID roles**: Security Reader, Security Operator, or Security Administrator
  - **Defender roles**: Security operations, Security data, Alerts \(manage\)

- One of the following roles to **create, edit, or remove** policies:

  - **Microsoft Entra ID roles**: At least Security Administrator
  - **Defender roles**: Security operations, Security data, Alerts \(manage\)

Tip

Use the least-privileged role that meets your needs. If your organization uses [Microsoft Entra Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure), request just-in-time role activation instead of permanent role assignments.

## Choose a correlation type

Before you create a rule, decide which correlation type fits your scenario. The following table describes the available options:

| Correlation type | Description | Example |
| --- | --- | --- |
| **Root UPN Prefix** | Correlates accounts with matching prefixes before the '@' symbol. | `user@acme.com` and `adm_user@acme.com` share the prefix `user`. |
| **Root UPN Suffix** | Correlates accounts with matching suffixes after the '@' symbol. | `user@acme.com` and `user_svc@acme.com` share the suffix `@acme.com`. |
| **Domain UPN** | Correlates accounts across different domains with the same username. | `user@acme.com` and `user@contoso.com`. |

## Add a correlation rule

To add an account correlation rule, follow these steps:

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Identities**.
2. Select **Account Correlation Rules**.
3. Select **Add Rule**.
4. In the wizard, enter a **Rule Name** \(up to 50 characters\). You can use letters, numbers, and the following special characters: `. - _ ! # ^ ~`.
5. Select the **Correlation Type** \(Root UPN Prefix, Root UPN Suffix, or Domain UPN\).
6. Enter the required values for the selected correlation type, such as prefixes, suffixes, or domains.
7. Review the summary, which includes the rule name, correlation type, and selected values.
8. Select **Submit** to create the rule. Correlation rule changes take effect within 12 hours.

## Edit a correlation rule

To change an existing account correlation rule, follow these steps:

1. On the **Account Correlation Rules** page, select the checkbox next to the rule you want to edit. You can select only one rule at a time.
2. Select **Edit**.
3. In the wizard, update the rule configuration as needed.
4. Review your changes, and then select **Save**. Changes take effect within 12 hours.

## Remove a correlation rule

To remove an account correlation rule, follow these steps:

1. On the **Account Correlation Rules** page, select the checkbox next to the rule you want to remove.
2. Select **Delete**.
3. In the confirmation prompt, select **Remove** to confirm, or **Cancel** to abort. Correlation rule changes take effect within 12 hours.

## Related content

- [Manage related identities and accounts](https://learn.microsoft.com/en-us/defender-for-identity/manage-related-identities-accounts)
- [View the identity inventory](https://learn.microsoft.com/en-us/defender-for-identity/identity-inventory)
