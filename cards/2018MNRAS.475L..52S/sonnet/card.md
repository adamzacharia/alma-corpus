# Imaging the molecular outflows of the prototypical ULIRG NGC 6240 with ALMA

`2018MNRAS.475L..52S` | Monthly Notices of the Royal Astronomical Society 2018 | first author: Saito, T. | arXiv: 1712.07660 | DOI: 10.1093/mnrasl/slx207

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars
- Question: What are the spatial and velocity distributions of the molecular outflows in the merging ULIRG NGC 6240, as traced by broad CO (2-1) wings?  
  > "The goal of this letter is to reveal the complete spatial and velocity distribution of the molecular outflow, which has been previously only partly mapped, in NGC 6240." (Introduction)
- Target **NGC 6240**: coordinates _not stated_; z/distance z = 0.024480, 1.0'' = 480 pc  
  > "NGC 6240 is a well-studied close galaxy pair in the local Universe (z = 0.024480, 1.0$''$ = 480 pc)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00003.S
- bands: Band 6  
  > "The Band 6 receiver was tuned to cover CO (2–1) ($\nu_{\rm obs}$ = 225.02928 GHz)." (ALMA Band 6 Observation)
- frequencies and spectral setup: CO spw: 1.953 MHz (~2.6 km/s) resolution, 1.875 GHz bandwidth  
  > "has a resolution of 1.953 MHz ($\sim$2.6 km s$^{-1}$) with a bandwidth of 1.875 GHz" (ALMA Band 6 Observation)
- continuum bandwidth: _not stated_
- arrays: forty-two 12 m antennas  
  > "using forty-two 12 m antennas" (ALMA Band 6 Observation)
- configurations: _not stated_
- baselines: 15.1–783.5 m  
  > "The field of view, on-source time, and baseline lengths are $\sim$28$''$, $\sim$4 minutes, and 15.1–783.5 m, respectively." (ALMA Band 6 Observation)
- angular resolution: 0.97'' x 0.53'' (PA = 64.5 deg)  
  > "The synthesized beam size and sensitivity are 0.97$''$ $\times$ 0.53$''$ (PA = 64.5$^\circ$)" (ALMA Band 6 Observation)
- max recoverable scale: _not stated_
- sensitivity: 2.5 mJy/beam at 5 km/s bin  
  > "2.5 mJy beam$^{-1}$ (at 5 km s$^{-1}$ bin)" (ALMA Band 6 Observation)
- time on source: ~4 minutes  
  > "The field of view, on-source time, and baseline lengths are $\sim$28$''$, $\sim$4 minutes, and 15.1–783.5 m, respectively." (ALMA Band 6 Observation)
- observing dates: 2016 June 26  
  > "NGC 6240 was observed on 2016 June 26" (ALMA Band 6 Observation)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (not stated)
- External data: Single-dish CO flux for comparison  
  > "which is 86 $\pm$ 15 % of the single-dish value (cite: Papadopoulos14)" (Results) [from (cite: Papadopoulos14)]
- External data: Systemic velocities of nuclei 7122 (north) and 7164 (south) km/s  
  > "the systemic velocity of the northern (southern) nucleus of 7122 (7164) km s$^{-1}$ in the radio LSRK velocity frame (cite: Hagiwara10)" (Discussion) [from (cite: Hagiwara10)]
- External data: Nuclear SFR ~61 Msun/yr  
  > "Using the nuclear SFR of $\sim$61 $M_{\odot}$ yr$^{-1}$ derived from radio-to-FIR SED fitting (cite: Yun02)" (Discussion) [from (cite: Yun02)]

## Processing

### Calibration

- pipeline or manual: Used delivered calibrated uv data  
  > "We used the delivered calibrated $uv$ data." (ALMA Band 6 Observation)
- casa version: CASA 4.5.3  
  > "The data reduction was carried out using `CASA` version 4.5.3" (ALMA Band 6 Observation)
- pipeline version: _not stated_
- archive products used as is: delivered calibrated uv data  
  > "We used the delivered calibrated $uv$ data." (ALMA Band 6 Observation)
- flux calibrator: Titan (amplitude); J1550+0527 bandpass; J1651+0129 phase  
  > "Titan, J1550+0527, and J1651+0129 were observed as the amplitude, bandpass, and phase calibrators, respectively." (ALMA Band 6 Observation)
