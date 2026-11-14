# Orbital polarimetric tomography of a flare near the Sagittarius A<SUP>*</SUP> supermassive black hole

`2024NatAs...8..765L` | Nature Astronomy 2024 | first author: Levis, Aviad | arXiv: 2310.07687 | DOI: 10.1038/s41550-024-02238-3

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: other
- Question: Recover the evolving 3D structure of a flare orbiting Sgr A* from the single-pixel ALMA linear-polarization light curves of April 11, 2017 (orbital polarimetric tomography), and constrain the observer inclination  
  > "we seek to recover an evolving 3D structure from a single-pixel observation over time." (Introduction); "In this work, we present the first 3D recovery of emission in orbit around Sgr A$^*$ reconstructed from ALMA light curves observed on April 11, 2017" (Introduction)
- Target **Sgr A***: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.01404.V
- bands: _not stated_
- frequencies and spectral setup: ~230 GHz  
  > "On April 11, 2017, ALMA observed Sgr A$^*$ at $\sim 230 {\rm GHz}$ as part of a larger EHT campaign" (Results)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: polarimetric noise sigma_Q = sigma_U = 0.01 Jy (homoscedastic, from Wielgus et al.)  
  > "We model the data as homoscedatic within a short and stable observation window with a polarimetric noise level estimated at $\sigma_Q = \sigma_U = 0.01~\text{Jy}$ (cite: wielgus2022orbital)." (Methods, Pre-processing)
- time on source: ~100 minutes of light curves, averaged to ~1 minute, ~100 points per Stokes component  
  > "We reduced the ${\sim}100$ minutes of ALMA light curves by time-averaging over ${\sim}1$ minute intervals, resulting in ${\sim}100$ data points for each Stokes component." (Methods, Pre-processing)
- observing dates: April 11, 2017, directly after an X-ray flare  
  > "On April 11, 2017, Sgr A$^*$ was observed by ALMA directly after a high-energy flare seen in X-ray." (Introduction)
- pi or archival as stated: ALMA data set obtained through the ALMA data portal  
  > "This paper makes use of the ALMA data set ADS/JAO.ALMA#2016.1.01404.V, available through the ALMA data portal." (Data Availability)
- Other facility **Event Horizon Telescope (EHT)**: ALMA observations were part of the larger EHT campaign; EHT results are used for context and comparison  
  > "as part of a larger EHT campaign" (Results)
- External data: ALMA-only linear-polarization light curves Q(t)+iU(t) of Sgr A* on April 11, 2017  
  > "The LP, measured by ALMA-only light curves (cite: Wielgus2022lc; wielgus2022orbital) as a complex time series $Q(t)+iU(t)$" (Results) [from (cite: Wielgus2022lc; wielgus2022orbital)]
- External data: Constant LP component subtracted for the background disk: P_disk = 0.16 Jy, xi_disk = -37 deg  
  > "we subtract a constant LP component with magnitude and angle of $P_{\rm disk}= 0.16~\text{Jy}$, $\xi_{\rm disk}= -37^\circ$ respectively, to account for the background accretion disk" (Methods, Pre-processing) [from (cite: wielgus2022orbital)]
- External data: EVPA de-rotation of 32.2 deg for the estimated Faraday rotation  
  > "We de-rotate the electric vector polarization angle (EVPA) by $32.2^\circ$ to account for the estimated Faraday rotation (cite: wielgus2022orbital)." (Methods, Pre-processing) [from (cite: wielgus2022orbital)]
- External data: Total-intensity regularisation: around 0.3 Jy with standard deviation 0.15 Jy  
  > "we regularize the model to have a total intensity around $0.3~\text{Jy}$ with a standard deviation of $0.15~\text{Jy}$ (cite: wielgus2022orbital)" (Methods, Pre-processing) [from (cite: wielgus2022orbital)]
- External data: Initial time of the analysis and flare reconstruction: 9:20 UT  
  > "Following (cite: wielgus2022orbital) we set 9:20 UT as the initial time of the analysis and 3D reconstruction of the flare." (Methods, Pre-processing) [from (cite: wielgus2022orbital)]
