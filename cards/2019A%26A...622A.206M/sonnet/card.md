# A 10-M<SUB>☉</SUB> YSO with a Keplerian disk and a nonthermal radio jet

`2019A&A...622A.206M` | Astronomy and Astrophysics 2019 | first author: Moscadelli, L. | arXiv: 1901.02713 | DOI: 10.1051/0004-6361/201834366

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical conditions and gas kinematics around the high-mass YSO in G16.59-0.05, and is there a Keplerian disk related to the nonthermal radio jet?  
  > "Our goals are to establish the physical conditions of the environment hosting the high-mass YSO and to study the kinematics of the surrounding gas in detail." (abstract)
- Target **G16.59-0.05 (IRAS 18182-1433)**: coordinates _not stated_; z/distance 3.6±0.3 kpc  
  > "at a distance of  3.6$\pm$0.3 kpc, as determined via maser trigonometric parallax observations (cite: Sat14)" (1 Introduction); distance from maser trigonometric parallax (Sato et al. 2014)  
  > "at a distance of  3.6$\pm$0.3 kpc, as determined via maser trigonometric parallax observations (cite: Sat14)" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00408.S
- bands: 1.2 mm (about 242 GHz continuum)  
  > "one broad 2-GHz spectral unit to obtain a sensitive continuum measurement at  $\approx$242 GHz" (2 ALMA observations)
