<!-- Source: https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Configure application access to online meetings or virtual events

For apps to access some cloud communications APIs with application permissions, in addition to the Microsoft Graph application permissions, tenant administrators must configure an application access policy. For details, see [supported application permissions](#supported-permissions-and-additional-resources).

The following sections describe the two main scenarios that require an application access policy.

## Allow applications to access online meetings on behalf of a user

In some cases, such as background services or daemon apps running on a server without a signed-in user, it is acceptable for an app to call Microsoft Graph and perform actions on behalf of a user. For example, an app might require Microsoft Graph to schedule multiple meetings based on published schedules \(like courses\) or external scheduling tools. In such situations, the application can act on behalf of any user. Therefore, it is important to make sure that the user possesses the necessary privileges, such as being the organizer or co-organizer, to access the online meeting.

## Allow applications to access virtual events created by the user

In cases where a signed-in user is not presented, an app can call Microsoft Graph to access a virtual event using application permissions. For example, an app can call Microsoft Graph to look up a virtual event that a user has created or retrieve attendance reports of a virtual event created by the user without using that user's delegated permissions. In these cases, the user must be the organizer of that virtual event.

Follow these steps to configure an application access policy for cloud communications resources such as online meetings and virtual events. These steps do not apply to other Microsoft Graph resources.

## Compare application access policy for online meetings and virtual events

The following table compares application access policy for online meeting and virtual event under various scenarios involving two users. These scenarios involve two users \(*user\_1* and *user\_2*\) and the following application access policies:

- *Policy\_1* contains one app ID \(*app\_1*\)
- *Policy\_2* contains one app ID \(*app\_2*\)
- *Policy\_3* contains both app IDs \(*app\_1* and *app\_2*\)

| Scenario | Online meeting | Virtual event |
| --- | --- | --- |
| *policy\_1* is assigned to *user\_1*, *policy\_2* is assigned to *user\_2* | *app\_1* can only access online meetings as *user\_1*  <br>*app\_2* can only access online meetings as *user\_2* | *app\_1* can only access virtual events created by *user\_1*  <br>*app\_2* can only access virtual events created by *user\_2* |
| *policy\_1* is assigned to *user\_1* and *user\_2* | *app\_1* can access online meetings as *user\_1*  <br>*app\_1* can access online meetings as *user\_2* | *app\_1* can access virtual events created by *user\_1*  <br>*app\_1* can access virtual events created by *user\_2* |
| *policy\_3* is assigned to *user\_1*, no policy is assigned to *user\_2* | *app\_1* and *app\_2* can access online meeting as *user\_1*  <br>No app can access online meeting as *user\_2* | *app\_1* and *app\_2* can access virtual events created by *user\_1*  <br>No app can access virtual events created by *user\_2* |
| *policy\_3* is assigned to the whole tenant | Both *app\_1* and *app\_2* can access online meetings as either *user\_1* or *user\_2* | Both *app\_1* and *app\_2* can access virtual events created by either *user\_1* or *user\_2* |

## Configure application access policy

To configure an application access policy and allow applications to access online meetings with application permissions:

1. Identify the app's application \(client\) ID and the user IDs of the users on behalf of which the app will be authorized to access online meetings.

   - Identify the app's application \(client\) ID in the [Microsoft Entra admin center > app registrations page](https://entra.microsoft.com/#view/Microsoft_AAD_RegisteredApps/ApplicationsListBlade/).
   - Identify the user's user \(object\) ID in the [Microsoft Entra admin center > user management page](https://entra.microsoft.com/#blade/Microsoft_AAD_IAM/UsersManagementMenuBlade).

2. Connect to Skype for Business PowerShell with an administrator account. For details, see [Manage Skype for Business Online with PowerShell](https://learn.microsoft.com/en-us/microsoft-365/enterprise/manage-skype-for-business-online-with-microsoft-365-powershell).
3. Create an application access policy containing a list of app IDs.

   Run the following cmdlet, replacing the **Identity**, **AppIds**, and **Description** \(optional\) arguments.

   ```powershell
   New-CsApplicationAccessPolicy -Identity Test-policy -AppIds "ddb80e06-92f3-4978-bc22-a0eee85e6a9e", "ccb80e06-92f3-4978-bc22-a0eee85e6a9e", "bbb80e06-92f3-4978-bc22-a0eee85e6a9e" -Description "description here"
   ```

4. Grant the policy to the user to allow the app IDs contained in the policy to access 1\) online meetings on behalf of the granted user, and 2\) virtual events created by the granted user.

   Run the following cmdlet, replacing the **PolicyName** and **Identity** arguments.

   ```powershell
   Grant-CsApplicationAccessPolicy -PolicyName Test-policy -Identity "748d2cbb-3b55-40ed-8c34-2eae5932b22a"
   ```

5. \(Optional\) Grant the policy to the whole tenant. This will apply to users who do not have an application access policy assigned. For details, see the cmdlet links in the [Related content](#related-content) section.

   Run the following cmdlet, replacing the **PolicyName** argument.

   ```powershell
   Grant-CsApplicationAccessPolicy -PolicyName Test-policy -Global
   ```

Note

- *Identity* refers to the policy name when creating the policy, but the user ID when granting the policy.
- When granting the policy, it will be applied to both online meetings and virtual events. If you prefer to manage online meetings and virtual events separately, we recommend that you have two separate applications.
- Changes to application access policies can take up to 30 minutes to take effect in Microsoft Graph REST API calls.

## Supported permissions and additional resources

Administrators can use ApplicationAccessPolicy cmdlets to control online meeting and virtual event access for an app that has been granted any of the following application permissions:

- OnlineMeetings.Read.All
- OnlineMeetings.ReadWrite.All
- OnlineMeetingArtifact.Read.All
- OnlineMeetingTranscript.Read.All
- OnlineMeetingRecording.Read.All
- VirtualEvent.Read.All

For more information about configuring application access policy, see the [PowerShell cmdlet reference for New-ApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/new-csapplicationaccesspolicy).

## Errors

If you attempt an API call to access an online meeting or virtual event without configuring the application access policy, you might encounter the following error:

```json
{
    "error": {
        "code": "Forbidden",
        "message": "No application access policy found for this app",
        "innerError": {
            "date": "<date_redacted>",
            "request-id": "599d9cb0-56ac-4dc5-b6f8-1456a1414609"
        }
    }
}
```

Follow the steps in this article to create and/or grant an application access policy that contains the app ID to the user ID.

## Related content

- [Permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference)
- [New-CsApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/new-csapplicationaccesspolicy)
- [Grant-CsApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/grant-csapplicationaccesspolicy)
- [Get-CsApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/get-csapplicationaccesspolicy)
- [Set-CsApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/set-csapplicationaccesspolicy)
- [Remove-CsApplicationAccessPolicy](https://learn.microsoft.com/en-us/powershell/module/skype/remove-csapplicationaccesspolicy)
- [Teams API overview](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
