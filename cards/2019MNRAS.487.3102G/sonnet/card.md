# GASP XVIII: star formation quenching due to AGN feedback in the central region of a jellyfish galaxy

`2019MNRAS.487.3102G` | Monthly Notices of the Royal Astronomical Society 2019 | first author: George, K. | arXiv: 1905.08973 | DOI: 10.1093/mnras/stz1443

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, galaxy_clusters_and_sz
- Question: Is star formation in the central region of the ram-pressure-stripped jellyfish galaxy JO201 suppressed, and is this due to AGN feedback or a stellar bar?  
  > "The observed reduction in star formation around the central region of JO201 can in principle be due to the AGN or the stellar bar." (Discussion: Star formation suppression due to AGN or stellar bar?)
- Target **JO201**: coordinates RA 00:41:30.325, Dec -09:15:45.96 (J2000)  
  > "JO201[^2] with a spectroscopic redshift $z \sim$ 0.056 is located at a luminosity distance of $\sim$ 250 Mpc in the Abell 85 galaxy cluster (cite: Moretti_2017)" (The jellyfish galaxy JO201); "$\alpha$(J2000) = 00:41:30.325, $\delta$(J2000) = - 09:15:45.96" (footnote 2); z/distance z ~ 0.056; luminosity distance ~250 Mpc  
  > "JO201[^2] with a spectroscopic redshift $z \sim$ 0.056 is located at a luminosity distance of $\sim$ 250 Mpc in the Abell 85 galaxy cluster (cite: Moretti_2017)" (The jellyfish galaxy JO201); "$\alpha$(J2000) = 00:41:30.325, $\delta$(J2000) = - 09:15:45.96" (footnote 2); distance from Moretti et al. 2017 (spectroscopic redshift, Abell 85 member)  
  > "JO201[^2] with a spectroscopic redshift $z \sim$ 0.056 is located at a luminosity distance of $\sim$ 250 Mpc in the Abell 85 galaxy cluster (cite: Moretti_2017)" (The jellyfish galaxy JO201); "$\alpha$(J2000) = 00:41:30.325, $\delta$(J2000) = - 09:15:45.96" (footnote 2)

## Data provenance

