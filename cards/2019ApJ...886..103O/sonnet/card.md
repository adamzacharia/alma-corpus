# Radial Variations in Grain Sizes and Dust Scale Heights in the Protoplanetary Disk around HD 163296 Revealed by ALMA Polarization Observations

`2019ApJ...886..103O` | The Astrophysical Journal 2019 | first author: Ohashi, Satoshi | arXiv: 1910.12868 | DOI: 10.3847/1538-4357/ab5107

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What grain sizes and dust scale heights, as a function of radius, reproduce the resolved 0.87 mm self-scattering polarization of the HD 163296 disk, and what do they imply for turbulence?  
  > "we conduct radiative transfer modeling that includes self-scattering polarization to constrain the grain size and its distribution." (abstract)
- Target **HD 163296**: coordinates _not stated_; z/distance 101.5 pc  
  > "The distance was derived to be 101.5 pc by (cite: gai18; bai18)." (1 Introduction); distance from Gaia (gai18; bai18)  
  > "The distance was derived to be 101.5 pc by (cite: gai18; bai18)." (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00616.S
- bands: 0.87 mm (Band 7) dust polarization  
  > "We used the archival data of the 0.87 mm dust polarization from the protoplanetary disk around HD 163296" (2.1 Analysis of Archival Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.20" x 0.18" (~20x18 au)  
  > "The beam size of the final product was $0.20\ensuremath{''}\times0.18\ensuremath{''}$, corresponding to a spatial resolution of $\sim20\times18$ au" (2.1 Analysis of Archival Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival, PI C. Pinte; originally presented by Dent et al. 2019  
  > "These data were originally presented by (cite: den19)." (2.1 Analysis of Archival Data)
- External data: Temperature profile T=220 K (R/1au)^-0.5  
  > "We adopted the following temperature profile with a smooth power law distribution derived by (cite: ise16)" (3 Disk Model) [from (cite: ise16)]
- External data: Inclination 47 deg and position angle 133.3 deg from DSHARP  
  > "The inclination and position angle were assumed to be $47^\circ$ and 133.3$^\circ$, respectively, as derived by the DSHARP project (cite: ise18)." (3 Disk Model) [from (cite: ise18)]
- External data: Gas surface density 3-10 g cm^-2 in 50 au gap and 0.1-2 g cm^-2 in 90 au gap from CO lines  
  > "The gas surface density has been constrained by multiple CO line observations to be $3-10 {\rm~g~cm^{-2}}$ in the 50 au gap and $0.1-2 {\rm~g~cm^{-2}}$ in the 90 au gap (cite: ise16)." (6.2 Estimate of turbulence strength) [from (cite: ise16)]
- External data: Spectral index from 0.87 and 1.3 mm continuum  
  > "(cite: den19) derived the spectral index, $\alpha$, using the ALMA 0.87 and 1.3 mm dust continuum observations" (6.1 Distributions of dust grains) [from (cite: den19)]

## Processing

### Calibration

- pipeline or manual: Standard manual-style reduction in CASA, plus phase and amplitude self-calibration  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2.1 Analysis of Archival Data)
- casa version: CASA 4.5.3  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2.1 Analysis of Archival Data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Phase and amplitude self-calibration performed  
  > "self-calibration for both phase and amplitude was performed." (2.1 Analysis of Archival Data)

### Imaging

- task: CASA tclean  
  > "Stokes images were reconstructed using the CASA task tCLEAN, with Briggs weighting with a robust parameter of 0.5." (2.1 Analysis of Archival Data)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "Stokes images were reconstructed using the CASA task tCLEAN, with Briggs weighting with a robust parameter of 0.5." (2.1 Analysis of Archival Data)
- uv taper: _not stated_
- cell size: 0.02 arcsec  
  > "The pixel size was set to $0.02\ensuremath{''}$." (2.1 Analysis of Archival Data)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.20" x 0.18"  
  > "The beam size of the final product was $0.20\ensuremath{''}\times0.18\ensuremath{''}$" (2.1 Analysis of Archival Data)
- final rms: sigma_Q=1.7e-5, sigma_U=3.0e-5, sigma_PI=4.0e-5 Jy/beam  
  > "$\sigma_{\it Q}=1.7\times10^{-5}$ Jy beam$^{-1}$, $\sigma_{\it U}=3.0\times10^{-5}$ Jy beam$^{-1}$, and $\sigma_{\rm PI}=4.0\times10^{-5}$ Jy beam$^{-1}$" (2.1 Analysis of Archival Data)

### Inherited from earlier work

- Opacity calculation follows Kataoka et al. 2016  
  > "The calculation of opacity followed that by (cite: kat16)." (3 Disk Model) [from (cite: kat16)]
- Multiple scattering in RADMC-3D as done by Kataoka et al. 2015  
  > "taking into account multiple scattering, as done by (cite: kat15)" (3 Disk Model) [from (cite: kat15)]
- Further flagging and calibration details in Dent et al. 2019  
  > "Note that (cite: den19) examined the calibrated data in more detail, and applied further flagging." (2.1 Analysis of Archival Data) [from (cite: den19)]

### Not stated but needed to reproduce (our reading)

- Observing dates, configurations, baselines, spectral setup and on-source time
- Self-calibration solution intervals and reference images
- Flagging details, calibrators and flux scale uncertainty
- Deconvolution settings (masking, threshold, niter) and image size
- RADMC-3D photon numbers, grid setup, stellar parameters and gas scale height/temperature setup
- Method of extracting radial profiles along major and minor axes and how model-data agreement was judged
- Minimum grain size for the two-population model and gas-to-dust ratio

## Analysis recipe

1. **Image Stokes I, Q, U and build polarization fraction map**: tclean imaging of archival data, debiased PI, Pfrac=PI/I above 3 sigma_PI  
  > "We thus debiased the polarized intensity map as $PI=\sqrt{Q^2+U^2-\sigma_{\rm PI}^2}$." (2.1 Analysis of Archival Data)
   - software: CASA
   - parameter: robust 0.5, 0.02" pixels  
  > "The pixel size was set to $0.02\ensuremath{''}$." (2.1 Analysis of Archival Data)
   - assumption: Stokes V ignored  
  > "Note that we ignore the Stokes *V* component in this study because it has not been well characterized for ALMA." (2.1 Analysis of Archival Data)
   - fitting: _not stated_
   - validation: Compared with Dent et al. 2019 images  
  > "These images are consistent with those obtained by (cite: den19)." (2.2 Results)
2. **Build axisymmetric dust disk model reproducing continuum**: Optical depth profile with ring Gaussians at 70, 104, 160 au; I=(1-e^-tau)B(Td); Sigma_dust=tau/kappa_abs  
  > "The surface density is derived with the assumption that $\tau=\kappa_{\rm abs}\times\Sigma_{\rm dust}$" (3 Disk Model)
   - parameter: Td=220 K (R/1au)^-0.5  
  > "$$\begin{equation}
T_{d}= 220\ {\rm K}\ \Big(\frac{R}{1\ {\rm au}}\Big)^{-0.5}. 
\label{temp}
\end{equation}$$" (3 Disk Model)
   - assumption: Spherical grains, q=-3.5, Mie theory, 50% silicate / 50% water ice, Maxwell-Garnett mixing  
  > "The composition was assumed to be a mixture of silicate (50%) and water ice (50%)" (3 Disk Model)
   - fitting: _not stated_
   - validation: Model intensity profile on major axis compared to data  
  > "The figure confirms that the model reproduces the continuum image." (3 Disk Model)
3. **Radiative transfer of self-scattering polarization**: RADMC-3D with multiple scattering; Stokes I,Q,U convolved with 0.2" Gaussian beam  
  > "The Stokes *I*, *Q*, and *U* images were convolved with a Gaussian beam with a full width at half maximum (FWHM) of $0.2\ensuremath{''}$ to produce the final model images." (3 Disk Model)
   - software: RADMC-3D
   - parameter: inclination 47 deg, PA 133.3 deg  
  > "The inclination and position angle were assumed to be $47^\circ$ and 133.3$^\circ$, respectively" (3 Disk Model)
   - assumption: Gaussian vertical distribution with h_d=h_g/f_set; polarization only from self-scattering  
  > "We set an additional dust settling parameter $f_{\rm set}$ such that $h_d=h_g/f_{\rm set}$" (3 Disk Model)
   - fitting: _not stated_
   - validation: Compared radial Pfrac profiles along axes and Stokes Q/U maps  
  > "We compare the images not only for the polarization fraction but also for the Stokes *Q* and *U* distributions." (5.4 Radial variation of dust scale height)
4. **Constrain grain populations and dust scale height by radius**: Single population then two populations (140 um and 1 mm); Stokes Q upper limit sets H_dust; best: f_set=10 for r<=68 au, 1.5 beyond  
  > "To reproduce the observations, we apply $f_{\rm set}=10$ within $r\leq68$ au and $f_{\rm set}=1.5$ for $r>68$ au." (5.4 Radial variation of dust scale height)
   - software: RADMC-3D
   - parameter: 1 mm grains within +-5 au of ring centers; 5.5:4.5 mixture at r<=40 au  
  > "We set a ratio of surface density (and density) of $5.5:4.5$ (corresponding to a ratio of $11/9$) between the 140 $\mu$m and 1 mm dust grain populations" (5.2 Model with Two Dust Grain Populations)
   - fitting: _not stated_
   - validation: Single-population model with variable f_set fails to reproduce Q  
  > "Therefore, a model with a single grain population is unlikely to explain the observations even if the dust scale height is changed." (8 Additional Test of Model with Single Grain Population)
5. **Derive turbulence alpha in gaps**: Settling-diffusion balance H_dust formula with Stokes number from gas surface density  
  > "By assuming a balance between vertical settling and turbulent diffusion, the dust scale height is written as (cite: dub95; you07)" (6.2 Estimate of turbulence strength)
   - assumption: Dust material density 1.67 g cm^-3; CO abundance 5e-5 for gas surface density  
  > "assuming that the dust material density is $\rho\sim1.67$ g cm$^{-3}$" (6.2 Estimate of turbulence strength)
   - fitting: _not stated_
   - validation: Compared with molecular-line turbulence limits  
  > "The low value of $\alpha\lesssim1.5\times10^{-3}$ inside the 70 au ring is consistent with the upper limit derived from molecular line observations" (6.2 Estimate of turbulence strength)

## Software

- **CASA** 4.5.3: Calibration and tclean imaging  
  > "The reduction and calibration of the data were done with CASA version 4.5.3 (cite: mcm07) in a standard manner." (2.1 Analysis of Archival Data)
- **RADMC-3D** : Radiative transfer including scattering polarization  
  > "We performed radiative transfer calculations with RADMC-3D[^1] (cite: dul12) taking into account multiple scattering" (3 Disk Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Polarization fraction at center | ~0.8 | 0.04 | % | 1 | The polarization fraction is $\sim0.8\pm0.04$% in the center |
| Polarization fraction in 50 au gap | ~2.3 | 0.5 | % | 1 | increases to $\sim2.3\pm0.5$% in the first gap at 50 au |
| Polarization fraction in 90 au gap | ~3 | 0.7 | % | 1 | to $\sim3\pm0.7$% in the second gap at 90 au along the major axis |
| Maximum grain size in gaps | 140 | not stated | micron | 4 | The maximum grain size was 140 microns in the gaps and significantly larger or smaller in the rings. |
| H_dust/H_gas inside 70 au ring | <~1/3 | 3 sigma upper limit | dimensionless | 4 | we can set the upper limit of the dust scale height as $H_{\rm dust}\lesssim (1/3)H_{\rm gas}$ |
| H_dust/H_gas outside 70 au ring | ~2/3 | not stated | dimensionless | 4 | $H_{\rm dust}/H_{\rm gas}\sim2/3$ for the $r\gtrsim 70$ au region |
| alpha in 50 au gap | <=1.5e-3 | upper limit | dimensionless | 5 | $\alpha\lesssim 1.5\times10^{-3}$ in the 50 au gap |
| alpha in 90 au gap | 0.015-0.3 | range | dimensionless | 5 | $\alpha\simeq0.015-0.3$ in the 90 au gap |
| St/alpha outside 70 au ring | 1.25 | not stated | dimensionless | 5 | ${\rm St}/\alpha \gtrsim 8$ inside the 70 au ring and ${\rm St}/\alpha \simeq 1.25$ outside the 70 au ring |

## Qualitative findings

- Dust scale height raises azimuthal polarization variation; grain size mainly sets polarization fraction and does not alter vectors.  
  > "We can thus conclude that the grain size only affects the polarization fraction; it does not affect the polarization vectors in self-scattering." (4.2 Dust Grain Size and Dust Scale Height Distribution)
- Turbulence transition at 70 au ring suggests a dead zone or e-heating zone.  
  > "The transition of the turbulence strength at the boundary of the 70 au ring indicates the existence of a dead zone." (abstract)

## Claim tuples

- H: Can a single grain population with constant settling reproduce the polarization? | E: Radiative transfer with a_max=140 and 160 um and f_set 1-10 | R: Minor-axis Pfrac too high and Stokes Q mismatch | F: A single radially constant population cannot reproduce observations | **supported**
- H: Do grain size and dust scale height vary radially? | E: Two-population model with 140 um in gaps, 1 mm in rings, f_set 10 inside and 1.5 outside 68 au | R: Model matches Pfrac, Q and U images | F: Gaps host ~140 um grains; dust is thinner inside 70 au than outside | **supported**
- H: Is turbulence different inside and outside the 70 au ring? | E: Convert H_dust/H_gas and gap grain size into alpha | R: alpha <=1.5e-3 vs 0.015-0.3 | F: Order-of-magnitude turbulence difference, suggesting a dead zone | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Radiative transfer needed to interpret resolved self-scattering polarization in terms of dust properties.  
  > "In this study, we perform radiative transfer modeling to determine what can be constrained based on spatially resolved polarimetric observations." (1 Introduction)
- Alternative: Single grain population with varied scale height rejected; larger or smaller grains instead of the mixture considered possible (~170 or ~80 um).  
  > "Note that it is also possible to explain the lower polarization fraction by assuming a slightly larger ($\sim170$ $\mu$m) or smaller dust grain size ($\sim80$ $\mu$m)" (5.2 Model with Two Dust Grain Populations)
- How they decided it was enough: _not stated_
- Limitation (authors): Polarization assumed to be only self-scattering; alignment contributions could change the interpretation.  
  > "Another caveat is that the polarization is assumed to be produced only by self-scattering." (6.4 Caveats of models)
- Limitation (authors): Grain size in rings is not constrained beyond being far from 140 um.  
  > "it is possible that dust grains much larger or smaller than 140 $\mu$m are distributed in the rings rather than the 1 mm dust grain population." (6.4 Caveats of models)
- Caveat (inferred, ours): Model comparison is qualitative with no formal fit or uncertainties on grain size and f_set
- Caveat (inferred, ours): Results depend on assumed composition, opacity and fixed temperature profile
- Caveat (inferred, ours): Alpha estimates rely on uncertain CO-based gas surface densities
- Caveat (inferred, ours): Self-scattering only; alignment effects not tested

## Reproducibility

- Data public (paper): Archival ALMA data, project 2015.1.00616.S  
  > "We used the archival data of the 0.87 mm dust polarization from the protoplanetary disk around HD 163296 (2015.1.00616.S; PI: C. Pinte)." (2.1 Analysis of Archival Data)
- Products in archive: _not stated_
- Missing: Self-calibration parameters and flagging
- Missing: RADMC-3D setup details (grid, photons, stellar parameters)
- Missing: Profile extraction and comparison procedure
- Data volume (inferred): ~50-150 GB raw for a polarization Band 7 dataset
- Score (inferred): 3/5, Public data and a clear model description, but imaging, self-calibration and RADMC-3D setup are incomplete, and the model comparison is not quantitative.
- Rediscovery candidate: no, Main results come from hand-tuned forward models that are compared qualitatively, so they cannot be redone from a complete recipe.

## Links

- Method: (cite: kat16) (Opacity and self-scattering polarization modeling)
- Method: (cite: kat15) (RADMC-3D multiple-scattering polarization approach)
- Companion: (cite: den19) (Original presentation of the ALMA polarization data)
- Companion: (cite: ise18) (DSHARP HD 163296 geometry and ring structure)
- Related: DSHARP

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
 "numeric_results": 9,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 48,
  "rate": 0.6
 },
 "evidence_ok": true
}
```
