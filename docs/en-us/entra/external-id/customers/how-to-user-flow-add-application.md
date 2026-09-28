<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application -->
<!-- Sitemap-Last-Modified: 2025-06-06 -->

# Add your application to the user flow

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

A user flow defines the authentication methods a customer can use to sign in to your application and the information they need to provide during sign-up. After you [create a user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers), you can associate it with one or more of the applications registered in your external tenant.

Because you might want the same sign-in experience for all of your apps, you can add multiple apps to the same user flow. But only one sign-in experience is needed for an application, so you can add each application to just one user flow.

## Prerequisites

- **A sign-up and sign-in user flow**: Before you begin, [create the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) that you want to associate with your application.
- **Application registration**: In your external tenant, [register your application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).

## Add the application to the user flow

If you already registered your application in your external tenant, you can add it to the new user flow. This step activates the sign-up and sign-in experience for users who visit your application. An application can have only one user flow, but a user flow can be used by multiple applications.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **External Identities** > **User flows**.
3. From the list, select your user flow.
4. In the left menu, under **Use**, select **Applications**.
5. Select **Add application**.

   ![Screenshot showing selecting an application for the user flow.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-user-flow-add-application/assign-user-flow.png)
6. Select the application from the list. Or use the search box to find the application, and then select it.
7. Choose **Select**.

## Extension app

You might find an app named **b2c-extensions-app** in the application list. This app is created automatically inside the new directory, and it contains all extension attributes for your external tenant. If you want to collect information beyond the built-in attributes, you can create [custom user attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes) and add them to your sign-up user flow. Custom attributes are also known as directory extension attributes, as they extend the user profile information stored in your customer directory. All extension attributes for your external tenant are stored in the **b2c-extensions-app**. Do not delete this app. You can learn more about this app [here](https://learn.microsoft.com/en-us/azure/active-directory-b2c/extensions-app).

## Related content

- If you selected email with password sign-in, [enable password reset](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers).
- Add [Google](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-google-federation-customers), [Facebook](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-facebook-federation-customers), [Apple](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-apple-federation-customers) or custom [OIDC federation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-custom-oidc-federation-customers) federation.
- [Add multifactor authentication \(MFA\) to an app](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-multifactor-authentication-customers).
- [Test your user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows).
