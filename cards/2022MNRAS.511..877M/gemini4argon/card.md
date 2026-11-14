# Subterahertz radius and limb brightening of the Sun derived from SST and ALMA

`2022MNRAS.511..877M` | Monthly Notices of the Royal Astronomical Society 2022 | first author: Menezes, Fabian | arXiv: 2111.15261 | DOI: 10.1093/mnras/stab3501

Card schema 1.0 | model gemini-4-argon | depth full | type archival_reuse

## Science

- Fields: sun
- Question: Determine the average radius and limb brightening of the Sun at 100, 212, 230, and 405 GHz using SST and ALMA single-dish observations, and investigate how antenna beam size and limb brightening level affect radius measurements from the half-power and inflection-point methods.  
  > "In this work, we determined the average radius and limb brightening at 100, 212, 230, and 405 GHz, using data from the Solar Submillimeter Telescope and ALMA’s single-dish observations." (Abstract); "We investigate how the antenna beam size and the limb brightening level, $L\!B$, can affect the radius measurements using both methods." (Abstract)
- Target **Sun**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00020.SV, 2016.1.00050.S, 2016.1.00070.S, 2016.1.00156.S, 2016.1.00166.S, 2016.1.00182.S, 2016.1.00201.S, 2016.1.00202.S, 2016.1.00423.S, 2016.1.00572.S, 2016.1.00788.S, 2016.1.01129.S, 2016.1.01408.S, 2016.1.01532.S, 2017.1.00009.S, 2017.1.00870.S, 2017.1.01138.S
- bands: Band 3 (84–116 GHz, 100 GHz) and Band 6 (211–275 GHz, 230 GHz)  
  > "From ALMA, we use fast-scan single-dish maps obtained in Band 3 (84–116 GHz, hereafter, 100 GHz) and in Band 6 (211–275 GHz, hereafter, 230 GHz), described by (cite: white17)." (Solar maps)
- frequencies and spectral setup: 100 GHz (Band 3: 84–116 GHz) and 230 GHz (Band 6: 211–275 GHz)  
  > "From ALMA, we use fast-scan single-dish maps obtained in Band 3 (84–116 GHz, hereafter, 100 GHz) and in Band 6 (211–275 GHz, hereafter, 230 GHz), described by (cite: white17)." (Solar maps)
- continuum bandwidth: _not stated_
- arrays: 12-meter single-dish  
  > "These maps were made during four solar observation campaigns from 2015 to 2018 by ALMA’s 12-meter single-dish." (Solar maps)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: nominal HPBW0: 58″ (100 GHz), 25″ (230 GHz); Gaussian-fitted HPBW: 1.1′ (100 GHz), 0.44′ (230 GHz)  
  > "ALMA’s single-dish nominal half-power beam widths, HPBW${}_0$, are 58″ at 100 GHz and 25″ at 230 GHz." (Antenna beam); "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively." (Antenna beam)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 to 2018  
  > "These maps were made during four solar observation campaigns from 2015 to 2018 by ALMA’s 12-meter single-dish." (Solar maps)
- pi or archival as stated: archival (science verification and science archive)  
  > "The images were extracted from FITS files provided by ALMA’s science verification page and ALMA science archive page[^3]." (Solar maps)
