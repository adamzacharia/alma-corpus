# An Updated 2017 Astrometric Solution for Betelgeuse

`2017AJ....154...11H` | The Astronomical Journal 2017 | first author: Harper, G. M. | arXiv: 1706.06020 | DOI: 10.3847/1538-3881/aa6ff9

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: stellar_physics, evolved_stars
- Question: Does the revised 2007 Hipparcos intermediate astrometric data, combined with VLA, e-MERLIN and ALMA radio positions, change Betelgeuse's parallax and distance?  
  > "we have been asked whether the revised (cite: 2007ASSL..350.....V) intermediate astrometric data would lead to a different VLA+*Hipparcos*  combined solution." (Introduction)
- Target **Betelgeuse (alpha Ori)**: coordinates 05 55 10.33 +07 24 25.6 (ICRS, from Table 1)  
  > "2015.854 | 05 55 10.33142 | 07 24 25.5646 | 2.0 | 330-345 GHz ALMA" (Table 1); z/distance parallax 4.51 +/- 0.80 mas (222 pc), derived here  
  > "2015.854 | 05 55 10.33142 | 07 24 25.5646 | 2.0 | 330-345 GHz ALMA" (Table 1); distance from this work's combined radio+Hipparcos solution  
  > "2015.854 | 05 55 10.33142 | 07 24 25.5646 | 2.0 | 330-345 GHz ALMA" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00206.S
- bands: Band 7  
  > "Both sets of observations were carried out in Band 7 with identical spectral setups" (2.1 ALMA)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: ~5.9 GHz centered at ~338 GHz  
  > "a single continuum data set centered at $\simeq$338 GHz with a $\sim$5.9 GHz bandwidth was used" (2.1 ALMA)
- arrays: _not stated_
- configurations: _not stated_
- baselines: max 16 km (long), 1.2 km (compact)  
  > "The maximum baseline in the long baseline observation was 16 km" (2.1 ALMA)
- angular resolution: ~15 mas (long), 185 mas (compact)  
  > "which yielded an angular resolution of $\sim$15 mas" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2015 Nov 9 (long); 2016 Aug 16 (compact)  
  > "on 2015 November 9 and again on 2016 August 16 in a more compact configuration" (2.1 ALMA)
- pi or archival as stated: PI P. Kervella  
  > "(Project code: 2015.1.00206.S , PI: P. Kervella)" (2.1 ALMA)
- Other facility **VLA**: radio positions from Harper et al. 2008  
  > "combined with the full radio positional data in Table [1](#tab:positions) and (cite: 2008AJ....135.1430H)." (4.2 Radio Positions and HIAD)
- Other facility **e-MERLIN**: 5.75 GHz positions (2012, 2015)  
  > "three e-MERLIN observations obtained at 5.75  GHz (5.2 cm)" (2 New Radio Positions)
- Other facility **Hipparcos**: revised intermediate astrometric data (HIAD)  
  > "The HIAD were retrieved from the DVD included in (cite: 2007ASSL..350.....V)" (4 Revised Intermediate Astrometric Solutions)
- External data: Hipparcos 2007 revised abscissae/HIAD  
  > "There are 66 scan level abscissa $(a)$ measurements" (4 Revised Intermediate Astrometric Solutions) [from van Leeuwen 2007 (cite: 2007ASSL..350.....V)]