- ALMA projects: 2017.1.00496.S
- bands: Band 3 (100 GHz) and Band 6 (230 GHz), Cycle 5  
  > "JO201 was observed with ALMA in Cycle 5, using Band 3 (100 GHz) and Band 6 (230 GHz) to observe the CO (J$_{1-0}$) and CO (J$_{2-1}$) transitions, respectively." (Data and Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1" in both bands  
  > "The ALMA configurations used provide a resolution of $\sim$ 1" in both bands" (Data and Observations)
- max recoverable scale: 20" (Band 3) and 10" (Band 6)  
  > "allow to recover spatial scales up to 20 and 10 " in band 3 and 6, respectively." (Data and Observations)
- sensitivity: RMS 0.5 mJy/beam (CO 1-0) and 0.85 mJy/beam (CO 2-1) in 20 km/s channels  
  > "The RMS achieved in 20 km/s wide channels have been 0.5 and 0.85 mJy/beam, for CO(1-0) and CO(2-1) respectively" (Data and Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Line: CO J=2-1 (not stated)
- Other facility **VLT/MUSE (GASP)**: Optical IFU spectroscopy: emission line maps, BPT classification, Av, SFH, red continuum  
  > "with the MUSE integral-field spectrograph on the VLT under the programme GASP" (Data and Observations)
- Other facility **AstroSat/UVIT**: FUV (F148W) and NUV (N242W) imaging  
  > "JO201 was observed in FUV (F148W filter, $\lambda_{mean}$=1481 Å, $\delta\lambda$=500 Å) and NUV (N242W filter, $\lambda_{mean}$=2418 Å, $\delta\lambda$=785 Å)" (Data and Observations)
- External data: UVIT observation details and UV SFR/extinction-correction method  
  > "The details of the UV observations of JO201 are given in Table 1 of (cite: George_2018)." (Data and Observations) [from (cite: George_2018)]
- External data: Total stellar mass ~3.55e10 Msun  
  > "total stellar mass $\sim$ 3.55 $\times$ $10^{10}$ M$_{\odot}$ (cite: Bellhouse_2017)" (The jellyfish galaxy JO201) [from (cite: Bellhouse_2017)]

## Processing

### Calibration

- pipeline or manual: Standard pipeline (Pipeline-CASA51-P2-B)  
  > "The data have been calibrated using the standard procedure (Pipeline-CASA51-P2-B)" (Data and Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean in CASA 5.4  
  > "imaged with the task clean using CASA version 5.4" (Data and Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust 0.5  
  > "using weighting Briggs with robust 0.5" (Data and Observations)
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

- Full ALMA observation description and results deferred  
  > "A full description of these observations and results is given in Moretti et al. (in preparation)" (Data and Observations) [from Moretti et al. (in preparation)]
- MUSE data reduction, line fitting details  
  > "(see (cite: Bellhouse_2017) for details)" (Data and Observations) [from (cite: Bellhouse_2017)]
- SFH derivation procedure for age bins  
  > "(cite: Bellhouse_2019) explains in detail the procedure used to derive the SFR for different age bins." (3.3 Star formation history maps) [from (cite: Bellhouse_2019)]

### Not stated but needed to reproduce (our reading)

- ALMA mosaic imaging parameters: cell size, image size, masking, cleaning threshold
- Moment-map construction for CO(2-1): channel range, clipping threshold
- Continuum subtraction and line-free channels
- Flux scale uncertainty and calibrators
- Quantitative size/upper limit of the CO cavity
- Primary beam correction details

## Analysis recipe

1. **Image CO data**: Pipeline calibration and clean imaging of Band 3/6 mosaics; CO(2-1) intensity map  
  > "imaged with the task clean using CASA version 5.4." (Data and Observations)
   - software: CASA
   - parameter: Briggs robust 0.5; 20 km/s channels  
  > "using weighting Briggs with robust 0.5" (Data and Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compare UV cavity, BPT regions and CO cavity**: Overlay NUV contours, BPT AGN/composite/SF regions and CO map; check Av via Balmer decrement; derive FUV SFR density  
  > "The contours created from this NUV image are used in the rest of our analysis to identify star forming regions as well as the region with reduced star formation" (3.1)
   - software: SINOPSIS, kubeviz
   - assumption: Intrinsic Halpha/Hbeta = 3.1; Salpeter IMF  
  > "assuming an intrinsic ratio H$\alpha$/H$\beta$ = 3.1 typical of regions ionized purely by AGN" (3.1)
   - fitting: _not stated_
   - validation: Extinction map checked to rule out dust as cause of UV deficit  
  > "We investigated whether the reduction in UV flux could be due to dust extinction (the map is shown in Fig 3), and concluded this is not the case." (3.1)

## Software

- **CASA** 5.4: ALMA imaging with clean  
  > "imaged with the task clean using CASA version 5.4" (Data and Observations)
- **SINOPSIS** : Stellar absorption correction and SFR maps by age  
  > "The spectrophotometric fitting code SINOPSIS is used to derive the star formation rate (SFR) map of JO201 disk" (3.3)
- **kubeviz** : Gaussian emission line fitting  
  > "The emission lines are then fitted with models comprising single or double Gaussian profiles using kubeviz" (Data and Observations)
- **ZAP** : Sky subtraction in red MUSE spectra  
  > "after having subtracted the sky emission using the ZAP code" (3.2)
- **IRAF ellipse** : Isophote luminosity profile of i-band image  
  > "we used the ellipse task in the isophote IRAF package" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SFR density of disk region | 0.39 | not stated | Msun/yr/kpc^2 | 2 | is found to be 0.39 M$_{\odot}$/yr/kpc$^2$ and for the cavity (as seen in Fig 2) to be 0.14 M$_{\odot}$/yr/kpc$^2$ |
| SFR density of cavity | 0.14 | not stated | Msun/yr/kpc^2 | 2 | is found to be 0.39 M$_{\odot}$/yr/kpc$^2$ and for the cavity (as seen in Fig 2) to be 0.14 M$_{\odot}$/yr/kpc$^2$ |
| Stellar bar length | ~13 | not stated | kpc | 0 | The stellar bar is of length $\sim$ 13 kpc. |
| AGN-dominated region diameter | 7.88" ~ 8.6 | not stated | kpc | 0 | its close surroundings (diameter $\sim$ 7.88" $\sim$ 8.6 kpc) are dominated by the emission due to the AGN |

## Qualitative findings

- CO(2-1) map shows no detection in the central region, inside the UV cavity  
  > "The CO map (which traces the cold phase of molecular gas) is clearly showing a region with no detection around the central region of the galaxy." (3.1)

## Claim tuples

- H: Central star formation suppression in JO201 is due to AGN feedback rather than a stellar bar | E: Combine UVIT, MUSE BPT, ALMA CO, red-continuum bar fit and SFH maps | R: UV and CO cavities coincide with the AGN-dominated region; bar is longer than cavity and old; cavity appears in young-age SFR only | F: AGN feedback most likely suppressed central star formation within the last ~5e8 yr | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dust extinction and stellar bar rejected as causes of central deficit  
  > "Hence, the bar could not have suppressed star formation by totally sweeping the cavity of gas." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Cannot exclude significant star formation in the center, which is AGN dominated  
  > "we cannot exclude the presence of even a significant level of star formation" (3.1)
- Caveat (inferred, ours): ALMA data only shown qualitatively; no quantified CO cavity or molecular gas mass
- Caveat (inferred, ours): Circumstantial AGN attribution; ram-pressure effects not excluded
- Caveat (inferred, ours): Coarse SFH age bins

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA imaging details deferred to unpublished Moretti et al.
- Missing: MUSE/UVIT reductions in companion papers
- Data volume (inferred): tens to ~100 GB for ALMA Band 3/6 mosaics
- Score (inferred): 2/5, ALMA role is minor and qualitative; processing deferred to other papers.
- Rediscovery candidate: no, ALMA result is a qualitative cavity; recipe incomplete.

## Links

- Method: (cite: Fritz_2017) (SINOPSIS code)
- Method: (cite: Bellhouse_2019) (SFH procedure)
- Companion: (cite: George_2018) (UVIT data and UV SFR of JO201)
- Companion: (cite: Poggianti_2017a) (AGN in jellyfish galaxies)
- Companion: (cite: Radovich_2019) (AGN outflow in JO201)
- Related: GASP
- Related: WINGS/OmegaWINGS

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
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
  "facts": 66,
  "stated": 31,
  "rate": 0.47
 },
 "evidence_ok": true
}
```
