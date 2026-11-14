# Measuring the Two-dimensional Thermal Structures of Protoplanetary Disks

`2025ApJ...994...98F` | The Astrophysical Journal 2025 | first author: Fehr, Anna J. | arXiv: 2509.15196 | DOI: 10.3847/1538-4357/ae0ca2

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How can the 2-D thermal structure T(r,z) of a protoplanetary disk be measured annulus by annulus from optically thick CO isotopologue emission, tested on synthetic models and applied to HD 163296?  
  > "We present a flexible, annulus-by-annulus method to constrain the 2-D thermal structure of a protoplanetary disk from optically thick spectral line emission." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **Synthetic disk model**: coordinates not applicable  
  > "the distance $d = 100$ pc, inclination $i=50^\circ$, and position angle $\vartheta=90^\circ$" (2.2 Model Processing); z/distance d = 100 pc  
  > "the distance $d = 100$ pc, inclination $i=50^\circ$, and position angle $\vartheta=90^\circ$" (2.2 Model Processing); distance from model assumption  
  > "the distance $d = 100$ pc, inclination $i=50^\circ$, and position angle $\vartheta=90^\circ$" (2.2 Model Processing)

## Data provenance

- ALMA projects: 2018.1.01055.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival MAPS project data  
  > "We selected ALMA observations of the HD 163296 disk from the MAPS project (cite: Oberg21)." (5.3 Demonstration with ALMA Data: HD 163296)
- Line: 12CO J=2-1 (not stated)
- Line: 13CO J=2-1, J=1-0 (not stated)
- Line: C18O J=2-1, J=1-0 (not stated)
- External data: HD 163296 ALMA MAPS image cubes  
  > "We selected ALMA observations of the HD 163296 disk from the MAPS project (cite: Oberg21)." (5.3 Demonstration with ALMA Data: HD 163296) [from Öberg et al. 2021 (cite: Oberg21)]
- External data: HD 163296 geometric parameters from CO J=2-1  
  > "We adopted the geometric parameters measured from the same CO $J$=2$-$1 observations in (cite: Izquierdo23)" (5.3 Demonstration with ALMA Data: HD 163296) [from (cite: Izquierdo23)]
- External data: Law et al. best-fit temperature models for comparison  
  > "They deviate from the (cite: Law21) best-fit model profiles, indicating that a single power law is not a good match to the temperature profile." (5.3 Demonstration with ALMA Data: HD 163296) [from (cite: Law21)]
- Simulation/model as data: RADMC-3D LTE synthetic CO/13CO/C18O cubes (J=1-0 to 6-5) of a parametric disk, with T0=100 K, q_T=-0.5, a0=0.05, gamma0=5, 1 Msun, i=50 deg, d=100 pc  
  > "We simulated the $J$=1$-$0, 2$-$1, 3$-$2, 4$-$3, and 6$-$5 emission lines for CO, $^{13}$CO, and C$^{18}$O" (2.2 Model Processing)

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
- smoothing: disksurf smooth=3 (Gaussian kernel, 3x beam major axis)  
  > "the image cube was smoothed with a 1D Gaussian kernel three times the size of the beam major axis (`smooth=3`)" (3.1 Emission Surfaces)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Velocity profile extraction method  
  > "we extracted the velocity profile from the emission cube following the method of (cite: Andrews24)." (4.3 Surface and Kinematic Uncertainties) [from (cite: Andrews24)]
- Direct 2-D fitting procedure for comparison  
  > "following the procedure outlined by (cite: Law21) and summarized here." (5.2 Fitting Points in Two Dimensions) [from (cite: Law21)]
- Surface extraction by deprojecting isovelocity loop peaks  
  > "deprojected them into the disk coordinate frame (cite: Pinte18) using the `disksurf` package (cite: Teague21ds)" (3.1 Emission Surfaces) [from (cite: Pinte18)]

### Not stated but needed to reproduce (our reading)

