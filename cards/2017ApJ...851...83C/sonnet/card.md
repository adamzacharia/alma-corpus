# Protoplanetary Disks in ρ Ophiuchus as Seen from ALMA

`2017ApJ...851...83C` | The Astrophysical Journal 2017 | first author: Cox, Erin G. | arXiv: 1711.03974 | DOI: 10.3847/1538-4357/aa97e2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the 870 um dust continuum fluxes and radii of disks in rho Oph, how do they differ between singles, binaries, triples and transition disks and compare with Taurus, and are binary disks tidally truncated?  
  > "We present flux and radius distributions for these systems; in particular, this is the first presentation of a reasonably complete probability distribution of disk radii at millimeter-wavelengths." (abstract)
- Target **49 Spitzer c2d-selected YSO systems in rho Ophiuchus (ROph 1-50)**: coordinates see Table of derived positions (e.g. 16:21:31.923 -23:01:40.761 for ROph1)  
  > "it is relatively close ($d \sim 137$ pc; (cite: or17))" (1 Introduction); z/distance 137 pc  
  > "it is relatively close ($d \sim 137$ pc; (cite: or17))" (1 Introduction); distance from (cite: or17)  
  > "it is relatively close ($d \sim 137$ pc; (cite: or17))" (1 Introduction)

## Data provenance

- ALMA projects: 2013.1.00157.S
- bands: Band 7 (870 um)  
  > "The ALMA Band 7 observations were taken under proposal 2013.1.00157.S using a continuum only setup" (3 Observations and Data Reduction)
