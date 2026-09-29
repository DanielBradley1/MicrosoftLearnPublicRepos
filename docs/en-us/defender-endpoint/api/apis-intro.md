<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Access the Microsoft Defender for Endpoint APIs

Important

Advanced hunting capabilities are not included in Defender for Business.

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Defender for Endpoint exposes much of its data and actions through a set of programmatic APIs. Those APIs will enable you to automate workflows and innovate based on Defender for Endpoint capabilities. The API access requires OAuth2.0 authentication. For more information, see [OAuth 2.0 Authorization Code Flow](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code).

Watch this video for a quick overview of Defender for Endpoint's APIs.

<iframe src="https://learn-video.azurefd.net/vod/player?id=f6300637-b48e-49d7-aa76-2778a711ae6c" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

In general, you'll need to take the following steps to use the APIs:

- Create a [Microsoft Entra application](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-nativeapp)
- Get an access token using this application
- Use the token to access Defender for Endpoint API

You can access Defender for Endpoint API with **Application Context** or **User Context**.

- **Application Context: \(Recommended\)**

  Used by apps that run without a signed-in user present. for example, apps that run as background services or daemons.

  Steps that need to be taken to access Defender for Endpoint API with application context:

  1. Create a Microsoft Entra Web-Application.
  2. Assign the desired permission to the application, for example, 'Read Alerts', 'Isolate Machines'.
  3. Create a key for this Application.
  4. Get token using the application with its key.
  5. Use the token to access the Microsoft Defender for Endpoint API

     For more information, see [Get access with application context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp).

- **User Context:**

  Used to perform actions in the API on behalf of a user.

  Steps to take to access Defender for Endpoint API with user context:

  1. Create Microsoft Entra Native-Application.
  2. Assign the desired permission to the application, e.g 'Read Alerts', 'Isolate Machines' etc.
  3. Get token using the application with user credentials.
  4. Use the token to access the Microsoft Defender for Endpoint API

     For more information, see [Get access with user context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-nativeapp).

Tip

When more than one query request is required to retrieve all the results, Microsoft Graph returns an `@odata.nextLink` property in the response that contains a URL to the next page of results. For more information, see [Paging Microsoft Graph data in your app](https://learn.microsoft.com/en-us/graph/paging).

## Related topics

- [Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-list)
- [Access Microsoft Defender for Endpoint with application context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-webapp)
- [Access Microsoft Defender for Endpoint with user context](https://learn.microsoft.com/en-us/defender-endpoint/api/exposed-apis-create-app-nativeapp)
