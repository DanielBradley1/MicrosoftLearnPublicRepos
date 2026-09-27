<!-- Source: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android-enterprise -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Android Enterprise device settings to configure email, authentication, and synchronization in Intune

This article describes the different email settings you can control on Android Enterprise personally owned devices with a work profile. As part of your mobile device management \(MDM\) solution, use these settings to configure an Exchange email server, use SSL to encrypt emails, and more. The email profile uses the email app on the device, and allows users to connect to their organization email.

As an Intune administrator, you can create and assign email settings to Android Enterprise personally owned devices with a work profile. To learn more about email profiles in Intune, go to [configure email settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email).

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> This feature supports the following platform:
> 
> - Android Enterprise personally owned devices with a work profile \(BYOD\)
> 
> On Android Enterprise Fully Managed, Dedicated, and Corporate-owned Work Profiles, use [app configuration policies](https://learn.microsoft.com/en-us/intune/app-management/configuration/configure-managed-android).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> To configure this policy and start collecting inventory data from devices, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/overview).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> - Deploy your [email app](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email). If your profile uses Gmail and you want to use modern authentication, you might need to deploy the Google Chrome app to the work profile.
> - Create an [Android Enterprise email device configuration profile](https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-email) > **Personally-owned work profile**.

## Android Enterprise

- **Email app**: Select **Gmail** or **Nine Work**. This client app connects to the email server you enter.
- **Email server**: Enter the host name of your Exchange server. For example, enter `outlook.office365.com`.
- **Username attribute from Microsoft Entra ID**: This name is the attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the username that this profile uses. Make sure your users have email addresses that match the attribute you select. Your options:

  - **User Principal Name**: Gets the name, like `user1` or `user1@contoso.com`.
  - **User name**: Gets only the name, like `user1`.

- **Email address attribute from Microsoft Entra ID**: This name is the email attribute Intune gets from Microsoft Entra ID. Intune dynamically generates the email address this profile uses. Your options:

  - **User principal name**: Uses the full principal name, like `user1@contoso.com` or `user1`, as the email address.
  - **Primary SMTP address**: Uses the primary Simple Mail Transfer Protocol \(SMTP\) address, like `user1@contoso.com`, to sign in to Exchange.

- **Authentication method**: Select **Username and Password** or **Certificates** as the authentication method used by the email profile.

  - If you select **Certificate**, select a client [SCEP](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/scep-profiles) or [PKCS](https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles) certificate profile that you previously created to authenticate the Exchange connection.

- **SSL**: **Enable** uses Secure Sockets Layer \(SSL\) communication when sending emails, receiving emails, and communicating with the Exchange server. **Disable** doesn't use SSL.
- **Amount of email to synchronize**: Select the amount of time of email you want to synchronize. Or, select **Unlimited** to synchronize all available email.
- **Content type to sync** \(Nine Work only\): Select the data you want to synchronize on the devices. Your options:

  - **Contacts**: **Enable** allows end users to sync contacts to their devices.
  - **Calendar**: **Enable** allows end users to sync the calendar to their devices.
  - **Tasks**: **Enable** allows end users to sync any tasks to their devices.

## Related articles

- [Assign the profile](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile) and [monitor its status](https://learn.microsoft.com/en-us/intune/device-configuration/monitor-device-profile).
- Create email profiles for [Android Samsung Knox](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-android), [iOS/iPadOS](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-ios), and [Windows](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-email-settings-windows) devices.
