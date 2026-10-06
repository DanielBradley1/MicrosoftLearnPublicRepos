<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer-contact-info?view=m365-app-prev -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# root.developer.contactInfo object

Your contact information that is used by customers to contact you through Teams chat or email. Customers may need extra information when evaluating your app or if they have any queries about your app when it doesn't work. Customers can contact you using Teams chat, so request your IT admins to [enable external communications](https://learn.microsoft.com/en-us/microsoftteams/communicate-with-users-from-other-organizations) in your organization. For more information, see [developer provided app and contact information](https://learn.microsoft.com/en-us/MicrosoftTeams/manage-apps#developer-provided-app-information-support-and-documentation).

Note

You must provide only one contact email address.

Properties that reference this object type:

- [root.developer.contactInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer?view=m365-app-prev#contactInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "defaultSupport": {
    "userEmailsForChatSupport": [
      "{string}"
    ],
    "emailsForEmailSupport": [
      "{string}"
    ]
  }
}
```

```json
{
  "type": "object",
  "description": "App developer contact information.",
  "properties": {
    "defaultSupport": {
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
  },
  "required": [
    "defaultSupport"
  ]
}
```

## Properties

#### defaultSupport

The default contact information for your app.

**Type**  
[defaultSupport](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-developer-contact-info-default-support?view=m365-app-prev)

**Required**  
✅

**Constraints**  


**Supported values**  


## Remarks

We recommend triaging your customer queries in a timely manner and route those internally within your organization, say to other functions to get the answers. It helps improve app adoption, builds developer trust, and increase revenue if you monetize the app.
