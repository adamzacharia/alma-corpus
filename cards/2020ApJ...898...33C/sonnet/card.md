# ALMA [{N} {II}] 205 μm Imaging Spectroscopy of the Lensed Submillimeter Galaxy ID 141 at Redshift 4.24

`2020ApJ...898...33C` | The Astrophysical Journal 2020 | first author: Cheng, Cheng | arXiv: 2006.01147 | DOI: 10.3847/1538-4357/ab980b

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the intrinsic morphology, kinematics, line ratios and star formation properties of the lensed SMG ID 141, from ALMA [N II] 205 um and continuum imaging?  
  > "To understand the origin of the high SFR in ID 141, we observe the \[N ii \] and FIR continuum with ALMA at a resolution of about 1$''$" (Introduction)
- Target **ID 141 (H-ATLAS)**: coordinates 14:24:13.9 +02:23:04 (J2000)  
  > "ID 141 (R.A. = 14:24:13.9; decl. = +02:23:04; J2000) at $z$ = 4.24" (Introduction); z/distance z = 4.24 (lens at z=0.595)  
  > "ID 141 (R.A. = 14:24:13.9; decl. = +02:23:04; J2000) at $z$ = 4.24" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00388.S
- bands: Band 7  
  > "ID 141 is observed in ALMA Band 7." (2 Observation)