- Other facility **Solar Submillimeter-wave Telescope (SST)**: 2148 maps at 212 GHz (receiver #3) and 1256 maps at 405 GHz (receiver #5) from 2015 to 2018  
  > "Since structural antenna deformations change the expected size and form of the beams (cite: valle21), in this study we only use receivers #3 (212 GHz) and #5 (405 GHz), which beams have less deformation compared to the other ones." (Radio Telescopes); "During the years of 2015 to 2018, a total of 2148 maps at 212 GHz and 1256 maps at 405 GHz were selected for this study (the selection criteria are described in Section [3](#sec:rad_determ))." (Solar maps)
- External data: Canonical optical apparent solar radius (959.63″)  
  > "The canonical value at optical wavelengths of the mean apparent solar radius is 959.63″ (cite: auwers1891)." (Introduction) [from (cite: auwers1891)]
- External data: Limb brightening measurements at 100 and 230 GHz  
  > "At 100 GHz, (cite: selhor19) found that the average brightness above $T\!_{qS}$ was 6.1% $\pm$ 2.8% at the North pole and 5.1% $\pm$ 2.7% at the South pole; whereas at 230 GHz, the average values were 9% $\pm$ 5% and 9% $\pm$ 4%, respectively for the South and North poles." (Introduction); "Also, SSC profiles $L\!B$~conv~ at 100 and 230 GHz are respectively lower, however close to the 10.5% and 17.8% levels reported by (cite: selhor19)." (Limb brightening estimate) [from (cite: selhor19)]
- External data: SSC 2-D solar atmospheric model predictions for radius and brightness temperature profiles  
  > "Also listed on the last two columns of Table [\[tab:radii\]](#tab:radii) are the predicted values of the solar radius, *R*~ssc~, and the respective convolved values, $R_\mathrm{ssc}^\mathrm{conv}$, using the SSC atmospheric model (cite: selhor05), further explained in the next section." (Radius Determination) [from (cite: selhor05)]
- Simulation/model as data: 153 synthetic brightness temperature profiles generated by scaling SSC atmospheric model (cite: selhor05) profiles with limb brightening from 0% to 40% (in 5% steps) and radius from 960″ to 976″ (in 1″ steps), convolved in 1-D with SST and ALMA beam profiles.  
  > "To investigate this, we simulated single scans over the solar disk, which consist of 1-D convolutions of the beam profiles with the synthetic $T\!_B$ profiles." (Simulated TB profiles); "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles." (Simulated TB profiles)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: yes, FITS files extracted from ALMA science verification and science archive pages  
  > "The images were extracted from FITS files provided by ALMA’s science verification page and ALMA science archive page[^3]." (Solar maps)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: ALMA nominal HPBW0: 58″ (100 GHz), 25″ (230 GHz); Gaussian-fitted HPBW: 1.1′ (100 GHz), 3.6′ (212 GHz), 0.44′ (230 GHz), 3.3′ (405 GHz)  
  > "ALMA’s single-dish nominal half-power beam widths, HPBW${}_0$, are 58″ at 100 GHz and 25″ at 230 GHz." (Antenna beam); "These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively." (Antenna beam)
- final rms: _not stated_

### Inherited from earlier work

- ALMA fast-scan single-dish solar mapping procedure  
  > "From ALMA, we use fast-scan single-dish maps obtained in Band 3 (84–116 GHz, hereafter, 100 GHz) and in Band 6 (211–275 GHz, hereafter, 230 GHz), described by (cite: white17)." (Solar maps) [from (cite: white17)]
- SST solar map reconstruction from azimuth-elevation scans  
  > "A few solar maps are reconstructed from radial and RA-dec[^2] raster scans, whereas the vast majority of the solar maps are reconstructed from azimuth-elevation scans with a 2′ separation between scans obtained (cite: gimenez20; valle21; menezes21)." (Solar maps) [from (cite: gimenez20; valle21; menezes21)]
- Solar scans tomography procedure for 2-D SST beam profile determination  
  > "The 2-D SST beam profiles were determined using a solar scans’ tomography procedure described in (cite: costa02), and are shown in panels *c* (212 GHz) and *e* (405 GHz) of Fig. [2](#fig:beams)." (Antenna beam) [from (cite: costa02)]
- Limb point filtering criteria and iterative circle fitting procedure for solar radius determination  
  > "As described by (cite: menezes21), some criteria are adopted to avoid extracting limb points associated with active regions and instrumental or random observational errors introduced by high Earth’s atmospheric attenuation." (Radius Determination) [from (cite: menezes21)]
- SSC 2-D solar atmospheric model  
  > "Atmospheric solar models, such as the SSC model (cite: selhor05) – a 2-D solar atmospheric model, which takes into account the curvature of the Sun and may include spicules – predict limb brightening of the solar disk at sub-THz frequencies." (Simulated TB profiles) [from (cite: selhor05)]

### Not stated but needed to reproduce (our reading)

- Exact list of the 125 Band 3 and 71 Band 6 FITS files used from the 17 listed ALMA project codes
- Software environment and libraries used for map interpolation, numerical differentiation, circle fitting, and 1-D convolution
- Exact functional form or parameterization used to scale the SSC brightness temperature profiles to arbitrary LB_synth and R_synth values
- How the 34 scan directions or chords across the ALMA FITS images were defined (orientation and spacing) to extract the ~34 limb points per map

## Analysis recipe

1. **Reconstruct 1-D antenna beam profiles and measure reference HPBWs**: For ALMA, reconstruct 1-D beams by averaging the derivatives of solar equator brightness temperature profiles extracted from all solar maps; for SST, determine 2-D beams via solar scan tomography and average a 2′ band centered on the peak; fit 1-D beams with a Gaussian to get reference HPBW.  
  > "ALMA beams were reconstructed using the derivatives of the solar equator $T\!_B$ profiles extracted from all the solar maps, such as those of Fig. [1](#fig:maps)." (Antenna beam); "The SST 1-D beam profiles were obtained by averaging a band of 2′ width centered on the 2-D profile peak, and are shown in panels *d* and *f* of Fig. [2](#fig:beams) for 212 and 405 GHz, respectively." (Antenna beam); "These four 1-D beams at 100, 212, 230, and 415 GHz are shown in panels (a), (b), (d), and (f) of Fig. [2](#fig:beams), respectively, were then fit by a Gaussian function to estimate the real HPBW." (Antenna beam)
   - parameter: 2′ band width centered on 2-D profile peak for SST 1-D beam extraction  
  > "The SST 1-D beam profiles were obtained by averaging a band of 2′ width centered on the 2-D profile peak, and are shown in panels *d* and *f* of Fig. [2](#fig:beams) for 212 and 405 GHz, respectively." (Antenna beam)
   - assumption: Derivatives of solar equator brightness temperature profiles are good approximations for the ALMA single-dish beam due to high spatial resolution and averaging over many maps.  
  > "Limb brightening/darkening affects the derivative, however due to the number of maps (the derivatives are superimposed), and to the high spatial resolution of ALMA single-dish, $T\!_B$ profiles derivatives are good approximations for the beam." (Antenna beam)
   - fitting: Gaussian function fit to 1-D beam profiles  
  > "These four 1-D beams at 100, 212, 230, and 415 GHz are shown in panels (a), (b), (d), and (f) of Fig. [2](#fig:beams), respectively, were then fit by a Gaussian function to estimate the real HPBW." (Antenna beam)
   - validation: Compared 2-D convolutions of asymmetric SST beams with 1-D convolutions using synthetic TB profiles (LB of 10%, 20%, 30%, 40% and R_synth of 960″ and 970″), finding differences < 0.5″ in radius and < 1% in LB.  
  > "To analyze that, we performed 2-D convolutions of SST beams and synthetic $T\!_B$ profiles, with $L\!B$ of 10%, 20%, 30% and 40%, and *R*~synth~ of 960″ and 970″." (Antenna beam); "The radii and $L\!B$ derived from the 2-D convolutions are very close to the 1-D convolutions (differences less than 0.5″ in radius and less than 1% in $L\!B$)." (Antenna beam)
2. **Extract solar limb coordinates and determine average solar radii from maps**: Correct maps for Earth's orbital eccentricity. Extract limb coordinates per scan using (1) inflection-point method (maxima and minima of numerical derivative) and (2) half-power method (mean TB between background mode outside disk and quiet-Sun median within 7.5′ radius). Perform iterative least-squares circle fits with outlier rejection to compute map radius as average center-to-limb distance.  
  > "All solar maps were corrected accordingly for the eccentricity of the Earth’s orbit that makes the apparent solar radii vary over the course of a year." (Radius Determination); "For the inflection-point method, the limb coordinates (black $\times$ in panels *c* and *d* of Fig. [3](#fig:method)) are defined as the maximum and minimum points of the numerical derivative (red curve in panel *c*, Fig. [3](#fig:method)) of each scan across the solar disk." (Radius Determination); "These extracted limb points are then fit by a circle (red dashed line in panel *d* of Fig. [3](#fig:method)) using a least-squares method to determine the center coordinates." (Radius Determination)
   - parameter: Quiet-Sun region radius: 7.5′  
  > "The background level is defined as the most common $T\!_B$ value, or mode, outside the solar disk (solid blue lines in panels *a* and *b* of Fig. [3](#fig:method)) and the $T\!_{qS}$value is the $T\!_B$ median value in the center of the solar disk (green dashed lines in panels *a* and *b* of Fig. [3](#fig:method)) constrained within a region of radius of 7.5′ (blue circle in Fig. [1](#fig:maps)b)." (Radius Determination)
   - parameter: Initial limb point distance filter: 815″ (0.85 R_theta) to 1100″ (1.15 R_theta)  
  > "For the limb point extraction, only those with a center-to-limb distance between 815″ ($0.85$ $R_\theta$) and 1100″ ($1.15$ $R_\theta$) are considered." (Radius Determination)
   - parameter: Iterative outlier rejection threshold: |r - R_bar| >= 10″; minimum 10 points (out of usual 34); maximum standard deviation 20″  
  > "For each fit, the points with center-to-limb distance, $r$, outside the interval $\bar{R}-\ang{;;10}<r<\bar{R}+\ang{;;10}$ are discarded, and then a new circle fit is performed with the remaining points." (Radius Determination); "If there are less than 10 points (out of the usual 34) remaining, the entire map is discarded; otherwise, the radius is calculated." (Radius Determination); "If the standard deviation is below 20″, then the calculated radius is stored and the next map is submitted to this process." (Radius Determination)
   - fitting: Iterative least-squares circle fit to extracted limb coordinates  
  > "These extracted limb points are then fit by a circle (red dashed line in panel *d* of Fig. [3](#fig:method)) using a least-squares method to determine the center coordinates." (Radius Determination)
   - validation: Compared measured radii against SSC model predictions and literature values.  
  > "Also, the inflection-point method radii are closer to the radius measurements reported in the literature (cite: selhor19b; alissan20; menezes21)." (Radius Determination)
3. **Forward model 1-D solar scan convolutions and estimate limb brightening ranges**: Generate 153 synthetic TB profiles by scaling SSC profiles across LB_synth (0% to 40%, step 5%) and R_synth (960″ to 976″, step 1″). Convolve in 1-D with reconstructed antenna beams. Measure R_conv (both methods) and LB_conv. Select the four R_conv closest to measured average radius R_bar within ±1 sigma for each R_synth, fit two linear bounds (lowest and highest LB vs R_synth), and evaluate the band at R_bar to estimate the LB range.  
  > "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles." (Simulated TB profiles); "First, for each *R*~synth~, we select the four *R*~conv~ closest to $\bar{R}$. From these four values, only those in the range $\bar{R}$$-\sigma\leq\textit{R}\textsubscript{conv}\leq$$\bar{R}$$+\sigma$ are considered, where $\sigma$ is the standard deviation of $\bar{R}$ for each frequency." (Simulated TB profiles); "Moreover, two linear fits are performed: one with the lowest $L\!B$ of each *R*~synth~, and another onefor the highest $L\!B$ of each *R*~synth~, resulting in a $L\!B$ band that ranges from 0% to 40%, as a function of *R*~synth~." (Simulated TB profiles)
   - parameter: LB_synth grid: 0% to 40% in 5% steps; R_synth grid: 960″ to 976″ in 1″ steps (153 profiles)  
  > "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles." (Simulated TB profiles)
   - assumption: Synthetic profiles follow scaled SSC atmospheric model shapes.  
  > "The synthetic profiles are generated by scaling SSC profiles with limb brightening levels above quiet-Sun level, $L\!B$~synth~, from 0 to 40% (in 5% steps), and radius, *R*~synth~, from 960″ to 976″ (varying by 1″), resulting in a total of 153 $T\!_B$ profiles." (Simulated TB profiles)
   - fitting: Two linear fits to the lowest and highest valid LB values as a function of R_synth  
  > "Moreover, two linear fits are performed: one with the lowest $L\!B$ of each *R*~synth~, and another onefor the highest $L\!B$ of each *R*~synth~, resulting in a $L\!B$ band that ranges from 0% to 40%, as a function of *R*~synth~." (Simulated TB profiles)
   - validation: Compared derived LB ranges against previous measurements at 100 and 230 GHz from Selhorst et al. (2019) and convolved SSC model predictions.  
  > "The $L\!B$ ranges at 100 and 230 GHz agree with the values reported by (cite: selhor19)." (Limb brightening estimate)

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gaussian-fitted antenna HPBW at 100 GHz (ALMA) | 1.1 | not stated | arcmin | 1 | These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively. |
| Gaussian-fitted antenna HPBW at 212 GHz (SST) | 3.6 | not stated | arcmin | 1 | These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively. |
| Gaussian-fitted antenna HPBW at 230 GHz (ALMA) | 0.44 | not stated | arcmin | 1 | These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively. |
| Gaussian-fitted antenna HPBW at 405 GHz (SST) | 3.3 | not stated | arcmin | 1 | These fits, also shown in each panel of Fig. [2](#fig:beams), yield values of 1.1′, 3.6′, 0.44′ and 3.3′ for 100, 212, 230, and 405 GHz, respectively. |
| Average solar radius at 100 GHz (inflection-point method) | 968 | 3 | arcsec | 2 | $\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz).; / 100 (ALMA) / $969\pm2$ / $968\pm3$ / 964.2 / 966.4 / |
| Average solar radius at 212 GHz (inflection-point method) | 963 | 3 | arcsec | 2 | $\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz).; / 212 (SST) / $967\pm3$ / $963\pm3$ / 963.6 / 969.0 / |
| Average solar radius at 230 GHz (inflection-point method) | 963 | 2 | arcsec | 2 | $\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz).; / 230 (ALMA) / $964.1\pm1.7$ / $963\pm2$ / 963.5 / 965.0 / |
| Average solar radius at 405 GHz (inflection-point method) | 963 | 5 | arcsec | 2 | $\ang{;;968}\pm\ang{;;3}$ (100 GHz), $\ang{;;963}\pm\ang{;;3}$ (212 GHz), $\ang{;;963}\pm\ang{;;2}$ (230 GHz), and $\ang{;;963}\pm\ang{;;5}$ (405 GHz).; / 405 (SST) / $965\pm5$ / $963\pm5$ / 962.9 / 967.4 / |
| Average solar radius at 100 GHz (half-power method) | 969 | 2 | arcsec | 2 | / 100 (ALMA) / $969\pm2$ / $968\pm3$ / 964.2 / 966.4 / |
| Average solar radius at 212 GHz (half-power method) | 967 | 3 | arcsec | 2 | / 212 (SST) / $967\pm3$ / $963\pm3$ / 963.6 / 969.0 / |
| Average solar radius at 230 GHz (half-power method) | 964.1 | 1.7 | arcsec | 2 | / 230 (ALMA) / $964.1\pm1.7$ / $963\pm2$ / 963.5 / 965.0 / |
| Average solar radius at 405 GHz (half-power method) | 965 | 5 | arcsec | 2 | / 405 (SST) / $965\pm5$ / $963\pm5$ / 962.9 / 967.4 / |
| Convolved SSC model solar radius R_ssc^conv at 100 GHz | 966.4 | not stated | arcsec | 3 | / 100 (ALMA) / $969\pm2$ / $968\pm3$ / 964.2 / 966.4 / |
| Convolved SSC model solar radius R_ssc^conv at 212 GHz | 969.0 | not stated | arcsec | 3 | / 212 (SST) / $967\pm3$ / $963\pm3$ / 963.6 / 969.0 / |
| Convolved SSC model solar radius R_ssc^conv at 230 GHz | 965.0 | not stated | arcsec | 3 | / 230 (ALMA) / $964.1\pm1.7$ / $963\pm2$ / 963.5 / 965.0 / |
| Convolved SSC model solar radius R_ssc^conv at 405 GHz | 967.4 | not stated | arcsec | 3 | / 405 (SST) / $965\pm5$ / $963\pm5$ / 962.9 / 967.4 / |
| Limb brightening range at 100 GHz | 5.0 - 18.7 | not stated | % | 3 | / 100 (ALMA) / / 5.0 - 18.7 / / 33.6 / 8.9 /; 5%-19% (100 GHz), 2%-12% (212 GHz), 6%-18% (230 GHz), and 3%-17% (405 GHz). |
| Limb brightening range at 212 GHz | 1.6 - 12.0 | not stated | % | 3 | / 212 (SST) / / 1.6 - 12.0 / / 36.5 / 4.2 /; 5%-19% (100 GHz), 2%-12% (212 GHz), 6%-18% (230 GHz), and 3%-17% (405 GHz). |
| Limb brightening range at 230 GHz | 6.4 - 17.6 | not stated | % | 3 | / 230 (ALMA) / / 6.4 - 17.6 / / 37.4 / 16.3 /; Therefore, based on the lower and upper limits and on $\bar{R}$ (average radii), $L\!B$ estimate at 230 GHz ranges from 6.4% to 17.6%. |
| Limb brightening range at 405 GHz | 3.3 - 17.0 | not stated | % | 3 | / 405 (SST) / / 3.3 - 17.0 / / 39.3 / 3.2 /; 5%-19% (100 GHz), 2%-12% (212 GHz), 6%-18% (230 GHz), and 3%-17% (405 GHz). |
| Convolved SSC model limb brightening LB_conv at 100 GHz | 8.9 | not stated | % | 3 | / 100 (ALMA) / / 5.0 - 18.7 / / 33.6 / 8.9 / |
| Convolved SSC model limb brightening LB_conv at 212 GHz | 4.2 | not stated | % | 3 | / 212 (SST) / / 1.6 - 12.0 / / 36.5 / 4.2 / |
| Convolved SSC model limb brightening LB_conv at 230 GHz | 16.3 | not stated | % | 3 | / 230 (ALMA) / / 6.4 - 17.6 / / 37.4 / 16.3 / |
| Convolved SSC model limb brightening LB_conv at 405 GHz | 3.2 | not stated | % | 3 | / 405 (SST) / / 3.3 - 17.0 / / 39.3 / 3.2 / |

