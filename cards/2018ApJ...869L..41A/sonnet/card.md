# The Disk Substructures at High Angular Resolution Project (DSHARP). I. Motivation, Sample, Calibration, and Overview

`2018ApJ...869L..41A` | The Astrophysical Journal Letters 2018 | first author: Andrews, Sean M. | arXiv: 1812.04040 | DOI: 10.3847/2041-8213/aaf741

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: Do protoplanetary disks show small-scale substructures in the distribution of mm-sized solids, and what are their prevalence, morphologies, spacings and amplitudes, as seen at ~5 au resolution in 240 GHz continuum for 20 nearby disks?  
  > "The primary goal of DSHARP is to find and characterize substructures in the spatial distributions of solid particles for a sample of 20 nearby protoplanetary disks" (abstract)
- Target **DSHARP sample of 20 disks (HT Lup, GW Lup, IM Lup, RU Lup, Sz 114, Sz 129, MY Lup, HD 142666, HD 143006, AS 205, SR 4, Elias 20, DoAr 25, Elias 24, Elias 27, DoAr 33, WSB 52, WaOph 6, AS 209, HD 163296)**: coordinates 2MASS designations given in Table 1; no other coordinates stated  
  > "Target distances ($d$) were derived from *Gaia* DR2 parallax measurements (cite: gaia_dr2), following (cite: astraatmadja16) for a flat $d$ prior." (Survey Design and Sample); z/distance 101–165 pc (Table 1; Elias 27: 116 +19/-10 pc)  
  > "Target distances ($d$) were derived from *Gaia* DR2 parallax measurements (cite: gaia_dr2), following (cite: astraatmadja16) for a flat $d$ prior." (Survey Design and Sample); distance from Gaia DR2 parallaxes, following Astraatmadja & Bailer-Jones 2016 with a flat distance prior  
  > "Target distances ($d$) were derived from *Gaia* DR2 parallax measurements (cite: gaia_dr2), following (cite: astraatmadja16) for a flat $d$ prior." (Survey Design and Sample)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2013.1.00226.S, 2013.1.00694.S, 2013.1.00798.S, 2013.1.00498.S, 2015.1.00964.S, 2011.0.00531.S, 2015.1.00486.S, 2013.1.00366.S, 2013.1.00601.S
- bands: Band 6 (240 GHz, 1.25 mm)  
  > "All measurements used the Band 6 receivers and correlated data from four spectral windows (SPWs) in dual polarization mode." (4 Observations)
