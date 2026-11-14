# Constraining the radial drift of millimeter-sized grains in the protoplanetary disks in Lupus

`2020A&A...638A..38T` | Astronomy and Astrophysics 2020 | first author: Trapman, L. | arXiv: 2004.07257 | DOI: 10.1051/0004-6361/201834537

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Can dust-based models without radial dust evolution reproduce the observed 12CO outer radius and gas-dust size difference in Lupus disks, or is radial drift and grain growth required?  
  > "determine whether radial dust evolution is required to match the observed gas–dust size difference." (abstract)
- Target **Ten Lupus disks (Sz 133, Sz 98, MY Lup, Sz 71, J16000236-4222115, Sz 129, Sz 68, Sz 100, Sz 65, Sz 84)**: coordinates Centroids in appendix mask table (e.g. Sz 133 16:03:29.37 -41:40:02.14)  
  > "Our final sample consists of ten disks (in order of decreasing dust mass): Sz 133, Sz 98, MY Lup, Sz 71, J16000236-4222115, Sz 129, Sz 68, Sz 100, Sz 65 and Sz 84." (2.2 Sample selection); z/distance 136-164 pc (Table 1; Gaia DR2 distances)  
  > "Our final sample consists of ten disks (in order of decreasing dust mass): Sz 133, Sz 98, MY Lup, Sz 71, J16000236-4222115, Sz 129, Sz 68, Sz 100, Sz 65 and Sz 84." (2.2 Sample selection); distance from Gaia DR2 (rescaled stellar parameters)  
  > "Our final sample consists of ten disks (in order of decreasing dust mass): Sz 133, Sz 98, MY Lup, Sz 71, J16000236-4222115, Sz 129, Sz 68, Sz 100, Sz 65 and Sz 84." (2.2 Sample selection)

## Data provenance

- ALMA projects: 2013.1.00220.S, 2015.1.00222.S, 2016.1.01239.S, 2013.1.00226.S
- bands: Band 7 (890 um) and Band 6 (1.33 mm)  
  > "The bandwidth-weighted mean continuum frequency of these observations was 225.66 GHz (1.33 mm)." (2.1 Observations)
- frequencies and spectral setup: Band 6: 12CO, 13CO, C18O 2-1 windows, 0.24 MHz channels, 0.3 km/s; Band 7: 13CO and C18O 3-2, 0.122 MHz channels, 0.11 km/s  
  > "Each spectral window has a bandwidth of 0.12 GHz, a channel width of 0.24 MHz, and velocity resolution of 0.3 km s$^{-1}$." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Band 7: 21.4-785.5 m; Band 6: 15-2483 m  
  > "The Band 6 observations were taken with a more extended configuration, covering baselines between 15 and 2483 m." (2.1 Observations)
- angular resolution: Band 7 continuum beam 0.34'' x 0.28''; Band 6 0.25'' x 0.24''  
  > "the average beam size for the continuum is $0.25\ensuremath{''} \times 0.24\ensuremath{''}$" (2.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: ~1 minute per source  
  > "taking $\sim1$ minute snapshots of each disk at moderately high resolution" (Introduction)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.51 GHz)
- Line: 13CO J=3-2 (330.6 GHz)
- Other facility **VLT/X-shooter**: Stellar parameters (luminosity, Teff, accretion luminosity)  
  > "used VLT X-Shooter spectra to derive stellar properties for all our sources." (3.2.4 Stellar spectrum)
- External data: Dust surface density profiles (Mdust, Rc, gamma, PA, i) from 890 um visibility fits  
  > "we use the surface density profiles from (cite: Tazzari2017)." (3.2 The physical model) [from (cite: Tazzari2017)]
- External data: Observed gas and dust outer radii (R90) for Lupus disks  
  > "the gas outer radius defined as the radius enclosing 90% of the $^{12}$CO flux (cite: ansdell2018)" (2.2 Sample selection) [from (cite: ansdell2018)]
- External data: Stellar luminosity, Teff, mass and accretion luminosity  
  > "Using their stellar luminosity and effective temperature, re-scaled to account for the new Gaia DR2 distances" (3.2.4 Stellar spectrum) [from (cite: alcala2014; alcala2017)]
- Simulation/model as data: DALI thermochemical models per source with CO isotopolog network, ray-traced to 12CO 2-1 cubes and 1.3 mm continuum maps  
  > "We use the thermochemical code `DALI` (cite: Bruderer2012; Bruderer2013) to create synthetic dust continuum and CO line emission maps." (3 Methods)

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

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Keplerian mask applied to line emission before moment-zero  
  > "A Keplerian masking technique is applied to the line emission to increase the S/N of the CO emission in the outer parts of the disk" (3.3 Measuring model outer radii)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Model cubes and maps convolved with Band 6 beam instead of full CLEAN synthetic observations  
  > "are convolved with the beam of the Band 6 observations" (3.3 Measuring model outer radii)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observational setup and data reduction  
  > "Further details on the observational setup and data reduction can be found in (cite: ansdell2016)." (2.1 Observations) [from (cite: ansdell2016); (cite: ansdell2018)]
