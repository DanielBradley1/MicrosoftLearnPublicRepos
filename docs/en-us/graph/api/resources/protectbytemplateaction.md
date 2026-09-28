<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectbytemplateaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# protectByTemplateAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Informs the application that an Azure Information Protection protection template should be applied. **protectionByTemplateAction** may be returned by [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta) or [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) if the resulting label has been configured to apply protection. The consuming application must read the templateId from the result and then use a client library, such as the Microsoft Purview Information Protection SDK, to apply protection via Azure Information Protection.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| templateId | String | The GUID of the Azure Information Protection template to apply to the information. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "templateId": "String"
}
```
