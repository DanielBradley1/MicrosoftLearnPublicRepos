<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Schema View Mapping

In Configuration Manager, the names of views and columns are designed to be as close to the SMS Provider Windows Management Instrumentation \(WMI\) schema as possible. Because the views names and view column names must be valid SQL Server identifiers, there are some discrepancies between WMI and SQL Server names. However, in most cases the following rules can be applied to convert a WMI class name to its corresponding SQL Server view:

- Replace SMS\_ with v\_ for the start of the view name.
- If a view name is longer than 30 characters, it's truncated.
- WMI property names are the same in the SQL Server views for non-inventory or discovery classes.

  Beyond this, the following class families have a differing nomenclature for their view equivalents:

## System Inventory Views

The syntax for the current inventory group is v\_GS*\_<group name>* \(for example, v\_GS\_Tape\_Drive\).

The syntax for the history inventory group is v\_HS*\_<group name>*\(for example, v\_HS\_Tape\_Drive\).

Note

There is no equivalent Extended History view \(WMI class SMS\_GEH\_System*\_<group name>*\) because it is implemented as a stored procedure.

## Custom Architecture Views

The syntax for the current groups is v\_G*<resource type number>\_<group name>* \(for example, v\_G6\_VendorData\).

In the previous example, it's assumed that a new inventory architecture, for example VendingMachine, has been added to the system and assigned the resource type number 6 and VendorData is an inventory group that is associated with the architecture. The resource type number might be related to the resource type name and its group's classes using the schema information views.

The corresponding history inventory classes will use the suffix H in place of G.

## Discovery Views

The views for discovery data differ from their WMI counterparts in that array properties in WMI are represented as separate views. For example, for the System resource, all the scalar properties are contained in the view v\_R\_System. There are many view tables for the array values, such as v\_RA\_System\_IPAddresses and v\_RA\_System\_MACAddresses. The general rules for the syntax of these views are:

- Scalar class: v\_R*\_<resource type name>*
- Array class: v\_RA**<architecture name>\\*<group name>*

  Each array property view has just two columns: ResourceID and a column that contains the actual data. For example, for the view v\_RA\_System\_IPAddresses the data column is v\_RA\_System\_IPAddresses. As with inventory groups for the discovery view, column names differ from those of WMI classes. Each column ends with a zero character, ensuring uniqueness with SQL Server reserved words. In general, this is the only difference between the WMI and view column names although there are exceptions.

  For more information about the classes that Configuration Manager supports, see [Configuration Manager Reference](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/configuration-manager-reference).

## See Also

[Configuration Manager Schema Overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-overview) [Configuration Manager Schema SQL Views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-sql-views) [Configuration Manager SQL View Security](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sql-view-security)
