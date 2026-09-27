<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-sql-views -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Schema SQL Views

In Configuration Manager, a number of schema information views are created to get information about the names of all the available views and the schema for the inventory and discovery classes. These are particularly useful for determining the names for custom inventory resource type \(architecture\) tables. The following table shows a list of these schema information views.

| View | Description | Sample Query |
| --- | --- | --- |
| v\_SchemaViews | Lists all the views in the view schema family. | `Select ViewName, Type from v_SchemaViews order by ViewName` |
| v\_ResourceMap | Lists the resource type views. | `select * from v_ResourceMap` |
| v\_ResourceAttributeMap | Lists attributes for each resource type. | `select * from v_ResourceAttributeMap` |
| v\_GroupMap | Lists inventory groups for each inventory architecture. | `select * from v_GroupMap` |
| v\_GroupAttributeMap | Lists attributes for each inventory group. | `select * from v_GroupAttributeMap` |
| v\_ReportViewSchema | Parallel to the `SMS_ReportViewSchema` class, this view lists all the classes and properties. | `select * from v_ReportViewSchema` |

For more information about how the SQL views map to their WMI class equivalents, see [Configuration Manager Schema View Mapping](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping)

## See Also

[Configuration Manager Schema Overview](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-overview) [Configuration Manager Schema View Mapping](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-schema-view-mapping) [Configuration Manager SQL View Security](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sql-view-security)
