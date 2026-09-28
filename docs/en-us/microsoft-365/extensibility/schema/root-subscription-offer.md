<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root-subscription-offer?view=m365-app-1.30 -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# root.subscriptionOffer object

Specifies the SaaS offer associated with your app.

Properties that reference this object type:

- [root.subscriptionOffer](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema/root?view=m365-app-1.30#subscriptionOffer-property)

## Syntax

- [Syntax](#tabpanel_1_syntax)
- [Schema](#tabpanel_1_schema)

```json
{
  "offerId": "{string}"
}
```

```json
{
  "type": "object",
  "description": "Subscription offer associated with this app.",
  "properties": {
    "offerId": {
      "type": "string",
      "description": "A unique identifier for the Commercial Marketplace Software as a Service Offer.",
      "maxLength": 2048
    }
  },
  "required": [
    "offerId"
  ],
  "additionalProperties": false
}
```

## Properties

#### offerId

A unique identifier that includes your Publisher ID and Offer ID, which you can find in [Partner Center](https://partner.microsoft.com/dashboard). You must format the string as `publisherId.offerId`.

**Type**  
string

**Required**  
✅

**Constraints**  
Maximum string length: 2048.

**Supported values**  


## Examples

```json
{
    "subscriptionOffer": {
        "offerId": "publisherId.offerId"
    }
}
```
