# An ALMA Survey of CO Isotopologue Emission from Protoplanetary Disks in Chamaeleon I

`2017ApJ...844...99L` | The Astrophysical Journal 2017 | first author: Long, Feng | arXiv: 1706.03320 | DOI: 10.3847/1538-4357/aa78fc

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Can CO isotopologue (13CO, C18O J=3-2) emission serve as an alternate probe of disk gas mass in Cha I disks, and what gas masses and gas-to-dust ratios result?  
  > "To investigate the utility of CO as an alternate probe of disk mass, we use ALMA to survey $^{13}$CO and C$^{18}$O J = $3-2$ line emission" (abstract)
- Target **Chamaeleon I Class II disks (93 sources)**: coordinates _not stated_; z/distance 188 ± 12 pc  
  > "nearby ($188\pm12$ pc, see Appendix [8](#gaia))" (Introduction); distance from Gaia DR1 TGAS parallaxes of Cha I members (Appendix)  
  > "nearby ($188\pm12$ pc, see Appendix [8](#gaia))" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00437.S
- bands: Band 7  
  > "We use ALMA Band 7 to survey the Class II protoplanetary disks in Cha I in the Cycle 2 program 2013.1.00437 (PI: I. Pascucci)." (2 ALMA observations)
- frequencies and spectral setup: One baseband split into segments at 330.6 GHz (13CO) and 329.3 GHz (C18O), each 117.2 MHz bandwidth, 0.122 MHz channels (0.11 km/s); three other spws for continuum  
  > "The correlator was configured to cover both lines, each with a bandwidth of 117.2 MHz and a channel separation of 0.122 MHz (0.11 km s$^{-1}$)." (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.7'' x 0.5'' synthesized beam  
  > "The resulting synthesized beam for the CO data cube is 0.$\ensuremath{''}$7$\times$0.$\ensuremath{''}$5 for both samples" (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 1σ rms 30 (43) mJy/beam for 13CO (C18O) in Cool and 107 (126) mJy/beam in Hot sample at 0.25 km/s  
  > "reach the 1$\sigma$ noise rms of 30 (43) mJy beam$^{-1}$ and 107 (126) mJy beam$^{-1}$ for $^{13}$CO (C$^{18}$O) in the Cool and Hot samples" (2 ALMA observations)
- time on source: 24 s per source (Hot sample), 120 s per source (Cool sample), two executions  
  > "two sets of observations were executed for a total integration time of 24 s per source for the Hot sample and 120 s per source for the Cool sample." (2 ALMA observations)
- observing dates: _not stated_
- pi or archival as stated: Cycle 2 program, PI I. Pascucci  
  > "in the Cycle 2 program 2013.1.00437 (PI: I. Pascucci)" (2 ALMA observations)
- Line: 13CO J=3-2 (330.6 GHz (segment center))
- Line: C18O J=3-2 (329.3 GHz (segment center))
- Other facility **Gaia DR1 TGAS**: Parallaxes used for Cha I and Lupus distances  
  > "We calculated a distance of $188\pm12$ pc to Cha I from the average Gaia DR1 TGAS parallax" (Distances)
- External data: Continuum flux densities, stellar masses, spectral types, phase-center offsets, dust masses  
  > "continuum flux densities and stellar masses[^4] of our sample are adopted from (cite: pascucci2016)" (4.2) [from (cite: pascucci2016)]
- External data: Accretion rates  
  > "Accretion rates are obtained from (cite: manara2016a; manara17)" (4.2) [from (cite: manara2016a; manara17)]
- External data: Disk model grids for CO luminosity to gas mass conversion (MvD16)  
  > "MvD16 developed hundreds of full thermal-chemical models that include isotope-selective photodissociation and CO freeze-out." (5.1) [from (cite: miotello2016)]
- External data: Parametric disk model grids (WB14)  
  > "we derive the gas mass from WB14 model grids by adopting the same approach described in detail in (cite: ansdell2016)" (5.1) [from (cite: WilliamsBest2014); (cite: ansdell2016)]

## Processing

### Calibration

- pipeline or manual: CASA with NRAO-provided data reduction scripts  
  > "following the data reduction scripts provided by NRAO, including flux, phase, bandpass, and gain calibrations." (2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10%  
  > "The absolute flux scale has a systematic uncertainty of 10$\%$." (2 ALMA observations)
- self calibration: _not stated_

### Imaging

- task: CASA concat, uvcontsub, clean  
  > "The two executions of each object are then concatenated using the *concat* task after flux calibration." (2 ALMA observations)
- deconvolver: _not stated_
- weighting robust: natural weighting, all baselines included  
  > "natural weighting is chosen in *clean* to favor shorter baselines and hence achieve a higher signal-to-noise ratio (S/N)." (2 ALMA observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction with uvcontsub  
  > "Continuum emission is subtracted in the uv-plane from the spectral windows containing CO isotopologue lines using *uvcontsub* task." (2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imaged at 0.25 km/s spectral resolution  
  > "The CO transitions are imaged at a spectral resolution of 0.25 km s$^{-1}$" (2 ALMA observations)
- final beam: 0.7'' x 0.5''  
  > "The resulting synthesized beam for the CO data cube is 0.$\ensuremath{''}$7$\times$0.$\ensuremath{''}$5" (2 ALMA observations)
- final rms: _not stated_

### Inherited from earlier work

- Observation setup, calibrators and continuum results  
  > "The sample, observation calibrator setups, and results of the dust continuum are described in detail by (cite: pascucci2016)." (2 ALMA observations) [from (cite: pascucci2016)]
- Gas mass derivation from WB14 grids follows Ansdell et al.  
  > "we derive the gas mass from WB14 model grids by adopting the same approach described in detail in (cite: ansdell2016)" (5.1) [from (cite: ansdell2016)]
- Stellar mass-binning approach for Lupus comparison  
  > "following the same approach in (cite: andrews2013) and (cite: ansdell2016)" (6.1) [from (cite: andrews2013); (cite: ansdell2016)]

### Not stated but needed to reproduce (our reading)

- CASA version and clean parameters (cell size, image size, niter, threshold, mask)
- Line-free channels used in uvcontsub and fit order
- Calibrator names and pipeline details
- Priors ranges and emcee settings (walkers, steps) for the flux-stellar mass fit
- Exact line-luminosity definition and unit conversion for MvD16 fits
- Dust-mass values from Pascucci et al. needed for gas-to-dust ratios

## Analysis recipe

1. **Calibrate and image CO cubes**: CASA calibration with NRAO scripts, concat, uvcontsub, clean with natural weighting  
  > "The spectral line data cubes are then created with the *clean* algorithm using the continuum-subtracted visibilities." (2 ALMA observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Alternate reductions excluding baselines <40 kλ  
  > "In alternate reductions that exclude baselines shorter than $< 40$ k$\lambda$, the flux differences are within uncertainty in most cases" (2 ALMA observations)
2. **Define extraction region and velocity range by stacking**: Stack images shifted to continuum centroid, weighted by noise; adopt 0.6'' radius (13CO), 0.3'' (C18O), 0-10 km/s  
  > "we adopt extraction radii of $\sim$ 0.$\ensuremath{''}$6 for $^{13}$CO and 0.$\ensuremath{''}$3 for C$^{18}$O, both centered at the continuum position." (3.1)
   - assumption: C18O has same velocity range as 13CO  
  > "we assume that C$^{18}$O and $^{13}$CO have the same emission velocity." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure flux uncertainties and detection significance**: Standard deviation of fluxes in 20 random apertures in each of six 10 km/s control ranges; mean adopted as uncertainty; 3σ detection threshold  
  > "we adopt the mean value from the six control channels as the flux uncertainty for each source" (3.2)
   - fitting: _not stated_
   - validation: Only 1 of 558 13CO control fluxes exceeds 3σ, consistent with Gaussian expectation  
  > "Only one of 558 $^{13}$CO and two of 558 C$^{18}$O data points have S/N larger than 3" (3.3)
4. **Measure fluxes for detections with adapted apertures**: Increase circular aperture in 0.15'' steps on moment-0 map until flux flattens  
  > "We then measure the fluxes by increasing the circular aperture size in $0.15\ensuremath{''}$ radius increments on the intensity map until the flux flattens." (3.4)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit 13CO flux vs stellar mass and continuum**: Bayesian power-law fit F=β M*^α with chi2 likelihood including intrinsic scatter; Linmix and cenken as checks  
  > "The posterior parameter space is sampled in a Markov Chain Monte Carlo (MCMC) algorithm with *emcee*" (4.2)
   - software: emcee, Linmix, R NADA
   - fitting: emcee MCMC, uniform priors, chi2 likelihood; non-detections use measured fluxes  
  > "with $\alpha$ and $\beta$ sampled uniformly in prior range." (4.2)
   - validation: Linmix with 3σ limits gives consistent slope 1.14±0.27; cenken slope 1.07  
  > "yields a best fit with a slope of $1.14\pm0.27$ and a lower intercept of $2.50\pm0.20$" (4.2)
6. **Convert line luminosities to gas masses**: Fitted functions to median luminosity per mass bin of MvD16 grids (T Tauri, 1 Lsun); WB14 grids matched within uncertainties  
  > "we fit simple functions of disk mass with line luminosity using the median value in each mass bin from MvD16 model grids" (5.1)
   - assumption: CO-to-H2 ~1e-4 ISM abundance; distance 188 pc; MvD16 T Tauri models with stellar luminosity 1 Lsun  
  > "In this analysis, we adopt the T Tauri models with stellar luminosity of 1 $L_{\odot}$." (5.1)
   - fitting: _not stated_
   - validation: Compared with Miotello et al. 2017 fits; our masses divided by 1.6 (10 deg) or 1.2 (80 deg) to match  
  > "by dividing our gas mass by factors of 1.6 for disks with an inclination angle of 10$\ensuremath{^\circ}$ and by 1.2 for an inclination angle of 80$\ensuremath{^\circ}$" (5.1)
7. **Compute gas-to-dust ratios and compare with Lupus**: Gas mass over dust mass (Td=20 K, 188 pc); Kaplan-Meier and cendiff two-sample tests for Cha I vs Lupus over 10^4 iterations  
  > "We also perform the two-sample test with the *cendiff* routine including censored data in NADA package" (6.1)
   - software: R NADA
   - assumption: Dust temperature fixed at 20 K  
  > "assuming a fixed dust temperature of 20 K and then scaled to the 188 pc Gaia distance" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, concat, uvcontsub, clean  
  > "The ALMA data are calibrated using the *Common Astronomy Software Application* (CASA) package" (2 ALMA observations)
- **emcee** : MCMC fit of 13CO flux vs stellar mass  
  > "sampled in a Markov Chain Monte Carlo (MCMC) algorithm with *emcee*" (4.2)
- **Linmix** : Bayesian linear regression with upper limits  
  > "the Bayesian linear regression method *Linmix* [^5] (cite: Kelly2007)" (4.2)
- **R NADA package (cendiff, cenken)** : Kaplan-Meier estimator and censored two-sample tests  
  > "The distributions are calculated using the Kaplan-Meier estimator in the R NADA package to include $3\sigma$ upper limits." (6.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 13CO detections | 17 of 93 (12 significant, 5 tentative) | not stated | sources | 3 | We detect $^{13}$CO emission from 17 out of 93 sources |
| log F13CO vs log M* slope | 1.16 | ±0.13 | dimensionless | 5 | $\log(F_{13CO}/{\rm mJy})=1.16 (\pm0.13)\times \log(M_*/M_\odot)+2.84(\pm 0.18)$ |
| log F13CO vs log Fmm slope | 0.58 | ±0.08 | dimensionless | 5 | $\log(F_{\rm 13CO}/{\rm mJy}) = 0.58 (\pm0.08)\times \log(F_{\rm mm}/{\rm mJy})+1.71 (\pm0.16).$ |
| Stacked 13CO flux of detections | 574 | ±31 | mJy km/s | 3 | The mean signals are 574$\pm$31 mJy km s$^{-1}$ in $^{13}$CO |
| Stacked 13CO flux of non-detections | 70 | ±15 | mJy km/s | 3 | yields a noise-weighted average line flux of 70$\pm$15 mJy km s$^{-1}$ in $^{13}$CO |
| log Mgas vs log M* slope (MvD16) | 1.27 | ±0.14 | dimensionless | 6 | log(M$_{\rm gas}$/M$_{\rm Jup}$)= 1.27 ($\pm$0.14)$\times$log(M$_*$/M$_\odot$) – 0.76 ($\pm$0.11) |
| Median gas-to-dust ratio (MvD16) | ~4 | not stated | dimensionless | 7 | The median value of gas-to-dust ratio is $\sim 4$ when the gas mass is evaluated from MvD16 |
| Stacked gas mass Hot sample | ~0.07 | not stated | MJup | 6 | $\sim$ 0.07 M$_{\rm Jup}$ (22 M$_{\rm Earth}$) for the Hot sample |
| Median P value Cha I vs Lupus 13CO flux | 0.25 | not stated | dimensionless | 7 | with the median P value of 0.25 |

## Qualitative findings

- 13CO emission is slightly more extended than dust, with FWHM 30% wider in stacked radial profile  
  > "with a radial profile FWHM 30$\%$ wider in $^{13}$CO emission" (4.3)

## Claim tuples

- H: Do CO isotopologues give plausible disk gas masses with ISM CO/H2? | E: Convert 13CO/C18O luminosities to gas mass via MvD16 and WB14 grids | R: Gas masses mostly 0.03-1 MJup, stacked ~0.05 MJup; gas-to-dust ~1-15 | F: Gas masses and gas-to-dust ratios are implausibly low unless CO is depleted | **supported**
- H: Does 13CO flux correlate with stellar mass? | E: Bayesian fit of flux vs M* | R: Slope 1.16±0.13 | F: 13CO flux scales with stellar mass, shallower than continuum | **supported**
- H: Are Cha I and Lupus CO properties similar? | E: Kaplan-Meier and censored two-sample tests | R: Median P=0.25, but 0.003 with smaller-aperture limits | F: No firm conclusion possible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Uniform stacking-based method to handle weak signals and upper limits  
  > "we develop a method to uniformly identify weak detections and measure line fluxes, uncertainties, and upper limits" (3 Measuring CO Line Fluxes and Upper Limits)
- Alternative: Excluding baselines <40 kλ rejected to retain total flux and consistency with continuum  
  > "Since our primary objective is to measure the total flux from the disk, all baselines are included in *clean*." (2 ALMA observations)
- How they decided it was enough: _not stated_
- Limitation (authors): 80% of sample undetected, so correlations are poorly constrained  
  > "Since 80$\%$ of our sample is not detected in $^{13}$CO, more sensitive observations, especially for the low-mass end, are needed" (4.2)
- Caveat (inferred, ours): Gas masses depend on grids not matched to Cha I accretion rates and stellar luminosities
- Caveat (inferred, ours): Results sensitive to choice of aperture for upper limits
- Caveat (inferred, ours): Gas-to-dust ratios depend on assumed dust temperature

## Reproducibility

- Data public (paper): ALMA project 2013.1.00437.S cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00437.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and clean parameters
- Missing: Line-free channels for uvcontsub
- Missing: Prior ranges and MCMC settings
- Missing: Per-source dust masses from Pascucci et al. 2016
- Data volume (inferred): Small: short snapshot Band 7 observations of 93 sources, likely tens of GB raw
- Score (inferred): 3/5, Data public and flux method well described with tables, but imaging parameters and software versions missing.
- Rediscovery candidate: yes, Public data, a described aperture-photometry recipe, and numeric flux and gas-mass tables.

## Links

- Method: (cite: miotello2016) (MvD16 line luminosity to gas mass conversion)
- Method: (cite: WilliamsBest2014) (WB14 parametric gas mass models)
- Companion: (cite: pascucci2016) (Continuum results and stellar properties for the same ALMA sample)
- Companion: (cite: ansdell2016) (Lupus ALMA CO survey for comparison)
- Related: ALMA Lupus disk survey
- Related: ALMA Upper Sco survey

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "stated": 48,
  "rate": 0.585
 },
 "evidence_ok": true
}
```
