# An ALMA/NOEMA study of gas dissipation and dust evolution in the 5 Myr-old HD 141569A hybrid disc

`2020A&A...635A..94D` | Astronomy and Astrophysics 2020 | first author: Di Folco, E. | arXiv: - | DOI: 10.1051/0004-6361/201732243

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, debris_disks
- Question: What are the physical parameters (dust and gas) of the gas-rich hybrid disc around HD 141569A, and what is its evolutionary status?  
  > "We determine the physical parameters of the brightest gas-rich debris disc orbiting HD 141569A." (abstract)
- Target **HD 141569A**: coordinates phase centre RA = 15:49:57.73, Dec = -03:55:16.62 (12CO 3-2)  
  > "The star is located at 110.6 ± 0.5 pc (Gaia Collaboration 2018)" (1. Introduction); z/distance 110.6 ± 0.5 pc  
  > "The star is located at 110.6 ± 0.5 pc (Gaia Collaboration 2018)" (1. Introduction); distance from Gaia Collaboration 2018  
  > "The star is located at 110.6 ± 0.5 pc (Gaia Collaboration 2018)" (1. Introduction)

## Data provenance

- ALMA projects: 2012.1.00698.S
- bands: ALMA Band 3 and Band 7; NOEMA 1.3 mm  
  > "We obtained ALMA observations of HD 141569 in Band 3 (84−116 GHz)." (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: NOEMA 7D/7C/6C configurations; ALMA 39 and 44 antennas (Band 3), 32 antennas (Band 7)  
  > "mapped with the 7D and 7C configurations (7 antennas) of the IRAM array" (2.1 PdBI/NOEMA observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3: 0.76'' x 0.56''; Band 7: 0.43'' x 0.35''; NOEMA 12CO 2-1: 2.4'' x 1.2''  
  > "The spatial resolution was 0.76 [′′] × 0.56 [′′] (baselines up to 1.55 km), and the spectral resolution 0.2 km s [−][1]." (2.2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 13CO 2-1 NOEMA: 12.7 h on source  
  > "antennas were used with a total on-source time of 12.7 h." (2.1 PdBI/NOEMA observations)
- observing dates: NOEMA Dec 2014 to Apr 2016; ALMA Band 3 Aug 2015  
  > "HD 141569 was observed with NOEMA during three runs from December 2014 to April 2016." (2.1 PdBI/NOEMA observations)
- pi or archival as stated: Band 3 own project (PI Péricaud); Band 7 archival (PI Boley)  
  > "we collected archival raw data from the project 2012.1.00698.S (PI. Boley)" (2.2 ALMA observations)
- Line: 12CO J=2-1 (230.538 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Line: 13CO J=1-0 (110.201 GHz)
- Line: 12CO J=3-2 (345.796 GHz)
- Other facility **NOEMA/PdBI**: 12CO and 13CO 2-1 and 1.3 mm continuum  
  > "The WIDEX correlator provided 4 GHz bandwidth during the observations of the [12] CO and [13] CO." (2.1 PdBI/NOEMA observations)
- Other facility **IRAM 30m/EMIR**: Deep search for HCN, HCO+, CS etc.; no detection  
  > "No emission was detected." (2.3 A deep search)
- External data: 12CO 1-0 integrated intensity 1.6 ± 0.2 Jy km/s (CARMA) used for opacity  
  > "From Flaherty et al. (2016)." (Table 3) [from Flaherty et al. (2016)]
- External data: Disc geometry PA=356°, i=53° from optical used to deproject visibilities  
  > "we therefore first deprojected the visibilities assuming the geometric parameters derived at optical wavelength (PA= 356 [◦], _i_ = 53 [◦], Augereau et al. 1999)" (3.1 Continuum emission) [from Augereau et al. 1999]

## Processing

### Calibration

- pipeline or manual: CASA used to calibrate ALMA data  
  > "We used the CASA package to calibrate the ALMA data" (2.2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: ALMA B3: Ceres/1550+054; B7: Titan; NOEMA: MWC 349 (1.86 Jy at 219 GHz, 1.91 Jy at 230.5 GHz)  
  > "we bootstrapped their fluxes using MWC 349 observations (with a flux model of 1.86 Jy at 219 GHz and 1.91 Jy at 230.5 GHz)" (2.1 PdBI/NOEMA observations)
- flux scale uncertainty: ~10% typical  
  > "Typical calibration uncertainties would amount to ∼10% for both instruments" (3.1 Continuum emission)
- self calibration: _not stated_

### Imaging

- task: GILDAS imaging, CLEAN  
  > "we carried out the imaging and analysis of all NOEMA and ALMA observations with the GILDAS software." (2.2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: Natural weighting (uniform for 12CO 3-2 cavity figure)  
  > "The imaging was performed with natural weighting for both ALMA and NOEMA." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Not subtracted in moment maps (very low level)  
  > "the continuum was not subtracted due to its very low level of emission" (Figure 2 caption)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Diskfit radiative transfer model with vertical Gaussian profile  
  > "The vertical density is assumed to have a Gaussian profile (see Eq. (1), Piétu et al. 2007)" (4. Modelling) [from Piétu et al. 2007]
- Dust opacity prescription kappa = 0.02(λ/1mm)^-β cm2/g  
  > "which is similar to that adopted by Beckwith et al. (1990) (with β = 1)" (5.2 Gas-to-dust ratio) [from Beckwith et al. 1990]

### Not stated but needed to reproduce (our reading)

- MCMC settings (walkers, steps, priors, burn-in) for emcee
- Line-free channels and continuum handling for line fits
- CASA version and calibration scripts
- Visibility binning and weighting in uv fits
- Cell size, image size, clean masks and thresholds

## Analysis recipe

1. **Continuum flux and size from uv-plane fits**: Gaussian fits in uv plane: single elliptical, and two circular Gaussians after deprojection  
  > "The spatial extent and flux values of the continuum emission were determined by fitting Gaussian functions in the u, v plane." (3.1 Continuum emission)
   - software: GILDAS
   - parameter: Deprojection with PA=356°, i=53°  
  > "(fixed PA = 356 [◦] _, i_ = 53 [◦] _)_" (Table 1)
   - fitting: _not stated_
   - validation: Compared with zero-baseline fluxes and literature (Table 2)  
  > "Our maximum flux values from the shortest baselines are consistent with those reported by single-dish observations or compact arrays (see Table 2)." (3.1 Continuum emission)
2. **Dust spectral index**: Fit slope of flux vs frequency at three frequencies, β=α-2, with 10% calibration error added  
  > "A fit to the three frequencies yields the slope α." (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **CO line opacity**: 12CO/13CO line ratio in 1 km/s channels, assuming 12C/13C=77  
  > "then τ 12 /τ 13 = 77 and we can solve for Eq. (1)." (3.3 Opacity of CO lines)
   - assumption: Opacity ratio equals elemental abundance ratio 77  
  > "opacity ratio of 12 CO over 13 CO is equal to the elemental abundance ratio (Wilson & Rood 1994)" (3.3 Opacity of CO lines)
   - fitting: _not stated_
   - validation: J=1-0 estimate agrees with J=2-1  
  > "in good agreement with the J = 2→1 transition estimate" (3.3 Opacity of CO lines)
4. **Model CO disc structure in uv plane**: Diskfit power-law models for Sigma, T, V, H fitted independently to each line in uv plane  
  > "The modelling is done in the u, v plane to avoid non-linear effects due to deconvolution." (4. Modelling)
   - software: Diskfit, emcee
   - parameter: Velocity exponent fixed to 0.5  
  > "we fixed the velocity exponent so that a v = 0.5 (Keplerian rotation)" (4. Modelling)
   - assumption: LTE, sharp outer edge, Gaussian vertical profile, constant local line width  
  > "local thermodynamic equilibrium (LTE; i.e. T 0 represents the rotation temperature of the level population distribution)" (4. Modelling)
   - fitting: Bayesian MCMC with emcee  
  > "The minimization is completed by a Bayesian analysis using a Markov chain Monte Carlo (MCMC) code, emcee (Foreman-Mackey et al. 2013)." (4. Modelling)
   - validation: Residuals in uv plane imaged; compared with channel maps and spectra  
  > "The latter is obtained by subtraction in the u, v plane before imaging and cleaning." (Figure 5 caption)
5. **CO, gas and dust masses**: CO mass from 13CO Sigma0, p, Rin, Rout with 12CO/13CO=77; H2 with ISM abundance; dust mass from mm flux and standard equation  
  > "Assuming a standard isotopic ratio 12CO/13CO = 77, these parameters yield M 12CO = 0.10" (4.2 Temperature and density laws)
   - parameter: Td = 65-90 K, β in [0,0.7]  
  > "typical values of the temperature for dust grains located at 50–100 au from this 30 L⊙ star ( T d = 65−90 K)" (5.2 Gas-to-dust ratio)
   - assumption: CO/H2 = 1e-4 ISM abundance  
  > "than the canonical ISM value of 10 [−][4] (see also the discussion on carbon depletion" (4. Modelling)
   - fitting: _not stated_
   - validation: Compared with Miotello et al. 2016 model grid  
  > "Using the grid of models developed by Miotello et al. (2016)" (4.2 Temperature and density laws)

## Software

- **CASA** : ALMA calibration  
  > "We used the CASA package to calibrate the ALMA data" (2.2 ALMA observations)
- **GILDAS** : Imaging and analysis of NOEMA and ALMA data  
  > "we carried out the imaging and analysis of all NOEMA and ALMA observations with the GILDAS software." (2.2 ALMA observations)
- **Diskfit** : Disc model fitting  
  > "with the Diskfit code (Piétu et al. 2007)" (4. Modelling)
- **emcee** : MCMC exploration  
  > "Markov chain Monte Carlo (MCMC) code, emcee (Foreman-Mackey et al. 2013)" (4. Modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 12CO 3-2 inner cavity radius | 17 | ±3 | au | 4 | an inner cavity is confirmed with a radius R in = 17 ± 3 au from [12] CO J = 3→2 |
| 13CO 2-1 inner radius | 35 | ±5 | au | 4 | The [13] CO J = 2→1 data suggest a larger value R in = 35 ± 5 au. |
| 12CO outer radius | 275 | ±3 | au | 4 | R out = 275 ± 3 au by the two transitions of [12] CO |
| 12CO opacity tau12 (J=2-1) | 14 | ±4 | dimensionless | 3 | derive τ 12 = 14 ± 4 and τ 13 = 0.18 ± 0.05 |
| 12CO 3-2 T0 at 100 au | 28.1 | ±0.2 | K | 4 | _T_ 0 (K) 28.1± 0.2 33 ± 12 |
| Stellar mass from V0 | 2.22 | ±0.01 | Msun | 4 | central stellar mass of 2.22 ± 0.01 M ⊙ |
| CO mass (12CO) | 0.10 | +0.05/-0.02 | Mearth | 5 | M 12CO = 0.10 [+] − [0] 0 [.] . [05] 02 M ⊕ |
| Dust mass | 0.03-0.52 | not stated | Mearth | 5 | We obtain values for M dust in the range 0.03−0.52 M ⊕. |
| Gas-to-dust ratio | 135-2370 | not stated | dimensionless | 5 | we can obtain a gas-to-dust mass ratio G / D in the range 135−2370. |
| Zero-baseline flux 1.3 mm | 4.00 | ±0.25 | mJy | 1 | 4.00 ± 0.25 |

## Qualitative findings

- Brightness asymmetry in 12CO 3-2 residuals coincides with the SPHERE ring region  
  > "We show that the observed CO brightness asymmetry is coincident with the complex ring structures discovered with VLT/SPHERE in the inner 90 au." (abstract)

## Claim tuples

- H: Is the gas primordial and is the disc in a transient gas dissipation phase? | E: Diskfit modelling of CO lines, gas mass from optically thin 13CO | R: Gas surface density an order of magnitude below younger Herbig Ae discs; continuous CO from 15-20 to 275 au | F: Gas is likely primordial in dissipation | **supported**
- H: Does the mm dust consist of multiple components with varying grain properties? | E: uv-plane two-component Gaussian fits at three frequencies | R: Equal flux in compact (≲50 au) and extended (~350 au) components; β difference not significant | F: Large grains dominate inner region; radial β change marginal | **partially**
- H: Is there a gas cavity? | E: 12CO 3-2 imaging and model fit | R: R_in = 17 ± 3 au | F: Small CO cavity confirmed without a dust cavity | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas mass conversion to total is very uncertain; CO/H2 and 12C/13C uncertain  
  > "The conversion to a total mass of gas is very uncertain." (4.2)
- Caveat (inferred, ours): Single-dish-like zero-baseline fluxes disagree with some literature values
- Caveat (inferred, ours): Low-S/N 13CO 1-0 only used as integrated flux
- Caveat (inferred, ours): Assumed LTE and sub-thermal excitation not tested

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Reduced datacubes and images available at CDS  
  > "Reduced datacubes and images are only available at the CDS via anonymous ftp" (title footnote)
- Missing: emcee configuration and priors
- Missing: CASA version and calibration details
- Missing: Cleaning parameters
- Missing: Only a subset of Band 7 data was calibrated; which not stated
- Data volume (inferred): ~20-50 GB (two ALMA projects plus NOEMA)
- Score (inferred): 4/5, Public ALMA data and clear model, but fitting and imaging details are missing.
- Rediscovery candidate: yes, Data are public, the recipe is moderately complete and results are numeric.

## Links

- Method: Piétu et al. 2007 (Diskfit code)
- Companion: Péricaud et al. 2017 (CO flux vs continuum correlation)
- Companion: White et al. 2016 (Earlier analysis of the same Band 7 data)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2013.1.00883.S"
 ],
 "codes_printed_but_missing": [
  "2013.1.00883.S"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 45,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
