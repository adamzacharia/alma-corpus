# Hidden in Plain Sight: A Massive, Dusty Starburst in a Galaxy Protocluster at z = 5.7 in the COSMOS Field

`2018ApJ...861...43P` | The Astrophysical Journal 2018 | first author: Pavesi, Riccardo | arXiv: 1803.08048 | DOI: 10.3847/1538-4357/aac6b6

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the properties of the serendipitously discovered dusty starburst CRLE at z=5.667 near HZ10, and does it lie in a galaxy protocluster?  
  > "Here we describe the serendipitous discovery of the brightest and highest redshift dusty starburst in COSMOS" (1 Introduction)
- Target **CRLE (COSMOS Red Line Emitter)**: coordinates J2000 10h0m59.2s, 1d33m6.6s  
  > "This new DSFG is located only 13$^{\prime\prime}$ ($\sim77$ kpc) away from HZ10" (1 Introduction); z/distance z=5.667  
  > "This new DSFG is located only 13$^{\prime\prime}$ ($\sim77$ kpc) away from HZ10" (1 Introduction); distance from line redshift from [CII], [NII], CO(2-1)  
  > "This new DSFG is located only 13$^{\prime\prime}$ ($\sim77$ kpc) away from HZ10" (1 Introduction)
- Target **HZ10**: coordinates _not stated_; z/distance z=5.654  
  > "HZ10, which is an above average dusty but “normal" (i.e., $\sim L^*_{\rm UV}$) galaxy at $z=5.654$" (1 Introduction); distance from Capak et al. 2015; Pavesi et al. 2016  
  > "HZ10, which is an above average dusty but “normal" (i.e., $\sim L^*_{\rm UV}$) galaxy at $z=5.654$" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00523.S, 2015.1.00928.S, 2015.1.00388.S
- bands: Band 7 ([CII], Cycle 1); Band 6 ([NII], Cycle 3)  
  > "were taken on 2013 November 16 in band 7" (2.1); "were taken on 2016 January 1 and 5 in band 6" (2.1)
- frequencies and spectral setup: [CII] setup at 284.835 GHz with 15.6 MHz channels (TDM); [NII] two 1.875 GHz windows per sideband at 15.6 MHz  
  > "The correlator was set up to target the expected frequency of the [Cii] line in HZ10 at 284.835 GHz" (2.1)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 3: compact configuration, max baseline ~300 m  
  > "with one track each in a compact configuration (max. baseline $\sim300\,$m)" (2.1)
- baselines: _not stated_
- angular resolution: [CII] ~0.6"x0.5"; [NII] 1.6"x1.2"  
  > "The synthesized beam size is approximately $0^{\prime\prime}.6\times0^{\prime\prime}.5$, when adopting natural baseline weighting." (2.1); "Imaging these [Nii] data results in a synthesized beam size of $1.6^{\prime\prime} \times 1.2^{\prime\prime}$" (2.1)
- max recoverable scale: _not stated_
- sensitivity: [NII] rms ~0.14 mJy/beam in 44 km/s channel; continuum ~18 uJy/beam  
  > "The rms noise in the phase center is $\sim0.14\,$mJy beam$^{-1}$ in a $44\,$km s$^{-1}$ wide channel." (2.1)
- time on source: 56 min (Cycle 1); 50 and 35 min (Cycle 3)  
  > "The pointing resulted in $56\,$min on source time with 25 usable antennas." (2.1); "The two sets of observations resulted in 50 min, and 35 min on source" (2.1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CII] 158 um (not stated)
- Line: [NII] 205 um (not stated)
- Line: CO 2-1 (VLA) (230.538 GHz)
- Other facility **VLA**: Ka band CO(2-1), 19.8 hr, project 17A-011  
  > "using NSF’s Karl G. Jansky Very Large Array (VLA) in Ka band (project ID: 17A-011, PI: Pavesi)" (2.2)
- Other facility **Herschel, SCUBA-2, HST, Spitzer, HSC**: Continuum photometry for SED  
  > "The SCUBA-2 flux was measured from the S2CLS images (cite: Geach17) and the other fluxes were obtained from the COSMOS2015 catalog (cite: Laigle16)." (Table 1)
- External data: COSMOS2015 photometric catalog and fluxes  
  > "the other fluxes were obtained from the COSMOS2015 catalog (cite: Laigle16)" (Table 1) [from (cite: Laigle16)]
- External data: LAE catalog at z~5.7  
  > "overdensity in the Lyman Alpha Emitter (LAE) catalog at $z\sim5.7$" (5.1) [from (cite: Murayama07)]
