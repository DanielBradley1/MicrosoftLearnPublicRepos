<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Create a Configuration Manager Action

To create a Configuration Manager console action, in Configuration Manager, you create an XML file that populates an [ActionDescription](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147252\(v=msdn.10\)) XML element for the action. You must then copy the XML file to the %*ProgramFiles*%\\Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Extensions\\Actions\\GUID folder.

For sample XML for each action type, see the following:

- [Configuration Manager Executable Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/executable-action)
- [Configuration Manager ShowDialog Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/showdialog-action)
- [Configuration Manager Report Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/report-action)
- [Configuration Manager AssemblyType Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/assemblytype-action)
- [Configuration Manager Group Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/group-action)

  For information about deploying the action XML, see [Configuration Manager Console Extension Deployment](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-extension-deployment).

### To add an executable action to the Configuration Manager console

1. If the Configuration Manager console is open, close it.
2. In Notepad, create an empty text file named MyConfigurationManagerNote.txt and save it to C:\\.
3. In Notepad, create an XML file that contains the following XML:

   ```
   <ActionDescription Class="Executable" DisplayName="Make a Note" MnemonicDisplayName="Note" Description = "Make a note about software updates">    <ShowOn>      <string>DefaultContextualTab</string> <!-- RIBBON -->     <string>ContextMenu</string> <!-- Context Menu -->   </ShowOn>       <Executable>
     <FilePath>Notepad.exe</FilePath>
     <Parameters>C:\MyConfigurationManagerNote.txt</Parameters>
    </Executable>
   </ActionDescription>
   ```

4. Save the XML file in the folder <%*Program Files*%> Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Extensions\\Actions\\f5445252-da1d-450f-a772-7c3d3cb929fb. The GUID identifies the software updates folder. The file name can be anything with an .xml extension, but it does alphabetically affect the ordering of actions in the context-sensitive menu and in the actions pane. If it is not already created, you must create the Extensions\\Actions\\f5445252-da1d-450f-a772-7c3d3cb929fb folder structure. Be sure to save the file as type `All Files`.
5. Start the Configuration Manager console.

   In the Configuration Manager console, right-click the **Software Updates** node under **Computer Management**, and then click **Make a Note**. Notepad opens the text file.

## See Also

[Configuration Manager Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions) [Configuration Manager Action XML](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-action-xml) [Configuration Manager Executable Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/executable-action) [How to Find a Configuration Manager Node GUID](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-find-a-configuration-manager-console-node-guid)
