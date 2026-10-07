<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer-contact-info-default-support?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-06-29 -->

# root.developer.contactInfo.defaultSupport object

The default contact information for your app.

Properties that reference this object type:

- [root.developer.contactInfo.defaultSupport](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer-contact-info?view=m365-app-prev#defaultSupport-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "userEmailsForChatSupport": [
    "{string}"
  ],
  "emailsForEmailSupport": [
    "{string}"
  ]
}
```

```json
{
  "type": "object",
  "description": "Support configuration.",
  "properties": {
    "userEmailsForChatSupport": {
      "type": "array",
      "description": "User email for chat support contacts.",
      "maxItems": 10,
      "minItems": 1,
      "items": {
        "type": "string",
        "maxLength": 80
      }
    },
    "emailsForEmailSupport": {
      "type": "array",
      "description": "Email address for email support.",
      "maxItems": 1,
      "minItems": 1,
      "items": {
        "type": "string",
        "maxLength": 80
      }
    }
  },
  "required": [
    "emailsForEmailSupport",
    "userEmailsForChatSupport"
  ]
}
```

## Properties

#### userEmailsForChatSupport

Mail address to receive customer queries using Teams chat. While the app manifest allows up to 10 email addresses, Teams uses only the first email address to let IT admins communicate with you. The object is an array with all elements of the type string.

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Maximum string length: 80. Minimum array items: 1. Maximum array items: 10.

**Supported values**  


#### emailsForEmailSupport

Contact email for customer inquiry. The object is an array with all elements of the type string.

**Type**  
Array of string

**Required**  
✅

**Constraints**  
Maximum string length: 80. Minimum array items: 1. Maximum array items: 1.

**Supported values**
