<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/protect-passwordless-students -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Passwordless for Students

With the rise of security threats, it's critical that schools start to think about ways to use security features typically avoided for students.

This article describes a way to use passwordless credentials in schools.

Requirements:

- A license or bundle that includes Entra P1.

Distributing passwordless phishing resistant credentials to students has been challenging due to the multifactor authentication \(MFA\) requirement for setup \(sometimes referred to as bootstrapping\). Temporary Access Pass \(TAP\) provides a phone free option for users to set up credentials, including device-bound passwordless credentials.

A Temporary Access Pass is a time-limited passcode that can be configured for single or multiple use. Users can sign in with a TAP to onboard other passwordless authentication methods, such as Microsoft Authenticator, FIDO2, Windows Hello for Business, Platform single sign-on \(SSO\) with Secure Enclave, and Passkeys.

Administrators can create a TAP and distribute to students. Students can use the TAP to create the passwordless credential. Students can then use the passworldess credential to sign in to the device.

![A diagram showing the steps to create and use a passwordless credential for students by authenticating using temporary access pass. First, the admin creates TAP. Second, the student uses TAP to create passwordless credential. Third, the student uses passwordless credential.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/bootstrap-using-temporary-access-pass.png)

Each operating system has a different implementation for device-bound passwordless credentials:

