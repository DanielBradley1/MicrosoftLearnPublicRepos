<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/apps/sms_mamstoreapplication-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_MAMStoreApplication Server WMI Class

The `SMS_MAMStoreApplication` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents mobile application management \(MAM\) store application lists.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_MAMStoreApplication : SMS_BaseClass
{
     String IdentityIdentifier;
     Boolean IsManagedBrowser;
     String MAMSDKVersion;
     Boolean PinToProfile;
     UInt32 StoreIdentifier;
     String StoreApplicationIdentifier;
};
```

## Methods

The `SMS_MAMStoreApplication` class does not define any methods.

## Properties

`IdentityIdentifier` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Identity identifier.

`IsManagedBrowser` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

True if managed browser MAM application.

`MAMSDKVersion` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Version of the MAM SDK.

`PinToProfile` Data type: `Boolean`

Access type: Read-only

Qualifiers: \[read\]

True if this application pin to profile.

`StoreIdentifier` Data type: `UInt32`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Store identifier.

`StoreApplicationIdentifier` Data type: `String`

Access type: Read-only

Qualifiers: \[not\_null, read\]

Store application identifier.

## Remarks

Class qualifiers for this class include:

- Dynamic
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
