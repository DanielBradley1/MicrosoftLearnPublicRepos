<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-serviceuseragent?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# serviceUserAgent resource type

Namespace: microsoft.graph.callRecords

Represents a service user agent of an endpoint in a call. Inherits from [userAgent](https://learn.microsoft.com/en-us/graph/api/resources/callrecords-useragent?view=graph-rest-1.0) type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationVersion | String | Identifies the version of application software used by this endpoint. |
| headerValue | String | User-agent header value reported by this endpoint. |
| role | microsoft.graph.callRecords.serviceRole | Identifies the role of the service used by this endpoint. The possible values are: `unknown`, `customBot`, `skypeForBusinessMicrosoftTeamsGateway`, `skypeForBusinessAudioVideoMcu`, `skypeForBusinessApplicationSharingMcu`, `skypeForBusinessCallQueues`, `skypeForBusinessAutoAttendant`, `mediationServer`, `mediationServerCloudConnectorEdition`, `exchangeUnifiedMessagingService`, `mediaController`, `conferencingAnnouncementService`, `conferencingAttendant`, `audioTeleconferencerController`, `skypeForBusinessUnifiedCommunicationApplicationPlatform`, `responseGroupServiceAnnouncementService`, `gateway`, `skypeTranslator`, `skypeForBusinessAttendant`, `responseGroupService`, `voicemail`, `unknownFutureValue`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "applicationVersion": "String",
  "headerValue": "String",
  "role": "String"
}
```
