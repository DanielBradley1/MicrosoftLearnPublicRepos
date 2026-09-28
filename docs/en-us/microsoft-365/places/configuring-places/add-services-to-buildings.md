<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/add-services-to-buildings -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Add services to buildings

You can customize the **Explore** tab of the Microsoft Places app to help end-users discover services and amenities available in different buildings. You can include web links and apps. For example, if a building has a cafeteria that offers online ordering, you can list the cafeteria and include a link to its website, or a link to a food ordering app.

Here's how services \(both links and apps\) appear in the Places app:

![Screenshot showing a page of available services, including parking, tech support, dining, and facility request.](https://learn.microsoft.com/en-us/microsoft-365/places/media/services-in-places/services-in-places-with-links.png)

Web links open in another browser tab, while apps open in the same host. Apps are more powerful because you can use existing Teams apps or build your own.

## Prerequisites

- Use the latest version of PowerShell 7 and follow additional management prerequisites described [here](https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/license-requirements).
- If you plan to add an app as a service, it must be configured to work in Teams and Outlook. See detailed instructions at the end of this article.

## Adding services to a building

1. Use **Get-PlaceV3** to look up the building's identity \(`PlaceId` parameter\). See [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3) for details.
2. Use **Set-PlaceV3** to associate the service with the building by using the **ResourceLinks** parameter as described in the examples. See [Set-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placev3) for details.

Important

The entire **ResourceLinks** set is replaced on update. To add or remove a service, include any existing values that you want to keep.

## Add your first web link

Use the following syntax to add a single web link to a building:

### PowerShell

```powershell
Set-PlaceV3 -Identity <PlaceId> -ResourceLinks @{name="Tech Support"; Value="https://www.contoso.sharepoint.com/TechSupport"; type="URL"}
```

## Add your first app

Your app must be a Teams app that is installed and deployed in your tenant. See [How to prepare your app](https://learn.microsoft.com/en-us/microsoft-365/places/configuring-places/add-services-to-buildings) for detailed instructions.

You also need the app's name and AppId. You can find the AppId in the [Teams Admin Center](https://admin.teams.microsoft.com/):

1. Select **Teams apps** > **Manage apps**.
2. Select the app.
3. Find the AppId in the **About** tab under app details.

Use the following syntax to add a single app to a building:

### PowerShell

```powershell
Set-PlaceV3 -Identity <PlaceId> -ResourceLinks @{name="<Application Name>"; Value="<AppId>"; type="MetaosApp"}
```

## Add more services to a building

This script shows how to add another web link to an existing **ResourceLinks** array:

### PowerShell

```powershell
$ResourceLinks = (Get-PlaceV3 <PlaceId>).ResourceLinks

$ResourceLinks.Add(@{
    name="Tech Support"
    Value="https://www.contoso.sharepoint.com/TechSupport"
    type="URL"
})

Set-PlaceV3 -Identity <PlaceId> -ResourceLinks $ResourceLinks
```

## Verify

After you've added links and apps to a building, open the **Explore** tab of the [Microsoft Places app](https://aka.ms/places) and navigate to the building to verify that the services appear in the correct location.

## How to prepare your app

Any Teams app can be added to the Places Explore page, but the app must be installed in Teams and deployed in Microsoft 365 by the tenant administrator. Both steps are required.

### Install the app in Teams

1. Go to the [Teams Admin Center](https://admin.teams.microsoft.com/).
2. Select **Teams apps** > **Setup Policies**.
3. In the **Manage Policies** tab, select the **Global \(Org-wide default\)** policy, or select a different policy if you want to install the app for a subset of users.
4. In the **Installed apps** section, select **+ Add apps**.
5. Type the app name in the search field, select **Select**, and then select **Add**.
6. Select **Save** and confirm the change.
7. Launch Microsoft Teams, select **...** in the navigation bar, and verify that the app is accessible.

### Deploy the app in Microsoft 365

1. Go to the [Microsoft Admin Center](https://admin.microsoft.com/).
2. Select **Show all** > **Settings** > **Integrated apps**.
3. Open the **Available apps** tab, search for the app, and select it.
4. In the app overview flyout, select **Deploy app**.
5. Verify that **Host products** includes Microsoft 365, Outlook, and Teams. If not, the app can't be used as a service in Microsoft Places. Contact the app developer for assistance.
6. Select **Next**, then assign the app to the **Entire organization** or to specific users or groups.
7. Select **Next**, then **Accept permissions**.
8. In the popup window, sign in and select **Accept** to provide consent.
9. Select **Next**, then **Finish deployment**.
10. Select **Done** to close the deployment wizard.
11. Verify that the app appears on the **Integrated apps** page.

#### Additional resources:

More details are available in these articles:

- To create a Teams app, visit the [Microsoft Teams developer documentation](https://learn.microsoft.com/en-us/microsoftteams/platform/mstdd-landing)
- [Teams apps that work on Outlook and Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/teams-apps-work-on-outlook-and-m365)
- [Use app setup policies to pin and install apps for users](https://learn.microsoft.com/en-us/microsoftteams/teams-app-setup-policies)
