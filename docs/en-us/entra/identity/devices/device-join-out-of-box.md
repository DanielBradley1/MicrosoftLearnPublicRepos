<!-- Source: https://learn.microsoft.com/en-us/entra/identity/devices/device-join-out-of-box -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Microsoft Entra join a new Windows device during the out of box experience

This tutorial shows you how to join a new Windows 11 device to Microsoft Entra ID during the out-of-box experience \(OOBE\). When you join a device during OOBE, the device becomes part of your organization's directory and can be managed according to their policies.

This functionality pairs well with mobile device management platforms like [Microsoft Intune](https://learn.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune) and tools like [Windows Autopilot](https://learn.microsoft.com/en-us/mem/autopilot/windows-autopilot) to ensure devices are configured according to your standards.

## Prerequisites

To Microsoft Entra join a Windows device, the device registration service must be configured to enable you to register devices. For more information about prerequisites, see the article [How to: Plan your Microsoft Entra join implementation](https://learn.microsoft.com/en-us/entra/identity/devices/device-join-plan).

Tip

Windows Home Editions do not support Microsoft Entra join. These editions can still access many of the benefits by using [Microsoft Entra registration](https://learn.microsoft.com/en-us/entra/identity/devices/concept-device-registration).

For information about how to complete Microsoft Entra registration on a Windows device, see the support article [Register your personal device on your work or school network](https://support.microsoft.com/account-billing/register-your-personal-device-on-your-work-or-school-network-8803dd61-a613-45e3-ae6c-bd1ab25bf8a8).

## Join a new Windows 11 device to Microsoft Entra ID

Your device might restart several times as part of the setup process. Your device must be connected to the Internet to complete Microsoft Entra join.

1. Turn on your new device and start the setup process. Follow the prompts to set up your device.
2. When prompted **How would you like to set up this device?**, select **Set up for work or school**.  ![Screenshot of Windows 11 out-of-box experience showing the option to set up for work or school.](https://learn.microsoft.com/en-us/entra/identity/devices/media/device-join-out-of-box/windows-11-first-run-experience-work-or-school.png)
3. On the **Let's set things up for your work or school** page, provide the credentials that your organization provided. These credentials might include a username and password, or a method like a [passkey](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-synced-passkeys). Your users should be able to use the credential that they have to sign in to Microsoft Entra ID, including [passkeys](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-synced-passkeys), as shown in the following animation.

   ![Animation of how to sign in to Windows 11 out of box by using a passkey.](https://learn.microsoft.com/en-us/entra/identity/devices/media/device-join-out-of-box/passkey-sign-in.gif)
4. Continue to follow the prompts to set up your device.
5. Microsoft Entra ID checks if an enrollment in mobile device management is required and starts the process.

   1. Windows registers the device in the organization's directory and enrolls it in mobile device management, if applicable.

6. If you sign in with a managed user account, Windows takes you to the desktop through the automatic sign-in process. Federated users are directed to the Windows sign-in screen to enter your credentials.  ![Screenshot of Windows 11 at the desktop after first run experience Microsoft Entra joined.](https://learn.microsoft.com/en-us/entra/identity/devices/media/device-join-out-of-box/windows-11-first-run-experience-complete-automatic-sign-in-desktop.png)

For more information about the out-of-box experience, see the support article [Join your work device to your work or school network](https://support.microsoft.com/account-billing/join-your-work-device-to-your-work-or-school-network-ef4d6adb-5095-4e51-829e-5457430f3973).

## Verification

To verify whether a device is joined to your Microsoft Entra ID, review the **Access work or school** dialog on your Windows device found in **Settings** > **Accounts**. The dialog should indicate that you're connected to Microsoft Entra ID, and provides information about areas managed by your IT staff.

![Screenshot of Windows 11 Settings app showing current connection.](https://learn.microsoft.com/en-us/entra/identity/devices/media/device-join-out-of-box/windows-11-access-work-or-school.png)

## Related content

- For more information about managing devices, see [Managing device identities](https://learn.microsoft.com/en-us/entra/identity/devices/manage-device-identities).
- [What is Microsoft Intune?](https://learn.microsoft.com/en-us/mem/intune/fundamentals/what-is-intune)
- [Overview of Windows Autopilot](https://learn.microsoft.com/en-us/autopilot/windows-autopilot)
- [Passwordless authentication options for Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2)
