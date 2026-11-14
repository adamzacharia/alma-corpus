# The multi-thermal chromosphere. Inversions of ALMA and IRIS data

`2020A&A...634A..56D` | Astronomy and Astrophysics 2020 | first author: da Silva Santos, J. M. | arXiv: 1912.09886 | DOI: 10.1051/0004-6361/201937117

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: sun
- Question: How do temperature and microturbulence stratification in plage and quiet Sun change when ALMA 1.25 mm continuum is added to NLTE inversions of IRIS NUV spectra, and what do cool holes and hot transient brightenings imply?  
  > "We revisit the problem of the stratification of temperature and microturbulence in plage and the quiet Sun, now adding millimeter (mm) continuum observations provided by the Atacama Large Millimiter Array (ALMA)" (abstract)
- Target **Plage in active region NOAA 12651**: coordinates IRIS raster initially centered at [x,y]~[-265'', 269''] (helioprojective)  
  > "ALMA and IRIS co-observed part of a plage on the eastern side of the active region NOAA 12651 at $\mu\approx0.92$" (2.1 Data reduction and alignment); z/distance mu ~ 0.92 (solar disk)  
  > "ALMA and IRIS co-observed part of a plage on the eastern side of the active region NOAA 12651 at $\mu\approx0.92$" (2.1 Data reduction and alignment); distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00050.S
- bands: Band 6, effective wavelength 1.25 mm  
  > "resulting in one brightness temperature map at 2 s cadence corresponding to the central frequency of Band 6 and thus to an effective wavelength of 1.25 mm" (2.1 Data reduction and alignment)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: Interferometric scans plus Total Power single-dish scans  
  > "consist of five interferometric scans (cite: 2017SoPh..292...87S) and five single-dish scans of the full solar disk with Total Power (TP) antennas" (2.1 Data reduction and alignment)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.8'' maximum ALMA resolution  
  > "maximum ALMA resolution ($\sim$0.8")" (6.1 Limitations of the inversions)
- max recoverable scale: _not stated_
- sensitivity: noise ~30 K at most  
  > "The noise level is $\sim30$ K at most." (2.1 Data reduction and alignment)
- time on source: 37 min net interferometric time in five scans  
  > "The net interferometric observing time on target spans 37 min divided into five scans" (2.1 Data reduction and alignment)
- observing dates: 22 April 2017, 15:59-16:34 UT  
  > "The observations were carried on 22 April 2017" (2.1 Data reduction and alignment)
- pi or archival as stated: _not stated_
- Line: Mg II h and k (IRIS NUV) (not stated)
- Other facility **IRIS**: NUV spectra (Mg II h&k, UV triplet, Ni I) and SJI  
  > "The IRIS data consist of dense (0.349$''$) 16-step rasters" (2.1 Data reduction and alignment)
- Other facility **Hinode/SOT/SP**: Fe I 6301/6302 slit scans for context and magnetic field  
  > "Hinode/SOT/SP (cite: 2008SoPh..249..167T) slit scans of the Fe I 6301 and 6302 Å lines" (2.1 Data reduction and alignment)
- Other facility **SDO AIA/HMI**: context images and line-of-sight magnetograms  
  > "we also use images taken with the Atmospheric Imaging Assembly" (2.1 Data reduction and alignment)
- External data: Quiet-Sun disk-center brightness temperature ~5900 K used as TP reference scale  
  > "the absolute scale is corrected by rescaling the TP maps based on the average value in the disk center region to a reference value of 5900 K" (2.1 Data reduction and alignment) [from (cite: 2017SoPh..292...88W)]

## Processing

### Calibration

- pipeline or manual: Solar ALMA Pipeline (SoAP2) with self-calibration, multi-scale CLEAN, primary beam correction, TP combination  
  > "The data are processed with the Solar ALMA Pipeline (SoAP2, Szydlarski et al. in prep)" (2.1 Data reduction and alignment)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated data downloaded from ALMA Archive  
  > "The calibrated ALMA Band 6 data (as downloaded from the ALMA Archive" (2.1 Data reduction and alignment)
- flux calibrator: _not stated_
- flux scale uncertainty: TP calibration 10-15% (590-885 K); combined likely 3-5%  
  > "the absolute calibration of the single-dish TP brightness temperatures has an uncertainty of bettween 10 and 15%" (2.1 Data reduction and alignment)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: multi-scale CLEAN in CASA  
  > "via application of the multi-scale CLEAN algorithm by (cite: 2011A&A...532A..71R) as implemented in CASA" (2.1 Data reduction and alignment)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: interferometric combined with TP data  
  > "combination of the interferometric data with the TP data" (2.1 Data reduction and alignment)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA data processing details with SoAP  
  > "We refer to (cite: Wsubmitted) for more details about data processing with SoAP." (2.1 Data reduction and alignment) [from (cite: Wsubmitted)]
