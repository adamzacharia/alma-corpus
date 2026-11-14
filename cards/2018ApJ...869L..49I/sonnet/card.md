# The Disk Substructures at High Angular Resolution Project (DSHARP). IX. A High-definition Study of the HD 163296 Planet-forming Disk

`2018ApJ...869L..49I` | The Astrophysical Journal Letters 2018 | first author: Isella, Andrea | arXiv: 1812.04047 | DOI: 10.3847/2041-8213/aaf747

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks
- Question: What are the morphology of the dust rings, the CO emission geometry, temperature and dust extinction optical depth of the HD 163296 disk at ~4 au resolution, and do the asymmetries support planet-disk interaction?  
  > "The observations of the CO and dust emission inform about the vertical structure of the disk and allow us to directly constrain the dust extinction optical depth at the dust rings." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "At a distance of 101 pc (cite: gaia_dr2), HD 163296 is in several respects the poster child of disks thought to be perturbed by planets." (Introduction); distance from Gaia DR2  
  > "At a distance of 101 pc (cite: gaia_dr2), HD 163296 is in several respects the poster child of disks thought to be perturbed by planets." (Introduction)

## Data provenance

- ALMA projects: 2016.1.00484.L, 2013.1.00366.S, 2013.1.00601.S
- bands: Band 6 (~1.3 mm)  
  > "the HD 163296 disk was observed in Band 6 ($\lambda \sim 1.3$ mm) in September 2017 in configuration C40-8" (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-8 (DSHARP) plus archival shorter-baseline tracks  
  > "in configuration C40-8, which delivered baselines $B$ between 41 m and 5.8 km" (2 Observations)
- baselines: _not stated_
- angular resolution: continuum beam 0.038''x0.048''; CO beam 0.104''x0.095''  
  > "The FWHM of the synthesized beam of the presented CO maps is 0.104$''$$\times$0.095$''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.023 mJy/beam; CO rms 0.84 mJy/beam per channel  
  > "The rms noise is 0.023 mJy beam$^{-1}$, and the peak signal to noise ratio is 185." (2 Observations); "The rms noise per channel is 0.84 mJy beam$^{-1}$." (2 Observations)
- time on source: _not stated_
- observing dates: September 2017 (DSHARP track)  
  > "observed in Band 6 ($\lambda \sim 1.3$ mm) in September 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- External data: Model temperature profiles of HD 163296 compared with observations  
  > "compares the temperature inferred from the 1.25 mm dust continuum intensity to the models discussed in (cite: isella16), (cite: rosenfeld13a), and (cite: flaherty15)." (5.1 Disk temperature and dust scattering) [from Isella et al. 2016; Rosenfeld et al. 2013; Flaherty et al. 2015]
- External data: Gaussian-ring widths from radial profile fits  
  > "Here, we compare the widths of the HD 163296 rings measured by Dullemond et al. (2018)" (3.2 Width of the continuum rings) [from Dullemond et al. (2018)]
- External data: Planet-disk simulation model (0.15 MJ planet at 54 au)  
  > "The model is part of the suite of models presented in Zhang et al. (2018)" (5.2 On the origin of the dust rings) [from Zhang et al. (2018)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline plus manual flagging of project 2013.1.00366.S; self-calibration  
  > "An initial calibration of each dataset was produced by the ALMA pipeline." (2 Observations); "required manual flagging" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: Flux scales of tracks adjusted to agree within 5% on overlapping baselines  
  > "adjusted the flux scale so that the source visibility amplitude measured on overlapping baselines agrees within 5%" (2 Observations)
- self calibration: Short baselines self-calibrated and re-centered separately; then phase and amplitude self-cal of combined data (43% peak SNR gain)  
  > "The self-calibration procedure resulted in an improvement of 43% in the peak signal-to-noise ratio in the dust continuum image." (2 Observations)

### Imaging

- task: CASA tclean  
  > "The 1.25 mm dust continuum emission was imaged using the CASA task *tclean* and a robust parameter of -0.5" (2 Observations)
- deconvolver: _not stated_
- weighting robust: continuum robust = -0.5; CO Briggs robust = 0.5, no uv-tapering  
  > "we imaged it using Briggs robust=0.5 (no uv-tapering)" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: CO channels 0.32 km/s, Hanning smoothed to 0.64 km/s resolution  
  > "Channels are spaced in velocity by 0.32 km s$^{-1}$, but, due to Hanning smoothing, the velocity resolution is 0.64 km s$^{-1}$." (2 Observations)
- final beam: continuum 0.038''x0.048''; CO 0.104''x0.095''  
  > "resulting in a synthesized beam FWHM of 0.038$''$$\times$0.048$''$" (2 Observations)
- final rms: 0.023 mJy/beam continuum  
  > "The rms noise is 0.023 mJy beam$^{-1}$" (2 Observations)

### Inherited from earlier work

- Full DSHARP calibration procedure and CO imaging details  
  > "A complete description of the DSHARP data calibration procedure is presented in Andrews et al. (2018)" (2 Observations) [from Andrews et al. 2018]
- Ring/gap ellipse fitting method  
  > "The fit is performed as discussed in Huang et al. (2018)." (3.1 Morphology of the dust rings) [from Huang et al. 2018]
- Gaussian ring profile fitting and initial parameters  
  > "initialized around the parameter values obtained by a Gaussian fitting of the radial intensity profile as in Dullemond et al. (2018)" (3.2 Width of the continuum rings) [from Dullemond et al. 2018]
- CO temperature map from non-continuum-subtracted line peak  
  > "Following (cite: weaver18), we generate a CO temperature map from non-continuum subtracted line emission" (4.2 Gas temperature) [from (cite: weaver18)]
- Scattering dust temperature formalism  
  > "Using the formalism discussed in Birnstiel et al. (2018)" (5.1 Disk temperature and dust scattering) [from Birnstiel et al. 2018]

### Not stated but needed to reproduce (our reading)

- CLEAN masks, niter and threshold for tclean
- Continuum channel selection and line-free channels for CO continuum subtraction
- Self-calibration solution intervals
- emcee priors and bounds for the visibility Gaussian-ring fit
- How the azimuthal intensity ratios and 18 lines of sight were extracted
- Exact Birnstiel et al. source function parameters used for temperatures

## Analysis recipe

1. **Fit ring and gap geometry**: Fit crests and troughs with ellipses using emcee, following Huang et al. (2018)  
  > "we locate the points (x,y) corresponding to the radial maxima (or minima) of each ring (or gap), and use the python *emcee* package to calculate the ellipses" (3.1 Morphology of the dust rings)
   - software: emcee
   - fitting: Uncertainties from 16th and 84th percentiles of marginalized posterior  
  > "The uncertainties on the best fit values correspond to the 16th and 84th percentile of the marginalized posterior probability distribution." (3.1 Morphology of the dust rings)
   - validation: _not stated_
2. **Fit axisymmetric Gaussian ring model in the uv plane**: Sum of 5 Gaussian rings, Fourier transformed at observed uvs; chi2 sampled with emcee; 19 free parameters  
  > "a minimum of 5 Gaussian components are required to reproduce the observed continuum emission. In total, the model therefore has 19 free parameters" (3.2 Width of the continuum rings)
   - software: galario, emcee
   - parameter: 200 walkers, 10^4 burn-in steps, convergence after ~4x10^4 steps  
  > "We run *emcee* using 200 walkers initialized around the parameter values obtained by a Gaussian fitting of the radial intensity profile" (3.2 Width of the continuum rings)
   - assumption: Axisymmetric dust emission  
  > "We start by assuming that the dust emission is axisymmetric" (3.2 Width of the continuum rings)
   - fitting: chi2 with pipeline weights; median of posterior, 0.3th and 99.7th percentile uncertainties  
  > "while the related uncertainties correspond to the 0.3th and 99.7th percentile of the marginalized posterior probability distribution." (3.2 Width of the continuum rings)
   - validation: Compared with image-domain Gaussian fit of Dullemond et al.; B67 widths agree  
  > "For B67, we find a width of $\sim 6.6$ au, that is very close to the 6.8 au derived by Dullemond et al. (2018)." (3.2 Width of the continuum rings)
3. **Image residuals and characterize asymmetries**: Subtract best-fit Gaussian model from visibilities and image residuals; fit crescents with 2D Gaussian in polar plane  
  > "The map obtained by imaging the residual visibilities obtained by subtracting the best fit Gaussian model from the observations" (3.3 Asymmetries of the continuum emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Constrain CO emitting surface**: Compare parametric isovelocity curves with z_co = z0 (r/r0)^q to the channel maps  
  > "we obtain a good match between model and observations for $q=0.5$ and $z_{co}(100\mathrm{au}) = 30$ au." (4.1 Morphology of the CO emission)
   - assumption: i=46.7 deg, stellar mass 2.0 Msun, Keplerian rotation  
  > "Assuming the disk inclination derived from the continuum ($i=46.7$$^\circ$) and a stellar mass of 2.0 M$_\star$" (4.1 Morphology of the CO emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Measure dust extinction optical depth from CO absorption**: Ratio of unattenuated CO (from gaps) to observed back-side CO at rings along 18 azimuths; tau = ln ratio  
  > "We measure the ratio $I_{co}/I_{co}^{obs}$ for B67 and B100 along 18 different lines of sight" (4.1 Morphology of the CO emission)
   - assumption: tau_d << 1 in gaps; epsilon between 0.1 and 1  
  > "We then use the values measured within the dust gaps, where, based on the results of the previous section, $\tau_d \ll 1$" (4.1 Morphology of the CO emission)
   - fitting: _not stated_
   - validation: _not stated_
6. **CO gas temperature profile and compare with models**: Peak-intensity temperature map from non-continuum-subtracted data, deprojected with z_co  
  > "it is possible to deproject the observed CO temperature and estimate its profile as a function of the cylindrical radius $r$." (4.2 Gas temperature)
   - assumption: CO peak optically thick and in LTE  
  > "the peak of the $^{12}$CO J=2-1 line emission is optically thick and the CO rotational levels are in local thermodynamic equilibrium" (4.2 Gas temperature)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : calibration scripts and tclean imaging  
  > "the CASA script used to calibrate and image HD 163296 data" (2 Observations)
- **emcee** : MCMC for ring ellipses and visibility Gaussian fit  
  > "the $\chi^2$ is used to sample the posterior likelihood using the python package *emcee*" (3.2 Width of the continuum rings)
- **galario** : chi2 computation of synthetic visibilities (CPU version)  
  > "The calculation of $\chi^2$ was performed using the cpu-based version of python package *galario*" (3.2 Width of the continuum rings)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean disk inclination (outer rings) | 46.7 | 0.1 | deg | 1 | average inclination of (46.7$\pm$0.1)$^\circ$ |
| Mean disk position angle (outer rings) | 133.3 | 0.1 | deg | 1 | average position angle of (133.3$\pm$0.1)$^\circ$ |
| B67 Gaussian width (visibilities) | 6.56 | 0.05 | au | 2 | B67 / 67.7 / 6.84 / 0.38 / 67.08$\pm$0.03  / 6.56$\pm$0.05 |
| B100 Gaussian width (visibilities) | 5.8 | 0.1 | au | 2 | B100 / 100.0 / 4.67 / 0.24 / 101.16$\pm$0.04 / 5.8$\pm$0.1 |
| C55 crescent peak intensity | 0.64 | not stated | mJy/beam | 3 | The peak intensity is 0.64 mJy beam$^{-1}$, corresponding to a signal-to-noise ratio of 28. |
| CO emitting surface z_co(100 au) | 30 (q=0.5) | not stated | au | 4 | $q=0.5$ and $z_{co}(100\mathrm{au}) = 30$ au |
| Dust extinction optical depth B67 | 0.64 | 0.05 | dimensionless | 5 | $\tau^{ext}_d(\mathrm{B}67)=0.64\pm0.05$, $\tau^{ext}_d(\mathrm{B}100)=0.74\pm0.05$ |
| Dust extinction optical depth B100 | 0.74 | 0.05 | dimensionless | 5 | $\tau^{ext}_d(\mathrm{B}67)=0.64\pm0.05$, $\tau^{ext}_d(\mathrm{B}100)=0.74\pm0.05$ |
| CO temperature relation 30-500 au | T_co(K) ~ 87 - 0.14 (r/au) | not stated | K | 6 | $T_{co} (\mathrm{K}) \sim 87 - 0.14 (r/\mathrm{au})$ |
| Systemic velocity | 5.8 | not stated | km/s | 0 | The systemic velocity inferred from CO observations is 5.8 km s$^{-1}$ |

## Qualitative findings

- New features: dark gap at 10 au, bright ring at 15 au, crescents at 4 and 55 au  
  > "a dark gap at 10 au, a bright ring at 15 au, a dust crescent at a radius of 55 au" (abstract)

## Claim tuples

- H: Do the high-resolution continuum data reveal new substructure in HD 163296? | E: Imaging and ring fitting of 1.25 mm continuum | R: Gap at 10 au, ring at 15 au, crescents at 4 and 55 au | F: New small-scale structures in addition to the known rings | **supported**
- H: Can CO absorption constrain the dust optical depth? | E: Back-side CO dimming at rings relative to gaps | R: tau_ext 0.64 (B67), 0.74 (B100), 0.1±0.2 (B168) | F: Direct extinction optical depth measurement | **supported**
- H: Do asymmetries support planet-shaped disk? | E: Residual imaging and qualitative comparison with Zhang et al. model | R: Crescents and ring asymmetries resemble corotation features | F: Corroborates planet-disk interaction hypothesis, qualitatively | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: C4 crescent could be a vortex or a warped optically thick inner disk; higher resolution needed  
  > "However, higher angular resolution observations are required to investigate the morphology of HD 163296 innermost disk regions in greater details." (3.3 Asymmetries of the continuum emission)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam smearing may bias optical depth low; CO velocity resolution too coarse for kinematic planet signatures  
  > "the ratio $I_{co}/I_{co}^{obs}$ could be affected by beam smearing, implying that our measurements provide only a lower limit" (4.1 Morphology of the CO emission)
- Caveat (inferred, ours): Optical depth and epsilon constraints depend on assumed temperature models
- Caveat (inferred, ours): Planet interpretation is qualitative
- Caveat (inferred, ours): Front/back-side CO contamination

## Reproducibility

- Data public (paper): Calibration/imaging script available online  
  > "is available online at <https://almascience.org/alma-data/lp/DSHARP>" (2 Observations)
- Products in archive: _not stated_
- Code: DSHARP CASA calibration/imaging script online  
  > "the CASA script used to calibrate and image HD 163296 data, including the manual flagging and flux rescaling, is available online" (2 Observations)
- Missing: Clean parameters and masks
- Missing: emcee priors
- Missing: CO measurement extraction details
- Data volume (inferred): ~100-300 GB raw for three projects
- Score (inferred): 3/5, Public data and script, but several fitting details are not given.
- Rediscovery candidate: yes, Data are public, the recipe is largely stated, and the main results are numeric (ring widths, tau, T_co).

## Links

- Method: Andrews et al. 2018 (DSHARP calibration and imaging)
- Method: Huang et al. 2018 (Ring fitting method)
- Method: Dullemond et al. 2018 (Gaussian ring fitting)
- Method: Birnstiel et al. 2018 (Scattering dust temperature formalism)
- Companion: Zhang et al. 2018 (Planet-disk simulations)
- Related: DSHARP

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 81,
  "stated": 46,
  "rate": 0.568
 },
 "evidence_ok": true
}
```
