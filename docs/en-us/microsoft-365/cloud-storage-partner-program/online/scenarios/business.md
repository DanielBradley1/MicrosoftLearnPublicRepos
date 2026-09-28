<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/scenarios/business -->
<!-- Sitemap-Last-Modified: 2026-07-10 -->

# Managing Microsoft 365 user licenses

Cloud Storage Partner Program \(CSPP\) partners are responsible for ensuring that all users have a valid Microsoft 365 license to edit files in Microsoft 365 for the web applications. For business user licenses, you must implement the Business User Flow as described below to support document editing for business users.

Visit the [Microsoft 365 homepage](https://www.microsoft.com/microsoft-365) or contact your nearest [Microsoft office location](https://www.microsoft.com/en-us/worldwide) for more information regarding Microsoft 365 licenses.

Note

Licenses are not required for read-only file operations.

## Validating a user license

1. Before calling any Graph API, [Get access on behalf of the user](https://learn.microsoft.com/en-us/graph/auth-v2-user?tabs=http).
2. Once the access token is obtained, call the [Licensing Details Graph API](https://learn.microsoft.com/en-us/graph/api/user-list-licensedetails) to retrieve the user's license information.
3. Compare the returned service plans with those found on [Product names and service plan identifiers for licensing](https://learn.microsoft.com/en-us/entra/identity/users/licensing-service-plan-reference) to determine if the required SKU is assigned to the user.

   Note

   Required service plans for CSPP are SHAREPOINTWAC \(e95bec33-7c88-4a70-8e19-b10bd9d0c014\) or equivalent.

## Implementing the Business User Flow

Microsoft 365 for the web requires that hosts specify a user as a business user when using any actions that include the [BUSINESS\_USER](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#business_user) placeholder value, such as `edit`, `editnew`, and `view`. to ensure compliance with the business user licensing requirements.

Do the following to implement the Business User Flow:

1. Indicate that a user is a business user

   1. Set the [BUSINESS\_USER](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#business_user) placeholder value on the Microsoft 365 for the web action URL. This parameter must always be in the action URL for business users.

      Important

      Hosts must properly set the [BUSINESS\_USER](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/discovery#business_user) placeholder value in the Microsoft 365 for the web action URL for all actions that include the placeholder, including the view action.
   2. Include the [LicenseCheckForEditIsEnabled](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#licensecheckforeditisenabled) property in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response) response. This property must always be set to `true` for business users.
   3. **Optional** To include a direct download link to a user's file, you can also include the [DownloadUrl](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#downloadurl) in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo) response.

      Important

      For security purposes, URLs must be served from domains that are on the [Redirect domain allow list](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/build-test-ship/settings#redirect-domain-allow-list).

2. Validate the license for business users.

   The CSPP partner is responsible for making sure their business users have a valid Microsoft 365 for the web subscription that includes service plan for SHAREPOINTWAC \(e95bec33-7c88-4a70-8e19-b10bd9d0c014\) or equivalent.

## More information about licensing

For more general information about licensing, visit [Microsoft 365 Products](https://www.microsoft.com/en-us/microsoft-365).
