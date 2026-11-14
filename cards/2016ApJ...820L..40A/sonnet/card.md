# Ringed Substructure and a Gap at 1 au in the Nearest Protoplanetary Disk

`2016ApJ...820L..40A` | The Astrophysical Journal Letters 2016 | first author: Andrews, Sean M. | arXiv: 1603.09352 | DOI: 10.3847/2041-8205/820/2/L40

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Does the TW Hya disk show ringed substructure in 870 um continuum at ~1 AU resolution, and what could cause it?  
  > "In this Letter, we present and analyze observations that shed new light on the substructure in the TW Hya disk." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance not stated (1 AU = 20 mas implied)  
  > "First, it is the closest gas-rich disk to Earth (cite: vanleeuwen07)" (Introduction); distance from van Leeuwen 2007 cited for closeness only  
  > "First, it is the closest gas-rich disk to Earth (cite: vanleeuwen07)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00686.S, 2011.1.00399.S, 2013.1.00198.S
- bands: _not stated_
- frequencies and spectral setup: Four SPWs at 344.5, 345.8, 355.1, 357.1 GHz; bandwidths 1875, 469, 1875, 1875 MHz  
  > "The correlator processed four spectral windows centered at 344.5, 345.8, 355.1, and 357.1 GHz with bandwidths of 1875, 469, 1875, and 1875 MHz, respectively." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 36, 31, 34 antennas (new); 16, 25, 34 antennas (archival)  
  > "The array included 36, 31, and 34 antennas, respectively" (2 Observations)
- configurations: _not stated_
- baselines: 20 m to 14 km (new); 15-375 m (archival)  
  > "configured to span baseline lengths from 20 m to 14 km" (2 Observations)
- angular resolution: 24x18 mas (robust 0) and 30 mas circular  
  > "to provide a $24\times18$ mas synthesized beam (at P.A.=78$^\circ$)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: RMS ~35 uJy/beam  
  > "have RMS noise levels around 35 $\mu$Jy beam$^{-1}$" (2 Observations)
- time on source: ~2 hours (new); 95 minutes (archival)  
  > "The total on-target integration time was $\sim$2 hours." (2 Observations); "The combined on-target integration time was 95 minutes." (2 Observations)
- observing dates: Long baseline: 2015 Nov 23, Nov 30, Dec 1; archival: 2012 May 20, 2012 Nov 20, 2014 Dec 31  
  > "TW Hya was observed by ALMA on 2015 November 23, November 30, and December 1." (2 Observations); "from 2012 May 20, 2012 Nov 20, and 2014 Dec 31" (2 Observations)
- pi or archival as stated: _not stated_
- External data: Broken power-law dust surface density prescription used in model  
  > "we employed a broken power-law dust surface density prescription (cite: hogerheijde16)" (3 Results) [from (cite: hogerheijde16)]
- Simulation/model as data: RADMC-3D representative model disk (not optimized) used for temperature profile and SED  
  > "we generated a representative (but not in any sense optimized) model disk using the radiative transfer code `RADMC-3D` (cite: dullemond12)" (3 Results)

## Processing

### Calibration

- pipeline or manual: Calibrated by NRAO staff; WVR phase correction, 2 s averaging, flagging  
  > "These raw data were calibrated by NRAO staff." (2 Observations)
- casa version: CASA v4.5.0  
  > "All calibration and imaging was performed with the `CASA` package (v4.5.0)." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 and J1107-4449 for new data  
  > "The amplitude scale was determined from J1037-2934 and J1107-4449." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: One round of phase-only self-calibration  
  > "Some modest improvements were made with a round of phase-only self-calibration." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: multi-scale, multi-frequency synthesis CLEAN  
  > "deconvolving with a multi-scale, multi-frequency synthesis version of the `CLEAN` algorithm" (2 Observations)
