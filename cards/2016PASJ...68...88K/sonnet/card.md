# The Sunyaev-Zel'dovich effect at 5″: RX J1347.5-1145 imaged by ALMA

`2016PASJ...68...88K` | Publications of the Astronomical Society of Japan 2016 | first author: Kitayama, Tetsu | arXiv: 1607.08833 | DOI: 10.1093/pasj/psw082

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: galaxy_clusters_and_sz
- Question: Can ALMA (7-m plus 12-m arrays, Band 3) image the thermal SZE of RX J1347.5-1145 at 5 arcsec resolution, and how should missing flux be corrected and the map compared with X-ray and earlier SZE data?  
  > "we present detailed analysis procedures including corrections for the missing flux, to provide guiding methods for analyzing and interpreting future SZE images by ALMA." (abstract)
- Target **RX J1347.5-1145**: coordinates _not stated_; z/distance z=0.451  
  > "The target is a galaxy cluster RX J1347.5–1145 at $z=0.451$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00246.S, 2013.1.00120.S, 2013.1.01312.S
- bands: Band 3, central 92 GHz  
  > "the dual-polarization Time Division Mode was adopted with the central observing frequency of 92 GHz and an effective band width of 7.5GHz" (2 Observations and Calibration)
- frequencies and spectral setup: four spectral windows ~2 GHz wide centered at 85, 87, 97, 99 GHz  
  > "the data were taken at four spectral windows with widths $\sim 2$ GHz centered at 85, 87, 97, and 99 GHz, respectively." (2 Observations and Calibration)
- continuum bandwidth: _not stated_
- arrays: 12-m and 7-m arrays, 13 execution blocks  
  > "The data were taken with the 12-m array and the 7-m array at 13 separate Execution Blocks listed in Table [1](#tab-obs) between August 2014 and January 2015." (2 Observations and Calibration)
- configurations: _not stated_
- baselines: 7.4-49 m (7-m); 12.5-347 m (12-m)  
  > "Compact configurations were adopted to cover the projected baseline ranges of $7.4 - 49$ m and $12.5 - 347$ m for the 7-m array and the 12-m array, respectively." (2 Observations and Calibration)
- angular resolution: 12-m beam 4.1"x2.4"; 7-m 20.5"x11.1"; smoothed to 5"  
  > "Synthesized beam FWHMs | $4.1''\times 2.4''$ | $20.5'' \times 11.1''$" (Table 2)
- max recoverable scale: ~40" (shortest baseline 2.1 kλ)  
  > "corresponding to the maximum recoverable scale for the shortest baseline length of 2.1 k$\lambda$ in the present data" (3.3)
- sensitivity: 0.017 mJy/beam at 5" (0.12 mK_CMB); dirty-map rms 0.012 (12-m), 0.083 (7-m) mJy/beam  
  > "The 1$\sigma$ statistical sensitivity of the image is 0.017 mJy/beam or 0.12 mK$_{\rm CMB}$ at the 5 arc-second full width at half maximum." (abstract)
- time on source: _not stated_
- observing dates: August 2014 to January 2015  
  > "EB12-4 | 12-m | 2015-01-04 | 40 | 40.42 | J1337–1257" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **Chandra**: X-ray data (6 ObsIDs, 233.8 ks) for pressure map and simulation input  
  > "the total net exposure time amounts to 233.8 ks." (4.1)
- External data: Spatially resolved deprojected electron temperatures for spherical SZE model  
  > "Spatially resolved and deprojected electron temperatures are taken from Table 7 of (cite: Ota08)" (3.4) [from (cite: Ota08)]
- External data: Peculiar velocity of cluster  
  > "the peculiar velocity of this cluster $v_{\rm pec}=-1040^{+870}_{-840}$ km/s reported by (cite: Sayers16)" (3.4) [from (cite: Sayers16)]
- External data: MUSTANG and NOBA SZE maps used for comparison  
  > "comparison of the ALMA map with previous SZE observations of RX J1347.5–1145 by MUSTANG (cite: Mason10; Korngut11) and NOBA (cite: Komatsu01)" (4.4) [from (cite: Mason10; Korngut11; Komatsu01)]
- External data: Peak y-parameter 8e-4 for simulation normalization  
  > "$y_{\rm   peak}=8\times10^{-4}$ as inferred from the previous SZE measurements of this cluster (cite: Komatsu01; Kitayama04)" (4.2) [from (cite: Komatsu01; Kitayama04)]
