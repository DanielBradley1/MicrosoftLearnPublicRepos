<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/scenarios/present -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Integrate present-live experiences in the Microsoft 365 Document Collaboration Partner Program

Meeting participants can interact and collaborate with PowerPoint Live directly in your collaboration application. Meeting attendees can keep in sync with the presenter or navigate through the presentation at their own pace.

To learn more about the PowerPoint Live experience currently available in Teams, see [Present from PowerPoint Live in Microsoft Teams](https://support.microsoft.com/office/28b20e74-7165-499c-9bd4-0ad975d448ad).

![PowerPoint Live experience.](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/images/powerpoint-live-experience.jpeg)

For a sample app demonstrating the experience, see [Present-live Sample Integration App](https://github.com/microsoft/MDCPP-samples/tree/main/present-live-integration-app-sample).

## Live experience: Present in a meeting

### Prerequisites

- The Presenter has chosen a OneDrive for Business or SharePoint file to present.
- The app must be able to obtain a valid user token to the OneDrive for Business or SharePoint resource.

  - If you use the [OneDrive File Picker](https://learn.microsoft.com/en-us/microsoft-365/document-collaboration-partner-program/onboard/set-up-integration#recommendations), you can use the same token acquisition code here.

- The user has been signed in with a Microsoft 365 account.
- The file must be a supported Present file type.

  - PowerPoint: pptx, ppsx, potx, pptm, ppsm

### Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            }
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl( { scopes } );
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);
    })
    .catch((e : any) => {
        console.log(e);
    })
}
```

## Live experience: Join as an attendee in a meeting

### Prerequisites

- The Presenter has called [startPresentation](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk#@microsoft-document-collaboration-sdk-startpresentation) and received a `joinInfo` string.
- The `joinInfo` string has been sent to an attendee in the meeting.

### Example

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

## Live experience: Manage switching roles

In Teams, an attendee can take control of what's being presented by selecting **Request control**. If the presenter accepts the request, the attendee becomes the presenter and now controls slide navigation, etc. To learn more about this feature, see the "Take Control" section of [Present content in Microsoft Teams meetings](https://support.microsoft.com/office/fcc2bf59-aecd-4481-8f99-ce55dd836ce8).

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. Keep track of which meeting participant is the Presenter.
2. If an attendee indicates that they want to take control of the presentation \(e.g., via a button in your application's attendee view\) and the presenter approves the request \(e.g., via a notification in your application's presenter view\), first change the current presenter's role to attendee by passing in `switchRole({role: "attendee"})` when you call [BootInfo.powerPointMeetingActions](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/document-collaboration-sdk/bootinfo#@microsoft-document-collaboration-sdk-bootinfo-powerpointmeetingactions). This is to avoid having two presenters at the same time.
3. Next, update the role of the attendee who requested control by passing in `switchRole({role: "presenter"})`.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_1_presenter)
- [Attendee](#tabpanel_1_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onSwitchRole } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl( { scopes } );
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);
        onSwitchRole(({role}=>response.powerPointMeetingActions.switchRole({role})));

    })
    .catch((e : any) => {
        console.log(e);
    })
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onSwitchRole } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);
        onSwitchRole(({role}=>response.powerPointMeetingActions.switchRole({role})));
    })
    .catch((err: any) => {
        console.log(err);
    })
}
```

## Live experience: Manage private viewing

