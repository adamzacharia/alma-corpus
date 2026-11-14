# Physical conditions in the gas phases of the giant H II region LMC-N 11. II. Origin of [C II] and fraction of CO-dark gas

`2019A&A...632A.106L` | Astronomy and Astrophysics 2019 | first author: Lebouteiller, V. | arXiv: 1911.03280 | DOI: 10.1051/0004-6361/201936303

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: What is the origin of the [C II] 158 um line in LMC-N 11, and what fraction of the molecular gas is CO-dark H2?  
  > "We investigate the origin of [C ii] in order to measure the total molecular gas content, the fraction of CO-dark H$_2$ gas, and how these parameters are impacted by environmental effects such as stellar feedback." (abstract)
- Target **LMC-N 11 (12 SOFIA/GREAT pointings; ALMA mosaic of N 11B)**: coordinates pointing #1: RA 4:57:16.2, Dec -66:23:20.2 (J2000); other pointings tabulated  
  > "| #1 | 4:57:16.2 | -66:23:20.2 | 2.5 | 139 | N 11 A $-$ compact H ii region $-$ [CII]+CO peak |" (Table 1); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00532.S, 2013.1.00556.S
- bands: Band 3 (CO(1-0))  
  > "We also obtained ALMA band-3 observations of N 11B (programs 2012.1.00532.S and 2013.1.00556.S; PI Lebouteiller)." (2.4 CO (1-0))
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12-m, 7-m and Total Power  
  > "The $7$-m, $12$-m, and Total Power observations were combined for the final data cube." (2.4 CO (1-0))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 2.2 arcsec  
  > "The spatial resolution is $2.2$$''$" (2.4 CO (1-0))
- max recoverable scale: 12 arcsec (12-m), 47 arcsec (7-m)  
  > "with a maximum recoverable scale of $12$$''$ and $47$$''$ for the $12$- and $7$-m arrays respectively" (2.4 CO (1-0))
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=1-0 (not stated)
- Other facility **SOFIA/GREAT**: [C II] 158 um and [N II] 205 um spectra at 12 pointings  
  > "Twelve pointings were observed within LMC-N 11" (2.1 SOFIA/GREAT)
- Other facility **Herschel/PACS**: [C II], [O I], [N II] maps  
  > "Herschel/PACS observations were taken as part of the SHINING key program" (2.2 Herschel/PACS)
- Other facility **ATCA+Parkes**: HI 21 cm cube  
  > "The H i $21$ cm data cube is taken from the ATCA+Parkes observations by (cite: Kim2003a)" (2.3 H i 21 cm)
- Other facility **MOPRA/MAGMA**: CO(1-0) survey  
  > "The CO(1-0) observations are taken from the MAGMA survey described in (cite: Wong2011a)." (2.4 CO (1-0))
- Other facility **VLT/GIRAFFE**: archival Halpha and [Ne III] spectra  
  > "We use archival ESO/VLT/U2 GIRAFFE observations" (2.5 VLT/GIRAFFE)
- External data: HI 21 cm cube  
  > "The H i $21$ cm data cube is taken from the ATCA+Parkes observations by (cite: Kim2003a)" (2.3 H i 21 cm) [from (cite: Kim2003a)]
- External data: MAGMA CO(1-0) data  
  > "The CO(1-0) observations are taken from the MAGMA survey described in (cite: Wong2011a)." (2.4 CO (1-0)) [from (cite: Wong2011a)]
- External data: HI opacity correction  
  > "We account for optically thick H i by using the results of (cite: Braun2012a) for the LMC." (2.3 H i 21 cm) [from (cite: Braun2012a)]

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
- array combination: 7-m, 12-m and Total Power combined into the final cube  
  > "The $7$-m, $12$-m, and Total Power observations were combined for the final data cube." (2.4 CO (1-0))
- smoothing: ALMA spectra computed at 45 arcsec and 14.4 arcsec resolution  
  > "We also show the ALMA spectra calculated for a $14.4\ensuremath{''}$ resolution (i.e., similar to GREAT)." (2.4 CO (1-0))
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- MAGMA CO updated reduction  
  > "Updated reduction is explained in (cite: Wong2017a)." (2.4 CO (1-0)) [from (cite: Wong2017a)]
- IRAC PAH estimation method  
  > "We refer to (cite: Lebouteiller2012b) for the method." (3.2.3 Photoelectric heating efficiency proxy) [from (cite: Lebouteiller2012b)]
