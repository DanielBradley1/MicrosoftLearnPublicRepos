<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/ -->
<!-- Sitemap-Last-Modified: 2025-03-27 -->

# Microsoft Authentication Library for Java

The Microsoft Authentication Library for Java \(MSAL Java or MSAL4J\) integrates applications with the [Microsoft identity platform](https://learn.microsoft.com/en-us/entra/identity-platform/v2-overview). It allows you to sign in users or apps with Microsoft identities \(Microsoft Entra ID, Microsoft accounts, and Azure AD B2C accounts\) and get tokens to call Microsoft APIs like [Microsoft Graph](https://graph.microsoft.io/) or your own APIs. MSAL Java uses industry standard OAuth2 and OpenID Connect protocols.

## Overview

1. [Why use MSAL4J?](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/why-use-msal4j)
2. **Prerequisite**: Before using MSAL4J you will have to [register your applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).
3. To start using MSAL4J, instantiate and configure the [client application](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/client-applications).
4. Learn about the ways to [acquire a token](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/acquiring-tokens) using MSAL4J.
5. Follow [best practices for a robust enterprise ready application](https://learn.microsoft.com/en-us/entra/msal/java/advanced/best-practices-enterprise).
6. Refer [FAQ](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/faq) for common issues and known bugs.

## MSAL Java scenarios

MSAL4J can be used by applications to acquire tokens to access protected APIs. Tokens can be acquired by different **application types**: desktop applications, web applications, web APIs, and applications running on devices that don't have a browser \(such as IoT devices\). In MSAL4J, applications are categorized as follows:

- **Public client applications \(desktop and mobile\)**. These types of apps cannot store app secrets securely.
- **Confidential client applications \(web apps, web APIs, and daemon applications\)**. These type of apps securely store a secret registered with Microsoft Entra ID.

Learn more details about instantiating and configuring the above in the [Client applications](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/client-applications) topic.

MSAL4J supports acquiring tokens either in the name of a user or in the name of the application itself \(without a user\). In the latter case, a confidential client application must be used.

MSAL4J can be used in applications running on different operating systems \(Windows, Linux, macOS\).

Key scenarios supported by MSAL4J:

- [Web application that signs in users](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-sign-user-overview)
- [Web Application signing in a user and calling a Web API in the name of the user](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-overview)
- [Desktop application calling a Web API in the name of the signed-in user](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-overview)
- [Desktop/service daemon application calling Web API without a user](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-daemon-overview)
- [Application without a browser, or IOT application calling an API in the name of the user](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token?tabs=java#command-line-tool-without-web-browser)

Can't find the scenario you are looking for? Check out the [supported scenarios and platforms](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-flows-app-scenarios#scenarios-and-supported-platforms-and-languages) across MSAL libraries.

## Releases

Refer to [MSAL Java releases on GitHub](https://github.com/AzureAD/microsoft-authentication-library-for-java/releases).
