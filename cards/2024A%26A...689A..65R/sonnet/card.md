# ALMA high-resolution observations unveil planet formation shaping molecular emission in the PDS 70 disk

`2024A&A...689A..65R` | Astronomy and Astrophysics 2024 | first author: Rampinelli, L. | arXiv: 2407.06272 | DOI: 10.1051/0004-6361/202449698

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: What is the molecular emission morphology and chemistry of the planet-hosting PDS 70 disk at high resolution, and does irradiation of the cavity wall or planet accretion shape it?  
  > "we suggest that the effect of the strongly irradiated cavity wall is playing an important role in shaping the molecular emission." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance ~113 pc  
  > "at a distance of $\sim$113 pc (cite: brown2018gaia) in the Upper Centaurus-Lupus subgroup." (Introduction); distance from Gaia (brown2018gaia)  
  > "at a distance of $\sim$113 pc (cite: brown2018gaia) in the Upper Centaurus-Lupus subgroup." (Introduction)

## Data provenance

- ALMA projects: 2019.1.01619.S
- bands: Band 6  
  > "we present ALMA band 6 line emission observations" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: two EBs short spacings, five EBs extended configuration  
  > "These observations consist of two execution blocks (EBs) for the short spacings, and five EBs in an extended configuration." (Observations and data reduction)
- baselines: _not stated_
- angular resolution: line beams ~0.20-0.31 arcsec; continuum 0.14x0.10 arcsec  
  > "over a synthesized beam of $0.14\ensuremath{''}\times0.10\ensuremath{''}$ (with a PA of -85.3$^\circ$)" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Program PI S. Facchini; short baselines previously shown by Facchini et al. 2021  
  > "we complement the results for the short baselines, previously shown by (cite: bib:facchini2021chemical), with the long-baseline data." (Observations and data reduction)
- Line: 12CO 2-1 (230.5380 GHz)
- Line: H2CO 3_0,3-2_0,2 (218.2221 GHz)
- Line: C2H 3_7/2,4-2_5/2,3 (262.0042 GHz)
- Line: CS 5-4 (244.9355 GHz)
- Line: SO 6_7-5_6 (261.8436 GHz)
- External data: Stellar/geometric parameters M*=0.875 Msun, i=51.7 deg, PA=160.4 deg, vsys=5.5 km/s  
  > "as they were obtained by (cite: keppler2019highly)" (Observations and data reduction) [from (cite: keppler2019highly)]
- External data: Emitting surface parameters for 12CO and 13CO  
  > "$\psi=1.61$ for (cite: law2024mapping)" (4.1 Disk-integrated spectra) [from (cite: law2024mapping)]
- External data: Line parameters (Eu, gu, Q, Aul) from CDMS  
  > "which we retrieved from the CDMS database (cite: pickett1998submillimeter; muller2001cologne)" (4.4 Disk-averaged column densities) [from (cite: pickett1998submillimeter; muller2001cologne)]

## Processing

### Calibration

- pipeline or manual: Own calibration of high-frequency setup following Law et al. 2024; phase-center realignment and self-calibration  
  > "We calibrated the high-frequency observations with the same procedure." (Observations and data reduction)
