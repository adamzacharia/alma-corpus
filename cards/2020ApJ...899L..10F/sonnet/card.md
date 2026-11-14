# A Low-velocity Bipolar Outflow from a Deeply Embedded Object in Taurus Revealed by the Atacama Compact Array

`2020ApJ...899L..10F` | The Astrophysical Journal Letters 2020 | first author: Fujishiro, Kakeru | arXiv: 2006.06378 | DOI: 10.3847/2041-8213/ab9ca8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the dense core L1535-NE/MC35 in Taurus host a deeply embedded first hydrostatic core candidate, as shown by a low-velocity bipolar outflow, 1.3 mm continuum and N2D+ emission?  
  > "Among the targets, MC35-mm centered at one of the densest $``$starless$"$ cores in Taurus has blueshifted/redshifted wings in the $^{12}$CO (2–1) line" (abstract)
- Target **L1535-NE/MC35 (MC35-mm)**: coordinates 4h35m7.5s, +24d09m17.0s (J2000, observed center)  
  > "The observed central coordinate was ($\alpha_{J2000.0}$, $\delta_{J2000.0}$)=(4$^{\rm h}$35$^{\rm m}$7.5s, +24$^\circ$09$'$17.0$''$)." (2 Observations); "corresponding to 850 au $\times$ 730 au at a distance of 126.6 pc (cite: Galli18)" (2 Observations); z/distance 126.6 pc  
  > "The observed central coordinate was ($\alpha_{J2000.0}$, $\delta_{J2000.0}$)=(4$^{\rm h}$35$^{\rm m}$7.5s, +24$^\circ$09$'$17.0$''$)." (2 Observations); "corresponding to 850 au $\times$ 730 au at a distance of 126.6 pc (cite: Galli18)" (2 Observations); distance from Galli et al. 2018  
  > "The observed central coordinate was ($\alpha_{J2000.0}$, $\delta_{J2000.0}$)=(4$^{\rm h}$35$^{\rm m}$7.5s, +24$^\circ$09$'$17.0$''$)." (2 Observations); "corresponding to 850 au $\times$ 730 au at a distance of 126.6 pc (cite: Galli18)" (2 Observations)

## Data provenance

