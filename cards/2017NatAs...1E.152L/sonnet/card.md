# A rotating protostellar jet launched from the innermost disk of HH 212

`2017NatAs...1E.152L` | Nature Astronomy 2017 | first author: Lee, Chin-Fei | arXiv: 1706.06343 | DOI: 10.1038/s41550-017-0152

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the HH 212 protostellar jet rotate, and if so, from what disk radius is it launched (does the jet remove angular momentum from the innermost disk)?  
  > "Here we show that highly collimated protostellar jets remove the residual angular momenta at the $\sim$ 0.05 AU scale" (abstract)
- Target **HH 212 (IRAS 05413-0104)**: coordinates RA(J2000) 05h43m51.4086s, Dec -01d02m53.147s  
  > "Asterisks mark the source position at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4086$" (Figure 1 caption); "HH 212 is a nearby protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (main text); z/distance ~400 pc  
  > "Asterisks mark the source position at $\alpha_{(2000)}=05^\mathrm{h} 43^\mathrm{m} 51^\mathrm{s}_{^\textrm{.}} 4086$" (Figure 1 caption); "HH 212 is a nearby protostellar system deeply embedded in a compact molecular cloud core in the L1630 cloud of Orion at a distance of $\sim$ 400 pc." (main text); distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00122.S, 2015.1.00024.S
- bands: Band 7 (~350 GHz), Cycles 1 and 3  
  > "carried out with ALMA in Band 7 at $\sim$ 350 GHz in Cycles 1 and 3, with 32-45 antennas" (Observations)
- frequencies and spectral setup: Cycle 1: 4 spws (CO 3-2, SiO 8-7, HCO+ 4-3, continuum 358 GHz); Cycle 3 adds SO and H13CO+; 0.212 km/s channels binned by 4 to 0.848 km/s  
  > "The velocity resolution is 0.212 km s$^{-1}$ per channel. However, we binned 4 channels to have a velocity resolution of 0.848 km s$^{-1}$" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Cycle 1: 15-1466 m; Cycle 3: 17-16196 m  
  > "The projected baselines are 17-16196 m." (Observations)
- angular resolution: Cycle 1 ~0.16" (64 AU); Cycle 3 0.02" (8 AU); tapered 0.06" (24 AU)  
  > "One pointing was used to map the innermost part of the jet at an angular resolution of $0^{\prime\prime}_{^\textrm{.}}02$ (8 AU)." (Observations)
- max recoverable scale: Cycle 1 ~2.5"; Cycle 3 ~0.4"  
  > "The maximum recoverable size scale is $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$." (Observations)
- sensitivity: 1.6 mJy/beam (~40 K) at 0.02"; 1.9 mJy/beam (~6 K) at 0.06"  
  > "found to be $\sim$ 1.6 mJy beam$^{-1}$ (or $\sim$ 40 K) for a beam of $\sim$ $0^{\prime\prime}_{^\textrm{.}}02$ (8 AU)" (Observations)
- time on source: ~148 minutes total  
  > "The total time on the HH 212 system is $\sim$ 148 minutes." (Observations)
- observing dates: Cycle 1: 2015 Aug 29 (2 executions); Cycle 3: 2015 Nov 5 and Dec 3  
  > "one on November 5 and the other on December 3, during the Early Science Cycle 3 phase." (Observations)
- pi or archival as stated: _not stated_
- Line: SiO J=8-7 (347.330631 GHz)
- External data: 350 GHz dust continuum map of the disk, overlaid  
  > "on top of the dust continuum map (orange image) of the accretion disk at 352 GHz(cite: Lee2017)" (Figure 1 caption) [from (cite: Lee2017)]
- External data: Jet velocity ~115±50 km/s  
  > "a jet velocity(cite: Lee2015) of $v_j
\sim$ 115$\pm$50 km s$^{-1}$" (main text) [from (cite: Lee2015)]
- External data: Protostellar mass 0.25±0.05 Msun  
  > "With a protostellar mass of $M_\ast \sim$ 0.25$\pm$0.05 $M_\odot$(cite: Lee2014; Codella2014)" (main text) [from (cite: Lee2014; Codella2014)]
- External data: Jet inclination ~4 deg to plane of sky  
  > "The jet, lying close ($\sim$ 4$^\circ$) to the plane of the sky(cite: Claussen1998)" (main text) [from (cite: Claussen1998)]

## Processing

### Calibration

- pipeline or manual: CASA calibration of passband, flux, gain  
  > "The data were calibrated with the CASA package (versions 4.3.1 and 4.5) for the passband, flux, and gain" (Observations)
- casa version: 4.3.1 and 4.5  
  > "The data were calibrated with the CASA package (versions 4.3.1 and 4.5) for the passband, flux, and gain" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: robust = 2 (natural weighting)  
  > "We used a robust factor of 2 (natural weighting) for the visibility weighting to generate the SiO maps." (Observations)
