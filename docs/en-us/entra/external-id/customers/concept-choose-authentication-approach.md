<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Choose an authentication approach

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Browser-delegated authentication and native authentication are two sign-in approaches in Microsoft Entra External ID that define how your customer-facing app handles the authentication experience. Both approaches are fully supported, but they differ in user experience, development effort, and security model. Understanding these differences helps you choose the approach that best fits your app.

With **browser-delegated authentication**, your app redirects users to a Microsoft-hosted sign-in page in a system browser or embedded web view. Microsoft Entra handles the entire authentication flow, and your app receives tokens after sign-in completes. This approach requires minimal code and offers built-in branding customization.

With **native authentication**, you build the sign-in UI experience directly into your app by using the Microsoft Authentication Library \(MSAL\) SDK or the native authentication API. Users never leave your app. You control every aspect of the UI, but your team is responsible for building and maintaining the authentication experience.

## When to use browser-delegated authentication

Browser-delegated authentication is the better fit when:

- Your app can accommodate a browser redirect during sign-in without disrupting the user experience.
- You prefer lower implementation and maintenance effort. Microsoft manages security updates and new features automatically.
- You want to support the broadest range of platforms and languages with less code.

For specific feature availability, see the [feature comparison](#feature-comparison).

## When to use native authentication

Native authentication is the better fit when:

- You need full control over the sign-in UI so it blends seamlessly into your app.
- A browser redirect would disrupt the user experience for your target platform.
- Your organization operates both the app and the authorization server, and your users perceive them as a single entity.
- Your development team can take on the additional implementation effort and ongoing maintenance.

For specific feature availability, see the [feature comparison](#feature-comparison).

## Feature comparison

The following table shows which features are available in each approach.

| Feature | Browser-delegated authentication | Native authentication |
| --- | --- | --- |
| Sign up and sign in with email one-time passcode \(OTP\) | ✔️ | ✔️ |
| Sign up and sign in with email and password | ✔️ | ✔️ |
| Sign in with email and password can use username \(alias\) and password | ✔️ | ✔️ |
| Self-service password reset \(SSPR\) | ✔️ | ✔️ |
| Custom claims provider | ✔️ | ✔️ |
| Multifactor authentication with email one-time passcode \(OTP\) | ✔️ | ✔️ |
| Multifactor authentication with SMS one-time passcode \(OTP\) | ✔️ | ✔️ |
| Social identity provider sign-in \(Apple, Facebook, and Google\)<sup>1</sup> | ✔️ | ✔️ |
| Single sign-on \(SSO\)<sup>2</sup> | ✔️ | ✔️ |

<sup>1</sup> Even with native authentication, social sign-in still uses a browser window for the identity provider step.

<sup>2</sup> Native authentication supports SSO for embedded web views only. Cross-app SSO through system browsers isn't available with native authentication.

## Supported languages and frameworks

The following languages and frameworks are supported for each approach.

| Approach | Supported languages and frameworks |
| --- | --- |
| Browser-delegated authentication | - ASP.NET Core<br>- Android \(Kotlin, Java\)<br>- iOS/macOS \(Swift, Objective-C\)<br>- JavaScript<br>- React<br>- Angular<br>- Node.js<br>- Python<br>- Java |
| Native authentication | - Android \(Kotlin, Java\)<br>- iOS/macOS \(Swift, Objective-C\)<br>- Web \(JavaScript, React, Angular\)<br><br>For other languages and platforms, you can use the [native authentication API](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api). |

## Security considerations

Browser-delegated authentication is the more secure option. Microsoft manages the sign-in surface, which reduces your app's exposure to phishing and credential-harvesting attacks.

With native authentication, your development team shares security responsibility with Microsoft Entra. Your team must follow security best practices for handling user credentials. Before you choose native authentication, discuss the security implications with your app's business owner and development team.

## Next steps

After you decide on an approach, register your app to continue your integration, or return to the [planning guide](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution) for the full sequence of steps:

**Browser-delegated authentication**:

- [Register an app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)
- [Samples by app type and language](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all)

**Native authentication**:

- [Native authentication overview](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)
- [Android native authentication tutorial](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-android-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)
- [iOS native authentication tutorial](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-run-native-authentication-sample-ios-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)
- [Native authentication in a React SPA](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication-single-page-app-sdk-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)
