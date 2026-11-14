# No Keplerian Disk &gt;10 AU Around the Protostar B335: Magnetic Braking or Young Age?

`2015ApJ...812..129Y` | The Astrophysical Journal 2015 | first author: Yen, Hsi-Wei | arXiv: 1509.04675 | DOI: 10.1088/0004-637X/812/2/129

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Does the Class 0 protostar B335 host a Keplerian disk larger than 10 AU, and is the small disk due to magnetic braking or young age?  
  > "there are two possible scenarios to explain the presence of such a small Keplerian disk in B335: magnetic braking and young age." (abstract)
- Target **B335**: coordinates 19h37m00.89s, +07d34m10.0s (J2000, pointing center)  
  > "B335 is an isolated Bok globule associated with an infrared source (IRAS 19347+0727) having a bolometric luminosity of 1.5 $L_{\ensuremath{\odot}}$ at a distance$\footnotemark$ of 150 pc (Keene et al. 1980, 1983; Stutz et al. 2008)." (1 Introduction); "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}10.0\ensuremath{''}$." (2 Observations); z/distance 150 pc  
  > "B335 is an isolated Bok globule associated with an infrared source (IRAS 19347+0727) having a bolometric luminosity of 1.5 $L_{\ensuremath{\odot}}$ at a distance$\footnotemark$ of 150 pc (Keene et al. 1980, 1983; Stutz et al. 2008)." (1 Introduction); "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}10.0\ensuremath{''}$." (2 Observations); distance from Keene et al. 1980, 1983; Stutz et al. 2008  
  > "B335 is an isolated Bok globule associated with an infrared source (IRAS 19347+0727) having a bolometric luminosity of 1.5 $L_{\ensuremath{\odot}}$ at a distance$\footnotemark$ of 150 pc (Keene et al. 1980, 1983; Stutz et al. 2008)." (1 Introduction); "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}10.0\ensuremath{''}$." (2 Observations)

## Data provenance

- ALMA projects: 2013.1.00879.S
- bands: Band 6 (1.3 mm), cycle 2  
  > "The ALMA Band 6 observations of B335 were made with 34 antennas during the cycle-2 observing period on September 2, 2014." (2 Observations)
- frequencies and spectral setup: Two 234 MHz windows for C18O (2-1) and SO, 3840 channels, 61 kHz channel width  
  > "Two spectral windows, each with a bandwidth of 234 MHz, were assigned to the C$^{18}$O (2–1) and SO (5$_6$–4$_5$) lines with 3840 spectral channels in each window, resulting in a channel width of 61 kHz." (2 Observations)