- External data: 3 GHz radio flux of CRLE  
  > "CRLE is detected at 7$\sigma$ significance in 3 GHz continuum emission ($24.3\pm3.8\,\mu$Jy; (cite: Smolcic17))" (4.3) [from (cite: Smolcic17)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.5 (ALMA), 4.7 (VLA)  
  > "We used the Common Astronomy Software Application (casa) version 4.5 for data reduction and analysis." (2.1)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (ALMA 2015.1.00388.S); 3C286 (VLA)  
  > "and Callisto was used for flux calibration." (2.1)
- flux scale uncertainty: ~10% (ALMA Band 6 and VLA)  
  > "We estimate the overall accuracy of the flux calibration to be within $\sim10\%$." (2.1)
- self calibration: _not stated_

### Imaging

- task: clean  
  > "produced all images with the clean algorithm" (2.1)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "produced all images with the clean algorithm, using natural weighting for maximal sensitivity" (2.1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: PB attenuation at CRLE ~3 (Band 7), ~1.8 (Band 6)  
  > "The primary beam attenuation factor at the position of CRLE is $\sim1.8$." (2.1)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cycle 1 [CII] data processing and imaging product  
  > "We refer to (cite: Pavesi16) for a complete description of the observations and the imaging product." (2.1) [from (cite: Pavesi16)]
- Overdensity procedure and redshift binning  
  > "We follow the procedure described in (cite: Vernesa_overdens) to evaluate a potential galaxy overdensity around CRLE." (5.1) [from (cite: Vernesa_overdens)]

### Not stated but needed to reproduce (our reading)

- Clean thresholds, masks, cell and image size
- Line-free channel ranges and continuum subtraction method
- Aperture sizes for spectral extraction
- Priors and bounds for dynamical model and MBB fit
- Exact MBB functional form and CMB correction
- Cycle 1 calibration details (in Pavesi16)

## Analysis recipe

1. **Extract line spectra and fit**: Aperture spectra fit with double Gaussians  
  > "we simply extract aperture spectra and fit double Gaussians to the spectral profiles to measure the intrinsic line properties" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure sizes**: uv-plane modeling and uvmodelfit  
  > "Using the casa task uvmodelfit, we measure a deconvolved FWHM major axis size of $0^{\prime\prime}.98\pm0^{\prime\prime}.18$" (3.1)
   - software: CASA uvmodelfit
   - fitting: _not stated_
   - validation: Compared with uv-plane dynamical modeling for [CII]  
  > "obtaining a result that is compatible with our more sophisticated uv plane modeling" (3.1)
3. **Fit FIR SED**: Modified blackbody connected to mid-IR power law, MCMC  
  > "we use a modified blackbody, smoothly connected to a mid-IR power-law. We use *emcee* (cite: emcee) to explore the posterior probability distribution" (4.2)
   - software: emcee
   - assumption: Uniform non-constraining priors; SFR from FIR luminosity with Chabrier IMF  
  > "We employ uniform, non-constraining priors for the parameters" (4.2)
   - fitting: emcee posterior sampling  
  > "We use *emcee* (cite: emcee) to explore the posterior probability distribution" (4.2)
   - validation: _not stated_
4. **Molecular gas mass and alpha_CO**: CO(2-1) luminosity with R21=1; alpha_CO bounded by dynamical mass and gas-to-dust ratio  
  > "By assuming the dynamical mass to be completely accounted for by molecular gas, we can derive a conservative upper limit on the CO conversion factor" (4.4)
   - assumption: R21=1; alpha_CO=1  
  > "we assume a brightness temperature ratio of $R_{21}=1$ between the CO *J*=2–1 and 1–0 lines" (4.4)
   - fitting: _not stated_
   - validation: Compared with dust-based ISM mass estimates  
  > "these dust-based methods would imply very large ISM masses, exceeding our dynamical mass estimate" (4.4)
5. **uv-plane dynamical modeling of [CII]**: KinMSpy disk model fit to visibilities, with and without second component  
  > "The first model fit to CRLE [Cii] is a rotating disk model, generated through the publicly available code *KinMSpy*" (Appendix C)
   - software: KinMSpy, emcee, MultiNest
   - fitting: emcee and MultiNest; uniform, log and sine priors  
  > "We choose uniform priors for additive parameters, logarithmic priors for scale parameters, and a sine prior for the inclination angle." (Appendix C)
   - validation: Evidence ratio e^86 ~1e37 favors two components  
  > "model evidence ratio evaluated through *MultiNest* of $e^{86}\sim10^{37}$" (Appendix C)
6. **Overdensity characterization**: delta_g in COSMOS2015 photo-z and LAE catalogs vs mock random catalogs; Voronoi tessellation  
  > "producing 10 mock random catalogs adopting the same masked regions with the same number of galaxies as the real ones, and measuring the overdensity around 1000 randomly placed centers" (5.1)
   - fitting: _not stated_
   - validation: 5% false-positive rate  
  > "adopting the same 5% false-positive rate as (cite: Vernesa_overdens)" (5.1)

## Software

- **CASA** 4.5 (ALMA), 4.7 (VLA): Data reduction, imaging, uvmodelfit  
  > "We used the Common Astronomy Software Application (casa) version 4.5 for data reduction and analysis." (2.1)
- **emcee** : SED and dynamical model MCMC  
  > "We use *emcee* (cite: emcee) to explore the posterior probability distribution" (4.2)
- **MultiNest (pymultinest)** : Nested sampling and model evidence  
  > "*MultiNest* for `python` (cite: Multinest; pymultinest)" (Appendix C)
- **KinMSpy** : Rotating disk model  
  > "generated through the publicly available code *KinMSpy* (cite: KinMS)" (Appendix C)
- **Cigale** : Foreground galaxy SED fitting  
  > "we use *Cigale* to carry out spectral energy distribution (SED) fitting" (4.1)
- **Galfit** : Foreground galaxy modeling in HST  
  > "We then fit the foreground galaxy with *Galfit*" (4.1)
- **Source Extractor** : HST Kron fluxes  
  > "adopting Kron fluxes as measured by *Source Extractor*" (4.1)
- **gravlens** : Lensing magnification test  
  > "the publicly available code `gravlens` (cite: Keeton01)" (Appendix A)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CII] total line flux | 10.8 | 1.2 | Jy km/s | 1 | / $I$ (Jy km s$^{-1}$) / $10.8\pm1.2$ / $0.73\pm0.15$ / $0.26\pm0.02$ / |
| Mean redshift | 5.6666 | 0.0008 | dimensionless | 1 | / Mean redshift / $5.6666\pm0.0008$ / |
| [CII]/[NII] luminosity ratio | 19 | 4 | dimensionless | 1 | We find a [Cii]/[Nii] line luminosity ratio of $19\pm4$ in CRLE |
| L_FIR (42.5-122.5 um) | 1.55e13 | 0.05e13 | Lsun | 3 | we find a FIR luminosity of $L_{\rm FIR}=(1.55\pm0.05)\times10^{13}\,L_\odot$ |
| SFR | 1550 | 50 | Msun/yr | 3 | we infer a star formation rate of $(1550\pm50)\,M_\odot$ yr$^{-1}$ |
| Dust mass | 1.3e9 | 0.3e9 | Msun | 3 | we find an estimated dust mass of $(1.3\pm0.3)\times10^9\,M_\odot$ |
| Dynamical mass | 1.5e11 | 0.4e11 | Msun | 2 | we derive a dynamical mass of $(1.5\pm0.4)\times10^{11}\,M_\odot$ |
| Molecular gas mass | 7.0e10 | 0.5e10 | Msun | 4 | $M_{\rm gas}= (7.0\pm0.5)\times10^{10} \,M_\odot$ |
| Gas depletion time | 45 | 4 | Myr | 4 | we derive a gas depletion time scale of $45\pm4\,$ Myr |
| Component separation | 2.0 | 0.4 | kpc | 5 | with a component separation of $2.0\pm0.4$ kpc |

## Qualitative findings

- CRLE and HZ10 lie in a galaxy overdensity, likely a protocluster  
  > "which indicates the location of a likely proto-cluster analogous to the case of AzTEC-3" (6 Conclusions)

## Claim tuples

- H: Part of the [CII] emission arises from diffuse ionized gas | E: [CII]/[NII] ratio and [CII]/LIR vs. GOALS relations | R: Ratio 19±4; PDR fraction 84%±4% | F: A significant diffuse ionized gas contribution is suggested | **partially**
- H: CRLE is a merger | E: uv-plane dynamical modeling | R: Single disk is a poor fit; second component strongly preferred | F: Evidence of ongoing merger | **partially**
- H: CRLE lies in a protocluster | E: Overdensity in photo-z and LAE catalogs | R: Significant overdensities, delta_g >~10 within ~5 cMpc in LAEs | F: Likely protocluster | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravitational lensing by foreground galaxy found negligible  
  > "This results in an approximately normally distributed magnification of $\mu=1.09\pm0.02$." (Appendix A)
- How they decided it was enough: _not stated_
- Limitation (authors): [NII] extent uncertain and higher resolution needed  
  > "but higher resolution, and higher signal-to-noise [Nii] observations are necessary to confirm this finding" (3.1)
- Caveat (inferred, ours): Small galaxy numbers make overdensity significance weak
- Caveat (inferred, ours): alpha_CO and R21 assumptions drive gas mass
- Caveat (inferred, ours): Foreground galaxy contaminates optical/NIR so stellar mass is poorly constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Custom uv-space dynamical code not released
- Missing: Cycle 1 calibration details
- Missing: Clean parameters and apertures
- Data volume (inferred): ~50-100 GB for three ALMA datasets
- Score (inferred): 3/5, ALMA projects are listed and tools named, but imaging parameters and custom code are missing.
- Rediscovery candidate: no, Custom modeling and incomplete imaging details prevent straightforward redoing.

## Links

- Method: (cite: Pavesi16) (Full description of the ALMA observations and imaging)
- Method: (cite: Vernesa_overdens) (Overdensity method)
- Companion: (cite: C15) (Original [CII] observations of HZ10)
- Related: COSMOS
- Related: GOALS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
