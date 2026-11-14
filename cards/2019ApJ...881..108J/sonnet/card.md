# New Constraints on the Dust and Gas Distribution in the LkCa 15 Disk from ALMA

`2019ApJ...881..108J` | The Astrophysical Journal 2019 | first author: Jin, Sheng | arXiv: 1907.00571 | DOI: 10.3847/1538-4357/ab2dfe

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What gas and dust surface density profiles and disk mass of the LkCa 15 disk best reproduce the ALMA 12CO 3-2 radial intensity profile, channel maps and 0.87 mm continuum?  
  > "Here, we fit the gas and dust surface density profiles based on the high-resolution dust continuum image and CO 3-2 line maps obtained from the ALMA." (Introduction)
- Target **LkCa 15**: coordinates _not stated_; z/distance 140 pc  
  > "It is located in the Taurus-Auriga star-forming region at a distance of 140 pc from the Earth(cite: vandenAncker1998)." (Introduction); distance from van den Ancker et al. 1998  
  > "It is located in the Taurus-Auriga star-forming region at a distance of 140 pc from the Earth(cite: vandenAncker1998)." (Introduction)

## Data provenance

- ALMA projects: 2012.1.00870.S
- bands: Band 7 (345 GHz, 880 μm)  
  > "ALMA Band 7 (345 GHz, 880 $\mu m$)" (2 Observation)
