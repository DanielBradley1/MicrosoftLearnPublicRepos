<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DDRAddIntegerArray

The `DDRAddIntegerArray` function, in Configuration Manager, adds an integer array property to the data discovery record \(DDR\).

## Syntax

```
[IDL]
HRESULT DDRAddIntegerArray();
```

#### Parameters

`Name` Name of the class property.

`Array` Array of integers assigned to the property.

`Flags` Characteristics of the property, such as identifying this property as a key field for comparisons. Enter the following flag or a zero.

| Flag | Description |
| --- | --- |
| ADDPROP\_KEY \(Hexadecimal 8\) | Identifies this property as a key field during a comparison of this DDR with class instances in the database. If an instance in the database matches the data of the DDR key properties, the instance is updated; otherwise, a new instance is created. |

## Return Values

If the function succeeds, the return value is S\_OK.

If the [DDRNew](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew) function has not been called, the return value is S\_FALSE.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[DDRAddInteger](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddinteger) [DDRAddStringArray](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray) [DDRPropertyFlagsEnum Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration) [SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class) [ISMSResGen Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ismsresgen-interface)