- Outer radius defined as 90% flux, curve of growth measurement  
  > "We follow the same approach as (cite: ansdell2018) to measure the gas and dust outer radii from our models." (3.3 Measuring model outer radii) [from (cite: ansdell2018)]
- Chemical network with CO isotope-selective processes  
  > "We use the CO isotopolog chemical network from (cite: Miotello2014)" (3.1.1 Chemical network) [from (cite: Miotello2014)]
- R_CO/R_mm >= 4 criterion for dust evolution  
  > "A gas–dust size difference $\ensuremath{\mathrm{R_{\rm CO}}/\mathrm{R_{\rm mm}}}\geq 4$ is a clear sign for radial drift." (Introduction) [from (cite: Trapman2019)]

### Not stated but needed to reproduce (our reading)

- Exact DALI grid resolution, cosmic-ray/X-ray settings and gas-phase C/O abundance reduction factors beyond filenames
- Archive products and the specific Keplerian mask code
- Fitted a and b values of the Rmm,mdl vs Rmm,obs line
- Flux calibration uncertainty and CASA version for observations
- Observed 12CO R_CO, R_mm values and uncertainties are only in figures
- Model parameters for the 12CO cubes such as velocity resolution and ray-tracing setup
- Observed 13CO 3-2 fluxes used for CO calibration

## Analysis recipe

1. **Build source-specific DALI disk models**: Tapered power-law surface density from Tazzari et al. 2017 with Gaussian vertical structure, settled large grains, stellar spectrum plus accretion UV  
  > "By using this surface density for the gas in our model, the gas and millimetre-sized grains follow the same surface density profile." (3.2 The physical model)
   - software: DALI
   - parameter: (h_c, psi) = (0.1, 0.1); f_large = 0.99; chi = 0.2  
  > "we set $f_{\rm large} = 0.99$ and $\chi =0.2$" (3.2.3 Dust properties)
   - assumption: No radial dust evolution; gas and mm dust share same surface density  
  > "Our null hypothesis is thus that no radial-dependent dust evolution has occurred." (3.2 The physical model)
   - fitting: _not stated_
   - validation: Models compared to observed 890 um radial profiles and sizes; agree within 15% except Sz 98  
  > "The models and observations agree to within 15 % except for Sz 98 ($\sim 29\%$)." (3.3 Measuring model outer radii)
2. **Calibrate total CO content**: Lower C and O abundances (or gas-to-dust ratio) until 13CO 3-2 flux matches observations; only CO-underabundant models shown  
  > "we run a CO underabundant model for each source, where we lower the C and O abundances until the $^{13}$CO 3 - 2 line flux matches the observations." (3.2.2 Total CO content)
   - software: DALI
   - fitting: _not stated_
   - validation: Gas-depleted and CO-underabundant approaches yield near identical results  
  > "Our tests show that both approaches yield near identical results." (3.2.2 Total CO content)
3. **Measure model outer radii with noise**: Convolve with beam, add observed noise patches, apply Keplerian mask, make moment-zero map, curve of growth for 90% flux in elliptical apertures; ~1000 noise realisations  
  > "This process is repeated for approximately $1000$ noise realisation" (4.1 Observed versus modeled disk sizes)
   - software: DALI
   - parameter: Keplerian mask parameters M*, PA, i, centroid from literature; Vsys and DeltaV_int tuned to maximize S/N  
  > "were obtained by varying them to maximize the total S/N in the moment-zero map." (Appendix: Keplerian mask parameters)
   - fitting: _not stated_
   - validation: Tests show full synthetic CLEAN observations give approximately the same radii  
  > "However, tests show that both methods yield approximately the same measured gas and dust outer radii." (3.3 Measuring model outer radii)
4. **Compare model vs observed R_CO/R_mm**: Fit straight line Rmm,mdl = a*Rmm,obs + b and use it to scale Rmm,mdl; compare ratios with uncertainties from 16th/84th quantiles of noisy R_CO,mdl  
  > "We fit the offset with a straight line ($\ensuremath{\mathrm{R_{\rm mm,\ mdl}}}= a\times\ensuremath{\mathrm{R_{\rm mm,\ obs}}}+b$" (4.2 Gas–dust size difference)
   - fitting: _not stated_
   - validation: _not stated_
