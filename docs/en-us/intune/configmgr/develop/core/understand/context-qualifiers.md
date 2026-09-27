<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/context-qualifiers -->
<!-- Sitemap-Last-Modified: 2022-10-10 -->

# Configuration Manager Context Qualifiers

Context objects are used, in Configuration Manager, to provide additional information to the SMS Provider. Typically, you use context qualifiers to give the SMS Provider contextual information, such as your application's name. You can use context qualifiers when you connect to the SMS Provider and with individual SMS Provider objects.

## Managed Code

When using the managed SMS Provider libraries, you use the [ConnectionManagerBase.Context](https://learn.microsoft.com/en-us/previous-versions/system-center/developer/cc147087\(v=msdn.10\)) property to specify context qualifiers. For more information, see [How to Add a Configuration Manager Context Qualifier by Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code).

## VBScript

When using VBScript, you use the [SWBemNamedValue](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalue) interface set to specify context qualifiers as a collection of named value objects. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi).

## Context Qualifiers

The following table contains the context qualifiers \(named values\) that are used by the SMS Provider. Most qualifiers, like `SessionHandle`, are only used with specific functional areas of the SMS Provider; but `LocaleID`, `MachineName`, and `ApplicationName` are for your application's use.

| Context qualifier | Description |
| --- | --- |
| `ApplicationName` | Identifies the application that made the call. |
| `ContextHandle` | Identifies where the SMS Provider has stored your cached context qualifiers. |
| `InstanceCount` | Limits the number of instances returned from [ExecQuery](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execquery) and [CreateInstanceEnum](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum). |
| `LimitToCollectionIDs` | Limits the results of a resource query to the members of the named collections. |
| `LocaleID` | Identifies the code page to use. |
| `MachineName` | Identifies which computer is running the application. |
| `QueryQualifiers` | Returns the SecurityVerbs bit flags when you execute queries against secured objects. |
| `SessionHandle` | Identifies your application's copy of the site control file to Configuration Manager. |

## ApplicationName

The `ApplicationName` context qualifier is a string value that identifies the name of the application that made the call. You should specify `ApplicationName` for your application because it is used for auditing. If you do not supply the name of your application, a value of Unknown is used. You must supply the `ApplicationName` value when you call any of the raise status message methods, such as [SMS\_StatusMessage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)::[RaiseErrorStatusMsg](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/raiseerrorstatusmsg-method-in-class-sms_statusmessage), or the call will fail.

## ContextHandle

The `ContextHandle` context qualifier is a string value that identifies where the SMS Provider has stored your cached context qualifiers. The managed SMS Provider manages data transfer. When using VBScript, You can use the following steps to reduce the amount of data that is passed over the network.

1. Create [SWBemNamedValue](https://learn.microsoft.com/en-us/windows/win32/wmisdk/swbemnamedvalue) value set.
2. Add your qualifiers to the context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi).
3. Call the [GetContextHandle](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods) method to cache your qualifiers on the server. The SMS Provider caches the context object that you pass as a parameter of [ExecMethod](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execmethod) when you call [GetContextHandle](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getcontexthandle-method-in-class-sms_contextmethods).
4. Remove all the qualifiers from your context object.
5. Add the `ContextHandle` qualifier and value to your context object.
6. Pass the context object on all calls to [IWbemServices](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nn-wbemcli-iwbemservices).

   You must call the [ClearContextHandle](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/clearcontexthandle-method-in-class-sms_contextmethods) method to remove your cached qualifiers before you exit your application. You can create as many `ContextHandle` values as you want, with each providing varying information for your application.

Note

After you cache your context qualifiers, you can override your cached values by adding the same context qualifiers, with different values, to your context object.

## InstanceCount

The `InstanceCount` context qualifier is an integer value that is used to limit the number of instances returned from the [ExecQuery](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execquery) and [CreateInstanceEnum](https://learn.microsoft.com/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) methods. You set `InstanceCount` equal to the maximum number of instances that you want returned from the query or enumerator. For example, setting `InstanceCount` to 10 returns, at most, 10 instances.

## LimitToCollectionIDs

The `LimitToCollectionIDs` context qualifier is a string array that contains a list of `CollectionID` values. Currently, you can specify only one `CollectionID` value. You use this qualifier to limit the results of a resource query to the members of the named collection. A resource query is a query that includes classes derived from [SMS\_Resource](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resource-server-wmi-class) or [SMS\_Group](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_group-server-wmi-class).

The user must have instance read resource permissions for the collection to which the resource belongs. You must use collection limiting when the user does not have class read resource rights for collections; otherwise, no data is returned. For SMS 2.0 with Service Pack 1 and later versions, this restriction applies only to classes derived from SMS\_Group.

You cannot use this qualifier when querying collections.

## LocaleID

The `LocaleID` context qualifier is a string value that accepts either a hexadecimal value or a decimal value in the form MS\\x, where x is the locale ID. For example, you can enter the English `LocaleID` value as ms\\0x0409 or ms\\1033. The SMS Provider only accepts `LocaleID` values that use the Microsoft format. You can find a list of `locale IDs` at [Locale IDs Assigned by Microsoft](https://learn.microsoft.com/en-us/openspecs/windows_protocols/ms-lcid).

If you need the locale for non-U.S. installations, you can get it from the [SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class) `LocaleID` property.

## MachineName

The `MachineName` context qualifier is a string value that identifies which computer is running the application. You should specify `MachineName` for your application because it is used for auditing. If you do not supply the computer name, a value of Unknown is used. You must supply the MachineName value when you call any of the raise status message methods, such as [SMS\_StatusMessage](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_statusmessage-server-wmi-class)::[RaiseRawStatusMsg](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage), or the call will fail.

## QueryQualifiers

The `QueryQualifiers` context qualifier is a Boolean value that is used to return the SecurityVerbs bit flags when you execute queries against secured objects, such as [SMS\_Site](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_site-server-wmi-class) or [SMS\_Package](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_package-server-wmi-class). Note that using `QueryQualifiers` when querying unsecured objects generates an error. By default, SecurityVerbs flags are not returned with the query. You must create this qualifier and set its value to `true` if you want the flags returned. Not creating `QueryQualifiers` is the same as setting its value to `false`.

## SessionHandle

The `SessionHandle` context qualifier is a string value that is returned as an out parameter of the GetSessionHandle method. The string is a unique GUID that identifies your application's copy of the site control file to Configuration Manager. You should use this mechanism to modify the site control file and reduce data collisions with other applications that are modifying the site control file at the same time. If you do not supply a `SessionHandle` value, your application modifies the global copy of the site control file, which has no protection from applications overwriting each other's data.

Note

If you are using the managed SMS Provider, site control file session management is managed for you.

## See Also

[How to Add a Configuration Manager Context Qualifier Using Managed Code](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code) [How to Add a Configuration Manager Context Qualifier Using WMI](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-add-a-configuration-manager-context-qualifier-by-using-wmi) [SMS Provider fundamentals](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals)
