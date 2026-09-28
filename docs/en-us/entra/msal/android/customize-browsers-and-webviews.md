<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/customize-browsers-and-webviews -->
<!-- Sitemap-Last-Modified: 2025-06-03 -->

# Customize browser and web views for interactive flows

This article explains the key differences between the authorization agents that the Microsoft Authentication Library \(MSAL\) lets your app use and how to enable them. Choosing a specific strategy for authorization agents is optional and lets apps customize additional functionalities. Most apps use MSAL's default settings.

When you use MSAL in your Android application, you choose between using a browser or WebView to launch the interactive sign-in experience.

![Screenshot of a login user experience in MSAL.](https://user-images.githubusercontent.com/16140683/49622087-f36bf680-f97c-11e8-9498-4b481100476e.jpg)

### Single Sign On implications

By default, applications use a browser or custom tabs strategy. This lets the user achieve single sign-on \(SSO\) and reduces the number of times they need to enter their credentials because Microsoft can persist a cookie in the browser. Doing so also enables other native android or web apps to also achieve SSO.

If the application uses a WebView strategy without integrating Authenticator or Company Portal support, users can achieve single sign-on with a single application but not across the device or between native and web apps.

If the application uses MSAL with Authenticator or Company Portal support, users can achieve single sign-on across applications through these apps, assuming they have an active sign-in with one of them.

## WebViews

An app uses the in-app WebView by specifying this line in its configuration JSON passed into MSAL:

```json
"authorization_user_agent" : "WEBVIEW"
```

By using the in-app WebView, the user signs in directly to the app. The tokens are kept inside the app's sandbox and aren't available outside the app's cookie jar. As a result, the user can't get SSO across applications unless they integrate with the Authenticator or Company Portal.

While Webview offers options that developers can use to customize the sign in experience, MSAL only supports enabling zoom inside the webview. Furthermore, this is only available in MSAL-only scenarios, as the broker webview does not support enabling zoom \(MSAL will default to using the broker webivew when a broker hosting app is installed on the device\), regardless of what the MSAL configuration sets. Also, if an app creates its own WebView instance and attempts to sign in with Microsoft Entra, single sign-on \(SSO\) with the Broker won't work. Cookies from the MSAL WebView aren't shared with WebView instances created independently by third-party apps.

## Default Browser + Custom Tab

### Basics

By default, MSAL uses the browser and custom tab strategy. MSAL lets apps explicitly indicate this strategy to prevent changes in future releases to `DEFAULT` using the JSON configuration:

```json
"authorization_user_agent" : "BROWSER"
```

Using the `BROWSER` approach lets users achieve SSO with the device browser. MSAL uses a shared cookie jar, letting other native or web apps get SSO on the device by using the persistent session cookie set by Microsoft.

### Browser Heuristic

Due to the diverse nature of Android OEMs, MSAL can't specify an exact browser package across different Android phone. As a result, MSAL has developed its browser selection heuristic focusing on providing the best cross-device SSO. MSAL's logic is in the following method:

```
[com.microsoft.identity.common.internal.ui.browser.BrowserSelector.select(final Context context)](https://github.com/AzureAD/microsoft-authentication-library-common-for-android/blob/dev/common/src/main/java/com/microsoft/identity/common/internal/ui/browser/BrowserSelector.java#L57)
```

To select which browser to use, MSAL retrieves the full list of browsers installed on the device. The list is in the order returned by the package manager, so indirectly reflects the user's preferences, that is, the default browser, if set, is the first entry in the list. The *first* browser in the list will be selected no matter whether or not the custom tabs supported. However, if it's supported, MSAL launches the custom tab. Custom tabs have a look and feel closer to an in-app WebView and let you customize some basic UI elements. To learn more, see [Custom Tabs in Android](https://developer.chrome.com/multidevice/android/customtabs).

If there's no browser packages on the device, MSAL falls back to use the in-app WebView.

### Additional Notes

> Note on the consistency of the browser list: The operating system determines the order of browsers and lists them from best to worst. If the device default setting isn't changed, the same browser launches for each sign-in, ensuring SSO.

> Note on Chrome: MSAL no longer always prefers Chrome if another browser is set as the default. For example, on the Samsung S7, which has both Samsung Browser and Chrome preinstalled, the Samsung Browser is set as the default browser. MSAL uses the Samsung Browser unless the user changes their preference.

> Note on broker browsers: Some browsers don't support the OAuth 2.0 authorization code flow. In a future release, Microsoft maintains a deny list to ensure these are never chosen.

### Tested Browsers

| Browser | Built-in Browser | Chrome | Opera | Microsoft Edge | UC Browser | Firefox |
| --- | :---: | ---: | ---: | ---: | ---: | ---: |
| Nexus 4 \(API 17\) | pass | pass | not applicable | not applicable | not applicable | not applicable |
| Samsung S7 \(API 25\) | pass\* | pass | pass | pass | fail | pass |
| Huawei \(API 26\) | pass\*\* | pass | fail | pass | pass | pass |
| Vivo \(API 26\) | pass | pass | pass | pass | pass | fail |
| Pixel 2 \(API 26\) | pass | pass | pass | pass | fail | pass |
| Oppo | pass | not applicable\*\*\* | not applicable | not applicable | not applicable | not applicable |
| OnePlus \(API 25 \) | pass | pass | pass | pass | fail | pass |
| Nexus \(API 28\) | pass | pass | pass | pass | fail | pass |
| MI | pass | pass | pass | pass | fail | pass |

\*Samsung's built-in browser is Samsung Internet.

\*\*Huawei's built-in browser is Huawei Browser.

\*\*\*The default browser can't be changed inside the Oppo device setting.
