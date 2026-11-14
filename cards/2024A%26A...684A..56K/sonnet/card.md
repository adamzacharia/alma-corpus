# Probing the interstellar medium of the quasar BRI 0952‒0115. An analysis of [C II], [C II], CO, OH, and H<SUB>2</SUB>O

`2024A&A...684A..56K` | Astronomy and Astrophysics 2024 | first author: Kade, K. | arXiv: 2312.10267 | DOI: 10.1051/0004-6361/202347453

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: agn_and_quasars, high_z_galaxies, milky_way_ism
- Question: What are the ISM properties and heating mechanisms (PDR vs XDR) of the lensed quasar BRI 0952-0115 at z=4.432, and what is its evolutionary stage?  
  > "Our aim is to better understand the processes governing the interstellar medium (ISM) of the quasar BRI 0952$-$0952 at $z = 4.432$" (abstract)
- Target **BRI 0952-0115**: coordinates _not stated_; z/distance z = 4.432  
  > "BRI 0952-0115 (hereafter BRI 0952), a doubly-imaged gravitationally lensed quasar at $z = 4.432$." (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.01081.S, 2015.1.00388.S, 2018.1.01536.S
- bands: Bands 3, 4, 6 (archival) and 7 (high-resolution)  
  > "ALMA archival bands 3 (2017.1.01081.S, P.I. Leung), 4 (2015.1.00388.S, P.I. Lu) and 6 (2015.1.00388.S, P.I. Lu) data." (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: ~23 kpc for CO(5-4)  
  > "The CO(5–4) observations were carried out in an extended configuration with a maximum recoverable scale of $\sim 23$ kpc." (CO emission)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 Jan 06 to 2019 Apr 06  
  > "| $7_{\rm [CII]}$ | 2019 04 06 | 41 | 348 | 13 | \[$0.48 \times 0.35$\] | 0.2 |" (Table 1)
- pi or archival as stated: Band 3 P.I. Leung; bands 4 and 6 P.I. Lu; archival  
  > "ALMA archival bands 3 (2017.1.01081.S, P.I. Leung), 4 (2015.1.00388.S, P.I. Lu)" (Observations)
- Line: CO 5-4 (576.26 GHz)
- Line: CO 7-6 (806.65 GHz)
- Line: CO 12-11 (1381.995 GHz)
- Line: [CI] 2-1 (809.34197 GHz)
- Line: [CII] 2P3/2-2P1/2 (1900.5369 GHz)
- External data: Lens parameters and band-7 reduction/[CII] results  
  > "The lens parameters used in our study are from (cite: Kade23), where a full description of these parameters is provided." (Visilens Modelling) [from (cite: Kade23)]
- External data: [CI]/H2 abundance (8.4±3.5)e-5  
  > "we choose to use \[C i\] /$\rm H_2 = (8.4 \pm 3.5) \times 10^{-5}$ from (cite: Walter11)" (Gas Mass) [from (cite: Walter11)]
- Simulation/model as data: MOLPOP-CEP grid of 1521 slab models (zone width, n(H2), Tkin)  
  > "The final grid consists of a total of 13$\times$13$\times$9 = 1521 models." (4 Radiative Transfer Modeling)

## Processing

### Calibration

- pipeline or manual: CASA pipeline calibration scripts  
  > "The data in each band were calibrated using the CASA pipeline calibration scripts" (Observations)
- casa version: CASA 4.5.1 (band 4 and 6 as written) and CASA 5.1.1  
  > "CASA 4.5.1 for the band 4 and 6 data and CASA version 5.1.1 for the band 6 data." (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% adopted  
  > "A conservative estimate of 10% is used to represent the uncertainty in the absolute flux calibration" (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Imaging was performed in CASA using the TCLEAN task" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5; band 3 cubes natural  
  > "Briggs weighting scheme with a robust parameter of 0.5." (Observations)
- uv taper: band 3 tapered to match band 7 resolution  
  > "a taper was performed to the *uv*-data which effectively lowered the resolution" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: circular mask radius ~20'', cleaned to 2 sigma  
  > "The images were cleaned down to a $2\sigma$ level for each band." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB, order 0 polynomial  
  > "Continuum subtraction was performed using CASA’s task UVCONTSUB using line-free channels and a polynomial fit order of 0 for all bands." (Observations)
- line free channels: _not stated_
- primary beam correction: applied to band 3 only  
  > "primary beam correction was applied to the band 3 data in addition to the taper." (Observations)
- array combination: _not stated_
- smoothing: band 3 binned by 8x in channels  
  > "we binned the data by a factor of 8$\times$" (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Band 7 data reduction  
  > "the full description of the data reduction process is described in (cite: Kade23)" (Observations) [from (cite: Kade23)]
- Continuum fluxes via IMFIT  
  > "we extracted continuum fluxes using CASA’s IMFIT routine following (cite: Kade23)." (Continuum) [from (cite: Kade23)]
- mu = 3.92 from earlier lens model  
  > "We present the line luminosity values using $\mu = 3.92$ (cite: Kade23)" (Spectral Reconstruction) [from (cite: Kade23)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges per band
- Velocity ranges for moment maps and spectral extraction
- Extraction ellipse coordinates
- Taper size for band 3
- Visilens parameter ranges and priors
- Gaussian fit procedure details
- Band 7 reduction details (in Kade23)
- Band 3 and 4 CASA versions inconsistent
- Starburst99 assumptions
- SFR and LIR values used for depletion time

## Analysis recipe

1. **calibrate and image archival data**: CASA pipeline calibration, tclean, uvcontsub  
  > "Continuum images were created using the line-free channels with a Briggs weighting scheme with a robust parameter of 0.5." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **extract spectra and fit line fluxes**: Regional spectral extraction, Gaussian fits, rms from 12 emission-free regions  
  > "We obtained the per-channel rms of the spectral cube by sampling twelve distinct emission-free regions" (Line Emission)
   - software: CASA
   - fitting: Gaussian fits (two for CO(7-6)); OH doublet fixed at systemic velocities  
  > "We fit an individual Gaussian for both lines of the doublet, but we fix the peak velocity to be the systemic velocity of each line in the doublet." (OH)
   - validation: _not stated_
3. **per-channel lensing magnification**: Visilens fit of each [CII] channel with Sersic source, magnification extrapolated to other lines by nearest velocity  
  > "we used a closest value finding algorithm to search for the velocity bin in the \[C ii\] data which is nearest the velocity bin of the particular line" (Spectral Reconstruction)
   - software: Visilens
   - assumption: Other lines follow bulk kinematics of [CII]  
  > "as long as the other line species detected follow the bulk motion and systematic kinematics of the entire galaxy, as traced by \[C ii\], this method of extrapolating the magnification factor is valid." (3.3 Lensing Reconstruction)
   - fitting: 4 model variants; Gaussian source rejected  
  > "the fit from VISILENS for this model was sufficiently poor that we disregarded it." (Visilens Modelling)
   - validation: Models compared; magnification consistent across models  
  > "the magnification factor across the velocity range does not change greatly depending on the model used." (Visilens Modelling)
4. **molecular gas mass from [CI]**: Weiss03 equation with Tex=30 K, [CI]/H2=8.4e-5  
  > "we adopt a excitation temperature of $T_{\rm ex} = 30$ K following (cite: Walter11) and (cite: Jarugula21)." (Gas Mass)
   - fitting: _not stated_
   - validation: _not stated_
5. **CO SLED radiative transfer modelling**: MOLPOP-CEP grid, PDR (Starburst99 SED, logG0 0-4) and XDR heating; chi2<=1sigma; two-component models; likelihood distributions  
  > "we consider only those models with $\chi^{2} \leq 1\sigma$ where $1\sigma = 2.30$ for the degrees of freedom in our model." (4.3 One-Component Models)
   - software: MOLPOP-CEP, Starburst99
   - parameter: 10 zones; Tkin 50-200 K step 25 K; XCO=1e-4  
  > "we divide the slab into 10 zones and employ a uniform setup in each zone throughout the slab" (4 Radiative Transfer Modeling)
   - assumption: CMB at z=4.432, T=14.742 K  
  > "At this redshift the CMB temperature is $T_{\rm CMB}$ = 14.742 K" (4 Radiative Transfer Modeling)
   - fitting: Grid chi2 plus Bayesian likelihood with flat priors and cutoffs  
  > "We follow the approach of (cite: Ward03), (cite: Kamenetzky11), and (cite: GonzalezAlfonso_21)" (4.4 Two-Component Models)
   - validation: _not stated_
6. **dust temperature from modified blackbody**: MCMC fit, T 14.742-120 K, beta 1.3-2.5  
  > "We explored the parameter space of both of these values using a Markov chain Monte Carlo (MCMC) approach" (5.1)
   - software: dust_emissivity
   - fitting: MCMC; sampler not stated  
  > "We explored the parameter space of both of these values using a Markov chain Monte Carlo (MCMC) approach in which the dust temperature was allowed to vary between 14.742 K and 120 K" (5.1 The -IR luminosity relation)
   - validation: _not stated_

## Software

- **CASA** 4.5.1 / 5.1.1: calibration, imaging, IMFIT  
  > "all calibration and imaging processes for the archival band 3, 4, and 6 data were performed in the Common Astronomy Software Application package" (Observations)
- **Visilens** : lens modelling per channel  
  > "We utilize the python-based code Visilens (cite: Spilker16) to model each channel containing \[C ii\] emission." (Visilens Modelling)
- **MOLPOP-CEP** : radiative transfer line models  
  > "We used the radiative transfer code MOLPOP-CEP (cite: Andres_2018) to model the line species detected in BRI 0952." (4 Radiative Transfer Modeling)
- **Starburst99** : stellar SED for PDR heating  
  > "we used the stellar population synthesis code Starburst99 (cite: Leitherer_1999) to generate an SED" (4.1 Heating via PDRs)
- **dust_emissivity** : modified blackbody fit  
  > "we use the python package (dust emissivity, (cite: dust_emm)) to fit a modified black body function" (5.1)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO(5-4) line flux | 1.4 | 0.30 | Jy km/s | 2 | / CO(5–4) / 576.26 / $1.4 \pm 0.30$ / $278 \pm 46$ |
| CO(12-11) line flux | 2.0 | 0.18 | Jy km/s | 2 | / CO(12–11) / 1381.95 / $2.0 \pm 0.18$ / $258 \pm 17$ |
| [CI] gas mass | 2.1e6 | 1.7e6 | Msun | 4 | we find a \[C i\] gas mass of $(2.1 \pm 1.7) \times 10^6$ M$_{\odot}$. |
| H2 gas mass | 6.2e9 | 4.9e9 | Msun | 4 | we obtain an $\rm H_{2}$ gas mass of $(6.2 \pm 4.9) \times 10^{9}\,M_{\odot}$. |
| CO(7-6)/[CI](2-1) ratio | ~4.8 | not stated | dimensionless | 0 | We find a ratio of CO(7–6)/\[C i\] (2–1) $\sim 4.8$. |
| Dust temperature | ~45 K, beta ~2.0 | large | K | 6 | The best-fit parameters returned from this method were $T_{\rm dust} \sim 45$ K and $\beta \sim 2.0$ |
| Depletion time (LIR, [CII] SFR) | ~8 Myr, ~25 Myr | not stated | Myr | 0 | find $t_{\rm dep_{L_{\rm IR}}} \sim 8$ Myr and $t_{\rm dep_{[CII]}} \sim 25$ Myr |
| [CII]/[CI] luminosity ratio | ~100 | not stated | dimensionless | 0 | We find \[C ii\] /\[C i\] $\sim100$ |

## Qualitative findings

- Lensing magnification varies across [CII]; velocity gradient found; broad [CII] wings not due to differential lensing  
  > "confirming that these are not due to differential lensing as hypothesized in (cite: Kade23)" (Spectral Reconstruction)

## Claim tuples

- H: Do single heating mechanisms reproduce the CO SLED? | E: One-component PDR and XDR MOLPOP-CEP grids | R: Neither reproduces all lines | F: Two components needed | **supported**
- H: Is the heating PDR or AGN dominated? | E: Two-component models | R: chi2 1.33 (PDR+XDR) vs 1.36 (PDR+PDR) | F: Cannot distinguish; PDR+XDR favoured given CO(16-15) | **partially**
- H: Is the quasar in a transitional phase? | E: Gas mass, depletion time, SLED, kinematics | R: Low depletion time, high SFR | F: Transitional from starburst to AGN dominated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Use [CII] for lensing since highest quality; cannot model each line individually  
  > "This approach is preferred because it enables us to leverage the high-quality \[C ii\] observations" (3.3 Lensing Reconstruction)
- Alternative: Gaussian source profile rejected as poor fit  
  > "the fit from VISILENS for this model was sufficiently poor that we disregarded it." (Visilens Modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): Data not standardized, resolution limited, CO SLED turnover unconstrained  
  > "these observations are not standardized and suffer from angular resolution limitations" (5.3)
- Caveat (inferred, ours): Magnification from [CII] applied to CO lines at differing locations
- Caveat (inferred, ours): Text inconsistencies: H2 mass 6.2e9 in text vs 6.2e11 in conclusions; CASA versions band 4/6
- Caveat (inferred, ours): Only three CO lines versus many free parameters
- Caveat (inferred, ours): chi2 1sigma=2.30 threshold ad hoc

## Reproducibility

- Data public (paper): Archival ALMA data with project codes listed  
  > "This paper makes use of the following ALMA data: 2017.1.01081.S, 2015.1.00388.S, and 2018.1.01536.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channels
- Missing: Extraction regions
- Missing: Visilens priors and ranges
- Missing: Band 7 reduction (in Kade23)
- Missing: Taper parameters
- Data volume (inferred): ~100-300 GB raw for four ALMA datasets
- Score (inferred): 3/5, Public data and software named, but many reduction and lens-model details deferred or unstated.
- Rediscovery candidate: no, Key steps depend on Kade23 lens model, unstated extraction details and modelling choices.

## Links

- Method: (cite: Spilker16) (Visilens)
- Method: (cite: Andres_2018) (MOLPOP-CEP)
- Companion: (cite: Kade23) (Band 7 data reduction, lens model, [CII] study)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 47,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
