<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-discovery-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for discovery in Configuration Manager

The following sample queries demonstrate how to join Configuration Manager discovery views to each other and views from other view categories. Discovery views use the **ResourceID** column when joining to other views.

## Joining discovery views

The following query retrieves all resources and their associated IP addresses. The query joins the **v\_R\_System** and **v\_RA\_System\_IPAddresses** discovery views by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, SYSIP.IP_Addresses0 
    FROM v_R_System SYS INNER JOIN v_RA_System_IPAddresses SYSIP 
    ��ON SYS.ResourceID = SYSIP.ResourceID 
    ORDER BY SYS.Netbios_Name0 
```

## Joining resource and inventory views

The following query retrieves all resources that have a local fixed disk listed in inventory and displays the NetBIOS name, the free disk space, and sorts the data in ascending order by free disk space. The query joins the **v\_R\_System** discovery view and the **v\_GS\_LOGICAL\_DISK** hardware inventory view by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, LD.FreeSpace0 
    FROM v_R_System SYS INNER JOIN v_GS_LOGICAL_DISK LD 
    ��ON SYS.ResourceID = LD.ResourceID 
    WHERE LD.Description0 LIKE 'Local fixed disk' 
    ORDER BY LD.FreeSpace0 
```

## Joining resource and collection views

The following query retrieves all resources in the **All Systems** collection and displays the NetBIOS name, domain name, and associated IP addresses. The query results are sorted by NetBIOS name. The query joins the **v\_R\_System** and **v\_RA\_System\_IPAddresses** discovery views, and joins the **v\_FullCollectionMembership** collection view by using the **ResourceID** column.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, FCM.Domain, SYSIP.IP_Addresses0 
    FROM v_R_System SYS INNER JOIN v_FullCollectionMembership FCM 
    ON SYS.ResourceID = FCM.ResourceID 
    INNER JOIN v_RA_System_IPAddresses SYSIP 
    ON SYS.ResourceID = SYSIP.ResourceID 
    WHERE FCM.CollectionID = 'SMS00001' 
    ORDER BY SYS.Netbios_Name0 
```

## Joining resource, software updates, and status views

The following query retrieves all resources that have performed a scan for software updates, the last scan time, the last scan state, and the Windows Update Agent version on the client. The query joins the **v\_R\_System** discovery view and **v\_UpdateScanStatus** software updates view by using the **ResourceID** column, and it uses LEFT OUTER JOIN between the **v\_UpdateScanStatus** software updates view and **v\_StateNames** status view by using the **LastScanState** and **StateID** columns. The state message topic types are filtered by **TopicType = 501**, which indicates scan-state messages.

Note

The state topic type, state ID, state name, and state description for all Configuration Manager state messages are listed in the **v\_StateNames** view.

```sql
    SELECT DISTINCT v_R_System.Netbios_Name0 AS [Computer Name], 
    ��v_UpdateScanStatus.LastScanTime AS [Last Scan], 
    ��v_UpdateScanStatus.LastWUAVersion AS [WUA Version], 
    ��v_StateNames.StateName AS [Last Scan State] 
    FROM v_UpdateScanStatus INNER JOIN v_R_System ON 
    ��v_UpdateScanStatus.ResourceID = v_R_System.ResourceID LEFT OUTER JOIN 
    ��v_StateNames ON v_UpdateScanStatus.LastScanState = v_StateNames.StateID 
    WHERE (v_StateNames.TopicType = 501) 
```

## See also

[Discovery views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager)
