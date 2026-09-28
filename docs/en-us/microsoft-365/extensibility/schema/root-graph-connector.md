<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-graph-connector?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.graphConnector object

Specify the app's Graph connector configuration. If this is present, then [webApplicationInfo.id](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-web-application-info) must also be specified.

Properties that reference this object type:

- [root.graphConnector](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#graphConnector-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "notificationUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Specify the app\u0027s Graph connector configuration. If this is present then webApplicationInfo.id must also be specified.",
  "properties": {
    "notificationUrl": {
      "$ref": "#/definitions/anyHttpUrl",
      "description": "The url where Graph-connector notifications for the application should be sent."
    }
  },
  "required": [
    "notificationUrl"
  ],
  "additionalProperties": false
}
```

- [Syntax](#tabpanel_2_syntax)
- [Schema](#tabpanel_2_schema)

```json
{
  "notificationUrl": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Specify the app\u0027s Graph connector configuration. If this is present then webApplicationInfo.id must also be specified.",
  "properties": {
    "notificationUrl": {
      "$ref": "#/definitions/httpsUrl",
      "description": "The url where Graph-connector notifications for the application should be sent."
    }
  },
  "required": [
    "notificationUrl"
  ],
  "additionalProperties": false
}
```

## Properties

#### notificationUrl

The url where Graph-connector notifications for the application should be sent.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  
The string must start with `http://` or `https://`.
