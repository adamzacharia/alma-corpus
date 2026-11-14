# First Detection of c-C<SUB>3</SUB>H<SUB>2</SUB> in a Circumstellar Disk

`2013ApJ...765L..14Q` | The Astrophysical Journal Letters 2013 | first author: Qi, Chunhua | arXiv: 1302.0251 | DOI: 10.1088/2041-8205/765/1/L14

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is c-C3H2 present in the HD 163296 disk, and what are its radial distribution, column density and ortho/para ratio?  
  > "we aim to provide first constraints on the abundance, distribution and $o/p$ ratio of $c$-C$_3$H$_2$ in the HD 163296 disk." (Introduction)
- Target **HD 163296**: coordinates RA 17h56m21.287s, Dec -21d57m22.39s (J2000)  
  > "HD 163296 (RA: 17$^{\rm h}$56$^{\rm m}$21.287s, DEC: $-$21$^\circ$57$'$22.39$''$; J2000.0)" (Observations); "At a distance of $\sim$122 pc ((cite: perryman_l97))" (Introduction); z/distance ~122 pc  
  > "HD 163296 (RA: 17$^{\rm h}$56$^{\rm m}$21.287s, DEC: $-$21$^\circ$57$'$22.39$''$; J2000.0)" (Observations); "At a distance of $\sim$122 pc ((cite: perryman_l97))" (Introduction); distance from Perryman et al. 1997 (Hipparcos)  
  > "HD 163296 (RA: 17$^{\rm h}$56$^{\rm m}$21.287s, DEC: $-$21$^\circ$57$'$22.39$''$; J2000.0)" (Observations); "At a distance of $\sim$122 pc ((cite: perryman_l97))" (Introduction)

## Data provenance

- ALMA projects: 2011.0.00010.SV
- bands: Band 6  
  > "as part of the ALMA Science Verification (SV) program in band 6" (Observations)
- frequencies and spectral setup: 4 spectral windows; SpwID #0 channel width 0.488 MHz (0.67 km/s), 216.167-218.042 GHz, binned to 1 km/s  
  > "retrieved from SpwID #0 with a channel width of 0.488 MHz (0.67 km s$^{-1}$) covering the total 1.875 GHz bandwidth from 216.167 to 218.042 GHz" (Observations)
