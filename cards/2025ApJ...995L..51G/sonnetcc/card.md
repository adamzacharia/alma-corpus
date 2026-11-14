# The CO-to-H<SUB>2</SUB> Conversion Factor in the Milky Way's Central Parsec

`2025ApJ...995L..51G` | The Astrophysical Journal Letters 2025 | first author: Gorski, Mark D. | arXiv: 2511.16720 | DOI: 10.3847/2041-8213/ae211f

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: What is the CO-to-H2 conversion factor (alpha_CO, X_CO) in the Milky Way's Circumnuclear Disk/Ring (~1 pc around Sgr A*), derived without assuming virialization  
  > "Here we present the first estimate of the CO-to-H$_{2}$ conversion factor on sub-kpc scales." (abstract); "we deduce the CO–to–H$_{2}$ conversion factor in the Milky Way’s CND without relying on the traditional assumption of virialization" (Introduction)
- Target **Galactic Center Circumnuclear Disk/Ring (CND/CNR) around Sgr A***: coordinates _not stated_; z/distance D = 8.3 kpc  
  > "or $\sim$2 pc at the approximate distance to the Galactic Center of $D=8.3$ kpc" (Observations); distance from not stated (called the approximate distance to the Galactic Center)  
  > "or $\sim$2 pc at the approximate distance to the Galactic Center of $D=8.3$ kpc" (Observations)

## Data provenance

- ALMA projects: 2016.1.00870.S, 2017.1.00995.S, 2019.1.01559.S, 2017.1.00040.S
- bands: Band 6 (12CO J=2-1 projects); HCN J=1-0 cube from project 2017.1.00040.S  
  > "We combined data from ALMA Band 6 observations of the Milky Way’s central black hole" (Calibration and Image quality)
- frequencies and spectral setup: around 230 GHz, 12CO(J=2-1) at 230.538 GHz; 25 km/s spectral resolution for CO cubes  
  > "All observations are conducted at around 230 GHz" (Calibration and Image quality); "data cubes have 25 $\mathrm{km \, s}^{-1}$ spectral resolution" (Calibration and Image quality)
- continuum bandwidth: _not stated_
- arrays: 12 m antennas (primary beam 22.7 arcsec HPBW at 230.538 GHz)  
  > "due to the size of 12 m antennas" (Calibration and Image quality)
- configurations: _not stated_
- baselines: shortest projected baseline 12.4 m  
  > "The absolute shortest projected baseline in the observations has a length of 12.4 m" (Calibration and Image quality)
- angular resolution: CO cubes smoothed to common beam 0.256 x 0.235 arcsec, PA 60.3 deg; HCN(1-0) beam 3.69 x 2.33 arcsec, PA 85.1 deg  
  > "smoothed to a common beam size of 0.256" (Calibration and Image quality); "The synthesized beam for" (Calibration and Image quality)
- max recoverable scale: 26.4 arcsec  
  > "for a maximum recovered scale of 26.4" (Calibration and Image quality)
- sensitivity: CO: 80 uJy rms; HCN(1-0): 0.11 Jy/beam rms  
  > "80 $\mu$Jy rms noise" (Calibration and Image quality); "the cube has an rms of 0.11 Jy/beam" (Calibration and Image quality)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PI Murchikova for the CO projects; HCN data adopted from Hsieh et al. 2021 dataset  
  > "(PI: Murchikova)" (Calibration and Image quality); "from the dataset of (cite: Hsieh2021)" (Calibration and Image quality)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: HCN J=1-0 (not stated)
- Other facility **Nobeyama 45 m**: single-dish 12CO(J=1-0) measurements (15 arcsec resolution) used to check ALMA flux recovery  
  > "with the Nobeyama 45 m single-dish telescope (cite: Tokuyama2019)" (Flux recovery); "The resolution of the Nobeyama data is 15" (Flux recovery)
- External data: HCN(J=1-0) data cubes (ALMA project 2017.1.00040.S) used for the density-weighted calculation  
  > "from the dataset of (cite: Hsieh2021)" (Calibration and Image quality) [from Hsieh et al. 2021 (cite: Hsieh2021)]
