<!-- Source: https://learn.microsoft.com/en-us/intune/device-management/specialty-devices -->
<!-- Sitemap-Last-Modified: 2026-05-21 -->

# Specialty device management

Specialty device management provides a range of management, configuration, and protection capabilities for specialized devices, such as AR/VR headsets, large smart-screen devices, and select conference room meeting devices.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> This feature requires Microsoft Intune Plan 2 or an additional subscription. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/cloud.svg) **Cloud requirements**

> Specialty device management is supported in the following cloud environments:
> 
> - Public cloud
> - Sovereign cloud environments:
> 
>   - U.S. Government Community Cloud \(GCC\) High
>   - U.S. Department of Defense \(DoD\)

### Licensing considerations

For specialty devices such as headsets and AR/VR devices, for example **Apple Vision Pro**, **RealWear**, and **HTC** devices, organizations must assign a required license to the users of these devices.

For **Microsoft Teams Rooms** devices including Microsoft Surface Hub, organizations need to have sufficient [Microsoft Teams Rooms Pro licenses](https://learn.microsoft.com/en-us/microsoftteams/rooms/rooms-licensing), conference area phone [Teams Shared Device license](https://learn.microsoft.com/en-us/microsoftteams/set-up-common-area-phones) or a Teams license plan that includes Microsoft Intune Plan 1, to cover the users of these devices.

For **Microsoft HoloLens**, subscribers of Microsoft Intune \(Plan 1\) aren't required to add more licenses to manage HoloLens devices.

For specialty devices that run in Microsoft Entra shared device Mode \(SDM\), organizations need to have the same volume of required licenses as their core Intune license \(Intune Plan 1 for either Microsoft E or F plans\) for those users. For example, if 10 frontline workers are sharing one device and they're all covered by Intune Plan 1 core licenses, the organization should also have 10 of the required specialty device licenses to cover those users.

## Next Steps

Learn about enrolling devices into Microsoft Intune here:

- [Enroll devices into Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/guide)
