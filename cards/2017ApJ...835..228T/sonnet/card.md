# A Surface Density Perturbation in the TW Hydrae Disk at 95 au Traced by Molecular Emission

`2017ApJ...835..228T` | The Astrophysical Journal 2017 | first author: Teague, R. | arXiv: 1702.02147 | DOI: 10.3847/1538-4357/835/2/228

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is the dip in the CS J=5-4 radial profile at 1.6'' in TW Hya caused by a gas surface density perturbation (as in scattered light) rather than a chemical or dust-only effect?  
  > "we follow the modelling carried out by (cite: vanBoekel_ea_2016) and argue that these features are the product of a depression in the surface density of the gas rather than a chemical effect." (Introduction)
- Target **TW Hya**: coordinates _not stated_; z/distance 59 ± 1 pc  
  > "TW Hya, as the nearest protoplanetary disk to us at $59\pm1$ pc (cite: Gaia_2016)" (Introduction); distance from Gaia (cite: Gaia_2016)  
  > "TW Hya, as the nearest protoplanetary disk to us at $59\pm1$ pc (cite: Gaia_2016)" (Introduction)

## Data provenance

- ALMA projects: 2013.1.00387.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5''  
  > "We present ALMA Cycle 2 observations at $0.5\ensuremath{''}$ resolution of TW Hya of CS $J=5-4$ emission." (abstract)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: May 13, 2015  
  > "The ALMA Cycle 2 observations, project 2013.1.00387.S, were performed on May 13, 2015." (2.1 Data Reduction)
- pi or archival as stated: Originally presented in Teague et al. 2016  
  > "were originally presented in (cite: Teague_ea_2016)." (2.1 Data Reduction)
- Line: CS J=5-4 (244.936 GHz)
- Line: CO J=2-1 (230.538 GHz)
- Line: CN N=2-1 (226.875 GHz)
- External data: TW Hya fiducial thermochemical disk model (surface density, 0.06 Msun)  
  > "we take the TW Hya model of (cite: Gorti_ea_2011) as the fiducial model." (3.1 Physical Structure) [from Gorti et al. 2011 (cite: Gorti_ea_2011)]
- External data: Scattered-light perturbation parameters (Debes: d=0.3; van Boekel: d=0.55)  
  > "Model C, the outer perturbation from (cite: vanBoekel_ea_2016), $d = 0.55$, $\Delta d = 15$ au and $d_0 = 80$ au" (3.1 Physical Structure) [from Debes et al. 2013; van Boekel et al. 2016]
- External data: CS collisional rates from LAMDA  
  > "The collisional rates for CS were taken from (cite: Lique_ea_2010), stored in the LAMDA database" (3.3 Radiative Transfer) [from Lique et al. 2010]
- External data: Inclination 7 deg  
  > "assuming an inclination of $7\ensuremath{^\circ}$ (cite: Qi_ea_2004)" (2.1 Data Reduction) [from Qi et al. 2004]
- Simulation/model as data: Seven models (A, B, C, D and dust-only Bd, Cd, Dd) with Gaussian surface density perturbations, run through ALCHEMIC, LIME and CASA simobserve  
  > "compares the different $n({\rm H}_2)$ and $T_{\rm gas}$ structures for the seven models around the perturbation centre." (4.1 Physical Structure)

## Processing

### Calibration

