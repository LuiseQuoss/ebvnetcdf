
<!-- README.md is generated from README.Rmd. Please edit that file -->

# ebvnetcdf package

<!-- badges: start -->

<!-- badges: end -->

This package can be used to easily access the data of the EBV NetCDFs
which can be downloaded from the [Geobon
Portal](https://portal.geobon.org/). It also provides some basic
visualization. Advanced users can build their own NetCDFs with the EBV
standard.

## Installation

You can install the ebvnetcdf packages with:

``` r
#visibility needs to be set to public first! Does not work right now. 
devtools::install_gitlab("lq39quba/ebvnetcdf", host='git.idiv.de') 
```

## Working with the package - a quick intro

### Take a very first look at the file

With the following two functions you get a basic impression what data
you can get from the EBV NetCDF. First we take a look at some basic
properties of that file.

``` r
library(ebvnetcdf)

file <- paste0(path.package("ebvnetcdf"),"/extdata/cSAR_idiv_v1.nc")
#file <- system.file("external/cSAR_idiv_v1.nc", package="raster")

#prop.file <- ebv_properties(file)
```

Now let’s get all possible paths to the datacubes. The resulting
dataframe including the paths and also descriptions of e.g. metric and
or scenario - take a look\!

``` r
#datacubes <- ebv_datacubepaths(file)
```

We will get the properties of one specific datacube - fyi: the result
also holds the general file properties from above. This time you get the
warning that the value\_range does not exists. So don’t take the
displayed value\_range
seriously.

``` r
#prop.dc <- ebv_properties(file, datacubes[1,1], verbose=T)
```

### Plot the data to get a better impression

``` r
# Plot a map of the datacube that we just looked at - it has 12 timesteps, mabe look at two different ones?
# dc <- datacubes[1,1]
# ebv_plot_map(file, dc, timestep = 1)
# ebv_plot_map(file, dc, timestep = 6)

# what was the data about again? Check the properties!
# prop.dc@title
# And the datacube?
# prop.dc@entity_information@label

# It's nice to see the global distribution, but how it the change of that datacube (non forest birds) over time?
# Let's take a look at the average. The function returns the values, catch them!
# averages <- ebv_plot_indicator(file, dc)

# It would be cool to have that for other indicators as well? Well you have to wait for an update of the package.
# Or maybe implement it yourself using the functions coming up next?
```

### Read the data from the files to start working

### Take a peek on the creation of an EBV NetCDF