- weighting robust: Briggs robust 0 (24x18 mas); robust 0.5 with taper (30 mas)  
  > "A second image was made with a robust parameter of 0.5 and an elliptical taper to create a circular 30 mas beam" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Visibilities shifted for proper motion and combined after excising line channels  
  > "The calibrated visibilities from each observation were shifted to account for the proper motion of the target and then combined" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: ~35 uJy/beam  
  > "have RMS noise levels around 35 $\mu$Jy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- RADMC-3D model follows the same basic assumptions as earlier TW Hya model  
  > "We followed the same basic assumptions as (cite: andrews12), with a few distinctions" (3 Results) [from (cite: andrews12)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and CLEAN mask
- Multiscale scales and clean threshold/iterations
- Line-free channels excised
- Self-calibration solution interval and reference
- Flux calibrator fluxes/scale uncertainty
- Details of azimuthal averaging and ellipse fits
- RADMC-3D model parameters (masses, radii, opacities, gas-to-dust)
- Distance adopted

## Analysis recipe

1. **Calibrate and combine data**: Calibrate each execution, combine new and archival visibilities, phase-only self-cal  
  > "The calibrated visibilities from each observation were shifted to account for the proper motion of the target and then combined after excising channels with potential emission from spectral lines." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared amplitudes of archival datasets on overlapping spatial frequencies  
  > "we compared the amplitudes from each individual dataset on overlapping spatial frequencies and found exceptional consistency." (2 Observations)
2. **Make continuum images**: Multi-scale multi-frequency CLEAN at 345.9 GHz; two weightings  
  > "Continuum images at a mean frequency of 345.9 GHz (867 $\mu$m) were generated by Fourier inverting the visibilities" (2 Observations)
   - software: CASA
   - parameter: robust 0 (24x18 mas) and robust 0.5 + taper (30 mas)  
  > "The first used a Briggs weighting (with a robust parameter of 0)" (2 Observations)
   - fitting: _not stated_
   - validation: Both images consistent within resolution differences  
  > "Both images are consistent (within the resolution differences)" (2 Observations)
3. **Radial profile and geometry**: Deproject to polar coordinates, azimuthally average; fit ellipses to rings/gap to get inclination and PA; compare azimuthal profiles  
  > "We fitted ellipses to the prominent bright rings at 2.4 and 40 AU (the latter between two dark annuli) and the dark annulus at 22 AU" (3 Results)
   - fitting: _not stated_
   - validation: Consistent with geometry from molecular line observations  
  > "Each feature was consistent with the standard geometry inferred from molecular line observations" (3 Results)
4. **Representative radiative transfer model**: RADMC-3D model following Andrews 2012 with broken power-law, inner dust belt, truncation at 2.4 AU; gives temperature profile  
  > "the outer disk is truncated at 2.4 AU (rather than the previously assumed 4 AU)" (3 Results)
   - software: RADMC-3D
   - parameter: Gaussian belt width 0.4 AU  
  > "a belt of dust that has a Gaussian density profile with a width of 0.4 AU" (3 Results)
   - fitting: _not stated_
   - validation: Reproduces SED but not brightness profile in detail  
  > "However, it still has difficulty reproducing the observed brightness profile in detail." (3 Results)

## Software

- **CASA** 4.5.0: calibration and imaging  
  > "All calibration and imaging was performed with the `CASA` package (v4.5.0)." (2 Observations)
- **RADMC-3D** : representative disk model and temperature profile  
  > "using the radiative transfer code `RADMC-3D` (cite: dullemond12)" (3 Results)
- **Astropy** : acknowledged software  
  > "benefitted from the `Astropy` (cite: astropy) and `Matplotlib` (cite: matplotlib) software packages" (Acknowledgments)
- **Matplotlib** : acknowledged software (figures)  
  > "benefitted from the `Astropy` (cite: astropy) and `Matplotlib` (cite: matplotlib) software packages" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner unresolved source flux | 0.93 | 0.04 | mJy | 2 | unresolved ($<$0.5 AU in radius) $0.93\pm0.04$ mJy source |
| Inclination | 7 | 3 | deg | 3 | an inclination of $7\pm3$$^\circ$ |
| Major axis position angle | 155 | 12 | deg | 3 | a major axis position angle of $155\pm12$$^\circ$ |
| Inner bright ring radius | 2.4 | not stated | AU | 3 | a bright ring that peaks at 2.4 AU |
| Dark annulus at 1 AU depth | >=30% brightness reduction | not stated | percent | 3 | we find at least a 30% brightness reduction |
| Median fractional azimuthal deviation | 7 | not stated | percent | 3 | the median fractional deviation is only 7% |

## Qualitative findings

- Concentric rings with dark annuli at 1, 22, 37, 43 AU (tentative 12, 28, 31 AU); no significant non-axisymmetric structure  
  > "The outer disk shows dark annuli at 22, 37, and 43 AU separated by more extended bright zones." (3 Results)

## Claim tuples

- H: Does TW Hya show ringed substructure at AU scales? | E: 870 um long-baseline ALMA imaging combined with archival data | R: Bright rings and narrow dark annuli at 1-43 AU with 5-30% contrasts | F: Ordered substructure on ~AU scales exists in the disk | **supported**
- H: Is the emission azimuthally symmetric? | E: Compare radial profiles over polar angle ranges | R: Median fractional deviation 7%, ~noise | F: No significant non-axisymmetric structures | **supported**
- H: What causes the substructure? | E: Compare features with temperatures from a representative RADMC-3D model and literature mechanisms | R: Outer features consistent with zonal flows; some near CO/N2 condensation fronts; 1 AU gap could be planet | F: Mechanism not determined; several plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Two images chosen after experimentation to balance resolution and sidelobes  
  > "After some experimentation, we settled on an analysis of two images made from the same composite dataset." (2 Observations)
- Alternative: H2O snowline as cause of 1-3 AU substructure judged unlikely  
  > "we do not see a good reason to expect that the H$_2$O snowline itself would result in the substantial density depletion" (4 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Depth of the 1 AU annulus is uncertain because it is unresolved; model is not optimized and fails to match the profile  
  > "Because it is unresolved, the depth of the dark annulus is difficult to determine unambiguously" (3 Results)
- Caveat (inferred, ours): Temperature model is crude, so snowline associations are weak
- Caveat (inferred, ours): Ring/gap radii and depths lack stated uncertainties
- Caveat (inferred, ours): Ellipse-fit and profile methods undescribed
- Caveat (inferred, ours): Dirty-beam sidelobes (~20%) could affect features in the robust 0 image

## Reproducibility

- Data public (paper): ALMA data identified by project codes; archival observations used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA$\#$2015.1.00686.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, scales)
- Missing: Self-cal solint
- Missing: Ring/gap fitting procedure
- Missing: RADMC-3D input parameters
- Data volume (inferred): Several hundred GB raw; tens of GB for long-baseline plus archival
- Score (inferred): 5/5, Data public and key settings (robust, beam, CASA version) given, but many imaging and analysis details missing.
- Rediscovery candidate: yes, Public data, a recoverable imaging recipe, and numeric ring radii and geometry results.

## Links

- Companion: (cite: zhang16) (Independent ALMA 0.3 arcsec images showing feature near 22 AU)
- Companion: (cite: nomura15) (Another ALMA study identifying a similar feature)
- Related: HL Tau ALMA long baseline campaign

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.1.00399.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00399.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 40,
  "rate": 0.597
 },
 "evidence_ok": true
}
```
