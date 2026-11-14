# Modeling of the ALMA HL Tau Polarization by Mixture of Grain Alignment and Self-scattering

`2021ApJ...908..153M` | The Astrophysical Journal 2021 | first author: Mori, Tomohiro | arXiv: 2012.01735 | DOI: 10.3847/1538-4357/abd08a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can a mixture of grain-alignment-induced polarization and self-scattering-induced polarization reproduce the ALMA 3.1 mm polarization of the HL Tau disk, and what does it imply for grain size and shape?  
  > "To quantitatively address the origin, we perform radiative transfer calculations of the mixture of alignment and self-scattering induced polarization to reproduce the 3.1 mm polarization of the HL Tau disk" (abstract)
- Target **HL Tau**: coordinates _not stated_; z/distance 140 pc  
  > "HL Tau is a class I/II protostar in the Taurus star-forming complex at a distance of 140 pc from the solar system" (Introduction); distance from (cite: rebull2004; robitaille2007)  
  > "HL Tau is a class I/II protostar in the Taurus star-forming complex at a distance of 140 pc from the solar system" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 3 (3.1 mm) polarization data (Stokes I, polarized intensity, polarization fraction)  
  > "previous studies have assumed that the Band 7 (0.87 mm) polarization is dominated by self-scattering while the Band 3 (3.1 mm) has no contribution of self-scattering" (6.2 How Efficient is the Scattering at 3.1 mm?); "We construct an axisymmetric disk model that reproduces the stokes I image obtained on the polarization observation at 3.1 mm" (2.1 Disk Model)
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
- pi or archival as stated: Analyzed ALMA Band 3 polarization data provided by I. Stephens (earlier published data, cite: kataoka2017; stephens2017)  
  > "We gratefully thank Ian Stephens for providing us the analyzed ALMA Band 3 polarization data, which has enabled us to conduct the modeling work." (Acknowledgments)
- External data: Observed Band 3 Stokes I image and polarization morphology of HL Tau at 3.1 mm used as the modeling target  
  > "We construct an axisymmetric disk model that reproduces the stokes I image obtained on the polarization observation at 3.1 mm" (2.1 Disk Model) [from (cite: kataoka2017; stephens2017)]
- External data: Temperature profile T(r) = 310 (r/1 AU)^-0.57 K  
  > "with the temperature profile of $\rm T(r) = 310 (r/1 AU)^{-0.57}$ K" (2.1 Disk Model) [from (cite: okuzumi2019)]
- External data: Grain composition model: mixture of silicate, troilite, organics and water ice  
  > "where the grains are the mixture of silicate, troilite, organics, and water ice" (2.2 Dust Model) [from (cite: birnstiel2018)]
- External data: Refractive indices: astronomical silicate, troilite and refractory organics, water ice  
  > "(cite: draine2003) for astronomical silicate, (cite: henning1996) for troilite and refractory organics, and (cite: warren2008) for water ice" (2.2 Dust Model) [from (cite: draine2003); (cite: henning1996); (cite: warren2008)]
- External data: Power-law grain size distribution with q = -3.5  
  > "We assume the grains have a power-law-size distribution with a power of $q$ = -3.5 (cite: mathis1977)" (2.2 Dust Model) [from (cite: mathis1977)]
- External data: Observed total polarization fractions at 1.3 mm and 0.87 mm updated with ALMA Band 6 and 7 data; 3.1 mm upper limit taken unchanged from earlier study  
  > "who used the SMA and CARMA data, with the ALMA data in Band 6 and 7 while its upper limit in ALMA 3 is presented the same as that study" (6.2 How Efficient is the Scattering at 3.1 mm?) [from (cite: kataoka2017)]
- Simulation/model as data: RADMC-3D radiative transfer models of an axisymmetric HL Tau disk with prolate or oblate aligned grains plus self-scattering, at i = 0, 45 and 60 deg and a_max = 50 to 200 um  
  > "The radiative transfer code RADMC-3D allows users to compute the alignment-induced polarization only when the dust scattering is turned on." (2.2 Dust Model)

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