- External data: Sgr A* mass M ~ 4e6 Msun from stellar dynamics  
  > "the mass of Sgr A$^*$ is well constrained through stellar dynamics (cite: ghez2008measuring); $M\simeq 4 {\times} 10^6 M_\odot$ where" (Data fitting) [from (cite: ghez2008measuring)]
- Simulation/model as data: Synthetic ALMA-like light curves from three 3D flare models (Simple Hotspot, Flux Tube, Double Source) at two inclinations (12 and 64 deg) on a Gaussian-random-field accretion disk background, used to validate recovery  
  > "We generate data consisting of three distributions of emission: `Simple Hotspot`, `Flux Tube`, `Double Source`" (Synthetic data generation, Emission flares); "observations are generated at two inclination angles: $\theta_{\rm o}^{\rm lo}=12^\circ$ and $\theta_{\rm o}^{\rm hi}=64^\circ$" (Synthetic data generation, Emission flares)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
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
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Light-curve pre-processing (time averaging, constant LP subtraction, EVPA de-rotation)  
  > "we perform pre-processing according to the procedure outlined in (cite: wielgus2022orbital)" (Data fitting); "Following the procedures outlined in (cite: wielgus2022orbital) we subtract a constant LP component" (Methods, Pre-processing) [from (cite: wielgus2022orbital)]
- Definition of reduced chi-squared used for the data fit  
  > "The data-fit used in this work relies on the reduced $\chi^2$ definitions of (cite: akiyama2019firstIV)." (Data fitting) [from (cite: akiyama2019firstIV)]
- Geodesic computation via explicit parametric form of Kerr null geodesics, implemented in kgeo  
  > "we solve Eq. [\[eq:ode\]](#eq:ode) using the explicit parametric form described by (cite: gralla2020null_supp) and implemented in (cite: kgeo2023_supp)." (General Relativistic Ray Tracing, Ray tracing) [from (cite: gralla2020null_supp; kgeo2023_supp)]
- Light-curve mean flux levels used to scale synthetic flares  
  > "average fluxes matching the real ALMA data (cite: wielgus2022orbital_supp)" (Synthetic data generation, Emission flares) [from (cite: wielgus2022orbital_supp)]

### Not stated but needed to reproduce (our reading)

- The calibrated, time-averaged Stokes I/Q/U light curves themselves (only available from the corresponding author on request); the ALMA calibration and polarization-calibration steps behind them are not described
- Exact time-bin edges and scan gaps used when averaging to ~1 minute
- Number and values of the random seeds ('several initial seeds') and which of them enter the error bars
- Batch size, loss weighting of the I term versus Q and U, and how the total-intensity regularisation enters the loss
- Training/validation split detail beyond ray-position perturbation, and the final emission normalisation or output activation of the MLP
- Value of the volumetric linear-polarization fraction q_f and the vertical magnetic field strength used for the real-data fit
- Distance and coordinates of Sgr A* and the physical scale conversion used (only mass and field of view are given)
- Pixel size and ray-sampling used for the 3D visualisation versus the optimisation grid

## Analysis recipe

1. **Pre-process ALMA LP light curves**: Time-average to ~1 minute, subtract a constant LP component for the disk, de-rotate EVPA, fix noise level and total-intensity regularisation, start at 9:20 UT  
  > "we subtract a constant LP component with magnitude and angle of $P_{\rm disk}= 0.16~\text{Jy}$, $\xi_{\rm disk}= -37^\circ$ respectively, to account for the background accretion disk" (Methods, Pre-processing); "We de-rotate the electric vector polarization angle (EVPA) by $32.2^\circ$ to account for the estimated Faraday rotation (cite: wielgus2022orbital)." (Methods, Pre-processing)
   - parameter: P_disk = 0.16 Jy, xi_disk = -37 deg, EVPA de-rotation 32.2 deg, sigma_Q = sigma_U = 0.01 Jy  
  > "We model the data as homoscedatic within a short and stable observation window with a polarimetric noise level estimated at $\sigma_Q = \sigma_U = 0.01~\text{Jy}$ (cite: wielgus2022orbital)." (Methods, Pre-processing)
   - assumption: Constant LP component interpreted as the ring-like accretion disk; data homoscedastic  
  > "we time average the data, subtract a constant (time-averaged) LP component interpreted as the ring-like accretion disk component observed by the EHT" (Data fitting)
   - fitting: _not stated_
   - validation: Supplementary analysis of different initial times around 9:20 UT  
  > "Supplementary Fig. 3 shows an analysis of different initial times around 9:20 UT, which provides further motivation for the selection of this initial time." (Methods, Pre-processing)
