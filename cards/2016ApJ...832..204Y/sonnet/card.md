# Stacking Spectra in Protoplanetary Disks: Detecting Intensity Profiles from Hidden Molecular Lines in HD 163296

`2016ApJ...832..204Y` | The Astrophysical Journal 2016 | first author: Yen, Hsi-Wei | arXiv: 1610.01780 | DOI: 10.3847/0004-637X/832/2/204

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can aligning spectra by Keplerian velocity before stacking boost S/N of molecular lines in a disk and reveal undetected weak lines and their intensity profiles?  
  > "We introduce a new stacking method in Keplerian disks that (1) enhances signal-to-noise ratios (S/N) of detected molecular lines and (2) that makes visible otherwise undetectable weak lines." (abstract)
- Target **HD 163296**: coordinates RA 17h56m21.28s, Dec -21d57m22.4s (J2000, pointing center)  
  > "HD 163296 is a Herbig Ae star at a distance of 122 pc (van den Ancker et al. 1998)." (3 Demonstration Case: HD 163296); "The pointing center was $\alpha$(J2000) = $17^{h}56^{m}21.28s$, $\delta$(J2000) = $-21\ensuremath{^\circ}57\ensuremath{'}22.4\ensuremath{''}$." (3 Demonstration Case: HD 163296); z/distance 122 pc  
  > "HD 163296 is a Herbig Ae star at a distance of 122 pc (van den Ancker et al. 1998)." (3 Demonstration Case: HD 163296); "The pointing center was $\alpha$(J2000) = $17^{h}56^{m}21.28s$, $\delta$(J2000) = $-21\ensuremath{^\circ}57\ensuremath{'}22.4\ensuremath{''}$." (3 Demonstration Case: HD 163296); distance from van den Ancker et al. 1998  
  > "HD 163296 is a Herbig Ae star at a distance of 122 pc (van den Ancker et al. 1998)." (3 Demonstration Case: HD 163296); "The pointing center was $\alpha$(J2000) = $17^{h}56^{m}21.28s$, $\delta$(J2000) = $-21\ensuremath{^\circ}57\ensuremath{'}22.4\ensuremath{''}$." (3 Demonstration Case: HD 163296)

## Data provenance

- ALMA projects: 2013.1.01268.S
- bands: _not stated_
- frequencies and spectral setup: Frequency Division Mode; 61 kHz spectral resolution; 58.6 MHz per spectral window  
  > "Each spectral window had a bandwidth of 58.6 MHz." (3 Demonstration Case: HD 163296); "were observed simultaneously with a spectral resolution of 61 kHz." (3 Demonstration Case: HD 163296)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' x 0.4''  
  > "The angular resolutions of the images are $\sim$0.5$''$ $\times$ 0.4$''$." (3 Demonstration Case: HD 163296)
- max recoverable scale: _not stated_
- sensitivity: 2.4 mJy/beam (DCO+, DCN), 2 mJy/beam (H2CO), 2.9 mJy/beam (N2D+) per channel  
  > "The noise levels are 2.4 mJy Beam$^{-1}$ in the DCO$^+$ and DCN, 2 mJy Beam$^{-1}$ in the H$_2$CO, and 2.9 mJy Beam$^{-1}$ in the N$_2$D$^+$ image." (3 Demonstration Case: HD 163296)
- time on source: 3.6 hours in total  
  > "HD 163296 was observed for 3.6 hours in total." (3 Demonstration Case: HD 163296)
- observing dates: July 27–29, 2014 (Cycle 2)  
  > "Observations were done with 31 to 33 antennas during the cycle-2 observing period on July 27–29, 2014." (3 Demonstration Case: HD 163296)
- pi or archival as stated: ALMA archive data  
  > "The HD 163296 data analyzed here are retrieved from the ALMA archive" (3 Demonstration Case: HD 163296)
- Line: DCO+ 3–2 (216.113 GHz)
- Line: DCN 3–2 (217.239 GHz)
- Line: N2D+ 3–2 (231.322 GHz)
- Line: H2CO 3_0,3–2_0,2 (218.222 GHz)
- Line: H2CO 3_2,2–2_2,1 (218.476 GHz)
- Line: H2CO 3_2,1–2_2,0 (218.76 GHz)
- External data: Stellar mass ~2.5 Msun  
  > "a central stellar mass $\sim$2.5 $M_\ensuremath{\odot}$" (3 Demonstration Case: HD 163296) [from Mannings & Sargent 1997; Isella et al. 2007; Hughes et al. 2008; de Gregorio-Monsalvo et al. 2013; Mathews et al. 2013; Rosenfeld et al. 2013]