- flux scale uncertainty: 5%  
  > "we regard the accuracy of the absolute flux calibration as 5% throughout this paper" (ALMA Band 6 Observation)
- self calibration: two rounds of phase self-calibration, model from bright compact source at CO peak (~7050 km/s)  
  > "we carried out a two-rounded phase self-calibration after the normal ALMA calibration process" (ALMA Band 6 Observation)

### Imaging

- task: CASA clean  
  > "We used the `CASA` task `clean` in multi-scale mode" (ALMA Band 6 Observation)
- deconvolver: multiscale CLEAN  
  > "to make use of the multiscale CLEAN deconvolution algorithm (cite: Cornwell08)" (ALMA Band 6 Observation)
- weighting robust: natural weighting  
  > "All maps are reconstructed with natural weighting." (ALMA Band 6 Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: iterative auto-masking per CASA guide  
  > "we performed an iterative auto-masking procedure as described in the CASA guide" (ALMA Band 6 Observation)
- multiscale scales: _not stated_
- continuum subtraction: uv-plane, first-order polynomial to line-free channels in both sidebands  
  > "Continuum emission was subtracted in the $uv$-plane by fitting the line-free channels in both lower and upper sidebands with a first order polynomial function" (ALMA Band 6 Observation)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.97'' x 0.53'', PA 64.5 deg  
  > "0.97$''$ $\times$ 0.53$''$ (PA = 64.5$^\circ$)" (ALMA Band 6 Observation)
- final rms: 2.5 mJy/beam at 5 km/s  
  > "2.5 mJy beam$^{-1}$ (at 5 km s$^{-1}$ bin)" (ALMA Band 6 Observation)

### Inherited from earlier work

- Uniformly filled cone geometry for mass outflow rate  
  > "This equation assumes a uniformly filled cone geometry (cite: Maiolino12)." (Discussion) [from (cite: Maiolino12)]
- Auto-masking procedure following CASA guide  
  > "we performed an iterative auto-masking procedure as described in the CASA guide" (ALMA Band 6 Observation) [from CASA guide (M100 Band3 combine)]

### Not stated but needed to reproduce (our reading)

- Multiscale scales, cell size, image size, clean threshold
- Line-free channel ranges
- Self-calibration solution intervals
- Fitting code and optimizer used for Gaussian fits
- How projected velocities and distances were measured from linewidth peaks
- Coordinates of the phase center

## Analysis recipe

1. **Image CO(2-1) cube**: Self-calibrate, subtract continuum in uv, multiscale clean with natural weighting to 5 km/s channels  
  > "then we made a CO (2–1) data cube with 5 km s$^{-1}$ resolution" (ALMA Band 6 Observation)
   - software: CASA
   - fitting: _not stated_
   - validation: Total flux compared with single-dish: 86 ± 15 %  
  > "which is 86 $\pm$ 15 % of the single-dish value (cite: Papadopoulos14)" (Results)
2. **Multiple Gaussian fit to spectra**: Hexagonal Nyquist sampling with 2.0'' apertures (step 1.0''); one-component fit if peak S/N>5, two-component if residual peak S/N>5  
  > "A hexagonal Nyquist sampling with 2.0$''$ aperture (step = 1.0$''$) was performed on the CO (2–1) cube to decrease the number of spectra" (Results)
   - parameter: Broad component defined as FWHM > 500 km/s  
  > "we simply define data whose linewidths are larger than 500 km s$^{-1}$ as “broad components"." (Results)
   - fitting: Initial guesses from peak flux, peak velocity and number of channels; second Gaussian from residual of one-component fit  
  > "initial parameters of the first Gaussian are obtained from the one-component fit, although those of the second Gaussian were chosen from the residual of the one-component fit" (Results)
   - validation: Residuals of two-component fit have peak S/N<5, so no third component  
  > "The peaks seen in the residual of the two-component fit are statistically insignificant (peak S/N $<$ 5)." (Results)
3. **Derive outflow mass, rate, and age**: Mdot = 3 v M tan(alpha)/R for uniformly filled cone; launching points at double nuclei  
  > "We assume the launching points are the double nuclei" (Discussion)
   - assumption: inclination 45 deg, CO(2-1)/CO(1-0) ratio unity, alpha_CO = 0.8 Msun (K km/s pc^2)^-1  
  > "are 45$^\circ$, unity, and 0.8 $M_{\odot}$ (K km s$^{-1}$ pc$^{2}$)$^{-1}$, respectively, for the sake of simplicity" (Discussion)
   - fitting: _not stated_
   - validation: Total mass compared with Cicone14  
  > "which is consistent with the value derived from unresolved CO data; (cite: Cicone14)" (Discussion)

## Software

- **CASA** 4.5.3: Data reduction, imaging with clean multiscale  
  > "The data reduction was carried out using `CASA` version 4.5.3" (ALMA Band 6 Observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total CO(2-1) integrated intensity inside 3 sigma | 1283 | 64 | Jy km/s | 1 | 1283 $\pm$ 64 Jy km s$^{-1}$ |
| Total outflow mass | 10^8.7 | not stated | Msun | 3 | $\log M_{\rm H_2, out}$ ($M_{\odot}$) / 7.9 / 8.1 / 8.2 / 8.2 / 8.7 |
| Total mass outflow rate | 231 | not stated | Msun/yr | 3 | $\dot{M}_{\rm H_2, out}$ ($M_{\odot}$ yr$^{-1}$) / 8 / 43 / 86 / 94 / 231 |
| Mass loading factor | ~4 | not stated | dimensionless | 3 | the mass loading factor ($\dot{M}_{\rm H_2, out}$ divided by SFR) is $\sim$4 |
| Outflow ages | 5 to 27 | not stated | Myr | 3 | found that it ranges from 5 to 27 Myr |

## Qualitative findings

- Broad CO wings with FWZI ~2000 km/s; four broad-linewidth peaks 1-2 kpc from the nuclei coincide with Halpha, H2 and X-ray  
  > "The distribution of the broad CO components show four extremely large linewidth regions ($\sim$1000 km s$^{-1}$) located 1-2 kpc away from both nuclei." (abstract)

## Claim tuples

- H: Broad CO wings in NGC 6240 trace spatially resolved molecular outflows from the double nuclei | E: Multi-Gaussian fitting of the ALMA CO(2-1) cube and comparison with Halpha, H2, X-ray | R: Four broad-component linewidth peaks (~1000 km/s) 1-2 kpc from the nuclei coincide with multiphase tracers | F: CO wings are associated with twin east-west bipolar molecular outflows | **supported**
- H: The outflow rate is lower than the previous unresolved estimate | E: Conical-geometry estimate | R: Total ~230 Msun/yr, 3.5 times lower than Cicone14 | F: The difference arises from assumed geometry | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Inflow motions as alternative explanation, rejected because OH high-velocity component is only on blueshifted side  
  > "we favor the latter because the absorption profile of the OH doublet toward the central 9$''$ shows that a high velocity component faster than 1000 km s$^{-1}$ is only detected on the blueshifted side" (Discussion)
- How they decided it was enough: _not stated_
- Caveat (inferred, ours): Assumed inclination 45 deg, alpha_CO and CO(2-1)/(1-0) ratio are unconstrained and drive mass and rate
- Caveat (inferred, ours): Outflow vs inflow/merger kinematics is ambiguous; no uncertainties on masses and rates
- Caveat (inferred, ours): Short ~4 min on-source observation; natural weighting may resolve out extended emission

## Reproducibility

- Data public (paper): ALMA project data cited with project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00003.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Multiscale scales, cell/image size, clean threshold
- Missing: Self-calibration solution intervals
- Missing: Details of measuring projected velocities and distances for the outflow peaks
- Data volume (inferred): ~10-50 GB
- Score (inferred): 6/5, Public data and a clear recipe, but several imaging and measurement parameters are missing.
- Rediscovery candidate: yes, Public single-dataset ALMA data; numeric results (flux, masses, rates) can be re-derived with the stated recipe.

## Links

- Method: (cite: Cornwell08) (Multiscale CLEAN)
- Method: (cite: Maiolino12) (Outflow rate equation for conical geometry)
- Companion: (cite: Feruglio13a) (Earlier CO(1-0) observations of broad wings)
- Companion: (cite: Cicone14) (Earlier outflow estimate for comparison)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
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
  "facts": 62,
  "stated": 41,
  "rate": 0.661
 },
 "evidence_ok": true
}
```
