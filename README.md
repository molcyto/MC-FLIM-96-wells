# MC-FLIM-96-wells
ImageJ macro for analyzing 96 wells plate FLIM data

## Requirements
Runs on 2019 FIJI and ImageJ 
The macros were tested on MacOS Mojave (10.14.5) running:
ImageJ v1.52p with Java 1.8.0_101 (64-bit) and on Fiji Version 2.0.0-rc-69/1.52p.

The macros were tested also on Windows 10 (version 1803 for x64-based systems) running:
ImageJ v1.52p with Java 1.8.0_112 (64-bit) and on Fiji version 1.52p running with Java 1.8.0 172 (64-bit)

BioFormats v.6.1.1 or v 6.1.0 (https://www.openmicroscopy.org/bio-formats/) must be installed in ImageJ. In Fiji this is installed automatically.

For usage see main manuscript Secondary screen - Fluorescence lifetime in mammalian cells.

## Usage
ImageJ & FIJI macro's can be dragged and droppped on the toolbar, which opens the editor from which the macros can be started.
Macros can also be loaded via Plugins->Macros menu, either use Edit or Run.

## Test data
Test can be downloaded from following zenodo repository : https://doi.org/10.5281/zenodo.3338150

[download test data](https://zenodo.org/record/3338150/files/Testdata_SupSoftw_4_FLIM_96wells.zip?download=1)

## Screenshot of input dialog for FLIM_96wells_macro_v14.ijm
<img src="https://github.com/molcyto/MC-FLIM-96-wells/blob/master/Screenshot%20FLIM_96wells_macro_v14.png" width="600">

## Explanation input dialog for FLIM_96wells_macro_v14.ijm
Note this is the same macro (but with other input settings) as Lifetimes14_for_Petridish.
- Work on current image or load from directory: Here you can choose to either use the current (e.g. a hyperstack with 96 positions each with 3 FLIM images: DC, tau(phi), tau(mod) ) image already displayed in ImageJ, or you load a file from a directory. The latter should be a hyperstack image with for instance 96 or 384 positions and 3 images per position: a DC image, a tau(phi) image and a tau(mod) image. These tau(phi) and tau(mod) images should have the fluorescence lifetimes in ps (1000x ns).
- Minimal/Maximal Tau for display (ns): Sets the minimal/maximal value of the lookup table for display of the lifetime values.

- Fixed threshold value or modal value threshold: Here you can choose how cells are recognized in the first time point image of the bleach series, either by selecting a fixed threshold intensity above which you assume there are cells, or a modal value determination that determines the modal (background) grey value and uses a statistical evaluation of pixels above this background.
- In case of fixed threshold, what intensity over the background: in case the previous choice was fixed, this is the lower intensity threshold for selecting cells in the analysis, otherwise this is a dummy input.
- Lower Threshold=number x Stdev + modal: In case a modal threshold was chosen for analysis, this value sets the lower intensity threshold for analysis based on the modal value + this input times the standard deviation found in the image. In case a fixed intensity threshold is chosen this is a dummy input.
- Keep cell ROIs: if selected an output image stack is generated with all analyzed cell ROIs per well.
- Create output 96/384 well tau image: if selected a colored bleach time to 50% of initial intensity image is generated.
- Low/high threshold for 50% time (2x): sets the minimal/maximal 50% bleach time for display in the colored bleach time multiwell image. 
- Automatic determination of thresholds: If selected, the previous 2 inputs will be overruled and the macro will scale the tau multiwell output image according to the minimal and maximal measured 50% bleach times.
- Create output 96/384 well non-bleached image: If selected, a multiwell image is added of the percent of initial intensity remaining in the last point of the acquired bleach time series. 
- Create output 96/384 well initial intensity image: If selected, a multiwell image is added of the detected average initial intensity. This is useful for inspecting wells with very bright or dim cells.
- Start row/Column: In case not an entire 96 well or 384 well is screened but a subsection of the plate, the first well (row, column) can be chosen. In case a 24 well plate is used, a 24 well plate output can be made by selecting E7 as first well.
- 96 wells or 384 wells: here the well plate format can be selected.


## links
[Visualizing heterogeneity](http://thenode.biologists.com/visualizing-heterogeneity-of-imaging-data/research/)
