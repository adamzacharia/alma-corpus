# A multifrequency study of sub-parsec jets with the Event Horizon Telescope

`2025A&A...695A.233R` | Astronomy and Astrophysics 2025 | first author: Röder, Jan | arXiv: 2501.05518 | DOI: 10.1051/0004-6361/202452600

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: How do VLBI core size, flux density and brightness temperature of 16 AGN depend on frequency from 2 to 230 GHz, and does this agree with the Blandford-Königl jet model?  
  > "We studied their dependence on the observing frequency in order to compare it with the Blandford-Königl (BK) jet model." (abstract)
- Target **Sixteen AGN in the EHT 2017 data set (e.g. 3C 279, M 87, OJ 287, 1749+096, CTA 102)**: coordinates J2000 names given in Table 1 (e.g. J1751+0939)  
  > "| 1749+096 | 1749+096 | J1751+0939 | 0.322 | B | 612 | 10 | J, L, S, X, Z | 9342 |" (Table 1); z/distance redshifts per source, e.g. 0.322 for 1749+096  
  > "| 1749+096 | 1749+096 | J1751+0939 | 0.322 | B | 612 | 10 | J, L, S, X, Z | 9342 |" (Table 1); distance from SIMBAD  
  > "| 1749+096 | 1749+096 | J1751+0939 | 0.322 | B | 612 | 10 | J, L, S, X, Z | 9342 |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00413.V, 2013.1.01022.S
