# Structure of the manual {#structure}

This manual should allow users with limited knowledge in R coding to perform a state-of-the-art analysis of geolocator data. Thus, we start with the very basics of loading packages  and data \@ref(loadingData) Starting with the initial data editing steps, which we call twilight annotation \@ref(twilight), we provide instructions on how to use several prominent analysis packages, illustrate the general analysis workflow using example data, and provide some recommendations for how to visualize and present results. We do not cover every available analysis package but focus on what we percieve to be the most frequently used tools, which are GeoLight \@ref(GeoLight), probGLS \@ref(probGLS), SGAT \@ref(SGAT) and FLightR \@ref(FLightR). The manual concludes with a section on data repositories such as Movebank that allows storing and shring geolocator tracks  \@ref(repositories).

## The datasets {-}

To illustrate the capabilities of the different packages, discuss the potential pitfalls, and provide some recommendations, we will use raw geolocator data from four individuals of different species. All used tag data and the results as well as the code for the analyses has been uploaded onto Movebank unter study: Light-Level Geolocation Manual.


TagID    |  Species             | Folder      |   Lon/Lat   | Tag type                          
-------  | -------------        | ----------- | ----------- | ---------------------- 
M034     | Red-backed Shrike    | LanCol      | 12.33/55.98 | Integio (Migrate Technology Ltd.)
14SA     | European bee-eater   | MerApi      | 11.96/51.32 | PAM (Swiss Ornithological Institute)
PasCir01 | Purple martin        | PasCir      | 33.9/-96.80 | Custom (by Eli Bridge)
2655     | Brünnich’s guillemot | UriLom      | 15.15/78.17 | Lotek


Although all of these tag types record light values over time, they differ in some key details. First, tags often differ in the frequency at which they write/log data. Many tags collect a reading every minute and store the maximal light value every 5 or 10 minutes. Other may store a maximum every 2 minutes. The tag that yielded the Purple martin data set, averaged 1min readings every 10min instead of taking a maximum. These four tags also differ in their sensitivity and how they record light levels. Some tags are sensitive only at low light levels and quickly “max out” when they experience a lot of light. As such, their light-levels do not have units and are simply an index of light intensity. The Integio tags can record unique light values for all natural light levels on earth, and they store lux values that range from 0 to ~70,000. Depending on the tag type, you may have to perform some preliminary steps such as log-transforming your data or time shifting light values for sunsets (we will provide details while working on the specific datasets).

## Reproducing the analyses {-}

This manual contains code that can be copy pasted into an R script and executed to reproduce the results. In order to do so, you need to download the raw data as well as annotated twilight files used in this manual. The data need to be in a specific structure of folders and we do recommend you have a similar structure for your own analysis. During the processing of the data we save intermediate steps that allow us to step into the next analysis step without going through all initial and often time consuming parts. Having your raw data and your results in a well structured fomr, becomes especially important if you run analyses for many tags of the same or different species. It is also recommended that you create a single R script for each analysis (e.g. for each individual and each analysis using different tools). For example, you can name the R scripts using the tag id and the tool e.g. `14SA_SGAT.R`. Since this manual is dealing with tags from different species, the following structure with sub-folders per speces (first three letters of the genus name and the species name) is setup within the main folder (called _data_):


- RawData
    + LanCol
    + MerApi
    + PasCir
- Results
    + LanCol
    + MerApi
    + PasCir
- RCode
    + LanCol
    + MerApi
    + PasCir


You can download the folders with the raw data as well as the annotaded twilight files directly via R and extract into a _data_ folder.


```r
url <- "https://github.com/slisovski/TheGeolocationManual/raw/master/download.zip"

temp <- tempfile()
download.file(url, temp)
unzip(temp, exdir = "data")
```

We also recommend using R Studio and creating a project (File -> NewProject). Alternatively, you can set the working directory using the `setwd` function. With the _data_ folder in your project folder (or more in general in your working directory) you should be able to run the code provided in this manual.

We also recommend to use _R Studio_ and to create a project (File -> NewProject). Save the project file into the existing _Data_ folder. This makes sure that _Data_ is your working directory and it will remain the working directory even if the folder moves around on your drive. Alternatively, you can set the working directory using the `setwd` function. With the suggested folder structure and the raw data and the annotaded twiligth files you should be able to run the code provided in this manual.
