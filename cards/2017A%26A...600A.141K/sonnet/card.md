# Resolving the fragmentation of high line-mass filaments with ALMA: the integral shaped filament in Orion A

`2017A&A...600A.141K` | Astronomy and Astrophysics 2017 | first author: Kainulainen, J. | arXiv: 1603.05688 | DOI: 10.1051/0004-6361/201628481

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the fragmentation length scales of the Orion A integral shaped filament, is there a preferred fragmentation scale or grouping of cores, and how do these relate to the young stellar population?  
  > "Our specific goals in this paper are to determine the fragmentation length scales of the filament, to look for preferential fragmentation scales and grouping of fragments" (Introduction)
- Target **Integral shaped filament (ISF), Orion A (OMC-2/3 section)**: coordinates not stated (core positions near RA 05:35, Dec -05:03 to -05:15 in Table)  
  > "At the distance of 420 pc (cite: sch14), the ISF is the nearest highly super-critical filament" (Introduction); z/distance 420 pc  
  > "At the distance of 420 pc (cite: sch14), the ISF is the nearest highly super-critical filament" (Introduction); distance from Schlafly et al. 2014 (cite: sch14)  
  > "At the distance of 420 pc (cite: sch14), the ISF is the nearest highly super-critical filament" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01114.S
- bands: 3 mm continuum (plus C18O line, not used)  
  > "In this paper we only use the continuum emission data." (Observations and methods)
- frequencies and spectral setup: Three 2 GHz sidebands at 107.29217, 96.97848, 98.97848 GHz; fourth at C18O 109.749042 GHz  
  > "three of the four correlator sidebands, each 2 GHz wide, were set to central frequencies of 107.29217 GHz, 96.97848 GHz, and 98.97848 GHz." (Observations and methods)
- continuum bandwidth: 11.1 GHz total used in imaging  
  > "The total bandwidth used in the imaging was 11.1 GHz (including two polarizations)." (Observations and methods)
- arrays: 12-m array and 7-m ACA  
  > "Both the 12-m and the 7-m (Atacama Compact Array; ACA) arrays were employed." (Observations and methods)
- configurations: 12-m in compact configuration; mosaics of 127 (12-m) and 42 (7-m) pointings  
  > "the 12-m array observations in a compact configuration on 16th January 2015." (Observations and methods); "No. of mosaic points | 127 | 42" (Table 1)
- baselines: 12-m 15.1-348.5 m; 7-m 8-48.9 m  
  > "Baseline length range | 15.1-348.5 m | 8-48.9 m" (Table 1)
- angular resolution: Combined beam 3.75'' x 2.27'' (PA 71 deg)  
  > "The final synthesised beam size full width half max, $FWHM$) of the combined 7-m and 12-m array map is $3.75\ensuremath{''} \times 2.27\ensuremath{''}$" (Observations and methods)
- max recoverable scale: 25'' (12-m), 42'' (7-m)  
  > "Max recoverable scale$^{a}$ | 25$''$ | 42$''$" (Table 1)
- sensitivity: rms 0.23 mJy/beam combined (0.14 12-m, 2.3 7-m)  
  > "The root-mean-square ($rms$) noise measured from an approximately emission free area is $\sigma_\mathrm{rms}$=0.23 mJy beam$^{-1}$." (Observations and methods)
- time on source: 78 min (12-m), 3h 44 min (7-m)  
  > "On-source time | 78 min | 3h 44 min" (Table 1)
- observing dates: 7-m 16 Aug 2014; 12-m 16 Jan 2015  
  > "The 7-m array observations were conducted on 16th August 2014 and the 12-m array observations in a compact configuration on 16th January 2015." (Observations and methods)
- pi or archival as stated: Cycle 2, PI Kainulainen  
  > "ESO Project ID 2013.1.01114.S, PI Kainulainen" (Observations and methods)
- Line: C18O not stated (observed but not used) (109.749042 GHz)
- Other facility **Herschel**: Dust column density map of Orion A, 18'' resolution  
  > "The map has the spatial resolution of $FWHM=18\ensuremath{''}$ (7 600 AU)." (Observations and methods)
- Other facility **Spitzer / HOPS**: Catalog of protostars and stars with disks  
  > "we also use the catalog of *Spitzer*-identified protostars and stars with disks from the HOPS survey" (Observations and methods)
- External data: Herschel column density map of Orion A  
  > "We refer to (cite: stu15) for the details of the map." (Observations and methods) [from (cite: stu15)]
- External data: Protostar catalog  
  > "(cite: meg12) for the disks and (cite: fur16) for the protostars" (Observations and methods) [from (cite: fur16); disks (cite: meg12)]
