<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Android device administrator settings that configure email in Intune

This article describes the different email settings you can control on Android device administrator Samsung Knox devices in Intune. As part of your mobile device management \(MDM\) solution, use these settings to configure an Exchange email server, use SSL to encrypt emails, and more. The email profile uses the native or built-in email app on the device, and allows users to connect to their organization email.

This feature applies to:

- Android device administrator \(DA\)

As an Intune administrator, you can create and assign email settings to Android Samsung Knox Standard devices. To learn more about email profiles in Intune, go to [configure email settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email).

Important

Android device administrator \(DA\) management is deprecated and no longer available for devices with access to Google Mobile Services \(GMS\). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

## Before you begin

- Create an [Android device administrator Email device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email).

## Android \(Samsung Knox\)

- **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
- **Account name**: Enter the display name for the email account. This name is shown to users on their devices.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Your options:

  - **User principal name**: Gets the name, like `user1` or `user1@contoso.com`.
  - **User name**: Gets only the name, like `user1`.
  - **sAM Account Name**: Requires the domain, like `domain\user1`. sAM account name is only used with Android devices. Also enter:

    - **User domain name source**: Select **Microsoft Entra ID** or **Custom**.

      When choosing to get the attributes from Microsoft Entra ID, enter:

      - **User domain name attribute from Microsoft Entra ID**: Select to get the **Full domain name** or the **NetBIOS name** attribute of the user.


      When choosing to use **Custom** attributes, enter:


      - **Custom domain name to use**: Enter a value that Intune uses for the domain name, like `contoso.com` or `contoso`.

- **Email address attribute from Microsoft Entra ID**: This name is the email attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the email address that this profile uses. Make sure your users have email addresses that match the attribute you select. Your options:

  - **User principal name**: Uses the full principal name, like `user1@contoso.com` or `user1`, as the email address.
  - **Primary SMTP address**: Uses the primary Simple Mail Transfer Protocol \(SMTP\) address, like `user1@contoso.com`, to sign in to Exchange.

- **Authentication method**: Select **Username and Password** or **Certificate** as the authentication method used by the email profile.

  - If you select **Certificate**, select a client [SCEP](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/scep-profiles) or [PKCS](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.

### Security settings

- **SSL**: **Enable** uses Secure Sockets Layer \(SSL\) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** does use SSL.
- **S/MIME**: **Disable S/MIME** \(default\): Doesn't use an S/MIME email certificate to sign, encrypt, or decrypt emails. **Enable S/MIME** sends outgoing email using S/MIME encryption. Also enter:

  - Select a client [SCEP](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/scep-profiles) or [PKCS](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.

### Synchronization settings

- **Amount of email to synchronize**: Select the number of days of email that you want to synchronize, or select **Unlimited** to synchronize all available email.
- **Sync schedule**: Select the schedule for devices to synchronize data from the Exchange server. You can also select **As Messages arrive**, which synchronizes data when it arrives, or **Manual**, where the user of the device must initiate the synchronization.

### Content type to sync

Select the content types that you want to synchronize on the devices.

**Not configured** disables the setting. When set to **Not configured**, if an end user enables synchronization on the device, synchronization is disabled again when the device syncs with Intune, as the policy is reinforced.

- **Contacts**: **Enable** allows end users to sync contacts to their devices.
- **Calendar**: **Enable** allows end users to sync the calendar to their devices.
- **Tasks**: **Enable** allows end users to sync any tasks to their devices.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create email profiles for [Android Enterprise](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android-enterprise), [iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-ios), and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-windows).
