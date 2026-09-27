<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Configuration Manager Actions

Configuration Manager console actions are tasks or commands that are performed by making context menu or action panel selections. There are a number of standard action types such as cut, paste, and properties. You can also add your own custom actions to perform tasks such as running programs and displaying dialog boxes. You can restrict the availability of actions to such criteria as regular expressions, security permissions, and method call results.

In the Configuration Manager console, actions are defined in XML by the [ActionDescription](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147252\(v=msdn.10\)) element.

## Standard Actions

A custom action can be associated with several standard actions. For example, a `ShowDialog` action can be associated with a `Properties` standard action. In this case, a property page is integrated into the properties property sheet for a selected object.

The standard actions are:

- `Delete`
- `Refresh`
- `Properties`

## Custom Actions

You can define the following custom actions.

| Action | Description |
| --- | --- |
| [Configuration Manager Executable Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/executable-action) | Runs a program or opens a file by using the program registered with Windows. |
| [Configuration Manager ShowDialog Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/showdialog-action) | Opens a dialog box. |
| [Configuration Manager Report Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/report-action) | Opens a report. |
| [Configuration Manager AssemblyType Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/assemblytype-action) | Defines the type and assembly for a method that is called. |
| [Configuration Manager Group Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/group-action) | Creates a menu group, also known as a submenu. |
| Separator | Creates a separator \(line\) under an action. |

### Adding Custom Actions

The steps for adding a new custom action to the Configuration Manager console are:

1. **Create the action XML file.** The name you choose for the file should have the .xml extension. The arrangement of the actions in the context menu and actions pane is based on the alphabetical ordering of the file names in the actions folder.
2. **Deploy the action XML.** The custom action XML file is placed in the *%ProgramFiles%*\\Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Extensions\\Actions folder under the GUID named folder of the Configuration Manager console node.

   For example, to create an action that is displayed on the software updates node you would have following folder structure:

   AdminConsole\\XmlStorage\\Extensions\\Actions\\f5445252-da1d-450f-a772-7c3d3cb929fb\\myfilename.xml

   For more information, see [How to Create a Configuration Manager Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action).

   For more information about the Configuration Manager console nodes, see [About console nodes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes).

## Conditional Actions

Actions can be made available \(displayed\) according to specified conditions. The conditions are defined by the following:

| Condition | Description |
| --- | --- |
| Regular expression | The action is made available depending on a defined search pattern. |
| Method call | The action is made available depending on the result of a method call. |
| Security permissions | The action is made available depending on the security permissions of the selected item. |

For more information, see [Configuration Manager Conditional Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/conditional-actions).

## See Also

[Configuration Manager Action XML](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-action-xml) [How to Create a Configuration Manager Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action) [About Configuration Manager console actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions) [About console forms](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-forms) [About console views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views) [How to Find a Configuration Manager Node GUID](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid)
