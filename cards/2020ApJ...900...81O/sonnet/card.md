# Solving Grain Size Inconsistency between ALMA Polarization and VLA Continuum in the Ophiuchus IRS 48 Protoplanetary Disk

`2020ApJ...900...81O` | The Astrophysical Journal 2020 | first author: Ohashi, Satoshi | arXiv: 2007.15014 | DOI: 10.3847/1538-4357/abaab4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Can the ALMA 860 um polarization (self-scattering, ~100 um grains) and the VLA 8.8 mm continuum (previously read as cm grains) of the IRS 48 dust trap be explained together?  
  > "To explain both, ALMA polarization and previous ALMA and VLA observations, we suggest that the thermal emission at 860 $\mu$m wavelength is optically thick" (abstract)
- Target **Ophiuchus IRS 48**: coordinates _not stated_; z/distance 120 pc (revised to 134 pc by Gaia, but 120 pc used)  
  > "The Ophiuchus IRS 48 is a young A-type star with a distance of 120 pc[^1] (cite: loi08)." (Introduction); distance from Loinard et al. 2008 (cite: loi08)  
  > "The Ophiuchus IRS 48 is a young A-type star with a distance of 120 pc[^1] (cite: loi08)." (Introduction)

## Data provenance

- ALMA projects: 2017.1.00834.S
- bands: Band 7 (860 um)  
  > "Figure [5](#test1) shows the comparisons of ALMA Band 7 polarization and VLA continuum observations" (Radiative Transfer Modeling)
- frequencies and spectral setup: 4 spws (2 per sideband), 64 channels each, 31.25 MHz channel width; centres 349.7, 351.5, 361.6, 363.5 GHz  
  > "The central frequencies in spws are 349.7 GHz, 351.5 GHz, 361.6 GHz, and 363.5 GHz, respectively." (Observations)
- continuum bandwidth: ~7.5 GHz in total  
  > "providing a bandwidth of $\sim7.5$ GHz in total" (Observations)
- arrays: _not stated_
- configurations: C43-2, 45 antennas  
  > "The antenna configurations were C43-2 with 45 antennas." (Observations)
- baselines: _not stated_
- angular resolution: 0.49"x0.39" (~59x47 au at 120 pc)  
  > "The beam size of the final product is $0.49\ensuremath{''}\times0.39\ensuremath{''}$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms I 33, Q 30, U 33, PI 44 uJy/beam  
  > "$\sigma_{\rm PI}=4.4\times10$ $\mu$Jy beam$^{-1}$" (Observations)
- time on source: ~90 min on target  
  > "The total integration time for the target was about 90 min." (Observations)
- observing dates: 2018 August 19  
  > "were carried out on 2018 August 19" (Observations)
- pi or archival as stated: PI Adriana Pohl  
  > "(2017.1.00834.S, PI: Adriana Pohl)" (Observations)
- Other facility **VLA 8.8 mm**: 34 GHz continuum image from van der Marel et al. 2015, CnB and B configurations  
  > "We also utilize the VLA data taken by (cite: van15)." (Observations)
- External data: VLA 8.8 mm continuum image (peak 138 uJy/beam)  
  > "We also utilize the VLA data taken by (cite: van15)." (Observations) [from van der Marel et al. 2015 (cite: van15)]
- External data: ALMA 440 um crescent model parameters rc=61 AU, rw=14 AU, phic=100 deg, phiw=41 deg  
  > "(cite: van15) found the best fit for $r_{\rm c}=61$ AU, $r_{\rm w}=14$ AU, $\phi_{\rm c}=100^\circ$, and $\phi_{\rm w}=41^\circ$." (Radiative Transfer Modeling) [from van der Marel et al. 2015 (cite: van15)]
- External data: Dust temperature 60 K at 60 au, inclination 50 deg  
  > "We assume a dust temperature of 60 K at 60 au (cite: bru14)." (An Optically Thin Case) [from Bruderer et al. 2014 (cite: bru14)]
- External data: Gas surface density 0.5 g cm-2 at the ring  
  > "they derived the gas surface density of 0.5 g cm$^{-2}$ at the ring" (Dust trapping model for ALMA polarization observations) [from van der Marel et al. 2016 (cite: van16)]

## Processing

### Calibration

- pipeline or manual: standard manner; details in Nagai et al. 2016  
  > "The reduction and calibration of the data were done with CASA version 5.1.1 (cite: mcm07) in a standard manner." (Observations)
