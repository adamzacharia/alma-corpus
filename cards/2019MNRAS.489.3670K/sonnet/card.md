# Imaging [CI] around HD 131835: reinterpreting young debris discs with protoplanetary disc levels of CO gas as shielded secondary discs

`2019MNRAS.489.3670K` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Kral, Quentin | arXiv: 1811.08439 | DOI: 10.1093/mnras/sty2923

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: debris_disks, astrochemistry
- Question: Can debris discs with protoplanetary-disc levels of CO be secondary (shielded by accumulated neutral carbon) rather than hybrid, tested with new ALMA [CI] and continuum data of HD 131835 plus a semi-analytic model?  
  > "Here we show that both the dust and gas in such systems could instead be secondary, with the high CO content caused by accumulation of neutral carbon (C$^0$) that shields CO from photodissociating" (abstract)
- Target **HD 131835**: coordinates _not stated_; z/distance 145±9 pc  
  > "HD 131835 is a 15-16 Myr old (cite: 2002AJ....124.1670M; 2012ApJ...746..154P) A-type star located at a distance[^3] of 145$\pm$9 pc" (1 Introduction); distance from Gaia DR1 (Gaia Collaboration 2016a,b)  
  > "HD 131835 is a 15-16 Myr old (cite: 2002AJ....124.1670M; 2012ApJ...746..154P) A-type star located at a distance[^3] of 145$\pm$9 pc" (1 Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 8  
  > "HD 131835 was observed by ALMA in band 8 on 22$^{\rm nd}$ March 2017" (3 ALMA continuum observation of HD 131835)
- frequencies and spectral setup: 3 continuum SPWs (128 channels, centred 480.201, 482.159, 494.201 GHz); 1 line SPW at 492.160651 GHz, 488.281 kHz (0.297 km/s) over 3840 channels  
  > "with a higher spectral resolution of 488.281 kHz (0.297 km/s at the rest frenquency of the line) over 3840 channels" (3 ALMA continuum observation of HD 131835)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 to 160 m, 42 antennas  
  > "The observations were carried out using 42 antennas with baselines ranging from 15 to 160m." (3 ALMA continuum observation of HD 131835)
- angular resolution: 0.89 x 0.68 arcsec continuum (robust 0.5); 0.89 x 0.63 arcsec [CI]  
  > "This yields a synthesised beam of 0.89 $\times$ 0.68 arcsec" (3.1 Dust continuum observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 14.1 min, mean PWV 0.57 mm  
  > "The total observing time on source (excluding overheads) was 14.1min and the mean PWV was 0.57mm." (3 ALMA continuum observation of HD 131835)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CI 3P0-3P1 (492.160651 GHz)
- Other facility **ALMA Band 6 (Moór 2017) and Herschel/APEX**: CO mass 0.04 Mearth from optically thin line; C+ and OI upper limits  
  > "the total CO mass derived (using an optically thin line) is $\sim$ 0.04 M$_\oplus$ (cite: 2017ApJ...849..123M)" (1 Introduction)
- External data: CO mass 0.04 Mearth of HD 131835 (optically thin line)  
  > "the total CO mass derived (using an optically thin line) is $\sim$ 0.04 M$_\oplus$ (cite: 2017ApJ...849..123M)" (1 Introduction) [from (cite: 2017ApJ...849..123M)]
- External data: C+ upper limit from Herschel 2e-3 Mearth  
  > "The C$^{+}$ upper limit from Herschel (at 30 K, assuming LTE) is $2\times 10^{-3}$ M$_\oplus$ (cite: 2015ApJ...814...42M)." (5.1) [from (cite: 2015ApJ...814...42M)]

## Processing

### Calibration

- pipeline or manual: ALMA-provided pipeline  
  > "We used the pipeline provided by ALMA to apply calibrations." (3 ALMA continuum observation of HD 131835)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Titan was used as a flux calibrator" (3 ALMA continuum observation of HD 131835)
- flux scale uncertainty: ~10%  
  > "flux calibration uncertainties ($\sim$ 10%) added in quadrature" (3.1 Dust continuum observations)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5  
  > "We deconvolved the image using the CLEAN algorithm and Briggs weighting with a robust parameter of 0.5." (3.1 Dust continuum observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA on line-free channels  
  > "we first subtract the continuum emission directly from the visibilities (with the task uvcontsub in CASA) using only channels where no [CI] emission is expected." (4.1 C0 gas detection)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 250 uJy/beam continuum; 66 mJy km/s/beam moment-0  
  > "The image rms around the disc is $\sigma=250\,\mu$Jy/beam." (3.1 Dust continuum observations)

### Inherited from earlier work

- Dust model setup for RADMC-3D imaging  
  > "to compute images for a given dust model (cite: 2016MNRAS.460.2933M)" (3.2) [from (cite: 2016MNRAS.460.2933M)]
- mu=14 mean molecular weight  
  > "We have thus chosen $\mu=14$ as in (cite: 2017MNRAS.469..521K)." (4.2.1) [from (cite: 2017MNRAS.469..521K)]
- double power-law temperature profile  
  > "The temperature profile is assumed to be a double power law profile (cite: 2016MNRAS.461..845K)" (4.2.1) [from (cite: 2016MNRAS.461..845K)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub
- Image size, cell size, CLEAN threshold/masks
- CASA and pipeline versions
- MCMC prior bounds and burn-in length
- Velocity range used for moment-0
- Grid ranges for the 1000-model semi-analytic grid
- Whether the archive pipeline products were used as delivered

## Analysis recipe

1. **Fit continuum visibilities with dust ring model**: RADMC-3D images converted to visibilities with GALARIO; emcee MCMC over 8 parameters  
  > "We use a Bayesian MCMC approach to constrain the 8 free parameters of the model." (3.2)
   - software: RADMC-3D, GALARIO, emcee
   - parameter: 100 walkers, 1200 steps after burn-in  
  > "We ran the MCMC with 100 walkers and for 1200 steps after the burn-in period." (3.2)
   - assumption: astrosilicate, 2.7 g/cm3, kappa=2.5 cm2/g at 610 um, sizes 2.5 um to 1 cm, slope -3.5  
  > "we assume an astrosilicate composition with a density of 2.7 g$\,$cm$^{-3}$" (3.2)
   - fitting: uniform priors, likelihood ∝ exp(-chi2/2)  
  > "We assume that the priors are uniform" (3.2)
   - validation: Best-fit model subtracted in image plane; residuals within noise  
  > "checked that the remaining residuals were all within the expected noise level" (3.2)
2. **Fit [CI] cube with Gaussian and double power-law gas models**: RADMC-3D in LTE plus GALARIO, MCMC on visibility cube; LTE checked with LIME  
  > "We also use RADMC-3D to produce the [CI] gas image and convert to visibilities using GALARIO" (4.2)
   - software: RADMC-3D, GALARIO, LIME, emcee
   - parameter: 10 free parameters for double power law  
  > "This leaves us with 10 free parameters that are $R_0$, $\Sigma_0$, $T_0$, $\beta_1^s$ $\beta_2^s$, $\beta_1^t$, $\beta_2^t$, $i$, PA and $v_\star$." (4.2.2)
   - assumption: LTE, mu=14, axisymmetric  
  > "We thus assume that LTE is a good approximation even for very low carbon ionisation fractions." (4.2)
   - fitting: same MCMC procedure as continuum  
  > "We explore the parameter space with the same MCMC procedure as presented for the continuum" (4.2.2)
   - validation: Compared model and data moment-0 visibilities; some residuals remain  
  > "leaves a few significant residuals probably linked to the detailed structure of the emission" (4.2.2)
3. **Fit semi-analytic CO/C0 evolution model to CO mass**: 0D box model of CO and C evolution with C0 and self-shielding; grid of 1000 models in Mdot_CO and alpha compared with CO mass 0.04 Mearth (0.5 dex uncertainty)  
  > "We ran a grid of 1000 models for different $\dot{M}_{\rm CO}$ and $\alpha$ values" (5.2.3)
   - parameter: R0=90 au, DR=70 au, T~30 K, ionisation fraction ~0  
  > "we assume that $R_0=90$ au, the ionisation fraction is close to 0, the temperature is $\sim 30$ K" (5.2.2)
   - fitting: contours at 1, 3, 5 sigma from observed CO mass  
  > "the uncertainty $\sigma_{\rm CO}$ is assumed to be 0.5 dex from the observed mass" (5.2.3)
   - validation: Predicted C0 mass compared to [CI] fit  
  > "which is similar to what we deduced from the [CI] observations" (5.2.3)

## Software

- **CASA** : uvcontsub continuum subtraction  
  > "with the task uvcontsub in CASA" (4.1)
- **RADMC-3D** : dust and [CI] model images  
  > "We then use the line radiative transfer code RADMC-3D" (3.2)
- **GALARIO** : model visibilities  
  > "GALARIO (cite: 2018MNRAS.tmp..402T) to convert them into model visibilities" (3.2)
- **emcee** : MCMC sampling  
  > "We sample the parameter space by using the emcee module" (3.2)
- **LIME** : non-LTE check  
  > "We first used the radiative transfer code LIME" (4.2)
- **DALI** : ionisation fraction and temperature of a shielded disc  
  > "We now use the DALI 2D code" (5.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux | 17.9 | 2.1 | mJy | 0 | The total flux in the Briggs-weighted image is 17.9$\pm$2.1 mJy |
| [CI] integrated flux | 2.8 | 0.4 | Jy km/s | 0 | The total integrated flux is 2.8$\pm$0.4 Jy$\,$km/s |
| Dust mass | 0.71 | +0.03/-0.05 | Mearth | 1 | $M_{\rm dust}$ (M$_\oplus$) / $0.71^{+0.03}_{-0.05}$ |
| Dust ring radius R0 | 90.5 | +3.8/-3.7 | au | 1 | $R_0$ (au)                  /  $90.5^{+3.8}_{-3.7}$ |
| C0 mass | 3.1e-3 best fit; 2.7e-3 to 1.2e-2 (16-84%) | percentile range | Mearth | 2 | we find that the best fit is for a mass $M_{{\rm C}^0}=3.1 \times 10^{-3}$ M$_\oplus$. |
| Gas temperature T0 (double power law) | 30 | +5/-4 | K | 2 | $T_0$ (K)                     / $28^{+4}_{-4}$      / $30^{+5}_{-4}$ |
| Stellar radial velocity | 3.57 | 0.1 | km/s | 2 | 3.57$\pm$0.1 km/s (heliocentric frame) |
| Viscosity alpha | 1e-3 < alpha < 1e-2 | not stated | dimensionless | 3 | we conclude that $10^{-3}<\alpha<10^{-2}$ can explain the observed CO mass |

## Qualitative findings

- Gas disc is not clearly at steady state; outer slope steep and gas extends at least to 35 au  
  > "this would imply that steady state is not reached, which is most likely the case here" (4.2.2)

## Claim tuples

- H: HD 131835 has enough C0 to shield CO | E: ALMA band 8 [CI] visibility fitting | R: M_C0 = 2.7e-3 to 1.2e-2 Mearth | F: C0 is sufficient to shield CO | **supported**
- H: Secondary gas with C0 shielding explains the high CO mass | E: semi-analytic evolution model grid | R: alpha ~1e-3 to 1e-2 fits | F: HD 131835 may be a shielded secondary disc | **supported**
- H: Other hybrid discs are also shielded | E: same model applied to 5 systems | R: overlapping Mdot_CO ranges | F: consistent but untested; primordial origin not ruled out | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Low resolution gives large uncertainties; [CI] optically thick so mass poorly constrained  
  > "The C$^0$ mass is not well constrained because the line is optically thick in the whole disc" (4.2.2)
- Limitation (authors): DALI outside its validated range  
  > "is strictly outside the parameter range for which DALI – a protoplanetary disc code – is validated to give correct results." (footnote 5)
- Caveat (inferred, ours): Model is 0D and degenerate with resolution
- Caveat (inferred, ours): LTE assumed
- Caveat (inferred, ours): Primordial origin not excluded

## Reproducibility

- Data public (paper): ALMA project data acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.0.01253.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MCMC priors
- Missing: Semi-analytic model code
- Data volume (inferred): ~10-20 GB raw
- Score (inferred): 3/5, Data and methods mostly described but many imaging/prior details and model code missing.
- Rediscovery candidate: no, Key results depend on unreleased models and unstated priors.

## Links

- Method: (cite: 2018MNRAS.tmp..402T) (GALARIO visibility modelling)
- Method: (cite: 2017MNRAS.469..521K) (secondary gas model)
- Companion: (cite: 2017ApJ...849..123M) (CO mass of HD 131835)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.01253.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 44,
  "rate": 0.611
 },
 "evidence_ok": true
}
```