- continuum bandwidth: _not stated_
- arrays: 25 12-m antennae (ACA 7-m flagged)  
  > "25 12-m antennae were used (2 7-m ACA antennae were present in the dataset but flagged)" (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.9x0.7" (PA=84)  
  > "resulting synthesized beam size of 0.9$\times$0.7$\ensuremath{''}$ (PA=84)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 2.2 mJy/beam per 1 km/s channel  
  > "The resulting line rms noise level is estimated to be 2.2 mJy beam$^{-1}$ per 1 km s$^{-1}$ channel in line free channels." (Observations)
- time on source: 84 minutes total integration  
  > "The source was observed with a total integration time of 84 minutes." (Observations)
- observing dates: 2012 June 9, June 23 and July 7  
  > "was observed on 2012 June 9, June 23 and July 7" (Observations)
- pi or archival as stated: _not stated_
- Line: c-C3H2 6_1,6-5_0,5 / 6_0,6-5_1,5 (217.822 GHz (Table 1))
- Line: c-C3H2 5_1,4-4_2,3 (217.940 GHz)
- Line: c-C3H2 3_3,0-2_2,1 (216.279 GHz)
- Line: 13CO 2-1 (220.399 GHz)
- Other facility **SMA**: Earlier continuum and 13CO/C18O data used for flux comparison  
  > "which agrees with the SMA observations (cite: Qi11)" (Observations)
- External data: Disk physical structure model (temperature, density, geometry; Table 3)  
  > "based on a previously developed accretion disk model with well-defined temperature and density structures (cite: Qi11)" (Ring structure model) [from Qi11]
- External data: Collisional rates  
  > "The collisional rates are taken from (cite: Chandra00)" (Ring structure model) [from Chandra00]
- External data: Molecular data file (LAMDA), Einstein A  
  > "the molecular data file is retrieved from the Leiden Atomic and Molecular Database (cite: Schoier05)" (Ring structure model) [from Schoier05]

## Processing

### Calibration

- pipeline or manual: SV team calibration scripts in CASA  
  > "following the detailed calibration and imaging scripts provided by the ALMA science verification team" (Observations)
- casa version: v3.4  
  > "The data were calibrated in the CASA software package (v3.4)" (Observations)
- pipeline version: _not stated_
- archive products used as is: Public calibrated measurement sets and scripts  
  > "Since those scripts, along with fully calibrated measurement sets, are publicly available online" (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: Gaussian taper 1" FWHM for weak lines  
  > "we applied a Gaussian taper to the visibility data that corresponds to 1$''$  FWHM in the image domain" (c-C3H2 detection)
- cell size: _not stated_
- image size: _not stated_
- masking: Separate per-channel masks from 6-5 emission used for spectra  
  > "we create separate masks to cover the $c$-C$_3$H$_2$ $6-5$ line emission at each channel" (c-C3H2 detection)
- multiscale scales: _not stated_
- continuum subtraction: Continuum from line-free channels; lines continuum-subtracted  
  > "The 218 GHz (1.37mm) continuum was generated from the line-free channels in the two spectral windows" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.9x0.7" (6-5); 1.3x1.2" (tapered, 3-2 and 5-4)  
  > "which resulted in a beam of 1.3$\times$1.2$\ensuremath{''}$ (PA=78)" (c-C3H2 detection)
- final rms: 2.2 mJy/beam per 1 km/s channel  
  > "The resulting line rms noise level is estimated to be 2.2 mJy beam$^{-1}$ per 1 km s$^{-1}$ channel in line free channels." (Observations)

### Inherited from earlier work

- Disk physical model and parameters  
  > "are summarized in Table 3 of (cite: Qi11)" (Ring structure model) [from Qi et al. 2011 (cite: Qi11)]
- Calibration and imaging scripts  
  > "following the detailed calibration and imaging scripts provided by the ALMA science verification team" (Observations) [from ALMA SV team]
- Vertical layer assumption for molecule  
  > "is present with a constant abundance in a layer with boundaries toward the midplane and toward the surface of the disk (cite: Qi08; Oberg12)" (Ring structure model) [from Qi08; Oberg12]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (weighting, robust, cell, image size, clean threshold)
- Line-free channels used for continuum subtraction
- Details of the chi2 model grid ranges and step sizes
- RATRAN settings (number of photons, grid)
- Spectral extraction mask thresholds
- Flux/gain calibrators (in SV scripts)

## Analysis recipe

1. **Image continuum and lines**: Calibrated SV data; continuum from line-free channels; lines continuum-subtracted and binned to 1 km/s; taper for weak lines  
  > "We have binned the lines in channels of 1 km s$^{-1}$ to achieve higher signal-to-noise ratios" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Continuum flux and 13CO/C18O compared with SMA  
  > "Excellent agreement is also seen between the SMA and ALMA spectra for the $^{13}$CO and C$^{18}$O $2-1$ lines with fluxes within 10%" (Observations)
2. **Extract spectra and fluxes**: Per-channel masks from 6-5 emission applied to all c-C3H2 lines  
  > "The same masks are also used for other $c$-C$_3$H$_2$ lines." (c-C3H2 detection)
   - fitting: _not stated_
   - validation: V_lsr and position angle compared with 13CO  
  > "The $6-5$ line is clearly detected with the expected line shape and V$_{\rm lsr}$ consistent with $^{13}$CO." (c-C3H2 detection)
3. **Fit radial ring model in the uv-plane**: Grid of synthetic 6-5 visibilities over Rout, Rin, p, N100; chi2 minimization on real and imaginary visibilities  
  > "we compute a grid of synthetic $c$-C$_3$H$_2$ J=$6-5$ visibility datasets over a range of R$_{out}$, R$_{in}$, $p$ and N$_{100}$ values and compare with the observations" (Ring structure model)
   - software: RATRAN
   - parameter: Vertical boundaries fixed: sigma_s = 0.32, sigma_m = 3.2  
  > "We therefore fix the vertical surface boundary $\sigma_s$ as 0.32 ($\log_{10}(\sigma_s)=-0.5$) and the midplane boundary $\sigma_m$ as 3.2" (Ring structure model)
   - assumption: Keplerian rotation; Qi11 disk structure; constant abundance in a layer; power-law column density  
  > "we assume the disk material orbits the central star in Keplerian motion" (Ring structure model)
   - fitting: chi2 grid minimization; 1 sigma ranges from chi2 surfaces  
  > "The best-fit model is obtained by minimizing $\chi^2$" (Ring structure model)
   - validation: Residual channel maps show no significant emission; reduced chi2 = 1.07  
  > "The residual image doesn’t show any significant emission" (Ring structure model)
4. **Constrain ortho/para ratio**: Fit unresolved 5-4 ortho line flux assuming 6-5 distribution; compare with total from 6-5  
  > "By assuming the $c$-C$_3$H$_2$ distribution derived from the $6-5$ line, however, we can use the unresolved line flux to constrain the $o/p$ ratio." (Ring structure model)
   - software: RATRAN
   - assumption: 6-5 ortho and para lines blended with equal A coefficients; fit ortho only gives o+p  
  > "we fit the data with the ortho line only and the resulting column density can be accounted as the sum of both ortho and para forms" (Ring structure model)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 3.4: Calibration and imaging  
  > "The data were calibrated in the CASA software package (v3.4)" (Observations)
- **RATRAN** : Radiative transfer and excitation for model  
  > "We use the two-dimensional Monte Carlo model RATRAN (cite: Hogerheijde00) to calculate the radiative transfer and molecular excitation." (Ring structure model)
- **LAMDA** : Molecular data file  
  > "the molecular data file is retrieved from the Leiden Atomic and Molecular Database (cite: Schoier05)" (Ring structure model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 218 GHz continuum flux | 608.5 | 2.5 | mJy | 1 | the flux is determined to be 608.5$\pm$2.5 mJy |
| c-C3H2 6-5 integrated flux | 185 | 10 | mJy km/s | 2 | 185\[10\] |
| c-C3H2 5-4 integrated flux | 74 | 9 | mJy km/s | 2 | 74\[9\] |
| c-C3H2 3-2 integrated flux | 53 | 9 | mJy km/s | 2 | 53\[9\] |
| Best-fit inner radius, outer radius, power-law index | Rin 30 AU, Rout 165 AU, p = -2 | 1 sigma: Rin 15-40, Rout 150-200 AU, p -2.5 to -1.5 | AU / dimensionless | 3 | with best-fit values at -2, 30 and 165 AU, respectively (reduced $\chi^2=1.07$) |
| N(c-C3H2) at 100 AU | 2.2e12 | 0.2e12 | cm^-2 | 3 | N($c$-C$_3$H$_2$) is determined to be 2.2$\pm$0.2 $\times$10$^{12}$ cm$^{-2}$ at 100 AU |
| ortho/para ratio | 2.7 | 1.7 | dimensionless | 4 | Hence $o/p$=2.7$\pm$1.7, which is close to the statistical value of 3 |

## Qualitative findings

- 6-5 emission is double-peaked, indicating an inner hole, and follows Keplerian rotation  
  > "the $c$-C$_3$H$_2$ $6-5$ moment map displays a double-peaked morphology, indicative of an inner hole" (c-C3H2 detection)
- 3-2 line is narrower and blue-shifted, possibly a disk wind, needing confirmation  
  > "the $3-2$ line is both narrower and clearly blue-shifted, suggestive of a different physical origin, perhaps in a disk wind" (c-C3H2 detection)

## Claim tuples

- H: c-C3H2 is present in the HD 163296 disk | E: ALMA SV Band 6 imaging of c-C3H2 lines | R: 6-5 line clearly detected, 5-4 and 3-2 tentative | F: First detection of c-C3H2 in a disk | **supported**
- H: c-C3H2 emission traces a Keplerian disk with a ring distribution | E: uv-plane chi2 fit of power-law ring model | R: Rin ~30 AU, Rout ~165 AU, N100 = 2.2e12 cm^-2 | F: c-C3H2 is in a ring | **supported**
- H: The o/p ratio constrains formation conditions | E: 5-4 flux vs 6-5 model | R: o/p = 2.7±1.7 | F: Consistent with 3 but too uncertain | **partially**

## Reasoning

- Why this data: Large disk and strong molecular emission make HD 163296 an ideal target  
  > "The large disk size and strong molecular emission make this system an ideal target to search for new molecules." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low S/N prevents constraining the vertical distribution; weak lines unresolved  
  > "we cannot constrain the location of this vertical layer based on the $c$-C$_3$H$_2$ data" (Ring structure model)
- Limitation (authors): 3-2 and 5-4 lines lie at the edge of the spectral window  
  > "both the $3-2$ and $5-4$ lines are observed at the edge of the spectral window" (c-C3H2 detection)
- Caveat (inferred, ours): Only a coarse grid fit with no formal posterior; parameter degeneracies unclear
- Caveat (inferred, ours): Vertical layer fixed rather than fitted, biasing column density
- Caveat (inferred, ours): Blending of ortho and para 6-5 lines complicates o/p inference
- Caveat (inferred, ours): Abstract quotes 217.882 GHz but Table 1 lists 217.822 GHz

## Reproducibility

- Data public (paper): Scripts and calibrated measurement sets are public  
  > "Since those scripts, along with fully calibrated measurement sets, are publicly available online" (Observations)
- Products in archive: _not stated_
- Missing: Model grid specification and RATRAN settings
- Missing: Mask construction details
- Missing: Qi11 disk model parameter table is external
- Data volume (inferred): ~10-30 GB for the SV calibrated measurement set
- Score (inferred): 6/5, Public data and scripts, clear model approach, but fitting grid and masking details are not given.
- Rediscovery candidate: yes, Public SV data and a stated ring-model recipe with numeric results, though requires the Qi11 model.

## Links

- Method: Hogerheijde00 (RATRAN radiative transfer code)
- Companion: Qi11 (Disk structure model and earlier SMA observations of HD 163296)
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 72,
  "stated": 46,
  "rate": 0.639
 },
 "evidence_ok": true
}
```
