<!-- Source: https://learn.microsoft.com/en-us/graph/use-postman-with-app-only-authentication -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Use app-only authentication with Postman for Microsoft Graph

This article describes how you can use app-only \(application\) authentication with Postman for Microsoft Graph to run requests without a signed-in user.

## Prerequisite

Complete the setup instructions in the [Use Postman with the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/use-postman) article, before you can continue with this tutorial.

## Step 1: Get an application access token

The first time you run a request as an application authentication flow, you need to get an access token:

1. Select the **Application** folder.
2. Select the **Authorization** tab.
3. In the **Configure New Token** section, leave all the fields as preconfigured, including the **Grant type** that is set to `Client Credentials`.
4. Scroll down on the right and select **Get New Access Token**.
5. Select **Proceed**, and then select the **Use Token** button.

You have now a valid access token to use for application requests.

## Step 2: Run your first application request

The **Application** folder contains many requests for Microsoft Graph workloads that you can consume:

1. Expand the **Application** folder, and then expand the **User** folder.
2. Double-click **Get Users** to open the request.
3. On the top right, select **Send**.

You have now successfully run a Microsoft Graph request using application authentication.

You can repeat these steps to run other requests to Microsoft Graph. Note that you have to add [permissions](https://learn.microsoft.com/en-us/graph/permissions-reference) to your Microsoft Entra application for other requests to work; otherwise, you get permission denied errors in your responses. To find the right permissions, check the **Permissions** section of the relevant API and look for the application permission type.

## Next steps

Now that you have successfully made a Microsoft Graph call using application authentication, proceed to the next article to run your first delegated request.

- [Use delegated authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-delegated-authentication)

### Contributing to the collection

If you want to contribute your own requests to the Microsoft Graph Postman collection, you need a Postman license. You can make your changes to the forked collection, and then hover over the collection top node and select **Create pull request**.

## Known issues

### Authentication fails with "You can't get there from here"

Certain [conditional access policies](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/overview) configured by your organization's administrators can block the authentication flow from Postman. To explore alternatives, contact your administrators.

### "Access to OData is disabled."

See [403 Forbidden "Access to OData is disabled."](https://learn.microsoft.com/en-us/graph/resolve-auth-errors#403-forbidden-access-to-odata-is-disabled).

## Related content

- [Use Postman with the Microsoft Graph API](https://learn.microsoft.com/en-us/graph/use-postman)
- [Use delegated authentication with Postman for Microsoft Graph](https://learn.microsoft.com/en-us/graph/use-postman-with-delegated-authentication)