- External data: Inclination ~45 deg and PA ~130 deg  
  > "Inclination and position angle are measured to be $\sim$45$\ensuremath{^\circ}$ and $\sim$130$\ensuremath{^\circ}$ (Isella et al. 2007)." (3 Demonstration Case: HD 163296) [from Isella et al. 2007 (cite: Isella07)]
- External data: Intrinsic line width ΔV_int ~(0.1–0.3)(r/100AU)^q km/s, q from -0.3 to -0.1  
  > "where $q$ ranges from $-0.3$ to $-0.1$ (e.g., Piétu et al. 2007)." (2.1 Narrower Line Widths) [from Piétu et al. 2007]

## Processing

### Calibration

- pipeline or manual: Standard cycle-2 reduction script in CASA  
  > "Calibration of the raw visibility data was performed with the standard reduction script for cycle-2 data using tasks in Common Astronomy Software Applications (CASA)" (3 Demonstration Case: HD 163296)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: None  
  > "and without self-calibration" (3 Demonstration Case: HD 163296)

### Imaging

- task: CASA clean  
  > "CLEANed with the CASA task “clean” at a velocity resolution of 0.1 km s$^{-1}$." (3 Demonstration Case: HD 163296)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Calibrated visibilities were Fourier-transformed with natural weighting" (3 Demonstration Case: HD 163296)
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

- Calibration with the standard cycle-2 reduction script  
  > "standard reduction script for cycle-2 data" (3 Demonstration Case: HD 163296) [from ALMA standard cycle-2 script]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean threshold, masks, cell and image size
- Continuum subtraction method and line-free channels
- Exact stellar mass, inclination, PA and systemic velocity used for alignment
- Velocity range used for the moment 0 maps beyond 9.3 km/s width
- Handling of pixels where Vk exceeds the velocity band
- Code for the stacking not released

## Analysis recipe

1. **Image line cubes**: Calibrate and CLEAN archival data with natural weighting at 0.1 km/s  
  > "CLEANed with the CASA task “clean” at a velocity resolution of 0.1 km s$^{-1}$." (3 Demonstration Case: HD 163296)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Align and stack spectra by Keplerian velocity**: Deproject pixels, compute projected Vk, shift each spectrum by Vk, mirror across minor axis, and sum over radial/azimuthal bins  
  > "We first align spectra ($\tbond I_V$) from different positions ($\Delta\alpha_j$, $\Delta\delta_j$) by shifting them by their $V_{{\rm k},j}$($\Delta\alpha_j$, $\Delta\delta_j$)." (2 New Stacking Method)
   - parameter: Radial ranges R<300 AU (DCO+, H2CO), R<200 AU (DCN), 100<R<300 AU (N2D+)  
  > "$R < 200$ AU ($\sim$1.6$''$) for DCN (3–2), and $100 < R < 300$ AU" (4 Results and Discussion)
   - assumption: Geometrically thin disk, Keplerian rotation  
  > "Assuming that the disk is geometrically thin, the projection correction is" (2 New Stacking Method)
   - fitting: _not stated_
   - validation: Integrated flux compared with unaligned spectra; S/N gain compared with analytic expectation  
  > "are consistent with those from the original spectra" (4 Results and Discussion)
3. **Derive radial intensity profiles and compare three methods**: Radial bins of half beam; mean integrated intensity from moment 0, unaligned stacks, and aligned stacks; uncertainties sigma_a*dv*sqrt(N)  
  > "Each radial bin is half of the synthesized beam size." (4 Results and Discussion)
   - fitting: _not stated_
   - validation: Compared S/N gain with Eq. for R_sn using ΔV_int ~0.3(r/100AU)^-0.3  
  > "We adopte $\Delta V_{\rm int} \sim 0.3 \times (r/{\rm 100\ AU})^{-0.3}$." (4 Results and Discussion)
