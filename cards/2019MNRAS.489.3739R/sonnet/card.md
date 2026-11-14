# The AGN fuelling/feedback cycle in nearby radio galaxies - II. Kinematics of the molecular gas

`2019MNRAS.489.3739R` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Ruffa, Ilaria | arXiv: 1908.09229 | DOI: 10.1093/mnras/stz2368

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What is the kinematics of the molecular gas in the CO(2-1) discs of six nearby LERGs, and does it indicate AGN fuelling, jet interaction, or external gas origin?  
  > "with the aim of better understanding the AGN fuelling/feedback cycle in these objects." (abstract)
- Target **IC 1531 (PKS 0007-325)**: coordinates _not stated_; z/distance z = 0.0256  
  > "| PKS 0007$-$325 | IC 1531           | 0.0256 |" (Table 1); distance from NED  
  > "| PKS 0007$-$325 | IC 1531           | 0.0256 |" (Table 1)
- Target **NGC 612 (PKS 0131-31)**: coordinates _not stated_; z/distance z = 0.0298  
  > "| PKS 0131$-$31  | NGC 612           | 0.0298 |" (Table 1); distance from NED  
  > "| PKS 0131$-$31  | NGC 612           | 0.0298 |" (Table 1)
- Target **NGC 3100 (PKS 0958-314)**: coordinates _not stated_; z/distance z = 0.0088  
  > "| PKS 0958$-$314 | NGC 3100          | 0.0088 |" (Table 1); distance from NED  
  > "| PKS 0958$-$314 | NGC 3100          | 0.0088 |" (Table 1)
- Target **NGC 3557 (PKS 1107-372)**: coordinates _not stated_; z/distance z = 0.0103  
  > "| PKS 1107$-$372 | NGC 3557$^{\ast}$ | 0.0103 |" (Table 1); distance from NED  
  > "| PKS 1107$-$372 | NGC 3557$^{\ast}$ | 0.0103 |" (Table 1)
- Target **IC 4296 (PKS 1333-33)**: coordinates _not stated_; z/distance z = 0.0125  
  > "| PKS 1333$-$33  | IC 4296           | 0.0125 |" (Table 1); distance from NED  
  > "| PKS 1333$-$33  | IC 4296           | 0.0125 |" (Table 1)
- Target **NGC 7075 (PKS 2128-388)**: coordinates _not stated_; z/distance z = 0.0185  
  > "| PKS 2128$-$388 | NGC 7075          | 0.0185 |" (Table 1); distance from NED  
  > "| PKS 2128$-$388 | NGC 7075          | 0.0185 |" (Table 1)

## Data provenance

- ALMA projects: 2015.1.01572.S
- bands: Band 6, CO(2-1) at about 230 GHz  
  > "The Band 6 archival data of NGC 3557 were taken in July 2016." (2.1 Archival ALMA Data)
