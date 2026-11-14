# ALMA 690 GHz Observations of IRAS 16293-2422B: Infall in a Highly Optically Thick Disk

`2013ApJ...764L..14Z` | The Astrophysical Journal Letters 2013 | first author: Zapata, Luis A. | arXiv: 1301.3105 | DOI: 10.1088/2041-8205/764/1/L14

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: What are the continuum structure, line morphology and infall kinematics of IRAS 16293-2422B at 690 GHz, and is its dust optically thick?  
  > "We suggest that the presence of this inner depression and the fact that we do not see inner structure (or a flat structure) in the continuum is produced by very optically thick dust" (abstract)
- Target **IRAS 16293-2422B**: coordinates _not stated_; z/distance 120 pc  
  > "Located at a distance of 120 pc (cite: Lau2008) in the $\rho$ Ophiuchi star forming region" (Introduction); distance from Loinard et al. 2008 (cite: Lau2008)  
  > "Located at a distance of 120 pc (cite: Lau2008) in the $\rho$ Ophiuchi star forming region" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00007.SV
- bands: 690 GHz (0.45 mm)  
  > "we report $\sim$0.2 arcsec resolution 690 GHz observations obtained with the Atacama Large Millimeter/Submillimeter Array (ALMA)" (Introduction)
- frequencies and spectral setup: 4 spectral windows of 1875 MHz, 3840 channels each; 0.488 MHz channels, 0.4 km/s resolution after Hanning smoothing  
  > "The ALMA digital correlator was configured in 4 spectral windows of 1875 MHz and 3840 channels each." (Observations)
- continuum bandwidth: _not stated_
- arrays: 15 12-m antennas  
  > "The array at that point only included antennas with diameters of 12 meters." (Observations)
- configurations: _not stated_
- baselines: 105 baselines, 26 to 403 m  
  > "The 105 independent baselines ranged in projected length from 26 to 403 m." (Observations)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: line rms ~50 mJy/beam per 0.4 km/s; continuum rms 20 mJy/beam  
  > "The resulting r.m.s. noise for the line images was about 50 mJy beam$^{-1}$ in a velocity width of 0.4 km s$^{-1}$ and 20 mJy beam$^{-1}$ for the continuum emission" (Observations)
- time on source: _not stated_
- observing dates: April 2012  
  > "The observations were made with fifteen antennas of ALMA on April 2012" (Observations)
- pi or archival as stated: ALMA science verification data  
  > "during the ALMA science verification data program" (Observations)
- Line: H13CN J=8-7 v=0 (690.55207 GHz)
- Line: HC15N J=8-7 v=0 (688.27379 GHz)
- Line: CH3OH 9(3,6)-8(2,7) vt=0 (687.22456 GHz)
- External data: Dust mass opacity extrapolated to 0.45 mm for coagulated grains without ice mantles (2.2 cm2/g)  
  > "obtained extrapolating at these wavelenghts the value obtained by (cite: Oss1994) for coagulated dust particles with no ice mantles" (0.45 mm continuum emission) [from (cite: Oss1994)]
- External data: Opacity index beta = 0.6  
  > "Assuming also an opacity power-law index $\beta$ = 0.6 (cite: Rod2005)" (0.45 mm continuum emission) [from (cite: Rod2005)]
- External data: Pineda et al. two-layer fit results at 220 GHz (Tx = 40 K) used to set Tx  
  > "From the fits of Pineda et al. (2012) to lines at lower frequencies (220 GHz) they estimate $T_x$ = 40 K." (Modeling) [from Pineda et al. (2012) (cite: Pin2012)]

## Processing

### Calibration

- pipeline or manual: calibrated in CASA (mode not specified)  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Juno  
  > "Observations of Juno provided the absolute scale for the flux density calibration" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "We used a robust parameter of 0.5 in the CLEAN task." (Observations)
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
- final beam: 0.31 x 0.18 arcsec, PA = -69.3 deg  
  > "at an angular resolution of $0\rlap.{''}31$ $\times$ $0\rlap.{''}18$ with a P.A. = $-69.3^\circ$" (Observations)
- final rms: line 50 mJy/beam per 0.4 km/s; continuum 20 mJy/beam  
  > "about 50 mJy beam$^{-1}$ in a velocity width of 0.4 km s$^{-1}$ and 20 mJy beam$^{-1}$ for the continuum emission" (Observations)