5. **Analyse low S/N disks**: _not stated_
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **DALI** : Thermochemical modeling and ray-tracing of CO and continuum  
  > "we use the thermochemical code Dust And LInes (`DALI`; (cite: Bruderer2012; Bruderer2013))." (3.1 DALI)
- **Matplotlib** : Figures  
  > "All figures were generated with the `PYTHON`-based package `MATPLOTLIB`" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks with R_CO,obs/R_mm,obs > model ratio | 5 of 10 | not stated | disks | 4 | For five of the ten disks in our sample (50%) we find |
| Mean observed R_CO/R_mm of sample | 2.06 | 0.37 (sample standard deviation) | dimensionless | 4 | $\langle \ensuremath{\mathrm{R_{\rm CO,\ obs}}/\mathrm{R_{\rm mm,\ obs}}}\rangle_{\rm obs} = 2.06 \pm 0.37$ |
| Disks with 12CO S/N=3 beyond 4 x R_mm | 6 | not stated | disks | 5 | we identify six disks where the S/N = 3 contour of their $^{12}$CO emission reaches beyond $4\times\ensuremath{\mathrm{R_{\rm mm}}}$ |
| V1192 Sco apparent R_CO/R_mm | 15-30 | not stated | dimensionless | 5 | V1192 Sco would seemingly have a gas–dust size difference of $\ensuremath{\mathrm{R_{\rm CO,\ obs}}/\mathrm{R_{\rm mm,\ obs}}}~15-30$ |

## Qualitative findings

- Disks with small gas-dust size differences in the bright sample may be explained by optical depth alone, but faint compact disks show large differences needing dust evolution  
  > "most of the disks in our sample, which represent the bright end of the Lupus disk population, are consistent with radial drift and grain growth." (Conclusions)

## Claim tuples

- H: Optical depth alone explains the observed gas-dust size difference in Lupus disks | E: DALI models without dust evolution compared to observed ratios per source | R: 5 of 10 disks have observed ratio above model; other 5 within noise uncertainty | F: Half need dust evolution plus optical depth; others consistent with optical depth only | **partially**
- H: Faint low-S/N disks also show radial drift | E: Used 12CO S/N=3 contour vs 4 x R_mm | R: Six disks exceed 4 x R_mm | F: Radial drift likely common in faint disks too | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Need quantitative estimate of optical depth contribution to separate it from dust evolution  
  > "quantitative estimates of the effect of line optical depth are required." (abstract)
- Alternative: Gas-depleted models (low gas-to-dust ratio) tested but gave near identical results to CO underabundance  
  > "We run a gas depleted disk model, where $\Delta_{\rm gd}$ is lowered until the model reproduces the observed $^{13}$CO 3 - 2 line flux." (3.2.2 Total CO content)
- How they decided it was enough: _not stated_
- Limitation (authors): Observations lack sensitivity; peak S/N 6-12 is below the S/N >= 10 needed for 20% R_CO accuracy; deeper surveys required  
  > "the peak S/N in our sample varies from $\sim6$ (Sz 100) to $\sim12$ (Sz 133)." (4.2)
- Limitation (authors): Models overpredict 1.3 mm sizes for several disks  
  > "our models overproduce the extent of the 1.3 millimeter continuum emission despite reproducing the extent of the continuum emission at $890\,\mu$m." (4.1)
- Caveat (inferred, ours): Fixed flaring, settling and stellar luminosity for all disks
- Caveat (inferred, ours): Sample biased to massive disks
- Caveat (inferred, ours): Proxy S/N=3 contour for R_CO is crude
- Caveat (inferred, ours): Convolving models instead of full visibility-domain imaging

## Reproducibility

- Data public (paper): ALMA project IDs given  
  > "id: ADS/JAO.ALMA#2013.1.00220.S, Band 7" (2.1 Observations)
- Products in archive: _not stated_
- Missing: DALI setup details
- Missing: Keplerian mask code
- Missing: Observed radii values in table form
- Missing: Fitted offset coefficients
- Data volume (inferred): ~50-100 GB of archival raw data for 4 projects; paper-level reproduction needs mostly the published products
- Score (inferred): 3/5, Public data and well-described method, but heavy dependence on inherited products and unreleased DALI models.
- Rediscovery candidate: no, Requires DALI thermochemical modelling and inherited literature products; results largely in figures.

## Links

- Method: (cite: Bruderer2012; Bruderer2013) (DALI code)
- Method: (cite: Trapman2019) (R_CO/R_mm >= 4 criterion and modelling)
- Method: (cite: Miotello2014) (CO isotopolog chemical network)
- Companion: (cite: ansdell2018) (Lupus survey Band 6 data and observed gas and dust radii)
- Companion: (cite: Tazzari2017) (Dust surface densities)
- Related: ALMA Lupus disk survey
- Related: Lupus Completion Survey

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 4,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 38,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
