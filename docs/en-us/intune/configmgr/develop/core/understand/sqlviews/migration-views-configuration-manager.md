<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/migration-views-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Migration views in Configuration Manager

Migration views contain information about the tasks involved in migrating to a Configuration Manager site.

For more information about migration in Configuration Manager, see [Migrating hierarchies in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/core/migration/configuring-source-hierarchies-and-source-sites-for-migration).

## Migration views

The views for migration are shown in this section:

### v\_MIG\_SiteMapping

Lists the current migration source site. **SiteMappingID** is used to uniquely identify a migration source site.

Note

If **IsDecommissioned** or **IsDeleted** has a value of true, it means this migration source site has either stopped migration data gathering or is deleted.

This view can be joined to other views by using the **SourceSiteCode** column.

### v\_MIG\_SiteRelation

This view is no longer used in Configuration Manager.

### v\_MIG\_MigratedDPs

Lists the shared distribution points from source sites. **AttachingSiteCode** is the source site code that the distribution point belongs to in the source hierarchy, and **SiteCode** is the site code of the destination site. This view can be joined to other views by using the **NALPath** column.

### v\_MIG\_JobEntity

Lists the relationship between a migration job and objects for migration. This is useful for listing the objects contained in a migration job. This view can be joined to other views by using the **JobID** column.

### v\_MIG\_Job

Lists the migration jobs that have been created. The **JobID** column uniquely identifies a migration job and is usually used to join with other migration job related tables or views.

### v\_MIG\_EntityState

Lists the state of migration objects. This view can be joined to other views by using the **EntityID** column.

### v\_MIG\_EntityReference

Lists the migration object dependency relationship. This can be used to find out the dependent objects for an object. This view can be joined to other views by using the **EntityID** column.

### v\_MIG\_Entities

Lists the objects available for migration in the source site. This view can be joined to other views by using the **EntityID** column.

### v\_MIG\_Dashboard

Lists the overall migration status from a source site hierarchy. Migration status in the Configuration Manager console information is based on this view.

### v\_MIG\_Collections

Lists collection information in a source site. The **SiteID** column represents the source site ID. This view can be joined to other views by using the **SiteID** column.

### v\_MIG\_ClientState

This view is no longer used in Configuration Manager.

### v\_MIG\_Clients

This view is no longer used in Configuration Manager.

### v\_MIG\_ClientGroupState

This view is no longer used in Configuration Manager.

### vSMS\_MigrationSourceSite

Lists the source site information. This view is similar to **v\_MIG\_SiteMapping**, but only contains information about the source site.

### vSMS\_MigrationCollectionInfo

This view is based on **v\_MIG\_Collections** and queries the list of collection information in a source site. Use this view to query collection information.

## See also

[SQL Server views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager)
