# The MESAS Project: ALMA Observations of the F-type Stars γ Lep, γ Vir A, and γ Vir B

`2020ApJ...894...76W` | The Astrophysical Journal 2020 | first author: White, Jacob Aaron | arXiv: 2003.12284 | DOI: 10.3847/1538-4357/ab8467

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, debris_disks
- Question: What are the submm/mm fluxes and chromospheric structure of debris-poor F-type stars, and is there short-term variability or bias for debris disk studies?  
  > "We use these data to constrain semi-empirical atmospheric models. We discuss the atmospheric structure of these stars, explore potential short term variability, and the potential impact on debris disk studies." (abstract)
- Target **gamma Lep**: coordinates RA 05h44m27.79s, Dec -22d26m54.18s (J2000)  
  > "The observations of $\gamma$ Lep used the J2000 coordinates of R.A. = $05^{\rm h}\, 44^{\rm m}\, 27^{\rm s}.79$" (2 Observations); "at the system distance of 8.9 pc for Bands 7 and 6, respectively." (2.1 gamma Lep); z/distance 8.9 pc  
  > "The observations of $\gamma$ Lep used the J2000 coordinates of R.A. = $05^{\rm h}\, 44^{\rm m}\, 27^{\rm s}.79$" (2 Observations); "at the system distance of 8.9 pc for Bands 7 and 6, respectively." (2.1 gamma Lep); distance from not stated (Table lists 8.93 pc with footnote a)  
  > "The observations of $\gamma$ Lep used the J2000 coordinates of R.A. = $05^{\rm h}\, 44^{\rm m}\, 27^{\rm s}.79$" (2 Observations); "at the system distance of 8.9 pc for Bands 7 and 6, respectively." (2.1 gamma Lep)
- Target **gamma Vir A/B**: coordinates RA 12h41m39.62s, Dec -01d26m57.82s (J2000, centered on gamma Vir A)  
  > "the observations of the $\gamma$ Vir system were centered on $\gamma$ Vir A using the J2000 coordinates of R.A. $= 12^{\rm h}\, 41^{\rm m}\,  39^{\rm s}.62$" (2 Observations); "corresponding to $\sim 8.7$ au at the system distance of 11.7 pc." (2.2 gamma Vir); z/distance 11.7 pc  
  > "the observations of the $\gamma$ Vir system were centered on $\gamma$ Vir A using the J2000 coordinates of R.A. $= 12^{\rm h}\, 41^{\rm m}\,  39^{\rm s}.62$" (2 Observations); "corresponding to $\sim 8.7$ au at the system distance of 11.7 pc." (2.2 gamma Vir); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00698.S, 2018.1.01149.S
- bands: Band 6 (1.29 mm) and Band 7 (0.87 mm)  
  > "We observed both targets with ALMA Band 6 and Band 7" (2 Observations)
- frequencies and spectral setup: 4 SPWs, each 128x15.625 MHz channels; Band 6 centered 224, 226, 240, 242 GHz; Band 7 centered 336.5, 338.4, 348.5, 350.5 GHz  
  > "The Band 6 SPWs were centered at 224 GHz, 226 GHz, 240 GHz, and 242 GHz, giving an effective continuum frequency of 233 GHz (1.29 mm)." (2 Observations)
