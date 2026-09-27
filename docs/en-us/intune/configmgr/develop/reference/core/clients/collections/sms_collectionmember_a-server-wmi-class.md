<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionmember_a-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_CollectionMember\_a Server WMI Class

The `SMS_CollectionMember_a` association Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that relates an [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object with [SMS\_Resource Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resource-server-wmi-class) objects that represent the member resources of the collection.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_CollectionMember_a : SMS_BaseAssociation
{
      UInt32 ClientCertType;
      UInt32 ClientType;
      ref:SMS_Collection collection;
      String CollectionID;
      UInt32 DeviceOwner;
      String Domain;
      Boolean IsActive;
      Boolean IsAlwaysInternet;
      UInt32 IsApproved;
      Boolean IsAssigned;
      Boolean IsBlocked;
      Boolean IsClient;
      Boolean IsDecommissioned;
      Boolean IsDirect;
      Boolean IsInternetEnabled;
      Boolean IsObsolete;
      String Name;
      ref:SMS_Resource resource;
      UInt32 ResourceID;
      UInt32 ResourceType;
      String SiteCode;
      String SMSID;
      Boolean IsVirtualMachine;
};
```

## Methods

The `SMS_CollectionMember_a` class does not define any methods.

## Properties

`ClientCertType` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Client certificate type. Possible values are:

| Value | Client certificate type |
| --- | --- |
| 1 | Self-signed certificate |
| 2 | Certificate issued by a certification authority. |

`ClientType` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Type of client. Possible values are:

| Value | Client type |
| --- | --- |
| 1 | Client |
| 3 | Device |

`Collection` Data type: `ref:SMS_Collection`

Access type: Read Only

Qualifiers: \[key\]

Reference to an [SMS\_Collection Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collection-server-wmi-class) object path.

`CollectionID` Data type: `String`

Access type: Read Only

Qualifiers: None

ID of the collection.

`DeviceOwner` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Owner of the device.

| Value | Device owner |
| --- | --- |
| 1 | Company |
| 2 | Personal |

`Domain` Data type: `String`

Access type: Read Only

Qualifiers: None

Windows NT or Windows 2000 domain to which the resource belongs.

`IsActive` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is active.

`IsAlwaysInternet` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is always associated with the Internet.

`IsApproved` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

Whether the resource is approved. Possible values are:

| Value | Approval type |
| --- | --- |
| 0 | Not approved |
| 1 | Approved |
| 2 | Not applicable |

`IsAssigned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is within the site boundaries and has been assigned to the site.

`IsBlocked` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is blocked.

`IsClient` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client software has been installed on the resource.

`IsDecommissioned` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is decommissioned.

`IsDirect` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the client is a member of the associated collection by a direct rule. For more information, see [SMS\_CollectionRuleDirect Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/collections/sms_collectionruledirect-server-wmi-class).

`IsInternetEnabled` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is Internet-enabled.

`IsObsolete` Data type: `Boolean`

Access type: Read Only

Qualifiers: None

`true` if the resource is obsolete.

`IsVirtualMachine` Data type: `Boolean`

Access type: Read/Write

Qualifiers: none

`true` if this is a virtual machine.

`Name` Data type: `String`

Access type: Read Only

Qualifiers: None

Name of the member resource.

`resource` Data type: `ref:SMS_Resource`

Access type: Read Only

Qualifiers: \[key\]

Reference to an [SMS\_Resource Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resource-server-wmi-class) object path.

`ResourceID` Data type: `UInt32`

Access type: Read Only

Qualifiers: None

The identifier of the member resource.

`ResourceType` Data type: `Uint32`

Access type: Read Only

Qualifiers: None

Type of the member resource as defined by instances of [SMS\_ResourceMap Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/manage/sms_resourcemap-server-wmi-class).

`SiteCode` Data type: `String`

Access type: Read Only

Qualifiers: \[SizeLimit\("3"\)\]

Site code of the site with which the resource is associated.

`SMSID` Data type: `String`

Access type: Read Only

Qualifiers: None

Configuration Manager unique ID of the member resource.

## Remarks

Class qualifiers for this class include:

- Association: ToInstance
- Read \(read-only\)

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

  The `CollectionID` and `ResourceID` properties can be used in a WMI Query Language \(WQL\) WHERE clause. However, you are limited to using an OR condition. Your query might not use the other properties in the relationship.

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).
