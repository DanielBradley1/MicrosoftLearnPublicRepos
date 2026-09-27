<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/certificates/remove-profiles -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# Remove SCEP and PKCS certificates in Microsoft Intune

In Microsoft Intune, you can use Simple Certificate Enrollment Protocol \(SCEP\) and Public Key Cryptography Standards \(PKCS\) certificate profiles to add certificates to devices.

These certificates can be removed when you [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) or [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) the device. Certificates that were provisioned by Intune are also removed when the profile that provisioned the certificate no longer targets the device or user. There are other scenarios where certificates are automatically removed, and scenarios where certificates stay on the device. This article lists some common scenarios and their effect on PKCS and SCEP certificates.

Note

To remove and revoke certificates for a user who's being removed from on-premises Active Directory or Microsoft Entra ID, follow these steps in order:

1. Wipe or retire the user's device.
2. Remove the user from on-premises Active Directory or Microsoft Entra ID.

The majority of this article applies to SCEP and PKCS certificate profiles, but not to imported PKCS certificates. Imported PKCS certificates are removed by Intune when company data is removed from the device or when a device is unenrolled from management.

## Manually deleted certificates

Manual deletion of a certificate is a scenario that applies across platforms and certificates provisioned by SCEP or PKCS certificate profiles. For example, a user might delete a certificate from a device, when the device remains targeted by a certificate policy.

In this scenario, after the certificate is deleted, the next time the device checks in with Intune it's found to be out of compliance as it is missing the expected certificate. Intune then issues a new certificate to restore the device to compliance. No other action is needed to restore the certificate.

Note

SCEP certificates are [removed but not revoked](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/third-party-ca-scep#removing-certificates) when using a third-party certification authority.

## Windows devices

### SCEP certificates

A SCEP certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.
- The device is removed from a Microsoft Entra group.
- A certificate profile is removed from the group assignment.

A SCEP certificate is revoked when:

- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.
- A certificate profile is removed from the group assignment.

SCEP certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.

### PKCS certificates

A PKCS certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

A PKCS certificate is removed when:

- The PKCS certificate profile no longer targets the device or user.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

PKCS certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.
- An administrator changes or updates the PKCS profile.

## iOS devices

### SCEP certificates

A SCEP certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.
- The device is removed from the Microsoft Entra group.
- A certificate profile is removed from the group assignment.

A SCEP certificate is revoked when:

- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

SCEP certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.

### PKCS certificates

A PKCS certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

A PKCS certificate is removed when:

- A certificate profile is removed from the group assignment.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

PKCS certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.
- An administrator changes or updates the PKCS profile.

## Android KNOX devices

### SCEP certificates

A SCEP certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.

A SCEP certificate is revoked when:

- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.
- The device is removed from a Microsoft Entra group.
- A certificate profile is removed from the group assignment.
- An administrator removes the user or group from Microsoft Entra ID.
- An administrator changes or updates the SCEP profile.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

SCEP certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.

### PKCS certificates

A PKCS certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

PKCS certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.
- An administrator changes or updates the PKCS profile.
- A certificate profile is removed from the group assignment.

Note

Android for Work devices are not validated for the preceding scenarios. Android legacy devices \(any non-Samsung, non-work profile devices\) are not enabled for certificate removal.

## macOS certificates

### SCEP certificates

A SCEP certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs a [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.
- The device is removed from a Microsoft Entra group.
- A certificate profile is removed from the group assignment.

A SCEP certificate is revoked when:

- An administrator changes or updates the SCEP profile.

SCEP certificates *stay* on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- An administrator removes the user or group from Microsoft Entra ID.

Note

Using the [wipe](https://learn.microsoft.com/en-us/intune/device-management/actions/wipe) action to factory reset macOS devices is not supported.

### PKCS certificates

A PKCS certificate is revoked *and* removed when:

- A user unenrolls.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

A root certificate is removed when:

- A user unenrolls.
- An administrator runs the [retire](https://learn.microsoft.com/en-us/intune/device-management/actions/retire) action.

PKCS certificates stay on the device \(certificates aren't revoked or removed\) when:

- A user loses the Intune license.
- An administrator withdraws the Intune license.
- A certificate profile is removed from the group assignment. \(The Profile is removed.\)
- An administrator removes the user or group from Microsoft Entra ID.
- An administrator changes or updates the PKCS profile.

## Next steps

[Use certificates for authentication](https://learn.microsoft.com/en-us/intune/fundamentals/certificates/overview)
