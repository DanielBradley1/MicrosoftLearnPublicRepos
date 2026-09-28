<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# informationProtectionPolicySetting resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings for a Microsoft Purview Information Protection label policy

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/security-informationprotectionpolicysetting-get?view=graph-rest-beta) | [microsoft.graph.security.informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta) | Read the properties and relationships of an [informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier for the policy. |
| isDowngradeJustificationRequired | Boolean | Exposes whether justification input is required on label downgrade. |
| isMandatory | Boolean | Exposes whether mandatory labeling is enabled. |
| moreInfoUrl | String | Exposes the more information URL that can be configured by the administrator. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| defaultLabel | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) | Represents the default label for an organization. If no label is selected, the default label is applied. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.informationProtectionPolicySetting",
  "id": "String (identifier)",
  "isDowngradeJustificationRequired": "Boolean",
  "isMandatory": "Boolean",
  "moreInfoUrl": "String"
}
```
