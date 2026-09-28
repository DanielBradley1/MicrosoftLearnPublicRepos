<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-protectadhocaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-22 -->

# protectAdhocAction resource type

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Informs the application that ad hoc protection should be applied. The **protectAdhocAction** informs applications that the label should apply ad hoc protection. Ad hoc protection is defined at runtime by the user or application. The consuming application must use the Microsoft Purview Information Protection SDK to locally apply the protection to the file or data.

Inherits from [informationProtectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotectionaction?view=graph-rest-beta).

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.protectAdhocAction"
}
```
