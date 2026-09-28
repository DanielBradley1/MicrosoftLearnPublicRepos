<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/reference-v2-libraries -->
<!-- Sitemap-Last-Modified: 2024-02-12 -->

# Microsoft identity platform authentication libraries

The following tables show Microsoft Authentication Library support for several application types. They include links to library source code, where to get the package for your app's project, and whether the library supports user sign-in \(authentication\), access to protected web APIs \(authorization\), or both.

The Microsoft identity platform has been certified by the OpenID Foundation as a [certified OpenID provider](https://openid.net/certification/). If you prefer to use a library other than the Microsoft Authentication Library \(MSAL\) or another Microsoft-supported library, choose one with a [certified OpenID Connect implementation](https://openid.net/developers/certified/).

If you choose to hand-code your own protocol-level implementation of [OAuth 2.0 or OpenID Connect 1.0](https://learn.microsoft.com/en-us/entra/identity-platform/v2-protocols), pay close attention to the security considerations in each standard's specification and follow secure software design and development practices like those in the [Microsoft SDL](https://www.microsoft.com/securityengineering/sdl/).

## Single-page application \(SPA\)

A single-page application runs entirely in the browser and fetches page data \(HTML, CSS, and JavaScript\) dynamically or at application load time. It can call web APIs to interact with back-end data sources.

Because a SPA's code runs entirely in the browser, it's considered a *public client* that's unable to store secrets securely.

| Language / framework | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs |
| --- | --- | --- | :---: | :---: | :---: |
| React | [MSAL React](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react)<sup>2</sup> | [msal-react](https://www.npmjs.com/package/@azure/msal-react) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |
| JavaScript | [MSAL.js](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)<sup>2</sup> | [msal-browser](https://www.npmjs.com/package/@azure/msal-browser) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |
| Angular | [MSAL Angular](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-angular)<sup>2</sup> | [msal-angular](https://www.npmjs.com/package/@azure/msal-angular) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) |

## Web application

A web application runs code on a server that generates and sends HTML, CSS, and JavaScript to a user's web browser to be rendered. The user's identity is maintained as a session between the user's browser \(the front end\) and the web server \(the back end\).

Because a web application's code runs on the web server, it's considered a *confidential client* that can store secrets securely.

| Language / framework | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs | Generally available \(GA\) *or*  <br>Public preview<sup>1</sup> |
| --- | --- | --- | --- | --- | --- | --- |
| .NET | [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) | — | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| .NET | [Microsoft.IdentityModel](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet) | [Microsoft.IdentityModel](https://www.nuget.org/packages?q=Microsoft.IdentityModel) | — | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png)<sup>2</sup> | ![Library cannot request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png)<sup>2</sup> | GA |
| ASP.NET Core | [Microsoft.Identity.Web](https://github.com/AzureAD/microsoft-identity-web) | [Microsoft.Identity.Web](https://www.nuget.org/packages/Microsoft.Identity.Web) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-dotnet-core-sign-in) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Java | [MSAL4J](https://github.com/AzureAD/microsoft-authentication-library-for-java) | [msal4j](https://central.sonatype.com/artifact/com.microsoft.azure/msal4j) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-java-sign-in) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Spring | [spring-cloud-azure-starter-active-directory](https://github.com/Azure/azure-sdk-for-java/tree/spring-cloud-azure-autoconfigure_4.3.0/sdk/spring/spring-cloud-azure-starter-active-directory) | [spring-cloud-azure-starter-active-directory](https://central.sonatype.com/artifact/com.azure.spring/spring-cloud-azure-starter-active-directory) | [Tutorial](https://learn.microsoft.com/en-us/azure/developer/java/spring-framework/configure-spring-boot-starter-java-app-with-azure-active-directory) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Node.js | [MSAL Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node) | [msal-node](https://www.npmjs.com/package/@azure/msal-node) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-nodejs-sign-in) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Python | [MSAL Python](https://github.com/AzureAD/microsoft-authentication-library-for-python) | [msal](https://pypi.org/project/msal) | — | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Python | [identity](https://github.com/rayluo/identity) | [identity](https://pypi.org/project/identity/) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-python-flask) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | -- |

<sup>\(1\)</sup> [Universal License Terms for Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) apply to libraries in *Public preview*.

<sup>\(2\)</sup> The [Microsoft.IdentityModel](https://github.com/AzureAD/azure-activedirectory-identitymodel-extensions-for-dotnet) library only *validates* tokens - it can't request ID or access tokens.

## Desktop application

A desktop application is typically binary \(compiled\) code that displays a user interface and is intended to run on a user's desktop.

Because a desktop application runs on the user's desktop, it's considered a *public client* that's unable to store secrets securely.

| Language / framework | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs | Generally available \(GA\) *or*  <br>Public preview<sup>1</sup> |
| --- | --- | --- | :---: | :---: | :---: | :---: |
| Electron | [MSAL Node.js](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node) | [msal-node](https://www.npmjs.com/package/@azure/msal-node) | — | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | Public preview |
| Java | [MSAL4J](https://github.com/AzureAD/microsoft-authentication-library-for-java) | [msal4j](https://mvnrepository.com/artifact/com.microsoft.azure/msal4j) | — | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| macOS \(Swift/Obj-C\) | [MSAL for iOS and macOS](https://github.com/AzureAD/microsoft-authentication-library-for-objc) | [MSAL](https://cocoapods.org/pods/MSAL) | [Tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-ios) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| UWP | [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) | [Tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-windows-uwp) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| WPF | [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client) | [Tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-windows-desktop) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |

<sup>1</sup> [Universal License Terms for Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) apply to libraries in *Public preview*.

## Mobile application

A mobile application is typically binary \(compiled\) code that displays a user interface and is intended to run on a user's mobile device.

Because a mobile application runs on the user's mobile device, it's considered a *public client* that's unable to store secrets securely.

| Platform | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs | Generally available \(GA\) *or*  <br>Public preview<sup>1</sup> |
| --- | --- | --- | :---: | :---: | :---: | :---: |
| Android \(Java\) | [MSAL Android](https://github.com/AzureAD/microsoft-authentication-library-for-android) | [MSAL](https://mvnrepository.com/artifact/com.microsoft.identity.client/msal) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-mobile-app-android-sign-in) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Android \(Kotlin\) | [MSAL Android](https://github.com/AzureAD/microsoft-authentication-library-for-android) | [MSAL](https://mvnrepository.com/artifact/com.microsoft.identity.client/msal) | — | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| iOS \(Swift/Obj-C\) | [MSAL for iOS and macOS](https://github.com/AzureAD/microsoft-authentication-library-for-objc) | [MSAL](https://cocoapods.org/pods/MSAL) | [Tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-v2-ios) | ![Library can request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |

<sup>1</sup> [Universal License Terms for Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) apply to libraries in *Public preview*.

## Service / daemon

Services and daemons are commonly used for server-to-server and other unattended \(sometimes called *headless*\) communication. Because there's no user at the keyboard to enter credentials or consent to resource access, these applications authenticate as themselves, not a user, when requesting authorized access to a web API's resources.

A service or daemon that runs on a server is considered a *confidential client* that can store its secrets securely.

| Language / framework | Project on  <br>GitHub | Package | Getting  <br>started | Sign in users | Access web APIs | Generally available \(GA\) *or*  <br>Public preview<sup>1</sup> |
| --- | --- | --- | :---: | :---: | :---: | :---: |
| .NET | [MSAL.NET](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet) | [Microsoft.Identity.Client](https://www.nuget.org/packages/Microsoft.Identity.Client/) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-dotnet-acquire-token) | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Java | [MSAL4J](https://github.com/AzureAD/microsoft-authentication-library-for-java) | [msal4j](https://javadoc.io/doc/com.microsoft.azure/msal4j/latest/index.html) | — | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Node | [MSAL Node](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-node) | [msal-node](https://www.npmjs.com/package/@azure/msal-node) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-console-app-nodejs-acquire-token) | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |
| Python | [MSAL Python](https://github.com/AzureAD/microsoft-authentication-library-for-python) | [msal-python](https://github.com/AzureAD/microsoft-authentication-library-for-python) | [Quickstart](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-daemon-app-python-acquire-token) | ![Library cannot request ID tokens for user sign-in.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/no.png) | ![Library can request access tokens for protected web APIs.](https://learn.microsoft.com/en-us/entra/identity-platform/media/common/yes.png) | GA |

<sup>1</sup> [Universal License Terms for Online Services](https://www.microsoft.com/licensing/terms/product/ForOnlineServices/all) apply to libraries in *Public preview*.

## Next steps

For more information about the Microsoft Authentication Library, see the [Overview of the Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-overview).
