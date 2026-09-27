<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-inventory-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Sample queries for software inventory in Configuration Manager

The following sample queries demonstrate how the Configuration Manager software inventory views can be joined to other views to retrieve specific data. The software inventory views are typically joined to other views by using the **ProductID**, **FileID**, and **ResourceID** columns.

## Joining software inventory views

The following query lists all software files for the Configuration Manager product that have been inventoried on Configuration Manager clients. The **v\_GS\_SoftwareProduct** and **v\_GS\_SoftwareFile** views are joined by using the **ProductID** columns.

```sql
    SELECT DISTINCT SF.FileName, SF.FileDescription, SF.FileVersion 
    FROM v_GS_SoftwareProduct SP INNER JOIN v_GS_SoftwareFile SF 
    ��ON SP.ProductID = SF.ProductId 
    WHERE SP.ProductName = 'Configuration Manager' 
    ORDER BY SF.FileName 
```

## Joining software inventory and discovery views

The following query lists all inventoried products and the associated files for a computer with the NetBIOS name of COMPUTER1. The **v\_R\_System** and **v\_GS\_SoftwareProduct** views are joined by using the **ResourceID** column, and the **v\_GS\_SoftwareProduct** and **v\_GS\_SoftwareFile** views are joined by using the **ProductID** columns.

```sql
    SELECT DISTINCT SP.ProductName, SF.FileName 
    FROM v_R_System SYS INNER JOIN v_GS_SoftwareProduct SP 
    ��ON SYS.ResourceID = SP.ResourceID INNER JOIN v_GS_SoftwareFile SF 
    ��ON SP.ProductID = SF.ProductId 
    WHERE SYS.Netbios_Name0 = 'COMPUTER1' 
    ORDER BY SP.ProductName 
```

## Joining software inventory, discovery, and hardware inventory views

The following query lists all computers that have Microsoft Office installed and have less than 1 GB of free space on the local C drive. The **v\_GS\_SoftwareFile** and **v\_SoftwareProduct** views are joined by the **ProductID** column, and the **v\_GS\_LOGICAL\_DISK** and **v\_R\_System** views are joined to **v\_GS\_SoftwareFile** by using the **ResourceID** columns.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, SYS.User_Domain0, LD.FreeSpace0 
    FROM v_GS_SoftwareFile SF INNER JOIN v_SoftwareProduct SP 
    ��ON SF.ProductId = SP.ProductID 
    ��INNER JOIN v_GS_LOGICAL_DISK LD 
    ��ON SF.ResourceID = LD.ResourceID 
    ��INNER JOIN v_R_System SYS 
    ��ON SF.ResourceID = SYS.ResourceID 
    WHERE (LD.Description0 = 'local Fixed Disk') 
    ��AND (SP.ProductName LIKE 'Microsoft Office%') 
    ��AND (LD.FreeSpace0 < 1000) 
    ��AND (LD.DeviceID0 = 'C:') 
```

## Joining software inventory, discovery, and software metering views

The following query lists all files that have been metered through software metering rules and sorted first by NetBIOS name, and then by product name, and then by file name. The **v\_GS\_SoftwareProduct** and **v\_MeteredFiles** views are joined by the **ProductID** column, and the **v\_GS\_SoftwareProduct** and **v\_R\_System** views are joined by using the **ResourceID** columns.

```sql
    SELECT SYS.Netbios_Name0, SP.ProductName, SP.ProductVersion, 
    ��MF.FileName, MF.MeteredFileVersion 
    FROM v_GS_SoftwareProduct SP INNER JOIN v_MeteredFiles MF 
    ��ON SP.ProductID = MF.MeteredProductID INNER JOIN v_R_System SYS 
    ��ON SP.ResourceID = SYS.ResourceID 
    ORDER BY SYS.Netbios_Name0, SP.ProductName, MF.FileName 
```

## See also

[Software inventory views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/software-inventory-views-configuration-manager)
