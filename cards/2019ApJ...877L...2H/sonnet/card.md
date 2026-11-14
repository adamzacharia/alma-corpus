# Dust Polarization in Four Protoplanetary Disks at 3 mm: Further Evidence of Multiple Origins

`2019ApJ...877L...2H` | The Astrophysical Journal Letters 2019 | first author: Harrison, Rachel E. | arXiv: 1905.06266 | DOI: 10.3847/2041-8213/ab1e46

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What polarization morphologies do four Class II disks show at 3 mm, and are they consistent with self-scattering or radiative grain alignment?  
  > "In this Letter, we investigate two mechanisms capable of producing polarized dust emission in disks: self-scattering and grain alignment to the radiation anisotropy." (abstract)
- Target **DG Tau**: coordinates _not stated_; z/distance 140 pc  
  > "DG Tau has a protostar mass of 0.7 $M_\odot$ and an inclination angle of 32$^{\circ}$" (Introduction); "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction); distance from assumed for all sources (cite: bacciotti18)  
  > "DG Tau has a protostar mass of 0.7 $M_\odot$ and an inclination angle of 32$^{\circ}$" (Introduction); "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction)
- Target **Haro 6-13**: coordinates _not stated_; z/distance 140 pc  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction); distance from assumed (cite: bacciotti18)  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction)
- Target **RY Tau**: coordinates _not stated_; z/distance 140 pc  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction); distance from assumed (cite: bacciotti18)  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction)
- Target **MWC 480**: coordinates _not stated_; z/distance 140 pc  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction); distance from assumed (cite: bacciotti18)  
  > "we have assumed a distance of 140 pc for all sources (cite: bacciotti18)" (Introduction)
- Target **DL Tau (non-detection)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **V892 Tau (non-detection)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00470.S
- bands: Band 3  
  > "The observations were taken at a frequency range of 91.48–103.54 GHz (ALMA Band 3)." (Observations)
- frequencies and spectral setup: 91.48–103.54 GHz  
  > "The observations were taken at a frequency range of 91.48–103.54 GHz (ALMA Band 3)." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-7  
  > "in ALMA configuration C43-7" (Observations)
- baselines: _not stated_
- angular resolution: 0.2–0.3 arcsec  
  > "All images had an angular resolution between 0.2 and 0.3 arcsec." (Observations)
- max recoverable scale: _not stated_
- sensitivity: Stokes Q and U 20-40 uJy/beam  
  > "The typical sensitivities of the Stokes $Q$ and $U$ images are  20-40 $\mu$Jy/beam." (Observations)
- time on source: _not stated_
- observing dates: 2017 November 29 to 2017 December 3  
  > "The observations were taken with ALMA between 2017 November 29 and 2017 December 3" (Observations)
- pi or archival as stated: _not stated_
- External data: Stellar masses and inclinations of DG Tau, Haro 6-13, MWC 480, RY Tau  
  > "DG Tau has a protostar mass of 0.7 $M_\odot$ and an inclination angle of 32$^{\circ}$ (cite: 2011AA...529A.105G)." (Introduction) [from (cite: 2011AA...529A.105G); (cite: kwon); (cite: schaefer09); (cite: 2018arXiv181006044L)]