- External data: VLA radio positions  
  > "combined with the full radio positional data in Table [1](#tab:positions) and (cite: 2008AJ....135.1430H)." (4.2 Radio Positions and HIAD) [from Harper et al. 2008 (cite: 2008AJ....135.1430H)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: e-MERLIN flux scale ~10%  
  > "The flux scale is accurate to $\sim$10%." (2.2 e-MERLIN)
- self calibration: _not stated_

### Imaging

- task: positions fitted in uv-plane with uvmultifit (uniform elliptical disk) on un-self-calibrated continuum  
  > "the source position was extracted from the un-self-calibrated continuum datasets using the Python-based task uvmultifit" (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line-emission channels excluded  
  > "the channels containing line emission were excluded from the analysis" (2.1 ALMA)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Full ALMA observation description deferred  
  > "will be described in more detail in a future publication (P. Kervella, et al. 2017, in preparation)" (2.1 ALMA) [from P. Kervella et al. 2017, in preparation]
- e-MERLIN 2012 observation details  
  > "(cite: 2013MNRAS.432L..61R) describes these observations in more detail" (2.2 e-MERLIN) [from (cite: 2013MNRAS.432L..61R)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration procedure for ALMA data
- Flux calibrator and ALMA flux scale
- Exact uvmultifit settings and fitted ellipse parameters
- Full 18 radio position list (VLA values in Harper et al. 2008)
- Details of the eight alternative ALMA fits used for 0.43 mas

## Analysis recipe

1. **Measure ALMA positions**: Fit uniform elliptical disk to calibrated continuum visibilities  
  > "fitting a uniform intensity elliptical disk to the calibrated visibilities" (2.1 ALMA)
   - software: uvmultifit
   - fitting: _not stated_
   - validation: Check source offsets scaled by separations give position uncertainty  
  > "$$Unc = \Delta{\rm CS}\times({\rm Star-PhaseCal})/({\rm ChkSource-PhaseCal})$$" (2.1 ALMA)
2. **Adopt radio cosmic noise**: Half of 5 mas axis extension taken as radio noise, added in quadrature  
  > "We adopt approximately half this value as the nominal radio noise, i.e. $\sigma_{radio}^{noise}=2.4$ mas." (2.3 Sources of Additional Radio Positional Noise)
   - fitting: _not stated_
   - validation: Eight alternative ALMA fits give centroid scatter of 0.43 mas  
  > "lead to shifts in the apparent ellipse centroid with a standard deviation of 0.43 mas" (2.3 Sources of Additional Radio Positional Noise)
3. **Combined radio+HIAD astrometric fit**: Minimize chi2 of HIAD abscissa residuals plus radio position offsets  
  > "We used Levenberg-Marquardt least-squares minimization (cite: 2009ASPC..411..251M) with the 65 1D HIAD scans and each of the 18 2D radio position." (4.2 Radio Positions and HIAD)
   - software: Levenberg-Marquardt (MPFIT)
   - assumption: JPL DE405 ephemerides for parallax  
  > "We compute the parallaxes using the JPL DE405 IRCF ephemerides" (3 Radio-Only Proper Motions and Parallax)
   - fitting: Least squares, 101 evaluations  
  > "for a total of 101 individual evaluations" (4.2 Radio Positions and HIAD)
   - validation: Sensitivity of parallax to radio noise explored  
  > "Figure [2](#fig:radionoise) shows the sensitivity of the new parallax to the adopted radio *cosmic noise*." (4.2 Radio Positions and HIAD)

## Software

- **uvmultifit** : fit position to ALMA visibilities  
  > "using the Python-based task uvmultifit" (2.1 ALMA)
- **MPFIT (Levenberg-Marquardt)** : astrometric least-squares fitting  
  > "We used Levenberg-Marquardt least-squares minimization (cite: 2009ASPC..411..251M)" (4.2 Radio Positions and HIAD)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radio-fixed-proper-motion + HIAD parallax | 5.27 | 0.78 | mas | 3 | we find a parallax of $\pi=5.27\pm 0.78$ mas |
| Combined radio+Hipparcos parallax | 4.51 | 0.80 | mas | 3 | Parallax $\pi$ (mas) / 6.55(0.83) / 4.51(0.80) |
| Combined distance | 222 | +48/-34 | pc | 3 | $4.51 \pm 0.80$ mas ($222^{+48}_{-34}$ pc) |
| Combined mu_delta | 9.60 | 0.12 | mas/yr | 3 | $\mu_\delta$ ( mas ${\rm yr}^{-1}$ ) / 11.30(0.65) / 9.60(0.12) |
| ALMA elliptical-fit centroid scatter | 0.43 | not stated | mas | 2 | standard deviation of 0.43 mas |

## Qualitative findings

- Radio proper motions differ from Hipparcos, giving smaller parallax and greater distance  
  > "leads to a smaller parallax (greater distance) than either *Hipparcos*  solution" (Conclusions)

## Claim tuples

- H: Revised HIAD with radio positions changes Betelgeuse's parallax | E: Combined fit of 2007 HIAD with VLA, e-MERLIN, ALMA positions with 2.4 mas radio noise | R: pi=4.51±0.80 mas, 222 pc | F: Consistent with Harper 2008 (0.7 sigma), 2.6 sigma from van Leeuwen | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Radio noise value is approximate; ALMA compact-configuration uncertainty may be underestimated  
  > "This in turn might lead to an underestimation of the uncertainty reported in Table [2](#tab:propermotion_alt)." (2.1 ALMA)
- Caveat (inferred, ours): Radio cosmic noise of 2.4 mas is heuristic and drives the parallax
- Caveat (inferred, ours): Photo-center motions are correlated, violating the random-noise assumption
- Caveat (inferred, ours): Only two ALMA epochs, one at modest quality

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA calibration/imaging details
- Missing: Full radio position table incl. VLA
- Data volume (inferred): ~100 GB for two ALMA Band 7 long and compact datasets
- Score (inferred): 3/5, Astrometric fit is clear, but ALMA processing and the radio-noise choice are thinly documented.
- Rediscovery candidate: no, ALMA role is minor and the processing recipe is incomplete.

## Links

- Method: Martí-Vidal et al. 2014 (cite: MV2014A&A...563A.136M) (uvmultifit)
- Companion: O'Gorman et al. 2017 (cite: OGorman_2017) (ALMA Betelgeuse high-resolution map)
- Companion: Harper et al. 2008 (cite: 2008AJ....135.1430H) (previous VLA+Hipparcos solution)

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
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
  "facts": 64,
  "stated": 32,
  "rate": 0.5
 },
 "evidence_ok": true
}
```