## Qualitative findings

- The inflection-point method is less susceptible to antenna beam shape and limb brightening variations than the half-power method, yielding lower bias in solar radius determinations.  
  > "This means that the inflection-point method is less susceptible to the shape of the beam and $T\!_B$ profiles. Therefore, the inflection-point method carries less bias to the calculation of the solar radius and should thus be preferred for radius determination." (Limb brightening versus radius determination method)
- The half-power method yields larger solar radius values than the inflection-point method by about 1″ for ALMA maps and about 10″ for SST maps.  
  > "The solar radius results (Table [\[tab:radii\]](#tab:radii)) indicated that the half-power method yield larger radius values when compared to the inflection-point method – the values derived from ALMA maps are about 1″ larger, while the ones derived from SST maps are about 10″ larger." (Radius Determination)
- Derived limb brightening ranges agree with previous literature measurements at 100 and 230 GHz and with beam-convolved SSC model predictions (except at 405 GHz where LB_conv is slightly below the lower limit), but are much lower than unconvolved SSC model predictions.  
  > "The $L\!B$ ranges at 100 and 230 GHz agree with the values reported by (cite: selhor19)." (Limb brightening estimate); "The $L\!B$ ranges estimate do not agree with the $L\!B$ derived from SSC’s $T\!_B$ profiles (second last column of Table [2](#tab:LB)), which predicts a much higher $L\!B$." (Limb brightening estimate); "Nevertheless, $L\!B$~conv~ (last column of Table [2](#tab:LB)) derived from the convolved SSC model $T\!_B$ profiles are within the estimate ranges, except at 405 GHz, that shows a lower $L\!B$~conv~  albeit very close to the lower limit." (Limb brightening estimate)

