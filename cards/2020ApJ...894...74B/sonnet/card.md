# Protoplanetary Disks in the Orion Nebula Cluster: Gas-disk Morphologies and Kinematics as Seen with ALMA

`2020ApJ...894...74B` | The Astrophysical Journal 2020 | first author: Boyden, Ryan D. | arXiv: 2003.12580 | DOI: 10.3847/1538-4357/ab86b7

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Do the dust-detected disks in the ONC have detectable CO(3-2) and HCO+(4-3) gas, and what are their sizes, kinematics, and dependence on distance from theta1 Ori C?  
  > "Here we examine the line data and investigate how gas in protoplanetary disks responds to a richly clustered environment, the typical environment of star and planet formation." (1 Introduction)
- Target **Orion Nebula Cluster (central 1.5' x 1.5')**: coordinates _not stated_; z/distance ~400 pc  
  > "At the distance to Orion, $\sim$400 pc (cite: Hirota07; Kraus07; Menten07; Sandstrom07; Kounkel17; Grob18; Kounkel18), the linear resolution is approximately 35 AU." (2 Observations); distance from Literature (Hirota07; Kraus07; Menten07; Sandstrom07; Kounkel17; Grob18; Kounkel18)  
  > "At the distance to Orion, $\sim$400 pc (cite: Hirota07; Kraus07; Menten07; Sandstrom07; Kounkel17; Grob18; Kounkel18), the linear resolution is approximately 35 AU." (2 Observations)

## Data provenance

- ALMA projects: 2015.1.00534.S
- bands: Band 7  
  > "mapped the central $1\rlap{.}'5$ $\times$ $1\rlap{.}'5$ region of the ONC at Band 7." (2 Observations)
- frequencies and spectral setup: 136 mosaic pointings; spws centered at 343, 345, 355, 358 GHz; 0.5 km/s channels (1 km/s resolution)  
  > "The map is comprised of 136 mosaicked pointings, with spectral windows centered at 343, 345, 355, and 358 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.09 arcsec (~35 AU)  
  > "The synthesized beam full width at half maximum (FWHM) is $0\rlap{.}''09$." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~0.1 mJy/beam  
  > "The unprecedented level of sensitivity ($\sim$0.1 mJy beam$^{-1}$)" (abstract)
- time on source: _not stated_
- observing dates: 2016 September 13  
  > "Observations were taken on 2016 September 13." (2 Observations)
- pi or archival as stated: Cycle 4 program, PI Eisner; continuum data reduced by Eisner et al. 2018  
  > "Our Cycle 4 ALMA program (2015.1.00534.S; PI: Eisner)" (2 Observations)
- Line: CO 3-2 (345.796 GHz)
- Line: HCO+ 4-3 (356.734 GHz)
- Other facility **Carma-NRO Orion survey**: CO(1-0) maps showing background cloud brightness  
  > "the Carma-NRO Orion survey of CO$(1-0)$ (cite: Kong18) reveals a clear increase in cloud brightness" (3.2 Detections in Absorption)
- Other facility **Gaia**: parallaxes for HC253, 170-337, 173-236  
  > "We searched the GAIA archive and found measured parallaxes only for HC253, 170-337, and 173-236." (5.5 Dynamical Masses)
- External data: 104 continuum sources, dust fluxes, dust masses, free-free fractions, spectroscopic masses  
  > "we searched the data cubes towards the positions of the 104 sources detected in the 850 $\mu$m continuum by (cite: Eisner18)." (3 Results) [from (cite: Eisner18)]
- External data: CO(3-2) model disk flux grid used to infer gas masses  
  > "compares the integrated CO $(3-2)$ fluxes of our ONC gas detections with the integrated CO $(3-2)$ fluxes of the models of (cite: WB14)." (5.1 Gas Flux Distribution) [from (cite: WB14)]
- External data: Lupus gas-disk radii  
  > "The gas-disk radii for Lupus are taken from (cite: Ansdell18)" (5.2 Gas Size Distribution) [from (cite: Ansdell18)]
- External data: Taurus gas-disk radii  
  > "For Taurus, the gas-disk radii are taken from (cite: Najita18)" (5.2 Gas Size Distribution) [from (cite: Najita18)]
- External data: Stellar L and Teff for 6 sources  
  > "The measurements for 170-337, HC401, HC253, HC422, 173-236, and 167-231 are taken from a new study by M. Fang in preparation (cite: Eisner18)" (5.5 Dynamical Masses) [from Fang in prep (cite: Eisner18)]
