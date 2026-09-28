<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectadhocaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# protectAdhocAction resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Caution

The Information Protection labels API is deprecated and will stop returning data on January 1, 2023. Please use the new [informationProtection](https://learn.microsoft.com/en-us/graph/api/resources/security-informationprotection?view=graph-rest-beta&preserve-view=true), [sensitivityLabel](https://learn.microsoft.com/en-us/graph/api/resources/security-sensitivitylabel?view=graph-rest-beta&preserve-view=true), and associated resources.

Informs the application that ad hoc protection should be applied. The **protectAdhocAction** informs that applications that the label should apply ad hoc protection. Ad hoc protection is defined at runtime by the user or application. The consuming application must use the Microsoft Purview Information Protection SDK to locally apply the protection to the file or data.

## Properties

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  
}
```