## Claim tuples

- H: Solar radius measurements at radio wavelengths are biased by antenna beam width (HPBW) and solar limb brightening (LB), and the magnitude of this bias depends on whether the half-power or inflection-point method is used. | E: Measured solar radii across >3000 SST and ALMA solar maps using both methods, and simulated 1-D convolutions of reconstructed antenna beams with 153 synthetic SSC brightness temperature profiles varying in radius (960″–976″) and limb brightening (0%–40%). | R: In simulations, the radius increase Delta R grows with both LB and HPBW for both methods, but is systematically larger for the half-power method; in observations, half-power radii are ~1″ larger for ALMA and ~10″ larger for SST than inflection-point radii. | F: The inflection-point method is less affected by antenna beam size and limb brightening level than the half-power method and should be preferred for solar radius estimates at radio wavelengths. | **supported**
- H: Forward modeling of 1-D beam convolutions with synthetic brightness temperature profiles can constrain the solar limb brightening at sub-THz frequencies (100, 212, 230, and 405 GHz), even when wide beams mask limb brightening in the raw maps. | E: Selected convolved synthetic profiles whose inflection-point radii fall within ±1 sigma of the measured average radii at each frequency, and performed linear fits to the upper and lower LB bounds as a function of synthetic radius. | R: Estimated LB ranges of 5.0%–18.7% (100 GHz), 1.6%–12.0% (212 GHz), 6.4%–17.6% (230 GHz), and 3.3%–17.0% (405 GHz), which match previous direct measurements at 100 and 230 GHz and convolved SSC model values (8.9%, 4.2%, 16.3%, 3.2%). | F: Forward modeling successfully estimates sub-THz limb brightening ranges (providing the first estimates at 212 and 405 GHz) that agree with prior observations and beam-convolved model profiles, though unconvolved SSC model profiles overpredict the brightening. | **supported**

