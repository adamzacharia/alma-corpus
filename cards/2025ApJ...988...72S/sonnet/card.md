# ALMA-JELLY. I. High Resolution CO(2─1) Observations of Ongoing Ram Pressure Stripping in NGC 4858 Reveal Asymmetrical Gas Tail Formation and Fallback

`2025ApJ...988...72S` | The Astrophysical Journal 2025 | first author: Souchereau, Harrison J. | arXiv: 2506.07262 | DOI: 10.3847/1538-4357/adde47

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, galaxy_clusters_and_sz
- Question: How do strong, highly-inclined ram pressure stripping, rotation and torques shape the asymmetric inner molecular gas tail of NGC 4858, and is there evidence for gas fallback?  
  > "The relationship between highly-inclined winds, asymmetric inner tails, and fallback is an open question addressed by this work." (Introduction)
- Target **NGC 4858**: coordinates RA 12:59:02.072, Dec +28:06:56.228 (J2000)  
  > "We adopt a luminosity distance for Coma of 100 Mpc, corresponding to a scale of 1" = 0.463 kpc." (The Coma Cluster and NGC 4858); "| \(1\) | $\alpha$ (J2000) | 12:59:02.072 | 12:59:03.906 | B |" (Table 1); z/distance Coma luminosity distance 100 Mpc; cz = 9416 km/s  
  > "We adopt a luminosity distance for Coma of 100 Mpc, corresponding to a scale of 1" = 0.463 kpc." (The Coma Cluster and NGC 4858); "| \(1\) | $\alpha$ (J2000) | 12:59:02.072 | 12:59:03.906 | B |" (Table 1); distance from Coma cluster distance adopted (100 Mpc); coordinates and velocity from SIMBAD  
  > "We adopt a luminosity distance for Coma of 100 Mpc, corresponding to a scale of 1" = 0.463 kpc." (The Coma Cluster and NGC 4858); "| \(1\) | $\alpha$ (J2000) | 12:59:02.072 | 12:59:03.906 | B |" (Table 1)

## Data provenance

- ALMA projects: 2021.1.01616.L
- bands: _not stated_
- frequencies and spectral setup: CO(2-1) at 230.5 GHz; 3.8 km/s channels  
  > "ALMA observed the 230.5 GHz CO(2-1)line" (2.1 ALMA CO(2-1)); "channel widths of 3.8 km s$^{-1}$" (2.1 ALMA CO(2-1))
- continuum bandwidth: _not stated_
- arrays: 12m and 7m arrays, mosaics (5 pointings 7m, 13 pointings 12m)  
  > "NGC 4858 was observed by ALMA with 5 mosaic pointings using the 7m array, and 13 mosaic pointings with the 12m array." (2.1 ALMA CO(2-1))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1" (beam 1.35" x 0.87", PA 30 deg)  
  > "The synthesized primary beam has major and minor axes of 1.35 and 0.87 arcseconds, respectively, and a position angle of $30\degree$." (2.1 ALMA CO(2-1))
- max recoverable scale: _not stated_
- sensitivity: RMS ~2.3 mJy/beam  
  > "The RMS of the cube is measured at $\sim 2.3$ mJy Beam$^{-1}$." (2.1 ALMA CO(2-1))
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA Cycle 8 large program ALMA-JELLY  
  > "ALMA-JELLY comprises combined 12m and 7m data obtained during ALMA Cycle 8 [^2] for 27 of the galaxies" (The ALMA-JELLY Project)
- Line: CO J=2-1 (230.5 GHz)
- Other facility **Subaru Suprime-Cam**: R-band and Halpha narrow-band images  
  > "Ground-based R-band and narrow-band (H$\alpha$ at the Coma cluster) images of NGC 4858 come from (cite: yagi_dozen_2010)" (2.2 Suprime Cam)
- Other facility **HST WFC3**: F350LP and F600LP images (Proposal 13777)  
  > "publicly-available HST Wide-Field Camera 3 (WFC3) F350LP and F600LP images from the *HST Legacy Archive* (PI Gregg, Proposal ID: 13777)" (2.3 HST Imaging)
- Other facility **LOFAR LoTSS**: 144 MHz radio continuum cutout, used for tail angle  
  > "A cutout surrounding emission from NGC 4858 was created from the larger Coma cluster mosaic image (cite: roberts_lotss_2021)." (2.4 LOFAR Imaging)
