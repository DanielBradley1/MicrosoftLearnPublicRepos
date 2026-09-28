<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/advanced/authorization-code-url-builder -->
<!-- Sitemap-Last-Modified: 2024-01-27 -->

# Authorization code URL builder

When performing Oauth2 authorization code flow, the first step is to direct the user to the authorization endpoint where they will authenticate and the identity provider will respond with an authentication code. The authentication code can then be used to redeem a token by calling MSALs [`PublicClientApplication.acquireToken(AuthorizationCodeParameters)`](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.abstractclientapplicationbase#com-microsoft-aad-msal4j-abstractclientapplicationbase-acquiretoken\(com-microsoft-aad-msal4j-authorizationcodeparameters\)) or [`ConfidentialClientApplication.acquireToken(AuthorizationCodeParameters)`](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.abstractclientapplicationbase#com-microsoft-aad-msal4j-abstractclientapplicationbase-acquiretoken\(com-microsoft-aad-msal4j-authorizationcodeparameters\)).

## Authorization URL builder

As of MSAL4J 1.4, there is now a helper method, [`getAuthorizationRequestUrl`](https://learn.microsoft.com/en-us/java/api/com.microsoft.aad.msal4j.abstractclientapplicationbase#com-microsoft-aad-msal4j-abstractclientapplicationbase-getauthorizationrequesturl\(com-microsoft-aad-msal4j-authorizationrequesturlparameters\)), that can be used to craft the authorization code URL, used in the first step of OAuth2 authorization code flow.

```java
PublicClientApplication publicClientApplication =
        PublicClientApplication
                .builder(CLIENT_ID)
                .authority(AUTHORITY)
                .build();

AuthorizationRequestUrlParameters parameters =
        AuthorizationRequestUrlParameters
                .builder(interactiveRequestParameters.redirectUri().toString(),
                        interactiveRequestParameters.scopes())
                .codeChallenge(verifier)
                .codeChallengeMethod("S256")
                .state(state);
                .build();

URL authorizationCodeUrl = publicClientApplication.getAuthorizationRequestUrl(parameters);
```
