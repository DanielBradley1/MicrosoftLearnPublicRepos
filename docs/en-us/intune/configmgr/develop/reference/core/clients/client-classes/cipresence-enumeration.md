<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cipresence-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CIPresence Enumeration

In Configuration Manager, the `CIPresence` enumeration defines configuration item presence types used in the discovery process.

## Syntax

```
typedef enum tagCIPresence
{
  ciNotPresent = 0,ciNonCompliant = 0,
  ciPresent = 1,ciCompliant = 1,
  ciNotApplicable = 2,
  ciPresenceUnknown = 3,ciComplianceUnknown = 3,
  ciEvaluationError = 4,
  ciNotEvaluated = 5
} CIPresence;
```

## Elements

`ciNotPresent, ciNonCompliant` Configuration item not present or not compliant.

`ciPresent, ciCompliant` Configuration item present or compliant.

`ciNotApplicable` Configuration item not applicable.

`ciPresenceUnknown, ciComplianceUnknown` Configuration item presence or compliance unknown.

`ciEvaluationError` Configuration item evaluation error.

`ciNotEvaluated` Configuration item not evaluated.

## Remarks

This enumeration is used by the [ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface).

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface)
