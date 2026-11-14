# ALMA Observations of Giant Molecular Clouds in M33. II. Triggered High-mass Star Formation by Multiple Gas Colliding Events at the NGC 604 Complex

`2020ApJ...903...94M` | The Astrophysical Journal 2020 | first author: Muraoka, Kazuyuki | arXiv: 2009.05804 | DOI: 10.3847/1538-4357/abb822

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What triggers high-mass star formation in the NGC 604 GMC: expansion of H II regions or cloud-cloud collisions/gas flows?  
  > "concluded that expansion of the H$\,$ii regions cannot explain the formation of such dense cores." (abstract)
- Target **NGC 604 GMC (M33)**: coordinates _not stated_; z/distance ~840 kpc  
  > "Its proximity ($\sim$840 kpc; (cite: freedman2001)) and favorable inclination (51$^{\circ}$; (cite: corbelli2000))" (Introduction); distance from Freedman et al. 2001 (cite: freedman2001)  
  > "Its proximity ($\sim$840 kpc; (cite: freedman2001)) and favorable inclination (51$^{\circ}$; (cite: corbelli2000))" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6 (211 – 275 GHz)  
  > "ALMA Cycle 6 observations toward NGC 604-GMC were carried out in Band 6 (211 – 275 GHz)" (2 Observations and Data Reduction)
- frequencies and spectral setup: 117.19 MHz bandwidth, 1920 channels for 12CO, 960 channels for 13CO and C18O  
  > "The bandwidths of the correlator settings were 117.19 MHz with 1920 channels for the $^{12}$CO line and 960 channels for $^{13}$CO and C$^{18}$O lines." (2 Observations and Data Reduction)
- continuum bandwidth: two spectral windows, aggregate 3750 MHz, 0.98 MHz channels  
  > "we used two spectral windows for the 1.3 mm continuum observations with an aggregate bandwidth of 3750 MHz with a channel width of 0.98 MHz." (2 Observations and Data Reduction)
