<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/office-for-the-web -->
<!-- Sitemap-Last-Modified: 2025-04-30 -->

# Integrate coauthoring using Office for the Web in the Microsoft 365 Document Collaboration Partner Program

Outside of a meeting experience, users can collaborate and edit Excel, PowerPoint, and Word documents from SharePoint and OneDrive for Business directly in your collaboration application.

To learn more about this experience in Teams, see [Edit a file in Microsoft Teams](https://support.microsoft.com/office/257a5e88-205a-4fb5-bbf1-c78c3e64de86).

![Office for the Web experience.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/office-for-the-web-experience.png)

## Prerequisites

- The user must use the appId that was provided to the MDCPP program administrator.
- The app must be able to obtain a valid user token to the OneDrive for Business or SharePoint resource.

  - If you use the [OneDrive File Picker](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration#recommendations), you can use the same token acquisition code here.

- The user has been signed in with a Microsoft 365 account.
- The file must be a supported file type.

  - Excel: xlsx, xls, xlsb, ods
  - PowerPoint: pptx, ppt, ppsx, potx, potm, pptm, ppsm, pps, pot, odp
  - Word: docx, doc, docm, dotm, dotx, odt

## Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

function launchDocument(
    siteUrl: string,
    documentId: string)
{
    Microsoft.initializeDocument({
        hostName: "Contoso",
        hostClientType: "web"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.launch({
        documentInfo: {
          documentIdentifier: {
            siteUrl: siteUrl,
            sourceDoc: documentId
          }
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
        console.log('Launch API finished {0}, {1}', response.isBootSuccess, response.errorInfo );
    })
    .catch((e : any) => {
        console.log(e);
    });
}
```

You can alternatively launch the document by passing in its shareUrl. The beginning of your function could look like the following:

```typescript
function launchDocument(
    shareUrl: string)
{
    Microsoft.initializeDocument({
        hostName: "Contoso",
        hostClientType: "web"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.launch({
        documentInfo: {
          shareUrl: shareUrl
        },
        sessionInfo: {
  ...
```
