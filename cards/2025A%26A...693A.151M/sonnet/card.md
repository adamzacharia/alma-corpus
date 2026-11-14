# REsolved ALMA and SMA Observations of Nearby Stars (REASONS): A population of 74 resolved planetesimal belts at millimetre wavelengths

`2025A&A...693A.151M` | Astronomy and Astrophysics 2025 | first author: Matrà, L. | arXiv: 2501.09058 | DOI: 10.1051/0004-6361/202451397

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: debris_disks, exoplanets
- Question: What are the spatial properties (radius, width, vertical aspect ratio) and evolution of mm-resolved planetesimal belts across a uniformly modelled population of 74 systems?  
  > "We uniformly modelled interferometric visibilities for the entire sample to obtain the basic spatial properties of each belt, and combined these with constraints from multi-wavelength photometry." (abstract)
- Target **REASONS sample of 74 resolved planetesimal belts (e.g. GJ14, HD14055, HD191089)**: coordinates _not stated_; z/distance 3.2 to 152 pc (Table 2)  
  > "Distances are from *Gaia* DR3 (cite: Gaia2016b; Gaia2023j), or from *Hipparcos* if Gaia measurement not available (cite: vanLeeuwen2007)." (Table 2); distance from Gaia DR3, or Hipparcos if Gaia unavailable  
  > "Distances are from *Gaia* DR3 (cite: Gaia2016b; Gaia2023j), or from *Hipparcos* if Gaia measurement not available (cite: vanLeeuwen2007)." (Table 2)

## Data provenance

- ALMA projects: 2017.1.00200.S, 2017.1.00704.S
- bands: Band 6 (1.27 mm) for new ALMA data  
  > "All observations were carried out using Band 6 receivers." (3.1 New ALMA data)
- frequencies and spectral setup: Two 2 GHz windows at 243.1 and 245.1 GHz; two 1.875 GHz windows at 227.2 and 230.1 GHz covering CN and CO 2-1  
  > "two 2 GHz-wide spectral windows centred at 243.1 and 245.1 GHz with a low spectral resolution (31.25 MHz)" (3.1 New ALMA data)
- continuum bandwidth: 7.75 GHz  
  > "The total bandwidth available for continuum was 7.75 GHz, with both polarisations combined." (3.1 New ALMA data)
- arrays: 12-m array with 43-50 antennas; ACA for HD170773 and HD161868  
  > "Data were taken using the 12-m array with 43-50 antennas in a single configuration per target, varying for different targets." (3.1 New ALMA data)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 12-68 uJy continuum for beams 0.2-3.1 arcsec (ALMA); 100-290 uJy for SMA  
  > "Typical continuum sensitivities, measured in a region of the images that is free of emission, are 12-68 $\mu$Jy for beam sizes ranging between 0.2$\ensuremath{''}$ and 3.1$\ensuremath{''}$." (3.1 New ALMA data)
- time on source: _not stated_
- observing dates: SMA between January 2018 and January 2019; ALMA Cycle 5  
  > "between January 2018 and January 2019" (3.2 New SMA data)
- pi or archival as stated: _not stated_
- Line: CO J=2-1 (230.538 GHz)
- Other facility **SMA**: 10 new belts observed at 1.27 mm; calibrated archival SMA data  
  > "15 with ALMA (Sect. [3.1](#sec:almaobs)), and 10 with the SMA (Sect. [3.2](#sec:smaobs))." (2.1 The sample)
- Other facility **JCMT SONS survey**: 850 um detections defining the flux-limited sample  
  > "complete a resolved follow-up census of a flux-limited sample of sources detected at (sub-)mm wavelengths by the SCUBA-2 Observations of Nearby Stars (SONS) JCMT Legacy Survey (cite: Holland2017)" (2.1 The sample)
- External data: Protoplanetary ring widths (65 rings) from DSHARP, Taurus and ODISEA surveys  
  > "We compile a sample of 65 protoplanetary rings from three ALMA surveys: DSHARP (cite: Huang2018), the Taurus star-forming region survey (cite: Long2018), and ODISEA" (5.2 The width of planetesimal belts) [from (cite: Huang2018; Long2018; Cieza2021)]
