
# Your contribution {#contribution}

We do consider this document to be a community endeavour for which we have given a starting point. We apprechiate any contribution in terms of thoughs on the current version, changes and additions.
Arguably, your expereince with geolocation is valuable for the community and by adding it to this manual it can help users significantly. Fortunately, the GitHub and RStudio environemnts make it (relatively)
easy to give access to the source code of this manual and to _push_ your changes directly into the online version

It may seem combersome at first but it is worth the effort to get familiar with GitHub and make use of the massive potential of version control and developing as well as publishing code,
such as this manual.

If you have not already created an account do so (www.github.com). And while RStudio has implemented a Git environment that allows direct communication with GitHub, we recommend to download the GitHub Desktop application
if you are new to this world of version control. The application can be downloaded from: https://desktop.github.com/.

Once you have installed and loged into your account you can _clone_ repositories that are already on GitHub or _create_ new repositories via the file menu.

To get started with _The Manual_, choose _clone a repository_, define the local path where the data should be saved and type in _slisovski/TheGeolocationManual_ and press _Clone_:
  
  <img src="images/GitHub1.png" style="display: block; margin: auto;" />

Navigate to the local folder that should now contain a subfolder called _TheGeolocationManual_. In this subfolder you will find a RStudio project file called "TheGeolocationManual.Rproj". Open this file with a double click.
In RStudio you are now working within this folder and in the _Files_ window, you will find all the files that are part of _The Manual_.

<img src="images/GitHub2.png" style="display: block; margin: auto;" />

The important files are the **.Rmd** files that contain all the code and text of _The Manual_. If you intent to edit something in the e.g. GeoLight section, open the _05-GeoLight.Rmd_ file and start editing. Make sure to save changes once you are done.

Back in the GitHub Application you can see all changes you have made that are different to the version your _fetched_ from GitHub:

<img src="images/GitHub3.png" style="display: block; margin: auto;" />

<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
<img src="images/caution.png" style="display: block; margin: auto;" />
Make sure to _fetch_ (pressing _Fetch origin_) before you start making any edits in RStudio. This gives you the newest version and avoids conflicts with edits from other users!
</div>

It is important(required) to provide a comment for your commit (your changes). Please use somthing that makes sense and allows others to have a rough idea what your changes entail. Feel free to provide more information in the _Decription_ such as "I have removed an obvious bug in line xx" or, "I have added text in the calibration section, please review!". Next, press commit to **contribution**.

<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
<img src="images/important.png" style="display: block; margin: auto;" />
GitHub allows to have different _branches_. This is a creat invention that is immensely usefull for such endavours; we can keep the current online version of _The Manual_ untouched but make edits etc. to the code. Once we are happy with new edits and maybe with a complete new version we can _merge_ the branches and update the _master_ branch and thereby the online version. This makes sure that the online version is always running and that changes can be reviewed and revised before going online.
</div>

To make sure that your changes will be submitted to the **contribution** branch select the correct branch in the menu:

<img src="images/GitHub4.png" style="display: block; margin: auto;" />

The press _Commit to **contribution**_ and if your want this commit to go online press _Push origin_.

<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
<img src="images/important.png" style="display: block; margin: auto;" />
_Commit_ only logges the changes into the version control file on your computer, you have to _Push origin_ to make sure that it is submitted to GitHub and visible for all other users!
</div>
