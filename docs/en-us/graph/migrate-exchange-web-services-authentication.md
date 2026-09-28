<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-exchange-web-services-authentication -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Authentication differences between Exchange Web Services \(EWS\) and Microsoft Graph

Exchange Web Services \(EWS\) and Microsoft Graph both use [Microsoft identity platform OAuth 2.0](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols) for authentication and authorization.

Note

EWS currently also supports basic authentication. [Basic authentication is deprecated](https://learn.microsoft.com/en-us/lifecycle/announcements/exchange-online-basic-auth-deprecated) and is being deactivated across Microsoft 365 organizations. Microsoft Graph does not support basic authentication, so apps that have not yet migrated to OAuth 2.0 must do so to access Microsoft Graph.

## Permissions

EWS and Microsoft Graph offer two types of permissions: delegated and application. Delegated permissions are in the context of an authenticated user. Application permissions are granted to an application that doesn't act on a user's behalf.

With EWS, an application has access to everything that the user has access to \(with delegated permissions\) or everything that EWS can access \(with application permissions\).

EWS has all or nothing access model and there is no granular scoping for limiting data access in a mailbox. Whereas, Microsoft Graph offers granular permissions to specific features within an Exchange Online mailbox. For example, it is possible to allow an application to only read mail messages, and have no access to calendars or contacts. The effective permissions for delegated authentication is the intersection of the user's privileges and the permissions that have been consented for the application. For application authentication, the effective permissions are the set of permissions consented to by an administrator.

For a full list of Exchange-related Microsoft Graph permissions, see:

- Mail permissions
- Calendar permissions
- Personal contacts permissions
- Tasks permissions

## Impersonation

[EWS impersonation](https://learn.microsoft.com/en-us/exchange/client-developer/exchange-web-services/impersonation-and-ews-in-exchange) provides a mechanism for EWS applications that run as a service account to act as a user. This allows the app to take actions, such as sending an email, that appear to come from the impersonated user.

With Microsoft Graph, there are no service accounts. Instead, permissions are granted to applications directly. The application authenticates using [client credentials flow](https://learn.microsoft.com/en-us/graph/auth-v2-service) with its own identity. By default, admin consent grants access to all users' mailboxes, but apps can be [limited to specific mailboxes](https://learn.microsoft.com/en-us/graph/auth-limit-mailbox-access) by an administrator. The way to achieve Impersonation in Microsoft Graph is by making use of app-access policy and application permissions.
