# ALMA Observations of Infalling Flows toward the Keplerian Disk around the Class I Protostar L1489 IRS

`2014ApJ...793....1Y` | The Astrophysical Journal 2014 | first author: Yen, Hsi-Wei | arXiv: 1407.2699 | DOI: 10.1088/0004-637X/793/1/1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How does infalling envelope gas connect to the Keplerian disk around the Class I protostar L1489 IRS, and what are the disk and infall properties?  
  > "Our next interest is direct imaging of the transition from an outer infalling envelope to an inner Keplerian disk in protostellar sources." (Introduction)
- Target **L1489 IRS**: coordinates RA 4h04m43.07s, Dec +26d18m56.3s (J2000, continuum point source)  
  > "a Class I protostar with a bolometric luminosity of 3.7 $L_\ensuremath{\odot}$ (Furlan et al. 2008) in the Taurus molecular cloud ($d$ = 140 pc)" (Introduction); "located at $\alpha$(J2000) = $4^{h}04^{m}43.07s$, $\delta$(J2000) = $26\ensuremath{^\circ}18\ensuremath{'}56.3\ensuremath{''}$" (1.3 mm Continuum Emission); z/distance 140 pc  
  > "a Class I protostar with a bolometric luminosity of 3.7 $L_\ensuremath{\odot}$ (Furlan et al. 2008) in the Taurus molecular cloud ($d$ = 140 pc)" (Introduction); "located at $\alpha$(J2000) = $4^{h}04^{m}43.07s$, $\delta$(J2000) = $26\ensuremath{^\circ}18\ensuremath{'}56.3\ensuremath{''}$" (1.3 mm Continuum Emission); distance from Taurus molecular cloud distance (no specific citation given)  
  > "a Class I protostar with a bolometric luminosity of 3.7 $L_\ensuremath{\odot}$ (Furlan et al. 2008) in the Taurus molecular cloud ($d$ = 140 pc)" (Introduction); "located at $\alpha$(J2000) = $4^{h}04^{m}43.07s$, $\delta$(J2000) = $26\ensuremath{^\circ}18\ensuremath{'}56.3\ensuremath{''}$" (1.3 mm Continuum Emission)

## Data provenance

- ALMA projects: 2011.0.00210.S
- bands: Band 6 (1.3 mm)  
  > "The ALMA Band 6 observations of L1489 IRS were made with its extended configuration of 23 antennas at the cycle 0 stage on 2012 August 9." (Observations)
- frequencies and spectral setup: FDM, 4 spectral windows of 234 MHz, 3840 channels each, Hanning smoothed, 122 kHz resolution (~0.17 km/s C18O/SO, ~0.16 km/s 12CO)  
  > "The correlator was configured in the Frequency Division Mode (FDM) to provide four independent spectral windows with a bandwidth of 234 MHz." (Observations); "Hanning smoothing was applied to the spectral channels, resulting in a frequency resolution of 122 kHz." (Observations)
- continuum bandwidth: ~550 MHz at 225 GHz, from emission-free channels  
  > "Emission-free channels in all of the four spectral windows were integrated to create the continuum image, which has a central frequency of 225 GHz and a bandwidth of $\sim$550 MHz." (Observations)
- arrays: 23 antennas, extended configuration, Cycle 0  
  > "The ALMA Band 6 observations of L1489 IRS were made with its extended configuration of 23 antennas at the cycle 0 stage on 2012 August 9." (Observations)
- configurations: _not stated_
- baselines: ~13 m to ~383 m  
  > "The projected $uv$ distances range from $\sim$13 m to $\sim$383 m" (Observations)
- angular resolution: 0.92x0.71'' continuum; 0.85x0.72'' 12CO; 0.96x0.75'' C18O; 0.96x0.74'' SO  
  > "The synthesized beams of the CLEANed images are 0.92$''$ $\times$ 0.71$''$ for the 1.3 mm continuum, 0.85$''$ $\times$ 0.72$''$ for the $^{12}$CO line" (Observations)
- max recoverable scale: 17'' (~2400 AU) at 10% level  
  > "our observations are insensitive to structures at the scales larger than 17$\ensuremath{''}$ ($\sim$2400 AU) at a 10% level (Wilner & Welch 1994)" (Observations)
- sensitivity: ~0.15 mJy/beam continuum; ~8 mJy/beam per channel lines  
  > "The rms noise levels are $\sim$0.15 mJy beam $^{-1}$ in the 1.3 mm continuum image and $\sim$8 mJy beam$^{-1}$ per channel in the line images." (Observations)
