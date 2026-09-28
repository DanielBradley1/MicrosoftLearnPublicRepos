<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lti/onedrive-lti-brightspace?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-12 -->

# Integrate Microsoft OneDrive LTI with Desire2Learn Brightspace

Note

The classic Microsoft OneDrive, OneNote, Teams Assignments, and Reflect LTI apps have been replaced by the [new Microsoft 365 LTI](https://aka.ms/LMSAdminDocs). The classic apps will be sunset on September 17, 2026. After that date, the classic apps and any content links in courses will stop working. However, the files, notebooks, teams, meetings, and check-ins created by the classic app will continue to be accessible through Microsoft 365. For further guidance on moving your users and courses to the new Microsoft 365 LTI experiences and migrating content links, review the [migration guidance for the classic LTI apps](https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-first-time-configuration#migration-guidance).

This guide provides IT admins steps for registering the OneDrive LTI app for the Desire2Learn \(D2L\) Brightspace LMS.

For an overview of Microsoft LTI, see [Integrating Microsoft products with your Learning Management System \(LMS\)](https://learn.microsoft.com/en-us/microsoft-365/lti/?view=o365-worldwide).

The steps to add the OneDrive LTI app are:

1. [Step 1: Add the new Microsoft OneDrive LTI app](#step-1-add-the-new-microsoft-onedrive-lti-app).
2. [Step 2: Deploy the LTI app in users' Brightspace experience](#step-2-deploy-the-lti-app-in-users-brightspace-experience).
3. [Step 3: Enable Microsoft 365 LTI OneDrive Filepicker Placements across Brightspace](#step-3-enable-microsoft-365-lti-onedrive-filepicker-placements-across-brighspace).

Note

The person who performs this integration should be an administrator of Brightspace and an administrator of the Microsoft 365 tenant.

The source documentation for LTI 1.3 settings is located in the [LTI Advantage - Administrator Guide](https://community.brightspace.com/s/article/LTI-Advantage-Administrator-Guide).

## Step 1: Add the new Microsoft OneDrive LTI app

### Register a new Microsoft OneDrive LTI app

1. Sign into the [Microsoft OneDrive LTI Registration Portal](https://onedrivelti.microsoft.com/admin).
2. Select the **Admin Consent** button and accept the permissions.

   Important

   If **Admin Consent** isn't accepted, the next step will give you an error, and you'll have to wait an hour before you can continue.
3. Select the **Create new LTI Tenant** button.
4. In the **LTI Consumer Platform** list, select **D2L Brightspace**.
5. In the **D2L Brightspace Base URL** field, enter your Brightspace base URL, like `https://myschool.brightspace.com`.
6. Select the **Next** button. The **Register LTI 1.3 App** page will load.  
   Keep this page open in its own tab when completing the next set of steps. The values required will be generated in the next steps.

### Add Microsoft LTI app to Brightspace

1. In a new browser tab, sign into your Brightspace LMS with an *Administrator* or *Super Administrator* account for the organizations you want to add the OneDrive LTI app to.
2. Select the gear icon at the top right to access **Admin Tools**.
3. Under the **Organization Related** category, find **Manage Extensibility**.  
   The URL should look similar to this example: `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/registrations/home`.
4. Select the **LTI Advantage** tab at the top, and then select **Register a Tool**.
5. Select the **Standard** radio button for the **Tool registration type**.
6. Enter a name for the app, like `Microsoft OneDrive LTI App`.
7. In the **Domain** field, enter `https://onedrivelti.microsoft.com`.
8. Navigate to the browser tab with the Microsoft OneDrive LTI Registration Portal to copy the other required values:

   1. Paste the `ToolOIDCLaunchRedirectUri` value into the **Redirect URLs** field.

      Important

      You'll use this **Redirect URL** value in later steps.
   2. Paste the ``OIDCLoginInitiationUri` value into the **OpenID Connect Login URL** field.
   3. Paste the `ToolPublicJwksUri` value into the **Keyset URL** field.

9. Under **Extensions**, select the **Deep Linking** checkbox.
10. Select the **Register** button at the bottom of the page.  
    Brightspace app registration details will be displayed. Keep this page open in its own tab while completing the next set of steps.

### Add Brightspace LTI Platform registration details to the Microsoft OneDrive LTI Registration Portal

After the app is registered in Brightspace, you'll copy values from Brightspace's registration portal into Microsoft's LTI Registration Portal.

1. Navigate back your open browser tab of Microsoft's OneDrive LTI Registration Portal page.
2. Copy the required Brightspace app registration details page and paste them into Microsoft's LTI Registration Portal.

   1. Paste Brightspace's **Issuer** value into Microsoft's **LTI Issuer** field.
   2. Paste Brightspace's **OpenID Connect Authentication Endpoint** value into Microsoft's **LTI Authorize URL** field.
   3. Paste Brightspace's **Brightspace Keyset URL** value into Microsoft's **LTI Public Jwks URL** field.
   4. Paste Brightspace's **Brightspace OAuth2 Access Token URL** value into Microsoft's **LTI Access Token URL** field.
   5. Paste Brightspace's **Client ID** value into Microsoft's **LTI Client ID** field.

3. Select **Next** > **Save**.  
   A message will appear saying *LTI consumer was created successfully.*  
   Optional: You can review the registration details by selecting the **View LTI Tenants** button on the home page.

## Step 2: Deploy the LTI app in users' Brightspace experience

After Microsoft OneDrive LTI and Brightspace are connected, you need to deploy the OneDrive LTI app in users' Brightspace experience.

1. In the tab with your Brightspace admin experience, navigate to **Admin Tools** > **Manage Extensibility** > **LTI Advantage** to view the LTI Advantage apps list.
2. Select the name of the LTI Advantage app you created in the previous step.
3. Scroll to the bottom of the page and select the **View Deployments** link.  
   The URL should look similar to this example: `https://<yourbrightspacedomain>/d2l/le/ltiadvantage/deployments/home`
4. Select **New Deployment**.
5. Select the app by the name you entered when creating the Brightspace app registration, like `Microsoft OneDrive LTI App`.
6. Enter a deployment name for this deployment, like `Microsoft OneDrive Deployment`.
7. In the **Extensions** section, select **Deep Linking**.
8. Select all the security settings checkboxes except for **Classlist** and **Anonymous**.
9. Don't select any configuration settings, substitution parameters, or customer parameters.
10. Select **Add Org Units** and choose the org units you want to use the new LTI app.  
    You can select:

    - The **Root org** along with the **All descendants** option to include everyone.
    - Individual org units to include just those units.
    - **All descendant** units using the radio buttons in the **Options** column.

11. Select **Create Deployment**.  
    Your new deployment will display in the list. Leave this tab option and continue with the next steps.

### Create links to the OneDrive LTI app in Brightspace

This step adds the OneDrive LTI app to menus in the Brightspace LMS where users select to insert OneDrive files.

1. In the tab with your Brightspace admin experience, navigate to **Admin Tools** > **Manage Extensibility** > **LTI Advantage** to view the LTI Advantage apps list.
2. Select the name of the LTI Advantage app you created.
3. Scroll to the bottom of the page and select the **View Deployments** link.
4. Select the name of the deployment you created in the previous step.
5. Scroll to the bottom of the page and select **View Links**.

#### Create a **Deep Linking Quicklink** for the app that will appear in the **Quicklinks** menu

1. From the **View Links** page, select **New Link**.
2. Enter a name for the link, like `Microsoft OneDrive`.  
   This name will be visible to users in their Brightspace experience.
3. Paste the **Redirect URL** into the **URL** field.  
   This is the same **Redirect URL** used in previous steps, listed as the `ToolOIDCLaunchRedirectUri` in Microsoft's OneDrive LTI Registration Portal.
4. Set the **Type** to **Deep Linking Quicklink**.
5. Select **+Add Customer Parameter** and enter `launchType` for the **Name** field and `linkSelection` for the **Value** field.
6. Select the **Save and Close** button.

#### Create a **Deep Linking Insert Stuff** link for the app that will appear in the **Insert Stuff** menu

1. From the **View Links** page, select **New Link**.
2. Enter in a name for the link, like `Microsoft OneDrive`.  
   This name will be visible to users in their Brightspace experience.
3. Paste the **Redirect URL** into the **URL** field.  
   This is the same **Redirect URL** used in previous steps, listed as the `ToolOIDCLaunchRedirectUri` in Microsoft's OneDrive LTI Registration Portal.
4. Set the **Type** to **Deep Linking Insert Stuff**.
5. Select the **Save and Close** button.

## Step 3: Enable Microsoft 365 LTI OneDrive Filepicker Placements across Brighspace

To add the OneDrive LTI app to Brightspace for quick access, you'll need to set a **Config Variable** with the link ID of the LTI app.

Note

D2L recommends that the Config Variable **d2l.3rdParty.Microsoft.OneDriveLTI.LinkId** should be set at the Organization level to be available to all Org Units. In the rare case that the customer wants to restrict the Microsoft 365 LTI app to some Programs or Departments, then the Config Variable **d2l.3rdParty.Microsoft.OneDriveLTI.LinkId** should be set only for those Org Units in the Override Values Section.

### Collect the Link ID

1. Sign in to Brightspace as an Administrator or Super Administrator.
2. Navigate to **Admin Tools** by selecting the gear icon at the top right.
3. Select **Manage Extensibility** to view the **LTI Advantage Deployments** list.
4. Select the name of the LTI Advantage app you created.
5. Scroll to the bottom of the page and select **View Deployments**.
6. Select the name of the app deployment you created.
7. Scroll down to the bottom of the page and select **View Links**.
8. Select the name of the link with the **Deep Linking Quicklink** type.
9. Move your mouse to the URL address bar in your browser.
10. Copy the numeric digits after the final `/` in the URL.  
    For example, if the link url is `https://example.desire2learn.com/d2l/le/ltiadvantage/deployments/3bfcc0b7-2fb6-4ffe-b353-95b520d4bae6/links/details/259`, copy the `259` numeric value.

### Update the Config Variables

1. In the Brightspace admin portal, navigate to **Admin Tools** by selecting the top right gear icon.
2. Select **Config Variable Browser**.
3. In the **All Variables** menu on the left, navigate to **3rdParty** > **Microsoft** > and select **OneDriveLTI**.  
   You should see the variable name `3rdparty.microsoft.onedriveLTI.linkId` in the right pane.
4. Select the **LinkId variable** name.
5. On the **LinkId configuration** screen, select **Add Value** to select an **Org Unit** and paste the numeric **Link ID** value you collected previously. D2L recommends selecting the OrgUnit at the Organization level so the app is available across the entire environment.
6. If you need to restrict the Microsoft LTI app for just some Org Units, repeat this step for each Org Unit you wish to use the **Quicklinks placements**.  
   To have this setting applied to descendent org types of those you added, you can edit the **Cascading Org Unit Types** and select which types and in which order the settings will apply.

The OneDrive LTI app will now show up in the **Add Existing Content**, **QuickLinks**, and **Insert Stuff** menus in Brightspace.

Users will see a generic link icon rather than a OneDrive cloud icon. The name shown in the menu will be the name provided in the app's LTI link settings.

These links can be turned off and on as desired and targeted to specific Orgs and decedents by configuration.

For more information on configuring applications in Brightspace, visit [Brightspace Help](https://documentation.brightspace.com).

## Common questions concerning the OneDrive LTI app

### Does the new OneDrive LTI FilePicker support personal accounts?

Yes, personal accounts are allowed to open OneDrive to upload the files. There's a checkbox in the app in the OneDrive LTI Registration Portal to allow multiple accounts or not. If checked, personal accounts are allowed.

### Does the FilePicker support multiple languages?

The OneDrive LTI FilePicker looks at the LTI language setting parameter passed from the LMS, and \(as backup\) the browser setting \(since the former is an optional claim\) to determine the language to use.
