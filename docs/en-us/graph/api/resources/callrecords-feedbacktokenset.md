<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callrecords-feedbacktokenset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-22 -->

# feedbackTokenSet resource type

Namespace: microsoft.graph.callRecords

This is an *open type* that represents the set of feedback tokens provided by the user of this endpoint for the Session. This is a set of Boolean properties. The property names shouldn't be relied upon since they may change depending on what tokens are offered to the user.

## Properties

Explicit property names won't be documented since the feedback token names can change, hence this is an [open type](https://learn.microsoft.com/en-us/aspnet/web-api/overview/odata-support-in-aspnet-web-api/odata-v4/use-open-types-in-odata-v4).

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "BackgroundNoise": true,
  "DistortedSpeech": true,
  "Echo": false,
  "ElectronicFeedback": false,
  "MuffledSpeech": true
}
```
