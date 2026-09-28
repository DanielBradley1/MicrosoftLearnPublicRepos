<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-25 -->

# profileCardProperty resource type

Represents an attribute of a user on the Microsoft 365 profile card for an organization to surface in a shared, people experience.

The attribute can be an Microsoft Entra ID built-in attribute, such as **Alias** or **UserPrincipalName**, or it can be a custom attribute. For a custom attribute, an administrator can define an `en-us` default display name String and a set of alternative translations for the languages supported in their organization.

For more information about how to add properties to the profile card for an organization, see [Add or remove custom attributes on a profile card using the profile card API](https://learn.microsoft.com/en-us/graph/add-properties-profilecard).

Note

Profile card properties correspond to attributes in Microsoft Entra ID. Adding an attribute as a **profileCardProperty** to the **profileCardProperties** collection for an organization configures profile cards to display the attribute value. Deleting the **profileCardProperty** from the collection *doesn’t delete the attribute from Microsoft Entra ID*; it deletes the configuration so that profile cards no longer display the attribute value.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-list-profilecardproperties?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) collection | Get a collection of [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) resources for an organization. |
| [Create](https://learn.microsoft.com/en-us/graph/api/peopleadminsettings-post-profilecardproperties?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) | Create a new [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) for an organization. |
| [Get](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-get?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) | Retrieve the properties of a [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) entity. |
| [Update](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-update?view=graph-rest-1.0) | [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) | Update the properties of a [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) object, identified by its **directoryPropertyName** property. |
| [Delete](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-delete?view=graph-rest-1.0) | None | Delete the [profileCardProperty](https://learn.microsoft.com/en-us/graph/api/resources/profilecardproperty?view=graph-rest-1.0) object specified by its **directoryPropertyName** from the organization's profile card, and remove any localized customizations for that property. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| annotations | [profileCardAnnotation](https://learn.microsoft.com/en-us/graph/api/resources/profilecardannotation?view=graph-rest-1.0) collection | Allows an administrator to set a custom display label for the directory property and localize it for the users in their tenant. |
| directoryPropertyName | String | Identifies a **profileCardProperty** resource in [Get](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-get?view=graph-rest-1.0), [Update](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-update?view=graph-rest-1.0), or [Delete](https://learn.microsoft.com/en-us/graph/api/profilecardproperty-delete?view=graph-rest-1.0) operations. Allows an administrator to surface hidden Microsoft Entra ID properties on the Microsoft 365 profile card within their tenant. When present, the Microsoft Entra ID field referenced in this property is visible to all users in your tenant on the contact pane of the profile card. Allowed values for this field are: `UserPrincipalName`, `Fax`, `StreetAddress`, `PostalCode`, `StateOrProvince`, `Alias`, `CustomAttribute1`, `CustomAttribute2`, `CustomAttribute3`, `CustomAttribute4`, `CustomAttribute5`, `CustomAttribute6`, `CustomAttribute7`, `CustomAttribute8`, `CustomAttribute9`, `CustomAttribute10`, `CustomAttribute11`, `CustomAttribute12`, `CustomAttribute13`, `CustomAttribute14`, `CustomAttribute15`. |
| isVisible | Boolean | Indicates whether the given directory property should be shown on a user’s profile card. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "annotations": [{ "@odata.type": "microsoft.graph.profileCardAnnotation" }],
  "directoryPropertyName": "String",
  "isVisible": "Boolean"
}
```