In Teams, attendees can view slides at their own pace or sync to the presenter's view if private viewing is enabled. The presenter can turn it off or on by toggling **Private view** in the meeting controls. To learn more about this feature, see the "Audience view" section of [Share slides in Microsoft Teams meetings with PowerPoint Live](https://support.microsoft.com/office/fc5a5394-2159-419c-bc59-1f64c1f4e470).

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. Keep track of which meeting participant is the Presenter.
2. If the presenter indicates that they want to turn off private viewing \(e.g., via a button in your application's presenter view\), pass in `setPrivateViewing({isEnabled: false})` for all participants \(presenter and attendees\) when you call [BootInfo.powerPointMeetingActions](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/document-collaboration-sdk/bootinfo#@microsoft-document-collaboration-sdk-bootinfo-powerpointmeetingactions).
3. If the presenter later indicates that they want to turn private viewing on again, pass in `setPrivateViewing({isEnabled: true});` for all participants.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_2_presenter)
- [Attendee](#tabpanel_2_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onSetPrivateViewing } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            }
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);
        onSetPrivateViewing(({isEnabled})=>response.powerPointMeetingActions.setPrivateViewing({isEnabled}));

    })
    .catch((e : any) => {
        console.log(e);
    })
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onSetPrivateViewing } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);
        onSetPrivateViewing(({isEnabled})=>response.powerPointMeetingActions.setPrivateViewing({isEnabled}));
    })
    .catch((err: any) => {
        console.log(err);
    })
}
```

## Live experience: Manage slide navigation synchronization

In PowerPoint Live, when a presenter navigates to a different slide or triggers animations, all attendees automatically see the same slide and animation state in real time. This ensures everyone stays synchronized during the presentation. To learn more about this feature, see the "Navigate through the slides" section of [Share slides in Microsoft Teams meetings with PowerPoint Live](https://support.microsoft.com/office/fc5a5394-2159-419c-bc59-1f64c1f4e470).

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. The presenter subscribes to slide change events to detect when navigation occurs.
2. When the presenter navigates slides, broadcast the slide change data to all attendees through your coordination service.
3. Attendees receive slide change events and apply them to navigate to the same slide and animation state.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_3_presenter)
- [Attendee](#tabpanel_3_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { broadcastSlideChange } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);

        // Subscribe to slide changes and broadcast them to attendees.
        if (response.powerPointMeetingActions?.subscribeToSlideChanges) {
            const unsubscribe = response.powerPointMeetingActions.subscribeToSlideChanges((slideData: Microsoft.SlideChangeData) => {
                // Broadcast slide change to all attendees via your coordination service.
                broadcastSlideChange(slideData);
                console.log('Broadcasting slide change:', {
                    slideIndex: slideData.slideIndex,
                    timeLineMappings: slideData.timeLineMappings,
                    metadata: slideData.metadata
                });
            });

            // Store unsubscribe function if you need to clean up later.
            // window.slideChangeUnsubscribe = unsubscribe;
        }
    })
    .catch((e: any) => {
        console.log(e);
    });
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onSlideChange } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);

        // Set up slide change handler to receive updates from presenter.
        if (response.powerPointMeetingActions?.navigateToSlide) {
            onSlideChange((slideData: Microsoft.SlideChangeData) => {
                // Apply slide change received from presenter.
                response.powerPointMeetingActions.navigateToSlide(slideData);
                console.log('Navigating to slide:', {
                    slideIndex: slideData.slideIndex,
                    timeLineMappings: slideData.timeLineMappings,
                    metadata: slideData.metadata
                });
            });
        }
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

## Live experience: Manage media event synchronization

In PowerPoint Live, when a presenter plays, pauses, seeks, or mutes media content \(videos/audio\), all attendees automatically see the same media state in real time. This ensures synchronized media playback across all participants during the presentation.

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. The presenter subscribes to media event changes to detect when media controls are used.
2. When the presenter controls media playback, broadcast the media event data to all attendees through your coordination service.
3. Attendees receive media events and apply them to synchronize their media playback state.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_4_presenter)
- [Attendee](#tabpanel_4_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { broadcastMediaEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);

        // Subscribe to media events and broadcast them to attendees.
        if (response.powerPointMeetingActions?.subscribeToMediaChangedEvent) {
            const unsubscribe = response.powerPointMeetingActions.subscribeToMediaChangedEvent((mediaData: Microsoft.MediaEventData) => {
                // Broadcast media event to all attendees via your coordination service.
                broadcastMediaEvent(mediaData);
                console.log('Broadcasting media event:', {
                    mediaPlayerName: mediaData.mediaPlayerName,
                    mediaEventType: mediaData.mediaEventType,
                    mediaPlayerState: mediaData.mediaPlayerState,
                    mediaPosition: mediaData.mediaPosition,
                    mediaMuted: mediaData.mediaMuted,
                    metadata: mediaData.metadata
                });
            });

            // Store unsubscribe function if you need to clean up later.
            // window.mediaEventUnsubscribe = unsubscribe;
        }
    })
    .catch((e: any) => {
        console.log(e);
    });
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onMediaEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);

        // Set up media event handler to receive updates from presenter.
        if (response.powerPointMeetingActions?.mediaEventAction) {
            onMediaEvent((mediaData: Microsoft.MediaEventData) => {
                // Apply media event received from presenter.
                response.powerPointMeetingActions.mediaEventAction(mediaData);
                console.log('Applying media event:', {
                    mediaPlayerName: mediaData.mediaPlayerName,
                    mediaEventType: mediaData.mediaEventType,
                    mediaPlayerState: mediaData.mediaPlayerState,
                    mediaPosition: mediaData.mediaPosition,
                    mediaMuted: mediaData.mediaMuted,
                    metadata: mediaData.metadata
                });
            });
        }
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

## Live experience: Manage annotation synchronization

In PowerPoint Live, when a presenter or attendee draws ink annotations, uses a laser pointer, or moves their cursor on a PowerPoint slide, all participants see these annotations in real time. This includes drawing strokes, erasing content, and laser pointer interactions that enhance presentation engagement. To learn more about this feature, see [Laser point or draw on PowerPoint slides in Microsoft Teams meetings](https://support.microsoft.com/en-us/office/laser-point-or-draw-on-powerpoint-slides-in-microsoft-teams-meetings-8eebe227-6d28-4b05-8156-f7bb63da4de4).

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. The presenter subscribes to annotation event changes to detect when drawing, erasing, or laser pointer actions occur.
2. When annotation activities happen, broadcast the annotation event data to all participants through your coordination service.
3. Participants receive annotation events and apply them to synchronize their annotation state.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_5_presenter)
- [Attendee](#tabpanel_5_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { broadcastAnnotationEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);

        // Subscribe to annotation events and broadcast them to attendees.
        if (response.powerPointMeetingActions?.subscribeToAnnotationChangedEvent) {
            const unsubscribe = response.powerPointMeetingActions.subscribeToAnnotationChangedEvent((annotationData: Microsoft.AnnotationData) => {
                // Broadcast annotation event to all attendees via your coordination service.
                broadcastAnnotationEvent(annotationData);
                console.log('Broadcasting annotation event:', {
                    eventType: annotationData.eventType,
                    eventJson: annotationData.eventJson,
                    strokeID: annotationData.strokeID,
                    slideID: annotationData.slideID,
                    metadata: annotationData.metadata
                });
            });

            // Store unsubscribe function if you need to clean up later.
            // window.annotationEventUnsubscribe = unsubscribe;
        }
    })
    .catch((e: any) => {
        console.log(e);
    });
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onAnnotationEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);

        // Set up annotation event handler to receive updates from presenter.
        if (response.powerPointMeetingActions?.annotationEventAction) {
            onAnnotationEvent((annotationData: Microsoft.AnnotationData) => {
                // Apply annotation event received from presenter.
                response.powerPointMeetingActions.annotationEventAction(annotationData);
                console.log('Applying annotation event:', {
                    eventType: annotationData.eventType,
                    eventJson: annotationData.eventJson,
                    strokeID: annotationData.strokeID,
                    slideID: annotationData.slideID,
                    metadata: annotationData.metadata
                });
            });
        }
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

## Live experience: Manage optical zoom synchronization

In PowerPoint Live, when a presenter zooms into a specific area of a PowerPoint slide, all attendees automatically see the same zoomed view with the same center point and zoom level in real time. This ensures everyone focuses on the same content during detailed discussions.

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. The presenter subscribes to optical zoom event changes to detect when zoom level or center point changes occur.
2. When the presenter changes zoom settings, broadcast the optical zoom data to all attendees through your coordination service.
3. Attendees receive zoom events and apply them to synchronize their zoom state and view.

The following is an example implementation based on the code samples earlier in this article. `@contoso/meetingCoordinationService` generically represents a service you implemented for your application to manage interactions in the meeting.

Select the tab for the role you'd like to view.

- [Presenter](#tabpanel_6_presenter)
- [Attendee](#tabpanel_6_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { broadcastOpticalZoomEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            },
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // The joinInfo string can now be used by the host to initialize attendee sessions.
        console.log('Present API finished {0}, {1}, {2}, {3}', response.isBootSuccess, response.joinInfo, meetingId, response.errorInfo);

        // Subscribe to optical zoom events and broadcast them to attendees.
        if (response.powerPointMeetingActions?.subscribeToOpticalZoomChangedEvent) {
            const unsubscribe = response.powerPointMeetingActions.subscribeToOpticalZoomChangedEvent((opticalZoomData: Microsoft.OpticalZoomData) => {
                // Broadcast optical zoom event to all attendees via your coordination service.
                broadcastOpticalZoomEvent(opticalZoomData);
                console.log('Broadcasting optical zoom event:', {
                    zoomLevel: opticalZoomData.opticalZoomState.zoomLevel,
                    centerX: opticalZoomData.opticalZoomState.canvasCenterSlidePointPercent.x,
                    centerY: opticalZoomData.opticalZoomState.canvasCenterSlidePointPercent.y,
                    shouldAnimate: opticalZoomData.shouldAnimate,
                    metadata: opticalZoomData.metadata
                });
            });

            // Store unsubscribe function if you need to clean up later.
            // window.opticalZoomEventUnsubscribe = unsubscribe;
        }
    })
    .catch((e: any) => {
        console.log(e);
    });
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getMeetingCoordinationService } from "@contoso/meetingCoordinationService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    const { onOpticalZoomEvent } = getMeetingCoordinationService({
        meetingId,
        participantId
    });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        console.log('Attendee join success: {0}, {1}, {2}', response.isBootSuccess, meetingId, response.errorInfo);

        // Set up optical zoom event handler to receive updates from presenter.
        if (response.powerPointMeetingActions?.opticalZoomEventAction) {
            onOpticalZoomEvent((opticalZoomData: Microsoft.OpticalZoomData) => {
                // Apply optical zoom event received from presenter.
                response.powerPointMeetingActions.opticalZoomEventAction(opticalZoomData);
                console.log('Applying optical zoom event:', {
                    zoomLevel: opticalZoomData.opticalZoomState.zoomLevel,
                    centerX: opticalZoomData.opticalZoomState.canvasCenterSlidePointPercent.x,
                    centerY: opticalZoomData.opticalZoomState.canvasCenterSlidePointPercent.y,
                    shouldAnimate: opticalZoomData.shouldAnimate,
                    metadata: opticalZoomData.metadata
                });
            });
        }
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

## Live experience: Enable Copilot Explainer

Copilot Explainer exposes a captured screenshot of the region a participant selects in the local PowerPoint Live viewer. The MDCPP raises a selection event that carries a Base64-encoded image of that region to your host application. Your application is then responsible for all downstream processing. For example, running OCR, calling a vision model, or displaying an explanation in your own UI.

Keep the following characteristics in mind:

- **The event is local to the current participant.** Selection events are raised only in the viewer where the selection happens. They are **not** broadcast to other participants in the meeting, and no Microsoft AI service processes the image.
- **You bring your own intelligence.** The MDCPP hands you the pixels; recognition, explanation, and rendering are implemented entirely by your application using your own \(non-Microsoft\) resources.
- **Any attendee can trigger it.** Because the event is emitted by the local viewer, attendees can capture a selection during a live presentation.

### Prerequisites

- The participant is in an active PowerPoint Live session. That is, the presenter has called [startPresentation](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk#@microsoft-document-collaboration-sdk-startpresentation) and attendees have joined with [joinPresentation](https://learn.microsoft.com/en-us/javascript/api/@microsoft/document-collaboration-sdk#@microsoft-document-collaboration-sdk-joinpresentation).
- The boot call resolved and returned a [BootInfo](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/document-collaboration-sdk/bootinfo) object with a populated `powerPointMeetingActions`.
- Your application has an AI or content-recognition pipeline \(for example, OCR or a vision model\) ready to receive a Base64-encoded image.

### Subscribe to selection events

Call `subscribeToSelectionChangedEvent` on [BootInfo.powerPointMeetingActions](https://learn.microsoft.com/en-us/javascript/api/%40microsoft/document-collaboration-sdk/bootinfo#@microsoft-document-collaboration-sdk-bootinfo-powerpointmeetingactions) to start receiving selection events. The method takes a callback that's invoked each time the local viewer captures a selection and returns an unsubscribe function that you should call when you tear down the session.

Through the MDCPP, you can implement this experience in your collaboration application by using the following steps.

1. Keep a reference to the `powerPointMeetingActions` object returned in `BootInfo`.
2. Subscribe to selection events by calling `subscribeToSelectionChangedEvent` and passing a callback.
3. In the callback, forward `selectionImage` to your AI or content-recognition pipeline and render the result in your own UI.
4. Store the returned unsubscribe function and call it when the participant leaves the session or the feature is disabled.

The following is an example implementation based on the present-live code samples. `@contoso/copilotExplainerService` generically represents a service you implemented for your application to run AI processing on the captured image.

Select the tab for the role you'd like to view. Because selection events are local to each viewer, the subscription is set up the same way for presenters and attendees.

- [Presenter](#tabpanel_7_presenter)
- [Attendee](#tabpanel_7_attendee)

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getCopilotExplainerService } from "@contoso/copilotExplainerService";

function launchPresenter(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    siteUrl: string,
    itemId: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    // Your own AI pipeline (OCR, vision model, etc.).
    const { explainImage } = getCopilotExplainerService({ meetingId, participantId });

    Microsoft.startPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        documentInfo: {
            documentIdentifier: {
                siteUrl: siteUrl,
                sourceDoc: itemId
            }
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        fetchAccessToken: async (resourceUrl: string, claim?: string[]) => {
            const scopes: string[] = [];
            if (claim && claim.length > 0) {
                claim.forEach((val) => {
                    scopes.push(`${resourceUrl}/${val}`);
                });
            } else {
                scopes.push(resourceUrl);
            }
            const token = await getTokenImpl({ scopes });
            return token;
        }
    })
    .then((response: Microsoft.BootInfo) => {
        // Subscribe to Copilot Explainer selection events raised by the local viewer.
        const unsubscribe = response.powerPointMeetingActions.subscribeToSelectionChangedEvent(
            (selection: Microsoft.SelectionData) => {
                // selection.selectionImage is a Base64-encoded image of the selected region.
                explainImage(selection.selectionImage, selection.metadata);
            }
        );

        // Call unsubscribe() when the participant leaves the session.
    })
    .catch((e: any) => {
        console.log(e);
    });
}
```

