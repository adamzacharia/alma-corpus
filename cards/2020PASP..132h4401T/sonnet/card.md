# Herschel Observations of Disks around Late-type Stars

`2020PASP..132h4401T` | Publications of the Astronomical Society of the Pacific 2020 | first author: Tanner, Angelle | arXiv: 2004.12597 | DOI: 10.1088/1538-3873/ab895f

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: Do late-type (K5-M5) stars show far-infrared excesses at 100 and 160 micron indicating circumstellar disks, and is the TYC 7443-1102-1 Herschel excess a disk or a background source?  
  > "A set of twenty late-type (K5-M5) stars were observed with the Herschel Space Observatory at 100 and 160 microns with the goal of searching for far-infrared excesses indicative of the presence of circumstellar disks." (abstract)
- Target **TYC 7443-1102-1**: coordinates 19 56 04.4 -32 07 37.7  
  > "TYC 7443-1102-1 is also a $\beta$ Pic Moving Group member at a distance of 51.24$\pm$0.12 pc and an age of 23$\pm$3 Myr" (TYC 7443-1102-1); "TYC 7443-1102-1 | 19 56 04.4 $-$32 07 37.7" (Table 1); z/distance 51.24±0.12 pc  
  > "TYC 7443-1102-1 is also a $\beta$ Pic Moving Group member at a distance of 51.24$\pm$0.12 pc and an age of 23$\pm$3 Myr" (TYC 7443-1102-1); "TYC 7443-1102-1 | 19 56 04.4 $-$32 07 37.7" (Table 1); distance from Gaia Collaboration et al. 2018  
  > "TYC 7443-1102-1 is also a $\beta$ Pic Moving Group member at a distance of 51.24$\pm$0.12 pc and an age of 23$\pm$3 Myr" (TYC 7443-1102-1); "TYC 7443-1102-1 | 19 56 04.4 $-$32 07 37.7" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01583.S
- bands: Band 7 (0.87 mm, 345 GHz)  
  > "observed with ALMA in band 7 (0.87 mm, 345 GHz) on 22 August 2018" (TYC 7443-1102-1)
