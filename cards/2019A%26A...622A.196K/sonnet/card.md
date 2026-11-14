# Spatially resolved origin of millimeter-wave linear polarization in the nuclear region of 3C 84

`2019A&A...622A.196K` | Astronomy and Astrophysics 2019 | first author: Kim, J.-Y. | arXiv: 1811.07815 | DOI: 10.1051/0004-6361/201832920

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: What is the spatially resolved origin of mm-wave linear polarization and Faraday rotation in the nuclear region of 3C 84, probed with GMVA 86 GHz plus VLBA and ALMA data?  
  > "We report results from a deep polarization imaging of the nearby radio galaxy 3C 84 (NGC 1275)." (abstract)
- Target **3C 84 (NGC 1275, Perseus A)**: coordinates _not stated_; z/distance z=0.0176, d_L=75 Mpc  
  > "3C 84 is also a relatively nearby source at a redshift of $z=0.0176$ and a luminosity distance of $d_{L}=75$ Mpc (cite: 3c84_dist)" (Introduction); distance from Strauss et al. 1992 (cite: 3c84_dist)  
  > "3C 84 is also a relatively nearby source at a redshift of $z=0.0176$ and a luminosity distance of $d_{L}=75$ Mpc (cite: 3c84_dist)" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: ALMA 97.5, 233.0, 343.5 GHz (calibrator catalogue polarization measurements)  
  > "The source was observed at 97.5, 233.0, and 343.5 GHz and was not resolved up to the baseline length of $537.5\,k\lambda$ at all frequencies." (2.4 Contemporaneous ALMA data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ALMA epoch 2015/05/31  
  > "2015/05/31 | 97.5 | $17.14\pm0.57$" (Table 2)
- pi or archival as stated: _not stated_
- Other facility **GMVA 86 GHz**: Main polarimetric VLBI data, 8 hr, 11 antennas, May 2015  
  > "3C 84 was observed with the GMVA at 86 GHz in dual circular polarization in May 2015." (2.1 GMVA 86 GHz data)
- Other facility **VLBA 15 and 43 GHz (MOJAVE, VLBA-BU-BLAZAR)**: Archival quasi-contemporaneous polarimetric data  
  > "We made use of archival polarimetric VLBA data of 3C 84 provided by the MOJAVE program" (2.2 Contemporaneous 43 and 15 GHz VLBA data)
- Other facility **IRAM 30m (POLAMI)**: EVPA calibration of GMVA via calibrators  
  > "These calibrators were also observed as part of the POLAMI (Polarimetric Monitoring of AGN at Millimeter Wavelengths) program" (2.1.2 Polarization calibration and imaging)
- Other facility **OVRO 40 m**: 15 GHz total flux densities for flux scaling  
  > "the Owens Valley Radio Observatory (OVRO; (cite: richards11)) monitoring program provided near-in-time flux density measurements" (Appendix A)
- External data: RM ~9e5 rad/m^2 at 230 GHz used in depolarization modelling  
  > "we take a RM $\sim9\times10^{5}~{\rm rad/m^{2}}$ from (cite: plambeck14)" (4.3 Faraday depolarization) [from Plambeck et al. 2014 (cite: plambeck14)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA polarization measurements taken from the ALMA Calibrator Source Catalogue  
  > "we made use of contemporaneous (May 2015) linear polarization measurements of 3C 84 from the Atacama Large Millimeter/submillimeter Array (ALMA) Calibrator Source Catalogue" (2.4 Contemporaneous ALMA data)
- flux calibrator: _not stated_
- flux scale uncertainty: ~30% at 86 GHz GMVA; ALMA catalogue fluxes used as is  
  > "the absolute flux density of the source in this epoch could be uncertain by $\sim30$%" (2.1.1 Total intensity calibration and imaging)
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

- Resolution of nπ ambiguity in EVPA fitting  
  > "We resolve the $n\pi$ ambiguity by following (cite: hovatta12)." (2.5 / 3.3) [from Hovatta et al. 2012 (cite: hovatta12)]
- Core model-fit uncertainties  
  > "estimated their uncertainties following (cite: schinzel12)" (2.5 Model-fitting) [from Schinzel et al. 2012 (cite: schinzel12)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and observation details for the calibrator catalogue entries
- Coordinates of 3C 84
- Exact spectral/EVPA fitting code

## Analysis recipe

1. **Fit RM from EVPA vs lambda^2**: Combine 43, 86 GHz VLBI core EVPAs with ALMA EVPAs, rotate by nπ, minimise chi^2 of lambda^2 law  
  > "Then we chose a set of $n_{i}$ which provided minimum $\chi^{2}$ value." (3.3)
   - assumption: ALMA polarized flux originates from the VLBI core; no RM >~1e8 rad/m^2  
  > "we assume that most of the polarized flux observed by the ALMA at 97.5, 233.0, and 343.5 GHz originates from the same VLBI core region." (3.3)
   - fitting: _not stated_
   - validation: Reduced chi^2 = 0.59  
  > "corresponding $\chi^{2}=3.52$ and the reduced $\chi^{2}=0.59$" (3.3)

## Software

- **AIPS** : VLBI fringe fitting, calibration, D-terms (LPCAL)  
  > "standard VLBI fringe-fitting and calibration procedures in AIPS" (2.1.1)
- **DIFMAP** : Imaging and MODELFIT  
  > "The frequency-averaged (but not yet time-averaged) data were read into the DIFMAP package" (2.1.1)
- **DiFX** : Correlation  
  > "The data were correlated using the DiFX correlator" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| RM of VLBI core, May 2015 | 2.02e5 | 0.03e5 | rad/m^2 | 1 | we obtain ${\rm RM}=(2.02\pm0.03)\times10^{5}~{\rm rad/m^{2}}$ |
| Intrinsic EVPA | -38 | 7 | deg | 1 | $\chi_{\rm int}=-(38\pm7)$ deg |
| Core spectral index 15-86 GHz | 0.51 | 0.10 | dimensionless | 0 | spectral index of $\alpha=0.51\pm0.10$ |
| m_L power-law index | 0.77 | 0.18 | dimensionless | 0 | $m_{L} \propto \nu^{0.77\pm0.18}$ |
| B_SSA | 21 | 14 | G | 0 | we obtain $B_{SSA}\sim(21\pm14)$ G |

## Qualitative findings

- Polarization increases toward higher frequency; Faraday screen likely a uniform external screen, e.g. jet boundary layer.  
  > "Our Faraday depolarization modeling suggests that the RM most likely originates from an external screen with a highly uniform RM distribution." (abstract)

## Claim tuples

- H: Is the core polarization at 86 GHz resolved and higher than at lower frequencies? | E: GMVA 86 GHz, VLBA 43/15 GHz polarimetry | R: m_L ~2% at 86 GHz, 0.4-0.5% at 43 GHz, <0.1% at 15 GHz | F: Polarization degree increases with frequency | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Absolute flux density at 86 GHz uncertain by ~30%.  
  > "could be uncertain by $\sim30$%" (2.1.1)
- Caveat (inferred, ours): ALMA data are only catalogue values; RM relies on assumption that ALMA polarized flux comes from the VLBI core
- Caveat (inferred, ours): Few EVPA points and large nπ search

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: GMVA project code and access
- Missing: Analysis scripts
- Data volume (inferred): ~100 GB (VLBI)
- Score (inferred): 3/5, ALMA part is catalogue values only; VLBI recipe fairly detailed.
- Rediscovery candidate: no, ALMA data minor and project codes not given.

## Links

- Companion: Plambeck et al. 2014 (cite: plambeck14) (Earlier mm polarization and RM of 3C 84)
- Related: MOJAVE
- Related: VLBA-BU-BLAZAR
- Related: POLAMI

## Checks

```json
{
 "quotes": 29,
 "quotes_ok": 29,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2011.0.00001.CAL"
 ],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 22,
  "rate": 0.373
 },
 "evidence_ok": true
}
```
