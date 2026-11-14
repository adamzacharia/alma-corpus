# Astronomical detection of radioactive molecule <SUP>26</SUP>AlF in the remnant of an ancient explosion

`2018NatAs...2..778K` | Nature Astronomy 2018 | first author: Kamiński, Tomasz | arXiv: 1807.10647 | DOI: 10.1038/s41550-018-0541-x

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: evolved_stars, astrochemistry, stellar_physics
- Question: Can the radioactive isotopologue 26AlF be detected in the stellar-merger remnant CK Vul, and how much 26Al does the remnant contain?  
  > "Here, we report observations of millimetre-wave rotational lines of the isotopologue of aluminium monofluoride that contains the radioactive isotope (26AlF)." (abstract)
- Target **CK Vul (Nova 1670)**: coordinates _not stated_; z/distance 0.7 kpc  
  > "At a distance of 0.7 kpc ( _17_ ), the maximum" (main text); distance from Hajduk et al. 2013 (ref 17)  
  > "At a distance of 0.7 kpc ( _17_ ), the maximum" (main text)

## Data provenance

- ALMA projects: 2015.A.00013.S, 2017.A.00030.S
- bands: ALMA Band 5 (AlF 6-5) and Band 6 (AlF 7-6)  
  > "Both isotopologues were observed with ALMA in the _**J**_ **=6-5** lines located in ALMA Band" (Interferometric observations)
- frequencies and spectral setup: Band 6 spectrum 7.75 GHz wide; native binning 3906.3 kHz  
  > "In the 7.75 GHz wide spectrum acquired with ALMA in Band 6" (Excitation analysis)
