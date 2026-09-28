<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-entitydefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# entityDefinition resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Defines a single entity reference included in [createAlertInput](https://learn.microsoft.com/en-us/graph/api/resources/security-createalertinput?view=graph-rest-beta) for alert creation. Each entity definition associates an entity \(such as a user, device, or IP address\) with the alert being created.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| entityIdentifier | String | The identifier kind for the selected entity type, such as `userPrincipalName`, `deviceId`, or `address`. |
| entityType | [microsoft.graph.security.manualAlertEntityType](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#manualalertentitytype-values) | The type of entity to associate with the alert. The possible values are: `user`, `device`, `file`, `ip`, `url`, `cloudApplication`, `mailbox`, `securityGroup`, `azureResource`, `amazonResource`, `googleCloudResource`, `oAuthApplication`, `emailMessage`, `emailCluster`, `process`, `registryKey`, `registryValue`, `unknownFutureValue`. |
| identifierValue | String | The value for the selected entity identifier. |
| role | [microsoft.graph.security.entityDefinitionInputRole](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#entitydefinitioninputrole-values) | Whether the entity is an impacted asset or related evidence. The possible values are: `impacted`, `related`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.entityDefinition",
  "entityIdentifier": "String",
  "entityType": "String",
  "identifierValue": "String",
  "role": "String"
}
```
