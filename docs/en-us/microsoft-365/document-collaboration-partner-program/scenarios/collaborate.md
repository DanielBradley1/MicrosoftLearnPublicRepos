<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/collaborate -->
<!-- Sitemap-Last-Modified: 2025-12-17 -->

# Integrate collaborate-live experiences in the Microsoft 365 Document Collaboration Partner Program

Meeting participants can interact and collaborate using Excel Live directly in your collaboration application. Meeting attendees can keep in sync with the presenter or navigate through the spreadsheet at their own pace. Participants with write access prior to joining the meeting can edit the spreadsheet during the session.

To learn more about the Excel Live experience currently available in Teams, see [Excel Live in Microsoft Teams meetings](https://support.microsoft.com/office/a5790e42-7f75-4859-8674-cc3d07c86ede).

![PowerPoint Live experience.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/excel-live-experience.png)

## Live experience: Collaborate as the presenter in a meeting

### Prerequisites

- The Presenter has chosen a OneDrive for Business or SharePoint file to present. Before sharing, ensure that attendees have access to view or edit the file as appropriate.
- The app must be able to obtain a valid user token to the OneDrive for Business or SharePoint resource.

  - If you use the [OneDrive File Picker](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration#recommendations), you can use the same token acquisition code here.

- The user has been signed in with a Microsoft 365 account.
- The file must be a supported Collaborate file type.

  - Excel: xlsx, xls, xlsb, ods

### Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

function launchPresenter(
    meetingId: string,
    userId: string,
    siteUrl: string,
    documentId: string
) {
    const fetchAccessTokenFunction = async (
        resourceUrl: string,
        claim?: string[]
    ) => {
        const scopes: string[] = [];
        if (claim && claim.length > 0) {
            claim.forEach((val) => {
                scopes.push(`${resourceUrl}/${val}`);
            });
        } else {
            scopes.push(resourceUrl);
        }

        // Get the access token to pass to MDCPP.
        const token = await getTokenImpl({ scopes });
        return token;
    };

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop",
    });

    Microsoft.startCollaboration({
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: documentId,
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4(),
        },
        container,
        fetchAccessToken: fetchAccessTokenFunction,
        meetingInfo: {
            id: meetingId,
        },
        userInfo: {
            userId: userId,
        },
    })
        .then((response: Microsoft.BootInfo) => {
            console.log(
                "StartCollaboration API success: {0}, {1}, {2}",
                response.isBootSuccess,
                meetingId,
                response.errorInfo
            );
            /**
             * Now send the meetingId, siteUrl, and documentId values to the attendee.
             * The attendee can use them to call the joinCollaboration() api to join the collaborate-live (Excel Live) session.
             */
        })
        .catch((err: any) => {
            console.log(err);
        });
}
```

## Live experience: Collaborate as an attendee in a meeting

### Prerequisites

- The presenter has called [startCollaboration](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk#@microsoft-document-collaboration-sdk-startcollaboration) using the specific `meetingId`, `siteUrl`, and `documentId`.
- The `meetingId`, `siteUrl`, and `documentId` have been sent to the attendee in the meeting.

### Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

/**
 * meetingId must be the same as the presenter's.
 * siteUrl and documentId must be the same as the presenter's.
 * userId: Attendee's userID.
 */
function launchAttendee(
    meetingId: string,
    userId: string,
    siteUrl: string,
    documentId: string
) {
    const fetchAccessTokenFunction = async (
        resourceUrl: string,
        claim?: string[]
    ) => {
        const scopes: string[] = [];
        if (claim && claim.length > 0) {
            claim.forEach((val) => {
                scopes.push(`${resourceUrl}/${val}`);
            });
        } else {
            scopes.push(resourceUrl);
        }

        // Get the access token to pass to MDCPP.
        const token = await getTokenImpl({ scopes });
        return token;
    };

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop",
    });

    Microsoft.joinCollaboration({
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: documentId,
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4(),
        },
        container,
        fetchAccessToken: fetchAccessTokenFunction,
        meetingInfo: {
            id: meetingId,
        },
        userInfo: {
            userId: userId,
        },
    })
        .then((response: Microsoft.BootInfo) => {
            console.log(
                "Attendee join success: {0}, {1}, {2}",
                response.isBootSuccess,
                meetingId,
                response.errorInfo
            );
        })
        .catch((err: any) => {
            console.log(err);
        });
}
```

## See also

- [Excel Live in Microsoft Teams meetings](https://support.microsoft.com/office/a5790e42-7f75-4859-8674-cc3d07c86ede)