## Reasoning

- Why this data: Observations at different sub-THz wavelengths probe different layers of the solar atmosphere, and SST receivers #3 (212 GHz) and #5 (405 GHz) were chosen because their beams have less structural deformation than the other SST receivers.  
  > "Since observation at distinct wavelengths probe different layers of the solar atmosphere, the study of the solar radius and limb brightening provides important information about the solar atmosphere structure and temperature." (Introduction); "Since structural antenna deformations change the expected size and form of the beams (cite: valle21), in this study we only use receivers #3 (212 GHz) and #5 (405 GHz), which beams have less deformation compared to the other ones." (Radio Telescopes)
- Why this method: 1-D beam convolutions were used instead of 2-D convolutions because test 2-D convolutions showed negligible differences (<0.5″ in radius and <1% in LB), and forward modeling was used because SST beams are too wide to resolve limb brightening directly in the maps.  
  > "The radii and $L\!B$ derived from the 2-D convolutions are very close to the 1-D convolutions (differences less than 0.5″ in radius and less than 1% in $L\!B$). Therefore, we use the 1-D beam for the analysis." (Antenna beam); "At 212 and 405 GHz, there are no measured values, because the SST beams are too wide and, hence, no $L\!B$ are seen in the solar maps." (Limb brightening estimate)
