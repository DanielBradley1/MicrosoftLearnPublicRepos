<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/mto-troubleshoot -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Troubleshoot multitenant management service issues

This article addresses potential issues that might arise as you use the multitenant management in Microsoft Defender. It provides guidance on how to troubleshoot these issues.

## Problem adding or removing tenants

When adding or removing tenants, you might encounter errors like the following:

![Screenshot of error message while adding a tenant](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/add-tenants-error-small.png)

[![Screenshot of error message while removing a tenant](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/remove-tenants-error-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/remove-tenants-error.png#lightbox)

The issue is resolved by refreshing the page and trying again.

## Some tenants are missing from the list

When loading the tenant list on the Settings page, you get the following error message:

[![Screenshot of error message where only some of the tenants are correctly loaded on the page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/partial-tenants-error-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/partial-tenants-error.png#lightbox)

The issue is due to [conditional access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) requiring multifactor authentication \(MFA\) on your Azure Resource Manager app.

To resolve this issue, add *Microsoft 365 Security and Compliance Center app \(80ccca67-54bd-44ab-8625-4b79c4dc7775\)* to the same conditional access policy as your Azure Resource Manager app. This mitigation applies MFA on the origin tenant when a user tries to sign in to the Microsoft Defender portal.

Here’s an example of the policy setting in the Microsoft Entra admin center.

[![Screenshot of a conditional access policy settings page](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/ca-policy-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/ca-policy.png#lightbox)

## Content assignment failure in cross-cloud tenant management

You see the following error when assigning content to distribution profiles:

[![Screenshot of permissions error when assigning content to tenants](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/tenant-perms-error.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mto-troubleshoot/tenant-perms-error.png#lightbox)

When a cross-cloud tenant is added to a distribution profile and subsequently removed from cross-cloud visibility, the tenant's name is removed from the tenant list and won't be available for content management, which causes the error. This is a recognized limitation of cross-cloud tenant management and is currently under review.

## Related content

- [Set up Microsoft Defender multitenant management](https://learn.microsoft.com/en-us/defender-xdr/mto-requirements)
- [Manage tenants](https://learn.microsoft.com/en-us/defender-xdr/mto-tenants)
