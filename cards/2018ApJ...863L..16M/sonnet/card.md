# The “Cosmic Seagull”: A Highly Magnified Disk-like Galaxy at z ≃ 2.8 behind the Bullet Cluster

`2018ApJ...863L..16M` | The Astrophysical Journal Letters 2018 | first author: Motta, V. | arXiv: 1808.02828 | DOI: 10.3847/2041-8213/aad6de

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: What are the kinematics (rotation curve at large radius), dynamical mass, stellar mass, gas content and star formation of the strongly lensed galaxy SMM J0658 (Cosmic Seagull) behind the Bullet Cluster?  
  > "which facilitates precise measurements of the kinematics at the outskirts of this dusty, star-forming galaxy." (Introduction)
- Target **SMM J0658 ('Cosmic Seagull')**: coordinates _not stated_; z/distance z=2.7779 (abstract); z=2.7793 (Introduction)  
  > "galaxy SMM J0658 at z=2.7793 (cite: 2012A&A...543A..62J), hereafter called the ‘Cosmic Seagull’" (Introduction); distance from Johansson et al. 2012 (cite: 2012A&A...543A..62J) for z in Introduction  
  > "galaxy SMM J0658 at z=2.7793 (cite: 2012A&A...543A..62J), hereafter called the ‘Cosmic Seagull’" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01559.S, 2012.1.00261.S
