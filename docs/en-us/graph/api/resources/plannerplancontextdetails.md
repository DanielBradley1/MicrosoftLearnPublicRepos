<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontextdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerPlanContextDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The **plannerPlanContextDetails** resource contains additional information about a [plannerPlanContext](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontext?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customLinkText | String | Nullable. Specifies the text to use in a user experience to display a link the the associated [plannerPlanContext](https://learn.microsoft.com/en-us/graph/api/resources/plannerplancontext?view=graph-rest-beta). If null, applications should display the link with a custom text based on the **displayLinkType** property. |
| displayLinkType | plannerPlanContextType | Specifies how an application should display the link to the associated **plannerPlanContext**. Applications may choose to provide customized text, description, icons, or other experiences based on the type of the link. The possible values are: `teamsTab`, `sharePointPage`, `meetingNotes`, `loopPage`, `project`, `other`, `unknownFutureValue`. |
| url | String | URL of the user experience represented by the associated **plannerPlanContext**. |
| state | plannerContextState | Indicates the state of the associated **plannerPlanContext**. |

### plannerContextState values

| Value | Description |
| :--- | :--- |
| active | The context has no problems. |
| delinked | A formerly linked **plannerPlanContext** is no longer linked to the plan. |
| unknownFutureValue | Evolvable enumeration sentinel value. Do not use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "url": "string",
  "customLinkText": "string",
  "displayLinkType": "string",
  "state": "string"
}
```
