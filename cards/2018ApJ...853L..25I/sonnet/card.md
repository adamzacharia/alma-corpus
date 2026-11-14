# ALMA Reveals an Inhomogeneous Compact Rotating Dense Molecular Torus at the NGC 1068 Nucleus

`2018ApJ...853L..25I` | The Astrophysical Journal Letters 2018 | first author: Imanishi, Masatoshi | arXiv: 1801.06564 | DOI: 10.3847/2041-8213/aaa8df

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: Do HCN J=3–2 and HCO+ J=3–2 trace a rotating dense molecular torus at the NGC 1068 nucleus, and what are its morphology and dynamics?  
  > "To better understand the properties of the torus, it is desirable to make high-spatial-resolution observations using different dense gas tracers." (Introduction)
- Target **NGC 1068**: coordinates 02h42m40.710s, -00d00m47.94s (ICRS, continuum peak)  
  > "NGC 1068 (z = 0.0037, distance $\sim$ 14 Mpc, 1 arcsec is $\sim$70 pc)" (Introduction); "The continuum peak position in our 0$\ensuremath{''}$01 pixel$^{-1}$ map is (02$^{h}$42$^{m}$40.710$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)ICRS" (Results); z/distance z = 0.0037, ~14 Mpc  
  > "NGC 1068 (z = 0.0037, distance $\sim$ 14 Mpc, 1 arcsec is $\sim$70 pc)" (Introduction); "The continuum peak position in our 0$\ensuremath{''}$01 pixel$^{-1}$ map is (02$^{h}$42$^{m}$40.710$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)ICRS" (Results); distance from cited (cite: ant85)  
  > "NGC 1068 (z = 0.0037, distance $\sim$ 14 Mpc, 1 arcsec is $\sim$70 pc)" (Introduction); "The continuum peak position in our 0$\ensuremath{''}$01 pixel$^{-1}$ map is (02$^{h}$42$^{m}$40.710$^{s}$, $-$00$^{\circ}$00$'$47.94$''$)ICRS" (Results)

## Data provenance

- ALMA projects: 2016.1.00052.S, 2013.1.00188.S
- bands: Band 6 (211–275 GHz)  
  > "We conducted ALMA band 6 (211–275 GHz) observations of the NGC 1068 nucleus" (2 Observations and Data Analysis)
- frequencies and spectral setup: 1.875 GHz wide spectral windows, three windows covering 263.7–268.6 GHz  
  > "We adopted the widest 1.875 GHz width mode in each spectral window. We took spectra at 263.7–268.6 GHz with three spectral windows" (2 Observations and Data Analysis)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: Cycle 4: 17–1808 m and 41–7552 m (H1); Cycle 2: 41–2270 m  
  > "Cycle 4 (H1) | 2017 Sep 11 | 40      | 41–7552" (Table 1)
- angular resolution: 0.04–0.07 arcsec (Cycle 4)  
  > "high-spatial-resolution (0$\ensuremath{''}$04–0$\ensuremath{''}$07) observations" (abstract)
- max recoverable scale: ~1.3 arcsec recovered; >2 arcsec resolved out  
  > "Diffuse emission with a spatial extent of $>$2$''$ is resolved out in our ALMA data." (2 Observations and Data Analysis)
- sensitivity: _not stated_
- time on source: 44 min and 39 min (Cycle 4), 25 min (Cycle 2)  
  > "Cycle 4 (H1) | 2017 Sep 11 | 40      | 41–7552  | 39" (Table 1)
- observing dates: 2016 Oct 19, 2017 Sep 11 (Cycle 4); 2015 Sep 19 (Cycle 2)  
  > "Cycle 2      | 2015 Sep 19 | 36      | 41–2270  | 25" (Table 1)
- pi or archival as stated: _not stated_
- Line: HCN J=3–2 (265.886 GHz)
- Line: HCO+ J=3–2 (267.558 GHz)
- External data: Inclination i = 34–46 deg  
  > "the inclination angle ($i$) is estimated to be $i$ = 34–46$^{\circ}$ (cite: gar16)" (Discussion) [from (cite: gar16)]