### Inherited from earlier work

- Modified two-layer infall model as described by Pineda et al. (2012)  
  > "We fitted the spectral profile using a modified two-layer model (Myers et al. 1996; Di Francesco et al 2001; Kristensen et al. 2012), as described by Pineda et al. (2012)." (Modeling) [from Pineda et al. (2012) (cite: Pin2012)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure (SV calibrated data vs. own reduction)
- Gain, bandpass calibrator assignment per execution and flux scale uncertainty
- Line-free channels and continuum subtraction method
- Cell size, image size, clean threshold, masks
- Grid ranges and fit statistic for the two-layer model
- Continuum position/coordinates and deconvolution method for size
- Velocity range for moment maps

## Analysis recipe

1. **Calibrate and image continuum and lines**: CASA calibration and CLEAN imaging, robust 0.5  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (Observations)
   - software: CASA, KARMA
   - parameter: robust = 0.5  
  > "We used a robust parameter of 0.5 in the CLEAN task." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Brightness temperature and lower-limit dust mass**: Planck-equation Tb from flux and Gaussian beam; optically thin isothermal dust mass  
  > "Assuming that the dust is optically thin and isothermal, the dust mass (M$_d$) will be directly proportional to the flux density" (0.45 mm continuum emission)
   - assumption: kappa = 2.2 cm2/g, beta = 0.6, Td = 160 K, d = 120 pc  
  > "as well as a characteristic dust temperature (T$_d$) of 160 K, we estimated a lower limit for the mass for the disk of about 0.03 M$_\odot$" (0.45 mm continuum emission)
   - fitting: _not stated_
   - validation: Mass uncertainty factor of five from range of opacities in Ossenkopf & Henning  
  > "the level of uncertainty in the mass lower limit is a factor of five" (0.45 mm continuum emission)
3. **Moment maps and velocity gradient / dynamical mass**: Moment 0 and 1 maps; Keplerian mass from east-west gradient, corrected by sin(i) with i=5 deg  
  > "If we assume that the rotation is Keplerian and attribute it to a disk in rotation then the dynamical mass associated to this velocity gradient corresponds to only 0.1 M$_\odot$" (Molecular line emission)
   - software: CASA, KARMA
   - assumption: Keplerian rotation, inclination 5 deg  
  > "if we correct by the inclination angle dividing this mass by the $\sin \theta$ with $\theta$ say 5$^\circ$, we obtain a value of 1.2 M$_\odot$" (Molecular line emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit inverse P-Cygni profiles with two-layer infall model**: Modified two-layer model with fixed Tc=160 K, Phi=0.37, Tx=50 K, Tf=3 K; fit Vin, sigma_v, tau0, VLSR  
  > "The fitting was minimized with a grid search, obtaining the following parameters: $V_{in}$ = 0.7 km s$^{-1}$, $\sigma_v$ = 0.6 km s$^{-1}$, and $\tau_0$ =0.17." (Modeling)
   - parameter: Tc = 160 K, Phi = 0.37, Tx = 50 K  
  > "The adopted filling fraction of the continuum source, $\Phi$ =0.37 is consistent with the ratio of solid angles between the region in absorption to the region in emission." (Modeling)
   - assumption: Tx decreases as sqrt of distance; Pineda gas 50% more distant  
  > "Assuming that the excitation temperature of the molecules decreases as the square root of the distance and that the gas sampled by Pineda et al. (2012) is 50% more distant than that sampled by us, we adopt $T_x$ = 50 K." (Modeling)
   - fitting: Grid search minimization  
  > "The fitting was minimized with a grid search" (Modeling)
   - validation: Compared with Pineda et al. 2012 parameters at 220 GHz  
  > "Several of the parameters are quite similar to those derived by Pineda et al. (2012) from lines at 220 GHz." (Modeling)

## Software

- **CASA** : Calibration, imaging and analysis  
  > "The data were calibrated, imaged, and analyzed using the Common Astronomy Software Applications (CASA)." (Observations)
- **KARMA** : Data analysis/visualization  
  > "To analyze the data, we also used the KARMA software (cite: Goo1996)." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum deconvolved size | 400 | ±55 | milli-arcsec (~50 AU) | 1 | The dust compact source has a deconvolved size of about 400 $\pm$ 55 *milli-arcseconds* or a spatial size of 50 AU |
| Continuum flux density | 12.5 | ±0.5 | Jy | 1 | The flux density of IRAS 16293$-$2422B at these wavelengths is 12.5 $\pm$ 0.5 Jy and has a peak flux of 3.2 $\pm$ 0.2 Jy Beam$^{-1}$. |
| Continuum peak flux | 3.2 | ±0.2 | Jy/beam | 1 | has a peak flux of 3.2 $\pm$ 0.2 Jy Beam$^{-1}$ |
| Brightness temperature | 160 | not stated | K | 2 | we estimated a brigthness temperature at these wavelengths for IRAS16293$-$2422B of 160 K |
| Disk mass lower limit | 0.03 | factor of five | Msun | 2 | we estimated a lower limit for the mass for the disk of about 0.03 M$_\odot$ |
| Molecular ring outer diameter | 850 | ±50 | milli-arcsec | 3 | The molecular ring like structure has a diameter of 850 $\pm$ 50 *milli-arcseconds* and an inner diameter of 300 $\pm$ 50 *milli-arcseconds* |
| Velocity gradient | 1.3 over 60 AU | not stated | km/s | 3 | a clear east-west velocity gradient of approximately 1.3 km s$^{-1}$ over 60 AU |
| Infall velocity | 0.7 | not stated | km/s | 4 | $V_{in}$ = 0.7 km s$^{-1}$, $\sigma_v$ = 0.6 km s$^{-1}$, and $\tau_0$ =0.17 |
| Velocity dispersion | 0.6 | not stated | km/s | 4 | $\sigma_v$ = 0.6 km s$^{-1}$ |
| Line-center opacity tau0 | 0.17 | not stated | dimensionless | 4 | $\tau_0$ =0.17 |

## Qualitative findings

- Line emission forms a ring with central hole around the continuum; cavity to the southeast likely from outflow  
  > "the ring like structure is not completely closed, there is a small cavity towards its southeast" (Molecular line emission)

## Claim tuples

- H: Dust in IRAS 16293-2422B is very optically thick at 690 GHz | E: Continuum size and brightness temperature, line hole size | R: Compact 400 mas featureless source, Tb 160 K, line hole comparable to continuum size | F: Very optically thick dust in innermost region | **supported**
- H: 690 GHz lines trace faster, more turbulent infall closer to the star than 220 GHz | E: Two-layer model fit of inverse P-Cygni profiles | R: Vin 0.7 and sigma 0.6 km/s vs ~0.5 and 0.3 for Pineda | F: Faster, more turbulent gas closer to the central object | **supported**
- H: Disk orientation is near face-on | E: Moment 1 map velocity gradient and Keplerian mass | R: 1.3 km/s over 60 AU gives 0.1 Msun unless inclination ~5 deg | F: Disk plane close to plane of the sky | **partially**

## Reasoning

- Why this data: Lines chosen for good contrast between absorption and emission  
  > "These selected lines show a good contrast between the absorption and emission features as compared with the rest." (Observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Disk mass is only a lower limit with factor of five uncertainty  
  > "Please note that the level of uncertainty in the mass lower limit is a factor of five" (0.45 mm continuum emission)
- Caveat (inferred, ours): Inclination of 5 deg is assumed ad hoc
- Caveat (inferred, ours): Tx and Tc fixed, not fitted; parameter errors not given
- Caveat (inferred, ours): Mass from thin-dust formula conflicts with claimed optically thick dust
- Caveat (inferred, ours): Only a few lines modeled; no fit uncertainties

## Reproducibility

- Data public (paper): ALMA Science Verification data  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00007.SV." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and calibration script
- Missing: Imaging parameters beyond robust
- Missing: Model grid details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 5/5, Public SV data and simple analysis, but many processing details and model grid specifics missing.
- Rediscovery candidate: yes, Public SV data; numeric results (size, flux, Tb, model parameters) are checkable, though recipe is incomplete.

## Links

- Method: Pineda et al. 2012 (cite: Pin2012) (Two-layer infall model used)
- Companion: Loinard et al. 2012 (cite: Lau2012) (ALMA SV outflow study of source B)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 37,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
