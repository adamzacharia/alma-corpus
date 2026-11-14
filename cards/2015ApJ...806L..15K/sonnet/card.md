# Mass Estimates of a Giant Planet in a Protoplanetary Disk from the Gap Structures

`2015ApJ...806L..15K` | The Astrophysical Journal Letters 2015 | first author: Kanagawa, Kazuhiro D. | arXiv: 1505.04482 | DOI: 10.1088/2041-8205/806/1/L15

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: How can observed gap depths, together with disk temperature, constrain the mass of a giant planet embedded in a protoplanetary disk (applied to HL Tau and HD 169142)?  
  > "We discuss how observed gap features can be used to constrain the disk and/or planet parameters based on the analytic formula for the gap depth." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "We use the data of dust continuum emission in Band 6 and 7 in our analyses, and assume the distance of $140$ pc." (Application to Observations); distance from assumed  
  > "We use the data of dust continuum emission in Band 6 and 7 in our analyses, and assume the distance of $140$ pc." (Application to Observations)
- Target **HD 169142**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 6 and Band 7 dust continuum (233 and 344 GHz central frequencies)  
  > "where $\nu_6=233~\mathrm{GHz}$ is the central frequency at Band 6, $\nu_7=344~\mathrm{GHz}$ is that at Band 7" (Application to Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Long Baseline Campaign  
  > "HL Tau was observed during the 2014 Long Baseline Campaign of ALMA" (Application to Observations)
- pi or archival as stated: _not stated_
- Other facility **VLA**: 7 mm observations of HD 169142 (Osorio et al. 2014) used for gap depth  
  > "Recent observations by (cite: Osorio2014) of 7 mm emission shows that there may exist a gap at $\sim 50$ AU" (Application to Observations)
- External data: HD 169142 7 mm radial profile, aspect ratio ~0.1 and alpha=5e-4  
  > "If we adopt the disk aspect ratio of $\sim 0.1$ and $\alpha=5\times10^{-4}$, as indicated by (cite: Osorio2014)" (Application to Observations) [from (cite: Osorio2014)]
- External data: HL Tau ALMA continuum images (Band 6 and 7)  
  > "HL Tau was observed during the 2014 Long Baseline Campaign of ALMA (cite: ALMA_HLTau)" (Application to Observations) [from (cite: ALMA_HLTau)]
- Simulation/model as data: 2D FARGO hydrodynamic simulation of Jupiter-mass planet at 40 AU, alpha=1e-3, h_p=0.1, delta=0.25, used to make mock 230 GHz images  
  > "we have performed two–dimensional hydrodynamic calculations using FARGO (cite: Masset2000) to obtain the gap and spiral structures caused by a Jupiter mass planet at $R_p=40~\mathrm{AU}$" (4 Spiral Structures)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Publicly available FITS image from ALMA archive site used  
  > "We use the FITS image of the HL Tau that is publicly available from the ALMA archive site." (Application to Observations)
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

- Gap depth formula derivation  
  > "(see K15 for detail derivation)" (Gap model) [from (cite: Kanagawa2015)]

### Not stated but needed to reproduce (our reading)

- Which archive FITS files (names, resolution, beam) were used for Band 6 and 7
- Whether images were convolved to a common beam before taking the ratio
- How profile uncertainties were estimated
- Coordinates of HL Tau and exact gap depth measurement procedure
- Details of the chi2 spiral fit

## Analysis recipe

1. **Derive radial brightness temperature profiles**: Average Band 6 and 7 images azimuthally over 130°<PA<140° between 20 and 50 AU about the brightest pixel  
  > "between $20~\mathrm{AU}$ – $50~\mathrm{AU}$ averaged over the position angles of $130^{\circ}<\mathrm{PA}<140^{\circ}$" (Application to Observations)
   - assumption: distance 140 pc  
  > "assume the distance of $140$ pc" (Application to Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Solve for optical depth and temperature**: Solve T_br = T(1-exp(-tau)) in both bands with tau7=tau6(nu7/nu6)^beta, for beta=1 and 2  
  > "We can derive $\tau_{6}$ and $T$ by using Equations ([\[eq:tau6\]](#eq:tau6)) and ([\[eq:tau7\]](#eq:tau7)) if we assume $\beta$." (Application to Observations)
   - assumption: beta = 1 or 2  
  > "shows the radial profiles of $\tau_6$ in the cases of $\beta=1$ and $\beta=2$" (Application to Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate gap depth and aspect ratio, then planet mass**: Ratio of tau max at 25 AU to min at 30 AU gives depth; T=55 K gives h~0.07; apply M_p/M_* formula  
  > "we estimate the depth of the gap to be $\Sigma_p/\Sigma_0 \sim \tau_{\max}/\tau_{\min} \sim 1/3-1/7$" (Application to Observations)
   - assumption: c = 1 km/s (T/300 K)^1/2, stellar mass 1 Msun  
  > "assume that the sound speed is $c=1~\mathrm{km/s} (T/300~\mathrm{K})^{1/2}$ and that the central star mass is $1~M_{\odot}$" (Application to Observations)
   - fitting: _not stated_
   - validation: Checked for dust pile-up at gap outer edge in tau profile  
  > "does not show any enhance at the outer edge. Hence, we can judge that dust filtration is not so effective in this case." (Application to Observations)

## Software

- **FARGO** : 2D hydrodynamic simulation of gap and spiral  
  > "two–dimensional hydrodynamic calculations using FARGO (cite: Masset2000)" (4 Spiral Structures)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HL Tau gap depth at 30 AU | 1/3-1/7 | not stated | dimensionless | 3 | $\Sigma_p/\Sigma_0 \sim \tau_{\max}/\tau_{\min} \sim 1/3-1/7$ |
| HL Tau aspect ratio at 25 AU | ~0.07 | not stated | dimensionless | 3 | we derive $h \sim 0.07$ as an estimate of the disk aspect ratio |
| HL Tau planet-to-star mass ratio | 3–5e-4 (h_p/0.07)^5/2 (alpha/1e-3)^1/2 | not stated | dimensionless | 3 | {M_{p}}{M_{\ast}}}   = 3 \ \mbox{--} \ 5 \times 10^{-4} |
| HD 169142 planet mass lower limit | ~0.4 | not stated | M_J | 3 | we obtain the lower limit of the planet mass as $\sim 0.4~M_J$ |

## Qualitative findings

- Dust filtration appears ineffective at the HL Tau 30 AU gap since no pile-up is seen at the outer edge  
  > "At the gap of HL Tau, the dust filtration does not seem so effective becasue no significant dust pilling–up is seen at outer edge of the gap." (Summary and Caveats)

## Claim tuples

- H: A planet can explain the HL Tau 30 AU gap and its mass can be estimated from gap depth | E: Used Band 6/7 brightness temperature ratio to get depth and temperature, applied analytic formula | R: Depth 1/3-1/7, h~0.07, Mp/M* = 3-5e-4 scaled | F: A planet with mass of roughly 0.3 M_J or more could cause the gap | **supported**
- H: The HD 169142 gap implies a planet | E: Applied formula with depth 0.5, h~0.1, alpha=5e-4 | R: Mp >~ 0.4 MJ | F: Planet mass lower limit 0.4 MJ | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gaps only marginally resolved, so depths are upper limits  
  > "the gaps we have focused on are only marginally resolved. Therefore, the gap depth quoted in this paper should be regarded as upper limit." (Summary and Caveats)
- Caveat (inferred, ours): Planet mass depends strongly on assumed h and alpha, which are poorly constrained
- Caveat (inferred, ours): Gap depth from tau ratio sensitive to beta and unresolved beam
- Caveat (inferred, ours): Equating dust and gas depth is an assumption
- Caveat (inferred, ours): Uncertainty not propagated

## Reproducibility

- Data public (paper): HL Tau FITS image publicly available from ALMA archive  
  > "We use the FITS image of the HL Tau that is publicly available from the ALMA archive site." (Application to Observations)
- Products in archive: _not stated_
- Missing: Exact FITS files and beam handling
- Missing: Gap depth measurement details
- Missing: Spiral chi2 fit method
- Data volume (inferred): <1 GB (reduced FITS images)
- Score (inferred): 3/5, Public images and simple analytic formulas, but profile extraction details are sparse.
- Rediscovery candidate: yes, Public HL Tau images and a short analytic recipe with numeric results.

## Links

- Method: (cite: Kanagawa2015) (Derivation of the gap depth formula)
- Companion: (cite: ALMA_HLTau) (Source of HL Tau ALMA data)
- Related: ALMA 2014 Long Baseline Campaign

## Checks

```json
{
 "quotes": 31,
 "quotes_ok": 31,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 66,
  "stated": 22,
  "rate": 0.333
 },
 "evidence_ok": true
}
```