- continuum bandwidth: _not stated_
- arrays: ALMA with 41 antennas (Band 6) and 41, 43 (Band 5)  
  > "|ALMA|Band 5|4, 5 Apr 2018|1.0×0.9, 156.5|41, 43|" (Table M3)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 5 beam 1.4×1.1 arcsec (natural weighting); Band 6 ~0.8 arcsec  
  > "At a beam size of 1.4´1.1 arcsec (at natural weighting), both emission regions are resolved" (Interferometric observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Band 5: 4, 5 Apr 2018; Band 6: 2, 3 Jun 2016  
  > "|ALMA|Band 6|2, 3 Jun 2016|0.8×0.8, 96.5|41|" (Table M3)
- pi or archival as stated: _not stated_
- Line: 27AlF J=6-5 (197.83306 GHz)
- Line: 27AlF J=7-6 (230.79377 GHz)
- Line: 26AlF J=6-5 (200.95430 GHz)
- Line: 26AlF J=7-6 (234.43488 GHz)
- Other facility **NOEMA**: AlF 3-2 and 4-3 interferometry, plus 89 and 146 GHz setups  
  > "The _**J**_ **=3-2** transition of both AlF isotopologues was observed with the emerging NOEMA interferometer." (Interferometric observations)
- Other facility **JVLA**: Ka-band AlF 1-0 spectrum  
  > "covered by a _Ka_ -band spectrum obtained with the Karl G. Jansky Very Large Array (JVLA) in the DnC configuration" (Interferometric observations)
- Other facility **IRAM 30m and APEX**: single-dish line survey of AlF  
  > "obtained with the IRAM 30 m and Atacama Pathfinder Experiment 12 m (APEX) telescopes in 2014-2017" (Single-dish observations)
- Other facility **SMA**: complementary molecular imaging reported earlier  
  > "Interferometric imaging of molecular emission was also obtained with the Submillimeter Array (SMA) and reported earlier" (Interferometric observations)
- External data: 27AlF Dunham parameters and hyperfine constants from laboratory measurements  
  > "we used mass-scaled Dunham parameters and hyperfine constants derived from laboratory measurements ( _31_ )" (Spectroscopic data for AlF isotopologues) [from Hedderich & Bernath 1992 (ref 31)]
- External data: permanent dipole moment of 1.53 D  
  > "A permanent dipole moment of _µ_ =1.53 D ( _ref._ _33_ ) was adopted for both isotopologues." (Spectroscopic data for AlF isotopologues) [from Lide 1965 (ref 33)]
- External data: AlF collision rates with p-H2 and He  
  > "Using collision rates of AlF with _p_ -H 2 and with He at 10 K ( _39, 40_ )" (Excitation analysis) [from Gotoum et al. (refs 39, 40)]
- Simulation/model as data: Monash stellar-evolution models (solar metallicity, 1-3 Msun) and TYCHO models for 26Al yields  
  > "we analyzed state of the art solar-metallicity evolutionary sequences calculated with the Monash stellar-evolution code ( _41_ )" (Nucleosynthesis of 26Al)

## Processing

### Calibration

- pipeline or manual: standard procedures; ALMA and NOEMA self-calibrated on continuum  
  > "All the interferometric data were calibrated using standard procedures. ALMA and NOEMA data were additionally self-calibrated on the strong continuum source." (Interferometric observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 20% systematic  
  > "a 20% systematic errors in the flux calibrations" (Excitation analysis)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "Interferometric maps presented here were obtained in CASA ( _35_ ) and using CLEAN." (Interferometric observations)
- deconvolver: _not stated_
- weighting robust: natural or robust, adjusted to aims  
  > "The weighting of visibilities, natural or robust, was adjusted to the aims of the" (Interferometric observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: zeroth- or first-order polynomial fit to full band avoiding strong lines  
  > "Continuum emission was subtracted from the visibilities as a zeroth- or first order polynomial fitted to the full band and avoiding strong lines." (Interferometric observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Band 5 1.0×0.9 arcsec robust; Band 6 0.8×0.8 arcsec  
  > "|ALMA|Band 5|4, 5 Apr 2018|1.0×0.9, 156.5|41, 43|" (Table M3)
- final rms: _not stated_

### Inherited from earlier work

- 27AlF single-dish line survey data  
  > "The presence of [27] AlF in CK Vul was revealed in the line survey" (Single-dish observations) [from Kamiński et al. 2017 (ref 12)]
- SMA imaging reported earlier  
  > "Interferometric imaging of molecular emission was also obtained with the Submillimeter Array (SMA) and reported earlier" (Interferometric observations) [from Kamiński et al. 2015 (ref 5)]
- Method similar to earlier 26AlF spectra calculations  
  > "The method of our calculations is similar to that used in earlier studies of rotational spectra of [26] AlF ( _14_ )." (Spectroscopic data for AlF isotopologues) [from Guelin et al. 1995 (ref 14)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline details
- robust values and cell/image sizes
- clean masks, thresholds and iteration limits
- line-free channels for continuum subtraction
- self-calibration solution intervals
- flux and bandpass calibrators
- aperture used to extract spectra
- emcee prior ranges and walker count

## Analysis recipe

1. **Compute AlF line list**: mass-scaled Dunham parameters with hyperfine structure derived for 26AlF from 27AlF  
  > "Accurate line positions of [26] AlF were calculated through the mass-scaled Dunham parameters of [27] AlF." (Spectroscopic data for AlF isotopologues)
   - software: pgopher
   - assumption: dipole moment 1.53 D for both isotopologues  
  > "A permanent dipole moment of _µ_ =1.53 D ( _ref._ _33_ ) was adopted for both isotopologues." (Spectroscopic data for AlF isotopologues)
   - fitting: _not stated_
   - validation: _not stated_
2. **Image data and measure line fluxes**: calibrate, self-calibrate, subtract continuum, CLEAN; extract spectra in AlF region; deblend 26AlF 4-3 and SO2 with two Gaussians; mirror profile for contaminated 27AlF 7-6  
  > "The line centers were fixed while the amplitudes and widths were free parameters in this / [2] minimization procedure." (Interferometric observations)
   - software: CASA
   - fitting: _not stated_
   - validation: chance coincidence probability 1:840 per line; all four lines matching below 10^-11  
  > "A probability that all four lines match the calculated frequencies is smaller than 10 [-11] ." (Excitation analysis)
3. **Population-diagram fit for Tex, N27 and isotopic ratio**: MCMC linear fits to population diagram with beam filling from 1.80×0.84 arcsec source; saturation correction iteration  
  > "Free parameters of the population-diagram fit were the excitation temperature, _T_ ex, the column density of [27] AlF, _N_ 27, and the ratio" (Excitation analysis)
   - software: emcee
   - parameter: a few thousand walkers; 20% flux calibration error  
  > "A few thousand “walkers” were used in _emcee_ to derive the posterior distributions." (Excitation analysis)
   - assumption: same volume and single Tex for both isotopologues; thermodynamic equilibrium  
  > "We assumed that both isotopologues are located in the same volume and have the same single excitation temperature." (Excitation analysis)
   - fitting: emcee with uniform priors on Tex, N27, N27/N26  
  > "We used uniform (“uninformative”) priors for the three parameters" (Excitation analysis)
   - validation: critical densities 10^4 to 10^7 cm-3 suggest near-LTE  
  > "The AlF gas is likely thermalized and the level population are likely close to TE." (Excitation analysis)
4. **Model 26Al nucleosynthesis in RGB stars**: Monash and TYCHO stellar evolution models sampled at the RGB tip  
  > "we sampled the interior composition of the star at the tip of the RGB, before core helium burning is ignited." (Nucleosynthesis of 26Al)
   - software: Monash code, TYCHO
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : imaging with CLEAN  
  > "Interferometric maps presented here were obtained in CASA ( _35_ ) and using CLEAN." (Interferometric observations)
- **emcee** : MCMC population-diagram fits  
  > "We used a _python_ ’s _emcee_ implementation ( _36_ )" (Excitation analysis)
- **pgopher** : line frequencies, Eu, line strengths and partition functions  
  > "were derived using _pgopher_ ( _34_ )" (Spectroscopic data for AlF isotopologues)
- **TYCHO** 6.0: stellar evolution of 0.9-3.0 Msun stars  
  > "TYCHO (version 6.0) stellar evolution code developed by David Arnett" (Nucleosynthesis of 26Al)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 26Al mass | 3.4e24 | ±1.8e24 | g | 3 | we derive a total mass of the observed [26] Al of (3.4±1.8)×10 [24] g |
| AlF emission FWHM size | 1.80×0.84 | ±0.05, ±0.06 | arcsec | 2 | 1.80(±0.05)×0.84(±0.06) arcsec, with the major axis at a position angle of 60°(±1°) |
| 26AlF 6-5 flux (ALMA) | 0.70 | 0.09 | Jy km/s | 2 | /6-5/200.95430/33.76/153.94/1.0/0.70/0.09/ALMA/ |
| 26AlF 7-6 flux (ALMA) | 0.56 | 0.08 | Jy km/s | 2 | /7-6/234.43488/45.01/178.98/0.8/0.56/0.08/ALMA/ |
| 27AlF 6-5 flux (ALMA) | 4.94 | 0.09 | Jy km/s | 2 | /6-5/197.83306/33.23/84.29/1.0/4.94/0.09/ALMA/ |
| 26Al-induced ionization rate | 2.0e-16 | not stated | s-1 per H nucleus | 0 | our results suggest a [26] Alinduced ionization rate of 2.0·10 [-16] s [-1] per H nucleus for CK Vul |
| Mergers per year needed to explain Galactic 26Al | ~1100 | not stated | per year | 0 | one would need ~1100 mergers like CK Vul going off every year |

## Qualitative findings

- First firm detection of a radioactive molecule in any astronomical object, 26AlF, in CK Vul  
  > "is the first firm detection of a radioactive molecule in any astronomical object" (main text)
- Progenitor contained at least one solar-mass RGB star  
  > "the CK Vul system contained at least one solar-mass star that evolved to the red giant branch." (abstract)

## Claim tuples

- H: 26AlF is present in CK Vul | E: Mapped 26AlF and 27AlF in several transitions with ALMA, NOEMA, JVLA | R: Line positions, widths and spatial distribution of 26AlF match 27AlF | F: 26AlF is detected | **supported**
- H: CK Vul-like mergers are major producers of Galactic 26Al | E: Compared derived 26Al mass with the Galactic production rate and red nova rates | R: ~1100 mergers per year would be needed | F: unlikely major producers | **supported**
- H: The progenitor can supply the observed 26Al | E: Stellar models of 26Al in RGB He cores | R: Stars of 0.8-2.5 Msun store about 1000 times more 26Al than observed | F: a merger of low-mass stars with at least one on the RGB is likely | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: False identification is highly unlikely given chance coincidence probabilities  
  > "Therefore, a false identification is highly unlikely." (Excitation analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainties underestimated; AlF gives only a lower limit on 26Al  
  > "These uncertainties are underestimated and do not take into account, for instance, errors in the source size." (Excitation analysis)
- Caveat (inferred, ours): The LTE assumption is untested
- Caveat (inferred, ours): The 26AlF 4-3 deblending depends on the SO2 fit
- Caveat (inferred, ours): Assuming atomic and dust Al are absent gives only a lower limit
- Caveat (inferred, ours): The source size is a single average

## Reproducibility

- Data public (paper): ALMA data cited by project code  
  > "This paper makes use of the following ALMA data:" (Acknowledgments)
- Products in archive: _not stated_
- Code: Spectroscopic data for AlF available online (goo.gl link)  
  > "are available online (goo.gl/uMV1h9)" (Spectroscopic data for AlF isotopologues)
- Missing: CASA version, imaging parameters and masks
- Missing: aperture definitions for spectra
- Missing: priors ranges
- Missing: stellar model inputs
- Data volume (inferred): about 100-300 GB for two ALMA datasets
- Score (inferred): 3/5, The data are public and the fluxes are tabulated, but the imaging and extraction details are sparse.
- Rediscovery candidate: no, The recipe lacks imaging and extraction detail and relies on non-ALMA data.

## Links

- Method: Goldsmith & Langer 1999 (ref 38) (population diagram analysis)
- Companion: Kamiński et al. 2017 (ref 12) (single-dish line survey of CK Vul)
- Companion: Kamiński et al. 2015 (ref 5) (earlier discovery of the molecular remnant)
- Related: IRAM 30m and NOEMA programs
- Related: APEX programs 095.F-9543(A), 296.D-5009(A)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 45,
  "rate": 0.577
 },
 "evidence_ok": true
}
```
