<!-- Source: https://learn.microsoft.com/en-us/graph/tutorials/powershell-app-only-users -->
<!-- Sitemap-Last-Modified: 2025-06-11 -->

# Get users in PowerShell scripts with Microsoft Graph and app-only authentication

In this article, you extend the application you created in [Build PowerShell scripts with Microsoft Graph and app-only authentication](https://learn.microsoft.com/en-us/graph/tutorials/powershell-app-only) with Microsoft Graph user APIs. You use Microsoft Graph to get a list of users in your organization.

1. Run the following command in your authenticated PowerShell session to list users.

   ```powershell
   Get-MgUser -Select "displayName,id,mail" -Top 25 -OrderBy "displayName"
   ```

2. Review the output.

   ```powershell
   Id                                   DisplayName              Mail                  UserPrincipalName UserType
   --                                   -----------              ----                  ----------------- --------
   05fb57bf-2653-4396-846d-2f210a91d9cf Adele Vance              AdeleV@contoso.com
   a36fe267-a437-4d24-b39e-7344774d606c Alex Wilber              AlexW@contoso.com
   54cebbaa-2c56-47ec-b878-c8ff309746b0 Allan Deyoung            AllanD@contoso.com
   9cb2ad7c-8e69-46a6-a947-a02c255048de Automate Bot
   9a7dcbd0-72f0-48a9-a9fa-03cd46641d49 Bianca Pisani
   a8989e40-be57-4c2e-bf0b-7cdc471e9cc4 Brian Johnson (TAILSPIN) BrianJ@contoso.com
   9e2d4937-44ee-4af4-bd56-77a12cc3ecc4 Cameron White
   8990227d-31dc-4120-a38e-f652576974f4 Christie Cline           ChristieC@contoso.com
   ...
   ```

## Code explained

Consider the command used to list users.

- It uses `-Select` to request specific properties
- It uses `-Top` to limit the number of users returned
- It uses `-OrderBy` to sort the response

## Next step

[Add additional Microsoft Graph APIs](https://learn.microsoft.com/en-us/graph/tutorials/powershell-app-only-extend-app)