- Stokes I image of the 3.1 mm polarization observation is the target of the disk model  
  > "We construct an axisymmetric disk model that reproduces the stokes I image obtained on the polarization observation at 3.1 mm" (2.1 Disk Model) [from (cite: kataoka2017; stephens2017)]
- Total polarization fraction estimated across the disk following earlier work  
  > "To estimate the scattering component at each wavelength, as conducted in (cite: kataoka2017), we compute the total polarization across the HL Tau disk" (6.2 How Efficient is the Scattering at 3.1 mm?) [from (cite: kataoka2017)]
- Temperature profile of the disk  
  > "with the temperature profile of $\rm T(r) = 310 (r/1 AU)^{-0.57}$ K" (2.1 Disk Model) [from (cite: okuzumi2019)]
- Grain composition model  
  > "We use a grain composition model developed by (cite: birnstiel2018)" (2.2 Dust Model) [from (cite: birnstiel2018)]

### Not stated but needed to reproduce (our reading)

- The observed Stokes I/Q/U images were supplied privately by a coauthor of earlier work; observing setup, beam size, rms and calibration of the Band 3 data are not given
- Disk inclination and position angle adopted for HL Tau (only 0, 45 and 60 deg test cases are described)
- Dust scale height or aspect ratio h_d/r and the gas pressure scale height prescription (stellar mass, gas temperature)
- Stellar luminosity or heating source, photon count, grid size and resolution, RADMC-3D version and settings
- How the model images were convolved to the observed beam, and the beam used
- How the tau profile parameters were obtained (fit method) and the fit region
- Definition of alignment efficiency and how it enters the RADMC-3D alignment setup
- Procedure and masking used to integrate Stokes I, Q, U over the disk for PF_total, and Band 6/7 data processing behind the 0.551 and 0.619 percent values

## Analysis recipe

1. **build axisymmetric Stokes I disk model at 3.1 mm**: Optical depth profile tau(r) with four parameters adopted to reproduce the observed 3.1 mm Stokes I image; smooth disk with no rings or gaps  
  > "By assuming that the Stokes I emission at 3.1 mm is optically thin, we construct the radial profile of the optical depth at 3.1 mm" (2.1 Disk Model); "We adopt the parameter set of ($\rm \tau_0, r_c, \gamma_1, \gamma_2$) = (1.0, 129.2, 6.6, 9.0), which reproduces the Stokes I emission." (2.1 Disk Model)
   - parameter: (tau_0, r_c, gamma_1, gamma_2) = (1.0, 129.2, 6.6, 9.0)  
  > "We adopt the parameter set of ($\rm \tau_0, r_c, \gamma_1, \gamma_2$) = (1.0, 129.2, 6.6, 9.0), which reproduces the Stokes I emission." (2.1 Disk Model)
   - assumption: Stokes I optically thin at 3.1 mm; T(r) = 310 (r/1 AU)^-0.57 K  
  > "By assuming that the Stokes I emission at 3.1 mm is optically thin, we construct the radial profile of the optical depth at 3.1 mm" (2.1 Disk Model); "with the temperature profile of $\rm T(r) = 310 (r/1 AU)^{-0.57}$ K" (2.1 Disk Model)
   - assumption: Smooth radial distributions without rings and gaps, for simplicity  
  > "We note that both the dust surface density and temperature are assumed to have smooth radial distributions without any ring and gap structures observed with the higher spatial resolution" (2.1 Disk Model)
   - fitting: _not stated_
   - validation: Observed, modeled and residual Stokes I compared; residuals significant but axisymmetric, parameters not searched further  
  > "While the residuals are still significant, they show axisymmetric distribution." (2.1 Disk Model)
