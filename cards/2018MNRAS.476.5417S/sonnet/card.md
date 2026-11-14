# Unveiling the inner morphology and gas kinematics of NGC 5135 with ALMA

`2018MNRAS.476.5417S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Sabatini, G. | arXiv: 1712.08834 | DOI: 10.1093/mnras/sty570

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the inner gas morphology and kinematics of the Seyfert 2 galaxy NGC 5135, and can a tilted-ring rotating disk model explain them?  
  > "Here we present a reconstruction of the gas morphology and kinematics in the inner regions of this galaxy" (abstract)
- Target **NGC 5135**: coordinates AGN region A: RA(J2000) +13:25:43.99, DEC(J2000) -29:50:00.02  
  > "NGC 5135, a nearby galaxy at $z$=$0.013693$ (implying a scale of $\sim$281 pc/arcsec)" (NGC5135); z/distance z = 0.013693 (~281 pc/arcsec)  
  > "NGC 5135, a nearby galaxy at $z$=$0.013693$ (implying a scale of $\sim$281 pc/arcsec)" (NGC5135); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00243.S, 2013.1.00524.S
- bands: Band 6 (~1.3 mm) and Band 9 (~500 um)  
  > "band 6 (B6, $\sim$1.3 mm) and band 9 (B9, $\sim$500 $\mu$m)" (Introduction)
- frequencies and spectral setup: B6: 1875 MHz windows at 227.4 and 241.6 GHz (488 kHz channels), 2 GHz continuum window at 228.8 GHz; B9: four windows at 678.2, 680.2, 683.7, 682.0 GHz  
  > "Two 1875 MHz spectral windows, centred respectively at the sky frequencies of 227.4 GHz, and 241.6 GHz" (3 The ALMA (archival) data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: B6: compact (38 antennas) and extended (44 antennas); B9: 39 antennas  
  > "The “compact” configuration was obtained with 38 antennas distributed over the baseline range between 15.0 and 348.5 m, while the “extended” one with 44 antennas over the baseline range 15 – 1600 m" (3 The ALMA (archival) data)
- baselines: B9: 20.5-886 m  
  > "39 12-m antennas included in a range of baselines between 20.5 and 886 m" (3 The ALMA (archival) data)
- angular resolution: B6 continuum beam 0.25x0.20 arcsec; B9 0.30x0.29 arcsec  
  > "The achieved continuum beam size of the concatenated image is 0.25$^{\prime \prime}\times$ 0.20$^{\prime \prime}$" (3 The ALMA (archival) data)
- max recoverable scale: B6 ~12 arcsec; B9 ~2.68 arcsec  
  > "The maximum recoverable scale for the B9 configuration is $\simeq$2.68 arcsec." (3 The ALMA (archival) data)
- sensitivity: B6 continuum rms 1.9e-5 Jy/beam; B9 2.11e-3 Jy/beam  
  > "the 1$\sigma$ RMS is 1.9$\times$ $10^{-5}$ Jy beam$^{-1}$" (3 The ALMA (archival) data)
- time on source: _not stated_
- observing dates: B9 on 2 June 2015 (Cycle 3)  
  > "were taken on June 2$^{nd}$ 2015" (3 The ALMA (archival) data)
- pi or archival as stated: Archival; PIs Colina (B6) and N. Lu (B9)  
  > "based on the analysis of Atacama Large Millimeter Array (ALMA) archival data" (abstract)
- Line: CO J=2-1 (not stated)
- Line: CS J=5-4 (not stated)
- Line: CO J=6-5 (not stated)
- Other facility **VLT SINFONI**: Near-IR line and continuum maps used for AGN and SF region positions  
  > "(cite: bedregal2009) observed NGC 5135 with VLT SINFONI in \[Si VI\]$\lambda \:1.96\: \mu m$ line" (NGC5135)
- Other facility **Chandra**: X-ray AGN position and obscuration  
  > "Our target was also observed by (cite: levenson2004) in the X-rays with Chandra (0.4-8 keV)" (NGC5135)
- External data: SED decomposition parameters (M*, L_IR, SFR, L_BOL AGN) and broad-band SED  
  > "the broad-band SED and the result of the decomposition performed by (cite: gruppioni2016) are shown in Figure [2]" (NGC5135) [from (cite: gruppioni2016)]

## Processing

### Calibration

- pipeline or manual: B6: archive ALMA pipeline; B9: manual calibration, improved over archive script  
  > "Manual calibration was performed for the archival data." (3 The ALMA (archival) data)
- casa version: B6 pipeline calibration CASA 4.2.2; concatenation with CASA 4.7.1  
  > "The calibrated data-sets of the two configurations were concatenated and combined with CASA 4.7.1." (3 The ALMA (archival) data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: B9 flux model scaled by factor 0.84 to 1.39 Jy; phase calibrator J1316-3338  
  > "updated the flux density model for the flux density calibrator by a factor 0.84 (to the value of 1.39 Jy)" (3 The ALMA (archival) data)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA standard cleaning on combined image  
  > "the CASA standard cleaning was performed on the combined image, considering *briggs - $robust=0.5$* weighting." (3 The ALMA (archival) data)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "considering *briggs - $robust=0.5$* weighting" (3 The ALMA (archival) data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact and extended B6 configurations concatenated  
  > "The calibrated data-sets of the two configurations were concatenated" (3 The ALMA (archival) data)
- smoothing: _not stated_
- final beam: B6 0.25x0.20 arcsec; B9 0.30x0.29 arcsec  
  > "The beam of the B9 continuum image is 0.30$^{\prime \prime}$v$\times$0.29$^{\prime \prime}$" (3 The ALMA (archival) data)
- final rms: B6 1.9e-5, B9 2.11e-3 Jy/beam; moment 0 rms 1.1e-3 (CO 2-1), 1.5e-2 (CO 6-5), 1.5e-4 (CS) Jy km/s/beam  
  > "The 1$\sigma$ RMS obtained for the moment 0 maps is 1.1$\times$ $10^{-3}$ and 1.5$\times$ $10^{-2}$ Jy km s$^{-1}$ beam$^{-1}$" (3 The ALMA (archival) data)

### Inherited from earlier work

- 3D tilted-ring fitting code and residual definition  
  > "the flux of the RMS of the data-cube is associated to D in case it is a blank pixel; see (cite: diteodoro2015) for details" (4 3DBAROLO) [from (cite: diteodoro2015)]
- SED decomposition of NGC 5135  
  > "the broad-band SED and the result of the decomposition performed by (cite: gruppioni2016) are shown in Figure [2]" (NGC5135) [from (cite: gruppioni2016)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and method of continuum subtraction
- Clean threshold, mask, image size, cell size
- Whether primary beam correction was applied
- Rest frequencies and velocity definition for cubes
- Full 3DBarolo parameter file (rings, widths, number of rings, fixed values, weighting function, fit-region)
- Which B9 flux calibrator and how the 0.84 correction was derived
- Self-calibration usage
- Flagged antenna names
- Region extraction geometries and region flux values

## Analysis recipe

1. **Calibrate and image continuum and line data**: B6 archive pipeline calibration with configurations concatenated; B9 manually recalibrated; CASA cleaning with briggs weighting  
  > "Finally, the CASA standard cleaning was performed on the combined image, considering *briggs - $robust=0.5$* weighting." (3 The ALMA (archival) data)
   - software: CASA
   - parameter: robust = 0.5  
  > "considering *briggs - $robust=0.5$* weighting" (3 The ALMA (archival) data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make moment maps and measure region fluxes**: Moment 0, 1, 2 maps; regions drawn on lower-resolution B9 continuum and applied to both bands using CASA viewer  
  > "we have selected the extraction region as to include all the flux in that band in the continuum image, applying the same extraction region to both bands." (3 The ALMA (archival) data)
   - software: CASA viewer
   - fitting: _not stated_
   - validation: _not stated_
3. **Fix geometric parameters**: PA from kpvslice; inclination from ellipse fit to DSS isophotes; kinematic centre from B6 continuum peak  
  > "The inclination ($i$) of the disc is estimated by using the DSS image of NGC 5135 (see Figure [7]) and matching the isophotal contours of the outer disc with an ellipsis." (4 3DBAROLO)
   - software: kpvslice, Karma
   - parameter: PA ~10 (+5/-10) deg; i = 57 +/- 2 deg; thin disk  
  > "This method provided an estimate of the inclination angle $i$=$57\pm 2$ deg" (4 3DBAROLO)
   - assumption: Thin disk, rotation-dominated kinematics, emission peak of B6 continuum coincident with AGN  
  > "assuming the emission peak of the B6 continuum coincident with the position of the AGN" (4 3DBAROLO)
   - fitting: _not stated_
   - validation: PA varied in 5 deg steps within error to test robustness  
  > "varying the PA by steps of 5$^{\circ}$ within the error, around the best-fit value" (4 3DBAROLO)
4. **Fit 3D tilted-ring model to CO(2-1) cube**: 3DBarolo chi-square-like minimisation with local and azim normalisations, within R_max = 4 arcsec  
  > "we have chosen a kind of $\chi^{2}$" (4 3DBAROLO)
   - software: 3DBarolo
   - parameter: Rmax = 4 arcsec (~1.167 kpc); 52 channels of 10 km/s shown  
  > "seven representative velocity channels (out of 52) of spectral resolution 10 km s$^{-1}$" (4.1)
   - fitting: Minimise Delta r = (M-D)^2/sqrt(D); no sampler or priors stated  
  > "then $^{\rm 3D}$`BAROLO` minimises the quantity:" (4 3DBAROLO)
   - validation: Compare local and azim solutions; compare moment maps and PV diagrams of model with data  
  > "the `local` model solutions must be compatible with those found by the `azim` one." (4 3DBAROLO)

## Software

- **CASA** 4.2.2 (pipeline), 4.7.1 (concatenation): Calibration, concatenation, cleaning, viewer for regions  
  > "The data available in the archive were calibrated using the ALMA calibration pipeline using CASA version 4.2.2." (3 The ALMA (archival) data)
- **3DBarolo** v1.3: Tilted-ring kinematic modelling of CO(2-1) cube  
  > "In the $^{\rm 3D}$`BAROLO` version used in this work (v1.3)" (4 3DBAROLO)
- **kpvslice (Karma)** : Estimating position angle of major axis  
  > "By using the code kpvslice, an extension of the Karma software" (4 3DBAROLO)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inclination | 57 | 2 | deg | 3 | This method provided an estimate of the inclination angle $i$=$57\pm 2$ deg |
| Position angle | 10 | +5/-10 | deg | 3 | we found $\phi \sim10^{+5}_{-10}$ deg |
| B6 continuum rms | 1.9e-5 | not stated | Jy/beam | 1 | the 1$\sigma$ RMS is 1.9$\times$ $10^{-5}$ Jy beam$^{-1}$ |
| CO(2-1) rotation velocity rise | 20 to ~50 at ~1 kpc | not stated | km/s | 4 | passing from 20 km s$^{-1}$ to $\sim$50 km s$^{-1}$ at $\sim$1 kpc from the centre |
| Velocity dispersion | ~20 to 30 | not stated | km/s | 4 | passing from $\simeq$20 to 30 km s$^{-1}$ |
| Radial velocity (inflow) | ~-30 | not stated | km/s | 4 | keeps almost constant, at around $-$30 km s$^{-1}$ |
| CS(5-4) flux density of region E | 0.29 | 0.03 | Jy/beam | 2 | flux density $\sim$0.29$\pm$0.03 Jy/beam |

## Qualitative findings

- Gas inflow toward the nucleus through spiral arms and bar, superimposed on disk rotation  
  > "discovery of radial motions overimposed to the galaxy disk rotation, with clear evidence of them consisting of gas inflow towards the nucleus" (Conclusions)
- AGN region unresolved in continuum, not detected in CO  
  > "while do not detected any CO emission, in agreement with the AGN being heavily obscured" (Conclusions)

## Claim tuples

- H: Can a rotating disk plus radial motion model explain the inner CO(2-1) kinematics? | E: 3DBarolo tilted-ring fit with local and azim normalisations | R: Models reproduce velocity field and most of the structure; not regions F and H or the dispersion map | F: Overall structure is rotation plus inflow, with non-axisymmetric exceptions | **partially**
- H: What is the origin of the two-velocity region F? | E: Examine channel maps, spectra, PV minor axis | R: Empty cavity bounded by +/-70 km/s blobs | F: Possible expanding super-bubble | **partially**
- H: Does the nuclear mm flux match torus-only SED expectations? | E: Compare B6 and B9 flux of region A with SED decomposition | R: Flux exceeds torus-only expectation by about two orders of magnitude | F: Upper limit to torus; possible contamination from SF or colder dust | **partially**

## Reasoning

- Why this data: Archival ALMA B6 and B9 data available for this Seyfert galaxy  
  > "For one of these Seyfert galaxies, NGC 5135, ALMA data were available in the archive in two bands" (Introduction)
- Why this method: _not stated_
- Alternative: SNR and AGN outflow origins for region F were discarded  
  > "Hence the SNR origin hypothesis is likely to be discarded for no clear evidence of the presence of the remnant." (5 The possible origins)
- How they decided it was enough: _not stated_
- Limitation (authors): B9 maximum recoverable scale is small, so fluxes between bands are not comparable  
  > "any direct comparison between the fluxes measured in the two bands will not be possible" (3 The ALMA (archival) data)
- Limitation (authors): Bar-induced non-circular motions are not fully reconstructed  
  > "the presence of the nuclear bar at the centre of NGC 5135 introduces motions in the innermost gas that the $^{3D}$`BAROLO` software is unable to reconstruct perfectly" (4.1)
- Caveat (inferred, ours): Inclination from a DSS outer-disc ellipse may not apply to the inner gas disk
- Caveat (inferred, ours): Thin-disk, axisymmetric assumption in a barred region
- Caveat (inferred, ours): Super-bubble interpretation is qualitative, with no quantitative energetics
- Caveat (inferred, ours): Region fluxes are not tabulated

## Reproducibility

- Data public (paper): Archival ALMA data  
  > "based on the analysis of Atacama Large Millimeter Array (ALMA) archival data" (abstract)
- Products in archive: _not stated_
- Missing: 3DBarolo parameter file
- Missing: Imaging parameters beyond robust
- Missing: Line-free channels
- Missing: Region definitions and fluxes
- Data volume (inferred): ~100-300 GB raw across both projects
- Score (inferred): 3/5, Public data and a named code, but many imaging and fitting parameters are missing and results are mostly qualitative.
- Rediscovery candidate: no, Recipe is incomplete and main results are mostly qualitative.

## Links

- Method: (cite: diteodoro2015) (3DBarolo tilted-ring code)
- Companion: (cite: gruppioni2016) (Seyfert SED decomposition sample)
- Related: 12 micron galaxy sample (12MGS)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
