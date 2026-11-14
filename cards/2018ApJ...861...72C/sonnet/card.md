# ALMA Resolves C I Emission from the β Pictoris Debris Disk

`2018ApJ...861...72C` | The Astrophysical Journal 2018 | first author: Cataldi, Gianni | arXiv: 1804.06479 | DOI: 10.3847/1538-4357/aac5f3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks
- Question: What is the spatial distribution and mass of atomic carbon (C I) in the beta Pic debris disk, and does C share the CO clump asymmetry?  
  > "We resolve C I emission at 492 GHz using ALMA and study its spatial distribution. C I shows the same clump as seen for CO." (abstract)
- Target **beta Pictoris**: coordinates _not stated_; z/distance not stated (1 arcsec ~ 19-20 au implied)  
  > "around a 1.75 M$_\Sun$ star (cite: Crifo_etal_1997), seen edge-on" (5.2 Comparison); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00459.S
- bands: Band 8  
  > "We observed the $\beta$ Pic disk using band 8 receivers of ALMA on December 19, 2015" (2 Observations and data reduction)
- frequencies and spectral setup: 3 SPWs of 1920 channels, 488 kHz spacing (937.5 MHz) on C I, CS 10-9, SiO 11-10; 4th SPW 128 channels, 1875 MHz at 479 GHz for continuum  
  > "three spectral windows, each with 1920 channels and a channel spacing of 488 kHz (total bandwidth 937.5 MHz)" (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 36 antennas, hybrid configuration, 3-pointing mosaic  
  > "The array consisted of 36 antennas arranged in a hybrid configuration" (2 Observations and data reduction)
- configurations: _not stated_
- baselines: 15 m to 6.3 km; baselines >2 km flagged  
  > "We therefore flagged all baselines longer than 2 km, effectively removing one third of the baselines." (2 Observations and data reduction)
- angular resolution: 1.18'' x 0.95'' (tapered 1'')  
  > "The beam size is 1.18$''$$\times$0.95$''$ (23 au$\times$19 au)" (3.1 Line emission)
- max recoverable scale: _not stated_
- sensitivity: ~70 mJy/beam per channel (line)  
  > "($\sim$70 mJy beam$^{-1}$) in the individual channels" (3.1 Line emission)
- time on source: 2.1 h total, 1.2 h on beta Pic; median pwv 0.6 mm  
  > "The total integration time was 2.1 h (with 1.2 h on $\beta$ Pic)" (2 Observations and data reduction)
- observing dates: December 19, 2015 (Cycle 3)  
  > "on December 19, 2015 during the ALMA cycle 3 Early Science campaign" (2 Observations and data reduction)
- pi or archival as stated: PI Brandeker  
  > "project ID 2013.1.00459.S, PI: Brandeker" (2 Observations and data reduction)
- Line: C I 3P1-3P0 (492.16 GHz)
- Line: CS 10-9 (489.75 GHz)
- Line: SiO 11-10 (477.50 GHz)
- Other facility **Herschel HIFI/PACS**: C II fluxes and spectrally resolved line used with C I  
  > "previously published spectrally resolved *Herschel*/HIFI observation of C II" (4.2 3D modelling)
- External data: ALMA CO 2-1 and 3-2 data cubes  
  > "Luca Matrà kindly provided the ALMA CO 3–2 and 2–1 data as well as the model of the dust radiation field." (Acknowledgments) [from Matra_etal_2017]
- External data: C II HIFI spectrum  
  > "previously published spectrally resolved *Herschel*/HIFI observation of C II (cite: Cataldi_etal_2014)" (4.2 3D modelling) [from Cataldi_etal_2014]
- External data: C II PACS flux from summed spaxels  
  > "we sum the flux values of the PACS spaxels listed in their table 1" (4.1) [from Brandeker_etal_2016]

## Processing

### Calibration

- pipeline or manual: Manual standard calibration with WVR and Tsys; bad antennas DA44, DA54 flagged  
  > "We performed standard water vapour radiometre (WVR) calibration and system temperature corrections." (2 Observations and data reduction)
- casa version: CASA 4.7.0  
  > "The data were calibrated using CASA 4.7.0 (cite: McMullin_etal_2007)." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 used for bandpass and flux  
  > "we discarded the data from the two flux calibrators and instead used J0522-3627 to calibrate both bandpass and flux" (2 Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "We then imaged the visibilities using the `CLEAN` task within CASA." (2 Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: 1''  
  > "we applied a taper of 1$''$" (2 Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub  
  > "we performed continuum subtraction using the `uvcontsub` task within CASA" (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: Not applied  
  > "We did not correct for the primary beam, as it changes the total flux only within the quoted error bars" (3.1 Line emission)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.18'' x 0.95'' PA 44 deg (line); 1.19'' x 0.96'' PA 46 deg (continuum)  
  > "The beam size is 1.19$''$$\times$0.96$''$ (23 au$\times$19 au) with the position angle of the major axis being 46$^\circ$." (3.3 Continuum)
- final rms: _not stated_

### Inherited from earlier work

- Deprojection of pv diagram following earlier work (edge-on, flux in front of sky plane)  
  > "for simplicity, we follow (cite: Dent_etal_2014) and assume that the disk is edge-on" (3.2 Deprojection) [from Dent_etal_2014]
- Mean molecular weight mu=14  
  > "For the mean molecular weigh $\mu$, we follow (cite: Matra_etal_2017) and assume $\mu=14$." (4.2.1) [from Matra_etal_2017]
- Clump azimuth fixed at -32 deg  
  > "We fix $\phi_{\mathrm{c}}=-32\ensuremath{^\circ}$ (cite: Matra_etal_2017)." (4.2.2) [from Matra_etal_2017]
- Chi2 definition analogous to Booth et al. eq. 2  
  > "we assign a $\chi^2$ measure by using expressions analogous to equation 2 in (cite: Booth_etal_2017)" (4.2.1) [from Booth_etal_2017]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (weighting/robust, cell, image size, threshold, masks, channel width of cubes)
- Line-free channels for uvcontsub
- Pixel positions of rectangular boxes and p-v region mask definition
- Stellar distance adopted
- Dust radiation field model from Kral+2017 (private communication) and CO cubes
- Ionisation rate/recombination coefficient details
- Grid-search chi2 noise correlation ratios

## Analysis recipe

1. **Calibrate and image C I cube and continuum**: CASA calibration, flag baselines >2 km, uvcontsub, tapered CLEAN  
  > "We then imaged the visibilities using the `CLEAN` task within CASA." (2 Observations and data reduction)
   - software: CASA
   - parameter: 1'' taper  
  > "we applied a taper of 1$''$" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line flux, profiles and pv diagram**: Moment 0 within +-6 km/s, rectangular aperture photometry, errors from emission-free sample volumes; pv restricted region  
  > "integrating the data cube along the spectral axis within $\pm6$ km s$^{-1}$" (3.1)
   - fitting: _not stated_
   - validation: Compared with single-dish flux of Higuchi et al.  
  > "The measured flux is consistent with the value of $(1.7\pm0.4)\times10^{-19}$ W m$^{-2}$" (3.1)
3. **Estimate total carbon mass with 1D non-LTE model**: pythonradex (RADEX-like) uniform sphere, electrons as colliders, fit C II (PACS) and C I flux over Tkin 40-1000 K  
  > "we use `pythonradex`, a python implementation of the RADEX code" (4.1)
   - software: pythonradex
   - parameter: b = 0.57 km/s; sphere volume equals torus with 35 au x 10 au  
  > "Here we used $b = 0.57$ km s$^{-1}$, derived in appendix" (4.1)
   - assumption: Carbon ionisation provides the electrons; uniform sphere geometry  
  > "photoionisation of carbon is the main electron source" (4.1)
   - fitting: _not stated_
   - validation: LTE comparison; size varied by 50%  
  > "increasing or decreasing the radius of the emitting sphere by 50% does not change the lower bound by more than 15%" (4.1)
4. **3D models of ring, ring+clump and eccentric gas**: Grid search with chi2 summed over C I (ALMA) and C II (HIFI); T=75 K isothermal; ionisation balance and SE solved per cell  
  > "We sum the $\chi^2$ from the *Herschel*/HIFI data (C II) and the ALMA data (C I)." (4.2)
   - software: pythonradex, LIME
   - parameter: Tkin = 75 K  
  > "we consider isothermal models and fix $T_\mathrm{kin}=75$ K everywhere" (4.2)
   - fitting: grid search chi2, parameter ranges in Tables 1-2  
  > "Explored parameter space and best fit values for the ‘ring’ and ‘ring + clump’ models" (Table 1)
   - validation: LIME full radiative transfer differs by at most factor 1.2  
  > "the total flux computed by `LIME` differs at most by a factor 1.2 for both C I and C II" (Approximate SE appendix)
5. **Fit line broadening parameter**: Gaussian fit to vertical cut at x=0 of pv diagrams, emcee MCMC  
  > "We use 100 walkers with $10^4$ steps." (Line broadening appendix)
   - software: emcee
   - fitting: emcee, chi2 likelihood, uninformative priors with positivity  
  > "We consider invariant, uninformative priors, imposing only that the peak of the Gaussian and the broadening parameter are positive." (Line broadening appendix)
   - validation: Three independent measurements combined by weighted mean  
  > "Combining these measurements as a weighted mean yields $b=0.57\pm0.03$ km s$^{-1}$." (Line broadening appendix)
6. **Derive CO/C production timescale**: C mass divided by CO mass loss rate using revised CO lifetime of 50 a  
  > "a CO lifetime of 50 a leads to a CO mass loss rate of $1.2\times10^{11}$ kg s$^{-1}$" (5.3)
   - assumption: Constant CO loss rate; C only from CO; no C removed  
  > "1) the CO mass loss rate is constant, 2) C is produced only from CO photodissociation" (5.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0: calibration and imaging  
  > "The data were calibrated using CASA 4.7.0" (2 Observations and data reduction)
- **pythonradex** : non-LTE radiative transfer for 1D model and 3D models  
  > "we use `pythonradex`" (4.1)
- **emcee** : MCMC for broadening parameter errors  
  > "We estimate errors using `emcee`" (Line broadening appendix)
- **LIME** 1.9.1: full non-LTE radiative transfer check  
  > "we used the `LIME` code version 1.9.1" (Approximate SE appendix)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| C I total flux | 1.6e-19 W m-2 (9.8 Jy km/s) | 0.2e-19 W m-2 (1.4 Jy km/s) | W m-2 | 2 | $(1.6\pm0.2)\times10^{-19}$ W m$^{-2}$ ($9.8\pm1.4$ Jy km s$^{-1}$) |
| Continuum flux ~485 GHz | 112 | 7 | mJy | 2 | ($112\pm7$ mJy) |
| Total carbon mass | 5e-4 to 3.1e-3 | range | M_earth | 3 | we determine a total carbon mass between $5\times10^{-4}$ and $3.1\times10^{-3}$ M$_\ensuremath{\oplus}$ |
| Line broadening b | 0.57 | 0.03 | km/s | 5 | $b=0.57\pm0.03$ km s$^{-1}$ |
| C production timescale | 1.7e3 to 1.1e4 | range | yr | 6 | we find a timescale between $1.7\times10^3$ and $1.1\times10^4$ years |
| SW/NE flux ratio (pv-restricted) | 1.2 | 0.2 | dimensionless | 2 | The SW/NE flux ratio (within the same box as in figure 1) is now $1.2\pm0.2$. |

## Qualitative findings

- No C I emission beyond ~120 au or inside ~50 au; no atomic accretion disk  
  > "no atomic accretion disk has formed (yet) as there seems to be little C I emission inside of $\sim$50 au" (4.3)

## Claim tuples

- H: Does C I share the CO clump asymmetry? | E: Resolved C I map and profile compared with CO | R: C I follows CO 2-1 profile with SW peak | F: Asymmetry is real, though statistical significance is marginal | **partially**
- H: Is gas production recent? | E: C mass divided by CO loss rate | R: 1.7e3-1.1e4 yr | F: Gas production started within ~5000 yr | **supported**
- H: Does Kral+2016 accretion disk exist? | E: Model emission compared to data | R: Model overpredicts inner C I | F: No atomic accretion disk | **supported**
- H: Resonance trapping explains the clump | E: Timescale and geometry argument | R: C integrated over ~10 orbits should be spread | F: Excluded | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Giant impact, resonance trapping, secular forcing disfavoured  
  > "our observation disfavours a few proposed scenarios (planet MMR trapping, giant impact, secular forcing)" (5.5.6)
- How they decided it was enough: _not stated_
- Limitation (authors): Data did not initially pass QA2 due to low elevation and array configuration  
  > "the data initially did not pass Quality Assurance 2 (QA2)" (2 Observations and data reduction)
- Limitation (authors): Uniform sphere geometry is a clear limitation; masses are first-order  
  > "The assumption of a uniform sphere is thus a clear limitation of this model." (4.1)
- Caveat (inferred, ours): No error bars on dynamical mass or grid-search parameters
- Caveat (inferred, ours): Marginal significance of asymmetry
- Caveat (inferred, ours): Mass upper bound sensitive to temperature, volume and b
- Caveat (inferred, ours): Tidal disruption is speculative

## Reproducibility

- Data public (paper): ALMA data cited by project ID; CO data from private communication  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00459.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: pythonradex on GitHub  
  > "pythonradex (<https://github.com/gica3618/pythonradex>)" (Software)
- Missing: CLEAN parameters
- Missing: Kral+2017 dust field model (private communication)
- Missing: 3D model code not released
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public data and software named, but imaging parameters and model code are incomplete.
- Rediscovery candidate: no, Imaging recipe is incomplete and key inputs (CO cubes, dust field) are not public.

## Links

- Method: Matra_etal_2017 (Deprojection and CO data)
- Method: Booth_etal_2017 (Chi2 definition)
- Companion: Dent_etal_2014 (Original CO 3-2 ALMA clump)
- Companion: Higuchi_etal_2017 (Single-dish C I detection)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 54,
  "rate": 0.651
 },
 "evidence_ok": true
}
```
