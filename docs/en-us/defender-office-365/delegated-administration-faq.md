<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/delegated-administration-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Frequently asked questions - Delegated administration

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

This article provides frequently asked questions and answers about delegated administration tasks in Microsoft 365 for Microsoft partners and resellers. Delegated administration includes the ability to manage the built-in security features for all cloud mailboxes in other tenants \(companies\).

## I'm a reseller and I need to manage my customer tenants. How does this work?

If you're a Microsoft partner or reseller, and you've signed up to be a Microsoft Cloud Solution Provider \(CSP\), you can request *delegated administration* capabilities in your customer's Microsoft 365 organization. For more information, see the following articles:

- [Cloud Solution Provider program](https://learn.microsoft.com/en-us/partner-center/csp-overview)
- [Obtain permissions to manage a customer's service or subscription](https://learn.microsoft.com/en-us/partner-center/customers-revoke-admin-privileges).

## I'm a customer, not a reseller. How can I set up delegated administrator for my subtenants?

Delegated administration is only available for resellers and partners. However, there's a sample PowerShell script to help you view policies in your subtenants \(companies\). For more information, see [Sample script to view Built-in security add-on for on-premises mailboxes settings for multiple on-premises organizations](https://learn.microsoft.com/en-us/exchange/standalone-eop/sample-script-standalone-eop-settings-to-multiple-tenants).

## Can I prevent my subtenant admin from modifying my policy?

No. Microsoft 365 doesn't currently have this capability.

## Can I get consolidated reporting across all of my subtenants?

Consolidated reporting across the companies you manage isn't available in Microsoft 365 admin center reports. However, you can get reports by using [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview).
