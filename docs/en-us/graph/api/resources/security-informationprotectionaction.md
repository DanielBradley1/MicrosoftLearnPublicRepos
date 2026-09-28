<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# informationProtectionAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes an abstract entity that is returned as the result of any of the information protection evaluation APIs. The object contains one or more of the following actions that instruct the application on how to apply, update, or remove the information protection label.

- [addContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addcontentfooteraction?view=graph-rest-beta)
- [addContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addcontentheaderaction?view=graph-rest-beta)
- [addWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/security-addwatermarkaction?view=graph-rest-beta)
- [applyLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/security-applylabelaction?view=graph-rest-beta)
- [customAction](https://learn.microsoft.com/en-us/graph/api/resources/security-customaction?view=graph-rest-beta)
- [justifyAction](https://learn.microsoft.com/en-us/graph/api/resources/security-justifyaction?view=graph-rest-beta)
- [metadataAction](https://learn.microsoft.com/en-us/graph/api/resources/security-metadataaction?view=graph-rest-beta)
- [protectAdhocAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectadhocaction?view=graph-rest-beta)
- [protectByTemplateAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectbytemplateaction?view=graph-rest-beta)
- [protectionDoNotForwardAction](https://learn.microsoft.com/en-us/graph/api/resources/security-protectdonotforwardaction?view=graph-rest-beta)
- [recommendLabelAction](https://learn.microsoft.com/en-us/graph/api/resources/security-recommendlabelaction?view=graph-rest-beta)
- [removeContentFooterAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removecontentfooteraction?view=graph-rest-beta)
- [removeContentHeaderAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removecontentheaderaction?view=graph-rest-beta)
- [removeProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removeprotectionaction?view=graph-rest-beta)
- [removeWatermarkAction](https://learn.microsoft.com/en-us/graph/api/resources/security-removewatermarkaction?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.informationProtectionAction"
}
```
