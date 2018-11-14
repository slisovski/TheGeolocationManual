


# Getting started {#start}

To analyse light-level geolocator data in R we need a couple of R packages as well as functions that allow to run our code. We created a package called _GeoLocTools_ that contains functions that are not nessesarily associated to a certain package but are used in this manual. Importantly the package can also run a check on you system (function: _setupGeolocation()_), detecting packages that are already on your computer and installs the missing tools directly from CRAN or GitHub.

The package requires _devtools_ (install if nessesary using the _install.packages()_ function). With _devtools_ on your system, you are able to download and built as well as install R packages directly from GitHub (e.g. _GeoLocTools_).


```r
library(devtools)
install_github("SLisovski/GeoLocTools")
```

You should now be able to load the package and run the `setupGeolocation()` function. We recommend to include this line at the beginning of each script you create for a geolocator analysis. Also check (every now and then), if there is a new version of _GeoLocTools_ available. And if that is the case, re-install the package using the same code you used for initial installation.


```r
library(GeoLocTools)
setupGeolocation()
```

if you see "You are all set!" in your console, the function ran succesfully and you are able to proceed.

Amongst dependencies, the following geolocator specific packages are loaded by this function:

- twGeos
- GeoLight
- probGLS
- SGAT
- FLightR


<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
* **What the $#@%!#!!!**
Although the _GeoLocTools_ should make things much easier, it is quite common for problems to arise when setting up your environment. A few frequent and frustrating issues are:
 
* **Outdated version of R**. If you are not running the latest (or at least a recent) version of R, then some of the packages might not be compatible. Use _sessionInfo()_ to see what version of R you are running. You can ususally track down the latest version of R at the R project webpage: [www.r-project.org](www.r-project.org). Note that you may have to reinstall all of your packages when you get a new version of R. So expect to spend a few minutes on the update.)
    
* **Missing libraries**. Some packages require that you have specific sofware libraries installed an accessible on your system. if you get a message like "configure: error: geos-config not found or not executable," you may be missing a library. Dealing with these issues may require some use of the Bash or Unix shell to install or locate a library. You can often find instructions for intalling new libraries by searching the internet, but if you do not feel comfortable installing stuff with the command line or you do not have permission to do so, you will probably need to seek some assistance from someone with IT credentials.
 
* **Typos**. Probably the most common error in R arises simply from typos. Even published scripts or manuals like these may contain small typos that prevent your script from running. 
</div>
