# Robust Constraint on a Drifting Proton-to-Electron Mass Ratio at z=0.89 from Methanol Observation at Three Radio Telescopes

`2013PhRvL.111w1101B` | Physical Review Letters 2013 | first author: Bagdonaite, J. | arXiv: 1311.3438 | DOI: 10.1103/PhysRevLett.111.231101

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: cosmology, astrochemistry
- Question: Constrain a possible cosmological variation of the proton-to-electron mass ratio mu using methanol absorption lines in the PKS1830-211 lensing galaxy at z=0.89, and quantify systematic effects  
  > "A limit on a possible cosmological variation of the proton-to-electron mass ratio $\mu$ is derived from methanol (CH$_3$OH) absorption lines in the benchmark PKS1830$-$211 lensing galaxy at redshift $z = 0.89$" (abstract)
- Target **PKS1830-211 (SW image, lensing galaxy at z=0.89)**: coordinates _not stated_; z/distance z = 0.88582 (lookback time 7.5 billion years)  
  > "the benchmark PKS1830$-$211 lensing galaxy at redshift $z = 0.89$" (abstract); "which was centered at $z = 0.88582$." (main text); distance from standard Lambda cosmology, Planck Collaboration (2013)  
  > "the benchmark PKS1830$-$211 lensing galaxy at redshift $z = 0.89$" (abstract); "which was centered at $z = 0.88582$." (main text)

## Data provenance

- ALMA projects: 2011.0.00405.S
- bands: _not stated_
- frequencies and spectral setup: 3_0-4_1A+ CH3OH at 261 GHz observed (rest 492.278713 GHz)  
  > "An observation of the $3_0-4_1A^+$ CH$_3$OH transition at a frequency of 261 GHz was conducted in June 2012" (main text)
- continuum bandwidth: _not stated_
- arrays: ALMA, 20 dishes of 12 m  
  > "\[ALMA, 20 dishes, 12 m in diameter each; see Fig. [1](#Fig1)(c)\]" (main text)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.6 arcsec  
  > "The angular resolution of the ALMA observations ($\sim$0.6 arcsec) made it possible to obtain a spectrum toward the south-western image only." (main text)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: June 2012 (ALMA)  
  > "was conducted in June 2012 with the Atacama Large Millimeter/submillimeter Array" (main text)
- pi or archival as stated: _not stated_
- Line: CH3OH 3_0-4_1A+ (ALMA) (492.278713(50) GHz)
- Other facility **Effelsberg 100-m**: Low-frequency (<35 GHz) CH3OH lines, reobserved in 2012-2013  
  > "were reobserved with the 100-m single-dish Effelsberg radio telescope of the Max-Planck-Institute für Radioastronomie" (main text)
- Other facility **IRAM 30-m**: CH3OH lines in 80-165 GHz with EMIR, 22-27 August 2012  
  > "using the EMIR receiver in observations during 22$-$27 August 2012." (main text)
- Other facility **ATCA (literature)**: Two data points from published observations  
  > "Table [\[tbl-1\]](#tbl-1) includes two data points resulting from observations with the Australia Telescope Compact Array (ATCA), presented in literature" (main text)
- External data: Laboratory rest frequencies of methanol transitions  
  > "as well as laboratory frequencies (cite: Breckenridge1995; Heuvel1973; Muller2004; Sastry1985; Herbst1984) with their uncertainties" (main text) [from Breckenridge1995; Heuvel1973; Muller2004; Sastry1985; Herbst1984]
- External data: Sensitivity coefficients K_mu  
  > "and the calculated $K_{\mu}$ coefficients (cite: Jansen2011a)" (main text) [from (cite: Jansen2011a)]
- External data: ATCA line positions for 2_-1-1_0E and 3_-1-2_0E  
  > "We adopt line positions from the latter work." (main text) [from (cite: Muller2011); (cite: Ellingsen2012)]
- External data: Covering factor f_c = 0.4 for SW sightline  
  > "we adopt $f_{\rm c} = 0.4$ (cite: Henkel2009) for the SW sightline of PKS1830$-$211." (main text) [from (cite: Henkel2009)]

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

- Low-frequency Effelsberg data from Dec 2011-Apr 2012 and the preliminary four-line analysis  
  > "previously observed in the time slot Dec. 2011–Apr. 2012 (cite: Bagdonaite2013)" (main text) [from (cite: Bagdonaite2013)]
