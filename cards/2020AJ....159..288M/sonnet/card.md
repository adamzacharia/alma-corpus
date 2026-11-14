# The Big Sibling of AU Mic: A Cold Dust-rich Debris Disk around CP-72 2713 in the β Pic Moving Group

`2020AJ....159..288M` | The Astronomical Journal 2020 | first author: Moór, Attila | arXiv: 2005.00861 | DOI: 10.3847/1538-3881/ab8f98

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: Characterize the newly identified cold debris disk around CP-72 2713 (size, dust and gas content, nature, stirring) using Spitzer, Herschel and ALMA 7-m data  
  > "Based on spatially resolved far-IR Herschel/PACS and millimeter ALMA images of the dust emission, we model the structure of the disk and constrain the location of the dust" (1. INTRODUCTION)
- Target **CP-72 2713**: coordinates _not stated_; z/distance 36.62±0.03 pc  
  > "CP−72 2713 (36.62±0.03 pc, Gaia Collaboration et al. 2018; Lindegren et al. 2018; Bailer-Jones et al. 2018)" (1. INTRODUCTION); distance from Gaia DR2 (Bailer-Jones et al. 2018)  
  > "CP−72 2713 (36.62±0.03 pc, Gaia Collaboration et al. 2018; Lindegren et al. 2018; Bailer-Jones et al. 2018)" (1. INTRODUCTION)

## Data provenance

- ALMA projects: 2016.2.00200.S
- bands: Band 6 (1.33 mm)  
  > "Our Band 6 observations include" (2.3. Observations with the ALMA 7-m Array)
- frequencies and spectral setup: two 1.875 GHz continuum SPWs (128 channels) at 217.0 and 233.5 GHz; 12CO window 468.8 MHz wide, 122.07 kHz channels; 13CO/C18O window 1.875 GHz, 428.28 kHz channels  
  > "two 1.875 GHz wide continuum spectral windows each with 128 channels centered at 217.0 and 233.5 GHz" (2.3. Observations with the ALMA 7-m Array)
- continuum bandwidth: _not stated_
- arrays: ALMA 7-m array, nine antennas  
  > "In both cases nine antennas were involved providing projected baseline lengths ranging between 8.9 and 44.7 m (6.7–33.6 kλ)." (2.3. Observations with the ALMA 7-m Array)
- configurations: _not stated_
- baselines: 8.9–44.7 m (6.7–33.6 kλ)  
  > "projected baseline lengths ranging between 8.9 and 44.7 m (6.7–33.6 kλ)" (2.3. Observations with the ALMA 7-m Array)
- angular resolution: 7.4″×5.5″, PA 6.3°  
  > "The beam size is 7 [′′] . 4×5 [′′] . 5 with a position angle of 6 [◦] . 3." (2.3. Observations with the ALMA 7-m Array)
- max recoverable scale: _not stated_
- sensitivity: rms 0.28 mJy/beam (continuum)  
  > "achieving an rms noise level of 0.28mJy beam [−][1]" (2.3. Observations with the ALMA 7-m Array)
- time on source: _not stated_
- observing dates: 2017 July 25 and 26  
  > "on 2017 July 25 and 26" (2.3. Observations with the ALMA 7-m Array)
- pi or archival as stated: Cycle 4 project, PI Á. Kóspál  
  > "Cycle 4 project (2016.2.00200.S, PI: Á. Kóspál)" (2.3. Observations with the ALMA 7-m Array)
- Line: 12CO J=2-1 (not stated)
- Other facility **Spitzer/MIPS**: 24 and 70 µm photometry  
  > "at 24µm and 70µm on 2008 November 23 (PI: P. Plavchan)" (2.1. Spitzer/MIPS)
- Other facility **Herschel/PACS**: 100 and 160 µm images, marginally resolved at 100 µm  
  > "This implies that CP−72 2713 is marginally resolved at 100µm." (2.2. Herschel/PACS Observations)
- Other facility **TESS**: light curve for rotation period and flares  
  > "providing a very precise, ∼52 days long photometric data set with a cadence of 2 minutes" (3.2. Stellar activity)
- External data: ATCA 9 mm flux 0.096±0.023 mJy  
  > "8820 0.096±0.023 ATCA 10.6×10 [−][5] Norfolk et al. in prep." (Table 1) [from Norfolk et al. in prep.]
- External data: Optical photometry from ASAS used for stellar SED  
  > "we limited our analysis to data that are based on longer term monitoring observations taken from Kiraga (2012)" (3.1. Basic stellar properties of CP−72 2713) [from Kiraga (2012)]
- External data: Dust opacity κν=2.3 cm2 g-1  
  > "By adopting κ ν =2.3 cm [2] g [−][1] for the dust opacity (Andrews et al. 2013)" (3.3.1. The dust component) [from Andrews et al. 2013]
