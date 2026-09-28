<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectdonotforwardaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-04-04 -->

# protectDoNotForwardAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Informs the application to apply Don't Forward protection. **protectionDoNotForwardAction** may be returned by [evaluateApplication](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateapplication?view=graph-rest-beta) or [evaluateClassificationResults](https://learn.microsoft.com/en-us/graph/api/informationprotectionlabel-evaluateclassificationresults?view=graph-rest-beta) if the resulting label has been configured to apply [Don't Forward protection](https://learn.microsoft.com/en-us/azure/information-protection/configure-usage-rights#do-not-forward-option-for-emails). The consuming application must use a client library to apply protection via Azure Information Protection.

## Properties

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  
}
```
