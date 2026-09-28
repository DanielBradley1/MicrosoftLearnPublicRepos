<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-authentication-library -->
<!-- Sitemap-Last-Modified: 2025-02-21 -->

# Review app authentication library changes

> This article is part of *Step 3: review app details* in the [Azure AD Graph app migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) series.

Most apps use an authentication library to acquire and manage access tokens to call Microsoft Graph. Microsoft offers two authentication libraries:

- [Microsoft Authentication Library](https://learn.microsoft.com/en-us/azure/active-directory/develop/reference-v2-libraries) \(MSAL\) - **Recommended**
- [Azure Active Directory Authentication Library](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-libraries) \(ADAL\) - **Retired**

## Updating ADAL

If your app still uses ADAL, use a two-stage migration approach:

1. Update your app to acquire access tokens for Microsoft Graph. Continue to use ADAL for this step. Update the **resourceURL**, which holds the URI representing the resource web API, from `https://graph.windows.net` to `https://graph.microsoft.com`.

   Newly acquired tokens have the same scopes after this change, but the audience of the access tokens is now Microsoft Graph.

   Once you update **resourceURL** and verified functionality, release an interim update for your app users.
2. Next, begin migrating your app to use MSAL, which is the only supported library, now that ADAL is retired.

## Migrating to MSAL

MSAL provides multiple benefits over ADAL, including incremental consent, richer single sign-on experiences, support for personal Microsoft accounts, and use of standards-based protocols.

When you switch your app over to MSAL, you need to make a few changes, including setting the **scopes** parameter in the token acquisition request:

```csharp
var scopes = new string[] { "https://graph.microsoft.com/.default" };
```

This expression restricts the permission scopes to those configured on the app registration in the Microsoft Entra admin center, preventing existing users from needing to re-consent to your app.

Learn [.NET client library](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-client-libraries) differences between Azure Active Directory \(Azure AD\) Graph and Microsoft Graph.

See [Migrate applications to the Microsoft Authentication Library \(MSAL\)](https://learn.microsoft.com/en-us/entra/identity-platform/msal-migration) for direct and extensive help with the process, including troubleshooting and help with common errors.

Once you migrate to MSAL, you can request more scopes dynamically, and users are prompted to provide incremental consent the next time they use your app.

## Next step

[Review the migration checklist again](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist)
