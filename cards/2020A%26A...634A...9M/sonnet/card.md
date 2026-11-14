# The flickering nuclear activity of Fornax A

`2020A&A...634A...9M` | Astronomy and Astrophysics 2020 | first author: Maccagni, F. M. | arXiv: 1911.09424 | DOI: 10.1051/0004-6361/201936867

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: What are the timescale and duty cycle of the nuclear activity of Fornax A, from the radio spectrum of its lobes, jets and core?  
  > "we study the radio spectrum of Fornax A, the third brightest nearby radio galaxy (cite: cantiello2013)[^1] after Centaurus A and M 87, to determine the time-scale and the duty-cycle of its nuclear activity." (Introduction)
- Target **Fornax A (NGC 1316)**: coordinates RA 03h22m41.7s, Dec -37d12m30s (J2000)  
  > "| Right Ascension $\alpha$ (J2000) | $03^\mathrm{h}22^\mathrm{m}41.7^\mathrm{s}$ | (\*) |" (Table 1); "| $D_{\rm L}$ | 20.8 Mpc | \(1\) |" (Table 1); z/distance D_L = 20.8 Mpc  
  > "| Right Ascension $\alpha$ (J2000) | $03^\mathrm{h}22^\mathrm{m}41.7^\mathrm{s}$ | (\*) |" (Table 1); "| $D_{\rm L}$ | 20.8 Mpc | \(1\) |" (Table 1); distance from Table 1 reference (1); not named in the text  
  > "| Right Ascension $\alpha$ (J2000) | $03^\mathrm{h}22^\mathrm{m}41.7^\mathrm{s}$ | (\*) |" (Table 1); "| $D_{\rm L}$ | 20.8 Mpc | \(1\) |" (Table 1)

## Data provenance

- ALMA projects: 2017.1.00129.S
- bands: 108 GHz (Band 3), ALMA Morita Array  
  > "Observations of Fornax A centred at 108 GHz were carried out during cycle 5" (2.3 ALMA: 108 GHz)
- frequencies and spectral setup: Three 2-GHz wide continuum spectral windows centred at 113.39, 103.27 and 101.39 GHz; CO(1-0) targeted  
  > "Three 2-GHz wide spectral windows were dedicated to continuum studies (centred at 113.39 GHz , 103.27 GHz and 101.39 GHz, respectively)." (2.3 ALMA: 108 GHz)
- continuum bandwidth: _not stated_
- arrays: ALMA Morita array (ACA), 10 pointings  
  > "consist of 10 different pointings of the ALMA-Morita array within the innermost $2\ensuremath{'}\times3\ensuremath{'}$ of Fornax A" (2.3 ALMA: 108 GHz)
- configurations: _not stated_
- baselines: 8.9 m to 48.9 m  
  > "The chosen array configuration has baselines ranging from 8.9 m to 48.9 m." (2.3 ALMA: 108 GHz)
- angular resolution: 18.1" x 9.0", PA = -89 deg  
  > "The synthesized beam is $18.1\ensuremath{''}\times9.0\ensuremath{''}$ ($\sim 1.8\times 0.99$ kpc) with $PA=-89^\circ$" (2.3 ALMA: 108 GHz)
- max recoverable scale: _not stated_
- sensitivity: 0.21 mJy/beam  
  > "and the noise is $0.21$ mJy beam$^{-1}$." (2.3 ALMA: 108 GHz)
- time on source: _not stated_
- observing dates: 16 October to 21 December 2017  
  > "These observations were taken during an observing campaign that lasted from October 16 to December 21, 2017" (2.3 ALMA: 108 GHz)
- pi or archival as stated: Archival data from ALMA survey of 65 Fornax galaxies (PI Morokuma-Matsui)  
  > "as part of an ALMA survey of $65$ galaxies in the Fornax cluster (PI Kana Morokuma-Matsui, project code 2017.1.00129.S)" (2.3 ALMA: 108 GHz)
