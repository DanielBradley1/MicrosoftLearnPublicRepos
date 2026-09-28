<!-- Source: https://learn.microsoft.com/en-us/graph/use-postman -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Use Postman with the Microsoft Graph API

Postman is an API platform for building and using APIs. Postman simplifies each step of the API lifecycle and streamlines collaboration so that you can create better APIs faster.

You can use the Microsoft Graph Postman collection to get started with Microsoft Graph APIs in minutes.

![Image of Postman](https://learn.microsoft.com/en-us/graph/images/postman-screenshot.png)

This article explains how to configure the initial setup for your environment to run Microsoft Graph on Postman. For details about how to authenticate to Microsoft Graph via Postman, see [Use delegated authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-delegated-authentication) and [Use app-only authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-app-only-authentication). You can also explore Microsoft Graph APIs directly in your web browser by using [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).

For details about how to use Postman, follow the steps in this article or watch the following video.

<iframe src="https://www.youtube-nocookie.com/embed/3RTHY3jScmA" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Tip

The Microsoft Graph Postman collection is configured to authenticate with the global Microsoft Entra service and access the global Microsoft Graph service \(`graph.microsoft.com`\). If you want to use the collection to connect to a [national cloud deployment](https://learn.microsoft.com/en-us/graph/deployments), you must modify your fork of the collection.

- Update the request URL, replacing `graph.microsoft.com` with the Microsoft Graph service root endpoint for your national cloud.
- Update the **Auth URL** and **Access Token URL** values on the **Authorization** tab of the **Delegated** and **Application** folders, replacing `login.microsoftonline.com` with the endpoint for your national cloud.
- Update the **Scope** value on the **Authorization** tab of the **Delegated** and **Application** folders, replacing `graph.microsoft.com` with the Microsoft Graph service root endpoint for your national cloud.

## Step 1: Fork the Microsoft Graph Postman collection

To use the Postman collection, fork it to your own Postman workspace. Do this from the web browser.

1. Go to [Postman](https://www.postman.com/) and sign in.
2. Go to the Postman collection labeled [Microsoft Graph](https://www.postman.com/microsoftgraph/workspace/microsoft-graph/collection/455214-085f7047-1bec-4570-9ed0-3a7253be148c/fork).
3. Fill in a label for your own fork; this can be any text.
4. Under **Workspace**, ensure that **My Workspace** is selected in the dropdown list.
5. Select **Fork Collection**.

Important

Don't fork this collection to a public workspace. Use a private workspace to reduce the risk of exposing credentials or other sensitive data.

You are redirected to a fork of the main Microsoft Graph Postman collection in your own workspace.

## Step 2: Download the Postman Agent \(optional - Postman web browser only\)

To use this particular Postman collection in your web browser, download the [Postman Desktop Agent](https://www.postman.com/downloads). You can't use Postman for the web without this due to CORS restrictions in the web browser.

You don't need the agent if you're using the Postman for Windows app. If you open Postman for Windows, you see this forked collection in your workspace.

## Step 3: Create a Microsoft Entra application

To use this collection in your own developer tenant, create a Microsoft Entra application and give it the appropriate permissions for the requests that you want to call. If you don't have a Microsoft 365 tenant, you might qualify for one through the [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program); for details, see the [FAQ](https://learn.microsoft.com/en-us/office/developer-program/microsoft-365-developer-program-faq#who-qualifies-for-a-microsoft-365-e5-developer-subscription-). Alternatively, you can [sign up for a 1-month free trial or purchase a Microsoft 365 plan](https://www.microsoft.com/en-us/microsoft-365/try).

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Expand the **Identity** menu > select **Applications** > **App registrations** > **New registration**.
3. Set the **Application name** to `Postman`.
4. From the dropdown menu, select **Web**.
5. Set the **Redirect URI** to `https://oauth.pstmn.io/v1/browser-callback`.
6. Select **Register**.
7. On the left menu, select **API Permissions**.
8. On the horizontal menu, select **Add a permission**, and choose **Microsoft Graph**.
9. Select the **Delegated permissions** option, type `Mail.`, expand the **Mail** options, and then select `Mail.Read`.
10. Select the **Application permissions** option, type `User.`, expand the **User** options, and then select `User.Read.All`.
11. Select **Add permissions** to add both permissions from the previous steps.
12. On the horizontal menu, select **Grant admin consent for**, and then select **Yes**.
13. On the left menu, select **Overview**. From here, you can get the **application \(client\) ID** and **directory \(tenant\) ID**. You'll need these in step 4.
14. On the left menu, select **Certificates and secrets**.
15. Select **New client secret**, enter a description, and then select **Add**. Hover over the new client secret **Value** and copy it; you'll need this in step 4.

The application now has two permissions configured. `Mail.Read` is added as a delegated permission, which is a permission that requires a signed-in user. The application can read mail on behalf of the user. `User.Read.All` is added as an application permission, which is a permission that does not require a signed-in user. The application can read users in Microsoft Entra ID.

## Step 4: Configure authentication

**IMPORTANT:** In the following steps, <u>always set values in the "Current value" column</u>, not the "Initial value" column. This ensures that your secrets and tokens are saved locally on your machine.

In this step, you set up the environment variables in Postman that you use to retrieve an access token.

1. Go to [Fork environment](https://www.postman.com/microsoftgraph/workspace/microsoft-graph/environment/455214-efbc69b2-69bd-402e-9e72-850b3a49bb21/fork).
2. Add a label for the fork. This can be any text.
3. Under **Workspace**, ensure that **My Workspace** is selected in the dropdown list.
4. Select **Fork Environment**.
5. In `ClientID`, set the **Current value** to the application \(client\) ID value from step 3.15.
6. In `TenantID`, set the **Current value** to the directory \(tenant\) ID value from step 3.15.
7. In `ClientSecret`, set the **Current value** to the client secret value from step 3.17.
8. On the top right, select **Save**.
9. Close the **Manage Environments** tab.
10. On the top right, next to the eye icon, verify that **M365 Environment** is selected in the dropdown and not **No environment**.

## Next steps

Now that you have successfully set up the environment to run Microsoft Graph on Postman, continue with the authentication steps:

- [Use delegated authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-delegated-authentication)
- [Use app-only \(application\) authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-app-only-authentication)

## Contributing to the collection

If you want to contribute your own requests to the Microsoft Graph Postman collection, you need a Postman license. You can make your changes to the forked collection, and then hover over the collection top node and select **Create pull request**.

## Known issues

### Authentication fails with "You can't get there from here"

Certain [conditional access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) configured by your organization's administrators can block the authentication flow from Postman. To explore alternatives, contact your administrators.

### "Access to OData is disabled."

See [403 Forbidden "Access to OData is disabled."](https://learn.microsoft.com/en-us/graph/resolve-auth-errors#403-forbidden-access-to-odata-is-disabled).
