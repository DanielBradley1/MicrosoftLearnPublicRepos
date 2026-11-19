<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all -->
<!-- Sitemap-Last-Modified: 2026-11-09 -->

# Microsoft Entra External ID app samples and guides

Use these samples and guides to integrate authentication and authorization with Microsoft Entra External ID. Choose by app type, language, or platform. Each guide explains how to build and run a sample or develop your own app, with code comments that explain the integration.

**Applies to external tenants:** Feature support varies by authentication approach and API or SDK version. Compare Microsoft-hosted authentication, Embedded native authentication, and Bring Your Own UX \(BYO UX\) in the [authentication approach overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach). Check feature availability in the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability).

**Sample inventory:** This index lists Microsoft-hosted and Embedded native authentication examples. No Bring Your Own UX \(BYO UX\) sample is listed here.

For Embedded native authentication, start with the [quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication) and [application configuration guide](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-native-authentication-configure-app). For an existing integration, review [SDK compatibility and migration requirements](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#sdk-compatibility).

## Embedded native authentication

Use the following onboarding guidance for the Microsoft Authentication Library \(MSAL\) interfaces. Check the [SDK compatibility table](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#sdk-compatibility) for the documented package versions and supported continuation interfaces. For direct HTTP integration, use the [Native Authentication API reference](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication).

| Platform | SDK | Guidance |
| --- | --- | --- |
| **JavaScript and TypeScript** | [MSAL for JavaScript releases](https://github.com/AzureAD/microsoft-authentication-library-for-js/releases), `@azure/msal-browser` 5.29.1 or later. | [JavaScript samples](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples), [React Next.js quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-native-authentication), and [browser CORS requirements](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-cors#proxy-contract). |
| **Android** | [MSAL for Android](https://github.com/AzureAD/microsoft-authentication-library-for-android/), `com.microsoft.identity.client:msal` 8.7.0 or later. | [Android sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample) and [Android SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#android-migration). |
| **Apple** | [MSAL for iOS and macOS releases](https://github.com/AzureAD/microsoft-authentication-library-for-objc/releases), 2.18.1 or later. | [iOS sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-ios-sample) and [Apple SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#ios-migration). |

Existing V1 integrations can use the [V1 API reference and SDK library links](https://learn.microsoft.com/en-us/entra/identity-platform/reference-native-authentication-api-v1). The passkey samples are separate credential-management integrations, not passkey sign-in through the Native Authentication API.

CORS and proxy guidance applies to cross-origin browser API calls from SPAs with Embedded native authentication and BYO UX websites. Android and iOS apps using native HTTP transports don't need a CORS proxy.

## Samples and guides

Use the tabs to sort samples either by app type or your preferred language or platform.

These tables list examples, not overall feature support. A missing sample doesn't mean a feature is unsupported. Check the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability) for availability.

- [**By app type**](#tabpanel_1_apptype)
- [**By language/platform**](#tabpanel_1_language)

### Single-page application \(SPA\)

These samples and how-to guides demonstrate how to integrate a single-page application with Microsoft Entra External ID.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| JavaScript | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=javascript-external)  <br>• [List, register, and delete passkeys \(GitHub sample\)](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/tree/main/passkey-sample) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-javascript-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant)  <br>• [Sign in with passkeys](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey) |
| Angular | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=angular-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-apps-angular-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant) |
| React | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=react-external)  <br>• [List, register, and delete passkeys \(GitHub sample\)](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/tree/main/passkey-sample) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant)  <br>• [Sign in with passkeys](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey) |

### Web app

These samples and how-to guides demonstrate how to write a web application that integrates with Microsoft Entra External ID.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| JavaScript, Node.js \(Express\) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-external)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-node-sign-in-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-node-sign-in-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-web-app-node-sign-in-call-api-prepare-tenant) |
| ASP.NET Core | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant) |
| Python Django | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=python-django-external) | --- |
| Python Flask | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=python-flask-external) | --- |

### Web API

These samples and how-to guides demonstrate how to protect a web API with the Microsoft identity platform, and how to call a downstream API from the web API.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| ASP.NET Core | --- | • [Secure an ASP.NET web API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-core-build-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |

### Desktop

These samples and how-to guides demonstrate how to write a desktop application that integrates with Microsoft Entra External ID.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| JavaScript, Electron | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-js-external) | --- |
| ASP.NET \(MAUI\) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=wpfdotnet-maui-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-desktop-app-maui-sign-in-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |
| .NET \(MAUI\) WPF | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=wpfdotnet-wpf-external) | --- |

### Mobile: Microsoft-hosted authentication

