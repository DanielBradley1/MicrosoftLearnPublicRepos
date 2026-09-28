<!-- Source: https://learn.microsoft.com/en-us/entra/msidweb/ -->
<!-- Sitemap-Last-Modified: 2026-08-07 -->

# Microsoft Identity Web documentation

Add authentication and authorization to your .NET applications and polyglot microservices with the Microsoft identity platform.

## Get started

### Overview

- [What is Microsoft.Identity.Web?](https://learn.microsoft.com/en-us/entra/msidweb/overview)
- [NuGet packages](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/packages)

### Quickstart

- [Sign in users in a web app](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapp)
- [Protect a web API](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/quickstart-webapi)
- [Call APIs from a daemon app](https://learn.microsoft.com/en-us/entra/msidweb/getting-started/daemon-app)

## Authentication and credentials

### Concept

- [Credentials overview](https://learn.microsoft.com/en-us/entra/msidweb/authentication/credentials-overview)
- [Certificateless authentication](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificateless)
- [Certificates](https://learn.microsoft.com/en-us/entra/msidweb/authentication/certificates)
- [Client secrets](https://learn.microsoft.com/en-us/entra/msidweb/authentication/client-secrets)
- [Token decryption](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-decryption)

### How-To Guide

- [Configure token caching](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-overview)
- [Troubleshoot token caches](https://learn.microsoft.com/en-us/entra/msidweb/authentication/token-cache-troubleshooting)
- [Set up authorization](https://learn.microsoft.com/en-us/entra/msidweb/authentication/authorization)

## Microsoft Entra ID Auth SDK \(sidecar\)

### Overview

- [What is the Entra ID Auth SDK \(sidecar\)?](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/overview)
- [Comparison with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/comparison)

### Get started

- [Installation and deployment](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/installation)
- [Configuration reference](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/configuration)
- [Security best practices](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/security)

### Tutorial

- [Validate authorization headers](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/validate-authorization-header)
- [Call downstream APIs](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/call-downstream-api)
- [Use managed identity](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/managed-identity)
- [Integrate from TypeScript](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-typescript)
- [Integrate from Python](https://learn.microsoft.com/en-us/entra/msidweb/agent-id-sdk/scenarios/using-from-python)

## Framework support

### How-To Guide

- [.NET Aspire](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspire)
- [ASP.NET Framework and .NET Standard](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/aspnet-framework)
- [MSAL.NET with Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/msal-dotnet-framework)
- [OWIN integration](https://learn.microsoft.com/en-us/entra/msidweb/frameworks/owin)

### Reference

- [Migrate to IDownstreamApi](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/migrate-to-downstreamapi)
- [Graph service client](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/graph-service-client)

## Call downstream APIs

### Concept

- [Choose an API calling approach](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/overview)
- [Token binding \(mTLS\)](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/token-binding)
- [Agent identities](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/agent-identities)

### How-To Guide

- [Call APIs from web apps](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apps)
- [Call APIs from web APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/from-web-apis)
- [Call Microsoft Graph](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/microsoft-graph)
- [Call Azure SDKs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/azure-sdks)
- [Call custom APIs](https://learn.microsoft.com/en-us/entra/msidweb/call-downstream-apis/custom-apis)