- frequencies and spectral setup: six SPWs: one 2-GHz continuum SPW and five narrow line SPWs (SiO, CH3CN, CH3OH, C34S, SO2)  
  > "The correlator frequency setup consisted of six spectral windows (SPWs)" (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: 47 12-m antennae, extended configuration  
  > "Fourty-seven 12-m antennae were used in an extended configuration with baselines ranging from 15 to 3300 m." (2 ALMA observations)
- configurations: _not stated_
- baselines: 15 to 3300 m  
  > "Fourty-seven 12-m antennae were used in an extended configuration with baselines ranging from 15 to 3300 m." (2 ALMA observations)
- angular resolution: 0.13''-0.17''  
  > "The clean beam FWHM of the resulting images varies in the range  0.13$''$–0.17$''$." (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.08 mJy/beam; 1-3 mJy/beam per channel  
  > "The 1$\sigma$ rms noise in a single spectral channel varies in the interval  1–3 mJy beam$^{-1}$, depending on the considered SPW/channel." (2 ALMA observations)
- time on source: about 1.8 h  
  > "The observing time on the target source was about 1.8 h." (2 ALMA observations)
- observing dates: Cycle 3, September 2016  
  > "ALMA observed G16.59$-$0.05 during Cycle 3 in September 2016." (2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CH3CN J=14-13 (257.1-257.5 GHz)
- Line: CH3OH 5_0,5-4_0,4 etc. (241700.219 MHz (and others))
- Line: C34S J=5-4 (241016.089 MHz)
- Line: CH3OCH3 5_3,3-4_2,2 etc. (240978.322 MHz (and others))
- Other facility **JVLA**: 6, 13 and 22 GHz continuum maps used for the jet and YSO position  
  > "We note that the JVLA 22-GHz continuum, pinpointing the YSO, falls exactly between the SW blue-shifted and the NE red-shifted line emission" (3.2 The massive YSO Bm)
- Other facility **EVN/VLBI**: 6.7-GHz methanol maser positions and proper motions  
  > "with that of the 6.7-GHz CH$_3$OH masers observed with VLBI by (cite: San10a)" (4 The Keplerian disk)
- External data: JVLA 6, 13 and 22 GHz continuum images of the jet  
  > "the eastern lobe of the radio jet is well detected with the JVLA at 6 GHz" (3.3 The surroundings of Bm) [from (cite: Mos13b)]
- External data: 6.7-GHz maser VLBI positions and proper motions  
  > "with that of the 6.7-GHz CH$_3$OH masers observed with VLBI by (cite: San10a)" (4 The Keplerian disk) [from (cite: San10a)]
- External data: Systemic cloud velocity 60±0.04 km/s from single-dish  
  > "$V_{sys}~=~60~\pm~0.04$ km s$^{-1}$, obtained from single-dish observations (cite: Hil10)" (5.2 Proper motion and precession) [from (cite: Hil10)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline, plus line self-calibration  
  > "Data calibration was performed using the pipeline for ALMA data analysis in the Common Astronomy Software Applications (cite: McM07) package, version 4.7." (2 ALMA observations)
- casa version: CASA 4.7  
  > "Data calibration was performed using the pipeline for ALMA data analysis in the Common Astronomy Software Applications (cite: McM07) package, version 4.7." (2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5%  
  > "the ALMA flux calibration uncertainty of  5%, as recently estimated from the analysis of calibrators in bands 3 and 6 by (cite: Bon18)" (3.1 G16.59-0.05 B)
- self calibration: Strongest line in each SPW self-calibrated (channel-averaged); phase solutions applied to all channels; S/N gain 1.1-1.5  
  > "self-calibrated its channel-averaged emission, and, before imaging, applied the self-calibration phase solutions to all the channels of the SPW." (2 ALMA observations)

### Imaging

- task: CLEAN, manual  
  > "The images for the continuum and line emissions were produced manually using the CLEAN task" (2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "with the robust parameter of (cite: Bri95) set to 0.5, as a compromise between resolution and sensitivity to extended emission" (2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: STATCONT per-pixel statistical continuum estimate  
  > "For each SPW, we use STATCONT[^1] (cite: Sanc17), a statistical method to estimate the continuum level at each position of the map" (2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.13''-0.17''  
  > "The clean beam FWHM of the resulting images varies in the range  0.13$''$–0.17$''$." (2 ALMA observations)
- final rms: 0.08 mJy/beam continuum  
  > "The mm continuum image of  G16.59$-$0.05  has a  1$\sigma$ rms noise level of  0.08 mJy beam$^{-1}$, limited by the dynamic range." (2 ALMA observations)

### Inherited from earlier work

- Continuum subtraction method  
  > "we use STATCONT[^1] (cite: Sanc17), a statistical method to estimate the continuum level" (2 ALMA observations) [from (cite: Sanc17)]
- Dust opacity 1 cm2/g at 1.4 mm  
  > "assuming a dust opacity of  1 cm$^2$ g$^{-1}$ at 1.4 mm (cite: Oss94)" (3.1 G16.59-0.05 B) [from (cite: Oss94)]
- Positional accuracy formula FWHM/2 * sigma/I  
  > "The positional accuracy is equal to   $\frac{\rm FWHM}{2.0} \ \frac{\sigma}{I}$ (cite: Rei88)" (4 The Keplerian disk) [from (cite: Rei88)]

### Not stated but needed to reproduce (our reading)

- Image size, cell size, masks and clean thresholds
- Which SPW lines were used for self-calibration and solution intervals
- Channel widths used for the peak-position fits and the selection of fitted channels
- Coordinates of the phase centre
- Spectral-line flux/continuum calibrator for flux scale
- Line-free channel handling and STATCONT parameters
- MADCUBA version and the line catalogs used

## Analysis recipe

1. **Continuum and line imaging with self-calibration**: Pipeline calibration, line self-calibration, manual CLEAN with robust 0.5, STATCONT continuum subtraction  
  > "The images for the continuum and line emissions were produced manually using the CLEAN task" (2 ALMA observations)
   - software: CASA, STATCONT
   - parameter: robust = 0.5  
  > "with the robust parameter of (cite: Bri95) set to 0.5" (2 ALMA observations)
   - fitting: _not stated_
   - validation: Astrometric check with quasar J1830-1606, offset <10 mas  
  > "differs from the nominal position by less than 10 mas" (2 ALMA observations)
2. **Derive gas temperature and column density in the mm sources**: LTE fitting of unblended optically thin CH3OCH3 (CH3OH for A3) lines at the continuum peak of each source  
  > "AUTOFIT provides the best nonlinear least-squared fit using the Levenberg-Marquardt algorithm." (3.1 G16.59-0.05 B)
   - software: MADCUBA
   - parameter: free: Ncol, Tex, VLSR, FWHM  
  > "Leaving four parameters free to vary, that is, column density ($N_{\rm col}$), excitation temperature ($T_{\rm ex}$)" (3.1 G16.59-0.05 B)
   - assumption: LTE; transitions with optical depth < 0.5  
  > "which have optical depths of less (or much less) than 0.5" (3.1 G16.59-0.05 B)
   - fitting: Levenberg-Marquardt least squares (AUTOFIT)  
  > "AUTOFIT provides the best nonlinear least-squared fit using the Levenberg-Marquardt algorithm." (3.1 G16.59-0.05 B)
   - validation: _not stated_
3. **Mass of mm sources from dust continuum**: Fluxes within the 10% peak contour with fitted gas temperature, corrected for dust opacity  
  > "The masses in molecular gas of the mm sources are derived from the mm fluxes (integrating inside the contours at 10% of the peak marked in Fig. [1](#cont)) and the fitted gas temperatures" (3.1 G16.59-0.05 B)
   - assumption: dust opacity 1 cm2/g at 1.4 mm, gas-to-dust ratio 100, d=3.6 kpc  
  > "assuming a dust opacity of  1 cm$^2$ g$^{-1}$ at 1.4 mm (cite: Oss94) and a gas-to-dust mass ratio of 100" (3.1 G16.59-0.05 B)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Keplerian rotation to the disk around Bm**: 2D Gaussian fits of channel peak positions, then chi2 minimization of a Keplerian curve for red-shifted CH3OH channels with 20<=Eu<=150 K  
  > "which allows us to fit a 2D Gaussian profile and determine the peak position at each velocity channel." (4 The Keplerian disk)
   - parameter: priors: 0<=S*<=0.15'', 60.0<=V*<=61.0 km/s, M* in 5-15 Msun  
  > "The mass of the YSO is searched over the range  5–15 $M_{\odot}$" (4 The Keplerian disk)
   - assumption: Keplerian rotation; velocity scaled by sin(i); disk mass much less than YSO mass  
  > "our choice of fitting a Keplerian velocity profile appears to be well justified *a posteriori*" (4 The Keplerian disk)
   - fitting: chi2 grid minimization, 1-sigma confidence for three free parameters following Lampton et al. 1976  
  > "The white contour in these two plots draws the 1-$\sigma$ confidence level for the three free parameters, following (cite: Lam76)." (4 The Keplerian disk)
   - validation: Found an absolute chi2 minimum; compared with the maser kinematics and ZAMS mass for L=1e4 Lsun  
  > "These plots show that we do find an absolute minimum of the $\chi^2$" (4 The Keplerian disk)

## Software

- **CASA** 4.7: Pipeline calibration, self-calibration and CLEAN imaging  
  > "Data calibration was performed using the pipeline for ALMA data analysis in the Common Astronomy Software Applications (cite: McM07) package, version 4.7." (2 ALMA observations)
- **STATCONT** : Continuum level estimation and subtraction  
  > "For each SPW, we use STATCONT[^1] (cite: Sanc17)" (2 ALMA observations)
- **MADCUBA** : SLIM line identification and AUTOFIT LTE fitting  
  > "Using the SLIM (Spectral Line Identification and Modeling) tool of MADCUBA[^2]" (3.1 G16.59-0.05 B)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Gas temperature of mm source B | 131 | ±11 | K | 2 | / B / 70$\pm$6 / 17.8$\pm$16.6 / 131$\pm$11 / 62.3$\pm$0.2 / 5.1$\pm$0.5 / 1.8$\pm$0.3 / |
| Mass of mm source A1 | 5.1 | ±1.5 | Msun | 3 | / A1 / 164$\pm$18 / 17.2$\pm$16.4 / 111$\pm$18 / 62.4$\pm$0.5 / 4$\pm$1 / 5.1$\pm$1.5 / |
| Temperature of A3 | 42 | ±7 | K | 2 | / A3 / 41$\pm$5 / 15.6$\pm$15.1 / 42$\pm$7 / 62.1$\pm$0.5 / 3.4$\pm$0.9 / 4.0$\pm$1.3 / |
| Disk major axis position angle | 18 | ±3 | deg | 4 | elongated along the same  PA = 18$\pm$3$^\circ$ |
| YSO mass M* sin^2(i) | 10 | ±2 | Msun | 4 | $M_{\star} \, \sin^2(i)~=~10~\pm~2$ $M_{\odot}$ |
| YSO LSR velocity | 60.4 | ±0.5 | km/s | 4 | $V_{\star}~=~60.4~\pm~0.5$ km s$^{-1}$ |
| YSO positional offset along disk axis | -0.084 | ±0.020 | arcsec | 4 | $S_{\star}~=~-0.084\ensuremath{''}~\pm~0.020\ensuremath{''}$ |
| Disk radius | ≈500 | not stated | au | 4 | The disk radius is  $\approx$500 au |

## Qualitative findings

- The velocity gradient makes a ~70 degree angle with the radio jet; P-V diagrams are butterfly-shaped, indicating rotation  
  > "This gradient is oriented along a direction forming a large ($\approx$70$^\circ$) angle with the radio jet" (abstract)
- The 6.7-GHz masers do not trace the disk midplane  
  > "the new ALMA data indicate now that the 6.7-GHz masers are not tracing the disk midplane, as originally assumed." (4 The Keplerian disk)

## Claim tuples

- H: Is the gas around the 22-GHz YSO Bm rotating in a Keplerian disk? | E: P-V plots and channel peak position fits with chi2 Keplerian fit | R: Keplerian fit gives M* sin^2 i = 10±2 Msun, disk radius ~500 au | F: Keplerian disk around a ~10 Msun YSO | **supported**
- H: Why is the YSO offset from the jet axis and dust peak? | E: Compare 22 GHz, 6 GHz and ALMA positions; crossing time argument | R: Offset >=0.1'' | F: YSO may have moved from the center by dynamical interaction with companions | **partially**
- H: What are the physical conditions in the mm sources? | E: MADCUBA LTE fits and dust masses | R: Temperatures 42-131 K, masses 1-5 Msun | F: Main clump resolved into four compact mm sources | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: STATCONT used because line forests make identifying line-free channels very difficult  
  > "identifying the channels where no line emission is present is a very difficult task" (2 ALMA observations)
- Alternative: Bm as a bound multiple system with disk truncation rejected, since other YSOs are not dynamically relevant  
  > "other (putative) YSOs embedded in the parental mm source B are not dynamically relevant for the disk or the motion of Bm" (5.2 Proper motion and precession)
- How they decided it was enough: _not stated_
- Limitation (authors): Blue-shifted emission cannot be adequately fitted  
  > "the blue-shifted emission concentrates within a small offset range ($\le$0.04$''$) and cannot be adequately fitted" (4 The Keplerian disk)
- Limitation (authors): Inclination only constrained by assuming luminosity-derived mass upper limit  
  > "if a sizeable fraction of the bolometric luminosity is due to gravitational energy released in the accretion process rather than nuclear burning, the mass of Bm could be less than  13 $M_{\odot}$" (4 The Keplerian disk)
- Caveat (inferred, ours): Only red-shifted side is fitted; only mass times sin^2 i is constrained
- Caveat (inferred, ours): Gas temperature used for dust mass from LTE fit of a different species, not dust
- Caveat (inferred, ours): Ejection scenario is speculative, with no direct proper-motion evidence
- Caveat (inferred, ours): Table 3 column density errors appear inconsistent

## Reproducibility

- Data public (paper): ALMA project data cited; public after proprietary period (not explicitly stated)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00408.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Exact channels used in the Keplerian fit
- Missing: JVLA maps from earlier papers
- Data volume (inferred): about 50-200 GB raw
- Score (inferred): 3/5, Data public and fits described, but imaging and fit-channel details and external JVLA data are missing.
- Rediscovery candidate: no, Key results require manual choices in channel peak fitting and external JVLA/VLBI data not fully specified.

## Links

- Method: (cite: Sanc17) (STATCONT continuum estimation)
- Method: (cite: Rei88) (positional accuracy of Gaussian peak fits)
- Method: (cite: Lam76) (chi2 confidence intervals)
- Companion: (cite: Mos13b) (JVLA observations of the radio jet and maser disk in the same region)
- Companion: (cite: San10a) (VLBI maser observations of the region)

## Checks

```json
{
 "quotes": 69,
 "quotes_ok": 69,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 52,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
