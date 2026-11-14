# A Three-dimensional View of Molecular Hydrogen in SN 1987A

`2019ApJ...873...15L` | The Astrophysical Journal 2019 | first author: Larsson, J. | arXiv: 1901.11235 | DOI: 10.3847/1538-4357/ab03d1

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, astrochemistry, other
- Question: What is the 3D morphology of H2 in the SN 1987A ejecta, how does it compare with H-alpha, ALMA CO, SiO and dust, and does it evolve with time?  
  > "We also compare the 3D distribution with the previous 3D maps of H$\alpha$, CO and SiO. Finally, we use our previous observations to study the time-evolution of H$_2$." (Introduction)
- Target **SN 1987A**: coordinates _not stated_; z/distance 51.2 kpc (LMC)  
  > "Throughout this paper we assume a distance to SN 1987A in the LMC of 51.2 kpc (cite: Panagia1991)" (Introduction); distance from Panagia1991  
  > "Throughout this paper we assume a distance to SN 1987A in the LMC of 51.2 kpc (cite: Panagia1991)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00063.S, 2013.1.00280.S, 2015.1.00631.S
- bands: Band 7 (dust, 311.9–319.5 GHz); Band 6 (CO 2–1, SiO 5–4)  
  > "| ALMA | Band 7 | dust (311.9–319.5 GHz) | 2015-06-28 – 2015-09-22 | 10,395 | 5 |" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Dust beam 0.19''x0.14'', PA 29 deg; CO/SiO ~0.05''  
  > "The beam size was 0.19$''$$\times$0.14$''$ with a position angle of $29^{\circ}$ in anti-clockwise direction from the north." (2.2 Other observations used for comparison)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: Dust: four 19 min observations in Band 7  
  > "The dust image from ALMA is based on four 19 min observations in Band 7" (2.2 Other observations used for comparison)
- observing dates: Band 7: 2015-06-28 – 2015-09-22; Band 6: 2014-09-02, 2015-11-02  
  > "| ALMA | Band 6 | CO 2–1, SiO 5–4 | 2014-09-02, 2015-11-02 | 10,053, 10,479 | 6 |" (Table 1)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- Line: SiO J=5-4 (not stated)
- Other facility **VLT/SINFONI**: K-band IFU observations of H2 2.12 and 2.41 um (main data)  
  > "The total exposure time in the K-band was 10,800 s." (2.1 SINFONI observations in 2017/2018)
- Other facility **HST WFC3/STIS**: H-alpha images and 3D maps  
  > "The HST/WFC3 image was obtained in the F625W filter using four $300\ \rm{s}$ dithered exposures." (2.2 Other observations used for comparison)
- External data: 3D maps of CO 2-1 and SiO 5-4 from ALMA Band 6  
  > "the ALMA/Band 6 observations were used to study molecular lines (CO 2–1 and SiO 5–4; (cite: Abellan2017))." (2.2 Other observations used for comparison) [from (cite: Abellan2017)]
- External data: Centre of ring/explosion and astrometry  
  > "the centre of the ring (determined by (cite: Alp2018)) coincides with the centre of the explosion." (Introduction) [from (cite: Alp2018)]

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
- continuum subtraction: Dust continuum image from narrow range around 315 GHz where no lines expected  
  > "The continuum image was constructed from a narrow frequency range around 315 GHz, where no lines are expected according to the spectral model in (cite: Matsuura2017)." (2.2 Other observations used for comparison)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- ALMA Band 7 data reduction details  
  > "The details of the observations and data reduction are described by P. Cigan et al. (in preparation)." (2.2 Other observations used for comparison) [from P. Cigan et al. (in preparation)]
