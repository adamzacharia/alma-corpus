# ALMA Survey of Lupus Protoplanetary Disks. I. Dust and Gas Masses

`2016ApJ...828...46A` | The Astrophysical Journal 2016 | first author: Ansdell, M. | arXiv: 1604.05719 | DOI: 10.3847/0004-637X/828/1/46

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: What are the bulk dust and gas masses of a near-complete sample of Lupus disks, how do they depend on stellar mass, and how do they compare to other regions and to planet formation constraints?  
  > "We present the first high-resolution sub-mm survey of both dust and gas for a large population of protoplanetary disks." (abstract)
- Target **Lupus I-IV protoplanetary disks (89 observed)**: coordinates per-source RA/Dec in Table 2  
  > "In general, Lupus III is at $\sim$200 pc while Lupus I, II, and IV are at $\sim$150 pc, though distance estimates vary due to the depth of the complex." (2 LUPUS SAMPLE & COMPLETENESS); z/distance 150 pc (Lupus I, II, IV); ~200 pc (Lupus III)  
  > "In general, Lupus III is at $\sim$200 pc while Lupus I, II, and IV are at $\sim$150 pc, though distance estimates vary due to the depth of the complex." (2 LUPUS SAMPLE & COMPLETENESS); distance from literature cloud distances, as listed in Table 1  
  > "In general, Lupus III is at $\sim$200 pc while Lupus I, II, and IV are at $\sim$150 pc, though distance estimates vary due to the depth of the complex." (2 LUPUS SAMPLE & COMPLETENESS)

## Data provenance

- ALMA projects: 2013.1.00220.S
- bands: 890 um continuum (Band 7), 13CO and C18O 3-2  
  > "Our observations cover the 890 $\mu$m continuum and the $^{13}$CO and C$^{18}$O 3–2 lines." (abstract)
- frequencies and spectral setup: continuum SPWs at 328.3, 340.0, 341.8 GHz; 13CO and C18O windows at 330.6 and 329.3 GHz, 58.594 MHz bandwidth, 0.11 km/s resolution  
  > "these spectral windows were centered on 330.6 and 329.3 GHz, respectively, with bandwidths of 58.594 MHz, channel widths of 0.122 MHz, and velocity resolutions of 0.11 km s$^{-1}$." (3 ALMA OBSERVATIONS)
- continuum bandwidth: _not stated_
- arrays: 12-m antennas, 37 (M-type) and 41 (AGK-type)  
  > "The array configuration used 37 12-m antennas for the M-type sample and 41 12-m antennas for the AGK-type sample" (3 ALMA OBSERVATIONS)
- configurations: _not stated_
- baselines: 21.4–783.5 m  
  > "with baselines of 21.4–783.5 m" (3 ALMA OBSERVATIONS)
- angular resolution: average continuum beam 0.34"x0.28"  
  > "The average continuum beam size was 0.34$^{\prime\prime}$$\times$0.28$^{\prime\prime}$" (3 ALMA OBSERVATIONS)
- max recoverable scale: _not stated_
- sensitivity: average rms 0.41 and 0.25 mJy/beam (AGK and M types)  
  > "for an average rms of 0.41 and 0.25 mJy beam$^{-1}$, respectively" (3 ALMA OBSERVATIONS)
- time on source: 30 s per source (AGK-type), 1 min per source (M-type)  
  > "We integrated for 30 sec per source on the AGK-type sample and 1 min per source on the M-type sample" (3 ALMA OBSERVATIONS)