- Which MAPS data products (image cubes, resolution, robust weighting) were used for HD 163296
- Prior ranges for the HD 163296 fits if different from synthetic tests
- Noise (RMS) values for the MAPS cubes
- Distance adopted for HD 163296
- Number of surface realizations N and radial annulus widths for HD 163296
- Which lines were treated as optically thick beyond the T_b<20 K criterion

## Analysis recipe

1. **Generate synthetic cubes**: RADMC-3D LTE raytracing of parametric disk, convolved with 0.1'' beam, noise 2 mJy/beam per channel  
  > "achieving an rms of 2 mJy beam$^{-1}$ in each 50 m s$^{-1}$ channel" (2.2 Model Processing)
   - software: RADMC-3D
   - assumption: X_CO=5e-5, T_frz=20 K, sigma_crit=0.01 g cm-2, D_CO=1e-3, CO/13CO=69, CO/C18O=557  
  > "CO$/^{13}\text{CO} =69$ and CO$/^{18}\text{CO}=557$ (cite: Wilson99)" (2.1 Physical Conditions)
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract emission surfaces**: disksurf isovelocity-loop peak extraction in three passes, then binning into annuli of half beam FWHM  
  > "For the second and third extractions, we filtered out pixels with SNR $<$ 2 and SNR $<$ 3 (`min_snr = `$[2, 3]$), respectively." (3.1 Emission Surfaces)
   - software: disksurf
   - parameter: smooth=3, min_snr=[1,2,3], nbeams=[2.0,1.0]  
  > "The initial extraction was clipped at that noise floor (`min_snr=1`)." (3.1 Emission Surfaces)
   - assumption: Axisymmetry, no external contamination  
  > "This strategy assumes an axisymmetric structure and kinematics" (3 Methods)
   - fitting: _not stated_
   - validation: Compared to true tau=2/3 surfaces from RADMC-3D tausurf  
  > "We used the `tausurf` mode of raytracing in `RADMC-3D` to generate cubes of the disk-frame coordinates" (4.1 Inferring the Vertical Temperature Structure)
3. **Measure brightness temperature profiles**: Moment-8 map (RMS subtracted) via bettermoments, azimuthally averaged along surface with gofish, converted with Planck function  
  > "we subtracted the RMS of the cube from the moment-8 maps before extracting the radial profiles" (3.2 Brightness Temperature Profiles)
   - software: bettermoments, gofish
   - assumption: Optically thick LTE gas so T_gas = T_b  
  > "For an optically thick gas in LTE, the gas temperature is equivalent to the peak brightness temperature along each line-of-sight" (3.2 Brightness Temperature Profiles)
   - fitting: _not stated_
   - validation: _not stated_
4. **Correct beam dilution bias**: Forward model T_m with Gaussian or top-hat emitting-region kernel K based on Keplerian width of the emitting region; fit to measured intensity  
  > "In each annulus, for a given model temperature $T_{\rm m}$, we computed the corresponding blackbody intensity $B_\nu(T_{\rm m})$, applied $\mathcal{K}(T_{\rm m})$" (4.2 Spatial Resolution Bias)
   - software: emcee
   - parameter: 16 walkers, 300 steps, 50 burn-in; uniform prior T_m 0-10,000 K  
  > "we ran 16 `emcee` walkers for 300 steps, initialized by random draws around $T_b$." (4.2 Spatial Resolution Bias)
   - assumption: Keplerian velocity, thermal broadening, small temperature gradient across emitting region  
  > "If we assume that thermal broadening dominates the shape of the line" (4.2 Spatial Resolution Bias)
   - fitting: Gaussian likelihood on intensity, emcee  
  > "We defined the log-likelihood function" (4.2 Spatial Resolution Bias)
   - validation: Corrected profiles agree with truth within 10% for r>10 au  
  > "the corrected $T_b(r)$ profiles agree with the expected values to within 10% for $r>10$ au" (4.3 Surface and Kinematic Uncertainties)