- External data: L and Teff for 177-341W  
  > "the measurements for 177-341W are taken from (cite: DaRio12)." (5.5 Dynamical Masses) [from (cite: DaRio12)]
- Simulation/model as data: Pre-MS evolutionary tracks: Baraffe15, Feiden16 magnetic/non-magnetic, Bressan12, Chen14  
  > "We considered the following evolutionary tracks: the models of (cite: Baraffe15), the magnetic and non-magnetic tracks of (cite: Feiden16), the PARSEC models of (cite: Bressan12), and the updated PARSEC models of (cite: Chen14)." (5.5 Dynamical Masses)

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

- task: CASA tclean  
  > "generated CO$(3-2)$ and HCO$^+$$(4-3)$ data cubes using the CASA task `tclean`." (2 Observations)
- deconvolver: _not stated_
- weighting robust: robust = 0.5  
  > "cleaned with a robust weighting parameter of 0.5." (2 Observations)
- uv taper: uv cut: none and 100 kλ tested  
  > "When searching for line detections in the CO and HCO$^+$ mosaics, we considered no *uv* cut as well as a 100 k$\lambda$ *uv* cut." (2 Observations)
- cell size: 0.02 arcsec per pixel  
  > "We gridded the data at $0\rlap{.}''02$ per pixel" (2 Observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from line emission (method not given)  
  > "We subtracted the continuum from the line emission" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: 0.5 km/s channels, 1 km/s spectral resolution, 0-20 km/s  
  > "The data cubes cover $0-20$ km s$^{-1}$ with 0.5 km s$^{-1}$ channels, corresponding to a spectral resolution of 1 km s$^{-1}$." (2 Observations)
- final beam: 0.09 arcsec FWHM  
  > "The synthesized beam full width at half maximum (FWHM) is $0\rlap{.}''09$." (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction pipeline and continuum map  
  > "(cite: Eisner18) presented the continuum map and provide a detailed description of the data reduction pipeline." (2 Observations) [from (cite: Eisner18)]
- 100 kλ uv cut optimal for continuum  
  > "(cite: Eisner18) determined an optimal *uv* cut of 100 k$\lambda$ for the continuum map." (2 Observations) [from (cite: Eisner18)]
- Inclination/position angle convention  
  > "Our setup for inclination and position angle follows the conventional setup as outlined by (cite: Czekala15; Czekala16)" (4.1 Model Disk) [from (cite: Czekala15; Czekala16)]
- Gas radius definition (90% flux curve of growth) for regional comparison  
  > "we recompute the gas-disk radius to match the definition employed by (cite: Ansdell18)" (5.2 Gas Size Distribution) [from (cite: Ansdell18)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details (only referred to Eisner18)
- Line-free channels for continuum subtraction
- Clean threshold, niter, mask, and mosaic imaging parameters
- Primary beam correction details
- Per-source F and vsys ranges, MCMC walkers, steps, and prior ranges
- Exact aperture/rms for upper limits and stacking
- Regression method details for size vs d_toc
- Spectral resolution element definition relative to Hanning smoothing

## Analysis recipe

1. **Make continuum-subtracted line cubes**: tclean on continuum-subtracted data, with and without 100 kλ uv cut  
  > "We subtracted the continuum from the line emission, and generated CO$(3-2)$ and HCO$^+$$(4-3)$ data cubes using the CASA task `tclean`." (2 Observations)
   - software: CASA
   - parameter: robust 0.5; 0.02" pixels; 0.5 km/s channels  
  > "cleaned with a robust weighting parameter of 0.5." (2 Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Detect gas at continuum source positions**: Inspect 0.5"x0.5" cutouts in channel maps for 3σ emission/absorption; moment maps for faint sources  
  > "We set a detection threshold of 3$\sigma$, where the noise level is calculated locally for each channel." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure gas sizes and fluxes**: Elliptical Gaussian fits to moment 0 maps with beam deconvolution; radius = HWTM major axis; flux summed within HWTM aperture  
  > "We define the gas radius as the half-width-tenth-maximum (HWTM) of the major axis of the 2D Gaussian fit." (3 Results)
   - assumption: distance 400 pc  
  > "At the distance to Orion, $\sim$400 pc" (2 Observations)
   - fitting: _not stated_
   - validation: Compared gas and dust inclinations, PAs and centroids  
  > "found broad agreement between the inclinations, position angles, and centroid positions derived from the gas and from the dust." (3 Results)
4. **Stack non-detections**: Average integrated emission maps of non-detections centered on continuum peaks  
  > "For each line, we compute the integrated emission maps of all non-detections and then average the set of images." (3.4 Stacked Non-detections)
   - fitting: _not stated_
   - validation: _not stated_
5. **Fit Keplerian model to channel maps for stellar masses**: Geometric flat Keplerian disk with power-law emission, 10 free parameters, fit in image plane over ~10^8 model grid then MCMC  
  > "We first generate a grid of $\sim10^{8}$ models over the range of parameters shown in Table [\[tab:grid_params\]]" (4.2 Fitting Procedure)
   - software: emcee
   - parameter: free: M*, r_in, R, i, theta, beta, vsys, x0, y0, F  
  > "Our final Keplerian model consists of synthetic channel maps as a function of position and velocity with 10 free parameters" (4.1 Model Disk)
   - assumption: flat axisymmetric disk, distance 400 pc  
  > "We assume a flat, axisymmetric disk that is rotating about a central mass $M_*$." (4.1 Model Disk)
   - fitting: chi2 minimization over grid, then emcee with flat priors set per source; best fit = minimum chi2, 1σ intervals  
  > "we run a MCMC fit with flat priors on the model parameters using the code `emcee`" (4.2 Fitting Procedure)
   - validation: reduced chi2 ~1, few residuals >3σ; CO and HCO+ fits of 177-341W agree  
  > "We also obtain reduced $\chi^2$ values approximately equal to 1 for all of the fits." (4.3 Best-fit Model Parameters)
6. **Compare CO fluxes with models for gas masses**: Compare measured CO(3-2) fluxes with WB14 model flux distributions  
  > "overlay the measured CO fluxes of gas-detected sources." (5.1 Gas Flux Distribution)
   - assumption: CO/H2 = 1e-4 (WB14)  
  > "the models of (cite: WB14) adopt a constant CO abundance relative to H$_2$ of $10^{-4}$" (5.1 Gas Flux Distribution)
   - fitting: _not stated_
   - validation: _not stated_
7. **Compare spectroscopic and dynamical masses**: Map L and Teff onto evolutionary tracks to get masses and ages, compare with dynamical masses  
  > "We mapped the stellar luminosities and effective temperatures onto different pre-MS evolutionary tracks and estimated the stellar masses and ages from each set of tracks." (5.5 Dynamical Masses)
   - software: pdspy
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : tclean imaging  
  > "using the CASA task `tclean`." (2 Observations)
- **emcee** : MCMC Keplerian fits  
  > "using the code `emcee` (cite: Foreman-Mackey13)" (4.2 Fitting Procedure)
- **pdspy** : compiling evolutionary tracks  
  > "We utilized the code `pdspy` (cite: Sheehan18) to compile the tracks." (5.5 Dynamical Masses)
- **Astropy** : listed in software acknowledgment  
  > "*Software:* `Astropy` (cite: astropy13)" (Conclusions)
- **Lifelines** v0.14.6: listed in software acknowledgment (use not stated)  
  > "CamDavidsonPilon/lifelines: v0.14.6" (References)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks detected in gas | 23 of 104 | not stated | sources | 2 | Out of the sample of 104 continuum-detected targets, we detected 23 in gas. |
| CO detections | 17 | not stated | sources | 2 | 17 were detected in CO$(3-2)$, 17 were detected in HCO$^+$$(4-3)$, and 11 were detected in both lines. |
| Mean HCO+ stacked flux of non-detections | 57 | 17 | mJy km/s | 4 | measure a mean flux of $\sim 57 \pm 17$ mJy km s$^{-1}$ |
| CO-to-dust size ratio | 1.77 | 0.1 | dimensionless | 3 | average CO-to-dust size ratio of $1.77 \pm 0.1$ |
| HCO+-to-dust size ratio | 1.25 | 0.02 | dimensionless | 3 | an average HCO$^+$-to-dust size ratio of $1.25 \pm 0.02$ |
| Combined gas-to-dust size ratio | 1.44 | 0.03 | dimensionless | 3 | a combined gas-to-dust size ratio of $1.44 \pm 0.03$ |
| Power-law slope of CO radius vs d_toc | 0.65 | 0.18 | dimensionless | 3 | obtained a power-law slope of $\alpha = 0.65 \pm 0.18$ for the CO data |
| Power-law slope of CO flux vs d_toc | 0.89 | 0.76 | dimensionless | 3 | $0.89 \pm 0.76$ |
| Gas-to-dust ratio | ~20-50 | not stated | dimensionless | 6 | yields gas-to-dust ratios of $\sim 20-50$ |
| K-S p-value gas-detected vs all dust masses | 0.003 | not stated | dimensionless | 2 | derive a p-value of 0.003 |
| Dynamical mass of 181-247 | 0.059 | +0.003/-0.007 | Msun | 5 | 181-247 & HCO$^+$ & 0.059\^0.003\_0.007 |
| Dynamical mass of HC189 | 1.294 | +0.006/-0.065 | Msun | 5 | HC189 & CO & 1.294\^0.006\_0.065 |

## Qualitative findings

- Gas is detected in emission, absorption, or both depending on location in the ONC; absorption lies against bright background cloud.  
  > "we see the line detections in emission, in absorption against the warm background, or in both emission and absorption." (abstract)
- ONC gas disks are compact (~50-200 AU), larger than dust but not correlated with dust size.  
  > "Gas sizes are universally larger than the dust sizes. However, the gas and dust sizes are not strongly correlated." (abstract)

## Claim tuples

- H: Are ONC gas disks smaller than those in low-density regions? | E: Compare ONC gas radius CDF with Lupus and Taurus | R: No ONC gas radii above 200 AU; >=40% of Lupus disks exceed ~200 AU | F: ONC gas disks are compact, linked to environment | **supported**
- H: Are gas disks influenced by photoionization from theta1 Ori C? | E: Regress gas size and flux against projected distance | R: Positive correlation of R_gas with d_toc, alpha=0.65±0.18 | F: External photoevaporation affects gas disks | **supported**
- H: Do dynamical masses match spectroscopic masses? | E: Keplerian fits vs evolutionary track masses | R: Only HC253 and HC401 agree within 2σ | F: Dynamical and spectroscopic masses are discrepant, possibly from systematics | **supported**
- H: Is gas kinematics consistent with Keplerian rotation? | E: Fit Keplerian model to 13 kinematic disk candidates | R: Reduced chi2 ~1 for all | F: Most are consistent with Keplerian rotation, with cloud contamination caveats | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Simple geometric model chosen because S/N too low for radiative transfer modeling  
  > "With our current observations, the S/N is too low to warrant the use of an extensive kinematic model in an initial assessment of the gas." (4 Keplerian Disk Modeling)
- Alternative: Fitting visibilities with multi-source model rejected as computationally inefficient  
  > "Fitting the visibilities to a multi-source Keplerian model has too many free parameters (10 per source) to be computationally efficient." (4.2 Fitting Procedure)
- How they decided it was enough: _not stated_
- Limitation (authors): Cloud contamination and low S/N limit Keplerian modeling  
  > "the biggest limitation in improving the accuracy and precision of the fitting is the quality of our data." (5.4 Assessment of the Keplerian Modeling)
- Limitation (authors): Individual source distances uncertain; dynamical mass scales linearly with distance  
  > "The dynamical mass scales linearly with distance" (5.5 Dynamical Masses)
- Caveat (inferred, ours): Grid plus MCMC with narrowed priors and minimum-chi2 adoption may underestimate uncertainties
- Caveat (inferred, ours): Several fits hit grid boundaries or fit cloud emission
- Caveat (inferred, ours): Gas mass inference depends on WB14 models with ISM CO abundance
- Caveat (inferred, ours): Fluxes in absorption/emission contaminated by cloud

## Reproducibility

- Data public (paper): ALMA data cited by project code (public archive implied but not stated)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA #2015.1.00534.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: _not stated_
- Missing: Custom Keplerian grid/MCMC code not released
- Missing: Calibration details deferred to Eisner18
- Missing: Per-source MCMC settings
- Data volume (inferred): Large mosaic Band 7 dataset (136 pointings), likely several hundred GB raw
- Score (inferred): 3/5, Public data and clear imaging parameters, but code unreleased and many fitting settings and calibration details unstated.
- Rediscovery candidate: no, Calibration inherited from earlier paper and the custom modeling lacks complete settings.

## Links

- Method: (cite: Eisner18) (Data reduction and continuum survey)
- Method: (cite: Czekala15) (Keplerian modeling convention)
- Companion: (cite: Eisner18) (Continuum survey of same ALMA data)
- Related: Carma-NRO Orion survey

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
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
  "facts": 93,
  "stated": 56,
  "rate": 0.602
 },
 "evidence_ok": true
}
```
