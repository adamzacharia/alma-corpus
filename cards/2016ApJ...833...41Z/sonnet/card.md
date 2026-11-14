# High-resolution Observations of Molecular Lines in Arp 220: Kinematics, Morphology, and Limits on the Applicability of the Ammonia Thermometer

`2016ApJ...833...41Z` | The Astrophysical Journal 2016 | first author: Zschaechner, Laura K. | arXiv: 1609.04824 | DOI: 10.3847/1538-4357/833/1/41

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: What are the kinematics, morphology and molecular content of the two nuclei of Arp 220 at 0.6" in the VLA K and Ka bands, and how well does the NH3 metastable thermometer work; is there an outflow when compared with ALMA spectra?  
  > "We provide constraints for the kinematics, morphology, and identify molecular species on scales resolving both nuclei (0.6" or 230 pc)." (abstract)
- Target **Arp 220**: coordinates pointing center 15h 34m 57.225s +23d 30m 11.57s  
  > "At a distance of 78 Mpc, Arp 220 is the nearest ULIRG, providing a unique opportunity to study these systems at high (380 pc arcsec$^{-1}$) resolution." (Introduction); z/distance 78 Mpc  
  > "At a distance of 78 Mpc, Arp 220 is the nearest ULIRG, providing a unique opportunity to study these systems at high (380 pc arcsec$^{-1}$) resolution." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00175.S
