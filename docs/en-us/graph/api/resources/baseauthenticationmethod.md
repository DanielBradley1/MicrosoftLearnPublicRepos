<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/baseauthenticationmethod?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-13 -->

# baseAuthenticationMethod enum type

Namespace: microsoft.graph

Defines the base authentication methods available in the system.

## Members

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following member in this evolvable enum: `qrCodePin`.

| Member | Description |
| --- | --- |
| password | Password authentication method. |
| voice | Voice call authentication method. |
| hardwareOath | Hardware OATH token authentication method. |
| softwareOath | Software OATH token authentication method. |
| sms | SMS authentication method. |
| fido | FIDO2 security key authentication method. |
| microsoftAuthenticator | Microsoft Authenticator authentication method. |
| windowsHelloForBusiness | Windows Hello for Business authentication method. |
| temporaryAccessPass | Temporary Access Pass authentication method. |
| email | Email authentication method. |
| x509Certificate | X.509 certificate authentication method. |
| federation | Federation authentication method. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| qrCodePin | QR code PIN authentication method. Use the `Prefer: include-unknown-enum-members` request header to get this value. |
