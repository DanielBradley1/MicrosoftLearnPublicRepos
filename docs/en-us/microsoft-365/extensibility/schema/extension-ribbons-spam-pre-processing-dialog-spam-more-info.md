<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog-spam-more-info?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# extensionRibbonsSpamPreProcessingDialog.spamMoreInfo object

Configures a link to provide informational resources to a user. In the preprocessing dialog, the link appears below the text provided in `spamPreProcessingDialog.description`.

Properties that reference this object type:

- [root.extensions.ribbons.spamPreProcessingDialog.spamMoreInfo](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/extension-ribbons-spam-pre-processing-dialog?view=m365-app-1.30#spamMoreInfo-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "text": "{string}",
  "url": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Specifies the custom text and URL to provide informational resources to the users.",
  "properties": {
    "text": {
      "type": "string",
      "description": "Specifies display content of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
      "maxLength": 128
    },
    "url": {
      "type": "string",
      "description": "Specifies the URL of the hyperlink pointing to the site containing informational resources in the preprocessing dialog of a spam-reporting add-in.",
      "maxLength": 2048
    }
  },
  "required": [
    "text",
    "url"
  ]
}
```

## Properties

#### text

Specifies the link text for a URL that directs users to informational resources from the preprocessing dialog.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### text

Specifies the link text for a URL that directs users to informational resources from the preprocessing dialog.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 128.

**Supported values**  


#### url

Specifies the HTTPS URL of a site that contains informational resources.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


#### url

Specifies the HTTPS URL of a site that contains informational resources.

This property is localizable. For more information, see the [localization schema](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/loc-schema/root?view=m365-app-1.30).

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**