2. **Build orbiting-emission forward model**: Emission e0(x) sheared by Keplerian orbit, polarized synchrotron radiative transfer along Kerr geodesics, summed over image plane to give I, Q, U light curves  
  > "We consider orbits characterized by a Keplerian angular velocity profile (neglecting radial or vertical velocity components), accounting for shearing due to differential rotation" (Assumptions and systematic noise); "We compute light curves by numerically sampling a large field-of-view (FOV) and summing over image-plane coordinates" (Methods, Forward model, 3. Light curves)
   - software: kgeo
   - parameter: Recovery domain 6M <= r <= 20M, |z| <= 4M  
  > "constrained to a domain with a radius of $6{\rm M} \leq r \leq 20 {\rm M}$ and close to the equatorial disk $|z| \leq 4{\rm M}$" (Data fitting)
   - parameter: 64x64 pixel grid, FOV 200 microarcsec  
  > "In our recoveries, we use an evenly sampled $64\times64$ grid for a FOV of $200~\mu {\rm as}$." (Methods, Model selection using Validation-chi2)
   - parameter: Spectral index alpha_nu ~ 1  
  > "the spectral index (reflecting the change in the local emission with frequency) is approximated as $\alpha_\nu\simeq1$ (cite: Narayan2021)" (Methods, Forward model, 2. Image formation)
   - assumption: Homogeneous fixed vertical magnetic field  
  > "we assume a homogeneous vertical magnetic field that is externally fixed and is independent of the flare or accretion disk dynamics." (Assumptions and systematic noise)
   - assumption: Optically thin millimeter emission region  
  > "Another key assumption made by our work is that the millimeter emission region is optically thin." (Assumptions and systematic noise)
   - assumption: Mass of about 4e6 Msun; data fit insensitive to spin so non-spinning black hole used  
  > "Furthermore, Fig. [1](#fig:alma_rec) (blue curve) illustrates that the data-fit is not very sensitive to black hole spin: $a\in[0,1]$." (Data fitting)
   - fitting: _not stated_
   - validation: Checked by varying magnetic field configuration, rotation direction and sub-Keplerian fraction  
  > "we analyze some of the systematic model choices detailed above by exploring the effects of a) magnetic field configuration b) rotation direction and c) sub-Keplerian orbits on the data fit and 3D reconstruction." (Assumptions and systematic noise)
3. **Fit 3D emission with a neural representation at fixed inclination**: Minimise chi-squared over Stokes I, Q, U between data and model light curves, with the 3D emission represented by an MLP with positional encoding  
  > "Mathematically, the 3D emission volume is estimated by minimizing a $\chi^2$ loss between the observed LP and the model prediction." (Data fitting); "we use a small MLP with 4 fully connected layers, where each layer is 128 units wide and uses ReLU activations." (Methods, Neural representation)
   - software: JAX, ADAM, bhnerf
   - parameter: MLP: 4 layers, 128 units, ReLU; positional encoding degree L = 3  
  > "We use a maximum positional encoding degree of $L=3$." (Methods, Neural representation)
   - parameter: ADAM, polynomial learning rate 1e-4 to 1e-6 over 50K iterations, about 1 hour on two NVIDIA Titan RTX GPUs  
  > "were optimized using an ADAM optimizer (cite: kingma2014adam) with a polynomial learning rate transitioning from $1{\rm e}^{-4} \rightarrow 1{\rm e}^{-6}$ over $50{\rm K}$ iterations." (Methods, Optimization procedure); "Run times were ${\sim} 1$ hour on two NVIDIA Titan RTX GPUs." (Methods, Optimization procedure)
   - parameter: Five runs with random initialisation per inclination  
  > "For each inclination, the recovery is run five times with a random initialization for the 3D structure." (Data fitting)
   - assumption: Non-convex stochastic-gradient optimisation reaches a local minimum; solution depends on initialisation  
  > "solving a non-convex optimization problem with stochastic gradient descent methods leads to a local (and not global) minimum." (Data fitting)
   - fitting: Gradient-based chi-squared minimisation (ADAM) of network weights; chi-squared normalised by number of data points; no sampler or priors  
  > "Rather, it is normalized by the total number of data points, which is useful for comparing fit quality in our experiments where degrees of freedom remain fixed." (Data fitting)
   - validation: Error bars from different random initialisations indicate stability of the local optimum, not posterior uncertainty  
  > "Therefore, the error bars are not a measure of posterior uncertainty; rather, they indicate the stability of the locally optimal solution." (Data fitting)
