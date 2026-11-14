# Study of the aluminium content in AGB winds using ALMA. Indications for the presence of gas-phase (Al<SUB>2</SUB>O<SUB>3</SUB>)<SUB>n</SUB> clusters

`2017A&A...608A..55D` | Astronomy and Astrophysics 2017 | first author: Decin, L. | arXiv: 1704.05237 | DOI: 10.1051/0004-6361/201730782

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, astrochemistry
- Question: How much aluminium is locked in gas-phase AlO, AlOH and AlCl in the inner winds of the O-rich AGB stars R Dor and IK Tau, and what does this imply for aluminium dust condensation?  
  > "We aim to constrain the dust formation histories in the winds of oxygen-rich AGB stars." (abstract)
- Target **R Dor**: coordinates _not stated_; z/distance 60 pc  
  > "their proximity (60 pc and 260 pc, respectively)" (2.1 Target selection); distance from _not stated_
- Target **IK Tau**: coordinates _not stated_; z/distance 260 pc  
  > "their proximity (60 pc and 260 pc, respectively)" (2.1 Target selection); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00166.S
- bands: Band 7, 335-362 GHz spectral scan  
  > "Spectral scans of IK Tau and R Dor were obtained covering the frequencies between 335–362 GHz, using four separate observations each, during August-September 2015." (2.2.1 ALMA observing strategy)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.12'' x 0.15''  
  > "We obtained the first ALMA spectral scan for O-rich AGB stars in band 7 at a spatial resolution of $\sim$0.12$''$$\times$0.15$''$." (Introduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: August-September 2015  
  > "using four separate observations each, during August-September 2015" (2.2.1 ALMA observing strategy)
- pi or archival as stated: _not stated_
- Line: AlO N=9-8 (345.457 GHz)
- Line: AlOH J=11-10 (346.156 GHz)
- Line: AlCl J=24-23 (349.444 GHz)
- Other facility **ISO/SWS, IRAS-LRS, VLTI/MIDI, SPHERE**: Literature infrared spectra and interferometric/polarimetric data used for dust context  
  > "Both R Dor and W Hya have been observed with the Short Wavelength Spectrometer (SWS) on board of the Infrared Space Observatory (ISO) using the AOT01 observing mode." (2.3 Infrared continuum emission)
- External data: Input parameters for radiative transfer models (T*, epsilon, v_inf, beta, mass-loss rate, luminosity)  
  > "The main input parameters for R Dor and IK Tau are listed in Table [2](#Table:input_RT), following (cite: Maercker2016A&A...591A..44M)." (3 Results) [from (cite: Maercker2016A&A...591A..44M)]
- External data: Chemical kinetic model predictions of Al species for IK Tau  
  > "The deduced AlO, AlOH, and AlCl abundances of IK Tau can be compared directly to the chemical predictions by (cite: Gobrecht2016A&A...585A...6G)." (4.1 The gas-phase aluminium budget) [from (cite: Gobrecht2016A&A...585A...6G)]
- External data: Collisional rates (HCN-H2 and SiO-H2 as substitutes) from LAMDA  
  > "we have used the values for the HCN-H$_2$ system (cite: Green1974ApJ...191..653G) as substitute for AlOH" (3 Results) [from (cite: Green1974ApJ...191..653G); (cite: Dayou2006A&A...459..297D); (cite: Schoier2005A&A...432..369S)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then self-calibration on line-free continuum  
  > "The observations and data reduction used the ALMA pipeline for calibration, followed by identifying and imaging the line-free continuum, which was then used for self-calibration." (2.2.1 ALMA observing strategy)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~7%  
  > "The astrometric accuracy is $\sim$17 mas and the flux scale is accurate to $\sim$7%." (2.2.1 ALMA observing strategy)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: different weighting used for high and low spectral resolution cubes; values not given  
  > "we made cubes at higher and lower spectral resolution (see info in Table [1](#Table:obs)), by using different weighting and spectral averaging" (2.2.1 ALMA observing strategy)
- uv taper: _not stated_
- cell size: 30 mas (R Dor), 40 mas (IK Tau)  
  > "we achieved a higher resolution and used a smaller pixel size (30 mas versus 40 mas) for R Dor versus IK Tau" (2.2.1 ALMA observing strategy)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: AlO wide-channel cube smoothed with 500 mas Gaussian kernel  
  > "for AlO, we further smoothed the wide-channel data set with a 500 mas Gaussian kernel" (2.2.1 ALMA observing strategy)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full ALMA data reduction and imaging process  
  > "The process is described in more detail in (cite: Decin2016scan); here, we concentrate on the parameters affecting the Al compound cubes." (2.2.1 ALMA observing strategy) [from (cite: Decin2016scan)]
- Stellar and wind parameters for radiative transfer  
  > "The main input parameters for R Dor and IK Tau are listed in Table [2](#Table:input_RT), following (cite: Maercker2016A&A...591A..44M)." (3 Results) [from (cite: Maercker2016A&A...591A..44M)]

### Not stated but needed to reproduce (our reading)

- tclean parameters (robust, deconvolver, masks, threshold)
- CASA/pipeline version
- line-free channel ranges and continuum subtraction method
- self-calibration solution intervals
- baselines/configurations and maximum recoverable scale
- non-LTE ALI code availability and fitting procedure/criterion
- uncertainties on the fitted abundances
- hyperfine splitting implementation details

## Analysis recipe

1. **Calibrate and image cubes**: ALMA pipeline calibration, continuum self-calibration, cubes at two spectral resolutions  
  > "The observations and data reduction used the ALMA pipeline for calibration, followed by identifying and imaging the line-free continuum, which was then used for self-calibration." (2.2.1 ALMA observing strategy)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract line profiles and azimuthally averaged flux densities**: Spectra extracted in apertures; angular width from zeroth moment in annuli of 60 (80) mas, taken as distance out to 2 sigma_rms  
  > "The angular size was taken as the distance out to 2 $\sigma_{\rm{rms}}$." (2.2 Al-bearing species detected with ALMA)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive fractional abundance profiles**: 1D non-LTE ALI radiative transfer; abundance structure varied until fit to azimuthally averaged flux densities  
  > "For all molecular species, the fractional abundance structure with respect to H$_2$ was varied until a fit with the ALMA azimuthally averaged flux density was achieved" (3 Results)
   - software: ALI non-LTE code
   - assumption: Power-law gas temperature, beta velocity law, turbulent velocity 1 km/s, solar Al/H = 3e-6, substitute collisional rates  
  > "The turbulent velocity for both stars is assumed to be 1 km/s." (3 Results)
   - fitting: manual variation of abundance profiles (constant or Gaussian)  
  > "For all molecular species, the fractional abundance structure with respect to H$_2$ was varied until a fit with the ALMA azimuthally averaged flux density was achieved" (Results: Abundances of aluminium-bearing molecules)
   - validation: Checked with CS-H2 collision rates; no significant difference  
  > "we also ran models using the CS-H$_2$ cross sections (cite: Turner1992ApJ...399..114T) and found no significant difference in results" (3 Results)
4. **Compare with chemical models and compute Al budget**: Compare abundances with Gobrecht et al. kinetic models; compute fraction of Al in molecules  
  > "we can see that both the observations and chemical models predict a higher abundance for AlOH than for AlO." (4.1 The gas-phase aluminium budget)
   - fitting: _not stated_
   - validation: _not stated_
5. **DFT of small (Al2O3)n clusters**: B3LYP/6-311+g* DFT for n=1-4, vibrational spectra  
  > "using the hybrid B3LYP (cite: Lee1988PhRvB..37..785L; Miehlich1989CPL...157..200M; Becke1993JChPh..98.5648B) exchange-correlation functional with a 6-311+g$^*$ basis set" (4.3.1)
   - software: GAUSSIAN 09
   - fitting: _not stated_
   - validation: Compared with Demyk et al. 2004 and Sierka et al. 2007 spectra  
  > "The predicted spectra compare well with the experimental results by (cite: Demyk2004A&A...420..547D)" (4.3.1)

## Software

- **ALI non-LTE radiative transfer code (Maercker et al. 2008)** : Retrieve fractional abundances in 1D CSE  
  > "We use a code based on the ‘Accelerated Lambda Iteration’ (ALI) method (cite: Maercker2008A&A...479..779M)" (3 Results)
- **GAUSSIAN 09** Revision D.01: DFT of alumina clusters  
  > "The computations were accomplished by the GAUSSIAN 09 package (cite: Frisch09)" (4.3.1)
- **LAMDA database** : Collisional rate format  
  > "The collisional rates are used in the form they appear in the LAMDA database" (3 Results)
- **CDMS** : Hyperfine line strengths  
  > "according to their relative quantum-mechanical line strength, $S$, as given in CDMS" (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| AlOH peak central abundance, IK Tau (Gaussian) | 4.4e-9 | not stated | relative to H2 | 3 | peak central abundance of $4.4\times10^{-9}$ and an $e$-folding radius, $r_e$, of 22 R$_{\star}$ |
| AlO abundance IK Tau (50-160 R*) | 4.4e-8 | not stated | relative to H2 | 3 | constant abundance of 4.4$\times$10$^{-8}$ from 50–160 R$_{\star}$ |
| AlCl peak abundance IK Tau | 9e-10 | not stated | relative to H2 | 3 | peak central abundance of $9\times10^{-10}$ and $r_e$ of 40 R$_{\star}$ |
| AlOH abundance R Dor (to 12 R*) | 1.4e-9 | not stated | relative to H2 | 3 | constant slab with abundance of 1.4$\times$10$^{-9}$ from the stellar surface out to 12 R$_{\star}$ |
| AlO and AlCl peak abundances R Dor | 8.4e-8 and 2.5e-8 | not stated | relative to H2 | 3 | peak central abundance of $8.4\times10^{-8}$ and $2.5\times10^{-8}$ and $e$-folding radius of 3.8 R$_{\star}$ and 2.4 R$_{\star}$ |
| Fraction of Al locked in AlO, AlOH, AlCl | <~2% | not stated | percent | 4 | only a small fraction of aluminium ($\ensuremath{\lesssim}$2%) is locked up in AlO, AlOH, and AlCl |
| AlCl abundance in IK Tau vs predicted | ~40 | not stated | dimensionless | 4 | the ALMA data show that the AlCl abundance in IK Tau is a factor $\sim$40 higher than predicted |

## Qualitative findings

- Al chemistry differs between R Dor and IK Tau; AlO and AlOH are detected beyond the dust formation region, so alumina condensation is not fully efficient.  
  > "This implies that the aluminium dust condensation cycle is not fully efficient." (5 Conclusions)

## Claim tuples

- H: Is a large fraction of Al in gas-phase molecules? | E: Non-LTE modelling of AlO, AlOH, AlCl ALMA lines | R: Abundances yield <=2% of Al in these molecules | F: Most Al is available for dust | **supported**
- H: Do chemical models reproduce the observed abundances in IK Tau? | E: Compare retrieved abundances with Gobrecht et al. 2016 | R: AlOH is 2 orders lower than predicted, AlCl ~40x higher | F: Models need improvement | **partially**
- H: Large gas-phase (Al2O3)n clusters cause the 11 micron feature | E: Literature cluster spectra plus DFT of small clusters | R: Hypothesis consistent with IR-REMPI; small clusters not constrained | F: Proposed, not proven | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): ALMA beam too large to test abundance variation within 5 R* for IK Tau; AlCl identification uncertain; 1D model ignores clumpiness.  
  > "The ALMA beam of $\sim$0.12$''$$\times$0.15$''$ is hence too large to confirm the predicted strong radial variation in molecular abundance within 5 R$_{\star}$" (4.1)
- Caveat (inferred, ours): Substitute collisional rates and LTE hyperfine splitting add systematic uncertainty
- Caveat (inferred, ours): No abundance uncertainties from formal fitting
- Caveat (inferred, ours): Cluster hypothesis is speculative
- Caveat (inferred, ours): Clumpy emission averaged in 1D

## Reproducibility

- Data public (paper): ALMA project 2013.1.00166.S acknowledged; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA2013.0.00166.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging details deferred to Decin et al. in prep.
- Missing: Fit procedure and non-LTE code access
- Missing: Spectral cubes
- Data volume (inferred): ~100 GB (four-execution band 7 spectral scans for two targets)
- Score (inferred): 4/5, Data identified but imaging details deferred and the radiative transfer fit is manual.
- Rediscovery candidate: no, Imaging recipe is incomplete and relies on an in-prep paper and a non-public RT code.

## Links

- Method: (cite: Decin2016scan) (ALMA reduction and imaging)
- Method: (cite: Maercker2008A&A...479..779M) (Non-LTE ALI code)
- Companion: (cite: Gobrecht2016A&A...585A...6G) (Chemical models compared)
- Related: ALMA project 2015.1.01466.S (W Hya, Takigawa)

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2015.1.01466.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 33,
  "rate": 0.446
 },
 "evidence_ok": true
}
```
