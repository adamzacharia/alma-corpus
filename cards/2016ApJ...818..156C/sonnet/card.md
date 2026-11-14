# A Disk-based Dynamical Constraint on the Mass of the Young Binary DQ Tau

`2016ApJ...818..156C` | The Astrophysical Journal 2016 | first author: Czekala, I. | arXiv: 1601.03806 | DOI: 10.3847/0004-637X/818/2/156

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, stellar_physics
- Question: What is the dynamical mass of the DQ Tau binary from its circumbinary CO disk, and does it agree with the spectroscopic orbit mass and pre-MS models?  
  > "These data are used to tomographically reconstruct the Keplerian disk velocity field in a forward-modeling inference framework, and thereby provide a dynamical constraint on the mass of the DQ Tau binary" (abstract)
- Target **DQ Tau**: coordinates _not stated_; z/distance 145 +/- 20 pc prior; fit d = 155 +/- 15 pc  
  > "We choose a conservative Gaussian prior on the distance with a mean of 145 pc and a width ($\sigma$) of 20 pc, meant to represent the range of possible distances to sources in the Taurus clouds (cite: torres10)." (3.1 CO Disk Modeling); distance from Taurus distance prior from Torres et al. 2010  
  > "We choose a conservative Gaussian prior on the distance with a mean of 145 pc and a width ($\sigma$) of 20 pc, meant to represent the range of possible distances to sources in the Taurus clouds (cite: torres10)." (3.1 CO Disk Modeling)

## Data provenance

- ALMA projects: 2012.1.00496.S
- bands: Band 6 (1.3 mm, 232 GHz continuum)  
  > "employing the Band 6 receivers to cover the CO, $^{13}$CO, and C$^{18}$O $J$=2$-$1 transitions in 61, 61, and 122 kHz channels, respectively" (2.1 Millimeter Interferometry)
- frequencies and spectral setup: same setup as Czekala et al. 2015; CO, 13CO, C18O J=2-1 with 61, 61, 122 kHz channels  
  > "The observations were configured with the same spectral setup as in (cite: czekala15)" (2.1 Millimeter Interferometry)
- continuum bandwidth: _not stated_
- arrays: 34 12 m antennas, separations 21 to 540 m  
  > "using 34 of its 12 m antennas with separations ranging from 21 to 540 m" (2.1 Millimeter Interferometry)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.8" x 0.6" at P.A. 145 deg  
  > "restoring with a synthesized beam with FWHM = $0.8\ensuremath{''}\times0.6\ensuremath{''}$ (at P.A. = 145$^\circ$)" (2.1 Millimeter Interferometry)
- max recoverable scale: _not stated_
- sensitivity: continuum 70 uJy/beam; CO and 13CO 8 mJy/beam per 0.1 km/s channel; C18O ~4 mJy/beam per 0.2 km/s channel  
  > "The RMS noise level is 70 $\mu$Jy beam$^{-1}$" (2.1 Millimeter Interferometry); "reach an RMS noise level of 8 mJy beam$^{-1}$ in each channel" (2.1 Millimeter Interferometry)
- time on source: ~28 minutes  
  > "The total on-source integration time was $\sim$28 minutes." (2.1 Millimeter Interferometry)
- observing dates: 2015 May 24  
  > "ALMA observed the DQ Tau system on 2015 May 24" (2.1 Millimeter Interferometry)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1 (not stated)
- Line: C18O J=2-1 (not stated)
- Other facility **CfA optical spectrographs and TRES (FLWO 1.5 m)**: Radial velocities for the updated orbital solution  
  > "The first set consists of 30 spectra obtained at the Harvard-Smithsonian Center for Astrophysics (CfA) between 1984 and 2005" (2.2 Optical Spectroscopy)
- Other facility **Lick, Keck, McDonald**: 22 RV differences from Mathieu et al. 1997  
  > "collected with instruments at the Lick Observatory, the Keck Observatory, and the McDonald Observatory" (2.2 Optical Spectroscopy)
- External data: BVRIJ photometry used for the HR-diagram fit  
  > "we explored a two-component fit to the $BVRIJ$ photometry compiled by (cite: rydgren84), (cite: kolotilov89), and (cite: skrutskie06) (cite: andrews13)." (4.2 Comparison to Pre-MS Evolution Models) [from Rydgren 1984; Kolotilov 1989; Skrutskie 2006; Andrews 2013]
