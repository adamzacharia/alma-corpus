# An ALMA archival study of the clump mass function in the Large Magellanic Cloud

`2019MNRAS.483.1624B` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Brunetti, Nathan | arXiv: 1811.07994 | DOI: 10.1093/mnras/sty3148

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, nearby_galaxies
- Question: What is the dust-derived clump mass function of star forming regions in the LMC, and how does it compare with Milky Way core/clump mass functions?  
  > "we calculate and analyze the dust-derived clump mass function in the lmc to facilitate comparison with mass functions of star forming regions in the Milky Way." (Introduction)
- Target **30 Doradus-10 (dor)**: coordinates 05:38:48 -69:04:48 (J2000)  
  > "dor | 05:38:48 | -69:04:48 | 2011.0.00471.S" (Table 1); z/distance 50 kpc (LMC)  
  > "dor | 05:38:48 | -69:04:48 | 2011.0.00471.S" (Table 1); distance from Pietrzynski et al. 2013  
  > "dor | 05:38:48 | -69:04:48 | 2011.0.00471.S" (Table 1)
- Target **N159W**: coordinates 05:39:37 -69:45:48 (J2000)  
  > "N159W | 05:39:37 | -69:45:48 | 2012.1.00554.S" (Table 1); z/distance 50 kpc (LMC)  
  > "N159W | 05:39:37 | -69:45:48 | 2012.1.00554.S" (Table 1); distance from Pietrzynski et al. 2013  
  > "N159W | 05:39:37 | -69:45:48 | 2012.1.00554.S" (Table 1)
- Target **N159E**: coordinates 05:40:09 -69:44:44 (J2000)  
  > "N159E | 05:40:09 | -69:44:44" (Table 1); z/distance 50 kpc (LMC)  
  > "N159E | 05:40:09 | -69:44:44" (Table 1); distance from Pietrzynski et al. 2013  
  > "N159E | 05:40:09 | -69:44:44" (Table 1)
- Target **N113**: coordinates 05:13:18 -69:22:25 (J2000)  
  > "N113 | 05:13:18 | -69:22:25 | 2013.1.01136.S" (Table 1); z/distance 50 kpc (LMC)  
  > "N113 | 05:13:18 | -69:22:25 | 2013.1.01136.S" (Table 1); distance from Pietrzynski et al. 2013  
  > "N113 | 05:13:18 | -69:22:25 | 2013.1.01136.S" (Table 1)
- Target **GMC 225, N166, PCC 11546**: coordinates GMC 225 05:47:09 -70:40:16; N166 05:44:29 -69:25:43; PCC 11546 05:24:09 -71:53:37  
  > "PCC 11546 | 05:24:09 | -71:53:37 | 2013.1.00832.S" (Table 1); z/distance 50 kpc (LMC)  
  > "PCC 11546 | 05:24:09 | -71:53:37 | 2013.1.00832.S" (Table 1); distance from Pietrzynski et al. 2013  
  > "PCC 11546 | 05:24:09 | -71:53:37 | 2013.1.00832.S" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00471.S, 2016.1.01533.S, 2012.1.00554.S, 2013.1.01136.S, 2012.1.00603.S, 2013.1.01091.S, 2013.1.00832.S
- bands: Band 3 (~3.2 mm) and Band 6 (~1.3 mm) continuum  
  > "we focused on continuum observations from 86 GHz to 100 GHz ({\sim}3.2 mm) and 217 GHz to 233 GHz ({\sim}1.3 mm) in alma’s Bands 3 and 6, respectively." (2.1 Spatial and spectral setups)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 1.6–4 GHz effective  
  > "Effective bandwidths used in making the continuum maps ranged between 1.6 GHz and 4 GHz." (2.1 Spatial and spectral setups)
