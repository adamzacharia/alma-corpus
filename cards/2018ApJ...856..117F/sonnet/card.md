# Turbulence in the TW Hya Disk

`2018ApJ...856..117F` | The Astrophysical Journal 2018 | first author: Flaherty, Kevin M. | arXiv: 1803.03842 | DOI: 10.3847/1538-4357/aab615

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: How strong is turbulent line broadening in the TW Hya disk when ALMA CO(2-1) plus SMA CO(3-2) and CO(6-5) are fit with a self-consistent parametric model, and why does it differ from the earlier Teague et al. (2016) detection?  
  > "find an upper limit on the turbulent broadening of $<$0.08c$_s$ ($\alpha<$0.007 for $\alpha$ defined only within 2-3 pressure scale heights above the midplane)" (abstract)
- Target **TW Hya**: coordinates _not stated_; z/distance 54 pc assumed (Gaia 59.0±0.5 pc)  
  > "The distance to TW Hya is assumed to be 54 pc, which is slightly smaller than the recent GAIA parallax measurement of 59.0$\pm$0.5 pc (cite: gaia16)" (Parametric models); distance from chosen to match T16; Gaia parallax noted  
  > "The distance to TW Hya is assumed to be 54 pc, which is slightly smaller than the recent GAIA parallax measurement of 59.0$\pm$0.5 pc (cite: gaia16)" (Parametric models)

## Data provenance