- Simulation/model as data: ACE collisional evolution models, 50 M⊕ belt, wind rates 0/50/300 × solar, used to simulate SED and radial profiles  
  > "We found that disk models with a mass of 50 M ⊕ – which include all solids up to the maximum size of 40 km" (4.3. Collisional evolution)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline script delivered with the data  
  > "utilising the pipeline script delivered with the data" (2.3. Observations with the ALMA 7-m Array)
- casa version: CASA v4.7.2 (calibration); v5.6.2 (imaging)  
  > "v4.7.2; McMullin et al. 2007) utilising the pipeline script" (2.3. Observations with the ALMA 7-m Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% calibration uncertainty  
  > "the quoted uncertainty includes a 10% calibration uncertainty" (2.3. Observations with the ALMA 7-m Array)
- self calibration: _not stated_

### Imaging

- task: tclean in CASA v5.6.2  
  > "We used the tclean task in CASA (v5.6.2, McMullin et al. 2007) to construct the continuum image" (2.3. Observations with the ALMA 7-m Array)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "applying Briggs weighting with a robustness parameter of 0.5" (2.3. Observations with the ALMA 7-m Array)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub on calibrated visibilities before CO imaging  
  > "the continuum emission was subtracted from the calibrated visibilities using the uvcontsub task" (2.3. Observations with the ALMA 7-m Array)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel widths 0.4 km/s (12CO), 1.4 km/s (13CO, C18O)  
  > "the channel width was set to 0.4 km s [−][1] for the [12] CO line and to 1.4 km s [−][1]" (2.3. Observations with the ALMA 7-m Array)
- final beam: 7.4″×5.5″, PA 6.3°  
  > "The beam size is 7 [′′] . 4×5 [′′] . 5 with a position angle of 6 [◦] . 3." (2.3. Observations with the ALMA 7-m Array)
- final rms: 0.28 mJy/beam  
  > "achieving an rms noise level of 0.28mJy beam [−][1]" (2.3. Observations with the ALMA 7-m Array)

### Inherited from earlier work

- Bayesian inference for PACS ring model fit  
  > "we used Bayesian inference following Moór et al. (2015)." (2.2. Herschel/PACS Observations) [from Moór et al. (2015)]
- Isochrone fitting method for stellar mass and age  
  > "we followed the method described by Pascucci et al. (2016)" (3.1. Basic stellar properties of CP−72 2713) [from Pascucci et al. (2016)]
- Correction of rms for channel correlation (×√2.667)  
  > "this rms was multiplied by √2.667 (see Matrà et al. 2019, and references therein)" (2.3. Observations with the ALMA 7-m Array) [from Matrà et al. 2019]
- ACE critical specific energy for disruption setup  
  > "we followed that described by Löhne et al. (2012)" (4.3. Collisional evolution) [from Löhne et al. (2012)]

### Not stated but needed to reproduce (our reading)

- Priors and sampler for the PACS Bayesian ring fit and for the uvmultifit ALMA fit
- Image size, cell size, masking and clean threshold for tclean
- Phase center, source coordinates and ring-model fixed parameters beyond FWHM=0.2R
- Line-free channels and uvcontsub fit order
- Rest frequencies for CO lines
- ACE sensitivity setup details (critical energy parameters, size grid)

## Analysis recipe

1. **Image ALMA continuum and fit ring model in uv plane**: tclean continuum image; Gaussian ring (FWHM 0.2R) fitted to visibilities with uvmultifit after statwt  
  > "we adopted a Gaussian ring model with a fixed FWHM width of 0.2R" (2.3. Observations with the ALMA 7-m Array)
   - software: CASA, tclean, uvmultifit, statwt
   - parameter: Briggs robust 0.5  
  > "applying Briggs weighting with a robustness parameter of 0.5" (2.3. Observations with the ALMA 7-m Array)
   - assumption: Gaussian radial profile, FWHM = 0.2R  
  > "fixed FWHM width of 0.2R" (2.3. Observations with the ALMA 7-m Array)
   - fitting: _not stated_
   - validation: Model and residual CLEAN images show no significant residual in the disk region  
  > "No significant residual emission appears in the disk region." (2.3. Observations with the ALMA 7-m Array)
2. **Fit PACS 100 µm ring model**: Grid of ring models convolved with alpha Boo PSF, Bayesian fit for R, PA, i  
  > "The models have three free parameters: the radius of the ring (R), the position angle (PA, measured east of north), and the inclination" (2.2. Herschel/PACS Observations)
   - software: HIPE
   - fitting: Bayesian inference following Moór et al. (2015)  
  > "we used Bayesian inference following Moór et al. (2015)." (2.2. Herschel/PACS Observations)
   - validation: No residuals >3σ toward source  
  > "toward the source no residuals higher than 3σ were observed" (2.2. Herschel/PACS Observations)
3. **Upper limit on 12CO(2-1) flux**: Spectrum extracted in disk mask (continuum SNR>2), rms scaled by √2.667, 3σ with linewidth 5 km/s  
  > "Using the corrected rms value and this linewidth we derived a 3σ upper limit of 0.216 Jy km s [−][1]" (2.3. Observations with the ALMA 7-m Array)
   - software: CASA
   - assumption: CO co-located with dust; stellar mass 0.71 Msun  
  > "we assumed that the possible CO gas is co-located with the dust material in the disk" (2.3. Observations with the ALMA 7-m Array)
   - fitting: _not stated_
   - validation: _not stated_
4. **SED fit for dust temperature and fractional luminosity**: Single-temperature modified blackbody with λ0 fixed at 100 µm, iterative color corrections  
  > "in the fitting we fixed its value to 100µm" (3.3. Disk properties)
   - software: mpfit
   - assumption: ATLAS9 photosphere, E(B-V)=0, solar metallicity, log g 4.5  
  > "By adopting solar metallicity and a log g of 4.5 dex" (3.1. Basic stellar properties of CP−72 2713)
   - fitting: Levenberg-Marquardt  
  > "We adopted a Levenberg-Marquardt approach (Markwardt 2009)" (3.3. Disk properties)
   - validation: _not stated_
5. **Derive dust and CO gas masses**: Optically thin single-temperature dust mass; LTE optically thin CO mass upper limit for 10–45 K  
  > "Adopting gas temperatures between 10 and 45 K we derived CO mass upper limits in the range of 6.8–9.4×10 [−][6] M ⊕ ." (3.3.2. The gas component)
   - assumption: κν=2.3 cm2/g, grain temperature ~15 K at 140 au  
  > "the temperature of such grains is ∼15 K" (3.3.1. The dust component)
   - fitting: _not stated_
   - validation: _not stated_
6. **Collisional evolution modelling and stirring feasibility**: ACE simulations of a 126–154 au belt with different wind rates; analytic stirring-onset models  
  > "the parent planetesimal belt was assumed to be located between 126 and 154 au corresponding to a radial extent of 0.2R" (4.3. Collisional evolution)
   - software: ACE
   - assumption: size distribution index -1.88, max 1e21 g, e=0.03, wind velocity 400 km/s  
  > "The average initial orbital eccentricity of the planetesimals was set to 0.03." (4.3. Collisional evolution)
   - fitting: _not stated_
   - validation: Model SED compared with measured SED  
  > "reproduce the measured SED at wavelengths ≤ 1.3 mm well" (4.3. Collisional evolution)

## Software

- **CASA** v4.7.2 (calibration), v5.6.2 (imaging): calibration and imaging  
  > "We used the tclean task in CASA (v5.6.2, McMullin et al. 2007)" (2.3. Observations with the ALMA 7-m Array)
- **uvmultifit** : fitting ring model to visibilities  
  > "we used the CASA-based uvmultifit tool (Martí-Vidal et al. 2014)" (2.3. Observations with the ALMA 7-m Array)
- **HIPE** 14.2: PACS data reduction  
  > "Herschel Interactive Processing Environment (HIPE, Ott 2010) version 14.2" (2.2. Herschel/PACS Observations)
- **MOPEX** : co-adding MIPS 70 µm images  
  > "used MOPEX (MOsaicking and Point source Extraction, Makovoz & Marleau 2005) to co-add them" (2.1. Spitzer/MIPS)
- **mpfit** : 2D Gaussian fit and SED fit  
  > "using the mpfit2dpeak IDL procedure (Markwardt 2009)" (2.2. Herschel/PACS Observations)
- **ACE** : collisional evolution simulations  
  > "We utilized the Analysis of Collisional Evolution (ACE, Krivov et al. 2006; Löhne et al. 2008) modelling code" (4.3. Collisional evolution)
- **FLATW'RM** : TESS flare detection  
  > "Flares in the light curve were identified using the FLATW’RM code (Vida & Roettenbacher 2018)" (Appendix A)
- **MUFRAN** : Fourier analysis of TESS light curve  
  > "The remaining data were analyzed using MUFRAN (Kolláth 1990)." (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA ring radius | 140 | ±14 | au | 1 | R = 140±14 au |
| ALMA inclination | 46 | ±12 | deg | 1 | ALMA 1.33 mm 130±16 46±12 140±14 |
| ALMA 1.33 mm flux density | 3.8 | ±0.6 | mJy | 1 | yields a flux density of 3.8±0.6 mJy |
| 12CO(2-1) 3σ upper limit | 0.216 | not stated | Jy km/s | 3 | we derived a 3σ upper limit of 0.216 Jy km s [−][1] |
| PACS 100 µm ring radius | 99 | +22/-26 | au | 2 | PACS 100µm 153 [+60] −64 29 [+26] −21 99 [+22] −26 |
| dust temperature | 43 | ±3 | K | 4 | we derived a dust temperature of 43±3 K and a β of 0.05±0.08 |
| fractional luminosity | 1.1e-3 | not stated | dimensionless | 4 | For the fractional luminosity we obtained f d = 1.1 × 10 [−][3] . |
| dust mass | 0.21 | ±0.03 | Earth masses | 5 | Eq. 1 provides a dust mass estimate of 0.21±0.03 M ⊕ . |
| CO mass upper limit | 6.8–9.4e-6 | not stated | Earth masses | 5 | we derived CO mass upper limits in the range of 6.8–9.4×10 [−][6] M ⊕ . |
| stellar mass | 0.71 | +0.05/-0.03 | Msun | 0 | 0.71 − [+0] 0 [.] . [03] 05 [M] [⊙] |

## Qualitative findings

- No CO emission detected; disk is gas poor and classified as debris  
  > "These findings suggest that our target harbors a gas poor disk" (4.1. Evolutionary status of the disk)
- Classical self-stirring incompatible; planetary stirring or pebble-concentration self-stirring feasible  
  > "is incompatible with the classical self-stirring scenario that assumes slow incremental growth of planetesimals" (5. SUMMARY)

## Claim tuples

- H: Is CP-72 2713's disk an unusually extended debris belt? | E: Fit ring models to ALMA visibilities and compare with other disks | R: R = 140±14 au vs 53±6 au predicted from L*–R relation | F: Disk is outstandingly large for a debris disk | **supported**
- H: Is the disk a debris disk rather than protoplanetary? | E: Compare fd, dust luminosity vs radius, CO limit | R: fd 1.1e-3, no CO, Lmm much lower than protoplanetary at similar size | F: Classified as debris disk | **supported**
- H: Can the belt at 140 au be stirred within 24 Myr? | E: Compare onset-time models with belt radius and age | R: Classical self-stirring too slow; planetary and pebble-concentration models consistent | F: Stirring needs a planet or rapid planetesimal formation | **supported**
- H: Does stellar wind drag explain smaller 100 µm radius? | E: ACE simulated PACS images fitted with same ring model | R: 114 au only for strongest wind at 24 Myr; difference not formally significant | F: Possible but not demonstrated | **partially**

## Reasoning

- Why this data: ALMA 7-m project focused on gas content of young dust-rich debris disks  
  > "a Cycle 4 project (2016.2.00200.S, PI: Á. Kóspál) that focused on the gas content of young dust-rich debris disks" (2.3. Observations with the ALMA 7-m Array)
- Why this method: _not stated_
- Alternative: Background galaxy as source of excess rejected on probability, size and SED grounds  
  > "Based on all of this, we believe that most of the measured millimeter flux is due to the dust disk." (3.4. Source confusion and contamination check)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse resolution; disk width fixed; contamination by faint background sources cannot be ruled out  
  > "positional coincidence with fainter extragalactic objects cannot be completely ruled out" (3.4. Source confusion and contamination check)
- Limitation (authors): Dust opacity systematics not in error budget  
  > "These factors were not considered in our error calculations." (3.3.1. The dust component)
- Caveat (inferred, ours): Peak SNR is only 5.7 at 7 arcsec resolution; ring parameters degenerate with width fixed
- Caveat (inferred, ours): Ring model with fixed 0.2R width is assumed
- Caveat (inferred, ours): Shallow mm slope may indicate contamination, weakening ALMA flux interpretation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: ALMA data from project 2016.2.00200.S (acknowledged as ADS/JAO.ALMA#2017.2.00200.S)  
  > "ADS/JAO.ALMA#2017.2.00200.S" (Acknowledgments)
- Code: _not stated_
- Missing: Priors/sampler for the ring fits
- Missing: tclean image parameters and masks
- Missing: ACE configuration files
- Missing: ATCA data are unpublished
- Data volume (inferred): ~10-30 GB raw for two 7-m execution blocks
- Score (inferred): 3/5, Data and main steps are described, but fit priors, imaging parameters and ACE inputs are missing.
- Rediscovery candidate: yes, The ALMA data are in the archive, the recipe is short and results are numeric (R, i, PA, flux, CO limit).

## Links

- Method: Martí-Vidal et al. 2014 (uvmultifit)
- Method: Matrà et al. 2019 (CO upper limit rms correction)
- Companion: Tanner et al. 2020 (independent study of the same disk)
- Related: 2016.2.00200.S

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.2.00200.S"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 63,
  "rate": 0.685
 },
 "evidence_ok": true
}
```