- frequencies and spectral setup: 4 continuum bands centered at 336.5, 338.4, 348.5, 350.5 GHz  
  > "the 4 continuum bands were centered at 336.5, 338.4, 348.5, and 350.5 GHz" (3 Observations and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C34-1/(2) and C34-7/(6)  
  > "in ALMA configuration C34-1/(2) for $\sim$30 minutes of total time" (3 Observations and Data Reduction)
- baselines: 14-356.3 m (C34-1/(2)); 42-1574 m (C34-7/(6))  
  > "The C34-7/(6) configuration baselines ranges from 42 to 1574 meters with typical recoverable scale of 2.6$''$." (3 Observations and Data Reduction)
- angular resolution: 0.21'' by 0.18'' (combined, natural weighting)  
  > "natural weighting to produce a typical resolution of 0.21$\ensuremath{''}$ by 0.18$''$" (3 Observations and Data Reduction)
- max recoverable scale: 8.4'' (C34-1) and 2.6'' (C34-7)  
  > "baselines ranged from 14 to 356.3 meters with typical recoverable scale of 8.4$''$" (3 Observations and Data Reduction)
- sensitivity: sigma ~ 0.2 mJy  
  > "high sensitivity ($\sigma \sim 0.2$ mJy)" (abstract)
- time on source: ~12 s per source (C34-1) and ~24 s per source (C34-7)  
  > "which was about 24 seconds of integration time on each source" (3 Observations and Data Reduction)
- observing dates: 2015 April 4 and 2015 July 24  
  > "The lower resolution observations were obtained on 2015 April, 4" (3 Observations and Data Reduction)
- pi or archival as stated: _not stated_
- Other facility **Spitzer c2d**: YSO catalog used for sample selection  
  > "we used the Spitzer c2d catalog of YSO candidate sources in $\rho$ Ophiuchus (cite: ev03)" (2 Sample Selection)
- Other facility **Herschel PACS**: 70 and 100 um maps to verify far-IR emission  
  > "These sources were then compared to Herschel PAC continuum maps at 70 and 100 $\mu$m" (2 Sample Selection)
- External data: Multiplicity data for targets  
  > "Reference key: \[a\] (cite: ra05), \[b\] (cite: du04) , \[c\] (cite: ch15), \[d\] (cite: rr16)" (Table 1) [from (cite: ra05); (cite: du04); (cite: ch15); (cite: rr16)]
- External data: Taurus comparison sample from Spitzer survey plus literature (sub)mm fluxes  
  > "we used the results of the *Spitzer* survey performed by (cite: re10)." (6.1 Comparison with Taurus) [from (cite: re10)]
- External data: Transition disk classification from IR colors  
  > "were identified by (cite: ci10) to be candidate transitional disks on the basis of *Spitzer* near-/mid-infrared colors" (2 Sample Selection) [from (cite: ci10); (cite: re15)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "using the 4.7.0 CASA and ALMA pipeline package" (3 Observations and Data Reduction)
- casa version: CASA 4.7.0  
  > "using the 4.7.0 CASA and ALMA pipeline package" (3 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan (bandpass/phase: J1517-2422, J1625-2527)  
  > "and Titan was used for flux calibration" (3 Observations and Data Reduction)
- flux scale uncertainty: ~10%  
  > "we assume an absolute flux calibration uncertainty of $\sim$10%, but only statistical uncertainties are considered." (3 Observations and Data Reduction)
- self calibration: Phase-only selfcal for C34-1/(2) sources with >=10 sigma detections; not used for C34-7/(6)  
  > "we performed a phase only selfcal over the integration time for the sources with $\geq$10$\sigma$ detections" (3 Observations and Data Reduction)

### Imaging

- task: CLEAN in CASA  
  > "we imaged the data using the `CLEAN` task in CASA" (3 Observations and Data Reduction)
- deconvolver: standard CLEAN for compact sources; multi-scale CLEAN for extended disks and all transition disks  
  > "we used the multi-scale version of the algorithm to produce images of some of the disks" (3 Observations and Data Reduction)
- weighting robust: natural weighting  
  > "The data were imaged with natural weighting" (3 Observations and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: two configurations' datasets combined after checking flux consistency  
  > "we combined the two datasets and used the combined datasets to produce the images analyzed in this work" (3 Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 0.21'' x 0.18''  
  > "typical resolution of 0.21$\ensuremath{''}$ by 0.18$''$" (3 Observations and Data Reduction)
- final rms: _not stated_

### Inherited from earlier work

- Statistical method to estimate true a and e from projected separation  
  > "we implement a statistical method to estimate the true orbital elements $a$ and $e$ based on the projected separation of the two stars; for details, see (cite: ha12)." (6.2 Disks in Binary Systems and Tidal Truncation) [from (cite: ha12)]
- Deprojection and azimuthal-profile procedure for gap structure  
  > "we follow the procedure used by (cite: al15) to study the gap structure in the millimeter emission of HL Tau" (6.3 Transition and Gapped Disks) [from (cite: al15)]
- Tidal truncation analytic model  
  > "We use the analytic model described in (cite: pi05) to estimate" (6.2 Disks in Binary Systems and Tidal Truncation) [from (cite: pi05)]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, niter and multiscale scale values
- CASA self-calibration solint and reference antenna details
- Which sources were imaged multi-scale individually
- Details of how disk radius is defined from imfit (e.g. deconvolved FWHM vs. other)
- Taurus 870 um flux inference details and source list
- How 6/49 planet-forming fraction confidence interval was computed
- Data volume and mapping of fields to pipeline products

## Analysis recipe

1. **Calibrate and image the data**: ALMA pipeline calibration per configuration, split fields, phase-only selfcal for C34-1, combine, CLEAN (multi-scale for extended)  
  > "These calibrations are performed separately for each of the two observations and each science target field was subsequently split out of its parent dataset." (3 Observations and Data Reduction)
   - software: CASA
   - parameter: natural weighting  
  > "The data were imaged with natural weighting" (3 Observations and Data Reduction)
   - fitting: _not stated_
   - validation: Fluxes from two configurations checked for consistency; residuals dominated by Gaussian noise  
  > "The use of the multi-scale `CLEAN` algorithm yielded residual maps that were dominated by Gaussian noise." (3 Observations and Data Reduction)
2. **Measure disk sizes and fluxes**: Gaussian fit in the image plane  
  > "were estimated by fitting a gaussian in the image plane using the CASA task `imfit`." (4 Results)
   - software: CASA imfit
   - assumption: distance 137 pc to convert to radii  
  > "We used a distance of 137 pc to compute the radius" (Table 3)
   - fitting: imfit Gaussian  
  > "The disk sizes and position angles, as well as the peak and integrated fluxes, were estimated by fitting a gaussian in the image plane using the CASA task `imfit`." (Results)
   - validation: _not stated_
3. **Derive disk dust+gas masses**: Optically thin isothermal: M = F d^2 / (kappa B(Td))  
  > "Disk masses were estimated from the integrated fluxes by assuming optically thin emission and an isothermal disk with a dust temperature of $T_d = 20$ K" (4 Results)
   - assumption: Td = 20 K, kappa = 0.03 cm2/g at 870 um (Hildebrand), gas-to-dust 100:1, d=137 pc  
  > "$\kappa_{\nu} = 0.03$ cm$^2$/g is the total opacity at 870 $\mu$m assuming a (cite: hi83) dust opacity and a 100:1 gas-to-dust ratio" (4 Results)
   - fitting: _not stated_
   - validation: Caveat that mass is only an estimate  
  > "An important caveat here is that this mass is calculation is only an estimate at best." (4 Results)
4. **Compare sub-population flux and radius distributions**: Kaplan-Meier estimators with upper limits for flux (detections only for radius) and pairwise log-rank test; significance p<~0.05  
  > "we use the non-parametric log-rank test to determine whether or not it is likely that the two cumulative distributions in flux or radius are different" (4 Results)
   - software: lifelines
   - parameter: 3 sigma map value used as upper limit for non-detections  
  > "in the case of a non-detection, the 3$\sigma$ value of the map was used as an upper limit for fluxes" (4 Results)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with Taurus**: Same KM method on Taurus sample from Rebull et al. 2010 with 870 um fluxes inferred from spectral index (assume 3 if unavailable)  
  > "where it was not available, we assumed that the intrinsic spectral index was 3." (6.1 Comparison with Taurus)
   - software: lifelines
   - fitting: _not stated_
   - validation: _not stated_
6. **Test tidal truncation of binary disks**: Pichardo et al. 2005 truncation radius with statistical deprojection of a, e from projected separation, uniform e in [0,1], mass ratio q=1  
  > "we choose a uniform distribution picking $e$ between 0 and 1 for this." (6.2 Disks in Binary Systems and Tidal Truncation)
   - assumption: mass ratio unity  
  > "as well as the mass ratio $q$, which we assume to be unity" (6.2 Disks in Binary Systems and Tidal Truncation)
   - fitting: _not stated_
   - validation: _not stated_
7. **Search for gaps via radial profiles**: Deproject using fit center, inclination and PA; azimuthally average surface brightness  
  > "deprojected each image using the fit disk center, inclination, and position angle, and produce azimuthally averaged surface brightness profiles." (6.3 Transition and Gapped Disks)
   - fitting: _not stated_
   - validation: Profiles constructed for every source to check for missed gaps  
  > "we constructed these deprojected profiles for each source in our sample." (6.3 Transition and Gapped Disks)

## Software

- **CASA** 4.7.0: Calibration with pipeline, selfcal, CLEAN imaging, imfit  
  > "using the 4.7.0 CASA and ALMA pipeline package" (3 Observations and Data Reduction)
- **lifelines** v0.11.1: Kaplan-Meier estimators  
  > "implementation of the Kaplan-Meier (KM) product estimator in the `lifelines` Python package (cite: dp17)" (4 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Singles vs binaries flux p-value | 0.06946 | not stated | dimensionless | 4 | $p_{flux}=0.06946$ and $p_{radius}=0.01766$ |
| Singles vs binaries (no circumbinary) flux p-value | 0.00876 | not stated | dimensionless | 4 | we get $p_{flux}=0.00876$ and $p_{radius}=0.00075$ |
| Median flux singles | 46.3 | not stated | mJy | 4 | / Singles / 46.3 / 17.9 / |
| Median flux binaries | 27.74 | not stated | mJy | 4 | / Binaries / 27.74 / 7.1 / |
| Median flux transition disks | 262 | not stated | mJy | 4 | / Transition Disks / 262 / 62.34 / |
| Singles Oph vs Taurus flux p-value | 0.00434 | not stated | dimensionless | 5 | /           Singles /           0.00434 / |
| Fraction of disks with gaps/cavities | 0.122 (6 of 49) | 95% CI 0.031<f<0.21 | dimensionless | 7 | This yields an estimate of $f = 0.122$ with a 95% confidence interval of $0.031 < f < 0.21$. |
| Gap radii in ROph 9 and ROph 38 | ~65 and ~170 | not stated | au | 7 | there are obvious deficits of emission observed at approximately 65 and 170 au, respectively. |

## Qualitative findings

- Disks in binaries are smaller and fainter than those around single stars and too small to be tidally truncated  
  > "We find that disks in binaries are both significantly smaller and have much less flux than their counterparts around isolated stars." (abstract)
- ROph 38 (WSB 82) newly identified as transition disk with mm cavity and gap  
  > "one of which is a newly identified transition disk with no signature of a dip in infrared excess in extant observations" (abstract)

## Claim tuples

- H: Disks in binaries differ in flux and radius from single-star disks | E: KM estimators and log-rank tests on singles vs binaries | R: p_flux=0.06946, p_radius=0.01766; without circumbinary disks 0.00876 and 0.00075 | F: Binary disks are smaller and fainter | **supported**
- H: Binary disk sizes are set by tidal truncation | E: Pichardo et al. truncation radii from statistical orbital elements | R: All sources except two upper limits lie well below equilibrium line | F: Disks too small to be affected by truncation; explained by gas/dust extent or eccentricity | **partially**
- H: Oph disks differ from Taurus | E: KM comparisons with Taurus sample | R: Singles median 31 vs 57 mJy, p=0.00282 | F: Oph singles dimmer, possibly due to environment | **partially**
- H: Gaps/cavities exist in the sample | E: Deprojected radial profiles | R: Clear gaps in ROph 9 and 38, candidate in ROph 8 | F: 6/49 disks show signs of planet formation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: KM estimator accounts for non-detections via upper limits  
  > "it has the advantage of being able to account for the non-detections in our sample by incorporating $\sigma$ upper limits when appropriate" (4 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Unresolved or unknown multiplicity may bias results; gas and dust extents differ  
  > "One caveat to keep in mind for this survey is the impact of unresolved (or unknown) multiplicity in the targets." (2 Sample Selection)
- Caveat (inferred, ours): Disk radius from a Gaussian fit is not a standard physical radius
- Caveat (inferred, ours): Small numbers of transition disks and class I sources
- Caveat (inferred, ours): Only statistical uncertainties; mass calculation assumes Td=20 K for all
- Caveat (inferred, ours): Taurus comparison involves heterogeneous flux extrapolation

## Reproducibility

- Data public (paper): Data from ALMA proposal 2013.1.00157.S; public status not explicitly stated  
  > "The ALMA Band 7 observations were taken under proposal 2013.1.00157.S" (3 Observations and Data Reduction)
- Products in archive: _not stated_
- Missing: CLEAN parameters and masks
- Missing: multiscale scales
- Missing: Taurus sample list and fluxes
- Missing: KM treatment details
- Data volume (inferred): ~50-100 GB raw for two short snapshot EBs
- Score (inferred): 3/5, Data are single project and methods are simple, but CLEAN settings and Taurus comparison details are missing.
- Rediscovery candidate: yes, Single ALMA project, simple imfit fluxes and tabulated numeric results can be checked.

## Links

- Method: (cite: ha12) (Binary truncation statistical method)
- Method: (cite: pi05) (Tidal truncation model)
- Companion: (cite: an17) (Similar ALMA survey in sigma Ori)
- Related: Spitzer c2d
- Related: Taurus survey comparison

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 82,
  "stated": 54,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
