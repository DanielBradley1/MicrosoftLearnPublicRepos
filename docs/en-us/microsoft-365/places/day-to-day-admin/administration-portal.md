<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/day-to-day-admin/administration-portal -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Administration Portal

The [Places Admin Portal](https://places.cloud.microsoft/places/admin) provides a user-friendly administrative experience designed to complement PowerShell. While PowerShell remains the foundation for large-scale deployment and advanced configuration, the Places Portal enables building, floor, and space administrators to make day-to-day updates quickly and without scripting knowledge.

To ensure that you have admin rights and are logging in as an admin, select **Admin** from the dropdown menu in the upper-right corner of the portal.

## When to use the Places Portal vs. PowerShell

### The Places Portal is best suited for:

- Ongoing maintenance and minor updates
- Delegated administration at the building or floor level
- Quickly reviewing and adjusting the workspace hierarchy

### PowerShell remains the recommended approach for:

- Initial deployments at scale, such as bulk creation of buildings, floors, or resources
- Advanced configuration scenarios
- Automation and repeatable processes

Using both together provides the most effective administrative model: PowerShell for setup and scale, and the Places Portal for intuitive, ongoing management.

## Admin Portal layout

The portal is organized into two primary areas:

- **Space Management** – Where administrators configure and maintain the workplace environment
- **Space Analytics** – Where administrators review usage and performance insights

Most administrative tasks are performed within **Space Management**, which focuses on managing the structure and properties of buildings and spaces.

## Space Management

### Managing the workplace hierarchy

The Places Portal presents the workplace as a clear hierarchical structure, making it easier to understand and manage:

- Buildings
- Floors within buildings
- Sections
- Rooms and desks within those spaces

This hierarchy allows admins to visually navigate their environment and make targeted updates. For example, a floor admin can quickly locate a specific section and adjust the desks or rooms within it.

This structure is especially important because Places relies on it to provide meaningful end-user experiences such as wayfinding, booking, and presence awareness.

### Unparented space

Unparented spaces are rooms or desks that exist in the tenant, often as Exchange resource accounts, but have not yet been assigned to a building or floor within the Places hierarchy.

This commonly happens when:

- An organization enables Places after already having rooms deployed, such as Teams Rooms.
- Resource accounts were created in bulk without being mapped to a physical location.

The **Unparented space** view helps admins identify these items and complete setup by placing them into the correct building and floor.

While these resources may still function for booking, assigning them properly ensures they participate fully in the Places experience.

### Day-to-day administrative updates

You can choose to create a new building hierarchy or edit existing buildings, floors, sections, desk pools, and desks.

One of the primary benefits of the Places Portal is simplifying operational tasks that previously required PowerShell.

Admins can:

- Update room and desk properties
- Reassign desks from one user to another
- Adjust naming conventions and metadata
- Enable or disable specific spaces, for example taking a desk offline

This enables a broader set of users, such as building or floor administrators, to manage their areas directly without relying on a centralized IT admin for every change.

## Space Analytics

Space Analytics provides easy-to-understand statistics on how your workplace is being used.

While Space Management is where you set up and organize your spaces, including buildings, floors, rooms, and desks, Space Analytics is where you can see how those spaces are performing.

It builds on that structure by highlighting trends and usage patterns over time, helping administrators evaluate performance, understand occupancy, and make more informed decisions about capacity and space planning.

### Key areas include

#### Home

A quick overview of your most important metrics and trends.

#### Building Analytics

Shows overall building usage and occupancy.

You can compare how many people plan to come in through work plans versus how many checked in, with data summarized at the organizational level.

Note

Badge swipe integration is required.

#### Room Analytics

Focuses on meeting room reservations, helping you understand booking patterns and identify underused or overbooked spaces.

#### Desk Pool Analytics

Tracks how shared desks are being reserved, providing insight into demand and usage trends.

#### Desk Analytics

Looks at individual desk reservations and usage over time.