2. **convert optical depth to dust surface density and vertical structure**: Sigma_d = tau_model / kappa_abs with kappa_abs(a_max = 100 um, 3.1 mm) = 0.0788 cm2/g; Gaussian vertical profile with h_d equal to the gas pressure scale height  
  > "We derive the dust surface density profile $\rm \Sigma_d (r)$ by calculating $\rm \Sigma_d (r)$ = $\rm \tau_{model}/\kappa_{abs}$, where $\rm \kappa_{abs}$ is the absorption opacity." (2.1 Disk Model); "We also assume that $h_d$ is same as the gas pressure scale height." (2.1 Disk Model)
   - parameter: kappa_abs(a_max = 100 um, lambda = 3.1 mm) = 0.0788 cm2 g-1  
  > "we adopt $\rm \kappa_{abs}(a_{max} = 100 \: \ensuremath{\mu}m, \lambda = 3.1 \: mm)$ = 0.0788 cm$^2$ g$^{-1}$ in calculating the dust surface density" (2.1 Disk Model)
   - assumption: Gaussian vertical dust density with scale height h_d  
  > "The vertical dust density is assumed to be Gaussian density distribution with a dust scale height $h_d$" (2.1 Disk Model)
   - fitting: _not stated_
   - validation: _not stated_
3. **set dust and alignment model**: Mixed-composition grains with Maxwell-Garnett mixing, power-law size distribution, Rayleigh-regime intrinsic polarization for prolate (alpha = 0.9) or oblate (alpha = 1.1) grains, alignment efficiency 0.6; prolate aligned azimuthally, oblate with short axis radial  
  > "We compute the mixture of them with the effective medium theory using the Maxwell-Garnett rule" (2.2 Dust Model); "We assume the axes ratio of the grains to be $\alpha = 0.9$ for prolate grains and $\alpha = 1.1$ for oblate grains and that the alignment efficiency to be $\epsilon=0.6$." (2.2 Dust Model)
   - parameter: q = -3.5, a_min = 0.05 um, a_max varied  
  > "We assume the grains have a power-law-size distribution with a power of $q$ = -3.5 (cite: mathis1977) with the maximum grain size of $a_{max}$, while the minimum grain size is fixed at $a_{min}$ = 0.05 $\mu$m." (2.2 Dust Model)
   - assumption: Rayleigh regime (size parameter x = 0.42 for 200 um at 3.1 mm); same grain population throughout the disk; temperature effects ignored  
  > "We assume the grain size up to 200 $\ensuremath{\mu}m$ at the wavelength of 3.1 mm, which corresponds to the size parameter of $x=0.42$, which justifies the use of Rayleigh regime." (2.2 Dust Model); "We assume the same grain population throughout the disk." (2.2 Dust Model)
   - assumption: Spherical grains used for scattering; angle-averaged absorption opacity of oblate/prolate grains equal to spherical grains  
  > "The angle-averaged absorption opacity of oblate/prolate grains is set to be the same as the spherical grains." (2.2 Dust Model)
   - fitting: _not stated_
   - validation: _not stated_
4. **alignment-only radiative transfer models at several inclinations**: RADMC-3D with scattering turned on at a_max = 50 um so that scattering polarization is negligible; disk viewed at i = 0, 45 and 60 deg; effect of beam dilution examined  
  > "we use $a_{max}$ = 50 $\mu$m with the scattering turned on, where the scattering-induced polarization is negligible" (2.2 Dust Model); "We use the same disk model of HL Tau but assume that the disk is observed with a face-on view, $i=0^\circ$." (3.1 Alignment-only Model)
   - software: RADMC-3D
   - parameter: inclinations 0, 45 and 60 deg  
  > "The polarization vectors are almost in the azimuthal directions in the inclination angles of 45$^\circ$ and 60$^\circ$ for both the prolate and oblate grains" (3.1 Alignment-only Model)
   - fitting: _not stated_
   - validation: Compared qualitatively with the observed polarized intensity and polarization fraction images  
  > "This illustrates that alignment-only models may not be able to reproduce the observed polarized intensity pattern." (3.1 Alignment-only Model)
