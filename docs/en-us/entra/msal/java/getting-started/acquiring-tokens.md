<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/getting-started/acquiring-tokens -->
<!-- Sitemap-Last-Modified: 2025-10-14 -->

# Acquiring tokens

As explained in [MSAL for Java scenarios](https://learn.microsoft.com/en-us/entra/msal/java/#msal-java-scenarios), there are many ways of acquiring a token. Some require user interactions through a web browser. Some don't require any user interactions.

In general the way to acquire a token is different depending on the application type - public client application \(desktop/mobile\) or a confidential client application \(Web App, Web API, daemon application like a Windows service\).

## Pre-requisites

Before acquiring tokens with MSAL4J, make sure to instantiate a [client application](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/client-applications)

## Token acquisition methods

Follow the topics below for detailed explanation with MSAL4J code usage for each token acquisition method.

### Public client applications

- Acquire tokens [interactively with system browser](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/acquiring-tokens-interactively)
- Acquire tokens by [authorization code](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/acquiring-tokens-with-authorization-codes) after letting the user sign-in through the authorization request URL.
- It's also possible to get a token with a [username and password](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token?tabs=java#username--password).\(This flow has been deprecated\)
- For applications running on Windows machines and joined to a domain or to Microsoft Entra ID, it is possible to acquire a token silently, leveraging [Integrated Windows Authentication \(IWA\)](https://learn.microsoft.com/en-us/entra/msal/java/advanced/integrated-windows-authentication).
- Finally, for applications running on devices which don't have a web browser, it's possible to acquire a token through the [device code flow](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/device-code-flow), which provides the user with a URL and a code. The user goes to a web browser on another device, enters the code and signs-in, and then Microsoft Entra ID returns back a token to the browser-less device.

### Confidential client applications

- Acquire token **as the application itself** using [client credentials](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/client-credentials), and not for a user. For example, in apps which process users in batches and not a particular user such as in syncing tools.
- In the case of Web Apps or Web APIs **calling another downstream Web API in the name of the user**, use the [On Behalf Of flow](https://learn.microsoft.com/en-us/entra/msal/java/advanced/service-to-service-calls) to acquire a token based on some User assertion \(SAML for instance, or a JWT token\).
- **For Web apps in the name of a user**, acquire tokens by [authorization code](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=java) after letting the user sign-in through the authorization request URL. This is typically the mechanism used by an application which lets the user sign-in using OpenID Connect, but then wants to access Web APIs for this particular user.

## MSAL4J caches tokens

For both Public client and Confidential client applications, MSAL maintains a token cache, and applications should try to get a token from the cache first before any other means \(except in the case of [client credentials](https://learn.microsoft.com/en-us/entra/msal/java/getting-started/client-credentials), which looks at the cache by itself\). Take a look at the [recommended pattern](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-desktop-acquire-token?tabs=java) for token acquisition.

To be able to make use of the cache, the application needs to customize the [token cache serialization](https://learn.microsoft.com/en-us/entra/msal/java/advanced/msal-java-token-cache-serialization).
