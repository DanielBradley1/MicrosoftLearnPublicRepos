<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/datetimetimezone?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-08 -->

# dateTimeTimeZone resource type

Namespace: microsoft.graph

Describes the date, time, and time zone of a point in time.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| dateTime | String | A single point of time in a combined date and time representation \(`{date}T{time}`; for example, `2017-08-29T04:00:00.0000000`\). |
| timeZone | String | Represents a time zone, for example, "Pacific Standard Time". See below for more possible values. |

In general, the **timeZone** property *can* be set to any of the [time zones currently supported by Windows](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/default-time-zones), as well as the other [time zones supported by the calendar API](#additional-time-zones).

- Methods such as [create](https://learn.microsoft.com/en-us/graph/api/user-post-events?view=graph-rest-1.0) or [update](https://learn.microsoft.com/en-us/graph/api/event-update?view=graph-rest-1.0) might not support all **dateTimeTimeZone** time zones.
- If you use **dateTimeTimeZone** with the [virtual event](https://learn.microsoft.com/en-us/graph/api/resources/virtualevent?view=graph-rest-1.0) APIs, the only supported format for the **timeZone** property is time zones currently supported by Windows. For details on how to get all available time zones using PowerShell, see [Get-TimeZone](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-timezone#example-3-get-all-available-time-zones).

### Additional time zones

Etc/GMT+12

Etc/GMT+11

Pacific/Honolulu

America/Anchorage

America/Santa\_Isabel

America/Los\_Angeles

America/Phoenix

America/Chihuahua

America/Denver

America/Guatemala

America/Chicago

America/Mexico\_City

America/Regina

America/Bogota

America/New\_York

America/Indiana/Indianapolis

America/Caracas

America/Asuncion

America/Halifax

America/Cuiaba

America/La\_Paz

America/Santiago

America/St\_Johns

America/Sao\_Paulo

America/Argentina/Buenos\_Aires

America/Cayenne

America/Godthab

America/Montevideo

America/Bahia

Etc/GMT+2

Atlantic/Azores

Atlantic/Cape\_Verde

Africa/Casablanca

Etc/GMT

Europe/London

Atlantic/Reykjavik

Europe/Berlin

Europe/Budapest

Europe/Paris

Europe/Warsaw

Africa/Lagos

Africa/Windhoek

Europe/Bucharest

Asia/Beirut

Africa/Cairo

Asia/Damascus

Africa/Johannesburg

Europe/Kyiv

Europe/Istanbul

Asia/Jerusalem

Asia/Amman

Asia/Baghdad

Europe/Kaliningrad

Asia/Riyadh

Africa/Nairobi

Asia/Tehran

Asia/Dubai

Asia/Baku

Europe/Moscow

Indian/Mauritius

Asia/Tbilisi

Asia/Yerevan

Asia/Kabul

Asia/Karachi

Asia/Toshkent \(Tashkent\)

Asia/Kolkata

Asia/Colombo

Asia/Kathmandu

Asia/Astana \(Almaty\)

Asia/Dhaka

Asia/Yekaterinburg

Asia/Yangon \(Rangoon\)

Asia/Bangkok

Asia/Novosibirsk

Asia/Shanghai

Asia/Krasnoyarsk

Asia/Singapore

Australia/Perth

Asia/Taipei

Asia/Ulaanbaatar

Asia/Irkutsk

Asia/Tokyo

Asia/Seoul

Australia/Adelaide

Australia/Darwin

Australia/Brisbane

Australia/Sydney

Pacific/Port\_Moresby

Australia/Hobart

Asia/Yakutsk

Pacific/Guadalcanal

Asia/Vladivostok

Pacific/Auckland

Etc/GMT-12

Pacific/Fiji

Asia/Magadan

Pacific/Tongatapu

Pacific/Apia

Pacific/Kiritimati

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "dateTime": "string",
  "timeZone": "string"
}
```