- uv taper: 0.05" taper giving 0.06" (24 AU) beam  
  > "a taper of $0^{\prime\prime}_{^\textrm{.}}05$ was used to degrade the beam size to $0^{\prime\prime}_{^\textrm{.}}06$ (24 AU" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 3 only for innermost jet; Cycle 1+3 for outer knots  
  > "In order to map the knots further out, which are more extended, we also include the Cycle 1 data" (Observations)
- smoothing: 4 channels binned to 0.848 km/s  
  > "we binned 4 channels to have a velocity resolution of 0.848 km s$^{-1}$" (Observations)
- final beam: 0.02" (8 AU) and 0.06" (24 AU)  
  > "This generates a synthesized beam with a size of $0^{\prime\prime}_{^\textrm{.}}02$ (8 AU)" (Observations)
- final rms: 1.6 mJy/beam (8 AU beam); 1.9 mJy/beam (24 AU beam)  
  > "1.9 mJy beam$^{-1}$ (or $\sim$ 6 K) for a beam of $\sim$ $0^{\prime\prime}_{^\textrm{.}}06$ (24 AU)" (Observations)

### Inherited from earlier work

- Systemic velocity 1.7 km/s LSR and disk rotation sense taken from earlier work  
  > "The systemic velocity is assumed to be 1.7$\pm$0.1 km s$^{-1}$ LSR, as found before(cite: Lee2014)." (Figure 1 caption) [from (cite: Lee2014)]
- Launching radius derived from Eq. 4 of Anderson et al. 2003  
  > "the governing equation (Eq. 4 in Anderson et al. 2003)(cite: Anderson2003) that is used to derive the jet launching radius can be simplified" (Estimation of Jet Launching Radius) [from (cite: Anderson2003)]

### Not stated but needed to reproduce (our reading)

- Flux/passband/gain calibrator names (only in Supplementary tables not given)
- Deconvolver, clean threshold, masks, cell and image size
- Continuum subtraction and line-free channels
- Self-calibration
- Which CASA version applies to which dataset
- Rest-frame/systemic velocity choice for each knot cut and PV cut widths
- Details of Gaussian peak fitting and error treatment

## Analysis recipe

1. **Image SiO jet at 8 AU and 24 AU**: Cycle 3 only for 0.02" maps; Cycle 1+3 with 0.05" taper for 0.06" maps; natural weighting, 0.848 km/s channels  
  > "only Cycle 3 data are used to study the jet rotation in the innermost part of the jet." (Observations)
   - software: CASA
   - parameter: robust = 2; taper 0.05"  
  > "We used a robust factor of 2 (natural weighting) for the visibility weighting to generate the SiO maps." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure knot widths**: Gaussian fits to spatial profiles perpendicular to the jet axis, deconvolved by the 8 AU beam  
  > "we fitted the spatial profiles of the knots with a gaussian profile." (Gaussian deconvolved width)
   - fitting: Gaussian profile  
  > "In order to derive the width of the knots, we fitted the spatial profiles of the knots with a gaussian profile." (Gaussian deconvolved width of the jet knots:)
   - validation: _not stated_
3. **Measure velocity gradients across knots**: PV diagrams cut across knots; emission peaks from Gaussian fits; linear least-squares fit; peak position errors = quarter FWHM; >7 sigma detections  
  > "we identified the emission peaks (as marked by the green squares) with Gaussian fits and then fitted them with a linear velocity gradient using the least squares method." (main text)
   - parameter: Peak position uncertainty = a quarter of the FWHM  
  > "which are assumed to be given by a quarter of the FWHM." (Figure 4 caption)
   - fitting: linear least squares  
  > "we identified the emission peaks (as marked by the green squares) with Gaussian fits and then fitted them with a linear velocity gradient using the least squares method." (main text)
   - validation: Same sense of gradient in all resolved knots, consistent with disk rotation; precession ruled out as small  
  > "Since the sense of the gradient is the same in the resolved knots, the gradients are unlikely due to random velocity fluctuations in the jet." (main text)
4. **Specific angular momentum**: l = m (ΔV)^2/4 from gradient m and velocity range ΔV; mean excluding N3  
  > "the resulting specific angular momentum is $l=m (\triangle V)^2/4$" (main text)
   - assumption: Jet rotation symmetric about knot center  
  > "Assuming that the jet rotation is symmetric about the knot center" (main text)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive jet launching radius**: Approximate analytic solution of magneto-centrifugal energy and angular momentum conservation (Anderson et al. 2003) with correction terms in eta  
  > "They can improve the accuracy of the launching radius estimate in the case where the dimensionless parameter $\eta$ is not much smaller than unity" (Estimation of Jet Launching Radius)
   - parameter: M*=0.25±0.05 Msun; v_j=115±50 km/s; l_j=10.2±1.0 AU km/s  
  > "a mean jet specific angular momentum of $l_j\sim$ 10.2$\pm$1.0 AU km s$^{-1}$" (main text)
   - assumption: Gravitational potential negligible at large distance, jet velocity much larger than rotation, inclination ~4 deg  
  > "the jet inclination angle is very small ($\sim$ 4$^\circ$)" (Estimation of Jet Launching Radius)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1 and 4.5: Calibration (passband, flux, gain) of the data  
  > "The data were calibrated with the CASA package (versions 4.3.1 and 4.5) for the passband, flux, and gain" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Velocity gradient knot N2 | 0.363 | 0.040 | AU/(km/s) | 3 | 0.363$\pm$0.040 AU/(km s$^{-1}$) for knot N2 |
