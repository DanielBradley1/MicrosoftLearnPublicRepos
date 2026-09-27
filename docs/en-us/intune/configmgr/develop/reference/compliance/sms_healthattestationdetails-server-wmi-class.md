<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/sms_healthattestationdetails-server-wmi-class -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# SMS\_HealthAttestationDetails Server WMI Class

The `SMS_HealthAttestationDetails` Windows Management Instrumentation \(WMI\) class is an SMS Provider server class, in Configuration Manager, that represents Health Attestation details.

The following syntax is simplified from Managed Object Format \(MOF\) code and includes all inherited properties.

## Syntax

```
Class SMS_HealthAttestationDetails : SMS_BaseClass
{
     UInt32 AIKPresent;
     SInt32 BitlockerStatus;
     UInt32 BootDebuggingEnabled;
     UIt32 CertRetrievalStatus;
     UInt32 CodeIntegrityEnabled;
     DateTime DateIssued;
     UInt64 DEPPolicy;
     UInt32 DeviceItemKey;
     UInt32 ELAMDriverLoaded;
     UInt32 HASSupported;
     UInt32 OSKernelDebuggingEnabled;
     UInt32 SafeMode;
     UInt32 SecureBootEnabled;
     UInt32 TestSigningEnabled;
     UInt32 VSMEnabled;
     UInt32 WinPE;
};
```

## Methods

The `SMS_HealthAttestationDetails` class does not define any methods.

## Properties

`AIKPresent` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether the Windows Automated Installation Kit \(Windows AIK\) is present.

`BitlockerStatus` Data type: `SInt32`

Access type: Read/Write

Qualifiers: none

The status of BitLocker.

`BootDebuggingEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether boot debugging is enabled.

`CertRetrievalStatus` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

The status of the certificate retrieval.

`CodeIntegrityEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether code integrity is enabled.

`DateIssued` Data type: `DateTime`

Access type: Read/Write

Qualifiers: none

The date and time that the certificate was issued.

`DEPPolicy` Data type: `UInt64`

Access type: Read/Write

Qualifiers: none

The Apple Device Enrollment Program \(DEP\) policy.

`DeviceItemKey` Data type: `UInt32`

Access type: Read/Write

Qualifiers: \[key\]

The device key.

`ELAMDriverLoaded` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether the Early-Launch Anti-Malware \(ELAM\) driver is loaded.

`HASSupported` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether health attestation is supported.

`OSKernelDebuggingEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Indicates whether operating system kernel debugging is enabled.

`SafeMode` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

`SecureBootEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether secure boot is enabled.

`TestSigningEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether test-signing is enabled.

`VSMEnabled` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

Specifies whether VSM is enabled.

`WinPE` Data type: `UInt32`

Access type: Read/Write

Qualifiers: none

## Remarks

Class qualifiers for this class include:

- Dynamic
- Secured

  For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/misc/class-and-property-qualifiers).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[Configuration Manager Compliance Settings \(DCM\) Server WMI Classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes)
