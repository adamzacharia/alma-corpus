# Modelling the abundance structure of isocyanic acid (HNCO) towards the low-mass solar type protostar IRAS 16293-2422

`2019MNRAS.483.2014H` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Hernández-Gómez, Antonio | arXiv: 1811.00766 | DOI: 10.1093/mnras/sty2971

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: What is the HNCO abundance structure toward IRAS 16293-2422, modelled with non-LTE radiative transfer using new HNCO-H2 collisional rate coefficients, and how does it compare with a chemical model?  
  > "In this work, we model HNCO spectral line profiles toward the low-mass solar" (abstract)
- Target **IRAS 16293-2422**: coordinates _not stated_; z/distance 141 pc  
  > "IRAS 16293-2422 (I16293 hereafter), a Class 0 protostar
located at 141 [+] − [30] 21 [pc] [(][Dzib] [et] [al.] [2018][)]" (1 INTRODUCTION); distance from Dzib et al. 2018  
  > "IRAS 16293-2422 (I16293 hereafter), a Class 0 protostar
located at 141 [+] − [30] 21 [pc] [(][Dzib] [et] [al.] [2018][)]" (1 INTRODUCTION)

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: _not stated_
- frequencies and spectral setup: 329.15-362.90 GHz, ~0.2 km/s channel spacing  
  > "reported ALMA observations in
