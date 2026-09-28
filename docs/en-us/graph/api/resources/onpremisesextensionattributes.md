<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisesextensionattributes?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-10-03 -->

# onPremisesExtensionAttributes resource type

Namespace: microsoft.graph

The return type of the **onPremisesExtensionAttributes** property of the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) object and **extensionAttributes** property of the [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) object. Returns 15 custom extension attribute properties. Each attribute can store up to 1024 characters.

On the [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0) entity and for an **onPremisesSyncEnabled** user, the source of authority for this set of properties is the on-premises Active Directory that is synchronized to Microsoft Entra ID, and is read-only. For a cloud-only user \(where **onPremisesSyncEnabled** is `false` or `null`\), these properties can be set during [creation](https://learn.microsoft.com/en-us/graph/api/user-post-users?view=graph-rest-1.0) or [update](https://learn.microsoft.com/en-us/graph/api/user-update?view=graph-rest-1.0). If a cloud-only user was previously synced from on-premises Active Directory, these properties can't be managed via the Microsoft Graph API. Instead, they can be managed through the Exchange Admin Center or the Exchange Online V2 module in PowerShell.

The **extensionAttributes** property of the [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) entity is managed only in Microsoft Entra ID during device [creation](https://learn.microsoft.com/en-us/graph/api/device-post-devices?view=graph-rest-1.0) or [update](https://learn.microsoft.com/en-us/graph/api/device-update?view=graph-rest-1.0).

> **Note:** These extension attributes are also known as Exchange custom attributes 1-15.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| extensionAttribute1 | String | First customizable extension attribute. |
| extensionAttribute2 | String | Second customizable extension attribute. |
| extensionAttribute3 | String | Third customizable extension attribute. |
| extensionAttribute4 | String | Fourth customizable extension attribute. |
| extensionAttribute5 | String | Fifth customizable extension attribute. |
| extensionAttribute6 | String | Sixth customizable extension attribute. |
| extensionAttribute7 | String | Seventh customizable extension attribute. |
| extensionAttribute8 | String | Eighth customizable extension attribute. |
| extensionAttribute9 | String | Ninth customizable extension attribute. |
| extensionAttribute10 | String | Tenth customizable extension attribute. |
| extensionAttribute11 | String | Eleventh customizable extension attribute. |
| extensionAttribute12 | String | Twelfth customizable extension attribute. |
| extensionAttribute13 | String | Thirteenth customizable extension attribute. |
| extensionAttribute14 | String | Fourteenth customizable extension attribute. |
| extensionAttribute15 | String | Fifteenth customizable extension attribute. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
      "extensionAttribute1": "string",
      "extensionAttribute2": "string",
      "extensionAttribute3": "string",
      "extensionAttribute4": "string",
      "extensionAttribute5": "string",
      "extensionAttribute6": "string",
      "extensionAttribute7": "string",
      "extensionAttribute8": "string",
      "extensionAttribute9": "string",
      "extensionAttribute10": "string",
      "extensionAttribute11": "string",
      "extensionAttribute12": "string",
      "extensionAttribute13": "string",
      "extensionAttribute14": "string",
      "extensionAttribute15": "string"
  }
```
