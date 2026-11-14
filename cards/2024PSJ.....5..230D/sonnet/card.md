# Surface Properties of the Kalliope─Linus System from ALMA and VLA Data

`2024PSJ.....5..230D` | The Planetary Science Journal 2024 | first author: de Kleer, Katherine | arXiv: 2409.12364 | DOI: 10.3847/PSJ/ad7797

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: What are the thermophysical and electrical (emissivity, dielectric) surface properties of Kalliope and Linus from mm-cm thermal emission, and what do they imply for metal content and the origin of the system?  
  > "The abundance and distribution of metal in asteroid surfaces can be constrained from thermal emission measurements at radio wavelengths, informing our understanding of planetesimal differentiation processes." (abstract)
- Target **(22) Kalliope and moon Linus**: coordinates _not stated_; z/distance 2.165 AU from Earth, 3.173 AU from Sun (ALMA epoch)  
  > "Kalliope, which was at a distance of 3.173 AU from the Sun and 2.165 AU from the Earth at the time of observation and subtended $\sim$100 mas." (2.1 ALMA); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01271.S
- bands: Band 6 (1.3 mm) ALMA; VLA Ku (12-18 GHz) and Ka (29-37 GHz)  
  > "centered at 224, 226, 240, and 242 GHz (around 1.3 mm, ALMA’s Band 6)" (2.1 ALMA)
