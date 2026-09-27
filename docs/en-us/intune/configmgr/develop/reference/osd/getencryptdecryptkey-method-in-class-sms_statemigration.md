<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/getencryptdecryptkey-method-in-class-sms_statemigration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# GetEncryptDecryptKey Method in Class SMS\_StateMigration

The `GetEncryptDecryptKey` Windows Management Instrumentation \(WMI\) class method, in Configuration Manager, retrieves the symmetric key that is used to encrypt and decrypt the user state during state migration.

The following syntax is simplified from Managed Object Format \(MOF\) code and defines the method.

## Syntax

```
SInt32 GetEncryptDecryptKey(
   String Key
);
```

#### Parameters

`Key` Data type: `String`

Qualifiers: \[out\]

The encryption key required to restore user state.

## Return Values

An `SInt32` data type that is 0 to indicate success or non-zero to indicate failure.

For information about handling returned errors, see [About Configuration Manager Errors](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/about-configuration-manager-errors).

## Requirements

## Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-runtime-requirements).

## Development Requirements

For more information, see [Configuration Manager Server Development Requirements](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/reqs/server-development-requirements).

## See Also

[SMS\_StateMigration Server WMI Class](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_statemigration-server-wmi-class) [AddAssociation Method in Class SMS\_StateMigration](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/addassociation-method-in-class-sms_statemigration)
