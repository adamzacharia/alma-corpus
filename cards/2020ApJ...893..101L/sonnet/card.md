# An Unbiased ALMA Spectral Survey of the LkCa 15 and MWC 480 Protoplanetary Disks

`2020ApJ...893..101L` | The Astrophysical Journal 2020 | first author: Loomis, Ryan A. | arXiv: 2006.16187 | DOI: 10.3847/1538-4357/ab7cc8

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What are the molecular inventories of the MWC 480 and LkCa 15 disks from an unbiased Band 7 spectral line survey, and how do they differ?  
  > "Significant differences are observed in the molecular inventories of MWC 480 and LkCa 15, and we discuss how these results may be interpreted in light of the different physical conditions of these two disk systems." (abstract)
- Target **MWC 480**: coordinates 04:58:46.3 +29:50:37.0 (J2000)  
  > "| MWC 480 | A1-A3/4$^{[1,2]}$ | 04:58:46.3 | 29:50:37.0 | 162 |" (Table 1); "Right ascension, declination, and distance of each source are from the Gaia DR2 catalog" (Table 1); z/distance 162 pc  
  > "| MWC 480 | A1-A3/4$^{[1,2]}$ | 04:58:46.3 | 29:50:37.0 | 162 |" (Table 1); "Right ascension, declination, and distance of each source are from the Gaia DR2 catalog" (Table 1); distance from Gaia DR2  
  > "| MWC 480 | A1-A3/4$^{[1,2]}$ | 04:58:46.3 | 29:50:37.0 | 162 |" (Table 1); "Right ascension, declination, and distance of each source are from the Gaia DR2 catalog" (Table 1)
- Target **LkCa 15**: coordinates 04:39:17.8 +22:21:03.4 (J2000)  
  > "| LkCa 15 | K3-K5$^{[2,8]}$ | 04:39:17.8 | 22:21:03.4 | 159 |" (Table 1); z/distance 159 pc  
  > "| LkCa 15 | K3-K5$^{[2,8]}$ | 04:39:17.8 | 22:21:03.4 | 159 |" (Table 1); distance from Gaia DR2  
  > "| LkCa 15 | K3-K5$^{[2,8]}$ | 04:39:17.8 | 22:21:03.4 | 159 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00657.S, 2013.1.00226.S
- bands: Band 7, 275–317 GHz covered  
  > "spanning $\sim$36 GHz from 275–317 GHz" (abstract)
