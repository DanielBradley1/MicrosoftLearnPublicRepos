<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-client-deployment-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for client deployment in Configuration Manager

The following sample queries demonstrate how to join the most common client deployment views to other views.

The following sample query demonstrates how to join client deployment views with other views. Client deployment views will most often use the **MachineID** column, which is the same as the **ResourceID** column in other views, and **NetBiosName** column when joining to other views.

## Joining client deployment and discovery views

This query retrieves the NetBIOS name for client computers that have provided client deployment status, the user name, assigned site, time of last state message, and state name. The results are sorted by deployment state and then NetBIOS name. The query joins the **v\_ClientDeploymentState** client deployment view with the **v\_R\_System** discovery view by using the **ResourceID** column, and the **v\_ClientDeployment** view with the **v\_StateNames** status view by using the **LastMessageStateID** and **StateID** columns, respectively. The retrieved information is filtered by the topic type of **800**, which includes only state messages for client deployment.

```sql
    SELECT v_ClientDeploymentState.NetBiosName AS Computer, 
    ��v_R_System.User_Name0 AS [User], 
    ��v_ClientDeploymentState.AssignedSiteCode AS [Assigned Site], 
    ��v_ClientDeploymentState.LastMessageTime AS [Last Message], 
    ��v_StateNames.StateName AS State 
    FROM v_ClientDeploymentState INNER JOIN v_R_System ON 
    ��v_ClientDeploymentState.SMSID = v_R_System.SMS_Unique_Identifier0 INNER JOIN v_StateNames ON 
    ��v_ClientDeploymentState.LastMessageStateID = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 800) 
    ORDER BY State, Computer 
```

## See also

[Client deployment views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/client-deployment-views-configuration-manager)
