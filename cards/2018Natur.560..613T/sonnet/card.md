# The gravitationally unstable gas disk of a starburst galaxy 12 billion years ago

`2018Natur.560..613T` | Nature 2018 | first author: Tadaki, K. | arXiv: 1808.09592 | DOI: 10.1038/s41586-018-0443-1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the spatial and kinematic structure of molecular gas in the compact starburst core of the z=4.3 SMG AzTEC-1, and is the starburst disk gravitationally unstable?  
  > "We map out for the first time the spatial and kinematic structure of molecular gas inside the heavily dust-obscured core." (abstract)
- Target **COSMOS AzTEC-1**: coordinates _not stated_; z/distance z=4.342  
  > "determined a spectroscopic redshift of z=4.342" (Methods); "An angular scale of 0.1″ corresponds a physical scale of 670 pc." (Methods); distance from LMT CO observations (Yun et al. 2015); H0=70, OmegaM=0.3, OmegaL=0.7  
  > "determined a spectroscopic redshift of z=4.342" (Methods); "An angular scale of 0.1″ corresponds a physical scale of 670 pc." (Methods)

## Data provenance

- ALMA projects: 2017.1.00300.S, 2017.A.00032.S
- bands: Band 3 (CO 4-3, CI 1-0); Band 4 (CI 2-1)  
  > "with ALMA band-3 and Band-4 receivers in 2018 March" (Methods)
- frequencies and spectral setup: CO(4-3) at 86.309 GHz observed; coverage 85.4-89.1 and 97.5-101.2 GHz  
  > "covering the frequency range of 85.4-89.1 GHz and 97.5-101.2 GHz" (Methods)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10 (2017 Oct) and C43-8 (2017 Nov)  
  > "The observations were executed in 2017 October (C43-10 array configuration) and November (C43-8)." (Methods)
- baselines: 41 m-16.2 km  
  > "in two array configurations with baseline lengths of 41 m-16.2 km" (Methods)
- angular resolution: 0.093″×0.072″ natural; 0.069″×0.058″ briggs  
  > "0.093″×0.072″ (624 pc×483 pc in physical scale)" (Methods)
- max recoverable scale: 1.15″ at 86.3 GHz  
  > "corresponding to the maximum recoverable scale of 1.15″ at 86.3 GHz" (Methods)
- sensitivity: 1σ=78 μJy per 30 km/s (natural); 87 μJy (briggs)  
  > "1σ=78 μJy per 30 km s [-1]" (Methods)
- time on source: 5.8 h and 1.2 h; total 14 h including overhead  
  > "On-source time is 5.8 hours and 1.2 hours, respectively." (Methods)
- observing dates: 2017 Oct-Nov (CO); 2018 Mar (CI)  
  > "The observations were executed in 2017 October (C43-10 array configuration) and November (C43-8)." (Methods)
- pi or archival as stated: _not stated_
- Line: CO 4-3 (461.040 GHz)
- Line: CI 1-0 (492.161 GHz)
- Line: CI 2-1 (809.342 GHz)
- Other facility **LMT**: CO(4-3) flux and redshift  
  > "Follow-up observations with Redshift Search Receiver on the Large Millimeter Telescope (LMT) detected CO (4-3) and CO (5-4) lines" (Methods)
- Other facility **Multiwavelength catalogs (Subaru, VISTA, Spitzer, Herschel, VLA)**: SED photometry  
  > "(Subaru [37], VISTA [37], Spitzer [37], Hershel [38,39], VLA [40] )" (Methods)
- External data: Previous 0.02″ ALMA 860 μm continuum data; clump identification  
  > "we also made a 0.055″×0.042″ map of 860 μm continuum emission using the previous ALMA data [13]" (Methods) [from Iono, D. et al. 2016 (cite: 13)]
- External data: Photometry for SED  
  > "We collected the photometric data for AzTEC-1 from the latest multi-wavelength catalogs" (Methods) [from Laigle et al. 2016 etc. (cite: 37-40)]

## Processing

### Calibration

- pipeline or manual: CASA used for calibration; details not given  
  > "We utilize the Common Astronomy Software Application package (CASA) [35] for the data calibration." (Methods)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "We used CASA/ tclean task with natural weighting to make a cube with a velocity width of 30 km s [-1]" (Methods)
- deconvolver: _not stated_
- weighting robust: natural; briggs robust=0.5 for high-res cube  
  > "with a briggs weighting of robust =0.5" (Methods)
