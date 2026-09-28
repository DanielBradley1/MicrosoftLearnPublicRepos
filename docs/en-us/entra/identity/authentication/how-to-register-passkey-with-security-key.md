<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-register-passkey-with-security-key -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Register a passkey with a FIDO2 security key

FIDO2 security keys are device-bound passkeys stored on a physical authenticator. The private key never leaves the security key, which provides strong protection against remote phishing attacks. Security keys are recommended for highly regulated industries or users with elevated privileges.

This article shows how to register a passkey as an authentication method by using a FIDO2 security key. After registration, you can [sign in with the security key](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-security-key-sign-in).

## First-time registration

To register a passkey for the first time, open [Security info](https://mysignins.microsoft.com/security-info) in a web browser to complete the registration.

1. Open a web browser and sign in to [Security info](https://mysignins.microsoft.com/security-info).
2. Sign in with multifactor authentication \(MFA\).
3. Tap **Add sign-in method** > **Choose a method** > **Passkey**.
4. Tap **Next**.
5. Select where you want to save your passkey \(FIDO2\).

   Note

   Options displayed vary depending on your browser and device operating system. If the device where you started the registration process supports passkeys \(FIDO2\), you'll be asked to save the passkey to that device. Select **Use another device** or **More options** to display additional ways for you to save the passkey.
6. \(Optional\) If you previously set up a passkey \(FIDO2\) on a mobile device and selected the option to remember that device for quicker sign-in, the device name might appear as a selectable option. In this case, do the following steps:

   1. Choose **Security key**.
   2. Follow the prompts to connect your security key and provide a PIN or biometric method.
   3. After you complete these steps, you're redirected to the **My Security info** screen, where you can change the default name for the new sign-in method.
   4. Select **Done** to finish registering the new method.

## Prompted registration

If your organization requires you to register a passkey \(FIDO2\), you're prompted after sign-in.

1. When you see the prompt to add a passkey \(FIDO2\), tap **Next**.
2. You're directed to `login.microsoftonline.com`.
3. Select where you want to save your passkey \(FIDO2\).

   Note

   Options displayed vary depending on your browser and device operating system. If the device where you started the registration process supports passkeys \(FIDO2\), you'll be asked to save the passkey \(FIDO2\) to that device. Select **Use another device** or **More options** to display additional ways for you to save the passkey.
4. \(Optional\) If you previously set up a passkey \(FIDO2\) on a mobile device and selected the option to remember that device for quicker sign-in, the device name might appear as a selectable option. In this case, do the following steps:

   1. Choose **Security key**.
   2. Follow the prompts to connect your security key and provide a PIN or biometric method.
   3. After you complete these steps, you're redirected to the **My Security info** screen, where you can change the default name for the new sign-in method.
   4. Select **Done** to finish registering the new method.

## Related content

- [Sign in with a FIDO2 security key](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-security-key-sign-in)
- [Register a synced passkey \(FIDO2\)](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-register-passkey)
- [Enable passkeys \(FIDO2\) in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-passkeys-fido2)
- [Passkey FAQ](https://learn.microsoft.com/en-us/entra/identity/authentication/passkey-faq)
