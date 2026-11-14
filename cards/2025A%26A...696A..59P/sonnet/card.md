# GA-NIFS: High number of dual active galactic nuclei at z ∼ 3

`2025A&A...696A..59P` | Astronomy and Astrophysics 2025 | first author: Perna, Michele | arXiv: 2310.03067 | DOI: 10.1051/0004-6361/202453430

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars, high_z_galaxies
- Question: What fraction of AGNs at 2<z<6 in the GA-NIFS JWST/NIRSpec IFS sample have dual or multiple AGN companions, and how does it compare with cosmological simulations?  
  > "This study is aimed at providing a first observational estimate of the fraction of dual AGNs at $2 < z < 6$ by analysing a sample of 16 AGNs observed with the JWST Near-InfraRed Spectrograph (NIRSpec) in integral field mode" (abstract)
- Target **COS1638**: coordinates RA 150.735557, Dec +2.19953 (deg)  
  > "| COS1638-A                 | $3.5079$  | 150.735557 +2.19953   | –      | –     | –             | $10.9\pm 0.4$ | $46.7$             | 44.5             | 2,3,4            |   |" (Table 1); z/distance z = 3.5079  
  > "| COS1638-A                 | $3.5079$  | 150.735557 +2.19953   | –      | –     | –             | $10.9\pm 0.4$ | $46.7$             | 44.5             | 2,3,4            |   |" (Table 1); distance from NIRSpec spectra  
  > "| COS1638-A                 | $3.5079$  | 150.735557 +2.19953   | –      | –     | –             | $10.9\pm 0.4$ | $46.7$             | 44.5             | 2,3,4            |   |" (Table 1)

## Data provenance

- ALMA projects: 2016.1.00463.S
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
- pi or archival as stated: Archival ALMA data, PI: Y. Matsuda  
  > "Archival ALMA data (2016.1.00463.S, PI: Y. Matsuda) tracing far-IR emission at $\sim 1$ mm" (5.7 Stellar masses of AGN host galaxies)
- Other facility **JWST/NIRSpec IFS**: Main data: GA-NIFS IFS cubes of 16 AGNs  
  > "The targets presented in this work were observed as part of the NIRSpec IFS GTO survey GA-NIFS" (3.1 NIRSpec IFS data)
- Other facility **VLT/MUSE**: Archival cubes for GS551 and GS10578 (Lyα, UV lines)  
  > "Two of the 16 systems in the GA-NIFS AGN sub-sample have archival VLT/MUSE data" (3.2 MUSE data)
- Other facility **Chandra**: X-ray catalogues and COS1638 morphology  
  > "we used one of the single exposures of the COSMOS-Legacy survey to study the X-ray morphology of COS1638" (3.3 X-ray data)

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

### Not stated but needed to reproduce (our reading)

- ALMA band, array configuration, resolution and integration time
- ALMA calibration/imaging procedure and CASA version
- How the 11.4 mJy flux and 62% split between components were measured (aperture or fit)
- Observed frequency of the ALMA continuum

## Analysis recipe

1. **ALMA continuum flux split of COS1638**: Measured total integrated flux and fraction associated with COS1638-B from archival ALMA data  
  > "we measured a total integrated flux of 11.4 mJy, with 62% of which associated with COS1638-B" (9.1 COS1638 (dual AGN))
   - assumption: Dust mass fraction in AGN-B equals 62%; M_dust/M_* = 0.02±0.01  
  > "Assuming that 62% of the dust mass is due to the AGN-B host, and considering a conservative M$_{dust}$/M$_* = 0.02\pm 0.01$" (5.7 Stellar masses of AGN host galaxies)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CIGALE** v0.11.0: SED fitting incl. ALMA detections/upper limits  
  > "We modelled the SED with the Code Investigating GALaxy Emission (CIGALE v0.11.0" (5.7 Stellar masses of AGN host galaxies)
- **CAP-MPFIT** : Emission-line fitting  
  > "We fitted the most prominent gas emission lines by using the Levenberg-Marquardt least-squares fitting code CAP-MPFIT" (4.2 NIRSpec spectroscopic analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| COS1638 total ALMA ~1 mm integrated flux | 11.4 | not stated | mJy | 1 | we measured a total integrated flux of 11.4 mJy, with 62% of which associated with COS1638-B |
| Fraction of ALMA flux from COS1638-B | 62 | not stated | % | 1 | we measured a total integrated flux of 11.4 mJy, with 62% of which associated with COS1638-B |
| Dual/multiple AGN fraction | ~20-30 | not stated | % | 0 | The identification of these 3-5 multiple AGNs out of the 16 AGN systems in the GA-NIFS survey (i.e. $\sim$ 20–30%) |

## Qualitative findings

- ALMA ~1 mm emission shows COS1638-B is brighter than the primary AGN host, indicating dust at the secondary AGN  
  > "a significant amount of dust is located at the position of the secondary AGN" (9.1 COS1638 (dual AGN))

## Claim tuples

- H: Dual AGNs are more common at z~3 than expected | E: Search of 16 GA-NIFS AGN fields for companions with BPT/UV diagnostics, compared with Horizon-AGN | R: 3-5 multiple AGN systems out of 16 (~20-30%) versus ~10% predicted | F: Multiple AGNs moderately exceed predictions; sample too small to be conclusive | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample size prevents conclusions about simulations underestimating dual AGNs  
  > "precludes us from conclusively determining whether Horizon-AGN cosmological simulations underestimate the number of dual AGNs at high-$z$" (6.3 Dual AGN fraction)
- Caveat (inferred, ours): ALMA part is minor and qualitative; no processing details
- Caveat (inferred, ours): Sample is heterogeneously selected, so fraction is not a clean statistic

## Reproducibility

- Data public (paper): ALMA data described as archival  
  > "Archival ALMA data (2016.1.00463.S, PI: Y. Matsuda)" (5.7 Stellar masses of AGN host galaxies)
- Products in archive: _not stated_
- Missing: ALMA imaging and flux measurement details
- Data volume (inferred): ALMA part: a few GB; whole paper: tens of GB (JWST, MUSE)
- Score (inferred): 3/5, ALMA role is a single small measurement with no processing details; JWST analysis is better documented.
- Rediscovery candidate: no, ALMA recipe is incomplete and the main results rely on JWST.

## Links

- Method: Perna et al. 2023 (cite: Perna2023) (Modified JWST pipeline reduction)
- Companion: Circosta et al., in prep. (SED analysis and ALMA)
- Related: GA-NIFS
- Related: MUSE-WIDE
- Related: MUSE-UDF
- Related: VANDELS
- Related: COSMOS-Legacy

## Checks

```json
{
 "quotes": 21,
 "quotes_ok": 21,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 54,
  "stated": 15,
  "rate": 0.278
 },
 "evidence_ok": true
}
```