| Velocity gradient knot N3 | 0.533 | 0.326 | AU/(km/s) | 3 | 0.533$\pm$0.326 AU/(km s$^{-1}$) for knot N3 |
| Velocity gradient knot S3 | 0.635 | 0.070 | AU/(km/s) | 3 | 0.635$\pm$0.070 AU/(km s$^{-1}$) for knot S3 |
| Specific angular momentum N2, N3, S3 | 9.4, 9.6, 11.4 | 1.0, 6.0, 1.3 | AU km/s | 4 | 9.4$\pm$1.0, 9.6$\pm$6.0, and 11.4$\pm$1.3 AU km s$^{-1}$ for knots N2, N3, and S3 |
| Mean specific angular momentum (excl. N3) | 10.2 | 1.0 | AU km/s | 4 | the mean specific angular momentum is $l_j \sim 10.2\pm1.0$ AU km s$^{-1}$ |
| Jet launching radius | 0.05 | +0.05/-0.02 | AU | 5 | the launching radius of the jet is estimated to be $r_\textrm{\scriptsize 0}\sim$ 0.05$_{-0.02}^{+0.05}$ AU |
| Jet position angle | ~23 | not stated | deg | 0 | with a position angle measured to be $\sim$ 23$^\circ$ |
| Mean velocity northern / southern jet | -3 / 4 | not stated | km/s LSR | 0 | with a mean velocity of $\sim$ 4 km s$^{-1}$ LSR |

## Qualitative findings

- Both northern and southern jets rotate clockwise viewed from north to south, same as disk rotation  
  > "both the northern and southern jets are rotating clockwise when viewed along the jet axis from north to south" (main text)
- Knot widths decrease toward the source, from ~9-16 AU (N3, S3) to <~5-6 AU (N1, S1)  
  > "decreasing toward the central source, from $\sim$ 9-16 AU for knots N3 and S3" (main text)

## Claim tuples

- H: Does the HH 212 SiO jet rotate? | E: PV cuts across knots at 8 AU, 1 km/s resolution | R: Consistent velocity gradients in N2, N3, S3, same sense as the disk | F: Jet rotation detected; specific angular momentum ~10 AU km/s | **supported**
- H: Where is the jet launched? | E: Magneto-centrifugal relation with measured l_j, v_j, M* | R: r0 ~0.05 AU | F: Jet launched from innermost disk, removing angular momentum there | **supported**

## Reasoning

- Why this data: Only Cycle 3 data used for rotation to avoid proper motion between epochs  
  > "In order to avoid the proper motion effect" (Observations)
- Why this method: _not stated_
- Alternative: Gradients unlikely due to random velocity fluctuations or jet precession  
  > "The gradients are also unlikely due to jet precession" (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk is optically thick, preventing detection of the jet further in; knot N3 gradient quite uncertain  
  > "Unfortunately, the disk is flared and optically thick(cite: Lee2017), preventing us from detecting the jet further in." (main text)
- Caveat (inferred, ours): Launching radius relies on a model with large uncertainty in v_j and M*
- Caveat (inferred, ours): Only three marginally resolved knots give gradients; N1, S1, S2 unresolved
- Caveat (inferred, ours): Gradient could be affected by shock or beam smearing, not tested

## Reproducibility

- Data public (paper): Data available from the corresponding author on request; ALMA codes given  
  > "The data that support the plots within this paper and other findings of this study are available from the corresponding author upon reasonable request." (acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator details and imaging parameters beyond weighting/taper
- Missing: Peak fitting details
- Data volume (inferred): ~100-300 GB raw for the two projects
- Score (inferred): 3/5, Simple analysis with stated numbers, but imaging details and calibration are sparse.
- Rediscovery candidate: yes, Public ALMA archive data; short recipe with numeric results, though imaging details are missing.

## Links

- Method: (cite: Anderson2003) (Launching radius formulation)
- Companion: (cite: Lee2017) (Disk continuum map)
- Companion: (cite: Lee2017b) (Disk CH3OH/CD3OD observations)
- Companion: (cite: Lee2015) (Jet velocity and precession)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 45,
  "rate": 0.608
 },
 "evidence_ok": true
}
```
