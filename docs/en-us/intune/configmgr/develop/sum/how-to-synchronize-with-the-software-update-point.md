<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-synchronize-with-the-software-update-point -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# How to Synchronize with the Software Update Point

You synchronize the software update point, in Configuration Manager SP1, by calling the `SyncNow` method.

## To synchronize the software update point

1. Set up a connection to the SMS Provider.
2. Create an instance of the [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) class.
3. Create and populate the method parameter value `fullSync`.
4. Call the [SyncNow Method in Class SMS\_SoftwareUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/syncnow-method-in-class-sms_softwareupdate) method, passing in the method parameter value.

## Example

The following example method shows how to synchronize the software update point by calling the [SyncNow Method in Class SMS\_SoftwareUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/syncnow-method-in-class-sms_softwareupdate) method.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```c#

public void SynchronizeSoftwareUpdatePoint(WqlConnectionManager connection)
{
    try
    {

        // Create the new SMS_SoftwareUpdate object.
        IResultObject newSoftwareUpdate = connection.CreateInstance("SMS_SoftwareUpdate");

        // Create dictionary object to pass parameters to the SyncNow method.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams["fullSync"] = true;

        // Initialize the outParams object.
        IResultObject outParams = null;
        // Call SyncNow method to initiate synchronization.
        outParams = connection.ExecuteMethod("SMS_SoftwareUpdate", "SyncNow", inParams);

    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See Also

[About software update deployments](https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments) [SMS\_SoftwareUpdate Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/sms_softwareupdate-server-wmi-class) [SyncNow Method in Class SMS\_SoftwareUpdate](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/sum/syncnow-method-in-class-sms_softwareupdate)