- frequencies and spectral setup: Full polarization continuum; four SPWs, 64 channels each, 2 GHz bandwidth, centered 224, 226, 240, 242 GHz  
  > "Full polarization data were collected in continuum mode, with four spectral windows each containing 64 channels over 2 GHz of bandwidth" (2.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA extended configuration, max baseline 15.2 km  
  > "ALMA was in an extended configuration at the time of observation, with a maximum baseline of 15.2 km" (2.1 ALMA)
- baselines: _not stated_
- angular resolution: ~20x25 mas (~30x40 km on Kalliope)  
  > "resulting in an angular resolution of ${\sim}20{\times}25$ milliarcseconds (mas)" (2.1 ALMA)
- max recoverable scale: _not stated_
- sensitivity: image noise 1.5-2.0 K, SNR ~40-60 per snapshot  
  > "resulting in a SNR of $\sim$40-60 for each snapshot image and a typical image noise level of 1.5-2.0 K" (2.1 ALMA)
- time on source: 75 minutes (93 scans of 18-72 s)  
  > "the on-source time consisted of 93 scans each of duration 18-72 seconds, for a total on-source time of 75 minutes" (2.1 ALMA)
- observing dates: 2019 June 20 03:12-06:28 UTC (ALMA); VLA 2020 Dec 18 and 19  
  > "on UTC 2019 June 20 between 03:12 and 06:28 UTC" (2.1 ALMA)
- pi or archival as stated: _not stated_
- Other facility **VLA**: Ku- and Ka-band (15, 33 GHz) thermal continuum of Kalliope and Linus (project 20B-259)  
  > "on two dates, under project code 20B-259" (2.2 VLA)
- External data: SAGE shape model and spin pole of Kalliope  
  > "We assume large-scale topography as described by the SAGE shape model from (cite: ferrais2022) with the corresponding spin pole orientation" (3.2.1 Global model) [from (cite: ferrais2022)]
- External data: Geometric albedo 0.166  
  > "We assume a geometric albedo of 0.166 (cite: 2019PDSSMainzer)" (3.2.1 Global model) [from (cite: 2019PDSSMainzer)]
- External data: Radar albedo used for surface density  
  > "where the surface bulk density $\rho$ is derived from the radar albedo using Eq. 5 in (cite: shepard2015), based on the radar measurements from (cite: 2007IcarMagri)" (3.2.1 Global model) [from (cite: shepard2015; 2007IcarMagri)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline; calibrated MS delivered  
  > "The raw data were calibrated via the ALMA pipeline." (2.1 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated MS delivered, then processed in CASA  
  > "The data were delivered in the form of a calibrated Measurement Set (MS)" (2.1 ALMA)
- flux calibrator: J1924-2914 (bandpass and flux scale); J1718-2850 gain; J1751+0939 polarization  
  > "J1924-2914 for bandpass and flux density scale calibration" (2.1 ALMA)
- flux scale uncertainty: 2% (ALMA)  
  > "we adopt a flux density scale calibration uncertainty of 2%" (2.1 ALMA)
- self calibration: One round per snapshot, applied from total intensity; improved SNR ~15%  
  > "after the first round of self-calibration, further iterations with shorter solution intervals did not improve the SNR" (2.1 ALMA)

### Imaging

- task: CASA imaging per snapshot of 3-5 scans (<=5.5 min), Linus modeled via clean components in circular region  
  > "to increase the SNR we combine 3-5 individual scans into a snapshot." (2.1 ALMA)
- deconvolver: _not stated_
- weighting robust: robust = 1.0 (VLA images only)  
  > "We then imaged each snapshot, with a robust parameter of 1.0" (2.2 VLA)
- uv taper: _not stated_
- cell size: 3 mas  
  > "The final images have a pixel scale of 3 milliarcseconds (mas)" (2.1 ALMA)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 20-25 mas  
  > "an angular resolution of 20-25 mas" (2.1 ALMA)
- final rms: 1.5-2.0 K  
  > "a typical image noise level of 1.5-2.0 K" (2.1 ALMA)

### Inherited from earlier work

- ALMA observing setup identical to Psyche data  
  > "The observing set-up was identical to that of the (16) Psyche data published in (cite: dekleer2021)." (2.1 ALMA) [from (cite: dekleer2021)]
- CASA processing, imaging and self-calibration procedure  
  > "as described in detail in (cite: dekleer2021) and briefly summarized below." (2.1 ALMA) [from (cite: dekleer2021)]
- Thermophysical/radiative transfer modeling and local model  
  > "builds on (cite: dekleer2021) and (cite: cambioni2022)" (3.2 Thermophysical model) [from (cite: dekleer2021); (cite: cambioni2022)]
- Metal-content conversions from emissivity  
  > "using the conversions from (cite: dekleer2021)" (5.1 Dielectric and material surface properties of Kalliope) [from (cite: dekleer2021)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Exact tclean parameters (weighting, robust, deconvolver, masking, iterations) for ALMA snapshots
- Self-calibration solution interval and reference antenna details
- Snapshot grouping scan lists
- Thermal inertia-dependent TPM code (Delbo 2015 implementation) not released
- Flux scale adjustment details for VLA 3C 138 are personal communication
- Radar-derived density and Fresnel/dielectric-to-metal conversion tables

## Analysis recipe

1. **Image snapshots and self-calibrate**: Group 3-5 scans into snapshots, iterative imaging and self-calibration in CASA, images in Stokes I and P  
  > "An iterative imaging and self-calibration procedure (cite: cornwell1999) was performed on the visibilities in each snapshot" (2.1 ALMA)
   - software: CASA
   - parameter: snapshot duration <5.5 min; pixel 3 mas  
  > "The total duration of each snapshot never exceeded 5.5 minutes" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure flux densities and positions of Kalliope and Linus**: Fit visibilities with uvmultifit: Kalliope disk, Linus delta function; compared with other methods  
  > "with Kalliope and Linus modeled as a disk and delta function respectively" (2.1 ALMA)
   - software: uvmultifit, CASA, AIPS
   - fitting: uvmultifit visibility fit; uncertainties from fit  
  > "are the uncertainties on the fit parameters as derived from the fitting algorithm" (2.1 ALMA)
   - validation: Cross-compared with two-disk fit, aperture photometry (imstat), AIPS OMFIT/TVSTAT, CLEAN components  
  > "The greatest consistency between methods, and the lowest scatter between observations, was found by using **uvmultifit**" (2.1 ALMA)
3. **Compute brightness temperatures**: Disk-averaged Tb from flux and SAGE-projected area, CMB-corrected; peak Tb via Planck function  
  > "assuming the flux density arises from the emitting area predicted by the SAGE shape model of (cite: ferrais2022)" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit global thermophysical model to ALMA images**: Forward models over grid of thermal inertia and dielectric constants (eps1, eps2) with SAGE shape; chi-square grid search, admissible-solution criterion  
  > "we consider that every combination of ($\Gamma$, $\epsilon$) that satisfies" (3.2.1 Global model)
   - software: TPM (Delbo 2015)
   - parameter: delta_elec = 10 lambda; cp = 500 J/kg/K; geometric albedo 0.166; bolometric emissivity 0.9; 23 images; 65 pixels per beam  
  > "we therefore adopt a value of $\delta_{elec}=$10$\lambda$" (3.2.1 Global model)
   - assumption: smooth surface; |eps|=eps'  
  > "we make the simplification that $|\tilde{\epsilon}| = \epsilon'$" (3.2 Thermophysical model)
   - fitting: Minimum chi2 best fit; 1sigma from range satisfying chi2 < chi2_min[1+sqrt(2/(Ndat-Npar))]  
  > "The reported 1$\sigma$ uncertainties are the 68th percentile above and below the minimum-$\chi^2$ of the full range that satisfies the criterion" (3.2.1 Global model)
   - validation: Blind fake-data retrievals for SNR, emissivity parameterization, shape model; delta_elec test  
  > "In all cases, the retrieved $\Gamma$ and $\epsilon$ were within 1$\sigma$ of the true values." (3.2.2.1 SNR of the data)
5. **Derive emissivities at 9 and 20 mm and Linus**: Emissivity = observed disk-averaged Tb / model mean surface temperature, using Gamma=116; Linus from flux-per-area ratio times Kalliope emissivity  
  > "The emissivity of the 9–20 mm observations is calculated as the ratio of the observed disk-averaged brightness temperature to the average model surface temperature on the observed hemisphere" (3. Models)
   - fitting: _not stated_
   - validation: Compared with STM/FRM bounds  
  > "The 1.3-mm observations have sufficient spatial resolution that the peak measured surface temperature can be compared with those predicted by the STM and FRM." (3.1 Emissivity bounds)
6. **Map local thermal inertia and dielectric constant**: Local model with surface units, time-curve fits per unit, binned 5x5 deg, Mollweide  
  > "we bin the surface properties in longitude and latitude on a grid with elements of angular size 5$^\circ\times 5^\circ$" (3.2.3 Local model)
   - assumption: eps = eps1 = eps2  
  > "assuming that $\epsilon = \epsilon_1= \epsilon_2$" (3.2.3 Local model)
   - fitting: Same chi2 criterion; median of admissible solutions shown  
  > "For each surface unit, the results in Figure 8 are obtained by computing the median of the model solutions that satisfy Eq." (4.1 Thermophysical and electrical properties of Kalliope)
   - validation: Median and min-chi2 solutions give same dielectric map  
  > "Both approaches yield the same map of dielectric constant" (4.1)
7. **Polarization test**: Bin polarization pixels by emission angle (40 bins) and compare with Fresnel-based simulated polarization  
  > "binned the results into 40 emission angle bins" (2.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : ALMA imaging, self-calibration, uvmultifit, VLA MS export  
  > "Processing of the MS was performed using the Common Astronomy Software Applications (CASA) package" (2.1 ALMA)
- **uvmultifit** : Flux density and position fitting in visibilities  
  > "determined from the visibilities using the CASA package **uvmultifit**" (2.1 ALMA)
- **AIPS** : VLA reduction, OMFIT flux fitting, polarization calibration  
  > "All further reduction and analysis were done in AIPS" (2.2 VLA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Kalliope thermal inertia | 116 | +326/-91 | J m^-2 s^-0.5 K^-1 | 4 | we find a best-fit solution of $\Gamma$ = 116$^{+326}_{-91}$ |
| Kalliope emissivity at 1.3 mm | 0.65 | 0.02 | dimensionless | 4 | 0.65$\pm$0.02, 0.56$\pm$0.03, and 0.77$\pm$0.02 at 1.3, 9, and 20 mm respectively |
| Kalliope emissivity at 9 mm | 0.56 | 0.03 | dimensionless | 5 | 0.65$\pm$0.02, 0.56$\pm$0.03, and 0.77$\pm$0.02 at 1.3, 9, and 20 mm respectively |
| Kalliope emissivity at 20 mm | 0.77 | 0.02 | dimensionless | 5 | 0.65$\pm$0.02, 0.56$\pm$0.03, and 0.77$\pm$0.02 at 1.3, 9, and 20 mm respectively |
| Linus emissivity at 1.3 mm | 0.73 | 0.04 | dimensionless | 5 | Linus’ emissivity is 0.73$\pm$0.04 at 1.3 mm and 0.85$\pm$0.17 at 9 mm |
| Linus emissivity at 9 mm | 0.85 | 0.17 | dimensionless | 5 | Linus’ emissivity is 0.73$\pm$0.04 at 1.3 mm and 0.85$\pm$0.17 at 9 mm |
| Global best-fit dielectric constant eps1 | 15 | +2/-1 | dimensionless | 4 | $\epsilon_1$ = 15$^{+2}_{-1}$ and $\epsilon_2$ = 20$^{+0}_{-15}$ |
| Global minimum reduced chi2 | 12 | not stated | dimensionless | 4 | corresponding to a minimum $\chi_r^2$ of 12 |
| Rotationally averaged flux density of Kalliope at 1.3 mm | 25.8 | 0.9 | mJy | 2 | 25.8$\pm$0.9, 0.501$\pm$0.029, and 0.148$\pm$0.006 mJy at 1.3, 9, and 20 mm respectively |
| Linus flux density at 1.3 mm | 1.01 | 0.03 | mJy | 2 | 1.01$\pm$0.03 mJy at 1.3 mm and 0.021$\pm$0.004 mJy at 9 mm |
| Flux-per-area ratio Kalliope/Linus at 1.3 mm | 0.87 | 0.05 | dimensionless | 5 | lower for Kalliope than Linus by a factor of 0.87$\pm$0.05 at 1.3 mm and 0.66$\pm$0.13 at 9 mm |
| Polarization upper limit at 1.3 mm | 1 | not stated | % | 7 | with an upper limit of 1% at 1.3 mm (Figure [4](#fig:polfrac)) and 2% at 9 mm |

## Qualitative findings

- Region of high dielectric constant (eps 40-60, emissivity ~0.45) in northern hemisphere at ~210-280 deg longitude, supported by radar albedo maxima  
  > "The strongest evidence for heterogeneity in Kalliope’s material properties is the region of high dielectric constant (low emissivity) around longitudes 210–280$^{\circ}$ in the north." (5.2)
- No polarization detected despite low emissivity, suggesting metallic grain scattering  
  > "The lack of polarization could potentially be explained by the presence of metallic grains $\sim$100 $\mu$m in size" (5.1)

## Claim tuples

- H: Is Linus's surface less metal-rich than Kalliope's? | E: Compare flux per unit area of Kalliope and Linus at 1.3 and 9 mm; test rotation-rate effect | R: Flux per area lower for Kalliope by 0.87±0.05 (1.3 mm); rotation can only give 0.93 minimum; Linus emissivity 0.73±0.04 | F: Linus has higher emissivity, i.e. less metal-rich or more porous surface | **supported**
- H: Is Kalliope's surface heterogeneous in dielectric properties? | E: Local thermophysical model fit to 23 ALMA images | R: Region with dielectric constant 40-60 in north | F: Localized metal-enhanced region | **supported**
- H: Does Kalliope's mm emissivity indicate metal-rich surface? | E: Global TPM at 1.3 mm plus 9, 20 mm emissivities and polarization limits | R: Emissivities 0.65, 0.56, 0.77 and no polarization | F: Suppressed mm emission and depolarization consistent with reduced regolith with ~15-25 wt.% metallic grains | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Applying the same observational and modeling approach as for Psyche, extended to VLA wavelengths  
  > "Here we apply the same observational and modeling approach to Kalliope and Linus using observations at 1.3 mm from ALMA." (1 Introduction)
- Alternative: MPCD-ADAM shape model rejected: chi2 more than 3 sigma higher than SAGE  
  > "the minimum $\chi_r^2$ = 16 for the MPCD-ADAM case is more than 3$\sigma$ higher than that obtained with the SAGE shape model" (3.2.2.3 Shape model)
- Alternative: Coupled eps1=eps2 global model rejected in favor of decoupled  
  > "We therefore adopt the latter as our nominal case" (3.2.2.2 Emissivity parameterization)
- How they decided it was enough: _not stated_
- Limitation (authors): High-dielectric region seen only at limb due to incomplete rotational coverage; shape mismatch could mimic it  
  > "This region of high dielectric constant is only observed when it is at Kalliope’s limb due to our incomplete rotational coverage." (5.2)
- Limitation (authors): Thermal inertia retrieval requires accurate shape model  
  > "retrieving an accurate thermal inertia is only possible when a shape model exists that provides a good approximation to the observations" (3.2.2.3 Shape model)
- Caveat (inferred, ours): Global model chi2_r ~12 indicates poor fit; uncertainties from chi2 criterion are not true posterior
- Caveat (inferred, ours): Thermal inertia poorly constrained (25-440)
- Caveat (inferred, ours): Delta_elec assumed 10 lambda
- Caveat (inferred, ours): VLA flux scale corrected by unpublished adjustments after 3C 138 flare
- Caveat (inferred, ours): Linus at 9 mm only ~5 sigma detection

## Reproducibility

- Data public (paper): ALMA project 2018.1.01271.S and VLA 20B-259 cited; no explicit statement of public availability  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.01271.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: TPM code and exact configuration
- Missing: Snapshot scan assignments
- Missing: VLA flux adjustments and AIPS parameters
- Missing: Fresnel-to-metal-content conversion details
- Data volume (inferred): ~tens of GB (ALMA long-baseline continuum MS plus VLA)
- Score (inferred): 3/5, Data identified and recipe broadly described, but key imaging parameters and code are missing and the heavily inherited method lives in prior papers.
- Rediscovery candidate: no, Requires custom thermophysical modeling code and inherited unstated imaging settings.

## Links

- Method: (cite: dekleer2021) (Original ALMA processing and thermophysical modeling for Psyche)
- Method: (cite: cambioni2022) (Local model for surface properties)
- Method: (cite: delbo2015) (Thermophysical model)
- Companion: (cite: ferrais2022) (Shape model and bulk density of Kalliope)
- Related: ALMA Psyche observations (de Kleer et al. 2021)

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
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
  "facts": 85,
  "stated": 56,
  "rate": 0.659
 },
 "evidence_ok": true
}
```