```typescript
import * as Microsoft from "@microsoft/document-collaboration-sdk";
import uuidv4 from "uuid/v4";
import { getCopilotExplainerService } from "@contoso/copilotExplainerService";

function launchAttendee(
    meetingId: string,
    userId: string,
    participantId: string,
    userDisplayName: string,
    joinInfo: string)
{
    Microsoft.initializeMeeting({
        hostName: "Contoso",
        hostClientType: "Desktop"
    });

    const container = window.document.createElement("div");
    container.style.height = "100%";
    window.document.body.appendChild(container);

    // Your own AI pipeline (OCR, vision model, etc.).
    const { explainImage } = getCopilotExplainerService({ meetingId, participantId });

    Microsoft.joinPresentation({
        meetingInfo: {
            id: meetingId
        },
        userInfo: {
            userId: userId,
            participantId: participantId,
            displayName: userDisplayName
        },
        sessionInfo: {
            // Use your preferred GUID generator package to get a unique ID for logging.
            hostCorrelationId: uuidv4()
        },
        container,
        joinInfo
    })
    .then((response: Microsoft.BootInfo) => {
        // Subscribe to Copilot Explainer selection events raised by the local viewer.
        const unsubscribe = response.powerPointMeetingActions.subscribeToSelectionChangedEvent(
            (selection: Microsoft.SelectionData) => {
                // selection.selectionImage is a Base64-encoded image of the selected region.
                explainImage(selection.selectionImage, selection.metadata);
            }
        );

        // Call unsubscribe() when the attendee leaves the session.
    })
    .catch((err: any) => {
        console.log(err);
    });
}
```

### Handle the captured image

The `selectionImage` string is a Base64-encoded image. Your application owns everything that happens after the event fires. A typical flow is:

1. Send the image to your content-recognition service \(for example, an OCR engine to extract text, or a vision model\) to describe or explain the content.
2. Render the result in your own UI \(a side panel, tooltip, or dialog\), keeping it local to the participant who made the selection.

Because the image never leaves your infrastructure and isn't shared with other participants or with Microsoft, your application is fully responsible for the privacy, compliance, and data-handling requirements of the captured content.

## See also

- [Present-live Sample Integration App](https://github.com/microsoft/MDCPP-samples/tree/main/present-live-integration-app-sample)
- [Present from PowerPoint Live in Microsoft Teams](https://support.microsoft.com/office/28b20e74-7165-499c-9bd4-0ad975d448ad)
