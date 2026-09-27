<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_userapplicationrequesthistoryitem-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_UserApplicationRequestHistoryItem Server WMI Class

The `SMS_UserApplicationRequestHistoryItem` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents an update to an instance of `SMS_UserApplicationRequest`.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_UserApplicationRequestHistoryItem :
{
    String Comments;
    String ModifiedBy;
    DateTime ModifiedDate;
    UInt32 State;
};
```

## Methods

The `SMS_UserApplicationRequestHistoryItem` class does not define any methods.

## Properties

`Comments` Data type: `String`

Access type: Read/Write

Qualifiers: none

Comments entered to explain why the change occurred. These could be user's comment explaining why they are requesting the application or approver comments explaining why the application was approved or denied.

`ModifiedBy` Data type: `String`

Access type: Read/Write

Qualifiers: none

The user who made the change to the request.

`ModifiedDate` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The date when the change to the request was made.

`State` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The state of the request after the change was made. Possible values are:

| Value | State |
| --- | --- |
| 1 | Requested |
| 2 | Canceled |
| 3 | Denied |
| 4 | Approved |

## Remarks

## Requirements

Each time a request is updated, an instance of this class is created to track the history of the request.

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_UserApplicationRequest Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_userapplicationrequest-server-wmi-class)
