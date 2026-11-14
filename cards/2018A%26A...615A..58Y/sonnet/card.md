# Constraint on ion-neutral drift velocity in the Class 0 protostar B335 from ALMA observations

`2018A&A...615A..58Y` | Astronomy and Astrophysics 2018 | first author: Yen, Hsi-Wei | arXiv: 1803.09893 | DOI: 10.1051/0004-6361/201732195

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: Is there a measurable velocity drift between ionized (H13CO+) and neutral (C18O) gas at 100 au in the Class 0 protostar B335, as expected from ambipolar diffusion?  
  > "we compare here gas kinematics traced by ionized and neutral molecular lines and discuss the implication on ambipolar diffusion." (abstract)
- Target **B335**: coordinates 19h37m00.89s, +7d34m09.6s (J2000)  
  > "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}9.6\ensuremath{''}$." (2 Observations); "We adopt the latest estimates of the distance of 100 pc (cite: Olofsson09) and an inclination angle of 87$\ensuremath{^\circ}$ (cite: Stutz08)" (4 Kinematical models); z/distance 100 pc  
  > "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}9.6\ensuremath{''}$." (2 Observations); "We adopt the latest estimates of the distance of 100 pc (cite: Olofsson09) and an inclination angle of 87$\ensuremath{^\circ}$ (cite: Stutz08)" (4 Kinematical models); distance from Olofsson & Olofsson 2009  
  > "The pointing center was $\alpha$(J2000) = $19^{h}37^{m}00.89s$, $\delta$(J2000) = $7\ensuremath{^\circ}34\ensuremath{'}9.6\ensuremath{''}$." (2 Observations); "We adopt the latest estimates of the distance of 100 pc (cite: Olofsson09) and an inclination angle of 87$\ensuremath{^\circ}$ (cite: Stutz08)" (4 Kinematical models)

## Data provenance

- ALMA projects: 2013.1.00879.S, 2015.1.01188.S
- bands: _not stated_
- frequencies and spectral setup: 117.2 MHz window, 960 channels, 122.1 kHz channel width; 1.2 mm continuum 2 GHz total  
  > "a spectral window with a bandwidth of 117.2 MHz was assigned to the H$^{13}$CO$^+$ emission with 960 channels, resulting in a channel width of 122.1 kHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: 40 antennas, cycle 3  
  > "obtained with the ALMA observations with 40 antennas during the cycle-3 observing period on May 23 and June 3, 2016." (2 Observations)
- configurations: C36-4 (H13CO+); C34-6 for C18O  
  > "The array configuration was C36-4 with the shortest baseline length of $\sim$15 m ($\sim$13 k$\lambda$)." (2 Observations)
- baselines: _not stated_
- angular resolution: 0.5" x 0.4", PA 111 deg  
  > "The achieved synthesized beam is 0.5$''$ $\times$ 0.4$''$ with a position angle (PA) of 111$^\circ$" (2 Observations)
- max recoverable scale: 7" at 50% level  
  > "our H$^{13}$CO$^+$ observations have a largest recoverable angular scale of 7$\ensuremath{''}$ at a 50% level" (2 Observations)
- sensitivity: 3.3 mJy/beam per channel  
  > "The achieved rms noise is 3.3 mJy beam$^{-1}$ per channel" (2 Observations)
- time on source: ~80 minutes  
  > "The on-source integration time on B335 was $\sim$80 minutes." (2 Observations)
- observing dates: May 23 and June 3, 2016  
  > "during the cycle-3 observing period on May 23 and June 3, 2016." (2 Observations)
- pi or archival as stated: _not stated_
- Line: H13CO+ 3-2 (260.255342 GHz)
- Line: C18O 2-1 (not stated)
- External data: C18O (2–1) ALMA data and results (images, PV diagrams, flattened envelope PA 16 deg, rotation j)  
  > "This velocity resolution is the same as that in the C$^{18}$O image obtained from (cite: Yen15b)." (2 Observations) [from (cite: Yen15b)]
- External data: Temperature 38 K at 100 au and power-law index -0.4  
  > "The power-law index of the temperature profile is adopted to be $-0.4$ (cite: Shirley00; Shirley11), and the temperature is adopted to be 38 K at a radius of 100 au (cite: Evans15)." (4 Kinematical models) [from (cite: Shirley00; Shirley11; Evans15)]

## Processing

### Calibration

- pipeline or manual: Standard cycle-3 reduction script  
  > "Calibration of the raw visibility data was performed with the standard reduction script for the cycle-3 data" (2 Observations)
