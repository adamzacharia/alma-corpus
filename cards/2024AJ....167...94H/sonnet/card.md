# The Hidden Clumps in VY CMa Uncovered by the Atacama Large Millimeter/submillimeter Array

`2024AJ....167...94H` | The Astronomical Journal 2024 | first author: Humphreys, Roberta M. | arXiv: 2401.14467 | DOI: 10.3847/1538-3881/ad1dd7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the motions, orientations, masses and ejection times of the four ALMA clumps near VY CMa, and what do the CO maps reveal about the outer ejecta?  
  > "We estimate their masses and ages, or time since ejection, and conclude that all four were ejected during VY CMa’s active period in the early 20th century." (abstract)
- Target **VY CMa**: coordinates 7:22:58.32 -25:46:03 (Table 1, 2015.74 epoch position)  
  > "at a distance of 1.15 kpc" (Proper Motions of the Clumps); "The weighted average of (cite: Choi)(1.14 (+0.11 -0.09) kpc) and (cite: Zhang)(1.20 (+0.13 -0.10) kpc)" (Footnote 3); z/distance 1.15 kpc  
  > "at a distance of 1.15 kpc" (Proper Motions of the Clumps); "The weighted average of (cite: Choi)(1.14 (+0.11 -0.09) kpc) and (cite: Zhang)(1.20 (+0.13 -0.10) kpc)" (Footnote 3); distance from weighted average of Choi et al. and Zhang et al.  
  > "at a distance of 1.15 kpc" (Proper Motions of the Clumps); "The weighted average of (cite: Choi)(1.14 (+0.11 -0.09) kpc) and (cite: Zhang)(1.20 (+0.13 -0.10) kpc)" (Footnote 3)

## Data provenance

- ALMA projects: 2021.1.01054.S, 2013.1.00156.S
- bands: Band 6 (216-270 GHz)  
  > "obtained with ALMA in Band 6 covering frequencies 216 to 270 GHz" (Data and Proper Motion Measurements)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.2 arcsec; continuum beams 196x180 mas (2021) and 175x132 mas (2015)  
  > "CO image cube with spatial resolution 0.2$''$ and velocity resolution of 1.25 km s$^{-1}$" (Data and Proper Motion Measurements)
- max recoverable scale: 3.4 arcsec (2021); 1.6 arcsec (2015)  
  > "| Continuum | 20150927 | 230.314 | – | – | – | 1”.6 |" (Table A1)
- sensitivity: rms 0.05 mJy (2021 continuum), 0.1 mJy (2015), 0.9 mJy 12CO, 1.0 mJy 13CO  
  > "| $^{12}$CO | 20211216 | 230.513 | 158 | 1.27 |" (Table A1)
- time on source: _not stated_
- observing dates: 2015-09-27 and 2021-12-09 (continuum); 2021-12-16 (CO cubes)  
  > "| Continuum | 20211209 | 249.339 |" (Table A1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.513 GHz)
- Line: 13CO J=2-1 (220.379 GHz)
- External data: 2015 Band 6 continuum data (project 2013.1.00156.S) used as first epoch  
  > "The 2015 data are described by (cite: Kaminski)." (Parameters for the 2021 ALMA Observations) [from (cite: Kaminski)]
- External data: Distance from Choi and Zhang parallaxes  
  > "The weighted average of (cite: Choi)(1.14 (+0.11 -0.09) kpc) and (cite: Zhang)(1.20 (+0.13 -0.10) kpc)" (Footnote 3) [from (cite: Choi); (cite: Zhang)]
