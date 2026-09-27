<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-client-status-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for client status in Configuration Manager

The following sample queries demonstrate how to join common client status views to other views.

## Joining client status and collection views

This query lists each client computer in the site, the last time it requested policy, and the collections to which the computer belongs. The query uses the **v\_CH\_PolicyRequestHistory** view to read the last policy request time and joins, using the **ResourceID** column to the **v\_ClientCollectionMembers** view.

```sql
    SELECT        dbo.CH_PolicyRequestHistory.MachineID AS ResourceID, dbo.CH_PolicyRequestHistory.RequestTime, dbo.v_ClientCollectionMembers.CollectionID
    FROM            dbo.CH_PolicyRequestHistory INNER JOIN
                             dbo.v_ClientCollectionMembers ON dbo.CH_PolicyRequestHistory.MachineID = dbo.v_ClientCollectionMembers.ResourceID
```

## See also

[Client status views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/client-status-views-configuration-manager)
