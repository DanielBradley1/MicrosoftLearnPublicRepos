<!-- Source: https://learn.microsoft.com/en-us/entra/msal/android/calling-an-api -->
<!-- Sitemap-Last-Modified: 2024-03-19 -->

# Calling an API

## Introduction

Most of you will be using MSAL to get an access token in order to call an API. You may be calling a Microsoft API, like Microsoft Graph or be calling an API that you and/or your organization published and are protecting with Microsoft Entra ID.

In either case there are some basic things that you'll need to know in order to make your request. The most important of which are the names of the scopes that your client application needs in order to enable corresponding features in your application.

## Scopes

Scope is the term used in the OAuth protocol, but the term permission is often used interchangeably within the Microsoft documentation. Scope refers to the scope of the authorization \(permission\) being requested by and/or granted to an application.

For Microsoft Graph the list of scopes \(permissions\) associated with it are published here: [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)

If you need to request a scope for an API that your organization published you can refer to the documentation provided by the API developer or can view the application registration associated with the API in either [apps.dev.microsoft.com](https://apps.dev.microsoft.com) or in the [Azure Portal](https://portal.azure.com).

### Unique Scopes

Microsoft Entra ID as an OAuth authorization server is used to protect multiple APIs \(resource servers\). In order to avoid name collisions within scope names and to clarify for which API a scope is being requested. Scopes are generally prefixed with either the application id \(GUID\) associated with the resource server or by one or more identifier URIs within the application registration for that API server.

Microsoft Graph is special in that if a scope value is not prefixed within an identifier URI it is assumed to belong to Microsoft Graph.
