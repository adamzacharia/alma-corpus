# Imaging the water snow-line during a protostellar outburst

`2016Natur.535..258C` | Nature 2016 | first author: Cieza, Lucas A. | arXiv: 1607.03757 | DOI: 10.1038/nature18612

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Can the water snow-line be imaged in the disk of the outbursting protostar V883 Ori, and what does the dust optical depth and spectral index across it reveal?  
  > "We find an intensity break corresponding to an abrupt change in the optical depth at about 42 au, where the elevated disk temperature approaches the condensation point of water" (abstract)
- Target **V883 Ori**: coordinates _not stated_; z/distance 414±7 pc  
  > "It is located in the Orion Nebula Cluster, which has a distance of 414$\pm$7 pc$^{[18]}$." (main text); distance from Orion Nebula Cluster distance, Menten et al. 2007 (ref 18)  
  > "It is located in the Orion Nebula Cluster, which has a distance of 414$\pm$7 pc$^{[18]}$." (main text)

## Data provenance

- ALMA projects: 2013.1.00710.S, 2015.1.00350.S
- bands: Band 6 (230 GHz/1.3 mm)  
  > "We have obtained 230 GHz/1.3 mm (band-6) observations of V883 Ori using the Atacama Large Millimeter/submillimeter Array (ALMA)" (main text)
