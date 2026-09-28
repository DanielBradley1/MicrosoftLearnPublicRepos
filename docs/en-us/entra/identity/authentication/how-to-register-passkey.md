<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-register-passkey -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Register a synced passkey \(FIDO2\)

This article shows how users can register a synced passkey \(FIDO2\) by using the **Passkey** flow. A synced passkey is stored in a passkey provider \(such as iCloud Keychain or Google Password Manager\) and syncs across the user's devices. For an overview of synced passkeys, see [Synced passkeys in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-synced-passkeys).

Note

Looking to provide passkeys \(FIDO2\) on behalf of users? Use our [APIs](https://aka.ms/passkeyprovision).

## Prerequisites

You need to configure a password manager on your mobile device to save a synced passkey.

- On your iOS device, you need to set **Set Up Codes In** to **Passwords** to manage synced passkeys. Open **Settings** > **General** > **AutoFill & Passwords**. For **Set Up Codes In**, select **Passwords**.
- On your Android device, open **Settings** > **Security and privacy** > **More security settings** > **Passwords, passkeys, and autofill**, and then select a provider.

## Register a passkey

To register a passkey on your device, follow these steps:

1. Open a web browser and sign in to [Security info](https://mysignins.microsoft.com/security-info).
2. Sign in with multifactor authentication \(MFA\).
3. Tap **+ Add sign-in method**.

   [![Screenshot of the Security info page on iOS showing the Add sign-in method option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/add-sign-in-method-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/add-sign-in-method-ios.png#lightbox)
4. Tap **Passkey**.

   [![Screenshot of the Add a sign-in method page on iOS showing the Passkey option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/choose-passkey-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/choose-passkey-ios.png#lightbox)
5. Tap **Next**.

   [![Screenshot of the Sign in faster with your face, fingerprint, or PIN page on iOS showing the Next option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/sign-in-faster-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/sign-in-faster-ios.png#lightbox)
6. On iOS, tap **Next**.

   [![Screenshot of the Setting up your passkey page on iOS showing the Next option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/setting-up-passkey-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/setting-up-passkey-ios.png#lightbox)

   On Android, tap **Continue**.

   Note

   The steps to enable passkey providers on Android might vary based on the make and model of your device. Search for Passkey on your device settings, or consult your device manufacturer for guidance. If your device runs Android 14 and you can't enable Authenticator as a passkey provider, we recommend that you upgrade to Android 15.

   [![Screenshot of the Create a passkey page on Android showing the account name and Continue option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/android-complete.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/android-complete.png#lightbox)
7. Name your passkey and tap **Next**.

   [![Screenshot of the Let's name your passkey page showing the passkey name field and Next option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/name-passkey.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/name-passkey.png#lightbox)
8. After the passkey is created, tap **Done**.

   [![Screenshot of the Passkey created page showing the Done option.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/passkey-created-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/passkey-created-ios.png#lightbox)
9. You can see your passkey in [Security info](https://mysignins.microsoft.com/security-info).

   [![Screenshot of the Security info page showing the registered passkey.](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/passkey-added-ios.png)](https://learn.microsoft.com/en-us/entra/identity/authentication/media/how-to-register-passkey/passkey-added-ios.png#lightbox)

## Related content

To register a passkey on a different type of authenticator, see:

- [Register passkeys in Microsoft Authenticator](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-register-passkey-authenticator)
- [Register a passkey with a FIDO2 security key](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-register-passkey-with-security-key)
