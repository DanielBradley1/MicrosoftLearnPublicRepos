<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/privacyprofile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# privacyProfile resource type

Namespace: microsoft.graph

Represents a [company's](https://learn.microsoft.com/en-us/graph/api/resources/organization?view=graph-rest-1.0) privacy profile, which includes a privacy statement URL and a contact person for questions regarding the privacy statement.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contactEmail | String | A valid smtp email address for the privacy statement contact. Not required. |
| statementUrl | String | A valid URL format that begins with http:// or https://. Maximum length is 255 characters. The URL that directs to the company's privacy statement. Not required. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "contactEmail": "string",
  "statementUrl": "string"
}
```
