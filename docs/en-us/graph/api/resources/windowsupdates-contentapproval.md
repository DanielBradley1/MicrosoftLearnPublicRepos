<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-27 -->

# contentApproval resource type

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents content approval to be deployed according to a policy.

Inherits from [complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-list-compliancechanges-contentapproval?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) objects and their properties. |
| [Create](https://learn.microsoft.com/en-us/graph/api/windowsupdates-updatepolicy-post-compliancechanges-contentapproval?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) | Create a new [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object. |
| [Get](https://learn.microsoft.com/en-us/graph/api/windowsupdates-contentapproval-get?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) | Read the properties and relationships of a [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/windowsupdates-contentapproval-update?view=graph-rest-beta) | [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) | Update the properties of a [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/windowsupdates-contentapproval-delete?view=graph-rest-beta) | None | Delete a [microsoft.graph.windowsUpdates.contentApproval](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-contentapproval?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| content | [microsoft.graph.windowsUpdates.deployableContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployablecontent?view=graph-rest-beta) | Specifies what content to deploy. Deployable content should be provided as one of the following derived types: [microsoft.graph.windowsUpdates.catalogContent](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-catalogcontent?view=graph-rest-beta). |
| createdDateTime | DateTimeOffset | The date and time when a compliance change was created. Inherited from [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta). |
| deploymentSettings | [microsoft.graph.windowsUpdates.deploymentSettings](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deploymentsettings?view=graph-rest-beta) | Settings for governing how to deploy **content**. |
| id | String | The unique identifier for the compliance change. Returned by default. Not nullable. Read-only. Inherited from [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta). |
| isRevoked | Boolean | `True` indicates that a compliance change is revoked, preventing further application. Revoking a compliance change is a final action. Inherited from [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta). |
| revokedDateTime | DateTimeOffset | The date and time when the compliance change was revoked. Inherited from [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| deployments | [microsoft.graph.windowsUpdates.deployment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-deployment?view=graph-rest-beta) collection | Deployments created as a result of applying the approval. |
| updatePolicy | [microsoft.graph.windowsUpdates.updatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-updatepolicy?view=graph-rest-beta) | The policy this compliance change is a member of. Inherited from [microsoft.graph.windowsUpdates.complianceChange](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-compliancechange?view=graph-rest-beta). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.windowsUpdates.contentApproval",
  "content": {
    "@odata.type": "microsoft.graph.windowsUpdates.deployableContent"
  },
  "createdDateTime": "String (timestamp)",
  "deploymentSettings": {
    "@odata.type": "microsoft.graph.windowsUpdates.deploymentSettings"
  },
  "id": "String (identifier)",
  "isRevoked": "Boolean",
  "revokedDateTime": "String (timestamp)"
}
```
