<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-protectdonotforwardaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# protectDoNotForwardAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Informs the application to apply **Do Not Forward** protection. **protectionDoNotForwardAction** might be returned by [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateapplication?view=graph-rest-beta) or [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/security-sensitivitylabel-evaluateclassificationresults?view=graph-rest-beta) if the resulting label has been configured to apply [Don't Forward protection](https://learn.microsoft.com/en-us/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails). The consuming application must use a client library to apply protection via Azure Information Protection.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.protectDoNotForwardAction"
}
```
