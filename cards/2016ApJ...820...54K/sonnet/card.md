# Grain Size Constraints on HL Tau with Polarization Signature

`2016ApJ...820...54K` | The Astrophysical Journal 2016 | first author: Kataoka, Akimasa | arXiv: 1507.08902 | DOI: 10.3847/0004-637X/820/1/54

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can self-scattering of thermal dust emission explain the millimeter-wave polarization of the HL Tau disk, and what maximum grain size does it imply?  
  > "In this paper, we report a modeling of the millimeter-wave polarization of the HL Tau disk with the self-polarization." (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a protostar 140 pc away from the sun (cite: Rebull04)." (Introduction); distance from Rebull et al. 2004 (cite: Rebull04)  
  > "HL Tau is a protostar 140 pc away from the sun (cite: Rebull04)." (Introduction)

## Data provenance

- ALMA projects: 2011.0.00015.SV
- bands: Band 6 (1.3 mm) continuum, used to calibrate the disk model  
  > "to reproduce the observation along the major axis of the disk observed with the continuum observed with the ALMA Band 6." (Method)
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
- pi or archival as stated: _not stated_
- Other facility **CARMA**: Polarization degree 0.89% at 1.3 mm, polarization vectors  
  > "The net polarization degree is $0.89 \%$ in average with CARMA, and $0.86 \pm 0.4 \%$ with SMA." (Introduction)
- Other facility **SMA**: Polarization degree 0.86 ± 0.4% at 0.89 mm  
  > "The net polarization degree is $0.89 \%$ in average with CARMA, and $0.86 \pm 0.4 \%$ with SMA." (Introduction)
- External data: ALMA Band 6 1.3 mm continuum image/profile of HL Tau (long baseline campaign)  
  > "reasonably reproduces the sub-mm continuum image at $\lambda = 1.3 {\rm~mm}$ (cite: Partnership15)." (Method) [from ALMA Partnership 2015 (cite: Partnership15)]
- External data: CARMA and SMA polarization measurements of HL Tau  
  > "we successfully reproduced the polarization vectors and polarization degree of HL Tau observed with CARMA and SMA(cite: Stephens14)." (Conclusions) [from Stephens et al. 2014 (cite: Stephens14)]
- Simulation/model as data: RADMC-3D radiative transfer of an axisymmetric gapped disk model with spherical Mie grains, amax varied  
  > "We perform the radiative transfer simulations with a public code RADMC-3D to obtain the dust continuum, the polarized intensity, and the polarization degree." (Method)

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

- Polarization formula P = C P90 omega and ±50% model uncertainty  
  > "The theoretical model is calculated as the product of polarization degree at $90^\circ$ scattering $P_{90}$ and the albedo $\omega$ (cite: Kataoka15)." (Results) [from Kataoka et al. 2015 (cite: Kataoka15)]
- Dust composition (silicate, organics, water ice)  
  > "The composition is assumed to be the mixture of silicate, organics, and water ice (cite: Kataoka14; Pollack94)." (Method) [from (cite: Kataoka14; Pollack94)]

### Not stated but needed to reproduce (our reading)

- Mixture mass fractions of silicate, organics and ice
- Gas scale height / stellar parameters used for h_g
- RADMC-3D version, photon numbers, grid and wavelength setup
- Beam convolution and how the model image was compared with the ALMA data
- Code for the disk model not released

## Analysis recipe

1. **Build disk model matching ALMA 1.3 mm profile**: Power-law temperature and optical depth with 7 Gaussian gaps tuned to the Band 6 major-axis brightness temperature  
  > "Then, we add the additional gaps on the density profile to reproduce the observation along the major axis of the disk observed with the continuum observed with the ALMA Band 6." (Method)
   - parameter: T0=280 K, qt=0.3, tau0=2.0, p=0.3, sexp=4, Rexp=120 AU  
  > "| $R_{\rm exp}$ | 120 AU |" (Table 1)
   - assumption: distance 140 pc, inclination 40 deg  
  > "The inclination is assumed to be $40^\circ$." (Method)
   - fitting: _not stated_
   - validation: Visual comparison of model and observed brightness temperature on the major axis  
  > "Figure [1](#fig:model) shows the brightness temperature derived from the Band 6 data on the major axis illustrated with the model brightness temperature" (Method)
2. **Compute dust opacity and surface density**: Mie theory with Maxwell-Garnett mixing; Sigma_d = tau/kappa_abs(amax,1.3 mm)  
  > "The opacity is calculated with Mie theory." (Method)
   - parameter: q=-3.5; kappa_abs(150 um,1.3 mm)=0.24 cm2/g  
  > "$\kappa_{\rm abs}(a_{\rm max}=150 {\rm~\mu m}, \lambda=1.3 {\rm~mm})=0.24 {\rm~cm^{2}~g^{-1}}$" (Method)
   - assumption: spherical grains, power-law size distribution, settling factor f_settle=10  
  > "we set $h_{\rm d}=h_{\rm g}/f_{\rm settle}$, where $h_{\rm g}$ is the gas pressure scale height and $f_{\rm settle}=10$" (Method)
   - fitting: _not stated_
   - validation: _not stated_
3. **Radiative transfer polarization vs amax**: RADMC-3D scattering polarization for several amax; calibrate P=C P90 omega, compare to CARMA 1.3 mm and SMA 0.89 mm  
  > "where $C=2.0~\%$ calibrated with the radiative transfer calculations in this paper." (Results)
   - software: RADMC-3D
   - assumption: model uncertainty ±50%  
  > "We also includes the uncertainty of the model of $\pm ~50~\%$" (Results)
   - fitting: _not stated_
   - validation: Alternative disk model (qt=0.5) gives C=1.3% and a similar amax  
  > "The calibration factor $C$ of the formula $CP_{90}\omega$ is set to be $C=1.3\%$." (Dependence on disk models)

## Software

- **RADMC-3D** : Radiative transfer for continuum, polarized intensity and polarization degree  
  > "We perform the radiative transfer simulations with a public code RADMC-3D" (Method)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Allowed maximum grain size (CARMA only) | 70-350 | not stated | micron | 3 | can only be explained with the grain size in the range of $70 {\rm~\mu m} < a_{\rm max} < 350 {\rm~\mu m}$ |
| Allowed maximum grain size (CARMA+SMA) | 70-270 | not stated | micron | 3 | $70 {\rm~\mu m} < a_{\rm max} < 270 {\rm~\mu m}$ to explain the polarization degree of the both CARMA and SMA observations |
| Calibration factor C | 2.0 | ±50% model | percent | 3 | where $C=2.0~\%$ calibrated with the radiative transfer calculations in this paper. |
| Stokes number for 150 um grains | 1e-4 to 1e-3 | not stated | dimensionless | 0 | the Stokes number is estimated to be ${\rm St}\sim 10^{-4} - 10^{-3}$ in the case of the 150 ${\rm \mu m}$ spherical grains. |

## Qualitative findings

- Polarization degree is about two times higher in gaps than in rings  
  > "The polarization degree is two times higher in the gap regions than that in ring regions." (Results)

## Claim tuples

- H: Self-scattering can explain HL Tau mm polarization | E: RADMC-3D models of a gapped disk | R: Vector direction and degree reproduced for amax ~150 um | F: Self-scattering is a viable explanation and constrains amax to 70-270 um | **supported**
- H: Polarization grain size is consistent with that from the opacity index | E: Compared with beta-based sizes | R: beta implies mm-cm sizes, much larger than 150 um | F: Inconsistent for compact spheres; porous aggregates may reconcile | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: amax = 350 um ruled out since it underestimates SMA 0.89 mm polarization  
  > "Therefore, we can rule out the possibility of $a_{\rm max} = 350{\rm~\mu m}$ to explain the polarization." (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk model is not a unique solution  
  > "This model is not a unique solution of the density and temperature of the HL Tau disk." (Method)
- Caveat (inferred, ours): Single disk model; no formal fit or uncertainty on amax
- Caveat (inferred, ours): Grain alignment not excluded
- Caveat (inferred, ours): Spherical grain assumption drives upper limit
- Caveat (inferred, ours): Composition fixed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Observed polarization data from Stephens et al. 2014
- Missing: RADMC-3D setup details
- Missing: Opacity mixture fractions
- Data volume (inferred): small; only the ALMA continuum profile is used, simulations are modest
- Score (inferred): 3/5, Model parameters are tabulated but RT settings and compositions are missing.
- Rediscovery candidate: no, The result is a model comparison to literature polarization values, not a numeric data reduction from public ALMA data.

## Links

- Method: Kataoka et al. 2015 (cite: Kataoka15) (Self-scattering polarization formula and calibration)
- Companion: Yang et al. 2015 (cite: Yang15) (Independent scattering interpretation of HL Tau polarization)
- Related: ALMA HL Tau Long Baseline Campaign

## Checks

```json
{
 "quotes": 33,
 "quotes_ok": 33,
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
  "facts": 68,
  "stated": 25,
  "rate": 0.368
 },
 "evidence_ok": true
}
```
