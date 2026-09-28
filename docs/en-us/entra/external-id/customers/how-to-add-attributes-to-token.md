<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-add-attributes-to-token -->
<!-- Sitemap-Last-Modified: 2025-09-16 -->

# Add user attributes to token claims

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

User attributes are values collected from the user during self-service sign-up. In addition to built-in user attributes, you can create custom attributes when you need to collect additional information. Because your application might rely on certain user attributes to function as designed, you can add any of these attributes to the token that is sent from Microsoft Entra ID to your application.

You can specify which built-in or custom attributes you want to include as claims in the token that Microsoft Entra ID sends to your application.

## Prerequisites

- [Register the application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app) with Microsoft Entra ID.
- [Create a sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) and selected the attributes you want to collect during sign-up.
- [Create the custom attributes](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes) you want to include.

## Add built-in or custom attributes to the token

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **App registrations**.
3. Select your application in the list to open the application's **Overview** page.

   ![Screenshot of the overview page of the app registration.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-attributes-to-token/select-app.png)
4. In the **Essentials** section, under **Managed application in local directory**, select the link showing the name of your application.

   ![Screenshot of the managed application in local directory link.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-attributes-to-token/managed-app-in-local-directory-link.png)
5. Under **Manage**, select **Single Sign-on**.
6. In the **Attributes & Claims** section, select the **Edit** icon.

   ![Screenshot of the attributes and claims section and the edit icon.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-attributes-to-token/single-sign-on-edit.png)

### To add a built-in attribute to the token as a claim

1. On the **Attributes & Claims** page, select **Add new claim**.
2. Enter a **Name**.
3. Next to **Source**, select **Attribute**. Then use the drop-down list to select the built-in attribute.

   ![Screenshot of the drop-down list of built-in attributes.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-attributes-to-token/add-built-in-claim.png)
4. Select **Save**. Repeat for all built-in attributes you want to add.

### To add a custom attribute to the token as a claim

1. On the **Attributes & Claims** page, select **Add new claim**.
2. Enter a **Name**.
3. Next to **Source**, select **Directory schema extension**.

   ![Screenshot of the Directory schema extension option.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/how-to-add-attributes-to-token/manage-claim-directory-schema.png)
4. In the **Select Application** pane, select **b2c-extensions-app** \(the app that contains all extension attributes for your external tenant\), and then choose **Select**.
5. In the **Add Extension Attributes** pane, find the custom attribute you want to add as a claim to the token, and then select it.
6. Select **Add**.
7. Select **Save**. Repeat for each custom attribute you want to add.

### Update the application manifest to accept mapped claims in Microsoft Graph App Manifest\(New\)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Entra ID** > **App registrations**.
3. Select your application in the list to open the application's **Overview** page.
4. In the left menu, under **Manage**, select **Manifest** to open the application manifest.
5. Find the **acceptMappedClaims** key and set its value to **true**.
6. Find the **isFallbackPublicClient** key and set its value to **true**.
7. Select **Save**.

## See also

- [Create a REST API with a token issuance start event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-setup)
- [Configure a custom claims provider for a token issuance event](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-tokenissuancestart-configuration)