- time on source: 74 minutes  
  > "L1489 IRS was observed for 74 minutes (on-source time)." (Observations)
- observing dates: 2012 August 9  
  > "at the cycle 0 stage on 2012 August 9." (Observations)
- pi or archival as stated: _not stated_
- Line: 12CO 2-1 (230.538 GHz)
- Line: C18O 2-1 (219.560358 GHz)
- Line: SO 5_6-4_5 (219.949433 GHz)
- External data: Single-dish 1.3 mm flux (~150 mJy in 1') and envelope mass 0.02 Msun  
  > "the 1.3 mm flux integrated over the 1$\ensuremath{'}$ (8400 AU) region around L1489 IRS is $\sim$150 mJy (Motte & André 2001)" (1.3 mm Continuum Emission) [from Motte & André 2001]
- External data: IRAM 30m C18O flux and (2-1)/(3-2) ratio used for missing flux and optical depth  
  > "By comparing the total C$^{18}$O flux observed with the IRAM 30 m telescope (Hogerheijde et al. 1998), $\sim$20% of the total C$^{18}$O flux is recovered" (C18O (2–1) Emission) [from Hogerheijde et al. 1998]
- External data: C18O abundance 3e-7  
  > "$X_{\rm C^{18}O}$ is the C$^{18}$O abundance adopted to be 3 $\times$ 10$^{-7}$ (Frerking et al. 1982)" (Analysis) [from Frerking et al. 1982]
- External data: Disk scale height 25 AU at 100 AU  
  > "$h_0$ is adopted to be the previously estimated value, 25 AU (Eisner et al. 2005)" (Analysis) [from Eisner et al. 2005]

## Processing

### Calibration

- pipeline or manual: Standard Cycle 0 reduction script in CASA  
  > "Calibration of the raw visibility data were performed with the standard reduction script for the Cycle 0 data, which uses tasks in Common Astronomy Software Applications (CASA)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Callisto, Butler-JPL-Horizons 2010 model; J0522-364 bandpass, J0325+226 gain  
  > "The absolute flux value of the amplitude calibrator, Callisto, was derived from the CASA Butler-JPL-Horizons 2010 model" (Observations); "J0522$-$364 ($\sim$4.7 Jy) and J0325+226 ($\sim$0.3 Jy) were observed as bandpass and gain calibrators." (Observations)
- flux scale uncertainty: 10%  
  > "which gives an estimated systematic flux uncertainty of 10$\%$" (Observations)
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "CLEANed with the CASA task “clean”." (Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = +0.5  
  > "The calibrated visibility data were Fourier-transformed with the Briggs robust parameter of +0.5" (Observations)
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
- final beam: 0.92x0.71'' continuum; C18O 0.96x0.75''  
  > "The synthesized beams of the CLEANed images are 0.92$''$ $\times$ 0.71$''$ for the 1.3 mm continuum" (Observations)
- final rms: ~0.15 mJy/beam continuum; ~8 mJy/beam per channel  
  > "The rms noise levels are $\sim$0.15 mJy beam $^{-1}$ in the 1.3 mm continuum image" (Observations)

### Inherited from earlier work

- Standard Cycle 0 reduction script for calibration  
  > "performed with the standard reduction script for the Cycle 0 data" (Observations) [from ALMA Cycle 0 standard script]
- Disk power-law indices p=-1.5, q=-0.4 initial values  
  > "typical power-law indices of the density and temperature profiles of disks around T Tauri stars ($p = -1.5$ and $q = -0.4$; Guilloteau & Dutrey 1994" (Analysis) [from Guilloteau & Dutrey 1994; Dutrey et al. 1998; Guilloteau et al. 2011]
- Dust opacity law kappa=0.1(0.3mm/lambda)^beta cm2/g, beta=1  
  > "$\kappa_{\lambda} = 0.1 \times (0.3\ {\rm mm}/\lambda)^{\beta}$ cm$^{2}$ g$^{-1}$ (Beckwith et al. 1990)" (Analysis) [from Beckwith et al. 1990; Jørgensen et al. 2007]
- Parabolic infall trajectories and velocity/density field  
  > "(Ulrich 1976)" (Analysis) [from Ulrich 1976; Mendoza et al. 2004]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, mask, cell and image size, number of iterations
- Line-free channels used for continuum and continuum subtraction
- CASA version used
- Exact channel width and velocity grid of imaged cubes
- Whether the fit used a fixed beam-convolved model and the pixel/likelihood noise definition
- Model grid details for infall flows (widths, n1 choice procedure)
- Whether primary beam correction applied

## Analysis recipe

1. **Fit continuum**: Point source plus Gaussian fit in image plane  
  > "intensity distribution can be described by a combination of a point source and a Gaussian intensity distribution (Figure 1b) derived by the MIRIAD fitting program, $imfit$" (1.3 mm Continuum Emission)
   - software: MIRIAD imfit
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit thin Keplerian disk to high-velocity C18O**: chi2 fitting of axisymmetric geometrically-thin LTE disk model to convolved channel maps, staged free parameters  
  > "we have built axisymmetric disk models with the geometrically-thin approximation, generated model C$^{18}$O images, and performed $\chi^2$ fitting to the observed channel maps of the high-velocity ($|V| \gtrsim 2.5$ km s$^{-1}$) C$^{18}$O emission." (Analysis)
   - parameter: Fit region central 2''x2'', velocities -6.1 to -2.5 and 2.5 to 7.1 km/s; Rd fixed 200 AU  
  > "We select the central 2$\ensuremath{''}$ $\times$ 2$\ensuremath{''}$ region and the velocity ranges of $-$6.1 to $-$2.5 and 2.5 to 7.1 km s$^{-1}$" (Analysis)
   - assumption: d=140 pc, LTE, X(C18O)=3e-7, Gaussian line profile  
  > "$d$ is the distance of 140 pc" (Analysis)
   - fitting: Grid chi2 minimization with staged parameter sets; uncertainty from delta reduced chi2 = 1 with others fixed  
  > "we adopt the parameter range that gives a reduced $\chi^2$ of 1+$\chi^2_{\rm min}$ as the fitting uncertainty" (Analysis)
   - validation: Tested different initial p and q; residuals mostly <=3 sigma  
  > "The levels of of residuals are all $\lesssim$4$\sigma$ and mostly $\lesssim$3$\sigma$" (Analysis)
3. **Disk mass from continuum**: Optically thin dust mass M=F d^2/(kappa B(T))  
  > "The mass of the Keplerian disk is then estimated to be $\sim$0.003–0.007 $M_\ensuremath{\odot}$ with a dust temperature of 55–25 K" (Analysis)
   - assumption: kappa1.3mm=0.023 cm2/g, beta=1, Tdust 55-25 K from the model  
  > "the mass opacity at 1.3 mm is 0.023 cm$^{2}$ g$^{-1}$ with $\beta = 1.0$" (Analysis)
   - fitting: _not stated_
   - validation: _not stated_
4. **Flared disk and SO ring models**: 3D flared disk (h0=25 AU, b=1.35) from best-fit; SO ring scaled C18O cube by SO/C18O ratio ~0.6 between 250-390 AU; compared via P-V diagrams  
  > "we simply scaled the model C$^{18}$O image cubes by the SO/C$^{18}$O intensity ratio ($\sim$0.6) in the radial range of the ring" (Analysis)
   - software: RADEX
   - assumption: LTE, isotropic T=44(r/100AU)^-0.3 K  
  > "$T(r) = 44 \cdot (r/100\ {\rm AU})^{-0.3}$ K for simplicity" (Analysis)
   - fitting: _not stated_
   - validation: Visual comparison of model and observed P-V diagrams  
  > "The linear velocity gradient seen in the SO emission as well as the intensity peaks at positional offsets of $\sim$$\pm$2$\ensuremath{''}$ and velocities of $\sim$$\pm$2 km s$^{-1}$ can be reproduced with our ring model." (Analysis)
5. **Model infalling flows**: Trace protrusion ridges, fit parabolic Ulrich trajectories with Rc=300 AU and free theta0, phi0; build infall+disk model and compare moment maps and P-V with Keplerian-protrusion alternative  
  > "we adopted the deprojected radius of these intensity peaks ($\sim$300 AU on the assumption the inclination angle of the disk plane $\sim$66$^\circ$) as the centrifugal radius of the infalling material" (Analysis)
   - parameter: Initial solid angle theta0±3, phi0±3 deg; n1=3e7 cm-3; flow lengths 5000 AU (red), 2000 AU (blue)  
  > "both redshifted and blueshifted infall flows have an initial solid angle of $\theta_0\pm3\ensuremath{^\circ}$ and $\phi_0\pm3\ensuremath{^\circ}$, $n_1$ of 3 $\times$ 10$^{7}$ cm$^{-3}$" (Analysis)
   - assumption: Gravity dominated by 1.6 Msun protostar, conserved angular momentum, zero total energy  
  > "On the assumption that the gravity is dominated by the central protostar, parabolic trajectories of infalling material are described as" (Analysis)
   - fitting: Trajectory matched to measured ridge peak positions (not a formal fit)  
  > "searched for the best-fit trajectories that trace the measured peak positions (green filled squares in Figure [13](#infall)) and reproduce the curvatures of the protrusions." (Analysis, Non-Keplerian Components: Infalling Flows)
   - validation: Infall model reproduces protrusion velocity structure better than coplanar Keplerian model  
  > "Figure 16 shows that the velocity structures of the protrusions can be explained by the infalling model better than the Keplerian rotation model." (Analysis)
6. **Infall mass, rate and angular momentum**: C18O flux at medium velocity gives mass (LTE, Tex 10-40 K); divide by infall time ~1e4 yr; compare specific angular momentum sqrt(GM Rc)/sin theta0 with sqrt(GM Rd)  
  > "the mass of the infalling flows is estimated to be 4–7 $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$, assuming the LTE condition, excitation temperature of the C$^{18}$O emission of 10–40 K" (Discussion)
   - assumption: X(C18O)=3e-7  
  > "the C$^{18}$O abundance of 3 $\times$ 10$^{-7}$ (Frerking et al. 1982)" (Discussion)
   - fitting: _not stated_
   - validation: Missing flux 20-50% noted; order-of-magnitude estimate  
  > "this estimate of the mass of the infalling flows should be regarded as just an order estimate" (Discussion)

## Software

- **CASA** : Calibration with standard script and clean imaging  
  > "CLEANed with the CASA task “clean”." (Observations)
- **MIRIAD** : imfit for continuum fitting  
  > "derived by the MIRIAD fitting program, $imfit$" (1.3 mm Continuum Emission)
- **RADEX** : SO optical depth and column density  
  > "With the statistical equilibrium radiative transfer code, RADEX (Van der Tak et al. 2007)" (Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Point source continuum flux | 7.6 | 0.5 | mJy | 1 | The point source has a total flux of $\sim$7.6$\pm$0.5 mJy |
| Gaussian component flux | 42 | 3.7 | mJy | 1 | The Gaussian component has a total flux of $\sim$42$\pm$3.7 mJy |
| Protostellar mass | 1.6 | 0.5 | Msun | 2 | Protostellar Mass ($M_*$) / 1.6$\pm$0.5 $M_\ensuremath{\odot}$ |
| Inclination | 66 | 10 | deg | 2 | Inclination ($i$) / 66$\pm$10$\ensuremath{^\circ}$ |
| Systemic velocity | 7.3 | 0.1 | km/s | 2 | Systemic Velocity ($V_{\rm  sys}$) / 7.3$\pm$0.1 km s$^{-1}$ |
| Disk position angle | 68 | 18 | deg | 2 | Position Angle ($\psi$) / 68$\pm$18$\ensuremath{^\circ}$ |
| Disk mass from continuum | 0.003–0.007 | not stated | Msun | 3 | The mass of the Keplerian disk is then estimated to be $\sim$0.003–0.007 $M_\ensuremath{\odot}$ |
| SO ring radii | 250 to 390 | not stated | AU | 4 | the inner and outer radii of the SO ring are roughly estimated to be $r$ $\sim$ 250 and 390 AU |
| Infall mass | 4–7e-3 | not stated | Msun | 6 | the mass of the infalling flows is estimated to be 4–7 $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$ |
| Mass infalling rate | 4–7e-7 | not stated | Msun/yr | 6 | the mass infalling rate onto the Keplerian disk in L1489 IRS is estimated to be $\sim$4–7 $\times$ 10$^{-7}$ $M_\ensuremath{\odot}$ yr$^{-1}$ |
| Infall specific angular momentum | 2.6e-3 | not stated | km/s pc | 6 | $\sim$ 2.6 $\times$ 10$^{-3}$ km s$^{-1}$ pc$^{-1}$ with $R_{\rm c}$ of 300 AU |
| Keplerian disk specific angular momentum (Rd=700 AU) | 4.8e-3 | not stated | km/s pc | 6 | the specific angular momentum of the Keplerian disk is estimated to be 4.8 $\times$ 10$^{-3}$ km s$^{-1}$ pc$^{-1}$ |
| Infall trajectory angles | theta0=52, phi0=74 (blue); theta0=124, phi0=262 (red) | not stated | deg | 5 | parabolic trajectory of material infalling from $\theta_0$ = 52$\ensuremath{^\circ}$ and $\phi_0$ = 74$\ensuremath{^\circ}$ |

## Qualitative findings

- Off-axis C18O protrusions are distinct from the Keplerian disk and consistent with non-coplanar infalling flows  
  > "One possibility of the nature of the non-Keplerian protrusions is that they trace infalling flows onto the Keplerian disk." (Summary)
- SO traces a ring in the flared disk, possibly accretion-shock enhanced at the centrifugal radius  
  > "The local enhancement of the SO abundance in the ring region can be due to the accretion shocks at the centrifugal radius" (abstract)

## Claim tuples

- H: A Keplerian disk around L1489 IRS is traced by high-velocity CO/C18O | E: chi2 fit of thin disk model to C18O channel maps | R: M*=1.6 Msun, i=66 deg; disk radius up to ~700 AU | F: Keplerian disk with size and mass comparable to T Tauri disks | **supported**
- H: Off-axis C18O protrusions are infalling flows | E: Parabolic trajectory models with conserved angular momentum compared with moment maps and P-V | R: Infall model reproduces velocities better than coplanar Keplerian; rate ~5e-7 Msun/yr | F: Infalling flows feed the disk | **partially**
- H: SO emission arises from a ring in the flared disk | E: Ring model scaled from C18O flared disk model | R: Reproduces linear velocity gradient for 250-390 AU | F: SO enhanced at accretion shock near centrifugal radius | **partially**

## Reasoning

- Why this data: Higher resolution and sensitivity than SMA to resolve transition from infalling envelope to disk  
  > "providing an angular resolution four times better and sensitivity more than ten times better than those of the previous SMA observations" (Introduction)
- Why this method: _not stated_
- Alternative: Protrusions as outflow or optical depth effects or coplanar Keplerian rotation were disfavored  
  > "these protrusions are unlikely to be related with the outflow, because the direction of the velocity gradient of the protrusions" (Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Missing flux (~80% of C18O) hinders outer disk radius; p, q, T0, vturb poorly constrained  
  > "it is difficult to unambiguously constrain the outer radius of the Keplerian disk due to the effect of the missing flux ($\sim$80%; Hogerheijde et al. 1998)" (Analysis); "We found that $p$, $q$, $T_0$, and $v_{\rm turb}$ are not well constrained by our fitting." (Analysis)
- Caveat (inferred, ours): Infall interpretation rests on hand-tuned models without formal fit or alternative flow geometries
- Caveat (inferred, ours): Missing flux (~80%) and outflow contamination affect the medium/low-velocity C18O
- Caveat (inferred, ours): Rd fixed at 200 AU and thin-disk assumption bias mass; mass infall rate order-of-magnitude only
- Caveat (inferred, ours): SO ring is an interpretation of a P-V gradient; non-unique

## Reproducibility

- Data public (paper): Project code given in acknowledgments; Cycle 0 data; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00210.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Custom disk and infall model codes not released
- Missing: CLEAN parameters, line-free channels and CASA version
- Missing: Details of the chi2 grid and noise estimation
- Data volume (inferred): ~10-20 GB raw (single Cycle 0 execution, 4 spws x 3840 channels)
- Score (inferred): 3/5, Single public dataset and fairly detailed models with equations, but custom code unreleased and imaging details missing.
- Rediscovery candidate: no, Key results rely on custom hand-tuned models and unspecified imaging settings.

## Links

- Method: Ulrich 1976 (ref: 1976ApJ...210..377U) (Infall trajectory and velocity/density model)
- Method: Guilloteau & Dutrey 1998 (ref: 1998A&A...339..467G) (Scale-height and density relations for flared disk)
- Companion: Yen et al. 2013 (ref: 2013ApJ...772...22Y) (Previous SMA C18O observations of L1489 IRS)
- Companion: Brinch et al. 2007b (ref: 2007A&A...475..915B) (Previous SMA modeling of L1489 IRS disk and envelope)

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
  "facts": 83,
  "stated": 57,
  "rate": 0.687
 },
 "evidence_ok": true
}
```
