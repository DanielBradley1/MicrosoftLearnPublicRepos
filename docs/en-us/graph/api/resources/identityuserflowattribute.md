<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityuserflowattribute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-22 -->

# identityUserFlowAttribute resource type

Namespace: microsoft.graph

Represents attributes that can be added to a user flow in Microsoft Entra External ID in workforce and external tenants, and in Azure AD B2C tenants.

Configuring user flow attributes in your tenant allows you to collect information about an external user during sign-up. You can choose to collect a built-in set of attribute; for example, Given Name, Surname, City, and Postal Code; or you can configure custom user flow attributes. Custom user flow attributes are an abstraction over [directory extensions](https://learn.microsoft.com/en-us/graph/extensibility-overview#directory-azure-ad-extensions).

[identityBuiltInUserFlowAttributes](https://learn.microsoft.com/en-us/graph/api/resources/identitybuiltinuserflowattribute?view=graph-rest-1.0) and [identityCustomUserFlowAttributes](https://learn.microsoft.com/en-us/graph/api/resources/identitycustomuserflowattribute?view=graph-rest-1.0) both inherit from this base type.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-list?view=graph-rest-1.0) | identityUserFlowAttributes collection | Retrieve all built-in and custom user flow attributes. |
| [Create](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-post?view=graph-rest-1.0) | identityUserFlowAttribute | Create a new custom user flow attribute. |
| [Get](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-get?view=graph-rest-1.0) | identityUserFlowAttribute | Retrieve properties of a user flow attribute. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-update?view=graph-rest-1.0) | None | Update a custom user flow attribute. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/identityuserflowattribute-delete?view=graph-rest-1.0) | None | Delete a custom user flow attribute. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dataType | identityUserFlowAttributeDataType | The data type of the user flow attribute. Can't be modified after the custom user flow attribute is created. The supported values for **dataType** are: `string` , `boolean` , `int64` , `stringCollection` , `dateTime`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| displayName | String | The display name of the user flow attribute.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| description | String | The description of the user flow attribute that's shown to the user at the time of sign up. |
| id | String | The identifier of the user flow attribute. Read-only.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |
| userFlowAttributeType | identityUserFlowAttributeType | The type of the user flow attribute. Read-only. Depending on the type of attribute, the values for this property are `builtIn`, `custom`, `required`, `unknownFutureValue`.  <br>  <br>Supports `$filter` \(`eq`, `ne`\). |

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "@odata.type": "#microsoft.graph.identityUserFlowAttribute",
    "id": "String (identifier)",
    "displayName": "String",
    "description": "String",
    "userFlowAttributeType": "String",
    "dataType": "String"
}
```
