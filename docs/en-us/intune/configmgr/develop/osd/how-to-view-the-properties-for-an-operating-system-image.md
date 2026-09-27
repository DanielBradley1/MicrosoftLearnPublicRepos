<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-view-the-properties-for-an-operating-system-image -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# How to View the Properties for an Operating System Image

In Configuration Manager, you view the image properties for the Windows Image \(WIM\) file that is contained in an operating system package by calling the [SMS\_ImagePackage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_imagepackage-server-wmi-class) class instance [GetImageProperties](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_imagepackage) method.

The image properties are available in XML format.

### To view image properties

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals).
2. Get the `SMS_ImagePackage` class instance that you want to update.
3. Call the [GetImageProperties](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getimageproperties-method-in-class-sms_imagepackage) class instance method.
4. Access property XML by using the *ImageProperty* parameter.

## Example

The following example displays the operating system image package property XML that defines the package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/calling-code-snippets).

```vbs
Sub ViewOSImage(connection,imagePackageID)

    Dim imagePackage
    Dim inParam
    Dim outParams

    ' Get the image.
    Set imagePackage = connection.Get("SMS_ImagePackage.PackageID='" & imagePackageID & "'")

    ' Obtain an InParameters object specific
    ' to the method.
    Set inParam = imagePackage.Methods_("GetImageProperties"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    inParam.Properties_.Item("SourceImagePath") =  imagePackage.PkgSourcePath

    ' Execute the method.
    Set outParams = connection.ExecMethod("SMS_ImagePackage", "GetImageProperties", inParam)

    ' Display the image properties XML.
    Wscript.echo "ImageProperty: " & outParams.ImageProperty

End Sub
```

```c#
public void ViewOSImage(
    WqlConnectionManager connection,
    string imagePackageId)
{
    try
    {
        IResultObject imagePackage = connection.GetInstance(@"SMS_ImagePackage.PackageID='" + imagePackageId + "'");

        Dictionary<string, Object> inParams = new Dictionary<string, object>();

        inParams.Add("SourceImagePath", imagePackage["PkgSourcePath"].StringValue);
        IResultObject result = connection.ExecuteMethod("SMS_ImagePackage", "GetImageProperties", inParams);

        Console.WriteLine(result["ImageProperty"].StringValue);
    }
    catch (SmsException e)
    {
        Console.WriteLine(e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`  <br>- VBScript: [SWbemServices](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `imagePackageID` | - Managed: `String`  <br>- VBScript: `String` | The package image identifier. It is available from `SMS_ImagePackage. PackageID`. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/configure/role-based-administration).

## See also

[About image management](https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-operating-system-deployment-image-management)