- H2 density and kinetic temperature for RADEX  
  > "values discussed in (cite: Henkel2009),(cite: Menten2008), and (cite: Muller2013)" (main text) [from (cite: Henkel2009); (cite: Menten2008); (cite: Muller2013)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction (CASA version, calibration, flux scale, imaging parameters)
- How the ALMA spectrum toward the SW image was extracted
- Spectral resolution and velocity channelization of ALMA data
- Exact regression implementation and error weighting
- Effelsberg and IRAM reduction details

## Analysis recipe

1. **Fit line profiles**: Fit absorption profiles to single Gaussians on an LSR velocity scale centred at z = 0.88582; IRAM blends fitted jointly with RADEX-based relative intensities  
  > "The absorption profiles of individual transitions were fitted to single Gaussians, and the line positions and widths were determined on a Local Standard of Rest (LSR) velocity scale" (main text)
   - software: RADEX
   - fitting: _not stated_
   - validation: Uncertainty of blended line position estimated by varying relative strengths by 10-20%  
  > "The uncertainty of the combined line position is estimated by varying the relative strengths of the three lines by 10-20$\%$ with regard to the RADEX prediction." (main text)
2. **Fit Delta mu/mu from velocity vs K_mu**: Fit 17 line positions with V/c = -K_mu Δμ/μ  
  > "The velocities between different transitions are interrelated via $V/c= -K_{\mu}\Delta\mu/\mu$" (main text)
   - assumption: Laboratory frequency uncertainty negligible; calibration of frequency scale ≤20 m/s  
  > "is small ($<$14$\%$) compared to the uncertainty obtained from the astrophysical spectra and is treated as negligible." (main text)
   - fitting: _not stated_
   - validation: Reduced chi2 = 10.2 (15 dof) shows an unaccounted systematic  
  > "with a reduced $\chi^2_{\nu} = 10.2$, where the number of degrees of freedom, $\nu$, is 15." (main text)
3. **Multi-dimensional linear regression for systematics**: Add E/A symmetry, excitation energy and observation epoch (quadratic) as independent variables; core-shift adopted as 1e-7 systematic  
  > "A two-dimensional LR analysis with the observation epoch and $K_{\mu}$ as independent variables" (main text)
   - fitting: _not stated_
   - validation: Compare chi2_nu across regressions  
  > "a two-dimensional linear regression (LR) analysis with $K_{\mu}$ and $E$/$A$ symmetry as independent variables results in an increase of $\chi_{\nu}^2$, if compared to a fit with $K_{\mu}$ alone" (Chemical segregation)

## Software

- **RADEX** : Relative component intensities and methanol column density  
  > "The RADEX radiative transfer model (cite: vandertak2007) was used to estimate the relative intensities." (main text)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Δμ/μ, K_mu-only fit (17 points) | 1.5e-7 | 1.5e-7 | dimensionless | 2 | $\Delta\mu/\mu = (1.5 \pm 1.5) \times 10^{-7}$ |
| Δμ/μ robust, multi-dimensional | -1.0e-7 | 0.8e-7 stat, 1.0e-7 sys | dimensionless | 3 | $\Delta\mu/\mu = (-1.0 \pm 0.8_{\rm stat} \pm 1.0_{\rm sys}) \times 10^{-7}$ |
| Total methanol column density | 1.6e14 | not stated | cm^-2 | 1 | this yields a total column density of $~1.6 \times 10^{14}$ cm$^{-2}$ |
| ALMA 3_0-4_1A+ V_LSR and width | 11.7 km/s; 15.1 km/s | 0.3; 0.7 | km/s | 1 | $11.7\pm 0.3$ & $15.1 \pm 0.7$ & 0.04 & ALMA Jun. 2012 |
| Rate of change of mu | <2e-17 | not stated | yr^-1 | 3 | $\dot{\mu}/\mu < 2 \times 10^{-17}$ yr$^{-1}$ |

## Qualitative findings

- E/A chemical segregation previously suggested is discarded  
  > "The suggested systematic on $E/A$ chemical segregation (cite: Bagdonaite2013) has now been discarded." (main text)

## Claim tuples

- H: Does mu vary over 7.5 Gyr? | E: Fit 17 methanol line positions from Effelsberg, IRAM, ALMA vs K_mu | R: Δμ/μ=(1.5±1.5)e-7 with chi2_nu=10.2 | F: No variation detected, but the scatter implies unmodelled systematics | **supported**
- H: Systematics (segregation, temperature, time variability) explain the excess scatter | E: Multi-dimensional linear regression | R: Δμ/μ=(-1.0±0.8)e-7 with chi2_nu=2.4 | F: Robust constraint including systematics | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: E/A segregation rejected: 2D regression increased chi2_nu  
  > "results in an increase of $\chi_{\nu}^2$, if compared to a fit with $K_{\mu}$ alone, thereby ruling out a possible $E$/$A$ segregation." (main text)
- How they decided it was enough: _not stated_
- Limitation (authors): Core-shift effect cannot be estimated from current data; K_mu and 1/nu correlated  
  > "As it is not possible to estimate the size of this effect based on the current data set, we adopt the latter value as a systematic uncertainty" (main text)
- Caveat (inferred, ours): Only one ALMA line; ALMA role minor
- Caveat (inferred, ours): Linear regression with several free variables on 17 points risks overfitting
- Caveat (inferred, ours): Quadratic time dependence is ad hoc

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Effelsberg and IRAM data are not identified as public
- Missing: ALMA reduction details absent
- Missing: Regression code and weighting unspecified
- Data volume (inferred): small (<10 GB for ALMA)
- Score (inferred): 3/5, Final table of line positions is given so the regression is reproducible, but raw data reduction is not described.
- Rediscovery candidate: no, Most data are single-dish non-ALMA and reduction is unstated.

## Links

- Method: (cite: Jansen2011a) (K_mu coefficients of methanol)
- Method: (cite: vandertak2007) (RADEX)
- Companion: (cite: Bagdonaite2013) (Preliminary four-line methanol constraint)

## Checks

```json
{
 "quotes": 39,
 "quotes_ok": 39,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 27,
  "rate": 0.409
 },
 "evidence_ok": true
}
```
