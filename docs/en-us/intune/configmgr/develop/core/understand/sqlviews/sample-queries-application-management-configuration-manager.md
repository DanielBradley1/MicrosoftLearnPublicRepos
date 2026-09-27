<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-application-management-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for application management in Configuration Manager

The following sample queries demonstrate how to join the most common application management views to other views.

## Joining package and program deployment and collection views

The following query lists all package and program deployments by advertisement ID, advertisement name, and the collection that was targeted for the deployment. The **v\_Advertisement** view is joined to the **v\_Collection** view by using the **AdvertisementID** column.

```sql
    SELECT ADV.AdvertisementID, ADV.AdvertisementName, 
    COL.CollectionID, COL.Name as CollectionName 
    FROM v_Advertisement ADV INNER JOIN v_Collection COL 
    ON ADV.CollectionID = COL.CollectionID 
    ORDER BY ADV.AdvertisementID 
```

## See also

[Application management views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/application-management-views-configuration-manager)