- frequencies and spectral setup: four windows at 347.883, 335.883, 333.987, 345.987 GHz; 2 GHz wide with 128 channels (last 1.875 GHz, 3840 channels)  
  > "The spectral setup comprised four windows centered on 347.883, 335.883, 333.987 and 345.987 GHz with a width 2 GHz and 128 channels" (TYC 7443-1102-1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 to 483.9 m, 48 antennae  
  > "The observations used baselines ranging from 15.1 to 483.9 m from 48 antennae" (TYC 7443-1102-1)
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: rms 40 uJy/beam  
  > "with a measured rms of 40 $\mu$Jy beam$^{-1}$" (TYC 7443-1102-1)
- time on source: 14.62 minutes  
  > "The total on-source observing duration was 14.62 minutes." (TYC 7443-1102-1)
- observing dates: 22 August 2018  
  > "on 22 August 2018 under project 2017.1.01583.S" (TYC 7443-1102-1)
- pi or archival as stated: PI G. Kennedy (archival use by this paper's authors)  
  > "under project 2017.1.01583.S (PI: G. Kennedy)" (TYC 7443-1102-1)
- Other facility **Herschel PACS**: 100 and 160 micron imaging photometry of 20 stars  
  > "we used the Herschel Photoconductor Array Camera and Spectrometer (PACS) photometer" (Observations and Analysis)
- Other facility **Gaia**: stellar parameters, distances, proper-motion adjusted position  
  > "The first guesses for the stellar radius and temperature are taken from the Gaia catalog" (SED Fitting)
- External data: Optical/near-IR photometry from TYCHO, DENIS, 2MASS  
  > "including TYCHO (H$\o$g et al. 2000), DENIS (Epchtein et al. 2007) and 2MASS (Cutri et al. 2003)" (SED Fitting) [from Høg et al. 2000; Epchtein et al.; Cutri et al. 2003]
- External data: DEBRIS 100 micron fluxes for comparison  
  > "Moro-Martin et al. (2015) report a 100 $\mu$m flux of 19.42$\pm$2.95 mJy for this star." (GJ 784) [from Moro-Martin et al. 2015]
- Simulation/model as data: PHOENIX NextGen stellar spectra grid  
  > "fitted using a grid of K and M dwarf PHOENIX NextGen spectra (Allard & Hauschildt 1995)" (SED Fitting)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script  
  > "The raw data was calibrated with the provided ALMA pipeline script in CASA version 5.1.2-4" (TYC 7443-1102-1)
- casa version: CASA 5.1.2-4  
  > "in CASA version 5.1.2-4 (McMullin et al. 2007)" (TYC 7443-1102-1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: not attempted  
  > "self-calibration was not attempted" (TYC 7443-1102-1)

### Imaging

- task: CLEAN in CASA  
  > "All images were generated with the CLEAN algorithm in CASA." (TYC 7443-1102-1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Continuum imaging was carried out using natural weighting" (TYC 7443-1102-1)
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
- final rms: 40 uJy/beam  
  > "with a measured rms of 40 $\mu$Jy beam$^{-1}$" (TYC 7443-1102-1)

### Inherited from earlier work

- Herschel scan-map parameters from PACS mini scan-map release note  
  > "These parameters are taken from the PACS mini scan-map mode release note (PICC-ME-TN-036, v2.0, 12th Nov. 2010)." (Observations and Analysis) [from PICC-ME-TN-036]
- Excess Ld/L* formulation  
  > "using the formulation given in Beichman et al. (2006)" (Photometry) [from Beichman et al. (2006)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, cell and image size
- Which window(s) used for continuum and flagging of line channels
- Flux calibrator flux scale and uncertainty
- Which of the two calibrators was used for which role
- Photometric aperture corrections for Herschel
- Herschel data reduction pipeline and map-making details

## Analysis recipe

1. **Herschel aperture photometry and excess significance**: Aperture photometry 5'' (100um) and 10'' (160um), sky annulus 20-40''; chi=(Fobs-F*)/sqrt(sig^2+sig*^2)  
  > "apertures of 5$\ensuremath{''}$ and 10$\ensuremath{''}$ in radius for 100 and 160 $\ensuremath{\mu}m$, respectively, and a sky annulus from 20 to 40$\ensuremath{''}$ in radius" (Photometry)
   - fitting: _not stated_
   - validation: _not stated_
2. **SED fitting of star plus blackbody dust**: PHOENIX star plus blackbody dust, radiative equilibrium, amoeba chi2 minimization  
  > "The best fit to the complete SED is achieved with the amoeba minimization algorithm by minimizing the $\chi^2$ value" (SED Fitting)
   - software: amoeba
   - assumption: Dust mass lower limit assuming spherical grains, density 3.5 g/cm3, radius 1.0 um  
  > "assuming spherical grains with a density of 3.5 g/cm$^3$, and radius of 1.0 $\ensuremath{\mu}m$" (SED Fitting)
   - fitting: Parameter errors by varying each parameter until reduced chi2 changed by one  
  > "varying each parameter until the reduced chi square value changed by one" (SED Fitting)
   - validation: _not stated_
3. **Fit ring model to resolved TYC 9340-437-1**: Thin ring (dR/R=0.1) convolved with PSF fit with MCMC  
  > "We use an MCMC procedure (emcee; Foreman-Mackey 2013) to find both the best fit parameters" (TYC 9340-437-1)
   - software: emcee
   - fitting: emcee MCMC; priors not stated  
  > "We use an MCMC procedure (emcee; Foreman-Mackey 2013) to find both the best fit parameters and the range of values that are consistent with the observations." (Results (TYC 9340-437-1))
   - validation: Residuals after subtracting ring model show no significant structure  
  > "The absence of significant residuals from this model subtraction" (TYC 9340-437-1)
4. **ALMA imaging of TYC 7443-1102-1 to test background contamination**: Pipeline calibration, natural-weighted CLEAN continuum, compare source positions to Gaia proper-motion adjusted stellar position  
  > "neither are centered at the Gaia DR2 proper-motion adjusted location of the star" (TYC 7443-1102-1)
   - software: CASA
   - fitting: _not stated_
   - validation: ALMA pointing accuracy ~30 mas compared with offsets  
  > "The ALMA absolute pointing accuracy for this observation is $\sim$30 mas" (TYC 7443-1102-1)

## Software

- **CASA** 5.1.2-4: ALMA calibration and CLEAN imaging  
  > "in CASA version 5.1.2-4 (McMullin et al. 2007)" (TYC 7443-1102-1)
- **emcee** : MCMC ring model fit  
  > "We use an MCMC procedure (emcee; Foreman-Mackey 2013)" (TYC 9340-437-1)
- **Astropy** : general analysis  
  > "made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA Band 7 image rms | 40 | not stated | uJy/beam | 4 | with a measured rms of 40 $\mu$Jy beam$^{-1}$ |
| Flux densities of two ALMA sources near TYC 7443-1102-1 | 1.3 and 0.5 | not stated | mJy | 4 | have flux densities of 1.3 mJy and 0.5 mJy respectively |
| TYC 9340-437-1 ring dust radius | 96 | 7.4 | AU | 3 | corresponding to a dust radius of 96$\pm$7.4 AU |
| TYC 9340-437-1 100um flux | 88.9 | 1.7 | mJy | 1 | With fluxes of 88.9$\pm$1.7 and 98.6$\pm$6.5 mJy at 100 and 160 |
| TYC 7443-1102-1 SED dust temperature | 27 | 4 | K | 2 | dust temperature and radius of 27$\pm$4 K and 37$\pm$12 AU |

## Qualitative findings

- Four of 20 stars show excess; only TYC 9340-437-1 is a robust resolved face-on disk.  
  > "four stars (TYC 7443-1102-1, TYC 9340-437-1, GJ 784 and GJ 707) have infrared excesses above their stellar photospheres" (abstract)

## Claim tuples

- H: Is the Herschel excess of TYC 7443-1102-1 from a circumstellar disk? | E: Band 7 ALMA continuum imaging compared to Gaia position | R: Two sub-mm sources 1.4'' and 0.9'' from star; star undetected | F: Excess most likely from background galaxies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: A disk detected by PACS but not ALMA rejected as needing spectral slope gamma <~ -1  
  > "Thus a scenario where the PACS detection is of a circumstellar disk that is then not detected by ALMA is improbable." (TYC 7443-1102-1)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Single short ALMA continuum observation; background nature inferred from offsets only
- Caveat (inferred, ours): ALMA project code in acknowledgements differs from that in text
- Caveat (inferred, ours): Photosphere excess uncertain for some stars

## Reproducibility

- Data public (paper): ALMA project cited by code; Herschel archival  
  > "under project 2017.1.01583.S (PI: G. Kennedy)" (TYC 7443-1102-1)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: Herschel reduction details
- Data volume (inferred): ~10-20 GB raw for the one ALMA execution
- Score (inferred): 3/5, ALMA part is small and simple but several imaging parameters are missing.
- Rediscovery candidate: no, ALMA role minor; recipe incomplete.

## Links

- Companion: Moro-Martin et al. 2015 (DEBRIS Herschel photometry for comparison)
- Related: DEBRIS
- Related: DUNES
- Related: GASPS

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.01234.S"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 39,
  "rate": 0.574
 },
 "evidence_ok": true
}
```