- ALMA projects: 2013.1.00387.S
- bands: _not stated_
- frequencies and spectral setup: CO(2-1) window with 15 kHz (40 m/s) channels  
  > "The spectral window containing the CO(2-1) line has 15 kHz (40 m s$^{-1}$) channels" (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 16-424 kλ (20-550 m)  
  > "baselines extending from 16-424 k$\lambda$ (20-550 meters)" (Observations)
- angular resolution: 0.64x0.51 arcsec beam (MIRIAD, robust=0.5)  
  > "results in a beam size of 0$\ensuremath{''}$64x0$\ensuremath{''}$51" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data, PI S. Guilloteau; archival SMA CO(3-2) and CO(6-5)  
  > "We also analyze archival SMA observations of CO(3-2) (cite: hug11) and CO(6-5) (cite: qi06)." (Observations)
- Line: CO 2-1 (230.538 GHz)
- Line: CO 3-2 (SMA) (345.79599 GHz)
- Line: CO 6-5 (SMA) (691.47308 GHz)
- Other facility **SMA**: CO(3-2) (2008, 16-182 m baselines) and CO(6-5) (2005, 7-68 m baselines)  
  > "The CO(3-2) observations were taken in 2008 with baselines of 16-182m" (Observations)
- External data: CO snow line used to fix midplane T = 19 K at 20 au  
  > "we use previous measurements of the CO snow line (cite: sch16) to fix the midplane temperature at 19 K at 20 au" (Parametric models) [from (cite: sch16)]
- External data: Disk mass 0.05 Msun and CO/H2 = 1e-6 from HD measurements  
  > "We assume the disk mass is 0.05M$_{\odot}$, with a CO/H$_2$ abundance of 10$^{-6}$, based on the measurements of HD from (cite: ber13)." (Parametric models) [from (cite: ber13)]
- External data: Synthetic-data input structure for the mock tests  
  > "Synthetic CO data are generated based on the temperature, density, and abundance distribution from (cite: kam16)" (Tests with Synthetic Data) [from (cite: kam16)]
- Simulation/model as data: Mock CO(2-1) data from the Kama et al. 2016 disk model via LIME, with turbulence 0.05 cs and 0.2 cs  
  > "one has weak turbulence ($\delta v_{\rm turb}$=0.05c$_s$) while the second has strong turbulence ($\delta v_{\rm turb}$=0.2c$_s$)" (Tests with Synthetic Data)

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration script, then self-calibration on the continuum window  
  > "The visibilities were calibrated using the standard ALMA calibration script and were self-calibrated using the continuum spectral window." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Amplitude/phase calibrator J1037-2934, referenced to Ganymede  
  > "This amplitude calibrator is referenced to the absolute flux calibrator Ganymede" (Results)
- flux scale uncertainty: 7% for J1037-2934 (per T16); ~6% Ganymede; tested ±20%  
  > "T16 note a 7% uncertainty in the flux of the amplitude and phase calibrator, J1037-2934." (Results)
- self calibration: _not stated_

### Imaging

- task: MIRIAD clean  
  > "Imaging the line emission with the MIRIAD clean task, using robust=0.5 visibility weighting" (Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "using robust=0.5 visibility weighting" (Observations)
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
- final beam: 0.64x0.51 arcsec  
  > "results in a beam size of 0$\ensuremath{''}$64x0$\ensuremath{''}$51" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Modeling code and method used for HD 163296  
  > "was used previously in (cite: fla15) and (cite: fla17) and is based on earlier work by (cite: ros13) and (cite: dar03)" (Parametric models) [from (cite: fla15), (cite: fla17), (cite: ros13), (cite: dar03)]
- Stellar mass 0.7 Msun and distance 54 pc chosen to match T16  
  > "We use a stellar mass of 0.7 M$_{\odot}$, identical to that used by T16" (Parametric models) [from (cite: tea16)]
- Exclude inner 40 au in image-plane fitting, matching T16  
  > "We exclude pixels within 40 au of the disk center in the image plane, matching the procedure in T16." (Image Plane Fitting) [from (cite: tea16)]
- Photodissociation column and freeze-out treatment, velocity field with pressure support  
  > "The velocity field is Keplerian, with corrections for the height above the midplane and the pressure support of the gas, as in (cite: ros13)." (Parametric models) [from (cite: ros13)]

### Not stated but needed to reproduce (our reading)

- Priors and bounds for the MCMC parameters
- Initial parameter distribution of the walkers
- Exact inclination, position angle and offset handling in the visibility fit beyond preliminary values
- Imaging and clean parameters for the MIRIAD images (mask, threshold)
- Visibility averaging and weights used in the fit
- Self-calibration solutions of the archival data (how reproduced)
- Detailed reduction of the SMA data (deferred to earlier papers)
- Code for the ray-tracing model is not given

## Analysis recipe

1. **Prepare visibilities**: Use calibrated ALMA CO(2-1) visibilities, ignore channels >0.6 km/s from line center, subtract point source of 0.189±0.002 Jy  
  > "ignoring the channels with velocities more than 0.6 km s$^{-1}$ from the line center when comparing with the model" (Parametric models)
   - software: MIRIAD
   - parameter: Point source flux 0.189±0.002 Jy from baselines >200 kλ  
  > "with a flux of 0.189$\pm$0.002 Jy, as derived from a fit to baselines $>$200k$\lambda$ across all spectral channels" (Parametric models)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit parametric disk model to visibilities**: LTE ray-tracing model with hydrostatic equilibrium, vertical temperature gradient, CO layer; model visibilities via UVMODEL; MCMC  
  > "Model images are generated at each velocity channel using an LTE ray-tracing code and model visibilities are created using the MIRIAD task UVMODEL." (Parametric models)
   - software: MIRIAD, emcee
   - parameter: Free: T_atm0, T_mid0, q_atm, R_c, inclination, δv_turb; fixed: stellar mass, distance, CO abundance, PA, systemic velocity, offset  
  > "we allow $T_{\rm atm0}$, $T_{\rm mid0}$, $q_{\rm atm}$, $R_c$, inclination and $\delta v_{\rm turb}$ to vary" (Parametric models)
   - assumption: Mdisk=0.05 Msun, CO/H2=1e-6, M*=0.7 Msun, d=54 pc, CO freeze-out at 19 K  
  > "We assume the disk mass is 0.05M$_{\odot}$, with a CO/H$_2$ abundance of 10$^{-6}$" (Parametric models)
   - fitting: emcee, 80 walkers, 1600 steps, 600 burn-in; log(R_c) fitted; uncertainties from line-free channel dispersion  
  > "Typical MCMC chains consist of 80 walkers and 1600 steps. The first 600 steps are removed as burn-in" (Parametric models)
   - validation: Recovery of input from mock LIME data  
  > "we recover the input density distribution, and the gas temperature at the $\tau$=1 surface of the CO(2-1) in our best fit temperature structure is within 5% of the input temperature structure." (Tests with Synthetic Data)
3. **Test systematics and model variants**: Refit with model visibilities scaled ±20%, multi-line fit, CO abundance 1e-7, variable gamma, vertically isothermal, image-plane fit  
  > "we rerun our fitting with the model visibilities either scaled up or down by 20% before comparing them to the data." (Amplitude Calibration Uncertainty)
   - software: emcee
   - fitting: same MCMC  
  > "The posterior distribution functions for each parameter are estimated using the MCMC routine EMCEE (cite: for13) based on the Affine-Invariant algorithm originally proposed in (cite: goo10)." (Parametric models)
   - validation: Compare turbulence limits and chi2 across variants (Table 1)  
  > "Median, plus 3$\sigma$ ranges, of the marginalized posterior distribution functions." (Table 1)
4. **Convert turbulence limit to alpha and accretion rate**: alpha<0.007 from limit; accretion rate via alpha-Sigma relation using HD/CO-isotopologue surface densities  
  > "we derive accretion rates through the outer disk of $<$4$\times$10$^{-9}$M$_{\odot}$ yr$^{-1}$." (Implications of modest turbulence around TW Hya)
   - assumption: alpha limit representative throughout disk  
  > "This assumes that our limit on $\alpha$ is representative of the turbulent behavior throughout the disk" (Implications of modest turbulence around TW Hya)
   - fitting: _not stated_
   - validation: Compared with measured stellar accretion rate  
  > "This accretion limit is also consistent with the measured accretion rate onto the star" (Implications of modest turbulence around TW Hya)

## Software

- **MIRIAD** : clean imaging and UVMODEL model visibilities  
  > "model visibilities are created using the MIRIAD task UVMODEL" (Parametric models)
- **emcee** : MCMC posterior estimation  
  > "The posterior distribution functions for each parameter are estimated using the MCMC routine EMCEE (cite: for13)" (Parametric models)
- **LIME** : mock CO(2-1) images  
  > "fed through LIME (cite: bri10) to generate model images of CO(2-1)" (Tests with Synthetic Data)
- **Astropy** : acknowledged as used  
  > "The research made use of Astropy, a community-developed core Python package for Astronomy (cite: astropy13)." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Turbulence upper limit, fiducial | <0.08 | 3σ | c_s | 2 | / Fiducial / -0.46$^{+0.02}_{-0.03}$ / 1.61$^{+0.09}_{-0.06}$ / 33$\pm1$ / 15$\pm2$ / 6.2$\pm$0.1 / $<$0.08c$_s$ |
| alpha upper limit | <0.007 | not stated | dimensionless | 4 | Our TW Hya limit corresponds to $\alpha<0.007$ |
| Turbulence limit, vertically isothermal | <10 m/s (≲0.04 c_s) | not stated | m/s | 3 | limiting the non-thermal motion to less than 10 m s$^{-1}$ ($\lesssim$0.04c$_s$ in the outer disk) |
| Turbulence limit, low CO abundance | <0.13 | not stated | c_s | 3 | from $<$0.08c$_s$ in the fiducial model to $<$0.13c$_s$ in the low abundance model |
| Accretion rate through outer disk | <4e-9 | not stated | Msun/yr | 4 | accretion rates through the outer disk of $<$4$\times$10$^{-9}$M$_{\odot}$ yr$^{-1}$ |
| CO(2-1) integrated flux | 16.3 | 3.3 | Jy km/s | 0 | consistent with our 16.3$\pm$3.3 Jy km s$^{-1}$ |

## Qualitative findings

- Image-plane and visibility fits agree for TW Hya, but image-plane fitting has pitfalls (covariance, fidelity)  
  > "We find that fitting to the image plane produces nearly identical results to fitting the visibilities." (Image Plane Fitting)

## Claim tuples

- H: TW Hya is substantially turbulent as reported by T16 | E: Fit ALMA CO(2-1) visibilities with a self-consistent parametric model | R: δv_turb<0.08 cs (3σ), range 0.04-0.13 cs across variants | F: Turbulence is weak, below T16's 0.2-0.4 cs | **supported**
- H: Calibration, CO abundance, or image-plane fitting explain the discrepancy | E: ±20% flux scaling, lower CO abundance, variable gamma, image-plane fit | R: limits stay below T16 in all cases | F: These are not the source of the discrepancy | **supported**
- H: Temperature-density coupling or CO layering causes the difference | E: Compare with T16 assumptions | R: Source narrowed but not quantified | F: Likely hydrostatic coupling and/or thin CO layer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Use the same data as T16 and the HD 163296 method to isolate methodological differences  
  > "By studying a similar data set, we can isolate differences in methodology." (Introduction)
- Alternative: Fixed gamma=1.9 rejected for poor fit  
  > "are unable to find an acceptable fit to the data under this condition" (CO abundance)
- How they decided it was enough: _not stated_
- Limitation (authors): Mock tests recover temperature poorly (20-50%) far from the tau=1 surface  
  > "we recover the temperature only to within 20-50%" (Tests with Synthetic Data)
- Limitation (authors): Source of discrepancy not conclusively identified  
  > "although further work is needed to quantify the influence of these prescriptions" (abstract)
- Caveat (inferred, ours): Model-dependent upper limit; the parametrization drives the result
- Caveat (inferred, ours): Distance 54 pc and fixed gas mass were not marginalized
- Caveat (inferred, ours): ALMA data dominate the weights, so the multi-line fit adds little
- Caveat (inferred, ours): Mock test uses the same functional form for turbulence as the fit

## Reproducibility

- Data public (paper): ALMA data publicly available; SMA data archival  
  > "were corrected by the time the data became publicly available" (Observations)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Modeling code (ray-tracer) not released
- Missing: MCMC priors and bounds
- Missing: Exact MIRIAD imaging parameters
- Data volume (inferred): ~10-50 GB for the ALMA CO(2-1) dataset
- Score (inferred): 3/5, Data are public and the method is described, but the custom model code and priors are missing.
- Rediscovery candidate: no, The custom ray-tracing code and the MCMC priors are not available, so the fit cannot be redone from the paper alone.

## Links

- Method: (cite: fla15; fla17) (original modeling method)
- Method: (cite: ros13) (velocity field and temperature prescription)
- Companion: (cite: tea16) (earlier analysis of same ALMA data finding 0.2-0.4 cs turbulence)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 45,
  "rate": 0.584
 },
 "evidence_ok": true
}
```