5. **mixture of alignment and self-scattering models**: Scattering switched on with full phase function and multiple scattering; a_max varied (100, 130, 200 um) at i = 45 deg to change the self-scattering contribution while alignment is fixed  
  > "We treat the full phase function and take into account the multiple scattering." (2.2 Dust Model); "The contributions of the self-scattering model increases by increasing $a_{max}$ from left to right panels while that of the alignment models are fixed." (3.2 Mixture of Alignment and Scattering Models)
   - software: RADMC-3D
   - parameter: a_max = 100, 130, 200 um; i = 45 deg  
  > "The top three panels of Figure [4](#fig:HLTau_main_PI) show the case of different grain sizes, which corresponds to difference of contribution of self-scattering." (3.2 Mixture of Alignment and Scattering Models)
   - fitting: _not stated_
   - validation: Best model chosen by visual comparison of polarized intensity azimuthal variation and polarization fraction with the observation  
  > "The $a_{max}$ = 130 $\mu$m case shows the half and half contributions between alignment and scattering, which reproduce little azimuthal variation as observed." (3.2 Mixture of Alignment and Scattering Models)
6. **decompose total polarization fraction into scattering and alignment components**: Compute signed PF_total from integrated Stokes Q, U, I of the whole disk (positive along minor axis, negative along major axis) for models and observations; compare with observed 3.1, 1.3 and 0.87 mm values  
  > "where $\Sigma$I, $\Sigma$Q, and $\Sigma$U are the Stokes I, Q, and U emissions integrated for the whole disk." (6.2 How Efficient is the Scattering at 3.1 mm?); "As shown in the table [1](#tab:scattering_contributions), the total polarization fraction is nearly equal to the sum of those of the scattering and alignment components." (6.2 How Efficient is the Scattering at 3.1 mm?)
   - assumption: No alignment contribution at Bands 6 and 7; wavelength dependence of alignment polarization unknown  
  > "we emphasize our big assumption that we do not know the wavelength dependency of the alignment-induced polarization, and assume that there is no contribution from alignment polarization at the wavelengths of the Band 6 and 7" (6.2 How Efficient is the Scattering at 3.1 mm?)
   - fitting: _not stated_
   - validation: Model PF_total compared with the observed 3.1 mm upper limit and the observed total polarization at 1.3 and 0.87 mm  
  > "To reproduce the tight upper limit on the absolute value of the total polarization fraction to be less than 0.1 %, the oblate grain model is not favored and the combination of the prolate model and self-scattering is the key." (6.2 How Efficient is the Scattering at 3.1 mm?)

## Software