- frequencies and spectral setup: 1920 1.129 MHz-wide channels (Cycle 3); archival 480 3.906 MHz-wide channels  
  > "using the high-resolution correlator configuration (1920 1.129 MHz-wide channels)" (2 ALMA observations); "is composed of 480 3.906 MHz-wide channels" (2.1 Archival ALMA Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: archival NGC 3557: 39 12-m antennas, max baseline 1.1 km  
  > "with a maximum baseline length of 1.1 km" (2.1 Archival ALMA Data)
- angular resolution: about 0.3 to 0.9 arcsec; combined NGC 3557 cube 0.44 arcsec  
  > "ranging from $\approx0.3$ to $\approx0.9$ arcsec" (2 ALMA observations)
- max recoverable scale: _not stated_
- sensitivity: 0.7 mJy for combined NGC 3557 cube; per-source rms in Table 1  
  > "The sensitivity (determined in line-free channels) is 0.7 mJy" (2.1 Archival ALMA Data)
- time on source: _not stated_
- observing dates: Cycle 3, March-July 2016; archival NGC 3557 July 2016  
  > "were taken during Cycle 3, between March and July 2016 (PI: I. Prandoni)" (2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380 GHz)
- Other facility **HST WFPC2**: F555W image of NGC 3557 used for MGE stellar mass model  
  > "we used the archival HST Wide-Field and Planetary Camera 2 (WFPC2) F555W image of NGC 3557" (4.5 NGC 3557)
- External data: Central stellar velocity dispersion of NGC 3557, 282 km/s  
  > "Assuming a central stellar velocity dispersion of $282$ km s$^{-1}$ (cite: Brough07)" (4.5 NGC 3557) [from (cite: Brough07)]
- External data: M_SMBH-sigma relation  
  > "derived from the $M_{\rm SMBH}$ – $\sigma_*$ relation of (cite: Tremaine02)" (4.5 NGC 3557) [from (cite: Tremaine02)]
- External data: Gas surface densities and kinematic PA starting values from Paper I  
  > "The gas surface densities ($\Sigma_{\rm gas}$) are derived from those reported in Paper I" (5.4 Gas disc stability) [from Paper I (Ruffa et al. 2019a)]

## Processing

### Calibration

- pipeline or manual: Manual calibration of archival data, same approach as Paper I  
  > "We calibrated the data manually, using the same approach as for the other observations (see Paper I for details)." (2.1 Archival ALMA Data)
- casa version: CASA 4.7.2  
  > "package, version 4.7.2" (2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan and Pallas; bright quasars if no solar-system object  
  > "Titan and Pallas were used as primary flux calibrators" (2 ALMA observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean; concat to combine NGC 3557 datasets  
  > "The archival data were then combined with our observations, using the casa task `concat`." (2.1 Archival ALMA Data)
- deconvolver: _not stated_
- weighting robust: natural weighting (Cycle 3 cubes); Briggs robust=0.5 for combined NGC 3557  
  > "using the `clean` task with natural weighting" (2 ALMA observations); "*Briggs* weighting (robust$=0.5$)" (2.1 Archival ALMA Data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Masked moments: Gaussian spatial smoothing (beam FWHM) and Hanning in velocity; threshold 1.2-2 sigma  
  > "We used thresholds varying from 1.2 to 2$\sigma$, depending on the significance of the CO detection" (2.2 Data products)
- final beam: 0.44 arcsec for combined NGC 3557; others in Table 1  
  > "the achieved angular resolution is 0.44$"$" (2.1 Archival ALMA Data)
- final rms: _not stated_

### Inherited from earlier work

- Full observation and data reduction details, clean parameters  
  > "Full details of our ALMA observations and data reduction can be found in Paper I; a brief summary is presented here." (2 ALMA observations) [from Paper I (cite: Ruffa19a)]
- Masked moment technique  
  > "using the masked moment technique as described by (cite: Dame11)" (2.2 Data products) [from (cite: Dame11)]
- Chi-square error rescaling by (2N)^0.25  
  > "As in (cite: Smith19), we re-scale the uncertainty in the cube by a factor of $(2N)^{0.25}$" (3.2 Fitting process) [from (cite: Smith19)]
- SMBH mass modelling approach with MGE circular velocity  
  > "we model the gas velocity by using the approach adopted by (cite: Onishi17) and (cite: Davis17)." (4.5 NGC 3557) [from (cite: Onishi17); (cite: Davis17)]

### Not stated but needed to reproduce (our reading)

- Cycle 3 clean parameters (robust, cell size, image size, masks, continuum-fit channels) deferred to Paper I
- Exact MCMC burn-in length and initial guesses
- Mass-to-light prior and MGE fitting details/PSF for NGC 3557
- Spiral model parameter values for NGC 3100
- Kinemetry settings
- Archival project code is printed as 2015.1.00878.7 (likely a typo)

## Analysis recipe

1. **Combine and image CO cubes**: Calibrate, concat NGC 3557 Cycle 3 + archival data, clean continuum-subtracted cubes, make masked moment maps and PVDs  
  > "A continuum-subtracted CO data cube of the combined dataset was then produced using the `clean` task" (2.1 Archival ALMA Data)
   - software: CASA
   - parameter: channel widths 10-40 km/s; 22 km/s for combined NGC 3557  
  > "The final channel widths range from 10 to 40 km s$^{-1}$" (2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Forward-model CO kinematics**: KinMS forward model with Gaussian surface brightness and arctan rotation curve, thin axisymmetric disc, constant sigma_gas; fit with KinMS_MCMC  
  > "The CO disc is assumed to be thin and the model axisymmetric." (3.1 Gas distribution and kinematics)
   - software: KinMS, KinMS_MCMC
   - parameter: Priors: velocity offset ±5 channel widths; PA ±20 deg around Paper I; inclination ±20 deg after first chain; v_flat ±40 km/s and r_turn within two beam widths of PVD estimates  
  > "The kinematic PA is allowed to vary by $\pm$20 degrees around the values estimated in Paper I (Table 7)." (3.2 Fitting process)
   - assumption: Purely circular motion initially  
  > "As a first step, we always assume that the gas is in purely circular motion" (3.1 Gas distribution and kinematics)
   - fitting: Gibbs sampling with adaptive stepping; log-likelihood -chi2/2; extra 1e5 steps after convergence; median and 68/99% CL  
  > "which utilises Gibbs sampling and adaptive stepping to explore the parameter space" (3.2 Fitting process)
   - validation: Residual moment-1 maps and PVD overlays; reduced chi-squared  
  > "The lower panels of Figures [5](#fig:IC1531) $-$ [20](#fig:NGC7075) show the data-model residual moment 1 map (panel c)" (4 Individual sources)
3. **Measure SMBH mass in NGC 3557**: MGE stellar mass model from HST F555W (dust masked) gives circular velocity; SMBH as point mass in KinMS; fit M/L and M_SMBH  
  > "The circular velocity curve arising from this mass model is then used to model the CO velocity curve in KINMS, with the SMBH treated as point mass." (4.5 NGC 3557)
   - software: MGE_FIT_SECTORS, KinMS
   - assumption: Constant M/L  
  > "assuming a constant mass-to-light ratio ($M/L$)" (4.5 NGC 3557)
   - fitting: _not stated_
   - validation: Compared with M-sigma expectation log M=8.82  
  > "consistent with the expectation from the $M_{\rm SMBH}$ – $\sigma_*$ relation" (4.5 NGC 3557)
4. **Model NGC 3100 spiral, warps and non-circular motions**: Exponential disc with hole plus two-arm logarithmic spiral, PA and inclination warps; KINEMETRY harmonic decomposition of velocity field  
  > "we use the KINEMETRY package (cite: Kraj06)" (4.6.1 Non-circular motions)
   - software: KinMS_MCMC, KINEMETRY
   - fitting: _not stated_
   - validation: chi2_red = 1.3; k5/k1 ratio  
  > "best-fit ($\chi^{2}_{\rm red}=1.3$) model parameters" (4.6 NGC 3100)
5. **Estimate Toomre Q and relaxation times**: Q = sigma kappa/(pi G Sigma); t_relax ≈ 5 t_dyn  
  > "We therefore assume $$\begin{eqnarray}
t_{\rm relax} \approx 5 \times t_{\rm dyn} = 5 \times \dfrac{2\pi R}{v_{\rm circ}}" (5.3.3 Relaxation timescales)
   - assumption: Eccentricity 0.2; sigma_gas from fit, alternate 8 km/s  
  > "assuming a canonical value of $\sigma_{\rm gas}=8$ km s$^{-1}$" (5.4 Gas disc stability)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: calibration, concat, clean  
  > "package, version 4.7.2" (2 ALMA observations)
- **KinMS** : forward-modelling kinematics  
  > "using the publicly available KINEMATIC MOLECULAR SIMULATION tool (cite: Davis13)" (3 Kinematic modelling)
- **KinMS_MCMC** : MCMC fitting  
  > "coupled with the Markov Chain Monte Carlo (MCMC) code (KINMS_MCMC[^3])" (3 Kinematic modelling)
- **MGE_FIT_SECTORS** : MGE of NGC 3557 light  
  > "adopted in the MGE_FIT_SECTORS package of (cite: Cappellari02)" (4.5 NGC 3557)
- **KINEMETRY** : harmonic decomposition of NGC 3100 velocity field  
  > "we use the KINEMETRY package (cite: Kraj06)" (4.6.1 Non-circular motions)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| M_SMBH NGC 3557 | 7.10e8 | ±0.02e8 | Msun | 3 | We find a best fit $M_{\rm SMBH}=(7.10\pm0.02)\times10^{8}$ M$_{\odot}$ |
| Stellar M/L NGC 3557 | 5.4 | ±0.1 | Msun/Lsun | 3 | Stellar $M/L$     / ($M_{\odot}/L_{\odot}$) /    5.4$\pm$0.1 |
| NGC 612 central hole radius | 0.3 | not stated | arcsec | 2 | is found to be $\approx0.3$ arcsec (180 pc |
| NGC 3100 v_flat | 354 | ±0.01 | km/s | 4 | v$_{\rm flat}$                  / (km s$^{-1}$) / 354$\pm$0.01 |
| NGC 3100 radial motions | 10% of circular velocity at peak | not stated | dimensionless | 4 | radial motions are not negligible (10% of the circular velocity at the peak) |
| t_relax NGC 612 | 5.2e8 | not stated | yr | 5 | estimating $t_{\rm relax}\simeq5.2\times10^{8}$ yr |
| t_relax NGC 3100 | 9.5e7 | not stated | yr | 5 | $t_{\rm relax} \simeq 9.5\times10^{7}$ yr |
| Toomre <Q> NGC 612 | 0.1 | not stated | dimensionless | 5 | / NGC 612  /    1.6$\times10^{3}$    /      303       /  0.1  / |

## Qualitative findings

- All six CO discs are mostly in ordered rotation but show low-level distortions, so not fully relaxed.  
  > "low-level distortions are ubiquitous, indicating that the molecular gas is not fully relaxed into the host galaxy potential." (abstract)

## Claim tuples

- H: Is the molecular gas in LERG discs relaxed and in ordered rotation? | E: 3D forward modelling of six CO(2-1) cubes with KinMS_MCMC | R: Simple axisymmetric models fit well but all show residuals | F: Bulk ordered rotation with ubiquitous low-level distortions | **supported**
- H: Can the SMBH mass of NGC 3557 be measured from the CO Keplerian upturn? | E: MGE + KinMS fit of combined cube | R: M_SMBH=(7.10±0.02)e8 Msun | F: Consistent with M-sigma, but not definitive due to asymmetric residuals | **partially**
- H: Does NGC 3100 gas show inflow that fuels the AGN? | E: Spiral+warp model and kinemetry | R: Radial motions ~10% of rotation, likely inward | F: Cold gas likely contributes to AGN fuelling | **partially**
- H: Is the gas in NGC 612 and NGC 3100 of external origin? | E: Misalignment, warps, relaxation times, dust co-spatiality | R: t_relax 5.2e8 and 9.5e7 yr | F: External origin strongly favoured | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Forward modelling accounts for beam smearing and marginal resolution  
  > "taking into account the observational effects of disc thickness, beam smearing, gas velocity dispersion, etc." (3 Kinematic modelling)
- Alternative: Stellar bar and jet-driven shocks rejected as origin of NGC 3100 spiral in favour of external accretion  
  > "We then favour external gas accretion as the mechanism giving rise to the spiral feature" (5.2 NGC 3100)
- How they decided it was enough: _not stated_
- Limitation (authors): Most discs only marginally resolved, preventing strong conclusions  
  > "The majority of the discs, however, are only marginally resolved, preventing us from drawing strong conclusions." (abstract)
- Caveat (inferred, ours): Quoted parameter uncertainties are tiny (random only) and likely underestimated
- Caveat (inferred, ours): SMBH mass ignores dust-affected F555W MGE and M/L degeneracy
- Caveat (inferred, ours): Warp vs non-circular motion degenerate at low resolution

## Reproducibility

- Data public (paper): Archival NGC 3557 data stated public; Cycle 3 data via ALMA project  
  > "are now publicly available in the ALMA archive" (2.1 Archival ALMA Data)
- Products in archive: _not stated_
- Code: KinMS_MCMC on GitHub  
  > "https://github.com/TimothyADavis/KinMS_MCMC" (footnote 3)
- Missing: Clean parameters from Paper I
- Missing: MGE fitting details
- Missing: Final cubes not released
- Data volume (inferred): ~50-100 GB raw for two projects
- Score (inferred): 5/5, Public data and public code, but imaging details are deferred to Paper I and several fit settings are missing.
- Rediscovery candidate: no, Processing recipe is deferred to Paper I and results depend on unspecified modelling choices.

## Links

- Method: (cite: Davis13) (KinMS)
- Method: (cite: Kraj06) (KINEMETRY)
- Companion: Paper I (cite: Ruffa19a) (ALMA observations, data reduction, sample)
- Related: ATLAS3D

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2015.1.00878.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 95,
  "stated": 59,
  "rate": 0.621
 },
 "evidence_ok": true
}
```
