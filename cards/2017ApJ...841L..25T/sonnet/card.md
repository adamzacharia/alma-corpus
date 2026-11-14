# Rotating Starburst Cores in Massive Galaxies at z = 2.5

`2017ApJ...841L..25T` | The Astrophysical Journal Letters 2017 | first author: Tadaki, Ken-ichi | arXiv: 1703.10197 | DOI: 10.3847/2041-8213/aa7338

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial extent, kinematics and CO-to-H2 conversion factor of molecular gas in the compact dusty star-forming cores of two massive z=2.5 galaxies?  
  > "we report results from CO $J = 3-2$ observations of two massive galaxies at $z=2.5$ using Atacama Large Millimeter/submillimeter Array (ALMA) to study the spatial distribution and the kinematics of molecular gas in the starburst cores." (Introduction)
- Target **U4-16795**: coordinates _not stated_; z/distance z=2.53 (z_CO=2.5236)  
  > "We select two galaxies at $z=2.53$ (U4-16795 and U4-16504) from Subaru narrow-band imaging in the SXDF field" (Observations); distance from Subaru narrow-band redshift; CO redshift in Table  
  > "We select two galaxies at $z=2.53$ (U4-16795 and U4-16504) from Subaru narrow-band imaging in the SXDF field" (Observations)
- Target **U4-16504**: coordinates _not stated_; z/distance z=2.53 (z_CO=2.5267)  
  > "We select two galaxies at $z=2.53$ (U4-16795 and U4-16504) from Subaru narrow-band imaging in the SXDF field" (Observations); distance from Subaru narrow-band redshift; CO redshift in Table  
  > "We select two galaxies at $z=2.53$ (U4-16795 and U4-16504) from Subaru narrow-band imaging in the SXDF field" (Observations)

## Data provenance

