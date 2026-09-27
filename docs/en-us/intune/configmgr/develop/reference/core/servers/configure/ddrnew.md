<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrnew -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# DDRNew

The `DDRNew` function, in Configuration Manager, begins a new data discovery record \(DDR\).

## Syntax

```
[IDL]
HRESULT DDRNew();
```

#### Parameters

`Architecture` Name of the architecture. The name can refer to an existing or new architecture. The name is used to determine the resource class name. For example, specifying `Car` identifies the `SMS_R_Car` resource class.

`AgentName` Discovery agent that reports the DDR. This name, which should be unique, is added to the `AgentName` property array.

`SiteCode` Site where the resource was discovered. This site name is added to the `AgentSite` property array.

## Return Values

The `DDRNew` function always returns S\_OK.

## Remarks

You must call this function first for each DDR that you create; calling this function begins your DDR.

The `sArchitecture` string is used to identify your resource class name and can take one of the following forms:

- A single word such as Car, which you can use to identify the `SMS_R_Car`resource class.
- A multiword string such as Carpool Inventory, which you can use to identify the `SMS_R_CarpoolInventory` resource class.
- A DMTF-formatted string such as ACME\|Car\|1.0, which you can use to identify the `SMS_R_ACME_Car_1_0` resource class.
- The string "System" identifies a computer system.

  The agent name, `sAgentName`*,* should always be filled in and should identify the program used to generate the DDR.

## Requirements

## Runtime Requirements

smsrsgenctl.dll

smsrsgen.dll

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[DDRWrite](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrwrite) [DDRPropertyFlagsEnum Enumeration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ddrpropertyflagsenum-enumeration) [SMSResGen COM Automation Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/smsresgen-com-automation-class) [ISMSResGen Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/ismsresgen-interface)
