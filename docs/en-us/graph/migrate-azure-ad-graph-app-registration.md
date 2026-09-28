<!-- Source: https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-app-registration -->
<!-- Sitemap-Last-Modified: 2025-02-21 -->

# Review app registration, permissions, and consent

> This article is part of *Step 3: review app details* in the [Azure AD Graph app migration planning checklist](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist) series.

Consider these three areas of your application's details:

- **App registration**: You can continue to use your existing app registration \(`appId`\) in your application code.

  You do **not** have to re-register your app to migrate to Microsoft Graph. Update the code, test heavily, and then deploy your update.
- **Permissions**: You should change your configured permissions to the equivalent Microsoft Graph permissions. Delegated permissions that were granted for Azure Active Directory \(Azure AD\) Graph are implicitly considered granted for Microsoft Graph also. Application permissions \(app roles\) need to be granted again. For a comparison, [review how Azure AD Graph permissions map to Microsoft Graph permissions](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-permissions-differences).

  If your update also includes the use of features or capabilities that aren't available in Azure AD Graph, you might need to request permissions for these new features. You can switch your app to use MSAL and the Microsoft identity platform endpoint, and request additional/incremental consent dynamically. Find more details about switching to MSAL in [review app authentication library changes](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-authentication-library).
- **Consent**: End-users who have granted consent for delegated permissions \(or for whom an admin granted consent\) can continue using your app without being asked to grant consent again.

  Users who have consented for your app to access their data can continue to use your app after it's been updated to use Microsoft Graph, without being asked to consent again. New users are prompted for consent.

  However, if you use new features, services, or add additional capabilities, you might need new permissions applicable to those features and end-user consent might be required. In such cases, consent is requested when tokens are refreshed.

## Next step

[Review the migration checklist again](https://learn.microsoft.com/en-us/graph/migrate-azure-ad-graph-planning-checklist)
