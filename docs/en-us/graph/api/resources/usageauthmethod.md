<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/usageauthmethod?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-12 -->

# usageAuthMethod enum type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the authentication method used for user credential and registration activity.

## Members

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following members in this evolvable enum: `externalAuthMethod`, `hardwareOneTimePasscode`, `windowsHelloForBusiness`, `microsoftAuthenticatorPasswordless`, `temporaryAccessPass`, `macOsSecureEnclaveKey`, `passKeyDeviceBound`, `passKeyDeviceBoundAuthenticator`, `passKeyDeviceBoundWindowsHello`, `softwareOneTimePasscode`, `microsoftAuthenticatorPush`, `mobilePhone`, `sms`, `alternateMobilePhone`, `fido2SecurityKey`, `oneTimePasscode`, `passKeySynced`, `qrCode`.

| Member | Description |
| :--- | :--- |
| email | Represents the email authentication method. |
| mobileSMS | Represents the mobile SMS authentication method. |
| mobileCall | Represents the mobile call authentication method. |
| officePhone | Represents the office phone authentication method. |
| securityQuestion | Represents the security question authentication method. |
| appNotification | Represents the app notification authentication method. |
| appCode | Represents the app code authentication method. |
| alternateMobileCall | Represents the alternate mobile call authentication method. |
| fido | Represents the FIDO authentication method. |
| appPassword | Represents the app password authentication method. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| externalAuthMethod | Represents an external authentication method. |
| hardwareOneTimePasscode | Represents the hardware one-time passcode authentication method. |
| windowsHelloForBusiness | Represents the Windows Hello for Business authentication method. |
| microsoftAuthenticatorPasswordless | Represents the Microsoft Authenticator passwordless authentication method. |
| temporaryAccessPass | Represents the temporary access pass authentication method. |
| macOsSecureEnclaveKey | Represents the macOS Secure Enclave key authentication method. |
| passKeyDeviceBound | Represents the device-bound passkey authentication method. |
| passKeyDeviceBoundAuthenticator | Represents the device-bound authenticator passkey authentication method. |
| passKeyDeviceBoundWindowsHello | Represents the device-bound Windows Hello passkey authentication method. |
| softwareOneTimePasscode | Represents the software one-time passcode authentication method. |
| microsoftAuthenticatorPush | Represents the Microsoft Authenticator push authentication method. |
| mobilePhone | Represents the mobile phone authentication method. |
| sms | Represents the SMS authentication method. |
| alternateMobilePhone | Represents the alternate mobile phone authentication method. |
| fido2SecurityKey | Represents the FIDO2 security key authentication method. |
| oneTimePasscode | Represents the one-time passcode authentication method. |
| passKeySynced | Represents the synced passkey authentication method. |
| qrCode | Represents the QR code authentication method. |