- Alternative: Other SST receivers (rejected due to larger structural antenna beam deformations)  
  > "Since structural antenna deformations change the expected size and form of the beams (cite: valle21), in this study we only use receivers #3 (212 GHz) and #5 (405 GHz), which beams have less deformation compared to the other ones." (Radio Telescopes)
- Alternative: 2-D beam convolutions for the full simulation grid (rejected in favor of 1-D convolutions after tests showed differences < 0.5″ in radius and < 1% in LB)  
  > "The radii and $L\!B$ derived from the 2-D convolutions are very close to the 1-D convolutions (differences less than 0.5″ in radius and less than 1% in $L\!B$). Therefore, we use the 1-D beam for the analysis." (Antenna beam)
- Alternative: Half-power method for solar radius determination (evaluated and rejected as inferior to the inflection-point method due to higher bias from beam size and limb brightening)  
  > "Therefore, the inflection-point method carries less bias to the calculation of the solar radius and should thus be preferred for radius determination." (Limb brightening versus radius determination method)
- How they decided it was enough: _not stated_
- Limitation (authors): SST antenna beams are wide (3.6′ and 3.3′), asymmetric, and have high secondary lobes, preventing direct measurement of limb brightening in SST maps and causing asymmetric convolved profiles.  
  > "In the case of the $T\!_B$ profiles at 212 and 405 GHz, $L\!B$~conv~ is very low and the convolved profiles are asymmetric, which are a result of wider beams with high secondary lobes." (Limb brightening estimate); "At 212 and 405 GHz, there are no measured values, because the SST beams are too wide and, hence, no $L\!B$ are seen in the solar maps." (Limb brightening estimate)
