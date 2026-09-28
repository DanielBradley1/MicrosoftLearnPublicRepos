<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/education-solution-faq -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Microsoft Education Solution Guide – FAQ

## Getting started

### How do I start with Microsoft Education Solution Guide and choose the right track?

Here's a step-by-step approach:

1. [Verify academic eligibility for Microsoft Education subscriptions.](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/verify-academic-eligibility)
2. Identify your license tier:

   - A1 \(Baseline\): Tier with essential services
   - A3 \(Standard\): Adds advanced identity, security, and device management
   - A5 \(Advanced\): Complete security, compliance, and analytics suite

3. Follow the deployment sequence

   - Baseline → Standard → Advanced \(each phase builds on the previous\)
   - Complete all sections within each phase:

     - Setup \(Tenant Configuration\)
     - Identity
     - Applications
     - Security and Compliance
     - Devices

Start here: [Microsoft Education Solution Guide overview](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start/a-start)

Note

Articles for Standard \(A3\) or Advanced \(A5\) licenses only include configuration steps specific to that license. However, each license also provides all features from the lower-level licenses, even though those steps aren't repeated in the higher license articles.

## Licensing and features

### Where can I compare A1, A3, and A5 for Education?

Use [Microsoft 365 Education licenses](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start/all-license).

## Identity and user management

### How do I set up School Data Sync \(SDS\)?

[School Data Sync \(SDS\)](https://learn.microsoft.com/en-us/schooldatasync/school-data-sync-overview) is a free service for education that syncs Student Information System \(SIS\) data with Microsoft 365.

- [Review SDS Planning Checklist](https://learn.microsoft.com/en-us/schooldatasync/planning-checklist)
- [Review SDS Identity Matching Rules](https://learn.microsoft.com/en-us/schooldatasync/identity-matching)
- [Connect data to SDS](https://learn.microsoft.com/en-us/schooldatasync/connect-data?tabs=sdsv21csv%2Ceditcsv)

### What’s the recommended identity setup for education tenants?

See:

- Phase 1 - [Baseline \(A1\) Identity](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-baseline/start-identity)
- Phase 2 - [Standard \(A3\) Identity](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-standard/start-std-identity)
- Phase 3 - [Advanced \(A5\) Identity](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-advanced/start-adv-identity)

### How do I sync my on-premises Active Directory?

After you secure and configure your network, you're ready to [sync your on-premises Active Directory with Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad). This step is crucial for managing your users and groups in one place. First, [choose the right authentication method](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#choose-your-authentication-method) for your Microsoft Entra hybrid identity solution. Then, [install Microsoft Entra Connect Sync](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#install-microsoft-entra-connect-sync) or [configure Active Directory Federated Services \(ADFS\)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/setup/baseline-setup-sync-on-premises-ad#configure-active-directory-federated-services-ad-fs).

## Devices and Intune for Education

### How do I set up shared classroom devices quickly? How do I use Intune for Education?

Use [Phase 1 - Baseline \(A1\) Devices Deployment Guide](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-baseline/start-devices) and Phase 2 - [Standard \(A3\) Devices Deployment Guide](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-standard/start-std-devices) for streamlined provisioning.

## Core Apps: OneDrive, SharePoint, Teams, Viva

### What’s the best practice for OneDrive and SharePoint security in EDU?

See [Configure security and access control in OneDrive and SharePoint for education](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/applications/baseline-apps-odsp-security-access).

## AI and Copilot in Education

### How do I enable or restrict AI features for classrooms?

See [Manage Microsoft 365 for Education AI Features](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/manage-microsoft-365-education-ai-features).

## Accessibility and inclusive learning

### Where can I find accessibility guidance?

Explore [Create an inclusive classroom with Microsoft accessibility tools](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/baseline-reference-accessibility).
