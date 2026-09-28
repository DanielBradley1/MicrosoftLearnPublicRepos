<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-sign-in -->
<!-- Sitemap-Last-Modified: 2025-12-01 -->

# A web app that calls web APIs: Remove accounts from the token cache on global sign-out

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Sign-out is different for a web app that calls web APIs. When the user signs out from your application, or from any application, you must remove the tokens associated with that user from the token cache. Refer to [Sign in users in a sample web app](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-web-app-sign-in) for details on how to implement sign-in in a web app.

## Intercept the callback after single sign-out

To clear the token-cache entry associated with the account that signed out, your application can intercept the after `logout` event. Web apps store access tokens for each user in a token cache. By intercepting the after `logout` callback, your web application can remove the user from the cache.

- [ASP.NET Core](#tabpanel_1_aspnetcore)
- [ASP.NET](#tabpanel_1_aspnet)
- [Java](#tabpanel_1_java)
- [Node.js](#tabpanel_1_nodejs)
- [Python](#tabpanel_1_python)

Microsoft.Identity.Web takes care of implementing sign-out for you. For details see [Microsoft.Identity.Web source code](https://github.com/AzureAD/microsoft-identity-web/blob/c29f1a7950b940208440bebf0bcb524a7d6bee22/src/Microsoft.Identity.Web/WebAppExtensions/WebAppCallsWebApiAuthenticationBuilderExtensions.cs#L168-L176)

The ASP.NET sample doesn't remove accounts from the cache on global sign-out.

The Java sample doesn't remove accounts from the cache on global sign-out.

The Node sample doesn't remove accounts from the cache on global sign-out.

The Python sample doesn't remove accounts from the cache on global sign-out.

## Next steps

- [ASP.NET Core](#tabpanel_2_aspnetcore)
- [ASP.NET](#tabpanel_2_aspnet)
- [Java](#tabpanel_2_java)
- [Node.js](#tabpanel_2_nodejs)
- [Python](#tabpanel_2_python)

Move on to the next article in this scenario, [Acquire a token for the web app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=aspnetcore).

Move on to the next article in this scenario, [Acquire a token for the web app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=aspnet).

Move on to the next article in this scenario, [Acquire a token for the web app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=java).

Move on to the next article in this scenario, [Acquire a token for the web app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=nodejs).

Move on to the next article in this scenario, [Acquire a token for the web app](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-web-app-call-api-acquire-token?tabs=python).
