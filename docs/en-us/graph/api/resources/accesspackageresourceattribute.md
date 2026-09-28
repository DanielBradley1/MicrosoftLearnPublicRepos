<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattribute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# accessPackageResourceAttribute resource type

Namespace: microsoft.graph

An access package resource attribute defines a property that a user is required to have to be able to access an application. This structure is included in the **attributes** within an [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0) of a catalog. It applies to applications whose roles are specified in an access package in that catalog. When you [create a resourceRequest](https://learn.microsoft.com/en-us/graph/api/entitlementmanagement-post-resourcerequests?view=graph-rest-1.0) for the application, you can include attributes. If a user requests the access package including the application role, they must provide values for each attribute. If the request is approved, these attribute values are written in the user's directory object. The application can then [read the attribute of the user](https://learn.microsoft.com/en-us/graph/api/user-get?view=graph-rest-1.0).

In entitlement management, this object is configured in the **attributes** property of [accessPackageResource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresource?view=graph-rest-1.0).

For assignments to a user where the **destination** is an [accessPackageUserDirectoryAttributeStore](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageuserdirectoryattributestore?view=graph-rest-1.0) object type, then the attribute indicated by **name** must be a writable property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object. These writable properties are String types that are either built-in properties of the user or registered as [extension properties](https://learn.microsoft.com/en-us/graph/api/resources/extensionproperty?view=graph-rest-1.0) on the target **User** object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| destination | [accessPackageResourceAttributeDestination](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattributedestination?view=graph-rest-1.0) | Information about how to set the attribute, currently a [accessPackageUserDirectoryAttributeStore](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageuserdirectoryattributestore?view=graph-rest-1.0) type. |
| name | String | The name of the attribute in the end system. If the destination is `accessPackageUserDirectoryAttributeStore`, then a user property such as **jobTitle** or a directory schema extension for the user object type, such as `extension_2b676109c7c74ae2b41549205f1947ed_personalTitle`. |
| source | [accessPackageResourceAttributeSource](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattributesource?view=graph-rest-1.0) | Information about how to populate the attribute value when an **accessPackageAssignmentRequest** is being fulfilled, currently a [accessPackageResourceAttributeQuestion](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceattributequestion?view=graph-rest-1.0) type. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageResourceAttribute",
  "destination": {
    "@odata.type": "microsoft.graph.accessPackageResourceAttributeDestination"
  },
  "name": "String",
  "source": {
    "@odata.type": "microsoft.graph.accessPackageResourceAttributeSource"
  }
}
```