| **Operating system** | **Hardware bound key technology** | **Suitable for** | **Hardware requirement** | **Biometric information** |
| --- | --- | --- | --- | --- |
| Windows | Windows Hello for Business | 1:1 devices | [Trusted Platform Module \(TPM\)](https://support.microsoft.com/en-us/topic/what-is-tpm-705f241d-025d-4470-80c5-4feeb24fa1ee) | [Windows Hello](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/faq) |
| macOS | Platform SSO with Secure Enclave \(preview\) | 1:1 devices | [Secure Enclave](https://support.apple.com/en-gb/guide/security/sec59b0b31ff/web) | [TouchID](https://support.apple.com/en-us/105095) |
| iOS | Passkeys with Microsoft Authenticator \(preview\) | 1:1 devices | iOS 16+ | [FaceID](https://support.apple.com/en-us/102381) |
| Android | Passkeys with Microsoft Authenticator \(preview\) | 1:1 devices | Android 14+ | OEM-specific |
| Windows, macOS | FIDO2 Security Keys | 1:1 or shared devices | [FIDO2 Security Key](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-fido2-hardware-vendor) | Various |
| Passkeys \(syncable\) - coming later in 2024 | n/a | Not hardware bound – protection varies by passkey provider vendor | n/a | Various |

These technologies provide Phishing-resistant authentication strength because they use a combination of a hardware bound private key, the user's physical possession of that device. The local device PIN or password used to unlock or "release" the device specific private key. The private key never leaves the device or is transmitted over the network. Microsoft Entra ID only possesses a corresponding public key used to validate data signed by the hardware bound private key. The PIN or local password is device specific and can't be used to log into services or other devices \(unless the user uses the same PIN\).

Tip

For the best passwordless experience on 1:1 devices for K-12 Students and Devices, Microsoft recommends TAP + Windows Hello \(or other platform specific hardware bound key technology\). For shared devices, Microsoft recommends [FIDO2 Security Keys](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-fido2-hardware-vendor).

For more information about Passwordless and Microsoft Entra ID, see [Microsoft Entra passwordless sign-in](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passwordless).

## Passwordless user experience

- [Windows](#tabpanel_1_windows)
- [macOS](#tabpanel_1_macOS)

These steps demonstrate the user experience during Autopilot in the following conditions:

- The user has a temporary access pass.
- Windows Hello for Business is enabled for this device.

If the device is already provisioned, the experience is the same from step 2 when the user logs in to a device with Windows Hello for Business enabled.

1. Sign in with a work or school account and use the temporary access pass to start Autopilot.
2. After provisioning is complete, the user is prompted to configure Windows Hello for Business.
3. The user is prompted to enter their temporary access pass.
4. The user creates a PIN and sets up biometric credentials if supported by the device.
5. The user can now sign in with their PIN or biometrics.

![A GIF demonstrating the experience of configuring Windows Hello for Business using Temporary Access Pass during Autopilot user-driven mode.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/protect-windows-hello-with-tap.gif)

#### User experience when a user doesn't have a TAP or the TAP is expired

If the user doesn't have a temporary access pass when going through Autopilot, they are prompted to register for multifactor authentication:

[![A screenshot showing the Windows Hello for Business more information required screen.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/windows-hello-no-tap-smaller.png)](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/windows-hello-no-tap.png#lightbox)

If you assign a temporary access pass to a user and ask them to try again or restart the computer, users are prompted to use the temporary access pass instead.

These steps demonstrate the user experience during Automated Device Enrollment with user driven mode in the following conditions:

- The user has a temporary access pass.
- Platform SSO with Secure Enclave is enabled for this device.

If the device is already provisioned, the experience is the same from step 3 when the user logs in to a device with Platform SSO with Secure Enclave enabled.

1. During setup assistant, the user enters their username and temporary access pass.
2. The user creates their local account with a local account password \(which could be a PIN\).
3. Once at the desktop, the user selects to register their device with Microsoft Entra ID.
4. During the registration process, the user uses their temporary access pass to authenticate.
5. The user selects to allow Company Portal as a Passkey provider in settings.
6. The user can now sign in with their PIN or biometrics and gain access to the device bound credential to authenticate to Microsoft Entra ID using Platform SSO.

![A GIF demonstrating the experience of configuring Platform SSO with secure enclave using Temporary Access Pass during Automated Device Enrollment.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/protect-macos-platform-sso-with-tap.gif)

For more details, check out the following articles depending on the scenario:

- [Join a Mac device with Microsoft Entra ID during the out of box experience](https://learn.microsoft.com/en-us/entra/identity/devices/device-join-macos-platform-single-sign-on)
- [Join a Mac device with Microsoft Entra ID using Company Portal](https://learn.microsoft.com/en-us/entra/identity/devices/device-join-microsoft-entra-company-portal)

## Planning for Passwordless

The main challenge of provisioning passwordless credentials to students is distributing the TAP.

Options include:

- Generating TAP when passwords are provided to students for the first time or providing only a TAP and no password to enforce passwordless.
- Generating and distributing a TAP when students receive new devices.
- Enabling the passwordless authentication options and asking students to configure them and call IT support to request a TAP when setting it up.
- Delegating access to create TAP to local IT or teachers.

You can use [Authentication Methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods) in Entra to control which users can use specific types of authentication methods. For example, you could allow teachers and staff to use Microsoft Authenticator but only allow students to use Temporary Access Pass.

| **Target user attributes** | **Typical users** | **Authentication Methods** |
| --- | --- | --- |
| Can use iOS or Android devices in addition to their main device | Staff, university students, students in schools where mobile devices are allowed | ✔️ Microsoft Authenticator  <br>✔️ Temporary Access Pass  <br>✔️ FIDO2 Security Key  <br>✔️ Passkeys |
| No mobile device access | K-12 students | ✔️ Temporary Access Pass  <br>✔️ FIDO2 Security Key  <br>✔️ Passkeys |

For more information about the authentication methods available in Entra, see [Authentication Methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods).

## Configure Authentication Methods

1. Configure Entra to use Authentication Methods policies

   Authentication methods can be configured after multifactor authentication and self-service password reset policy settings are migrated to the Authentication Methods functionality. For more information, see [How to migrate MFA and Self Service Password Reset policy settings to the Authentication methods policy for Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-methods-manage).
2. Configure the authentication methods based on your requirements

   Use Authentication Methods to target the required configuration at groups of users. For more information, see [Authentication Methods](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-methods). For example:

   - Change the target groups for Phone, SMS, Microsoft Authenticator methods to include staff and exclude students.
   - Change the target group of Temporary Access Pass to include students.

3. Issue Temporary Access Pass

   Administrators can issue Temporary access passes and distribute them to users. For more information, see [Create a temporary access pass](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-temporary-access-pass#create-a-temporary-access-pass).

## Configure Devices

Configure the passwordless sign in method for each operating system to meet your requirements.

- [Windows](#tabpanel_2_windows)
- [macOS](#tabpanel_2_macOS)

For Intune-managed devices, there are two methods for configuring Windows Hello for Business:

- **Tenant-wide**. The tenant wide Windows Hello for Business policies in **Devices** > **Windows** > **Windows** **Enrollment > Windows Hello for Business**. It's typical for schools to disable Windows Hello for Business to avoid students being asked to set up multifactor authentication during sign in.
- **Targeted using policies**. Targeted policies take precedence over the tenant-wide policy, allowing settings to be targeted at groups or to stage the rollout.

For more information, see [Configure Windows Hello for Business](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/configure).

Additional steps are required to configure single sign-on access to on premises resources with Windows Hello for Business credentials. For more information, see [Configure single sign-on for Microsoft Entra joined devices](https://learn.microsoft.com/en-us/windows/security/identity-protection/hello-for-business/hello-hybrid-aadj-sso).

#### Customize the Windows Hello for Business experience

These settings are optional but can be used to customize the Windows Hello for Business experience.

- [DisablePostLogonProvisioning](https://learn.microsoft.com/en-us/windows/client-management/mdm/passportforwork-csp) – By default Windows Hello for Business requires provisioning during sign-in. With this setting enabled, the sign-in prompt is disabled. Users can configure Windows Hello for Business in the settings app.
  | Configuration | Value |
  | --- | --- |
  | **OMA-URI:** | `./Device/Vendor/MSFT/PassportForWork/**Microsoft Entra ID Tenant ID**/Policies/DisablePostLogonProvisioning` |
  | **Data type:** | Boolean |
  | **Value:** | True |
- [EnablePasswordlessExperience](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-authentication) - When the policy is enabled on Windows 11, certain Windows authentication scenarios don't offer users the option to use a password, helping organizations and preparing users to gradually move away from passwords. For more information, see [Windows passwordless experience](https://learn.microsoft.com/en-us/windows/security/identity-protection/passwordless-experience/).
  | Configuration | Value |
  | --- | --- |
  | **OMA-URI:** | `./Device/Vendor/MSFT/Policy/Config/Authentication/EnablePasswordlessExperience` |
  | **Data type:** | Integer |
  | **Value:** | 1 |

For steps on creating a custom policy, see [Add custom settings for Windows 10/11 devices in Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/configuration/custom-settings-windows-10).

To use passwordless credentials on macOS, you can set up **Platform SSO with secure enclave**. For more information about setting up Platform SSO with Intune, see [https://learn.microsoft.com/mem/intune/configuration/platform-sso-macos](https://learn.microsoft.com/en-us/mem/intune/configuration/platform-sso-macos).

## Monitor Passworldess Authentication

Entra includes reports for monitoring authentication methods. For more information, see [Authentication Methods Activity](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity).

Use the reports to see your rollout progress and identify when users are using paswordless credentials.

## Enforce Authentication Strength with Conditional Access

Access to services that use Microsoft Entra ID for authentication can be restricted based on authentication method strength, among other conditions, using Conditional Access.

For example, to require students access services using Microsoft Entra ID for authentication use a managed device with passwordless credentials, configure a Conditional Access policy with these settings:

| Configuration | Value |
| --- | --- |
| **Name** | Students |
| **Target** | All students |
| **Grant** | Complaint device: yes  <br>Authentication strength: Phishing-resistant |

For more information on authentication strength in conditional access policies, see [Overview of Microsoft Entra authentication strength](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-strengths).

For instructions on configuring Conditional Access policies, see [What is Conditional Access in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview).

Tip

In scenarios where devices are shared among multiple users, an alternative passwordless authentication option is FIDO 2 security keys. Shared devices could be excluded from conditional access policies based on location however this isn't recommended.

## Manage Passwordless Credentials

Passwordless credentials are unaffected by password changes, resets, or policies. If a device is compromised or stolen, you should follow procedures required by your security team. Some examples of actions could include:

- Taking no action until a compromise is investigated.
- Triggering a remote wipe of the compromised device.
- Disabling the credential or user account.

If a device is compromised, you may choose to delete the associated passwordless credential from Microsoft Entra ID to prevent unauthorized use.

To remove an authentication method associated with a user account, delete the key from the user's authentication method. You can identify the associated device in the **Detail** column.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) and search for the user whose passkey needs to be removed.
2. Select **Authentication methods** > next to the relevant authentication method, select the "…" menu and then select **Delete**.

## Next Steps

For more information about enrolling your devices into Intune, go to:

- [Tutorial: Set up and configure a cloud-native Windows endpoint with Microsoft Intune](https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/tutorial-cloud-native-setup?tabs=intuneadminconsole)
- [End-to-end guide to get started with macOS endpoints](https://learn.microsoft.com/en-us/mem/solutions/end-to-end-guides/macos-endpoints-get-started)
