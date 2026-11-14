# A Gap with a Deficit of Large Grains in the Protoplanetary Disk around TW Hya

`2016ApJ...829L..35T` | The Astrophysical Journal Letters 2016 | first author: Tsukagoshi, Takashi | arXiv: 1605.00289 | DOI: 10.3847/2041-8205/829/2/L35

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What is the dust continuum structure (gaps, rings) and the radial profile of spectral index and dust opacity index beta in the TW Hya disk at ~3 au resolution, and what do they imply for the gap origin?  
  > "we report multi-frequency observations of the disk around TW Hya with ALMA to probe the detailed disk structure and the change of dust spectral index across the dust gaps and rings" (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance ~54 pc  
  > "TW Hya is a 0.8 $M_\ensuremath{\odot}$ T Tauri star surrounded by a disk at a distance of $\sim$54 pc (cite: bib:andrews2012)." (Introduction); "Since the disk is almost face-on with an inclination angle of $7\ensuremath{^\circ}$ (cite: bib:qi2004)" (Introduction); distance from Andrews et al. 2012 (cite: bib:andrews2012)  
  > "TW Hya is a 0.8 $M_\ensuremath{\odot}$ T Tauri star surrounded by a disk at a distance of $\sim$54 pc (cite: bib:andrews2012)." (Introduction); "Since the disk is almost face-on with an inclination angle of $7\ensuremath{^\circ}$ (cite: bib:qi2004)" (Introduction)

## Data provenance

- ALMA projects: 2015.A.00005.S, 2012.1.00422.S
- bands: Band 4 (145 GHz) and Band 6 (233 GHz)  
  > "High-resolution continuum observations at bands 4 and 6 (145 and 233 GHz) with ALMA were carried out on 2015 December 1 and 2 (2015.A.00005.S)." (2 Observations)
- frequencies and spectral setup: TDM, 4 spectral windows of 1.875 GHz each, 7.5 GHz total per band  
  > "The correlator was configured to detect dual polarizations in 4 spectral windows with a bandwidth of 1.875 GHz each, resulting in a total bandwidth of 7.5 GHz for each observed band." (2 Observations)
- continuum bandwidth: 7.5 GHz per band  
  > "resulting in a total bandwidth of 7.5 GHz for each observed band" (2 Observations)
- arrays: 36 12-m antennas  
  > "36 of the 12-m antennas were operational" (2 Observations)
- configurations: in transition from C36-7 to C36-1  
  > "the antenna configuration was in transition from C36-7 to C36-1" (2 Observations)
- baselines: max 6.5 km (Band 4), 10.4 km (Band 6)  
  > "resulting in maximum baselines of 6.5 and 10.4 km for band 4 and 6, respectively" (2 Observations)
- angular resolution: 88.1x62.1 mas (B4), 75.4x55.2 mas (B6), 72.7x47.8 mas (MFS)  
  > "The spatial resolutions of the final images are 88.1$\times$62.1 mas with a position angle (PA) of $57.8\ensuremath{^\circ}$ and 75.4$\times$55.2 mas" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: 12.4 (B4), 28.7 (B6), 15.9 (MFS) uJy/beam  
  > "The noise levels of the band 4 and 6 images are 12.4 and 28.7 $\mu$Jy beam$^{-1}$, respectively." (2 Observations)
- time on source: _not stated_
- observing dates: 2015 December 1 and 2  
  > "were carried out on 2015 December 1 and 2 (2015.A.00005.S)" (2 Observations)
- pi or archival as stated: _not stated_
- External data: Band 7 high-resolution (~1 au) ALMA results used for comparison  
  > "These observed features agree with those found by recent high-resolution ($\sim$1 au) observations at band 7 (cite: bib:andrews2016)." (3 Results) [from (cite: bib:andrews2016)]
- External data: Archival Band 6 short-baseline data 2012.1.00422.S  
  > "We have combined band 6 archival data (2012.1.00422.S)" (2 Observations) [from not stated]
- External data: Dust mass opacity theory for interpreting small beta  
  > "according to the theoretical calculation of dust mass opacity (cite: bib:draine2006)" (4.1) [from (cite: bib:draine2006)]

## Processing

### Calibration

- pipeline or manual: CASA reduction with flagging, bandpass, gain and flux scaling  
  > "After flagging bad data and applying the calibrations for bandpass, complex gain, and flux scaling, the corrected visibilities were imaged by the CLEAN algorithm." (2 Observations)
- casa version: CASA 4.5.0  
  > "using the Common Astronomical Software Application (CASA) package, version 4.5.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1037-2934 for absolute flux calibration  
  > "J1037-2934 was used for absolute flux calibration" (2 Observations)
- flux scale uncertainty: assumed ~10%  
  > "If the accuracy of the absolute flux scale is assumed to be $\sim10$%" (3 Results)
- self calibration: iterative, solint 600 to 90 s (B4), 1200 to 240 s (B6)  
  > "The interval time to solve the complex gain was varied from 600 to 90 sec for band 4 and from 1200 to 240 sec for band 6." (2 Observations)

### Imaging

- task: CLEAN  
  > "the corrected visibilities were imaged by the CLEAN algorithm" (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 (B4), 1.0 (B6), 0.0 (MFS)  
  > "briggs weighting of robust parameters 0.5 and 1.0 for band 4 and 6, respectively" (2 Observations); "Briggs weighting with robust=0.0 was employed for the deconvolution" (2 Observations)
- uv taper: Band 6 visibilities with uv >3000 klambda flagged  
  > "The visibilities at band 6 with uv lengths $>$3000 k$\lambda$ were flagged out because of significant phase noise." (2 Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0,100,300] mas (B4), [0,50,150] mas (B6), [0,60,180] mas (MFS)  
  > "multiscale clean with scale parameters of \[0, 100, 300\] and \[0, 50, 150\] mas for band 4 and 6, respectively" (2 Observations)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Band 6 combined with archival short-baseline Band 6 after phase shift; B4 long baselines only  
  > "There were no available short-baseline data at band 4, hence only the long-baseline data were used for imaging." (2 Observations)
- smoothing: _not stated_
- final beam: 72.7x47.8 mas, PA 52.9 deg (MFS)  
  > "The achieved spatial resolution of the combined image is $72.7\times47.8$ mas, with a PA of $52.9\ensuremath{^\circ}$" (2 Observations)
- final rms: 12.4, 28.7, 15.9 uJy/beam  
  > "The noise level is 15.9 $\mu$Jy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- Temperature profile assumption based on earlier fits  
  > "This assumption is based on our fitting to the temperature profile at the disk midplane in (cite: bib:andrews2012) and (cite: bib:andrews2016)." (4.1) [from (cite: bib:andrews2012); (cite: bib:andrews2016)]
- Multi-frequency synthesis method  
  > "we also used the multi-frequency synthesis (MFS) method using all of the corrected visibilities after the iterative self-calibration imaging (cite: bib:rau2011)" (2 Observations) [from (cite: bib:rau2011)]
- Inclination 7 deg  
  > "the disk is almost face-on with an inclination angle of $7\ensuremath{^\circ}$ (cite: bib:qi2004)" (Introduction) [from (cite: bib:qi2004)]
- Gap-shape to planet-mass relation  
  > "Using the relationship that connects the gap shape with the planet mass (cite: bib:kanagawa2015; bib:kanagawa2016)" (4.2) [from (cite: bib:kanagawa2015; bib:kanagawa2016)]

### Not stated but needed to reproduce (our reading)

- Disk center, position angle for deprojection and radial bin widths
- Line-free channel selection and flagging details
- Number of self-calibration iterations and clean thresholds/masks
- Flux model for J1037-2934 and flux scale details
- How the alpha map was made in CASA (Taylor terms nterms)
- Procedure for solving tau and beta from I and alpha (grid, error propagation)
- Reference frequencies for Band 4 and 6 images
- Proper-motion shift values

## Analysis recipe

1. **Calibrate and combine visibilities**: CASA calibration; combine archival B6 short baselines with new B6 after phase shift; flag B6 uv>3000 klambda  
  > "after applying a phase shift to account for proper motion and different input phase centers" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Self-calibrate and image each band**: Iterative self-calibration using the initial CLEAN image as model; multiscale CLEAN with Briggs weighting  
  > "we performed the iterative self-calibration imaging for each band data using the initial CLEAN image as a model image" (2 Observations)
   - software: CASA
   - parameter: robust 0.5/1.0; scales [0,100,300]/[0,50,150] mas  
  > "We also employed the multiscale clean with scale parameters of \[0, 100, 300\] and \[0, 50, 150\] mas for band 4 and 6, respectively" (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make combined MFS image and alpha map**: MFS imaging of all self-calibrated data at 190 GHz, robust=0, scales 0,60,180 mas  
  > "Using the MFS method, we obtain the combined image and the map of the spectral index at 190 GHz." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: CASA uncertainty map for alpha is lower than the azimuthal standard deviation  
  > "the uncertainty map for $\alpha$ produced by CASA shows an error is lower than the standard deviation" (3 Results)
4. **Derive deprojected radial profiles of brightness temperature and alpha**: Deprojected azimuthal averaging; flux converted to Tb with Planck function; errors from azimuthal standard deviation  
  > "The error bars in figure [2](#fig:radp) are determined from the standard deviation determined by the azimuthal averaging." (3 Results)
   - assumption: Disk inclination 7 deg  
  > "inclination angle of $7\ensuremath{^\circ}$ (cite: bib:qi2004)" (Introduction)
   - fitting: _not stated_
   - validation: Comparison with Band 7 profiles of Andrews et al. 2016  
  > "These observed features agree with those found by recent high-resolution ($\sim$1 au) observations at band 7 (cite: bib:andrews2016)." (3 Results)
5. **Derive tau(R) and beta(R)**: Solve I_nu = B_nu(Td)(1-exp(-tau)) and alpha equation with tau_nu ∝ nu^beta given assumed Td(R)  
  > "If we assume one of them, we are able to derive the rest of them by using the observation data of $I_\nu (R)$ and $\alpha (R)$." (4.1)
   - parameter: T10 22-30 K, q 0.3-0.5  
  > "We vary $T_{10}$ from 22 to 30 K and $q$ from 0.3 to 0.5" (4.1)
   - assumption: Td = T10 (R/10 au)^-q, smooth  
  > "Here, we assume that $T_d (R)$ is given by $T_d (R) = T_{10} (R/10~\mathrm{AU})^{-q}$." (4.1)
   - fitting: _not stated_
   - validation: Conclusions insensitive to temperature profile choice  
  > "The assumed temperature profiles, however, have no great impact on the following conclusions as shown in figure [3](#fig:tau-beta)." (4.1)
6. **Estimate planet mass from gap**: Kanagawa et al. gap shape-planet mass relation  
  > "a planet with 1.5 $M_\mathrm{Neptune}$ may be responsible for the gap, assuming a viscosity parameter $\alpha=10^{-3}$ and a disk aspect ratio of 0.05" (4.2)
   - assumption: viscosity alpha=1e-3, aspect ratio 0.05  
  > "assuming a viscosity parameter $\alpha=10^{-3}$ and a disk aspect ratio of 0.05" (4.2)
   - fitting: _not stated_
   - validation: Similar values from gap width and depth  
  > "We note that similar values are derived from both gap width and depth." (4.2)

## Software

- **CASA** 4.5.0: Calibration, CLEAN imaging, self-calibration, MFS and spectral index map  
  > "The visibility data were reduced and calibrated using the Common Astronomical Software Application (CASA) package, version 4.5.0." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gap locations (deep) | 22 and 37 | not stated | au | 4 | There are two prominent gaps at 22 and 37 au, and relatively weak decrements are also seen at 6, 28, and 44 au. |
| 22 au gap FWHM and relative depth | 7 au, 50% | not stated | au, % | 4 | The full width at half maximum and the relative depth are roughly 7 au and 50 % for the 22 au gap |
| Total flux density Band 4 | 152.0 | 0.3 | mJy | 2 | The total flux densities are 152.0$\pm$0.3 and 558.3$\pm$0.7 Jy for band 4 and 6, respectively. |
| Total flux density Band 6 | 558.3 | 0.7 | mJy | 2 | The total flux densities are 152.0$\pm$0.3 and 558.3$\pm$0.7 Jy for band 4 and 6, respectively. |
| Total flux density at 190 GHz (SN>10) | 360.3 | 0.5 | mJy | 3 | 360.3$\pm$0.5 mJy at 190 GHz |
| Mean spectral index | 2.42 | 0.42 | dimensionless | 4 | the weighted mean value is estimated to be $<\alpha>=2.42\pm0.42$ |
| Peak alpha at 22 au | ~3.0 | not stated | dimensionless | 4 | There is a prominent peak around 22 au with $\alpha\sim3.0$ |
| beta at 22 au gap | ~1.7 | not stated | dimensionless | 5 | The derived power-law index of the dust opacity $\beta (R)$ is $\sim1.7$ at the 22 au gap and decreases toward the disk center to $\sim0$. |
| Planet mass upper limit | 1.5 | not stated | M_Neptune | 6 | a planet with 1.5 $M_\mathrm{Neptune}$ may be responsible for the gap |
| Inner hole radius | ~3 | not stated | au | 3 | we have resolved an inner hole with radius $\sim3$ au |

## Qualitative findings

- Disk is optically thin at R>15 au and marginally optically thick at R<15 au  
  > "The disk is optically thin at $R>15$ au in all the cases and marginally optically thick at $R<$15 au." (4.1)

## Claim tuples

- H: Does the 22 au gap show a deficit of large grains? | E: Spectral index map between Bands 4 and 6 converted to beta(R) | R: alpha peaks ~3.0 and beta ~1.7 at 22 au, decreasing to ~0 inward | F: Deficit of mm-sized grains in the gap, consistent with dust filtration by a planet | **supported**
- H: Are the multiple gaps of Andrews et al. confirmed at Bands 4 and 6? | E: ~3 au imaging at 145 and 233 GHz | R: Gaps at 22, 37 au and weaker at 6, 28, 44 au; inner hole ~3 au marginally resolved | F: Confirms the gap structure | **supported**
- H: Is a planet the cause of the 22 au gap? | E: Gap shape-mass relation with alpha=1e-3, h/r=0.05 | R: <=1.5 M_Neptune | F: Planet plausible, though other origins may be possible; snow line model fails to explain beta enhancement | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Spectral index across bands gives dust size information at resolution comparable to Band 7 results  
  > "additional information on the dust size distribution with comparable spatial resolution is required to address the physical structure of the gap" (Introduction)
- Alternative: Snow line sintering model (Okuzumi) does not predict strong beta variation; other instabilities possible  
  > "the model of (cite: bib:okuzumi2016) does not predict a strong radial variation of $\beta (R)$" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Results depend on assumed smooth temperature profiles; more bands needed  
  > "The discussions of $\tau_\mathrm{190GHz} (R)$ and $\beta (R)$ presented here are based on the assumptions of smooth temperature profiles." (4.1)
- Limitation (authors): Planet mass is an upper limit  
  > "This planet mass should be considered as the upper limit" (4.2)
- Caveat (inferred, ours): beta derived from two bands with assumed Td; degenerate with optical depth
- Caveat (inferred, ours): Absolute flux scale uncertainty (10%) shifts alpha by ~0.4
- Caveat (inferred, ours): Optically thick inner region makes beta unreliable
- Caveat (inferred, ours): Only the gap at 22 au has clear beta evidence

## Reproducibility

- Data public (paper): Both datasets are ALMA data with project codes; archival Band 6 explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.A.00005.S and ADS/JAO.ALMA#2012.1.00422.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Deprojection geometry and radial binning
- Missing: Self-calibration iteration details and masks
- Missing: Exact procedure for tau/beta solution and error ranges
- Missing: Flux calibrator flux model
- Data volume (inferred): ~200-500 GB raw for long-baseline Band 4/6 plus archival
- Score (inferred): 3/5, Data public and imaging parameters mostly given, but geometry, self-cal and inversion details missing.
- Rediscovery candidate: yes, Public data, fairly complete imaging recipe, numeric results (alpha, beta, gap positions).

## Links

- Method: (cite: bib:rau2011) (Multi-frequency synthesis imaging)
- Companion: (cite: bib:andrews2016) (Band 7 ~1 au imaging of TW Hya gaps)
- Companion: (cite: bib:nomura2016) (Earlier gap in TW Hya consistent with super-Neptune)

## Checks

```json
{
 "quotes": 72,
 "quotes_ok": 72,
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
  "facts": 78,
  "stated": 53,
  "rate": 0.679
 },
 "evidence_ok": true
}
```
