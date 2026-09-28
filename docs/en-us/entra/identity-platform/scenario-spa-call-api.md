<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-call-api -->
<!-- Sitemap-Last-Modified: 2025-05-13 -->

# Single-page application: Call a web API

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

We recommend that you call the `acquireTokenSilent` method to acquire or renew an access token before calling a web API. After you have a token, you can call a protected web API.

## Call a web API

- [JavaScript](#tabpanel_1_javascript)
- [Angular](#tabpanel_1_angular)

Use the acquired access token as a bearer in an HTTP request to call any web API, such as Microsoft Graph API. For example:

```javascript
    var headers = new Headers();
    var bearer = "Bearer " + access_token;
    headers.append("Authorization", bearer);
    var options = {
         method: "GET",
         headers: headers
    };
    var graphEndpoint = "https://graph.microsoft.com/v1.0/me";

    fetch(graphEndpoint, options)
        .then(function (response) {
             //do something with response
        })
```

The MSAL Angular wrapper takes advantage of the HTTP interceptor to automatically acquire access tokens silently and attach them to the HTTP requests to APIs. For more information, see [Acquire a token to call an API](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-spa-acquire-token).

## Next steps

- Learn more by building a React Single-page application \(SPA\) that signs in users in the following multi-part [tutorial series](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app).
- Explore Microsoft identity platform [single-page application code samples](https://learn.microsoft.com/en-us/entra/identity-platform/sample-v2-code#single-page-applications)