- arrays: 12 m plus ACA (7 m); N113 main array only  
  > "12 m (main array) plus aca data were obtained for all fields except N113, which was observed as a single pointing and only with the main array." (2.1 Spatial and spectral setups)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: average synthesized beam ~2.3 arcsec (~0.6 pc)  
  > "The average synthesized beam size was {\sim}2.3 ″ corresponding to {\sim}0.6" (2.4 Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2011 Dec 31 to 2017 Apr 21 (Cycles 0, 1, 2, 4)  
  > "The projects were observed between 2011 December 31 and 2017 April 21 spanning Cycles 0, 1, 2, & 4." (2.1 Spatial and spectral setups)
- pi or archival as stated: _not stated_
- Other facility **ATCA**: 4.8 and 8.4 GHz radio images of 30 Dor and N159 used to test free-free decomposition  
  > "4.8 GHz (6 cm) and 8.4 GHz (3 cm) observations were made of 30 Doradus (cite: Laz2003) and N159 (cite: Ind2004) with the atca." (3.1 Free-free correction)
- Other facility **Herschel (Gordon et al. 2014 maps)**: dust temperature and emissivity maps  
  > "The dust temperature and opacity were calculated from the (cite: Gor2014) temperature and emissivity maps" (3.3 Converting dust flux to total gas mass)
- External data: dust emissivity index beta=1.49 from LMC-wide Herschel SED fits (bembb)  
  > "We use an average value for the dust emissivity spectral index of $\beta=1.49$ from the (cite: Gor2014) lmc-wide dust sed fits to Herschel observations." (3.1 Free-free correction) [from (cite: Gor2014)]
- External data: gas-to-dust ratio 500  
  > "we applied a conversion to total gas mass through a g2d ratio of 500 from (cite: Rom2017)." (3.3 Converting dust flux to total gas mass) [from (cite: Rom2017)]
- External data: Milky Way core/clump double power law fits for comparison  
  > "using the best fit parameters reported by (cite: Rei2006b) will remove any variability introduced in the fitting step." (4.2 Comparison to other studies) [from (cite: Rei2006b)]

## Processing

### Calibration

- pipeline or manual: Dor: archive calibrated visibilities with statwt reweighting; others re-run manual scripts or pipeline  
  > "dor had calibrated visibilities available and we used those data after recalculating the weights based upon the scatter in the visibilities using the casa `statwt` command." (2.3 Calibration)
- casa version: CASA 4.7.2-REL (r39762) for manual calibration; pipeline data used CASA closest to observatory version  
  > "in the latest version of casa available at the time, 4.7.2-REL (r39762)." (2.3 Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 4.7.2 clean, multi-frequency synthesis, psfmode psfclark  
  > "with the `robust` parameter set to 0.5, in multi-frequency synthesis mode, with `psfmode` set to “psfclark”" (2.4 Imaging)
- deconvolver: _not stated_
- weighting robust: Briggs robust=0.5 (robust=2.0 for non-detection fields)  
  > "setting `robust` to 2.0 to favor s/n over resolution." (2.5 Fields without detections)
- uv taper: Band 3 uv trimmed at Band 6 minimum uv; Band 6 tapered to Band 3 beam, restoringbeam forced  
  > "we used the `restoringbeam` parameter in `clean` to force the Band 6 Gaussian beam shape to be the same as that of the Band 3 map." (2.4 Imaging)
- cell size: _not stated_
- image size: _not stated_
- masking: auto-masking script based on M100 CASA guide; thresholds 1.5–3 x noise; min mask 0.5 beam  
  > "All auto-masking was done with stopping thresholds between 1.5 and 3 times the noise in the map and using minimum mask areas of 0.5 times the map synthesized beam." (2.4 Imaging)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: strong lines identified with plotms and flagged  
  > "Strong emission lines were identified with the plotms task and flagged before the visiblities were imaged to produce continuum maps." (2.4 Imaging)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Auto-masking algorithm based on M100 CASA guide  
  > "This algorithm is heavily based upon the auto-masking code given in the M100 casa Guide as it appeared in August, 2016." (2.4 Imaging) [from M100 CASA Guide (Aug 2016)]
- Fitting weights and Monte Carlo uncertainty approach  
  > "To estimate fitting weights we followed the approach used by (cite: Rei2006a)" (4.1 lmc clump mass function) [from (cite: Rei2006a)]
- ClumpFind contour settings tested against synthetic detection  
  > "This combination of lowest contour level and contour spacing was also shown to result in the lowest number of missed and “false” clumps" (3.2 Clump finding) [from (cite: Wil1994)]

### Not stated but needed to reproduce (our reading)

- Line-free channel/spw selections per field for continuum imaging
- Exact uv-trim values for Band 3 and taper values per field (partly in table)
- Auto-masking code is only in a thesis appendix
- Band 3 and Band 6 central frequencies used in the combination
- Data weights/flux calibrator choices per project
- Completeness fit parameters for dor are only in a figure

## Analysis recipe

1. **Make matched-resolution continuum maps**: Trim Band 3 uv, taper Band 6 to Band 3 beam, clean with auto-masking, Briggs robust 0.5  
  > "Matching the spatial scale sensitivities was achieved through a combination of trimming the shortest uv-spacings and tapering the weighting of the longest uv-spacings." (2.4 Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: beam axes differ <10 per cent  
  > "Differences between the Band 6 and Band 3 beam axes were \<10 per cent (and usually much less)" (2.4 Imaging)
2. **Free-free correction to dust-only map**: Solve S_B6=S_d+S_ff and S_B3 scaled with (2+beta) and -0.1 indices algebraically per pixel  
  > "We combine the Band 3 and Band 6 images using Equation [\[eq:b6_dust_only\]](#eq:b6_dust_only) to produce dust-only emission maps for our fields." (3.1 Free-free correction)
   - software: CASA
   - parameter: beta=1.49, free-free index -0.1  
  > "We use an average value for the dust emissivity spectral index of $\beta=1.49$" (3.1 Free-free correction)
   - assumption: Only dust and free-free contribute; synchrotron neglected (<=4 per cent of Band 6 oversubtracted)  
  > "This results in, at most, four per cent of the total Band 6 flux being oversubtracted" (3.1 Free-free correction)
   - fitting: _not stated_
   - validation: Compared with ATCA 4.8/8.4 GHz extrapolated free-free: dor within 15 per cent, N159W consistent, N159E ~4x discrepant  
  > "the total free-free emission in dor matches within 15 per cent between extrapolated and decomposed estimates (0.82 Jy and 0.97 Jy, respectively)." (3.1 Free-free correction)
3. **Identify clumps**: ClumpFind lowest contour 3 rms, spacing 2 rms, fwhm=0 with minpix 56 (dor, N159W) or 61 (N159E), no background subtraction  
  > "The lowest contour was set to three times the map rms" (3.2 Clump finding); "56 for dor and N159W and 61 for N159E." (3.2 Clump finding)
   - software: Starlink Cupid ClumpFind
   - fitting: _not stated_
   - validation: visual inspection of clump regions  
  > "we inspected the clump regions identified with ClumpFind visually for each field." (3.2 Clump finding)
4. **Convert flux to total mass**: M_d = S d^2/(kappa B(T_d)), times g2d  
  > "M_{\mathrm{d}} = \frac{S d^{2}}{\kappa B(T_{\mathrm{d}})}" (3.3 Converting dust flux to total gas mass)
   - assumption: T_d=36.7 K, kappa(1.3mm)=1.16 cm2/g, g2d=500, d=50 kpc  
  > "with $T_{\mathrm{d}}=\SI{36.7}{\kelvin}$, $\kappa_{\SI{1.3}{\milli\metre}}=\SI{1.16}{\square\centi\metre\per\gram}$, and g2d$=\num{500}$." (Table of clump properties)
   - fitting: _not stated_
   - validation: _not stated_
5. **Completeness correction**: Inject 600 beam-sized Gaussian sources per mass bin, rerun ClumpFind, fit logistic function; N_corr=N/f using dor curve  
  > "We inject 600 synthetic sources per mass bin." (3.4 Completeness corrections)
   - software: ClumpFind
   - assumption: Tested only beam-size sources, likely overestimating completeness  
  > "our completeness estimates are likely overestimating the total fraction of clumps recovered for a given mass." (3.4 Completeness corrections)
   - fitting: logistic function  
  > "We fit each completeness curve with a standard logistic function" (3.4 Completeness corrections)
   - validation: _not stated_
6. **Fit cumulative mass function**: Double power law fit with Levenberg-Marquardt; weights as in Reid; Monte Carlo of mass uncertainties for errors; also lognormal  
  > "we carried out our fits with the standard nonlinear Levenberg-Marquardt least-squares minimization" (4.1 lmc clump mass function)
   - fitting: Levenberg-Marquardt least squares; MC with ×10^5 artificial mass functions, inner 68 per cent for 1sigma  
  > "From the distributions of fit parameters we used the inner 68 per cent to obtain the 1$\sigma$ uncertainties on each fit parameter" (4.1 lmc clump mass function)
   - validation: fit with M>500 only statistically indistinguishable  
  > "The best fit double power laws for the two methods end up being statistically indistinguishable" (4.1 lmc clump mass function)

## Software

- **CASA** 4.7.2 (r39762): calibration, imaging, statwt, observation simulation  
  > "carried out in casa 4.7.2[^3] (r39762) for all fields." (2.4 Imaging)
- **Starlink Cupid ClumpFind** : clump identification  
  > "we used the ClumpFind algorithm (cite: Wil1994) available in Starlink[^6] through the Cupid package" (3.2 Clump finding)
- **Astropy** : general analysis  
  > "This research made use of Astropy, a community-developed core Python package for Astronomy" (Acknowledgements)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of clumps | 32 | not stated | clumps | 3 | A total of 32 dust clumps were identified in three fields (dor, N159W and N159E) |
| alpha_low (completeness corrected) | -1.76 | +0.04/-0.05 | dimensionless | 6 | $\alpha_{\mathrm{low}} = -1.76^{+0.04}_{-0.05}$ |
| alpha_high | -3.3 | 0.2 | dimensionless | 6 | $\alpha_{\mathrm{high}} = -3.3 \pm 0.2$ |
| Break mass | 2500 | +300/-200 | Msun | 6 | a break mass of $2500^{+300}_{-200}$ M$_{\odot}$ |
| Clump mass range | 205–5740 | not stated | Msun | 4 | with masses ranging between 205 and 5740. |
| Mass sensitivity (1 sigma) dor, N159W, N159E | 45, 85, 72 | not stated | Msun | 4 | results in mass sensitivities (1$\sigma$) of 45, 85, and 72 |

## Qualitative findings

- Free-free emission is significant even at 1.3 mm and shifts the mass function to lower masses  
  > "our free-free correction is significantly larger than the random noise in each clump and systematically shifts the clump mass function to smaller masses." (3.3 Converting dust flux to total gas mass)

## Claim tuples

- H: The LMC dust clump mass function is consistent with CO-derived and Milky Way mass functions | E: Double power law fit to 32 completeness-corrected clump masses; comparison to Reid et al. 2006 and Indebetouw 2013 | R: alpha_low=-1.76, alpha_high=-3.3, break 2500 Msun; agrees with Indebetouw slope -1.9 | F: LMC low-mass index matches high-mass indices of several Milky Way regions, suggesting extension of the MW power law | **partially**
- H: Band 3 and Band 6 can be combined to remove free-free contamination | E: Algebraic decomposition tested against ATCA radio extrapolation | R: dor within 15 per cent, N159W consistent, N159E ~4x too much free-free | F: Method adopted despite N159E discrepancy | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: ClumpFind chosen for direct comparison with previous work  
  > "We chose to use this algorithm to facilitate direct comparison with previous work that also used ClumpFind." (3.2 Clump finding)
- Alternative: N113 excluded from mass function due to non-trivial free-free emission and no 3.2 mm data  
  > "We are not able to include N113 in our final mass function analysis" (3.1 Free-free correction)
- How they decided it was enough: _not stated_
- Limitation (authors): CASA <5.0 7m mosaic flux scaling issue: Band 6 overestimated ~8 per cent, Band 3 ~2 per cent, not corrected  
  > "the Band 6 flux densities are overestimated by \sim 8 per cent and Band 3 by \sim 2 per cent." (footnote 3)
- Limitation (authors): Completeness tested only for beam-sized sources  
  > "we only tested source recovery for sources that were the same size as the synthesized beam" (3.4 Completeness corrections)
- Caveat (inferred, ours): Small sample (32 clumps), mostly from one region
- Caveat (inferred, ours): Single dust temperature, opacity and g2d for all clumps
- Caveat (inferred, ours): ClumpFind-dependent masses and blended clumps
- Caveat (inferred, ours): Uncertain free-free decomposition (N159E)
- Caveat (inferred, ours): Fit weights from cumulative counts correlated

## Reproducibility

- Data public (paper): Public archival ALMA data (plus one project by the author)  
  > "We retrieved six publicly available projects from the alma archive" (2.1 Spatial and spectral setups)
- Products in archive: _not stated_
- Code: Auto-masking code listed in author's MSc thesis appendix  
  > "A full code listing of the auto-masking algorithm is available in Appendix B of Nathan Brunetti’s MSc thesis" (footnote 4)
- Missing: Line-free channel selections
- Missing: Complete cleaning parameters for all fields
- Missing: Completeness fit parameters
- Data volume (inferred): hundreds of GB raw (many mosaic pointings across 7 projects)
- Score (inferred): 3/5, Public data and a fairly detailed recipe, but heavy manual calibration/imaging with several unstated settings.
- Rediscovery candidate: no, Large multi-project reprocessing with unstated details; results numeric but recipe incomplete.

## Links

- Method: (cite: Wil1994) (ClumpFind algorithm)
- Method: (cite: Rei2006a) (mass function fitting and Monte Carlo errors)
- Companion: (cite: Ind2013) (CO and continuum study of dor with same data)
- Companion: (cite: Rei2006b) (Milky Way mass function comparison sample)
- Related: HERITAGE
- Related: NANTEN LMC survey
- Related: MAGMA

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 7,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 94,
  "stated": 63,
  "rate": 0.67
 },
 "evidence_ok": true
}
```