- External data: SMBH mass ~1e7 Msun from water maser disk  
  > "SMBH mass of NGC 1068, $\sim$ 1 $\times$ 10$^{7}$M$_{\odot}$ (cite: gre96; hur02; lod03)" (Discussion) [from (cite: gre96; hur02; lod03)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Started from calibrated data provided by ALMA  
  > "starting from calibrated data provided by ALMA" (2 Observations and Data Analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "We then applied the task “clean” (Briggs-weighting" (2 Observations and Data Analysis)
- deconvolver: _not stated_
- weighting robust: Briggs, robust=0.5, gain=0.1  
  > "robust=0.5, gain $=$ 0.1" (2 Observations and Data Analysis)
- uv taper: _not stated_
- cell size: 0.01 arcsec/pixel  
  > "the pixel scale was 0$\ensuremath{''}$01 pixel$^{-1}$" (2 Observations and Data Analysis)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, constant continuum  
  > "used the CASA task “uvcontsub” to subtract a constant continuum from molecular line data" (2 Observations and Data Analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: (a) Cycle 4 longest baseline only; (b) Cycle 2 plus all Cycle 4 data  
  > "(b) Cycle 2 and all Cycle 4 data" (2 Observations and Data Analysis)
- smoothing: velocity resolution ~20 km/s  
  > "The adopted velocity resolution was $\sim$20 km s$^{-1}$" (2 Observations and Data Analysis)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cycle 2 data and earlier results at the same lines  
  > "previously revealed by our 0$\ensuremath{''}$1–0$\ensuremath{''}$2 resolution Cycle 2 data (cite: ima16)" (Results) [from (cite: ima16)]
- HCN luminosity derivation  
  > "derived using Equations (1) and (3) of (cite: sol05)" (Discussion) [from (cite: sol05)]
- Dense gas mass conversion factor M_dense = 10 x L'HCN(1-0)  
  > "M$_{\rm dense}$ = 10 $\times$ HCN J=1–0 luminosity" (Discussion) [from (cite: gao04; kri08)]

### Not stated but needed to reproduce (our reading)

- Line-free channels used for continuum
- Clean mask, threshold and iterations
- Final beam sizes and rms noise
- CASA version
- Flux scale uncertainty and self-calibration
- Moment clipping thresholds
- Which Cycle 4 execution blocks were combined in (b) and weighting between datasets

## Analysis recipe

1. **Image continuum and line data**: uvcontsub then clean on continuum-subtracted data; two datasets (a) H1 only and (b) all  
  > "We created cleaned images by using (a) Cycle 4 longest baseline data only (dubbed as “H1” in Table 1) and (b) Cycle 2 and all Cycle 4 data." (2 Observations and Data Analysis)
   - software: CASA
   - parameter: robust=0.5, 0.01 arcsec pixel, ~20 km/s channels  
  > "robust=0.5, gain $=$ 0.1" (2 Observations and Data Analysis)
   - fitting: _not stated_
   - validation: Same features in HCN and HCO+ suggest they are real  
  > "strongly suggesting that they are real" (Results)
2. **Measure torus morphology**: imfit on moment 0 maps for PA and deconvolved sizes  
  > "We used the CASA task “imfit” function in these maps to estimate the position angles" (Results)
   - software: CASA
   - fitting: imfit 2D Gaussian  
  > "We used the CASA task “imfit” function in these maps to estimate the position angles to be PA = 107$\pm$3$^{\circ}$ and 109$\pm$6$^{\circ}$ (east of north)" (Results)
   - validation: _not stated_
3. **Extract and fit spectra**: Spectra in 0.2x0.15 arcsec rectangle; Gaussian fits  
  > "We extracted HCN J=3–2 and HCO$^{+}$ J=3–2 spectra within the 0$\ensuremath{''}$2 (east–west) $\times$ 0$\ensuremath{''}$15 (north–south) rectangular region" (Results)
   - fitting: Gaussian fits  
  > "We extracted HCN J=3–2 and HCO$^{+}$ J=3–2 spectra within the 0$\ensuremath{''}$2 (east–west) $\times$ 0$\ensuremath{''}$15 (north–south) rectangular region around the mass-accreting SMBH position and applied Gaussian fits" (Results)
   - validation: _not stated_
4. **Derive dense gas mass and enclosed dynamical mass**: L'HCN to M_dense with factor 10; Keplerian enclosed mass from v/sin i ~20 km/s at r~3 pc  
  > "we derive the rotational velocity to be v/sin($i$) $\sim$ 20 (km s$^{-1}$) at distance r $\sim$3 (pc)" (Discussion)
   - assumption: HCN optically thick and thermalized so L'(1-0)=L'(3-2); Keplerian rotation; i=34 deg  
  > "even if we adopt the lowest value of $i$ = 34$^{\circ}$" (Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction, uvcontsub, clean, imfit  
  > "We used CASA (https://casa.nrao.edu) for our data reduction" (2 Observations and Data Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| PA HCN J=3–2 | 107 | 3 | deg | 2 | PA = 107$\pm$3$^{\circ}$ and 109$\pm$6$^{\circ}$ |
| PA HCO+ J=3–2 | 109 | 6 | deg | 2 | PA = 107$\pm$3$^{\circ}$ and 109$\pm$6$^{\circ}$ |
| HCN deconvolved size | 186 x 63 | 17 x 7 | mas | 2 | 186$\pm$17 mas $\times$ 63$\pm$7 mas (13 pc $\times$ 4 pc) for HCN J=3–2 |
| HCN peak velocity / FWHM | 1137 / 156 | 3 / 9 | km/s | 3 | peak optical LSR velocity = 1137$\pm$3 (km s$^{-1}$), full-width at half-maximum FWHM = 156$\pm$9 (km s$^{-1}$) |
| HCN J=3–2 line flux | 2.6 | 0.2 | Jy km/s | 3 | 2.6$\pm$0.2 (Jy km s$^{-1}$) and 2.0$\pm$0.1 (Jy km s$^{-1}$) |
| Dense molecular mass | ~2e6 | not stated | Msun | 4 | $\sim$2 $\times$ 10$^{6}$ M$_{\odot}$, or possibly even higher |
| Enclosed Keplerian mass | ~9e5 | not stated | Msun | 4 | $\sim$9 $\times$ 10$^{5}$M$_{\odot}$ |

## Qualitative findings

- Eastern side redshifted and western blueshifted; west has larger dispersion and stronger emission; torus counter-rotates relative to host gas  
  > "are found to be counter-rotating, suggesting an external process happened in the past at the NGC 1068 nucleus" (abstract)

## Claim tuples

- H: HCN and HCO+ J=3–2 trace rotating dense gas aligned with the torus direction | E: Moment maps of long baseline data | R: PA ~107-109 deg, east redshifted, west blueshifted | F: Lines are better torus probes than CO 6-5 | **supported**
- H: Torus is axisymmetric | E: Moment 0 and 2 maps | R: West brighter and more dispersed | F: Torus is inhomogeneous | **supported**
- H: Torus motion is Keplerian around the SMBH | E: Compare enclosed mass from rotation to SMBH mass | R: ~9e5 vs ~1e7 Msun | F: Motion is far from Keplerian | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Large ambiguity in HCN-to-dense-mass conversion factor  
  > "Though there may be a large ambiguity in the above conversion factor" (Discussion)
- Caveat (inferred, ours): Rotation velocity ~20 km/s derived from a barely resolved velocity gradient with no kinematic model fit
- Caveat (inferred, ours): Beam smearing and the large inclination uncertainty affect enclosed mass
- Caveat (inferred, ours): No error estimate on enclosed mass or dense mass conversion

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Clean masks and thresholds
- Missing: Line-free channels
- Missing: CASA version
- Missing: Moment map thresholds
- Missing: Flux and beam values
- Data volume (inferred): ~100-300 GB raw for three execution blocks plus Cycle 2
- Score (inferred): 3/5, Project codes and main imaging parameters given, but many processing details and kinematic derivation steps are sparse.
- Rediscovery candidate: yes, Data from ALMA archive, imfit sizes, PAs and Gaussian fit numbers are checkable, though some settings are missing.

## Links

- Companion: Imanishi, Nakanishi & Izumi 2016 (cite: ima16) (Cycle 2 observations of same lines)
- Companion: Garcia-Burillo et al. 2016 (cite: gar16) (CO 6-5 comparison)

## Checks

```json
{
 "quotes": 53,
 "quotes_ok": 53,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 65,
  "stated": 35,
  "rate": 0.538
 },
 "evidence_ok": true
}
```
