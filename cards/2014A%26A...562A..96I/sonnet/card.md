# The molecular circumnuclear disk (CND) in Centaurus A. A multi-transition CO and [CI] survey with Herschel, APEX, JCMT, and SEST

`2014A&A...562A..96I` | Astronomy and Astrophysics 2014 | first author: Israel, F. P. | arXiv: 1402.0999 | DOI: 10.1051/0004-6361/201322780

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What are the physical conditions, excitation and mass of the molecular circumnuclear disk (CND) and extended thin disk in Cen A, from multi-transition CO and [CI] single-dish data?  
  > "In this paper, we combine single-dish CO and \[CI\] observations of the Cen A nucleus obtained from the ground over many years, and from space." (Introduction)
- Target **NGC 5128 (Centaurus A) nucleus**: coordinates _not stated_; z/distance D = 3.84 Mpc  
  > "NGC 5128 is the nearest ($D$ = 3.84 Mpc) giant elliptical (review by Israel 1998)." (Introduction); distance from Israel 1998 (review)  
  > "NGC 5128 is the nearest ($D$ = 3.84 Mpc) giant elliptical (review by Israel 1998)." (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6, CO J=2-1 mosaic  
  > "we have taken the ALMA Band 6 high-resolution mosaic of the $J$=2-1 $\,{\rm ^{12}CO}$ emission from Centaurus A" (Integral CND/ETD line profiles)
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
- pi or archival as stated: Public ALMA Calibration and Science Verification program data  
  > "obtained in the public ALMA Calibration and Science Verification program" (Integral CND/ETD line profiles)
- Line: 12CO J=2-1 (ALMA) (230.538 GHz)
- Other facility **Herschel SPIRE-FTS and HIFI**: CO, [CI], [CII], [NII] line fluxes and profiles  
  > "The spectral range covered the $\,{\rm ^{12}CO}$ lines in the $J$=4-3 to $J$=13-12 transitions as well as the two submillimeter \[C$\;$I\] lines" (Herschel-SPIRE)
- Other facility **APEX, JCMT, SEST**: Ground-based CO, 13CO, [CI] and HCN spectra  
  > "observe the $J$=1-0 HCN, $J$=1-0, and $J$=2-1 $\,{\rm ^{12}CO}$ and $\,{\rm ^{13}CO}$ transitions" (SEST 15m)
- External data: 13CO J=1-0 data used in pV maps  
  > "we have used $J$=1-0 $\,{\rm ^{13}CO}$ data from Wild et al.  (1997)" (Determination of individual CND and ETD CO ladders) [from Wild et al. 1997]
- External data: 12CO J=3-2 data used in pV maps  
  > "$J$=3-2 $\,{\rm ^{12}CO}$ data from Liszt (2001)" (Determination of individual CND and ETD CO ladders) [from Liszt 2001]

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
- smoothing: ALMA maps convolved to the resolution of each single-dish beam; central line profile integrated  
  > "we have constructed a series of maps at spatial resolutions identical to those of our single-dish line observations." (Integral CND/ETD line profiles)
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- ALMA data reduction/calibration details, CASA version, imaging parameters
- Which ALMA SV dataset/execution and exact map product used
- How the convolved beam shapes were defined
- Line-free channels and baseline details for single-dish spectra
- Gaussian decomposition fit details beyond stated constraints

## Analysis recipe

1. **Beam normalisation using ALMA CO(2-1) map**: Convolve ALMA CO(2-1) map to each single-dish resolution, extract nuclear profile integral, derive beam normalisation factors to a 22'' beam  
  > "we have determined the beam normalisation factors (BNFs) required to relate the emission line fluxes to one another." (Integral CND/ETD line profiles)
   - assumption: Distribution of CO-emitting clouds identical for all transitions  
  > "Assuming that the distribution on the sky of CO emitting clouds is identical for all transitions" (Integral CND/ETD line profiles)
   - fitting: _not stated_
   - validation: Normalised [CII] flux within 10% of interpolation of HIFI and ISO-LWS values  
  > "our normalised flux for the \[C$\;$II\] line is only $10\%$ above the value interpolated" (Integral CND/ETD line profiles)
2. **Decompose CND and ETD with Gaussians**: Fit ETD Gaussian plus one or two CND Gaussians to get CND_min and CND_max, adopt mean  
  > "The last two columns contain the mean of these two decompositions which we believe that best represents the actual situation." (Determination of individual CND and ETD CO ladders)
   - fitting: _not stated_
   - validation: _not stated_
3. **LVG and PDR/XDR modelling and gas mass**: Two-phase RADEX LVG grid fits; PDR/XDR fits; mass as geometric mean of LVG and PDR results  
  > "For the best estimate of the CND mass we use the geometric mean of the LVG and PDR results." (Beam-averaged molecular gas properties)
   - software: RADEX
   - assumption: [12CO]/[13CO] = 40  
  > "we assume a constant CO isotopical abundance \[$\,{\rm ^{12}CO}$\]/\[$\,{\rm ^{13}CO}$\] = 40 throughout." (LVG modelling)
   - fitting: Grid search over Tk, n(H2), N(CO)/dV; lowest chi-square for PDR  
  > "We identify acceptable fits by searching a grid of model parameter combinations" (LVG modelling)
   - validation: _not stated_

## Software

- **RADEX** : LVG radiative transfer modelling  
  > "with the *RADEX* large velocity gradient (LVG) radiative transfer models" (LVG modelling)
- **HIPE** 9.0.0: Herschel SPIRE processing  
  > "The data were processed and calibrated using *HIPE* version 9.0.0." (Herschel-SPIRE)
- **CLASS** : HIFI data reduction  
  > "Data were reduced using the *HIPE* and *CLASS* software packages." (Herschel-HIFI)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CND gas mass (best estimate) | 8.4e7 | factor of three (table); factor of two (conclusions) | Msun | 3 | This brings the mass to $M_{gas}\,=\,8.4\times10^{7}\,\rm M_{\odot}$ |
| CND CO-to-H2 conversion factor X | 4e20 | factor of two | cm^-2 (K km/s)^-1 | 3 | $X$ = 4$\times10^{20}$ $\,{\rm cm^{-2}}/\,{\rm {K\,km s^{-1}}}$ |
| CND molecular hydrogen column density (LVG) | 1.7e22 | 0.1e22 | cm^-2 | 3 | $N(\,{\rm H_{2}})=(1.7\pm0.1)\times10^{22}\,\,{\rm cm^{-2}}$ |
| CND surface filling factor | 0.10 | 0.01 | dimensionless | 3 | a four times higher molecular gas surface-filling factor ($0.10\pm0.01$) for the CND |
| [CI](2-1)/[CI](1-0) luminosity ratio | 2.6 | 0.5 | dimensionless | 1 | / \[C$\;$I\](2-1)/\[C$\;$I\](1-0) / 2.6$\pm$0.5 |

## Qualitative findings

- Cen A center CO ladder peaks at J=5-4 and drops faster than in AGN and starburst galaxies.  
  > "Thus, the central NGC 5128 CO ladder is the ’coolest’ of all galaxies considered." (Comparison of the central CO ladders)
- [CI] lines are stronger than neighbouring CO lines, unlike other galaxies, inconsistent with standard PDR models.  
  > "This behaviour is not seen in other (star-burst or AGN) galaxies, and is thus unique to the Cen A center." (Conclusions)

## Claim tuples

- H: Is the Cen A nuclear CO ladder different from those of starburst and AGN galaxies? | E: Compare SPIRE CO line ratios with literature galaxies | R: CO(10-9)/CO(5-4) = 0.26 vs 0.38 (AGN) and 1.25 (starburst) | F: Cen A has the steepest drop | **supported**
- H: What is the CND gas mass and X factor? | E: LVG and PDR/XDR modelling of decomposed CND CO ladder | R: 8.4e7 Msun, X = 4e20 | F: X is about twice the Milky Way value | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single-phase LVG models gave no satisfactory fit  
  > "We find that no combination of parameters from a single-phase gas provides a satisfactory fit to the observed line intensities." (LVG modelling)
- How they decided it was enough: _not stated_
- Limitation (authors): PDR/XDR fits not unique; high-J CND excitation not constrained  
  > "We note that the fits are not unique" (PDR/XDR modelling)
- Caveat (inferred, ours): Mass depends on assumed carbon abundances and model choice
- Caveat (inferred, ours): Decomposition is non-unique
- Caveat (inferred, ours): ALMA map used only for beam normalisation, with unspecified processing

## Reproducibility

- Data public (paper): ALMA data public SV  
  > "obtained in the public *ALMA* Calibration and Science Verification program" (Integral CND/ETD line profiles)
- Products in archive: _not stated_
- Missing: ALMA processing details
- Missing: Final fitted Gaussian parameters
- Missing: PDR model grid details
- Data volume (inferred): ~10-50 GB for ALMA SV mosaic; Herschel/single-dish data small
- Score (inferred): 2/5, ALMA is minor and undocumented; main results rely on single-dish data and models.
- Rediscovery candidate: no, ALMA role minor and recipe incomplete.

## Links

- Companion: Kazandjian et al. 2012 (mechanical heating in PDR models)
- Related: Herschel HEXGAL
- Related: ALMA Science Verification

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00008.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 25,
  "rate": 0.385
 },
 "evidence_ok": true
}
```
