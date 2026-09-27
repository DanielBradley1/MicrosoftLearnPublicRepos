<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-resourceassembly-element -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Configuration Manager Console ResourceAssembly Element

In Configuration Manager, the `ResourceAssembly` element defines the resources that are used by the node. The following XML defines the assembly, `AdminUI.CollectionProperty.dll`, and the type of the resource within the assembly.

```
<ResourceAssembly>
    <Assembly>AdminUI.CollectionProperty.dll</Assembly>
    <Type>Microsoft.ConfigurationManagement.AdminConsole.CollectionProperty.Properties.Resources.resources</Type>
</ResourceAssembly>
```

## See Also

[About Configuration Manager Administrator Console Nodes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-nodes) [How to Find a Configuration Manager Node GUID](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid) [Configuration Manager Console Node XML](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-node-xml)