- uv taper: 0.03″ for 860 μm map  
  > "We adopted a uv-taper of 0.03″, resulting in the rms level of 47 μJy." (Methods)
- cell size: _not stated_
- image size: _not stated_
- masking: clean to 2σ in circular mask radius 0.4″  
  > "We cleaned down to the 2σ noise level in a circular mask with a radius of 0.4″." (Methods)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub, continuum excluding 86.1-86.5 GHz  
  > "excluding 86.1-86.5 GHz, and then subtracted it from the visibility data in the u-v plane using CASA/ uvcontsub task" (Methods)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: imsmooth to match CI(1-0) beam  
  > "using CASA/ imsmooth task" (Methods)
- final beam: 0.093″×0.072″  
  > "0.093″×0.072″ (624 pc×483 pc in physical scale)" (Methods)
- final rms: 78 μJy per 30 km/s  
  > "1σ=78 μJy per 30 km s [-1]" (Methods)

### Inherited from earlier work

- 860 μm continuum data and clump identification from earlier ALMA observations  
  > "we also made a 0.055″×0.042″ map of 860 μm continuum emission using the previous ALMA data [13]" (Methods) [from Iono et al. 2016 (cite: 13)]
- CI excitation temperature and mass formulae  
  > "T ex =38.8 K/ln(2.11/ R CI ) [ 45]" (Methods) [from Weiss et al. 2003 (cite: 45)]

### Not stated but needed to reproduce (our reading)

- Calibration details and CASA version
- Line-free channels for CI continuum subtraction
- Cell and image size
- Flux calibrators and flux scale uncertainty
- GalPaK3D priors and settings
- Rotation curve/velocity dispersion beam-smearing correction details
- Project code for 860 μm data (Iono 2016) and 2015.1.01345.S usage

## Analysis recipe

1. **Image CO(4-3), CI and continuum**: uvcontsub then tclean, moment maps with immoments  
  > "We made the CO moment maps of velocity-integrated intensity, velocity field and velocity dispersion" (Methods)
   - software: CASA
   - parameter: 30 km/s channels; 2σ threshold for moment 1/2  
  > "The 2σ threshold was adopted to exclude noise for creating the velocity field and velocity dispersion maps." (Methods)
   - fitting: _not stated_
   - validation: ALMA flux compared to LMT flux  
  > "which is comparable with an ALMA flux of S CO dv =1.60±0.13 Jy km s [-1] in dv =390 km s [-1]" (Methods)
2. **SED fit for SFR, Mstar, Mdust**: MAGPHYS fit to photometry from optical to radio  
  > "Using the MAGPHYS code [41,42], we fit the observed SED to stellar population synthesis models [43]" (Methods)
   - software: MAGPHYS
   - assumption: Chabrier IMF  
  > "a Chabrier initial mass function [34]" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive gas masses (CO, CI, dust)**: CO luminosity with alpha_CO and R41; CI mass from Tex and XCI; dust-based with gas-to-dust ratio  
  > "The CO (4-3) luminosity also gives a gas mass of M CO,gas =(6.6±0.6)×10 [10] ×( α CO /0.8)×(1.0/ R 41 ) M" (Methods)
   - assumption: alpha_CO=0.8, R41=0.91, XCI=4e-5  
  > "we adopt a gas excitation of R 41 =0.91" (Methods)
   - fitting: _not stated_
   - validation: CO-based and CI-based masses made consistent  
  > "For the consistency between CI and CO, we adopt a gas excitation of R 41 =0.91" (Methods)
4. **Fit disk kinematics**: GalPaK3D thick exponential disk with arctan rotation curve fitted to natural-weighted cube  
  > "We fit the natural-weighted CO cube with dynamical models of a disk galaxy using GalPaK 3D code [55]." (Methods)
   - software: GalPaK3D
   - parameter: 10 free parameters; 20000 MCMC iterations  
  > "Model galaxies have 10 free parameters" (Methods)
   - assumption: disk thickness q_int=0.15  
  > "if we assume a disk thickness of q int =0.15" (Methods)
   - fitting: MCMC; median and 95% interval of last 60% of chain  
  > "We adopted the median and the 95% confidence interval of the last 60% of the Malkov Chain Monte Carlo (MCMC) chain" (Methods)
   - validation: Model spectra compared to data along major axis  
  > "The observed CO kinematics is well characterized by a rotating disk model." (Methods)