- External data: Stellar mass, SFR, HI mass of NGC 4858  
  > "(6,7,8): Stellar mass, star formation rate measured using NUV and $22\mu m$ luminosity, and HI gas mass estimates from (cite: molnar_westerbork_2022)." (Table 1) [from (cite: molnar_westerbork_2022)]
- External data: Subaru R-band and Halpha images  
  > "Ground-based R-band and narrow-band (H$\alpha$ at the Coma cluster) images of NGC 4858 come from (cite: yagi_dozen_2010)" (2.2 Suprime Cam) [from (cite: yagi_dozen_2010)]
- External data: Coma NFW mass 1.2e15 Msun, c=9  
  > "We model the Coma cluster mass distribution as an NFW profile with a total mass of $1.2\times10^{15}M_\odot$, with a concentration ($c=R_\text{vir}/R_s =9$) (cite: lokas_dark_2003)." (7.1 Estimating the 3D Tail Geometry) [from (cite: lokas_dark_2003)]
- Simulation/model as data: Qualitative comparison to snapshots of two galaxy-scale simulations (one hydrodynamical, one sticky N-body) under highly-inclined ram pressure  
  > "compares these phases to snapshots of two galaxy-scale simulations (one hydrodynamical, one sticky N-body) under highly-inclined ram pressure." (7.4 Evolution in the Inner Tail)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: PHANGS-ALMA pipeline calling tclean multiple times over multiple scales with masks  
  > "the PHANGS-ALMA pipeline differs by calling TCLEAN multiple times over multiple scales, while supplying masks to guide deconvolution." (2.1 ALMA CO(2-1))
- deconvolver: _not stated_
- weighting robust: natural weighting (Briggs robust=2)  
  > "We choose to use a natural weighting scheme (Briggs `robust=2`) to give us the best surface brightness sensitivity." (2.1 ALMA CO(2-1))
- uv taper: _not stated_
- cell size: _not stated_
- image size: 480 x 303 pixels (72x45 arcsec)  
  > "The datacube has 480 x 303 pixels (corresponding to $72\times45$ arcseconds, or $34 \times 21$ kpc, respectively)" (2.1 ALMA CO(2-1))
- masking: MASKMOMENT: >3.0 sigma in at least 2 contiguous channels, area at least a beam  
  > "The weakest features are required to be detected at $>3.0\sigma$ in at least 2 contiguous channels, and must cover a minimum spatial area as large as the synthesized beam." (2.1 ALMA CO(2-1))
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied in pipeline  
  > "The data is also corrected for the primary beam, and then automatically trimmed to an appropriate image size." (2.1 ALMA CO(2-1))
- array combination: combined 12m and 7m data  
  > "ALMA-JELLY comprises combined 12m and 7m data" (The ALMA-JELLY Project)
- smoothing: _not stated_
- final beam: 1.35" x 0.87", PA 30 deg  
  > "The synthesized primary beam has major and minor axes of 1.35 and 0.87 arcseconds, respectively, and a position angle of $30\degree$." (2.1 ALMA CO(2-1))
- final rms: ~2.3 mJy/beam  
  > "The RMS of the cube is measured at $\sim 2.3$ mJy Beam$^{-1}$." (2.1 ALMA CO(2-1))

### Inherited from earlier work

- Data reduction and imaging via PHANGS-ALMA pipeline  
  > "The ALMA data were cleaned using the PHANGS-ALMA data reduction pipeline (cite: leroy_phangsalma_2021), which we will briefly describe." (2.1 ALMA CO(2-1)) [from (cite: leroy_phangsalma_2021)]
- CO luminosity procedure  
  > "We can then follow the procedure in (cite: solomon_molecular_1997) to obtain a CO line luminosity" (2.1 ALMA CO(2-1)) [from (cite: solomon_molecular_1997)]
- Complete sample and project description deferred  
  > "The complete sample and full description of the project will be presented in Jachym et al. (in prep.)." (The ALMA-JELLY Project) [from Jachym et al. (in prep.)]
- Subaru data acquisition and processing  
  > "to which we refer the reader for a more in-depth explanation of the data acquisition and processing (cite: yagi_extended_2017)" (2.2 Suprime Cam) [from (cite: yagi_dozen_2010; yagi_extended_2017)]

### Not stated but needed to reproduce (our reading)