- Line: 12CO J=1-0 (115.27 GHz)
- Other facility **MeerKAT**: New L-band observation giving 1.03 and 1.44 GHz images  
  > "We use the MeerKAT observation to generate images of Fornax A at $1.03$ and $1.44$ GHz." (2.1 MeerKAT)
- Other facility **SRT**: New 5.7-6.9 GHz single-dish images  
  > "Fornax A was observed with the SRT on January 26 and February 7, 2017." (2.2 SRT)
- Other facility **MWA, VLA, Planck**: Archival images 84 MHz-217 GHz  
  > "archival data between $84$ MHz and $217$ GHz" (abstract)
- External data: Previously published total flux densities of Fornax A, used for comparison  
  > "we show the total flux density distribution of Fornax A measured in this work along with the previously published measurements of (cite: mckinley2015) and (cite: perley2017)." (Appendix 10) [from (cite: mckinley2015); (cite: perley2017)]
- External data: Magnetic field of lobes B = 2.6 +/- 0.3 uG from synchrotron plus inverse-Compton X-ray modelling  
  > "Assuming that the magnetic field of the lobes is $2.6\pm 0.3\mu$G (cite: isobe2006; tashiro2009)" (5.1 Spectral modelling of the lobes) [from (cite: isobe2006; tashiro2009)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline run at JAO  
  > "The calibration of the Morita-Array observations was conducted with the ALMA pipeline version 40896 (cite: petry2012) at the Joint ALMA Observatory (JAO)." (2.3 ALMA: 108 GHz)
- casa version: _not stated_
- pipeline version: ALMA pipeline version 40896  
  > "The calibration of the Morita-Array observations was conducted with the ALMA pipeline version 40896" (2.3 ALMA: 108 GHz)
- archive products used as is: _not stated_
- flux calibrator: ALMA flux scale per Perley & Butler 2017  
  > "while MeerKAT, SRT and ALMA observations have been calibrated according to (cite: perley2017)." (3.1 The lobes)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean, gridder mosaic  
  > "The continuum image was generated using CASA. In particular, we used the task `tclean` with `Briggs` weighting and `robust` parameter 0.5." (2.3 ALMA: 108 GHz)
- deconvolver: hogbom  
  > "We performed cleaning using the `hogbom` algorithm" (2.3 ALMA: 108 GHz)
- weighting robust: Briggs, robust = 0.5  
  > "we used the task `tclean` with `Briggs` weighting and `robust` parameter 0.5." (2.3 ALMA: 108 GHz)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: auto-threshold: sidelobethreshold 1.25, noisethreshold 5, meanbeamfrac 0.1, lownoisethreshold 2.0, negativethreshold 0.0  
  > "`sidelobethreshold` = 1.25, `noisethreshold` = 5, `meanbeamfrac` = 0.1, `lownoisethreshold` = 2.0, `negativethreshold` = 0.0" (2.3 ALMA: 108 GHz)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Frequency range of 12CO(1-0) and tentative CN at 112.85 GHz flagged  
  > "where the frequency range of the detected $^{12}$CO (1-0) line emission and of the tentative detection of the CN hyper-fine transitions at $112.85$ GHz have been flagged." (2.3 ALMA: 108 GHz)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 18.1" x 9.0"  
  > "The synthesized beam is $18.1\ensuremath{''}\times9.0\ensuremath{''}$" (2.3 ALMA: 108 GHz)
- final rms: 0.21 mJy/beam  
  > "| ALMA - Morita Array$^\star$ | 108 | $8\times10^3$ | $18.1\ensuremath{''}\times 9.0\ensuremath{''}$ | $0.21$ |" (Table 2.1)

### Inherited from earlier work

- MeerKAT data reduction fully described elsewhere  
  > "A complete description of the reduction of this observation can be found in (cite: serra2019)." (2.1 MeerKAT) [from (cite: serra2019)]
- MWA flux-scaling factor 1.325 applied  
  > "the authors calculated a flux-scaling factor of $1.325$. We apply the same scaling factor to our flux measurements" (Appendix 9.1) [from (cite: mckinley2015)]
- ALMA CO(1-0) science goal and data description  
  > "traced by the CO(1-0) line at $\nu_{\rm rest} = 115.27$ GHz (cite: morokuma2019)" (2.3 ALMA: 108 GHz) [from (cite: morokuma2019)]

### Not stated but needed to reproduce (our reading)

- ALMA image size and cell size
- number of clean iterations and threshold
- CASA version used for tclean
- how the 108 GHz continuum flux scale uncertainty was set
- how the kpc-core thermal contamination at 108 GHz was handled in detail
- SYNAGE++ fitting details (grid, priors, error estimation)
- regions used for flux extraction (coordinates)
- whether the fourth spectral window frequency is given (text says three windows but also four)

## Analysis recipe

1. **Image ALMA 108 GHz continuum**: CASA tclean mosaic of the Morita array continuum excluding CO and CN channels  
  > "The continuum image was generated using CASA. In particular, we used the task `tclean` with `Briggs` weighting and `robust` parameter 0.5." (2.3 ALMA: 108 GHz)
   - software: CASA
   - parameter: robust 0.5, hogbom, gridder mosaic  
  > "We performed cleaning using the `hogbom` algorithm within a mask selected by standard `auto-threshold` and mosaicking options" (2.3 ALMA: 108 GHz)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure kpc-core and jet flux densities**: Regrid and convolve all images to 18.1" x 18.1"; core flux = peak in central beam; jets = region sum minus core  
  > "Since the kpc-core is unresolved, its flux density is equal to the peak flux within the central synthesized beam. The flux density of the jets is the sum of the emission in the selected region minus the flux density of the kpc-core." (3.2 The central emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit synchrotron spectra with CI and CI_OFF models**: Fit continuous injection and injection-plus-turn-off models to lobe, core and jet spectra, choosing by reduced chi-squared  
  > "To determine the best-fit models, we use the software package `SYNAGE++` (cite: murgia1999)" (5 Spectral analysis)
   - software: SYNAGE++
   - parameter: B = 2.6 uG for lobes  
  > "Assuming that the magnetic field of the lobes is $2.6\pm 0.3\mu$G (cite: isobe2006; tashiro2009)" (5.1 Spectral modelling of the lobes)
   - assumption: Jaffe & Perola isotropic electron distribution; no escape of particles (T_conf = infinity)  
  > "We assume that the distribution of electrons stays isotropic during its losses, which is known as the Jaffe &Perola approximation (cite: jaffe1973)." (5 Spectral analysis)
   - fitting: reduced chi-squared comparison of CI vs CI_OFF  
  > "We use the reduced-chi-squared to determine which model is best fits the spectrum." (5.1 Spectral modelling of the lobes)
   - validation: _not stated_
4. **Derive radiative ages and activity timeline**: Compute radiative age from break frequency and B; compare to dynamical age; build timeline  
  > "Knowing the magnetic field, and the break-frequency of the spectral energy distribution, from Eq. [\[eq:t_s\]](#eq:t_s), we estimate the radiative ages of the kpc-core and jets." (5.2 Spectral modelling of the central emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging of ALMA continuum  
  > "The continuum image was generated using CASA." (2.3 ALMA: 108 GHz)
- **SYNAGE++** : fitting CI and CI_OFF synchrotron models  
  > "we use the software package `SYNAGE++` (cite: murgia1999)" (5 Spectral analysis)
- **WSclean** : MeerKAT imaging  
  > "Imaging was performed in Stokes I using WSclean (cite: offringa2014)." (2.1 MeerKAT)
- **SoFiA** : source finding for clean masks  
  > "the clean mask was recursively improved by running the source finder SoFiA (cite: serra2015) on the cleaned image." (2.1 MeerKAT)
- **MeqTrees** : MeerKAT self-calibration  
  > "we calibrated, using MeqTrees (cite: noordam2010)" (2.1 MeerKAT)
- **eidos** : MeerKAT primary beam model  
  > "using eidos (cite: asad2019)" (2.1 MeerKAT)
- **AIPS** : VLA 320 MHz reduction  
  > "Calibration and imaging were performed with the Astronomical Image Processing System (AIPS)." (Appendix 9.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 108 GHz kpc-core flux density | 6.7 | 0.4 | mJy | 2 | / 108       / $6.7\pm0.4$ / $(0.0007)$  / |
| Lobes radiative age | ~24 | not stated | Myr | 4 | we infer that the total radiative age of the lobes is $\sim 24$ Myr and that they have not been injected with relativistic particles for the last $12$ Myr. |
| East lobe CI_OFF injection index | 0.57 | +0.02/-0.10 | dimensionless | 3 | the injection spectral index of the particles in the East lobe is $\alpha_{\rm inj}= 0.57^{+0.02}_{-0.10}$ |
| Jets last active | 3 | +7/-2 | Myr ago | 4 | Their last active phase seems to have occurred $3^{+7}_{-2}$ Myr ago |
| kpc-core synchrotron age | ~1 | +0.3/-0.5 | Myr | 4 | the age of the synchrotron emission is $\sim 1^{+0.3}_{-0.5}$ Myr |

## Qualitative findings

- Lobes have double-shell morphology with filaments in diffuse cocoon  
  > "the lobes of Fornax A have a double-shell morphology, where dense filaments are embedded in a diffuse and extended cocoon." (abstract)

## Claim tuples

- H: Were the lobes formed by multiple episodes of nuclear activity? | E: Compared radiative age (~24 Myr) with dynamical age (~200 Myr) and spectral fits | R: CI_OFF fits lobes best; dynamical age much exceeds radiative age | F: Multiple episodes inflated the lobes; last injection started ~24 Myr ago and stopped 12 Myr ago | **supported**
- H: Is the central emission a remnant of the lobe-forming activity? | E: CI and CI_OFF fits to kpc-core and jets including ALMA 108 GHz | R: Jets better fit by CI_OFF (~3 Myr), core by CI | F: Fornax A is rapidly flickering and the core may be active again | **supported**

## Reasoning

- Why this data: Arcsecond-resolution data needed to resolve central emission; ALMA 108 GHz used for core at high frequency  
  > "To achieve the second goal we need images with $\sim 10\ensuremath{''}$ angular resolution to resolve the central emission." (2 Multi-wavelength observations)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Core result holds only if thermal contamination of 108 GHz flux is below ~80%, which is poorly constrained  
  > "This result holds as long as the thermal contamination to the 108 GHz flux of the kpc-core, poorly constrained by currently available data, is $\lesssim 80\%$." (5.2)
- Caveat (inferred, ours): Core flux at 108 GHz from one low-resolution ACA point drives the CI vs CI_OFF choice for the core
- Caveat (inferred, ours): Reduced chi-squared with correlated errors is a weak model discriminator
- Caveat (inferred, ours): Radiative ages depend on assumed constant B

## Reproducibility

- Data public (paper): ALMA data cited by project code; acknowledged as ADS/JAO.ALMA#2017.1.00129.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00129.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: MeerKAT pipeline repository linked (meerkathi/stimela); SYNAGE++ not released in paper  
  > "<https://github.com/ska-sa/meerkathi>" (footnote 2)
- Missing: MeerKAT and SRT data access not described
- Missing: SYNAGE++ configuration
- Missing: flux extraction regions
- Missing: ALMA image/cell size
- Data volume (inferred): ALMA ACA 108 GHz continuum: a few GB; MeerKAT data tens to hundreds of GB
- Score (inferred): 3/5, ALMA imaging recipe is mostly given but the main science needs MeerKAT, SRT and other data and unreleased modelling software.
- Rediscovery candidate: no, ALMA is a minor part and the main results depend on non-ALMA data and SYNAGE++.

## Links

- Method: (cite: murgia1999) (SYNAGE++ spectral ageing package)
- Method: (cite: serra2019) (MeerKAT reduction)
- Companion: (cite: morokuma2019) (ALMA CO survey of Fornax galaxies)
- Companion: (cite: serra2019) (H I analysis of the same MeerKAT observation)
- Related: MeerKAT Fornax Survey
- Related: GLEAM
- Related: ALMA survey of 65 Fornax cluster galaxies

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 50,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
