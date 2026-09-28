<!-- Source: https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-configure-single-sign-on-password-vaulting -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Password vaulting for single sign-on with application proxy

## Overview

Microsoft Entra application proxy helps you improve productivity by publishing on-premises applications so that remote employees can securely access them. In the Microsoft Entra admin center, you can also set up single sign-on \(SSO\) to these apps. Your users only need to authenticate with Microsoft Entra ID, and they can access your enterprise application without having to sign in again.

Application proxy supports several [single sign-on modes](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/plan-sso-deployment#choosing-a-single-sign-on-method). Password-based sign-on is intended for applications that use a username and password combination for authentication. Microsoft Entra ID stores the sign-in information and automatically provides it to the application when your users access it remotely.

## Prerequisites

This article requires that an app is published and tested with application proxy. For more information, see [Publish applications using Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-add-on-premises-application).

## Set up password vaulting for your application

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#application-administrator).
2. Browse to **Entra ID** > **Enterprise apps** > **All applications**.
3. From the list, select the app that you want to set up with SSO.
4. Select **application proxy**.
5. Change the **Pre Authentication type** to **Passthrough** and select **Save**. Later you can switch back to **Microsoft Entra ID** type again.
6. Select **Single sign-on**.
7. For the SSO mode, choose **Password-based Sign-on**.
8. For the Sign-on URL, enter the URL for the page where users enter their username and password to sign in to your app outside of the corporate network. The page could be the External URL that you created when you published the app through application proxy.

   ![Screenshot that shows the password-based sign-on configuration with URL entry.](https://learn.microsoft.com/en-us/entra/identity/app-proxy/media/application-proxy-configure-single-sign-on-password-vaulting/password-sso.png)

9. Select **Save**.
10. Select **application proxy**.
11. Change the **Pre Authentication type** to **Microsoft Entra ID** and select **Save**.
12. Select **Users and Groups**.
13. Assign users to the application.
14. Select **Add user**.
15. If you want to predefine credentials for a user, check the box in front of the user name and select **Update credentials**.
16. Browse to **Entra ID** > **App registrations** > **All applications**.
17. From the list, select the app that you configured with Password SSO.
18. Select **Branding**.
19. Update the **Home page URL** with the **Sign on URL** from the password SSO page and select **Save**.

## Test your app

Go to the My Apps portal. Sign in with your credentials \(or the credentials for a test account that you set up with access\). After you sign in, select the icon of the app. Opening the My Apps portal might trigger the installation of the My Apps Secure Sign-in browser extension. If credentials are predefined, the authentication to the app happens automatically. Otherwise, you must specify the user name or password for the first time.

## Next steps

- For more information about other ways to implement [single sign-on](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Security considerations for accessing apps remotely with Microsoft Entra application proxy](https://learn.microsoft.com/en-us/entra/identity/app-proxy/application-proxy-security)
