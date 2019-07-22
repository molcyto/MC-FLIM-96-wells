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
- Fixed background value or modal value background: Here you can choose how cells are recognized in the DC image, either by selecting a fixed threshold intensity above which you assume there are cells, or a modal value determination that determines the modal (background) grey value and uses a statistical evaluation of pixels above this background.
- In case of fixed BG, low threshold for Intensity: in case the previous choice was fixed, this is the lower intensity threshold in the DC image for selecting cells in the analysis, otherwise this is a dummy input.
- In case of modal BG: low Threshold=number x Stdev + modal: In case a modal threshold was chosen for analysis, this value sets the lower intensity threshold for analysis based on the modal value + this input times the standard deviation found in the image. In case a fixed intensity threshold is chosen this is a dummy input.
- Minimal object size for lifetime analysis (pixels): The smallest object in number of pixels that is selected for lifetime determination.
- High threshold for Intensity: Upper intensity limit in DC image for lifetime analysis. Pixels with higher intensity (e.g. due to overexposure) will be rejected.
- Gamma for Intensity: Gamma value for displaying output image. A gamma value of 1 will produce standard output. A gamma value<1 will emphasize more the cells with lower fluorescence intensity.
- Modulation frequency (MHz): Here use the modulation frequency in MegaHertz for drawing the polar plots.
- Threshold intensity image: if selected, in the output the DC image will be thresholded according to the background/threshold settings.
- Exclude analysis for I>Ihigh: Excludes analysis of pixels with output intensity over this intensity limit (the value is set as high threshold for intensity). Also histograms are scaled to this value.
- Automatic determination of Ihigh: if selected the macro will define the maximum value for scaling automatically
- Include 2D histograms: If selected the output image stack will contain 2D histograms if intensity vs lifetime and polar plots.
- Make additional image stack: If selected it makes an additional output stack of the analyzed data without text labels.
- Time between FLIM stacks: This is a dummy input for 96 wells FLIM analysis, but it can be used for analyzing FLIM timelapse hyperstacks.
- Time lapse units: This is a dummy input for 96 wells FLIM analysis, but it can be used for analyzing FLIM timelapse hyperstacks.
- Display only Tau(phi), only Tau(mod), or both: Depending on what is selected the output image will contain the information on Tau(phi), Tau(mod) or both.
- Colortable for Lifetime Images: Different color tables can be selected for the output lifetime images. 
- Colortable for Intensity Images: Different color tables can be selected for intensity images in the output. 
- Background: Sets the color of the background in the output image.
- Foreground: Sets the color of the foreground and text in the output image. 
- Import/export metadata from FLIM screen: If selected it tells the macro it is dealing with multiwell data. The metadata should contain the frame number, well position, name, exposure time and comment for each acquired FLIM image according to this format: "frame0001=A1, mScarlet, 100.0, U2OS cells" in the metadata (without the quotes). The frame number should refer to frame number in the image hyperstack, A1 to the position in the well, mScarlet is the sample ID, 100.0 is the exposure time and U2OS cells is a comment. Each frame number/well position should have a separate line in the metadata.
- Export logfile with lifetime data from FLIM screen: If selected a tab delimited text file is generated with the quantified data from the multiwell plate. If saved as .csv file it can be directly imported into Microsoft Excel.
- 96 wells or 384 wells: this selects the format of the well plate.


## links
[Visualizing heterogeneity](http://thenode.biologists.com/visualizing-heterogeneity-of-imaging-data/research/)
