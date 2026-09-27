<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DDRPropertyFlagsEnum Enumeration

The `DDRPropertyFlagsEnum` enumeration, in Configuration Manager, specifies flags that are used by `ISMSResGen`.

## Syntax

```
enum DDRPropertyFlagsEnum
{
    ADDPROP_NONE = 0x0,
    ADDPROP_GUID = 0x00000002,
    ADDPROP_GROUPING = 0x00000004,
    ADDPROP_KEY = 0x00000008,
    ADDPROP_ARRAY = 0x00000010,
    ADDPROP_AGENT = 0x00000020,
    ADDPROP_NAME = 0x00000044,
    ADDPROP_NAME2 = 0x00000084
};
```

## Elements

ADDPROP\_NONE\(0x0\) No special properties.

ADDPROP\_GUID\(0x00000002\) Defines this property as being a GUID.

ADDPROP\_GROUPING\(0x00000004\) Reserved.

ADDPROP\_KEY\(0x00000008\) Defines this property as being a Key value that must be unique.

ADDPROP\_ARRAY\(0x00000010\) Reserved.

ADDPROP\_AGENT\(0x00000020\) Reserved.

ADDPROP\_NAME\(0x00000044\) Specifies this property as the actual `Name` property in the resource.

ADDPROP\_NAME2\(0x00000084\) Specifies this property as the actual `Comment` property in the resource.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class) [DDRAddStringArray](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray) [DDRAddIntegerArray](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray) [DDRAddInteger](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddinteger) [DDRNew](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew) [DDRWrite](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrwrite) [DDRAddString](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstring) [SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class) [ISMSResGen Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ismsresgen-interface)