- ALMA projects: 2013.1.00742.S
- bands: Band 3  
  > "with ALMA Band-3 receivers covering the frequency range of 95–99 and 107–111 GHz" (Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.66"x0.55" synthesized beam  
  > "The synthesized beamsize is 0.66$''$$\times$0.55$''$." (Observations)
- max recoverable scale: _not stated_
- sensitivity: 147 uJy/beam per 50 km/s channel; 8.1 uJy/beam continuum  
  > "The rms levels are 147 $\mu$Jy beam$^{-1}$ in the channel map and 8.1 $\mu$Jy beam$^{-1}$ in the continuum map." (Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.796 GHz)
- Other facility **ALMA 870 um continuum (0.2")**: high-resolution dust continuum maps from earlier paper  
  > "0.2$''$-resolution 870 $\mu$m continuum maps are available for both galaxies (cite: 2017ApJ...834..135T)." (Spatial extent of dust)
- Other facility **Herschel-PACS / Spitzer-MIPS**: 160 um and 24 um detections for SFRs  
  > "U4-16795 is detected in a deep $Herschel$-PACS 160 $\mu$m map from archival data" (Observations)
- Other facility **Subaru narrow-band, HAWK-I Ks, 3D-HST**: redshifts, Ks maps, photometry for stellar masses  
  > "In deep HAWK-I/$K_s$-band maps (cite: 2014A&A...570A..11F), 81% and 71% of the total fluxes come from the central 1.5$''$ aperture region" (Observations)
- External data: 0.2" 870 um continuum maps  
  > "0.2$''$-resolution 870 $\mu$m continuum maps are available for both galaxies (cite: 2017ApJ...834..135T)." (Spatial extent of dust) [from (cite: 2017ApJ...834..135T)]
- External data: ALMA 1.1 mm flux of U4-16795  
  > "We also use the ALMA 1.1 mm flux ($S_{1.1\mathrm{mm}}=1.75\pm0.07~$mJy beam$^{-1}$; (cite: 2015ApJ...811L...3T))." (Dust mass) [from (cite: 2015ApJ...811L...3T)]

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

- task: tclean  
  > "We use the `tclean` task with natural weighting to make a channel map with a velocity width of 50 km s$^{-1}$" (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "We use the `tclean` task with natural weighting" (Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: dirty continuum maps excluding the CO line frequency range  
  > "dirty continuum maps excluding the frequency range of the CO line" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Stellar masses/SFR-related methodology and 870 um continuum data; circular disk models previously used  
  > "while (cite: 2017ApJ...834..135T) have adopted circular disk models ($q=1$)" (Spatial extent of dust) [from (cite: 2017ApJ...834..135T)]
- SFR recipes  
  > "Following the recipes of (cite: 2011ApJ...738..106W), we derive SFRs" (Observations) [from (cite: 2011ApJ...738..106W)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- flux calibrator and flux scale uncertainty
- image size and cell size, clean threshold/masks
- DYSMAL model grid and priors, pressure support prescription details
- how kinematic center and PA were fixed for PV extraction
- UVMULTIFIT starting parameters
- PV slit width

## Analysis recipe

1. **Image CO cube and continuum, measure CO fluxes**: tclean natural weighting, 50 km/s channels; fluxes in 1.5" aperture, errors from 200 random apertures  
  > "The uncertainties are estimated from the standard deviation of 200 random aperture photometry measurements." (Table 1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit dust size in uv plane**: Elliptical exponential disk fit to visibility amplitudes of 870 um data  
  > "We use the `UVMULTIFIT` tool to fit the visibility amplitudes to models in the $u-v$ plane" (Spatial extent of dust)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
3. **Fit CO size**: uv-plane fit of CO with axis ratio and PA fixed from dust (q=0.49, PA=35 deg; q=1 for U4-16504)  
  > "We fix to $q=0.49$ and PA$_\mathrm{mor}=35^\circ$ for U4-16795, and $q=1$ for U4-16504." (Spatial extent of molecular gas)
   - software: UVMULTIFIT
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit PV diagram with dynamical model**: DYSMAL exponential-disk PV models convolved with beam, chi-squared on pixels >3 sigma; free Mdyn and sigma0  
  > "the remaining free parameters in the model are dynamical mass, $M_\mathrm{dyn}$, and local velocity dispersion, $\sigma_0$." (Molecular gas kinematics)
   - software: DYSMAL
   - parameter: Re fixed to CO size; inclination from sin^2 i=(1-q^2)/(1-thickness^2), thickness 0.25  
  > "for symmetric oblate disks with an intrinsic thickness of 0.25" (Molecular gas kinematics)
   - assumption: U4-16504 uses mean sin i=0.79 for isotropic disks  
  > "we adopt the average of possible inclinations ($\langle \sin i\rangle=0.79$)" (Molecular gas kinematics)
   - fitting: chi-squared minimization; errors from p-value above 5%  
  > "These uncertainties are based on the reduced-chi squared values corresponding to a p-value above 5%." (Molecular gas kinematics)
   - validation: residual maps  
  > "along with the residual maps after subtracting the model from the data" (Molecular gas kinematics)
5. **Dust and gas masses, conversion factor test**: Modified blackbody dust mass from 3 mm limit; CO gas mass with alpha_CO 4.36 and 0.8; gas-to-dust 120; Monte Carlo for baryon fraction  
  > "Monte Carlo simulations incorporating the uncertainties of gas, stellar and dynamical mass show that the probability of the baryonic mass fraction being less than one" (Gas mass)
   - parameter: Td=32 K, beta=2.2, kappa850=0.4-1.5  
  > "we reasonably assume $T_d=$32 K and $\beta=2.2$ to explain all data points" (Dust mass)
   - assumption: CO J=3-2 thermalized  
  > "The CO $J=3-2$ emission line is assumed to be thermalized" (Gas mass)
   - fitting: _not stated_
   - validation: compare to dynamical and stellar masses  
  > "We then compare the gas masses derived with these two different conversion factors to the dynamical and stellar masses." (Gas mass)

## Software

- **CASA** : calibration and imaging  
  > "The calibration is processed through the Common Astronomy Software Application package" (Observations)
- **UVMULTIFIT** : uv-plane size fitting  
  > "We use the `UVMULTIFIT` tool to fit the visibility amplitudes" (Spatial extent of dust)
- **DYSMAL** : PV diagram dynamical models  
  > "We use the `DYSMAL` code (cite: 2011ApJ...741...69D) to generate PV diagrams" (Molecular gas kinematics)
- **FAST** : SED fitting for stellar mass  
  > "We compute the stellar mass using the `FAST` spectral energy distribution fitting code" (Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Re 870um U4-16795 | 1.3 | 0.1 | kpc | 2 | effective radii of $R_\mathrm{e}=1.3\pm0.1$ kpc and $R_\mathrm{e}=1.2\pm0.1$ kpc |
| Re CO U4-16795 | 1.9 | 0.4 | kpc | 3 | The effective radii are $R_\mathrm{e}=1.9\pm0.4$ kpc for U4-16795 and $R_\mathrm{e}=2.3\pm0.4$ kpc for U4-16504 |
| vmax/sigma0 U4-16795 | 7.0 | +2.5/-2.8 | dimensionless | 4 | $v_\mathrm{max}/\sigma_0=7.0^{+2.5}_{-2.8}$ |
| vmax/sigma0 U4-16504 | 4.1 | +1.7/-1.5 | dimensionless | 4 | $v_\mathrm{max}/\sigma_0=4.1^{+1.7}_{-1.5}$ |
| log Mdyn U4-16795 | 11.10 | +0.13/-0.12 | dex Msun | 4 | our final uncertainties are +0.13 dex (-0.12 dex) for U4-16795 |
| gas depletion time | 46 and 79 | 11 and 46 | Myr | 5 | $M_\mathrm{gas}/SFR=46\pm11$ Myr and $79\pm46$ Myr |

## Qualitative findings

- Gas is more extended than dust in both galaxies  
  > "which are larger than those of the 870 $\mu$m continuum emission" (Spatial extent of molecular gas)

## Claim tuples

- H: Are the dusty starburst cores rotation-dominated? | E: PV diagram fits with DYSMAL | R: vmax/sigma0 = 7.0 and 4.1 | F: Both cores are rotation-dominated | **supported**
- H: Is a starburst alpha_CO appropriate in the cores? | E: Compare gas masses with dynamical, stellar and dust-based masses | R: Galactic alpha_CO gives baryon fraction above unity | F: alpha_CO=0.8 appropriate | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Td=25 K, beta=1.8 rejected by 3 mm limit  
  > "The 5$\sigma$ upper limit at 3 mm rejects the models with $T_d=$25 K" (Dust mass)
- How they decided it was enough: _not stated_
- Limitation (authors): Not clear that starburst alpha_CO holds for entire galaxies  
  > "it is not clear yet that the starburst conversion factor is appropriate for entire galaxies" (Discussion and Summary)
- Caveat (inferred, ours): Only two galaxies and low-S/N PV diagrams
- Caveat (inferred, ours): Inclination of U4-16504 not measured
- Caveat (inferred, ours): Dynamical mass depends on assumed disk model and pressure support
- Caveat (inferred, ours): Gas-based conclusions depend on assumed Td, beta and kappa

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version and calibration details
- Missing: DYSMAL configuration and priors
- Missing: imaging parameters
- Data volume (inferred): ~10-50 GB raw
- Score (inferred): 3/5, Public ALMA project and methods broadly described, but many imaging and modeling settings are missing.
- Rediscovery candidate: no, Key settings unspecified and 870 um data come from another paper.

## Links

- Method: (cite: 2014A&A...563A.136M) (UVMULTIFIT)
- Method: (cite: 2011ApJ...741...69D) (DYSMAL)
- Companion: (cite: 2017ApJ...834..135T) (870 um continuum observations of the same galaxies)
- Related: SXDF
- Related: 3D-HST

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 79,
  "stated": 37,
  "rate": 0.468
 },
 "evidence_ok": true
}
```
