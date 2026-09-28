<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/informationprotectionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# informationProtectionAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

The **informationProtectionAction** is an abstract entity that is returned as the result of any of the information protection evaluation APIs. The object contains one or more of the following actions that instruct the application on how to apply, update, or remove the information protection label.

- [addContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/addcontentfooteraction?view=graph-rest-beta)
- [addContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/addcontentheaderaction?view=graph-rest-beta)
- [addWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/addwatermarkaction?view=graph-rest-beta)
- [applyLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/applylabelaction?view=graph-rest-beta)
- [customAction](https://learn.microsoft.com/en-us/graph/api/resources/customaction?view=graph-rest-beta)
- [justifyAction](https://learn.microsoft.com/en-us/graph/api/resources/justifyaction?view=graph-rest-beta)
- [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/metadataaction?view=graph-rest-beta)
- [protectAdhocAction](https://learn.microsoft.com/en-us/graph/api/resources/protectadhocaction?view=graph-rest-beta)
- [protectByTemplateAction](https://learn.microsoft.com/en-us/graph/api/resources/protectbytemplateaction?view=graph-rest-beta)
- [protectionDoNotForwardAction](https://learn.microsoft.com/en-us/graph/api/resources/protectdonotforwardaction?view=graph-rest-beta)
- [recommendLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/recommendlabelaction?view=graph-rest-beta)
- [removeContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/removecontentfooteraction?view=graph-rest-beta)
- [removeContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/removecontentheaderaction?view=graph-rest-beta)
- [removeProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/removeprotectionaction?view=graph-rest-beta)
- [removeWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/removewatermarkaction?view=graph-rest-beta)

## Properties

None

## JSON representation

The following JSON representation shows the resource type.

```json
{

}
```
