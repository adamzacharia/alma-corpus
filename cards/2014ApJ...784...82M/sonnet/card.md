# ALMA Observations of the Orion Proplyds

`2014ApJ...784...82M` | The Astrophysical Journal 2014 | first author: Mann, Rita K. | arXiv: 1403.2026 | DOI: 10.1088/0004-637X/784/1/82

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: What are the dust disk masses of the Orion proplyds and other ONC stars, and how do they depend on distance from theta1 Ori C (external photoevaporation)?  
  > "To probe the full disk mass distribution in the ONC and further study the impact of external photoionizing radiation on disk properties" (Introduction)
- Target **Orion Nebula Cluster proplyds (5 fields, 22 HST proplyds plus 26 other stars)**: coordinates Field 1 phase center 05:35:16.30 -05:23:22.40 (J2000); five fields in Table 1  
  > "| 1 | 05:35:16.30 | -05:23:22.40 | 2600 | 0.24 | 0.50$\times$0.44 | 84 |" (Table 1); "where $d=400$ pc is the distance to Orion (cite: sandstrom; menten; kraus07; kraus09)" (Results); z/distance 400 pc  
  > "| 1 | 05:35:16.30 | -05:23:22.40 | 2600 | 0.24 | 0.50$\times$0.44 | 84 |" (Table 1); "where $d=400$ pc is the distance to Orion (cite: sandstrom; menten; kraus07; kraus09)" (Results); distance from Sandstrom et al. 2007; Menten et al. 2007; Kraus et al. 2007, 2009  
  > "| 1 | 05:35:16.30 | -05:23:22.40 | 2600 | 0.24 | 0.50$\times$0.44 | 84 |" (Table 1); "where $d=400$ pc is the distance to Orion (cite: sandstrom; menten; kraus07; kraus09)" (Results)

## Data provenance

- ALMA projects: 2011.0.00028.S
- bands: Band 7 (345 GHz), 856 um  
  > "observed with ALMA using the Band 7 (345 GHz) receivers on 2012 October 24, as part of the Cycle 0 Early Science operations" (Observations)
- frequencies and spectral setup: four 1.875 GHz-wide spectral windows, 3840 channels each; covering CO(3-2), HCN(4-3), HCO+(4-3), CS(7-6)  
  > "The correlator was configured to observe simultaneously four 1.875 GHz-wide spectral windows, each divided into 3840 channels each with a width of 488.28 kHz" (Observations)
- continuum bandwidth: ~7.5 GHz  
  > "The focus here will be on the wideband ($\Delta \nu \approx7.5$ GHz) continuum emission, extracted by integrating over all line-free channels" (Observations)
- arrays: Twenty-two 12-m antennas  
  > "Twenty-two 12-m diameter ALMA antennas were arranged in a hybrid configuration" (Observations)
- configurations: _not stated_
- baselines: shortest baseline 21.2 m  
  > "Since the shortest baseline was 21.2 m in length, the maximum recoverable scale was 4$\ensuremath{''}$99." (Observations)
- angular resolution: ~0.5 arcsec (robust weighting); beam 0.51x0.46  
  > "yielded (with robust weighting) images with a $\sim$0$\ensuremath{''}$5 angular resolution" (Observations)
- max recoverable scale: 4.99 arcsec  
  > "Since the shortest baseline was 21.2 m in length, the maximum recoverable scale was 4$\ensuremath{''}$99." (Observations)
- sensitivity: 1 sigma rms 0.24-1.15 mJy/beam by field  
  > "| 4 | 05:35:25.30 | -05:15:35.50 | 1300 | 1.15 | 0.51$\times$0.46 | 89 |" (Table 1)
- time on source: 136 s per visit; 2600 s Field 1, 1300 s Fields 2-5  
  > "Each Field was observed for 136 seconds per visit." (Observations)
- observing dates: 2012 October 24  
  > "observed with ALMA using the Band 7 (345 GHz) receivers on 2012 October 24" (Observations)
