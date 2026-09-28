<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspnet-framework -->
<!-- Sitemap-Last-Modified: 2026-04-29 -->

# Integrate Microsoft.Identity.Web with ASP.NET Framework and .NET Standard

Microsoft.Identity.Web extends Microsoft Entra ID authentication to .NET Framework and .NET Standard applications. This article helps you choose the right package and integration pattern for your scenario.

## Choose your scenario

Select the integration pattern that matches your application type. Microsoft Entra offers different packages for web apps and background services.

### MSAL.NET with Microsoft.Identity.Web packages

**For console apps, daemon services, and non-web .NET Framework applications**

Use Microsoft.Identity.Web.TokenCache and Microsoft.Identity.Web.Certificate packages with MSAL.NET for:

- Token cache serialization \(SQL Server, Redis, Cosmos DB, PostgreSQL\)
- Certificate loading from KeyVault, certificate store, or file system
- Console applications and daemon services
- .NET Standard 2.0 libraries

**[MSAL.NET with Microsoft.Identity.Web Guide](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework)**

---

### OWIN integration for ASP.NET MVC/Web API

**For ASP.NET MVC and Web API applications**

Use Microsoft.Identity.Web.OWIN package for full-featured web authentication with:

- TokenAcquirerFactory for automatic token acquisition
- Controller extensions for easy access to Microsoft Graph and downstream APIs
- Distributed token cache support
- Incremental consent handling

**[OWIN Integration Guide](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin)**

---

## Compare integration options

The following table summarizes the key differences between the two integration approaches.

| Feature | MSAL.NET + TokenCache/Certificate | OWIN Integration |
| --- | --- | --- |
| **Package** | Microsoft.Identity.Web.TokenCache  <br>Microsoft.Identity.Web.Certificate | Microsoft.Identity.Web.OWIN |
| **Target** | Console apps, daemons, worker services | ASP.NET MVC, ASP.NET Web API |
| **Authentication** | Manual MSAL.NET configuration | Automatic OWIN middleware |
| **Token Acquisition** | Manual with `IConfidentialClientApplication` | Automatic with controller extensions |
| **Token Cache** | All providers \(SQL, Redis, Cosmos, PostgreSQL\) | All providers \(SQL, Redis, Cosmos, PostgreSQL\) |
| **Certificate Loading** | KeyVault, store, file, Base64 | Via MSAL.NET configuration |
| **Microsoft Graph** | Manual `GraphServiceClient` setup | `this.GetGraphServiceClient()` |
| **Downstream APIs** | Manual HTTP calls with tokens | `this.GetDownstreamApi()` |
| **Incremental Consent** | Manual challenge handling | Automatic with `MsalUiRequiredException` |

---

## Review available packages

Starting with **Microsoft.Identity.Web 1.17+**, you can use Microsoft Identity libraries in non-ASP.NET Core environments. The following packages target .NET Framework and .NET Standard workloads.

### Available packages

| Package | Purpose | Target Applications |
| --- | --- | --- |
| **Microsoft.Identity.Web.TokenCache** | Token cache serializers for MSAL.NET | Console, daemon, worker services |
| **Microsoft.Identity.Web.Certificate** | Certificate loading utilities | Console, daemon, worker services |
| **Microsoft.Identity.Web.OWIN** | OWIN middleware integration | ASP.NET MVC, ASP.NET Web API |

### Understand package benefits

These packages simplify common authentication tasks without requiring ASP.NET Core.

| Feature | Benefit |
| --- | --- |
| **Token Cache Serialization** | Reusable cache adapters for in-memory, SQL Server, Redis, Cosmos DB, PostgreSQL |
| **Certificate Helpers** | Simplified certificate loading from KeyVault, file system, or cert stores |
| **OWIN Integration** | Seamless authentication for ASP.NET MVC/Web API |
| **.NET Standard 2.0** | Compatible with .NET Framework 4.7.2+, .NET Core, and .NET 5+ |
| **Minimal Dependencies** | Targeted packages without ASP.NET Core dependencies |

## Explore sample applications

Use these samples as starting points for your own implementation.

### MSAL.NET samples

- [ConfidentialClientTokenCache](https://github.com/Azure-Samples/active-directory-dotnet-v1-to-v2/tree/master/ConfidentialClientTokenCache) - Console app with token cache
- [active-directory-dotnetcore-daemon-v2](https://github.com/Azure-Samples/active-directory-dotnetcore-daemon-v2) - Daemon with certificate from KeyVault

### OWIN samples

- [ms-identity-aspnet-webapp-openidconnect](https://github.com/Azure-Samples/ms-identity-aspnet-webapp-openidconnect) - ASP.NET MVC with Microsoft.Identity.Web.OWIN

## Related content

- [MSAL.NET with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework)
- [OWIN integration](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin)
- [Daemon applications](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app)
- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
