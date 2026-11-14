# Accretion Kinematics through the Warped Transition Disk in HD142527 from Resolved CO(6-5) Observations

`2015ApJ...811...92C` | The Astrophysical Journal 2015 | first author: Casassus, S. | arXiv: 1505.07732 | DOI: 10.1088/0004-637X/811/2/92

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What physical structure underlies the non-Keplerian intra-cavity gas kinematics in HD 142527, as seen in new CO(6-5) data?  
  > "We aim to understand the physical structure that underlies the intra-cavity gaseous flows, guided by new molecular-line data in CO(6-5) with unprecedented angular resolutions." (abstract)
- Target **HD 142527**: coordinates _not stated_; z/distance ~145 pc  
  > "The pre-main-sequence star HD 142527 (F6iiie, at a distance of $\sim$145 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00465.S
- bands: Band 9 (~700 GHz)  
  > "HD 142527 was observed with ALMA in band 9, at $\sim$700 GHz, during June 2012" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 0.04 to 0.9 Mlambda  
  > "with baselines ranging from 0.04 M$\lambda$ to 0.9 M$\lambda$" (2 Observations)
- angular resolution: MEM PSF 0.062" x 0.051" for a point source, up to ~50% coarser for extended emission; natural-weight beam 0.30" x 0.25"  
  > "the full-width at half-maximum (FWHM) of the MEM PSF varies from 0.062$''$  $\times$ 0.051$''$  for a bright point source" (2.1 Choice of image-plane representations of the visibility data)
- max recoverable scale: _not stated_
- sensitivity: rms 0.04 Jy/beam after self-calibration (0.08 before)  
  > "while the rms noise level decreased to 0.04 Jy beam$^{-1}$" (6.1 ALMA CO(6-5) data)
- time on source: _not stated_
- observing dates: June 2012  
  > "during June 2012" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=6-5 (not stated)
- Other facility **ALMA Cycle 0 band 7 (CO(3-2), HCO+(4-3))**: Complementary previously published molecular-line data  
  > "the HCO$^+$(4-3) and CO(3-2) data previously described in the literature also display deviations from Keplerian rotation" (2.3 Complementary sub-mm molecular-line data)
- Other facility **APEX CHAMP+**: Single-dish CO(6-5) flux of 80 Jy km/s for comparison  
  > "flux density of 80 Jy km s$^{-1}$ reported by (cite: Casassus2013A&A...553A..64C) from APEX+CHAMP+ single-dish observations" (2.2 CO(6-5) kinematics)
- External data: Inner disk PA of -8±5 deg and 70 deg relative inclination from scattered-light shadows; SED-fitting parametric disk model  
  > "Yet the scattered light shadows from the inner disk show that its PA is $-8\pm5$$^\circ$" (2.2 CO(6-5) kinematics) [from (cite: Marino2015ApJ...798L..44M)]
- External data: Stellar accretion rate 1e-7 Msun/yr  
  > "We use a stellar accretion rate $dM_\star/dt = 10^{-7}~M_\odot$" (3.1 Parametric modeling) [from (cite: 2006A&A...459..837G)]
- External data: 12C/13C = 76 ISM isotopic abundance  
  > "we used the ISM isotopic abundance for $^{12}$C/$^{13}$C of 76" (3.2.1 Adopted abundance fields and depth of the cavity) [from (cite: 2008A&A...477..865S)]
