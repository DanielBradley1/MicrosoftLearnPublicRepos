<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/collection-views-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Collection views in Configuration Manager

Collection views contain information about the collections, collection rules, and collection members. Many of the collection views are useful when creating reports on site data, software update deployments, application deployments, and compliance settings.

The two types of collection views are as follows:

- The first type lists all members of a specific collection and starts with the **v\_CM\_RES\_COLL\_** view name and ends with the collection ID, with the exception of the **v\_FullCollectionMembership** view, which lists all members of all collections. This collection type will be used most often when creating reports.
- The second type of collection view has a name that starts with **v\_** and contains general information about the collections but not the member resources within each collection.

## Collection views

The collection views are described in this section.

### v\_ClientCollectionMembers

Lists all devices, by resource ID, that are not in an obsolete or decommissioned state, what collections the device is a member of, and whether the resource is a Configuration Manager client. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_CM\_RES\_COLL\_<CollectionID>

Lists all devices that are members of the collection. The device ID, name, client GUID, site code, whether the computer is assigned to a site, whether the computer has been approved, whether the computer is an active client, and so on. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_Collection

Lists all collections by collection ID, collection name, and what view the collection maps to \(listed in the **v\_CM\_RES\_COLL\_<***CollectionID***>** row\), the last time the collection membership changed, as well as other collection information. The view can be joined to other views by using the **CollectionID** column.

### v\_CollectionRuleDirect

Lists the collections that contain direct membership rules. The view can be joined to other views by using the **CollectionID** or **ResourceID** columns.

### v\_CollectionRuleQuery

Lists the query statement for each query-based collection. The view can be joined to other views by using the **CollectionID** and **LimitToCollectionID** columns.

### v\_CollectionSettings

Lists the configured settings for each collection, such as restart countdown, polling interval, collection variable precedence, source site, last modification time, and more. The view can be joined to other views by using the **CollectionID** column.

### v\_CollectionVariable

Lists the collections that have associated task sequence variables. The view can be joined to other views by using the **CollectionID** column.

### v\_FullCollectionMembership

Lists the resources for all collections. Contains the collection ID, resource ID, name, domain, resource GUID, site code, and other client information. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_FullCollectionMembership\_Valid

Lists the resources that are not in an obsolete or decommissioned state for all collections and contains a subset of information from the **v\_FullCollectionMembership** view. The view can be joined to other views by using the **CollectionID** and **ResourceID** columns.

### v\_ServiceWindow

Lists all collections that have a configured maintenance window and information about the maintenance window, such as the maintenance window name, description, start time, and duration. The view can be joined to other views by using the **CollectionID** column.

### v\_Collections

Lists all collections by collection ID and collection name. Also contains further information about each collection, for example:

- The last time the collection was changed \(**LastChangeTime**\)
- The last time the collection was re-evaluated \(**LastRefreshRequest**\)
- The collections limiting collection \(**LimitToCollectionID**\)
- Whether the collection is built-in, or was created by an administrator \(**IsBuiltIn**\)

The view can be joined to other views by using the **CollectionID** column.

## See also

[SQL Server views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sql-server-views-configuration-manager)
