<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/migrate-from-ata-overview -->
<!-- Sitemap-Last-Modified: 2026-08-19 -->

# Migrate from Advanced Threat Analytics \(ATA\) to Microsoft Defender for Identity

Important

Advanced Threat Analytics \(ATA\) has reached end of life. Mainstream support ended on January 12, 2021, and extended support ended on January 13, 2026. ATA no longer receives updates of any kind, including security updates, and is no longer supported by Microsoft. For more information, see [Advanced Threat Analytics 1.X lifecycle](https://learn.microsoft.com/en-us/lifecycle/products/advanced-threat-analytics-1x).

We strongly recommend migrating to Microsoft Defender for Identity as soon as possible. For migration guidance, see [Migrate from Advanced Threat Analytics \(ATA\) to Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/migrate-from-ata-overview).

This article describes how to migrate from an existing ATA installation to a Microsoft Defender for Identity sensor. Before you begin, make sure your environment meets the [Defender for Identity prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/prerequisites). The migration includes the following steps:

- Review and confirm Defender for Identity service prerequisites
- Document your existing ATA configuration
- Plan your migration
- Set up and configure your Defender for Identity service
- Perform post-migration checks and verifications
- Decommission ATA

ATA is a standalone on-premises solution with multiple components, such as the ATA Center that requires dedicated hardware on-premises.

Defender for Identity is a cloud-based security solution that uses your on-premises Active Directory signals. Defender for Identity is highly scalable and is frequently updated.

In contrast to the ATA Lightweight Gateway, the Defender for Identity sensor also uses data sources such as Event Tracing for Windows \(ETW\) enabling Defender for Identity to deliver extra detections. Defender for Identity also provides:

- Support for [multi-forest environments](https://learn.microsoft.com/en-us/defender-for-identity/deploy/multi-forest)
- [Microsoft Secure Score posture assessments](https://learn.microsoft.com/en-us/defender-for-identity/security-assessment)
- Direct integrations with other services like Microsoft Defender for Cloud Apps and Microsoft Entra for a hybrid view of what's taking place in both on-premises and hybrid environments
- And more

Defender for Identity also uses the Microsoft 365 security portfolio to automatically analyze cross-domain threat data, building a complete picture of each attack in a single dashboard.

Important

This migration guide is designed for Defender for Identity sensors only, and not standalone sensors.

While you can migrate to Defender for Identity from any ATA version, your ATA data isn't migrated. Therefore, we recommend that you plan to retain your ATA Data Center and any alerts required for ongoing investigations until all ATA alerts are closed or remediated.

Note

The final release of ATA is [Update 3 for Microsoft Advanced Threat Analytics 1.9](https://support.microsoft.com/help/4568997/update-3-for-microsoft-advanced-threat-analytics-1-9). ATA ended Mainstream Support on January 12, 2021. Extended Support will continue until January 2026. For more information, read [End of mainstream support for Advanced Threat Analytics](https://techcommunity.microsoft.com/t5/microsoft-security-and/end-of-mainstream-support-for-advanced-threat-analytics-january/ba-p/1539181).

## Prerequisites

To migrate from ATA to Defender for Identity, you must have an environment and domain controllers that meet Defender for Identity sensor requirements. For more information, see [Microsoft Defender for Identity prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/prerequisites).

Make sure that all the domain controllers you plan to use have sufficient internet access to the Defender for Identity service. For more information, see [Configure endpoint proxy and internet connectivity settings](https://learn.microsoft.com/en-us/defender-for-identity/configure-proxy).

## Plan your migration

Before starting the migration, gather all of the following information:

- **Account details for your [Directory Services](https://learn.microsoft.com/en-us/defender-for-identity/directory-service-accounts) account**.
- **Syslog [notification settings](https://learn.microsoft.com/en-us/defender-for-identity/notifications)**.
- **Email [notification settings](https://learn.microsoft.com/en-us/defender-for-identity/notifications)**.
- **All [ATA role group memberships](https://learn.microsoft.com/en-us/advanced-threat-analytics/ata-role-groups)**.
- **[VPN integration details](https://learn.microsoft.com/en-us/defender-for-identity/vpn-integration)**.
- **Alert exclusions**: Exclusions are not transferable from ATA to Defender for Identity, so details of each exclusion are required to [replicate the exclusions as Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/exclusions) in Microsoft Defender.
- **Account details for entity tags**: If you don't already have dedicated entity tags, create new ones for use with Defender for Identity. For more information, see [Defender for Identity entity tags in Microsoft Defender](https://learn.microsoft.com/en-us/defender-for-identity/entity-tags).
- **A complete list of all entities, such as computers, groups, or users, that you want to manually tag as *Sensitive* entities**: For more information, see [Defender for Identity entity tags in Microsoft Defender](https://learn.microsoft.com/en-us/defender-for-identity/entity-tags).
- **[Report scheduling and classic reports](https://learn.microsoft.com/en-us/defender-for-identity/classic-reports)**: Including a list of all reports and scheduled timing.

Caution

Don't uninstall the ATA Center until all ATA Gateways are removed. Uninstalling the ATA Center with ATA Gateways still running leaves your organization exposed with no threat protection.

## Move to Defender for Identity

Use the following steps to migrate to Defender for Identity:

1. [Create your new Defender for Identity workspace](https://learn.microsoft.com/en-us/defender-for-identity/deploy-defender-identity#start-using-microsoft-defender-xdr).
2. Uninstall the ATA Lightweight Gateway on all domain controllers.
3. Install the Defender for Identity Sensor on all domain controllers:

   1. [Download and install the Defender for Identity sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor) on your domain controllers.

4. [Configure the your Defender for Identity sensor](https://learn.microsoft.com/en-us/defender-for-identity/configure-sensor-settings).

After the migration is complete, allow two hours for the Defender for Identity sensor initial synchronization to complete before starting validation tasks.

## Validate your migration

In Microsoft Defender, check the following areas to validate your migration:

- Review any [Defender for Identity health alerts](https://learn.microsoft.com/en-us/defender-for-identity/health-alerts) for signs of service issues.
- Review Defender for Identity [sensor error logs](https://learn.microsoft.com/en-us/defender-for-identity/troubleshooting-using-logs) for any unusual errors.

## Post-migration activities

After completing your migration to Defender for Identity, do the following to clean up your legacy ATA resources:

1. Make sure that you've recorded or remediated all existing ATA alerts. Existing ATA security alerts aren't imported to Defender for Identity with the migration.
2. Do one or both of the following:

   - **Decommission the ATA Center**: We recommend keeping ATA data online for a period of time.
   - **Back up Mongo DB**: If you want to keep the ATA data indefinitely. For more information, see [Backing up the ATA database](https://learn.microsoft.com/en-us/advanced-threat-analytics/ata-database-management#backing-up-the-ata-database).

## Related content

- [View and manage security alerts](https://learn.microsoft.com/en-us/defender-for-identity/understanding-security-alerts)
