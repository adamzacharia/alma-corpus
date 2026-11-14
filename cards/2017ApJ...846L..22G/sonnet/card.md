# ALMA Resolves the Molecular Gas in a Young Low-metallicity Starburst Galaxy at z = 1.7

`2017ApJ...846L..22G` | The Astrophysical Journal Letters 2017 | first author: González-López, Jorge | arXiv: 1708.07898 | DOI: 10.3847/2041-8213/aa87af

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: high_z_galaxies
- Question: How are molecular gas, dust and CO excitation distributed in the lensed low-metallicity starburst RCS0327 at z=1.7 once the arc is reconstructed in the source plane?  
  > "In this letter we present the CO and continuum emission of the second-brightest optical giant arc discovered to date, the arc RCSGA 032727–132609 (hereafter RCS0327)" (Introduction)
- Target **RCS0327 (RCSGA 032727–132609)**: coordinates _not stated_; z/distance z = 1.7037455  
  > "At the redshift for RCS0327 of $z = 1.7037455 \pm 0.000005$ (cite: Wuyts2014)" (Observations); distance from Wuyts et al. 2014  
  > "At the redshift for RCS0327 of $z = 1.7037455 \pm 0.000005$ (cite: Wuyts2014)" (Observations)

## Data provenance

- ALMA projects: 2015.1.00920.S
- bands: _not stated_
- frequencies and spectral setup: two overlapping SPWs on the line and two for continuum in each observation  
  > "In each observation, two overlapping spectral windows (SPWs) were placed to detect the line and two were placed to detect continuum." (Observations)
