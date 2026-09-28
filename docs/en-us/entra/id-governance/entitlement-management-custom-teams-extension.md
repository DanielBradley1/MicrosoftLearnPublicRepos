<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-custom-teams-extension -->
<!-- Sitemap-Last-Modified: 2024-07-15 -->

# Tutorial: Integrating Microsoft Entra Entitlement Management with Microsoft Teams using Custom Extensibility and Logic Apps

Scenario: Use custom extensibility and an Azure Logic App to automatically send notifications to end users on Microsoft Teams when they receive or are denied access to an access package.

In this tutorial, you learn how to:

- Adding a Logic App Workflow to an existing catalog.
- Adding a custom extension to a policy within an existing access package.
- Register an application in Microsoft Entra ID for resuming Entitlement Management workflow
- Configuring ServiceNow for Automation Authentication.
- Requesting access to an access package as an end-user.
- Receiving access to the requested access package as an end-user.

## Prerequisites

- A Microsoft Entra user account with an active Azure subscription. If you don't already have one, you can [Create an account for free](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn).
- At least one of the following roles: Cloud Application Administrator, Application Administrator, or owner of the service principal.

## Create a Logic App and custom extension in a catalog

To create a Logic App and custom extension in a catalog, you'd follow these steps:

1. Navigate To Microsoft Entra admin center [Identity Governance - Microsoft Entra admin center](https://entra.microsoft.com/#view/Microsoft_AAD_ERM/DashboardBlade/%7E/elmEntitlement) as at least an [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator).

   Tip

   Other least privilege roles that can complete this task include the Catalog owner and the Resource group owner.
2. In the left menu, select **Catalogs**.
3. Select the catalog for which you want to add a custom extension and then in the left menu, select **Custom Extensions**.
4. In the header navigation bar, select **Add a Custom Extension**.
5. In the **Basics** tab, enter the name of the custom extension and a description of the workflow. These fields show up in the **Custom Extensions** tab of the Catalog.
6. Select the **Extension Type** as “**Request workflow**” to correspond with the policy stage of the access package requested being created, when the request is approved, when assignment is granted, and when assignment is removed.

   Note

   Another custom extension can be created for the **Pre-Expiration workflow**.

   [![Screenshot of creating a custom extension for entitlement management.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-create-custom-extension.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-create-custom-extension.png#lightbox)
7. Under Extension Configuration, select “**Launch and continue**”, which ensures that Entitlement Management continues after this workflow is triggered.  [![Screenshot of entitlement management custom extension behavior actions tab.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-custom-extension-behavior.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-custom-extension-behavior.png#lightbox)
8. In the **Details** tab, choose Yes in the "*Create new logic App*" field and provide the Azure subscription and resource group details, along with the Logic App name. Select “*Create a logic app*”.  [![Screenshot of expanded custom extension details selection.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-custom-extension-details-expanded.png)](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-custom-extension-details-expanded.png#lightbox)
9. It shows as “*Deploying*”, and once done a success message appears such as:  ![Screenshot of a successful deploy of a new Logic App.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-successful-deploy.png)
10. In **Review and Create**, review the summary of your custom extension and make sure the details for your Logic App call-out are correct. Then select **Create**.

This custom extension to the linked Logic App now appears in your Custom Extensions tab under Catalogs. You're able to call on this in the access package policies.

## Configuring the Logic App

1. The custom extension created shows under the **Custom Extensions** tab. Select the “*Logic app*” in the custom extension that will redirect you to a page to configure the logic app.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-configure-logic-app.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-configure-logic-app.png" alt="Screenshot of the configure logic apps screen." data-linktype="relative-path">
   </a>
   </span>

2. On the left menu, select **Logic app designer**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer.png" alt="Screenshot of the logic apps designer screen." data-linktype="relative-path">
   </a>
   </span>

3. Delete the **Condition** by selecting the 3 dots on the right side and select “*Delete*” and select “*OK*”. Once deleted, the page should have an option to add a new step.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-condition.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-condition.png" alt="Screenshot of setting the logic app designer condition." data-linktype="relative-path">
   </a>
   </span>

4. Select “*New Step*”, which opens a dialog box and then select **All** and expand the list of connectors.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-connectors.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-connectors.png" alt="Screenshot of the list of connectors for the Logic App." data-linktype="relative-path">
   </a>
   </span>

5. In the list that appears, search and select Microsoft Teams.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-connectors-teams.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-logic-app-designer-connectors-teams.png" alt="Screenshot of Microsoft Teams app in the Logic App connectors list." data-linktype="relative-path">
   </a>
   </span>

6. In the list of actions, select “*Post message in a chat or channel*”.  ![Screenshot of the teams actions in logic app designer.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-teams-post-message.png)
7. For **Post as** select “*Flow Bot*”, and for **Post In** select “*Chat with Flow bot*”.  ![Screenshot of setting the teams post message parameters.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-teams-post-message-parameters.png)
8. Selecting **Recipient** provides a pop up to select Dynamic Content. Select “*ObjectID -Requestor-Objectid*”.  ![Screenshot of setting the recipient ID for the teams post message.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-teams-post-message-recipient.png)
9. Add the email content in the message. You can also format plain text, or add dynamic content.  ![Screenshot of the dynamic content setting in the teams post message settings.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-teams-post-message-dynamic-content.png)
10. Select inside “*Add new Parameter*” and check the “*IsAlert*” box to have the message show up on Microsoft Teams’s activity feed.  ![Screenshot of setting isAlert in the teams post message settings.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-teams-post-message-alert.png)
11. Select **Save** to ensure your changes are stored. The Logic App is now ready to send emails when updates are made to an access package linked to it.

## Add Custom Extension to a policy in an existing Access Package

After setting up custom extensibility in the catalog, administrators can create an access package with a policy to trigger the custom extension when the request has been approved. This enables them to define specific access requirements, and tailor the access review process to meet their organization's needs.

1. In the Identity Governance portal as at least an [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator), select **Access packages**.

   Tip

   Other least privilege roles that can complete this task include the Catalog owner and the Access package manager.
2. Select the access package you want to add a custom extension \(Logic App\) to from the list of already created access packages.
3. Select **Edit** and under **Properties** change the catalog to one previously used in the section: [Create a Logic App and custom extension in a catalog](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-custom-teams-extension#create-a-logic-app-and-custom-extension-in-a-catalog) then select **Save**.
4. Change to the Policies tab, select the policy, and select **Edit**.
5. In the policy settings, go to the **Custom Extensions** tab.
6. In the menu below Stage, select the access package event you wish to use as trigger for this custom extension \(Logic App\). For our scenario, to trigger the custom extension Logic App workflow when an access package is requested, approved, granted, or removed, select **Request is created**, **Request is approved**, **Assignment is Granted**, and **Assignment is removed**.  ![Screenshot of custom extension policies for an access package.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-custom-extension-policy.png)
7. Select **Update** to add it to an existing access package's policy.

## Add Custom Extension to a new Access Package

1. In the Identity Governance portal, select **Access packages** and create a new access package.
2. Under the Basics tab, add the name of the policy, description and the catalog used in the section [Create a Logic App and custom extension in a catalog](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-custom-teams-extension#create-a-logic-app-and-custom-extension-in-a-catalog).  ![Screenshot of creating an access package.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-create-access-package.png)
3. Add the required **Resource roles**.
4. Add the required **Requests**.
5. Provide **Requestor Information** if needed.
6. Add **Lifecycle** details.
7. Under the Custom Extensions tab, in the menu below Stage, select the access package event you wish to use as trigger for this custom extension \(Logic App\). For our scenario, to trigger the custom extension Logic App workflow when an access package is requested, approved, granted, or removed, select **Request is created**, **Request is approved**, **Assignment is Granted**, and **Assignment is removed**.  ![Screenshot of access package policy selection.](https://learn.microsoft.com/en-us/entra/id-governance/media/entitlement-management-servicenow-integration/entitlement-management-access-package-policy.png)
8. In **Review and Create**, review the summary of your access package, and make sure the details are correct, then select **Create**.

Note

Select **New access package** if you want to create a new access package. For more information about how to create an access package, see: [Create a new access package in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-create). For more information about how to edit an existing access package, see: [Change request settings for an access package in Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-request-policy#open-and-edit-an-existing-policys-request-settings).

## Validation

To validate successful integration with Microsoft Teams, you'd add or remove a user to the access package created in the section [Add Custom Extension to a new Access Package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-custom-teams-extension#add-custom-extension-to-a-new-access-package). The user receives a notification on Microsoft Teams from **Power Automate**.

## Next step

[Configure verified ID settings for an access package in entitlement management](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-verified-id-settings)