4. **Reconstruct azimuthally resolved moment 0 maps**: Sectors 1.5 beam radially and 45 deg azimuthally for r>0.45''; inner region averaged over 2π  
  > "each sector spanning 1.5 times the beam size along the radial axis and 45$\ensuremath{^\circ}$ in azimuth" (4 Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and CLEAN imaging  
  > "using tasks in Common Astronomy Software Applications (CASA)" (3 Demonstration Case: HD 163296)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Integrated flux DCO+ (3–2), aligned | 12.9 | 0.1 | mJy/beam km/s | 2 | are measured to be 12.9$\pm$0.1 and 4.9$\pm$0.1 mJy Beam$^{-1}$ km s$^{-1}$ |
| Integrated flux H2CO 3_0,3–2_0,2, aligned | 4.9 | 0.1 | mJy/beam km/s | 2 | are measured to be 12.9$\pm$0.1 and 4.9$\pm$0.1 mJy Beam$^{-1}$ km s$^{-1}$ |
| Integrated flux unaligned DCO+ and H2CO | 11.4 and 4.5 | 0.2 and 0.3 | mJy/beam km/s | 2 | (11.4$\pm$0.2 and 4.5$\pm$0.3 mJy Beam$^{-1}$ km s$^{-1}$) |
| Peak intensity increase for DCO+ and H2CO | ~5 | not stated | dimensionless | 2 | the peak intensities of the spectra increase by a factor $\sim$5 |
| S/N gain of profiles vs moment 0 (DCO+, DCN) | ~4–6 | not stated | dimensionless | 3 | $\sim$4–6 times higher than those from moment 0 maps |

## Qualitative findings

- H2CO 3_2,2–2_2,1 and 3_2,1–2_2,0 become detected at >3σ after aligned stacking, with intensity peaking near ~100 AU  
  > "the intensities peak at radii around $\sim$100 AU" (4 Results and Discussion)
- N2D+ ring lies furthest out (~200 AU); DCN ring closer (~50 AU)  
  > "the ring-like structure of N$_2$D$^+$ is further outside than all the other lines at around 200 AU" (4 Results and Discussion)

## Claim tuples

- H: Velocity-aligned stacking boosts S/N while conserving flux | E: Compared aligned and unaligned spectra of six lines | R: Peak S/N up by ≳4–5; integrated flux consistent | F: Method enhances S/N | **supported**
- H: Undetectable weak lines can be recovered | E: Stacked H2CO 3_2,2 and 3_2,1 lines | R: Detected at >3σ | F: Hidden lines are revealed and their profiles measured | **supported**

## Reasoning

- Why this data: Several lines were only marginally or not detected, making HD 163296 a proof-of-concept target  
  > "This disk is, thus, an excellent proof-of-concept target." (3 Demonstration Case: HD 163296)
- Why this method: _not stated_
- Alternative: Optimal filtering of Dutrey et al. 2007 requires a best-fit line profile from model fitting  
  > "Their technique, however, relies on a best-fit line profile that needs to be derived first from model fitting." (1 Introduction)
- How they decided it was enough: _not stated_
- Limitation (authors): Enhancement is lower at radii smaller than the beam, and depends on accurate Vk  
  > "except at radii smaller than the synthesized beam size where the observed enhancement is lower" (4 Results and Discussion)
- Caveat (inferred, ours): Stellar mass, inclination and PA fixed to literature values without optimization
- Caveat (inferred, ours): Aligned stacking depends on assumed thin-disk geometry; scale height ignored
- Caveat (inferred, ours): Higher integrated intensities than other methods may reflect bias
- Caveat (inferred, ours): No error propagation for geometry uncertainties

## Reproducibility

- Data public (paper): Archival ALMA data, project 2013.1.01268.S  
  > "retrieved from the ALMA archive (project code: 2013.1.01268.S)" (3 Demonstration Case: HD 163296)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Adopted geometry and systemic velocity
- Missing: Stacking code
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data and explicit equations, but imaging and adopted parameters are not fully given and no code.
- Rediscovery candidate: yes, Public data, explicit algorithm, and numeric fluxes and S/N gains to compare.

## Links

- Method: Dutrey et al. 2007 (Optimal filtering technique for Keplerian disks)
- Companion: Mathews et al. 2013; Qi et al. 2015 (DCO+ and N2H+ rings in HD 163296)

## Checks

```json
{
 "quotes": 52,
 "quotes_ok": 52,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 33,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
