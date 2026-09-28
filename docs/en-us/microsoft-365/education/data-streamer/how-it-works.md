<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/how-it-works -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# What Is Data Streamer and What Does it Do?

Data Streamer is a bidirectional data transfer utility that streams data between Excel and a microcontroller via the serial port, or app to app via Universal Windows Platform \(UWP\) app service. This connection provides interactivity between a data source and the powerful calculation engine of Microsoft Excel. By using a set of commands and techniques users can design dynamic Excel dashboards to visualize data and control program flow.

## How Data Streamer Works

Data Streamer connects to a data source which can be a serial device, such as the Arduino UNO microcontroller, a UWP app via App Service, or an Electron app using a UWP middleman via App Service. The data source collects data and packages it into a Comma Separated Values \(CSV\) format and sends the data at a frequency to Data Streamer. Data Streamer displays the data into an Excel worksheet. Data can also be sent from Excel to the device or app.

![Microsoft Data Streamer data flow diagram.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/how-it-works/add-in-functional-diagram.png)

Once an app or device is connected, Data Streamer will generate 3 worksheets: Data In, Data Out, and Settings.

## Data In

CSV data is streamed into the **Data In** worksheet and Excel is updated whenever a new data packet is received.

## Data Out

Data that is entered into the **Data Out** worksheet is packaged in CSV format and sent to the connected device or app.

## Settings

Sets the parameters for the Data In and Data Out ranges and user settings. For more information, see [Workbook settings for Excel's Data Streamer add-in](https://support.office.com/en-us/article/workbook-settings-for-excel-s-data-streamer-add-in-e9ca60fe-a8ef-4124-8a0a-95df7ba62998).
