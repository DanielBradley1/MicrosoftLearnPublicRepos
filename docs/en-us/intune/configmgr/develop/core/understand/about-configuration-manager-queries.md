<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-queries -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# About Configuration Manager Queries

You can create and run the queries that are accessible in the Configuration Manager console under **Queries**.

The queries can be used to locate objects in a Configuration Manager site that match your query criteria. These objects include items such as specific types of computers or user groups. Queries can return most types of Configuration Manager objects, including sites, collections, packages, and saved queries themselves. However, queries are most useful for extracting information that is related to resource discovery, inventory data, and status messages.

Note

For more information, see [Introduction to queries](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/introduction-to-queries).

## SMS\_Query

Configuration Manager queries are defined by `SMS_Query` object instances. The query is a WQL query and is defined in the `Expression` property. For more information about WQL, see [Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language).

Each query has a unique identifier assigned to it by the SMS Provider and can be used to get a specific query. For information about running a query, see [How to Run a Configuration Manager Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-run-a-query).

You can also create queries by creating instances of `SMS_Query`. When you create a query, it is displayed in the Configuration Manager console under **Queries**. If you want to, you can limit the results returned to those resources that belong to a specific collection. For more information about creating queries, see [How to Create a Configuration Manager Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-query).

## See Also

[Configuration Manager Extended WMI Query Language](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/extended-wmi-query-language)

[Configuration Manager Result Sets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/result-sets)

[Configuration Manager Special Queries](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/special-queries)

[How to Create a Configuration Manager Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-create-a-configuration-manager-query)

[How to Run a Configuration Manager Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-run-a-query)

[SMS\_Query](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_query-server-wmi-class)
