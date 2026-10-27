<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enums-windowsupdates?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Microsoft Graph Windows Updates enumeration values

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

### azureADDeviceRegistrationErrorReason values

| Member |
| :--- |
| invalidGlobalDeviceId |
| invalidAzureADDeviceId |
| missingTrustType |
| invalidAzureADJoin |
| unknownFutureValue |

### deploymentStateReasonValue values

| Member |
| :--- |
| scheduledByOfferWindow |
| offeringByRequest |
| pausedByRequest |
| pausedByMonitoring |
| unknownFutureValue |
| faultedByContentOutdated |

### deploymentStateValue values

| Member |
| :--- |
| scheduled |
| offering |
| paused |
| faulted |
| archived |
| unknownFutureValue |

### enrollmentState values

| Member |
| :--- |
| notEnrolled |
| enrolled |
| enrolledWithPolicy |
| enrolling |
| unenrolling |
| unknownFutureValue |

### monitoringAction values

| Member |
| :--- |
| alertError |
| offerFallback |
| pauseDeployment |
| unknownFutureValue |

### monitoringSignal values

| Member |
| :--- |
| ineligible |
| rollback |
| unknownFutureValue |

### qualityUpdateClassification values

| Member |
| :--- |
| all |
| security |
| nonSecurity |
| unknownFutureValue |

### qualityUpdateCadence values

| Member |
| :--- |
| monthly |
| outOfBand |
| unknownFutureValue |

### requestedDeploymentStateValue values

| Member |
| :--- |
| none |
| paused |
| archived |
| unknownFutureValue |

### resourceConnectionState values

| Member |
| :--- |
| connected |
| notAuthorized |
| notFound |
| unknownFutureValue |

### safeguardCategory values

| Member |
| :--- |
| likelyIssues |
| unknownFutureValue |

### updateCategory values

| Member |
| :--- |
| feature |
| quality |
| unknownFutureValue |
| driver |

### cveSeverityLevel values

| Member |
| :--- |
| critical |
| moderate |
| important |
| unknownFutureValue |

### bodyType values

| Member |
| :--- |
| text |
| html |
| unknownFutureValue |

### remediationType values

| Member |
| :--- |
| inPlaceUpgrade |
| unknownFutureValue |

### approvalStatus values

| Member |
| :--- |
| approved |
| suspended |
| unknownFutureValue |

### approvedBy values

| Member |
| :--- |
| system |
| user |
| unknownFutureValue |

### deviceClientState values

| Member |
| :--- |
| offering |
| onHold |
| installing |
| installed |
| cancelled |
| uninstalling |
| uninstalled |
| notOffering |
| unknownFutureValue |

### deviceClientSubstate values

| Member |
| :--- |
| deferred |
| offerReady |
| paused |
| offerReceived |
| downloadStart |
| downloadComplete |
| installStart |
| installComplete |
| restartRequired |
| restartInitiated |
| restartComplete |
| updateInstalled |
| rollbackComplete |
| userCancelled |
| deviceCancelled |
| uninstall |
| rollback |
| updateUninstalled |
| notSupported |
| previousUpdateInProgress |
| unknownFutureValue |

### deviceServiceState values

| Member |
| :--- |
| unknown |
| pending |
| offering |
| onHold |
| cancelled |
| notOffering |
| unknownFutureValue |

### deviceServiceSubstate values

| Member |
| :--- |
| unknown |
| scheduled |
| offerReady |
| adminPaused |
| adminCancelled |
| removedFromDeployment |
| notOffering |
| unknownFutureValue |

### hotpatchReadiness values

| Member |
| :--- |
| ready |
| notReady |
| unknownFutureValue |

### osStatus values

| Member |
| :--- |
| endOfServicing |
| inServicing |
| nearEndOfServicing |
| unknownFutureValue |
