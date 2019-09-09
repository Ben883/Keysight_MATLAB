# MATLAB Keysight M9383B & M9384B Virtual Measurement Guide

This program is designed to be an additional tool for Keysight VXG users and developers. This program automates the measurements in the VXG Measurement Guide and has two additional functions to automate EVM and ACP vs. Power.

## Required Equipment

**a)**	Keysight X-Series Analyzer with Software version A.24.57 or later. (Note: Some measurements go up to 44 GHz and they will be cut off if your analyzer cannot go that high)

**b)**	MATLAB 2019b or later installed on PC or X-Series Analyzer.

**c)**	VSA version 24.20.134.0 or later (VSA portion only) 

**d)**	A VXG (Single or Dual Channel) Vector Signal Generator.

**e)**	Physical connections specified by the official M9384B Measurement Guide.

**f)**	LAN connections to both instruments you wish to control.

**g)**	The waveform and settings files specified in the Measurement Guide. The measurement guide and other documentation can be found [here](https://www.keysight.com/main/techSupport.jspx?nid=-31849.1261271&pid=2976298&cc=US&lc=eng&pageMode=PL).

**h)**	Keysight IO Libraries (Keysight Connection Expert)

## Connecting to Your Instruments

When the program first launches, it will pull all of your VISAs from Keysight Connection Expert. Once you select the instruments you want to use, press the `Connect to Instruments` button. Once you are succesfully connected, the light in the bottom right corner of the GUI will turn green.

## Connecting to VSA

For connecting to VSA, you must first open VSA **seperately from X-Apps** (opening VSA in X-Apps disables SCPI communication with VSA)

In VSA, go to `Utilities` >> `SCPI Preferences`

<img width="500" alt="rename_screenshot" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/VSA%20User%20Pref.PNG?raw=true">

The socket location must be changes as 5025 will be in use by the analyzer that is communicating with VSA, (5024 or 5026 is safe). Next, select `Configure External SCPI Server`. Enable SCPI on startup will help so that you don't have to go through this process every time. This is also where you want to get the VISA address for you VSA application.

<img width = "400" alt="VSA_SCPI_server" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/VSA%20SCPI%20Conf.PNG?raw=true">

Once these steps have been completed, select the `Connect to VSA` button in the Virtual Measurement Guide and a message will appear saying "Connected to `your device info`"

### TIP:
You can change the VSA Visa that is preloaded by editing the .mlapp file and changing the value of app.VSAVisaEditField

<img width = "600" alt="VSA_SCPI_server" src="https://github.com/Ben883/Keysight_MATLAB/blob/master/images/ChangingVISA.png?raw=true">

## Additional Features

On the main GUI, there is an `SA Display` switch. This switch allows you to turn the display of your Signal Analyzer on and off. This can drastically increase the speed of reading trace data.

There is also an `Optimize EVM` button which only works if you are in one of the 5G NR measurements. This button will configure the analyzer to optimize EVM and return the new data in tabular form.

Above the measurement choices are two text boxes named `Time to Run` and `Total Time`. `Time to Run` tells you how long that specific measurement took and `Total Time` tells you how long that batch of measurements took

**Making Measurements**

In order to make any measurement that reads a waveform/setup file (Such as the 5G NR measurements) you will need to ensure that the file paths are correct for your instrument. The preset file locations are the standard files preinstalled on the VXG. If you do not have these waveforms on your instrument, they are also located [here](need to add link). If you need to modify the file directories in the code, right-click the .mlapp file and select edit.

## Rename this repository to publish your site

We've already set-up a GitHub Pages website for you, based on your personal username. This repository is called `hello-world`, but you'll rename it to: `username.github.io`, to match your website's URL address. If the first part of the repository doesn’t exactly match your username, it won’t work, so make sure to get it right.

Let's get started! To update this repository’s name, click the `Settings` tab on this page. This will take you to your repository’s settings page. 

![repo-settings-image](https://user-images.githubusercontent.com/18093541/63130482-99e6ad80-bf88-11e9-99a1-d3cf1660b47e.png)

Under the **Repository Name** heading, type: `username.github.io`, where username is your username on GitHub. Then click **Rename**—and that’s it. When you’re done, click your repository name or browser’s back button to return to this page.

<img width="1039" alt="rename_screenshot" src="https://user-images.githubusercontent.com/18093541/63129466-956cc580-bf85-11e9-92d8-b028dd483fa5.png">

Once you click **Rename**, your website will automatically be published at: https://your-username.github.io/. The HTML file—called `index.html`—is rendered as the home page and you'll be making changes to this file in the next step.

Congratulations! You just launched your first GitHub Pages website. It's now live to share with the entire world

## Making your first edit

When you make any change to any file in your project, you’re making a **commit**. If you fix a typo, update a filename, or edit your code, you can add it to GitHub as a commit. Your commits represent your project’s entire history—and they’re all saved in your project’s repository.

With each commit, you have the opportunity to write a **commit message**, a short, meaningful comment describing the change you’re making to a file. So you always know exactly what changed, no matter when you return to a commit.

## Practice: Customize your first GitHub website by writing HTML code

Want to edit the site you just published? Let’s practice commits by introducing yourself in your `index.html` file. Don’t worry about getting it right the first time—you can always build on your introduction later.

Let’s start with this template:

```
<p>Hello World! I’m [username]. This is my website!</p>
```

To add your introduction, copy our template and click the edit pencil icon at the top right hand corner of the `index.html` file.

<img width="997" alt="edit-this-file" src="https://user-images.githubusercontent.com/18093541/63131820-0794d880-bf8d-11e9-8b3d-c096355e9389.png">


Delete this placeholder line:

```
<p>Welcome to your first GitHub Pages website!</p>
```

Then, paste the template to line 15 and fill in the blanks.

<img width="1032" alt="edit-githuboctocat-index" src="https://user-images.githubusercontent.com/18093541/63132339-c3a2d300-bf8e-11e9-8222-59c2702f6c42.png">


When you’re done, scroll down to the `Commit changes` section near the bottom of the edit page. Add a short message explaining your change, like "Add my introduction", then click `Commit changes`.


<img width="1030" alt="add-my-username" src="https://user-images.githubusercontent.com/18093541/63131801-efbd5480-bf8c-11e9-9806-89273f027d16.png">

Once you click `Commit changes`, your changes will automatically be published on your GitHub Pages website. Refresh the page to see your new changes live in action.

:tada: You just made your first commit! :tada:

## Extra Credit: Keep on building!

Change the placeholder Octocat gif on your GitHub Pages website by [creating your own personal Octocat emoji](https://myoctocat.com/build-your-octocat/) or [choose a different Octocat gif from our logo library here](https://octodex.github.com/). Add that image to line 12 of your `index.html` file, in place of the `<img src=` link.

Want to add even more code and fun styles to your GitHub Pages website? [Follow these instructions](https://github.com/github/personal-website) to build a fully-fledged static website.

![octocat](./images/create-octocat.png)

## Everything you need to know about GitHub

Getting started is the hardest part. If there’s anything you’d like to know as you get started with GitHub, try searching [GitHub Help](https://help.github.com). Our documentation has tutorials on everything from changing your repository settings to configuring GitHub from your command line.