- continuum bandwidth: _not stated_
- arrays: array configuration C36-1  
  > "Both emission lines were observed using the array configuration C36-1." (Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: CO(3-2) natural beam 2.54"x1.85"; CO(6-5) 1.49"x0.98" natural, tapered to 2.16"x2.08"  
  > "The data for CO(3-2) was imaged using natural weighting returning a synthesized beam size of 2.54$''$$\times$1.85$''$" (Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: January 1st and 10th 2016  
  > "The observations of the lines CO(6-5) and CO(3-2) were carried out during January 1st and 10th 2016." (Observations)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (127.895 GHz (observed))
- Line: CO 6-5 (255.746 GHz (observed))
- Other facility **HST**: imaging used for the lensing model and clump positions  
  > "allowing us to incorporate the detailed lensing model that is already available, based on HST imaging (cite: Sharon2012)" (Discussion)
- External data: Lensing model deflection field based on HST imaging  
  > "allowing us to incorporate the detailed lensing model that is already available, based on HST imaging (cite: Sharon2012)" (Discussion) [from Sharon2012]
- External data: SED SFR of clumps a–f, 9.0 Msun/yr  
  > "which have a combined spectral energy distribution of ${\rm SFR}=9.0_{-1.5}^{+8.3}\,{\rm M}_{\odot}\,{\rm yr}^{-1}$ (cite: Wuyts2014)" (Discussion) [from Wuyts2014]
- External data: Total SFR 29±8 Msun/yr used as upper limit  
  > "We use the estimated total ${\rm SFR}=29\pm8\,{\rm M}_{\odot}\,{\rm yr}^{-1}$ in the same region derived by (cite: Sharon2012)" (Discussion) [from Sharon2012]
- External data: SMG CO(3-2)/CO(1-0) luminosity ratio 0.66  
  > "$L'_{\rm CO(3-2)}/L'_{\rm CO(1-0)}=0.66$ (cite: Carilli_Walter2013)" (Discussion) [from Carilli_Walter2013]

## Processing

### Calibration

- pipeline or manual: ALMA-provided scripts with cycle 3 pipeline  
  > "The reduction of the data was performed using the scripts provided by ALMA and used the pipeline version for cycle 3" (Observations)
- casa version: 4.5.1  
  > "casa (cite: Mcmullin2007) version 4.5.1" (Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (passband and amplitude); phase calibrator J0336-1302  
  > "The passband and amplitude calibrator for both observations was J0423-0120, with J0336-1302 being used as phase calibrator." (Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: casa clean  
  > "The imaging of the calibrated data was done using the casa task `clean`." (Observations)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "The data for CO(3-2) was imaged using natural weighting" (Observations)
- uv taper: taper on CO(6-5) to match CO(3-2) beam (values not given)  
  > "To achieve a beam size similar to CO(3-2), a taper is applied to the CO(6-5) data" (Observations)
- cell size: _not stated_
- image size: _not stated_
- masking: interactive, manual masks  
  > "The continuum and line images were interactively cleaned by manually masking out the emission." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: line-free channels, uvcontsub  
  > "The continuum emission is estimated by using the line free channels and then is subtracted from the $uv$ data using `uvcontsub`" (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: CO(3-2) 2.54"x1.85" PA -85.68; CO(6-5) tapered 2.16"x2.08" PA 59.64  
  > "a taper is applied to the CO(6-5) data to obtain a synthesized beam of 2.16$''$$\times$2.08$''$ at a position angle of 59.64$^\circ$." (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Source-plane lens model (held fixed) and clump definitions  
  > "During the fitting of the emission, the lensing model is held fixed and only the source plane emission model is allowed to vary." (Discussion) [from Sharon2012]
- uvmcmcfit uv-plane fitting method  
  > "we used `uvmcmcfit`,[^1] which is a `Python` implementation to fit emission models to interferometric data in the $uv$ plane (cite: Bussmann2013; Bussmann2015; Gonzalez-Lopez2017)" (Discussion) [from Bussmann2013; Bussmann2015; Gonzalez-Lopez2017]

### Not stated but needed to reproduce (our reading)

- Channel ranges used for continuum estimation
- Taper parameters for CO(6-5)
- clean threshold, cell and image size
- uvmcmcfit priors, walkers and iteration counts
- Modified uvmcmcfit code accepting the external deflection field
- Lens model files from Sharon2012
- How the continuum frequencies and bandwidth were set
- Details of the astrometric offset applied
- How SFR was apportioned to individual regions

## Analysis recipe

1. **Calibrate and image**: ALMA scripts, clean with natural weighting, taper for CO(6-5), 20 km/s cubes, uvcontsub  
  > "Data cubes using a spectral resolution of 20 km s$^{-1}$ were created for each of the emission lines." (Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure image-plane fluxes**: Extract spectra at e1, e2, u1+u2 and integrate over 127.874–127.976 GHz  
  > "We find that the region going from 127.874–127.976 GHz ($\approx239.3$ km s$^{-1}$) provides a good range for the total emission of the line." (Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Source-plane reconstruction**: Fit uv-plane visibilities with a 2D elliptical Gaussian source model through a fixed lens deflection field  
  > "The galaxy emission is fitted assuming a 2D elliptical Gaussian (special case of a Sérsic profile with $n=0.5$) while the lensing potential is fitted by a singular isothermal ellipsoid (SIE)." (Discussion)
   - software: uvmcmcfit
   - parameter: One Gaussian for each CO line; two Gaussians for 450 µm continuum  
  > "we needed two Gaussians in the source plane, since a single component was not enough to account for the whole observed flux outside the PB" (Discussion)
   - assumption: Gaussian source model adequate  
  > "supporting the usage of a simple 2d elliptical Gaussian function for the source model" (Discussion)
   - fitting: uvmcmcfit MCMC; sampler and priors not stated  
  > "we used `uvmcmcfit`,[^1] which is a `Python` implementation to fit emission models to interferometric data in the $uv$ plane" (Discussion, Source plane reconstruction)
   - validation: Residual maps from subtracting model visibilities  
  > "In all cases the best fit models appear to account for most of the observed emission." (Discussion)
4. **Gas mass and surface densities**: L'CO(1-0)=L'CO(3-2)/0.66; H2 mass with alpha_CO=0.8; divide by area from effective radius; SFR over area  
  > "Assuming a CO excitation level valid for SMGs of $L'_{\rm CO(3-2)}/L'_{\rm CO(1-0)}=0.66$ (cite: Carilli_Walter2013)" (Discussion)
   - assumption: alpha_CO = 0.8 (SMG/starburst value); alternative 4 or ~25 discussed  
  > "Because of RCS0327 being cataloged as a starburst, to estimate the molecular mass we will use the values estimated for SMGs and starbursts at high redshift." (Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Resolved regional properties**: 0.25" source-plane regions; 50 reconstructions from fitting iterations for significance; noise map propagated for 2σ upper limits  
  > "We use a set of 50 source plane reconstructions taken from the fitting iterations to estimate the significance of the detection in each region." (Discussion)
   - software: uvmcmcfit
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.5.1: calibration, clean imaging, uvcontsub  
  > "casa (cite: Mcmullin2007) version 4.5.1" (Observations)
- **uvmcmcfit** : uv-plane source-plane reconstruction (modified to use fixed lens deflection field)  
  > "We modified `uvmcmcfit` so that it uses a user provided lensing model deflection field" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Intrinsic CO(3-2) luminosity | 2.90e8 | +0.21/-0.23 e8 | K km/s pc^2 | 3 | $L'_{\rm CO(3-2)}=2.90_{-0.23}^{+0.21}\times10^{8}$ |
| Intrinsic CO(6-5) luminosity | 8.0e7 | +1.4/-1.3 e7 | K km/s pc^2 | 3 | $L'_{\rm CO(6-5)}=8.0_{-1.3}^{+1.4}\times10^{7}$ |
| Intrinsic 450 µm flux density | 23.5 | +26.8/-8.1 | µJy | 3 | $S_{450\,\mu m}=23.5_{-8.1}^{+26.8}$ |
| Magnification CO(3-2) | 33.1 | +5.0/-4.9 | dimensionless | 3 | $\mu_{\rm CO(3-2)}=33.1_{-4.9}^{+5.0}$ |
| Molecular gas surface density | 16.2 | +5.8/-3.5 | Msun/pc^2 | 4 | $\Sigma_{\rm H2}=16.2_{-3.5}^{+5.8}\,{\rm M}_{\odot}\,{\rm pc}^{-2}$ |
| SFR surface density | 0.54 | +0.89/-0.27 | Msun/yr/kpc^2 | 4 | $\Sigma_{\rm SFR}=0.54_{-0.27}^{+0.89}\,{\rm M}_{\odot}\,{\rm yr}^{-1}\,{\rm kpc}^{-2}$ |
| Intrinsic CO(6-5)/CO(3-2) flux ratio | 1.1 | 0.2 | dimensionless | 4 | $S_{\rm CO(6-5)}/S_{\rm CO(3-2)}=1.1\pm0.2$ |

## Qualitative findings

- CO and dust lie on the star-forming clumps, with dust extending to regions faint in CO(3-2)  
  > "The continuum dust emission follows a similar angular extension and distribution as the molecular gas but also extending towards parts of the galaxy not as bright in CO(3-2), showing a clear spatial offset." (Conclusion)

## Claim tuples

- H: Is RCS0327 a starburst relative to local spirals at similar gas density? | E: Compared Sigma_SFR and Sigma_H2 with literature relations | R: Falls above the Daddi2010 relation with alpha_CO=0.8 | F: Supports a merger-driven starburst; position depends strongly on alpha_CO | **supported**
- H: Is RCS0327 similar to local BCDs? | E: Compared its properties with BCDs and used the alpha_CO–metallicity relation | R: alpha_CO~25 would put it near the MS with depletion time ~1 Gyr | F: Low-density starburst similar to BCDs, though conclusions are alpha_CO dependent | **partially**
- H: What is the CO excitation level and does it vary spatially? | E: CO(6-5)/CO(3-2) ratios globally and in source-plane regions | R: 1.1±0.2 overall; <0.3 in region 10 to 3.0±0.9 in region 9 | F: Peak at J~5, with higher excitation in clumps | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: uv-plane fitting retains the maximum information from the data  
  > "Exploring the emission in the $uv$ plane should return the maximum amount of information from the observations" (Discussion)
- Alternative: Fitting the lens and source together from ALMA alone was rejected because the HST model is better  
  > "outperforms in complexity and quality to the model we could find by fitting the lensing potential and source structure together using only the ALMA observations" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Coarse resolution; results depend strongly on alpha_CO  
  > "Our coarse observations already show that RCS0327 is not well described by a single mode star-forming galaxy" (Conclusion)
- Caveat (inferred, ours): Gas mass depends on an assumed alpha_CO and r31 spanning 0.8 to 25
- Caveat (inferred, ours): Single Gaussian source model with fixed lens model; lens uncertainties not propagated
- Caveat (inferred, ours): Only low resolution data (~2 arcsec)
- Caveat (inferred, ours): The SFR upper limit mixes sources of differing definition

## Reproducibility

- Data public (paper): ALMA project cited in acknowledgments; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00920.S." (Acknowledgments)
- Products in archive: _not stated_
- Code: uvmcmcfit public on GitHub; modified version not stated as released  
  > "<https://github.com/sbussmann/uvmcmcfit>" (Discussion)
- Missing: Lens model files
- Missing: Modified uvmcmcfit
- Missing: MCMC settings and priors
- Missing: Continuum channels
- Data volume (inferred): ~10-30 GB raw for two short C36-1 observations
- Score (inferred): 3/5, Data are likely public and methods are standard, but key fitting and imaging settings plus the modified code and lens model are missing.
- Rediscovery candidate: no, Recipe is incomplete: needs the external lens model and a modified fitting code, and fit settings are unstated.

## Links

- Method: Bussmann2013; Bussmann2015; Gonzalez-Lopez2017 (uvmcmcfit implementation)
- Companion: Sharon2012 (HST lens model and clump definitions)
- Companion: Wuyts2014 (redshift, SFR, kinematics)

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
