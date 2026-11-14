# Vortices and Spirals in the HD135344B Transition Disk

`2016ApJ...832..178V` | The Astrophysical Journal 2016 | first author: van der Marel, N. | arXiv: 1607.05775 | DOI: 10.3847/0004-637X/832/2/178

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: Do the millimeter dust structures in the HD135344B transition disk relate to the scattered-light spiral arms, and are they consistent with spirals or with vortices triggered by planets?  
  > "A natural question is whether there is any relation between the spiral arms observed in near-infrared scattered light (from the disk surface) and the structures seen in submillimeter emission (from the midplane)." (Introduction)
- Target **HD 135344B (SAO 206462)**: coordinates 15h15m48.42s -37d09m16.36s (from 13CO emission)  
  > "HD 135344B [^1] (F4 star, $d\sim$140 pc, $\sim$8 Myr (cite: vanBoekel2005; Grady2009))" (Introduction); "we use the stellar position 15$^h$15$^m$48.$^s$42 -37$^{\circ}$09’16.”36) as derived from the $^{13}$CO emission" (3 Observations); z/distance d ~140 pc  
  > "HD 135344B [^1] (F4 star, $d\sim$140 pc, $\sim$8 Myr (cite: vanBoekel2005; Grady2009))" (Introduction); "we use the stellar position 15$^h$15$^m$48.$^s$42 -37$^{\circ}$09’16.”36) as derived from the $^{13}$CO emission" (3 Observations); distance from cited literature (vanBoekel2005; Grady2009)  
  > "HD 135344B [^1] (F4 star, $d\sim$140 pc, $\sim$8 Myr (cite: vanBoekel2005; Grady2009))" (Introduction); "we use the stellar position 15$^h$15$^m$48.$^s$42 -37$^{\circ}$09’16.”36) as derived from the $^{13}$CO emission" (3 Observations)

## Data provenance

- ALMA projects: 2012.1.00158.S
- bands: Band 7 (~335 GHz, 896 um)  
  > "in Band 7 ($\sim$335 GHz or 896 $\mu$m) in the C32-5 configuration (20-800 m baselines)" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C32-5  
  > "in the C32-5 configuration (20-800 m baselines)" (Observations)
- baselines: 20-800 m  
  > "in the C32-5 configuration (20-800 m baselines)" (Observations)
- angular resolution: 0.20x0.16 arcsec (superuniform)  
  > "resulting in a smaller beam size of 0.20$\times$0.16” (Figure [1](#fig:imagedata)a)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: rms 0.25 mJy/beam; peak S/N 120 (superuniform)  
  > "The peak S/N decreases from 210$\sigma$ (briggs) to 120$\sigma$ (superuniform) with $\sigma$ the rms level (0.25 mJy beam$^{-1}$)." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Cycle 1 program, PI van Dishoeck; previously presented  
  > "previously presented in (cite: vanderMarel2015-isot; Pinilla2015beta)" (Observations)