- External data: C18O/12CO ISM ratio of 500  
  > "with an ISM isotopologue abundance for C$^{18}$O/$^{12}$CO of 500" (3.2.1 Adopted abundance fields and depth of the cavity) [from (cite: 1994ARA&A..32..191W)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Self-calibration derived from continuum, gain corrections applied to line data; peak 0.42 to 0.67 Jy/beam  
  > "Applying the same gain corrections to the line data also resulted in improved dynamic range." (6.1 ALMA CO(6-5) data)

### Imaging

- task: _not stated_
- deconvolver: uvmem maximum-entropy (MEM) non-parametric visibility fit  
  > "Image synthesis was performed with a non-parametric least-squares fit to the visibility data" (2.1 Choice of image-plane representations of the visibility data)
- weighting robust: natural weights for flux and noise; Briggs restoration beam  
  > "extracted from the restored datacube, using natural weights" (2.2 CO(6-5) kinematics)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: first-order fit to continuum in visibility domain  
  > "Continuum subtraction under CO(6-5) was performed with a first-order fit to the continuum in the visibility domain." (6.1 ALMA CO(6-5) data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: moment maps median-smoothed with 5x5 kernel  
  > "The resulting moment maps are embellished by median-smoothing with a square $5\times5$ kernel." (7.2 Moment maps)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Instrumental setup and uvmem algorithm details  
  > "Details on the instrumental setup are described in a companion article on the continuum emission" (6.1 ALMA CO(6-5) data) [from (cite: Casassus2015hd142trap)]
- Accretion flow model developed from HCO+ interpretation  
  > "we developed on the accretion flows proposed to account for the HCO$^+$ observations" (3.1 Parametric modeling) [from (cite: Casassus2013Natur)]

### Not stated but needed to reproduce (our reading)

- Calibrator and pipeline/CASA version, flux scale uncertainty
- Self-calibration solution intervals
- Line-free channels for continuum fit
- Channel width and velocity resolution
- uvmem code and regularization settings
- Dust model, disk mass and dust SED parameters for the RADMC-3D model
- Photodissociation/abundance taper details beyond Gaussian width

## Analysis recipe

1. **Image synthesis with MEM**: uvmem deconvolution of continuum-subtracted visibilities; Monte Carlo with 120 noise realizations for uncertainties  
  > "We then took statistics on 120 realizations" (7.1 Angular resolution and statistics of the deconvolved MEM models)
   - software: uvmem
   - fitting: _not stated_
   - validation: Compared with clean restored maps  
  > "The details of the centroid map do not depend on the reconstruction." (7.4 Comparison of different image synthesis schemes)
2. **Extract moment maps**: Peak-centred velocity range to first nulls plus two channels; standard moments and Gaussian fit  
  > "we take standard moments over this reduced velocity range, and also fit a Gaussian." (7.2 Moment maps)
   - fitting: _not stated_
   - validation: Intrinsic line width check by subtracting bulk motion dispersion in quadrature  
  > "The corresponding dispersion at $\vec{P}$ is $\sigma_{\rm int.}(\vec{P}) = 1.81~$km s$^{-1}$." (8 Impact of a finite beam in estimates of intrinsic line-widths.)
3. **Parametric warped accretion model with radiative transfer**: RADMC-3D line predictions for a warped disk with radial infall and steady-state surface density, smoothed to MEM resolution and compared with data  
  > "Emergent specific intensity fields were predicted by transferring the stellar radiation through the model circumstellar material with the radmc3d" (3.1 Parametric modeling)
   - software: RADMC-3D
   - parameter: Stellar mass 1.8 Msun; outer disk i=20 deg, PA=-20 deg; inner disk relative inclination 70 deg, PA=-8 deg; warp between 20 and 23 AU; free-fall at 30 AU  
  > "The stellar mass is set at $1.8~M_\odot$; higher masses produce higher velocities inside the cavity than observed." (3.1 Parametric modeling)
   - assumption: X_CO = 1e-4; HCO+ abundance 1e-9; T=70 K inside 30 AU, r^-0.5 beyond  
  > "We adopted a nominal H$_2$/$^{12}$CO ratio $X_{\mathrm{CO}}=10^{-4}$" (3.2.1 Adopted abundance fields and depth of the cavity)
   - fitting: No systematic search; model tuned by hand  
  > "is not derived from a systematic search in parameter space." (3.1 Parametric modeling)
   - validation: Qualitative match to CO(6-5) centroid, CO isotopologue non-detections in cavity, and CRIRES spectro-astrometry  
  > "The model is in agreement with the non-detection of $^{13}$CO and C$^{18}$O inside the gap." (3.2.1 Adopted abundance fields and depth of the cavity)

## Software

- **RADMC-3D** v0.39: Radiative transfer predictions of line emission  
  > "with the radmc3d[^3] package (cite: RADMC3D0.39)" (3.1 Parametric modeling)
- **uvmem** : Maximum-entropy image synthesis of visibilities  
  > "Details on our image synthesis algorithm `uvmem` are given in a companion paper" (7.1 Angular resolution and statistics of the deconvolved MEM models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(6-5) central decrement relative to ring at 0.2" | 0.25 | 0.03 | dimensionless | 2 | minimum intensity is a factor of $\sim 0.25\pm0.03$ times lower than the average intensity |
| Integrated CO(6-5) flux (2.5" aperture) | 70 | not stated | Jy km/s | 2 | is 70 Jy km s$^{-1}$ |
| Velocity dispersion at (+0.2",+0.2") restored / MEM / intrinsic | 2.01 / 1.78 / 1.81 | not stated | km/s | 2 | is 2.01 km s$^{-1}$, while the 1 $\sigma$ dispersion extracted from the deconvolved datacubes, $\sigma_{\rm mem}$, still shows a dispersion of 1.78 km s$^{-1}$ |
| PA of velocity axis inside 0.1" | 110 | 10 | deg | 2 | Inside 0.1$''$, the PA appears to rotate further and reaches $110\pm10$$^\circ$ . |

## Qualitative findings

- Intra-cavity kinematics consistent with axisymmetric stellocentric accretion near free-fall through a warp to the inner disk  
  > "the kinematics are consistent, to first order, with axisymmetric accretion onto the inner disk occurring at all azimuth." (abstract)

## Claim tuples

- H: Intra-cavity flows are stellocentric accretion at all azimuth near free-fall rather than outflow | E: Warped, accreting parametric RADMC-3D model compared with CO(6-5) MEM moment maps | R: Model reproduces twist of centroid PA and the inner 110 deg flip, and the isotopologue cavity depth | F: Accretion at near free-fall with steady-state rate fixed at the stellar accretion rate explains the data | **supported**
- H: Disk tearing by an inclined companion explains the abrupt warp and fast accretion | E: Qualitative comparison of break radius estimates with model | R: Estimated a~15 AU consistent with 30 AU breaking radius | F: Plausible but needs targeted simulations | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: MEM deconvolved moments avoid clean-beam broadening of velocity dispersions  
  > "We thus chose to base our study on the moments maps inferred from deconvolved (MEM) datacubes." (2.1 Choice of image-plane representations of the visibility data)
- Alternative: Outflowing disk wind ruled out because it would twist kinematics the opposite way  
  > "we can rule out an outflowing disk wind" (4.2 What about an outflow?)
- How they decided it was enough: _not stated_
- Limitation (authors): Model is parametric, not dynamically consistent, no systematic parameter search  
  > "It is not a dynamically consistent model." (3.1 Parametric modeling)
- Limitation (authors): MEM resolution varies with image  
  > "the resolution of the MEM images is variable and depends on the image." (2.1 Choice of image-plane representations of the visibility data)
- Caveat (inferred, ours): Model tuned by eye with no goodness-of-fit metric; degeneracies unquantified
- Caveat (inferred, ours): Free-fall interpretation relies on assumed temperature and abundance profiles
- Caveat (inferred, ours): Astrometric alignment was chosen to symmetrize the centroid, which may bias the interpretation

## Reproducibility

- Data public (paper): ALMA program cited; public status not stated  
  > "Based on observations acquired at the ALMA Observatory, through program `ALMA#2011.0.00465.S`." (Acknowledgments)
- Products in archive: _not stated_
- Missing: uvmem code
- Missing: Full RADMC-3D input files
- Missing: Calibration details in companion paper
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Data have a project code, but calibration and the uvmem imaging are in a companion paper, and the model is hand-tuned without full inputs.
- Rediscovery candidate: no, Key results are qualitative model comparisons, and the recipe depends on unreleased code and a companion paper.

## Links

- Method: (cite: Casassus2015hd142trap) (Instrument setup and uvmem algorithm)
- Companion: (cite: Casassus2013Natur) (Cycle 0 HCO+(4-3) accretion flow observations)
- Companion: (cite: Marino2015ApJ...798L..44M) (Scattered-light shadows and inner disk orientation)

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 37,
  "rate": 0.544
 },
 "evidence_ok": true
}
```