- pi or archival as stated: _not stated_
- Other facility **SMA**: Previous 880 um disk masses (Mann & Williams 2010) combined with ALMA  
  > "Combining these ALMA data with previous SMA observations" (abstract)
- Other facility **VLA**: Published cm flux densities for free-free extrapolation  
  > "using published VLA flux densities from 1.3 cm to 6 cm" (Results)
- Other facility **HST**: Proplyd identification  
  > "22 *HST*-identified proplyds" (abstract)
- External data: VLA centimeter flux densities used for free-free extrapolation  
  > "using published VLA flux densities from 1.3 cm to 6 cm (cite: garay; felli; felli93; zapata)" (Results) [from (cite: garay; felli; felli93; zapata)]
- External data: SMA disk masses at intermediate distances  
  > "including the previous SMA results from (cite: mann10) to fill in the intermediate distances not yet probed with ALMA" (Disk Masses and Distance from theta1 Ori C) [from (cite: mann10)]
- External data: Positions and names of non-proplyd targets from HST ACS and CTIO surveys  
  > "ACS sources from (cite: robberto), ROB sources from (cite: robberto10)" (Table 3) [from (cite: robberto; robberto10; ricci)]
- Simulation/model as data: Callisto flux model from Butler (2012)  
  > "The model of Callisto was that provided by Butler (2012)." (Observations)

## Processing

### Calibration

- pipeline or manual: standard procedures in CASA  
  > "Data calibration and image reconstruction were performed using standard procedures in the `CASA` package." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto (Butler 2012 model); gain J0607-085; bandpass J0522-364  
  > "The absolute amplitude scale was determined from observations of Callisto, and the bandpass response of the system was measured from observations of the bright quasar J0522–364." (Observations)
- flux scale uncertainty: ~10%  
  > "error does not include uncertainties in the flux scale of $\sim$ 10%" (Table 2)
- self calibration: _not stated_

### Imaging

- task: CASA CLEAN, multi-frequency synthesis, each field separately  
  > "Each field was Fourier-inverted separately, using the multi-frequency synthesis mode in the `CLEAN` task" (Observations)
- deconvolver: Clark, threshold ~2x RMS  
  > "These dirty images were then `CLEAN`ed with the Clark algorithm down to a threshold of $\sim$2$\times$ the RMS" (Observations)
- weighting robust: Briggs robust = 0.5  
  > "with an intermediate Briggs robustness parameter of 0.5 chosen to achieve the desired angular resolution" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: dirty image to ~34 arcsec diameter  
  > "A dirty image was generated out to a diameter of $\sim$34$''$" (Observations)
