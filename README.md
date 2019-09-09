# MATLAB Keysight M9383B & M9384B Virtual Measurement Guide

This program is designed to be an additional tool for Keysight VXG users and developers. This program automates the measurements in the VXG Measurement Guide and has two additional functions to automate EVM and ACP vs. Power.

## Required Equipment

**a)**	Keysight X-Series Analyzer with Software version A.24.57 or later. (Note: Some measurements go up to 44 GHz and they will be cut off if your analyzer cannot go that high)

**b)**	MATLAB 2019b or later installed on PC or X-Series Analyzer.

**c)**	VSA version 24.20.134.0 or later (VSA portion only) 

**d)**	A Keysight VXG (Single or Dual Channel) Vector Signal Generator.

**e)**	Physical connections specified by the official M9384B Measurement Guide.

**f)**	LAN connections to both instruments you wish to control.

**g)**	The waveform and settings files specified in the Measurement Guide. The measurement guide and other documentation can be found [here](https://www.keysight.com/main/techSupport.jspx?nid=-31849.1261271&pid=2976298&cc=US&lc=eng&pageMode=PL).

**h)**	Keysight IO Libraries (Keysight Connection Expert)

## Connecting to Your Instruments

When the program first launches, it will pull all your VISAs from Keysight Connection Expert. Once you select the instruments you want to use, press the `Connect to Instruments` button. Once you are successfully connected, the light in the bottom right corner of the GUI will turn green.

## Connecting to VSA

For connecting to VSA, you must first open VSA **seperately from X-Apps** (opening VSA in X-Apps disables SCPI communication with VSA)

In VSA, go to `Utilities` >> `SCPI Preferences`

<img width="500" alt="rename_screenshot" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/VSA%20User%20Pref.PNG?raw=true">

The socket location must be changes as 5025 will be in use by the analyzer that is communicating with VSA, (5024 or 5026 is safe). Next, select `Configure External SCPI Server`. Enable SCPI on startup will help so that you don't have to go through this process every time. This is also where you want to get the VISA address for your VSA application.

<img width = "400" alt="VSA_SCPI_server" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/VSA%20SCPI%20Conf.PNG?raw=true">

Once these steps have been completed, select the `Connect to VSA` button in the Virtual Measurement Guide and a message will appear saying "Connected to `your device info`"

### TIP:
You can change the VSA Visa that is preloaded by editing the .mlapp file and changing the value of app.VSAVisaEditField

<img width = "600" alt="VSA_SCPI_server" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/ChangingVISA.png?raw=true">

## Additional Features

On the main GUI, there is an `SA Display` switch. This switch allows you to turn the display of your Signal Analyzer on and off. This can drastically increase the speed of reading trace data.

There is also an `Optimize EVM` button which only works if you are in one of the 5G NR measurements. This button will configure the analyzer to optimize EVM and return the new data in tabular form.

Above the measurement choices are two text boxes named `Time to Run` and `Total Time`. `Time to Run` tells you how long that specific measurement took and `Total Time` tells you how long that batch of measurements took

## Making Measurements

In order to make any measurement that reads a waveform/setup file (Such as the 5G NR measurements) you will need to ensure that the file paths are correct for your instrument. The preset file locations are the standard files preinstalled on the VXG. If you do not have these waveforms on your instrument, they are also located [here](need to add link). If you need to modify the file directories in the code, right-click the .mlapp file and select edit. 

<img width="500" alt="rename_screenshot" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/EditApp.png?raw=true">

Once you are in app editor:

**1)** Select `code view`

**2)** Select `functions` and go to the measurement you wish to modify

**3)** In the SCPI commands, you can edit the file directories to match those on your instrument

Once the file directories are correct for your instrument and you are connected to these instruments, simply select the measurement you want to perform and press the `Measure` button.

Keep in mind that VSA must be launched and connected, as shown by the connecting VSA section of this document, before you can perform any of the VSA measurements.

## Misc. Programs with Example
EVM and ACP vs. Power both follow the same process; increment the power level of the source and take the corresponding measurement to be graphed after it has completed.

EVM vs. Power uses the waveform and setup files from `Setting Up a 1 CC 28 GHz EVM Measurement` in `5G NR Using X-Apps` and ACP vs. Power uses the waveform file and setup from `Setting Up a 1 CC 3.5 GHz ACP Measurement`. An example of using these functions is shown below.

**1)** Edit the file paths to match your instrument and connect to your instruments (as shown in *Making Measurements* section

**2)** Navigate to the `Misc.` tab and select `EVM vs. Power (x_apps)` or `ACP vs. Power (x_apps)` 

**3)** Select your amplitude range and step size

<img width="500" alt="rename_screenshot" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/evmvspow.PNG?raw=true">

**4)** Once the measurements are complete, the results will be graphed.

<img width="500" alt="rename_screenshot" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/acpvspow.PNG?raw=true">

# Additional Resources

The Programmers Manual for remote programming of Keysight Signal Analyzers from MATLAB can be found [here.](http://literature.cdn.keysight.com/litweb/pdf/N9060-90027.pdf)

To learn more about demonstrating or selling MATLAB together with Keysight instruments, visit:

**1)** [Keysight's product page for MATLAB](www.keysight.com/find/matlab)

**2)** [Keysight's library of MATLAB demonstration videos](www.keysight.com/find/matlab_videos)

**3)** [Mathworks product page with demos, drivers, and more](www.mathworks.com/keysight)
