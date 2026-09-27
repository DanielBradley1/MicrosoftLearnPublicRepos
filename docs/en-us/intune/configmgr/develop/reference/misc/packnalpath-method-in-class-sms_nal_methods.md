<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/packnalpath-method-in-class-sms_nal_methods -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# PackNALPath Method in Class SMS\_NAL\_Methods

The `PackNALPath` method, in Configuration Manager, encodes a network abstraction layer \(NAL\) path from its components. A NAL path is an abstract representation of a network path or a user account.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 PackNALPath(
     String DisplayQualifiers[],
     String NALType,
     String NetworkOSPath,
     String NetworkConnectionQualifiers[],
     String NALPath
);
```

#### Parameters

`DisplayQualifiers` Data type: `String` Array

Qualifiers: \[in\]

Qualifiers that are used by the Configuration Manager console. The possible values are: Display=<path, group, or user>. The value that you specify for the path must be the same as the value that you specify for `NetworkOSPath`. For path formats, see `NetworkOSPath` formats later in this topic.

`NALType` Data type: `String`

Qualifiers: \[in\]

The NAL type specified by the network operating system. Possible values are:

| Value | NAL type |
| --- | --- |
| GENERIC | All providers accept this account specification. Use this value only when you specify a user or group name. |
| MSWNET | Windows NT. |

`NetworkOSPath` Data type: `String`

Qualifiers: \[in\]

The network operating system path. Possible values are:

| Provider | NetworkOSPath |
| --- | --- |
| Windows NT user names | <domain>\\<user name> |
| Windows NT group names | <domain>\\group=<group name> |
| Generic group names | GROUP=<group name> |
| Windows NT \(UNC\) computer names | \\\\<computer name> |
| Windows NT \(UNC\) share names | \\\\<computer name>\\<share name> |

`NetworkConnectionQualifiers` Data type: `String` Array

Qualifiers: \[in\]

Optional. Configuration Manager component-specific qualifiers. The possible values are: SMS\_SITE=<site code> \[Preferred\]. SMS\_SITE identifies the site to which the path belongs. Preferred is optional and identifies the path to use when multiple paths are specified.

`NALPath` Data type: `String`

Qualifiers: \[out\]

Encoded NAL path.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Example Code

The following example encodes a NAL path for an MSWNET network operating system.

```
Dim clsNALMethods As SWbemObject
Dim NALPath As String

Set clsNALMethods = Services.Get("SMS_NAL_Methods")
clsNALMethods.PackNALPath Array("Display=\\<server>"), "MSWNET", _
"\\<server>", Array("SMS_SITE=<site code>"), NALPath
```

## Remarks

Your application uses this method when creating a distribution point or defining system resources in the site control file programmatically. The method is not used to create a NAL path of an existing distribution point for an [SMS\_DistributionPoint Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) object. To determine the NAL path for an existing distribution point, the application should query the [SMS\_SystemResourceList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_NAL\_Methods Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_nal_methods-server-wmi-class) [UnPackNALPath Method in Class SMS\_NAL\_Methods](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/unpacknalpath-method-in-class-sms_nal_methods) [SMS\_DistributionPoint Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_distributionpoint-server-wmi-class) [SMS\_SystemResourceList Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/configure/sms_systemresourcelist-server-wmi-class)
