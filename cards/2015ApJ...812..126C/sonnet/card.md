# A Compact Concentration of Large Grains in the HD 142527 Protoplanetary Dust Trap

`2015ApJ...812..126C` | The Astrophysical Journal 2015 | first author: Casassus, Simon | arXiv: 1505.07743 | DOI: 10.1088/0004-637X/812/2/126

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do multi-frequency (34-700 GHz) observations of HD 142527 show size-segregated dust trapping, with larger grains more compactly concentrated than mm grains and gas?  
  > "A testable prediction of azimuthal dust trapping is that progressively larger grains should be more sharply confined and furthermore the trapped grains should follow a distribution that is markedly different from the gas." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance ~140 pc  
  > "HD 142527, at $\sim$140 pc, is a promising laboratory to observe on-going gas giant planet formation" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00465.S, 2011.0.00318.S
- bands: ALMA Band 9 (700 GHz, ~0.43 mm) new; Band 7 (345 GHz) archival; ATCA 34 GHz (8.8 mm)  
  > "obtained at 700 GHz (ALMA band 9; wavelengths of $\sim$0.43 mm" (Introduction)
- frequencies and spectral setup: Band 9: four spectral windows, 1875 MHz bandwidth, 488.28125 kHz channels, targeting CO(6-5), HCO+(8-7), H13CO+(8-7), HCN(8-7)  
  > "The ALMA correlator provided 1875 MHz bandwidth in four different spectral windows at 488.28125 kHz resolution" (6.1 ALMA band 9 observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m (20 antennas, one flagged); ATCA with maximum baselines to 6 km  
  > "The number of 12 m antennas available at the time of the observation was 20" (6.1 ALMA band 9 observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 9 beam 0.25''; ATCA 34 GHz beam 0.64''x0.30''  
  > "is resolved with a beam size of 0.25$''$" (2 An optically thick sub-mm continuum); "with a $0.64\ensuremath{''}\times0.30$$''$ beam" (3.1)
- max recoverable scale: _not stated_
- sensitivity: ATCA thermal noise 10 uJy/beam  
  > "while the thermal noise is at 10 $\mu$Jy beam$^{-1}$" (7 Monte-Carlo tests)
- time on source: Band 9: 43 min (June 3) and 49 min (June 4)  
  > "the total time on source for HD 142527 was 43 min on June 3, and 49 min on June 4" (6.1 ALMA band 9 observations)
- observing dates: Band 9: 3-4 June 2012; ATCA: May 2010, June 2010, July 2013, August 2013; Band 7 block 10-Aug-2012  
  > "in May 2010 (6A), June 2010 (6C), July 2013 (6A) and August 2013 (H168)" (6.2 ATCA data)
- pi or archival as stated: _not stated_
- Line: CO 6-5 (691.47308 GHz)
- Other facility **ATCA**: New 34 GHz (33/35 GHz) continuum data  
  > "We centred each sidebands at 19/21, 23/25, 33/35 and 41/43 GHz (in this work we focus on the 33/35 dataset)." (6.2 ATCA data)
- Other facility **Herschel SPIRE**: Flux density at 345 GHz (13.7 Jy) used for the absolute flux scale  
  > "The *Herschel* SPIRE flux density (cite: vanderwiel2014MNRAS.444.3911V) at the same frequency is 13.7 Jy." (9 Absolute flux scale)
- External data: ALMA Band 7 data (2011.0.00318.S) of HD 142527  
  > "we used the dataset acquired by Fukagawa et al. (cite: 2013PASJ...65L..14F)" (6.3) [from Fukagawa et al. 2013 (cite: 2013PASJ...65L..14F)]
- External data: Band 6 250 GHz data giving alpha_b6^b7 ~ 2.7  
  > "the band 6 ALMA data at 250 GHz (cite: Perez2015ApJ...798...85P) yields $\alpha_{b6}^{b7} \sim 2.7$" (9 Absolute flux scale) [from Perez et al. 2015 (cite: Perez2015ApJ...798...85P)]
- External data: Herschel SPIRE flux density of 13.7 Jy  
  > "The *Herschel* SPIRE flux density (cite: vanderwiel2014MNRAS.444.3911V) at the same frequency is 13.7 Jy." (9 Absolute flux scale) [from van der Wiel et al. 2014 (cite: vanderwiel2014MNRAS.444.3911V)]
- Simulation/model as data: RADMC3D synthetic dust trap model with tilted inner disk, passive heating, used to test grey-body biases  
  > "We used RADMC3D (cite: RADMC3D0.39) to transfer the stellar radiation through the synthetic disk and predict emergent intensity maps, under the assumption of passive heating." (10 Synthetic dust trap model)

## Processing

### Calibration

- pipeline or manual: ATCA reduced with Miriad and CASA; ALMA calibration pipeline not stated  
  > "All subsequent data reduction and calibration was performed with the Miriad software" (6.2 ATCA data)
- casa version: CASA 4.2.2 (ATCA concat/self-cal)  
  > "concatenated with the task `concat` from `CASA` (cite: CASA) version 4.2.2" (6.2 ATCA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 9: Titan primary, 3C279 bandpass, J1517-243 phase; ATCA: 1934-638 flux, 1253-055 bandpass, 1600-44 gain  
  > "The primary flux calibrator was Titan, while 3C279 was used as bandpass calibrator." (6.1 ALMA band 9 observations); "the quasar 1934-638" (6.2 ATCA data)
- flux scale uncertainty: Band 7 flux densities vary by up to 50% between programs; J1517-243 0.70±0.14 Jy at 702 GHz  
  > "the flux densities reported for different ALMA programs in band 7 vary by up to 50%" (9 Absolute flux scale)
- self calibration: Band 9: antenna-based phase self-cal; ATCA Ka: phase self-cal with 30 min solint, both spectral windows combined  
  > "We used a solution interval of 30 min and combined both spectral windows for sensitivity." (6.2 ATCA data)

### Imaging

- task: Custom uvmem (MEM-like least-squares) plus CASA clean for comparison  
  > "We call this tool `uvmem`." (6.4 Image synthesis)
- deconvolver: _not stated_
- weighting robust: natural weights  
  > "In this work we used natural weights." (6.4 Image synthesis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: ATCA 6 km data from several configurations concatenated; ALMA datasets brought to common uv coverage using uvsim  
  > "We then compute synthetic interferometer data corresponding to the more compact $uv-$coverage using our tool ` uvsim`." (6.5 Alignment)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Image synthesis technique (uvmem)  
  > "For image synthesis we use a non-parametric least-squares modeling technique (cite: 2006ApJ...639..951C)" (6.4 Image synthesis) [from Casassus et al. 2006 (cite: 2006ApJ...639..951C)]
- Band 7 program 2011.0.00465.S data previously presented, astrometry tied to it  
  > "tied the astrometric pointing to the data previously presented by Casassus et al. (cite: Casassus2013Natur)" (6.3) [from Casassus et al. 2013 (cite: Casassus2013Natur)]
- Synthetic model builds on the warped-disk model of scattered-light shadows  
  > "is a perfected version of that which accounts for the scattered-light shadows (cite: Marino2015ApJ...798L..44M), with a tilted inner disk" (10) [from Marino et al. 2015 (cite: Marino2015ApJ...798L..44M)]
- Radial trap and azimuthal trapping prescriptions  
  > "we used the radial trap model from (cite: Pinilla2012A&A...538A.114P) coupled with the prescriptions for azimuthal trapping from (cite: Birnstiel2013A&A...550L...8B)" (10) [from Pinilla et al. 2012; Birnstiel et al. 2013]

### Not stated but needed to reproduce (our reading)

- Band 9 CASA version and calibration procedure details
- Line-free channels and continuum bandwidth used for Band 9 continuum
- Self-calibration solution intervals for Band 9
- uvmem regularisation and entropy weight; uvmem/uvsim/uvreweight code availability
- Pixel size, image size and clean parameters
- ATCA flux and Band 7 scheduling-block flux scaling details
- Full model parameter table for the RADMC3D disk (stellar parameters, inner disk tilt, opacities)
- Coordinates of target

## Analysis recipe

1. **Reweight visibilities**: Scale weights to 1/sigma^2 using single median scale factor (uvreweight)  
  > "we therefore scaled the weights so that they correspond to 1/$\sigma^2$" (6.4 Image synthesis)
   - software: uvreweight
   - fitting: _not stated_
   - validation: _not stated_
2. **Align multi-frequency datasets**: Cross-correlate visibilities at common uv coverage over a grid of WCS shifts; centroid of elliptical fit to chi2 image  
  > "The best WCS shift is given by the centroid $\vec{\delta}_\circ$ of an elliptical fit to $\chi^2(\{\vec{\delta}_i\})$." (6.5)
   - software: uvmem, uvsim
   - fitting: _not stated_
   - validation: Offset of 0.065 arcsec found between band 7 blocks  
  > "we measured an offset of 0.065 arcsec between this scheduling block and the single scheduling block in band 7" (6.3)
3. **Spectral index maps**: Power-law fit per pixel to restored uvmem images (band 7 SPWs and band 7/band 9)  
  > "we extract a spectral index map by fitting the restored specific intensity maps with a power-law" (6.6)
   - software: uvmem
   - assumption: Flux scale C13scale: 3.5 Jy at 345 GHz band 7, SPIRE for band 9  
  > "we adopted a reference band 7 flux density of 3.5 Jy at 345 GHz, and took the SPIRE flux density for band 9" (9)
   - fitting: _not stated_
   - validation: Compared with alternative SEDscale flux scale  
  > "All morphological trends are similar in both flux scales" (9)
4. **Grey-body optical depth, temperature and beta maps**: Fit uniform slab I=B(T)[1-exp(-tau)] per pixel to three frequency points  
  > "We fit the observations with the intensities emergent from a uniform slab" (2)
   - parameter: Constant beta_S = 1.5 for ALMA-only fit  
  > "despite the use of a constant emissivity law $\beta_S(\vec{x}) = 1.5$" (11)
   - fitting: beta uncertainties from varying ATCA intensities by ±1 sigma of dirty residual scatter  
  > "estimated by varying the ATCA intensities by $\pm 1\sigma$" (11)
   - validation: Applied same diagnostic to synthetic RADMC3D model  
  > "We also applied the line-of-sight diagnostic based on grey-body models to the synthetic emergent intensities." (12)
5. **Monte-Carlo test of ATCA uv filtering**: Simulate ATCA observations of deconvolved band 7/9 models with ATCA uv coverage and noise, 200 realisations  
  > "We repeat this procedure 200 times before taking statistics." (7)
   - software: uvmem, uvsim
   - fitting: _not stated_
   - validation: Reduced chi2 4.2 (band 7), 4.9 (band 9)  
  > "is 4.2 for band 7, and 4.9 for band 9" (7)
6. **Dust mass in 11.5h clump**: Optically thin flux to mass, single 1 cm grains, 20 K  
  > "corresponds to $>$7.4 M$_\oplus$ of dust" (3.1)
   - assumption: 1 cm grains, circular cross section, 20 K, fiducial density of water  
  > "For the fiducial density of water, and for a single grain size of 1 cm with a circular cross section, at 20 K" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
7. **Synthetic dust trap radiative transfer**: RADMC3D passive heating with three dust species, size distribution exponent -3.5, trapping prescriptions; ATCA response simulated with 100 uvmem reconstructions  
  > "averaged 100 `uvmem` reconstructions with different realizations of noise" (10)
   - software: RADMC3D, uvmem
   - parameter: a_c = 0.7 cm at 133 AU; alpha_t = 1e-2; gas mass 0.25 Msun; contrast c=20  
  > "we obtain a critical grain size of 0.7 cm at 133 AU" (10)
   - assumption: Scattering switched off at sub-mm frequencies  
  > "We switched-off scattering for the purpose of calculating images at sub-mm frequencies and lower." (10)
   - fitting: _not stated_
   - validation: Predicted flux densities close to observed SED  
  > "the predicted integrated flux densities fall close to the observed dereddened SED" (10)

## Software

- **CASA** 4.2.2: concat, clean, gaincal, applycal for ATCA data; dirty maps of residuals  
  > "using the `clean` model and the `CASA` tasks `gaincal` and `applycal`" (6.2 ATCA data)
- **Miriad** : ATCA data reduction and calibration, uvedit proper motion correction  
  > "All subsequent data reduction and calibration was performed with the Miriad software" (6.2 ATCA data)
- **RADMC3D** 0.39: Radiative transfer of synthetic dust trap model  
  > "The synthetic model was implemented in RADMC3D (cite: RADMC3D0.39)" (4.1)
- **uvmem** : Maximum-entropy image synthesis and deconvolved models  
  > "We call this tool `uvmem`." (6.4 Image synthesis)
- **uvsim** : Synthetic visibilities at a given uv-coverage  
  > "using our tool ` uvsim`" (6.5)
- **uvreweight** : Rescaling visibility weights to observed scatter  
  > "This procedure was carried out using a tool we call `uvreweight`." (6.4 Image synthesis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak 34 GHz intensity at 11.5h | 147 | not stated | uJy/beam | 0 | The peak 34 GHz intensity at 11.5h reaches 147$\mu$Jy beam$^{-1}$ |
| Dust mass in unresolved 11.5h clump | >7.4 | not stated | Earth masses | 6 | corresponds to $>$7.4 M$_\oplus$ of dust |
| Stellar-position spectral index alpha_20^45 | 1.0 | 0.2 | dimensionless | 0 | $\alpha_{20}^{45} = 1.0 \pm 0.2$ |
| beta_S under 11.5h clump | 1.18 | 0.04 | dimensionless | 4 | corresponds to $\beta_S = 1.18 \pm 0.04$ |
| Mean beta_S outside clump | 1.50 | rms 0.07 | dimensionless | 4 | the average value outside the regions of low $\beta_S$ is 1.50, with a rms dispersion of 0.07 |
| Peak optical depth at 345 GHz | ~2.5 (C13scale), 0.7 (SEDscale) | not stated | dimensionless | 4 | dropping by about 2.5 in *C13scale* to 0.7 in *SEDscale* (at 345 GHz) |
| Critical grain size at 133 AU | 0.7 | not stated | cm | 7 | we obtain a critical grain size of 0.7 cm at 133 AU |

## Qualitative findings

- Band 7/9 crescent is optically thick; double-peaked band 9 morphology reflects temperature structure from shadows cast by the inner warp.  
  > "shadowing of UV-optical radiation by the central warp explains the temperature structure of the crescent" (Conclusion)

## Claim tuples

- H: Sub-mm spectral trends at ALMA frequencies reflect grain growth/trapping. | E: Grey-body fits to band 7 and band 9 | R: Optical depths ~1-2.5 at 345 GHz | F: Spectral trends are optical-depth effects; no trapping needed for grains up to 1 mm. | **supported**
- H: Larger grains are more compactly concentrated than mm grains. | E: ATCA 34 GHz imaging compared with ALMA, MC tests, beta map | R: 11.5h clump at 10 sigma, beta_S minimum 1.18, ~7 sigma | F: Compact concentration of ~cm-sized grains embedded in mm-grain crescent | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Brought datasets to common Fourier basis to avoid uv-filtering artefacts  
  > "thus bringing the multi-frequency data to an approximately common Fourier basis" (3.1)
- Alternative: Combining all band 7 scheduling blocks rejected due to pointing offsets and image-synthesis-limited dynamic range  
  > "The reason for not combining the whole dataset is because the dynamic range under the crescent is limited by image synthesis" (6.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux scale uncertain, affecting spectral index and optical depths  
  > "There are however substantial uncertainties on the observed SED." (9)
- Caveat (inferred, ours): Clump significance depends on ATCA uv coverage and the chosen flux scale
- Caveat (inferred, ours): Grey-body fits use three points and fixed beta, biased low by ~50% after ATCA filtering
- Caveat (inferred, ours): Custom undocumented tools (uvmem, uvsim, uvreweight) hamper reproducibility
- Caveat (inferred, ours): Grain size estimates depend on opacity model

## Reproducibility

- Data public (paper): ALMA programs referenced; ATCA data not stated as public  
  > "through programs `ALMA#2011.0.00465.S` and ` ALMA#2011.0.00318.S`" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom uvmem/uvsim/uvreweight code
- Missing: Band 9 calibration and self-cal details
- Missing: Complete RADMC3D model inputs
- Data volume (inferred): ~50-100 GB for ALMA raw data from two projects plus ATCA data
- Score (inferred): 3/5, ALMA data are archival but key tools are custom and many imaging/calibration parameters are unstated.
- Rediscovery candidate: no, Recipe relies on unreleased custom tools and unspecified parameters.

## Links

- Method: Casassus et al. 2006 (cite: 2006ApJ...639..951C) (uvmem image synthesis)
- Method: Birnstiel et al. 2013 (cite: Birnstiel2013A&A...550L...8B) (azimuthal trapping prescriptions)
- Method: Pinilla et al. 2012 (cite: Pinilla2012A&A...538A.114P) (radial trap model)
- Companion: Casassus et al. 2013 (cite: Casassus2013Natur) (Previous Band 7 crescent observations)
- Companion: Marino et al. 2015 (cite: Marino2015ApJ...798L..44M) (Warped inner disk shadow model)
- Companion: Fukagawa et al. 2013 (cite: 2013PASJ...65L..14F) (Band 7 dataset)

## Checks

```json
{
 "quotes": 71,
 "quotes_ok": 71,
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
  "facts": 88,
  "stated": 56,
  "rate": 0.636
 },
 "evidence_ok": true
}
```
