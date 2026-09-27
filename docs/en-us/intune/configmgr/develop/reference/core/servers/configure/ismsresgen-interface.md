<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ismsresgen-interface -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# ISMSResGen Interface

The `ISMSResGen` automation interface, in Configuration Manager, enables the creation of Data Discovery Records \(DDR\). This interface inherits from `IDispatch`.

## In This Section

| Term | Definition |
| --- | --- |
| [DDRNew](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew) | Creates a new DDR. |
| [DDRAddInteger](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddinteger) | Adds an integer property to the DDR. |
| [DDRAddString](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstring) | Adds a string property to the DDR. |
| [DDRAddIntegerArray](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddintegerarray) | Adds an integer array property to the DDR. |
| [DDRAddStringArray](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddraddstringarray) | Adds a string array property to the DDR. |
| [DDRWrite](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrwrite) | Writes the DDR to a file. |
| [DDRPropertyFlagsEnum Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration) | Defines flags used by `ISMSResGen`. |

## Remarks

These functions create a single DDR that is sent to the Data Discovery Manager \(DDM\). The order in which you call the functions is important; you must call `DDRNew` before calling any of the functions that add properties. However, the order in which you add properties to your class is arbitrary. The last function you call must be `DDRWrite` to create the DDR. The DDR must then be manually copied to the **SMS\\Inboxes\\Auth\\Ddm.box** directory.

DDRs that fail to load are moved to the **SMS\\Inboxes\\Ddm.box\\Bad\_ddrs** directory. If you have logging turned on, you can view the DDM.log file for an explanation of the failure. After you fix the errors, you can rerun your program to load the DDR.

The IID for `ISMSResGen` is ECB65D0E-B16B-4817-92B0-BF2D9CEFB3AC.

## Requirements

### Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class)
