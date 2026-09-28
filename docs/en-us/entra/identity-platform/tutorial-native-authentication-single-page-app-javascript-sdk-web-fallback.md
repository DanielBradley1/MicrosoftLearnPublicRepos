<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-javascript-sdk-web-fallback -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# Tutorial: Support web fallback in native authentication JavaScript SDK

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

This tutorial demonstrates how to acquire security tokens through a browser-based authentication where native authentication isn't sufficient to complete the authentication flow by using a mechanism called *web fallback*.

Web fallback allows a client app that uses native authentication to use browser-delegated authentication as a fallback mechanism to improve resilience. This scenario happens when native authentication isn't sufficient to complete the authentication flow. For example, if the authorization server requires capabilities that the client can't provide. Learn more about [web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback).

In this tutorial, you:

- Check `isRedirectRequired` error.
- Handle `isRedirectRequired` error.

## Prerequisites

- [React](#tabpanel_1_react)
- [Angular](#tabpanel_1_angular)

- Complete the steps in [Tutorial: Sign in users into a React single-page app by using native authentication JavaScript SDK](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-react-sdk-sign-in).

- Complete the steps in [Tutorial: Sign in users into Angular single-page app by using native authentication JavaScript SDK](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-native-authentication-single-page-app-angular-sign-in).

## Check and handle web fallback

One of the errors you can encounter when you use the JavaScript SDK's `signIn()` or `SignUp()` method is `result.error?.isRedirectRequired()`. The utility method `isRedirectRequired()` checks the need to fall back to browser-delegated authentication. Use the following code snippet to support web fallback:

```typescript
const result = await authClient.signIn({
         username,
     });

if (result.isFailed()) {
   if (result.error?.isRedirectRequired()) {
      // Fallback to the delegated authentication flow.
      const popUpRequest: PopupRequest = {
         authority: customAuthConfig.auth.authority,
         scopes: [],
         redirectUri: customAuthConfig.auth.redirectUri || "",
         prompt: "login", // Forces the user to enter their credentials on that request, negating single-sign on.
      };

      try {
         await authClient.loginPopup(popUpRequest);

         const accountResult = authClient.getCurrentAccount();

         if (accountResult.isFailed()) {
            setError(
                  accountResult.error?.errorData?.errorDescription ??
                     "An error occurred while getting the account from cache"
            );
         }

         if (accountResult.isCompleted()) {
            result.state = new SignInCompletedState();
            result.data = accountResult.data;
         }
      } catch (error) {
         if (error instanceof Error) {
            setError(error.message);
         } else {
            setError("An unexpected error occurred while logging in with popup");
         }
      }
   } else {
         setError(`An error occurred: ${result.error?.errorData?.errorDescription}`);
   }
}
```

When the app uses the fallback mechanism, the app acquires security tokens by using the `loginPopup()` method.

## Related content

- Learn more about [web fallback](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-web-fallback).
- Learn more about [Native authentication challenge types](https://learn.microsoft.com/en-us/entra/identity-platform/concept-native-authentication-challenge-types).
