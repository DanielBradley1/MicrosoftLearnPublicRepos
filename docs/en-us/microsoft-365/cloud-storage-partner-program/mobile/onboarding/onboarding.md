<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/mobile/onboarding/onboarding -->
<!-- Sitemap-Last-Modified: 2025-12-23 -->

# Onboarding information

Use the [CSPP Partner WOPI Environment Values form](https://aka.ms/cspp/nativeintegration) to provide Microsoft with the information necessary to enable end-to-end testing and release of Microsoft 365 for Mobile integration.

| Property | Data Type | Sample Value | Description |
| --- | --- | --- | --- |
| Localized Provider Name | String | Contoso | The name to display for this storage. provider |
| Icon Locations | String\[\] | `https://contoso.com/images/logo16.png`  <br>`https://contoso.com/images/logo32.png`  <br>`https://contoso.com/images/logo48.png`  <br>`https://contoso.com/images/logo64.png`  <br>`https://contoso.com/images/logo80.png`  <br>`https://contoso.com/images/logo96.png` | The path to the provider hosted icons, one for each of the following dimensions:  <br>  <br>● 16x16  <br>● 32x32  <br>● 48x48  <br>● 64x64  <br>● 80x80  <br>● 96x96  <br>  <br>Requirements:  <br>  <br>● must be PNG  <br>● icons must have at least a 1px white border to avoid bleed. |
| BootstrapperUri | String | `https://contoso.com/wopibootstrapper` | The full path to the Bootstrapper endpoint. Must end in wopibootstrapper. |
| English Description | String | Free online storage. Store, access, and share thousands of documents. | Used to show more information about the service.  <br>  <br>Specify which part of the string shouldn't be localized. For example, your product or brand name if you include it in your description. |
| Client ID | String | s6BhdRkqt3 | OAuth2 Client ID \(for Office\). |
| Client Secret | String | 7FjfpZBr1K3tDRbnfVdmIw98 | OAuth2 Client Secret \(for Office\).  <br>  <br>Don't provide this in email. This must be transferred securely. |
| Client App Name | String | Office | Please set this as the app name. |
| RedirectUri | String | `https://localhost` | The redirect URI that returns an authorization code. This URI is a known stop-URL and isn't loaded by Microsoft 365 for mobile. |
| ProviderId | String | TP\_CONTOSO | Supplied by Microsoft. |
| TrustedDomain | String | `contoso.com`, `qa-contos.com` | Known domains for bootstrapper, authorization, and token issuance endpoints. |
| Scope \(optional\) | String | userprofile, editdocs | Set of comma-delimited scopes that are requested during authentication with the storage provider. |
| SupportRefresh | Bool | True | Denotes whether you'll issue a refresh token that can get a new access token. |
| SiteUrl | String | `http://www.contoso.com` | Fully qualified address to your website. |

## Additional information required

- Three test accounts on each environment you want to onboard.

  - If your service has a commercial versus consumer offering, provide three of each.

- Website interface of each environment, if one exists.
- Whether each environment can be reached outside your network \(if it's Internet accessible so we can use it\).
- How many apps you have on each platform. \(For example, on iOS, do you have a *for enterprise app* versus a *for consumer app*, or do you just have one?\)
- If you've already integrated with Office for the web, provide directions to access the Validator.

## Security Questions

- What's the expiry for access and refresh token for each environment?
- Do you actually check the redirect URI sent during OAuth2 flow against the one registered above, such that the authorization code would only ever be sent to the redirect URI?
