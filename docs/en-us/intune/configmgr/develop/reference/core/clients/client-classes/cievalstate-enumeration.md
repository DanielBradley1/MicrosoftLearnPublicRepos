<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/cievalstate-enumeration -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# CIEvalState Enumeration

In Configuration Manager, the `CIEvalState` enumeration defines configuration item evaluation states. This enumeration is used by the [ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface).

## Syntax

```
typedef enum tagCIEvalState
{
  ciIdle = 0,
  ciEvaluating
} CIEvalState;
```

## Elements

ciIdle Configuration item is idle.

ciEvaluating Configuration item is being evaluated.

## See Also

[ICIINFO Interface](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/iciinfo-interface)