- frequencies and spectral setup: 4 SPWs of 1.75 GHz; one centered on [N II] at 277.4 GHz; continuum SPWs around 277.7, 287.7, 289.7 GHz; 128 channels of 15.6 MHz each  
  > "One of the four available spectral windows (with a bandwidth of 1.75 GHz ) was centered at the red-shifted \[N ii \] line at 277.4 GHz." (2 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 to 331 m, 45 antennas  
  > "The observation utilizes 45 antennas and the baselines range from 15.1 to 331 m." (2 Observation)
- angular resolution: 1.46"x0.88" continuum; 1.25"x0.8" [N II]  
  > "resulting in a synthesized beam size of $1.46'' \times 0.88''$ with a $\rm P.A. = 57.7^{\circ}$ for the continuum" (2 Observation)
- max recoverable scale: about 9"  
  > "corresponds to about $9''$, much larger than the angular size of our target" (2 Observation)
- sensitivity: continuum rms 0.25 mJy/beam; cube rms ~0.6 mJy/beam per 100 km/s channel  
  > "The final continuum image is an average of the three continuum SPWs and the RMS noise is 0.25 mJy beam$^{-1}$." (2 Observation)
- time on source: 302.4 s on target; total 25 minutes  
  > "The on-target exposure time is 302.4 s." (2 Observation)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [N II] 205 um (1461.134 GHz)
- External data: [C II] flux 107±17 Jy km/s and CO(7-6) flux 6.5±1.4 Jy km/s  
  > "together with the \[C ii \] flux ($107\pm 17$ Jy km/s) and CO (7-6) flux ($6.5\pm1.4$ Jy km/s) from (cite: Cox2011)" (4.2 Line ratio properties) [from (cite: Cox2011)]
- External data: Lens configuration: two lens galaxies at z=0.595; Keck astrometry for secondary lens offset  
  > "using the astrometry information provided by Keck image (cite: Bussmann2012)" (4.1 Lensing Modeling) [from (cite: Bussmann2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5.3  
  > "Common Astronomy Software Applications (CASA) 4.5.3 (cite: McMullin2007)" (2 Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (phase J1359+0159, bandpass J1337-1257)  
  > "The phase, bandpass and flux calibrations are based on the observations of J1359+0159, J1337-1257, and Callisto, respectively." (2 Observation)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "the final images are cleaned using the natural weighting only on the pixels with values $>3\sigma$" (2 Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: clean only pixels >3 sigma  
  > "cleaned using the natural weighting only on the pixels with values $>3\sigma$" (2 Observation)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub order=1  
  > "the continuum is subtracted using the task “uvcontsub” with order$=1$" (2 Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.25 mJy/beam continuum; ~0.6 mJy/beam per 100 km/s channel  
  > "an RMS noise of about 0.6 mJy beam$^{-1}$ per velocity channel" (2 Observation)

### Inherited from earlier work

- Lens modeling procedure technical detail  
  > "more technical detail can be found in (cite: Hezaveh13)" (4.1 Lensing Modeling) [from (cite: Hezaveh13)]
- SFR from CO(7-6) luminosity calibration  
  > "or from the CO (7–6) luminosity: $8.18\times 10^{-6}L_{\rm CO \, (7-6)}/L_{\odot}$ (cite: Lu2015)" (4.3 Star Formation Properties) [from (cite: Lu2015)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used in uvcontsub
- Clean threshold, cell and image size
- Which SPWs/channels and mask define the moment maps
- Polygon aperture definitions for spectra
- Details of moment-map back-projection to source plane
- Exact visibility data selection/averaging for lens modelling

## Analysis recipe

1. **Image continuum and [N II] cube**: CASA cleaning with natural weighting, uvcontsub order 1; continuum averaged over three SPWs  
  > "The final continuum image is an average of the three continuum SPWs" (2 Observation)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract and fit [N II] spectra**: polygon apertures on each lensed image; double-Gaussian fits  
  > "All spectra are fitted with a double-Gaussian function and the results are listed in Table 1." (3.2 Spectra)
   - fitting: double Gaussian  
  > "All spectra are fitted with a double-Gaussian function and the results are listed in Table 1." (Results, Spectra)
   - validation: _not stated_
3. **Fit FIR SED**: modified blackbody fit with beta fixed  
  > "We fit the FIR SED with a modified blackbody function (cite: Beelen2006), with a fixed power-law index of the dust emissivity $\beta = 1.8$" (3.3 Dust continuum)
   - assumption: beta = 1.8  
  > "fixed power-law index of the dust emissivity $\beta = 1.8$" (3.3 Dust continuum)
   - fitting: _not stated_
   - validation: CMB effect tested following da Cunha 2013, insignificant  
  > "found an insignificant effect" (3.3 Dust continuum)
4. **Lens model the continuum in the uv-plane**: two SIE lenses plus one Sérsic source; visibility fitting with nested sampling  
  > "which also consists of two SIEs for the lens and one Sérsic profile for the source" (4.1 Lensing Modeling)
   - software: tiny_lens, Visilens, pymultinest, PyAutoLens
   - parameter: secondary lens offset fixed to (-0.025", -0.327")  
  > "We fix the position offset between the secondary lens and the main lens to (-0.025$''$, -0.327$''$)" (4.1 Lensing Modeling)
   - assumption: single Sérsic source; lens mass ratio not fixed  
  > "we do not assume the mass ratio of two lens galaxies to be 2:1 in this work" (4.1 Lensing Modeling)
   - fitting: chi2 likelihood on visibilities; priors in Table 2 (uniform, Gaussian, log-uniform); pymultinest  
  > "We use the nested sampling tool – pymultinest(cite: Buchner2014; Feroz2009)" (4.1 Lensing Modeling)
   - validation: mock data test (~10% accuracy); PyAutoLens on cleaned image; Bayesian evidence comparison with source size fixed to 0.46"  
  > "Modeling results under this assumption decrease the Bayesian evidence by a factor of $\sim$500." (4.1 Lensing Modeling)
5. **Reconstruct source-plane velocity fields**: trace [N II] moment maps to source plane with the continuum lens model, stacking multiple image counterparts weighted by flux  
  > "we just use the lens model derived from the continuum to trace the \[N ii \] moment map back to the source planes" (4.1 Lensing Modeling)
   - assumption: beam smearing not accounted for; qualitative  
  > "Although this method does not account for the beam smearing effect properly, it still offers a qualitative illustration" (4.1 Lensing Modeling)
   - fitting: _not stated_
   - validation: _not stated_
6. **Line ratios, SFR and SF region size**: line ratios vs C(60/100) from Lu2015; SFR from LIR (Kennicutt) and CO(7-6); Sigma_SFR from C(60/100); R_SF from Sigma_SFR = 0.5 SFR/(pi R^2)  
  > "The half-light radius, $R_{\rm SF}$, of the star-forming region is given by $\Sigma_{\rm SFR} = {0.5\times\rm SFR} / (\pi \times R_{\rm SF}^2)$" (4.3 Star Formation Properties)
   - assumption: Chabrier IMF; magnification 5.8  
  > "Both formulae assume a Chabrier initial mass function" (4.3 Star Formation Properties)
   - fitting: _not stated_
   - validation: SFR_FIR and SFR_CO consistent within ~30%  
  > "These SFR estimates are consistent with each other" (4.3 Star Formation Properties)

## Software

- **CASA** 4.5.3: data reduction and imaging  
  > "The data reduction was carried out with the Common Astronomy Software Applications (CASA) 4.5.3" (2 Observation)
- **tiny_lens** : uv-plane lens modeling (authors' code)  
  > "In this work, we introduce our code – tiny_lens" (4.1 Lensing Modeling)
- **Visilens** : basis for visibility modeling  
  > "which is based on another open-source project – Visilens" (4.1 Lensing Modeling)
- **pymultinest** : nested sampling of lens parameters  
  > "We use the nested sampling tool – pymultinest" (4.1 Lensing Modeling)
- **PyAutoLens** : independent lens modeling check on cleaned image  
  > "using another lens modeling tool–PyAutoLens (cite: Nightingale18)" (4.1 Lensing Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total [N II] flux | 7.9 | 1.9 | Jy km/s | 2 | The total \[N ii \] flux is $7.9\pm 1.9$ Jy km/s. |
| Total continuum flux | 52.0 | 5.2 | mJy | 3 | The total continuum flux measured by ALMA is 52.0 $\pm$ 5.2 mJy. |
| Source Sérsic index | 0.9539 | 0.0595 | dimensionless | 4 | $n_{S}$ / 0 / \[0.30 ,8.00\] / 0.9539 / 0.0595 |
| Source effective radius | 0.1798 | 0.0016 | arcsec | 4 | $R_{e}$ ($''$) / 0 / \[0.01 ,1.00\] / 0.1798 / 0.0016 |
| Reduced chi2 of lens model | 1.01 | not stated | dimensionless | 4 | The best-fit model has $\chi^2 = 757972$ with 746981 degrees of freedom |
| log([N II]/[C II]) | -1.12 | 0.16 | dimensionless | 6 | log(\[N ii \] /\[C ii \] ) = -1.12$\pm$0.16 |
| Intrinsic LIR (8-1000 um) | 1.7e13 | 0.4e13 | Lsun | 6 | $= 1.7 \pm 0.4 \times 10^{13} L_\odot$ |
| SFR_FIR | 1843 | 424 | Msun/yr | 6 | SFR$_{\rm FIR} = 1843 \pm 424 M_{\odot}/\rm yr$ |
| R_SF | 0.74 | 0.30 | kpc | 6 | $R_{\rm SF}$ = 0.74 $\pm$ 0.30 kpc |
| Dust temperature | ~40 | not stated | K | 3 | The resulting dust temperature is $\sim$40 K. |

## Qualitative findings

- Source-plane velocity field is rotation-dominated with ~300 km/s at large radii; favors disk interpretation  
  > "Therefore, we favor the conclusion that an orderly rotating disk is the source of the observed velocity field of ID 141." (4.1 Lensing Modeling)

## Claim tuples

- H: Is ID 141 a rotating disk rather than a compact merger? | E: Back-project [N II] moment maps via continuum lens model; check Sérsic index | R: Rotation ~300 km/s; Sérsic n = 0.95 | F: ID 141 is likely a rotation-supported disk | **partially**
- H: Do line ratios of ID 141 follow local LIRG correlations with C(60/100)? | E: Compare [N II]/[C II] and [N II]/CO(7-6) with Lu2015 relations | R: Offsets within 1 sigma | F: Correlations still hold at high z | **supported**
- H: What is the intrinsic size of the star-forming region? | E: Lens model of continuum and Sigma_SFR from C(60/100) | R: Re=0.18" (1.24 kpc); R_SF=0.74 kpc | F: Compact source, smaller than FIR size-luminosity relation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Lens modeling done in uv-plane because CLEAN makes uncertainties hard to quantify  
  > "it is better to work on the u-v plane directly" (4.1 Lensing Modeling)
- Alternative: Source size fixed to Bussmann's 0.46" rejected (evidence lower by ~500)  
  > "Modeling results under this assumption decrease the Bayesian evidence by a factor of $\sim$500." (4.1 Lensing Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Source-plane velocity reconstruction ignores beam smearing; only partially resolved  
  > "we can conclude that ID 141 is only partially resolved in \[N ii \] emission for our current data" (4.1 Lensing Modeling)
- Caveat (inferred, ours): Low S/N and ~1" resolution limit kinematic conclusions
- Caveat (inferred, ours): Dark matter halo mass inferred from a single assumed flat rotation velocity; abstract (1e12) and conclusion (5e12) differ
- Caveat (inferred, ours): Double-Gaussian fit uncertainties are large
- Caveat (inferred, ours): Single Sérsic source model

## Reproducibility

- Data public (paper): ALMA data cited by project code 2015.1.00388.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00388.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: tiny_lens available at gitlab.com/cxylzlx/tiny_lens  
  > "<https://gitlab.com/cxylzlx/tiny_lens>" (footnote 1)
- Missing: Imaging parameters (cell, image size, line-free channels)
- Missing: Aperture polygons
- Missing: Source-plane back-projection details
- Data volume (inferred): ~ a few GB (single short Band 7 execution)
- Score (inferred): 3/5, Public data and public code, and lens priors tabulated, but imaging and kinematic reconstruction details are sparse.
- Rediscovery candidate: yes, Public single-EB data, numeric results (fluxes, lens parameters), code available.

## Links

- Method: (cite: Hezaveh13) (uv-plane lens modeling procedure)
- Method: (cite: Spilker16) (Visilens basis)
- Companion: (cite: Cox2011) (prior ID 141 line and continuum measurements)
- Companion: (cite: Bussmann2012) (previous lens model)
- Companion: (cite: Lu2015) (line ratio SFR/color method)
- Related: H-ATLAS

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 47,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