the frequency range [329.15, 362.90] GHz with a ∼0.2 km
s [−][1] channel spacing" (2.4 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5 arcsec  
  > "a ∼0.5 [′′] spatial resolution" (2.4 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS survey (Jørgensen et al. 2016)  
  > "PILS, the ALMA Protostellar Interferometric Line Survey
(Jørgensen et al. 2016)" (2.4 ALMA observations)
- Line: HNCO 15(0,15)-14(0,14) (329664.367 MHz)
- Other facility **IRAM-30m / JCMT (TIMASSS)**: Single-dish spectra 80-280 GHz and 328-366 GHz; new IRAM 2017 high-resolution HNCO 5-4 data  
  > "conducted with the IRAM-30m
telescope (Granada, Spain) between 80 and 280 GHz and
the JCMT-15m telescope (Mauna Kea, Hawaii) between
328 and 366 GHz" (2.1 IRAM-30m and JCMT-15m observations)
- Other facility **APEX**: Spectra 265-323.5 GHz and 372-462 GHz  
  > "The observations of I16293 in the frequency range 265–
323.5 GHz were performed with the APEX telescope" (2.2 APEX observations)
- Other facility **Herschel-HIFI (CHESS)**: Spectral scans in bands 3b and 4a (860-1060 GHz)  
  > "The data used in this article are part of a full
spectral coverage of bands 3b (860-960 GHz ; Obs. Id
1342192330) and 4a (950-1060 GHz ; Obs. Id 1342191619)" (2.3 Herschel-HIFI observations)
- External data: HNCO-H2 collisional rate coefficients (ortho and para)  
  > "The HNCO collisional coefficients are taken from Sahnoun
et al. (2018)" (3 RESULTS) [from Sahnoun et al. (2018)]
- External data: 1D temperature and density structure of the envelope  
  > "we have used the 1D physical structure
derived by Crimier et al. (2010), fixing thereby the main H 2
density for all components" (3.2 The physical model) [from Crimier et al. (2010)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
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
- final rms: _not stated_

### Inherited from earlier work

- ALMA observations and reduction come from the PILS survey  
  > "PILS, the ALMA Protostellar Interferometric Line Survey
(Jørgensen et al. 2016), reported ALMA observations" (2.4 ALMA observations) [from Jørgensen et al. (2016)]
- TIMASSS observation details  
  > "For more details
on these observations, see Caux et al. (2011)." (2.1 IRAM-30m and JCMT-15m observations) [from Caux et al. (2011)]
- Continuum SED model, to be published  
  > "derived the expected
continuum from ∼1 mm to ∼70 µm (∼150 GHz to ∼5 THz)
(Bottinelli et al., in prep.)." (3.2 The physical model) [from Bottinelli et al., in prep.]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details, and how spectra were extracted from the PILS cubes (aperture, position)
- MCMC priors, ranges and convergence criteria in CASSIS
- Predicted continuum SED values used for the lines
- Nautilus input files and the exact protostellar-phase set-up
- Which lines were fitted jointly and how upper limits were weighted

## Analysis recipe

1. **Identify HNCO lines**: Identify HNCO transitions in all datasets using CASSIS and CDMS  
  > "a software developed at IRAP-UPS/CNRS which makes use of the CDMS database" (3 RESULTS)
   - software: CASSIS
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit non-LTE three-component model**: RADEX in CASSIS with three components, fitted with MCMC chi2 minimisation  
  > "We used the Monte Carlo Markov Chain (MCMC)
method inside CASSIS (Hastings 1970; Guan et al. 2006)
which explores the space of parameters to find the best
solution by means of χ [2] minimisation" (3.3 Model fitting)
   - software: CASSIS, RADEX
   - parameter: 10 free parameters out of 18; 1,000 models run  
  > "running 1,000 models
with these 10 free parameters randomly chosen" (3.3 Model fitting)
   - parameter: VLSR fixed 4.1 km/s for envelopes; cold FWHM fixed 0.4 km/s; sizes fixed 0.5 and 100 arcsec for hot corino and cold envelope  
  > "we
fixed V LSR of the lines for the warm and cold envelopes
to 4.1 km s [−][1]" (3.3 Model fitting)
   - assumption: Source A alone is responsible for the hot corino emission; ortho-to-para H2 = 3 for hot corino; para-H2 dominant in envelope  
  > "For the hot corino, we adopted an ortho-to-para
H 2 ratio of 3" (3.3 Model fitting)
   - fitting: MCMC chi2 minimisation; priors not stated  
  > "which explores the space of parameters to find the best solution by means of" (3.3 Model fitting)
   - validation: Predicted continuum checked against observations to about 15%; comparison with Green coefficients  
  > "We have checked that the predicted continuum level is consistent with the observations

within an error of about 15%." (3.2 The physical model)
3. **Compare with chemical model**: Nautilus gas-grain model for parental cloud then protostellar envelope  
  > "we computed the
abundance profiles using the Nautilus chemical code." (4.4 Chemical modelling with Nautilus)
   - software: Nautilus
   - parameter: Best: Av = 4, zeta = 8.0e-17 s-1  
  > "The abundance
profiles that best reproduces the observations are obtained
with A v = 4 and ζ = 8.0 × 10 [−][17] s [−][1] ." (4.4 Chemical modelling with Nautilus)
   - fitting: _not stated_
   - validation: Compared with abundances from the radiative transfer model  
  > "we observe that the abundance profile, although not
constant, is in good agreement with the abundances derived
directly from the observations with our radiative transfer
model." (4.5 Results of the Nautilus chemical model for HNCO)

## Software

- **CASSIS** : Line identification and RADEX MCMC modelling  
  > "We used the Monte Carlo Markov Chain (MCMC) method inside CASSIS (Hastings 1970; Guan et al. 2006)" (3.3 Model fitting)
- **RADEX** : Non-LTE radiative transfer  
  > "we used the statistical equilibrium non-LTE radiative transfer
code RADEX (van der Tak et al. 2007)" (3 RESULTS)
- **Nautilus** : Chemical modelling of HNCO abundance profile  
  > "Nautilus is a three phase gas-grain chemical code" (4.4 Chemical modelling with Nautilus)
- **GILDAS/CLASS90** : IRAM and APEX data reduction  
  > "the data reduction was performed using the
GILDAS/CLASS90 [2] package." (2.2 APEX observations)
- **HIPE** : HIFI data processing  
  > "Using the HIPE
(Ott 2010) “flagTool” task, we removed the spurs" (2.3 Herschel-HIFI observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Hot corino N(HNCO) | 1.9e16 | 0.4e16 | cm-2 | 2 | Hot corino (1.9 ± 0.4) × 10 [16] 190 ± 50 6.2 ± 0.7 2.9 ± 0.1 0.5 [∗] 3×10 [8] (7.1 ± 0.6) × 10 [−][8] |
| Hot corino Tkin | 190 | 50 | K | 2 | Hot corino (1.9 ± 0.4) × 10 [16] 190 ± 50 6.2 ± 0.7 2.9 ± 0.1 0.5 [∗] 3×10 [8] (7.1 ± 0.6) × 10 [−][8] |
| Hot corino abundance X(HNCO) | 7.1e-8 | 0.6e-8 | relative to H2 | 2 | abundance relative to H 2 of
(7.1 ± 0.6) × 10 [−][8] for a fixed size of 0.5 [′′] |
| Warm envelope abundance | 1.8e-11 | 0.4e-11 | relative to H2 | 2 | Warm envelope (2.5 ± 0.5) × 10 [13] 31 ± 5 4.9 ± 0.8 4.1 [∗] 15.6 ± 2.4 5×10 [7] (1.8 ± 0.4) × 10 [−][11] |
| Warm envelope size | 15.6 | 2.4 | arcsec | 2 | Warm envelope (2.5 ± 0.5) × 10 [13] 31 ± 5 4.9 ± 0.8 4.1 [∗] 15.6 ± 2.4 5×10 [7] (1.8 ± 0.4) × 10 [−][11] |
| Cold envelope abundance | 9.8e-12 | 0.3e-12 | relative to H2 | 2 | Cold envelope (5.3 ± 0.6) × 10 [12] 8.7 ± 0.8 0.4 [∗] 4.1 [∗] 100.0 [∗] 3×10 [6] (9.8 ± 0.3) × 10 [−][12] |
| Best-matching protostar age in Nautilus | 5.8e4 | not stated | yr | 3 | If we take an age of about 5.8×10 [4]

years |

## Qualitative findings

- Ka=0,1 lines are well reproduced; Ka=2 lines are not  
  > "While the transitions on the _K_ a = 0, 1 bands are
well reproduced, the transitions belonging to the upper
rotational band _K_ a = 2 levels are not." (5 CONCLUSIONS)

## Claim tuples

- H: HNCO line profiles are explained by three physical components | E: Non-LTE RADEX modelling with MCMC of single-dish and ALMA lines | R: Hot corino 190 K, warm envelope 31 K, cold envelope 8.7 K with the abundances in Table 1 | F: Emission arises from hot corino, warm envelope and cold outer envelope | **supported**
- H: Radiative-transfer abundances agree with chemical model predictions | E: Nautilus two-step models of cloud and envelope | R: Younger ages agree better; the age depends strongly on initial parameters | F: HNCO cannot serve as a reliable chemical clock | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: HNCO is not always in LTE, and H2 collision rates are needed rather than He rates  
  > "A non-LTE radiative transfer
approach is necessary to properly interpret the line profiles, and accurate collisional
rate coefficients are needed." (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Observations cannot constrain sizes of the hot corino and extended envelope  
  > "study cannot constrain the size of the hot corino, nor that
of the extended envelope" (3.3 Model fitting)
- Caveat (inferred, ours): ALMA data play a minor role, and the hot corino size is fixed, so its abundance is degenerate with that size
- Caveat (inferred, ours): Uncertainties from MCMC with 1,000 models may be underestimated
- Caveat (inferred, ours): Ka=2 lines are poorly fit

## Reproducibility

- Data public (paper): ALMA PILS data are cited with project 2013.1.00278.S; the other data are described as survey or telescope data  
  > "This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2013.1.00278.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Continuum SED model (in prep.)
- Missing: MCMC priors and settings
- Missing: ALMA spectrum extraction details
- Data volume (inferred): ~100 GB (PILS ALMA data plus small single-dish spectra)
- Score (inferred): 3/5, The model set-up is mostly described, but several inputs and the fit settings are missing.
- Rediscovery candidate: no, The ALMA part is minor and the work depends on multi-facility data and unpublished inputs.

## Links

- Method: Sahnoun et al. (2018) (HNCO-H2 collisional rate coefficients)
- Method: Jørgensen et al. (2016) (PILS ALMA survey)
- Companion: Crimier et al. (2010) (1D physical structure of I16293)
- Related: PILS
- Related: TIMASSS
- Related: CHESS

## Checks

```json
{
 "quotes": 45,
 "quotes_ok": 45,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 33,
  "rate": 0.465
 },
 "evidence_ok": true
}
```