- CO and SiO 3D maps  
  > "have been analyzed in previous works" (2.2 Other observations used for comparison) [from (cite: Abellan2017)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging parameters (weighting, cell, deconvolver, masks) for Band 7 dust image
- Calibration details and flux calibrator
- Line-free channel selection
- Processing of Band 6 CO/SiO cubes

## Analysis recipe

1. **Align ALMA data and compare with H2 contours/3D iso-surfaces**: ALMA aligned via absolute astrometry and SN position; compared 60% of max iso-surfaces and contours with H2  
  > "A comparison of iso-surfaces corresponding to 60$\%$ of max for CO, SiO and H$_2$ is shown in Fig. [6](#fig:alma_h2_3d)." (4.2 Comparison with ALMA observations of CO, SiO and dust)
   - software: Mayavi, CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare line widths**: Gaussian fits to integrated line profiles  
  > "As a crude estimate of the widths, we fit Gaussian lines" (4.2 Comparison with ALMA observations of CO, SiO and dust)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.1: Reduction of ALMA Band 7 data  
  > "The data were reduced with the Common Astronomy Software Application package (CASA[^2], (cite: McMullin2007)) version 4.5.1." (2.2 Other observations used for comparison)
- **Mayavi** : 3D visualization (listed in Software)  
  > "Mayavi (cite: Ramachandran2011)" (Software)
- **DrizzlePac** : Combining HST/WFC3 images  
  > "These were combined using DrizzlePac[^1]" (2.2 Other observations used for comparison)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| FWHM of CO line | 2470 | 40 | km/s | 2 | $\rm{FWHM_{CO}} = 2470 \pm 40$, $\rm{FWHM_{SiO}} = 3140 \pm 100$, and $\rm{FWHM_{H_2}} = 2100 \pm 80$ |
| FWHM of SiO line | 3140 | 100 | km/s | 2 | $\rm{FWHM_{CO}} = 2470 \pm 40$, $\rm{FWHM_{SiO}} = 3140 \pm 100$, and $\rm{FWHM_{H_2}} = 2100 \pm 80$ |
| FWHM of H2 line | 2100 | 80 | km/s | 2 | $\rm{FWHM_{CO}} = 2470 \pm 40$, $\rm{FWHM_{SiO}} = 3140 \pm 100$, and $\rm{FWHM_{H_2}} = 2100 \pm 80$ |
| H2 2.12 um flux in 2017 | 2.5e-16 | 0.3e-16 | erg cm-2 s-1 | 0 | the flux in 2017 is $2.5\pm0.3 \times 10^{-16}$ $\rm ~erg~cm^{-2}~s^{-1}$ |

## Qualitative findings

- Brightest H2, CO and SiO occupy different parts of the inner ejecta; brightest H2 coincides with weak dust emission.  
  > "the brightest regions of H$_2$, CO and SiO occupy different parts of the inner ejecta and that the brightest H$_2$ clump coincides with a region of very weak dust emission" (abstract)

## Claim tuples

- H: Does H2 form on dust grains or in the gas phase? | E: Overlay H2 contours on ALMA 315 GHz dust image | R: Brightest H2 lies in a gap between dust clumps | F: Consistent with gas-phase formation | **supported**
- H: Are H2, CO and SiO co-spatial? | E: 60% iso-surface comparison in 3D and line-profile widths | R: Brightest regions distinct; H2 FWHM slightly smaller | F: Different parts of ejecta; evidence of mixing | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Dust may obscure H2 on the far side and no 3D information for dust; comparison limited by resolution.  
  > "However, the comparison is complicated by the lack of 3D information for the dust and the fact that the dust may obscure H$_2$ emission" (6.1 Formation, excitation and evolution of H2 in SN 1987A)
- Caveat (inferred, ours): Dust comparison is qualitative and the dust image is from a non-standard narrow band
- Caveat (inferred, ours): Epoch differences of ~2 years between datasets

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Band 7 reduction details (in prep paper)
- Missing: Band 6 cube processing (Abellan2017)
- Missing: SINFONI custom combination software
- Data volume (inferred): ~10-50 GB for the ALMA parts
- Score (inferred): 2/5, ALMA is a supporting comparison; the data processing is deferred to other papers and the main data are VLT/SINFONI.
- Rediscovery candidate: no, ALMA processing is not specified here and the main results rely on SINFONI data.

## Links

- Method: (cite: Abellan2017) (3D CO and SiO ALMA maps)
- Companion: P. Cigan et al. (in preparation) (ALMA Band 7 dust image reduction)
- Companion: (cite: Larsson2016) (Previous 3D maps of ejecta (L16))

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 21,
  "rate": 0.35
 },
 "evidence_ok": true
}
```