- bands: _not stated_
- frequencies and spectral setup: two 2 GHz bands centered at 227.1 GHz (LO) and 229.1 GHz (HI)  
  > "Two frequency bands, each 2 GHz wide, centered at 227.1 GHz (LO band) and 229.1 GHz (HI band) were recorded." (2.1 EHT observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: April 5-11, 2017  
  > "Eight facilities participated in the EHT observing campaign on April 5-11, 2017" (2.1 EHT observations and data reduction)
- pi or archival as stated: _not stated_
- Other facility **EHT array (APEX, LMT, IRAM 30m, SMT, JCMT, SMA, SPT)**: 230 GHz VLBI visibilities  
  > "the Large Millimeter Telescope Alfonso Serrano (LMT, L) in Mexico; the IRAM 30 m telescope (PV, P) in Spain" (2.1 EHT observations and data reduction)
- Other facility **RadioAstron, VLBA, VSOP, GMVA**: 2-86 GHz core measurements  
  > "The EHT+ data set below 230 GHz spans a range of frequencies from 2 to 86 GHz, taken from a variety of surveys and monitoring efforts." (3 Measurements in the EHT+ data set)
- External data: VLBA 15 GHz core measurements  
  > "Further VLBA data include 8 GHz (cite: Pushkarev2012), 15 GHz (cite: Homan2021), and 43 GHz (cite: Weaver2022)." (3 Measurements in the EHT+ data set) [from Homan2021; Pushkarev2012; Weaver2022]
- External data: 86 GHz GMVA survey core measurements  
  > "At 86 GHz, we used results obtained in a single-epoch GMVA AGN survey (cite: Lee2008)." (3 Measurements in the EHT+ data set) [from Lee2008]
- External data: Doppler factors from 15 GHz variability  
  > "we used values obtained from variability measurements at 15 GHz ((cite: Hovatta2009; Hovatta2009E; Liodakis2017), compiled in (cite: Pushkarev2017))" (Doppler factor correction and power law fitting) [from Pushkarev2017]

## Processing

### Calibration

- pipeline or manual: EHT-HOPS and rPICARD pipelines  
  > "the data were reduced using the `EHT-HOPS` (cite: Blackburn2019) and `rPICARD` (cite: Janssen2019) pipelines to independently validate the results" (2.1 EHT observations and data reduction)
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

- EHT calibration procedures  
  > "The EHT calibration procedures are described in detail in (cite: SgraP2), with minor updates with respect to (cite: M87p3)." (2.1 EHT observations and data reduction) [from SgraP2; M87p3]
- BK model parameters (gamma=10, N1)  
  > "we assume a characteristic bulk Lorentz factor $\gamma_{\rm j}=10$ for the entire sample and $N_1=5\times10^3$ cm$^{-3}$" (4.1) [from Lee2016_I]

### Not stated but needed to reproduce (our reading)

- Exact lower-frequency data tables per source
- Starting values and optimiser settings for the SciPy model fits
- Number of Gaussian components and parameter bounds per source
- Individual source power-law fit ranges

## Analysis recipe

1. **Fit geometric models to seven AGN**: Circular Gaussian components with linear polarization fit to visibilities, closure phases, fractional polarization  
  > "we performed geometric model fitting with linearly polarized circular Gaussian components using `eht-imaging`" (2.2 EHT data sets and model fitting)
   - software: eht-imaging, SciPy
   - parameter: acceptable reduced chi-square < 2  
  > "generally characterized by the reduced $\chi$-square $\chi_n^2<2$" (2.2 EHT data sets and model fitting)
   - fitting: heuristic optimisation in SciPy  
  > "exploiting heuristic optimisation tools implemented in `SciPy` (cite: 2020SciPy) to search for the best-fit solution" (2.2 EHT data sets and model fitting)
   - validation: _not stated_
2. **Compute brightness temperature**: Gaussian formula from flux density, frequency, size, redshift  
  > "For a circular Gaussian source model the peak brightness temperature in Kelvins can be calculated as" (3.3 Brightness temperature)
   - fitting: _not stated_
   - validation: visibility-only Tb,min and Tb,lim estimates  
  > "The latter indicate broad consistency with the brightness temperatures obtained based on Gaussian component modeling." (3.3 Brightness temperature)
3. **Fit per-source power laws and aggregate**: Fit slope per source at 15-230 GHz with nuisance scaling b; mean of 16 slopes, error sigma/sqrt(N)  
  > "We extracted their mean value $m$ and standard deviation $\sigma$, and used $m \pm \sigma/\sqrt{N}$ as our estimate" (3.1)
   - fitting: _not stated_
   - validation: compared with single power-law fits and Doppler-corrected fits  
  > "demonstrating robustness of the estimated slopes" (Appendix 8)
4. **Estimate core distance and magnetic field**: BK model distance from synchrotron luminosity; B from Tb  
  > "The magnetic field strength of a synchrotron self-absorbed core can be roughly estimated as" (4.2 Magnetic field strength)
   - assumption: gamma_j=10, phi=0.01 rad, viewing angle 0.1 rad, equipartition, m=1, n=2, alpha=-0.5  
  > "we set ${\phi=0.01\,{\rm rad}\approx0.6^\degree}$ and $\phi_{\rm o}=\phi \csc\iota$ with the viewing angle $\iota=0.1$ rad" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **eht-imaging** : geometric model fitting  
  > "using `eht-imaging` (cite: Chael2016; ehtim2022; Roelofs2023)" (2.2)
- **SciPy** : optimisation  
  > "heuristic optimisation tools implemented in `SciPy`" (2.2)
- **EHT-HOPS** : VLBI data reduction  
  > "`EHT-HOPS` (cite: Blackburn2019)" (2.1)
- **rPICARD** : VLBI data reduction  
  > "`rPICARD` (cite: Janssen2019)" (2.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tb slope vs frequency (15-230 GHz) | -0.95 | 0.13 | dimensionless | 3 | / brightness temperature $T_{\rm b}$ / $-0.96\pm0.16$ / $-0.46\pm0.10$ / $-0.93\pm0.13$ / $-0.95\pm0.13$ / |
| core size slope | -0.64 | 0.05 | dimensionless | 3 | / core size $\theta$ / $-0.80\pm0.07$ / $-0.72\pm0.04$ / $-0.77\pm0.06$ / $-0.64\pm0.05$ / |
| flux density slope | -0.43 | 0.13 | dimensionless | 3 | / flux density $S_{\nu}$ / $-0.43\pm0.13$ / $-0.01\pm0.09$ / $-0.48\pm0.11$ / $-0.43\pm0.13$ / |
| VLBI vs ALMA flux deficit | 25% | not stated | percent | 0 | We identify a systematic flux density deficit of 25% between short intra-site VLBI baselines and the ALMA-only connected interferometric array measurements |

## Qualitative findings

- Brightness temperature increases with distance from the central engine; data are inconsistent with a standard conical BK jet  
  > "properties of AGN jet sources constrained by the VLBI observations at 15-230 GHz are incompatible with the standard BK model" (7 Summary and conclusions)

## Claim tuples

- H: Do 230 GHz-to-2 GHz core properties agree with the BK model? | E: Power-law fits of core size, flux and Tb vs frequency for 16 AGN | R: theta ~ nu^-0.6, Tb ~ nu^-1.0 | F: BK model with constant Lorentz factor and energy partition is incompatible | **supported**
- H: What explains the Tb trend? | E: Doppler factor and energy partition scaling | R: delta ~ r^0.5 for constant eta | F: Jet acceleration and/or magnetic energy conversion required | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Parabolic-to-conical transition and steeper B(r) profile considered but not fully reconciling  
  > "However, this predominantly shows the inconsistency of the canonical BK model with the data." (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse uv-coverage causes large systematic uncertainties on core size and flux  
  > "Both core size and core flux density parameters are generally subject to significant systematic uncertainties, related to the sparse $(u,v)$–coverage." (3.2)
- Caveat (inferred, ours): Single-epoch snapshots of variable sources at 86 and 230 GHz
- Caveat (inferred, ours): Sample is heterogeneous and surveys combine different resolutions
- Caveat (inferred, ours): Fixed BK parameters assumed for all sources

## Reproducibility

- Data public (paper): Compiled table available at CDS  
  > "A table compiling measured VLBI core flux densities, FWHM sizes and brightness temperatures, as well as the derived distances to the black hole and magnetic field strengths is available in electronic form at the CDS" (Data availability)
- Products in archive: _not stated_
- Missing: EHT 2017 VLBI visibilities processing
- Missing: Model-fit start settings
- Missing: Compiled lower-frequency tables
- Data volume (inferred): Large raw EHT data; compiled products small
- Score (inferred): 3/5, Final fit recipe is clear and tables are given, but EHT VLBI data and fit settings are not fully specified, and ALMA is a minor element.
- Rediscovery candidate: no, Relies on EHT VLBI data and literature compilations, not ALMA imaging.

## Links

- Method: Blackburn2019 (EHT-HOPS calibration)
- Method: Janssen2019 (rPICARD pipeline)
- Method: Lee2016_I (BK distance framework)
- Companion: Janssen2021 (Cen A dedicated analysis)
- Companion: Paraschos2024 (3C 84 dedicated analysis)
- Related: MOJAVE
- Related: VLBA-BU-BLAZAR/BEAM-ME
- Related: RadioAstron
- Related: GMVA survey

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.01170.S",
  "2016.1.00415.S",
  "2016.1.01114.V",
  "2016.1.01116.V",
  "2016.1.01154.V",
  "2016.1.01176.V",
  "2016.1.01198.V",
  "2016.1.01216.V",
  "2016.1.01290.V",
  "2016.1.01404.V",
  "2017.1.00608.S",
  "2017.1.00841.V"
 ],
 "codes_printed_but_missing": [
  "2015.1.01170.S",
  "2016.1.00415.S",
  "2016.1.01114.V",
  "2016.1.01116.V",
  "2016.1.01154.V",
  "2016.1.01176.V",
  "2016.1.01198.V",
  "2016.1.01216.V",
  "2016.1.01290.V",
  "2016.1.01404.V",
  "2017.1.00608.S",
  "2017.1.00841.V"
 ],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 31,
  "rate": 0.437
 },
 "evidence_ok": true
}
```