- masking: boxes on features visible in dirty images  
  > "boxes were used to focus the algorithm toward features that could be visually confirmed in the dirty images" (Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum made by integrating line-free channels  
  > "extracted by integrating over all line-free channels" (Observations)
- line free channels: _not stated_
- primary beam correction: applied after CLEAN  
  > "After `CLEAN`ing, each field was corrected for primary beam attenuation" (Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.51 x 0.46 arcsec  
  > "restored with a synthesized 0$\ensuremath{''}$51 $\times$ 0$\ensuremath{''}$46 beam" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Optically thin isothermal mass relation and opacity 0.034 cm2/g at 856 um  
  > "assuming the standard optically thin isothermal relationship (cite: beckwith90)" (Results) [from (cite: beckwith90)]
- Disk temperature 20 K for comparison with earlier surveys  
  > "We assume a typical disk temperature of 20 K, as in previous disk surveys of Taurus and Ophiuchus by (cite: andrews05; andrews07)" (Results) [from (cite: andrews05; andrews07; mann09a; mann10)]
- Censored correlation tests  
  > "Using the correlation tests described by (cite: isobe), including the Cox Hazard Model, Generalized Kendall’s Tau, and Spearman’s Rho tests" (Disk Masses and Distance from theta1 Ori C) [from (cite: isobe)]

### Not stated but needed to reproduce (our reading)

- Line-free channel selection for continuum
- Exact CASA version and CLEAN parameters (niter, cell size, image size in pixels, box definitions)
- Exact numerical RMS threshold used for CLEAN
- Specific cm flux values and spectral index fits used for free-free extrapolation
- Details of Gaussian fitting procedure for flux and sizes
- Details of the survival analysis implementation (ASURV?) and the SMA data table
- Whether the 3-sigma upper limit was computed from local or field-center rms

## Analysis recipe

1. **Image continuum**: CASA CLEAN with MFS, Briggs robust 0.5, Clark, boxes, primary beam correction  
  > "Each field was Fourier-inverted separately, using the multi-frequency synthesis mode in the `CLEAN` task with an intermediate Briggs robustness parameter of 0.5" (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure fluxes**: Fit elliptical Gaussians in the image plane for centroids and integrated flux densities; noise from emission-free regions  
  > "The centroid positions and 856 $\mu$m integrated flux densities for each target were measured by fitting elliptical Gaussians in the image plane." (Results)
   - fitting: elliptical Gaussian  
  > "The centroid positions and 856 $\mu$m integrated flux densities for each target were measured by fitting elliptical Gaussians in the image plane." (Results)
   - validation: _not stated_
3. **Subtract free-free emission**: Extrapolate maximum cm flux with F_ff ∝ nu^-0.1 to 856 um, subtract to get F_dust  
  > "The highest levels of centimeter emission were used to account for the free-free contributions to result in the most conservative estimate of disk mass." (Results)
   - parameter: cm data only at wavelengths <= 6 cm  
  > "We avoided observations taken at wavelengths longer than 6 cm (5 GHz) in this analysis" (Results)
   - assumption: free-free ∝ nu^-0.1, dust ∝ nu^2  
  > "Fits to the free-free emission ($F_{\rm ff} \propto \nu^{-0.1}$) and dust emission ($F_{\rm dust} \propto \nu^{2}$)" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive disk masses**: M = F d^2/(kappa B_nu(T))  
  > "$$M_{\rm disk} = \frac{F_{\rm dust}d^2}{\kappa_{\nu}B_{\nu}(T)},$$" (Results)
   - assumption: d=400 pc, kappa=0.034 cm2/g with gas-to-dust 100:1, T=20 K (40 K for massive stars)  
  > "$\kappa_{\nu}=0.034$ cm$^2$ g$^{-1}$ is the (cite: beckwith90) dust grain opacity at 856 $\mu$m with an implicit gas-to-dust mass ratio of 100:1" (Results)
   - fitting: _not stated_
   - validation: Optical depth discussed: up to ~10-25% optically thick emission for brighter disks  
  > "the brighter disks could have up to $\sim$10-25% of their emission being optically thick" (Results)
5. **Completeness**: Fraction of sources detectable at >=3 sigma vs disk mass  
  > "An overall disk mass sensitivity for the survey was determined by measuring the fraction of sources that could be detected at $\geq 3\sigma$ as a function of $M_{\rm disk}$" (Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Test mass vs distance correlation**: Censored-data correlation tests on ALMA plus SMA data  
  > "including the Cox Hazard Model, Generalized Kendall’s Tau, and Spearman’s Rho tests, that make use of the combined, censored dataset" (Disk Masses and Distance from theta1 Ori C)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration and imaging (CLEAN)  
  > "Data calibration and image reconstruction were performed using standard procedures in the `CASA` package." (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Proplyds detected | 21 of 22 | not stated | count | 2 | We detected submillimeter emission from 21 of the 22 targeted *HST*-identified proplyds in this survey |
| 100% completeness mass limit | 1.2 | not stated | M_jup | 5 | the observed fields are 100% complete for $M_{\rm disk} \geq\,1.2\,M_{\rm jup}$ |
| 50% completeness mass limit | 0.4 | not stated | M_jup | 5 | 50% complete for $M_{\rm disk} \ge 
0.4\,M_{\rm jup}$ |
| 114-426 flux density | 7.0 | 1.2 | mJy | 2 | / 3 / 114-426 / 5:35:11.32 / -5:24:26.52 / 7.0 $\pm$1.2 / 0 / 7.0$\pm$1.2 / 3.38 $\pm$0.56 / |
| 253-1536 dust flux density | 162.9 | 0.9 | mJy | 3 | / 5 / 253-1536 / 5:35:25.30 / -5:15:35.40 / 162.9 $\pm$0.9 / 0 / 162.9$\pm$0.9 / 78.66 $\pm$0.42 / |
| Upper limits on undetected disk masses | 0.1-0.6 | 3 sigma | M_jup | 4 | The ALMA observations place stringent (3 $\sigma$) upper limits of 0.1–0.6 $M_{\rm jup}$ on the disk masses for the undetected targets |
| Probability of no correlation, mass vs projected distance | <1e-4 | not stated | dimensionless | 6 | the probability of no correlation between disk mass and projected distance to $\theta^1$ Ori C is $<$10$^{-4}$ for all 3 tests |

## Qualitative findings

- Massive disks (>~3 Mjup) are lacking within 0.03 pc of theta1 Ori C (EUV-dominated), while FUV-dominated region shows a wide range of disk masses  
  > "There is a clear lack of massive disks ($\gtrsim$ 3 $M_{\rm jup}$) within 0.03 pc of $\theta^1$ Ori C where EUV irradiation dominates" (Discussion)

## Claim tuples

- H: Disk masses depend on distance from theta1 Ori C | E: Combine ALMA and SMA masses with censored correlation tests | R: p(no correlation) <1e-4 in all three tests | F: Disk masses are lower closer to theta1 Ori C, attributed to photoevaporation | **supported**
- H: Massive stars and non-proplyd stars host detectable disks | E: Image 26 non-HST-proplyd stars incl. theta1 C and F | R: Only 2 detected; limits 0.1-0.6 Mjup | F: Such disks must be low mass and small; massive stars have no disks or short-lived disks | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Beam of ~0.5 arcsec chosen to separate disks in crowded Trapezium, resolve large proplyds, and filter out extended cloud emission  
  > "This target resolution was chosen to distinguish individual disks toward the crowded Trapezium cluster, resolve the emission from three large proplyds" (Observations)
- Alternative: Projection effects, stellar mass segregation, optical depth and tidal stripping rejected as explanations  
  > "Instead, the evidence suggests that an externally driven disk evolution factor is likely responsible for the behavior in Figure [5](#fig3)." (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk masses may be underestimated for brighter disks due to optical depth  
  > "resulting in an underestimation of their disk masses" (Results)
- Limitation (authors): Selection effects in incomplete ONC disk census  
  > "there are still strong selection effects at play in the currently incomplete ONC disk mass census" (Footnote)
- Caveat (inferred, ours): Single temperature (20 K) and opacity assumed for all disks
- Caveat (inferred, ours): Maximum cm flux used for free-free, biasing masses low and variability unaccounted for
- Caveat (inferred, ours): Background cloud emission not corrected
- Caveat (inferred, ours): Projected rather than true distances

## Reproducibility

- Data public (paper): Cycle 0 data ADS/JAO.ALMA#2011.0.00028.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00028.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and exact CLEAN parameters
- Missing: cm flux values used
- Missing: SMA data table and survival analysis details
- Data volume (inferred): ~10-50 GB (Cycle 0, 5 fields, 4 spws)
- Score (inferred): 3/5, Data are public and the recipe is mostly described, but several processing parameters and the literature fluxes are not given.
- Rediscovery candidate: yes, Public Cycle 0 data; fluxes and masses in tables with a simple mass formula.

## Links

- Method: (cite: beckwith90) (Optically thin disk mass formula and opacity)
- Method: (cite: andrews05) (Optical depth discussion and temperature convention)
- Method: (cite: isobe) (Censored correlation tests)
- Companion: (cite: mann10) (SMA survey of Orion proplyds combined with ALMA data)
- Companion: J. Bally et al., in preparation (Forthcoming article on disk 114-426)
- Related: ONC HST Treasury Program
- Related: ALMA Cycle 1 ONC survey

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 79,
  "stated": 53,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
