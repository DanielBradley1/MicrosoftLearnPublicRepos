<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/using-microbit-and-makecode -->
<!-- Sitemap-Last-Modified: 2026-09-02 -->

# Tutorial: Using micro:bit and Make Code with Data Streamer

## Introduction

Microsoft [MakeCode](https://www.microsoft.com/en-us/makecode) is a helpful tool to learn or teach beginners of all ages how to code with the added bonus of allowing you to use software to control hardware devices.

This tutorial teaches you how to use the Make Code platform to write a program that sends live data from the BBC micro:bit to Microsoft Excel using the [Microsoft Data Streamer](https://aka.ms/data-streamer) add-in.

The example program we use in this tutorial prints the micro:bit accelerometer data into Excel. You can modify and adapt the basic program to work with other micro:bit sensors or external sensors.

## What you need for this project

### Hardware

- micro:bit microcontroller

Note

Windows 8 and newer don't need an another driver. For first-time programming a micro:bit on Windows 7, you need to [download the mbed drivers](https://os.mbed.com/docs/mbed-os/v6.15/program-setup/windows-serial-driver.html) for your computer.

- microUSB to USB cable

### Software

- Microsoft Excel Office 365
- Data Streamer Excel add-in enabled

  - Data Streamer is free with all subscriptions to Office 365

## Using the Make Code Blocks to Print Data to Serial

*The serial port on your computer is how Microsoft Data Streamer gathers data from external devices. This section shows you how to use the Make Code blocks to print data to the serial port.*

1. Plug in your micro:bit and go to the [Make Code](https://www.microsoft.com/en-us/makecode) website.
2. Select the "micro:bit" option and create a new file. The MakeCode block interface opens.
3. Add the HackingSTEM Data Streamer extension.

   ![Data Streamer Add-In.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/data-streamer-extension.png)


   Go to Extensions, located at the bottom of the code blocks, and search for **Data Streamer**. Select the HackingSTEM Data Streamer add-in to enable it.


   ![Set Baud Rate.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/set-baud-rate.png)

4. Back in the Block section of MakeCode, locate and open the yellow/orange **Data Streamer** blocks in the top section.

   ![Set Baud Rate On Start.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/set-baud-rate-on-start.png)

5. Set the Baud Rate by dragging the "Set Baud Rate" block into 'On Start'. Use the default setting \(9600\).

   Note

   Baud Rate is the speed at which the computer and the micro:bit communicate.

   ![Write Number Array 1.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/write-number-array-1.png)

6. Next, print data to serial with the **write number array** block. Drag into the **forever** block.

   ![Write Number Array 2.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/write-number-array-2.png)

7. In the **array of** slots, insert the data you want to print to serial. For this example, we're printing the micro:bit accelerometer x, y, and z values.

   ![Accelerometer Change Axes.png.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/accelerometer-change-axes.png)


   Accelerometer blocks are in the "Input" section. Remember to change the selected variable from "x" to y and z accordingly.


   ![Write New Line.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/write-new-line.png)

8. Print a new line after the array to denote the end of the data packet in Data Streamer by dragging the "write line" block from the Data Streamer section.

   ![Add Pause.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/add-pause.png)

9. Optional: Add a pause to more easily see the data as it is printed.

## Downloading Code onto the micro:bit

Once you've got the Make Code block program, you're ready to upload it to your micro:bit! You have two options.

Note

Option 1 is faster as it involves fewer steps. However, some computers might not permit you to download files directly onto the micro:bit, so you might need to use Option 2.

### Option 1

![Download Code Onto Micro:bit.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/download-code-onto-microbit.png)

Download and save the code file directly onto the micro:bit drive.

### Option 2

![Download Code Into Downloads 1.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/download-code-into-downloads-1.png)

Download and save the code file into a folder on your computer.

![Download Code Into Downloads 2.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/download-code-into-downloads-2.png)

Open File Explorer, navigate to the folder in which you saved the code file, then drag the code file onto the micro:bit drive.

## Using Data Streamer

You're ready to use Data Streamer! Open Excel and navigate to the Data Streamer tab.

![Connect A Device.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/connect-a-device.png)

1. Select "connect your device" to select the micro:bit USB device.

> \[!!NOTE\] If you see more than one device listed, unplug your micro:bit and observe which one disappears, then reconnect and select that USB device.

![Start Data.](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/media/using-microbit-and-makecode/start-data.png)

1. Select "start data" in the Data Streamer tab and navigate to the Data In sheet to see micro:bit accelerometer data printed in three separate columns.
2. You can plot the data to more easily observe changes over time and do data analysis with Excel’s built-in functions.

## More to Explore

### Excel Data Analysis

Experiment with different data visualization tools and built-in equations for data analysis. Here are some helpful Excel guides:

1. [Visualize Streaming Data in Excel](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/visualize-streaming-data-in-excel)
2. [Create Macros for Streaming Data](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-macros-for-streaming-data)
3. [Creating a Data Table](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-data-table)
4. [Create a Trial Storage Table](https://learn.microsoft.com/en-us/microsoft-365/education/data-streamer/create-trial-storage-table)

### HackingSTEM Projects

Check out the [full HackingSTEM activity library here](https://aka.ms/hackingstem).

Reach out to us if you have any questions, comments, or ideas! We also love seeing what folks build with our projects, so share your creations and tag us on social media!
