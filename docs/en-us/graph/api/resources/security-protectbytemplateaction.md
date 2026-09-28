<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-protectbytemplateaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# protectByTemplateAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Informs the application that a protection template in Microsoft Purview Information Protection should be applied. **protectionByTemplateAction** might be returned by [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta) or [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) if the resulting label has been configured to apply protection. The consuming application must read the **templateId** from the result and then use a client library, such as the Microsoft Purview Information Protection SDK, to apply protection via Azure Information Protection.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| templateId | String | The unique identifier for a protection template in Microsoft Purview Information Protection to apply to the content. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.protectByTemplateAction",
  "templateId": "String"
}
```