- Calibration details (CASA version, pipeline, flux calibrators, self-calibration)
- Individual execution blocks, observing dates, configurations and on-source time
- Whether 12m and 7m were combined before or inside tclean, and the feathering/combination method
- Spectral line-free channels and continuum subtraction
- MASKMOMENT parameters beyond the 3 sigma / 2 channel criteria (e.g. smoothing, low-threshold)
- 3DBarolo parameter settings (rings, widths, fit mode)
- Tully-Fisher calibration details used to get Vmax=165 km/s
- Isophote fitting settings in GALPRIME
- Details of the Sersic fit
- Simulation snapshots used in the comparison

## Analysis recipe

1. **Image CO cube and make moment maps**: PHANGS-ALMA pipeline tclean multi-scale with masks, natural weighting; masks and moment maps with MASKMOMENT  
  > "We generate masks for the cleaned datacube using the Python MASKMOMENT package, developed by Tony Wong" (2.1 ALMA CO(2-1))
   - software: CASA, PHANGS-ALMA Pipeline, MASKMOMENT
   - parameter: robust=2; 3.8 km/s channels; >3 sigma in 2 contiguous channels  
  > "channel widths of 3.8 km s$^{-1}$" (2.1 ALMA CO(2-1))
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive CO flux, luminosity and H2 mass**: Integrate moment-0; L'CO from Solomon et al. formula; MH2 = alphaCO/R21 L'CO  
  > "We then convert the CO luminosity to a total H$_2$ mass using" (2.1 ALMA CO(2-1))
   - assumption: R21 ~0.8; alphaCO = 4.3 Msun (K km/s pc^2)^-1; DL = 100 Mpc  
  > "where $R_{21} \approx 0.8$ (cite: leroy_heracles_2009) is the CO(2-1)/CO(1-0) ratio, and $\alpha_{CO} = 4.3\text{M}_\odot$ (K km s$^{-1}$ pc$^2$)$^{-1}$" (2.1 ALMA CO(2-1))
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterize stellar disk (PA, ellipticity, inclination, Sersic)**: Elliptical isophote fitting of Subaru R-band image and 1D Sersic fit; same for CO moment-0 profile  
  > "We use the elliptical isophote analysis tool in GALPRIME, which has a modified wrapper for the PHOTUTILS algorithm" (3 Stellar Distribution)
   - software: GALPRIME, Photutils
   - parameter: Northern region heavily masked to avoid NGC 4860 light  
  > "We mitigate this contamination by heavily masking the Northern region of the image" (3 Stellar Distribution)
   - fitting: Iterative isophote fit of centre, PA, ellipticity, a3, a4; 1D Sersic profile  
  > "We fit a 1D Sérsic profile model to the light distribution of NGC 4858." (3 Stellar Distribution)
   - validation: _not stated_
4. **Azimuthal/quadrant analysis of CO distribution and tail angle**: Elliptical annuli with stellar PA/ellipticity; median flux in theta +/-5 deg; tail angle from LOFAR flux bisection; four quadrants  
  > "We then take the median flux in regions of $\theta \pm 5\degree$." (4.2 CO Brightness Azimuthal Distribution)
   - software: MASKMOMENT
   - parameter: theta_wind = -15 deg equally divides radio flux at 18-27 kpc  
  > "We find a position angle of of $\theta_\text{wind} = -15\degree$ equally divides the radio continuum flux at distances 18-27 kpc, and adopt this as the tail angle." (4.1 Tail Asymmetry)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit circular rotation model and obtain velocity residuals**: 3DBarolo on moment-1 with fixed stellar PA, inclination, centre, Vsys; extend with tanh rotation curve; subtract model from moment-1  
  > "We fix these parameters, as well as $x_0$, $y_0$, and $V_\text{sys}$ and assume no radial velocities." (5.1 Residual Velocities)
   - software: 3DBarolo
   - parameter: Vmax = 165 km/s from Tully-Fisher; rt free, best fit 2.4 kpc  
  > "Our best-fit to the available datapoints from $^\mathrm{3D}\textsc{Barolo}$ returns a transition radius of $r_t=2.4$kpc" (5.1 Residual Velocities)
   - assumption: Motions in disk plane; tail in front of the disk  
  > "We assume for all of these features that the tail is in front of the disk." (6 Selected Features with High Velocity Residuals)
   - fitting: Fit of tanh URC to 3DBarolo points with free rt  
  > "The transition radius $r_t$ adjusts the scaling of the rotation curve, which we leave as a free parameter when fitting the model." (5.1 Residual Velocities)
   - validation: Tested flat and 2x Vmax outer rotation curves; features robust  
  > "None of the features we discuss with significant velocity residuals can be explained away by any plausible rotation curve" (5.1 Residual Velocities)