5. **Infer stellar mass**: Fit Keplerian v_peak(r) to extracted velocity profile excluding inner ~5 beams, over 200 surface draws  
  > "excluding the inner $\sim5$ beams to mitigate the spatial resolution bias" (4.3 Surface and Kinematic Uncertainties)
   - software: emcee
   - parameter: uniform prior M* 0-5 Msun, 32 walkers, 1000 steps, 300 burn-in  
  > "sampled the posterior with `emcee`, using 32 walkers for 1000 steps." (4.3 Surface and Kinematic Uncertainties)
   - fitting: emcee  
  > "We used the `emcee` Monte Carlo Markov Chain sampler (cite: ForemanMackey13) to explore the (log-)posterior distribution," (Methods, The T(z) Inference Step)
   - validation: Recovered 0.99±0.02 Msun for the 1 Msun model  
  > "we found $M_* = 0.99 \pm 0.02M_\odot$" (4.3 Surface and Kinematic Uncertainties)
6. **Infer vertical T(z) in each annulus**: Fit T_mid, gamma, a_z per annulus to (z, T_b) of all lines, repeated over N surface realizations  
  > "The posterior sampling was conducted for each of the $N$ realizations of the surface" (3.3 The T(z) Inference Step)
   - software: emcee
   - parameter: uniform priors T_mid U(0,1500 K), gamma U(0,100), a_z U(0,1); 32 walkers, 50,000 steps, 10,000 burn-in (synthetic tests)  
  > "We removed the first 10,000 steps as burn-in." (4.1 Inferring the Vertical Temperature Structure)
   - assumption: Parametric form: isothermal midplane then exponential rise; lines optically thick where T_b>20 K  
  > "We approximated where each line became optically thin based on where $T_b(r) < 20$ K." (5.3 Demonstration with ALMA Data: HD 163296)
   - fitting: Gaussian likelihood with uniform priors, emcee  
  > "We defined a Gaussian likelihood function" (3.3 The T(z) Inference Step)
   - validation: Compared with injected temperature; accuracy |Tm-Tgas| and precision sigma_T  
  > "We defined accuracy as the deviation of the inferred temperature from the true gas temperature" (4.1 Inferring the Vertical Temperature Structure)
7. **Apply to HD 163296**: Same pipeline on MAPS cubes, geometry from Izquierdo23, M* fit from 12CO J=2-1, annuli fitted to r=3.0'' where at least two lines available  
  > "only fit annuli out to $r=3.0\ensuremath{''}$, where at least two lines are available" (5.3 Demonstration with ALMA Data: HD 163296)
   - software: disksurf, gofish, bettermoments, emcee
   - fitting: _not stated_
   - validation: Compared to Law21 profiles  
  > "our midplane and atmosphere temperature profiles agree outside $1.0\ensuremath{''}$, but exhibit a steeper temperature increase in the inner disk." (5.3 Demonstration with ALMA Data: HD 163296)

## Software

- **RADMC-3D** : LTE raytracing of synthetic cubes and tausurf  
  > "we used the local thermodynamic equilibrium (LTE) excitation and raytracing capabilities of `RADMC-3D`" (2.2 Model Processing)
- **disksurf** : emission surface extraction  
  > "using the `disksurf` package (cite: Teague21ds)" (3.1 Emission Surfaces)
- **bettermoments** : moment-8 peak intensity maps  
  > "constructed a peak intensity (moment-8) map from the cube using the `bettermoments` package" (3.2 Brightness Temperature Profiles)
- **gofish** : azimuthally averaged intensity along emission surface  
  > "used the `gofish` package (cite: Teague19fish) to extract the azimuthally averaged intensity" (3.2 Brightness Temperature Profiles)
- **emcee** : MCMC posterior sampling  
  > "We used the `emcee` Monte Carlo Markov Chain sampler (cite: ForemanMackey13)" (3.3 The T(z) Inference Step)
- **LAMDA database** : CO molecular data  
  > "The CO quantum properties were compiled from the LAMDA database (cite: Schoier05)" (2.2 Model Processing)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Recovered stellar mass, synthetic model | 0.99 | 0.02 | Msun | 5 | we found $M_* = 0.99 \pm 0.02M_\odot$ |