These samples and how-to guides show you how to write a public client mobile application with browser-delegated authentication that integrates with Microsoft Entra External ID.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| ASP.NET Core MAUI | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=android-netmaui-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-mobile-app-maui-sign-in-prepare-tenant) |
| Android \(Kotlin\) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=android-external)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=android-external) | • [Sign in users, call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-mobile-app-android-kotlin-prepare-tenant) |
| iOS \(Swift\) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=ios-macos-external)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/sample-mobile-app-ios-swift-sign-in-call-api) | • [Sign in users, call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-mobile-app-ios-swift-prepare-tenant?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external) |

### Desktop: Embedded native authentication

For macOS, use the [MSAL iOS/macOS SDK reference](https://azuread.github.io/microsoft-authentication-library-for-objc/) and [Apple SDK compatibility and migration guidance](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#ios-migration).

### Mobile: Embedded native authentication

Use these samples with the [onboarding guidance](#embedded-native-authentication) for the response-driven integration.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Android \(Kotlin\) | • [Android sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample) | • [SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#android-migration) |
| iOS \(Swift\) | • [iOS sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-ios-sample) | • [SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#ios-migration) |

### Daemon

These samples and how-to guides demonstrate how to write a daemon application that integrates with Microsoft Entra External ID.

| Language/  <br>Platform | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Node.js | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-app-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-external) | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-daemon-node-call-api-build-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) |
| .NET | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-app-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-dotnet-daemon-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |

### .NET

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Daemon | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-app-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-dotnet-daemon-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |

### Android \(Kotlin\)

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Mobile: Microsoft-hosted authentication | • [Sign in users](https://learn.microsoft.com/en-us/entra/external-id/customers/sample-mobile-app-android-kotlin-sign-in)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/sample-mobile-app-android-kotlin-sign-in-call-api) | • [Sign in users, call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-mobile-app-android-kotlin-prepare-tenant) |
| Mobile: Embedded native authentication | • [Android sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-android-sample) | • [SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#android-migration) |

### ASP.NET Core

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Web API | --- | • [Secure an ASP.NET web API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-api-dotnet-core-build-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |
| Web app | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-dotnet-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant) |

### .NET \(MAUI\)

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Desktop | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=wpfdotnet-maui-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-desktop-app-maui-sign-in-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) |
| Mobile: Microsoft-hosted authentication | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=android-netmaui-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-mobile-app-maui-sign-in-prepare-tenant) |

### Python, Django

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Web app | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=python-django-external) | --- |

### Python, Flask

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Web app | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=python-flask-external) | --- |

### iOS/macOS \(Swift\)

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Mobile: Microsoft-hosted authentication | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=ios-macos-external)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/sample-mobile-app-ios-swift-sign-in-call-api) | • [Sign in users, call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-mobile-app-ios-swift-prepare-tenant?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external) |
| Mobile: Embedded native authentication | • [iOS sample](https://github.com/Azure-Samples/ms-identity-ciam-native-auth-ios-sample) | • [SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#ios-migration) |
| Desktop: Embedded native authentication | --- | • [MSAL iOS/macOS SDK reference](https://azuread.github.io/microsoft-authentication-library-for-objc/)  <br>• [SDK compatibility and migration](https://learn.microsoft.com/en-us/entra/identity-platform/how-to-migrate-native-authentication-v1-v2#ios-migration) |

### JavaScript

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Single-page application | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=javascript-external)  <br>• [List, register, and delete passkeys \(GitHub sample\)](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/tree/main/passkey-sample) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-javascript-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant)  <br>• [Sign in with passkeys](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey) |

### JavaScript, Angular

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Single-page application | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=angular-external) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-apps-angular-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant) |

### JavaScript, React

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Single-page application | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-single-page-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=react-external)  <br>• [List, register, and delete passkeys \(GitHub sample\)](https://github.com/Azure-Samples/ms-identity-ciam-native-javascript-samples/tree/main/passkey-sample) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&tabs=external-tenant)  <br>• [Sign in with passkeys](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey) |

### JavaScript, Node

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Daemon | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-app-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-external) | • [Call an API](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-daemon-node-call-api-build-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=asp-dot-net-core-external) |

### JavaScript, Node.js \(Express\)

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Web app | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-external)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-node-sign-in-call-api?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json) | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-web-app-node-sign-in-prepare-app?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json)  <br>• [Sign in users and call an API](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-web-app-node-sign-in-call-api-prepare-tenant) |

### JavaScript, Electron

| App type | Code sample guide | Build and integrate guide |
| --- | --- | --- |
| Desktop | • [Sign in users](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-desktop-app-sign-in?toc=/entra/external-id/toc.json&bc=/entra/external-id/breadcrumb/toc.json&pivots=external&tabs=node-js-external) | --- |