- arrays: 12 m main array and ACA 7 m; no Total Power  
  > "Note that the ALMA program did not include the Total Power (TP) array observations." (2 Observations and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.44'' x 0.27'' (CO); 0.41'' x 0.25'' (continuum)  
  > "The beam size of CO data is 0.44$''$ $\times$ 0.27$''$" (2 Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: CO rms ~1.1 K at ~0.2 km/s; continuum 0.019 mJy/beam  
  > "the rms noise level is $\sim$1.1 K at a velocity resolution of $\sim$0.2 km s$^{-1}$." (2 Observations and Data Reduction)
- time on source: _not stated_
- observing dates: 2017 October to 2018 October  
  > "between 2017 October and 2018 October" (2 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **IRAM 30m**: single-dish 12CO data used for missing flux check and feathering  
  > "We thus combined the ALMA and the IRAM data using the `feathering` technique." (2 Observations and Data Reduction)
- Other facility **HST WFPC2**: Halpha image  
  > "the H$\alpha$ luminosity (red) obtained with the Wide Field and Planetary Camera 2 on the Hubble Space Telescope" (3.1)
- External data: IRAM 30m 12CO single-dish data and XCO = 4e20  
  > "We applied the $X_{\rm CO}$ factor, 4 $\times$10$^{20}$ cm$^{-2}$ (K km s$^{-1}$)$^{-1}$ (cite: druard2014)" (3.1) [from (cite: druard2014)]
- External data: HI velocity components  
  > "they found that the H$\,$i clouds in NGC 604 are composed of two velocity components separated by 20 km s$^{-1}$" (3.1) [from (cite: tachihara2018)]
- External data: Spitzer MIR source catalog  
  > "MMS-1, MMS-2, and MMS-3 correspond to Src 1, Src 4, and Src 2 in their catalog, respectively." (3.2) [from (cite: martinez2012)]

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

- task: tclean  
  > "We used the `tclean` task with `multi-scale` deconvolver (cite: kepley2020)" (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "The weighting scheme of `tclean` was $``$Briggs$"$ with a robust parameter of 0.5." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m+7m feathering; then ALMA combined with IRAM 30m by feathering  
  > "We combined the 12 m and 7 m array data with the `feathering` task." (2 Observations and Data Reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed data reduction processes  
  > "The detailed processes of data reduction are the same as (cite: tokuda2020)." (2 Observations and Data Reduction) [from (cite: tokuda2020)]
- 13CO abundance [H2]/[13CO]=1.4e6  
  > "(see the justification by (cite: tokuda2020))" (3.1) [from (cite: tokuda2020)]

### Not stated but needed to reproduce (our reading)

- Project code printed in the paper
- Multiscale scales, cell/image size, masking and cleaning thresholds
- Continuum-line-free channels and continuum subtraction
- Feathering parameters and IRAM scaling
- Pipeline/calibrators
- Line excitation temperature details and 13CO column calculation
- Method of PV cuts and filament mass measurement

## Analysis recipe

1. **Image and combine data**: tclean multiscale, Briggs 0.5; feather 12m+7m, then with IRAM 30m  
  > "We combined the 12 m and 7 m array data with the `feathering` task." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: missing flux compared to IRAM 30m: <~30% north, ~50% south  
  > "whereas the southern side has a $\sim$50% missing flux." (2 Observations and Data Reduction)
2. **Gas masses from CO**: 12CO mass with XCO and ratio 0.85; 13CO mass via LTE  
  > "The local thermodynamic equilibrium (LTE) approximation was applied to estimate the total mass from the $^{13}$CO observations" (3.1)
   - assumption: XCO 4e20; CO(2-1)/(1-0)=0.85; [H2]/[13CO]=1.4e6  
  > "a CO($J=2-1$)/CO($J=1-0$) intensity ratio of 0.85 toward H$\,$ii regions" (3.1)
   - fitting: _not stated_
   - validation: consistent with single-dish measurements  
  > "which is consistent with the single-dish measurements (cite: gratier2012)" (3.1)
3. **Continuum source properties and masses**: 2D elliptical Gaussian fits; virial mass 210 dV^2 R; dust mass from total flux  
  > "Source size (FWHM) derived from 2D elliptical gaussian fitting." (Table 1)
   - assumption: Tdust 22 K, gas-to-dust 300, kappa_1.3mm 1 cm2/g  
  > "assuming dust temperature of 22 K (cite: tabatabaei2014), a gas-to-dust ratio of 300 (cite: relano2018), and $\kappa_{\rm 1.3~mm}$ of 1 cm$^2$ g$^{-1}$" (Table 1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test H II expansion via PV diagrams**: 12CO PV diagrams perpendicular to expansion direction, compared with elliptical shape expected (Torii 2015)  
  > "we examine the velocity structures based on the $^{12}$CO($J=2-1$) position-velocity (PV) diagrams" (4.1)
   - fitting: _not stated_
   - validation: qualitative  
  > "(cite: torii2015) qualitatively described that PV diagrams in CO show an elliptical shape if the expanding motion of the H$\,$ii region compresses the surrounding molecular materials" (Discussion, Triggering mechanism of star formation)

## Software

- **CASA** 5.4.0: tclean imaging, feathering  
  > "CASA (v5.4.0; (cite: mcmullin2007))" (Software)
- **Astropy** : listed software  
  > "Astropy (cite: astropy2018)" (Software)
- **APLpy** 1.1.1: plotting  
  > "APLpy (v1.1.1; (cite: Robi12))" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO-traced gas mass | ~3e6 | not stated | Msun | 2 | is $\sim$3 $\times$10$^6$ $M_{\odot}$ |
| 13CO LTE mass | ~3e5 | not stated | Msun | 2 | The resultant $M_{\rm ^{13}CO}$ is calculated to be $\sim$3 $\times$10$^{5}$ $M_{\odot}$ |
| MMS-1 total mass | 4.5e4 | not stated | Msun | 3 | / MMS-1 / 01 34 33.42 / 30 46 48.59 / 2.9 $\times$ 1.9 / 0.37 / 1.2 / 6.0 / 1.8 $\times$10$^4$ / 1.8 $\times$10$^4$ / **4.5 $\times$10$^4$** / |
| MMS-2 total mass | 3.3e4 | not stated | Msun | 3 | / MMS-2 / **01 34 33.42** / **30 46 57.31** / 3.2 $\times$ 1.6 / 0.29 / 0.9 / 6.0 / 1.7 $\times$10$^4$ / 1.9 $\times$10$^4$ / **3.3 $\times$10$^4$** / |
| MMS-3 total mass | 1.9e4 | not stated | Msun | 3 | / MMS-3 / **01 34 33.63** / **30 46 51.38** / 3.2 $\times$ 2.2 / 0.12 / 0.5 / 5.7 / 1.8 $\times$10$^4$ / 1.3 $\times$10$^4$ / **1.9 $\times$10$^4$** / |

## Qualitative findings

- C18O detected at MMS-1 (1 K) and MMS-3 (0.6 K) but not MMS-2, interpreted as different evolutionary stages  
  > "we found no C$^{18}$O($J=2-1$) emission at MMS-2." (3.2)

## Claim tuples

- H: H II region expansion triggers dense clump formation | E: 12CO PV diagrams around the MMSs | R: nearly constant velocity field, only a small local ellipse near MMS-1 | F: H II expansion is not the trigger | **supported**
- H: Cloud-cloud collisions form the shells and hub filament | E: Comparison of morphology and velocities with collision models and HI flows | R: shells at MMS-2/3 and hub filament at MMS-1 consistent with collisions | F: multiple colliding events build NGC 604 | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Supernovae, H II expansion (globule squeezing, collect and collapse) rejected  
  > "whereas no supernova is found within the three molecular shells" (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Magnetic field properties in the molecular phase unknown  
  > "the actual magnetic field properties toward the molecular phase are still unknown" (4.2.3)
- Caveat (inferred, ours): Collision interpretation is qualitative and relies on morphology
- Caveat (inferred, ours): Mass uncertainties not given
- Caveat (inferred, ours): Single-dish combination only for 12CO

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Project code and imaging details
- Missing: PV cut definitions
- Missing: IRAM data scaling
- Data volume (inferred): tens of GB
- Score (inferred): 3/5, Imaging parameters are partly given but details are deferred to Tokuda 2020 and the analysis is largely qualitative.
- Rediscovery candidate: no, Recipe is incomplete and key conclusions are qualitative.

## Links

- Method: Tokuda et al. 2020 (cite: tokuda2020) (data reduction procedure)
- Companion: Tokuda et al. 2020 (cite: tokuda2020) (GMC-16 in M33)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2017.1.00461.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 35,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
