<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/clearing-token-cache -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Clearing the token cache

Clearing the token cache is achieved by removing the accounts from the cache. This does not remove the session cookie which is in the browser.

The example below is using an instance of [IClientApplicationBase](https://learn.microsoft.com/en-us/dotnet/api/microsoft.identity.client.iclientapplicationbase).

```csharp
// Clear the cache
var accounts = await app.GetAccountsAsync();
while (accounts.Any())
{
   await app.RemoveAsync(accounts.First());
   accounts = await app.GetAccountsAsync();
}
```