- frequencies and spectral setup: Five observed settings of 4 FDM SPWs each, 1920 channels, 975 kHz width (~1 km/s); gaps at 306–310 and 318–322 GHz  
  > "Each spectral setup consisted of 4 Frequency Division Mode (FDM) spectral windows, each with 1920 channels." (3 Observations); "resulting in coverage gaps between 306–310 GHz and 318–322 GHz" (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15–650 m across executions  
  > "| C | 2016 Dec. 13 | 39 | 15–650 | 20.2 |" (Table 2)
- angular resolution: Natural-weighted beams ~0.5–1.3 arcsec  
  > "1.30$''$$\times$1.05$''$ (12.7$\degree$)" (Table 3)
- max recoverable scale: _not stated_
- sensitivity: Per-channel rms 1.7–3.9 mJy/beam depending on SPW  
  > "| 3 | 312.18–314.06 | 0.95$''$$\times$0.53$''$ (155.2$\degree$) | 0.86$''$$\times$0.53$''$ (-33.2$\degree$) | 3.7 | 3.9 |" (Table 3)
- time on source: ~12.6–20.7 min per source per execution  
  > "| 2016 Dec. 12 | 36 | 15–650 | 20.7 |" (Table 2)
- observing dates: 2016 Jan–Dec  
  > "| A | 2016 Jan. 17 | 36 | 15–331 | 19.2 |" (Table 2)
- pi or archival as stated: _not stated_
- Line: H2CO 4_14–3_13 (281526.9 MHz)
- Line: CS 6–5 (293912.1 MHz)
- Line: N2H+ 3–2 (279511.7 MHz)
- Other facility **Gaia DR2**: Source positions and distances  
  > "Right ascension, declination, and distance of each source are from the Gaia DR2 catalog" (Table 1)
- External data: Prior ALMA observations of 12CO, 13CO, C18O, DCO+, H13CO+ used as template filters  
  > "We use prior observations of $^{12}$CO, $^{13}$CO, C$^{18}$O, DCO$^{+}$, and H$^{13}$CO$^{+}$ (cite: Huang_2017) to generate a bank of data-driven template filters" (3.2 Matched filtering) [from (cite: Huang_2017)]
- External data: Disk inclination, PA, stellar and disk parameters in Table 1  
  > "| 0.11$^{[6]}$ | 37$^{[7]}$ | 148$^{[7]}$ |" (Table 1) [from (cite: Huang_2017); (cite: Chiang_2001); (cite: Isella_2012)]

## Processing

### Calibration

- pipeline or manual: Initial calibration by ALMA/NAASC staff; then self-calibration in CASA  
  > "Data was initially calibrated by the ALMA/NAASC staff." (3 Observations)
- casa version: CASA 4.3.1  
  > "Subsequent self-calibration and imaging of the data were completed using `CASA` 4.3.1." (3 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0510+1800  
  > "| A | 2016 Jan. 17 | 36 | 15–331 | 19.2 | J0510+1800 | J0438+3004 | J0510+1800 |" (Table 2)
- flux scale uncertainty: _not stated_
- self calibration: 3 rounds phase-only (100s, 30s, 10s) then one amplitude iteration, on continuum  
  > "Three rounds of phase-only self-calibration on the disk continuum emission were then completed with solution intervals of 100s, 30s, and 10s, followed by one iteration of amplitude self-calibration." (3 Observations)

### Imaging

- task: CLEAN in CASA 4.3.1  
  > "Each of the spectral windows for both sources was imaged with `CLEAN` in CASA 4.3.1, using natural weighting for optimal sensitivity." (4.1)
- deconvolver: _not stated_
- weighting robust: Natural for survey cubes; continuum robust −0.5; strong lines (>20σ) Briggs robust 0.5  
  > "with a Briggs robust parameter of -0.5" (3 Observations); "An identical imaging process was used, but with Briggs weighting and a robust value of 0.5." (4.3)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Elliptical masks: MWC 480 3.5" major axis, i=37, PA=148; LkCa 15 4.5", i=52, PA=60; same in all channels; clean to 4σ  
  > "For MWC 480, the mask had a major axis length of 3.5$''$, inclination of 37$\degree$, and PA of 148$\degree$" (4.1); "They were then `CLEAN`ed down to a threshold of 4$\sigma$" (4.1)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub fit-order = 1  
  > "continuum subtracted using the CASA task `uvcontsub` (fit-order = 1)" (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Executions of the same setting concatenated before imaging  
  > "When a spectral setting had multiple executions taken, the respective measurement sets for each spectral window were concatenated prior to imaging." (4.1)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Matched filtering method  
  > "In (cite: Loomis_2018_MF), we developed a method to efficiently apply matched filters to interferometric observations" (3.2 Matched filtering) [from (cite: Loomis_2018_MF)]
- Bootstrapping flux uncertainty  
  > "sampled with replacement (cite: Bergner_2018)" (4.3) [from (cite: Bergner_2018)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum imaging and uvcontsub
- Image size and cell size
- Exact stacking procedure and filter normalisation details
- Deprojection/radial profile procedure for ring radii
- Rest-frequency sources and hyperfine handling
- Whether the 2013.1.00226.S data were actually used
- Template-filter cubes (Huang et al. 2017) availability

## Analysis recipe

1. **Calibrate and self-calibrate**: Staff calibration, continuum self-calibration applied to full data, uvcontsub  
  > "These calibration tables were applied to the full data for each execution" (3 Observations)
   - software: CASA
   - parameter: solints 100s, 30s, 10s phase; one amplitude; robust -0.5  
  > "solution intervals of 100s, 30s, and 10s" (3 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image full band and extract disk-integrated spectra**: Natural-weighted CLEAN per SPW with fixed elliptical masks; spectra extracted within masks  
  > "disk-integrated spectra were extracted from the image cubes using the elliptical `CLEAN` masks" (4.1)
   - software: CASA
   - parameter: clean threshold 4σ  
  > "They were then `CLEAN`ed down to a threshold of 4$\sigma$" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify lines by matched filtering**: Apply bank of Keplerian data-driven template filters to continuum-subtracted visibilities, yielding filter impulse response spectra  
  > "The interpolated filter is then convolved with the data, producing a normalized filter impulse response spectrum." (3.2 Matched filtering)
   - software: VISIBLE
   - parameter: templates: 12CO, 13CO, C18O, DCO+, H13CO+, plus H2CO, N2H+, CS from survey  
  > "Filters were also created using strong lines of H$_2$CO, N$_2$H$^+$, and CS imaged from the presently described observations." (3.2 Matched filtering)
   - fitting: _not stated_
   - validation: Detection threshold >4σ in filter response  
  > "All spectral lines that were detected by matched filtering in either disk at greater than 4$\sigma$ significance" (4.3)
4. **Image individual lines and measure fluxes**: Natural-weighted CLEAN (robust 0.5 for >20σ lines), 1.5 km/s channels, integrate disk spectra over fixed velocity ranges, bootstrap errors  
  > "Fluxes for each transition were determined by integrating these spectra from 2.0 to 9.5 km s$^{-1}$ and 3.5 to 11 km s$^{-1}$ in MWC 480 and LkCa 15, respectively." (4.3)
   - software: CASA
   - parameter: bootstrap 10000 draws on emission-free channels  
  > "repeating this process 10000 times on randomly selected nearby emission-free channels, sampled with replacement" (4.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare inventories and derive ring radii and upper limits**: Flux ratios as proxy for abundance; deprojected azimuthal profiles for radii; CH3OH upper limit at assumed Tex  
  > "We therefore use the flux density ratios as a rough proxy for abundance comparisons between the two sources." (6.1)
   - assumption: Optically thin emission except CS and N2H+; CH3OH Tex = 25 K  
  > "assuming an excitation temperature of 25 K(cite: Walsh_2016; Carney_2019)" (6.4)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.3.1: Self-calibration, uvcontsub, CLEAN imaging  
  > "Subsequent self-calibration and imaging of the data were completed using `CASA` 4.3.1." (3 Observations)
- **VISIBLE** : Matched filtering of visibilities  
  > "applied to each continuum-subtracted spectral window using the `VISIBLE` package" (3.2 Matched filtering)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Molecular species detected | 14 | not stated | species | 3 | we detect 14 molecular species (including isotopologues) at a $>$4$\sigma$ significance toward MWC 480 and LkCa 15 |
| N2H+ 3–2 flux LkCa 15 | 1750 | 20 | mJy km/s | 4 | 1750 $\pm$ 20 vs 228 $\pm$ 13 mJy km s$^{-1}$ |
| N2H+ 3–2 flux MWC 480 | 228 | 13 | mJy km/s | 4 | 1750 $\pm$ 20 vs 228 $\pm$ 13 mJy km s$^{-1}$ |
| CS 6–5 flux LkCa 15 | 1497 | 19 | mJy km/s | 4 | 1497 $\pm$ 19 vs 811 $\pm$ 19 mJy km s$^{-1}$ |
| 13C18O emission extent MWC 480 | ~120 | not stated | AU | 5 | we find that the emission extends out to $\sim$120 AU |
| N2H+ inner ring radius MWC 480 | ~115 | not stated | AU | 5 | we find an inner ring radius of $\sim$115 AU for MWC 480 and $\sim$40 AU for LkCa 15 |
| N2H+ inner ring radius LkCa 15 | ~40 | not stated | AU | 5 | we find an inner ring radius of $\sim$115 AU for MWC 480 and $\sim$40 AU for LkCa 15 |
| DCO+ 4–3/3–2 flux ratio MWC 480 | ~1.9 | 0.3 | dimensionless | 5 | yields a DCO$^{+}$ 4–3/3–2 flux ratio of $\sim$1.9$\pm0.3$ in MWC 480 |
| CH3OH 3σ upper limit column density | ~8e12 | not stated | cm^-2 | 5 | we find a 3$\sigma$ upper limit column density of $\sim$8$\times$10$^{12}$ cm$^{-2}$ |
| SNR improvement from matched filtering | ~2-3 | not stated | factor | 3 | improved SNR by factors of $\sim$2-3 |

## Qualitative findings

- Species requiring CO freeze-out (N2H+, H2CO) and S-bearing species are brighter toward LkCa 15; hydrocarbons and nitriles brighter toward MWC 480  
  > "Species that require CO freeze-out are enhanced toward LkCa 15" (7 Summary); "Observed transitions of hydrocarbons and nitriles are brighter toward MWC 480." (7 Summary)

## Claim tuples

- H: Can an unbiased ALMA Band 7 survey reveal new molecules in disks? | E: Imaging and matched filtering of 275–317 GHz | R: 14 species detected, 5 new | F: Five species first detected in disks | **supported**
- H: Do the two disks differ in molecular inventory? | E: Compare integrated flux ratios | R: Large differences in many species | F: Differences possibly mostly due to temperature | **partially**
- H: Are COMs present at levels predicted by models? | E: Search and stack CH3OH lines | R: No firm detections; low upper limit | F: Models over-produce gas-phase O-bearing COMs | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Matched filtering gives higher SNR and faster line identification  
  > "Matched filtering of the survey using prior observations as templates allowed much faster line identification than a traditional imaging approach" (7 Summary)
- Alternative: Lower robust values rejected due to higher noise  
  > "Lower values of robustness produced images with substantially higher noise and thus were not used." (4.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Flux ratios are only a rough abundance proxy; high-Eu lines biased by temperature  
  > "we cannot directly compare abundances between the two disks" (6.1)
- Caveat (inferred, ours): Abundance comparisons rely on flux ratios without radiative transfer or excitation modelling
- Caveat (inferred, ours): Fixed elliptical masks and integration ranges may bias fluxes
- Caveat (inferred, ours): Ring radii from low-resolution data lack stated uncertainties

## Reproducibility

- Data public (paper): Project codes listed; VISIBLE public  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00226.S and ADS/JAO.ALMA#2015.1.00657.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: VISIBLE public under MIT license on GitHub  
  > "`VISIBLE` is publicly available under the MIT license at <https://github.com/AstroChem/VISIBLE>" (footnote)
- Missing: Line-free channel ranges
- Missing: Image/cell sizes
- Missing: Template cubes from Huang et al. 2017
- Missing: Radial-profile deprojection details
- Data volume (inferred): ~100–300 GB raw for 9 executions
- Score (inferred): 3/5, Recipe is mostly described and public software exists, but several imaging parameters and templates are missing, and old CASA is required.
- Rediscovery candidate: yes, Public data, tabulated numeric fluxes and a mostly complete recipe.

## Links

- Method: (cite: Loomis_2018_MF) (Matched filter method for interferometric spectra)
- Companion: (cite: LeGal_2019) (S-bearing species analysis)
- Companion: (cite: Bergner_2018) (HC3N and CH3CN survey)
- Companion: (cite: Huang_2017) (Prior deuterium chemistry observations used as templates)
- Related: 2013.1.00226.S

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 77,
  "stated": 47,
  "rate": 0.61
 },
 "evidence_ok": true
}
```