- External data: Beta values of the disks  
  > "The estimated $\beta$ values for these disks are 0.57 for DG Tau (cite: 2011AA...529A.105G)" (Introduction) [from (cite: 2011AA...529A.105G); (cite: kwon); (cite: ricci)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by NAASC data analysts, then phase-only self-calibration  
  > "The dataset was calibrated by data analysts at the North American ALMA Science Center." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800 (also bandpass)  
  > "J0510+1800 was the bandpass calibrator and flux calibrator." (Observations)
- flux scale uncertainty: ~10%  
  > "The uncertainty on absolute flux calibrations with ALMA is estimated at $\sim$10%." (Observations)
- self calibration: Three rounds phase-only on I,Q,U,V; solints scan length, 30.25 s, 15 s  
  > "we performed three rounds of phase-only self-calibration on all Stokes parameters ($I$, $Q$, $U$, and $V$)." (Observations); "The first iteration of gaincal used a solution interval equal to the scan length, the second iteration used a solution interval of 30.25 s, and the third iteration used a solution interval of 15 s." (Observations)

### Imaging

- task: CASA tclean  
  > "We used the CASA task tclean with Briggs weighting and a robust parameter of 0.5." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "We used the CASA task tclean with Briggs weighting and a robust parameter of 0.5." (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Thresholds 10x Stokes I rms (first three iterations), 3x (fourth)  
  > "The threshold for the first three iterations of tclean was set to 10 times the $I$ rms, and the threshold for the fourth iteration was set to three times the $I$ rms." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version
- Calibration pipeline version
- Image size and cell size
- Deconvolver and masks
- Source coordinates
- Number of execution blocks and baseline range
- Details of the simple polarization model (disk brightness profile, position angles, fitting criterion for 'best fit')
- Which sources' self-cal parameters apply to each source

## Analysis recipe

1. **Self-calibrate and image all Stokes**: Three rounds of phase-only self-cal on I,Q,U,V, imaging with tclean Briggs robust 0.5  
  > "we performed three rounds of phase-only self-calibration on all Stokes parameters ($I$, $Q$, $U$, and $V$)." (Observations)
   - software: CASA
   - parameter: solints: scan length, 30.25 s, 15 s  
  > "the second iteration used a solution interval of 30.25 s, and the third iteration used a solution interval of 15 s." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Produce polarized intensity and angle maps**: Debias polarized intensity P = sqrt(Q^2+U^2-sigma^2) using average Q,U noise  
  > "The polarized intensity maps were debiased using the average noise value determined from the $Q$ and $U$ maps" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Compare with simple polarization mechanism models**: Axisymmetric model maps of polarized intensity/angle for Rayleigh scattering, radiative, Gold mechanical, and toroidal magnetic alignment, given inclination, PA and beam  
  > "The model creates a map of the polarized intensity and polarization angle based on the disk’s inclination and position angle, as well as the beam size and position angle" (Discussion)
   - assumption: Scattering fraction scales as sin^2(i); scattering angle parallel to minor axis; radiative angle is radial direction rotated 90 deg  
  > "The polarization fraction produced by self-scattering depends on the disk inclination angle $i$ as $\sin^2(i)$." (Discussion)
   - fitting: _not stated_
   - validation: Qualitative comparison with maps  
  > "Figures [4](#dg_haro_mod) and [5](#mwc_ry_mod) show the models that best fit the observed polarization for each source" (Discussion)

## Software

- **CASA** : Calibration, self-calibration, tclean imaging  
  > "We used the CASA task tclean with Briggs weighting and a robust parameter of 0.5." (Observations)
- **astropy** : Listed software  
  > "CASA (McMullin et al. 2007), astropy (The Astropy Collaboration 2013, 2018), APLpy (Robitaille & Bressert 2012)" (Software)
- **APLpy** : Listed software (plotting)  
  > "CASA (McMullin et al. 2007), astropy (The Astropy Collaboration 2013, 2018), APLpy (Robitaille & Bressert 2012)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| DG Tau Stokes I flux | 42.71 | 0.64 | mJy | 1 | / DG Tau / 32$^{\circ}$ / $42.71 \pm 0.64$ / 16.0 / 127 / 15 / |
| Haro 6-13 Stokes I flux | 24.96 | 0.08 | mJy | 1 | $24.96 \pm 0.08$ |
| MWC 480 Stokes I flux | 23.21 | 0.41 | mJy | 1 | $23.21 \pm 0.41$ |
| RY Tau Stokes I flux | 29.50 | 0.09 | mJy | 1 | $29.50 \pm 0.09$ |
| P peak DG Tau | 127 | 15 | uJy/beam | 2 | / DG Tau / 32$^{\circ}$ / $42.71 \pm 0.64$ / 16.0 / 127 / 15 / |
| P peak RY Tau | 243 | 19 | uJy/beam | 2 | / RY Tau / 65$^{\circ}$ / $29.50 \pm 0.09$ / 29.7 / 243 / 19 / |
| 3-sigma polarization fraction limit DL Tau | 0.8 | not stated | % | 2 | The 3-$\sigma$ upper limits on the polarization fraction in DL Tau and V892 Tau are 0.8% and 0.4%, respectively. |

## Qualitative findings

- DG Tau and Haro 6-13 show azimuthal polarization with two low-polarization holes; RY Tau and MWC 480 show polarization parallel to the minor axis peaking at the center.  
  > "those with polarization angles oriented azimuthally in the outer part of the polarized region (DG Tau and Haro 6-13)" (Conclusions)

## Claim tuples

- H: Do similar disks at 3 mm show the same polarization mechanism? | E: ALMA Band 3 polarimetry of six disks, four detected | R: Two distinct morphologies: azimuthal vs minor-axis parallel | F: Different polarization mechanisms may dominate in different disks at the same wavelength | **supported**
- H: Are the differences due to inclination or S/N? | E: Compare with simple axisymmetric models | R: Haro 6-13 and MWC 480 have similar inclination but different morphologies | F: Not solely due to inclination | **supported**
- H: Does radiative alignment explain DG Tau and Haro 6-13? | E: Model comparison | R: Broadly consistent but expected azimuthal intensity variations not seen | F: Radiative alignment does not account for all features | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gold mechanical alignment predicts low-polarization holes along minor axes, unlike radiative alignment  
  > "models of the expected polarization from mechanical alignment through the Gold mechanism for these disks produced azimuthally oriented polarization vectors with low-polarization holes on either side of the disks’ minor axes." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Polarized regions of RY Tau and MWC 480 are only about a beam across; models axisymmetric  
  > "The polarized regions of RY Tau and MWC 480 are only about a beam across." (Results)
- Limitation (authors): Only statistical uncertainties considered  
  > "For the rest of this Letter only statistical uncertainties are considered." (Observations)
- Caveat (inferred, ours): Model comparison is qualitative with no quantitative fit statistic
- Caveat (inferred, ours): Polarized emission only about a beam across for two sources
- Caveat (inferred, ours): Source distances assumed identical
- Caveat (inferred, ours): No multi-wavelength data to test mechanisms

## Reproducibility

- Data public (paper): Project code given; archive public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ALMA #2017.1.00470.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Image/cell size and masks
- Missing: Model code and parameters
- Missing: Source coordinates and position angles
- Data volume (inferred): ~100-300 GB raw (one Band 3 polarization dataset, six targets)
- Score (inferred): 5/5, Data and main imaging/self-cal settings given, but versions, model details and image parameters are missing; results are partly qualitative.
- Rediscovery candidate: no, Main conclusions are qualitative morphological comparisons with an under-specified model.

## Links

- Method: (cite: yang18) (Models of radiative and aerodynamic alignment polarization)
- Companion: (cite: 2017ApJ...851...55S) (HL Tau multi-wavelength polarization)
- Companion: (cite: bacciotti18) (DG Tau ALMA 870 um polarization)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 38,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
