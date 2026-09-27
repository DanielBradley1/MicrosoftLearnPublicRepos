<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About Configuration Manager Console Nodes

Configuration Manager uses XML to define the nodes and their content, that you see in the Configuration Manager console. New nodes can be added anywhere in the existing node hierarchy.

The XML for a node describes the navigation pane, results pane, and action pane, and the resources that are needed by each pane to display the node.

When writing a new node, consider the following:

- **The position of the node in the hierarchy.** Each node is uniquely identified by a GUID. For an example, see [How to Create a Configuration Manager Administrator Console Node](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node).
- **The node hierarchy.** The node structure is hierarchical, and you can nest nodes as deeply as you require. You can also use regular expressions to determine whether a node should be displayed. For an example, see [How to Create a Configuration Manager Administrator Console Node](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node).
- **Actions.** You can define actions that the user selects in the Configuration Manager console. You can use an action to launch forms, run programs, call methods, show reports, and define action menus. For more information, see [Configuration Manager Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions).
- **Queries.** You can define queries that populate the navigation pane and results pane with SMS Provider objects. You can specify regular expressions to pick the properties that are displayed from the objects queried. For an example, see [Configuration Manager Administrator Console RootNodes Element](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-rootnodes-element).
- **Security.** You can secure a node based on security flags that you specify. For an example that sets security for an action, see [Configuration Manager Conditional Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/conditional-actions).
- **Views.** You can launch views in the Configuration Manager console at desired nodes. For more information about views, see [About console views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views).

Note

The Configuration Manager SDK includes a sample XML file and GUID folder for a node that displays the available collections. The GUID folder is the namespace identifier for the tools node

For information about node XML, see [Configuration Manager Console Node XML](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-node-xml).

## See Also

[About Configuration Manager console actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions) [About console forms](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-forms) [About console views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views) [How to Create a Configuration Manager Administrator Console Node](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-node) [How to Find a Configuration Manager Node GUID](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid) [Configuration Manager Console Node XML](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-node-xml)
