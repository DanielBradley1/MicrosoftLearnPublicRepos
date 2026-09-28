<!-- Source: https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/cloud-sync-migration-faq -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Migrate from Microsoft Entra Connect Sync to Cloud Sync FAQ

This article answers frequently asked questions about migrating from Microsoft Entra Connect Sync to Microsoft Entra Cloud Sync. For a full feature comparison, see the [decision guide](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/connect-to-cloud-sync-decision-guide). For step-by-step migration procedures, see [Migrating from Microsoft Entra Connect to Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/migrate-azure-ad-connect-to-cloud-sync).

## Migration eligibility and timeline

### How will I know when it's my turn to migrate to Cloud Sync?

Microsoft notifies your organization when it becomes eligible to begin migration. Eligibility is determined by factors including your current configuration and supported scenarios, and migration is rolled out in phases. When it's time, you receive clear instructions through official communication channels on how to proceed.

### What if my organization can't migrate within the recommended window?

If you're unable to migrate within the recommended timeframe, you need to request an exception. If approved, you can continue using your existing setup while working with Microsoft support or your account team to plan an appropriate migration timeline.

### How long does migration take?

Migration time varies depending on the number of objects and the complexity of your environment. Factors that influence duration include the number of users and groups, custom sync rules, and the number of organizational units \(OUs\) being migrated.

## Migration process

### How do I migrate from Connect Sync to Cloud Sync?

To prepare for migration, explore the following resources:

- [What is Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/what-is-cloud-sync)
- [Cloud Sync deep dive - how it works](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/concept-how-it-works)
- [Step-by-step migration guidance](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/migrate-azure-ad-connect-to-cloud-sync)

**Migration scenarios:**

- [Migrate to Microsoft Entra Cloud Sync for a synced Active Directory forest](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-pilot-aadc-aadccp)
- [Migrate Microsoft Entra Connect Sync group writeback v2 to Microsoft Entra Cloud Sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/migrate-group-writeback)
- [Microsoft Entra Cloud Sync vs. Microsoft Entra Connect Sync feature comparison](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/connect-to-cloud-sync-decision-guide#comparison-between-microsoft-entra-connect-and-cloud-sync)

### Can I run Connect Sync and Cloud Sync side by side?

Running Connect Sync and Cloud Sync side by side for the same objects isn't supported. During migration, use OU-based scoping so that each organizational unit is managed by only one sync tool at a time. This phased approach allows you to validate Cloud Sync on a subset of users before migrating additional OUs. For details on implementing this approach, see the [migration tutorial](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-pilot-aadc-aadccp).

### Can I test migration before fully rolling it out?

Yes. You can pilot the migration using a test Active Directory forest before committing to a full rollout. The tutorial [Migrate to Microsoft Entra Cloud Sync for a synced Active Directory forest](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-pilot-aadc-aadccp) walks you through a sandbox migration. You can also use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-on-demand-provision) to validate configuration changes by applying them to a single user.

## Configuration and customization

### Will my existing configurations be preserved during migration?

During migration, Connect Sync is placed in staging mode, allowing you to validate Cloud Sync before fully switching over. If needed, you can roll back to your previous configuration. Before migrating, back up your Microsoft Entra Connect configuration using the [import and export settings](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-import-export-config) feature.

### Will customizations carry over automatically?

The migration tool transfers supported configurations to Cloud Sync. After migration, run an [on-demand sync](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/how-to-on-demand-provision) to validate that configurations are working as expected before proceeding with the initial production sync. For details on which features and customizations are supported, see the [feature comparison](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/connect-to-cloud-sync-decision-guide#comparison-between-microsoft-entra-connect-and-cloud-sync).

## Feature support and compatibility

### Which Connect Sync features are currently supported in Cloud Sync?

For a full feature comparison, see the [Connect Sync to Cloud Sync decision guide](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/connect-to-cloud-sync-decision-guide#comparison-between-microsoft-entra-connect-and-cloud-sync). The decision guide includes a detailed comparison table covering 40+ capabilities and their availability in Cloud Sync.

### What happens if I rely on features that aren't yet available in Cloud Sync?

You aren't required to migrate until the features your organization depends on are supported in Cloud Sync. You can continue using Connect Sync in the interim. Once those features become available, you can proceed with migration. Check the [decision guide](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/connect-to-cloud-sync-decision-guide) regularly for updates on feature availability.

### What happens to hybrid authentication features like Pass-Through Authentication \(PTA\)?

Once you migrate to Cloud Sync, your hybrid authentication features that enable on-premises credentials to be used for accessing cloud resources continue to be available. Features like [Pass-Through Authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta) and [seamless single sign-on](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso) are configured separately from the sync tool and remain functional after migration through the Connect Sync configuration wizard.