- External data: ISF density profile and line-mass used in model comparison  
  > "(cite: stu15prep) have evaluated the (cylindric) density profile of the ISF to be 17 M$_\odot$ pc$^{-3} (r / \mathrm{pc})^{-13/8}$" (4.3 Comparison against gravitational fragmentation models) [from (cite: stu15prep)]

## Processing

### Calibration

- pipeline or manual: 12-m: ALMA pipeline; 7-m: ARC calibration scripts  
  > "The 12-m array data were calibrated using the ALMA calibration pipeline (part of casa 4.5.0)." (Observations and methods)
- casa version: CASA 4.5.0  
  > "Both the 7-m and 12-m array data were calibrated and imaged using the casa version 4.5.0." (Observations and methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Uranus (12-m); Uranus or J0423-013 (7-m)  
  > "J0423-0120 and Uranus were observed in the beginning of the measurement set for bandbass and flux calibration, respectively." (Observations and methods)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean, 7-m and 12-m separately and jointly  
  > "We imaged the 7-m and 12-m array data both separately and simultaneously using the clean task of casa." (Observations and methods)
- deconvolver: _not stated_
- weighting robust: natural  
  > "During cleaning, we used the ‘natural’ weighting scheme." (Observations and methods)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: Clean without mask first; then boxes around significant emission, re-clean  
  > "the resulting image of this first cleaning was used to make the cleaning mask; this was done by setting boxes around significant emission structures in the cleaned map." (Observations and methods)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: Excluded band edges and channels with prominent emission lines (not listed)  
  > "We excluded from the cleaning the channels at the edges of the bands and the channels coinciding with prominent emission lines." (Observations and methods)
- primary beam correction: _not stated_
- array combination: Joint imaging with weights adjusted by statwt  
  > "the relative weights of the 7-m and 12-m array visibility data were adjusted with the casa task statwt." (Observations and methods)
- smoothing: _not stated_
- final beam: 3.75'' x 2.27'', PA 71 deg  
  > "$3.75\ensuremath{''} \times 2.27\ensuremath{''}$ ($\sim$1 600 AU $\times$ 950 AU) and the beam position angle 71$^\circ$" (Observations and methods)
- final rms: 0.23 mJy/beam  
  > "$\sigma_\mathrm{rms}$=0.23 mJy beam$^{-1}$" (Observations and methods)

### Inherited from earlier work

- Herschel column density map details  
  > "We refer to (cite: stu15) for the details of the map." (Observations and methods) [from (cite: stu15)]
- Dust opacity law with beta=1.5  
  > "where $\beta$ is taken to be 1.5 (cite: sad16)" (Observations and methods) [from (cite: sad16)]
- Two-point correlation estimator  
  > "We adopt the (cite: lan93) estimator for the two-point correlation function" (3.3 Two-point correlation function) [from (cite: lan93)]

### Not stated but needed to reproduce (our reading)

- Clean threshold, niter, cell size, image size and mosaic gridding
- Exact channels excluded from continuum
- Mask box coordinates
- Exact gaussclumps parameter file beyond Thresh and filter width (e.g. other FWHMBeam, Rms, fit-failure settings)
- Whether primary-beam correction was applied
- Exact HOPS catalog versions (Furlan 2016 was submitted)
- Area used for random placement and boundary treatment in the Monte Carlo
- Random seed

## Analysis recipe

1. **Image continuum**: Joint 7-m+12-m mosaic cleaning with natural weighting and box masks  
  > "We imaged the 7-m and 12-m array data both separately and simultaneously using the clean task of casa." (Observations and methods)
   - software: CASA
   - parameter: statwt weight adjustment; 11.1 GHz bandwidth  
  > "The total bandwidth used in the imaging was 11.1 GHz (including two polarizations)." (Observations and methods)
   - fitting: _not stated_
   - validation: Fourier amplitude spectrum and scale-dependent rms of the map  
  > "We further investigate the sensitivity of the ALMA map by inspecting the amplitudes of its Fourier modes." (Observations and methods)
2. **Identify dense cores**: 2D Gaussian fitting with gaussclumps after median-filter background subtraction  
  > "gaussclumps identifies cores by fitting 2-dimensional Gaussians at the locations defined by the highest pixel values in the map." (2.1 Identification of dense cores)
   - software: gaussclumps (starlink/cupid 2.0)
   - parameter: Threshold 3 x rms = 0.23 mJy/beam rms; filter width 10''  
  > "We chose to use the threshold three times the $rms$ noise calculated from an emission free region in the ALMA+ACA map" (2.1 Identification of dense cores); "The filter width for the background subtraction was chosen to be 10$\ensuremath{''}$" (2.1 Identification of dense cores)
   - fitting: Gaussian profile fit; poorly fitted structures rejected  
  > "if the structure profile is not well fitted by a Gaussian, the core is rejected." (2.1 Identification of dense cores)
   - validation: Filter widths 7.5''-15'' tested; conclusions unchanged  
  > "between 7.5$\ensuremath{''}$-15$\ensuremath{''}$ the choice of the width does not change the conclusions based on the two-point correlation function" (2.1 Identification of dense cores)
3. **Classify cores as protostellar or starless**: Cross-match core centroids with HOPS protostars and disks within 2''; reclassify four disk matches as protostars based on chance-alignment probability  
  > "The objects were considered coincident if their centroids were within a $2\ensuremath{''}$ radius of the protostars or disks." (2.1 Identification of dense cores)
   - fitting: Binomial chance-alignment estimate  
  > "results in $P$(0)=83% and the expected value of $N$ of 0.2." (2.1 Identification of dense cores)
   - validation: Robustness test excluding seven weakest starless cores  
  > "We conclude that the results based on two-point correlation analysis are not strongly affected by possible misclassifications of low-intensity starless cores." (On the robustness of the two-point correlation analysis)
4. **Estimate core masses**: Optically thin dust emission M = F d^2 / (B(T) kappa)  
  > "M = \frac{F_\nu d^2}{B_\nu (T)\kappa_\nu}" (2.1 Identification of dense cores)
   - parameter: T = 20 K; d = 420 pc; kappa = 0.1 (nu/1000 GHz)^1.5 cm2/g  
  > "For the temperature, we adopt 20 K" (2.1 Identification of dense cores)
   - assumption: Gas-to-dust ratio 100; kappa_100GHz = 0.0032 cm2/g  
  > "This expression assumes the gas-to-dust ratio of 100." (2.1 Identification of dense cores)
   - fitting: _not stated_
   - validation: _not stated_
5. **Nearest-neighbour separation statistics**: Mean, median and CDFs of projected nearest neighbour separations for cores, protostars and disks  
  > "We report the mean and median nearest neighbour separation, $d_\mathrm{nn}$, for all different object classes in Table [2](#tab:objects)." (3.2 Nearest neighbour separations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Two-point correlation function of separations**: Landy-Szalay estimator with Monte Carlo random samples and Gaussian density estimator  
  > "We calculate all separation distributions using a Gaussian density estimator that has a $FWHM=5\ensuremath{''}$ (2 100 AU)." (3.3 Two-point correlation function)
   - parameter: 10 000 random realisations with N=43 points; smoothing FWHM 5'' (20'' for large scales)  
  > "This is repeated 10 000 times (and the resulting distribution is divided by 10 0000) to obtain adequate statistics." (3.3 Two-point correlation function)
   - fitting: Bootstrapping (10 000 resamples); quartiles 25% and 75% as uncertainty  
  > "For each $r$, we compute the 25% and 75% quartiles of these functions and use the quartiles as uncertainty estimates" (3.3 Two-point correlation function)
   - validation: FWHM choice tested; simulated periodic groups  
  > "We construct a simplistic model in which groups of cores are located along a line with a constant separation." (Two-point correlation analysis at large scales)
7. **Large-scale grouping and model comparison**: Core surface density map smoothed with 40'' Gaussian kernel; compared with Herschel peaks; Jeans and cylindrical fragmentation scales computed  
  > "derived using a Gaussian smoothing kernel that has the $FWHM$ of 40$\ensuremath{''}$ (17  000 AU)" (4.1 The fragmentation picture)
   - parameter: T = 20 K; density 1e5 to 2e5 cm-3  
  > "To evaluate this, we adopt the temperature of 20 K as before." (4.3 Comparison against gravitational fragmentation models)
   - assumption: Inclination angle of zero; spherical structures for density  
  > "We also have assumed an inclination angle of zero throughout this paper." (4.3 Comparison against gravitational fragmentation models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.0: Calibration and imaging (clean, statwt)  
  > "Both the 7-m and 12-m array data were calibrated and imaged using the casa version 4.5.0." (Observations and methods)
- **gaussclumps (starlink/cupid)** 2.0: Core identification  
  > "we chose to use the implementation of gaussclumps in the starlink/cupid package version 2.0" (2.1 Identification of dense cores)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of dense cores | 43 | not stated | dimensionless | 2 | Running gaussclumps resulted in detection of 43 compact objects from the ALMA map. |
| Protostellar / starless cores | 26 / 17 | not stated | dimensionless | 3 | our dense core catalog consists of 26 protostellar cores and 17 starless cores. |
| Core mass range | 0.2-2.6 | not stated | Msun | 4 | The masses of the cores span 0.2-2.6 M$_\odot$ |
| Mean nearest neighbour separation, all cores | 7.7 (median 4.2) | not stated | kAU | 5 | All dense cores / 43 / 7.7 / 4.2 / 0.9 |
| Grouping scale of cores (significant / strong) | <17 000 / <6 000 | not stated | AU | 6 | it shows significant grouping below 17 000 AU and strong grouping below $\sim$6 000 AU. |
| Group separation (six largest groups) | 62 000 | 19 000 | AU | 7 | 62 000 $\pm$ 19 000 AU when considering the six largest groups |
| Herschel column density peak mean separation | 56 000 | 14 000 | AU | 7 | mean separation of 56 000 $\pm$ 14 000 AU |
| Jeans fragmentation scale | ~10 000 (7 000 from Herschel density) | not stated | AU | 7 | the density of $\sim10^5$ cm$^{-3}$ and the fragmentation scale of $\sim$10 000 AU follows. |
| Cylindrical fragmentation scale | ~40 000 (30 000 from Herschel density) | not stated | AU | 7 | the $FWHM$$\approx$0.06 pc follows, yielding the fragmentation scale of $\sim$40 000 AU. |

## Qualitative findings

- Stars with disks are consistent with random distribution, unlike cores and protostars  
  > "The distribution of stars with disks is in agreement with random distribution within the ALMA-covered region" (Conclusions)

## Claim tuples

- H: Does the ISF have a preferred nearest-neighbour fragmentation scale? | E: Nearest-neighbour separation CDFs of 43 ALMA cores | R: Short separations increase down to resolution limit 1 200 AU | F: No preferential separation; hierarchical scale-dependent fragmentation | **supported**
- H: Are cores grouped, and do starless and protostellar cores differ? | E: Two-point correlation function with bootstrap errors | R: Significant grouping below 17 000 AU, strong below 6 000 AU, driven by starless cores | F: Two-mode hierarchical fragmentation | **supported**
- H: Do cores group periodically on large scales matching Herschel structure? | E: Smoothed core surface density and smoothed 2-pt function compared with Herschel peaks | R: Groups ~30 000 AU in size separated by ~50 000 AU | F: Quasi-periodic filament fragmentation mode | **partially**
- H: Is the grouping retained in protostars and disk stars (slingshot)? | E: Two-point functions of HOPS protostars and disks | R: Protostars grouped below ~17 000 AU; disks not | F: Grouping partly retained over protostar lifetime, erased by disk stage, consistent with slingshot | **partially**
- H: Do fragmentation models for near-critical filaments describe the ISF? | E: Compute Jeans and cylindrical scales from ISF density | R: Jeans ~10 000 AU and cylindrical ~40 000 AU roughly match, but no single model captures the multi-scale pattern | F: Existing models fail to self-consistently describe ISF fragmentation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: gaussclumps chosen because the varying extended background and many local maxima suit 2D model fitting, and it is public and documented  
  > "These properties are suited to a technique based on 2-dimensional model fitting (as opposed to segmentation)." (2.1 Identification of dense cores)
- How they decided it was enough: _not stated_
- Limitation (authors): Starless core sample may be incomplete for low-contrast cores due to background filter and may include column density enhancements  
  > "Because of the background filtering of gaussclumps, we may be insensitive to low-contrast cores that have sizes of 10$\ensuremath{''}$ (4 000 AU) or larger." (2.1 Identification of dense cores)
- Caveat (inferred, ours): Core identification depends on gaussclumps parameters and the missing short-spacing data; mass uses single T=20 K for all cores
- Caveat (inferred, ours): Starless vs protostellar split depends on HOPS completeness
- Caveat (inferred, ours): Large-scale periodicity rests on six groups and marginal 2-pt signal
- Caveat (inferred, ours): Continuum alone cannot distinguish cores from outflow cavity walls or line-of-sight overlap

## Reproducibility

- Data public (paper): Calibration scripts available in archive with the data  
  > "these are included in the standard data delivery and they available in the archive with the data." (Observations and methods)
- Products in archive: _not stated_
- Missing: Full clean parameters
- Missing: Final HOPS catalog (Furlan 2016 submitted)
- Missing: Full cupid configuration
- Missing: Core catalog is in the paper table, so downstream stats can be redone
- Data volume (inferred): ~50-150 GB raw (12-m and 7-m mosaics, four 2 GHz sidebands)
- Score (inferred): 3/5, Public ALMA data and fully listed core catalog, with main gaussclumps settings given, but imaging parameters and the protostar catalog details are missing.
- Rediscovery candidate: yes, Public data, a core catalog table and stated gaussclumps settings, and numeric results (43 cores, 2-pt scales) that can be redone.

## Links

- Method: (cite: lan93) (Two-point correlation estimator)
- Method: (cite: stu90) (Original gaussclumps algorithm)
- Companion: (cite: stu15prep) (Slingshot model and ISF density profile)
- Companion: (cite: stu15) (Herschel column density map)
- Related: HOPS
- Related: Spitzer Orion Survey

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 83,
  "stated": 61,
  "rate": 0.735
 },
 "evidence_ok": true
}
```
