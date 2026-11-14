# Cm-wavelength observations of MWC 758: resolved dust trapping in a vortex

`2019MNRAS.483.3278C` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Casassus, Simon | arXiv: 1805.03023 | DOI: 10.1093/mnras/sty3269

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: Does the multi-frequency morphology of the Clump 1 and Clump 2 dust concentrations in MWC 758 (VLA 33 GHz vs ALMA 342 GHz) match dust trapping in an anticyclonic vortex?  
  > "Deep multiconfiguration integrations reveal the morphology of Clump 1 and additional cm-wave components which we characterize via comparison with a deconvolution of recent 342 GHz data" (abstract)
- Target **MWC 758**: coordinates _not stated_; z/distance 160.2±1.7 pc  
  > "MWC 758, at a distance of $160.2\pm1.7$ pc (cite: Gaia2016A&A...595A...1G)" (1 Introduction); distance from Gaia (Gaia2016A&A...595A...1G)  
  > "MWC 758, at a distance of $160.2\pm1.7$ pc (cite: Gaia2016A&A...595A...1G)" (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00725.S
- bands: _not stated_
- frequencies and spectral setup: VLA Ka band, 28.976-37.024 GHz, 64 spectral windows of 64 channels, centre 33.0 GHz; ALMA Band 7 at 342 GHz  
  > "covered from 28.976 GHz to 37.024 GHz in 64 spectral windows, each divided into 64 channels, and with a center frequency of 33.0 GHz." (2.1 Instrumental setup)
- continuum bandwidth: _not stated_
- arrays: VLA configurations A, B, C  
  > "The new VLA data were acquired in array configurations C, B (project ID 16A-314), and A (project ID 16B-065)" (2.1 Instrumental setup)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: uvmem effective resolution 0.11"x0.08" at 342 GHz; natural-weights beam 0.33"x0.21"  
  > "an elliptical Gaussian fit gives $(0.11\ensuremath{''}\times0.08\ensuremath{''})$, in the direction BPA=38.3 deg" (2.3 Comparison with the sub mm continuum)
- max recoverable scale: _not stated_
- sensitivity: 342 GHz residual rms 0.08 mJy/beam; 33 GHz thermal noise 1.6 uJy/beam  
  > "with an rms noise of 0.08 mJy beam$^{-1}$" (2.3 Comparison with the sub mm continuum)
- time on source: VLA: C 30m; B 1h02m each x6; A 1h55m each x3  
  > "| C | 02-14 04:41 | 1h10m | 30m | 0.029 | 3C48 |  |" (Table 1)
- observing dates: VLA 2016: C Feb 14; B Aug 25-30; A Oct 20-24  
  > "Start UTC date of each integration, year 2016" (Table 1)
- pi or archival as stated: _not stated_
- Other facility **VLA**: New 33 GHz continuum in A, B, C configurations  
  > "This corresponds to the Ka band of the VLA." (2.1 Instrumental setup)
- External data: Reprocessed 342 GHz ALMA data and midplane temperature, optical depth and CO-isotopologue gas surface density (1.8 g cm-2)  
  > "we compare the VLA data with the ALMA observations at 342 GHz recently published by (cite: Boehler2018ApJ...853..162B)" (2.3 Comparison with the sub mm continuum) [from (cite: Boehler2018ApJ...853..162B)]
- External data: Earlier 34 GHz B-array VLA detection of Clump 1; stellar flux 63±5 uJy  
  > "the stellar flux amounted to $63\pm5 \mu$Jy." (2.2 Imaging) [from (cite: Marino2015ApJ...813...76M)]
- External data: Analytical dust opacities for porous grains  
  > "are given by the analytical approximations from (cite: Kataoka2014A&A...568A..42K)" (3.2.2 Continuous grain size population) [from (cite: Kataoka2014A&A...568A..42K)]

## Processing

### Calibration

- pipeline or manual: VLA pipeline with small amount of extra flagging  
  > "All datasets were processed by the VLA pipeline (CASA 4.3.1), and required only a small amount of posterior flagging" (2.1 Instrumental setup)
- casa version: CASA 4.3.1  
  > "All datasets were processed by the VLA pipeline (CASA 4.3.1)" (2.1 Instrumental setup)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C48 (C), 3C138 (A, B)  
  > "Source for bandpass and amplitude calibration" (Table 1)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: tclean, multi-scale Clean  
  > "These images were obtained with an application of the multi-scale Clean algorithm (cite: RauCornwell2011A&A...532A..71R), using task `tclean` from the CASA package." (2.2 Imaging)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: Pipeline visibility weights kept; best of tested schemes  
  > "found that the visibility weights as delivered by the pipeline produced the best results" (2.2 Imaging)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Distance to MWC 758  
  > "MWC 758, at a distance of $160.2\pm1.7$ pc (cite: Gaia2016A&A...595A...1G)" (1 Introduction) [from (cite: Gaia2016A&A...595A...1G)]
- Dust surface density prescription from Lyra-Lin vortex trapping  
  > "The dust mass surface density fields per unit grain size is given by (cite: Marino2015ApJ...813...76M)" (3.2.2 Continuous grain size population) [from (cite: Marino2015ApJ...813...76M); (cite: LyraLin2013ApJ...775...17L)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales, cell size, image size, weighting/robust and clean threshold for VLA tclean
- ALMA calibration/imaging details of the reprocessed archival data (CASA version, self-cal)
- Priors' bounds for most MCMC parameters (only Sigma_g in [0.1,100])
- Exact uvmem settings for ALMA beyond M and lambda; sigma_D value
- Polynomial baseline order in azimuthal fits
- Disk inclination and PA used to deproject

## Analysis recipe

1. **Image VLA data**: Multi-scale tclean images per configuration and combined A+B+C  
  > "These images were obtained with an application of the multi-scale Clean algorithm (cite: RauCornwell2011A&A...532A..71R), using task `tclean` from the CASA package." (2.2 Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Tested weighting schemes for combination  
  > "we tested different combination schemes" (2.2 Imaging)
2. **Deconvolve 342 GHz and 33 GHz visibilities**: Maximum entropy uvmem model images; lambda=1e-3, M=1e-3 for ALMA; positivity only for 33 GHz  
  > "here we set $M =10^{-3}$, and $\lambda = 10^{-3}$." (2.3 Comparison with the sub mm continuum)
   - software: uvmem
   - fitting: _not stated_
   - validation: Effective resolution from simulated spike; residual dirty maps thermal  
  > "The effective angular resolution of the `uvmem` model image can be estimated by simulating the same $uv-$coverage on a spike" (2.3 Comparison with the sub mm continuum)
3. **Measure Clump 1 azimuthal width and aspect ratio**: Polar maps, Gaussian fits at constant radius, subtraction of effective resolution; beam subtracted in quadrature for aspect ratio  
  > "A Gaussian fit to the intensity profiles extracted at constant radii gives a fairly good representation of the azimuthal extent of Clump 1" (3.1 Azimuthal dust trapping in Clump 1: spectral trends)
   - software: uvmem
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit Lyra-Lin vortex dust trapping model**: Isothermal slab emission with Kataoka opacities, 8 free parameters fit to 6 observables  
  > "our simplified observational constraints number a total of 6 independent data points, while there are 8 free parameters in the model" (3.2.2 Continuous grain size population)
   - software: emcee
   - parameter: 6000 iterations, 1500 walkers, burn-in 1500  
  > "with flat priors, and with 6000 iterations and 1500 walkers, burning-in the first 1500 iterations" (3.2.2 Continuous grain size population)
   - assumption: 60% astrosilicate + 40% amorphous carbon, constant filling factor, isotropic scattering, r_S=1  
  > "We assume optical constants corresponding to a mix of astrosilicates (60%) and amorphous carbon(40%)." (3.2.2 Continuous grain size population)
   - fitting: _not stated_
   - validation: Kida and GNG solutions give similar results; no-scattering variant within uncertainties  
  > "Both of the Kida and GNG vortex solutions resulted in very similar optimisations" (3.2.2 Continuous grain size population)

## Software

- **CASA** 4.3.1: VLA pipeline and tclean imaging  
  > "All datasets were processed by the VLA pipeline (CASA 4.3.1)" (2.1 Instrumental setup)
- **uvmem** : Maximum-entropy deconvolution of visibilities  
  > "We used the `uvmem` package (cite: Carcamo2018A&C....22...16C)" (2.3 Comparison with the sub mm continuum)
- **emcee** : MCMC exploration of vortex model parameters  
  > "We used the ` emcee` package (cite: emcee2013PASP..125..306F)" (3.2.2 Continuous grain size population)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stellar 33 GHz flux density | 43.6 | 2.0 | uJy | 1 | with a 33 GHz flux density of $43.6\pm2.0\,\mu$Jy |
| Clump 1 aspect ratio lower limit | chi > 5.6 (3 sigma) | chi=5.94±0.11 | dimensionless | 3 | we report a $3\sigma$ lower limit of $\chi > 5.6$ |
| Azimuthal width ratio Q_phi | 2.26 | 0.04 | dimensionless | 3 | $Q_\phi =
s_\phi(342{\rm\,GHz})/s_\phi(33{\rm\,GHz}) = 2.26\pm0.04$ |
| Vortex temperature | 23.5 | +2.8/-1.9 | K | 4 | median value $T=23.5^{+2.8}{-1.9}$ K |
| Vortex aspect ratio | 13.8 | +4.3/-1.7 | dimensionless | 4 | $\chi = 13.8^{+4.3}_{-1.7}$ |
| log10(<Sigma_g> x alpha) | -2.3 | +0.3/-0.6 | g cm-2 | 4 | = -2.3^{+0.3}_{-0.6} |
| Clump1/Clump2 peak ratio at 342 GHz | 1.51 | 0.01 | dimensionless | 0 | $R_{342{\rm\,GHz}} = 1.51 \pm 0.01$ |

## Qualitative findings

- Clump 2 is detected at 33 GHz but is less compact, suggesting less efficient cm-grain trapping  
  > "the concentration of the cm-grains is not as effective as for Clump 1" (3.3 The contrast between Clump 1 and Clump 2)

## Claim tuples

- H: Clump 1 spectral trends follow Lyra-Lin vortex dust trapping | E: Compare 33 GHz and 342 GHz azimuthal widths with an MCMC-fitted vortex model | R: Q_phi=2.26±0.04; fit gives chi~14, T~23 K, porous grains | F: Trends are quantitatively consistent with a dust-trapping vortex | **supported**
- H: Clump 1 is resolved at 33 GHz | E: Deconvolve A-config data | R: chi>5.6 | F: Clump 1 is a narrow arc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Fractal aggregates with dimension 2 discarded since Stokes numbers would be size independent  
  > "We can discard dust models based on fractal aggregates, at least with dimension 2" (3.2.2 Continuous grain size population)
- How they decided it was enough: _not stated_
- Limitation (authors): Model under-constrained: 8 parameters vs 6 data points  
  > "The model is therefore under-constrained." (3.2.2 Continuous grain size population)
- Caveat (inferred, ours): Sub-mm optical depth biases width ratio
- Caveat (inferred, ours): Systematics not in width errors
- Caveat (inferred, ours): Isothermal steady-state model with few data points

## Reproducibility

- Data public (paper): ALMA project 2012.1.00725.S cited; VLA project IDs given  
  > "(project ID 16A-314), and A (project ID 16B-065)" (2.1 Instrumental setup)
- Products in archive: _not stated_
- Missing: Tclean parameters
- Missing: ALMA reprocessing details
- Missing: Full priors
- Data volume (inferred): ~100s of GB (VLA Ka multi-config plus ALMA Band 7)
- Score (inferred): 3/5, Public data and clear model, but imaging parameters and ALMA reprocessing are unstated.
- Rediscovery candidate: no, Key imaging and ALMA reprocessing settings missing.

## Links

- Method: (cite: Carcamo2018A&C....22...16C) (uvmem package)
- Method: (cite: Kataoka2014A&A...568A..42K) (opacities)
- Companion: Baruteau et al. 2018 (hydrodynamical simulations of Clumps 1 and 2)
- Companion: (cite: Boehler2018ApJ...853..162B) (ALMA 342 GHz data)

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
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
