# Very Large Array Ammonia Observations of the HH 111/HH 121 Protostellar System: A Detection of a New Source with a Peculiar Chemistry

`2017ApJ...849...68S` | The Astrophysical Journal 2017 | first author: Sewiło, Marta | arXiv: 1709.04856 | DOI: 10.3847/1538-4357/aa8b18

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry
- Question: What are the kinematic, physical and chemical properties of HH 111 and the newly detected ammonia source NH3-S, and is NH3-S a starless core?  
  > "We study the kinematic and physical properties of HH 111 and the newly discovered NH$_{3}-$S." (abstract)
- Target **HH 111/HH 121 (NH3-Main and NH3-S)**: coordinates NH3-S: 5:51:46.579 +2:48:11.23 (J2000); NH3-Main: 5:51:46.045 +2:48:25.72  
  > "It is located in the L1617 dark cloud of the Orion B molecular cloud at a distance of 400 pc" (Introduction); z/distance 400 pc  
  > "It is located in the L1617 dark cloud of the Orion B molecular cloud at a distance of 400 pc" (Introduction); distance from e.g., sandstrom2007  
  > "It is located in the L1617 dark cloud of the Orion B molecular cloud at a distance of 400 pc" (Introduction)

## Data provenance

- ALMA projects: 2012.1.00013.S
- bands: Band 6  
  > "HH 111 was observed with ALMA in Band 6 as part of project 2012.1.00013.S, using both the 12m and 7m arrays." (2.3 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m and 7m  
  > "using both the 12m and 7m arrays" (2.3 ALMA)
- configurations: _not stated_
- baselines: 12m: 20-558 m; 7m: 9-49 m  
  > "using the 12m array with baselines from 20 to 558 m, for a total time on source of 144 minutes" (2.3 ALMA)
- angular resolution: 13CO 0.84x0.67 arcsec; C18O 0.84x0.72; N2D+ and 13CS 0.81x0.67  
  > "| $^{13}$CO | (2–1) | 220.39868 | 0.2 | 0.84 $\times$ 0.67, -79.3 |" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: 13CO 4.5, C18O 3.5, N2D+ 1.8, 13CS 1.1 mJy/beam  
  > "The noise levels in the final N$_{2}$D$^{+}$ and $^{13}$CS images are 1.8 and 1.1 mJy beam$^{-1}$, respectively." (2.3 ALMA)
- time on source: 12m: 144 min; 7m: 414 min  
  > "incorporating baselines from 9 to 49 m and a total of 414 minutes on source" (2.3 ALMA)
- observing dates: 12m: May 2014; 7m: Dec 2013 to Dec 2014  
  > "The project was executed three times in May 2014 using the 12m array" (2.3 ALMA)
- pi or archival as stated: archival  
  > "We also describe the analysis of the archival Atacama Large Millimeter/submm Array (ALMA) Band 6 data" (2.3 ALMA)
- Line: 13CO 2-1 (220.39868 GHz)
- Line: C18O 2-1 (219.56035 GHz)
- Line: N2D+ 3-2 (231.32183 GHz)
- Line: 13CS 5-4 (231.22069 GHz)
- Other facility **VLA**: NH3 (1,1) and (2,2) observations, primary data  
  > "The ammonia data were obtained with the ‘historical’ Very Large Array (VLA) of the National Radio Astronomy Observatory" (2.1 VLA)
- Other facility **JCMT**: HCO+ and HCN (4-3) maps  
  > "HCO$^{+}$ (4–3) and HCN (4–3) emission from the HH 111/HH 121 protostellar system was observed using the Heterodyne Array Receiver Program (HARP)" (2.2 JCMT)
- Other facility **Spitzer and Herschel**: archival IR images to check for embedded source  
  > "We use archival data from the *Spitzer* Space Telescope and the *Herschel* Space Observatory." (2.4)

## Processing

### Calibration

- pipeline or manual: Re-calibrated raw data with ALMA calibration pipeline  
  > "we retrieved the raw visibility data and calibrated them using the ALMA calibration pipeline included in the CASA 4.5.3 package" (2.3 ALMA)
- casa version: CASA 4.5.3  
  > "calibrated them using the ALMA calibration pipeline included in the CASA 4.5.3 package" (2.3 ALMA)
- pipeline version: _not stated_
- archive products used as is: No; raw data recalibrated for weighting  
  > "The calibration in the archive was performed with several different CASA versions as the data were taken" (2.3 ALMA)
- flux calibrator: Ganymede, Callisto, J0510+180 (12m); also Pallas, J0423-013 (7m)  
  > "Absolute flux calibration of the three executions was performed using Ganymede, J0510+180 (1.27 Jy at 220 GHz), and Callisto." (2.3 ALMA)
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
- continuum subtraction: uv-domain subtraction from each line spectral window  
  > "Continuum was subtracted in the uv domain from each line spectral window" (2.3 ALMA)
- line free channels: _not stated_
- primary beam correction: CASA impbcor  
  > "The data cubes were corrected for the primary beam attenuation using the CASA task `impbcor`." (2.3 ALMA)
- array combination: 7m and 12m imaged simultaneously, interactively deconvolved  
  > "the 7m and 12m data were simultaneously imaged and deconvolved interactively" (2.3 ALMA)
- smoothing: _not stated_
- final beam: 13CO 0.84x0.67 arcsec; C18O 0.84x0.72  
  > "Synthesized beams for $^{13}$CO and C$^{18}$O are 0$\rlap.{''}$84$\times$0$\rlap.{''}$67 and 0$\rlap.{''}$84$\times$0$\rlap.{''}$72, respectively." (2.3 ALMA)
- final rms: 4.5 mJy/beam (13CO), 3.5 (C18O), 15 mJy/beam fidelity floor for 13CO near line center  
  > "The noise levels in the images away from line center are 4.5 and 3.5 mJy beam$^{-1}$, respectively" (2.3 ALMA)

### Inherited from earlier work

- NH3 forward model (cold-ammonia) used for hyperfine fitting  
  > "using a forward model presented by Friesen & Pineda et al. (submitted)" (3.1.1) [from Friesen & Pineda et al. (submitted); friesen2017]
- ALMA C18O data and 1.3 mm continuum for HH 111 previously presented  
  > "The ALMA C$^{18}$O data for HH 111 were presented in (cite: lee2016)." (2.3 ALMA) [from (cite: lee2016)]

### Not stated but needed to reproduce (our reading)

- tclean/clean weighting, robust, cell and image size, and masks for the ALMA cubes
- line-free channels for continuum subtraction
- exact method for ALMA 1.3 mm continuum image and its rms
- how the 1.8 mJy/beam continuum rms was obtained
- velocity-averaging for the 0.2 and 0.7 km/s cubes

## Analysis recipe

1. **Calibrate and image ALMA 12m+7m line data**: Archive raw data recalibrated with pipeline, uv continuum subtraction, joint 7m+12m interactive imaging, impbcor  
  > "the 7m and 12m data were simultaneously imaged and deconvolved interactively" (2.3 ALMA)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit NH3 (1,1)+(2,2) hyperfine profiles per pixel**: Pixel-by-pixel forward-model fit of all hyperfine components for vLSR, sigma_v, Tkin, Tex, N(NH3), pixels with S/N>5  
  > "We fit the NH$_3$ line profiles on a pixel-by-pixel basis to construct the maps of physical parameters." (3.1.1)
   - software: pyspeckit
   - assumption: LTE ortho/para ratio of 1  
  > "We adopt the local thermodynamic equilibrium (LTE) value of 1 for the ortho- to para-NH$_3$ ratio." (3.1.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive core masses from NH3 and ALMA 1.3 mm upper limit**: NH3-based mass with X=1e-8; optically thin dust mass upper limit at 3x rms  
  > "we adopt 3$\times$ the image rms for $S_{1.3{\rm mm}}$ to calculate the mass upper limit" (3.1.3)
   - software: CASA imfit
   - assumption: X(NH3/H2)=1e-8, mu=2.8, Rgd=100, Ossenkopf & Henning dust opacity 0.899 cm2/g at 1.3 mm, Td=12.1 K, D=400 pc  
  > "Adopting a distance of 400 pc, the temperature of 12.1 K, and the flux density of 1.8 mJy beam$^{-1}$" (3.1.3)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit N2D+ spectra**: Single Gaussian fit of mean spectrum over 20% peak contour ellipse  
  > "We thus fitted the N$_{2}$D$^{+}$ lines with the single Gaussian profiles" (3.3 N2D+)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3 (ALMA pipeline): ALMA calibration, imaging, impbcor, imfit  
  > "calibrated them using the ALMA calibration pipeline included in the CASA 4.5.3 package" (2.3 ALMA)
- **AIPS** : VLA calibration  
  > "The data were calibrated using the Astronomical Image Processing System (AIPS) software package." (2.1 VLA)
- **pyspeckit** : cold-ammonia model for NH3 fitting  
  > "The model is implemented in the Python analysis toolkit `pyspeckit` as ‘cold-ammonia’" (3.1.1)
- **ORAC-DR** : JCMT data reduction  
  > "The data were reduced using the ORAC Data Reduction pipeline (`ORAC-DR`)" (2.2 JCMT)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NH3-S Tkin | 12.1 | 0.5 | K | 2 | / NH$_3-$S / 5:51:46.579 / $+$2:48:11.23 / 9.2 (0.1) / 0.018 / 12.1 (0.5) / 7.8 (0.3) / 5.5 (0.4) / 0.33 / |
| NH3-S N(NH3) | 5.5e14 | 0.4e14 | cm^-2 | 2 | / NH$_3-$S / 5:51:46.579 / $+$2:48:11.23 / 9.2 (0.1) / 0.018 / 12.1 (0.5) / 7.8 (0.3) / 5.5 (0.4) / 0.33 / |
| NH3-S mass (NH3) | 0.33 | factor 3-4 | Msun | 3 | we obtain the NH$_3-$S and NH$_3-$Main masses of 0.33 M$_{\odot}$ and 0.37 M$_{\odot}$, respectively |
| NH3-S clump mass upper limit from ALMA 1.3 mm | ~1.7 | not stated | Msun | 3 | which corresponds to $\sim$1.7 M$_{\odot}$ if we adopt a source size determined from the ammonia data |
| N2D+ vLSR NH3-S | 9.47 | 0.02 | km/s | 4 | / S / 9.47 $\pm$ 0.02 / 1.00 $\pm$ 0.04 / 0.30 $\pm$ 0.02 / 0.39 $\pm$ 0.01 / |
| mean non-thermal velocity dispersion NH3-S | 0.16 | 0.06 (std dev) | km/s | 2 | The mean values of $\sigma_{nth}$ are 0.16 km s$^{-1}$ and 0.14 km s$^{-1}$ for NH$_{3}-$S and NH$_{3}-$Main |
| virial parameter NH3-S | 2.5 | not stated | dimensionless | 3 | we derive the virial parameter $\alpha$ of 2.5 using $M_{{\rm vir}}$ of 0.75 M$_{\odot}$ |

## Qualitative findings

- CO isotopologues and 13CS are not detected at center of NH3-S while N2D+ peaks there, consistent with selective freeze-out  
  > "What is striking in Figs.  [10](#f:12co)–[12](#f:13COmom) is the lack of the C$^{18}$O, $^{12}$CO, and $^{13}$CO emission in the center of NH$_{3}-$S." (3.2)

## Claim tuples

- H: NH3-S is a starless dense core with selective freeze-out | E: Compared NH3, ALMA CO isotopologues, N2D+, 13CS and IR archival data | R: No CO or 13CS at center, N2D+ peaks at NH3 peak, no IR source | F: NH3-S is a starless core showing selective freeze-out | **supported**
- H: NH3-S is a coherent core with jet-induced turbulence at edges | E: Non-thermal velocity dispersion maps from NH3 | R: Subsonic inner motions increasing toward the jets | F: Coherent core in a turbulent medium | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: External UV illumination of NH3-S rejected because faint HCO+ detected  
  > "A detection of faint HCO$^{+}$ emission toward NH$_{3}-$S is not consistent with the predictions of theoretical models of external illumination by the strong ultraviolet radiation." (4.4 HCO+ and HCN)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot fully explain nature of NH3-S; virial state uncertain  
  > "Based on the currently available data, we cannot fully explain the nature of NH$_3-$S." (5 Summary)
- Caveat (inferred, ours): ALMA data used only qualitatively, no continuum detection
- Caveat (inferred, ours): Alfven wave interpretation speculative
- Caveat (inferred, ours): single-dish JCMT beam blends NH3-S with NH3-Main

## Reproducibility

- Data public (paper): ALMA archival data, project listed with ASDM UIDs in appendix  
  > "The complete list of ALMA Science Data Model (ASDM) UIDs used:" (Appendix A)
- Products in archive: _not stated_
- Missing: clean parameters for ALMA imaging
- Missing: VLA AIPS calibration details
- Missing: unpublished forward model (Friesen & Pineda submitted)
- Data volume (inferred): ~100-300 GB raw ALMA 12m+7m plus VLA data
- Score (inferred): 3/5, ALMA part is qualitative with limited imaging detail; VLA and model parts partly specified.
- Rediscovery candidate: no, ALMA role minor and imaging recipe incomplete; main results rely on VLA and an unpublished model.

## Links

- Method: Friesen & Pineda et al. (submitted); (cite: friesen2017) (NH3 forward model)
- Companion: (cite: lee2016) (previous ALMA C18O and continuum analysis of HH 111)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
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
  "facts": 70,
  "stated": 41,
  "rate": 0.586
 },
 "evidence_ok": true
}
```
