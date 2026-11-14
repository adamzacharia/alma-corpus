# Gas Dynamics of a Luminous z = 6.13 Quasar ULAS J1319+0950 Revealed by ALMA High-resolution Observations

`2017ApJ...845..138S` | The Astrophysical Journal 2017 | first author: Shao, Yali | arXiv: 1707.03078 | DOI: 10.3847/1538-4357/aa826c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies, agn_and_quasars
- Question: What are the gas dynamics, dynamical mass and black hole to host mass ratio of the z=6.13 quasar J1319+0950 from high-resolution [C II] and dust continuum imaging?  
  > "we report on ALMA Cycle 1 observations of a FIR-luminous quasar ULAS J131911.29$+$095051.4 (hereafter J1319$+$0950) at $z$ = 6.13, and combine it with ALMA Cycle 0 data to study gas dynamics." (1 Introduction)
- Target **ULAS J131911.29+095051.4 (J1319+0950)**: coordinates J131911.29+095051.4  
  > "(cite: Mortlock2009) discovered this optically bright quasar from UKIRT Infrared Deep Sky Survey (UKIDSS) with $m_{1450\AA}$ = 19.65." (1 Introduction); z/distance z = 6.13 ([C II] z = 6.1331 ± 0.0005)  
  > "(cite: Mortlock2009) discovered this optically bright quasar from UKIRT Infrared Deep Sky Survey (UKIDSS) with $m_{1450\AA}$ = 19.65." (1 Introduction); distance from [C II] redshift from this work; also CO(6-5) and Mg II  
  > "(cite: Mortlock2009) discovered this optically bright quasar from UKIRT Infrared Deep Sky Survey (UKIDSS) with $m_{1450\AA}$ = 19.65." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00206.S, 2012.1.00240.S
- bands: Band 6  
  > "We used the ALMA band-6 receivers with 34 12 m antennas in the C34-6 configuration." (2.1 ALMA Observations and Data Reduction)