- External data: Nobeyama 45 m 12CO(J=1-0) measurements for the flux-recovery check  
  > "with the Nobeyama 45 m single-dish telescope (cite: Tokuyama2019)" (Flux recovery) [from Tokuyama et al. 2019 (cite: Tokuyama2019)]
- External data: CND model ellipse: semi-major axis 58 arcsec, inclination 30 deg, area 5284.2 arcsec^2  
  > "we adopt an ellipse with a semi-major axis of 58" (Caculating by area); "(dotted line in Figure [2](#fig:CNDwhole), (cite: Tsuboi2018))" (Caculating by area) [from Tsuboi et al. 2018 (cite: Tsuboi2018)]
- External data: CND total molecular mass adopted as 3.0 +/- 1.5 x 10^4 Msun, closest to the Tsuboi et al. estimate  
  > "which is closest to the estimate of (cite: Tsuboi2018)" (Caculating by area); "The total molecular mass of the CND is usually estimated to be a few $10^4$" (Caculating by area) [from Tsuboi et al. 2018 (cite: Tsuboi2018); range from James2021, Hsieh2018, Requena-Torres2012, Lau2013, Liu2013, Oka2011, Etxaluze2011]
- External data: 12CO(2-1)/12CO(1-0) ratio of 0.85 +/- 0.2, bounded by 1 (optically thick) and 0.7 (commonly measured)  
  > "with an uncertainty of $\pm$0.2. We adopt this value because it is the mean between the optically thick limit" (Flux recovery); "commonly measured in the local universe (cite: Sandstrom2013)" (Flux recovery) [from Sandstrom et al. 2013 (cite: Sandstrom2013)]
- External data: CND average properties for RADEX: 100 K, CO column 1e18 cm^-2, H2 density 1e5 cm^-3, line width 15 km/s  
  > "The CND has an average temperature of 100 K, CO column density of 10$^{18}$" (Foreground Absorption) [from (cite: Hsieh2021; Requena-Torres2012)]
- External data: Foreground absorption features: velocity ranges and six spiral-arm/orbit features, column density 6e17 cm^-2 total  
  > "resulting in the total column density of $6\times10^{17}{{\rm cm}^{-2}}$" (Foreground Absorption) [from (cite: Bieging1980; Binney1991; Liszt1978; Scoville1972; Oort1977; Menon1970); (cite: Christopher2005; Requena-Torres2012)]