6. **Estimate disk-wind angle**: Geometric dot product of wind and disk normal vectors using theta_tail, theta_maj, i and total velocity from GALA NFW orbit estimate  
  > "we can use the galaxy dynamics package GALA to model the mass distribution of the Coma cluster" (7.1 Estimating the 3D Tail Geometry)
   - software: GALA
   - parameter: Vtot = 3410 km/s; uncertainty = Coma velocity dispersion  
  > "the expected total velocity at NGC 4858’s current location is 3410 km s$^{-1}$." (7.1 Estimating the 3D Tail Geometry)
   - assumption: Projected distance equals true distance to cluster centre; NFW with M=1.2e15, c=9  
  > "Assuming that the projected distance from the cluster center is the true distance to the cluster center" (7.1 Estimating the 3D Tail Geometry)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare with simulations and evaluate torque asymmetry**: Differential ram pressure R formula; qualitative comparison to simulation snapshots  
  > "this corresponds to a differential RP strength of $\mathcal{R} = 0.23$." (7.2 Role of Ram Pressure Torques)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA imaging (tclean) via pipeline  
  > "CASA (cite: casa_team_casa_2022), PHANGS-ALMA Pipeline (cite: leroy_phangsalma_2021)" (Software)
- **PHANGS-ALMA Pipeline** : Cleaning and primary beam correction  
  > "The ALMA data were cleaned using the PHANGS-ALMA data reduction pipeline (cite: leroy_phangsalma_2021)" (2.1 ALMA CO(2-1))
- **MASKMOMENT** : Masks, moment maps and uncertainty maps  
  > "We generate masks for the cleaned datacube using the Python MASKMOMENT package, developed by Tony Wong" (2.1 ALMA CO(2-1))
- **3DBarolo** : Rotation curve fit  
  > "To obtain the rotation curve we use the $^\mathrm{3D}\textsc{Barolo}$ fitting package" (5.1 Residual Velocities)
- **GALPRIME** : Isophote analysis wrapper of Photutils  
  > "We use the elliptical isophote analysis tool in GALPRIME, which has a modified wrapper for the PHOTUTILS algorithm" (3 Stellar Distribution)
- **Photutils** 1.13.0: Isophote fitting  
  > "modified wrapper for the PHOTUTILS algorithm" (3 Stellar Distribution)
- **reproject (astropy)** : Align images to ALMA frame  
  > "We use the astropy subpackage REPROJECT [^3] to align and rescale the images to the ALMA CO coordinate frame." (2 Data and Data Reduction)
- **GALA** 1.8.1: Coma NFW potential to estimate total velocity  
  > "we can use the galaxy dynamics package GALA to model the mass distribution of the Coma cluster" (7.1 Estimating the 3D Tail Geometry)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated CO(2-1) flux (disk+tail) | 46.2 | 2.7 | Jy km/s | 2 | $S_{CO}\Delta v = 46.2 \pm 2.7$ Jy km s$^{-1}$ |
| Molecular hydrogen mass | 1.5e9 | 0.1e9 | Msun | 2 | M$_{\text{H}_2} = 1.5\pm0.1\times10^9M_\odot$ |
| MH2/M* | 0.31 | not stated | dimensionless | 2 | {M_{H_2}}{M_*} = \frac{1.5\times10^9 M_\odot}{4.9\times10^9 M_\odot} = 0.31 |
| Stellar disk inclination | 38 | not stated | deg | 3 | This corresponds to an inclination of $38\degree$. |
| Stellar major-axis PA | 32 | 6 | deg | 3 | $\theta_\text{maj} = 32 \pm 6\deg$ |
| Sersic index | 0.98 | not stated | dimensionless | 3 | a Sérsic index of $n=0.98$ |
| CO exponential scale length | 2.49" = 1.16 kpc | not stated | arcsec / kpc | 4 | exponential scale length of $h_R = 2.49" = 1.16$kpc |
| F_lead/F_trail in innermost annulus | 1.25 | not stated | dimensionless | 4 | $F_\text{lead}/F_\text{trail} = 1.25$ |
| Tail position angle | -15 | 20 | deg | 4 | $\theta_\text{tail} = -15\pm20\degree$ |
| Tail rotation curve transition radius | 2.4 | not stated | kpc | 5 | returns a transition radius of $r_t=2.4$kpc |
| Disk-wind angle | 75 | +10/-27 | deg | 6 | a disk-wind angle of $\phi_\text{DW}=75_{-27}^{+10}$ degrees |
| Differential ram pressure strength | 0.23 | not stated | dimensionless | 7 | $\mathcal{R} = 0.23$ |
| Fraction of CO flux beyond leading-side truncation (inner tail) | 14 | not stated | percent | 4 | 14% of the total CO emission is located beyond the southern side truncation radius |

