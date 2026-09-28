<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/getting-started/why-use-msal4j -->
<!-- Sitemap-Last-Modified: 2024-02-29 -->

# Why use MSAL4J

The Microsoft Authentication Library for Java \(MSAL for Java or MSAL4J\) enables developers to **acquire [tokens](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary#security-token) in order to call secured web APIs**. These web APIs include Microsoft Graph, other Microsoft APIS, third party web APIs, or your own web API.

## Multiple application architectures

MSAL for Java supports all the possible application topologies including:

- [Native client](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary#native-client) \(desktop applications\) calling an API, such as Microsoft Graph, in the name of the user.
- Daemons/services or [web clients](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary#web-client) \(web apps/ web APIs\) calling other APIs, such as Microsoft Graph in the name of a user or without a user.

MSAL4J does not support [user-agent based clients](https://learn.microsoft.com/en-us/entra/identity-platform/developer-glossary#user-agent-based-client), which are only supported in JavaScript.

For details about the supported scenarios see [the introductory section](https://learn.microsoft.com/en-us/entra/msal/java/#msal-java-scenarios).

## Value of MSAL4J over generic libraries

MSAL4J is a token acquisition library. Depending on your scenario it provides you with various way of getting a token, with a consistent API for a number of platforms.

It also adds value by:

- Maintaining a **token cache** and **automatically refreshing tokens** for you when they are close to expiration.
- Helping you specify which **audience** you want your application to sign-in \(your org, several orgs, work and school and Microsoft personal accounts, social identities with Azure AD B2C, users in sovereign and national clouds\).
- **Helping you troubleshoot** your app by exposing actionable exceptions, logging, and telemetry.

## Token acquisition

MSAL4J is used to acquire tokens. It's not used to protect a Web API. If you are interested in protecting a Web API with Microsoft Entra ID, check out the following resources:

- [Spring Starter for Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/developer/java/spring-framework/spring-boot-starter-for-azure-active-directory-developer-guide?tabs=SpringCloudAzure4x)
- [Validating tokens manually](https://learn.microsoft.com/en-us/entra/identity-platform/access-tokens#validating-tokens)