- Limitation (authors): Solar atmospheric models such as SSC represent average approximations and do not always reproduce observations, particularly at millimeter wavelengths where chromospheric features like spicules near the limb cause discrepancies.  
  > "Those discrepancies could be due to the presence of chromospheric features such as spicules located close to the limb or, in the case of SST maps, probably due to the large beam width and deformations. In fact, the model represents average approximations, which do not always reproduce the observations." (Conclusions)
- Caveat (inferred, ours): Reconstructing the ALMA single-dish beam from the derivative of the solar equatorial limb profile inherently folds any real equatorial solar limb brightening or extended chromospheric structure into the inferred beam profile, potentially circularizing the forward modeling of limb brightening.
- Caveat (inferred, ours): The forward-modeled limb brightening ranges depend directly on the assumed true underlying solar radius (R_synth); without an independent constraint on the true deconvolved emission radius at each frequency, R_synth and LB_synth are degenerate.
- Caveat (inferred, ours): Averaging full-disk radius measurements across 2015-2018 mixes polar and equatorial limbs (which have different limb brightening levels) and spans a declining phase of the solar cycle.

## Reproducibility

- Data public (paper): ALMA data are publicly available in the ALMA Science Verification Data page and ALMA Science Archive; SST data are shared upon request to the corresponding author with permission of CRAAM.  
  > "The data from the Solar Submillimeter-wave Telescope (SST) underlying this article were provided by the Center for Radio Astronomy and Astrophysics Mackenzie (CRAAM) by permission. Data will be shared upon request to the corresponding author with permission of CRAAM." (Data Availability); "The data from the Atacama Large Millimeter/submillimeter Array (ALMA) underlying this article are available in ALMA Science Verification Data page at `https://almascience.eso.org/alma-data/science-verification` (ADS/JAO.ALMA #2011.0.00020.SV), and in ALMA Science Archive page at `http://almascience.eso.org/asax/` (the rest of ALMA data)." (Data Availability)