## Qualitative findings

- Inner tail gas is concentrated in quadrant 4, the trailing side rotating into the wind (~90% of outskirts CO flux)  
  > "almost $90\%$ of the CO flux in the outskirts is found in this quadrant." (4.2 CO Brightness Azimuthal Distribution)
- Redshifted residuals at the tail base interpreted as fallback gas  
  > "these motions all correspond to material falling into the disk potential." (6.4 Inner Tail Redshifted Gas)

## Claim tuples

- H: Does NGC 4858 experience strong, highly inclined ram pressure? | E: Estimate geometry from stellar PA, inclination, radio tail angle and orbital velocity | R: phi_DW = 75 (+10/-27) deg | F: Highly inclined disk-wind angle, though with large uncertainty | **supported**
- H: Is the inner tail asymmetric because of rotation-ram pressure interaction? | E: Azimuthal/quadrant analysis of CO | R: Over 90% of CO beyond the truncation radius is in Q4 | F: Asymmetric inner tail on side rotating into wind, consistent with simulations | **supported**
- H: Is there evidence for gas fallback? | E: Subtract circular velocity model and inspect residuals | R: Redshifted residuals of 20 to 60 km/s at tail base in Q4 | F: Gas previously stripped is falling back into the disk | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Fit circular model to understand how CO velocities compare to a pre-stripped galaxy  
  > "We are concerned with how the CO gas velocities compare to the simplest model of the pre-stripped galaxy" (5.1 Residual Velocities)
- Alternative: Tail behind the disk rejected: would require total velocity >5000 km/s, over 5x the cluster dispersion  
  > "the tail lying behind the disk would require a total velocity through the cluster of $> 5000$km s$^{-1}$" (6 Selected Features with High Velocity Residuals)
- How they decided it was enough: _not stated_
- Limitation (authors): Large uncertainty on disk-wind angle due to assumptions on total velocity  
  > "The uncertainty on this estimate is large, due to the many assumptions required of the galaxy’s total velocity." (7.1 Estimating the 3D Tail Geometry)
- Limitation (authors): Outer rotation curve uncertain  
  > "Since the rotation curve beyond the inner disk is somewhat uncertain" (5.1 Residual Velocities)
- Limitation (authors): Milky Way alphaCO may be too high for RPS galaxies  
  > "the adopted Milky Way value for CO/$M_{H_2}$ possibly being too high for RPS galaxies" (2.1 ALMA CO(2-1))
- Caveat (inferred, ours): Single galaxy; residual interpretation depends on assuming the tail lies in front of the disk
- Caveat (inferred, ours): Residuals from a simple model fitted to moment-1 rather than the cube
- Caveat (inferred, ours): Simulation comparison is qualitative with no matched simulation
- Caveat (inferred, ours): Total velocity assumes projected distance equals true distance

## Reproducibility

- Data public (paper): ALMA project 2021.1.01616.L cited; HST data from MAST  
  > "The data described here may be obtained from the MAST archive" (2.3 HST Imaging)
- Products in archive: _not stated_
- Code: GalPRIME github link given; MASKMOMENT github link given  
  > "<https://github.com/HSouch/GalPRIME>" (footnote)
- Missing: Calibration and observing details
- Missing: Pipeline and CASA versions
- Missing: 3DBarolo and MASKMOMENT settings
- Missing: Simulation snapshots
- Data volume (inferred): ~100 GB to few hundred GB for 12m+7m mosaics of one galaxy
- Score (inferred): 5/5, Public data and pipeline named, with many numeric results, but key settings and calibration are not given.
- Rediscovery candidate: yes, Data are public, the pipeline is standard, and main results (CO flux, H2 mass, residual maps, angles) are numeric.

## Links

- Method: (cite: leroy_phangsalma_2021) (PHANGS-ALMA imaging pipeline)
- Method: (cite: di_teodoro_3d_2015) (3DBarolo rotation curve fitting)
- Companion: Jachym et al. (in prep.) (Full ALMA-JELLY sample and project description)
- Related: ALMA-JELLY (2021.1.01616.L)
- Related: PHANGS-ALMA
- Related: LoTSS

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 63,
  "rate": 0.643
 },
 "evidence_ok": true
}
```
