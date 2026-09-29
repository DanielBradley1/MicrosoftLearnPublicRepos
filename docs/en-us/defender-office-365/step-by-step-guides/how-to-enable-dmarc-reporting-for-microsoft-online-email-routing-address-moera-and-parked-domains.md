<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/how-to-enable-dmarc-reporting-for-microsoft-online-email-routing-address-moera-and-parked-domains -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Enable DMARC reporting for Microsoft Online Email Routing Address \(MOERA\) and parked domains

Best practice for domain email security protection is to protect yourself from spoofing using Domain-based Message Authentication, Reporting, and Conformance \(DMARC\). Enabling DMARC for your domains should be the first step. For instructions, see [Set up DMARC to validate the From address domain for cloud senders](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure).

This article explains how to configure DMARC for your `onmicrosoft.com` \(MOERA\) domain and parked custom domains, which aren't covered in [Set up DMARC to validate the From address domain for cloud senders](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure). These domains aren't used for email, but could be exploited by attackers if the domains remain unprotected:

- Your `onmicrosoft.com` domain, also known as the Microsoft Online Email Routing Address \(MOERA\) domain.
- Parked custom domains that you're currently not using for email yet.

## Prerequisites

Before you begin, make sure you have the following items:

- Microsoft 365 admin center and access to your DNS provider hosting your domains.
- Sufficient permissions as a Global Administrator<sup>\*</sup> to make the appropriate changes in the Microsoft 365 admin center.
- 10 minutes to complete the steps in this article.

Important

<sup>\*</sup> Microsoft strongly advocates for the principle of least privilege. Assigning accounts only the minimum permissions necessary to perform their tasks helps reduce security risks and strengthens your organization's overall protection. Global Administrator is a highly privileged role that you should limit to emergency scenarios or when you can't use a different role.

## Activate DMARC for a MOERA domain

Use the following steps to add a DMARC TXT record for your MOERA domain in the Microsoft 365 admin center:

1. Open the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).
2. On the left-hand navigation, select **Show All**.
3. Expand **Settings** and press **Domains**.
4. Select your tenant domain \(for example, contoso.onmicrosoft.com\).
5. On the page that loads, select **DNS records**.
6. Select **+ Add record**.
7. A flyout opens. Ensure that the selected Type is **TXT \(Text\)**.
8. Add `_dmarc` as **TXT name**.
9. Add your specific DMARC value. For more information, see [Syntax for DMARC TXT records](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure#syntax-for-dmarc-txt-records).
10. Press **Save**.

## Activate DMARC for parked domains

Use the following steps to add a DMARC TXT record for your parked custom domains:

1. Check if SPF is already configured for your parked domain. For instructions, see [SPF TXT records for custom cloud domains](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure#spf-txt-records-for-custom-domains-in-microsoft-365).
2. Contact your DNS Domain provider.
3. Ask to add this DMARC txt record with your appropriate email addresses: `v=DMARC1; p=reject; rua=mailto:d@rua.contoso.com;ruf=mailto:d@ruf.contoso.com`.

## Next Steps

Wait until the DNS changes propagate, and then try to spoof the MOERA domain or any parked custom domain where you added the DMARC record. Check whether the spoofing attempt is blocked based on the DMARC record you added for the domain you tested, and verify that you receive a DMARC report.

## Related content

[Set up SPF to identify valid email sources for your custom cloud domains](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-spf-configure).

[Set up DMARC to validate the From address domain for cloud senders](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dmarc-configure).