- Simulation/model as data: Simulated ALMA observations (simobserve) of X-ray derived pseudo pressure map as input SZE model  
  > "Visibility data were then produced using the CASA task *simobserve*." (4.2)

## Processing

### Calibration

- pipeline or manual: 12-m: standard Cycle 2 reduction script; 7-m: ALMA pipeline; QA2 data used  
  > "The data taken with the 7-m array were calibrated by the ALMA pipeline using the CASA version 4.2.2." (2 Observations and Calibration)
- casa version: CASA 4.3.1 (12-m), 4.2.2 (7-m) for calibration; 4.5.0 for imaging  
  > "program version 4.3.1 as implemented in a standard reduction script for ALMA Cycle 2 data." (2 Observations and Calibration)
- pipeline version: _not stated_
- archive products used as is: QA2 products used  
  > "We use the data produced from the second stage of ALMA’s Quality Assurance process (QA2) for both the 12-m array and the 7-m array." (2 Observations and Calibration)
- flux calibrator: Mars, Callisto, Ceres, Ganymede, J1337-1257; Butler-JPL-Horizons-2012 model  
  > "The Butler-JPL-Horizons-2012 Model (Butler 2012) was used for determining the absolute flux density of solar system objects." (2 Observations and Calibration)
- flux scale uncertainty: 6%  
  > "we estimate the flux calibration error in the present analysis to be $6\%$" (2 Observations and Calibration)
- self calibration: _not stated_

### Imaging

- task: CASA mosaic, multi-frequency synthesis  
  > "We use the multi-frequency synthesis mode for spectral gridding and the mosaic mode for imaging." (3 Imaging Analysis)
- deconvolver: Multi-Scale CLEAN, scales [0,5,8,13,20,30,45]", small-scale bias 0.4, gain 0.05, threshold 0.03 mJy (2.5σ)  
  > "we adopt the scales \[$0, ~5'', ~8'', ~13'',   ~20'', ~30'', ~45''$\] with the small-scale bias parameter of 0.4 as our fiducial choice." (3.3)
- weighting robust: natural  
  > "Natural weighting is adopted to maximize sensitivity to an extended signal." (3 Imaging Analysis)
- uv taper: _not stated_
- cell size: 0.5"  
  > "The pixel size is $0.5''$." (3.1)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: applied  
  > "All the results presented have been corrected for primary beam attenuation." (3 Imaging Analysis)
- array combination: 7-m and 12-m visibilities imaged jointly  
  > "the dynamic range of the signal is enhanced significantly once the data taken by the 12-m array and the 7-m array are combined." (3.1)
- smoothing: Gaussian kernel to 5" FWHM, beam asymmetry corrected  
  > "Figure [4](#fig-sz) shows the deconvolved map smoothed to an effective beam size of $5''$ FWHM." (3.4)
- final beam: combined dirty beam 4.1"x2.5", PA 84.1 deg  
  > "The synthesized beam of the combined map has $4.1''\times 2.5''$ FWHMs with a position angle $84.1^{\circ}$." (3.1)
- final rms: 0.017 mJy/beam at 5"  
  > "we measure the rms noise level of 0.017 mJy/beam over a diameter of $90''$ around the field center." (3.4)

### Not stated but needed to reproduce (our reading)

- Phase center coordinates (blank in text)
- Exact CASA task parameters (niter, mask, spw selection) for tclean/clean
- Simulation details: simobserve PWV and noise settings, exact large-scale fall-off factor shape
- Contour-binning and XSPEC fit details for pseudo pressure map
- Whether Band 3 7-m QA2 weights were rescaled
- Number of pixels/image size

## Analysis recipe

1. **Dirty maps and noise**: Dirty images from calibrated visibilities; noise from half-split difference maps  
  > "we also created a difference map by dividing the data set in half, taking a difference between their dirty images, and dividing it by 2" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: rms nearly constant within 90" diameter  
  > "the noise level is nearly constant except at the map edge." (3.1)
2. **Subtract central AGN**: Point-source fit in uv plane for uv>30 kλ, separately for 84-88 and 96-100 GHz, subtracted from visibilities  
  > "We determined the position and the flux density of the central AGN at our observing bands using long baseline data at the $uv$ distance larger than $30$k$\lambda$." (3.2)
   - software: CASA
   - fitting: Point source model with free flux and position fitted to 12-m EB12-1 to 4 simultaneously  
  > "we fitted a point source model to the $uv$ data from the central pointing (without mosaicing) varying both the flux density and the position." (3.2)
   - validation: 7-m data at 7-16 kλ give consistent flux  
  > "The flux values measured by the two arrays are thus consistent within the statistical and calibration errors." (3.2)
