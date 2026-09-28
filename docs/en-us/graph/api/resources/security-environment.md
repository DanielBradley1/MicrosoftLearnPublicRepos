<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# environment resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a cloud-native environment that can be selected within a specific [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) for security management. Environments include Azure subscriptions, AWS accounts, GCP projects, and other resources native to the cloud.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta)

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-zone-list-environments?view=graph-rest-beta) | [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) collection | Get all [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) objects associated with a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta) object. |
| [Create](https://learn.microsoft.com/en-us/graph/api/security-zone-post-environments?view=graph-rest-beta) | [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) | Create an [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object to attach it to a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta). |
| [Get](https://learn.microsoft.com/en-us/graph/api/security-environment-get?view=graph-rest-beta) | [microsoft.graph.security.environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) | Get a specific [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) associated with a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta). The **environment ID** must be URL-encoded. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/security-environment-delete?view=graph-rest-beta) | None | Delete an [environment](https://learn.microsoft.com/en-us/graph/api/resources/security-environment?view=graph-rest-beta) object by providing the **environment ID** to detach it from a [zone](https://learn.microsoft.com/en-us/graph/api/resources/security-zone?view=graph-rest-beta). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Environment identifier. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). Supports `$orderby` and `$filter` \(`eq`, `contains`\). For example, `$filter=contains(id, '123')`.  <br>  <br>For Azure subscriptions, use the `/subscriptions/{subscription-id}` format for the **id** property. For example, `/subscriptions/02687862-a843-4846-81f0-efe9ef244daa`. For other environment types, use the native identifier - for example, AWS account number \(`181994123251`\) or GCP project number \(`69483221284`\). |
| kind | microsoft.graph.security.environmentKind | Environment type. The possible values are: `azureSubscription`, `awsOrganization`, `awsAccount`, `gcpOrganization`, `gcpProject`, `dockersHubOrganization`, `devOpsConnection`, `azureDevOpsOrganization`, `gitHubOrganization`, `gitLabGroup`, `jFrogArtifactory`, `unknownFutureValue`.  <br>  <br>Supports `orderby` and `$filter` \(`eq`, `in`\). For example, `$filter=kind eq 'azureSubscription'` or `$filter=kind in ('azureSubscription', 'awsAccount')`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.environment",
  "id": "String (identifier)",
  "kind": "String"
}
```