- ALMA projects: 2018.1.00756.S
- bands: 1.3 mm continuum (Band 6)  
  > "in 1.3 mm continuum and molecular lines using the Atacama Large Millimeter/submillimeter Array–Atacama Compact Array (ALMA–ACA) stand-alone mode" (abstract)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ACA (7 m) stand-alone, plus Total Power for 12CO  
  > "We use the combined 7 m + Total Power (TP) array data to recover the extended emission of $^{12}$CO" (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 6.8'' x 6.0'' (850 au x 730 au)  
  > "The angular resolution is 6.8$''$ $\times$ 6.0$''$, corresponding to 850 au $\times$ 730 au" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum ~0.4 mJy/beam; lines ~0.06 mJy/beam (~0.05 K) at ~0.1 km/s  
  > "The rms sensitivities of the continuum and lines are $\sim$0.4 mJy beam$^{-1}$ and $\sim$0.06 mJy beam$^{-1}$ ($\sim$0.05 K) at a velocity resolution of $\sim$0.1 km s$^{-1}$" (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (not stated)
- Line: N2D+ 3-2 (not stated)
- Line: 13CO, C18O 2-1 (not stated)
- Other facility **IRAM 30 m (MAMBO)**: 1.2 mm continuum image for comparison  
  > "the 1.2 mm continuum emission by the IRAM 30 m telescope, and infrared images by the Spitzer" (2 Observations)
- Other facility **Spitzer, Herschel**: archival non-detection of point sources shorter than 70 um; 100 um flux  
  > "We checked the archival data of the Herschel and Spitzer and confirmed the non-detection of point sources at wavelengths shorter than 70 $\mu$m." (2 Observations)
- External data: Dense core catalog of Taurus (MC35 etc.)  
  > "there is a dense core catalog (cite: Oni2002), which was sampled by an unbiased large-scale molecular gas survey" (1 Introduction) [from (cite: Oni2002)]
- External data: Turbulent line width of the source, ~0.3 km/s  
  > "the turbulence of this source ($\Delta V$ $\sim$0.3 km s$^{-1}$, see (cite: Tob2013))" (3.1) [from (cite: Tob2013)]
- External data: Herschel 100 um integrated flux ~0.6 Jy  
  > "The Herschel Gould Belt survey (cite: Andre2014) detected the 100 $\mu$m emission with an integrated luminosity of $\sim$0.6 Jy" (4.1) [from (cite: Andre2014)]

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
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 7 m + Total Power for 12CO; 7 m alone for N2D+  
  > "while for N$_2$D$^+$  we use the 7 m array data alone to be compared with the compact 1.3 mm source" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation settings, data quality and calibration/imaging details  
  > "As the detailed observational properties of this project are given in Paper I, and thus we summarize the data qualities of the target briefly." (2 Observations) [from Paper I = (cite: Tok2020)]
- CO mass estimate equations  
  > "following the equations written by (cite: Pin2011)" (3.1) [from (cite: Pin2011)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/CASA version, calibrators, imaging parameters (weighting, cell, masks) are only in Paper I
- Rest frequencies and how TP and 7 m data were combined
- Exact velocity ranges and contour levels for the wing maps beyond the stated ranges
- Opacity correction for 12CO mass estimate

## Analysis recipe

1. **Fit the continuum source**: Two-dimensional Gaussian fitting of the 1.3 mm continuum  
  > "Based on the two-dimensional Gaussian fitting to it, the central coordinate and deconvolved size are derived" (3.1)
   - fitting: _not stated_
   - validation: Peak position compared with IRAM 30 m peak  
  > "The peak position coincides with that obtained by the IRAM 30 m (cite: Mot2001)." (3.1)
2. **Identify outflow wings in 12CO**: Visual search for high-velocity wings as excess over Gaussian-like profile; blue 3.5–4.7 and red 7.5–10.0 km/s  
  > "we searched for high-velocity wing components more than a few km s$^{-1}$ apart from the systemic velocity as the excess emission to the Gaussian-like spectral profile by eye" (3.1)
   - parameter: Blue 3.5–4.7 km/s; red 7.5–10.0 km/s  
  > "The selected velocity ranges of the blueshifted and redshifted components are 3.5–4.7 km s$^{-1}$, and 7.5–10.0 km s$^{-1}$, respectively." (3.1)
   - fitting: _not stated_
   - validation: No significant 13CO in these ranges; turbulence cannot explain the velocities  
  > "We could not detect significant $^{13}$CO emission in these velocity ranges." (3.1)
3. **Derive outflow parameters**: Max velocity relative to N2D+ centroid (5.9 km/s); size from continuum peak to lobe peak; dynamical time = size/velocity; LTE mass  
  > "The resultant dynamical time (=size/velocity) of the wing is $\sim$(1–6) $\times$ 10$^3$ yr." (3.1)
   - assumption: Inclination 30 and 70 deg; Tex = 20 K; [12CO/H2] = 1e-4; LTE  
  > "assuming the local thermo-dynamical equilibrium with a uniform excitation temperature of 20 K and \[$^{12}$CO/H$_2$\] = 10$^{-4}$" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Map dense gas with N2D+**: Moment 0 and moment 1 maps from 7 m data  
  > "The intensity-weighted mean velocity (moment 1) map of N$_2$D$^+$ (Figure [4](#fig:N2DP) (b)) marginally shows a velocity gradient from the northeast to the southwest" (3.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software


## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 2.8 | not stated | mJy/beam | 1 | The peak and total continuum fluxes obtained by the ACA are 2.8 mJy beam$^{-1}$ and 7.8 mJy, respectively. |
| Total continuum flux | 7.8 | not stated | mJy | 1 | The peak and total continuum fluxes obtained by the ACA are 2.8 mJy beam$^{-1}$ and 7.8 mJy, respectively. |
| Deconvolved continuum size | 10.3'' x 7.2'', PA ~178.1 deg | not stated | arcsec, deg | 1 | 10.3$''$ $\times$ 7.2$''$ with a position angle of $\sim$178.1$^\circ$ |
| N2D+ peak brightness temperature | ~0.5 | not stated | K | 4 | strongest N$_2$D$^+$ emission with a peak brightness temperature of $\sim$0.5 K at MC35-mm |
| Outflow dynamical time | ~(1–6) x 10^3 | not stated | yr | 3 | The resultant dynamical time (=size/velocity) of the wing is $\sim$(1–6) $\times$ 10$^3$ yr. |
| Wing masses (south blue, south red, north red) | 0.6, 1.2, 2.0 | not stated | 1e-5 Msun | 3 | Mass ($10^{-5}\,M_\odot$)      / 0.6 |

## Qualitative findings

- Bipolar conical wing features connected to the continuum peak; N2D+ velocity gradient roughly perpendicular to outflow  
  > "which is roughly perpendicular to that of the wing components" (3.2)

## Claim tuples

- H: MC35-mm drives a molecular outflow from a deeply embedded object | E: Searched 12CO ACA+TP data for high-velocity wings toward continuum-detected cores | R: Blue/red wings up to ~4 km/s, lobe sizes ~2e3 au, dynamical time ~1e3 yr | F: A low-velocity wide-angle outflow from an embedded object is present | **supported**
- H: MC35-mm is a first hydrostatic core candidate | E: Compared outflow, N2D+, and continuum properties to theory and other sources | R: Properties not in conflict with first-core predictions; Herschel 100 um peak offset is a concern | F: MC35-mm is the only first-core candidate in Taurus, though VeLLO cannot be excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Contamination from the nearby protostar IRAS 04325+2402 outflow rejected  
  > "we conclude that the wing components are not just arising from the contamination of the protostellar activity in the southern part." (4.1)
- How they decided it was enough: _not stated_
- Limitation (authors): First core and VeLLO are hard to distinguish; follow-up high-resolution observations are needed  
  > "it is observationally difficult to distinguish between the first core and VeLLO" (4.1)
- Caveat (inferred, ours): Wing identification done by eye with no significance threshold
- Caveat (inferred, ours): Low resolution (~6'') and the nearby protostar leave contamination ambiguity
- Caveat (inferred, ours): Outflow parameters depend on assumed inclination and Tex with no uncertainties
- Caveat (inferred, ours): Lifetime estimate rests on one candidate

## Reproducibility

- Data public (paper): ALMA project 2018.1.00756.S acknowledged  
  > "ADS/ JAO.ALMA #2018.1.00756.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (in Paper I)
- Missing: Contour levels and moment-map settings
- Missing: Mass calculation details
- Data volume (inferred): ~10-50 GB for the ACA and TP data of the project
- Score (inferred): 3/5, Public data and simple analysis, but processing is deferred to Paper I and key parameters are missing.
- Rediscovery candidate: no, Processing is only in Paper I and the wing identification is subjective.

## Links

- Method: (cite: Tok2020) (Paper I: observation settings, data reduction and 1.3 mm continuum results)
- Method: (cite: Pin2011) (Equations for the outflow mass)
- Companion: (cite: Tok2020) (FREJA survey Paper I)
- Related: FREJA (FRagmentation and Evolution of dense cores Judged by ALMA)

## Checks

```json
{
 "quotes": 44,
 "quotes_ok": 44,
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
  "facts": 67,
  "stated": 28,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