- External data: Archival ALMA, SMA, CARMA calibrated data of resolved belts  
  > "For SMA and CARMA archival observations, we obtained calibrated, science-ready visibilities from PIs/co-Is of the respective projects" (3.3 Archival observations) [from archival projects]
- External data: Stellar ages and memberships from BANYAN Sigma  
  > "Membership from BANYAN Sigma (cite: Gagne2018), or moving group age also from (cite: Gagne2018)" (Table 2) [from (cite: Gagne2018)]
- Simulation/model as data: L7 synthetic Kuiper belt model used to estimate Kuiper belt radius and width  
  > "These values are estimated from the L7 synthetic model of the inner, main and outer Kuiper belt (cite: Kavelaars2009; Petit2011)" (5.2 The width of planetesimal belts)

## Processing

### Calibration

- pipeline or manual: ALMA observatory pipeline; archival data calibrated with provided pipeline or scripts; SMA calibrated in MIR  
  > "Standard calibrations were applied to each visibility dataset by the ALMA observatory, using its pipeline." (3.1 New ALMA data)
- casa version: CASA v5.4.0 (imaging)  
  > "All concatenated datasets were imaged in the Common Astronomy Software Applications (CASA) software v5.4.0" (3.1 New ALMA data)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% for ALMA; ~20% for SMA  
  > "The flux calibration accuracy of all ALMA observations was conservatively assumed to be 10%." (3.1 New ALMA data)
- self calibration: _not stated_

### Imaging

- task: CASA tclean, multi-frequency synthesis  
  > "The continuum imaging was carried out in multi-frequency synthesis mode with multiscale deconvolution (cite: Cornwell2008)." (3.1 New ALMA data)
- deconvolver: multiscale CLEAN  
  > "Continuum imaging of the combined observations for each target was carried out using multiscale CLEAN deconvolution within CASA v5.4.0" (3.3 Archival observations)
