<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-content-management-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for content management in Configuration Manager

The following sample queries demonstrate how to join the most common content management views to other views.

## Joining software distribution and package status views

The following query lists all packages by package ID and package name, the current status of each package, the Network Abstraction Layer \(NAL\) path for the distribution point, and the last time the package was refreshed on the distribution point. The **v\_Package** view is joined to the **v\_PackageStatusDetailSumm** status view and **v\_DistributionPoint** software distribution view by using the **PackageID** columns.

```sql
    SELECT PCK.PackageID, PCK.Name as PackageName, PSD.Targeted, 
    PSD.Installed, PSD.Retrying, PSD.Failed, DP.ServerNALPath, 
    DP.LastRefreshTime 
    FROM v_Package PCK INNER JOIN v_PackageStatusDetailSumm PSD 
    ON PCK.PackageID = PSD.PackageID INNER JOIN v_DistributionPoint DP 
    ON PCK.PackageID = DP.PackageID 
    ORDER BY PCK.PackageID 
```

## See also

[Content management views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/content-management-views-configuration-manager)