- **RADMC-3D** : Radiative transfer including scattering and alignment-induced polarization  
  > "The radiative transfer code RADMC-3D allows users to compute the alignment-induced polarization only when the dust scattering is turned on." (2.2 Dust Model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I disk model parameters (tau_0, r_c, gamma_1, gamma_2) | (1.0, 129.2, 6.6, 9.0) | not stated | tau_0 dimensionless; r_c in au; gamma_1 and gamma_2 dimensionless | 1 | We adopt the parameter set of ($\rm \tau_0, r_c, \gamma_1, \gamma_2$) = (1.0, 129.2, 6.6, 9.0), which reproduces the Stokes I emission. |
| Absorption opacity at a_max = 100 um, 3.1 mm | 0.0788 | not stated | cm2 g-1 | 2 | we adopt $\rm \kappa_{abs}(a_{max} = 100 \: \ensuremath{\mu}m, \lambda = 3.1 \: mm)$ = 0.0788 cm$^2$ g$^{-1}$ in calculating the dust surface density |
| Best-fitting maximum grain size (prolate + scattering) | 130 | not stated | um | 5 | Therefore, we conclude that prolate + scattering model with $a_{max}$ = 130 $\mu$m best reproduces the observed HL Tau polarization at 3.1 mm. |
| PF_align, prolate model at 3.1 mm | -0.55 | not stated | percent | 6 | prolate / 3.1 / -0.55 / 0 / -0.55 |
| PF_align, oblate model at 3.1 mm | 1.07 | not stated | percent | 6 | oblate / 3.1 / 1.07 / 0 / 1.07 |
| PF_scat for a_max = 130 um at 3.1 mm | 0.42 | not stated | percent | 6 | our study revealed that the non-detection of total polarization at 3.1 mm is explained by the combination of the alignment (-0.55 %) and the self-scattering ($+0.42$ %) |
| PF_total, prolate + scattering (a_max = 130 um), 3.1 mm | -0.12 | not stated | percent | 6 | prolate + scattering ($a_{max}$ = 130 $\ensuremath{\mu}m$) / 3.1 / -0.12 / 0.42 / -0.55 |
| PF_total, prolate + scattering (a_max = 100 um), 3.1 mm | -0.35 | not stated | percent | 6 | prolate + scattering ($a_{max}$ = 100 $\ensuremath{\mu}m$) / 3.1 / -0.35 / 0.20 / -0.55 |
| PF_total, prolate + scattering (a_max = 200 um), 3.1 mm | 0.68 | not stated | percent | 6 | prolate + scattering ($a_{max}$ = 200 $\ensuremath{\mu}m$) / 3.1 / 0.68 / 1.21 / -0.55 |
| Observed total polarization fraction at 1.3 mm | 0.551 | 0.003 | percent | 6 | observation / 1.3 / $0.551 \pm 0.003$ |
| Observed total polarization fraction at 0.87 mm | 0.619 | 0.004 | percent | 6 | observation / 0.87 / $0.619 \pm 0.004$ |
| Stokes number of a_max = 130 um grains | 5e-3 (for Sigma_g ~ 20 g cm-2) | not stated | dimensionless | 0 | which gives the Stokes number to be St = 5 $\times$ 10$^{-3}$ with the assumption of the gas surface density of $\rm \Sigma_g$ $\sim$ 20 g cm$^{-2}$ |

## Qualitative findings

- Alignment-only models predict azimuthal variation in polarized intensity that the observed HL Tau 3.1 mm image lacks  
  > "This illustrates that alignment-only models may not be able to reproduce the observed polarized intensity pattern." (3.1 Alignment-only Model)
- Effectively prolate grains plus self-scattering reproduce the observations; oblate plus scattering does not  
  > "However, the combination of the effectively oblate grain emission and self-scattering cannot reproduce the polarization." (Conclusions)
- Self-scattering contributes even at 3.1 mm, but less than at 0.87 and 1.3 mm, so the decreasing trend with wavelength still holds  
  > "This means that the decreasing trend of the self-scattering polarization still holds" (6.2 How Efficient is the Scattering at 3.1 mm?)

## Claim tuples

- H: Alignment-induced polarization alone explains the HL Tau 3.1 mm polarization | E: Alignment-only RADMC-3D models with prolate and oblate grains at i = 0, 45 and 60 deg | R: Prolate models are brighter along the minor axis and oblate along the major axis, unlike the observed azimuthally uniform polarized intensity | F: Alignment alone cannot reproduce the observed polarized intensity pattern | **refuted**
- H: A mixture of alignment and self-scattering reproduces the 3.1 mm polarization | E: Prolate and oblate alignment models with added self-scattering at a_max = 100, 130, 200 um | R: Prolate + scattering at a_max = 130 um gives little azimuthal variation and a ~1-2 percent uniform polarization fraction; PF_align -0.55 and PF_scat +0.42 percent | F: A mixture of alignment (parallel to the major axis) and self-scattering (parallel to the minor axis) is needed | **supported**
- H: Effectively oblate grains plus self-scattering can explain the observations | E: Oblate + scattering models for a_max = 100, 130, 200 um | R: Both oblate alignment and self-scattering strengthen polarization along the major axis, increasing azimuthal variation | F: Oblate + scattering is rejected and effectively prolate grains are preferred | **refuted**
- H: Including self-scattering at 3.1 mm changes the grain-size constraint of about 70 um from earlier studies | E: Decompose total polarization fraction into scattering and alignment components and compare with 0.87 and 1.3 mm totals | R: a_max about 130 um; scattering component at 3.1 mm (0.42 percent) is below the 0.87 and 1.3 mm totals; still a few times smaller than multi-wavelength continuum sizes | F: The tight grain size constraint is slightly eased but grains remain around 100 um, in tension with SED-based sizes; further modeling needed | **partially**

## Reasoning

- Why this data: HL Tau 3.1 mm polarization was interpreted as pure alignment but also suspected to be contaminated by self-scattering  
  > "which has been interpreted purely as alignment-induced polarization (cite: kataoka2017), but also pointed out to be contaminated by self-scattering (cite: yang2019)" (Introduction)
- Why this method: Investigate the superposition of the two major polarization mechanisms with radiative transfer  
  > "we investigate the effects of superposition of the two major polarization mechanisms, which are the self-scattering and alignment" (Introduction)
- Alternative: Effectively oblate grains (with and without scattering) were rejected as the alignment shape; Mie-regime treatment and multiband modeling were left for future work  
  > "However, the combination of the effectively oblate grain emission and self-scattering cannot reproduce the polarization." (Conclusions); "In this paper, however, we do not treat the Mie regime for simplicity and we focus on the single band observations on the HL Tau at 3.1 mm." (2.2 Dust Model)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk model is axisymmetric with no rings or gaps, and residuals against the observed Stokes I are significant  
  > "While the residuals are still significant, they show axisymmetric distribution." (2.1 Disk Model)
- Limitation (authors): Dust models for alignment (non-spherical) and scattering (spherical) are not self-consistent  
  > "the dust models are not fully consistent between the alignment and scattering models" (Caveats)
- Limitation (authors): Wavelength dependence of alignment polarization unknown; Mie regime not computed  
  > "we emphasize our big assumption that we do not know the wavelength dependency of the alignment-induced polarization" (6.2 How Efficient is the Scattering at 3.1 mm?)
- Limitation (authors): No physical mechanism for effectively prolate grains in protoplanetary disks is identified  
  > "the grain alignment model requires effectively prolate grains but the physics to reproduce it in protoplanetary disks is still a mystery" (abstract)
- Caveat (inferred, ours): Best model chosen by visual comparison of polarized intensity images; no quantitative fit statistic or uncertainty on a_max
- Caveat (inferred, ours): Only a few a_max values (100, 130, 200 um) sampled; 130 um is a grid point, not a fit
- Caveat (inferred, ours): Fixed alignment efficiency (0.6) and axis ratios (0.9, 1.1) not explored
- Caveat (inferred, ours): Band 6/7 comparison assumes no alignment polarization at those bands
- Caveat (inferred, ours): Dust surface density depends on a kappa_abs computed at a_max = 100 um while models use other sizes

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Observed Band 3 Stokes I/Q/U images were provided by a coauthor of earlier work and are not stated to be public
- Missing: RADMC-3D setup (grid, photons, version), inclination, position angle, scale height and beam convolution
- Missing: Fit procedure for the tau profile
- Missing: Details of the integration and masking behind PF_total and Band 6/7 values
- Data volume (inferred): Small: processed Stokes I/Q/U images and RADMC-3D runs (MB to a few GB); raw ALMA calibration would be tens of GB but is not needed.
- Score (inferred): 2/5, The modeling recipe (profiles, dust model, parameters, a_max grid) is mostly given, but the observed Stokes images came from a private communication and RADMC-3D, geometry and beam-convolution settings are missing.
- Rediscovery candidate: no, Observed data are not stated to be public, key RADMC-3D and geometry settings are missing, and model-observation agreement is judged visually.

## Links

- Method: (cite: kataoka2017) (Total polarization fraction estimation across the disk, followed here)
- Method: (cite: birnstiel2018) (Grain composition model)
- Method: (cite: okuzumi2019) (Temperature profile of the HL Tau disk)
- Companion: (cite: stephens2017) (Source of the Band 3 polarization observation)
- Companion: (cite: yang2019) (Semi-analytical alignment models and suggested self-scattering contamination)
- Companion: (cite: carlos2019) (Multi-wavelength continuum grain size analysis compared with the polarization result)
- Related: ALMA HL Tau Band 3, 6 and 7 polarization observations (cite: kataoka2017; stephens2017)

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00115.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 92,
  "stated": 48,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