- frequencies and spectral setup: 12CO centered 345.796 GHz, 1885 channels of 122.06 kHz (0.106 km/s); 13CO 330.588 GHz; C18O 329.331 GHz; continuum 4 spws of 64 channels  
  > "The $^{12}$CO 3–2 data were obtained with a spectral window centered on 345.796 GHz, with 1885 channels of 122.06 kHz (0.106 km s$^{-1}$) channel width." (2 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 12CO 0.36''x0.23''; 13CO 0.28''x0.21''; C18O 0.30''x0.23''; continuum 0.23''x0.17''  
  > "The angular resolution of the dust continuum image is 0.23$\ensuremath{''}\times$0.17$\ensuremath{''}$ (32 AU x 23 AU)." (2 Observation)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: August 17 and August 29, 2014  
  > "The LkCa 15 was observed at August 17 and August 29, 2014" (2 Observation)
- pi or archival as stated: ALMA program PI Pérez, L. M.  
  > "in ALMA program 2012.1.00870.S (PI Pérez, L. M.)" (2 Observation)
- Line: 12CO J=3-2 (centered 345.796 GHz)
- Line: 13CO J=3-2 (centered 330.588 GHz)
- Line: C18O J=3-2 (centered 329.331 GHz)
- External data: Stellar properties: L ~0.74 Lsun, M ~1.0 Msun, age 2-5 Myr  
  > "LkCa 15 is a 2-5 Myr old K5 star with $L_{\star}$ $\sim$ 0.74 $L_{\odot}$ and $M_{\star}$ $\sim$ 1.0 $M_{\odot}$ (cite: Kenyon1995; Simon2000)." (Introduction) [from (cite: Kenyon1995; Simon2000)]
- Simulation/model as data: 4096-model grid of parametric disk models (RADMC-3D) compared with the observed radial profile  
  > "they are used for all the 4096 runs in the parameter space." (3.1 surface density profile and parameter grid)

## Processing

### Calibration

- pipeline or manual: CASA ALMA pipeline 5.4.0 listed under software  
  > "CASA ALMA pipeline 5.4.0" (Software)
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

- Photodissociation boundary procedure (vertically integrated H nuclei column threshold)  
  > "We follow the same procedure as in that of (cite: Qi2011) and (cite: Rosenfeld2013)" (3.2 physical model) [from (cite: Qi2011); (cite: Rosenfeld2013)]
- Dust opacities calculated similarly to earlier work  
  > "The dust opacities used in this work were calculated similar to that of (cite: Isella2009)." (3.2 physical model) [from (cite: Isella2009)]

### Not stated but needed to reproduce (our reading)

- Imaging details (tclean parameters, weighting, robust, cell/image size) for the continuum and line cubes
- Calibration details and flux scale uncertainty
- Continuum subtraction and line-free channels
- Moment-map and radial-profile extraction details (inclination, PA, bins, noise/error estimation)
- Disk inclination, position angle and systemic velocity used in the models
- Gas temperature/microturbulence and line broadening used for line radiative transfer
- Number of photon packages and grid settings in RADMC-3D
- Stellar luminosity/mass values used in the model
- Chi-square definition and how the observed noise was set

## Analysis recipe

1. **Make moment-0 maps and radial profiles**: Azimuthally averaged radial intensity profiles extracted from zero-moment maps of continuum and CO lines  
  > "The observed radial intensity profiles of CO isotopes and dust continuum emission in the LkCa 15 disk were obtained by extracting the azimuthal averaged intensity of the zero-moment maps shown in Figure 1." (3.1 surface density profile and parameter grid)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit the dust continuum profile**: Fit a fixed dust surface density profile to the observed continuum radial profile  
  > "These values are determined by fitting the azimuthal averaged radial intensity profile of the observed dust continuum map" (3.1 surface density profile and parameter grid)
   - software: RADMC-3D
   - parameter: RC = 66 AU, gamma = -0.15, RC_arctan = 66 AU, gamma_arctan = 5.35, Mdust = 9.8e-5 Msun  
  > "we adopt a fixed dust density profile of $RC = 66$ AU, $\gamma = -0.15$, $RC_{\rm arctan} = 66$ AU, $\gamma_{\rm arctan} = 5.35$" (3.1 surface density profile and parameter grid)
   - assumption: mm-dust scale height 0.1 x 1 AU x (r/20 AU)^1.25; opacity at 1 mm 13.2 cm2/g  
  > "The resulting dust opacity at the wavelength of 1 mm is 13.2 cm$^2$ g$^{-1}$." (3.2 physical model)
   - fitting: _not stated_
   - validation: reduced chi2 of dust profile  
  > "Then we calculate the reduced $\chi^{2}$ for dust continuum emission between the radial intensity profiles of the model and the ALMA observation." (3.2 physical model)
3. **Compute self-consistent disk temperature for each gas model**: Iterate Monte Carlo radiative transfer and hydrostatic equilibrium until temperatures agree within 3%  
  > "the difference between two temperature structures is within 3% everywhere" (3.2 physical model)
   - software: RADMC-3D
   - parameter: Teff = 4350 K blackbody star; dust-to-gas ratio 0.001 for micron dust  
  > "We assume the host star of LkCa 15 is a black-body radiator with an effective temperature of 4350 K." (3.2 physical model)
   - assumption: MRN size distribution n(a)~a^-3.5, 5e-6 to 1e-2 mm; opacity at 1 um 5.2e3 cm2/g  
  > "between a minimum grain size of $5 \times 10^{-6}$ mm and a maximum grain size of $1 \times 10^{-2}$ mm" (3.2 physical model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Grid search of gas surface density for 12CO**: Compute 12CO channel and moment-0 maps for 4096 models (8^4 grid of Mdisk, gamma, RC_arctan, gamma_arctan), subtract continuum, convolve with Gaussian beam, compare azimuthal radial profile with reduced chi2  
  > "Then, we search the parameter space to obtain the best-fit model that has the least reduced $\chi^2$ of the radial intensity profile of $^{12}$CO emission." (3.1 surface density profile and parameter grid)
   - software: RADMC-3D
   - parameter: RC fixed at 12500 AU; no exponential cutoff in gas  
  > "we fix the $RC$ at 12500 AU to slow down the decrease of the gas density at the outer part of the disk" (3.1 surface density profile and parameter grid)
   - parameter: Photodissociation threshold 2.0e20 H nuclei; CO freeze-out below 20 K  
  > "We include the freeze-out effect of CO by setting the number density of $^{12}$CO to zero at the region where temperature is below 20 K." (3.2 physical model)
   - assumption: 12CO/H2 = 1.4e-4 by mass  
  > "we assume the abundance ratio of $^{12}$CO/H$_2$ to be 1.4 $\times 10^{-4}$ in mass" (3.2 physical model)
   - fitting: Brute-force grid search, minimum reduced chi2; no sampler  
  > "We set up a four-dimensional parameter space of these four free parameters." (3.1 surface density profile and parameter grid)
   - validation: Heat maps of chi2; comparison of channel maps of best-fit, high and low mass models with observation  
  > "In Figure 9 we compare the three models’ channel maps with the ALMA observation" (5.2 Constraint on the disk mass)
5. **Estimate 13CO abundance**: Manually adjust a power-law 12CO/13CO ratio, inner and outer 45 AU, using best-fit 12CO temperature structure  
  > "We separately fit the $\alpha$ for the inner and outer disk regions by manually adjusting $n_0$ and $\alpha$." (4.2 13CO image)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: reduced chi2 of 13CO = 0.33  
  > "The reduced $\chi^2$ of $^{13}$CO is derived to be 0.33." (4.2 13CO image)

## Software

- **RADMC-3D** v0.41: Monte Carlo radiative transfer for temperature, continuum and CO line maps  
  > "calculated using the Monte Carlo radiative transfer code RADMC-3D" (3.2 physical model)
- **CASA ALMA pipeline** 5.4.0: data reduction (as listed)  
  > "CASA ALMA pipeline 5.4.0" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Best-fit gas disk mass | 0.1 | not stated | Msun | 4 | $M_{\rm disk} = 0.1 M_{\odot}$, $\gamma = 4.0$, $RC_{\rm arctan} =  45$ AU, and $\gamma_{\rm arctan} = 10$ |
| Best-fit gamma | 4.0 | not stated | dimensionless | 4 | $\gamma = 4.0$ |
| Best-fit gas cavity radius | 45 | not stated | AU | 4 | $RC_{\rm arctan} =  45$ AU |
| Reduced chi2 of best-fit 12CO | 2.51 | not stated | dimensionless | 4 | The best-fit model results in a reduced $\chi^2$ of 2.51. |
| Reduced chi2 high-mass (0.33 Msun) and low-mass (0.033 Msun) models | 14.6 and 6.7 | not stated | dimensionless | 4 | The high-mass model result in a reduced $\chi^2$ of 14.6, and the low-mass model result in a reduced $\chi^2$ of 6.7. |
| Dust cavity radius / FWHM | ~65 AU / ~40 AU | not stated | AU | 2 | The dust continuum map shows an inner hole of $\sim$ 65 AU in radius, and the full width at half maximum of this dust cavity is at $\sim$ 40 AU. |
| Dust disk outer edge | ~200 | not stated | AU | 2 | The mm-size dust disk has an outer edge at $\sim$ 200 AU |
| Fitted dust mass | 9.8e-5 | not stated | Msun | 2 | a total dust mass of $M_{dust} = 9.8 \times 10^{-5} M_{\odot}$ |
| Midplane temperature at 100 AU and 500 AU | ~15 K and ~11 K | not stated | K | 3 | In the mid-plane, the temperature decreases from $\sim$ 15 K at 100 AU to $\sim$ 11 K at 500 AU. |
| Reduced chi2 of continuum for best-fit model | 255 | not stated | dimensionless | 2 | has a large reduced $\chi^2$ of 255 |

## Qualitative findings

- Gas disk extends to ~600 AU while mm dust ends at ~200 AU, consistent with dust drift and trapping  
  > "Such a discrepancy between the outer edges of the gas and dust disks is consistent with dust drifting and trapping models." (abstract)

## Claim tuples

- H: What gas disk mass and density profile reproduce the 12CO emission? | E: 4096-model grid search with RADMC-3D fit to the 12CO radial profile | R: Best fit Mdisk=0.1 Msun, gamma=4, cavity 45 AU, reduced chi2 2.51 | F: Gas disk ~0.1 Msun (for 12CO/H2=1.4e-4) with a 45 AU cavity | **supported**
- H: Is the disk mass degenerate with the density slope? | E: chi2 heat maps across the grid | R: Linear correlation between Mdisk and gamma among good fits | F: 12CO is optically thick, so a mass-gamma degeneracy exists | **supported**
- H: Can channel maps break the degeneracy? | E: Compare channel maps of best-fit, 0.33 and 0.033 Msun models | R: High- and low-mass models give double-cone too strong or too weak | F: ~0.1 Msun best reproduces channel morphology | **supported**
- H: Do gas and dust share the same outer edge? | E: Fit continuum profile and compare with the gas model | R: Dust edge ~200 AU vs gas ~600 AU | F: Consistent with dust drift and trapping | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Gas and dust cannot be fit with a single surface density profile, so two profiles are used  
  > "The dust continuum and the CO line emissions cannot be fitted using a single surface density profile." (3.1 surface density profile and parameter grid)
- Alternative: Larger photodissociation threshold of 5e20 fails to fit 12CO beyond ~400 AU  
  > "We find that it is hard to fit the $^{12}$CO intensity beyond $\sim$ 400 AU using a larger photodissociation threshold like 5.0 $\times 10^{20}$ in H nuclei" (3.2 physical model)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple power law underpredicts 12CO beyond ~400 AU; mass depends on the CO/H2 abundance  
  > "Note that the fitted disk mass depends on the abundance ratio of $^{12}$CO/H$_2$ in our model." (4.1 12CO intensity profile)
- Limitation (authors): 13CO fit is not self-consistent  
  > "it is not a self-consistent way as compared to the fitting of $^{12}$CO intensity" (4.2 13CO image)
- Caveat (inferred, ours): Grid is coarse and the chi2 comparison uses only the azimuthally averaged profile with a Gaussian beam rather than visibility-space fitting
- Caveat (inferred, ours): Photodissociation threshold and CO abundance fixed, so the mass is degenerate with them
- Caveat (inferred, ours): No uncertainties on best-fit parameters
- Caveat (inferred, ours): Inclination and geometry unspecified

## Reproducibility

- Data public (paper): ALMA archival program cited  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00870.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters and calibration details
- Missing: Disk geometry, kinematic and line-model settings
- Missing: Exact chi2 definition and noise estimates
- Data volume (inferred): ~50-100 GB raw for the archival Band 7 project
- Score (inferred): 4/5, Public data and a clearly specified model grid, but imaging and RT setup details are missing.
- Rediscovery candidate: no, Main results depend on an undisclosed RADMC-3D line setup and imaging, so exact reproduction is difficult.

## Links

- Method: (cite: Rosenfeld2013) (Photodissociation boundary method and Keplerian double-cone channel maps)
- Method: (cite: Isella2009) (Dust opacity model)
- Companion: (cite: Isella2012) (Earlier continuum and CO observations of LkCa 15)

## Checks

```json
{
 "quotes": 57,
 "quotes_ok": 57,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 37,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
