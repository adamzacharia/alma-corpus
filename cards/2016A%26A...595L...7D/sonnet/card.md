# ALMA reveals optically thin, highly excited CO gas in the jet-driven winds of the galaxy IC 5063

`2016A&A...595L...7D` | Astronomy and Astrophysics 2016 | first author: Dasyra, K. M. | arXiv: 1609.03421 | DOI: 10.1051/0004-6361/201629689

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Is molecular gas accelerated or impacted by the jet in IC5063 more highly excited and less optically thick than the gas in the disk, and what does this imply for the wind mass?  
  > "we provide observational evidence that the molecular gas accelerated or impacted by a jet is more highly excited and less optically thick than the rest of the ISM." (Introduction)
- Target **IC5063**: coordinates nucleus at 20:52:02.37 -57:04:07.6  
  > "(at 20:52:02.37 -57:04:07.6)" (Results: gas excitation differences in the wind and in the ambient medium); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00420.S, 2012.1.00435.S
- bands: Band 8 (CO 4-3); Band 6 (CO 2-1)  
  > "New, band 8 data of IC5063 were taken with ALMA on May 18 2016" (The ALMA data); "Thirty one antennas observed IC5063 in band 6 for 30 mins on-source." (The ALMA data)
- frequencies and spectral setup: Band 8: three 1.875 GHz spectral windows, two overlapping covering ±1000 km/s around CO(4-3), third ±300 km/s for duplication; Band 6: four 1.875 GHz windows, one covering ±1000 km/s around CO(2-1)  
  > "Three 1.875 GHz-bandwidth spectral windows were employed." (The ALMA data); "Four 1.875 GHz-bandwidth spectral windows were employed, with one of them covering the $\pm$1000 km s$^{-1}$ range around $\rm CO(2$-$1)$." (The ALMA data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.4'' x 0.4'' (CO 4-3); 0.56'' x 0.53'' (CO 2-1)  
  > "The synthesized beam size was 0.4$''$ $\times$0.4$''$ ." (The ALMA data)
- max recoverable scale: _not stated_
- sensitivity: Noise at common resolution: 0.26 mJy/beam (CO 2-1), 3.4 mJy/beam (CO 4-3)  
  > "the noise is 0.26 mJy/beam for $\rm CO(2$-$1)$, and 3.4 mJy/beam for $\rm CO(4$-$3)$" (The ALMA data)
- time on source: 39 min (Band 8, 42 antennas); 30 min (Band 6, 31 antennas)  
  > "Forty two antennas observed the galaxy for 39 minutes on-source." (The ALMA data)
- observing dates: Band 8 on May 18 2016  
  > "New, band 8 data of IC5063 were taken with ALMA on May 18 2016" (The ALMA data)
- pi or archival as stated: CO(4-3) program PI Combes; CO(2-1) from earlier program (Morganti et al. 2015)  
  > "for the program 2015.1.00420.S (PI Combes)" (The ALMA data)
- Line: CO 4-3 (not stated)
- Line: CO 2-1 (not stated)
- Other facility **VLT NIR**: H2 and [Fe II] data identifying wind starting points  
  > "Using ultra-deep ESO VLT near infrared (NIR) data, we identified at least four discrete starting points of ionized and warm molecular gas winds near the jet trail" (Introduction)
- Other facility **APEX**: single-dish CO(2-1) flux for comparison  
  > "The $\rm CO(2$-$1)$ flux is 30% lower than that measured from single-dish, APEX data." (Results: gas excitation differences in the wind and in the ambient medium)
- External data: CO(2-1) ALMA data (project 2012.1.00435.S) and earlier wind mass 1.9e7 Msun  
  > "we also used $\rm CO(2$-$1)$ data from the program 2012.1.00435.S (cite: morganti15)" (The ALMA data) [from (cite: morganti15)]
- External data: Eq. 3 and alpha_CO=4.6 for optically thick gas  
  > "we use Eq. 3 of (cite: solomon97) with $\alpha_{CO}$=4.6" (Discussion: gas mass in the wind) [from (cite: solomon97)]
- External data: optically thin alpha_CO formula  
  > "for a Galactic CO/ $\rm{H_ 2}$ abundance (cite: bolatto13)" (Discussion: gas mass in the wind) [from (cite: bolatto13)]

## Processing

### Calibration

- pipeline or manual: Band 8 calibration script executed as delivered by ESO  
  > "The calibration script was executed as delivered by ESO." (The ALMA data)
- casa version: CASA 4.6.0 (Band 8 reduction, Band 6 imaging); CASA 4.2.2 (Band 6 flux calibration)  
  > "The flux calibration was performed in CASA 4.2.2." (The ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 8: Pallas (flux), J1924-2914 (bandpass), J2056-4714 (phase); Band 6: Neptune flux, J2056-4714 bandpass/phase  
  > "Pallas, J1924-2914, and J2056-4714 were respectively used as flux, bandpass, and phase calibrators." (The ALMA data)
- flux scale uncertainty: better than 5% (Band 8)  
  > "The flux calibration accuracy was better than 5%" (The ALMA data)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5  
  > "All images were reconstructed using Briggs robust=0.5 weighting, and primary-beam corrected." (The ALMA data)
- uv taper: _not stated_
- cell size: 0.06'' (Band 8); 0.1'' (Band 6, later regridded to 0.06'')  
  > "we chose a 25 km s$^{-1}$ spectral bin and a 0.06$''$ pixel scale" (The ALMA data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: done in CASA 4.6.0; method details not given  
  > "Imaging was carried out in CASA 4.6.0 (because of continuum subtraction improvements)." (The ALMA data)
- line free channels: _not stated_
- primary beam correction: applied  
  > "All images were reconstructed using Briggs robust=0.5 weighting, and primary-beam corrected." (The ALMA data)
- array combination: _not stated_
- smoothing: CO(4-3) cube Gaussian-convolved to CO(2-1) beam; CO(2-1) regridded to CO(4-3) pixel scale  
  > "we smoothed by Gaussian convolution the $\rm CO(4$-$3)$ cube to the resolution of the $\rm CO(2$-$1)$ beam" (The ALMA data)
- final beam: 0.56''x0.53'' common resolution  
  > "The synthesized beam was 0.56$''$ $\times$0.53$''$ ." (The ALMA data)
- final rms: _not stated_

### Inherited from earlier work

- CO(2-1) data and S-shaped feature, earlier wind mass assumptions  
  > "we also used $\rm CO(2$-$1)$ data from the program 2012.1.00435.S (cite: morganti15)" (The ALMA data) [from (cite: morganti15)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction order/method
- Cleaning threshold, masks, number of iterations
- Distance to IC5063 used for masses
- Rest frequencies and exact velocity zero point
- Self-calibration usage
- Details of the Gaussian disk-model fitting (initial guesses, error treatment)
- Flux scale correction for Band 6 and how Band 6 imaging reconciled with its older calibration
- Region definitions for the beam-radius integrations and conversion of Jy km/s to K km/s pc^2

## Analysis recipe

1. **Image the cubes and match resolution**: Image both bands at 25 km/s bins, robust 0.5, primary-beam correct; regrid CO(2-1) and smooth CO(4-3) to CO(2-1) beam  
  > "To compare them, we re-gridded the $\rm CO(2$-$1)$ cube to the pixel scale of the $\rm CO(4$-$3)$ cube" (The ALMA data)
   - software: CASA
   - parameter: robust=0.5, 25 km/s bin  
  > "All images were reconstructed using Briggs robust=0.5 weighting, and primary-beam corrected." (The ALMA data)
   - fitting: _not stated_
   - validation: No important flux losses assumed given high uv coverage and small source area  
  > "No important flux losses were considered for them: the *uv* plane coverage was high" (The ALMA data)
2. **Separate disk and jet-affected gas**: Fit a single Gaussian per pixel to model disk emission and subtract it from the cube; integrate the residuals  
  > "we modeled the disk emission and subtracted it from the observed spectrum in each pixel." (Results: gas excitation differences in the wind and in the ambient medium)
   - parameter: disk V within ±250 km/s; sigma < 50 km/s  
  > "The velocity dispersion $\sigma$ was constrained to values below 50 km s$^{-1}$" (Results: gas excitation differences in the wind and in the ambient medium)
   - fitting: Single Gaussian preferred over two-component Gaussian for lower errors  
  > "A Gaussian fitting algorithm was employed, prefered over a two-component Gaussian fitting algorithm for its lower errors." (Results: gas excitation differences in the wind and in the ambient medium)
   - validation: _not stated_
3. **Compute F43/F21 ratios and maps**: Integrated flux ratios for residual gas, disk, fast wind, and maps collapsed over -600<V<400 km/s  
  > "after collapsing the disk-subtracted cubes in the -600$<$V$<$400 km s$^{-1}$ range" (Results: gas excitation differences in the wind and in the ambient medium)
   - fitting: _not stated_
   - validation: Also checked ratio maps from cubes prior to disk subtraction  
  > "All the above-mentioned regions are also seen in $\rm F_{43}/F_{21}$ maps that we created from the cubes prior to the disk subtraction" (Results: gas excitation differences in the wind and in the ambient medium)
4. **Derive excitation temperature and wind mass**: Analytic LTE solutions for optically thick/thin F43/F21; mass from alpha_CO for thick (disk) and thin (wind) gas  
  > "we determined the gas mass in the wind and in the disk using the appropriate CO-luminosity-to- $\rm{H_ 2}$-mass conversion factor" (Discussion: gas mass in the wind)
   - assumption: LTE, Tex >> T_CMB, alpha_CO=4.6 for thick gas with F21/F10=4, Galactic CO/H2 abundance for thin gas  
  > "assuming that the molecular gas is in local thermodynamic equilibrium (LTE) and that its excitation temperature $T_{\rm ex}$ greatly exceeds that of the cosmic microwave background" (Discussion: gas mass in the wind)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.6.0 (also 4.2.2 for Band 6 flux calibration): data reduction and imaging  
  > "The data were reduced within the Common Astronomy Software Applications (CASA) environment, version 4.6.0." (The ALMA data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(4-3) flux | 118.0 | 5.0 | Jy km/s | 3 | The total flux detected in $\rm CO(4$-$3)$ is 118.0 $\pm$ 5.0  Jy km s$^{-1}$ |
| Total CO(2-1) flux | 70.2 | 4.7 | Jy km/s | 3 | whereas  that detected  in $\rm CO(2$-$1)$ is 70.2 $\pm$ 4.7 Jy km s$^{-1}$ |
| Residual CO(4-3) flux (jet-affected) | 59.7 | 9.2 | Jy km/s | 2 | 12.3($\pm$2.5) Jy km s$^{-1}$ for $\rm CO(2$-$1)$, and 59.7($\pm$9.2) Jy km s$^{-1}$ for $\rm CO(4$-$3)$ |
| F43/F21 jet-affected gas | 4.9 | 1.7 | dimensionless | 3 | The $\rm F_{43}/F_{21}$ ratio is 4.9($\pm$)1.7 for this gas, and 1.0($\pm$)0.4 for the rest of the gas in the disk. |
| F43/F21 fastest wind gas | 8.0 | 2.4 | dimensionless | 3 | $\rm F_{43}/F_{21}$ is 8.0($\pm$2.4). |
| Tex for optically thin gas with ratio 5, 8, 11 | 32, 56, 100 | not stated | K | 4 | we find that  $T_{\rm ex}$=32K, if all of the gas kinematically or excitationally affected by the jet (with $\rm F_{43}/F_{21}$=5) is optically thin. |
| Disk molecular mass (optically thick) | 4.0e8 | 0.5e8 | Msun | 4 | a mass of 4.0($\pm$0.5)$\times$10$^8$ $M_{\odot}$ is obtained for the disk |
| Wind mass (optically thin, ratio 5) | 1.7e6 | 0.3e6 | Msun | 4 | the wind mass is 1.7($\pm$0.3) $\times$10$^6$ $M_{\odot}$ |
| Wind mass (optically thin, ratio 8) | 2.4e6 | 0.5e6 | Msun | 4 | the wind mass is 2.4($\pm$0.5)$\times$10$^6$ $M_{\odot}$ |

## Qualitative findings

- Jet-impacted gas is partly optically thin and highly excited; CO(4-3) mainly detected along the jet; IR pumping unlikely  
  > "We found that $\rm CO(4$-$3)$ is mainly detected along the jet." (Summary)

## Claim tuples

- H: Jet-driven wind gas has higher CO excitation than disk gas | E: Compared CO(4-3)/CO(2-1) flux ratios in disk-subtracted and original cubes | R: Ratio ~5 for jet-affected gas vs ~1 for disk, up to 8-11 in regions | F: Wind gas is more highly excited and partly optically thin | **supported**
- H: Previous molecular wind mass was overestimated | E: LTE optically thin alpha_CO applied to CO(2-1) residual flux | R: Lower mass limit ~2e6 Msun vs 1.9e7 previously | F: Molecular wind masses can be overestimated | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Single Gaussian disk model chosen for lower errors than two-component fit  
  > "prefered over a two-component Gaussian fitting algorithm for its lower errors" (Results: gas excitation differences in the wind and in the ambient medium)
- Alternative: Infrared pumping rejected as unlikely  
  > "It is unlikely that this result reflects infrared (IR) pumping of the populations of quantum states with high rotational number J." (Discussion: gas mass in the wind)
- How they decided it was enough: _not stated_
- Limitation (authors): Simplified LTE analysis; true mass requires non-LTE SLED modelling with CO(1-0) and (3-2)  
  > "The actual molecular wind mass will be derived when all data, including new CO (1-0) and (3-2) observations, are analyzed assuming non-LTE conditions" (Discussion: gas mass in the wind)
- Caveat (inferred, ours): Disk-subtraction with a single Gaussian may leak disk flux into residuals and bias ratios
- Caveat (inferred, ours): Ratios >4 could also arise from calibration or flux-recovery differences between bands
- Caveat (inferred, ours): Wind mass assumes all gas optically thin and LTE; gives only a lower limit
- Caveat (inferred, ours): Uncertainty on the ratio of fluxes with different uv coverage not discussed

## Reproducibility

- Data public (paper): Programs identified by code; public status not explicitly stated  
  > "This paper makes use of the ALMA data 2015.1.00420.S and 2012.1.00435.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Cleaning parameters and masks
- Missing: Disk-fit implementation details
- Missing: Distance and conversion to luminosities
- Missing: Region definitions
- Data volume (inferred): ~50-100 GB raw for two datasets
- Score (inferred): 5/5, Data identified and processing outline given, but many imaging and fitting details missing.
- Rediscovery candidate: no, Recipe lacks key details (distance, fitting setup, masks) and data public status is not stated.

## Links

- Companion: (cite: morganti15) (Source of the CO(2-1) data and earlier wind mass)
- Companion: (cite: dasyra15) (NIR wind starting points)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 41,
  "rate": 0.603
 },
 "evidence_ok": true
}
```