- C+ level population with collisions  
  > "see details in (cite: Lebouteiller2013a)" (4.3.2 Modeling strategy) [from (cite: Lebouteiller2013a)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration and imaging details (CASA version, weighting, masks)
- MCMC settings: number of iterations, burn-in, tuning, and likelihood noise model
- Exact atomic and molecular column-density grids and the C+ collisional rates used
- Mapping of ALMA spectra to GREAT pointings (aperture/center)

## Analysis recipe

1. **Compare integrated profiles and test for ionized-gas [C II]**: Gaussian fits to line profiles; line-width, [N II]/[C II] and (CII+OI)/PAH diagnostics  
  > "We can then compare the observed [N ii]/[C ii] ratio to the theoretical value in the ionized gas" (3.2.2)
   - software: GILDAS/CLASS
   - assumption: ionized gas at 10000 K  
  > "For a temperature of $10\,000$ K" (3.1 Comparison of the spectral profiles)
   - fitting: _not stated_
   - validation: several independent methods agree  
  > "Overall, the results obtained with ([C ii]+[O i])/PAH, together with those obtained in Sections [3.2.1](#sec:linewidth) and [3.2.2](#sec:ciiorigin_nii), suggest that most of the [C ii] arises in the neutral gas." (Section 3.2.3 Photoelectric heating efficiency proxy)
2. **Bayesian decomposition of CO, [C II], HI profiles**: Simultaneous fit of N components with shared velocity and width, independent intensities, via MCMC  
  > "We use a Bayesian approach with the Markov Chain Monte Carlo (MCMC) `PyMC3` code (cite: Salvatier2016a) along with the Metropolis-Hastings sampling algorithm." (4.1 Profile decomposition)
   - software: PyMC3
   - parameter: components 10, 15; min width 1, 2 km/s; min separation 0, 1, 2 km/s  
  > "| Minimum line width ($\sigma_{\rm min}$) | fixed | $1, 2$ km s$^{-1}$ |" (Table 4)
   - assumption: all tracers peak at same velocity per cloud  
  > "all tracers (CO, [C ii], H i) are assumed to peak at the same velocity for any given cloud." (4.1 Profile decomposition)
   - fitting: uniform priors on intensity, half-normal on width, half-uniform on separation  
  > "| Line width | free, half-normal | $>\sigma_{\rm min}$ |" (Table 4)
   - validation: different input parameters tested; results stable  
  > "We also performed decompositions allowing potentially different line widths for each tracer for any given velocity component, but the main results shown in the following remain unchanged." (Section 4.1 Profile decomposition)
3. **Derive CO-dark H2 with collisional [C II] model**: C+ level populations with H0, H2, e- collisions; atomic [C II] subtracted, remainder attributed to H2  
  > "The \[C ii\] intensity from the molecular gas is inferred from the difference of the estimated \[C ii\] emission in the atomic phase with the observed \[C ii\]." (4.3.2 Modeling strategy)
   - parameter: cloud size 1-10 pc; atomic T=100 K; molecular T=50 K; n_e/n_H=1e-4  
  > "The ionization fraction is fixed to a value of $n_e/n_{\rm H}=10^{-4}$" (4.3.2 Modeling strategy)
   - assumption: X'_CO = 2e20 cm-2 (K km/s)-1 for CO-bright H2; thermal pressure equilibrium by default  
  > "$X'_{\rm CO}=2\times10^{20}$ cm$^{-2}$ (K  km s$^{-1}$)$^{-1}$" (2.4 CO (1-0))
   - fitting: _not stated_
   - validation: compared with literature f_dark estimates  
  > "The $f_{\rm dark}$ values we find are in good agreement with the estimates of (cite: Galametz2016a)" (4.4.2)

## Software

- **GILDAS/CLASS** : GREAT spectra generation  
  > "Spectra were generated from the level 3 GREAT product using the [GILDAS/CLASS]" (2.1 SOFIA/GREAT)
- **PyMC3** : MCMC profile decomposition  
  > "Markov Chain Monte Carlo (MCMC) `PyMC3` code (cite: Salvatier2016a)" (4.1 Profile decomposition)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| fraction of [C II] attributable to CO-dark H2 | >95 | not stated | % | 3 | Globally, we find that $>95$% of the [C ii] emission across all pointings can be attributed to CO-dark H$_2$ gas |
| CO-dark fraction f_dark | ≳60 | not stated | % | 3 | most of the molecular gas is CO-dark overall, with $f_{\rm dark}\gtrsim60\%$ |
| effective X_CO | 10^21-22 | not stated | (K km/s)^-1 cm^-2 | 3 | lies in the range $10^{21-22}$ (K  km s$^{-1}$)$^{-1}$ for most of the bright velocity components |
| CO-dark H2 thermal pressure | 10^3.5-5 | not stated | K cm-3 | 3 | corresponding to a pressure of $10^{3.5-5}$ K cm$^{-3}$ |

## Qualitative findings

- [C II] profile resembles CO but is wider; width lies between CO and HI  
  > "the integrated \[C ii\] line width lies between that of CO and that of H i" (abstract)

## Claim tuples

- H: [C II] originates in neutral gas | E: line width, [N II]/[C II], [N II] profile, (CII+OI)/PAH | R: no ionized component unambiguously identified | F: [C II] mostly from neutral gas | **supported**
- H: [C II] traces CO-dark H2 | E: Bayesian decomposition and collisional model | R: >95% of [C II] from CO-dark H2 | F: most molecular gas is CO-dark | **supported**
- H: f_dark depends on CO column and environment | E: f_dark vs N(H2|CO) per pointing | R: f_dark decreases with CO column; slope varies with radiation | F: stellar feedback may play a role | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): limited HI spatial resolution is the main caveat  
  > "The main caveat concerns the derived column density and number density in the atomic medium, with limited spatial resolution" (5 Conclusions)
- Caveat (inferred, ours): Components from different tracers assumed to be the same cloud
- Caveat (inferred, ours): Single fixed temperature and cloud size drive f_dark
- Caveat (inferred, ours): Decomposition non-unique

## Reproducibility

- Data public (paper): ALMA projects cited in acknowledgements; HI and MAGMA from published surveys  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00532.S and ADS/JAO.ALMA#2013.1.00556.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: MCMC convergence settings
- Missing: ALMA reduction details
- Missing: model code for C+ level populations
- Data volume (inferred): tens of GB for the ALMA mosaic; the other data are small
- Score (inferred): 3/5, ALMA is minor; the analysis is described but with missing settings.
- Rediscovery candidate: no, Main results depend on SOFIA data and an incompletely specified model.

## Links

- Method: (cite: Lebouteiller2012b) (first N 11B paper; PAH method)
- Method: (cite: Lebouteiller2013a) (C+ level population model)
- Companion: (cite: Lebouteiller2012b) (Paper I on N 11B)
- Related: MAGMA
- Related: Herschel SHINING
- Related: Herschel Dwarf Galaxy Survey

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 36,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