- pipeline or manual: Standard ALMA calibration script in CASA  
  > "Data were calibrated using the standard ALMA calibration script in the `CASA` software package" (2.1 Data Reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede; phase/amplitude calibrator J1037-2934 at 0.72 Jy  
  > "The absolute flux calibration was estimated using Ganymede." (2.1 Data Reduction)
- flux scale uncertainty: about 7%  
  > "We hence estimate that the calibration uncertainty is about 7%." (2.1 Data Reduction)
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
- continuum subtraction: Moment 0 map is continuum subtracted  
  > "Figure [1](#fig:observations_zeroth) shows the continuum subtracted zeroth moment of the CS $J=(5-4)$ line emission" (2.1 Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observations and reduction originally presented in earlier paper  
  > "were originally presented in (cite: Teague_ea_2016)." (2.1 Data Reduction) [from Teague et al. 2016 (cite: Teague_ea_2016)]
- Position angle 240 deg  
  > "position angle $240\ensuremath{^\circ}$ (cite: Teague_ea_2016)" (2.1 Data Reduction) [from Teague et al. 2016]
- Physical structure solved following Gorti et al. 2011  
  > "was solved for self-consistently including heating and cooling processes following (cite: Gorti_ea_2011)" (3.2 Chemistry) [from Gorti et al. 2011]
- Turbulent broadening 0.3 c_s  
  > "we assumed a turbulent broadening component of $v_{\rm turb} = 0.3 c_s$ where $c_s$ is the local soundspeed (cite: Teague_ea_2016)" (3.3 Radiative Transfer) [from Teague et al. 2016]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters (weighting, robust, cell, image size, channel width)
- CASA version
- line-free channels for continuum subtraction
- moment-0 velocity range and masking
- simobserve configuration and noise settings
- LIME grid and photon settings
- Model code/outputs not released
- Radial bin width for the azimuthal average

## Analysis recipe

1. **Calibrate and make CS moment-0 map**: Standard ALMA calibration script, continuum-subtracted zeroth moment  
  > "Data were calibrated using the standard ALMA calibration script in the `CASA` software package" (2.1 Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive radial intensity profile**: Azimuthal average of moment-0 assuming inclination 7 deg, PA 240 deg  
  > "these data were azimuthally averaged assuming an inclination of $7\ensuremath{^\circ}$ (cite: Qi_ea_2004) and position angle $240\ensuremath{^\circ}$ (cite: Teague_ea_2016)" (2.1 Data Reduction)
   - assumption: d = 59 pc  
  > "or 95 au when assuming a distance of $d = 59$ pc (cite: Gaia_2016)" (2.2 Radial Features)
   - fitting: _not stated_
   - validation: Second derivative used to identify dips and bumps  
  > "each consisting of a ‘dip’ and a ‘bump’ depending on the sign of the second derivative" (2.2 Radial Features)
3. **Build perturbed disk models and solve physical structure**: Gorti et al. 1+1D thermal model with Gaussian depression in surface density (Models A-D, plus dust-only variants)  
  > "The surface density is then perturbed with a Gaussian depression characterised by center $d_0$, width $\Delta d$ and depth $d$" (3.1 Physical Structure)
   - parameter: Model B d=0.3, Δd=20 au; C d=0.55, Δd=15 au; D d=1, Δd=9.45 au; d0=80 au  
  > "Model D, a fully depleted gap, $d = 1$, $\Delta d = 9.45$ au and $d_0 = 80$ au" (3.1 Physical Structure)
   - assumption: Gas-to-dust 100, MRN grains 0.09 µm–1 mm, PAH 1e-9  
  > "The model assumes a gas-to-dust ratio of 100, with an MRN-like grain size distribution" (3.1 Physical Structure)
   - fitting: _not stated_
   - validation: Equal mass removed in all perturbed models  
  > "The widths have been chosen such that each perturbed model has the same amount of mass removed relative to the unperturbed Model A" (3.1 Physical Structure)
4. **Chemical modelling**: ALCHEMIC gas-grain network with deuterium fractionation, 1 Myr, low-metals initial abundances  
  > "Chemistry was modelled over 1 Myr without taking dynamics and disk evolution into account" (3.2 Chemistry)
   - software: ALCHEMIC
   - parameter: CRP ionization 1.3e-17 s^-1; grain radius 7 µm  
  > "The standard CRP ionization rate of $1.3 \times 10^{-17}$ s$^{-1}$ is adopted throughout the entire disk." (3.2 Chemistry)
   - fitting: _not stated_
   - validation: _not stated_
5. **Non-LTE radiative transfer and simulated observations**: LIME for CS J=5-4, then CASA simobserve with same array configuration; compare radial profiles  
  > "The `simobserve` task in `CASA` was used to simulate observations using the same array configuration" (3.3 Radiative Transfer)
   - software: LIME, CASA
   - fitting: No fit; qualitative comparison of normalised profiles  
  > "we focus on the deviation between models, rather than a direct fit of the TW Hya disk" (4.1 Physical Structure)
   - validation: CO isotopologue fluxes in Model A agree within 10% of observed  
  > "which all agreed within 10% of the observed values (Schwarz, K. private communication)" (5.1 Applicability to TW Hya)
6. **Estimate embedded planet mass**: Duffell 2015 analytic gap-depth relation  
  > "(cite: Duffell_2015) derives an analytic expression for the planet mass" (5.3 Embedded Planet)
   - parameter: d=0.45, M*=0.7 Msun, alpha=1e-4–1e-3  
  > "$M_{\ast} = 0.7\,M_{\ensuremath{\odot}}$ and $\alpha = 10^{-4}$ – $10^{-3}$" (5.3 Embedded Planet)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and simobserve  
  > "The `simobserve` task in `CASA` was used to simulate observations" (3.3 Radiative Transfer)
- **ALCHEMIC** : Gas-grain chemical modelling  
  > "the 1+1D code `ALCHEMIC` (cite: Semenov_ea_2010)" (3.2 Chemistry)
- **LIME** : Non-LTE 3D radiative transfer  
  > "non-local thermal equilibrium (non-LTE) 3D radiative transfer modeling using `LIME`" (3.3 Radiative Transfer)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS J=5-4 integrated flux | 1.24 | not stated | Jy beam^-1 km s^-1 | 1 | The integrated flux of the line was 1.24 Jy beam$^{-1}$ km s$^{-1}$ |
| Flux calibration uncertainty | 7 | not stated | % | 1 | We hence estimate that the calibration uncertainty is about 7%. |
| Dip I location | 1.6 (95 au) | not stated | arcsec | 2 | The most prominent feature, ‘Dip I’, at $1.6\ensuremath{''}$, or 95 au |
| Observed CS peak flux | 34.5 at 0.58'' | not stated | mJy beam^-1 km s^-1 | 2 | the CS $J=5-4$ line has a peak flux of 34.5 mJy beam$^{-1}$ km s$^{-1}$ at a radial offset $0.58\ensuremath{''}$ |
| Model A CS peak flux | 26.7 at 1.01'' | not stated | mJy beam^-1 km s^-1 | 5 | has a peak flux of 26.7 mJy beam$^{-1}$ km s$^{-1}$ at $1.01\ensuremath{''}$ |
| Mass removed by perturbation | 2.7e-3 (2.8 MJup) | not stated | Msun | 3 | $2.7 \times 10^{-3}~M_{\ensuremath{\odot}}$ ($2.8~M_{\rm Jup}$) |
| Potential embedded planet mass | 12–38 | not stated | Earth masses | 6 | a potential planet mass of 12 – 38 $M_{\ensuremath{\oplus}}$ |
| Model A N(CS) at 100 au | ~1e13 | not stated | cm^-2 | 4 | $N({\rm CS}) \sim 10^{13}$ cm$^{-2}$ |

## Qualitative findings

- A 55% surface density depression (Model C) gives the best match to the CS dip; a 30% depression has no effect; a full gap is too deep; dust-only perturbations give CS enhancement, contrary to observations.  
  > "produces the best fit to the morphology of the radial profile." (Conclusion)
- The outer enhancement at ~3'' arises from the exponential surface density edge and increased UV penetration.  
  > "naturally reproduce the outer enhancement at $3\ensuremath{''}$." (Conclusion)

## Claim tuples

- H: A gas surface density perturbation explains the CS dip at 1.6'' | E: Thermochemical, chemical and non-LTE modelling of perturbed disks with simulated observations | R: Model C (d=0.55) reproduces dip morphology; B too weak, D too deep | F: Surface density depression is consistent with the CS feature and scattered light | **supported**
- H: A dust-only gap could produce the CS feature | E: Models Bd, Cd, Dd with only dust surface density perturbed | R: Enhanced gas-to-dust ratio reduces freeze-out and enhances CS | F: Dust-only gap cannot reproduce the feature | **supported**
- H: The outer CS enhancement at 3.1'' has a chemical origin | E: UV flux analysis in the models | R: Reproduced in all models, tied to the exponential edge | F: Likely enhanced UV penetration and desorption, though not proven for TW Hya | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Molecular emission depends on both excitation and abundance, so self-consistent modelling is needed  
  > "it is important to perform self-consistent modelling taking into account the impact of the surface density perturbations on the physical structure and the resulting change in chemical abundances." (3 Modelling Surface Density Perturbations)
- Alternative: Instabilities producing azimuthal structure are disfavoured given no azimuthal variance; MRI dead-zone edge and grain evolution remain candidates  
  > "instabilities which routinely produce vortices, spiral arms or azimuthally asymmetric gaps are likely not present at $\sim 90$ au in TW Hya." (5.4 Disk Instabilities)
- How they decided it was enough: _not stated_
- Limitation (authors): Models do not fully reproduce observed profiles; fiducial model was fit to integrated intensities  
  > "Clearly these models do not fully recover the observations profiles of TW Hya" (5.1 Applicability to TW Hya)
- Caveat (inferred, ours): Model-observation comparison is qualitative with no fit or statistical test
- Caveat (inferred, ours): Model intensities off by factor ~2 in the inner disk
- Caveat (inferred, ours): Dip vs bump degeneracy due to lack of baseline
- Caveat (inferred, ours): Single fiducial model; alternatives like grain evolution not modelled

## Reproducibility

- Data public (paper): Project code and ALMA acknowledgement given; public status not stated explicitly  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00387.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Gorti model code and ALCHEMIC setup files
- Missing: LIME and simobserve settings
- Data volume (inferred): ~10-50 GB raw for one Cycle 2 execution
- Score (inferred): 3/5, Observational part is simple but poorly specified; modelling relies on unreleased codes and inherited setups.
- Rediscovery candidate: no, Main results are qualitative model comparisons requiring heavy unreleased modelling.

## Links

- Method: Teague et al. 2016 (cite: Teague_ea_2016) (Original presentation of the ALMA data)
- Method: Gorti et al. 2011 (cite: Gorti_ea_2011) (Fiducial thermochemical model)
- Method: van Boekel et al. 2016 (cite: vanBoekel_ea_2016) (Perturbation model followed)
- Companion: Debes et al. 2013 (cite: Debes_ea_2013) (NICMOS scattered-light dip)

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 43,
  "rate": 0.524
 },
 "evidence_ok": true
}
```