- casa version: CASA 4.5.3  
  > "Common Astronomy Software Applications (cite: McMullin07) of version 4.5.3." (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2148+0657 (bandpass and flux)  
  > "J2148+0657 was observed as a bandpass and flux calibrator." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean  
  > "CLEANed with the CASA task “clean” at a velocity resolution of 0.17 km s$^{-1}$." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0  
  > "generated with the Briggs robust parameter of 0 from the calibrated visibility data" (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Both lines convolved to 0.5" circular beam for spectra comparison  
  > "both data were first convolved with the same circular beam with a size of 0$\ensuremath{''}$5" (3 Results)
- final beam: 0.5" x 0.4", PA 111 deg  
  > "The achieved synthesized beam is 0.5$''$ $\times$ 0.4$''$ with a position angle (PA) of 111$^\circ$" (2 Observations)
- final rms: 3.3 mJy/beam per channel  
  > "The achieved rms noise is 3.3 mJy beam$^{-1}$ per channel" (2 Observations)

### Inherited from earlier work

- C18O data, imaging parameters for synthetic images and 1.3 mm continuum envelope geometry  
  > "We generated synthetic images from the simulated visibility data with the same imaging parameters as (cite: Yen15b)" (4 Kinematical models) [from (cite: Yen15b)]
- Envelope thickness h(r)=r sin30 deg  
  > "meaning that the thickness of the model envelope $h(r) = r \sin 30\ensuremath{^\circ}$, identical to (cite: Yen15b)." (4 Kinematical models) [from (cite: Yen15b)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters of the model synthetic images (cell, image size, masks, clean threshold) are only given by reference to Yen15b
- Software used for 3D model radiative transfer and PV extraction is not named
- Continuum subtraction and line-free channels not stated
- Free-parameter grid and ranges for chi2 fitting not given
- Which fraction of the data range along PV axes is fitted and the noise used for chi2

## Analysis recipe

1. **Make moment maps, spectra and PV diagrams**: Moment 0/1 maps, spectra at protostar after convolution to 0.5" beam, PV cuts along major (PA 16 deg) and minor axes  
  > "Figure 4 presents the position–velocity (PV) diagrams along the major and minor axes of the flattened envelope passing through the protostellar position." (3 Results)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit kinematical model of infalling flattened envelope to PV diagrams**: 3D power-law density/temperature envelope, free-fall velocity, LTE model images, simulated ALMA observations, chi2 fit to PV diagrams of C18O and H13CO+  
  > "Then we simulated ALMA observations of the model images with the same array configuration and coverage of hour angle as our real observations." (4 Kinematical models)
   - software: RADEX
   - parameter: Free parameters n(R0), p, Vin(R0); j fixed at 3e-5 km/s pc or 0; low-velocity channels 7.7–8.9 km/s excluded; R0=100 au; outer radius 700 au  
  > "The channels at the low velocities of $V_{\rm LSR} = 7.7\mbox{--}8.9$ km s$^{-1}$ (vertical dashed lines in Fig. 5) are excluded in the fitting" (4 Kinematical models)
   - assumption: Distance 100 pc, inclination 87 deg, T=38 K (r/100au)^-0.4, polar cavity within 60 deg of axis empty  
  > "T(r) = 38 \cdot (\frac{r}{100~{\rm au}})^{-0.4}\ {\rm K}" (4 Kinematical models)
   - fitting: chi2 minimization; uncertainties from models with chi2 < chi2min + 1  
  > "The uncertainties of our best-fit parameters are estimated from the parameter ranges of the models having $\chi^2$ less than the minimum $\chi^2$ + 1" (4 Kinematical models)
   - validation: Tested PA changes of ±10 deg and shallower velocity profile r^-0.25; results unchanged within 0.1 km/s  
  > "The difference between the best-fit $V_{\rm in}$(100 au) with the two different velocities profiles is 0.1 km s$^{-1}$, less than our uncertainty." (4 Kinematical models)
3. **Estimate Hall parameter and compare with MHD simulations**: Hall parameter from B, n(H2), momentum transfer rate; compare drift limit to simulations  
  > "Still, with a conservative value of $B > 100$ $\mu$G, $\beta_{i,{\rm H_2}}$ is estimated to be $>$20 on a 100 au scale." (5 Discussion)
   - assumption: C18O abundance 3e-7 relative to H2; B>100 uG; mu=2.36  
  > "On the assumption of a typical C$^{18}$O abundance of $3\times10^{-7}$ relative to H$_2$ (cite: Frerking82)" (4 Kinematical models)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.3: Calibration and clean imaging  
  > "of version 4.5.3. The image of the H$^{13}$CO$^+$ emission was generated" (2 Observations)
- **RADEX** : Check H13CO+ (3-2) thermalization  
  > "as calculated with the non-LTE radiative transfer code *RADEX* (cite: radex07)" (4 Kinematical models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Vin(100 au) H13CO+ | 0.85 | 0.2 | km/s | 2 | $V_{\rm in}$(100 au) / 0.85$\pm$0.2 km s$^{-1}$ / 0.85$\pm$0.2 km s$^{-1}$ |
| Vin(100 au) C18O | 0.85 | 0.2 | km/s | 2 | $V_{\rm in}$(100 au) / 0.85$\pm$0.2 km s$^{-1}$ / 0.85$\pm$0.2 km s$^{-1}$ |
| Upper limit on ion-neutral velocity difference at 100 au | 0.3 | not stated | km/s | 2 | estimated to be less than 0.3 km s$^{-1}$ at a radius of 100 au |
| Density power-law index p | -2.1 | 0.5 | dimensionless | 2 | $p$ / $-2.1$$\pm$0.5 / $-2.1$$\pm$0.5 |
| H2 number density at 100 au | 9e6 | not stated | cm^-3 | 2 | the H$_2$ number density is estimated to be $9\times10^6$ cm$^{-3}$ |
| Protostellar mass from free fall | ~0.04 | not stated | Msun | 2 | corresponds to a protostellar mass of $\sim$0.04 $M_\ensuremath{\odot}$ |
| Hall parameter of H13CO+ | >20 | not stated | dimensionless | 3 | $\beta_{i,{\rm H_2}}$ is estimated to be $>$20 on a 100 au scale |

## Qualitative findings

- Central compact 1–2" component elongated perpendicular to the outflow with velocity gradient along outflow, tracing infalling flattened envelope  
  > "most likely traces the infalling flattened envelope." (abstract)

## Claim tuples

- H: Ions and neutrals show different infall velocities at 100 au due to ambipolar drift | E: Kinematical model chi2 fit of H13CO+ and C18O PV diagrams | R: Both Vin = 0.85±0.2 km/s; difference <0.3 km/s | F: No detectable drift; field well coupled at 100 au | **supported**
- H: Enhanced ambipolar diffusivity simulations (no small grains) apply to B335 | E: Compare drift limit with simulated 0.5–1 km/s | R: Not detected | F: Inconsistent with such simulations, though midplane drift not excluded due to resolution | **partially**

## Reasoning

- Why this data: C18O and H13CO+ chemically similar, abundant in inner envelope, likely optically thin  
  > "C$^{18}$O and H$^{13}$CO$^+$ are chemically similar (cite: Lee04; Aikawa08)" (1 Introduction)
- Why this method: _not stated_
- Alternative: Ideal MHD case judged less likely because outflow/jets suggest a small disk  
  > "Thus, B335 is less likely the ideal MHD case." (5 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Limited angular resolution may dilute midplane drift; H13CO+ cannot resolve velocity gradient seen in C18O  
  > "the angular resolution of our H$^{13}$CO$^+$ observations is not sufficient to resolve the velocity gradient observed in the C$^{18}$O emission." (3 Results)
- Caveat (inferred, ours): Result depends on assumed B>100 uG and ISM C18O abundance for the Hall parameter
- Caveat (inferred, ours): Fixed model geometry and temperature and a single power-law velocity profile may bias Vin
- Caveat (inferred, ours): Upper limit relies on error propagation of ±0.2 km/s uncertainties

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Model code not named or released
- Missing: C18O data details only in Yen et al. 2015b
- Missing: Clean masks and thresholds not given
- Data volume (inferred): ~20-50 GB for two ALMA projects
- Score (inferred): 3/5, Data identifiable and key numbers given, but the modeling code and many imaging details are missing.
- Rediscovery candidate: no, Model code and imaging details not provided, so the fit is hard to redo exactly.

## Links

- Method: Yen et al. 2015b (cite: Yen15b) (C18O data, imaging and kinematical model setup)
- Method: Pinto & Galli 2008 (cite: Pinto08) (Momentum transfer rate coefficient)
- Companion: (cite: Yen15b) (Earlier ALMA C18O analysis of B335)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 38,
  "rate": 0.594
 },
 "evidence_ok": true
}
```
