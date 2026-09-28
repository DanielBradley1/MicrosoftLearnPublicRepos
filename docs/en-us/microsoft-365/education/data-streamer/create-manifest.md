<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-manifest -->
<!-- Sitemap-Last-Modified: 2025-08-01 -->

# Create a manifest

A manifest describes the data that comes in from a streaming data source. The manifest is sent by the data source on a connection.

## Fields

| **Field Name** | **Type** | **Required** | **Notes** |
| --- | --- | --- | --- |
| Name | string | Yes | Localize |
| ID | guid | Yes | This is used to specify the device or app to DataStreamer and should never change. |
| Version | string | No |  |
| DataInterval | number | No | Must be a positive integer. DataStreamer matches this interval if specified. If not set DataStreamer uses the value in the Settings worksheet, or the default value if not specified. |
| Channels | array | Yes | At least one channel |
| Commands | array | No |  |

## Channel Fields

| **Field Name** | **Type** | **Required** | **Notes** |
| --- | --- | --- | --- |
| ID | string | Yes if no subchannels | Don't localize. This value is used to create two named ranges for the channel. The named ranges will be HST\_<channel id> for the history column and CUR\_<channel\_id> for the current column \(one row\). |
| Name | string | Yes | Localize |
| Description | string | No | Localize |
| UnitOfMeasure | string | No | Localize. When this is a subchannel and this isn't specified, it inherits from the parent. |
| Range | object | No | Only if channel value is numeric |
| Min | number | No | Either Min, Max or Both must be specified. |
| Max | number | No |  |
| SubChannels | array | No |  |

## Command Fields

The list of commands describes the commands the device or app can run.

| **Field Name** | **Type** | **Required** | **Notes** |
| --- | --- | --- | --- |
| Name | string | Yes |  |
| Params | array | No |  |
| Name | string | No |  |
| Name | string | Yes |  |
| Type | string | Yes |  |
| **LookupList** |  | No | For any type, Will show up as a dropdown in a worksheet. If LookupList is provided then Range is ignored if present. |
| Value | any | Yes | The actual value sent in the command |
| Caption | string | Yes | The text shown in the dropdown |
| **Range** |  | No | For integer and float types only |
| Min | number | No | If not provided then the Min is the min for that data type. |
| Max | number | No | If not provided then the Max is the max for that data type. |

## Manifest JSON Example

```
{
   Name:         "Built-in Sensors",
   Id:           “23323-gba6-abd788",
   Version:      “1.0”,
   DataInterval: 40,
   Channels:
   [
     {
       Id:            "ILLUM",
       Name:          "Illuminance",
       Description:   "Illuminance in Lux",
       UnitOfMeasure: "lux",
       Range:         
 {
          Min: 0,
          Max: 100
 }
     },
     {
       Id:            "<group>",
       Name:          "Accelerometer",
       Description:   "G-force acceleration",
       UnitOfMeasure: "g's",
       Channels:
  [
         {
           Id:            "ACC-X",
           Name:          "X",
           Description:   "G-force acceleration along the x-axis"                
         },
         {
           Id:            "ACC-Y",
           Name:          "Y",
           Description:   "G-force acceleration along the y-axis"                
         },
         {
           Id:            "ACC-Z",
           Name:          "Z",
           Description:   "G-force acceleration along the z-axis"                
         }
       ]
     },   
     {
       Id:            "ALT",
       Name:          "Altimeter",
       Description:   "Current altitude determined by the altimeter sensor in meters",
       UnitOfMeasure: "m"
     }                                        
   ],
```

## Commands Example

```
[
     {
        Name:           "SwitchSensor"
        Params:      
        [
           Name:        "SensorName",
           Type:        "string"
           LookupList:  
       [
      {
          Value: “RAW”,
          Caption: “Show Raw Data”

      },
      {
          Value: “TOSS”,
          Caption: “Show Toss Data”
      }
       ]        
        ]
     },
     {
        Name:           "EnableSensor"
        Params:      
        [
           Name:        "SensorName",
           Type:        "string"        
        ]
     }
   ]
}
```