- frequencies and spectral setup: 3 continuum SPWs at 232.6, 245.0, 246.9 GHz (128 channels, 1.875 GHz each); 1 SPW at 12CO J=2-1 (938 MHz, 3840 channels, 488 kHz spacing)  
  > "The continuum was sampled in three SPWs, centered at 232.6, 245.0, and 246.9 GHz, each with 128 channels spanning 1.875 GHz (31.25 MHz per channel)." (4 Observations); "covered a bandwidth of 938 MHz in 3840 channels (488 kHz channel spacing, 0.64 km s$^{-1}$ velocity resolution)" (4 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Compact C40-5 (15 m–1.1 km) plus extended C40-8/C40-9 (up to ~12–15 km); archival compact data for some targets  
  > "The compact observations used an array with baseline lengths from 15 m to 1.1 km (a resolution of $\sim$0.25$''$)." (4 Observations); "The Cycle 4 configuration schedule was set to provide the requisite resolution (with baseline lengths out to 6.8–12.6 km) during 2017 June and July." (2 Survey Design and Sample)
- baselines: _not stated_
- angular resolution: ~0.035'' (5 au) FWHM target; fiducial continuum beams ~22–67 mas (Table 4)  
  > "very high resolution ($\sim$0.035$''$, or 5 au, FWHM) observations of their 240 GHz (1.25 mm) continuum emission" (abstract)
- max recoverable scale: FWHM continuum and CO emission scales ≲2'', spatial filtering negligible with compact data  
  > "The FWHM continuum and CO (per channel) emission scales are $\lesssim$ 2$''$, so spatial filtering should be negligible" (4 Observations)
- sensitivity: 10–20 µJy/beam in combined self-calibrated continuum data  
  > "The typical noise measured in the combined, self-calibrated datasets is 10–20 $\mu$Jy beam$^{-1}$ (0.1–0.5 K)." (4.2 Self-Calibration)
- time on source: ~12 min per source compact; ~35 min per execution extended (two executions typical)  
  > "These observations cycled between nearby targets and totaled $\sim$12 minutes of integration time per source." (4 Observations); "each with $\sim$35 minutes of on-source integration time" (4 Observations)
- observing dates: 2017 May–November  
  > "The DSHARP ALMA observations were conducted in 2017 May–November as part of program 2016.1.00484.L." (4 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.538 GHz)
- Other facility **Gaia DR2**: Parallax distances for the sample  
  > "Target distances ($d$) were derived from *Gaia* DR2 parallax measurements (cite: gaia_dr2)" (Survey Design and Sample)
- External data: Literature spectral types, Teff, L*, and accretion luminosities for host stars (Table 1)  
  > "the references for the quoted SpT, {$T_{\rm eff}$, $L_\ast$}, and accretion luminosity measurements, respectively" (Table 1 notes) [from Table 1 refs 1–15 (e.g., (cite: alcala17), (cite: fairlamb15), (cite: luhman12))]
- External data: Archival ALMA compact-configuration datasets for 8 targets  
  > "We relied on archival ALMA observations of 5 targets (IM Lup, HD 142666, Elias 24, Elias 27, HD 163296) instead of obtaining new compact data" (4 Observations) [from (cite: oberg15); (cite: cleeves17); (cite: pinte18); (cite: salyk14); (cite: dipierro18); (cite: perez16); (cite: huang16); (cite: fedele18); (cite: flaherty15); (cite: isella16)]
- External data: Previous ~0.3'' resolution continuum observations used for sample selection  
  > "This metric requires previous continuum observations at modest (0.3$''$) resolution for selection" (2 Survey Design and Sample) [from (cite: andrews09; andrews10b; ansdell16; barenfeld16)]
- External data: Median Class II SED for comparison  
  > "Relative to the median SED (normalized at 1.5 $\mu$m) of larger samples of Class II targets (cite: ribas17)" (2 Survey Design and Sample) [from (cite: ribas17)]
- Simulation/model as data: MIST stellar evolutionary models used to derive stellar masses and ages  
  > "were adopted to derive masses ($M_\ast$) and ages ($t_\ast$) based on the `MIST` models (cite: choi16)" (2 Survey Design and Sample)

## Processing

### Calibration

- pipeline or manual: Standard ALMA pipeline by ALMA staff, followed by custom self-calibration and alignment  
  > "The first step was a standard ALMA pipeline calibration. This procedure was performed by ALMA staff separately for the compact and extended data" (4.1 Pipeline Calibration)
- casa version: CASA v4.7.2 or v5.1.1 (pipeline); v5.1.1 for self-calibration  
  > "using `CASA` `v4.7.2` or `v5.1.1` for datasets that were processed before or after 2017 November, respectively" (4.1 Pipeline Calibration); "using `CASA` `v5.1.1` and a set of custom `python` routines" (4.2 Self-Calibration)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Second quasar in the calibrator list, with power-law model from Band 3/7 monitoring tied to planets/moons  
  > "The flux density in each SPW for that quasar is determined from a power-law spectral model based on bi-monthly monitoring in ALMA Bands 3 and 7" (4.1 Pipeline Calibration)
- flux scale uncertainty: ~10% claimed; 5–25% mismatches between datasets, rescaled to within 5%  
  > "The claimed calibration accuracy is $\sim$10%" (4.4 Astrometric and Flux Scale Alignment); "the majority exhibited 15–25% discrepancies for at least one dataset" (4.4 Astrometric and Flux Scale Alignment)
- self calibration: Compact: phase-only 60, 30, 18, 6 s then one amplitude (scan interval); combined: phase 900, 360, 180, 60, 30 s, one amplitude iteration  
  > "stepping down the solution interval (60, 30, 18, and 6 s)" (4.2 Self-Calibration); "The phases for this combined dataset were iteratively self-calibrated on solution intervals of {900, 360, 180, 60, 30 s}" (4.2 Self-Calibration)

### Imaging

- task: tclean  
  > "All imaging was performed with the `tclean` task." (4.3 Imaging During Self-Calibration)
- deconvolver: Multi-scale, multi-frequency synthesis (flat spectrum); scales target-dependent: point, ~θb, 2–3θb, further scales up to mask radius  
  > "We used the multi-scale, multi-frequency synthesis (assuming a flat spectrum) deconvolution mode (cite: cornwell08) with a Briggs `robust`=0.5 weighting scheme." (4.3 Imaging During Self-Calibration)
- weighting robust: Briggs robust = 0.5 during self-calibration; fiducial images tailored per target (Table 4)  
  > "with a Briggs `robust`=0.5 weighting scheme" (4.3 Imaging During Self-Calibration)
- uv taper: Target-dependent tapers in fiducial images (Table 4); CO tapers in Table 5  
  > "this involved adopting a visibility weighting scheme that traded SNR for resolution, as well as a visibility taper to improve the PSF symmetry" (4.5 Fiducial Images)
- cell size: 30 mas (compact, to primary beam); 3 mas for combined data  
  > "we used 9$''$-wide images with 3 mas pixels (again, $\sim$10 pixels per $\theta_b$) for the combined datasets" (4.3 Imaging During Self-Calibration)
- image size: 26'' (primary beam FWHM) for compact; 9''-wide for combined  
  > "we imaged out to the primary beam FWHM (26$''$) with 30 mas pixels" (4.3 Imaging During Self-Calibration)
- masking: Elliptical masks reflecting target geometry, padded around emission  
  > "Elliptical masks were designed to reflect the target geometry (aspect ratio, position angle) and pad the outer reaches of the emission distribution." (4.3 Imaging During Self-Calibration)
- multiscale scales: _not stated_
- continuum subtraction: Pseudo-continuum made by flagging ±25 km/s around CO line; CO visibilities continuum-subtracted for channel maps  
  > "A pseudo-continuum dataset was created by flagging data within $\pm$25 km s$^{-1}$ from the CO $J$=2$-$1 line center and averaging into 125 MHz channels." (4.2 Self-Calibration)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Compact self-calibrated first, then combined with extended data and self-calibrated jointly  
  > "the compact (already self-calibrated) and extended datasets were combined" (4.2 Self-Calibration)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 13–25 µJy/beam for fiducial continuum images (Table 4)  
  > "HD 142666 | 231.9 | $32 \times 22$, | 13, | 1.28, | 130" (Table 4)

### Inherited from earlier work

- Stellar mass and age derivation methodology  
  > "following the methodology described by (cite: andrews18)" (2 Survey Design and Sample) [from (cite: andrews18)]
- Flat-prior distance estimation from Gaia parallaxes  
  > "following (cite: astraatmadja16) for a flat $d$ prior" (2 Survey Design and Sample) [from (cite: astraatmadja16)]
- Scaling of 340 GHz fluxes with I_nu ∝ nu^2.5 for sample selection  
  > "we assumed that $I_\nu \propto \nu^{2.5}$ (cite: aw05)" (2 Survey Design and Sample) [from (cite: aw05)]
- Setups and strategies of archival compact observations  
  > "The setups, observing strategies, and weather conditions are described in the listed references." (4 Observations) [from Table 3 references (cite: oberg15; cleeves17; pinte18 etc.)]

### Not stated but needed to reproduce (our reading)

- Exact deconvolution scales, masks and noise thresholds per target (only in released scripts)
- Per-target self-calibration choices, reference antennas and stopping iteration
- Which datasets required flux rescaling and the reference dataset chosen
- Per-target astrometric shifts applied
- Robust value for many fiducial images (blank in Table 4 text)
- Line-free/continuum channel definition for CO per target

## Analysis recipe

1. **Pipeline calibration**: Standard ALMA pipeline by ALMA staff on compact and extended data (WVR, bandpass, flux, gain)  
  > "The first step was a standard ALMA pipeline calibration." (4.1 Pipeline Calibration)
   - software: CASA
   - parameter: CASA v4.7.2 or v5.1.1 depending on processing date  
  > "using `CASA` `v4.7.2` or `v5.1.1` for datasets that were processed before or after 2017 November, respectively" (4.1 Pipeline Calibration)
   - fitting: _not stated_
   - validation: _not stated_
2. **Align astrometry and flux scales between observations**: Gaussian-fit centroids per execution, fixvis/fixplanets phase shifts; compare deprojected azimuthally averaged visibilities at 200–500 kλ and rescale with gaincal  
  > "We measure emission centroid positions with Gaussian fits in the image plane for each individual observation and calculate the offsets relative to the highest quality extended dataset." (4.4 Astrometric and Flux Scale Alignment); "We selected a reference dataset and used the `gaincal` task to re-scale the outlier datasets." (4.4 Astrometric and Flux Scale Alignment)
   - software: CASA
   - parameter: Relative flux scales consistent within 5%  
  > "noticeably improved self-calibration results were obtained if the relative flux scales between observations were consistent within 5%" (4.4 Astrometric and Flux Scale Alignment)
   - fitting: _not stated_
   - validation: Checked deprojected visibilities between datasets  
  > "we inspected the deprojected (according to the Gaussian fit geometries noted above), azimuthally-averaged visibilities from different datasets" (4.4 Astrometric and Flux Scale Alignment)
3. **Iterative self-calibration of compact then combined data**: Phase-only iterations with decreasing solution intervals then one amplitude iteration; images made after each iteration with tclean  
  > "This self-calibration sequence is stopped after reaching a solution interval on the record length (6 s) or if the peak SNR does not increase by $> 5$% from the previous iteration." (4.2 Self-Calibration)
   - software: CASA, tclean
   - parameter: Combined data: SPWs combined; applymode='calonly' for antenna pairs with SNR ≤ 1.5  
  > "For antenna pairings with SNR $\le 1.5$ on these intervals, the self-calibration solutions were not applied but the corresponding data were not flagged" (4.2 Self-Calibration)
   - fitting: _not stated_
   - validation: PSF sidelobe effects tested with different weightings/tapers; negligible impact on self-calibration  
  > "Direct comparisons (of both visibilities and images) between these variants and the standard methodology outlined above demonstrated that the PSF features had negligible impact on the self-calibration." (4.3 Imaging During Self-Calibration)
4. **Make fiducial continuum images and CO channel maps**: tclean with per-target weighting and taper to minimize PSF artifacts; CO continuum-subtracted and imaged in ~0.35 km/s LSRK channels with shorter-baseline weighting and taper  
  > "The continuum imaging followed the methodology outlined in Section [4.3](#sec:imaging), but was tailored to individual sources with the aim of minimizing PSF artifacts." (4.5 Fiducial Images); "We compromised by increasing the relative weight of shorter baselines and employing a modest taper." (4.5 Fiducial Images)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive host star properties**: Gaia DR2 distances; Teff and L* (rescaled) fit with MIST models for mass and age  
  > "Literature estimates of the effective temperatures ($T_{\rm eff}$) and luminosities ($L_\ast$; re-scaled for the appropriate $d$) were adopted to derive masses ($M_\ast$) and ages ($t_\ast$) based on the `MIST` models" (2 Survey Design and Sample)
   - software: ScottiePippen
   - assumption: flat distance prior  
  > "following (cite: astraatmadja16) for a flat $d$ prior" (2 Survey Design and Sample)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v4.7.2 / v5.1.1: Pipeline calibration, self-calibration, imaging  
  > "All calibration tasks are performed with the `CASA` package (cite: mcmullin07) and a small supplement of `python` tasks." (4 Calibration and Imaging)
- **tclean** : All imaging  
  > "All imaging was performed with the `tclean` task." (4.3 Imaging During Self-Calibration)
- **fixvis** : Phase shifts to align datasets  
  > "The `fixvis` task then implements the appropriate phase adjustments." (4.4 Astrometric and Flux Scale Alignment)
- **fixplanets** : Reconcile different pointing centers  
  > "we manually reconcile them with the `fixplanets` task" (4.4 Astrometric and Flux Scale Alignment)
- **gaincal** : Rescale outlier flux datasets  
  > "used the `gaincal` task to re-scale the outlier datasets" (4.4 Astrometric and Flux Scale Alignment)
- **ScottiePippen** : Listed in software section (stellar parameter inference)  
  > "`ScottiePippen` (cite: czekala16)" (Software)
- **MIST** : Stellar evolutionary models for masses and ages  
  > "based on the `MIST` models (cite: choi16)" (2 Survey Design and Sample)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Typical peak SNR improvement from compact-data self-calibration | 3 | not stated | factor | 3 | The typical peak SNR increased by a factor of 3; the resulting noise was 30 $\mu$Jy beam$^{-1}$ (10 mK) for a $\sim$0.25$''$ beam. |
| Typical peak SNR improvement from combined-data self-calibration | 40% | not stated | percent | 3 | This self-calibration of the combined datasets resulted in a typical improvement of 40% in the peak SNR |
| Noise in combined self-calibrated continuum data | 10–20 | not stated | µJy/beam | 3 | The typical noise measured in the combined, self-calibrated datasets is 10–20 $\mu$Jy beam$^{-1}$ (0.1–0.5 K). |
| Median WVR phase RMS improvement (extended data) | ~1.7 | range 1.2–3 | factor | 1 | the WVR corrections improved the median RMS phase variations by a factor of $\sim$1.7 |
| Flux scale mismatches between datasets | majority 15–25%; a third 5–10% | not stated | percent | 2 | About a third of the sample had 5–10% mismatches, but the majority exhibited 15–25% discrepancies for at least one dataset. |
| Sample stellar mass range | 0.2–2 | not stated | Msun | 5 | The sample hosts exhibit a range of young star properties, with $M_\ast \approx 0.2$–2 $M_\odot$ |
| Sample average continuum flux density | 150 | not stated | mJy | 0 | The DSHARP averages are $M_\ast \approx 0.8$ $M_\odot$ (spectral type K7), $F_\nu \approx 150$ mJy, and $R_{\rm eff} \approx 50$ au |

## Qualitative findings

- Continuum substructures are ubiquitous in the sample, at radii from 5 au to >150 au  
  > "Continuum substructures are ubiquitous in this sample, as can be deduced from Figure [\[fig:gallery\]](#fig:gallery)." (6 Overview)
- Most common substructures are concentric rings and gaps; spirals less common; azimuthal asymmetries rare  
  > "The most common form of these substructures are concentric bright rings and dark gaps." (6 Overview); "Azimuthal asymmetries are rare in this sample." (6 Overview)
- Sample is biased toward bright, large disks and massive, accreting hosts  
  > "it is worth emphasizing that this range is not representative of the general population" (2 Survey Design and Sample)

## Claim tuples

- H: Are substructures common in large, bright protoplanetary disks? | E: Imaged 240 GHz continuum at ~35–50 mas for 20 disks | R: Small-scale substructures seen in all targets, often FWHM ≲10 au | F: Substructures are ubiquitous in this sample | **supported**
- H: Self-calibration and combining configurations yield reliable high-resolution images despite PSF sidelobes | E: Repeated self-calibration with different weightings/tapers and compared | R: PSF features had negligible impact on self-calibration | F: Standard homogeneous self-calibration is robust | **supported**
- H: Observed ring sizes and amplitudes reflect dust trapped in gas pressure bumps and planet-disk interactions | E: Summarized companion analyses | R: Ring sizes/amplitudes consistent with pressure bumps; simulations suggest sub-Jupiter planets | F: Plausible explanations offered in companion papers | **partially**

## Reasoning

- Why this data: Band 6 (~240 GHz) was optimal given ALMA Cycle 4 Large Program restrictions and the resolution/sensitivity goals  
  > "The combination of these criteria and ALMA technical restrictions meant that the optimal observing frequency was in the vicinity of 240 GHz (Band 6)." (2 Survey Design and Sample)
- Why this method: _not stated_
- Alternative: Higher frequency observations rejected: not permitted for Cycle 4 Large Programs, and high optical depth would limit discovery to deep gaps  
  > "Higher frequency observations at comparable (or better) resolution were not permitted for Cycle 4 Large Programs" (2 Survey Design and Sample)
- How they decided it was enough: Self-calibration stopped when peak SNR did not improve by >5% (and map quality did not visually improve)  
  > "The sequence was stopped when the peak SNR does not increase by $> 5$% and the map quality does not visually improve." (4.2 Self-Calibration)
- Limitation (authors): Sample is biased to bright, large disks and earlier spectral types, not representative of the general population  
  > "this range is not representative of the general population" (2 Survey Design and Sample)
- Limitation (authors): CO data not sensitive enough for useful channel maps at best resolution; cloud contamination in many targets  
  > "The DSHARP data are generally not sensitive enough to reconstruct useful channel maps of the emission line at the best available resolution." (4.5 Fiducial Images)
- Caveat (inferred, ours): Per-target imaging parameters live in released scripts, so the paper alone does not fix the final images
- Caveat (inferred, ours): Flux calibration mismatches of 15–25% were corrected ad hoc by a chosen reference dataset
- Caveat (inferred, ours): Few quantitative results; main science is in companion papers
- Caveat (inferred, ours): Sample selection biases limit prevalence statements

## Reproducibility

- Data public (paper): Calibrated visibilities, images, scripts released publicly  
  > "The DSHARP data – including visibilities, images, calibration scripts, and more – are released for community use at <https://almascience.org/alma-data/lp/DSHARP>." (abstract)
- Products in archive: Release goes beyond standard ALMA archive products  
  > "we have released a suite of data products that go beyond the standard contents in the ALMA archive" (5 Data Release)
- Code: CASA scripts and python modules used to calibrate and image the data are released  
  > "(1) `CASA` scripts and associated `python` modules used to calibrate and image the data" (5 Data Release)
- Missing: Per-target calibration scripts are external (data release)
- Missing: Exact per-target masks, scales, thresholds
- Missing: Which executions needed flux/astrometric correction
- Data volume (inferred): Large: ~20 targets, multiple executions each in Band 6 with long baselines; likely several TB raw, hundreds of GB for calibrated measurement sets
- Score (inferred): 4/5, Data, scripts and calibrated products are public and the procedure is detailed, but per-target parameters reside in released scripts and results are mostly qualitative.
- Rediscovery candidate: no, Data are public and the recipe is largely given, but the paper's main results are qualitative and per-target details are in external scripts.

## Links

- Method: (cite: cornwell08) (Multi-scale multi-frequency deconvolution used in tclean)
- Method: (cite: andrews18) (Stellar parameter derivation methodology)
- Companion: Huang et al. 2018a (DSHARP II) (Rings and gaps analysis)
- Companion: Huang et al. 2018b (DSHARP III) (Spirals)
- Companion: Kurtovic et al. 2018 (DSHARP IV) (HT Lup and AS 205 multiples)
- Companion: Birnstiel et al. 2018 (DSHARP V) (Fiducial dust model)
- Companion: Dullemond et al. 2018 (DSHARP VI) (Rings as dust traps in pressure bumps)
- Companion: Zhang et al. 2018 (DSHARP VII) (Planet-disk hydrodynamics simulations)
- Companion: Guzmán et al. 2018 (DSHARP VIII) (AS 209)
- Companion: Isella et al. 2018 (DSHARP IX) (HD 163296)
- Companion: Pérez et al. 2018 (DSHARP X) (HD 143006)
- Related: DSHARP (ALMA Large Program 2016.1.00484.L)

## Checks

```json
{
 "quotes": 98,
 "quotes_ok": 98,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 10,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2012.1.00694.S",
  "2013.1.00631.S"
 ],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 66,
  "rate": 0.767
 },
 "evidence_ok": true
}
```
