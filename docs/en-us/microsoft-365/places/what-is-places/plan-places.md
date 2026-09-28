<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/places/what-is-places/plan-places -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Planning your desired Places end user experience

Before deploying Microsoft Places, define how your organization plans to use it and which experiences matter most to employees, workplace operations, and leadership.

Places supports scenarios ranging from basic hybrid coordination to advanced desk booking, workplace analytics, and automated work location detection.

Many Places features rely on the same workplace hierarchy and infrastructure. Early configuration decisions directly impact scalability, administration, analytics, and the end-user experience. Thoughtful planning helps reduce deployment complexity and ensures the environment aligns with your long-term workplace strategy.

## Identify primary workplace goals

Start by determining what your organization is trying to achieve. Different goals require different configuration approaches.

Common objectives include:

- Desk booking
- Room booking
- Maps and floor plans
- Awareness of whether team members are working in the office

These priorities determine which capabilities to deploy first and which to introduce later.

Examples include:

- **Hybrid collaboration** – Prioritize presence, work plans, and workplace awareness.
- **Shared seating** – Prioritize desk pools and desk booking.
- **Workplace optimization** – Prioritize analytics, reporting, and automation.
- **Distributed operations** – Prioritize delegated administration and portal-based management.

## Choose an administration approach

Microsoft Places supports both PowerShell and portal-based management.

- **PowerShell** is best for initial deployment, bulk configuration, automation, and large-scale or advanced scenarios.
- **The Places management portal** is best for day-to-day administration, delegated management, and facilities-led operations.

Most organizations use both: PowerShell to establish the environment and the Places management portal for ongoing administration.

### Already have rooms with Exchange resource accounts?

Use `Initialize-Places` to build your Places hierarchy from existing Exchange rooms. This approach allows you to:

- Discover existing spaces.
- Infer buildings and floors.
- Export a mapping file.
- Validate the hierarchy.
- Create the Places hierarchy more efficiently.

### Starting from scratch?

If you don't have existing room resources, use PowerShell or the Places management portal to manually create your hierarchy, buildings, floors, rooms, desks, and workplace structure.

Manual creation is often preferred when:

- Building a new workplace hierarchy.
- Creating desk neighborhoods.
- Designing custom floor structures.
- Delegating administration to non-IT staff.

## Deployment decision tree

The following decision tree can help determine the best deployment approach for your organization.

### Is workplace presence awareness a priority?

**Yes**

- Enable work plans.
- Consider automatic work location detection and check-in capabilities.

**No**

- Focus on room booking and desk booking scenarios.

### Do you want employee work locations to update automatically?

**Yes**

- Configure Wi-Fi-based location detection.
- Configure peripheral-based work location detection.

**No**

- Allow users to manually update their location through Teams, Outlook, or Places.

### Is improving the room booking experience a primary goal?

**Yes**

- Add rooms to the Places hierarchy.
- Configure room metadata and photos.
- Enable Places Finder.

**No**

- Focus primarily on buildings, presence, and desk booking.

### Do your rooms already have Exchange resource accounts?

**Yes**

- Use `Initialize-Places` to import and organize existing rooms.

**No**

- Build the hierarchy manually.

### Is desk hoteling a primary business need?

**Yes**

- Configure desk pools \(workspaces\).
- Configure reservation policies.
- Configure auto-release policies.

**No**

- Focus on workplace presence and room experiences.

### Do employees have permanently assigned desks?

**Yes**

- Configure desks as assigned.

**No**

- Configure reservable desks, drop-in desks, or desk pools.

### Do you want to add floor plans and maps?

**Yes**

- Identify your current floor plan format.
- Plan for conversion to IMDF format.

**No**

- Use consistent room, building, and desk naming conventions to help users locate spaces.

### Will non-technical staff manage spaces?

**Yes**

- Assign appropriate Places administration roles.
- Use the Places management portal.

**No**

- Use centralized PowerShell administration.

### Are analytics important?

**Yes**

- Prioritize hierarchy accuracy.
- Drive user adoption.
- Configure work plans and workplace signals.

**No**

- Focus first on core booking and workplace functionality.

This decision tree connects key deployment choices, including hierarchy design, workplace automation, desk strategy, administration, and analytics, to recommended implementation paths.

## Determine your desk model

Desk configuration affects workplace hierarchy, operations, reporting, and user experience.

Consider the following questions:

- Are desks assigned or shared?
- Are reservations required?
- Do bring-your-own-device \(BYOD\) workspaces exist?
- Are peripherals used for location detection or check-in?
- Are desks grouped into pools?

### Shared desks \(hoteling\)

Focus on:

- Desk pools
- Reservations
- Peripheral integration
- Sections and neighborhoods
- Analytics

### Assigned desks

Focus on:

- Workplace presence
- Room experiences
- Hierarchy management
- Basic analytics

### Hybrid model

Use a combination of:

- Assigned desks
- Shared desks
- Visitor spaces
- Hoteling spaces

## Define the operating model

Determine who will manage the environment.

Possible models include:

- Centralized IT administration
- Facilities-led administration
- Delegated building administration
- Hybrid administration

Places supports administrative roles such as:

- Places Administrator
- Places Building Administrator
- Places Desk Administrator

Delegated administration is especially valuable for organizations that manage multiple buildings or locations.

## Determine analytics priorities

If analytics are important, plan for them early in the deployment process.

Analytics quality depends on:

- An accurate workplace hierarchy
- Proper room and desk configuration
- Work plan adoption
- Reliable location signals
- Consistent metadata

Common reporting scenarios include:

- Building occupancy
- Planned versus actual attendance
- Room utilization
- Desk utilization
- Capacity planning
- Reservation trends

To support workplace analytics, prioritize:

- Work plans
- Desk booking
- Workplace hierarchy accuracy
- Automated location detection
- Consistent room and desk metadata

Investing in these capabilities early helps ensure analytics remain accurate and actionable as your Places deployment grows.
