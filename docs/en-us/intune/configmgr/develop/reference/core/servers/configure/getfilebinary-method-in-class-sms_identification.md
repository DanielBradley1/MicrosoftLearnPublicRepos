<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/getfilebinary-method-in-class-sms_identification -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetFileBinary Method in Class SMS\_Identification

The `GetFileBinary` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, gets the binary user interface for a feature. The binary can be separated into multiple blocks starting with number 1. If `isTheLastBlock` equals `False`, then you need call the method again with blockNumber+1 to get the next block.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetFileBinary (
    String FileName,
    UInt32 blockNumber,
    String binary64Encoded,
    Boolean isTheLastBlock
);
```

#### Parameters

`FileName` Data type: `String`

Qualifiers: \[in\]

The name of the file.

`blockNumber` Data type: `UInt32`

Qualifiers: \[in\]

The block number. To get the next block, call the method again with blockNumber+1, as long as isTheLastBlock equals `False`.

`binary64Encoded` Data type: `String`

Qualifiers: \[out\]

The binary 64-encoded file.

`isTheLastBlock` Data type: `Boolean`

Qualifiers: \[out\]

`True` if the current block is the last block; otherwise, `False`. While `False`, you can get the next block by calling the method again with blockNumber+1.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_Identification Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_identification-server-wmi-class)
