<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-macros-for-streaming-data -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Tutorial: Creating Macros for Streaming Data

In this tutorial, you learn how to:

- Create modules for organizing macros
- Declare reference functions
- Create macros for saving trials

## Prerequisites

- Sensor data previously streamed into Data In page of Excel
- Trial data table created and structured
- Developer ribbon tab enabled

## Create Modules in VBA

<iframe src="https://learn-video.azurefd.net/vod/player?id=d64c2ff6-bc24-4557-84ba-632833f0db6b" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Select **Developer > Visual Basic** to open Visual Basic for Excel
2. Select **Insert > Module** to add a module for storing macros
3. In the **Properties** tab, rename *Module1* as desired. This will store your references.
4. Repeat steps 2 and 3, also renaming as desired. This will store your active macros.

## Declare Reference Functions

<iframe src="https://learn-video.azurefd.net/vod/player?id=4533c378-956d-4741-8e51-9ff31779510c" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. In the Project window, select the module desired for your references.
2. In the code window, start by declaring `Option Explicit`.
3. Below this, define the sheet name where your table is stored.
4. Repeat step 3 for the name of your table.

   ```vba
    Option Explicit
    Public Const sheetname = "Backend"
    Public Const tblname = "Tbl_Backend"
    Public Const sensorcount = 2
   ```

5. Use the Function command to create a shorthand reference for your table.

   ```vba
   Function BT_tbl() as ListObject
           Set BT_tbl = Sheets(sheetname).ListObjects(tblname)
   End Function
   ```

6. Use the Function command to create a shorthand reference for the streaming columns of each sensor.

   ```vba
   Function Live_CH(snum As Integer) As Range
           Set Live_CH = BT_tbl.ListColumns("CH" & snum).DataBodyRange
   End Function
   ```

7. Use the Function command to create a shorthand reference for the trial columns each sensor.

   ```vba
   Function Trial_CH(snum As Integer, tnum As Integer) As Range
           Set Trial_CH = BT_tbl.ListColumns("CH" & snum & "_T" & tnum).DataBodyRange
   End Function
   ```

These functions allow the user to easily reference objects and ranges in the workbook, making the active macros substantially easier to write and understand.

## Create Macros for Saving Trials

<iframe src="https://learn-video.azurefd.net/vod/player?id=b1d6261e-0ca9-4728-8886-76f0ac07b14f" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. In the Project window, select the module desired for your references.
2. In the code window, start by declaring the name for your save trial macro, using a sub.vba

   ```vba
   Sub SaveTrial()

   End Sub
   ```

3. To allow the macro to understand which trial to reference based on the clicked button, insert the following code into this sub

   ```vba
   Sub SaveTrial()
           Dim tnum As Integer
           tnum = Right(ActiveSheet.Shapes(Application.Caller).Name,1)
   End Sub
   ```

4. Finally, for each sensor, add a line of code to make the desired trial column equal to its corresponding streaming column.

   ```vba
   Sub SaveTrial()
           Dim Num As Integer
           Num = Right(ActiveSheet.Shapes(Application.Caller ).Name,1)
           References.BT_CH1_Trial(Num).Value = References.BT_CH1.Value
           References.BT_CH2_Trial(Num).Value = References.BT_CH2.Value
   End Sub
   ```

With this macro written, the user can now assign the macros to objects.

## Assign Macros to Objects

<iframe src="https://learn-video.azurefd.net/vod/player?id=66ef0467-e715-4c5f-9c13-2f5d03fc924b" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

1. Go to the Excel workbook, to the worksheet that contains your table and named objects.
2. Select all trial buttons by holding **SHIFT** and selecting each object.
3. Open the right-click menu on these objects and select **Assign Macro...**
4. Select the **SaveTrial** macro.

When clicked, these buttons will now trigger the **SaveTrial** macro, copying data from the live data columns to the desired trial columns.