- External data: Comparison values: MW disk alpha_CO = 4.3 +/- 1.3 and CMZ alpha_CO = 1.0 +/- 0.3  
  > "(cite: Kohno2024)" (Summary) [from Kohno & Sofue 2024 (cite: Kohno2024)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (~2 Jy) flux/bandpass; J1744-3116 (0.27 +/- 0.03 Jy) complex gain  
  > "Every observation used J1924-2914" (Calibration and Image quality); "for flux/bandpass calibration and J1744-3116" (Calibration and Image quality)
- flux scale uncertainty: 10% (ALMA standard Band 6)  
  > "standard Band 6 calibration uncertainty of 10% on the flux values" (Calibration and Image quality)
- self calibration: Sgr A* variability fit at uv-level with UVmultifit; time-dependent lightcurve used to self-calibrate; black hole continuum then removed at uv-level  
  > "We then used the time-dependent lightcurve to self-calibrate the data." (Calibration and Image quality); "we removed the continuum emission of the black hole from the data at the uv-level" (Calibration and Image quality)

### Imaging

- task: CASA tclean  
  > "The imaging was conducted with the Common Astronomy Software Applications (CASA)" (Calibration and Image quality)
- deconvolver: multiscale  
  > "with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5)" (Calibration and Image quality)
- weighting robust: Briggs weighting 0.5  
  > "with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5)" (Calibration and Image quality)
- uv taper: _not stated_
- cell size: 0.02 arcsec  
  > "The produced image has 0.02$^{\prime\prime}$pixels and a diameter of about 54" (Calibration and Image quality)
- image size: diameter about 54 arcsec (~2 pc), covering the primary beam nearly completely  
  > "The produced image covers the primary beam nearly completely." (Calibration and Image quality)
- masking: integrated intensity maps use pixels >5 sigma; inner 0.5 arcsec (0.002 pc) around Sgr A* masked for residual black hole emission  
  > "Integrated intensity maps are made using pixels with values $>5\sigma$." (Calibration and Image quality); "is masked due to residual (i.e., not fully removed at the uv-level) black hole emission" (Calibration and Image quality)
- multiscale scales: 0, 7, 42, 126 pixels  
  > "with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5)" (Calibration and Image quality)
- continuum subtraction: Sgr A West continuum subtracted in the image domain via linear fit to line-free channels (after uv-level removal of the black hole continuum)  
  > "Continuum subtraction of Sgr A West was done in the image domain via linear fitting to line-free channels." (Calibration and Image quality)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO cubes smoothed to a common beam  
  > "smoothed to a common beam size of 0.256" (Calibration and Image quality)
- final beam: _not stated_
- final rms: 80 uJy rms (CO cubes, 25 km/s resolution)  
  > "80 $\mu$Jy rms noise" (Calibration and Image quality)

### Inherited from earlier work

- HCN(J=1-0) cubes taken from an existing dataset  
  > "from the dataset of (cite: Hsieh2021)" (Calibration and Image quality) [from (cite: Hsieh2021)]
- CND geometry (ellipse model) and mass estimate for the CND  
  > "which is closest to the estimate of (cite: Tsuboi2018)" (Caculating by area) [from (cite: Tsuboi2018)]
- Sgr A* variability timescales and flux changes  
  > "the flux can change by $\sim1$ Jy within half hour" (Calibration and Image quality) [from (cite: Murchikova2021)]
- UVmultifit used for the uv-level fit of Sgr A* variability  
  > "We used `UVmultifit` (cite: marti-vidal2014)" (Calibration and Image quality) [from (cite: marti-vidal2014)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channel ranges for the image-domain continuum subtraction
- Self-calibration solution interval, reference model and how the UVmultifit lightcurve was applied
- Which CASA version and whether the archive pipeline or manual calibration products were used
- Exact tclean parameters (niter, threshold, mask, imsize in pixels, phasecenter, mosaic or single field, gridder)
- How the common beam smoothing and primary beam correction were done
- Exact polygon of the white-contour regions and how flux was summed (west and east sides)
- How the 0.436/0.444 filling factors and the 14,300 Jy km/s expected flux were combined
- Whether HCN regions were matched to the CO regions and the HCN cube processing
- How the quoted uncertainties on alpha_CO were propagated (formula)
- Conversion between alpha_CO and X_CO factor (assumed helium correction/factor 4.3)
- RADEX inputs for T0 conversion and the final observed integrated intensity used

## Analysis recipe

1. **calibrate and remove Sgr A* variability**: Fit Sgr A* variability at uv-level with UVmultifit, self-calibrate with the lightcurve, remove black hole continuum at uv-level  
  > "We used `UVmultifit` (cite: marti-vidal2014) to fit the variability of Sgr A$^*$ at uv-level." (Calibration and Image quality); "We then used the time-dependent lightcurve to self-calibrate the data." (Calibration and Image quality)
   - software: UVmultifit, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **image the 12CO(2-1) cube**: CASA tclean with multiscale deconvolution, Briggs 0.5, 0.02 arcsec pixels, smoothed to common beam, image-domain continuum subtraction  
  > "with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5)" (Calibration and Image quality); "Continuum subtraction of Sgr A West was done in the image domain via linear fitting to line-free channels." (Calibration and Image quality)
   - software: CASA tclean
   - parameter: scales 0, 7, 42, 126 pixels; Briggs 0.5; 25 km/s resolution; 80 uJy rms  
  > "with multiscale deconvolution (scales: 0, 7, 42, 126 pixels; and Briggs weighting: 0.5)" (Calibration and Image quality)
   - fitting: _not stated_
   - validation: _not stated_
3. **check flux recovery against Nobeyama**: Compare ALMA integrated flux with the expected 12CO(2-1) flux from Nobeyama 12CO(1-0) scaled by 0.85 and filling factors  
  > "The expected $^{12}{\rm CO}(J=2-1)$ integrated flux density would be 14,300$\pm$3000 Jy km s$^{-1}$." (Flux recovery)
   - parameter: filling factors 0.436 (west), 0.444 (east); Nobeyama beam 15 arcsec; region 15 x 34 arcsec  
  > "The respective values for the west side and east side are 0.436 and 0.444." (Flux recovery)
   - assumption: 12CO(2-1)/12CO(1-0) ratio 0.85 +/- 0.2  
  > "assuming a ${^{12}{\rm CO}(J=2-1)}/ {^{12}{\rm CO}(J=1-0)}$ ratio of 0.85 with an uncertainty of $\pm$0.2" (Flux recovery)
   - fitting: _not stated_
   - validation: ALMA recovers 88 +/- 21% of single-dish flux, consistent with full recovery  
  > "We find that the flux recovered in our ALMA observations is $88\pm21$% of the flux observed by the single-dish Nobeyama 45 m telescope" (Flux recovery)
4. **alpha_CO by area**: Assume the fraction of CND area captured (8.7%) equals the fraction of mass, apply it to the adopted CND mass and divide by the CO luminosity  
  > "assume that the fraction of the captured area corresponds to the fraction of mass in this region" (Caculating by area)
   - parameter: integrated flux 12,400 Jy km/s; captured area 460.6 arcsec^2; CND area 5284.2 arcsec^2; CND mass 3.0 +/- 1.5 x 10^4 Msun  
  > "The total integrated flux in this region is 12,400 Jy km s$^{-1}$." (Caculating by area); "Here we adopt the value of $3.0 \pm 1.5\times10^4$" (Caculating by area)
   - assumption: Uniform mass distribution; no density variations; D = 8.3 kpc  
  > "This approach does not take into account density variations in the CND." (Caculating by area)
   - fitting: _not stated_
   - validation: _not stated_
5. **alpha_CO by HCN fraction**: Use the fraction of HCN(1-0) flux in the selected regions (350 +/- 35 of 3700 Jy km/s, 9.7%) as the mass fraction  
  > "is about 350$\pm$35 Jy km s$^{-1}$, i.e., 9.7%" (Calculating by fraction of HCN emission)
   - parameter: total HCN(1-0) CND flux 3700 Jy km/s; implied H2 mass 2.9 +/- 1.4 x 10^3 Msun  
  > "implying that H$_2$ mass in this region is $2.9\pm1.4\times10^3~M_\odot$" (Calculating by fraction of HCN emission)
   - assumption: HCN(1-0) integrated flux traces density variations in the CND  
  > "Let us assume that the density variations in the CND are relatively well represented by the variations of the integrated" (Calculating by fraction of HCN emission)
   - fitting: _not stated_
   - validation: Agrees with the area-based estimate  
  > "give nearly the same result" (Calculating by fraction of HCN emission)
6. **estimate foreground absorption**: RADEX estimate of CND brightness T0 and radiative transfer formula with six foreground features to derive optical depth  
  > "we use the radiative transfer code RADEX (cite: vanderTak2007) to estimate the expected brightness temperature of the CND" (Foreground Absorption)
   - software: RADEX
   - parameter: T0 = 700 K km/s; observed 695 K km/s; T_foreground = 29 K km/s; foreground n(H2) 1e3 cm^-3, width ~20 km/s, 10 K, N(CO) 1e17 cm^-2 per feature  
  > "For the foreground, we assume there are six absorption features from the spiral arms and other orbits crossing the line-of-sight toward the Galactic center" (Foreground Absorption)
   - assumption: CND average: 100 K, N(CO) 1e18 cm^-2, n(H2) 1e5 cm^-3, line width 15 km/s  
  > "The CND has an average temperature of 100 K, CO column density of 10$^{18}$" (Foreground Absorption)
   - fitting: _not stated_
   - validation: Selecting a sub-region near the middle of the CND avoids the most significant absorption  
  > "by selecting a sub-region near the middle of the CND, we avoid the most significant effects" (Foreground Absorption)
7. **combine into final alpha_CO and X_CO**: Average the two alpha_CO estimates and convert to X_CO  
  > "We report the average as the final result:" (Summary)
   - assumption: Errors dominated by uncertainty in CND mass  
  > "the errorbars are dominated by the uncertainties on the mass of the CND" (Caculating by area)
   - fitting: _not stated_
   - validation: Compared with MW disk (4.3 +/- 1.3) and CMZ (1.0 +/- 0.3) values  
  > "However, it is higher than what is known of the larger central molecular zone" (Summary)

## Software

- **CASA** : imaging with tclean (multiscale)  
  > "The imaging was conducted with the Common Astronomy Software Applications (CASA)" (Calibration and Image quality)
- **UVmultifit** : fit Sgr A* variability at uv-level  
  > "We used `UVmultifit` (cite: marti-vidal2014) to fit the variability of Sgr A$^*$ at uv-level." (Calibration and Image quality)
- **RADEX** : expected CND brightness for the foreground absorption estimate  
  > "we use the radiative transfer code RADEX (cite: vanderTak2007)" (Foreground Absorption)
- **astropy** : listed under Software; specific use not stated  
  > "astropy (cite: Astropy2013; Astropy2018; Astropy2022)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| alpha_CO (final) | 4.5 | +/-2.5 | Msun (K km/s pc^2)^-1 | 7 | We derive a conversion factor of $\alpha_\mathrm{CO} \simeq 4.5\pm2.5$ |
| X_CO | 2.1e20 | +/-1.1e20 | cm^-2 (K km/s)^-1 | 7 | X\[CO\] $\simeq (2.1\pm1.1)\times 10^{20}$ |
| alpha_CO by area | 4.3 | +/-2.3 | Msun (K km/s pc^2)^-1 | 4 | \simeq& 4.3\pm2.3 |
| alpha_CO by HCN fraction | 4.7 | +/-2.6 | Msun (K km/s pc^2)^-1 | 5 | \simeq& 4.7\pm2.6 |
| Fraction of CND captured in CO(2-1) map | 8.7 | not stated | % | 4 | is about 8.7% |
| Total integrated 12CO(2-1) flux in selected region | 12,400 | not stated | Jy km/s | 4 | The total integrated flux in this region is 12,400 Jy km s$^{-1}$. |
| ALMA flux recovered relative to Nobeyama | 88 | +/-21 | % | 3 | is $88\pm21$% of the flux observed by the single-dish Nobeyama 45 m telescope |
| Expected 12CO(2-1) flux from Nobeyama | 14,300 | +/-3000 | Jy km/s | 3 | would be 14,300$\pm$3000 Jy km s$^{-1}$. |
| HCN(1-0) flux in selected regions | 350 | +/-35 | Jy km/s | 5 | is about 350$\pm$35 Jy km s$^{-1}$, i.e., 9.7% |
| H2 mass in selected region (HCN method) | 2.9e3 | +/-1.4e3 | Msun | 5 | implying that H$_2$ mass in this region is $2.9\pm1.4\times10^3~M_\odot$ |
| Foreground optical depth tau | 0.007 | not stated | dimensionless | 6 | We obtain $\tau\simeq0.007$ and the foreground absorption of just $\lesssim1\%.$ |

## Qualitative findings

- alpha_CO in the CND is slightly higher than but consistent with the Galactic disk value, and higher than the CMZ value  
  > "This value is consistent with the Galactic disk but higher than CMZ." (abstract)
- Foreground absorption is negligible (<~1%) for the selected sub-region  
  > "by selecting a sub-region near the middle of the CND, we avoid the most significant effects" (Foreground Absorption)
- The CND may not inherit the properties of the larger CMZ  
  > "This suggests that the CND may not inherit the properties of the larger CMZ." (Summary)

## Claim tuples

- H: What is alpha_CO in the Galactic Center CND without assuming virialization | E: ALMA 12CO(2-1) map of part of the CND combined with literature CND mass, using area fraction and HCN fraction | R: alpha_CO = 4.3+/-2.3 (area) and 4.7+/-2.6 (HCN fraction); average 4.5+/-2.5 | F: alpha_CO ~ 4.5 +/- 2.5 Msun (K km/s pc^2)^-1, X_CO ~ 2.1e20 | **supported**
- H: Does the ALMA map recover the total CO flux | E: Compare with Nobeyama 45 m 12CO(1-0) scaled by 0.85 | R: 88 +/- 21% of single-dish flux recovered | F: Consistent with all flux being recovered | **supported**
- H: Does foreground absorption bias alpha_CO | E: RADEX-based radiative transfer estimate with six foreground features | R: tau ~ 0.007, absorption <~ 1% | F: Foreground absorption negligible in the selected region | **supported**
- H: Is the CND alpha_CO like the CMZ value | E: Compare with alpha_CO of MW disk and CMZ from Kohno & Sofue 2024 | R: CND value higher than CMZ (1.0 +/- 0.3) and consistent with disk (4.3 +/- 1.3) | F: CND may not inherit CMZ properties | **partially**

## Reasoning

- Why this data: First observations of this region in 12CO(2-1) since Marshall & Lasenby 1994  
  > "These are the first observations of this region in this line since (cite: Marshall1994)." (Introduction)
- Why this method: Geometric area fraction and HCN fraction used so alpha_CO does not rely on virialization  
  > "without relying on the traditional assumption of virialization" (Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties dominated by wide variation in the CND mass estimates  
  > "The uncertainties are large due to the wide variations in the estimated mass of the molecular gas in the Galactic Center’s CND" (Summary)
- Limitation (authors): Area method ignores density variations  
  > "This approach does not take into account density variations in the CND." (Caculating by area)
- Limitation (authors): If the CND is optically thick (tau of a few), alpha_CO could be overestimated by a similar factor  
  > "This would lead to an overestimation of the CO–to–H$_{2}$ conversion factor by a similar factor as the optical depth." (Summary)
- Limitation (authors): Inner 0.5 arcsec around Sgr A* masked due to residual black hole emission  
  > "is masked due to residual (i.e., not fully removed at the uv-level) black hole emission" (Calibration and Image quality)
- Caveat (inferred, ours): The CND mass (3.0 +/- 1.5e4 Msun) is adopted from literature, not measured, and dominates the result; alpha_CO is essentially circular with that choice
- Caveat (inferred, ours): Two alpha_CO estimates share the same mass and flux and are not independent, so averaging does not reduce error
- Caveat (inferred, ours): Assumed 0.85 CO(2-1)/(1-0) ratio and ~10% flux calibration are not propagated explicitly
- Caveat (inferred, ours): Spatial selection of white-contour regions and the 8.7% area fraction are not reproducible from the text alone
- Caveat (inferred, ours): Light-weight region-level treatment ignores temperature/optical depth variations across the CND

## Reproducibility

- Data public (paper): ALMA project codes listed; whether data are public is not stated in the paper  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2016.1.00870.S, #2017.1.00995.S, #2017.1.00040.S, and #2019.1.01559.S." (Facilities)
- Products in archive: _not stated_
- Missing: Line-free channel ranges and CASA version
- Missing: Self-calibration and UVmultifit lightcurve details
- Missing: Exact tclean parameters and image masks
- Missing: Precise region definitions for the white contours (west and east sides)
- Missing: Uncertainty propagation recipe and X_CO conversion factor definition
- Missing: Full numerical CND mass inputs beyond the adopted 3.0 +/- 1.5e4 Msun
- Data volume (inferred): Large: three Band 6 12CO(2-1) projects of a high-resolution mosaic/field (hundreds of GB raw; tens of GB calibrated) plus one HCN(1-0) cube from a fourth project
- Score (inferred): 2/5, Project codes are given and the headline numbers are explicit, but key processing details (CASA version, line-free channels, selfcal solutions, region definitions) are missing and the result is mostly set by adopted literature mass
- Rediscovery candidate: no, Public status of the data is not stated, and the recipe lacks region definitions and processing details; the final alpha_CO is dominated by the adopted literature CND mass

## Links

- Method: Martí-Vidal et al. 2014 (cite: marti-vidal2014) (UVmultifit used to fit Sgr A* variability at uv-level)
- Method: van der Tak et al. 2007 (cite: vanderTak2007) (RADEX used for foreground absorption estimate)
- Companion: Hsieh et al. 2021 (cite: Hsieh2021) (HCN(J=1-0) cubes from project 2017.1.00040.S)
- Companion: Murchikova & Witzel 2021 (cite: Murchikova2021) (Sgr A* variability with ALMA)
- Companion: Tsuboi et al. 2018 (cite: Tsuboi2018) (CND geometry and mass estimate)

## Checks

```json
{
 "quotes": 110,
 "quotes_ok": 110,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 72,
  "rate": 0.735
 },
 "evidence_ok": true
}
```