- casa version: CASA v5.8  
  > "through the `CASA` software (cite: mcmullin2007casa) `v5.8`" (Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% absolute flux calibration  
  > "without accounting for 10% absolute flux calibration uncertainties" (Observations and data reduction)
- self calibration: short baselines first, then combined; phase-only down to 120 s, final amp+phase round  
  > "for data combining short and long baselines we computed and applied a phase-only solution down to 120 s." (Observations and data reduction)

### Imaging

- task: tclean  
  > "We imaged the different lines using the `tclean` task" (Observations and data reduction)
- deconvolver: multiscale  
  > "We applied the `multiscale` deconvolver, with scales (0, 5, 10, 20, 30)pix" (Observations and data reduction)
- weighting robust: natural weighting for lines; Briggs robust 0.5 for continuum  
  > "using natural weighting." (Observations and data reduction)
- uv taper: 0.2 arcsec for faint lines  
  > "we imaged their data cubes with an additional $uv$-tapering of $0.2\ensuremath{''}$" (Observations and data reduction)
- cell size: 0.02 arcsec  
  > "pix indicates the pixel dimension ($0.02\ensuremath{''}\times0.02\ensuremath{''}$)" (Observations and data reduction)
- image size: _not stated_
- masking: 7 sigma cleaning mask (adopted); Keplerian mask tested  
  > "We performed all the following analyses on cubes imaged using the 7$\sigma$ mask." (Observations and data reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub first-order polynomial  
  > "we subtracted the continuum emission using the `uvcontsub` task with a first-order polynomial." (Observations and data reduction)
- line free channels: channels within ±15 km/s of systemic flagged around lines  
  > "After flagging the channels in the proximity of the lines detected by (cite: bib:facchini2021chemical) in a $\pm 15\,$km s$^{-1}$ range from the systemic velocity" (Observations and data reduction)
- primary beam correction: _not stated_
- array combination: short and long baselines concatenated  
  > "then the concatenated short and long baselines" (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: continuum 9.27 uJy/beam; line RMS 0.06-0.91 mJy/beam  
  > "shows a root mean square (RMS) of 9.27 $\mu$Jy." (Observations and data reduction)

### Inherited from earlier work

- Calibration of the lower-frequency setup and same procedure for high-frequency  
  > "The calibration of the lower-frequency setup is reported by (cite: law2024mapping)." (Observations and data reduction) [from (cite: law2024mapping)]
- Self-calibration solution intervals for short baselines  
  > "we used the same solution intervals as in (cite: bib:facchini2021chemical)" (Observations and data reduction) [from (cite: bib:facchini2021chemical)]
- JvM correction procedure  
  > "following (cite: czekala2021molecules), by rescaling the residual map by the $\epsilon$ factor" (Observations and data reduction) [from (cite: czekala2021molecules)]
- LTE optically thin column density method and radial profile methodology  
  > "We assumed local thermodynamic equilibrium (LTE), and optically thin emission, following (cite: bib:facchini2021chemical)." (4.4 Disk-averaged column densities) [from (cite: bib:facchini2021chemical)]

### Not stated but needed to reproduce (our reading)

- Exact line-free channels and spectral windows used for continuum subtraction
- Self-calibration solution intervals for short baselines (only referenced)
- Cleaning thresholds for final cubes and mask definitions in detail
- Observing dates, configurations, baselines, time on source
- Flux/bandpass/phase calibrators

## Analysis recipe

1. **Calibrate, self-calibrate and image cubes**: Phase-centre alignment, self-calibration on continuum, uvcontsub, tclean multiscale natural weighting with 7 sigma mask, JvM correction  
  > "We imaged the different lines using the `tclean` task, based on the `CLEAN` algorithm (cite: hogbom1974aperture), using natural weighting." (Observations and data reduction)
   - software: CASA, tclean, uvcontsub, fixvis, fixplanets
   - parameter: scales (0,5,10,20,30) pix, pix=0.02 arcsec  
  > "with scales (0, 5, 10, 20, 30)pix" (Observations and data reduction)
   - fitting: _not stated_
   - validation: Tested thresholds 2 and 3.5 sigma and two masks; consistent images  
  > "and we obtained consistent images." (Observations and data reduction)
2. **Boost and confirm faint lines**: Keplerian-shifted stacking (GoFish), matched filter (visible), uv-stacking of SO lines via cvel2+concat  
  > "We then combined the two measurement sets using the `CASA` task `concat`" (3.3 uv-stacking of SO)
   - software: GoFish, visible, CASA cvel2, concat
   - parameter: Filter mask outer radius 1 arcsec (218 GHz) and 2 arcsec (244 GHz)  
  > "an outer radius of $1^{\prime\prime}$ (218 GHz) and $2^{\prime\prime}$ (244 GHz)" (3.2 Detection of c-C3H2)
   - fitting: _not stated_
   - validation: uv-stacking tested on two detected H2CO lines  
  > "shows a test of the $uv$-stacking performed on two molecular lines of H$_2$CO that are also individually detected" (3.3 uv-stacking of SO)
3. **Moment maps, radial profiles, line fluxes**: bettermoments integrated intensity maps, GoFish radial profiles in annuli of 1/4 beam major axis; fluxes from deprojected circles; noise from 26 circles  
  > "The uncertainty is evaluated as the standard deviation of the flux measured in 26 de-projected circles" (4.3 Line fluxes)
   - software: bettermoments, GoFish
   - parameter: Integration radius 3 arcsec (12CO, 13CO), 2 arcsec others  
  > "over a de-projected circle of radius 3$^{\prime\prime}$ for the lines with the most extended emission" (4.1 Disk-integrated spectra)
   - assumption: Midplane emission except 12CO/13CO tapered power-law surface; distance 113 pc  
  > "We assumed midplane emission for all molecules except for the most elevated $^{12}$CO and $^{13}$CO emission." (4.1 Disk-integrated spectra)
   - fitting: Double Gaussian for C2H hyperfine components  
  > "we extracted the integrated flux of the individual components by fitting a double-Gaussian to the shifted-stacked spectrum" (4.3 Line fluxes)
   - validation: _not stated_
4. **Column densities and rotational diagrams**: LTE optically thin column densities at Tex=30 K (20-50 K range); rotational diagram for H2CO and c-C3H2 via emcee  
  > "We explored the posterior distribution through the MCMC method implemented in the `emcee` package (cite: foreman2013emcee), with 128 walkers, 5000 burn-in steps, and 500 steps." (4.4 Disk-averaged column densities)
   - software: emcee
   - parameter: Priors uniform Tex in (0,50) K, Nt in (1e11,1e14) cm-2 (disk-averaged); Tex (0,100) K, Nt (1e11,1e16) radial  
  > "We considered a uniform prior with $T_\mathrm{ex}\in(0,100)$ K, and $N_\mathrm{t}\in(10^{11}, 10^{16})$ cm$^{-2}$." (4.5 Radial profiles of column density)
   - assumption: LTE, optically thin, ortho-to-para ratio 3:1  
  > "assuming an ortho-to-para ratio of 3:1" (4.4 Disk-averaged column densities)
   - fitting: emcee, 128 walkers, 5000 burn-in, 500 steps, 16th/84th percentiles  
  > "Error bars refer to the 16th and 84th percentiles of the posterior distribution." (4.4 Disk-averaged column densities)
   - validation: _not stated_
5. **Emission peak radii and comparison**: Multi-Gaussian fits to radial profiles with scipy curve_fit; R68/R90 from cumulative profiles; peak-intensity profiles comparison  
  > "using `scipy.optimize.curve_fit`" (5.1 Molecular emission peaking at the cavity wall)
   - software: scipy
   - fitting: Triple Gaussian for H2CO and C2H lines, double for others  
  > "(triple for and , double for the other molecules)" (5.1 Molecular emission peaking at the cavity wall)
   - validation: Compared integrated and peak intensity profile peaks  
  > "the peak positions are consistent within the error bars for most of the molecules" (5.1 Molecular emission peaking at the cavity wall)

## Software

- **CASA** 5.8: calibration, imaging, cvel2, concat  
  > "through the `CASA` software (cite: mcmullin2007casa) `v5.8`" (Observations and data reduction)
- **GoFish** : Keplerian stacking, spectra, radial profiles  
  > "This method has been implemented in the `GoFish` package (cite: teague2019gofish)" (3 Boosting faint lines detection)
- **visible** : matched filter  
  > "using the `visible` package (cite: loomis2018visible)" (3.2 Detection of c-C3H2)
- **bettermoments** : integrated and peak intensity maps  
  > "with the `bettermoments` tool (cite: teague2019bettermoments)" (4.2 Integrated intensity maps and radial profiles)
- **keplerian_mask.py** : Keplerian masks  
  > "using the `keplerian`$\_$`mask.py` tool by (cite: kepmask)" (Observations and data reduction)
- **emcee** : rotational diagram posteriors  
  > "the MCMC method implemented in the `emcee` package" (4.4 Disk-averaged column densities)
- **scipy** : Gaussian fits to radial profiles  
  > "using `scipy.optimize.curve_fit`" (5.1 Molecular emission peaking at the cavity wall)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum total flux density at 252.8 GHz | 68.42 | 0.10 (excl. 10% calibration) | mJy | 1 | The total flux density of the disk at the weighted frequency of 252.8 GHz is $68.42\pm0.10\,$mJy |
| c-C3H2 rotational diagram Tex | 15 | ±4 | K | 4 | $T_\mathrm{ex}= (15 \pm 4)$ K and $N_\mathrm{t}= (6.8 \pm 1.8)\times10^{12}$ cm$^{-2}$ |
| c-C3H2 total column density | 6.8e12 | ±1.8e12 | cm-2 | 4 | $N_\mathrm{t}= (6.8 \pm 1.8)\times10^{12}$ cm$^{-2}$ |
| H2CO rotational diagram Tex | 25 | ±2 | K | 4 | $T_\mathrm{ex}=(25 \pm 2)$ K and $N_\mathrm{t}=(2.0\pm 0.2)\times10^{13}$ cm$^{-2}$ |
| H2CO total column density | 2.0e13 | ±0.2e13 | cm-2 | 4 | $N_\mathrm{t}=(2.0\pm 0.2)\times10^{13}$ cm$^{-2}$ |
| SO column density upper limit (uv-stacked) | <2.7e12 | not stated | cm-2 | 4 | $N_\mathrm{t}<2.7\times10^{12}$ cm$^{-2}$, assuming $T_\mathrm{ex}=30$ K |
| CS/SO lower limit | 0.8-1.1 | not stated | dimensionless | 4 | we obtained a lower limit on the average CS/SO ratio between 0.8 and 1.1 |
| c-C3H2 244 GHz detection matched-filter peak | 5.7 | not stated | sigma | 2 | with a peak filter response of 5.7$\sigma$ (for the 244 GHz line) and of 4.2$\sigma$ (for the 218 GHz lines) |
| H2CO 3_2,1-2_2,0 asymmetry significance | 2.5 | not stated | sigma | 5 | the statistical significance of the spectral difference is low (2.5$\sigma$) |

## Qualitative findings

- Most molecules peak inside the mm continuum ring, linked to the irradiated cavity wall  
  > "Most of the molecules show a peak in the emission inside the millimeter dust ring" (Conclusions)
- First detection of c-C3H2 218 GHz lines in PDS 70; SO undetected  
  > "We present the first detection of the 218 GHz lines in the PDS 70 disk, leveraging boosting techniques;" (Conclusions)

## Claim tuples

- H: Does cavity-wall irradiation shape molecular emission in PDS 70? | E: Radial peak positions of integrated and peak intensity profiles compared with continuum and scattered light | R: Most tracers peak inside the mm ring, correlating with NIR scattered light peak | F: Efficient irradiation of the cavity wall enhances emission of specific tracers | **partially**
- H: Is the outer disk O-depleted (C/O>1)? | E: Non-detection of SO, CH3OH, C-rich molecule detections, CS/SO lower limit | R: CS/SO lower limit 0.8-1.1 | F: Outer disk gas may have C/O>1 | **partially**
- H: Do planets leave accretion signatures in high-energy lines? | E: Azimuthal asymmetry of H2CO 3_2,1-2_2,0 and rotational diagram at two positions | R: 2.5 sigma asymmetry, Tex ~42 K vs ~22 K consistent within errors | F: Possible but not significant accretion heating near PDS 70b | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Boosting in image and uv plane to detect faint lines  
  > "we applied boosting techniques both in the image and in the visibility plane, to the weak lines included in the dataset" (3 Boosting faint lines detection)
- Alternative: Thermal desorption of H2CO from ice deemed unlikely at r>0.4 arcsec; grain-surface pathway not ruled out  
  > "thermal-desorption from icy grains is an unlikely process to release" (5.4 On the origin of the observed H2CO emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Radial profile uncertainties may be underestimated inside the beam  
  > "The uncertainties may be underestimated, especially in the inner regions, inside the beam FWHM" (4.2 Integrated intensity maps and radial profiles)
- Caveat (inferred, ours): Excitation temperature of 30 K assumed for most column densities
- Caveat (inferred, ours): Low significance of several faint-line detections and asymmetry
- Caveat (inferred, ours): Optically thin LTE assumptions
- Caveat (inferred, ours): c-C3H2 rotational diagram assumes uniform temperature despite different emitting regions

## Reproducibility

- Data public (paper): Data from ALMA program 2019.1.01619.S acknowledged; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.01619.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrator details and observing dates
- Missing: Self-calibration intervals for short baselines
- Missing: Exact clean thresholds
- Data volume (inferred): Large (~hundreds of GB; seven EBs, two spectral setups)
- Score (inferred): 6/5, Recipe largely described with software and parameters, but key calibration details defer to companion papers.
- Rediscovery candidate: no, Calibration details inherited and several steps (self-cal intervals) unstated; large data volume.

## Links

- Method: (cite: bib:facchini2021chemical) (Earlier chemical inventory with methodology followed)
- Method: (cite: law2024mapping) (Calibration of lower-frequency setup and emitting surfaces)
- Method: (cite: czekala2021molecules) (JvM correction)
- Companion: (cite: law2024mapping) (Companion study of vertical gas structure of PDS 70 from same program)
- Related: MAPS Large Program

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 58,
  "rate": 0.707
 },
 "evidence_ok": true
}
```
