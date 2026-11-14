# Masses and Densities of Dwarf Planet Satellites Measured with ALMA

`2023PSJ.....4..193B` | The Planetary Science Journal 2023 | first author: Brown, Michael E. | arXiv: 2307.04848 | DOI: 10.3847/PSJ/ace52a

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: solar_system
- Question: Can ALMA absolute astrometry detect the barycentric wobble of Orcus and Eris from their satellites Vanth and Dysnomia, giving satellite-primary mass ratios and densities?  
  > "We have used the Atacama Large Millimeter Array (ALMA) to measure precise absolute astrometric positions and detect the astrometric wobble of dwarf planet Orcus and its satellite Vanth over a complete orbit." (abstract)
- Target **Orcus-Vanth**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Eris-Dysnomia**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.00929.S, 2015.1.00810.S, 2016.1.00830.S
- bands: 2018 observation: Band 6 (~233 GHz)  
  > "We obtained a single epoch in Band 6 (center frequency $\sim$233 GHz)" (The size and density of Dysnomia)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 2018: C43-6  
  > "in configuration C43-6 (resulting resolution $0.15\times0.12$ arcsec)" (The size and density of Dysnomia)
- baselines: _not stated_
- angular resolution: 0.15x0.12 arcsec (2018); 2016 Orcus beams from ~98x90 to 197x163 mas  
  > "98 X 90 @ -56$^\circ$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 78 minutes (2018 epoch)  
  > "with an on-source integration time of 78 minutes" (The size and density of Dysnomia)
- observing dates: Orcus-Vanth 4 times Oct/Nov 2016; Eris-Dysnomia 3 times Nov/Dec 2015; re-observation 11 Oct 2018  
  > "The Orcus-Vanth system was observed 4 times in Oct/Nov 2016. The Eris-Dysnomia system was observed 3 times in Nov/Dec 2015." (Observations and Data Reduction); "we re-observed the Eris-Dysnomia system with ALMA on 11 October 2018" (The size and density of Dysnomia)
- pi or archival as stated: _not stated_
- Other facility **HST**: Vanth orbital phase measurement from BB18  
  > "allow for the uncertainty in the decade-old orbital phase measurement from the Hubble Space Telescope (HST)" (Analysis)
- External data: Eris disk diameter 1163 km; Eris density 2.4 g cm-3 context  
  > "a slightly limb-darkened disk, with diameter 1163 km (cite: 2011_Sicardy)" (Observations and Data Reduction) [from (cite: 2011_Sicardy)]
- External data: Eris-Dysnomia system mass 1.65e22 kg  
  > "for a system mass of 1.65$\times10^{22}$ kg (cite: 2021Icar..35514130H)" (Eris-Dysnomia) [from (cite: 2021Icar..35514130H)]
- External data: Orcus, Vanth diameters and Vanth orbit from BB18  
  > "ALMA observations have measured diameters of 910$^{+50}_{-40}$ and $475\pm75$ km for Orcus and Vanth (BB18)" (Introduction) [from (cite: 2018_Brown)]
- External data: Calibrator/check source positions from ICRF and RFC  
  > "The positions of these sources are either taken from the International Celestial Reference Frame (ICRF), or the Radio Fundamental Catalog (RFC)" (Observations and Data Reduction) [from (cite: 2009_Ma; 2019_Petrov)]

## Processing

### Calibration

- pipeline or manual: Reduced identically to BB18  
  > "We reduced the data in an identical manner to that described in BB18" (The size and density of Dysnomia)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 0  
  > "with a robust weighting parameter of 0" (Table 1)
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
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation description and flux density method  
  > "A complete description of the observations, including the method for obtaining final flux densities, is contained in BB18." (Observations and Data Reduction) [from BB18 (cite: 2018_Brown)]
- 2018 data reduction and thermal model  
  > "We add this Band 6 flux density of Dysnomia (and the simultaneously measured flux density of Eris) to our thermal model from BB18" (The size and density of Dysnomia) [from BB18 (cite: 2018_Brown)]