- casa version: CASA 5.1.1  
  > "CASA version 5.1.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: bandpass J1427-4206; gain J1625-2527; polarization J1427-4206  
  > "The bandpass and the gain calibrations were performed by observations of J1427-4206 and J1625-2527, respectively" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean for Stokes I, Q, U  
  > "All images (Stokes *I*, *Q*, and *U*) were reconstructed with the CASA task *tclean*" (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.49"x0.39"  
  > "The beam size of the final product is $0.49\ensuremath{''}\times0.39\ensuremath{''}$" (Observations)
- final rms: I 33 uJy/beam  
  > "$\sigma_{\it I}=3.3\times10$ $\mu$Jy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Detailed data reduction description  
  > "A detailed description of the data reduction is given in (cite: nag16)." (Observations) [from Nagai et al. 2016 (cite: nag16)]
- Radiative transfer with multiple scattering  
  > "we performed radiative transfer calculations with RADMC-3D[^2] (cite: dul12) that take into account multiple scattering, as done by (cite: kat15)" (Radiative Transfer Modeling) [from Kataoka et al. 2015 (cite: kat15)]
- Dust opacity calculation  
  > "The dust opacity is calculated following (cite: kat16)." (Radiative Transfer Modeling) [from Kataoka et al. 2016 (cite: kat16)]
- Fourth-power Gaussian intensity profile  
  > "following (cite: van13; van15)" (Radiative Transfer Modeling) [from van der Marel et al. 2013, 2015]

### Not stated but needed to reproduce (our reading)

- Imaging details: cell size, image size, masks, niter and threshold
- Self-calibration and pipeline version
- Flux calibrator flux density and flux scale uncertainty for Band 7
- Procedure for proper-motion correction of images
- Stellar luminosity/mass used for Toomre Q
- Number of photons and grid settings in RADMC-3D
- Details of polarization calibration in CASA (not stated beyond reference)

## Analysis recipe

1. **Image Stokes I, Q, U and derive polarization**: tclean with Briggs weighting; PI debiased; Pfrac computed above 3 sigma_PI  
  > "We thus debiased the polarized intensity map as $PI=\sqrt{Q^2+U^2-\sigma_{\rm PI}^2}$." (Observations)
   - software: CASA
   - parameter: robust 0.5; Pfrac only where PI > 3 sigma_PI  
  > "The polarization fraction ($P_{\rm frac}=PI/I$) was derived only where detection was above the threshold 3$\sigma_{\rm PI}$." (Observations)
   - assumption: Stokes V ignored  
  > "we ignore the Stokes *V* component in this study because it has not been well characterized for ALMA" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure continuum peak offset and proper motion; N-S contrast**: Compare ALMA and VLA peak positions; two-component Gaussian fit to intensity profile along PA=36+-15 deg  
  > "We fit the profile with a two component Gaussian profile" (Stokes I Continuum Data)
   - fitting: two-component Gaussian  
  > "We fit the profile with a two component Gaussian profile" (Stokes I Continuum Data)
   - validation: _not stated_
3. **Radiative transfer models of self-scattering for three dust scenarios**: RADMC-3D models with Mie opacity (silicate+water ice 50/50, Maxwell-Garnett), q=-3.5, i=50 deg, PA=110 deg, fset=10; models 1 (thin, 140 um), 2 (140 um + 5 cm), 3 (thick, 140 um); also a 10/20/40-population dust-trap model  
  > "The opacity was calculated using Mie theory." (Radiative Transfer Modeling)
   - software: RADMC-3D
   - parameter: amax=140 um; Sigma0 0.26 (model1), 0.65 and 0.1 (model2), 8.2 g cm-2 (model3); T=60 K (thin), 35 K (thick) at 60 au  
  > "The temperature is assumed to be 35 K at 60 au" (An Optically Thick Case)
   - assumption: Distance 120 pc; VLA emission dominated by dust  
  > "Therefore, we assume that the most of the VLA emission comes from dust grains in this study." (Results)
   - fitting: Surface density tuned by hand to match intensities; no optimal fit  
  > "It should be noted that this study does not make an optimal fitting" (An Optically Thin Case)
   - validation: Compared model Stokes Q/U, polarization fraction and VLA/ALMA 440 um peak intensities with observations  
  > "The both models follow the observed peak intensities at 440 $\mu$m (ALMA Band 9), 860 $\mu$m (ALMA Band 7), and 8.8 mm (VLA) wavelengths." (Discussion)
4. **Test gravitational stability and dependence on optical depth and scale height**: Toomre Q with gas-to-dust 100; vary Sigma0 and fset in model 3  
  > "the Toomre $Q$ is derived to be $Q\sim0.1$" (Is the disk gravitationally unstable)
   - software: RADMC-3D
   - assumption: gas-to-dust mass ratio 100  
  > "By assuming the gas to dust mass ratio of 100" (Is the disk gravitationally unstable)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: data reduction, calibration and tclean imaging  
  > "The reduction and calibration of the data were done with CASA version 5.1.1" (Observations)
- **RADMC-3D** : radiative transfer with self-scattering  
  > "we performed radiative transfer calculations with RADMC-3D" (Radiative Transfer Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I peak | 120 | not stated | mJy/beam | 1 | The peak emission is 120 mJy beam$^{-1}$ toward the southeast of the disk, corresponding to 13 K in brightness temperature. |
| Integrated continuum flux | 190 | not stated | mJy | 1 | The integrated flux of the continuum emission is 190 mJy. |
| Polarization fraction | 1-2 | not stated | % | 1 | is on average $\sim1-2$% |
| Proper motion (RA, Dec) | (-24.2, -32.5) | 5.7, 5.7 | mas/yr | 2 | ($-24.2\pm5.7,-32.5\pm5.7$) mas yr$^{-1}$ |
| North-South brightness contrast | ~170 | not stated | dimensionless | 2 | The brightness contrast between the southern and northern sides of the disk is $\sim170$ |
| Optical depth at 860 um in thick model | 7.3 | not stated | dimensionless | 3 | The optical depth corresponds to $\tau_{\rm abs}=7.3$ at 860 $\mu$m |
| Surface density in thick model | 8.2 | not stated | g cm-2 | 3 | the surface density needs to be $\Sigma_{0}\sim8.2$ g cm$^{-2}$ |
| Toomre Q | ~0.1 | not stated | dimensionless | 4 | the Toomre $Q$ is derived to be $Q\sim0.1$ |

## Qualitative findings

- Polarization vectors parallel to the disk minor axis, consistent with self-scattering  
  > "These characteristics are consistent with the dust self-scattering in inclined disks." (Conclusion)

## Claim tuples

- H: Is 860 um polarization consistent with self-scattering by ~100 um grains? | E: ALMA polarization imaging and RADMC-3D model | R: Pfrac 1-2%, vectors parallel to minor axis, model 3.5% for 140 um | F: Self-scattering with amax~100 um explains polarization | **supported**
- H: Can optically thin dust trap with cm grains explain both datasets? | E: Two-population and 40-population dust trap models | R: Pfrac ~0.2% in trap model, Q/U drop at peak in two-population | F: Simple optically thin trapping is disfavoured but not ruled out at this resolution | **partially**
- H: Does an optically thick 860 um model with amax~140 um reproduce ALMA and VLA? | E: Model 3 with T=35 K, Sigma0=8.2 g cm-2 | R: Pfrac 1.3% model vs 1.1+-0.1% observed; VLA matched | F: Optically thick model is more likely | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single optically thin 140 um population rejected because VLA peak ~10 times too low  
  > "Therefore, this model with a single population of dust grains with $a_{\rm max}\sim100$ $\mu$m cannot explain the VLA observations." (An Optically Thin Case)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam too large to resolve structure or constrain dust scale height  
  > "our current polarization observations are not enough to constrain the dust scale height due to the large beam size" (Dependence of polarization on Dust Scale Height)
- Caveat (inferred, ours): Models tuned by hand, no formal fit or uncertainties
- Caveat (inferred, ours): Large gas surface density Toomre result implies unrealistic gas-to-dust ratio, possibly signalling the thick model is questionable
- Caveat (inferred, ours): Degenerate with larger grains settled in midplane
- Caveat (inferred, ours): Proper motion claim based on offset smaller than beam

## Reproducibility

- Data public (paper): ALMA project code printed; archival data credit given  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00834.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, cleaning threshold)
- Missing: RADMC-3D configuration details
- Missing: Calibrator fluxes and proper-motion correction procedure
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Public data and most imaging parameters given, but the modelling is hand-tuned with missing RADMC-3D settings.
- Rediscovery candidate: no, Main results depend on hand-tuned radiative transfer models and inherited VLA data and parameters.

## Links

- Method: Kataoka et al. 2015 (cite: kat15) (Self-scattering radiative transfer method)
- Method: Nagai et al. 2016 (cite: nag16) (Detailed data reduction)
- Companion: van der Marel et al. 2015 (cite: van15) (VLA 8.8 mm data and ALMA 440 um model)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
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
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
