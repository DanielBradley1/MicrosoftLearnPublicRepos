<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-mof-file-for-a-configuration-manager-custom-action -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to Create a MOF File for a Configuration Manager Custom Action

You define a custom task sequence action, its properties and its user interface controls by creating a managed object format \(MOF\) file to describe the class. The MOF file is then compiled by using Mofcomp.exe.

For more information about custom action MOF files, see [About the Configuration Manager Custom Action MOF File](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-action-mof-files).

The following procedure adds a class declaration for the custom action that you created in [How to Create a Configuration Manager Custom Action Control](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-configuration-manager-custom-action-control).

For information about using the custom action, see [About Configuration Manager Custom Action Client Applications](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-action-client-applications).

### To create a MOF file for a custom action

1. In Notepad, create a new file.
2. Add the following MOF code to the file.

   ```

   #pragma autorecover

   #pragma namespace("\\\\.\\root")

   // SMS Root Storage
   instance of __Namespace
   {
       Name = "SMS";
   };

   #pragma namespace("\\\\.\\root\\SMS")

   // Configuration Manager database name for this computer.
   instance of __Namespace
   {
       Name = "site_REPLACESITECODE";
   };

   #pragma namespace("\\\\.\\root\\SMS\\site_REPLACESITECODE")

   #pragma classflags("forceupdate")

   [   CommandLine("smsswd.exe /run:%1 Application.exe /user:%2"),
       VariablePrefix("MyCustomActionPrefix"),
       ActionCategory("My Custom Action Category,7,1"),
       ActionName{"ConfigMgrTSAction.dll", "ConfigMgrTSAction.Properties.Resources", "ConfigMgrTSAction"},
       ActionUI{"ConfigMgrTSAction.dll", "ConfigMgrTSAction","ConfigMgrTSActionControl",
   "ConfigureTSActionOptions"}
       ]
   class ConfigMgrTSActionControl : SMS_TaskSequence_Action
   {
       [TaskSequencePackage, CommandLineArg(1)]
       string          PackageIDForApplicationExe;

       [Not_Null, CommandLineArg(2)]
       string          User;

       [VariableName("CustomLocation")]
       string          Location;

   };
   ```

3. Replace `REPLACESITECODE` with the site code for your Configuration Manager site.
4. Choose a folder, and save the file as type `All Files` with the name CustomAction.mof.
5. Open a Command Prompt window, navigate to the folder that you saved CustomAction.mof in, and enter the following:

   ```
   mofcomp CustomAction.mof
   ```

6. Press ENTER to compile the CustomAction.mof.
7. Confirm that the class has been added in CIM Studio. The class should be listed as a child class of [SMS\_TaskSequence\_Action](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_action-server-wmi-class).
8. Complete [How to Use a Configuration Manager Custom Action Control](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-a-configuration-manager-custom-action-control).

## See Also

[About Configuration Manager Custom Actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-actions) [About the Configuration Manager Custom Action MOF File](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-action-mof-files) [How to Create a Configuration Manager Custom Action Control](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-a-configuration-manager-custom-action-control) [About Configuration Manager Custom Action Client Applications](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-action-client-applications)