- observing dates: 2015 June 14 and 15  
  > "were obtained on 2015 June 14 (AGK-type sources and unknown spectral types) and 2015 June 15 (M-type sources)" (3 ALMA OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: 13CO 3-2 (not stated)
- Line: C18O 3-2 (not stated)
- Other facility **VLT/X-Shooter**: spectra for stellar parameters and rejecting background giants  
  > "follow-up VLT/X-Shooter spectra (Alcalá et al., in prep) revealed as background giants" (2 LUPUS SAMPLE & COMPLETENESS)
- External data: Stellar masses, Teff, L* from spectroscopy and Siess evolutionary models  
  > "For details on the derivation of these $M_{\ast}$ values, as well as their associated $T_{\rm eff}$ and $L_{\ast}$ values, see (cite: 2014A&A...561A...2A) and Alcalá et al. (in prep)." (2 LUPUS SAMPLE & COMPLETENESS) [from (cite: 2014A&A...561A...2A); Alcalá et al. (in prep)]
- External data: Sz 82 (IM Lup) ALMA continuum and line fluxes  
  > "For Sz 82, we report the ALMA continuum measurement from Cleeves et al. (in prep)." (4.1 Continuum Emission) [from Cleeves et al. (in prep)]
- External data: Taurus continuum fluxes and stellar masses  
  > "translating the sub-mm continuum fluxes (or $3\sigma$ upper limits) given in (cite: 2013ApJ...771..129A) and Barenfeld et al. (submitted) into dust masses" (6.1 Correlations with Stellar Mass) [from (cite: 2013ApJ...771..129A)]
- External data: Upper Sco ALMA continuum fluxes  
  > "Scott Barenfeld for providing ALMA continuum fluxes for Upper Sco sources in advance of publication." (Acknowledgements) [from Barenfeld et al. (submitted)]
- Simulation/model as data: WB14 parametrized disk model grids of 13CO and C18O line luminosities vs gas mass (ISM and 3x reduced C18O abundance)  
  > "We compare our measured $^{13}$CO and C$^{18}$O 3–2 line luminosities to the WB14 model grids in Figure [4](#fig-gas)." (5.2 Gas Masses)

## Processing

### Calibration

- pipeline or manual: pipeline calibrated by NRAO  
  > "The data were pipeline calibrated by NRAO and included flux, phase, bandpass, and gain calibrations." (3 ALMA OBSERVATIONS)
- casa version: CASA 4.4.0  
  > "Data calibration and imaging were performed using CASA 4.4.0." (3 ALMA OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Flux calibration used observations of Titan" (3 ALMA OBSERVATIONS)
- flux scale uncertainty: 10%  
  > "We estimated an absolute flux calibration error of 10% based on variations in the gain calibrators." (3 ALMA OBSERVATIONS)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: continuum robust +0.5 (unresolved), -1.0 (resolved); lines robust +0.5  
  > "cleaning with a Briggs robust weighting parameter of $+0.5$ for unresolved sources and $-1.0$ for resolved sources." (3 ALMA OBSERVATIONS)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: zero-moment maps integrated over channels with emission by visual inspection; otherwise ±2.3 km/s about mean Lupus radial velocity  
  > "If no emission was visible, we summed across the average velocity range of the detected sources ($\pm2.3$ km s$^{-1}$)" (3 ALMA OBSERVATIONS)
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted before line channel maps  
  > "by subtracting the continuum and cleaning with a Briggs robust weighting parameter of $+0.5$ in all cases" (3 ALMA OBSERVATIONS)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.34"x0.28" average continuum  
  > "The average continuum beam size was 0.34$^{\prime\prime}$$\times$0.28$^{\prime\prime}$" (3 ALMA OBSERVATIONS)
- final rms: _not stated_

### Inherited from earlier work

- Gas mass determination via WB14 model grids  
  > "This structure has been simulated by (cite: 2014ApJ...788...59W) (hereafter WB14) in parametrized models" (5.2 Gas Masses) [from (cite: 2014ApJ...788...59W)]
- Bayesian linear regression with censored data  
  > "we employed the same Bayesian linear regression technique from (cite: 2007ApJ...665.1489K) used by (cite: 2013ApJ...771..129A)" (6.1 Correlations with Stellar Mass) [from (cite: 2007ApJ...665.1489K)]
- MC two-sample test comparison accounting for stellar distributions  
  > "following the methodology of (cite: 2013ApJ...771..129A)" (6.2 Comparison to Other Regions) [from (cite: 2013ApJ...771..129A)]

### Not stated but needed to reproduce (our reading)

- Number of CLEAN iterations, threshold, cell and image size, masks
- Which sources were treated as resolved (robust -1.0)
- Line-free channels for continuum subtraction and continuum channel selection
- Aperture radii for each source and exact upper-limit aperture procedure
- Detailed WB14 grid values and the 69 stellar masses (Alcalá et al. in prep)
- Kelly regression priors/settings and MC mass assignment details
- Sz 82 data from Cleeves et al. (in prep)

## Analysis recipe

1. **Image continuum and CO line maps**: Average continuum channels and clean; subtract continuum and clean line channels; make zero-moment maps  
  > "We extracted continuum images from the calibrated visibilities by averaging over the continuum channels and cleaning" (3 ALMA OBSERVATIONS)
   - software: CASA
   - parameter: Briggs robust +0.5 or -1.0 (continuum), +0.5 (lines)  
  > "cleaning with a Briggs robust weighting parameter of $+0.5$ for unresolved sources and $-1.0$ for resolved sources." (3 ALMA OBSERVATIONS)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum flux densities**: Elliptical Gaussian fit to visibilities; point-source fit if a/sigma_a<5; aperture photometry with curve of growth for resolved disks  
  > "We measured continuum flux densities by fitting elliptical Gaussians to the visibility data with *uvmodelfit* in CASA." (4.1 Continuum Emission)
   - software: CASA uvmodelfit
   - parameter: point-source model if a/uncertainty < 5  
  > "If the ratio of $a$ to its uncertainty was less than five, a point-source model with three free parameters" (4.1 Continuum Emission)
   - assumption: inclination derived from axis ratio assuming circular disk  
  > "the inclination, $i$, derived from $r$ assuming circular disk structure" (4.1 Continuum Emission)
   - fitting: uvmodelfit least squares; aperture uncertainty from random apertures  
  > "Uncertainties were estimated by taking the standard deviation of the flux densities measured within a similarly sized aperture placed randomly" (4.1 Continuum Emission)
   - validation: _not stated_
3. **Measure line fluxes**: Aperture photometry on zero-moment maps; upper limit 3x uncertainty in beam-sized aperture  
  > "For non-detections, we took an upper limit of $3\times$ the uncertainty when using an aperture of the same size as the beam" (4.2 Line Emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust masses**: Optically thin isothermal Hildebrand relation  
  > "Assuming dust emission at sub-mm wavelengths is isothermal and optically thin, the sub-mm continuum flux at a given wavelength ($F_{\nu}$) is directly related to the mass of the emitting dust" (5.1 Dust Masses)
   - parameter: T_dust = 20 K; kappa = 10 cm^2/g at 1000 GHz; beta = 1  
  > "We took the dust grain opacity, $\kappa_{\nu}$, as 10 cm$^{2}$ g$^{-1}$ at 1000 GHz and used an opacity power-law index of $\beta=1$" (5.1 Dust Masses)
   - assumption: T_dust=20 K, median for Taurus disks; not scaled with L*  
  > "we do not scale $T_{\rm dust}$ with $L_{\ast}$" (5.1 Dust Masses)
   - fitting: _not stated_
   - validation: Opacity argument: Ossenkopf & Henning show kappa cannot account for factor ~10 gas-to-dust discrepancy  
  > "the dust opacity, $\kappa$, used in Equation [\[eqn-mass\]](#eqn-mass) does not change sufficiently to account for the factor of $\sim$10 discrepancy" (6.3 Gas Depletion)
5. **Derive gas masses**: Compare 13CO and C18O line luminosities to WB14 grids; log-mean of grid points within ±3sigma, with min/max limits  
  > "we calculated the mean (in log space) of the WB14 model grid points within $\pm$3$\sigma$ of our measured $^{13}$CO and C$^{18}$O line luminosities" (5.2 Gas Masses)
   - parameter: line luminosity errors include 10% flux calibration in quadrature  
  > "The line luminosity uncertainties included the statistical errors in Table [3](#tab-gas) and a 10% absolute flux calibration error (added in quadrature)." (5.2 Gas Masses)
   - assumption: [CO]/[H2]=1e-4; [CO]/[13CO]=70; [CO]/[C18O]=550 or 1650  
  > "WB14 assumed an ISM-like $\rm {[CO]/[H_2]}=10^{-4}$ abundance and isotopologue ratios of ${\rm [CO]/[^{13}CO]} = 70$ and ${\rm [CO]/[C^{18}O]} = 550$ or 1650." (6.3 Gas Depletion)
   - fitting: _not stated_
   - validation: _not stated_
6. **Stack undetected sources**: Center images on expected positions, scale flux to 200 pc, aperture photometry on stacks  
  > "Before stacking, we centered each image on the expected source location and scaled the flux to 200 pc." (5.3 Stacked Non-detections)
   - fitting: _not stated_
   - validation: Mean offsets of detections from phase centers smaller than beam  
  > "both smaller than the average beam size" (5.3 Stacked Non-detections)
7. **Mdust-M* and Mgas-M* correlations**: Bayesian linear regression (Kelly 2007) with 100 MC runs for missing stellar masses; Cox proportional hazard test  
  > "We combined the posterior distributions of 100 MC runs, finding a positive relation between ${\rm log}(M_{\rm dust})$ and ${\rm log}(M_{\ast})$" (6.1 Correlations with Stellar Mass)
   - software: R, survival package
   - fitting: Kelly (2007) Bayesian linear regression handling errors, upper limits, intrinsic scatter  
  > "This technique characterizes linear correlations given measurement errors, upper limits, and intrinsic scatter." (6.1 Correlations with Stellar Mass)
   - validation: Same results when removing sources without M*, and with other evolutionary models  
  > "Note that we find the same results to within errors when simply removing the sources with unknown stellar masses." (6.1 Correlations with Stellar Mass)
8. **Compare dust mass distributions with Taurus and Upper Sco**: Kaplan-Meier cumulative distributions and two-sample tests in ASURV; MC two-sample tests matching spectral types (10^4 runs)  
  > "calculated using the Kaplan-Meier estimator in the ASURV package (cite: 1992ASPC...25..245L) to include upper limits" (6.2 Comparison to Other Regions)
   - software: ASURV
   - assumption: T_dust=20 K; distances 145 pc (Upper Sco), 140 pc (Taurus); M*>0.1 Msun  
  > "We assumed $T_{\rm dust}=20$ K for all disks and adopted distances of 145 pc for Upper Sco" (6.1 Correlations with Stellar Mass)
   - fitting: _not stated_
   - validation: Consistent results with Taurus as reference sample  
  > "We found consistent results when using Taurus as the reference sample instead of Lupus." (6.2 Comparison to Other Regions)

## Software

- **CASA** 4.4.0: calibration, imaging, uvmodelfit  
  > "Data calibration and imaging were performed using CASA 4.4.0." (3 ALMA OBSERVATIONS)
- **R (survival package)** survival 2.38: Cox proportional hazard test for censored data  
  > "implemented in the `R Project for Statistical Computing`" (6.1 Correlations with Stellar Mass)
- **ASURV** : Kaplan-Meier estimator and two-sample tests with upper limits  
  > "calculated using the Kaplan-Meier estimator in the ASURV package" (6.2 Comparison to Other Regions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum detections | 62 of 89 | not stated | sources | 2 | Of the 89 sources, 62 were detected with $>3\sigma$ significance |
| 13CO detections | 36 | not stated | sources | 3 | Of the 89 targets, 36 were detected in $^{13}$CO while only 11 were detected in C$^{18}$O |
| Mean stacked continuum of undetected sources | 0.08 | 0.06 | mJy | 6 | We measured a mean signal of $0.08\pm0.06$ mJy |
| 3sigma upper limit on mean dust mass of undetected sources | 0.03 | not stated | Earth masses | 6 | $\sim$6 Lunar masses (0.03 $M_{\oplus}$) |
| Mdust-M* slope (Lupus) | 1.8 | 0.4 | dimensionless | 7 | with a slope of $1.8\pm0.4$ and dispersion of $0.9\pm0.2$ dex |
| Mdust-M* dispersion (Lupus) | 0.9 | 0.2 | dex | 7 | with a slope of $1.8\pm0.4$ and dispersion of $0.9\pm0.2$ dex |
| Mdust-M* slope (Taurus) | 1.7 | 0.2 | dimensionless | 7 | we find a similar slope ($1.7\pm0.2$) and dispersion ($0.7\pm0.1$) for Taurus disks |
| Mdust-M* slope (Upper Sco) | 2.4 | 0.4 | dimensionless | 7 | a steeper slope ($2.4\pm0.4$) |
| Mean dust mass Lupus / Taurus / Upper Sco | 15 / 15 / 5 | 3 / 2 / 3 | Earth masses | 8 | Lupus and Taurus have consistent mean dust masses ($15\pm3$ $M_{\oplus}$ and $15\pm2$ $M_{\oplus}$, respectively), while Upper Sco has a significantly lower mean dust mass ($5\pm3$ $M_{\oplus}$) |
| Probability of no Mgas-M* correlation | 0.01 | not stated | dimensionless | 7 | with a 0.01 probability of no correlation on average |
| Average gas-to-dust ratio of stacked continuum+13CO sources | ~7 | not stated | dimensionless | 6 | giving an average gas-to-dust ratio of only $\sim$7 |
| Fraction of transition disks with resolved cavities | 10% (6/62) | not stated | fraction | 0 | the fraction of TDs in our Lupus sample with resolved cavities is 10% (6/62) |

## Qualitative findings

- Typical Lupus disks have gas masses well below MMSN and gas-to-dust ratios below the ISM value of 100 (assuming ISM-like CO abundance).  
  > "typical disks in Lupus have gas masses well below the MMSN and gas-to-dust ratios lower than the inherited ISM value" (6.3 Gas Depletion)

## Claim tuples

- H: Mdust correlates with M* in Lupus | E: Bayesian regression with censored data | R: slope 1.8±0.4, dispersion 0.9±0.2 dex; p<0.0005 of no correlation | F: Positive Mdust-M* correlation, similar to Taurus | **supported**
- H: Mgas correlates with M* | E: Cox test with MC stellar masses | R: 0.01 probability of no correlation, slope not determinable | F: Tentative first evidence of positive correlation | **partially**
- H: Lupus dust masses differ from other regions | E: ASURV and MC two-sample tests | R: Lupus mean 3x higher than Upper Sco; indistinguishable from Taurus | F: Dust mass evolves between 1-3 Myr and 5-10 Myr | **supported**
- H: Lupus disks are gas-depleted | E: WB14 model-based gas masses from 13CO/C18O | R: Most Mgas ≲1 MJup, gas-to-dust <100 | F: Rapid gas depletion unless CO is depleted | **partially**
- H: Undetected disks have very little dust | E: Stacking 27 continuum non-detections | R: Mean 0.08±0.06 mJy; ≲0.03 Mearth | F: Rapid evolution to debris-disk levels once clearing begins | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple single-opacity, single-temperature dust mass to ease comparison with other surveys  
  > "to ease interpretation and comparison with surveys of other regions" (5.1 Dust Masses)
- Alternative: Scaling T_dust with L* rejected due to missing L* values and survey inconsistency  
  > "we do not scale $T_{\rm dust}$ with $L_{\ast}$ (cite: 2013ApJ...771..129A) because" (5.1 Dust Masses)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas masses depend inversely on assumed [CO]/[H2] and isotopologue ratios; CO depletion would raise gas masses  
  > "The main caveat with our derived gas masses is that they depend inversely on the assumed ${\rm [CO]/[H_{2}]}$ molecular abundance" (6.3 Gas Depletion)
- Caveat (inferred, ours): Gas masses rely on a parametrized model grid with an ad hoc factor-3 C18O reduction
- Caveat (inferred, ours): Uniform 20 K dust temperature ignores luminosity dependence
- Caveat (inferred, ours): Short snapshot integrations give many upper limits
- Caveat (inferred, ours): Several inputs are unpublished (in prep)

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code (public via archive after proprietary period); not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00220.S." (Acknowledgements)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: WB14 model grid values
- Missing: Stellar masses from in-prep papers
- Missing: Sz 82 data
- Missing: Clean parameters and aperture radii
- Data volume (inferred): ~50-200 GB raw for one Cycle 2 project of ~90 short-integration fields
- Score (inferred): 3/5, Data and main recipe are given, but imaging details, aperture choices, model grids and in-prep inputs are missing.
- Rediscovery candidate: no, Key inputs (WB14 grids, stellar masses, Sz 82) come from external or unpublished sources and imaging details are incomplete.

## Links

- Method: (cite: 2014ApJ...788...59W) (WB14 gas mass model grids)
- Method: (cite: 2013ApJ...771..129A) (Taurus dust mass survey and comparison methodology)
- Method: (cite: 2007ApJ...665.1489K) (Bayesian regression method)
- Companion: Miotello et al., submitted (isotope-selective photodissociation models for Lupus)
- Companion: van der Marel et al., in prep. (transition disk analysis)
- Companion: Barenfeld et al. (submitted) (Upper Sco ALMA survey)
- Related: Taurus sub-mm survey (Andrews et al. 2013)
- Related: Upper Sco ALMA survey (Barenfeld et al.)

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
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 91,
  "stated": 59,
  "rate": 0.648
 },
 "evidence_ok": true
}
```
