<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/enable-places-analytics/enable-places-analytics -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Enable Places analytics

Microsoft Places analytics provide a comprehensive view of planned versus actual occupancy for buildings, rooms, and desk pools. These insights help real estate and facilities managers and administrators optimize space management and improve employee experiences.

Setting up Places analytics consists of two steps:

1. Give users access to analytics.
2. Enable buildings for analytics.

## Step 1 - Give users access to analytics

We recommend enabling analytics only for users who require access to building and workspace occupancy information.

If you participated in the Microsoft Places Preview, the **DeployPlaces** script created a **Places Analytics Users** mail-enabled security group in your tenant.

Otherwise, you can create or use another mail-enabled security group for this purpose.

Important

- If you plan to use a standard security group, your configuration might not work as expected. To ensure proper functionality, the security group must be configured as a mail-enabled security group.
- Before April 1, 2026, users needed a Teams Premium license to access Places Analytics. This is no longer required.

Once the security group is ready, use [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings).

For example, to enable analytics for users in a specific mail-enabled security group:

```powershell
Set-PlacesSettings –SpaceAnalyticsEnabled 'Default:false,OID:507121fd-a361-40a1-907b-2ca512e6ce50@1a2a08524-022b7-4bab7-8a8c-bc2c4006201c:true'
```

## Step 2 - Enable buildings for analytics

Buildings must be configured in your tenant before they can be enabled for analytics.

Follow the instructions in [Configure buildings and floors](https://learn.microsoft.com/en-us/microsoft-365/places/get-started/quick-setup-buildings-floors).

Then use [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings) to enable analytics.

The syntax for analytics differs from other Places settings.

### Enable all configured buildings

Use:

```text
Default:All
```

### Disable all buildings

Use:

```text
Default:
```

### Enable a subset of buildings

Look up the building identifiers \(PlaceIds\) by using [Get-PlaceV3](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placev3), and then use the following syntax:

```text
Default:[PlaceId1],[PlaceId2],...[PlaceIdN]
```

## Examples

### Enable all buildings for analytics

```powershell
Set-PlacesSettings -Collection Places -SpaceAnalyticsBuildingsList 'Default:All'
```

### Enable two buildings for analytics

```powershell
Set-PlacesSettings -Collection Places -SpaceAnalyticsBuildingsList 'Default:<PlaceId1>,<PlaceId2>'
```

Note

- It can take up to 12 hours for settings to propagate and appear in the user interface.
- For best performance, we recommend limiting analytics to 200 buildings.

## Checking your settings

To view the current settings, use [Get-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/get-placessettings).

Example:

```powershell
Get-PlacesSettings -Collection Places -SpaceAnalyticsBuildingsList
```
