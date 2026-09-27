<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-endpoint-protection-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for endpoint protection in Configuration Manager

The following sample queries demonstrate how to join the most common Endpoint Protection views to other views.

## Joining endpoint protection and collection views

The following query lists the deployment state of the Endpoint Protection client on all computers by using the **v\_GS\_EPDeploymentState** view. For each computer, it also adds the client name and site code by joining by **ResourceID** to the **v\_ClientCollectionMembers** view.

```sql
    SELECT   v_GS_EPDeploymentState_1.ResourceID, v_ClientCollectionMembers.Name, v_ClientCollectionMembers.SiteCode, 
                     v_GS_EPDeploymentState_1.LastMessageTime, v_GS_EPDeploymentState_1.DeploymentState, v_GS_EPDeploymentState_1.Error, 
                     v_GS_EPDeploymentState_1.ErrorCode
    FROM    v_GS_EPDeploymentState AS v_GS_EPDeploymentState_1 INNER JOIN
            v_ClientCollectionMembers ON v_GS_EPDeploymentState_1.ResourceID = v_ClientCollectionMembers.ResourceID
```

## See also

[Endpoint protection views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/endpoint-protection-views-configuration-manager)