- bands: VLA K (18-26.5 GHz) and Ka (26.5-40 GHz); ALMA data only used for comparison  
  > "Observations were carried out using the VLA between March 2011 and June 2012 with the K-band (18-26.5 GHz) and Ka-band (26.5-40 GHz) receivers." (2 Observations and Data Reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.6" (cubes smoothed to circular beam)  
  > "All cubes used for analysis of line data are smoothed to a circular 0.6" beam." (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 3.6 h K band, 3.2 h Ka band (VLA)  
  > "On-Source Time K Band (hours) | 3.6" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: NH3 metastable (1,1)-(5,5), (9,9) (23.69477-24.53292, 27.47794 GHz)
- Line: OH 2Pi3/2 J=9/2 F=4-4; 5-5 (23.8176153, 23.8266211 GHz)
- Other facility **VLA**: Primary K and Ka band data  
  > "Observations were carried out using the VLA between March 2011 and June 2012" (2 Observations and Data Reduction)
- Other facility **ALMA**: HCN(4-3) and CS(7-6) spectra compared with VLA absorption  
  > "We compare the absorption spectra we observe with the VLA with HCN (4-3) and CS (7-6) spectra observed with ALMA by (cite: 2015ApJ...800...70S)." (4.3 An outflow demonstrated by a comparison with emission lines seen by ALMA)
- External data: ALMA HCN(4-3) and CS(7-6) spectra  
  > "HCN (4-3) and CS (7-6) spectra observed with ALMA by (cite: 2015ApJ...800...70S)" (4.3 An outflow demonstrated by a comparison with emission lines seen by ALMA) [from (cite: 2015ApJ...800...70S)]
- External data: Nuclear systemic velocities (5350 and 5410 km/s)  
  > "Assuming the LSR (radio) value of 5350 km s$^{-1}$ for the systemic velocity of the western nucleus (cite: 2009ApJ...700L.104S)" (4.3 An outflow demonstrated by a comparison with emission lines seen by ALMA) [from (cite: 2009ApJ...700L.104S)]
- External data: L_FIR = 1.4e12 Lsun  
  > "adopt L$_{FIR}$=1.4$\times$10$^{12}$ L$_{\odot}$ from (cite: 2003AJ....126.1607S)" (4.1.1) [from (cite: 2003AJ....126.1607S)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Two iterations of phase-only self-cal on continuum only; not applied to line data  
  > "we apply two iterations of phase-only self-calibration to the continuum alone" (2 Observations and Data Reduction)

### Imaging

- task: CASA CLEAN  
  > "Total intensity (Stokes I) image cubes and maps were created in CASA using the task `CLEAN`." (2 Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: Natural weighting  
  > "Natural weighting was used for all frequencies." (2 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Cubes convolved to a common beam during imaging  
  > "the spectral line cubes are convolved to the same beam size during imaging using `CLEAN`." (2 Observations and Data Reduction)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Boltzmann-diagram rotation temperature method  
  > "We use methods involving Boltzmann statistics such as those presented in (cite: 2005PASJ...57L..29T), (cite: 2011ApJ...742...95O), and (cite: 2013ApJ...772..105M) to gauge $T_{rot}$" (4.2.1 Method) [from (cite: 2005PASJ...57L..29T), (cite: 2011ApJ...742...95O), (cite: 2013ApJ...772..105M)]

### Not stated but needed to reproduce (our reading)

- Gaussian line-fitting procedure and software for tau, velocity, width
- Continuum model used to convert absorption to optical depth
- Self-cal solint and reference calibrators
- Cleaning thresholds, cell and image size
- How ALMA spectra were extracted and aligned (taken from published work)

## Analysis recipe

1. **Reduce VLA data and image cubes**: CASA standard spectral line reduction, CLEAN with natural weighting, common 0.6" beam  
  > "Data reduction was completed in Common Astronomy Software Applications (CASA, (cite: 2007ASPC..376..127M)) using standard spectral line methods." (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotation temperature from NH3 Boltzmann diagram**: Compute N_u/T_ex from tau and FWHM, fit line to log weighted column density vs upper-level energy; T_rot = -log10(e)/m  
  > "In the end $T_{rot}=-log_{10}(e)/m$ where $m$ is the slope of the best fit line." (4.2.1 Method)
   - parameter: Fits including (1,1)-(5,5), and omitting (1,1) and (4,4); (9,9) omitted  
  > "In the first we include the (1,1) through (5,5) transitions. In the second, we omit the (1,1) and (4,4) transitions." (4.2.1 Method)
   - assumption: LTE (found not to hold)  
  > "An assumption for this method is LTE, which the two nuclei do not fulfill." (4.2.1 Method)
   - fitting: _not stated_
   - validation: Compared with non-metastable (3,1),(4,2) populations  
  > "we examine the (3,1) and (4,2) transitions for the Western nucleus." (4.2.1 Method)
3. **Compare VLA absorption with ALMA spectra for outflow**: Compare velocity of blue-shifted absorption to HCN(4-3) and CS(7-6) self-absorption  
  > "When the self-absorption in the ALMA data is compared to the absorption in the VLA data in the western nucleus, one can see that they are aligned with each other." (4.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and imaging  
  > "Data reduction was completed in Common Astronomy Software Applications (CASA" (2 Observations and Data Reduction)
- **RADEX** : NH3 (3,1)/(4,2) intensity ratio estimate  
  > "A RADEX (cite: 2007A&A...468..627V) calculation assuming T$_{k}$$\sim$150 K" (4.1.1)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NH3(4,2) peak optical depth, western nucleus | 0.07 | 0.002 | dimensionless | 1 | NH$_{3}$(4,2) / 21.70341 / 0.07$\pm$0.002 |
| L_H2O/L_FIR | ~1e-10 to 1e-9 | not stated | dimensionless | 0 | we find a value of 10$^{-10}$–10$^{-9}$ for L$_{H_{2}O}$/L$_{FIR}$ |
| Blue-shifted absorption extent, western nucleus | ~400 | not stated | km/s | 3 | this self-absorption could indicate a blue-shifted outflow extending to $\sim$400 km s$^{-1}$ in the western nucleus. |

## Qualitative findings

- Metastable NH3 thermometer breaks down in Arp 220; non-metastable transitions likely matter  
  > "There are indications that a substantial fraction of ammonia could be in the non-metastable transitions as opposed to only the metastable ones." (abstract)

## Claim tuples

- H: Can metastable NH3 give T_rot in Arp 220? | E: Boltzmann diagram of (1,1)-(5,5) absorption in both nuclei | R: Points not described by a single straight line | F: Standard thermometer breaks down; non-metastable states important | **supported**
- H: Is there a 22 GHz H2O maser in Arp 220? | E: Resolved spectra of the two nuclei near 21.84 GHz | R: Opposite-sign features in the two nuclei cancel when unresolved | F: Tentative H2O(6_15-5_23) detection | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: LVG analysis not pursued because basic analysis already fits poorly  
  > "We forgo further Large Velocity Gradient (LVG) and other analyses of these data" (4.2.1 Method)
- How they decided it was enough: _not stated_
- Limitation (authors): Interferometric data do not recover full flux  
  > "the single dish data from (cite: 2013ApJ...779...33M) allow for full flux recovery, which these data do not" (3 The Data)
- Caveat (inferred, ours): The ALMA comparison is qualitative, using published spectra
- Caveat (inferred, ours): Large uncertainties on the (9,9) fits
- Caveat (inferred, ours): Systemic velocity choice affects the outflow velocity
- Caveat (inferred, ours): H2O/NH3(3,1) decomposition is uncertain

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VLA project code not given
- Missing: Calibrator details
- Missing: Fit procedures
- Data volume (inferred): ~100-500 GB for VLA data (ALMA only used via published spectra)
- Score (inferred): 3/5, Main data are VLA and the recipe is loosely described; ALMA role is only a comparison.
- Rediscovery candidate: no, Main data are VLA, and key reduction and fitting details are missing.

## Links

- Method: (cite: 2015PASP..127..266M) (Source of the column density equation)
- Companion: (cite: 2015ApJ...800...70S) (ALMA HCN(4-3) and CS(7-6) spectra)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 28,
  "rate": 0.424
 },
 "evidence_ok": true
}
```
