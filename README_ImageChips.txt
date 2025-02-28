Solar Panels in Satellite Imagery: Image Chips
________________________________________________


The folders in Maxar_HD_and_Native_Solar_Panel_Image_chips.zip contain image chips as part of the Solar Panels in Satellite Imagery dataset. 

The native image chips are from image Catalogue ID 1040050029DC8C00, with 0.0% cloud coverage, 3.9 degree off-nadir angle, and 42.2 degree sun elevation. 
The full image was originally collected on September 18, 2020 and has a maximum Ground Sampling Distance (GSD) of 31 cm.

The HD image chips were created by applying Maxar's HD product to the native imagery, resulting in HD images with a resolution of 15.5 cm.

The image chips are partitioned based on resolution: 31 cm native (image_chips_native) and 15.5 cm HD resolution imagery (image_chips_hd). 
In total, there are 2,542 object labels for each image type, following the same naming convention as the corresponding labels. 
The corresponding labels may be accessed at: 

http://doi.org/10.6084/m9.figshare.22081091

The naming convention for all image chips includes the name of the dataset, image type, tile identification number, minimum x bound, minimum y bound, and window size. 
The minimum bounds correspond to the origin of the chip in the full tile. An example image chip would be "solarpanels_hd_1__x0_0_y0_14027_dxdy_832.tif," 
which is an HD image chip from Tile 1 in the solar panel dataset, with a minimum x bound of 0, minimum y bound of 14,207 and window size of 832 by 832 pixels. 
The corresponding label for this example would be "solarpanels_hd_1__x0_0_y0_14027_dxdy_832.txt."

________________________________________________

Any use of the Maxar image chips must include the following statement: 
“© 2023 Maxar Technologies. This imagery is provided under the Creative Commons Attribution-NonCommercial 4.0 International Public License. (https://creativecommons.org/licenses/by-nc/4.0/legalcode#s3a1Ai)"