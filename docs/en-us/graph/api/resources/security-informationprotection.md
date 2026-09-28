<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# informationProtection resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes methods that you can use to get Microsoft Purview Information Protection labels and label policies.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/security-informationprotectionpolicysetting-get?view=graph-rest-beta) | [microsoft.graph.security.informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta) collection | Read the properties and relationships of an [informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta) object. |
| [List sensitivityLabels](https://learn.microsoft.com/en-us/graph/api/security-informationprotection-list-sensitivitylabels?view=graph-rest-beta) | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) collection | Get a list of [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) objects associated with a user or organization. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| labelPolicySettings | [microsoft.graph.security.informationProtectionPolicySetting](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionpolicysetting?view=graph-rest-beta) | Read the Microsoft Purview Information Protection policy settings for the user or organization. |
| sensitivityLabels | [microsoft.graph.security.sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta) collection | Read the Microsoft Purview Information Protection labels for the user or organization. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.informationProtection"
}
```
