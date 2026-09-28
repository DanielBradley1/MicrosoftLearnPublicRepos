<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/start-page -->
<!-- Sitemap-Last-Modified: 2025-06-25 -->

# Integrate start-page experiences in the Microsoft 365 Document Collaboration Partner Program

Outside of a meeting experience, users can open the Excel, PowerPoint, and Word apps in your collaboration application. A user will see the files they recently opened in that Office app, templates for creating a new file, and be able to take action. To view this experience, the user must open the Office app without opening a specific file or document.

To see what the start-page experience looks like in Teams, access the Excel, PowerPoint, and Word app from the left-side App bar, whether it was [pinned to the left side of Teams](https://support.microsoft.com/office/3045fd44-6604-4ba7-8ecc-1c0d525e89ec) or not \(see [Access your apps in Microsoft Teams](https://support.microsoft.com/office/0758cb09-9e85-40e7-a974-51df7734646a)\).

The following image displays this experience using the Word app in Teams.

[![Start Page experience in the Word app in Teams.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/start-page-experience-word.png)](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/start-page-experience-word.png#lightbox)

## Prerequisites

- The user must use the appId that was provided to the MDCPP program administrator.
- The app must be able to obtain a valid user token to the OneDrive for Business or SharePoint resource.

  - If you use the [OneDrive File Picker](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration#recommendations), you can use the same token acquisition code here.

- The user has been signed in with a Microsoft 365 account.
- A tenant admin has configured for token generation under `MDCPP.All` scope. To learn how to configure, see [Configure for token generation under MDCPP.All scope](#configure-for-token-generation-under-mdcppall-scope).

## Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

function loadStartPage(
    documentType: Microsoft.DocumentType)
{
  Microsoft.initializeDocument({
    hostName: "Contoso",
    hostClientType: "web"
  });

  const container = window.document.createElement("div");
  container.style.height = "100%";
  window.document.body.appendChild(container);

  Microsoft.launchStartPage({
    startPageInfo: {
      documentType: Microsoft.DocumentType.Word
    },
    sessionInfo: {
      hostCorrelationId: uuidv4()
    },
    container,
    fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
      let scopes: string[] = [];

      if (claim && claim.length > 0) {
        claim.forEach((val) => {
            scopes.push(`${resourceUrl}/${val}`);
        });
      } else {
        scopes.push(resourceUrl);
      }

      let token = await getTokenImpl({ scopes });
      return token;
    }
  })
  .then((response: Microsoft.BootInfo) => {
    console.log('Launch API finished {0}, {1}', response.isBootSuccess, response.errorInfo);
  })
  .catch((e : any) => {
    console.log(e);
  });
}
```

## Configure for token generation under MDCPP.All scope

To configure for token generation under the `MDCPP.All` scope, a tenant admin must use the following instructions.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) with a tenant admin account for your service tenant.
2. In another browser tab or window, open [Microsoft Graph Explorer](https://developer.microsoft.com/graph/graph-explorer) and sign in with the tenant admin account.
3. On the **Access token** tab, you should already have a token.
4. Select the **Modify Permissions** tab and look for the `Application.ReadWrite.All` permission. If consent hasn't been granted for this scope, choose the **Consent** button to grant consent.

   ![Application.ReadWrite.All permission requires consent in the Modify permissions tab of Microsoft Graph Explorer.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/ms-graph-explorer-modify-permissions.png)
5. Create a Service Principal with the following API.

   POST: `https://graph.microsoft.com/v1.0/servicePrincipals`

   Body:

   ```json
   {
     "appId": "4765445b-32c6-49b0-83e6-1d93765276ca"
   }
   ```

6. Return to the Microsoft Entra admin center tab or window after a few minutes and select **Applications** > **Enterprise applications** in the left nav where you should see an app named **OfficeHome** listed.

   ![OfficeHome listed on Enterprise applications page of Microsoft Entra admin center.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/ms-entra-admin-center-enterprise-applications-officehome.png)
7. Generate a token for the `MDCPP.All` scope against the resource "4765445b-32c6-49b0-83e6-1d93765276ca" \(the OfficeHome app\) signed in with the tenant admin account at [https://m365.cloud.microsoft/v2](https://m365.cloud.microsoft/v2).