3. **Deconvolve extended SZE**: Multi-Scale CLEAN with scale set chosen for minimal residuals and maximal recovered flux  
  > "Having searched for a combination of parameters that gives minimal residuals as well as the maximal recovered flux" (3.3)
   - software: CASA
   - parameter: loop gain 0.05, threshold 0.03 mJy  
  > "We also use a loop gain of 0.05 suitable for diffuse emission and a flux threshold of 0.03 mJy ($2.5   \sigma$)" (3.3)
   - fitting: _not stated_
   - validation: Converged for largest scale 40-50"; insensitive to bias <0.8  
  > "the deconvolved results are insensitive to the value of the small-scale bias parameter as long as its value is less than 0.8." (3.3)
4. **X-ray pseudo pressure map**: Chandra spectra in contour-binned regions give projected T and normalization; pseudo density and pressure  
  > "The pseudo pressure map is a product of the pseudo density and the projected X-ray temperature." (4.1)
   - software: CIAO, XSPEC
   - parameter: S/N threshold 83 (~7000 counts)  
  > "We adopt the S/N threshold of 83 ($\sim 7000$ counts)" (4.1)
   - assumption: Gas uniformly distributed over line-of-sight length L; CIE plasma; Anders & Grevesse abundances; NH=4.6e20  
  > "assuming that the gas is distributed uniformly over the line-of-sight distance of $L$" (4.1)
   - fitting: Spectral fit in XSPEC  
  > "Spectral fitting was done with XSPEC version 12.9.0o (cite: Arnaud96), assuming that the intracluster plasma is in collisional ionization equilibrium" (4.1 X-ray Data of RX J1347.5–1145)
   - validation: Compared morphology with SZE map  
  > "The pseudo pressure map (panel d) shows a reasonable agreement with the ALMA SZE map" (4.1)
5. **Imaging simulations for missing flux**: Simulate ALMA observations of pressure-map model with simobserve; derive Fourier-space correction (i) and real-space linear relation (ii)  
  > "we performed imaging simulations using the latter as a realistic input model to quantify the degree of missing flux" (4.2)
   - software: CASA simobserve
   - parameter: y_peak=8e-4; four spectral windows 1.875 GHz each  
  > "We created model images separately at four spectral windows centered at 85, 87, 97, and 99 GHz with an effective bandwidth of 1.875 GHz each." (4.2)
   - assumption: Relativistic SZE correction of Nozawa05 with projected temperature  
  > "A relativistic correction to the SZE intensity by (cite: Nozawa05) was applied" (4.2)
   - fitting: Linear fit I_out = c1 I_in + c0 to unbinned pixels  
  > "with $c_1=0.88$ and $c_0=3.6 ~\mu$Jy/arcsec$^2$." (4.2)
   - validation: Repeated with y_peak doubled/halved and different noise; relations converge  
  > "we repeated the simulations by doubling or halving the signal of the entire input map" (4.2)
6. **Differential y map**: Divide by 0.88, subtract mean at 40" from peak, convert to Δy with relativistic correction  
  > "the map is divided by the mean reduction factor of $0.88$ ($c_1$ in equation  \[[\[eq-conv\]](#eq-conv)\]) and the mean value at $40''$ from the emission peak" (4.3)
   - fitting: _not stated_
   - validation: Comparison with MUSTANG and NOBA maps  
  > "Morphology of the ALMA map is in good agreement with both MUSTANG and NOBA maps" (4.4)

## Software

- **CASA** 4.2.2, 4.3.1 (calibration); 4.5.0 (imaging): Calibration, imaging, Multi-Scale CLEAN, simobserve  
  > "We performed imaging analysis using CASA version 4.5.0 on the visibility data produced by the ALMA QA2 process." (3 Imaging Analysis)
- **CIAO** 4.7: Chandra data processing  
  > "The data were processed using CIAO version 4.7 (cite: Fruscione06)" (4.1)
- **XSPEC** 12.9.0o: X-ray spectral fitting  
  > "Spectral fitting was done with XSPEC version 12.9.0o (cite: Arnaud96)" (4.1)
