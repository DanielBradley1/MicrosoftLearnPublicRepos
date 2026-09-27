<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/getfeatures-method-in-class-sms_whatsnewfeature -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetFeatures Method in Class SMS\_WhatsNewFeature

For internal use only.

## Syntax

```
SInt32 GetFeatures(
     UInt32 MinMilestone,
     UInt32 MaxMilestone,
     UInt32 LocaleID,
     SMS_WhatsNewFeature Features[]
);
```

#### Parameters

`MinMilestone` Data type: `UInt32`

Qualifiers: \[in\]

Reserved for internal use.

`MaxMilestone` Data type: `UInt32`

Qualifiers: \[in\]

Reserved for internal use.

`LocaleID` Data type: `UInt32`

Qualifiers: \[in\]

Reserved for internal use.

`Features` Data type: `SMS_WhatsNewFeature Array`

Qualifiers: \[out\]

Reserved for internal use.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For more information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_WhatsNewFeature Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/sms_whatsnewfeature-server-wmi-class)
