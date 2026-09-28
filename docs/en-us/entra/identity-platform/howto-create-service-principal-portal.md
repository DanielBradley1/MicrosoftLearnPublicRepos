<!-- Source: https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal -->
<!-- Sitemap-Last-Modified: 2025-05-26 -->

# Register a Microsoft Entra app and create a service principal

In this article, you'll learn how to create a Microsoft Entra application and service principal that can be used with role-based access control \(RBAC\). When you register a new application in Microsoft Entra ID, a service principal is automatically created for the app registration. The service principal is the app's identity in the Microsoft Entra tenant. Access to resources is restricted by the roles assigned to the service principal, giving you control over which resources can be accessed and at which level. For security reasons, it's always recommended to use service principals with automated tools rather than allowing them to sign in with a user identity.

This example is applicable for line-of-business applications used within one organization. You can also [use Azure PowerShell](https://learn.microsoft.com/en-us/entra/identity-platform/howto-authenticate-service-principal-powershell) or the [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli) to create a service principal.

Important

Instead of creating a service principal, consider using managed identities for Azure resources for your application identity. If your code runs on a service that supports managed identities and accesses resources that support Microsoft Entra authentication, managed identities are a better option for you. To learn more about managed identities for Azure resources, including which services currently support it, see [What is managed identities for Azure resources?](https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/overview).

For more information on the relationship between app registration, application objects, and service principals, read [Application and service principal objects in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity-platform/app-objects-and-service-principals).

## Prerequisites

To register an application in your Microsoft Entra tenant, you need:

- A Microsoft Entra user account. If you don't already have one, you can [create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- Sufficient permissions to register an application with your Microsoft Entra tenant, and assign to the application a role in your Azure subscription. To complete these tasks, you'll need the `Application.ReadWrite.All` permission.

## Register an application with Microsoft Entra ID and create a service principal

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **App registrations** then select **New registration**.
3. Give the application a name, such as *example-app*.
4. Under **Supported account types**, select *Accounts in this organizational directory only*.
5. Under **Redirect URI**, select **Web** for the type of application you want to create. Enter the URI where the access token is sent to.
6. Select **Register**.

   ![Screenshot showing the application registration page.](https://learn.microsoft.com/en-us/entra/identity-platform/media/howto-create-service-principal-portal/create-app.png)

## Assign a role to the application

To access resources in your subscription, you must assign a role to the application. This needs to be done through the Azure portal. Decide which role offers the right permissions for the application. To learn about the available roles, see [Azure built-in roles](https://learn.microsoft.com/en-us/azure/role-based-access-control/built-in-roles).

You can set the scope at the level of the subscription, resource group, or resource. Permissions are inherited to lower levels of scope.

1. Sign in to the [Azure portal](https://portal.azure.com).
2. In the search bar at the top of the screen, search for and select **Subscriptions**.
3. In the new window, select the subscription to want to modify. If you don't see the subscription you're looking for, select **global subscriptions filter**. Make sure the subscription you want is selected for the tenant.
4. In the left pane, select **Access control \(IAM\)**.
5. Select **Add**, then select **Add role assignment**.
6. In the **Role** tab, select the role you wish to assign to the application in the list, then select **Next**.
7. On the **Members** tab, for **Assign access to**, select **User, group, or service principal**.
8. Select **Select members**. By default, Microsoft Entra applications aren't displayed in the available options. To find your application, search for it by name.
9. Select the **Select** button, then select **Review + assign**.

   ![Screenshot showing role assignment, and highlighting how to add members.](https://learn.microsoft.com/en-us/entra/identity-platform/media/howto-create-service-principal-portal/add-role-assignment.png)

Your service principal is set up. You can start using it to run your scripts or apps. To manage your service principal \(permissions, user consented permissions, see which users have consented, review permissions, see sign in information, and more\), go to **Enterprise applications**.

The next section shows how to get values that are needed when signing in programmatically.

## Sign in to the application

When programmatically signing in, you pass the directory \(tenant\) ID and the application \(client\) ID in your authentication request. You also need a certificate or an authentication key. To obtain the directory ID and application ID:

1. Open the [Microsoft Entra admin center](https://entra.microsoft.com) **Home** page.
2. Browse to **Entra ID** > **App registrations**, then select your application.
3. On the app's overview page, copy the Directory \(tenant\) ID value and store it in your application code.
4. Copy the Application \(client\) ID value and store it in your application code.

## Set up authentication

There are two types of authentication available for service principals: password-based authentication \(application secret\) and certificate-based authentication. *We recommend using a trusted certificate issued by a certificate authority*, but you can also create an application secret or create a self-signed certificate for testing.

### Option 1 \(recommended\): Upload a trusted certificate issued by a certificate authority

To upload the certificate file:

1. Browse to **Entra ID** > **App registrations**, then select your application.
2. Select **Certificates & secrets**.
3. Select **Certificates**, then select **Upload certificate** and then select the certificate file to upload.
4. Select **Add**. Once the certificate is uploaded, the thumbprint, start date, and expiration values are displayed.

After registering the certificate with your application in the application registration portal, enable the [confidential client application](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-flows-app-scenarios#single-page-public-client-and-confidential-client-applications) code to use the certificate.

### Option 2: Testing only: Create and upload a self-signed certificate

Optionally, you can create a self-signed certificate for *testing purposes only*. To create a self-signed certificate, open Windows PowerShell and run [New-SelfSignedCertificate](https://learn.microsoft.com/en-us/powershell/module/pki/new-selfsignedcertificate) with the following parameters to create the certificate in the user certificate store on your computer:

```powershell
$cert=New-SelfSignedCertificate -Subject "CN=DaemonConsoleCert" -CertStoreLocation "Cert:\CurrentUser\My"  -KeyExportPolicy Exportable -KeySpec Signature
```

Export this certificate to a file using the [Manage User Certificate](https://learn.microsoft.com/en-us/dotnet/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in) MMC snap-in accessible from the Windows Control Panel.

1. Select **Run** from the **Start** menu, and then enter **certmgr.msc**. The Certificate Manager tool for the current user appears.
2. To view your certificates, under **Certificates - Current User** in the left pane, expand the **Personal** directory.
3. Right-click on the certificate you created, select **All tasks->Export**.
4. Follow the Certificate Export wizard.

To upload the certificate:

1. Browse to **Entra ID** > **App registrations**, then select your application.
2. Select **Certificates & secrets**.
3. Select **Certificates**, then select **Upload certificate** and then select the certificate \(an existing certificate or the self-signed certificate you exported\).
4. Select **Add**.

After registering the certificate with your application in the application registration portal, enable the [confidential client application](https://learn.microsoft.com/en-us/entra/identity-platform/authentication-flows-app-scenarios#single-page-public-client-and-confidential-client-applications) code to use the certificate.

### Option 3: Create a new client secret

If you choose not to use a certificate, you can create a new client secret.

1. Browse to **Entra ID** > **App registrations**, then select your application.
2. Select **Certificates & secrets**.
3. Select **Client secrets**, and then select **New client secret**.
4. Provide a description of the secret, and a duration.
5. Select **Add**.

Once you've saved the client secret, the value of the client secret is displayed. This is only displayed once, so copy this value and store it where your application can retrieve it, usually where your application keeps values like `clientId`, or `authority` in the source code. You'll provide the secret value along with the application's client ID to sign in as the application.

## Configure access policies on resources

You might need to configure extra permissions on resources that your application needs to access. For example, you must also [update a key vault's access policies](https://learn.microsoft.com/en-us/azure/key-vault/general/security-features#privileged-access) to give your application access to keys, secrets, or certificates.

To configure access policies:

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select your key vault and select **Access policies**.
3. Select **Add access policy**, then select the key, secret, and certificate permissions you want to grant your application. Select the service principal you created previously.
4. Select **Add** to add the access policy, then select **Save**.

   ![Add access policy](https://learn.microsoft.com/en-us/entra/identity-platform/media/howto-create-service-principal-portal/add-access-policy.png)

## Related content

- Learn how to use [Azure PowerShell](https://learn.microsoft.com/en-us/entra/identity-platform/howto-authenticate-service-principal-powershell) or [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/azure-cli-sp-tutorial-1) to create a service principal.
- To learn about specifying security policies, see [Azure role-based access control \(Azure RBAC\)](https://learn.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal).
- For a list of available actions that can be granted or denied to users, see [Azure Resource Manager Resource Provider operations](https://learn.microsoft.com/en-us/azure/role-based-access-control/resource-provider-operations).
- For information about working with app registrations by using **Microsoft Graph**, see the [Applications](https://learn.microsoft.com/en-us/graph/api/resources/application) API reference.