- External data: Stellar temperature 3500 K  
  > "with an adopted temperature of 3500 K (cite: Wittkowski) for VY CMa" (Mass Lost and the Mass Loss Mechanism) [from (cite: Wittkowski)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Started from ALMA archive delivered data with instrumental, bandpass, flux and phase calibration applied  
  > "We started from the data delivered from the ALMA Science Archive with all instrumental calibration as well as bandpass, flux scale and phase referencing corrections applied." (Parameters for the 2021 ALMA Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase then amplitude self-calibration on line-free channels per tuning and configuration  
  > "we selected the line-free channels to use these for phase and then amplitude self-calibration." (Parameters for the 2021 ALMA Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: 36 arcsec on a side, out to <0.3 of full primary beam sensitivity  
  > "Both cubes were made to cover 36” on a side, out to $<0.3$ of the full primary beam sensitivity." (Parameters for the 2021 ALMA Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: First-order linear fit to line-free continuum in visibilities per spectral window  
  > "the line-free continuum was substracted from the calibrated visibility data using a first-order linear fit for the image cubes." (Parameters for the 2021 ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 196x180 mas PA 39 deg (continuum 2021); 265x251 mas (12CO)  
  > "| Continuum | 20211209 | 249.339 | – | – | – | 3”.4 | 196$\times$180 39$^{\circ}$ | 0.05 |" (Table A1)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and calibration of 2021 data  
  > "The data reduction steps and calibration are described in Paper I and its Appendix." (Data and Proper Motion Measurements) [from Paper I (cite: Singh)]
- Dust mass calculation with same input parameters  
  > "We determined the dust mass following (cite: OGorman) with the same input parameters." (Mass Lost and the Mass Loss Mechanism) [from (cite: OGorman)]
- Gas to dust ratio of 200  
  > "we adopt a gas to dust ratio of 200 (cite: Mauron) for the total mass lost." (Mass Lost and the Mass Loss Mechanism) [from (cite: Mauron)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (tclean weighting, robust, deconvolver, cell size) given only in Paper I
- CASA version
- Initial Gaussian estimates for imfit
- Dust opacity law and input parameters of the O'Gorman dust mass calculation
- Peak-location algorithm for Figure 6 centroids
- Renormalization procedure for continuum subtraction image
- Line-free channel ranges and self-cal solution intervals

## Analysis recipe

1. **Measure clump proper motions**: Simultaneous 2D Gaussian fits to five continuum peaks in 2015 and 2021 images, compare offsets from VY CMa  
  > "2D Gaussian compoments were then fit to all five peaks simultaneously" (The Fitting Method for the Proper Motion Measurements)
   - software: CASA imfit
   - parameter: Position errors approx (synthesised beam)/(S/N)  
  > "approximately (synthesised beam)/(S/N), for moderately extended array configurations (ALMA memo 620)" (The Fitting Method for the Proper Motion Measurements)
   - assumption: Distance 1.15 kpc  
  > "at a distance of 1.15 kpc" (Proper Motions of the Clumps)
   - fitting: _not stated_
   - validation: Residual images after subtraction have rms 0.4 and 0.2 mJy (2015, 2021)  
  > "the residual images have rms 0.4 and 0.2 mJy for the 2015 and 2021 data, respectively" (The Fitting Method for the Proper Motion Measurements)
2. **Determine line-of-sight velocities**: Inspect 12CO/13CO cube channels, line profiles and position-velocity slice at PA 120 deg; adopt peak velocities relative to LSR 22 km/s  
  > "we measure the intensity of the signal at positions along a line or slit at 120$^{\circ} \pm 0.05$ arcsec." (Line of Sight Velocities Toward the ALMA Clumps)
   - parameter: Uncertainty roughly FWHM/5, +-3 km/s typical  
  > "the realistic uncertainty of a peak in these data tends to be roughly ${\pm}$ FWHM/5." (The Line Profiles for the Four Clumps)
   - assumption: VY CMa LSR velocity 22+-1 km/s  
  > "VY CMa has an LSR velocity of 22$\pm$1 km s$^{-1}$" (Line of Sight Velocities Toward the ALMA Clumps)
   - fitting: _not stated_
   - validation: Sensitivity check: 5 km/s error in Clump D changes velocity and distance by <4%  
  > "That would alter the total expansion velocity and distance from the star by less than 4%" (The Line Profiles for the Four Clumps)
3. **Derive 3D motion, projected distance and ages**: Combine transverse and Doppler velocity for total velocity and orientation; age = distance/velocity from proper motion, no acceleration  
  > "The age estimates assume no acceleration or deceleration." (Morphology and Ages of the ALMA Clumps)
   - assumption: Reference ejection epoch 2015 for ages  
  > "The reference epoch for the proper motions, 2015, is the reference date for when the clumps were ejected." (Morphology and Ages of the ALMA Clumps)
   - fitting: _not stated_
   - validation: Acceleration effect 5-10%, less than age errors  
  > "showed that the effect was minimal, on the order of 5% to 10%" (Morphology and Ages of the ALMA Clumps)
4. **Estimate dust temperature, optical depth and masses**: T_gr ~ zeta (R*/r)^(1/2) T*; tau from e^-tau = 1 - T_obs/T_gr; dust mass following O'Gorman; total mass with gas to dust 200  
  > "The optical depth $\tau$ is estimated from the standard relation between the observed and dust temperatures" (Mass Lost and the Mass Loss Mechanism)
   - parameter: T* = 3500 K, R* ~ 7 AU  
  > "with an adopted temperature of 3500 K (cite: Wittkowski) for VY CMa and radius, $R_*$, $\approx$ 7 AU" (Mass Lost and the Mass Loss Mechanism)
   - assumption: Gas to dust ratio 200; dust optically thin for T_gr so masses for C and D are lower bounds  
  > "The mass estimates, especially for Clumps C and D, are lower bounds since the calculation uses the dust temperature for an optically thin case." (Mass Lost and the Mass Loss Mechanism)
   - fitting: _not stated_
   - validation: Compared with O'Gorman and Vlemmings masses for Clump C  
  > "Our result for Clump C is comparable to that from (cite: OGorman), but is less than the value from (cite: Vlemmings)." (Mass Lost and the Mass Loss Mechanism)
5. **Examine outer ejecta opacity and continuum subtraction artifact**: Compare position-velocity maps and channel images with and without continuum subtraction  
  > "Figure 9b is the image after continuum subtraction; it shows a very conspicuous dark spot which is merely a negative image of Clump C." (Unexpected phenomena in the outer ejecta)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imfit Gaussian fits of continuum peaks; viewer for initial estimates  
  > "We used the CASA task imfit for fitting the continuum peaks of the four Clumps A, B, C and D plus VY CMa" (The Fitting Method for the Proper Motion Measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Clump C proper motion | 3.7 | 0.4 | mas/yr | 1 | / Clump C / 320 / 122 / 23$\pm$2.0 / 3.7$\pm$0.4 / 20$\pm$2 / 102.0 $\pm$ 5 / |
| Clump C transverse velocity | 20 | 2 | km/s | 1 | / Clump C / 320 / 122 / 23$\pm$2.0 / 3.7$\pm$0.4 / 20$\pm$2 / 102.0 $\pm$ 5 / |
| Clump A transverse velocity | 46 | 11 | km/s | 1 | / Clump A / 560 / 19 / 53$\pm$12 / 8.5$\pm$2.0 / 46$\pm$11 / 27.5 $\pm$ 13 / |
| Clump D transverse velocity | 52 | 23 | km/s | 1 | / Clump D / 716 / 120 / 59$\pm$25.3 / 9.5$\pm$4.1 / 52$\pm$23 / 138.3 $\pm$ 29 / |
| Clump C age | 86 | -7,+8 | yr | 3 | / Clump C / 20$\pm$2 / +4$\pm$3 / 21$\pm$3 / +11$\pm$8 / 375$\pm$30 / 86$\pm$-7,+8 / |
| Clump A age | 66 | -12,+19 | yr | 3 | / Clump A / 46$\pm$11 / -18$\pm$5 / 50$\pm$11 / -21$\pm$7 / 691$\pm$60 / 66$\pm$-12,+19 / |
| Clump D Doppler velocity relative to star | +22 | 3 | km/s | 2 | / Clump D / 52$\pm$23 / +22$\pm$3 / 57$\pm$23 / +23$\pm$10 / 895$\pm$90 / 75$\pm$-15,+25 / |
| Clump C dust mass | > 1.2e-4 | not stated | Msun | 4 | / Clump C / 161 / 243 / 478 / 0.71 / $>$ 1.2$\times$ 10$^{-4}$ / $>$ 2.4$\times$ 10$^{-2}$ / |
| Total mass of four ALMA clumps | >= 0.05 | not stated | Msun | 4 | The total mass shed during this active period by the four ALMA knots is $\ge$ 0.05 M$_{\odot}$. |
| Clump C kinetic energy | a little more than 1e44 | not stated | erg | 4 | Clump C’s kinetic energy is a little more than 10$^{44}$ ergs |

## Qualitative findings

- Outer ejecta are opaque in 12CO near V_rel* ~ -28 km/s, so standard continuum subtraction produces an illusory dark spot (negative image of Clump C)  
  > "This fact produces a conspicuous but illusory dark spot if one attempts to subtract the continuum in a normal way." (abstract)

## Claim tuples

- H: Were the four ALMA clumps ejected during VY CMa's early 20th century active period? | E: Proper motions from 2015 and 2021 continuum plus CO Doppler velocities | R: Ages 66-86 yr with uncertainties | F: All four were ejected in the active period 1920-1950 | **supported**
- H: How much mass was lost in these ejections? | E: Dust mass from 249 GHz flux with gas to dust ratio 200 | R: Four clumps >= 0.05 Msun; with W1 A and B at least 0.07 Msun | F: Discrete episodes dominate recent mass loss | **supported**
- H: Is the dark spot at Clump C a real feature? | E: Compare data with and without continuum subtraction | R: Without subtraction the spot is absent; emission is from an opaque layer | F: The spot is an artifact of continuum subtraction | **supported**

## Reasoning

- Why this data: Closest 2015 dataset in frequency and resolution with a decent time baseline  
  > "The closest dataset to ours in terms of frequency and resolution with a decent time scale is from Kaminski" (Proper Motions of the Clumps)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Clump B Doppler velocity very uncertain  
  > "We consider this to be very uncertain." (Outflow Velocities of the Clumps)
- Limitation (authors): Mass lower bounds for C and D; clumps poorly resolved  
  > "The mass estimates, especially for Clumps C and D, are lower bounds" (Mass Lost and the Mass Loss Mechanism)
- Caveat (inferred, ours): Proper-motion errors are large for A, B, D
- Caveat (inferred, ours): Different frequencies and beams between epochs may bias positions
- Caveat (inferred, ours): Doppler velocity errors informal and systematic
- Caveat (inferred, ours): Dust mass depends on assumed opacity and gas to dust ratio

## Reproducibility

- Data public (paper): Data from ALMA Science Archive  
  > "We started from the data delivered from the ALMA Science Archive" (Parameters for the 2021 ALMA Observations)
- Products in archive: _not stated_
- Missing: Full imaging parameters (in Paper I)
- Missing: Opacity inputs for dust mass
- Missing: Peak-location algorithm details
- Data volume (inferred): ~100-300 GB for two epochs of Band 6 data
- Score (inferred): 3/5, Proper motion recipe is clear with tabulated numbers, but imaging and dust-mass inputs are deferred to other papers.
- Rediscovery candidate: no, Key imaging and mass inputs are in Paper I and the Kaminski and O'Gorman papers, so the recipe is not complete in this paper.

## Links

- Method: (cite: Singh) (Paper I: data reduction and calibration)
- Method: (cite: OGorman) (dust mass method)
- Companion: (cite: Singh) (Paper I, large-scale CO outflows from the same data)
- Companion: (cite: Kaminski) (2015 ALMA data and earlier clump study)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 42,
  "rate": 0.56
 },
 "evidence_ok": true
}
```