- **contour binning** : X-ray thermodynamic mapping regions  
  > "We performed X-ray thermodynamic mapping using the contour binning algorithm (cite: Sanders06)" (4.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AGN flux density at 86 GHz | 4.16 | ±0.03 stat ±0.25 sys | mJy | 2 | we find $F_\nu=4.16 \pm 0.03 \pm 0.25$ mJy and $3.96 \pm 0.03 \pm 0.24$ mJy at the central frequencies of 86 GHz and 98 GHz |
| AGN flux density at 98 GHz | 3.96 | ±0.03 stat ±0.24 sys | mJy | 2 | $3.96 \pm 0.03 \pm 0.24$ mJy at the central frequencies of 86 GHz and 98 GHz, respectively |
| AGN spectral index 86-98 GHz | -0.38 | ±0.12 | dimensionless | 2 | The spectral index of the source inferred from the two measurements over a narrow range between 86 GHz and 98 GHz is $-0.38 \pm 0.12$. |
| SZE intensity at south-east peak | -0.286 | ±0.017 ±0.017 | mJy/beam | 3 | $-0.286 \pm 0.017 \pm 0.017$ mJy/beam |
| SZE flux within 40" of SE peak | -12.4 | ±0.2 ±0.8 | mJy | 3 | The measured flux within a radius of $40''$ from the south-east peak is $-12.4 \pm 0.2 \pm 0.8$ mJy. |
| Fit slope c1 | 0.88 | not stated | dimensionless | 5 | with $c_1=0.88$ and $c_0=3.6 ~\mu$Jy/arcsec$^2$. |
| Peak differential Compton y | 5.9e-4 | ±0.4 ±0.8 (e-4) | dimensionless | 6 | The peak value of the Compton $y$-parameter is $\Delta y = (5.9 \pm 0.4 \pm 0.8) \times 10^{-4}$ |
| Integrated ΔY within 40" | 1.6e-11 | ±0.03 ±0.8 (e-11) | sr | 6 | $\Delta Y = \int \Delta y d\Omega = (1.6 \pm 0.03 \pm 0.8)\times 10^{-11}$ |

## Qualitative findings

- SZE decrement peak lies 11" south-east of the central AGN, consistent with X-ray pressure peak and hot (>20 keV) gas  
  > "its peak position (,) is at $11''$ to the south-east from the central AGN." (3.4)

## Claim tuples

- H: ALMA can image the SZE at 5" resolution | E: 7-m + 12-m Band 3 mosaic, point-source subtraction, Multi-Scale CLEAN | R: Decrement detected at >15σ with 0.017 mJy/beam noise at 5" | F: First ALMA SZE image with highest resolution to date, recovering structure to 40" | **supported**
- H: SZE map agrees with X-ray pressure | E: Compare with Chandra pseudo pressure map | R: Reasonable agreement including SE peak | F: ALMA SZE traces the pressure structure | **supported**
- H: Missing flux can be corrected | E: Imaging simulations | R: ~80% lost at smallest uv; linear relation with c1=0.88 plus offset | F: Missing flux mostly a constant offset | **supported**

## Reasoning

- Why this data: Band 3 has largest field of view, lowest system temperature, minimal synchrotron and dust contamination  
  > "Band 3 is the most suitable for the SZE imaging owing to the largest field-of-view, the lowest system temperature, and minimal contamination by synchrotron and dust emission." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux on large scales due to no Total Power Array  
  > "The accuracy of the map is limited primarily by missing flux arising from the lack of short-spacing data in the current configuration of ALMA." (Conclusions)
- Caveat (inferred, ours): Missing-flux correction depends on a model built from X-ray pressure, introducing model dependence
- Caveat (inferred, ours): Absolute flux scale scatter (6%) across calibrators
- Caveat (inferred, ours): 10% deficit relative to spherical model not resolved

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00246.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Phase center coordinates
- Missing: Exact simulation configuration
- Missing: Large-scale fall-off factor values
- Data volume (inferred): ~100-300 GB raw for 13 EBs (mosaics, four spws)
- Score (inferred): 4/5, Detailed recipe with parameters and public data; some simulation and X-ray details are unspecified.
- Rediscovery candidate: yes, Public ALMA and Chandra data, detailed imaging recipe, numeric results (flux, y, c1).

## Links

- Method: (cite: Cornwell08) (Multi-Scale CLEAN)
- Method: (cite: Nozawa05) (Relativistic SZE correction)
- Method: (cite: Sanders06) (Contour binning)
- Companion: (cite: Yamada12) (ALMA SZE imaging simulations)
- Companion: (cite: Komatsu01) (NOBA SZE detection of substructure)
- Related: MUSTANG
- Related: NOBA
- Related: CARMA
- Related: NIKA

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 58,
  "rate": 0.744
 },
 "evidence_ok": true
}
```