- weighting robust: Different weighting and u-v tapers per target; natural weighting for CO  
  > "Different weighting schemes and u-v tapers were used for different targets to find an optimal balance between surface brightness sensitivity and resolution." (3.1 New ALMA data)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub for CO cubes  
  > "CO imaging was carried out after continuum subtraction from the visibility measurements (using the uvcontsub CASA task)." (3.1 New ALMA data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Selection requirements for belts  
  > "We direct the reader to §3 of (cite: Matra2018b) for a full description of the requirements for a belt to be selected." (2.2 Observational bias) [from (cite: Matra2018b)]
- SED fitting with star + modified blackbody  
  > "following the method of (cite: Yelverton2019)" (4.3 SED modelling) [from (cite: Yelverton2019)]
- Radius-luminosity fit method  
  > "A fit as described in §2 of (cite: Matra2018b) leads to a slope" (5.1) [from (cite: Matra2018b)]
- Model image size/pixel choice  
  > "The choice was analogous to the criteria described in (cite: Tazzari2018)" (4.2.1 Data preparation) [from (cite: Tazzari2018)]

### Not stated but needed to reproduce (our reading)

- Per-target weighting, robust and u-v taper values (only on Zenodo)
- MCMC prior ranges and exact step counts per system
- Line-free channels for continuum subtraction/ CO
- Details of bias map selection thresholds per wavelength
- Exact photometry compilations used in SED fits

## Analysis recipe

1. **Calibrate and image continuum**: Pipeline calibration, concatenation, tclean multiscale imaging  
  > "Standard calibrations were applied to each visibility dataset by the ALMA observatory, using its pipeline." (3.1 New ALMA data)
   - software: CASA, tclean
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit visibilities with belt model**: Radially and vertically Gaussian ring model from RADMC-3D images, Fourier transformed with GALARIO, fit with MCMC  
  > "We then use the GALARIO software package (cite: Tazzari2018) to obtain a Fourier transform of the model image, and sample it at the same u-v locations as the data." (4.2.3 The fitting process)
   - software: MIAO, RADMC-3D, GALARIO, emcee, CASA
   - parameter: h fixed to 0.03 unless vertically constrained; temperature r^-0.5  
  > "In other cases, we fix this value to $h=0.03$, motivated by the aspect ratio of the AU Mic disc (cite: Daley2019)." (4.2.2 The physical model)
   - assumption: Gaussian radial profile; large grains behave as blackbodies  
  > "on the assumption that the large grains probed by millimetre observations are well approximated by blackbodies" (4.2.2 The physical model)
   - fitting: Affine-invariant emcee v3, uniform priors, likelihood proportional to exp(-chi2/2), walkers = 10x free parameters, >=1000 steps, weight rescaling free  
  > "We ran the MCMC to sample the posterior probability distribution of the parameters using a number of walkers equal to 10 times the number of free parameters" (4.2.3 The fitting process)
   - validation: Residual images and deprojected visibility profiles; 65/74 fit well  
  > "Based on the compatibility of residual images with pure noise, we find that 65/74 belts are fit well by our radially and vertically Gaussian model." (4.2.4 Modelling results)
3. **Fit SEDs**: Star + modified blackbody fit to multi-wavelength photometry  
  > "fit it with a star + modified blackbody model, following the method of (cite: Yelverton2019)" (4.3 SED modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive dust masses and test collisional evolution**: Mass at 1.33 mm from flux, kappa and blackbody temperature; compare with collisional isochrones with age groups  
  > "$\kappa_\nu$ is the dust opacity, assumed to be 0.23 m$^2$ kg$^{-1}$, by scaling down 1 m$^2$ kg$^{-1}$ at 1000 GHz linearly" (5.3)
   - parameter: t0 = 10 Myr, delta = 13/3, epsilon = 1, D ~2e-8 Myr Mearth au^-13/3  
  > "We find that a good qualitative fit to the data can be found by setting $D\sim2\times10^{-8}$ Myr M$_{\oplus}$ au$^{-13/3}$." (5.3)
   - assumption: T(R)=278.3 L^0.25 R^-0.5  
  > "T(R) = 278.3 L_{\star}^{0.25} R^{-0.5}," (5.3)
   - fitting: not stated (qualitative by eye)  
  > "Based on the compatibility of residual images with pure noise, we find that 65/74 belts are fit well by our radially and vertically Gaussian model." (Modelling results)
   - validation: Compared eps=1 with eps=0.4 models  
  > "we also test models with $\epsilon=0.4$" (5.3)
5. **Selection bias maps**: Synthetic populations of 1000 belts per bin passed through selection criteria  
  > "We create a synthetic population of 1000 belts per log-uniform log$_{10}$(X)-log$_{10}$(Y) bins" (5.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** v5.4.0: Imaging, mstransform averaging, uvcontsub  
  > "imaged in the Common Astronomy Software Applications (CASA) software v5.4.0 using the CLEAN algorithm implemented through the tclean task" (3.1)
- **MIAO** : Common framework for imaging, modelling, post-processing  
  > "available on GitHub as a package called MIAO: Modelling Interferometric Array Observations" (4.2.1)
- **RADMC-3D** : Model belt images  
  > "We then create a model image of the belt using the RADMC-3D radiative transfer code" (4.2.2)
- **GALARIO** : Fourier transform of model images  
  > "We then use the GALARIO software package (cite: Tazzari2018)" (4.2.3)
- **emcee** v3: MCMC sampling  
  > "implemented through the EMCEE v3 software package" (4.2.3)
- **MIR (Millimeter Interferometer Reduction)** : SMA calibration  
  > "All calibrations were applied to the complex visibilities within the Millimeter Interferometer Reduction (MIR) package" (3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radius-luminosity slope alpha | 0.14 | +0.03/-0.03 | dimensionless | 2 | leads to a slope $\alpha=0.14^{+0.03}_{-0.03}$ |
| Intrinsic scatter in R-L relation | 0.44 | +0.05/-0.04 | fraction of radius | 2 | an intrinsic scatter $f=0.44^{+0.05}_{-0.04}$ |
| Median fractional width of belts | 0.71 | not stated | dimensionless | 2 | with a median fractional width of 0.71 |
| Median fractional width of protoplanetary rings | 0.18 | not stated | dimensionless | 0 | with a median fractional width of 0.18 and only 9% having values above 0.5 |
| Kuiper belt radius and FWHM (L7 model) | 43 au, 12 au | not stated | au | 0 | estimate a central radius of 43 au and a FWHM of 12 au |
| Belt aspect ratio range (24 belts) | 0.01-0.3 | not stated | dimensionless | 2 | We find well-constrained aspect ratios in the range between $\sim$0.01 and 0.3 |
| Mass depletion exponent | ~1 | not stated | dimensionless | 4 | ($\epsilon\sim1$, so Mass$_{\rm 1.33mm}\propto (t-t_0)^{-1}$) |

## Qualitative findings

- Most belts are broad rings, ~70% with fractional width >0.5, unlike protoplanetary rings  
  > "roughly 70% of discs are wide ($\Delta R/R>0.5$)" (5.2)

## Claim tuples

- H: Belt masses deplete via radius-dependent collisional evolution | E: Mass vs radius in three age groups with bias maps and isochrones | R: ~2 dex mass depletion over ~2 dex collisional age; field belts follow R^13/3 locus | F: Consistent with t^-1 collisional depletion, faster for smaller belts | **supported**
- H: Belts are narrow rings like protoplanetary rings | E: Compare fractional widths of 50 belts with 65 protoplanetary rings | R: Median 0.71 vs 0.18; KS probability <1e-9 | F: Belts are broad; unresolved substructure or migrating rings may explain | **supported**
- H: Belt vertical heights increase with age via viscous stirring | E: Aspect ratios of 24 belts vs age | R: No trend with age; inclinations ~1-20 deg | F: Early stirring, inheritance, or diverse pathways | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Gaussian ring chosen as simple prescription to derive radius and width  
  > "we deemed a Gaussian a simple enough prescription to derive the centroid radius $R$ and width (FWHM) $\Delta R$" (4.2.2)
- Alternative: Slower epsilon=0.4 evolution overestimates old field belt masses  
  > "significantly overestimates the mass of belts in the old field population" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Sample biased by flux-density limits; heights may be extracted from azimuthal profile rather than resolved  
  > "this does not necessarily mean that these belts were all vertically resolved" (5.4)
- Caveat (inferred, ours): Gaussian ring model biases widths for belts with substructure
- Caveat (inferred, ours): Age uncertainties and 1.33 mm opacity assumption drive mass trends
- Caveat (inferred, ours): Collisional isochrone comparison is qualitative, not fitted
- Caveat (inferred, ours): Protoplanetary ring widths measured inconsistently

## Reproducibility

- Data public (paper): Calibrated continuum visibilities, images, fits released on Zenodo  
  > "the mm calibrated visibility continuum data used for the analysis, the CLEAN images shown in Fig. [1](#fig:gallery) (in FITS and PDF format)" (Data Availability)
- Products in archive: _not stated_
- Code: MIAO on GitHub  
  > "available on GitHub as a package called MIAO: Modelling Interferometric Array Observations" (4.2.1)
- Missing: Per-target imaging weightings and tapers (in Zenodo tables)
- Missing: MCMC priors and steps per system
- Missing: SED photometry compilation
- Data volume (inferred): Several hundred GB raw; tens of GB for calibrated visibilities
- Score (inferred): 4/5, Code and calibrated data released and method well described, but many per-target settings only in external tables.
- Rediscovery candidate: yes, Public data and released visibilities; numeric results (R, width, h) for each belt can be re-derived.

## Links

- Method: (cite: Tazzari2018) (GALARIO visibility modelling)
- Method: (cite: Matra2019b) (Vertical structure and inclination relation)
- Method: (cite: Yelverton2019) (SED fitting method)
- Companion: (cite: Matra2018b) (Earlier resolved belt sample)
- Companion: (cite: Holland2017) (SONS JCMT survey)
- Related: SONS
- Related: ARKS
- Related: DSHARP
- Related: ODISEA

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00437.S",
  "2019.1.01517.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 51,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
