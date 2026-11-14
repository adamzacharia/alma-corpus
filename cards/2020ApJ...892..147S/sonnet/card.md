# Oversized Gas Clumps in an Extremely Metal-poor Molecular Cloud Revealed by ALMA's Parsec-scale Maps

`2020ApJ...892..147S` | The Astrophysical Journal 2020 | first author: Shi, Yong | arXiv: 2002.10209 | DOI: 10.3847/1538-4357/ab7a12

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation, milky_way_ism
- Question: Does low metallicity suppress gas fragmentation, giving larger CO clumps than Milky Way clumps at the same gas surface density, in the extremely metal-poor galaxy DDO 70?  
  > "Metals are thought to have profound effects on the internal structures of molecular clouds in which stars are born." (abstract)
- Target **DDO 70**: coordinates ALMA region about 09 59 58.0 +05 19 46 (J2000)  
  > "DDO 70 is a nearby dwarf irregular galaxy at a distance of 1.38 Mpc (cite: Tully13)." (Introduction); z/distance 1.38 Mpc  
  > "DDO 70 is a nearby dwarf irregular galaxy at a distance of 1.38 Mpc (cite: Tully13)." (Introduction); distance from Tully13  
  > "DDO 70 is a nearby dwarf irregular galaxy at a distance of 1.38 Mpc (cite: Tully13)." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00359.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-4 and C40-7  
  > "were composed of two array configurations of C40-4 and C40-7" (2.1 ALMA data of DDO 70)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 1-sigma about 0.9 mJy/beam at 0.4 km/s  
  > "The 1-$\sigma$ sensitivity is about 0.9 mJy/beam at a velocity resolution of 0.4 km/s." (2.1 ALMA data of DDO 70)
- time on source: 1.1 hours and 0.6 hours  
  > "The corresponding integration time is 1.1 hours and 0.6 hours, respectively." (2.1 ALMA data of DDO 70)
- observing dates: 11 Nov 2016 and 03 Aug 2017  
  > "The observations were performed on 11 Nov. 2016 and 03 Aug 2017, respectively." (2.1 ALMA data of DDO 70)
- pi or archival as stated: PI: Y. Shi  
  > "(PID: 2016.1.00359.S, PI: Y. Shi)" (2.1 ALMA data of DDO 70)
- Line: CO J=2-1 (not stated)
- Other facility **IRAM 30-m**: single-dish CO J=2-1 detection used for comparison of flux  
  > "search for the CO $J$=2-1 emission with the Institut de Radioastronomie Millimetrique (IRAM) 30-m telescope (cite: Shi16)" (Introduction)
- Other facility **Herschel**: 70-350 micron images for dust SED  
  > "The infrared data at 70, 160, 250 and 350 $\mu$m were retrieved from the archive of the *Herschel* Space Observatory" (2.2 Ancillary data of DDO 70)
- Other facility **Spitzer**: 3.6-24 micron images  
  > "The reduced *Spitzer* images at 3.6, 4.5, 5.8 and 24 $\mu$m are from the Local Volume Legacy program (cite: Dale09)." (2.2 Ancillary data of DDO 70)
- Other facility **APEX**: SMC CO J=2-1 data  
  > "The CO $J$=2-1 data with an angular resolution of 28 arcsec were retrieved from the archive of the APEX telescope" (4.1)
- External data: HI image of DDO 70  
  > "The HI image is from the program of Local Irregulars That Trace Luminosity Extremes (cite: Hunter12)" (2.2 Ancillary data of DDO 70) [from Hunter12]
- External data: SMC Herschel images (HERITAGE)  
  > "the *Herschel* images were retrieved from Herschel Inventory of the Agents of Galaxy Evolution (HERITAGE) (cite: Meixner13)" (4.1) [from Meixner13]
- External data: Milky Way gas maps of Cygnus X  
  > "four massive star-forming regions including Cygnus X (cite: Cao19), NGC 6344 (cite: Russeil13), RCW 79 (cite: Liu17) and NGC 7538 (cite: Fallscheer13)" (4.4) [from Cao19; Russeil13; Liu17; Fallscheer13]

## Processing

### Calibration

- pipeline or manual: standard pipeline in CASA, each configuration calibrated individually  
  > "We calibrated the data individually with CASA, following the standard pipeline" (2.1 ALMA data of DDO 70)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: about 10%  
  > "The uncertainty of the absolute flux calibration is about 10%" (2.1 ALMA data of DDO 70)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: briggs weighting 1.5  
  > "We selected briggs weighting with a weighting of 1.5" (2.1 ALMA data of DDO 70)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: visibilities of both configurations combined for cleaning  
  > "then combined all visibility data together for cleaning" (2.1 ALMA data of DDO 70)
- smoothing: _not stated_
- final beam: 0.21x0.19 arcsec (1.47x1.27 pc)  
  > "A final datacube with a beam size of 0.21$''$$\times$0.19$''$(1.47$\times$1.27 pc) was produced." (2.1 ALMA data of DDO 70)
- final rms: _not stated_

### Inherited from earlier work

- Herschel reduction and ancillary data details  
  > "We refer readers to our previous work (cite: Shi14; Shi16) for details." (2.2) [from Shi14; Shi16]
- photometry and GDR method  
  > "Following the methods of our previous work (cite: Shi14)" (4.2) [from Shi14]

### Not stated but needed to reproduce (our reading)

- Clean threshold, niter, mask, cell and image size
- CASA version
- Line-free channels / continuum subtraction
- Sky frequency and spectral setup
- Details of clump identification code
- Exact measured SMC clump sizes for the CO/dust ratio