4. **Estimate inclination with validation chi-squared**: Grid over inclination, recover 3D emission at each, compute validation-chi2 on perturbed off-centre ray positions averaged over 10 random rays, take the global minimum  
  > "we avoid the extreme angles of face-on and edge-on by gridding $\theta_{\rm o}\in[4^\circ, 80^\circ]$ (at $2^\circ$ increments)" (Data fitting); "We average $\chi^2$ of 10 randomly sampled (uniform) ray positions to compute validation-$\chi^2$ curves." (Methods, Model selection using Validation-chi2); "$\theta_{\rm o}^\star$ is estimated as the global minimum of the validation $\chi^2$." (Methods, Model selection using Validation-chi2)
   - parameter: Inclination grid 4 to 80 deg in 2 deg steps; perturbation pixel area 3.125 x 3.125 microarcsec^2  
  > "In our recoveries, we used a pixel area of $3.125 \times 3.125~\mu {\rm as}^2$." (Methods, Model selection using Validation-chi2)
   - fitting: _not stated_
   - validation: Simulations show the validation curve recovers true inclination and mitigates over-fitting  
  > "Through simulations, we highlight how this procedure is a more robust selection criterion for models that are not overfitting the fixed ray positions" (Methods, Model selection using Validation-chi2)
5. **Test systematic model choices and synthetic recoveries**: Compare validation-chi2 for vertical, radial and toroidal magnetic fields, CW vs CCW rotation, and sub-Keplerian fractions; recover synthetic hotspot, flux-tube and double-source datasets with accretion-disk noise  
  > "three magnetic field configurations: vertical, radial, and toroidal" (Assumptions and systematic noise); "we highlight the tomographic ability to recover different underlying emission structures and distinguish between different 3D flare morphologies." (Synthetic data recovery)
   - parameter: Angular velocity profile Omega = +/- f_K Omega_K tested; f_K = 0.9 shown  
  > "we set the angular velocity profile to $\Omega= \pm f_{\rm K}\Omega_{\rm K}$ where the $\pm$ sign dictates the direction (`CW/CCW`) and $f_{\rm K}$ the magnitude" (Assumptions and systematic noise)
   - fitting: _not stated_
   - validation: Recovered inclination compared with known synthetic truth  
  > "For each level of noise, $\sigma_P$, we are able to estimate $\theta_{\rm o}^\star$ to within $\pm4^\circ$ of the true value." (Synthetic data recovery, Sensitivity to background noise)

## Software

- **kgeo** 1.0.0: Kerr geodesic computation for ray tracing  
  > "The software packages used analyze the data are available at the following sites: `kgeo` (<https://github.com/achael/kgeo>), `bhnerf` (<https://github.com/aviadlevis/bhnerf>)." (Code Availability)
- **bhnerf** : Neural-representation tomography code for analysing the data  
  > "The software packages used analyze the data are available at the following sites: `kgeo` (<https://github.com/achael/kgeo>), `bhnerf` (<https://github.com/aviadlevis/bhnerf>)." (Code Availability)
- **JAX** : Implementation of the neural network  
  > "The neural network was implemented in `JAX` (cite: jax2018github)." (Methods, Optimization procedure)
