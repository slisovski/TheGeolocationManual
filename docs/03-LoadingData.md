# Loading data {#loadingData}



The first step is to load your raw data into R. Different geolocator types (e.g. from different manufacturers or different series) provide raw data in different formats. And while there are functions available to read a whole range of formats, you may have to either write your own function, use simple read text utilities or get in touch with the package managers to write code that fits your format if it is not yet implemented.

The most frequently used geolocators provide files with the extension `.lux` (Migrate Technology Ltd), `.lig` (BAS, Biotrack) or `.glf` (Swiss Ornithological Institute). The functions `readMTlux`, `ligTrans` and `glfTrans` allows you to read these files. The documentations of the different packages may help to provide information on how to read other files (e.g. ?GeoLight). In most cases the raw data is stored in a text file that can also be read in to R using the base function `read.table()`.


<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">

<img src="images/note.png" style="display: block; margin: auto;" />

A short note on ***naming and saving of data files*** (final results and intermediate steps):
We have already discussed, that it makes sense to have a certain folder structure for the analysis of geolocators. It not only helps to keep track of all files and analysis, but most importantly it allows to run the same code for saving and reading of data once you defined a set of metadata information.
</div>

With the suggested data structure, we can then define metadata information on the individual, the species, the deployment location, and define the sub-folder for saving and extracting data files.


```r
ID <- "14SA"
Species <- "MerApi"

lon.calib <- 11.96
lat.calib <- 51.32

wd <- "data"
```

By using the above metadata we can use the `paste0` command to include this information in reading and writing of files.


```r
raw <- glfTrans(paste0(wd, "/RawData/", Species, "/", ID, ".glf"))
  names(raw) <- c("Date", "Light")
  raw$Light  <- log(raw$Light+0.0001) + abs(min(log(raw$Light+0.0001)))
head(raw)
```

```
                 Date Light
1 2015-07-10 00:00:00     0
2 2015-07-10 00:05:00     0
3 2015-07-10 00:10:00     0
4 2015-07-10 00:15:00     0
5 2015-07-10 00:20:00     0
6 2015-07-10 00:25:00     0
```

<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
<img src="images/important.png" style="display: block; margin: auto;" />

In this case it is required log transform the light data. In addition, we add a small value since the night readings are sometimes smaller than zero, values that cannot be log transformed.
</div>

Adding to the confusion of different raw data types, the read functions also provide different output. However, the most important columns are,

1. Date
2. Light

and these columns need to be in a specific format with Date being a `POSIXc` class and Light being `numeric` integers. Check if the structure of your data follows the required format with the function `str`. If not adjust Date format with `as.POSIXct(raw$Date, tz = "GMT")`.


```r
str(raw)
```

```
'data.frame':	112161 obs. of  2 variables:
 $ Date : POSIXct, format: "2015-07-10 00:00:00" "2015-07-10 00:05:00" ...
 $ Light: num  0 0 0 0 0 0 0 0 0 0 ...
```

<div style="background-color:rgba(0, 0, 0, 0.0470588); border-radius: 10px; text-align:left; vertical-align: middle; padding:6px 2; width: 700px; margin: auto:">
<img src="images/tip.png" style="display: block; margin: auto;" />

_Do I need to log-transform my raw light measurements?_
  
Log-transformation of the light intensities is helpful to visualize and inspect the data and for the twilight annotation process. It allows to focus at the low light values while seeing the whole light curve and thus makes sense for the tags that measure the full light spectrum (e.g. tags from Migrate Technology Ltd. and from the Swiss Ornithological Institute). If you proceed to analyse your data with FLightR, where you need the raw light intensities, there is no need to back-transform you light data as FLightR will do that automatically.
</div>

