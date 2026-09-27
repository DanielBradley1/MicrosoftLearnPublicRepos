<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/showdialog-action -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Configuration Manager ShowDialog Action

The `ShowDialog` action, in Configuration Manager, opens a property sheet or regular dialog box in the Configuration Manager console. With the `ShowDialog` action, you can display existing dialog boxes or extension dialog boxes that you create.

The following attributes and elements are specific to an action that opens a dialog box:

- The `ActionDescription` element `Class` attribute is set to `ShowDialog`.
- The `DialogID` element is the identifier for a property sheet or dialog box displayed in a dialog. It matches the name of the form XML file in the *%ProgramFiles%*\\Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Extensions\\Forms folder.

## Sample ShowDialog Action XML

The following XML shows how to show a dialog box with the identifier **PrototypeForm**:

```
<ActionDescription Class="ShowDialog" DisplayName="Test Action (dialog)" MnemonicDisplayName="Mnemonic" Description="Description"> <ShowOn>              <string>DefaultHomeTab</string>      <string>ContextMenu</string>           </ShowOn>
 <DialogId>PrototypeForm</DialogId>
</ActionDescription>
```

## Sample Properties ShowDialog Action XML

The following attributes and elements are specific to an action that adds a property page to a properties property sheet:

- The `ActionDescription` element `ActionVerb` attribute is set to `Properties`.
- The `DialogID` element identifies a property sheet containing the property page to be displayed in the `Properties` dialog.

  The following XML shows how to integrate a property page \(`PrototypeForm`\) into a properties context menu option:

```
<ActionDescription ActionVerb="Properties" Class="ShowDialog">  <ShowOn>    <string>DefaultHomeTab</string>    <string>ContextMenu</string>  </ShowOn>  <DialogId>PrototypeForm</DialogId>
</ActionDescription>
```

For more information about creating and showing dialog boxes, see [About console forms](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-forms).

## See Also

[About Configuration Manager Dialog Boxes](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-forms) [Configuration Manager Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions) [How to Create a Configuration Manager Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action) [How to Create Form XML for a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet) [How to Create Form XML for a Configuration Manager Dialog Box](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box) [How to Find a Configuration Manager Node GUID](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid)