- IRIS reduction (flat-field, dark, geometry, wavelength)  
  > "calibrated in wavelength as described in (cite: 2018SoPh..293..149W)" (2.1 Data reduction and alignment) [from (cite: 2018SoPh..293..149W)]
- Ni I 2814.4 line selection  
  > "a selected photospheric line of Ni I at 2814.4 Å as in (cite: 2016ApJ...830L..30D)" (3.1 Inversion setup) [from (cite: 2016ApJ...830L..30D)]

### Not stated but needed to reproduce (our reading)

- SoAP2 parameters (CLEAN scales, self-cal solints, imaging weights, cell size) and CASA version
- Form and values of the ad hoc ALMA weighting function in chi2
- Regularization weights alpha and node positions
- Initial model atmospheres and data weights sigma
- Exact alignment procedure and ALMA PSF treatment
- Selection of pixels for Monte Carlo tests

## Analysis recipe

1. **Reduce and align ALMA and IRIS data**: Process ALMA with SoAP2, rescale TP to 5900 K, combine up to 14 ALMA images per IRIS raster, interpolate to common grid, convert Tb to intensity via Planck function  
  > "Up to 14 ALMA images were then combined to replicate the IRIS rasters" (2.1 Data reduction and alignment)
   - software: CASA, SoAP2
   - fitting: _not stated_
   - validation: _not stated_
2. **NLTE inversions of IRIS vs IRIS+ALMA**: STiC regularized Levenberg-Marquardt inversion of Mg II h&k, UV triplet, Ni I, NUV continuum with and without the 1.25 mm point; NLTE hydrogen ionization, free-free mm opacity  
  > "which is a regularized Levenberg-Marquardt code for multi-atom NLTE inversions of multiple spectral lines and continua including partial frequency redistribution (PRD) effects" (3.1 Inversion setup)
   - software: STiC
   - parameter: 19 temperature nodes, 9 vturb nodes, 7 vLOS nodes  
  > "We used nine and seven equidistant nodes for $v_{\rm turb}$ and $v_{\rm LOS}$, respectively." (3.1 Inversion setup)
   - parameter: IRIS instrumental profile Gaussian FWHM 53 mÅ  
  > "Gaussian function with a fullwidth at half maximum of 53 mÅ" (3.1 Inversion setup)
   - assumption: 1D plane-parallel hydrostatic atmosphere; instantaneous NLTE electron densities; cyclotron and synchrotron neglected  
  > "STiC code which assumes a 1D, plane-parallel atmosphere in hydrostatic equilibrium" (6.1 Limitations of the inversions)
   - fitting: chi2 minimization with regularization penalties and ad hoc ALMA weighting  
  > "we introduced an *ad hoc* weighting function that ensures that the ALMA data are well fitted" (3.1 Inversion setup)
   - validation: Monte Carlo tests for overfitting; node-count tests  
  > "we ran a set of Monte Carlo simulations as explained in Section" (3.1 Inversion setup)
3. **Response functions and uncertainties**: Numerical temperature response functions; up to 100 Monte Carlo inversions per pixel with random starting atmospheres  
  > "we ran sets of up to $n=100$ Monte Carlo simulations per pixel of synthetic IRIS and ALMA data generated from the best-fit models" (3.3 Uncertainties)
   - software: STiC
   - fitting: _not stated_
   - validation: 68% confidence intervals accurate to <0.5%  
  > "accurate (to <0.5%) 68% confidence intervals on the parameters" (3.3 Uncertainties)
4. **Synthesize CO lines in cool holes**: LTE vibration-rotation CO lines near 4.67 micron computed from inverted models  
  > "We computed a few vibration-rotation CO lines in the commonly observed near-infrared (NIR) range around 4.67 $\rm \mu m$ assuming LTE." (4.3 Chromospheric holes)
   - assumption: _not stated_
   - fitting: _not stated_
   - validation: _not stated_
5. **Time evolution of plage subfield**: Invert 18 time steps (~7.5 min) with IRIS and IRIS+ALMA; compare temperature, vturb, vLOS and Mg II wavelength-time diagrams  
  > "We inverted 18 time steps, which is about $\sim7.5$ min (before ALMA pauses for calibration)" (4.5 Time evolution of the plage region)
   - software: STiC
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **STiC** : NLTE inversions  
  > "The inversions were performed with the STockholm Inversion Code" (3.1 Inversion setup)
- **CASA** : multi-scale CLEAN within SoAP2  
  > "as implemented in CASA" (2.1 Data reduction and alignment)
- **SolarSoft iris_get_response** : IRIS radiometric calibration  
  > "using version four of the calibration files obtained using the *iris_get_response* routine in SolarSoft" (2.1 Data reduction and alignment)
- **SunPy** : data analysis  
  > "This research has made use of SunPy, an open-source and free community-developed solar data analysis Python package" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean plage Tb at 1.25 mm | 8500 | not stated | K | 1 | The average value for the center of the plage region is $\sim8500$ K |