- Dysnomia ephemeris  
  > "We use the Dysnomia ephemeris from BB18, which has uncertainties of only 2 mas at the epoch of observation." (Eris-Dysnomia) [from BB18 (cite: 2018_Brown)]

### Not stated but needed to reproduce (our reading)

- Software used for visibility fitting and imaging (CASA version etc.)
- MCMC priors, number of walkers, burn-in length
- Image cell size and sizes, deconvolution settings
- Limb-darkening coefficient for Eris disk
- Vanth orbit elements from BB18
- Calibrator flux values and ALMA flux scale uncertainty

## Analysis recipe

1. **Fit source positions in visibilities**: Direct visibility fits: two point sources for Orcus/Vanth, limb-darkened disk for Eris; initial positions from image Gaussian fits  
  > "In the case of Orcus and Vanth, we use a model of two point sources, with initial position estimates given by Gaussian fits to the images." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate astrometric errors**: RSS of formal fit error, systematic fit error (visibility vs Gaussian image positions), and celestial-frame error from check-source offsets  
  > "We then take the total error in either direction (right ascension or declination) as the root sum squared (RSS) of those three values." (Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit Orcus-Vanth barycentre motion**: 6-parameter likelihood model: phase offset, mass ratio, 2D ephemeris offset, 2D ALMA-optical center-of-light offset  
  > "we fit the deviations of Orcus and Vanth from the expected system ephemeris position to a 6-parameter likelihood model" (Analysis)
   - software: emcee
   - parameter: 100000 samples after burn-in; median and 15.9/84.1% intervals  
  > "After an initial burn-in, we collect 100000 samples of the Markhov chain (MCMC) for analysis." (Analysis)
   - fitting: MCMC with emcee; priors not stated  
  > "We evaluate this 6-parameter model using the Markhov Chain Monte Carlo method implemented in *emcee*" (Analysis)
   - validation: _not stated_
4. **Fit Eris barycentre motion**: 3-parameter MCMC (barycentre offset plus 2D ephemeris offset) using Eris positions only  
  > "Our model thus only has 3 parameters, the barycenter offset and the two-dimensional ephemeris offset." (Eris-Dysnomia)
   - software: emcee
   - fitting: MCMC; reported as 1 sigma upper limit  
  > "we chose to instead report the derived mass ratio as a 1$\sigma$ upper limit of 0.0084 also corresponding to a 3$\sigma$ upper limit of 0.015" (Analysis, Eris-Dysnomia)
   - validation: reduced chi^2 of 1.8  
  > "with a reduced $\chi^2$ value of 1.8" (Eris-Dysnomia)
5. **Detect Dysnomia and update size**: Two-source visibility fit of 2018 Band 6 data; add flux to BB18 thermal model  
  > "We fit visibilities to a two-source model and find flux densities of $390\pm7 \mu$Jy for Eris and $45\pm7 \mu$Jy for Dysnomia." (The size and density of Dysnomia)
   - fitting: _not stated_
   - validation: Fitted positions insensitive to initial model positions  
  > "the final fitted positions for Eris and Dysnomia are insensitive to their positions in the initial model provided to the fit" (The size and density of Dysnomia)
6. **Derive masses and densities**: Mass ratio times system mass; density from diameters  
  > "For diameters of Orcus and Vanth of 910$^{+50}_{-40}$ and 475$\pm$75km and a system mass of $6.32\times10^{20}$ kg" (Orcus-Vanth)
   - assumption: System mass 6.32e20 kg (Orcus-Vanth); 1.65e22 kg (Eris)  
  > "for a system mass of 1.65$\times10^{22}$ kg (cite: 2021Icar..35514130H) the 1 $\sigma$ upper limit to the mass of Dysnomia is $1.4\times 10^{20}$ kg." (Analysis, Eris-Dysnomia)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC fitting of barycentre models  
  > "using the Markhov Chain Monte Carlo method implemented in *emcee*" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vanth-Orcus mass ratio | 0.16 | ±0.02 | dimensionless | 3 | we find a Vanth-Orcus mass ratio of 0.16$\pm$0.02 |
| Vanth mass | 8.7e19 | ±0.8e19 | kg | 6 | $8.7\pm0.8\times 10^{19}$ |
| Vanth density | 1.5 | +1.0/-0.5 | g cm^-3 | 6 | $1.4\pm0.2$ and $1.5^{+1.0}_{-0.5}$ g cm$^{-3}$, respectively |
| Dysnomia-Eris mass ratio | 0.0050 | ±0.0035 | dimensionless | 4 | corresponding to a mass ratio of 0.0050$\pm$.0035 |
| Dysnomia flux density (Band 6) | 45 | ±7 | μJy | 5 | $45\pm7 \mu$Jy for Dysnomia |
| Dysnomia diameter | 615 | +60/-50 | km | 5 | derive a new size for Dysnomia of 615$^{+60}_{-50}$km, with an albedo of 0.05$\pm$0.01 |
| Dysnomia density | 0.7 | ±0.5 | g cm^-3 | 6 | the density of Dysnomia is $0.7\pm0.5$ g cm$^{-3}$ |

## Qualitative findings

- Orcus-Vanth likely reached double synchronous state; Vanth is a largely intact impactor  
  > "consistent with the hypothesis that Vanth is a largely-intact impactor from a giant collision in the system" (abstract)

## Claim tuples

- H: Does Vanth have a high mass ratio like a Pluto-Charon analogue? | E: Astrometric wobble fit of Orcus/Vanth over 4 epochs | R: Mass ratio 0.16±0.02, 10σ barycentre detection | F: Highest mass ratio of any known planet/dwarf planet; consistent with intact giant impactor | **supported**
- H: Is Dysnomia dense like Eris? | E: Eris wobble limit plus 2018 Band 6 detection | R: Mass ratio <0.0085, density 0.7±0.5 (<1.2) | F: Dysnomia is significantly less dense than Eris | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Eris 1.5σ barycentre motion not claimed as detection; reported as upper limit  
  > "While this barycentric motion may represent a true detection, we chose to instead report the derived mass ratio as a 1$\sigma$ upper limit of 0.0084" (Eris-Dysnomia)
- How they decided it was enough: _not stated_
- Limitation (authors): Two Orcus epochs have much larger errors due to poor conditions and compact configuration  
  > "The observation on October 13 was impacted by poor observing conditions; that on November 7 was taken when antennas had been moved into a more compact configuration." (Observations and Data Reduction)
- Caveat (inferred, ours): Eris result is only 1.5σ, upper limit choice is subjective
- Caveat (inferred, ours): Density depends on large diameter uncertainties from thermal modelling
- Caveat (inferred, ours): Only four Orcus epochs, two with large errors
- Caveat (inferred, ours): Mismatch: abstract upper limit 0.0085 vs text 0.0084

## Reproducibility

- Data public (paper): ALMA data cited by project code; public status not stated  
  > "This paper makes use of ALMA data: ADS/JAO.ALMA#2018.1.00929.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: BB18 reduction details
- Missing: MCMC priors
- Missing: Software versions
- Missing: Vanth orbit elements from BB18
- Data volume (inferred): ~50-200 GB raw for 8 ALMA execution blocks
- Score (inferred): 5/5, Methods are clear in outline and data are archival, but software, priors and calibration are delegated to BB18 or not stated.
- Rediscovery candidate: no, Recipe depends heavily on BB18 and lacks software and prior details.

## Links

- Method: (cite: 2019JOSS....4.1864F) (emcee sampler)
- Companion: BB18 (cite: 2018_Brown) (Original ALMA observations, reduction and thermal model)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 33,
  "rate": 0.423
 },
 "evidence_ok": true
}
```