- External data: LKM RV differences reconstructed from Table 1 of Mathieu et al. 1997  
  > "We therefore reconstructed the original velocity differences trivially from the primary and secondary “measurements” reported by (cite: mathieu97) in their Table 1." (3.2 An Updated Spectroscopic Orbital Solution) [from (cite: mathieu97)]
- External data: Infrared interferometry astrometric constraint used to enforce i > 90 deg  
  > "we employ the astrometric constraint made by (cite: boden09) from infrared interferometry measurements to enforce $i > 90\ensuremath{^\circ}$ in our analysis." (Footnote 3) [from (cite: boden09)]
- Simulation/model as data: BT-Settl synthetic photometry and pre-MS evolutionary models (Siess, Dotter, Tognelli, Baraffe)  
  > "The adopted model magnitudes were interpolated for a given {$T_{\rm eff}$, $\log g$} from the BT-Settl synthetic photometry catalog (cite: allard03) for solar metallicity." (4.2 Comparison to Pre-MS Evolution Models)

## Processing

### Calibration

- pipeline or manual: standard techniques with CASA  
  > "The visibilities were calibrated using standard techniques with the `CASA` software package (v4.3)." (2.1 Millimeter Interferometry)
- casa version: CASA v4.3  
  > "The visibilities were calibrated using standard techniques with the `CASA` software package (v4.3)." (2.1 Millimeter Interferometry)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (also bandpass)  
  > "The bright quasar J0423$-$0120 was also observed to calibrate the bandpass behavior and absolute flux levels." (2.1 Millimeter Interferometry)
- flux scale uncertainty: _not stated_
- self calibration: phase and amplitude self-cal on bright continuum  
  > "After a phase and amplitude self-calibration based on the bright continuum, the spectral line visibilities were time-averaged (to 30 s intervals) and continuum-subtracted." (2.1 Millimeter Interferometry)

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "deconvolving with the `CLEAN` algorithm" (2.1 Millimeter Interferometry)
- weighting robust: Briggs robust = 0.5  
  > "assuming a Briggs robust weighting parameter of 0.5, to balance S/N and resolution" (2.1 Millimeter Interferometry)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: done in visibility domain after self-cal  
  > "the spectral line visibilities were time-averaged (to 30 s intervals) and continuum-subtracted." (2.1 Millimeter Interferometry)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.8" x 0.6", PA 145 deg  
  > "restoring with a synthesized beam with FWHM = $0.8\ensuremath{''}\times0.6\ensuremath{''}$ (at P.A. = 145$^\circ$)" (2.1 Millimeter Interferometry)
- final rms: continuum 70 uJy/beam; CO 8 mJy/beam per channel  
  > "The RMS noise level is 70 $\mu$Jy beam$^{-1}$" (2.1 Millimeter Interferometry)

### Inherited from earlier work

- Spectral setup identical to AK Sco observations  
  > "The observations were configured with the same spectral setup as in (cite: czekala15)" (2.1 Millimeter Interferometry) [from (cite: czekala15)]
- Disk forward-modeling framework  
  > "We analyze the CO $J$=2$-$1 line emission using the framework detailed in (cite: czekala15) and (cite: rosenfeld12)." (3.1 CO Disk Modeling) [from (cite: czekala15); (cite: rosenfeld12)]
- Surface density profile follows the Lynden-Bell & Pringle similarity solution  
  > "We assume the standard (cite: lynden-bell74) similarity solution describes the radial surface density profile of the gas" (3.1 CO Disk Modeling) [from (cite: lynden-bell74)]
- RV zero-point corrections  
  > "small run-to-run corrections were applied in the manner described by (cite: latham92)" (2.2 Optical Spectroscopy) [from (cite: latham92)]
