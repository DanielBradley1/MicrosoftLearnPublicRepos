<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/about-configuration-manager-wmi-programming -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# About Configuration Manager WMI programming

Programming the Configuration Manager client Windows Management Instrumentation \(WMI\) provider differs according to the programming language you use.

## C#

If you use C#, use the System.Management namespace. It provides access to a rich set of management information and management events about the system, devices, and applications that are instrumented to the WMI infrastructure.

Note

The managed Configuration Manager library is for use with a Configuration Manager site server and cannot be used to access client WMI namespaces.

For more information about connecting to the Configuration Manager client WMI namespace by using the System.Management namespace, see [How to connect to the Configuration Manager client WMI namespace by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace).

For more information about using Configuration Manager client WMI namespace objects by using the System.Management namespace, see [How to read a WMI object by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management).

For more information about using the System.Management namespace, see [System.Management Namespace](https://learn.microsoft.com/en-us/dotnet/api/system.management).

## VBScript

If you use VBScript, you access and use Configuration Manager client WMI objects by using the same coding techniques that are used for accessing other WMI objects, including the Configuration Manager WMI objects. For more information, see the [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page).

## Client WMI namespace

The Configuration Manager client WMI namespace begins at `\\<client>\root\ccm`. For example, `root\ccm` contains the [SMS\_Client](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/sms_client-client-wmi-class) class that can be used to get and set client information.

## See also

- [How to call a WMI class method by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-call-a-wmi-class-method-by-using-system.management)
- [How to connect to the Configuration Manager client WMI namespace by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-connect-to-the-client-wmi-namespace)
- [How to perform an asynchronous query by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-an-asynchronous-query-by-using-system.management)
- [How to perform a synchronous query by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-perform-a-synchronous-query-by-using-system.management)
- [How to read a WMI object by using System.Management](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-read-a-wmi-object-by-using-system.management)
- [Windows Management Instrumentation](https://learn.microsoft.com/en-us/windows/win32/wmisdk/wmi-start-page)
- [System.Management namespace](https://learn.microsoft.com/en-us/dotnet/api/system.management)
