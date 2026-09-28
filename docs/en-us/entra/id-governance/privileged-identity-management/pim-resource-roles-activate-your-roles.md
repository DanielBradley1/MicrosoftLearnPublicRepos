<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-activate-your-roles -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Activate my Azure resource roles in Privileged Identity Management

Use Microsoft Entra Privileged Identity Management \(PIM\), to allow eligible role members for Azure resources to schedule activation for a future date and time. They can also select a specific activation duration within the maximum \(configured by administrators\).

This article is for members who need to activate their Azure resource role in Privileged Identity Management.

Important

When a role is activated, Microsoft Entra PIM temporarily adds active assignment for the role. Microsoft Entra PIM creates active assignment \(assigns user to a role\) within seconds. When deactivation \(manual or through activation time expiration\) happens, Microsoft Entra PIM removes the active assignment within seconds as well.

Application may provide access based on the role the user has. In some situations, application access may not immediately reflect the fact that user got role assigned or removed. If application previously cached the fact that user does not have a role – when user tries to access application again, access may not be provided. Similarly, if application previously cached the fact that user has a role – when role is deactivated, user may still get access. Specific situation depends on the application’s architecture. For some applications, signing out and signing back in may help get access added or removed.

## Prerequisites

None

## Activate a role

When you need to take on an Azure resource role, you can request activation by using the **My roles** navigation option in Privileged Identity Management.

Note

