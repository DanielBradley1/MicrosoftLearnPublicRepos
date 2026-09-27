<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-for-migration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Plan for migration to Configuration Manager current branch

*Applies to: Configuration Manager \(current branch\)*

Before you migrate data to a Configuration Manager current branch destination hierarchy, make sure that you are familiar with sites and hierarchies in Configuration Manager. For more about sites and hierarchies, see [Fundamentals of Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals).

Install a Configuration Manager current branch hierarchy to be the destination hierarchy before you migrate data from a supported source hierarchy.

After you install the destination hierarchy, set up the management features and functions that you want to use in your destination hierarchy before you start to migrate data.

Additionally, you might have to plan for overlap between the source hierarchy and your destination hierarchy. For example, you might set up the source hierarchy to use the same network locations or boundaries as your destination hierarchy, and you then install new clients to your destination hierarchy and use automatic site assignment. In this scenario, because a newly installed Configuration Manager client can select a site to join from either hierarchy, the client might incorrectly assign to your source hierarchy. Therefore, plan to assign each new client in the destination hierarchy to a specific site in that hierarchy instead of using automatic site assignment.

For more about site assignments, see [Client site assignment considerations](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/interoperability-between-different-versions#client-site-assignment-considerations) in [Interoperability between different versions of Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/interoperability-between-different-versions).

Use the following articles to help you plan how to migrate a supported source hierarchy to a Configuration Manager destination hierarchy:

- [Prerequisites for migration](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/prerequisites-for-migration)
- [Administrator checklists for migration planning](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/administrator-checklists-for-migration-planning)
- [Determine whether to migrate data to Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/determine-whether-to-migrate-data)
- [Plan a source hierarchy strategy](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-a-source-hierarchy-strategy)
- [Administrator checklists for migration planning](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/administrator-checklists-for-migration-planning)
- [Plan a client migration strategy](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-a-client-migration-strategy)
- [Plan a content deployment migration strategy](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-a-content-deployment-migration-strategy)
- [Plan for the migration of Configuration Manager objects to Configuration Manager current branch](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-for-the-migration-of-objects)
- [Plan to monitor migration activity](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-to-monitor-migration-activity)
- [Plan to complete migration](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/planning-to-complete-migration)