| Median vturb at logtau=-5, IRIS vs IRIS+ALMA (full FoV) | ~4 and ~2 | not stated | km/s | 2 | The median values for the entire FoV are approximately $\sim4\,\rm km\,s^{-1}$ and $\sim2\,\rm km\,s^{-1}$ for the IRIS and IRIS+ALMA inversions respectively |
| Median depth-averaged vturb in plage over time, IRIS vs IRIS+ALMA | 5.5 and 4.8 | 16-84%: 4.4-6.6 and 3.9-5.9 | km/s | 5 | $5.5^{6.6}_{4.4}\rm\,km\,s^{-1}$ and $4.8^{5.9}_{3.9}\rm\,km\,s^{-1}$ in the IRIS and IRIS+ALMA inversions |
| Std of 1.25 mm residuals | 3 | not stated | % | 2 | The standard deviation of the distribution of the residuals at 1.25 mm is 3%. |
| Coolest region Tb: mean and minimum | ~4050 and ~3100 | not stated | K | 1 | has an average $T_{\rm b}\sim4050$ K and a minimum $T_{\rm b}\sim3100$ K |
| Shock periodicity in Mg II peaks | 3.5-4 | not stated | min | 5 | we find a shock wave signature in the Mg II peak intensities with periods between 3.5 and 4 min |

## Qualitative findings

- IRIS-only inversions fail to reproduce observed ALMA contrast; adding ALMA increases temperature contrast and lowers microturbulence  
  > "the IRIS+ALMA inversions have increased contrast and temperature range, and tend to favor lower values of microturbulence" (abstract)

## Claim tuples

- H: Does mm continuum constrain chromospheric temperature and microturbulence in NLTE inversions of real data? | E: Compare IRIS-only and IRIS+ALMA STiC inversions | R: IRIS+ALMA gives higher temperature contrast and lower vturb (median ~2 vs ~4 km/s) | F: ALMA provides a useful constraint on chromospheric temperature and vturb | **supported**
- H: Cool ALMA holes are chromospheric and could host CO | E: Inversions with more nodes plus LTE CO synthesis | R: Temperature dips at logtau -6 to -5 reproduce cool mm values; CO lines show small chromospheric contribution | F: Localized cool regions may allow CO to form | **partially**
- H: Hot mm brightenings relate to shocks and non-equilibrium ionization | E: Time series inversions and Mg II wavelength-time diagrams | R: ~2000 K temperature rise, velocity gradient sign change, 3.5-4 min Mg II shock pattern | F: Shock heating, possibly with non-equilibrium hydrogen ionization | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: LTE hydrogen ionization rejected in favour of NLTE electron densities, which are more uniform and more realistic  
  > "We compared inversions with LTE and NLTE hydrogen ionization and verified that the NLTE calculations give us much more uniform electron densities" (3.1 Inversion setup)
- How they decided it was enough: _not stated_
- Limitation (authors): STiC cannot treat time-dependent hydrogen ionization; 1D plane-parallel assumption; resolution difference between IRIS and ALMA  
  > "It is not possible to take these effects into account with STiC or with any other current inversion code to our knowledge." (3.1 Inversion setup)
- Caveat (inferred, ours): Ad hoc ALMA weighting may force fits and bias results
- Caveat (inferred, ours): Single field and single raster/short time series limits generality
- Caveat (inferred, ours): Absolute ALMA Tb scale uncertain by up to 10-15%
- Caveat (inferred, ours): Cool holes fit poorly, so CO inference rests on imperfect models

## Reproducibility

- Data public (paper): ALMA calibrated data downloaded from ALMA Archive; STiC on GitHub  
  > "The calibrated ALMA Band 6 data (as downloaded from the ALMA Archive" (2.1 Data reduction and alignment)
- Products in archive: _not stated_
- Code: STiC publicly available on GitHub  
  > "https://github.com/jaimedelacruz/stic" (3.1 Inversion setup)
- Missing: SoAP2 pipeline details (in prep)
- Missing: Exact ALMA weighting function and regularization weights
- Missing: Inversion initial models and node placement
- Data volume (inferred): tens of GB for ALMA plus IRIS rasters; inversions need heavy HPC
- Score (inferred): 3/5, Public data and public code, but key parameters (weighting function, regularization, SoAP2 settings) are missing and inversions are very costly.
- Rediscovery candidate: no, Inversion recipe lacks key weights and requires large computing; pipeline unpublished.

## Links

- Method: (cite: 2016ApJ...830L..30D) (STiC inversion method)
- Method: (cite: 2019A&A...623A..74D) (STiC regularization)
- Method: (cite: 2017SoPh..292...88W) (ALMA TP calibration)
- Companion: (cite: PaperI) (Synthetic experiments with IRIS+ALMA inversions)
- Companion: (cite: Wsubmitted) (SoAP data processing)
- Related: SolarALMA

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 41,
  "rate": 0.532
 },
 "evidence_ok": true
}
```
