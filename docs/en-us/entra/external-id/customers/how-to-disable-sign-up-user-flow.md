<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-disable-sign-up-user-flow -->
<!-- Sitemap-Last-Modified: 2025-08-08 -->

# Disable sign-up in a sign-up and sign-in user flow

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

To restrict access so that only existing external users can sign in, you can disable the sign-up option in your sign-up and sign-in user flow. This article shows you how to use the Microsoft Graph API to update your user flow settings, preventing new registrations while allowing sign-in for current users.

You use the [Update authenticationEventsFlow API in Microsoft Graph](https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-update) to update the **onInteractiveAuthFlowStart** property > **isSignUpAllowed** property to `false`.

## Prerequisites

- **A sign-up and sign-in user flow**: Before you begin, [create the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers) that you want to associate with your application.
- **Application registration**: In your external tenant, [register your application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).

## Disable sign-up flow

To disable sign-up flow, you need to know the ID of the user flow whose sign-up you want to disable. You can't read the user flow ID from the Microsoft Entra admin center, but you can retrieve it via Microsoft Graph API if you know the app associated with it.

Follow these steps to disable the sign-up flow:

1. Read the application ID associated with the user flow:

   1. Browse to **Entra ID** > **External Identities** > **User flows**.
   2. From the list, select your user flow.
   3. In the left menu, under **Use**, select **Applications**.
   4. From the list, under **Application \(client\) ID** column, copy the Application \(client\) ID.

2. Identify the ID of the user flow whose sign-up you want to disable. To do so, [List the user flow associated with the specific application](https://learn.microsoft.com/en-us/graph/api/identitycontainer-list-authenticationeventsflows#example-4-list-user-flow-associated-with-specific-application-id). This Microsoft Graph API endpoint requires you to know the application ID you obtained from the previous step.
3. [Update your user flow](https://learn.microsoft.com/en-us/graph/api/authenticationeventsflow-update) to disable sign-up.

   **Example**:

   ```http
   PATCH https://graph.microsoft.com/beta/identity/authenticationEventsFlows/{user-flow-id} 
   ```


   **Request body**


   ```json
       {    
           "@odata.type": "#microsoft.graph.externalUsersSelfServiceSignUpEventsFlow",    
           "onInteractiveAuthFlowStart": {    
               "@odata.type": "#microsoft.graph.onInteractiveAuthFlowStartExternalUsersSelfServiceSignUp",    
               "isSignUpAllowed": false    
         }    
       }
   ```


   Replace `{user-flow-id}` with the user flow ID that you obtained in the previous step. Notice the `isSignUpAllowed` parameter is set to *false*. To re-enable sign-up, make a call to the Microsoft Graph API endpoint, but set the `isSignUpAllowed` parameter to *true*.

## Next steps

- [Add your application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)
- [Create custom user attributes and customize the order of the attributes on the sign-up page](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-define-custom-attributes).

## Related content

- [Test your user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows).
