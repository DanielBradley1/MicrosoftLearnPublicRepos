<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# deviceManagementTemplateInsightsDefinition resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

template insights definition

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List deviceManagementTemplateInsightsDefinitions](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition-list?view=graph-rest-beta) | [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) collection | List properties and relationships of the [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) objects. |
| [Get deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition-get?view=graph-rest-beta) | [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) | Read properties and relationships of the [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) object. |
| [Create deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition-create?view=graph-rest-beta) | [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) | Create a new [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) object. |
| [Delete deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition-delete?view=graph-rest-beta) | None | Deletes a [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta). |
| [Update deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition-update?view=graph-rest-beta) | [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) | Update the properties of a [deviceManagementTemplateInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementtemplateinsightsdefinition?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of Templateinsights document. |
| settingInsights | [deviceManagementSettingInsightsDefinition](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfigv2-devicemanagementsettinginsightsdefinition?view=graph-rest-beta) collection | Setting insights in a template |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceManagementTemplateInsightsDefinition",
  "id": "String (identifier)",
  "settingInsights": [
    {
      "@odata.type": "microsoft.graph.deviceManagementSettingInsightsDefinition",
      "settingDefinitionId": "String",
      "settingInsight": {
        "@odata.type": "microsoft.graph.deviceManagementConfigurationGroupSettingValue",
        "settingValueTemplateReference": {
          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
          "settingValueTemplateId": "String",
          "useTemplateDefault": true
        },
        "children": [
          {
            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
            "settingDefinitionId": "String",
            "settingInstanceTemplateReference": {
              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
              "settingInstanceTemplateId": "String"
            },
            "auditRuleInformation": {
              "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
              "auditType": "String",
              "auditRuleMetadata": {
                "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                "metadataType": "String",
                "ruleId": "String",
                "ruleName": "String",
                "ruleDescription": "String",
                "ruleVersion": "String",
                "ruleSeverity": "String"
              }
            },
            "choiceSettingValue": {
              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
              "settingValueTemplateReference": {
                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                "settingValueTemplateId": "String",
                "useTemplateDefault": true
              },
              "value": "String",
              "children": [
                {
                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                  "settingDefinitionId": "String",
                  "settingInstanceTemplateReference": {
                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                    "settingInstanceTemplateId": "String"
                  },
                  "auditRuleInformation": {
                    "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                    "auditType": "String",
                    "auditRuleMetadata": {
                      "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                      "metadataType": "String",
                      "ruleId": "String",
                      "ruleName": "String",
                      "ruleDescription": "String",
                      "ruleVersion": "String",
                      "ruleSeverity": "String"
                    }
                  },
                  "choiceSettingValue": {
                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                    "settingValueTemplateReference": {
                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                      "settingValueTemplateId": "String",
                      "useTemplateDefault": true
                    },
                    "value": "String",
                    "children": [
                      {
                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                        "settingDefinitionId": "String",
                        "settingInstanceTemplateReference": {
                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                          "settingInstanceTemplateId": "String"
                        },
                        "auditRuleInformation": {
                          "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                          "auditType": "String",
                          "auditRuleMetadata": {
                            "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                            "metadataType": "String",
                            "ruleId": "String",
                            "ruleName": "String",
                            "ruleDescription": "String",
                            "ruleVersion": "String",
                            "ruleSeverity": "String"
                          }
                        },
                        "choiceSettingValue": {
                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                          "settingValueTemplateReference": {
                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                            "settingValueTemplateId": "String",
                            "useTemplateDefault": true
                          },
                          "value": "String",
                          "children": [
                            {
                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                              "settingDefinitionId": "String",
                              "settingInstanceTemplateReference": {
                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                "settingInstanceTemplateId": "String"
                              },
                              "auditRuleInformation": {
                                "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                "auditType": "String",
                                "auditRuleMetadata": {
                                  "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                  "metadataType": "String",
                                  "ruleId": "String",
                                  "ruleName": "String",
                                  "ruleDescription": "String",
                                  "ruleVersion": "String",
                                  "ruleSeverity": "String"
                                }
                              },
                              "choiceSettingValue": {
                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                "settingValueTemplateReference": {
                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                  "settingValueTemplateId": "String",
                                  "useTemplateDefault": true
                                },
                                "value": "String",
                                "children": [
                                  {
                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                    "settingDefinitionId": "String",
                                    "settingInstanceTemplateReference": {
                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                      "settingInstanceTemplateId": "String"
                                    },
                                    "auditRuleInformation": {
                                      "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                      "auditType": "String",
                                      "auditRuleMetadata": {
                                        "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                        "metadataType": "String",
                                        "ruleId": "String",
                                        "ruleName": "String",
                                        "ruleDescription": "String",
                                        "ruleVersion": "String",
                                        "ruleSeverity": "String"
                                      }
                                    },
                                    "choiceSettingValue": {
                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                      "settingValueTemplateReference": {
                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                        "settingValueTemplateId": "String",
                                        "useTemplateDefault": true
                                      },
                                      "value": "String",
                                      "children": [
                                        {
                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                          "settingDefinitionId": "String",
                                          "settingInstanceTemplateReference": {
                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                            "settingInstanceTemplateId": "String"
                                          },
                                          "auditRuleInformation": {
                                            "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                            "auditType": "String",
                                            "auditRuleMetadata": {
                                              "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                              "metadataType": "String",
                                              "ruleId": "String",
                                              "ruleName": "String",
                                              "ruleDescription": "String",
                                              "ruleVersion": "String",
                                              "ruleSeverity": "String"
                                            }
                                          },
                                          "choiceSettingValue": {
                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                            "settingValueTemplateReference": {
                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                              "settingValueTemplateId": "String",
                                              "useTemplateDefault": true
                                            },
                                            "value": "String",
                                            "children": [
                                              {
                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                "settingDefinitionId": "String",
                                                "settingInstanceTemplateReference": {
                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                  "settingInstanceTemplateId": "String"
                                                },
                                                "auditRuleInformation": {
                                                  "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                  "auditType": "String",
                                                  "auditRuleMetadata": {
                                                    "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                    "metadataType": "String",
                                                    "ruleId": "String",
                                                    "ruleName": "String",
                                                    "ruleDescription": "String",
                                                    "ruleVersion": "String",
                                                    "ruleSeverity": "String"
                                                  }
                                                },
                                                "choiceSettingValue": {
                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                  "settingValueTemplateReference": {
                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                    "settingValueTemplateId": "String",
                                                    "useTemplateDefault": true
                                                  },
                                                  "value": "String",
                                                  "children": [
                                                    {
                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                      "settingDefinitionId": "String",
                                                      "settingInstanceTemplateReference": {
                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                        "settingInstanceTemplateId": "String"
                                                      },
                                                      "auditRuleInformation": {
                                                        "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                        "auditType": "String",
                                                        "auditRuleMetadata": {
                                                          "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                          "metadataType": "String",
                                                          "ruleId": "String",
                                                          "ruleName": "String",
                                                          "ruleDescription": "String",
                                                          "ruleVersion": "String",
                                                          "ruleSeverity": "String"
                                                        }
                                                      },
                                                      "choiceSettingValue": {
                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                        "settingValueTemplateReference": {
                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                          "settingValueTemplateId": "String",
                                                          "useTemplateDefault": true
                                                        },
                                                        "value": "String",
                                                        "children": [
                                                          {
                                                            "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                            "settingDefinitionId": "String",
                                                            "settingInstanceTemplateReference": {
                                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                              "settingInstanceTemplateId": "String"
                                                            },
                                                            "auditRuleInformation": {
                                                              "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                              "auditType": "String",
                                                              "auditRuleMetadata": {
                                                                "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                "metadataType": "String",
                                                                "ruleId": "String",
                                                                "ruleName": "String",
                                                                "ruleDescription": "String",
                                                                "ruleVersion": "String",
                                                                "ruleSeverity": "String"
                                                              }
                                                            },
                                                            "choiceSettingValue": {
                                                              "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                              "settingValueTemplateReference": {
                                                                "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                                "settingValueTemplateId": "String",
                                                                "useTemplateDefault": true
                                                              },
                                                              "value": "String",
                                                              "children": [
                                                                {
                                                                  "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                  "settingDefinitionId": "String",
                                                                  "settingInstanceTemplateReference": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                                    "settingInstanceTemplateId": "String"
                                                                  },
                                                                  "auditRuleInformation": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                                    "auditType": "String",
                                                                    "auditRuleMetadata": {
                                                                      "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                      "metadataType": "String",
                                                                      "ruleId": "String",
                                                                      "ruleName": "String",
                                                                      "ruleDescription": "String",
                                                                      "ruleVersion": "String",
                                                                      "ruleSeverity": "String"
                                                                    }
                                                                  },
                                                                  "choiceSettingValue": {
                                                                    "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                                    "settingValueTemplateReference": {
                                                                      "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingValueTemplateReference",
                                                                      "settingValueTemplateId": "String",
                                                                      "useTemplateDefault": true
                                                                    },
                                                                    "value": "String",
                                                                    "children": [
                                                                      {
                                                                        "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingInstance",
                                                                        "settingDefinitionId": null,
                                                                        "settingInstanceTemplateReference": {
                                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationSettingInstanceTemplateReference",
                                                                          "settingInstanceTemplateId": "String"
                                                                        },
                                                                        "auditRuleInformation": {
                                                                          "@odata.type": "microsoft.graph.deviceManagementAuditPowerShellRuleDetail",
                                                                          "auditType": "String",
                                                                          "auditRuleMetadata": {
                                                                            "@odata.type": "microsoft.graph.deviceManagementAuditRuleMetadata",
                                                                            "metadataType": "String",
                                                                            "ruleId": "String",
                                                                            "ruleName": "String",
                                                                            "ruleDescription": "String",
                                                                            "ruleVersion": "String",
                                                                            "ruleSeverity": "String"
                                                                          }
                                                                        },
                                                                        "choiceSettingValue": {
                                                                          "@odata.type": "microsoft.graph.deviceManagementConfigurationChoiceSettingValue",
                                                                          "settingValueTemplateReference": null,
                                                                          "value": "String",
                                                                          "children": null
                                                                        }
                                                                      }
                                                                    ]
                                                                  }
                                                                }
                                                              ]
                                                            }
                                                          }
                                                        ]
                                                      }
                                                    }
                                                  ]
                                                }
                                              }
                                            ]
                                          }
                                        }
                                      ]
                                    }
                                  }
                                ]
                              }
                            }
                          ]
                        }
                      }
                    ]
                  }
                }
              ]
            }
          }
        ]
      }
    }
  ]
}
```