5. **Compute surface densities and Toomre Q**: Pixel-wise Sigma_gas and Sigma_SFR; Q=κσ/(πGΣ) with κ=1.4 vmax/R, Qcri=0.67  
  > "assuming a flat rotation curve with κ=1.4v max / R [58]" (Methods)
   - assumption: Sigma_SFR traced by 860 μm flux scaled to total SFR  
  > "Since the 860 μm continuum flux density, S 860μm, traces star formation, we compute SFR surface densities in each pixel" (Methods)
   - fitting: linear fit of log Sigma_SFR vs log Sigma_gas  
  > "a linear function of log(Σ SFR /" (main text)
   - validation: Three independent gas mass tracers give Q<1  
  > "All three methods indicate that the Q value is less than unity in the central 2.5 kpc region" (main text)

## Software

- **CASA** : calibration, uvcontsub, tclean, immoments, imsmooth  
  > "We utilize the Common Astronomy Software Application package (CASA) [35] for the data calibration." (Methods)
- **MAGPHYS** : SED fitting  
  > "Using the MAGPHYS code [41,42]" (Methods)
- **GalPaK3D** : 3D disk kinematic modelling  
  > "using GalPaK 3D code [55]" (Methods)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disk half-light radius | 1.05 | +0.02/-0.02 | kpc | 4 | R 1/2 =1.05 [+0.02] -0.02 kpc |
| Maximum rotation velocity | 227 | +5/-6 | km/s | 4 | v max =227 [+5] -6 km s [-1] |
| Velocity dispersion sigma_0 | 74 | +1/-1 | km/s | 4 | σ 0 =74 [+1] -1 km s [-1] |
| Total CO(4-3) flux | 1.84 | 0.17 | Jy km/s | 1 | S CO,total dv =1.84±0.17 Jy km s [-1] |
| CI-based gas mass | 7.2e10 | 1.3e10 | Msun | 3 | M CI,gas =(7.2±1.3)×10 [10] |
| CI excitation temperature | 27.7 | 4.8 | K | 3 | T ex =27.7±4.8 K |
| Sigma_SFR vs Sigma_gas slope | 1.4 | 0.2 | dimensionless | 5 | (1.4±0.2)×log(Σ gas / |

## Qualitative findings

- Gas distribution clumpy with underlying rotation-supported disk; two CO clumps aligned with 860 μm clumps  
  > "The gas distribution is clumpy while the underlying disk is rotation-supported." (abstract)

## Claim tuples

- H: The starburst disk is gravitationally unstable | E: Compute Toomre Q from CO, CI and dust gas masses with GalPaK3D kinematics | R: Q below critical over the central 2.5 kpc for all three tracers | F: Disk is gravitationally unstable | **supported**
- H: The core is rotation-dominated | E: 3D kinematic modelling of CO cube | R: vmax/σ0=3.1±0.1 | F: Rotating disk | **supported**
- H: Gas depletion time is short | E: Gas mass over SFR | R: consumed within 100 Myr | F: Comparable to merging starbursts | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: alpha_CO=4 rejected since CO-based gas mass would exceed CI-based mass  
  > "is not appropriate since the CO-based gas mass substantially exceeds the CI-based one" (Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Other faint clumps not detected due to sensitivity  
  > "Other faint star-forming clumps are not detected in the CO data, probably due to the lack of the sensitivity." (main text)
- Caveat (inferred, ours): Gas mass depends on assumed alpha_CO, R41, XCI
- Caveat (inferred, ours): Q computed without beam-smearing correction locally
- Caveat (inferred, ours): Single galaxy
- Caveat (inferred, ours): Q_cri for thick disk vs two-component

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration/pipeline details
- Missing: GalPaK3D configuration
- Missing: Exact imaging parameters
- Data volume (inferred): ~100-300 GB raw for long-baseline Band 3 data
- Score (inferred): 4/5, Data public in ALMA archive and key steps described, but calibration and several imaging/fit settings are missing.
- Rediscovery candidate: no, Public status not stated in the paper and several settings are missing.

## Links

- Method: Bouche et al. 2015 (cite: 55) (GalPaK3D)
- Method: da Cunha et al. 2008 (cite: 41) (MAGPHYS)
- Companion: Iono et al. 2016 (cite: 13) (Previous 860 μm ALMA observations of AzTEC-1)
- Companion: Yun et al. 2015 (cite: 32) (LMT CO and [CII] observations)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2012.1.00978.S",
  "2015.1.01345.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 50,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
