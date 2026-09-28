<!-- Source: https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/reference-managed-identity-libraries -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# Client libraries for managed identities authentication

This document provides an overview of the client libraries available for authenticating your applications using managed identities for Azure resources. These libraries include the Azure Identity libraries and Microsoft Authentication Libraries \(MSAL\).

Some Azure services built client libraries on top of these libraries. For example, the `Microsoft.Data.SqlClient` package can be used to authenticate to an Azure SQL database using managed identities. Behind the scenes, the Azure Identity library for .NET is being used.

## Choosing the right library

MSAL libraries offer lower-level abstractions than libraries like Azure Identity. Both MSAL and Azure Identity libraries allow you to acquire tokens via managed identity. Internally, Azure Identity libraries use MSAL and provide higher-level APIs such as `DefaultAzureCredential` that remove the need to implement manual switches between identity types when developing and deploying your application.

- If your application already uses one of the libraries, continue using the same library.
- If you're developing a new application and plan to call other Azure resources, use an Azure Identity library. This library provides an improved developer experience by allowing the app to authenticate on local developer machines where managed identities are not available.
- If you need to call other downstream web APIs like Microsoft Graph or your own web API, use MSAL. For .NET applications, use the *Microsoft.Identity.Web* library, which is built on top of MSAL.

In cases where an Azure service built a client library on top of these libraries, consider using the service-specific client library. For example, for Azure SQL, use the [`Microsoft.Data.SqlClient`](https://learn.microsoft.com/en-us/sql/connect/ado-net/sql/azure-active-directory-authentication#using-managed-identity-authentication) package.

## Language-specific API references

| Language | Azure Identity | MSAL |
| --- | --- | --- |
| .NET | [Azure Identity client library for .NET](https://learn.microsoft.com/en-us/dotnet/api/overview/azure/identity-readme#managed-identity-support) | [MSAL .NET](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.managedidentityapplication) |
| C++ | [Azure Identity client library for C++](https://azure.github.io/azure-sdk-for-cpp/identity.html) |  |
| Java | [Azure Identity client library for Java](https://learn.microsoft.com/en-us/java/api/overview/azure/identity-readme#managed-identity-support) | [MSAL Java](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.managedidentityapplication) |
| JavaScript | [Azure Identity client library for JavaScript](https://learn.microsoft.com/en-us/javascript/api/overview/azure/identity-readme#managed-identity-support) | [MSAL JavaScript](https://github.com/AzureAD/microsoft-authentication-library-for-js/blob/dev/lib/msal-node/docs/managed-identity.md) |
| Python | [Azure Identity client library for Python](https://learn.microsoft.com/en-us/python/api/overview/azure/identity-readme#managed-identity-support) | [MSAL Python](https://learn.microsoft.com/en-us/python/api/msal/msal.managed_identity) |
| Go | [Azure Identity client library for Go](https://pkg.go.dev/github.com/Azure/azure-sdk-for-go/sdk/azidentity) | [MSAL Go](https://pkg.go.dev/github.com/AzureAD/microsoft-authentication-library-for-go) |