- frequencies and spectral setup: Three 58.6 MHz windows at 230.5380, 220.3987, 219.5603 GHz (12CO, 13CO, C18O 2-1); two 1.875 GHz continuum windows at 232.6 and 218.0 GHz  
  > "three spectral windows with 58.6 MHz bandwidths were centered at 230.5380, 220.3987, and 219.5603 GHz to cover the $^{12}$CO J = 2-1, $^{13}$CO J = 2-1, and C$^{18}$O J = 2-1 transitions, respectively." (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle-2: C34-2/1, C34-1/2, C34-7/6; Cycle-3: C38-8  
  > "The target was reobserved on August 30$^{th}$, 2015, with 35 antennas on the C34-7/6 configuration with baselines in the 42 m to 1.5 km range." (Methods)
- baselines: 14 m to 12.6 km across four configurations; Cycle-3 C38-8: 267 m to 12.6 km  
  > "in four different array configurations with baselines ranging from 14 m to 12.6 km" (main text)
- angular resolution: 0.03 arcsec (12 au) continuum; 0.2 arcsec (90 au) for C18O  
  > "We use the C$^{18}$O gas line to investigate the dynamics of the system at 0.2$''$ (90 au) resolution" (main text)
- max recoverable scale: _not stated_
- sensitivity: Cycle-3 continuum rms 0.05 mJy/beam; Cycle-2 C18O cube rms 10 mJy/beam per 0.25 km/s  
  > "The continuum data resulted in a 0.029$''$ $\times$ 0.038$''$ beam, and a rms of 0.05 mJy/beam, after one iteration of phase-only self-calibration." (Methods)
- time on source: Cycle-3: 23 minutes on source; Cycle-2: ~2 min per epoch (two compact epochs), ~3 min (C34-7/6)  
  > "The total on-source integration time was 23 minutes." (Methods)
- observing dates: 2014-12-12, 2015-04-05, 2015-08-30 (Cycle-2); 2015-10-27 (Cycle-3)  
  > "V883 Ori was observed on December 12$^{th}$, 2014 and April 5$^{th}$, 2015" (Methods)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Line: 13CO J=2-1 (220.3987 GHz)
- Line: C18O J=2-1 (219.5603 GHz)
- External data: Model predictions of spectral index and optical depth across the water snow-line (alpha_vis=1e-4), provided in tabular form  
  > "We also thank A. Banzatti and P. Pinilla for providing their model predictions in tabular form (Fig. 2d, e)." (Acknowledgments) [from Banzatti et al. 2015 (ref 14)]
- External data: Distance to Orion Nebula Cluster 414±7 pc  
  > "which has a distance of 414$\pm$7 pc$^{[18]}$" (main text) [from Menten et al. 2007 (ref 18)]
- External data: Disk mass >=0.3 Msun and bolometric luminosity 400 Lsun  
  > "It has a disk mass of $\gtrsim$0.3 M$_{\odot}$ and a bolometric luminosity of 400 L$_{\odot} ^{[19]}$." (main text) [from Sandell & Weintraub 2001 (ref 19)]

## Processing

### Calibration

- pipeline or manual: Calibrated by the ALMA observatory; pipeline-calibrated visibilities used  
  > "All the data were calibrated using the Common Astronomy Software Applications package (CASA v4.4.0)$^{[30]}$ by the ALMA observatory." (Methods)
- casa version: CASA v4.4.0  
  > "All the data were calibrated using the Common Astronomy Software Applications package (CASA v4.4.0)$^{[30]}$ by the ALMA observatory." (Methods)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Cycle-2: Ganymede and J0423-013; Cycle-3: J0423-0120  
  > "Ganymede and J0423-013 were used as flux calibrators" (Methods)
- flux scale uncertainty: 10% systematic flux calibration error  
  > "are given by a systematic flux calibration error of 10$\%$ (68$\%$ confidence interval)." (Methods)
- self calibration: One iteration of phase-only self-calibration on Cycle-3 continuum  
  > "after one iteration of phase-only self-calibration." (Methods)

### Imaging

- task: CLEAN in CASA 4.4.0 with Briggs weighting; multi-scale Cotton-Schwab CLEAN for spectral-index maps  
  > "using the CLEAN routine and Briggs weighting in the CASA v4.4.0 software package." (Methods)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Visibility-domain subtraction before imaging CO lines; continuum cleaned after removing line channels  
  > "Continuum subtraction was performed in the visibility domain before imaging the CO lines." (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: All three Cycle-2 epochs combined for a single C18O cube  
  > "All the Cycle-2 observations (3 epochs with 3 different array configurations) were combined together to produce a single C$^{18}$O data cube." (Methods)
- smoothing: 232.6 GHz map degraded with elliptical Gaussian (quadrature difference of clean beams) to match 218.0 GHz  
  > "We then degraded the higher frequency with an elliptical Gaussian whose axes correspond to the difference in quadrature of both clean beams." (Methods)
- final beam: Cycle-3 continuum 0.029'' x 0.038''; Cycle-2 C18O ~0.35'' x ~0.27'', PA 89.9 deg  
  > "with a beam $\sim$0.35$''$ by $\sim$0.27$''$ in size and a PA of 89.9 (deg)." (Methods)
- final rms: 0.05 mJy/beam continuum; 10 mJy/beam per 0.25 km/s channel C18O  
  > "The rms in this data cube is 10 mJy/beam per 0.25 km/s channel" (Methods)

### Inherited from earlier work

- Grey-body fitting approach for optical depth and temperature  
  > "Following \[20\], we performed grey-body fits to the our 218.0 and 232.6 GHz images" (Methods) [from Casassus et al. 2015 (ref 20)]
- Geometrically thin Keplerian disk model for C18O  
  > "we fitted a geometrically thin disk model, based on the model made by \[29\]." (Methods) [from ref 29 (Casassus et al. 2013 / Thindisk, Maret)]
- chi2 minimization fitting method  
  > "We conducted a $\chi^2$-minimization fitting using the method by \[34\]." (Methods) [from ref 34 (Powell 1964)]

### Not stated but needed to reproduce (our reading)

- Briggs robust value, cell size, image size and clean masks
- Line-free channels used for continuum
- Self-calibration solution interval
- Details of the Bayesian image synthesis code and settings
- Priors/starting parameter ranges and number of runs in Keplerian fit
- Exact radial bin widths for ellipse profiles
- Temperature extrapolation normalization at tau=3

## Analysis recipe

1. **Image continuum and CO lines**: CLEAN with Briggs weighting on pipeline-calibrated visibilities; Cycle-2 combined for C18O; Cycle-3 separately with phase self-cal  
  > "The long-baseline Cycle-3 dataset was reduced by itself in a similar fashion as the Cycle-2 observations." (Methods)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Build matched-resolution maps and spectral index profile**: Two approaches (multi-scale CS-CLEAN with degraded beam; Bayesian image synthesis); Bayesian adopted. Radial profiles from concentric ellipses (i=38.3 deg, PA=32.4 deg)  
  > "We followed two independent approaches to build such comparable maps, and confirmed that the two approaches provide very similar spectral index maps and physical conditions." (Methods)
   - software: CASA
   - parameter: alpha = ln(F232.6/F218.0)/ln(218.0/232.6)  
  > "The spectral index $\alpha$ = ln(F$_{232.6 GHz}$/F$_{218.0 GHz}$) / ln(218.0 GHz/232.6 GHz) as a function of $a$ is shown" (main text)
   - fitting: Weighted least-square image model fit in visibility domain  
  > "We fit an image model to the observations at each spectral window, and in the visibility domain, by minimizing the weighted least-square distance," (Methods)
   - validation: Two approaches agree; Bayesian residuals more homogeneous  
  > "and the residual were more homogeneous (i.e. free from structure) across the image than the CLEAN residuals." (Methods)
3. **Grey-body fit for tau and T_s**: I_nu = B_nu(T_s)[1-exp(tau)] with tau=tau0 (nu/nu0)^beta, nu0=218 GHz  
  > "where the optical depth $\tau (a)$ = $\tau_0 \times (\nu/\nu_0)^{\beta}$ and T$_s$ is the average dust temperature along the line of sight" (Methods)
   - assumption: beta = 1.0; T_s ∝ 1/sqrt(a) extrapolated from region where tau=3  
  > "We therefore adopt a temperature profile with $T_s \propto 1/ \sqrt{a}$ extrapolated from the region where $\tau$=3." (main text)
   - fitting: _not stated_
   - validation: Result insensitive to beta and to prescription beyond 0.1''  
  > "This result is robust and insensitive to $\beta$ and to the exact prescription used to estimate $\tau$ and $T_s$ beyond 0.1$"$." (main text)
4. **Dynamical mass from C18O Keplerian fit**: Thin Keplerian disk model, chi2 minimization with multiple random starts, fitting M, Rd, I0, fwhm  
  > "The parameters used by the fitting algorithm were: the mass of the central object ($M$), the size of the Keplerian disk ($R_d$), the peak intensity ($I_0$)" (Methods)
   - software: Thindisk
   - parameter: PA 32.4 deg, inclination 38.3±1 deg, v_src 4.3 km/s, distance 414 pc  
  > "We adopted a distance of $414$ pc$^{[18]}$" (Methods)
   - assumption: Pure Keplerian, no infall  
  > "we decided to model a pure Keplerian disk without any infall." (Methods)
   - fitting: chi2 minimization, multiple random starting parameters  
  > "multiple runs were done using different random starting parameters." (Methods)
   - validation: Model contours overlaid on C18O emission follow data  
  > "The shape of the contours follow the data well." (Methods)

## Software

- **CASA** 4.4.0: Calibration and CLEAN imaging  
  > "using the CLEAN routine and Briggs weighting in the CASA v4.4.0 software package." (Methods)
- **Thindisk** 1.0: Geometrically thin disk line emission model  
  > "Thindisk 1.0: Compute the line emission from a geometrically thin protoplanetary disk" (Methods references)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Spectral index, central beam inner disk | 2.02 | ±0.03 | dimensionless | 2 | $\alpha = 2.02\pm0.03$ in the central beam of the inner disk |
| Spectral index, outer disk | 3.7 | ±0.2 | dimensionless | 2 | $\alpha$ reaching 3.7$\pm 0.2$ in the outer disk |
| Temperature at intensity break | 105 | ±11 | K | 3 | This intensity break occurs where the temperature has dropped below 105 $\pm$ 11 K. |
| Dynamical mass | 1.29 | ±0.02 (fit); 10% adopted | Msun | 4 | $M = 1.29 \pm 0.02$ M$_{\odot}$, $R_d = 361 \pm 27$ AU |
| Keplerian disk radius | 361 | ±27 | AU | 4 | $M = 1.29 \pm 0.02$ M$_{\odot}$, $R_d = 361 \pm 27$ AU |
| Accretion rate | 7e-5 | not stated | Msun/yr | 0 | we derive an accretion rate of 7$\times$10$^{-5}$ M$_{\odot}$yr$^{-1}$ |

## Qualitative findings

- Sharp intensity break at ~42 au marks transition from optically thick to thin, interpreted as outburst-shifted water snow-line, matching Banzatti et al. model predictions  
  > "Our ALMA observations thus represent both a confirmation of the predictions by \[14\] and" (main text)

## Claim tuples

- H: The outburst has pushed the water snow-line outward in V883 Ori and it can be imaged | E: 0.03'' 1.3 mm continuum, two-window spectral index, grey-body fits | R: Intensity break at ~42 au with alpha rising from 2.0 to 3.7 and T≈105 K | F: Water snow-line imaged at ~42 au | **supported**
- H: Spectral behaviour matches dust fragmentation models | E: Compare alpha and tau profiles with Banzatti et al. models | R: alpha increases and tau drops steeply near snow-line | F: Confirms model predictions | **supported**
- H: Central star mass and accretion rate of V883 Ori | E: Keplerian fit to C18O | R: M=1.3±0.1 Msun, accretion 7e-5 Msun/yr | F: Typical FU Ori accretion rate | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: CLEAN-based matched maps vs Bayesian image synthesis; Bayesian adopted for finer detail and more homogeneous residuals  
  > "Since both approaches provided very similar trends, we adopted the Bayesian image synthesis" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Temperature is an extrapolation from the optically thick surface and may underestimate midplane snow-line temperature; tau0 and Ts degenerate when optically thin  
  > "our temperature estimate is based on an extrapolation from the surface of the optically thick inner disk and might underestimate the true temperature" (main text)
- Caveat (inferred, ours): Only two frequency points, beta fixed at 1
- Caveat (inferred, ours): 105 K is lower than expected water sublimation temperature in disks; relies on pressure argument
- Caveat (inferred, ours): Dynamical mass error dominated by distance; Rd degenerate
- Caveat (inferred, ours): Break could have other origins (e.g. dust properties not tied to water)

## Reproducibility

- Data public (paper): Data available in ALMA archive with accession numbers 2013.1.00710.S and 2015.1.00350.S  
  > "Our work made use of ALMA data available at https://almascience.eso.org/alma-data with the following accession numbers: 2013.1.00710.S and 2015.1.00350.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Briggs robust, cell and image size, masks
- Missing: Bayesian image synthesis code and settings
- Missing: Fit starting ranges and Keplerian model details
- Missing: Tabulated Banzatti model predictions
- Data volume (inferred): ~50-200 GB raw for both projects
- Score (inferred): 3/5, Public data and a clear conceptual recipe, but key imaging parameters and the custom image-synthesis code are missing.
- Rediscovery candidate: no, Imaging and image-synthesis settings insufficiently specified for a full redo, though the main results are numeric.

## Links

- Method: Casassus et al. 2015 (ref 20) (Grey-body fitting and multi-frequency image synthesis)
- Method: Rau & Cornwell 2011 (Multi-scale CLEAN)
- Companion: Banzatti et al. 2015 (ref 14) (Model predictions of water snow-line spectral signature)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 47,
  "rate": 0.671
 },
 "evidence_ok": true
}
```