- bands: Band 3 (CO(3-2) at 91.50 GHz) and Band 6 (continuum at 231 GHz)  
  > "We used the Atacama Large Millimeter/submillimeter Array (ALMA) band-3 to observe the redshifted CO(3–2) line at 91.50 GHz, and also band-6 to target the continuum centered at 231 GHz" (ALMA Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: 7.5 GHz (band 6)  
  > "over a 7.5 GHz bandwidth (project 2015.1.01559.S)" (ALMA Observations)
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5"x0.7" (band 3), 0.5"x0.8" (band 6)  
  > "achieving a synthesised beam of $0.5''\times 0.7''$ for band 3 and $0.5''\times 0.8''$ for band 6" (ALMA Observations)
- max recoverable scale: _not stated_
- sensitivity: CO cube rms 0.2 mJy/beam per 7.8 MHz (26 km/s) channel; continuum 9 uJy/beam (band 3), 25 uJy/beam (band 6)  
  > "The final CO(3-2) cube has a root mean squared (RMS) noise of 0.2 mJy beam$^{-1}$ per 7.8 MHz (26 km s$^{-1}$) channel width in band-3." (ALMA Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: 2015.1.01559.S data via P.I. scripts; 2012.1.00261.S archival (PI J. Richard)  
  > "Calibrated $u$-$v$ products were obtained using the scripts provided to the P.I." (ALMA Observations)
- Line: CO J=3-2 (not stated (observed at 91.50 GHz))
- Other facility **HST/WFC3**: F110W and F160W photometry of A0 for SED  
  > "data from HST/WFC3 (F110W and F160W), Spitzer/IRAC 3.6, 4.5, 5.8 and 8.0 $\mu$m bands" (Methods, Results and Discussion)
- Other facility **Spitzer/IRAC**: 3.6, 4.5, 5.8, 8.0 um photometry of A0 for SED  
  > "Spitzer/IRAC 3.6, 4.5, 5.8 and 8.0 $\mu$m bands" (Methods, Results and Discussion)
- Other facility **ATCA**: previous CO(1-0) and (3-2) observations at ~2" resolution  
  > "Previous observations with the Australia Telescope Compact Array (ATCA) (cite: 2012A&A...543A..62J) at $\sim$2” resolution" (ALMA Observations)
- External data: Best published lens model of the Bullet Cluster, used as the base model  
  > "we employ the best model published to date (cite: 2016A&A...594A.121P) (which did not consider $\mathscr{A}0$)" (Methods, Results and Discussion) [from (cite: 2016A&A...594A.121P)]
- External data: Typical L'CO(3-2)/L'CO(1-0) ratio of 0.56  
  > "a typical ratio (cite: 2013ARA&A..51..105C) of $L'_{\rm CO(3-2)}/L'_{\rm CO(1-0)}=0.56$" (Methods, Results and Discussion) [from (cite: 2013ARA&A..51..105C)]

## Processing

### Calibration

- pipeline or manual: Scripts provided to the PI (Pipeline-Cycle3-R4-B)  
  > "using the scripts provided to the P.I.  (version Pipeline-Cycle3-R4-B)" (ALMA Observations)
- casa version: CASA 4.7.2  
  > "Common Astronomy Software Application (CASA version 4.7.2)" (ALMA Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: clean  
  > "The imaging was performed with clean using a Briggs weighting (robust $=0.5$)" (ALMA Observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The imaging was performed with clean using a Briggs weighting (robust $=0.5$)" (ALMA Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: manual cleaning to 3 sigma with masks at source positions  
  > "The sources were cleaned manually down to a 3 $\sigma$ level, using masks at source positions." (ALMA Observations)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub using line-free channels  
  > "The continuum in each band was calculated excluding channels presenting line emission, and subtracted from the visibilities with the task uvcontsub." (ALMA Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.5"x0.7" band 3; 0.5"x0.8" band 6  
  > "achieving a synthesised beam of $0.5''\times 0.7''$ for band 3" (ALMA Observations)
- final rms: 0.2 mJy/beam per 26 km/s channel (CO); 9 uJy/beam band 3, 25 uJy/beam band 6 continuum  
  > "the noise level is 9$\mu$Jy beam$^{-1}$ in band-3 and 25$\mu$Jy beam$^{-1}$ in band-6" (ALMA Observations)

### Inherited from earlier work

- Source-plane reconstruction method  
  > "We perform a source-plane reconstruction (cite: 2012ApJ...746..161S) by ray-tracing the images" (Methods, Results and Discussion) [from (cite: 2012ApJ...746..161S)]
- Velocity-field fitting procedure  
  > "We adopt a fitting procedure (cite: 2012MNRAS.426..935S) to search for four free parameters" (Methods, Results and Discussion) [from (cite: 2012MNRAS.426..935S)]
- Half-light radius from tilted rings  
  > "construct tilted rings to estimate the radii (cite: 2017MNRAS.466..892M)" (Methods, Results and Discussion) [from (cite: 2017MNRAS.466..892M)]
- Lens model mass components and base model  
  > "three dark matter clumps (cite: 2009ApJ...706.1201B; 2016A&A...594A.121P)" (Methods, Results and Discussion) [from (cite: 2009ApJ...706.1201B; 2016A&A...594A.121P)]

### Not stated but needed to reproduce (our reading)

- Line-free channels and velocity range for uvcontsub
- Number of clean iterations, image size and cell size
- Which spectral windows/channels define the moment maps
- Lens model parameter files from Paraficz et al. 2016 (shared privately)
- Swinbank velocity-field fitting code (shared privately), priors and starting values
- MAGPHYS settings, aperture definitions and photometry values
- Number of ALMA execution blocks, configurations and dates
- Rest frequency used for CO(3-2) and velocity zero point

## Analysis recipe

1. **Calibrate, image and make moment maps**: Pipeline scripts, concat, uvcontsub, clean (Briggs), immoments  
  > "Moment maps were produced using task immoments, excluding pixels below 4$\sigma$." (ALMA Observations)
   - software: CASA
   - parameter: robust = 0.5; moment maps exclude pixels below 4 sigma  
  > "Moment maps were produced using task immoments, excluding pixels below 4$\sigma$." (ALMA Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Lens model optimisation**: LENSTOOL Bayesian optimisation of a nearby galaxy PIEMD, constrained by CO centroids, starting from published cluster model  
  > "We fixed the galaxy position (X,Y), adopt a Pseudo-Isothermal Elliptical Mass Distribution (cite: 2005MNRAS.356..309L), and optimize the remaining parameters with broad uniform priors." (Methods, Results and Discussion)
   - software: LENSTOOL
   - fitting: Bayesian optimisation with broad uniform priors  
  > "optimize the remaining parameters with broad uniform priors" (Methods, Results and Discussion)
   - validation: rmsi = 0.09" and chi2/dof of 1.2; magnification uncertainty from +-1 sigma models gives 10%  
  > "a $\chi^2$ per degree of freedom of $1.2$" (Methods, Results and Discussion)
3. **Reconstruct source plane**: Ray-trace A1 and A2 through best-fit lens model  
  > "we ‘unlensed’ the observed images, $\mathscr{A}1$ and $\mathscr{A}2$ (Figure [2](#source_rec)), to the source plane" (Methods, Results and Discussion)
   - software: LENSTOOL
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit rotation curve and derive dynamical mass**: 2D arctan velocity model fit with four free parameters, centered on the continuum peak; thick-disk approximation  
  > "we fit the two-dimensional velocity map by assuming an arctan velocity profile model" (Methods, Results and Discussion)
   - parameter: free parameters: V_asym, r_t, PA, inclination  
  > "the asymptotic rotational velocity $V_{\rm asym}$, the turnover radius $\rm r_t$ (cite: 1997AJ....114.2402C), the position angle $PA$, and the disk inclination $i$" (Methods, Results and Discussion)
   - assumption: thick disk; dynamical center at the continuum peak  
  > "we consider a thick disk approximation" (Methods, Results and Discussion)
   - fitting: _not stated_
   - validation: Freeman exponential disk model tried but gave no improved fit  
  > "A Freeman model (exponential disk) was also tried, but this did not provide an improved fit." (Footnote 2)
5. **Stellar mass and SFR from SED of A0**: Aperture photometry from HST, Spitzer, ALMA band 6; MAGPHYS fit  
  > "Using the MAGPHYS Bayesian SED fitting code (cite: 2008MNRAS.388.1595D; 2015ApJ...806..110D)" (Methods, Results and Discussion)
   - software: MAGPHYS
   - parameter: A0 magnification mu = 4 (+-10%); 2.1 kpc lens-corrected aperture  
  > "it is expected to have a magnification of $\mu = 4$ ($\pm$10% error)" (Methods, Results and Discussion)
   - fitting: _not stated_
   - validation: consistent with Gonzalez et al. 2010 stellar mass  
  > "consistent with previous results within the errors (cite: 2010ApJ...720..245G)" (Methods, Results and Discussion)
6. **Molecular gas mass, gas fraction and depletion time**: CO(3-2) flux to L'CO, scaled to CO(1-0), times alpha_CO upper limit from M_dyn - M_star  
  > "an upper limit for $\alpha_{\rm CO}$ of $3.0\,{\rm M_\odot\,(K\,km\,s^{-1}\,pc^2)^{-1}}$ derived from the dynamical mass ($M_{H_2}\leq M_{dyn}-M_{star}$)" (Methods, Results and Discussion)
   - assumption: L'CO(3-2)/L'CO(1-0)=0.56; constant SFR for depletion time  
  > "Assuming a constant SFR, we estimate a molecular gas depletion time" (Methods, Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: calibration products, concat, uvcontsub, clean, immoments  
  > "Common Astronomy Software Application (CASA version 4.7.2)" (ALMA Observations)
- **LENSTOOL** : lens modelling and source reconstruction  
  > "The reconstruction of the source was performed using the LENSTOOL code (cite: 2007NJPh....9..447J)" (Methods, Results and Discussion)
- **MAGPHYS** : SED fitting for stellar mass, SFR and dust mass  
  > "Using the MAGPHYS Bayesian SED fitting code" (Methods, Results and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Dynamical mass (inclination corrected) within r=2.6 kpc | 6.3e10 | 0.7e10 | Msun | 4 | The dynamical mass corrected by inclination is $(6.3\pm0.7) \times 10^{10} \rm M_{\odot}$ inside $2.6 \pm 0.1$ kpc. |
| Inclination | 59 | 2 | deg | 4 | We found a best inclination of $i=(59\pm 2)^{\circ}$ |
| Rotational velocity | 323 | 8 | km/s | 4 | $V_{\rm rot}=(323 \pm 8)$ km s$^{-1}$ |
| Stellar mass | 1.6e10 | +1.9/-0.86 e10 | Msun | 5 | $1.6^{+1.9}_{-0.86} \times 10^{10} \, M_{\odot}$ |
| SFR | 190 | 10 | Msun/yr | 5 | (190$\pm$10)  M$_\odot$ yr$^{-1}$ |
| Maximum molecular gas mass | 4.7e10 | 1.4e10 | Msun | 6 | $M_{\rm H_2} = (4.7\pm1.4)\times10^{10}\,M_\odot$ |
| Gas depletion time | >=0.25 | 0.08 | Gyr | 6 | $\geq 0.25\pm0.08$ Gyr |
| Magnification ranges | A1: 11-22; A2: 13-50 | 10% | dimensionless | 2 | $\mu_{\mathscr{A}1} \approx 11-22$ and $\mu_{\mathscr{A}2} \approx 13-50$ (with an estimated $\pm$10% error) |

## Qualitative findings

- Rotation curve keeps rising to 2.5 kpc (~1.6 r_1/2,CO), with no evidence of a decline  
  > "the rotational velocity increases as a function of galactocentric radius as far as our observations extend" (Methods, Results and Discussion)
- A third unpredicted lensed image (A0) was found  
  > "This image was not predicted by any previous lensing model" (ALMA Observations)

## Claim tuples

- H: Does the high-z galaxy rotation curve decline at large radius? | E: Fit arctan model to the source-plane CO(3-2) velocity map | R: Rotation curve rising out to 2.5 kpc | F: No evidence of a decreasing rotation curve | **supported**
- H: Is the galaxy gas dominated and not a major merger? | E: Dynamical, SED stellar and CO gas masses; continuum-kinematic centre coincidence | R: f_gas <= 80+-20%, depletion time >=0.25 Gyr | F: Gas-dominated disk, not in a major merger | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: A0 used for stellar mass because it is little affected by neighbors and differential magnification  
  > "this image is preferred as it is not significantly affected by near neighbors" (Methods, Results and Discussion)
- Alternative: Freeman exponential disk model gave no improved fit  
  > "A Freeman model (exponential disk) was also tried, but this did not provide an improved fit." (Footnote 2)
- How they decided it was enough: _not stated_
- Limitation (authors): A3 could not be confirmed because local RMS is too high  
  > "the local RMS $\sim$ 0.3 mJy beam$^{-1}$ at 230 GHz is too high at that position" (Methods, Results and Discussion)
- Caveat (inferred, ours): The lens model does not predict A0, so its magnification mu=4 is uncertain
- Caveat (inferred, ours): The alpha_CO upper limit is circular (derived from M_dyn - M_star)
- Caveat (inferred, ours): Thick-disk and pressure support corrections are not detailed
- Caveat (inferred, ours): Single rotation-curve model; no stated priors or sampler

## Reproducibility

- Data public (paper): Archival ALMA data from projects 2015.1.01559.S and 2012.1.00261.S  
  > "ADS/JAO.ALMA #2012.1.00261.S, ADS/JAO.ALMA #2015.1.01559.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: Lens model parameter files (shared privately)
- Missing: Velocity-fitting code (shared privately)
- Missing: HST/Spitzer photometry values and MAGPHYS setup
- Missing: Imaging cell/image sizes and line-free channels
- Data volume (inferred): ~50-100 GB raw for two projects
- Score (inferred): 3/5, Public ALMA data and clear high-level recipe, but key lens model and fitting code are private and many settings are missing.
- Rediscovery candidate: no, Lens model and kinematic code are not available, so the numeric results cannot be redone from the text alone.

## Links

- Method: (cite: 2007NJPh....9..447J) (LENSTOOL)
- Method: (cite: 2012MNRAS.426..935S) (velocity-field fitting procedure)
- Method: (cite: 2008MNRAS.388.1595D) (MAGPHYS)
- Companion: (cite: 2012A&A...543A..62J) (Previous ATCA CO observations of SMM J0658)
- Companion: (cite: 2016A&A...594A.121P) (Bullet Cluster lens model)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 49,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