PIM is now available in the Azure mobile app \(iOS \| Android\) for Microsoft Entra ID and Azure resource roles. Easily activate eligible assignments, request renewals for ones that are expiring, or check the status of pending requests. [Read more below](#activate-pim-roles-using-the-azure-mobile-app)

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com).
2. Browse to **Identity Governance** > **Privileged Identity Management** > **My roles**.

   [![Screenshot of my roles page showing roles you can activate.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles.png#lightbox)

3. Select **Azure resources** to see a list of your eligible Azure resource roles.

   ![Screenshot of my roles - Azure resource roles page.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles-azure-resources.png)

4. In the **Azure resource roles** list, find the role you want to activate.

   [![Screenshot of azure resource roles - My eligible roles list.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles-activate.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles-activate.png#lightbox)

5. Select **Activate** to open the Activate page.

   ![Screenshot of the opened Activate pane with scope, start time, duration, and reason.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/azure-role-eligible-activate.png)

6. If your role requires multifactor authentication, select **Verify your identity before proceeding**. You only have to authenticate once per session.
7. Select **Verify my identity** and follow the instructions to provide additional security verification.

   ![Screenshot of screen to provide security verification such as a PIN code.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-mfa-enter-code.png)

8. It's a best practice to only request access to the resources you need. If you want to specify a reduced scope.

   1. Go to the **Scope** tab.
   2. Click **Select scope** to select the scope.


   ![Screenshot of the Scope tab in the Activate - Billing Reader pane, showing the 'Select scope' button and a management group listed under Selected resources. This helps users identify where to click to begin scoping their activation request.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/activate-billing-reader-select-scope.png)


   3. Use the dropdown provided to scope the search to a specific resource.
   4. The reduced scoped resources are shown in **Selected resources** before activation and should be selected from the grid provided. The dropdown selection does not define the reduced scope.


   ![Screenshot showing the process of setting the scope for activation, with a management group selected in the grid. This image demonstrates how to confirm the correct resource is selected before proceeding with activation.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/active-billing-reader-set-scope.png)


   Note


   If your eligibility is at the management group level, the dropdown will show all direct child resources \(management group and subscription\). You can select either a management group or subscription from the grid shown, or further scope down the search by selecting the appropriate management group or subscription.


   ![Screenshot of activate - Resource filter pane to specify scope.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-roles-resource-filter.png)

9. If necessary, specify a custom activation start time. The member would be activated after the selected time.
10. In the **Reason** box, enter the reason for the activation request.
11. Select **Activate**.

    Note

    If the [role requires approval](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-approval-workflow) to activate, a notification will appear in the upper right corner of your browser informing you the request is pending approval.

## Activate a role with Azure Resource Manager API

Privileged Identity Management supports Azure Resource Manager API commands to manage Azure resource roles, as documented in the [PIM ARM API reference](https://learn.microsoft.com/en-us/rest/api/authorization/role-eligibility-schedule-requests). For the permissions required to use the PIM API, see [Understand the Privileged Identity Management APIs](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-apis).

To activate an eligible Azure role assignment and gain activated access, use the [Role Assignment Schedule Requests - Create REST API](https://learn.microsoft.com/en-us/rest/api/authorization/role-assignment-schedule-requests/create?tabs=HTTP) to create a new request and specify the security principal, role definition, requestType = SelfActivate and scope. To call this API, you must have an eligible role assignment on the scope.

Use a GUID tool to generate a unique identifier for the role assignment identifier. The identifier has the format: 00000000-0000-0000-0000-000000000000.

Replace {roleAssignmentScheduleRequestName} in the PUT request with the GUID identifier of the role assignment.

For more information about eligible roles for Azure resources management, see [PIM ARM API tutorial](https://learn.microsoft.com/en-us/rest/api/authorization/privileged-role-assignment-rest-sample?source=docs#activate-an-eligible-role-assignment).

This is a sample HTTP request to activate an eligible assignment for an Azure role.

### Request

```HTTP
PUT https://management.azure.com/providers/Microsoft.Subscription/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleAssignmentScheduleRequests/{roleAssignmentScheduleRequestName}?api-version=2020-10-01
```

### Request body

```JSON
{ 
"properties": { 
  "principalId": "aaaaaaaa-bbbb-cccc-1111-222222222222", 
  "roleDefinitionId": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608", 
  "requestType": "SelfActivate", 
  "linkedRoleEligibilityScheduleId": "b1477448-2cc6-4ceb-93b4-54a202a89413", 
  "scheduleInfo": { 
      "startDateTime": "2020-09-09T21:35:27.91Z", 
      "expiration": { 
          "type": "AfterDuration", 
          "endDateTime": null, 
          "duration": "PT8H" 
      } 
  }, 
  "condition": "@Resource[Microsoft.Storage/storageAccounts/blobServices/containers:ContainerName] StringEqualsIgnoreCase 'foo_storage_container'", 
  "conditionVersion": "1.0" 
} 
} 
```

### Response

Status code: 201

```HTTP
{ 
  "properties": { 
    "targetRoleAssignmentScheduleId": "c9e264ff-3133-4776-a81a-ebc7c33c8ec6", 
    "targetRoleAssignmentScheduleInstanceId": null, 
    "scope": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e", 
    "roleDefinitionId": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608", 
    "principalId": "aaaaaaaa-bbbb-cccc-1111-222222222222", 
    "principalType": "User", 
    "requestType": "SelfActivate", 
    "status": "Provisioned", 
    "approvalId": null, 
    "scheduleInfo": { 
      "startDateTime": "2020-09-09T21:35:27.91Z", 
      "expiration": { 
        "type": "AfterDuration", 
        "endDateTime": null, 
        "duration": "PT8H" 
      } 
    }, 
    "ticketInfo": { 
      "ticketNumber": null, 
      "ticketSystem": null 
    }, 
    "justification": null, 
    "requestorId": "a3bb8764-cb92-4276-9d2a-ca1e895e55ea", 
    "createdOn": "2020-09-09T21:35:27.91Z", 
    "condition": "@Resource[Microsoft.Storage/storageAccounts/blobServices/containers:ContainerName] StringEqualsIgnoreCase 'foo_storage_container'", 
    "conditionVersion": "1.0", 
    "expandedProperties": { 
      "scope": { 
        "id": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e", 
        "displayName": "Pay-As-You-Go", 
        "type": "subscription" 
      }, 
      "roleDefinition": { 
        "id": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/roleDefinitions/c8d4ff99-41c3-41a8-9f60-21dfdad59608", 
        "displayName": "Contributor", 
        "type": "BuiltInRole" 
      }, 
      "principal": { 
        "id": "a3bb8764-cb92-4276-9d2a-ca1e895e55ea", 
        "displayName": "User Account", 
        "email": "user@my-tenant.com", 
        "type": "User" 
      } 
    } 
  }, 
  "name": "fea7a502-9a96-4806-a26f-eee560e52045", 
  "id": "/subscriptions/aaaa0a0a-bb1b-cc2c-dd3d-eeeeee4e4e4e/providers/Microsoft.Authorization/RoleAssignmentScheduleRequests/fea7a502-9a96-4806-a26f-eee560e52045", 
  "type": "Microsoft.Authorization/RoleAssignmentScheduleRequests" 
} 
```

## View the status of your requests

You can view the status of your pending requests to activate.

1. Open Microsoft Entra Privileged Identity Management.
2. Select **My requests** to see a list of your Microsoft Entra role and Azure resource role requests.

   [![Screenshot of my requests - Azure resource page showing your pending requests.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-requests.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-requests.png#lightbox)

3. Scroll to the right to view the **Request Status** column.

## Cancel a pending request

If you don't require activation of a role that requires approval, you can cancel a pending request at any time.

1. Open Microsoft Entra Privileged Identity Management.
2. Select **My requests**.
3. For the role that you want to cancel, select the **Cancel** link.

   ```
   When you select Cancel, the request will be canceled. To activate the role again, you will have to submit a new request for activation.
   ```


   ![Screenshot of my request list with Cancel action highlighted.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/resources-my-requests-cancel.png)

## Deactivate a role assignment

When a role assignment is activated, you see a **Deactivate** option in the PIM portal for the role assignment. Also, you can't deactivate a role assignment within five minutes after activation.

## Activate with Azure portal

Privileged Identity Management role activation is integrated into the Billing and Access Control \(AD\) extensions within the Azure portal. Shortcuts to Subscriptions \(billing\) and Access Control \(AD\) allow you to activate PIM roles directly from these blades.

From the Subscriptions blade, select “View eligible subscriptions” in the horizontal command menu to check your eligible, active, and expired assignments. From there, you can activate an eligible assignment in the same pane.

![Screenshot of view eligible subscriptions on the Subscriptions page.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/view-subscriptions-1.png)

![Screenshot of view eligible subscriptions on the Cost Management: Integration Service page.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/view-subscriptions-2.png)

In Access control \(IAM\) for a resource, you can now select “View my access” to see your currently active and eligible role assignments and activate directly.

![Screenshot of current role assignments on the Measurement page.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/view-my-access.png)

By integrating PIM capabilities into different Azure portal blades, this new feature allows you to gain temporary access to view or edit subscriptions and resources more easily.

## Activate PIM roles using the Azure mobile app

PIM is now available in the Microsoft Entra ID and Azure resource roles mobile apps in both iOS and Android.

1. To activate an eligible Microsoft Entra role assignment, start by downloading the Azure mobile app \([iOS](https://apps.apple.com/us/app/microsoft-azure/id1219013620) \| [Android](https://play.google.com/store/apps/details?id=com.microsoft.azure)\). You can also download the app by selecting **Open in mobile** from Privileged Identity Management > My roles > Microsoft Entra roles.

   [![Screenshot shows how to download the mobile app.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/download-mobile-app.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/download-mobile-app.png#lightbox)
2. Open the Azure mobile app and sign in. Click on the ‘Privileged Identity Management’ card and select **My Azure Resource roles** to view your eligible and active role assignments.

   [![Screenshot of the mobile app showing privileged identity managementand the user's roles.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-select-role.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-select-role.png#lightbox)
3. Select the role assignment and click on **Action > Activate** under the role assignment details. Complete the steps to active and fill in any required details before clicking **Activate** at the bottom.

   [![Screenshot of the mobile app showing the validation process has completed. The image shows an Activate button.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-activate-role.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-activate-role.png#lightbox)
4. View the status of your activation requests and your role assignments under ‘My Azure Resource roles’.

   [![Screenshot of the mobile app showing the activation in progress message.](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-activation-processing.png)](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/media/pim-resource-roles-activate-your-roles/mobile-activation-processing.png#lightbox)

## Related content

- [Extend or renew Azure resource roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-resource-roles-renew-extend)
- [Activate my Microsoft Entra roles in Privileged Identity Management](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-how-to-activate-role)
