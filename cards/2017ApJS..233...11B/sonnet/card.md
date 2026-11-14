# Rotational and High-resolution Infrared Spectrum of HC<SUB>3</SUB>N: Global Ro-vibrational Analysis and Improved Line Catalog for Astrophysical Observations

`2017ApJS..233...11B` | The Astrophysical Journal Supplement Series 2017 | first author: Bizzocchi, Luca | arXiv: 1711.08592 | DOI: 10.3847/1538-4365/aa9571

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: astrochemistry, star_formation
- Question: Can a global ro-vibrational analysis of laboratory HC3N spectra give accurate rest frequencies, and does it improve the LTE modelling of vibrationally excited HC3N in the ALMA EMoCA spectrum of Sgr B2(N2)?  
  > "perform a global fit of all the literature data with a careful treatment of the resonance effects" (Introduction)
- Target **Sgr B2(N2)**: coordinates _not stated_; z/distance systemic velocity 74 km/s  
  > "a velocity offset of $-1.0$ km s$^{-1}$ with respect to the assumed systemic velocity of Sgr B2(N2) of 74 km s$^{-1}$" (Astrophysical Implications); distance from _not stated_

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
- Other facility **Laboratory FTIR and mm/submm spectrometers (Bologna, Garching, Cologne)**: New IR spectra 450-1350 cm-1 and rotational spectra up to ~1 THz of HC3N  
  > "A substantial amount of new spectroscopic data of HC$_3$N have been collected in four laboratories located in Bologna, Cologne, and Munich." (Experiments)
- External data: ALMA EMoCA 3 mm spectral survey of Sgr B2(N2) and its LTE model parameters  
  > "have recently published a complete 3 mm spectral survey of the hot molecular core Sgr B2(N2) performed with the Atacama Large Millimeter/submillimeter Array (ALMA)." (Astrophysical Implications) [from (cite: Belloche-AA16-EMoCA)]
- External data: Experimental dipole moment of HC3N used for Einstein A  
  > "computed using the experimental values of the dipole moment derived by (cite: DeLeon-JCP85-HC3N)" (Astrophysical Implications) [from (cite: DeLeon-JCP85-HC3N)]

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

- LTE model parameters: source size 0.9'', T=200 K, linewidth 5.8 km/s, offset -1.0 km/s, N=5.2e17 cm-2  
  > "with the same parameters as derived in (cite: Belloche-AA16-EMoCA): a source size of 0.9$''$, a rotational temperature of 200 K" (Astrophysical Implications) [from (cite: Belloche-AA16-EMoCA)]

### Not stated but needed to reproduce (our reading)

- EMoCA data reduction, calibration and imaging details
- Exact spectral windows, frequencies and beam sizes used
- Dipole moment value and the new line list file needed for WEEDS
- Continuum subtraction and how blended species were modelled

## Analysis recipe

1. **Global ro-vibrational fit of lab data**: Weighted least-squares fit of effective Hamiltonian to IR and rotational lines  
  > "A different weighting factor, $w_i = 1/\sigma_i^2$ has been given to each $i$-th datum" (Analysis)
   - software: SPFIT, custom Python code
   - fitting: Iterative least squares; some constants fixed from linear v-dependence  
  > "The coefficients of the molecular Hamiltonian are optimised through an iterative least-squares procedure" (Analysis)
   - validation: Weighted rms 0.875  
  > "We obtained $\sigma_\text{rms} = 0.875$" (Discussion)
2. **Model Sgr B2(N2) HC3N spectrum with new predictions**: LTE synthetic spectra overlaid on ALMA EMoCA spectrum, compared with old predictions  
  > "We model the emission of the vibrationally excited states of HC$_3$N above $\varv_7 = 1$ assuming local thermodynamic equilibrium (LTE)" (Astrophysical Implications)
   - software: WEEDS
   - fitting: _not stated_
   - validation: Visual comparison with spectrum using old vs new predictions  
  > "it improves the agreement between the synthetic and observed spectra for $\varv_7 = 4$ and $\varv_5=\varv_7=1$" (Astrophysical Implications)

## Software

- **SPFIT** : Computational core of the global fit  
  > "uses the SPFIT program (cite: Pick-JMS91-calpgm) as the computational core" (Analysis)
- **WEEDS** : LTE synthetic spectra for Sgr B2(N2)  
  > "The computation has been performed using the software WEEDS (cite: Maret-AA11-WEEDS)" (Astrophysical Implications)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Weighted rms of global fit | 0.875 | not stated | dimensionless | 1 | We obtained $\sigma_\text{rms} = 0.875$ |

## Qualitative findings

- New v6=1,v7=2 state of HC3N identified in EMoCA spectrum  
  > "one previously unreported vibrational state of HC$_3$N ($\varv_6=1,\varv_7=2$) has been newly identified in the EMoCA observed spectra." (Conclusion)

## Claim tuples

- H: Accurate treatment of resonances improves HC3N modelling in Sgr B2(N2) | E: LTE models with new vs old predictions compared with EMoCA spectrum | R: Inconsistencies for v7=4 and v5=v7=1 resolved; v4=1 and v6=2 unchanged | F: New predictions remove discrepancies | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Agreement judged visually, no quantitative fit statistics
- Caveat (inferred, ours): ALMA reprocessing details absent

## Reproducibility

- Data public (paper): ALMA data available in archive  
  > "The interferometric data are available in the ALMA archive at" (Acknowledgments)
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging details
- Missing: LTE model inputs beyond those inherited
- Data volume (inferred): Large (EMoCA 3 mm survey cubes, hundreds of GB)
- Score (inferred): 2/5, ALMA role minor and processing details inherited
- Rediscovery candidate: no, ALMA part is a qualitative comparison; main results are laboratory.

## Links

- Companion: (cite: Belloche-AA16-EMoCA) (Source of ALMA EMoCA data and LTE parameters)
- Related: EMoCA

## Checks

```json
{
 "quotes": 20,
 "quotes_ok": 20,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 1,
 "numeric_problems": 0,
 "fill": {
  "facts": 56,
  "stated": 15,
  "rate": 0.268
 },
 "evidence_ok": true
}
```