- continuum bandwidth: 8 GHz total  
  > "a total continuum bandwidth of 8 GHz split among 4 spectral windows (SPW)" (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15-1397 m (gamma Lep); 15-500 m and 15-313 m (gamma Vir Band 7); 15-312 m (Band 6)  
  > "43 antenna configuration with baselines ranging from $15 - 1397$ m" (2.1 gamma Lep)
- angular resolution: gamma Lep 0.25x0.20" (B7), 0.36x0.30" (B6); gamma Vir 0.79x0.69" (B7), 1.43x1.25" (B6)  
  > "$0.25\ensuremath{''}\times 0.20\ensuremath{''}$ at a position angle (PA) of $83.1^{\circ}$ for Band 7" (2.1 gamma Lep)
- max recoverable scale: _not stated_
- sensitivity: gamma Lep 30 (B7), 10 (B6) uJy/beam; gamma Vir 15 (B7), 10 (B6) uJy/beam  
  > "The Band 7 data achieve a $\sigma_{rms}$ sensitivity of $30~\rm \mu Jy~beam^{-1}$" (2.1 gamma Lep)
- time on source: gamma Lep 18.5 min (B7), 42.0 min (B6); gamma Vir 29.4 min per EB (B7), ~34.5 min (B6)  
  > "for 36.1 min (18.5 min on-source)" (2.1 gamma Lep)
- observing dates: 2018 Sep-2019 Mar (see Table)  
  > "The Band 7 observations were made on 2018 December 20 for 49.2 min (29.4 min on-source) and 2019 March 20" (2.2 gamma Vir)
- pi or archival as stated: Own proposals, PI White  
  > "We observed $\gamma$ Lep and $\gamma$ Vir with ALMA during Cycle 5 (ID 2017.1.00698.S, PI White)" (2 Observations)
- Other facility **Herschel/PACS**: Far-IR photometry of gamma Lep (100, 160 um) used to constrain the atmosphere model  
  > "adjust the synthetic spectrum to the ALMA data presented here and the *Herschel*/PACS data for $\gamma$ Lep (cite: montesinos16)" (3.3 Stellar atmosphere models)
- External data: Herschel/PACS fluxes for gamma Lep  
  > "the *Herschel*/PACS data for $\gamma$ Lep (cite: montesinos16)" (3.3 Stellar atmosphere models) [from Montesinos et al. 2016 (cite: montesinos16)]
- External data: Solar semi-empirical model used as starting atmosphere  
  > "a semi-empirical Solar model (cite: avrett) in hydrostatic equilibrium was adopted as the starting point" (3.3 Stellar atmosphere models) [from Avrett & Loeser 2008 (cite: avrett)]
- External data: Stellar parameters (distance, radius, Teff) in Table  
  > "Effective temperature, T$_{eff}$ (K) | 5800$\pm$5$^c$ | 6255$\pm$70$^b$ | 6730$\pm$300$^d$ | 6694$^e$" (Table 2) [from footnotes a-e not given in text]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "All of the data were reduced using the Common Astronomy Software Applications (CASA 5.4.1) pipeline" (2 Observations)
- casa version: CASA 5.4.1  
  > "CASA 5.4.1" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0522-3627 (gamma Lep); J1256-0547 (gamma Vir)  
  > "Quasar J0522-3627 was the flux and bandpass calibrator" (2.1 gamma Lep)
- flux scale uncertainty: ~10%  
  > "which we adopt as $\sim10\%$ (this is the commonly adopted uncertainty at these wavelengths per Sec. A.9.2 in the ALMA Proposer’s Guide)" (3.1 Visibility model fitting)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN  
  > "Both of the bands were imaged using the CASA *CLEAN* algorithm" (2.1 gamma Lep)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using threshold of $\frac{1}{2}~\sigma_{rms}$ and natural weighting" (2.1 gamma Lep)
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
- final beam: see angular_resolution  
  > "The size of the resulting synthesized beam is $1.43\ensuremath{''}\times 1.25\ensuremath{''}$ at a position angle of $-65.2^{\circ}$" (2.2 gamma Vir)
- final rms: 10-30 uJy/beam  
  > "Together, these Band 6 data achieve a $\sigma_{rms}$ sensitivity of $10~\rm \mu Jy~beam^{-1}$ in the CLEANed image." (2.2 gamma Vir)

### Inherited from earlier work

- Point-source uvmodelfit flux measurement approach  
  > "we utilize the same approach used in (cite: white18; white19) and obtain the flux using the CASA task *uvmodelfit*" (3.1 Visibility model fitting) [from (cite: white18; white19)]
- Debris mass calculation methods  
  > "Adopting the methods in (cite: white_fom), a lower level total debris mass can be calculated" (4.3 Relevance for debris disk studies) [from (cite: white_fom)]

### Not stated but needed to reproduce (our reading)

- CLEAN mask, niter, cell and image size
- Whether pipeline products were used or manually re-imaged; spectral line flagging
- uvmodelfit starting parameters
- KINICH-PAKAL settings, convergence criteria and weighting of data points
- Source of stellar parameters (footnotes a-e)
- How per-scan time series were binned and uncertainties assigned
- Gamma Vir EB combination procedure

## Analysis recipe

1. **Image continuum**: CLEAN with natural weighting, threshold 1/2 sigma_rms  
  > "using threshold of $\frac{1}{2}~\sigma_{rms}$ and natural weighting" (2.1 gamma Lep)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure stellar fluxes**: Point-source uvmodelfit to visibilities per EB  
  > "obtain the flux using the CASA task *uvmodelfit* and a point source model for all targets" (3.1 Visibility model fitting)
   - software: CASA uvmodelfit
   - assumption: Stars are point sources; absolute flux uncertainty ~10%  
  > "All of the stars observed are effectively point sources given the achieved synthesized beams." (3.1 Visibility model fitting)
   - fitting: Iterative chi^2 minimization  
  > "This approach converges on a minimum $\chi^{2}$ through an iterative procedure." (3.1 Visibility model fitting)
   - validation: _not stated_
3. **Characterize background source near gamma Vir**: Point and Gaussian uvmodelfit; Gaussian preferred; spectral index and beta from two bands  
  > "we fit both a point source and Gaussian model to the object with *uvmodelfit* and find it to be more consistent with a Gaussian." (3.2 Additional source)
   - software: CASA uvmodelfit
   - assumption: Rayleigh-Jeans regime, S_nu ∝ nu^(2+beta)  
  > "assuming the object is in the Rayleigh-Jeans regime with $S_\nu \propto \nu^{2+\beta}$" (3.2 Additional source)
   - fitting: _not stated_
   - validation: Compared expected high-z galaxy counts (~0.5 in field)  
  > "meaning the expected number of objects within our ALMA Band 6 field-of-view is about 0.5" (3.2 Additional source)
4. **Fit semi-empirical chromosphere models**: KINICH-PAKAL iteratively modifies temperature/density profiles, ionization and opacity of a solar base model to fit ALMA and Herschel data  
  > "This code iteratively modifies the radial temperature and hydrogen density profiles, the ionization balance, and the opacity of a base model using the Levenberg-Marquardt algorithm" (3.3 Stellar atmosphere models)
   - software: KINICH-PAKAL
   - assumption: Non-LTE ionization-excitation and radiative transfer; hydrostatic equilibrium Avrett & Loeser solar starting model  
  > "we do not assume that ionization-excitation and radiative transfer are in local thermal equilibrium" (3.3 Stellar atmosphere models)
   - fitting: Levenberg-Marquardt  
  > "using the Levenberg-Marquardt algorithm to adjust the synthetic spectrum" (3.3 Stellar atmosphere models)
   - validation: Synthetic spectrum compared with observed  
  > "leading the synthethic spectrum to be in agreement with the observed one shown in Fig. [3](#tb_plot)" (3.3 Stellar atmosphere models)
5. **Assess short-term variability**: uvmodelfit applied to each on-source scan (6-8 min between phase calibrations); compare stars with background source  
  > "We can therefore further divide up the observations into increments of $6-8$ minutes between individual phase calibrations" (4.2 Potential millimeter wavelength variability)
   - software: CASA uvmodelfit
   - assumption: Background source has constant flux  
  > "the assumption that it has a relatively constant flux during each EB" (3.2 Additional source)
   - fitting: _not stated_
   - validation: Qualitative comparison of time series  
  > "While the curves are indeed not flat, they are roughly consistent with the full integrated flux and there is likely no variability at the level of the flux calibrations over the course of the observations." (Potential millimeter wavelength variability)
6. **Estimate debris excess and mass for gamma Vir B**: Compare Band 6 flux with Sirius-like (~0.6 TB) and full-blackbody extrapolations; debris masses per White et al. 2017  
  > "we would get an excess of 180 $\mu$Jy and 65 $\mu$Jy, respectively." (4.3 Relevance for debris disk studies)
   - parameter: ring at 4 au; grain density 2.5 g cm^-3; 2-4 au disk, 10 um to 25 km, q~3.5  
  > "is populated by grains ranging from $10\,\mu$m to 25 km with a size distribution of $q\sim3.5$" (4.3 Relevance for debris disk studies)
   - assumption: Grains perfect emitters (mm-grain case)  
  > "along with some other basic idealized assumptions such as as the grains being perfect emitters" (4.3 Relevance for debris disk studies)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.4.1: Pipeline calibration, CLEAN imaging, uvmodelfit  
  > "All of the data were reduced using the Common Astronomy Software Applications (CASA 5.4.1) pipeline" (2 Observations)
- **KINICH-PAKAL** : Semi-empirical chromospheric atmosphere models  
  > "These models were generated using the KINICH-PAKAL code (cite: tapia20)." (3.3 Stellar atmosphere models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| gamma Lep flux 0.87 mm | 707 | 17 (model); 30 obs | uJy | 2 | / $\gamma$ Lep / 0.87 / 2018 Sep 22 / J0522-3627 / 707 / 17 / 30 / 2.83 / |
| gamma Lep flux 1.29 mm | 345 | 6 (model); 10 obs | uJy | 2 | / $\gamma$ Lep / 1.29 / 2018 Sep 28 / J0522-3627 / 345 / 6 / 10 / 2.82 / |
| gamma Vir B flux 1.29 mm (2019 Mar 18) | 356 | 8 (model) | uJy | 2 | / $\gamma$ Vir B / 1.29 / 2019 Mar 18 / J1256-0547 / 356 / 8 / 14 / 3.48 / |
| Background source Band 7 flux | 430 | 25 | uJy | 3 | The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$. |
| Background source Band 6 flux | 160 | 16 | uJy | 3 | The Band 7 total flux is $430\pm25~\mu \rm Jy$ and the Band 6 total flux is $160\pm16~\mu \rm Jy$. |
| Background source spectral index | ≈2.5 | not stated | dimensionless | 3 | This corresponds to a spectral index $\alpha\approx 2.5$ and a dust emissivity $\beta\approx 0.5$ |
| gamma Lep temperature minimum | 4800 K at 750 km (Teff/TRmin = 0.76) | not stated | K | 4 | we see a temperature minimum of T$_{R, min}$ = 4800 K (T$_{eff}$/T$_{R, min}$ = 0.76) at a height of 750 km above the photosphere |
| Debris excess for gamma Vir B (Sirius-like / blackbody) | 180 / 65 | not stated | uJy | 6 | we would get an excess of 180 $\mu$Jy and 65 $\mu$Jy, respectively. |
| Total debris mass in disk (size distribution) | 0.02-0.07 | not stated | M_earth | 6 | This would lead us to infer $0.02-0.07\,\rm M_{\oplus}$ of total debris in the disk |

## Qualitative findings

- First mm observations of F-type stars with no significant circumstellar material; first observationally constrained mm atmosphere models  
  > "The ALMA data presented here are the first mm observations of F-type stars with no significant circumstellar material." (4 Discussion)

## Claim tuples

- H: Can mm data constrain chromospheric structure of F stars? | E: Fit KINICH-PAKAL models to ALMA plus Herschel fluxes | R: gamma Lep shows Tmin 4800 K at 750 km; gamma Vir models poorly constrained | F: Models show brightness temperature minimum in submm and rise beyond ~1 mm; gamma Vir constraints limited by lack of longer-wavelength data | **partially**
- H: Is there short-term mm variability in the gamma Vir stars? | E: Per-scan uvmodelfit time series compared with background source | R: A and B deviate from the background trend and each other at times | F: Variability possible but not confirmed | **partially**
- H: Does an unconstrained stellar spectrum bias debris inference? | E: Compute excess and debris mass for gamma Vir B under alternative stellar emission assumptions | R: Excess of 65-180 uJy, 0.02-0.07 Earth masses | F: Unconstrained stellar emission can lead to inferred spurious debris | **supported**

## Reasoning

- Why this data: Debris-poor nearby F stars are ideal for testing stellar emission at mm wavelengths  
  > "making them ideal targets for studying the stellar emission of F-type stars in the mm wavelength regime" (1 Introduction)
- Why this method: _not stated_
- Alternative: Point source vs Gaussian for background source: Gaussian preferred  
  > "find it to be more consistent with a Gaussian" (3.2 Additional source)
- How they decided it was enough: _not stated_
- Limitation (authors): gamma Vir models lack constraints at other wavelengths; temperature minimum cannot be analyzed  
  > "Therefore, it is not possible to perform an analysis of the temperature minimum in these two stars." (4.1 Semi-empirical chromospheric model)
- Limitation (authors): Variability at longer timescales cannot be ruled out for gamma Lep  
  > "we cannot rule out the possibility of variability at time periods longer than the length of the EBs." (4.2 Potential millimeter wavelength variability)
- Caveat (inferred, ours): Reduced chi^2 of 2.8-3.6 indicates poor fits not discussed
- Caveat (inferred, ours): Variability claim rests on 6-8 min bins with unquantified uncertainties and a background source of unknown nature
- Caveat (inferred, ours): Model fit has few data points and unquantified uncertainties
- Caveat (inferred, ours): Background galaxy identification is speculative

## Reproducibility

- Data public (paper): ALMA project codes given; public status not explicitly stated  
  > "ADS/JAO.ALMA#2017.1.00698.S and ADS/JAO.ALMA#2018.1.01149.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Model parameter files and fitting setup for KINICH-PAKAL
- Missing: Imaging parameters
- Missing: Time series binning details
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Flux measurement is easily repeatable with archival data, but atmospheric modeling and variability analysis lack details.
- Rediscovery candidate: yes, Data are from ALMA cycle 5/6 projects likely public, and fluxes via uvmodelfit are numeric and reproducible.

## Links

- Method: Tapia-Vázquez & De la Luz 2020 (cite: tapia20) (KINICH-PAKAL atmosphere code)
- Method: White et al. 2018, 2019 (cite: white18; white19) (uvmodelfit approach for stellar flux)
- Method: White et al. 2017 (cite: white_fom) (debris mass methods)
- Companion: White et al. 2018a, 2019 (cite: white18; white19) (Earlier MESAS observations of Sirius)
- Related: MESAS Project

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