| HD 163296 stellar mass | 1.93 | +0.11/-0.09 | Msun | 7 | found $M_*=1.93\substack{+0.11\\-0.09}$ $M_\odot$ |
| Surface bias for CO | ~0.1 | not stated | dimensionless (Δz/r) | 2 | biasing them low by up to $\Delta z/r \approx0.1$ for CO and $\Delta z/r \approx0.15$ for C$^{18}$O |
| Resolution-bias intensity underestimate | up to 50% | not stated | percent | 4 | The bias can extend up to 8 times the size of the beam, and the intensity can be underestimated by as much as 50%. |

## Qualitative findings

- HD 163296 temperature decreases smoothly with radius with no substructure, and departs from a single power law  
  > "The temperature decreases smoothly with radius within $1 \sigma_T$ uncertainties, showing no evidence of substructure." (5.3 Demonstration with ALMA Data: HD 163296)

## Claim tuples

- H: Annulus-by-annulus inference recovers the 2-D thermal structure | E: Inference on synthetic cubes with true surfaces | R: Temperatures consistent within <1.5 sigma; J=1-0 lines improve accuracy | F: Even a few CO lines constrain T(r,z) | **supported**
- H: Beam dilution biases peak T_b at small radii and can be corrected | E: Forward-model with emitting-region kernel | R: Corrected profiles within 10% for r>10 au | F: Correction is accurate | **supported**
- H: Emission-surface extraction is the dominant systematic | E: Compare extracted and true surfaces | R: Downward bias propagates to overestimated temperatures | F: Biased surfaces are the main error source | **supported**
- H: The method applies to real data | E: Application to HD 163296 MAPS cubes | R: Smooth T(r,z), non-power-law radial dependence; cannot rule out alternative vertical prescriptions | F: Parametric radial models may obscure disk complexity | **partially**

## Reasoning

- Why this data: HD 163296 chosen for moderate inclination, large CO extent, axisymmetry and no foreground contamination  
  > "is generally axisymmetric (cite: Teague21), and does not show problematic foreground contamination." (5.3 Demonstration with ALMA Data: HD 163296)
- Why this method: _not stated_
- Alternative: Direct 2-D fitting of all {r,z} points gives deceptively tight posteriors and is biased  
  > "The 2-D fitting approach yields deceptively tight posteriors, substantially underestimating the true uncertainties at all radii and heights." (5.2 Fitting Points in Two Dimensions)
- How they decided it was enough: _not stated_
- Limitation (authors): Surface bias and limited number of lines per annulus prevent discriminating between vertical temperature prescriptions  
  > "given the small number of points per annulus we cannot rule out alternate temperature prescriptions" (5.3 Demonstration with ALMA Data: HD 163296)
- Caveat (inferred, ours): Only one real disk tested; synthetic model uses same parametric form as the fit
- Caveat (inferred, ours): HD 163296 results have no ground truth
- Caveat (inferred, ours): Surface bias not corrected for real data
- Caveat (inferred, ours): Optically thick criterion T_b<20 K is a heuristic

## Reproducibility

- Data public (paper): MAPS archival ALMA data (2018.1.01055.L)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01055.L." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Analysis code for the correction and inference not stated as released
- Missing: Exact MAPS cube versions and beams
- Missing: HD 163296 distance and geometry numbers
- Data volume (inferred): ~10-50 GB (MAPS cubes for several lines)
- Score (inferred): 3/5, Method well specified with sampler settings and synthetic model parameters, but code release and exact HD 163296 inputs are not stated.
- Rediscovery candidate: yes, Public MAPS data and detailed recipe; numeric results such as M*=1.93 Msun can be checked, though some inputs are inherited.

## Links

- Method: (cite: Pinte18) (emission surface extraction method)
- Method: (cite: Law21) (2-D temperature fitting and HD 163296 comparison)
- Method: (cite: Andrews24) (velocity extraction and surface bias)
- Method: (cite: Teague21ds) (disksurf)
- Companion: (cite: Oberg21) (MAPS data)
- Companion: (cite: Izquierdo23) (HD 163296 geometry)
- Related: MAPS (ALMA large program 2018.1.01055.L)

## Checks

```json
{
 "quotes": 62,
 "quotes_ok": 62,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 48,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