- **ADAM** : Optimizer for network weights  
  > "were optimized using an ADAM optimizer (cite: kingma2014adam)" (Methods, Optimization procedure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Preferred observer inclination from validation-chi2 | < 18 | not stated | deg | 4 | Low inclination angles ($\theta_{\rm o}<18^\circ$, Fig. [1](#fig:alma_rec) left panel, red) are preferred by the *validation-$\chi^2$* |
| Radii of the two compact bright regions in the recovered 3D emission | r ~ 11M and 13M | not stated | M (GM/c^2) | 3 | The recovered 3D emission has two compact bright regions at $r \sim 11M, 13M$ |
| Synthetic test: inclination recovery accuracy, Simple Hotspot at low and high inclination | within +/-10 | not stated | deg | 5 | enable estimating $\theta_{\rm o}^\star$ (as the global minimum) to within $\pm10^\circ$ of the underlying true inclination |
| Synthetic test: low-inclination recovery accuracy across three accretion noise levels (Simple Hotspot) | within +/-4 | not stated | deg | 5 | For each level of noise, $\sigma_P$, we are able to estimate $\theta_{\rm o}^\star$ to within $\pm4^\circ$ of the true value. |
| Synthetic test: low-inclination (12 deg) recovery accuracy, all three 3D structures | within +/-6 | not stated | deg | 5 | Our approach is able to estimate $\theta_{\rm o}^{\rm lo}$ to within $\pm 6^\circ$ for all three levels of accretion noise and 3D fiducial datasets. |
| Synthetic test: high-inclination (64 deg) recovery accuracy at low and moderate accretion noise | within +/-16 | not stated | deg | 5 | While low and moderate accretion noise enable detection $\theta_{\rm o}^{\rm hi}$ to within $\pm 16^\circ$ |

## Qualitative findings

- The ALMA light curves are fit very accurately by an orbiting 3D emission structure  
  > "Our model, detailed in the Methods section, is able to fit the ALMA light curve data very accurately" (Results)
- Vertical magnetic field, clockwise rotation and Keplerian orbit are preferred by the data fit  
  > "vertical magnetic fields are preferred with a lower validation-$\chi^2$ value." (Assumptions and systematic noise); "highlight how clockwise rotation (`CW`) and a Keplerian orbit are favorable to counter-clockwise rotation (`CCW`) or sub-Keplerian orbits" (Assumptions and systematic noise)
- Azimuthal and radial positions of recovered structures are stable across inclinations and initialisations; exact angular extent is not  
  > "While the exact angular extent of the structures is not stable, the azimuthal and radial positions appear stable and consistent with the average structure." (Data fitting)
- Under high inclination Doppler boosting makes some sources dim, creating an invisible region in the recovery  
  > "reveal an “invisible region” at high inclination angles where sources are dim due to Doppler boosting." (Synthetic data recovery, Recovery blind spot)

## Claim tuples

- H: A 3D structure orbiting Sgr A* can be recovered from unresolved ALMA LP light curves | E: Neural-representation orbital polarimetric tomography fit to the April 11, 2017 ALMA Q/U light curves | R: Two compact bright regions at r ~ 11M and 13M with a good fit to the light curves | F: An azimuthally elongated bright structure near 11M trailed by a dimmer source near 13M | **partially**
- H: The data constrain the observer inclination | E: Grid over inclination with validation-chi2 selection | R: Low inclinations below 18 deg are preferred | F: Low inclination favoured, consistent with earlier EHT and GRAVITY analyses | **supported**
- H: Vertical magnetic field, clockwise Keplerian rotation are favoured over alternatives | E: Compare validation-chi2 for vertical, radial and toroidal fields, CW vs CCW, and sub-Keplerian fractions | R: Vertical field and CW Keplerian orbit give lower validation-chi2 | F: Data favour vertical field and clockwise Keplerian rotation | **supported**
- H: The method can recover 3D morphology and inclination in controlled tests | E: Synthetic ALMA-like datasets with three flare morphologies, two inclinations and accretion-disk noise | R: Inclination recovered to within a few to ~16 deg; morphology captured but smoothed; high-inclination dim regions are a blind spot | F: The approach works on simulated data with known limitations | **supported**

## Reasoning

- Why this data: High signal-to-noise and cadence of the ALMA data plus LP information  
  > "We take advantage of the very high signal-to-noise and cadence of the ALMA dataset (cite: Wielgus2022lc), as well as the linear polarization information (cite: wielgus2022orbital)." (Introduction)
- Why this method: Only LP light curves are fit because the background disk's unpolarised intensity is uncertain  
  > "The choice to only fit the LP light curves reflects the uncertainty associated with the un-polarized intensity of the background accretion disk." (Introduction)
- Alternative: Radial and toroidal magnetic fields, counter-clockwise rotation and sub-Keplerian orbits were tested; the radial-field best fit is a faint diffuse structure  
  > "For a radial magnetic field, the best fit recovery is not a compact bright emission region" (Assumptions and systematic noise); "However, this consistency eventually breaks down at strong deviations from the Keplarian velocity assumption" (Assumptions and systematic noise)
- Alternative: An alternative jet interpretation is not modelled  
  > "While our model does not account for an alternative jet interpretation" (Assumptions and systematic noise)
- How they decided it was enough: _not stated_
- Limitation (authors): Recovery is highly ill-posed and not unique; relies on the imposed gravitational and synchrotron models  
  > "The ill-posed inverse problem we solve does not have a unique solution." (Data fitting); "The robustness of the results thus relies on the validity of the constraints imposed by the gravitational and synchrotron emission models." (Introduction)
- Limitation (authors): Error bars show stability of local optima, not posterior uncertainty  
  > "Therefore, the error bars are not a measure of posterior uncertainty; rather, they indicate the stability of the locally optimal solution." (Data fitting)
- Limitation (authors): Un-modelled accretion-disk variability affects recovery because the model attributes all dynamics to orbital motion  
  > "Any un-modeled accretion dynamics will impact recovery results as our model fully attributes dynamics to orbital motion." (Synthetic data recovery, Sensitivity to background noise)
- Caveat (inferred, ours): No uncertainty on the recovered radii or the inclination beyond seed-to-seed scatter and a heuristic validation-chi2 curve
- Caveat (inferred, ours): Single epoch of ~100 minutes of unresolved data; recovered 3D structure is strongly shaped by the neural-network prior and imposed physics
- Caveat (inferred, ours): Light-curve pre-processing (disk subtraction, EVPA de-rotation, noise level) is inherited from Wielgus et al. 2022 and not independently tested
- Caveat (inferred, ours): Calibrated light curves are not public, so the real-data fit cannot be reproduced without contacting the authors

## Reproducibility

- Data public (paper): ALMA data set available through the ALMA data portal  
  > "This paper makes use of the ALMA data set ADS/JAO.ALMA#2016.1.01404.V, available through the ALMA data portal." (Data Availability)
- Products in archive: Fully calibrated data are not in the archive; available from the corresponding author on request  
  > "Fully calibrated data and other materials are available from the corresponding author upon reasonable request." (Data Availability)
- Code: kgeo and bhnerf released on GitHub  
  > "The software packages used analyze the data are available at the following sites: `kgeo` (<https://github.com/achael/kgeo>), `bhnerf` (<https://github.com/aviadlevis/bhnerf>)." (Code Availability)
- Missing: Calibrated Stokes light curves (on request only)
- Missing: Random seeds, batch and loss-weighting details
- Missing: Polarization calibration and ALMA processing steps behind the light curves
- Data volume (inferred): Small for the analysis itself (~100 time points per Stokes parameter); raw ALMA visibilities of the VLBI-mode project are not needed if the light curves are obtained
- Score (inferred): 4/5, Code is public and the model is well specified, but the calibrated light curves are only available on request, many pre-processing settings are inherited, and results are model-dependent.
- Rediscovery candidate: no, The calibrated input light curves are not public and the main results are model-dependent reconstructions rather than simple numeric measurements.

## Links

- Method: (cite: wielgus2022orbital) (Source of the pre-processing procedure and the hotspot model compared against)
- Method: (cite: levis2022gravitationally) (Prior neural-representation emission tomography in curved spacetime)
- Companion: (cite: Wielgus2022lc) (Source of the ALMA light curves)
- Companion: (cite: yfantis2023) (Companion analysis of the same flare)
- Related: Event Horizon Telescope April 2017 campaign

## Checks

```json
{
 "quotes": 87,
 "quotes_ok": 87,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 61,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