## Analysis recipe

1. **Identify CO clumps**: pixels S/N>3.5 in two adjacent channels over 280-290 km/s; regions >10 pixels; integrated S/N>4; single Gaussian spectral fit  
  > "we first identified pixels that have a signal to noise ratio (S/N) $>$ 3.5 in two adjacent channels of ALMA data." (2.1 ALMA data of DDO 70)
   - software: CASA
   - fitting: single Gaussian  
  > "A single Gaussian profile was used to fit the spectra." (2.1 ALMA data of DDO 70)
   - validation: circle size varied by 20% with negligible changes  
  > "if the size of the circular region increases or decreases by 20%, the changes in the derived clump sizes are negligible" (2.1 ALMA data of DDO 70)
2. **Measure clump size and virial mass**: imfit 2-D Gaussian on moment-0, R from geometric mean sigma, Mvir=1040 R sigma_v^2  
  > "we used CASA imfit() to fit a 2-D Gaussian profile to the velocity-integrated flux (moment-zero) map of the clump within a circular region." (2.1 ALMA data of DDO 70)
   - software: CASA imfit
   - assumption: distance 1.38 Mpc  
  > "DDO 70 is a nearby dwarf irregular galaxy at a distance of 1.38 Mpc (cite: Tully13)." (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive gas-to-dust ratio**: DL07 SED fit to diffuse region, GDR = HI/dust, corrected for DL08/MBB and diffuse-to-dense drop of 2.5  
  > "we fitted the full infrared SEDs with the DL07 dust model (cite: Draine07) to estimate the dust masses" (4.2)
   - assumption: kappa_160um=13.1 cm2/g; drop factor 2.5+-0.5  
  > "We thus adopted a factor of 2.5$\pm$0.5 to correct the above GDR to be 4,594 with a 1-$\sigma$ error of 62%." (4.3)
   - fitting: DL07 model fit  
  > "we fitted the full infrared SEDs with the DL07 dust model (cite: Draine07) to estimate the dust masses" (The gas-to-dust (GDR) ratio of DDO 70)
   - validation: cross-checked with Roman-Duval17 relations  
  > "These two equations indicate that the GDR drops by a factor of 2.1-3.2" (4.3)
4. **Convert CO extinction threshold to gas surface density**: tau160=1/2200 threshold from SMC CO/dust size ratio; Sigma_gas=tau*GDR/kappa  
  > "we derived the gas mass surface densities of CO clumps in DDO 70 to be 756$\pm$468 M$_{\odot}$/pc$^{2}$." (4.3)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare with Milky Way clump sizes**: scale MW Herschel gas maps, rebin and convolve to DDO 70 resolution, subtract Sigma_limit, measure five largest clumps per region  
  > "we compare them to the five largest clumps in each region of the Milky Way" (4.4)
   - fitting: _not stated_
   - validation: compared with Hi-GAL clumps radii <1.3 pc  
  > "all their radii are smaller than 1.3 pc" (5 RESULTS)

## Software

- **CASA** : calibration, imaging, imfit  
  > "We calibrated the data individually with CASA" (2.1 ALMA data of DDO 70)
- **unimap** : Herschel data reduction  
  > "were reduced with unimap (cite: Traficante11)" (2.2 Ancillary data of DDO 70)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO flux of five clumps | 127 | 11 | mJy km/s | 1 | the total fluxes (127$\pm$11 mJy km/s) of these individual clumps |
| Diffuse-region GDR | 6078 | +1000/-1600 | dimensionless | 3 | The GDR of the galaxy is thus derived to be $6078^{+1000}_{-1600}$ |
| Final GDR | 4594 | 2848 | dimensionless | 3 | By adopting the above final GDR (4594$\pm$2848) |
| Gas surface density of CO clumps | 756 | 468 | Msun/pc2 | 4 | 756$\pm$468 M$_{\odot}$/pc$^{2}$ |
| Mean clump radius DDO 70 vs MW | 2.0 pc vs ~0.5 pc | not stated | pc | 5 | The mean radius of the former is 2.0 pc, while the latter has a mean of $\sim$0.5 pc including upper-limits. |

## Qualitative findings

- CO clumps follow Larson's law roughly like the MW and NGC 6822  
  > "clumps in DDO 70 do not show systematic deviations from those in the Milky Way" (3 The Larson's law)

## Claim tuples

- H: Low metallicity suppresses fragmentation, giving larger clumps | E: Compare DDO 70 CO clump sizes with MW clumps at equal gas surface density | R: DDO 70 clumps all >1.5 pc; MW clumps <1.5 pc | F: Clumps are significantly larger, consistent with suppressed fragmentation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only one cloud, so not statistically significant  
  > "our result is not statistically important, given that our observation is only for one cloud." (5 RESULTS)
- Caveat (inferred, ours): Result depends on large GDR uncertainty and assumed metallicity-independent CO-Av relation
- Caveat (inferred, ours): SMC calibration at coarse resolution applied to pc scales

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: clump-finding implementation
- Missing: MW map scaling details
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public ALMA data but imaging details and multi-step literature-based scaling are incomplete.
- Rediscovery candidate: no, Imaging recipe incomplete and the main result relies on external Herschel maps and assumptions.

## Links

- Method: Shi14 (GDR and photometry method)
- Companion: Shi16 (IRAM 30-m CO detection)
- Related: HERITAGE
- Related: Local Volume Legacy

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 73,
  "stated": 39,
  "rate": 0.534
 },
 "evidence_ok": true
}
```