- frequencies and spectral setup: One 2 GHz spw at 266.443 GHz for [C II]; three other spws for continuum  
  > "We tuned one of the 2 GHz spectral windows to the redshifted [C II] line frequency of $\nu_{\rm obs}$ = 266.443 GHz" (2.1 ALMA Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-6 (Cycle 1)  
  > "We used the ALMA band-6 receivers with 34 12 m antennas in the C34-6 configuration." (2.1 ALMA Observations and Data Reduction)
- baselines: _not stated_
- angular resolution: 0.28'' x 0.22'' (1.61 x 1.27 kpc)  
  > "The synthesized beam size of the final [C II] image is $0.28\ensuremath{''}$ $\times$ $0.22\ensuremath{''}$" (2.1 ALMA Observations and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: 0.22 mJy/beam per 62.5 MHz (line); 0.03 mJy/beam (continuum)  
  > "The 1-$\sigma$ noise is 0.22 mJy beam$^{-1}$ per 62.5 MHz for the line, and 0.03 mJy beam$^{-1}$ for the continuum." (2.1 ALMA Observations and Data Reduction)
- time on source: 0.6 hours (Cycle 1)  
  > "The total on-source integration time was 0.6 hours." (2.1 ALMA Observations and Data Reduction)
- observing dates: August 2014 (Cycle 1)  
  > "We imaged the [C II] line emission ($\nu_{\rm rest}$ = 1900.5369 GHz) of J1319+0950 in August 2014." (2.1 ALMA Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Line: [C II] 158 um fine structure (1900.5369 GHz)
- Other facility **Gemini NIRI**: Near-IR spectrum used for Mg II line width and L3000 to derive M_BH  
  > "we fit the Gemini NIRI spectrum of ULAS J1319+0950 (cite: Mortlock2009) with a linear continuum, a Gaussian for Mg II line" (3.2.3 M_BH-M_dyn relation)
- External data: ALMA Cycle 0 data of J1319+0950 combined with the new data  
  > "We then combined the new data with ALMA Cycle 0 data (cite: Wang2013)" (2.1 ALMA Observations and Data Reduction) [from (cite: Wang2013)]
- External data: CO(6-5) gas mass 1.5e10 Msun  
  > "(cite: Wang2011fir) presented a gas mass of 1.5 $\times$ 10$^{10}$ $M_{\odot}$ by PdBI CO (6$-$5) observations." (3.1 Gas, Dust and Star Formation Distribution) [from (cite: Wang2011fir)]
- External data: FIR luminosity (10.7 ± 1.3)e12 Lsun (47 K, beta=1.6)  
  > "(cite: Wang2013) estimated the FIR luminosity of (10.7 $\pm$ 1.3) $\times$ 10$^{12}$ $L_{\odot}$" (3.1 Gas, Dust and Star Formation Distribution) [from (cite: Wang2013)]
- External data: Gemini NIRI spectrum of the quasar  
  > "We also thank professor D. J. Mortlock for providing the Gemini NIRI spectrum of J1319+0950." (Acknowledgments) [from (cite: Mortlock2009)]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data were reduced using the Common Astronomy Software Application (CASA[^1]; Version 4.5.0) pipeline." (2.1 ALMA Observations and Data Reduction)
- casa version: CASA 4.5.0  
  > "The data were reduced using the Common Astronomy Software Application (CASA[^1]; Version 4.5.0) pipeline." (2.1 ALMA Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "We calibrated the flux scale based on observations of Titan." (2.1 ALMA Observations and Data Reduction)
- flux scale uncertainty: ~15% adopted for combined data  
  > "For our combined data, we considered a calibration uncertainty $\sim$ 15$\%$." (2.1 ALMA Observations and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "made the continuum image and line image data cube from the combined data using the CLEAN task in CASA with robust weighting (robust = 0.5)" (2.1 ALMA Observations and Data Reduction)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "made the continuum image and line image data cube from the combined data using the CLEAN task in CASA with robust weighting (robust = 0.5)" (2.1 ALMA Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction  
  > "We subtracted the dust continuum under the [C II] line emission in the uv-plane" (2.1 ALMA Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Cycle 1 combined with Cycle 0 data  
  > "We then combined the new data with ALMA Cycle 0 data (cite: Wang2013)" (2.1 ALMA Observations and Data Reduction)
- smoothing: binned to 62.5 MHz (~70 km/s) channels  
  > "binned the data to a channel width of 62.5 MHz ($\sim$ 70 km s$^{-1}$)" (2.1 ALMA Observations and Data Reduction)
- final beam: 0.28'' x 0.22''  
  > "The synthesized beam size of the final [C II] image is $0.28\ensuremath{''}$ $\times$ $0.22\ensuremath{''}$" (2.1 ALMA Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Cycle 0 data, redshift and flux calibration uncertainty from earlier paper  
  > "The flux calibration uncertainty is $\ensuremath{\lesssim}$ 15$\%$ for ALMA Cycle 0 J1319$+$0950 [C II] observations (cite: Wang2013)" (2.1 ALMA Observations and Data Reduction) [from (cite: Wang2013)]
- ROTCUR weighting and exclusion angle follow recommendation  
  > "Following the recommendation by (cite: Lucero2015), we adopt a UNIFORM weighting and an exclusion angle of 0 $\ensuremath{^\circ}$" (3.2.1 GIPSY modeling of gas dynamics) [from (cite: Lucero2015)]
- M_BH from Mg II using Shen & Liu virial relation and Fe II template  
  > "The final $M_{\rm BH}$ calculated from Equation 3 in (cite: Shen2012) is (2.7 $\pm$ 0.6) $\times$ 10$^{9} M_{\odot}$." (3.2.3 M_BH-M_dyn relation) [from (cite: Shen2012)]

### Not stated but needed to reproduce (our reading)

- Cycle 0 execution blocks and calibration details
- Image size, cell size, cleaning threshold and mask
- Line-free channels for continuum subtraction
- Rest-frame velocity zero point and moment-map pixel handling
- How M_dyn is computed from V_c (formula, e.g. M = V^2 R/G)
- Initial values for ROTCUR fit
- Continuum bandwidth/frequency

## Analysis recipe

1. **Image combined Cycle 0+1 data**: uv-plane continuum subtraction, channel binning, CLEAN with robust 0.5 of combined data  
  > "made the continuum image and line image data cube from the combined data using the CLEAN task in CASA with robust weighting (robust = 0.5)" (2.1 ALMA Observations and Data Reduction)
   - software: CASA
   - parameter: 62.5 MHz channels, robust = 0.5  
  > "binned the data to a channel width of 62.5 MHz ($\sim$ 70 km s$^{-1}$)" (2.1 ALMA Observations and Data Reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line and continuum size, flux, and spectrum**: 2-D Gaussian fits to maps; spectrum integrated over pixels above 2 sigma, fit with Gaussian  
  > "We fitted the [C II] line emission with a 2-D Gaussian, which yielded a deconvolved source size" (2.2 Results)
   - parameter: 2-sigma region for spectrum extraction  
  > "including pixels determined in the line-emitting region above 2-$\sigma$ in the [C II] velocity-integrated map" (2.2 Results)
   - fitting: Gaussian line profile  
  > "The resulting line spectrum is shown as a black histogram in the right panel of Figure 1, with the best-fit Gaussian profile superposed." (Results)
   - validation: Flux compared to Cycle 0 and to total flux in 2-sigma region  
  > "We also got a consistent value by calculating the total flux within the 2-$\sigma$ region in the [C II] intensity map." (2.2 Results)
3. **Make velocity field**: Gaussian spectral fit per position with 2-sigma flux cut  
  > "It was made using the AIPS[^2] XGAUS task with 2-$\sigma$ flux cut at each position by Gaussian spectral fit." (2.2 Results)
   - software: AIPS
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit tilted ring model to velocity field**: ROTCUR in GIPSY, five rings width 0.1'' centred 0.15''-0.55''; phi, i fit first, then centre and Vsys; weighted means  
  > "We solve for $V_{c}(R)$ in five concentric rings, each with a width of $0.1\ensuremath{''}$ and central radius from $0.15\ensuremath{''}$ to $0.55\ensuremath{''}$." (3.2.1 GIPSY modeling of gas dynamics)
   - software: GIPSY ROTCUR
   - parameter: UNIFORM weighting, exclusion angle 0 deg; only rings >3 sigma used  
  > "Note that only rings with fitting parameter values above 3-$\sigma$ are considered as a successful fit" (3.2.1 GIPSY modeling of gas dynamics)
   - assumption: Pure circular rotation; shared centre, Vsys, phi, i across rings  
  > "we simply assume that the gas has a pure circular rotation in a gas disk" (3.2 Gas Dynamics in the Quasar Host Galaxy)
   - fitting: Least-squares in ROTCUR; errors are weighted standard deviations  
  > "The final values of $\phi$ and $i$ are calculated as the weighted mean of each $\phi(R)$ and $i(R)$, and the uncertainties are taken as the weighted standard deviations ($\sigma_{sdv}$) of the fitting parameters" (Discussion, GIPSY modeling of gas dynamics)
   - validation: Model velocity field (VELFI) and residual map <30 km/s; inclination varied 26-48 deg  
  > "The residual map is shown in the middle panel with velocity difference less than 30 km s$^{-1}$ across the entire velocity field." (3.2.2 Rotation curve)
5. **Derive M_dyn, M_BH and mass ratio**: M_dyn from V_c at 3.2 kpc; M_BH from Mg II width and L3000 via Shen & Liu; compare with local ratio from Kormendy & Ho  
  > "The derived $M_{\rm BH}$/$M_{\rm dyn}$ ratio is 0.020, which is about 4 times higher than the present-day $M_{\rm BH}$/$M_{\rm bulge}$ ratio" (3.2.3 M_BH-M_dyn relation)
   - assumption: Dynamical mass taken as bulge mass for local ratio  
  > "calculated taking our dynamical mass as the bulge mass by Equation 11 in (cite: Ho2013)" (3.2.3 M_BH-M_dyn relation)
   - fitting: Linear continuum + Gaussian Mg II + Fe II template  
  > "we fit the Gemini NIRI spectrum of ULAS J1319+0950 (cite: Mortlock2009) with a linear continuum, a Gaussian for Mg II line, and an ultraviolet Fe II template based on (cite: Shen2012)" (Discussion, M_BH-M_dyn relation)
   - validation: Errors from i = 26 and 48 deg  
  > "And as a sequence, the $M_{\rm BH}$/$M_{\rm dyn}$ ratio would be 0.013 and 0.033, which are 2 and 7 times higher than the local values." (Discussion, M_BH-M_dyn relation)

## Software

- **CASA** 4.5.0: Pipeline reduction and CLEAN imaging  
  > "The data were reduced using the Common Astronomy Software Application (CASA[^1]; Version 4.5.0) pipeline." (2.1 ALMA Observations and Data Reduction)
- **AIPS** : XGAUS task for velocity map  
  > "It was made using the AIPS[^2] XGAUS task with 2-$\sigma$ flux cut at each position by Gaussian spectral fit." (2.2 Results)
- **GIPSY** : ROTCUR tilted ring fit and VELFI model velocity field  
  > "We use ROTCUR task in the Groningen Image Processing System (GIPSY[^3]; (cite: vanderHulst1992))" (3.2.1 GIPSY modeling of gas dynamics)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [C II] redshift | 6.1331 | 0.0005 | dimensionless | 2 | 6.1331 $\pm$ 0.0005 |
| [C II] FWHM | 548 | 47 | km/s | 2 | 548 $\pm$ 47 |
| Continuum flux density | 4.72 | 0.17 | mJy | 2 | 4.72 $\pm$ 0.17 |
| [C II] line flux (Gaussian fit) | 4.85 | 0.40 | Jy km/s | 2 | $^{c}$4.85 $\pm$ 0.40 |
| Inclination | 34 | 4 | deg | 4 | 237 $\pm$ 4 $\ensuremath{^\circ}$, and 34 $\pm$ 4 $\ensuremath{^\circ}$ |
| Circular velocity at 3.2 kpc | 427 | 55 | km/s | 4 | The circular velocity at the largest radius (i.e., 3.2 kpc) is 427 $\pm$ 55 km s$^{-1}$. |
| Dynamical mass within 3.2 kpc | 13.4 | +7.8/-5.3 | 1e10 Msun | 5 | 13.4$_{-5.3}^{+7.8}$ $\times 10^{10}\,M_{\odot}$ |
| M_BH | 2.7e9 | 0.6e9 | Msun | 5 | is (2.7 $\pm$ 0.6) $\times$ 10$^{9} M_{\odot}$ |
| M_BH/M_dyn | 0.020 | +0.013/-0.007 | dimensionless | 5 | 0.020$_{-0.007}^{+0.013}$ |

## Qualitative findings

- [C II] emission is more irregular than the dust continuum, suggesting different distributions  
  > "The [C II] line emission is more irregular than the dust continuum emission" (abstract)

## Claim tuples

- H: Does the quasar's [C II] gas show ordered rotation? | E: Tilted ring fit of the velocity field | R: Vc = 427 ± 55 km/s at 3.2 kpc, i = 34 deg | F: Consistent with a rotating disk, though outflow is not excluded | **partially**
- H: Does the SMBH lie above the local M_BH/M_bulge relation? | E: Compare M_BH/M_dyn with local ratio | R: 0.020 vs 0.0051, ~4 times higher | F: SMBH grows before the bulk of the host stellar mass | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Inclination derived from only two successful rings; real uncertainty may be much larger  
  > "the inclination angle ($i$) is calculated as the weighted mean of only two successful $i(R)$ values." (3.2.2 Rotation curve)
- Caveat (inferred, ours): Tilted ring model ignores beam smearing with only ~5 beam-sized rings
- Caveat (inferred, ours): Dynamical mass assumes bulge equals dynamical mass and disk geometry
- Caveat (inferred, ours): Inclination poorly constrained

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Cycle 0 calibration/imaging details
- Missing: Imaging grid and mask parameters
- Missing: Gemini NIRI spectrum (provided privately)
- Data volume (inferred): ~10-20 GB raw for two small projects
- Score (inferred): 3/5, Public ALMA data and named tools, but imaging parameters and mass formulae are incomplete.
- Rediscovery candidate: no, Public data status is not stated by the paper and key imaging and fit settings are missing.

## Links

- Method: (cite: Rogstad1974) (Tilted ring model)
- Method: (cite: Shen2012) (M_BH Mg II relation)
- Companion: (cite: Wang2013) (Cycle 0 ALMA [C II] observations)

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 50,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