- Component masses and ages from HR diagram  
  > "we followed the formalism of (cite: jorgensen05) to derive component masses and ages" (4.2 Comparison to Pre-MS Evolution Models) [from (cite: jorgensen05)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum subtraction method details
- Which 23 CO channels were excluded (only marked in a figure)
- MCMC settings: walkers, steps, burn-in, convergence
- Image size and cell size, CLEAN masks and threshold
- Rest frequencies, grid and model setup for RADMC-3D (e.g. outer radius, resolution)
- Prior bounds on uniform parameters
- Source coordinates

## Analysis recipe

1. **Calibrate and image ALMA data**: CASA calibration, self-calibration on continuum, time-averaging to 30 s, continuum subtraction, CLEAN imaging with robust 0.5  
  > "After a phase and amplitude self-calibration based on the bright continuum, the spectral line visibilities were time-averaged (to 30 s intervals) and continuum-subtracted." (2.1 Millimeter Interferometry)
   - software: CASA
   - parameter: robust = 0.5; 0.1 km/s channels for CO  
  > "assuming a Briggs robust weighting parameter of 0.5, to balance S/N and resolution" (2.1 Millimeter Interferometry)
   - fitting: _not stated_
   - validation: _not stated_
2. **Forward-model CO visibilities of Keplerian disk**: Parametric disk model, LTE excitation, RADMC-3D ray tracing, Fourier transform to data uv points, chi2 likelihood, 23 contaminated channels excluded  
  > "We then use the `RADMC-3D` radiative transfer code (cite: dullemond12) to ray-trace spectral images, which are Fourier transformed and sampled at the same spatial frequencies as the data." (3.1 CO Disk Modeling)
   - software: RADMC-3D, emcee
   - parameter: p fixed to 1; 12-dimensional posterior  
  > "For computational expediency, we fix $p = 1$." (3.1 CO Disk Modeling)
   - assumption: Vertically isothermal, radial power-law temperature, hydrostatic equilibrium, Keplerian rotation, LTE  
  > "We simplify the scenario by assuming a vertically isothermal structure, with a radial power-law temperature profile" (3.1 CO Disk Modeling)
   - fitting: Ensemble MCMC; uniform priors except sin(i)/2 on inclination and Gaussian distance prior 145+/-20 pc; i>90 deg enforced  
  > "employing uniform (uninformative) priors on all parameters except for $i_d$ and $d$." (3.1 CO Disk Modeling)
   - validation: Model compared with data in channel maps  
  > "A comparison of the data with the model is shown in the form of channel maps in Figure [\[fig:results\]](#fig:results)." (3.1 CO Disk Modeling)
3. **Measure RVs from CfA spectra**: TODCOR two-dimensional cross-correlation with PHOENIX synthetic templates, equal temperatures assumed  
  > "using the two-dimensional cross-correlation technique TODCOR (cite: zucker94), with templates taken from a library of synthetic spectra based on PHOENIX model atmospheres" (2.2 Optical Spectroscopy)
   - software: TODCOR
   - parameter: Teff ~4000 K, vsini 14 and 11 km/s, solar metallicity, logg 3.5-4.5  
  > "The best matches to the DQ Tau spectra were found for temperatures of $\sim$4000 K" (2.2 Optical Spectroscopy)
   - fitting: _not stated_
   - validation: vsini consistent with Nguyen et al. 2012  
  > "These latter values are similar to the measurements of (cite: nguyen12)" (2.2 Optical Spectroscopy)
4. **Fit updated spectroscopic orbit**: Weighted least-squares joint fit of 33 CfA RV pairs and 22 LKM RV differences; uncertainties iteratively adjusted to reduced chi2 near unity  
  > "The 22 RV differences were combined in a weighted least-squares fit with our 33 pairs of primary/secondary velocities" (3.2 An Updated Spectroscopic Orbital Solution)
   - parameter: common gamma adopted  
  > "Consequently, the final fit assumed a common value of $\gamma$." (3.2 An Updated Spectroscopic Orbital Solution)
   - fitting: _not stated_
   - validation: Compared with CfA-only fit and Mathieu et al. 1997  
  > "Our results in Table [3](#table:orbit) are generally consistent with those of (cite: mathieu97), but with uncertainties typically reduced by factors of 2–5." (3.2 An Updated Spectroscopic Orbital Solution)
5. **Combine disk and RV constraints**: Joint posterior of M and i assuming coplanarity; dynamical distance; mutual inclination  
  > "If we assume that the binary and disk orbital planes are exactly aligned ($i = i_d$), the joint constraints from the RV and ALMA data indicate $M_\ast = 1.21\pm0.26\,M_\odot$" (4.1 Comparison of Disk- and Binary-based Constraints)
   - assumption: Disk and binary planes coplanar for combined mass  
  > "If we assume that the binary and disk orbital planes are exactly aligned ($i = i_d$)" (4.1 Comparison of Disk- and Binary-based Constraints)
   - fitting: _not stated_
   - validation: _not stated_
6. **Compare with pre-MS models**: Two-component BVRIJ photometric fit with BT-Settl, then masses and ages from pre-MS tracks assuming coevality  
  > "we followed the formalism of (cite: jorgensen05) to derive component masses and ages {$\tau$, $M_1$, $M_2$} from the predictions of pre-MS evolutionary models in the HR diagram" (4.2 Comparison to Pre-MS Evolution Models)
   - parameter: logg = 4.0 fixed; RV mass ratio prior 0.93+/-0.05; Teff prior 3900+/-250 K; R_V = 3.1  
  > "we adopted a Gaussian prior with mean of 3900 K and dispersion of 250 K on $T_1$ and $T_2$" (4.2 Comparison to Pre-MS Evolution Models)
   - assumption: Coeval stars, normal pre-MS evolution  
  > "We note that this analysis is under the assumption of coevality of the two stars, which may not necessarily be true." (4.2 Comparison to Pre-MS Evolution Models)
   - fitting: chi2 likelihood with per-band jitter terms  
  > "The model quality for a given set of parameters was determined with a $\chi^2$ likelihood function and a reasonable set of priors." (4.2 Comparison to Pre-MS Evolution Models)
   - validation: Different model sets give consistent predictions  
  > "make consistent predictions within the (considerable) uncertainties" (4.2 Comparison to Pre-MS Evolution Models)

## Software

- **CASA** 4.3: Calibration and imaging  
  > "The visibilities were calibrated using standard techniques with the `CASA` software package (v4.3)." (2.1 Millimeter Interferometry)
- **RADMC-3D** : Ray-tracing model spectral images  
  > "We then use the `RADMC-3D` radiative transfer code (cite: dullemond12) to ray-trace spectral images" (3.1 CO Disk Modeling)
- **emcee (ensemble MCMC sampler)** : Exploring posterior  
  > "We explore the 12-dimensional posterior-space with an ensemble MCMC sampler (cite: foreman-mackey13)" (3.1 CO Disk Modeling)
- **TODCOR** : Measuring component RVs  
  > "using the two-dimensional cross-correlation technique TODCOR (cite: zucker94)" (2.2 Optical Spectroscopy)
- **triangle.py** : Corner plot  
  > "Figure [\[fig:triangle\]](#fig:triangle) was generated with the `triangle.py` code (cite: foreman-mackey14)." (Acknowledgments)
- **Julia** : Programming language for analysis  
  > "This research made extensive use of the Julia programming language (cite: julia12)" (Acknowledgments)
- **Astropy** : General analysis  
  > "This research made extensive use of the Julia programming language (cite: julia12) and Astropy software package (cite: astropy13)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk-based binary mass | 1.27 | +0.46/-0.27 | Msun | 2 | $1.27_{-0.27}^{+0.46}$ |
| Disk inclination | 160 | 3 | deg | 2 | $i_d$ (${}^\circ$)                   / 160      / 3 |
| M/d | 0.0086 | +0.0021/-0.0018 | Msun/pc | 2 | $M_{\ast}/d = 0.0086_{-0.0018}^{+0.0021}\,M_{\odot}$ pc$^{-1}$ |
| M sin^2 i_d | 0.164 | 0.016 | Msun | 2 | $M_\ast\, \sin^2 i_d = 0.164\pm0.016\,M_\odot$ |
| Spectroscopic (M1+M2) sin^3 i | 0.0674 | 0.0033 | Msun | 4 | $(M_1+M_2) \sin^3 i$ ($M_{\ensuremath{\odot}}$) /  0.0674 $\pm$ 0.0033 |
| Orbital period | 15.80158 | 0.00066 | days | 4 | 15.80158 $\pm$ 0.00066 |
| Eccentricity | 0.568 | 0.013 | dimensionless | 4 | 0.568 $\pm$ 0.013 |
| Mass ratio | 0.936 | 0.051 | dimensionless | 4 | 0.936 $\pm$ 0.051 |
| Combined system mass | 1.21 | 0.26 | Msun | 5 | $M_\ast = 1.21\pm0.26\,M_\odot$ and $i = 158\pm2\ensuremath{^\circ}$ |
| Dynamical distance | 184 | 26 | pc | 5 | we estimate $d_{\rm dyn}= 184\pm26$ pc |
| Mutual inclination psi | -1.3 | 1.1 | deg | 5 | $\psi \equiv i - i_d = -1.3 \pm 1.1\ensuremath{^\circ}$ |
| Pre-MS model total mass | 1.20 | 0.16 | Msun | 6 | indicating a total binary mass of $1.20\pm0.16\,M_\odot$ |
| Continuum integrated flux density | 79 | not stated | mJy | 1 | peak intensity of $\sim$68 mJy beam$^{-1}$ and integrated flux density of 79 mJy |

## Qualitative findings

- Disk-based and RV-based masses agree and the disk and binary planes are aligned within 3 deg  
  > "the disk and binary orbital planes are aligned within 3$^\circ$ (at 3 $\sigma$ confidence)" (abstract)

## Claim tuples

- H: Disk-based dynamical mass agrees with the binary orbit mass for DQ Tau | E: Forward-model ALMA CO 2-1 and compare with updated RV orbit | R: M = 1.27 +0.46/-0.27 Msun from disk; M sin^3 i = 0.0674 Msun from orbit | F: Constraints agree well within 1 sigma | **supported**
- H: Disk and binary orbital planes are coplanar | E: Joint posterior of disk and binary inclinations | R: psi = -1.3 +/- 1.1 deg | F: Aligned within 3 deg | **supported**
- H: Pre-MS models reproduce the dynamical mass | E: Photometric HR-diagram placement and tracks | R: Total mass 1.20 +/- 0.16 Msun | F: Consistent, but limited by component uncertainties | **partially**

## Reasoning

- Why this data: DQ Tau is a cooler, younger equal-mass binary, an important supplementary test  
  > "An important supplementary test would employ a cooler and younger binary." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Mass precision limited by face-on geometry and cloud contamination  
  > "the dynamical mass precision is limited by an unfortunate combination of two factors" (Summary and Context)
- Caveat (inferred, ours): Mass depends on a distance prior; the dynamical distance is imprecise.
- Caveat (inferred, ours): 23 channels excluded for cloud contamination may bias the fit.
- Caveat (inferred, ours): Fixed p=1 and simple thermal structure.
- Caveat (inferred, ours): Systemic velocity differs between disk and orbit.

## Reproducibility

- Data public (paper): Posterior samples and code are public; ALMA project code listed  
  > "Samples from the posterior are published at <https://figshare.com/articles/MCMC_Samples/2063424>" (Table 2)
- Products in archive: _not stated_
- Code: Open-source MIT code at github.com/iancze/JudithExcalibur  
  > "The code used to perform the analysis described here is open source and freely available under an MIT license at <https://github.com/iancze/JudithExcalibur>" (Footnote 1)
- Missing: Excluded channel list
- Missing: MCMC configuration
- Missing: CLEAN parameters
- Missing: Optical spectra not available except RV table
- Data volume (inferred): ~10-30 GB raw ALMA data for one 28-minute execution
- Score (inferred): 4/5, Code and posteriors public and a clear recipe, but some imaging and MCMC details are missing.
- Rediscovery candidate: yes, Data are public in the ALMA archive, code is released and the results are numeric.

## Links

- Method: Czekala et al. 2015 (cite: czekala15) (Disk modeling framework and spectral setup)
- Method: Rosenfeld et al. 2012 (cite: rosenfeld12) (Disk modeling framework)
- Companion: Mathieu et al. 1997 (cite: mathieu97) (Original orbital solution and RV data)

## Checks

```json
{
 "quotes": 84,
 "quotes_ok": 84,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 90,
  "stated": 62,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