- continuum bandwidth: total 4 GHz in two spectral windows  
  > "Two spectral windows with of a total bandwidth of 4 GHz were assigned to the 1.3 mm continuum." (2 Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: ~25 kλ to ~800 kλ  
  > "The projected $uv$ distances range from $\sim$25 k$\lambda$ to $\sim$800 k$\lambda$." (2 Observations)
- angular resolution: ~0.3'' (synthesized beams 0.19''-0.37'')  
  > "Robust ($r$ = 0.5) | 0.34$''$ $\times$ 0.28$''$ (55$^\circ$) | 3.8$^{a}$ | 0.17" (Table 1)
- max recoverable scale: ~3.5'' (~525 AU) at 50% level  
  > "Our observations are insensitive to structures larger than $\sim$3.5$''$ ($\sim$525 AU) at a 50% level (Wilner & Welch 1994)." (2 Observations)
- sensitivity: _not stated_
- time on source: ~25 minutes  
  > "The on-source integration time on B335 was $\sim$25 minutes." (2 Observations)
- observing dates: 2014 September 2  
  > "during the cycle-2 observing period on September 2, 2014." (2 Observations)
- pi or archival as stated: _not stated_
- Line: C18O 2-1 (219.560358 GHz)
- Line: SO 5_6-4_5 (219.949433 GHz)
- External data: Systemic velocity V_LSR = 8.34 km/s from single-dish C18O (2-1)  
  > "The systemic velocity of B335 was previously estimated to be $V_{\rm LSR} = 8.34$ km s$^{-1}$ from the single-dish spectrum of the C$^{18}$O (2–1) emission" (3 Results) [from Yen et al. 2011]
- External data: Inclination of 80 deg from plane of sky  
  > "The inclination angle, i.e., the angle between the plane of the sky and the envelope equator, is adopted to be 80$\ensuremath{^\circ}$ (Hirano et al. 1988)." (4.1.2) [from Hirano et al. 1988]
- External data: C18O abundance 3.7e-7  
  > "a constant C$^{18}$O abundance of 3.7 $\times$ 10$^{-7}$ (Frerking et al. 1982)" (4.1.2) [from Frerking et al. 1982]

## Processing

### Calibration

- pipeline or manual: Standard cycle-2 reduction script in CASA  
  > "Calibration of the raw visibility data was performed with the standard reduction script for the cycle-2 data, which uses tasks in Common Astronomy Software Applications (CASA)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1751+096, 2.53 Jy at 233 GHz from other observations, extrapolated  
  > "The absolute flux of J1751+096 was measured to be 2.53 Jy at a frequency of 233 GHz in other observations." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: none  
  > "and without self calibration." (2 Observations)

### Imaging

- task: CASA clean  
  > "CLEANed with the CASA task “clean” at a velocity resolution of 0.17 km s$^{-1}$." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust +0.5 for lines; natural, uniform and >500 kλ uniform for continuum  
  > "Fourier-transformed with the Briggs robust parameter of +0.5" (2 Observations); "three different weightings (natural, uniform, and long baseline only with $uv> 500$ k$\lambda$)" (2 Observations)
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
- final beam: Continuum 0.37x0.32 (natural), 0.25x0.22 (uniform), 0.19x0.15 (>500 kλ); lines 0.34x0.28  
  > "| Continuum | Natural | 0.37$''$ $\times$ 0.32$''$ (56$^\circ$) | 0.24 |" (Table 1)
- final rms: Continuum 0.24/0.26/0.41 mJy/beam; C18O 3.8 and SO 4.8 mJy/beam per channel  
  > "| SO (5$_6$–4$_5$) | Robust ($r$ = 0.5) | 0.34$''$ $\times$ 0.28$''$ (54$^\circ$) | 4.8$^{a}$ | 0.17 |" (Table 1)

### Inherited from earlier work

- Dust opacity law kappa=0.1(0.3mm/λ)^β cm2/g, β=1.3  
  > "the mass opacity at 1.3 mm is 0.014 cm$^{2}$ g$^{-1}$ with $\beta = 1.3$ (Chandler & Sargent 1993)" (3.1) [from Beckwith et al. 1990; Chandler & Sargent 1993]
- Dust temperature of 30 K at ~600 AU and power-law index -0.4  
  > "$T_{\rm dust}$ on a scale of $\sim$600 AU in B335 has been estimated to be $\sim$30 K (Chandler & Sargent 1993)." (3.1) [from Chandler & Sargent 1993; Shirley et al. 2000]
- Density index p = -1.5 and -2, temperature index q = -0.4 in models  
  > "$q$ is adopted to be $-0.4$ (Shirley et al. 2000, 2002)." (4.1.2) [from Shirley et al. 2000, 2002; Harvey et al. 2003a,b; Doty et al. 2010]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- clean threshold, masks, cell and image size, number of iterations
- line-free channels and continuum subtraction method for the line cubes
- primary-beam correction details
- exact moment 0/1 velocity ranges and PV slice widths
- chi2 definition and noise used in model fitting
- model grid details of the CASA simulator setup
- how the H2 column density and sigma = 2e22 cm-2 were derived

## Analysis recipe

1. **Fit continuum components in uv plane**: Two Gaussians fitted to 1.3 mm visibilities (extended + compact)  
  > "we fit two Gaussians to the 1.3 mm continuum in the $uv$ plane to derive the basic parameters of these two components." (3.1)
   - fitting: _not stated_
   - validation: Compared visibility amplitudes with the two Gaussians (Fig. 1a)  
  > "A comparison between the observed visibility amplitudes and the two Gaussian components is shown in Figure [1](#con)a." (3.1)
2. **Estimate continuum masses**: M = F d^2 / (kappa B(T_dust)), T_dust 30-100 K  
  > "Therefore, here $M_{\rm 1.3mm}$ of the compact and unresolved components is estimated with $T_{\rm dust}$ of 30–100 K." (3.1)
   - assumption: kappa_1.3mm = 0.014 cm2/g, gas-to-dust 100, d = 150 pc  
  > "the mass opacity at 1.3 mm is 0.014 cm$^{2}$ g$^{-1}$ with $\beta = 1.3$ (Chandler & Sargent 1993) and a gas-to-dust mass ratio of 100." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure sizes and velocity gradients in line moment maps and PV diagrams**: 2D Gaussian fits to moment 0 maps; Gaussian peak positions per channel in PV diagrams, linear V∝r fit with 1000 Monte Carlo iterations perturbing PA, center and systemic velocity  
  > "We repeat this fitting process for a 1000 times, where each time the position angle and the center of the P–V diagram, and the systemic velocity are randomly changed within their 1$\sigma$ uncertainties" (4.1.1)
   - software: IDL gaussfit, MPFIT
   - parameter: Only channels with peaks >5σ and ΔV>1.2 km/s  
  > "Only channels with emission peaks above 5$\sigma$ are included." (4.1.1)
   - fitting: Linear fit by MPFIT; moments 1 and 2 of the distribution give value and uncertainty  
  > "The moment 1 and 2 of the probability distribution are adopted as the estimated magnitude and its uncertainty, respectively." (4.1.1)
   - validation: 1000 iterations stated sufficient to converge  
  > "The 1000 iterations are sufficient to stably converge." (4.1.1)
4. **Fit kinematic infall+rotation envelope models to C18O PV diagrams**: Power-law density/temperature envelope with free fall and constant j, LTE radiative transfer, processed with CASA simulator, chi2 grid fit of PV diagrams  
  > "The model images are processed with the CASA simulator to mimic our observational $uv$ coverage." (4.1.2); "we perform $\chi^2$ fitting of the model P–V diagrams to the observed ones." (4.1.2)
   - software: CASA simulator
   - parameter: Free parameters M*, j, n0, T0; p = -1.5 or -2, q = -0.4; outer radius 3'' (450 AU); cavity of 60 deg  
  > "Our models have four free parameters: $M_*$, $j$, $n_0$, and $T_0$." (4.1.2)
   - parameter: Grid: M* 0.03-0.07 Msun step 0.01; j 0-5e-5 step 1e-5; n0 5e6-4e7 factors of two; T0 20-60 K step 10 K  
  > "$M_*$ from 0.03 $M_\ensuremath{\odot}$ to 0.07 $M_\ensuremath{\odot}$ in steps of 0.01 $M_\ensuremath{\odot}$" (4.1.2)
   - assumption: Inclination 80 deg, LTE, C18O abundance 3.7e-7, free-fall infall  
  > "on the assumption of the LTE condition and a constant C$^{18}$O abundance of 3.7 $\times$ 10$^{-7}$ (Frerking et al. 1982)" (4.1.2)
   - fitting: chi2 grid search  
  > "Then, P–V diagrams are generated along the minor and major axes from the simulated model images, and we perform $\chi^2$ fitting of the model P–V diagrams to the observed ones." (Gas Kinematics, Kinematic Model Fitting of Observed P–V Diagrams)
   - validation: Compared with fixed M*=0.1 and 0.02 Msun models, which fail; refit high-velocity channels only for j  
  > "our ALMA observations cannot be well explained by the model with $M_*=0.1$ $M_\ensuremath{\odot}$" (4.1.2)
5. **Estimate SO rotation and expected Keplerian disk radius**: Rotational velocity = characteristic radius x velocity gradient, inclination-corrected; j; Keplerian radius j^2/GM*  
  > "The rotational velocity is then estimated from the characteristic radius $\times$ the velocity gradient." (4.2)
   - assumption: M* = 0.05 Msun, constant j within 10 AU  
  > "the expected radius of the Keplerian disk around B335, $j^2/GM_*$, is derived to be 1–3 AU" (4.2)
   - fitting: _not stated_
   - validation: Compared PV and moment 0 estimates  
  > "Thus, the specific angular momenta estimated from the P–V diagram along the major axis and from the moment 0 map of the high-velocity components are comparable." (4.2)
6. **Estimate magnetic field strength and collapse timescale for two scenarios**: Steady-state magnetic braking relation with Bz~Bphi, Δr~1000 AU; collapse time from infall radius 2700 AU and sound speed 0.23 km/s  
  > "The resulting magnetic field strength for magnetic braking in B335 is then estimated to be $\sim$200 $\mu$G." (5.2)
   - assumption: Krasnopolsky & Königl 2002 formula; sound speed 0.23 km/s  
  > "In this scenario, the time scale of the collapse in B335 is $\sim$5.3 $\times$ 10$^4$ yr, assuming a sound speed of 0.23 km s$^{-1}$ (e.g., Zhou et al. 1993)." (Hints of Young Age?)
   - fitting: _not stated_
   - validation: Compared collapse time with outflow dynamical and accretion timescales  
  > "all these time scales appear consistent with each other." (5.3)

## Software

- **CASA** : Calibration, clean imaging, and simulator for model visibilities  
  > "CLEANed with the CASA task “clean” at a velocity resolution of 0.17 km s$^{-1}$." (2 Observations)
- **IDL gaussfit** : Gaussian fits of PV intensity profiles  
  > "The peak positions are derived by fitting Gaussians to the intensity profiles in these channels using the IDL routine *gaussfit*." (4.1.1)
- **MPFIT** : Linear fit minimization of velocity gradient  
  > "The minimization of the fitting is done by using the IDL routine *MPFIT* (Markwardt 2009)." (4.1.1)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Compact continuum component flux | 25.3 | 0.3 | mJy | 1 | 25.3$\pm$0.3 mJy, 0.24$''$$\pm$0.01$''$ $\times$ 0.13$''$$\pm$0.01$''$ |
| Extended continuum component flux | 62.2 | 2.8 | mJy | 1 | 62.2$\pm$2.8 mJy, 3.34$''$$\pm$0.13$''$ $\times$ 1.41$''$$\pm$0.06$''$ |
| Unresolved continuum flux | 13.2 | 0.6 | mJy | 1 | The flux of this unresolved component is estimated to be $\sim$13.2$\pm$0.6 mJy. |
| Compact continuum mass | (1.3-5.4)e-3 | not stated | Msun | 2 | $M_{\rm 1.3mm}$ of the compact component is $\sim$(1.3–5.4) $\times$ 10$^{-3}$ $M_\ensuremath{\odot}$ |
| C18O velocity gradient perpendicular to outflow | 0.27 | 0.03 | km/s/AU | 3 | is estimated to be 0.27$\pm$0.03 km s$^{-1}$ AU$^{-1}$. |
| SO major-axis velocity gradient | 0.51 | 0.11 | km/s/AU | 3 | is measured to be 0.51$\pm$0.11 km s$^{-1}$ AU$^{-1}$. |
| Protostellar mass | 0.05 | not stated | Msun | 4 | The final best-fit parameters are $M_*=0.05$ $M_\ensuremath{\odot}$, $j$ = 2 $\times$ 10$^{-5}$ km s$^{-1}$ pc |
| Specific angular momentum at 100 AU (C18O) | 4.3e-5 | 0.5e-5 | km/s pc | 4 | The specific angular momentum, on a 100 AU scale, is (4.3$\pm$0.5) $\times$ 10$^{-5}$ km s$^{-1}$ pc. |
| SO rotational velocity at 4.7 AU | 2.7 | 0.5 | km/s | 5 | The rotational velocity at a radius of 4.7$\pm$0.3 AU is estimated to be 2.7$\pm$0.5 km s$^{-1}$. |
| Expected Keplerian disk radius | 1-3 | not stated | AU | 5 | is derived to be 1–3 AU |
| Magnetic field strength | ~200 | not stated | microgauss | 6 | The resulting magnetic field strength for magnetic braking in B335 is then estimated to be $\sim$200 $\mu$G. |
| Collapse time (young age scenario) | ~5.3e4 | not stated | yr | 6 | the time scale of the collapse in B335 is $\sim$5.3 $\times$ 10$^4$ yr |

## Qualitative findings

- Continuum, C18O and SO all show central compact components elongated perpendicular to the outflow, tracing a flattened envelope  
  > "These central components are elongated perpendicularly to the outflow axis and most likely trace the inner flattened envelope." (6 Summary)

## Claim tuples

- H: Is there a Keplerian disk >10 AU in B335? | E: Kinematic modelling of C18O and velocity gradient of SO | R: SO rotation velocity below Keplerian for 0.05 Msun; expected disk radius 1-3 AU | F: No Keplerian disk >10 AU | **supported**
- H: Protostellar mass inferred from small-scale infall | E: C18O PV model fitting | R: M* = 0.05 Msun; 0.1 Msun fails | F: Mass is lower than single-dish estimates | **supported**
- H: Magnetic braking or young age explains small disk | E: Compare j and M* with inside-out collapse expectations | R: j is a factor 2-3 lower than expected for 4000 AU infall radius; consistent if radius 2700 AU | F: Both scenarios remain viable | **partially**

## Reasoning

- Why this data: B335 shows no rotation at 1000 AU; C18O traces envelope kinematics and SO the transition region  
  > "Therefore, the SO line can potentially be used to study the transitional region from infalling to dominating rotational motion." (1 Introduction)
- Why this method: _not stated_
- Alternative: Geometrically thin model with 30 deg cavity fit worse than 60 deg cavity  
  > "We find that the model with the zero density within 60$\ensuremath{^\circ}$ from the polar axis fits the observational results better." (4.1.2 footnote)
- How they decided it was enough: _not stated_
- Limitation (authors): Significant missing flux in the outer envelope; M* is a lower limit if infall slower than free fall  
  > "Due to this significant amount of missing flux, the complete velocity structures of the outer emission remain uncertain." (4.1.1)
- Caveat (inferred, ours): No formal parameter uncertainties from the coarse chi2 grid
- Caveat (inferred, ours): SO is not modelled; rotation from linear gradients with unresolved structure
- Caveat (inferred, ours): Magnetic field estimate uses order-of-magnitude assumptions
- Caveat (inferred, ours): Distance and inclination are assumed

## Reproducibility

- Data public (paper): ALMA project 2013.1.00879.S acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00879.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Model code for kinematic envelope not released
- Missing: clean parameters and masks
- Missing: CASA version
- Data volume (inferred): ~10-30 GB for one execution block
- Score (inferred): 3/5, Public data and a fairly clear recipe, but model code and many imaging parameters are missing.
- Rediscovery candidate: no, Key results depend on a custom kinematic model without code and unstated settings.

## Links

- Method: Yen et al. 2014 (cite) (Radiative transfer model approach for kinematic modelling)
- Companion: Yen et al. 2010, 2015 (Previous SMA kinematics of B335)

## Checks

```json
{
 "quotes": 77,
 "quotes_ok": 77,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 53,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
