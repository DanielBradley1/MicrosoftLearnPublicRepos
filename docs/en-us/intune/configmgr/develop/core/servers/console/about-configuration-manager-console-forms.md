<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-forms -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# About Configuration Manager Console Forms

You can extend the Configuration Manager console with new Windows forms. Specifically, you can add form-based dialog boxes and property sheets. A user accesses these forms from Configuration Manager actions that you define.

Note

Wizards are another Windows form that is used by the Configuration Manager console, but you cannot extend or add wizards by using the Configuration Manager console framework. You can, however, run your own wizard solution by using Configuration Manager actions.

In Configuration Manager, forms are stored in .NET Framework assemblies that are called by the Configuration Manager console after the appropriate action is selected.

## Creating an Extension Form

To write an extension form, you do the following:

- Create the extension form assembly.
- Create the extension form action XML.
- Create the extension form XML.

### Create the Extension Form Assembly

#### Property sheets

A property sheet is made up of one or more property pages that you define. You can also integrate property pages into existing Configuration Manager property sheets.

To create a property sheet, you create a Windows Control Library project in Visual Studio. In this project, you create a class that inherits from the [Microsoft.ConfigurationManagement.AdminConsole.SmsPageControl](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147309\(v=msdn.10\)) class. This class implements the control you want to display on a property page. In a property sheet, you create an [SmsPageControl](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147309\(v=msdn.10\)) class for each property page that you need. The Property Sheet Prototype sample in the Configuration Manager SDK has a complete solution that you can use. For more information, see [How to Create a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet).

#### Dialog boxes

A dialog box in Configuration Manager is displayed like a typical modeless dialog box. You create an SMSPageControl and specify "Dialog" in the Form XML. For more information, see [How to Create a Configuration Manager Dialog Box](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box).

### Create the Form Action XML

An action describes the type of extension that is called, and where the action is placed in the Configuration Manager console user interface. For an extension form, you use the `ShowDialog` action type to display the form. For more information, see [How to Create Action XML for a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet).

For more information about actions, see [About Configuration Manager console actions](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions).

### Create the Form Property Sheet XML

Whether or not the form is a property sheet, the form has a form XML file that defines the assembly, namespace, and type of the form. In property sheets, it defines the order of the property pages on the property sheet. There is a property sheet XML file for every Configuration Manager console form.

Note

The Configuration Manager console property sheet XML files are stored in *%ProgramFiles%*\\Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Forms.

When you create a new form, you create a new property sheet XML file. If you are adding a new property page to an existing property sheet, you merge the property page XML with an existing property sheet XML file.

Note

Extension property sheets are stored in *%ProgramFiles%*\\Microsoft Endpoint Manager\\AdminConsole\\XmlStorage\\Extensions\\Forms.

For more information about form XML deployment, see [Configuration Manager Console Extension Deployment](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-extension-deployment).

Depending on whether you are displaying a dialog box or a property sheet, the FormType attribute values must be set.

| FormType | Description |
| --- | --- |
| PropertySheet | The form is a property sheet. |
| Dialog | The form is a dialog box. |

When an action is selected, the Configuration Manager console uses the property sheet XML to determine which assembly is needed to load and display the form.

For more information, see [How to Create Form XML for a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet).

## Managing Object Data in a Form

A Configuration Manager form can be passed custom data and also, from the results pane, the objects returned from a query. Selected objects from the results pane are made available to a form through a [PropertyManager](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146982\(v=msdn.10\)) object. For more information, see [How to Use Objects Passed to a Configuration Manager Form](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form). You can bind a form control to objects passed in to the form's `PropertyManager`. For more information, see [How to Bind Configuration Manager Data to a Form](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form).

The Configuration Manager console serializes Configuration Manager objects passed into a form when the form is dismissed.

## Queries

You can perform both synchronous and asynchronous queries in forms by using the managed SMS Provider. You get the [Microsoft.ConfigurationManagement.AdminConsole.SmsPageControl.QueryProcessor](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146983\(v=msdn.10\)) object from the form's `PropertyManager` [ConnectionManager](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc146965\(v=msdn.10\)). After it is obtained, the code is identical to the SMS Provider examples. For an example of a synchronous query, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code).

For an example of an asynchronous query, see [How to Perform an Asynchronous Configuration Manager Query by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-perform-an-asynchronous-query-by-using-managed-code).

## See Also

[How to Add a Property Page to an Existing Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-add-a-property-page-to-an-existing-configuration-manager-property-sheet) [How to Bind Configuration Manager Data to a Form](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form) [How to Create a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet) [How to Create Action XML for a Configuration Manager Dialog Box](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-dialog-box) [How to Create Action XML for a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet) [How to Create a Configuration Manager Dialog Box](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box) [How to Create Form XML for a Configuration Manager Dialog Box](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box) [How to Create Form XML for a Configuration Manager Property Sheet](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet) [How to Use Objects Passed to a Configuration Manager Form](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form)
