<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/places-api-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# Working with the Places API in Microsoft Graph

The Places API in Microsoft Graph provides a unified way to manage and interact with physical spaces, such as buildings, rooms, desks, and workspaces, within an organization.

## Supported types

The following types are supported in the Places API.

### Place types

Place represents different space types within a tenant. A **place** object can be one of the following types.

| Place type | Details |
| :--- | :--- |
| [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) | Represents a building within the tenant and has properties such as name, address, and geographic coordinates. |
| [desk](https://learn.microsoft.com/en-us/graph/api/resources/desk?view=graph-rest-1.0) | Represents individual desks. A **desk** must be added to a **section**. The rich properties of the **section** include email address, mode, and accessibility. |
| [floor](https://learn.microsoft.com/en-us/graph/api/resources/floor?view=graph-rest-1.0) | Represents a floor within a building, including properties such as **name**, **parentId**, and **sortOrder**. A **building** is always the parent of a **floor**. |
| [room](https://learn.microsoft.com/en-us/graph/api/resources/room?view=graph-rest-1.0) | Represents a room within the tenant. All rooms must be associated with Exchange mailboxes. A **room** can be added to a **floor** or to a **section**. The rich properties of the **room** include an email address for the room, accessibility, capacity, audio device, video device, and so on. |
| [roomList](https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0) | A collection of rooms in the tenant. Places supports **roomList** to ensure room booking works in **Room Finder** across all clients on all devices, such as classic Outlook across desktop and mobile.  <br>  <br>However, we recommend that you rely on the new **place** types and hierarchy if you don't use **roomFinder** in the tenant. For more information about **roomList**, see the [roomList](https://learn.microsoft.com/en-us/graph/api/resources/roomlist?view=graph-rest-1.0) resource type. |
| [section](https://learn.microsoft.com/en-us/graph/api/resources/section?view=graph-rest-1.0) | Represents a section within a floor, including properties such as **name**, **parentId**, and **label**. A **floor** is always the parent of a **section**. |
| [workspace](https://learn.microsoft.com/en-us/graph/api/resources/workspace?view=graph-rest-1.0) | Represents a collection of desks. All workspaces must be associated with Exchange mailboxes. A **workspace** can be added to a **section**. The rich properties of a workspace include an email address for the workspace, mode, accessibility, and capacity. |

### Map feature types

The map feature represents the corresponding map of a place. A map feature object can be one of the following types.

| Map feature type | Details |
| :--- | :--- |
| [buildingMap](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) | Represents a map file associated with a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) in Places. This object is the IMDF-format representation of building.geojson. |
| [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) | Represents a fixture.geojson file in IMDF format that defines movable or semi-permanent physical assets within a space. These assets support utility, service, or aesthetic functions without affecting structural integrity. |
| [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) | Represents a footprint.geojson file in IMDF format that defines the approximate physical extent of a referenced [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). |
| [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) | Represents a level.geojson file in IMDF format that defines the physical floor structure within a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). |
| [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) | Represents a section.geojson file in IMDF format that defines sections \(such as zones or partitions\) on the floor of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). |
| [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) | Represents a unit.geojson file in IMDF format that defines units \(such as rooms or offices\) on a floor of a [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0). |

## Using the Places API

The Places API enables applications with appropriate read or write permissions to interact with **place** objects. Every **place** object includes fundamental properties such as **id**, **placeId**, and **displayName**. More advanced types, such as rooms, workspaces, and desks, offer more properties such as **mode**, **emailAddress**, and **deviceInformation**.

The map APIs in Places enable applications with appropriate read or write permissions to interact with map feature objects. Each map feature object includes fundamental properties like **id**, and other properties such as **placeId**, **geometry**, and **display\_point**.

Detailed descriptions of each type are available in their respective documentation sections.

### Prerequisites for Places list and descendant APIs

Before you can use the [List place objects](https://learn.microsoft.com/en-us/graph/api/place-list?view=graph-rest-1.0) or [place: descendants](https://learn.microsoft.com/en-us/graph/api/place-descendants?view=graph-rest-1.0) APIs, you must ensure that Places settings are properly configured in your Microsoft 365 environment; otherwise, these APIs do not return any places unless the following setup steps are completed:

1. Download and connect to the *MicrosoftPlaces* PowerShell module. For more information, see [Connect-MicrosoftPlaces](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/connect-microsoftplaces).
2. Make places visible by enabling buildings with the following command. For more information, see [Set-PlacesSettings](https://learn.microsoft.com/en-us/microsoft-365/places/powershell/set-placessettings#-enablebuildings).

   ```PowerShell
   Set-PlacesSettings -EnableBuildings 'Default:true'
   ```

## Common use cases

The following table lists some of the common uses for the Places API.

| Use case | REST resource | See also |
| :--- | :--- | :--- |
| Create and manage a place | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | [place methods](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0#methods) |
| Interact with place spaces such as building, floor, section, room, room list, workspace, or desk | [place](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0) | [place methods](https://learn.microsoft.com/en-us/graph/api/resources/place?view=graph-rest-1.0#methods) |
| Ingest the map file for a building | [building](https://learn.microsoft.com/en-us/graph/api/resources/building?view=graph-rest-1.0) | [Ingest map file](https://learn.microsoft.com/en-us/graph/api/building-ingestmapfile?view=graph-rest-1.0) |
| List levels in a building | [levelMap](https://learn.microsoft.com/en-us/graph/api/resources/levelmap?view=graph-rest-1.0) | [List levels](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-levels?view=graph-rest-1.0) |
| List footprints in a building | [footprintMap](https://learn.microsoft.com/en-us/graph/api/resources/footprintmap?view=graph-rest-1.0) | [List footprints](https://learn.microsoft.com/en-us/graph/api/buildingmap-list-footprints?view=graph-rest-1.0) |
| Get and delete a **buildingMap** | [buildingMap](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0) | [buildingMap methods](https://learn.microsoft.com/en-us/graph/api/resources/buildingmap?view=graph-rest-1.0#methods) |
| Create and manage a **unitMap** | [unitMap](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0) | [unitMap methods](https://learn.microsoft.com/en-us/graph/api/resources/unitmap?view=graph-rest-1.0#methods) |
| Create and manage a **fixtureMap** | [fixtureMap](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0) | [fixtureMap methods](https://learn.microsoft.com/en-us/graph/api/resources/fixturemap?view=graph-rest-1.0#methods) |
| Create and manage a **sectionMap** | [sectionMap](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0) | [sectionMap methods](https://learn.microsoft.com/en-us/graph/api/resources/sectionmap?view=graph-rest-1.0#methods) |

## Next steps

Use the Microsoft Graph Places APIs to interact with different place entities. To learn more:

- Explore the resources and methods that are most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