- Other facility **VLT/NACO**: Archival Ks-band PDI scattered light image (0.09" resolution)  
  > "We also make use of archival data of HD135344B obtained in Polarization Differential Imaging (PDI) in the K$_s$ band ($\sim$2.2 micron) (cite: Garufi2013) with VLT/NACO." (Observations)
- External data: Stellar position/PA 62 deg and inclination 16 deg for deprojection; alpha, beta values  
  > "for the deprojection a position angle of $62^{\circ}$ and an inclination of $16^{\circ}$ (cite: vanderMarel2015-isot)" (Observations) [from (cite: vanderMarel2015-isot)]
- External data: Scattered-light spiral description and launching-point fits for S1/S2  
  > "(cite: Muto2012) find a best-fit for the launching point of S1 at $r_c$=0.39" (55 AU) at $\theta_0$=204$^{\circ}$" (Discussion and conclusions) [from (cite: Muto2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibration as in earlier paper; not detailed here  
  > "The spectral settings and calibration are discussed in (cite: vanderMarel2015-isot)." (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: superuniform weighting instead of briggs  
  > "the continuum emission is re-imaged using superuniform rather than briggs weighting of the observed visibilities" (Observations)
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
- final beam: 0.20x0.16 arcsec  
  > "resulting in a smaller beam size of 0.20$\times$0.16” (Figure [1](#fig:imagedata)a)" (Observations)
- final rms: 0.25 mJy/beam  
  > "with $\sigma$ the rms level (0.25 mJy beam$^{-1}$)" (Observations)

### Inherited from earlier work

- Spectral settings and calibration  
  > "The spectral settings and calibration are discussed in (cite: vanderMarel2015-isot)." (Observations) [from (cite: vanderMarel2015-isot)]
- Vortex Gaussian prescription  
  > "using the vortex prescription by (cite: LyraLin2013) of a Gaussian in the radial and azimuthal direction" (The Ring plus Asymmetry Model) [from (cite: LyraLin2013)]
- Analytical spiral shape  
  > "using the analytical shape derived by (cite: rafikov2002)" (The Spiral Model) [from (cite: rafikov2002)]

### Not stated but needed to reproduce (our reading)

- Briggs/superuniform CASA task and parameters, cell and image size
- Self-calibration and flux calibrator details (in earlier paper)
- MCMC priors, walkers, steps and likelihood for emcee fit
- Pixel selection for the maxima in the spiral fit
- Initial guesses for spiral fits in Figure 4

## Analysis recipe

1. **Re-image continuum with superuniform weighting**: Re-image visibilities with superuniform weighting  
  > "the continuum emission is re-imaged using superuniform rather than briggs weighting of the observed visibilities" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit spiral model to S1 arm**: Rafikov analytic spiral fit with orthogonal distance regression, free r_c and theta_0  
  > "We adopt an Orthogonal Distance Regression fitting procedure, that searches for the curve that minimizes the sum of the distances to the data points orthogonally to the curve itself" (The Spiral Model)
   - parameter: alpha=1.5, beta=0.45, h_c=0.12 fixed  
  > "we fix the scale-height value to the average $h_{\rm c}=0.12$, so only two free parameters remain for the fit" (The Spiral Model)
   - assumption: Position uncertainty equals beam FWHM; points weighted by pixel intensity  
  > "We assume the uncertainty on the positions of the maxima to be equal to the FWHM of the beam." (The Spiral Model)
   - fitting: Orthogonal distance regression  
  > "each data point is weighted proportional to the corresponding pixel intensity" (The Spiral Model)
   - validation: _not stated_
3. **Fit ring plus vortex asymmetry model**: Gaussian vortex plus Gaussian ring, 8 free parameters, fit to the image  
  > "Our model has therefore 8 free parameters (5 for the asymmetry and 3 for the ring model), and we fit it to the image using the MCMC python package `emcee`." (The Ring plus Asymmetry Model)
   - software: emcee
   - fitting: MCMC with emcee; priors not stated  
  > "The chains from the fit show good convergence for all the free parameters" (The Ring plus Asymmetry Model)
   - validation: Best fit simulated onto observed visibilities; compared with convolved image; residuals ~10%  
  > "The best fit was simulated onto the observed visibilities, and no significant differences were found with the convolved image." (The Ring plus Asymmetry Model)
4. **Estimate lower limit mass of F1**: M_gas = 0.08*F_nu*(d/140 pc)^2 MJup with total flux ~200 mJy  
  > "using $M_{\rm gas} = 0.08*F_{\nu}(d/140 {\rm pc})^2$ M$_{\rm Jup}$, (cite: Cieza2008)" (Discussion and conclusions)
   - assumption: ISM gas-to-dust ratio 100; emission partially optically thick so lower limit  
  > "with a total flux of $\sim$200 mJy and a ISM gas-to-dust ratio of 100, the total mass is $>$16 M$_{\rm Jup}$" (Discussion and conclusions)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **emcee** : MCMC fit of ring plus asymmetry model  
  > "we fit it to the image using the MCMC python package `emcee`" (The Ring plus Asymmetry Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vortex radius r_v | 80.7 | 0.005 | AU | 3 | 80.7 $\pm$ 0.005 AU |
| Ring radius r_r | 51.3 | 0.004 | AU | 3 | 51.3 $\pm$ 0.004 AU |
| Vortex azimuthal position theta_v | 172 | 0.02 | deg | 3 | $172^{\circ} \pm0.02^{\circ}$ |
| F1 mass lower limit | >16 | not stated | MJup | 4 | the total mass is $>$16 M$_{\rm Jup}$ |
| Peak brightness temperature | 20 | not stated | K | 0 | The peak brightness temperature is 20 K |

## Qualitative findings

- F1 is mostly coradial and inconsistent with a spiral arm; ring plus vortex describes it  
  > "The fit in Figure [2](#fig:spiraloverlay) (left) shows that the F1 structure is mostly coradial" (Morphology)

## Claim tuples

- H: Is the outer millimeter feature F1 a spiral arm? | E: Fit Rafikov spiral to F1 and compare with ring plus vortex model | R: Spiral launching point r_c<0.2", pitch angle near 0 | F: F1 is not a spiral but a vortex-like asymmetry | **supported**
- H: Can a planet at ~30 AU plus a secondary vortex explain both scattered-light spirals? | E: Refit S1 and S2 launching points | R: S2 launched at 32 AU, S1 at 84 AU | F: Scenario is consistent but needs hydrodynamical tests | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Single outer planet launching both spirals (Dong 2015) cannot be confirmed as planet undetected  
  > "As this planet has remained undetected, this scenario cannot be confirmed." (Discussion and conclusions)
- How they decided it was enough: _not stated_
- Limitation (authors): Launching-point fits uncertain due to scale height and shadowing  
  > "One of the major uncertainties in the scenario are the fits to the locations of the launching points." (Discussion and conclusions)
- Caveat (inferred, ours): MCMC errors are unrealistically small; real uncertainty ~2-3 AU
- Caveat (inferred, ours): Fixed scale height drives spiral fit results
- Caveat (inferred, ours): No hydrodynamical simulation done for this system

## Reproducibility

- Data public (paper): Archival ALMA program acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA/2012.1.00158.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: MCMC setup and priors
- Missing: Calibration details (in earlier paper)
- Data volume (inferred): ~20-50 GB
- Score (inferred): 3/5, Public data and simple models, but imaging and fit settings are sparse.
- Rediscovery candidate: no, Imaging and fitting details are incomplete.

## Links

- Method: (cite: rafikov2002) (Analytic spiral wave shape)
- Method: (cite: LyraLin2013) (Vortex Gaussian prescription)
- Companion: (cite: vanderMarel2015-isot) (Same ALMA data, calibration and disk parameters)
- Companion: (cite: Pinilla2015beta) (Previous presentation of same data)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 68,
  "stated": 35,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