- Products in archive: ALMA single-dish FITS images available in the ALMA Science Verification page and ALMA Science Archive  
  > "The images were extracted from FITS files provided by ALMA’s science verification page and ALMA science archive page[^3]." (Solar maps)
- Missing: Exact list of the 125 Band 3 and 71 Band 6 ALMA single-dish FITS maps selected from the 17 project codes
- Missing: Access to the proprietary SST solar maps (2148 at 212 GHz and 1256 at 405 GHz) and reconstructed 2-D SST beam profiles
- Missing: Tabulated SSC model brightness temperature profiles at 100, 212, 230, and 405 GHz and the exact scaling formula used to generate the 153 synthetic profiles
- Missing: Exact geometry/angles of the ~34 scans extracted across each solar map to find limb points
- Data volume (inferred): ~1–5 GB (196 archival ALMA single-dish FITS maps plus 3404 interpolated 600x600 SST maps)
- Score (inferred): 6/5, The ALMA single-dish FITS images are public in the archive and the algorithmic steps for limb extraction, iterative circle fitting, and 1-D convolution are well described, but SST data require permission, no analysis code or software packages are named or released, the exact subset of 196 ALMA FITS files is not listed, and the SSC model profiles are not provided.
- Rediscovery candidate: yes,  For the ALMA portion (100 and 230 GHz), the single-dish FITS maps are directly downloadable from the ALMA Science Archive and Science Verification page under the listed project codes, and the inflection-point and half-power radius algorithms are simple and fully specified with numeric answer keys in Table 1.

## Links

- Method: (cite: white17) (Describes ALMA fast-scan single-dish solar mapping in Bands 3 and 6)
- Method: (cite: costa02) (Solar scans tomography procedure used to reconstruct 2-D SST beam profiles)
- Method: (cite: menezes21) (Defines the limb-point selection criteria and iterative circle-fitting algorithm for solar radius determination)
- Method: (cite: selhor05) (SSC 2-D solar atmospheric model used to generate synthetic brightness temperature profiles)
- Companion: (cite: menezes21) (Preceding paper measuring equatorial and polar solar radii and solar activity correlations from the same SST and ALMA datasets)

## Checks

```json
{
 "quotes": 125,
 "quotes_ok": 125,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 10,
 "unsupported_facts": 0,
 "project_codes": 17,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00020.SV"
 ],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
