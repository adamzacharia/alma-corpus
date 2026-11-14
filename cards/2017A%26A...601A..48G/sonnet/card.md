# Exploring molecular complexity with ALMA (EMoCA): Simulations of branched carbon-chain chemistry in Sgr B2(N)

`2017A&A...601A..48G` | Astronomy and Astrophysics 2017 | first author: Garrod, R. T. | arXiv: 1701.07160 | DOI: 10.1051/0004-6361/201630254

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: astrochemistry, star_formation
- Question: Explain the observed i:n ratio of propyl cyanide in Sgr B2(N2), predict abundances of the four butyl cyanide isomers and alkanes up to pentane, and test for n-butyl cyanide in EMoCA data  
  > "Through computational methods, we seek to explain the observed $i$:$n$ ratio for propyl cyanide, and to predict the abundances of the four different forms of the homologous nitrile, butyl cyanide (C$_4$H$_9$CN)." (abstract)
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- External data: Gas-phase rate data for CN addition to C3H6 and C4H8 at 195 K and 298 K  
  > "based on the rates provided by Gannon et al. (2007) at 195 K and 298 K" (2.2.2 CN addition to carbon multiple bonds) [from Gannon et al. 2007 (cite: Gannon2007)]
- External data: Observed i/n propyl cyanide ratio 0.40 ± 0.06 and abundances toward Sgr B2(N2)  
  > "indicating an $i$/$n$ ratio of $0.40 \pm 0.06$" (Introduction) [from (cite: Belloche14)]
- External data: Spectroscopic predictions for n-C4H9CN in CDMS  
  > "Using the spectroscopic predictions of (cite: Ordu12) that are available in the CDMS catalog, we searched for *n-*C$_4$H$_9$CN" (4 Comparison with observations) [from (cite: Ordu12)]

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

- Basic chemical and physical treatments of MAGICKAL  
  > "The basic chemical and physical treatments used in the model have been described in detail in past publications; in particular, by (cite: GWWH) and (cite: Garrod13)." (Methods) [from (cite: GWWH); (cite: Garrod13)]
- Chemical network based on Belloche et al. 2014 with Mueller16 additions; initial elemental abundances as Garrod13  
  > "The chemical network is based on that presented by (cite: Belloche14), and includes the recent additions by (cite: Mueller16)." (2.2 Chemical model) [from (cite: Belloche14); (cite: Mueller16); (cite: Garrod13)]

### Not stated but needed to reproduce (our reading)

- EMoCA data reduction, line-survey spectral setup and calibration details are not given
- Fitting/LTE modelling details (spectral modelling software, linewidth, rms) for the n-C4H9CN upper limit
- Full MAGICKAL code and network files, and ODE solver settings
- Warm-up timescale values for fast/medium/slow in this paper

## Analysis recipe

1. **Run collapse and warm-up chemical models**: MAGICKAL three-phase rate-equation model with free-fall collapse then warm-up from 8 to 400 K at three timescales  
  > "The physical model consists of two stages: free-fall collapse, followed by a dynamically-static warm-up." (2.1 Physical model)
   - software: MAGICKAL
   - parameter: n_H = 2e8 cm-3 post-collapse; zeta = 1.3e-17 s-1; 0.1 micron grains  
  > "A post-collapse gas density of $n_{\mathrm{H}} = 2 \times 10^{8}$ cm$^{-3}$ is assumed" (2.1 Physical model)
   - assumption: Canonical cosmic-ray ionization rate 1.3e-17 s-1  
  > "A canonical cosmic-ray ionization rate of $\zeta$ = $1.3 \times 10^{-17}$ s$^{-1}$ is assumed" (2.1 Physical model)
   - fitting: _not stated_
   - validation: Compared model ice abundances and i:n ratio with observations; tested high CN-addition barriers  
  > "In order to test the dependence of the model results on these barriers, we re-ran the collapse model and the three subsequent warm-up models" (3.6 High activation-energy models)
2. **Search for n-C4H9CN in EMoCA spectrum and derive upper limit**: Assumed source size 0.7'', T=200 K and propyl cyanide linewidth; derived column-density upper limit with partition function corrections  
  > "Assuming a source size of 0.7$\ensuremath{''}$, a temperature of 200 K, and the same linewidth as for *n-*C$_3$H$_7$CN, we derive an upper limit" (4 Comparison with observations)
   - assumption: Temperature scaling r^-0.83; H2 column inversely proportional to radius  
  > "With a temperature scaling as r$^{-0.83}$ (cite: Rolffs11)" (4 Comparison with observations)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MAGICKAL** : Coupled gas-phase/grain-surface/ice-mantle chemical kinetics simulations  
  > "coupled gas-phase, grain-surface, and ice-mantle chemical kinetics model *MAGICKAL*" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Upper limit N(n-C4H9CN) in Sgr B2(N2) | 1.2e17 | not stated | cm-2 | 2 | we derive an upper limit to the column density of *n-*C$_4$H$_9$CN of $1.2 \times 10^{17}$ cm$^{-2}$ |
| Upper limit [n-C4H9CN]/[n-C3H7CN] | 0.59 | not stated | dimensionless | 2 | The resulting upper limit on the abundance ratio \[*n-*C$_4$H$_9$CN\] / \[*n-*C$_3$H$_7$CN\] = 0.59 |
| Model i/n propyl cyanide, medium warm-up low EA | 0.24 | not stated | dimensionless | 1 | C$_3$H$_7$CN, $i$ / $n$ / / 3.0 / / 0.45 / / 0.24 / / 0.17 / / 1.8 / / 1.5 |

## Qualitative findings

- sec-butyl cyanide is predicted to be the dominant butyl cyanide form; tert form is least abundant  
  > "The *sec* form of butyl cyanide is expected to be the most abundant" (Conclusions)

## Claim tuples

- H: Updated network with CN addition reproduces observed i:n propyl cyanide ratio | E: MAGICKAL models with fast/medium/slow warm-up and low/high CN barriers | R: Model i/n spans 0.17 to 3.0 versus observed 0.40 | F: Observed ratio reproduced, best for medium to fast warm-up | **supported**
- H: n-butyl cyanide is detectable in EMoCA data | E: Searched EMoCA spectrum of Sgr B2(N2) | R: Non-detection; abundance ratio to n-propyl cyanide <0.59 | F: Upper limit consistent with model range 0.1–1 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cosmic-ray ionization rate poorly constrained; full sensitivity study left for future  
  > "the cosmic-ray ionization rate for Sgr B2(N2) is poorly constrained by observations" (5 Discussion)
- Caveat (inferred, ours): Model results depend on assumed CN-addition barriers
- Caveat (inferred, ours): No fit of models to observations beyond ratio comparison

## Reproducibility

- Data public (paper): Interferometric data available in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MAGICKAL code and warm-up timescales
- Missing: EMoCA spectral modelling details
- Data volume (inferred): Not needed for the modelling; EMoCA data of order hundreds of GB
- Score (inferred): 3/5, Chemical network tables given but code and timescales not provided; ALMA part minor.
- Rediscovery candidate: no, Main results come from a non-public code; ALMA part is only an upper limit.

## Links

- Method: Garrod 2013 (cite: Garrod13) (Basic model treatment)
- Companion: Belloche et al. 2014 (cite: Belloche14) (Detection of i-propyl cyanide in EMoCA)
- Related: EMoCA

## Checks

```json
{
 "quotes": 24,
 "quotes_ok": 24,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 16,
  "rate": 0.267
 },
 "evidence_ok": true
}
```
