# PFCD + IGRI-2 Polarization Denoising and Demosaicking Codes
This is the source code of our proposed interpolation-based monochrome and color polarization denoising and demosaicking method, PFCD + IGRI-2, published in ICIP2025. <a href="http://www.ok.sc.e.titech.ac.jp/res/PolarDem/PDD.html" target="_blank">[Project]</a>.
 
## Demo

### - Settings
This denoising algorithm requires a gray-scale denoiser, and we used BM3D for denoising.
Please download BM3D [1] MATLAB code. <a URL=https://webpages.tuni.fi/foi/GCF-BM3D/BM3D.zip /a>.
Or, you can just run sample_download.m to obtain the codes. 

### - Dataset
Our 24-channel noisy-color-polarization dataset is downloadable from our project page <a href="URL">[Project]</a>.
Our 24-channel noisy-color-polarization dataset contains 12-channel noise-free color polarization data and 12-channel noisy color polarization data.

In such structure, 
Scene(number) - GT_0
              - GT_45
              - GT_90
              - GT_135
              - Test_0
              - Test_45
              - Test_90
              - Test_135

Here, 12-channel noise-free color-polarization data:  GT_0, GT_45, GT_90, GT_135. Use these data as ground-truth intensity images
And, 12-channel noisy color-polarization data: Test_0, Test_45, Test_90, Test_135. Use these data to make input polarization mosaic images

Here, we provide 24-channel full noisy-color-polarization dataset in three different noise-level condition which is low, medium, and high.
The average noise-level for each condition can be refer to Table 1 in our paper. 
To obtain same results as our main paper and supplementary material, 
please use the correct dataset (low, medium, high) with the corresponding noise level parameter

### - sample_download.m
To run our demo codes, please first run sample_download.m code to obtain sample 24-channel noisy-color-polarization data and BM3D settings to be used for the demo.


### - demo_monochrome.m
#### Input
8-channel monochrome-polarization data (G channel data): GT_0, GT_45, GT_90, GT_135, Test_0, Test_45, Test_90, Test_135

#### Mosaic pattern
90 ; 45
135  ; 0

### Denoising 
Set the noise-level parameter to be use to control denoising power. 
For MPFA denoising, noise-level for (G channel data) being used: sigma_g
In the code, we provide the noise-level parameter for high noise-level condition

#### Output
Demosaicked-denoised monochrome images for each polarization direction: Dem_0, Dem_45, Dem_90, Dem_135
Stokes parameter images derived from the demosaicked-denoised images: Dem_S0, Dem_S1, Dem_S2, Dem_DoP, Dem_AoP
CSV file containing PSNR values and angle RMSE for Table 2 in the paper

### - demo_color.m
#### Input
24-channel noisy-color-polarization mat data: mat = cat(3, GT_0, GT_45, GT_90, GT_135, Test_0, Test_45, Test_90, Test_135)

#### Mosaic pattern
R_90 ; R_45 ; G_90 ; G_45
R_135 ; R_0 ; G_135 ; G_0
G_90 ; G_45 ; B_90 ; B_45
G_135 ; G_0 ; B_135 ; B_0

### Denoising 
Set the noise-level parameter to be use to control denoising power. 
For CFA denoising, noise-level for (RGB channel data) being used: [sigma_r,sigma_g,sigma_b]
In the code, we provide the noise-level parameter for high noise-level condition


#### Output
Demosaicked-denoised RGB images for each polarization direction: Dem_0, Dem_45, Dem_90, Dem_135
Stokes parameter images derived from the demosaicked-denoised RGB images: Dem_S0, Dem_S1, Dem_S2, Dem_DoP, Dem_AoP
CSV file containing PSNR values and angle RMSE for Table 3 in the paper


## Reference
[1]K. Dabov, A. Foi, V. Katkovnik, and K. Egiazarian, 窶・Image denoising with block-matching and
3D filtering, Proc. SPIE Electronic Imaging, no.6064A窶・0, 2006.

The code is available only for research purpose. If you use this code for publications, please cite the following papers.

"Polarization Denoising and Demosaicking: Dataset and Baseline Method"
Muhamad Daniel Ariff Bin Abdul Rahman, Yusuke Monno, Masayuki Tanaka, and Masatoshi Okutomi,
IEEE International Conference on Image Processing (ICIP), PAGE, MONTH, 2025.

