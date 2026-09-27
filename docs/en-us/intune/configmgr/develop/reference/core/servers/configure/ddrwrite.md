<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrwrite -->
<!-- Sitemap-Last-Modified: 2024-01-12 -->

# DDRWrite

The `DDRWrite` function, in Configuration Manager, writes the data discovery records \(DDRs\) to a file.

## Syntax

```
[IDL]
HRESULT DDRWrite();
```

#### Parameters

`FileName` Valid Universal Naming Convention \(UNC\) file name. Use the .ddr file name extension when you specify the file name.

## Return Values

If the function succeeds, the return value is S\_OK.

If the [DDRNew](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew) function hasn't been called or a file error occurs, the return value is S\_FALSE.

## Remarks

Calling `DDRWrite` completes the DDR and writes the record to a binary file. The DDR must be copied to the Data Discovery Manager \(DDM\) inbox on the site server at a later time \(SMS\\Inboxes\\Auth\\Ddm.box\).

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[DDRPropertyFlagsEnum Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration) [SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class) [ISMSResGen Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ismsresgen-interface)
