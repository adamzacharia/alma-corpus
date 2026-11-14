# Measurement of Circumstellar Disk Sizes in the Upper Scorpius OB Association with ALMA

`2017ApJ...851...85B` | The Astrophysical Journal 2017 | first author: Barenfeld, Scott A. | arXiv: 1711.04045 | DOI: 10.3847/1538-4357/aa989d

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: protoplanetary_disks
- Question: What are the radial extents of dust and CO gas in Upper Sco disks, and how do they compare with younger regions?  
  > "We fit power-law models to the dust surface density and CO $J$ = 3-2 surface brightness to measure the radial extent of dust and gas in these disks." (abstract)
- Target **57 disks in Upper Scorpius OB Association**: coordinates _not stated_; z/distance not stated (fluxes scaled to 140 pc for comparison)  
  > "The 5-11 Myr age of this association (cite: Preibisch2002; Pecaut2012)" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00395.S, 2011.0.00966.S
- bands: Band 7 (0.88 mm), mean 340.7 GHz Cycle 0 and 341.1 GHz Cycle 2  
  > "All observations used band 7, with a mean frequency of 340.7 GHz for Cycle 0 and 341.1 GHz for Cycle 2 (0.88 mm) and a total bandwidth of 7.5 GHz." (Sample & Observations)
- frequencies and spectral setup: one spectral window with 0.488 MHz channels (0.429 km/s) covering CO J=3-2  
  > "One spectral window was configured with channel widths of 0.488 MHz (0.429 km s$^{-1}$, the spectral resolution is twice the channel width)" (Sample & Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m array, Cycle 0 and Cycle 2  
  > "The ALMA observations were obtained in Cycle 0 and Cycle 2 using the 12 m array (see Paper I)." (Sample & Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.35'' to 0.73'', median 0.37''  
  > "The observations had angular resolution between 0$\overset{''}{.}$35 and 0$\overset{''}{.}$73 with a median of 0$\overset{''}{.}$37" (Sample & Observations)
- max recoverable scale: _not stated_
- sensitivity: continuum rms 0.13-0.26 mJy/beam, median 0.15  
  > "a continuum rms ranging from 0.13 mJy/beam to 0.26 mJy/beam, with a median of 0.15 mJy/beam." (Sample & Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.79599 GHz)
- Other facility **Spitzer and WISE**: identification of the disk-host candidate sample (via Luhman2012, Carpenter2006)  
  > "identified by (cite: Luhman2012) using *Spitzer* and *WISE* observations" (Sample & Observations)
- External data: SED-fit inner radii, h0 and p used as fixed values/priors  
  > "We fixed $R_{in}$ at the values found by the SED fitting of (cite: Mathews2013) for the 24 sources we share with their survey." (Continuum Modeling) [from (cite: Mathews2013)]
- External data: Tripathi2017 effective radii and size-luminosity relation for Taurus/Ophiuchus  
  > "(cite: Tripathi2017) found effective radii, defined as the radius containing 68% of the disk continuum flux, ranging from 19 au to 182 au, with a median of 48 au." (Dust Disk Sizes) [from (cite: Tripathi2017)]
- External data: Lupus effective radii and surface densities  
  > "(cite: Tazzari2017) measure effective radii ranging from 18 au to 129 au, with a median of 55 au." (Dust Disk Sizes) [from (cite: Tazzari2017)]

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

- Observations, source detections, positions, fluxes, stellar parameters, CO velocity ranges and fluxes come from Paper I  
  > "The observed visibilities were corrected to center the disk at the phase center of observations using the disk positions determined in Paper I." (Continuum Modeling) [from Paper I (Barenfeld et al. 2016)]
- Dust opacity from Pollack et al. mix  
  > "calculated as a function of wavelength using Mie theory for dust grains composed of a mix of carbons, ices, and silicates (cite: Pollack1994)" (Continuum Modeling) [from (cite: Pollack1994)]

### Not stated but needed to reproduce (our reading)

- Calibration and data reduction details (all in Paper I)
- MCMC walker number, steps, burn-in and priors on Sigma0, R_dust, inclination, PA
- RADMC-3D photon numbers and grid setup
- How visibilities were averaged and the moment 0 visibility construction
- Dust sublimation radius and temperature prescription details
- Stellar parameters per source (from Paper I)

## Analysis recipe

1. **Fit dust continuum visibilities**: Truncated R^-1 power-law dust surface density model with RADMC-3D temperature and images, Fourier transformed and compared with visibilities by chi^2  
  > "we compared our observed visibilities to the synthetic visibilities of a model disk, deriving the model visibilities from an assumed dust density distribution in a self-consistent way." (Continuum Modeling)
   - software: RADMC-3D, emcee
   - parameter: Free: Sigma0, R_dust, h0, p, inclination, position angle; R_in fixed; minimum temperature 10 K  
  > "was used to constrain $\Sigma_0$, $R_{dust}$, $h_0$, $p$, inclination, and position angle." (Continuum Modeling)
   - assumption: Uniform opacity, a^-3.5 size distribution, max grain size 1 cm; Gaussian vertical structure  
  > "with a grain size distribution of $n(a)\propto a^{-3.5}$ and a maximum grain size of 1 cm." (Continuum Modeling)
   - fitting: emcee MCMC; likelihood from real and imaginary visibility chi^2; values at posterior peak with 68.3% intervals  
  > "The uncertainties were defined as the bounds of the range around the peak containing 68.3% of the integrated probability." (Continuum Modeling)
   - validation: Residual images checked; point-source fits to 5 sigma residuals; alternative slopes -0.5 and -1.5 tested  
  > "Assuming $\Sigma \propto R^{-0.5}$ and $\Sigma \propto R^{-1.5}$ power laws resulted in slightly smaller or larger disk sizes" (Continuum Modeling)
2. **Fit CO surface brightness**: Fit truncated power-law surface brightness to moment 0 visibilities of continuum-subtracted data  
  > "we used the velocity range corresponding to the $J=3-2$ emission line, as determined by Paper , to generate integrated “moment 0 visibilities.”" (CO Modeling)
   - software: emcee
   - parameter: Free: S0, gamma, R_CO, inclination, PA  
  > "We used *emcee* to fit for the surface brightness normalization, $S_0$, the power law slope, $\gamma$, the outer radius, $R_{CO}$, the inclination, and position angle." (CO Modeling)
   - fitting: emcee, as for continuum  
  > "We used *emcee* to fit for the surface brightness normalization, $S_0$, the power law slope, $\gamma$, the outer radius, $R_{CO}$, the inclination, and position angle." (CO Modeling, CO Surface Brightness Fitting)
   - validation: CO channel maps inspected; one source excluded for cloud contamination  
  > "Examination of the CO channel maps suggested contamination by a surrounding molecular cloud and we therefore excluded this source from further CO analysis." (CO Modeling)
3. **Predict CO fluxes from dust models**: Add CO to posterior dust disks and compute J=3-2 flux with RADMC3D, with and without photodissociation  
  > "We used the results of our continuum modeling to predict the CO $J=3-2$ line flux from our continuum-detected disks assuming the gas and dust share the same spatial distribution." (Expected CO Fluxes)
   - software: RADMC-3D
   - parameter: CO freeze-out below 20 K; photodissociation below 1e21 cm^-2 H2 column, or none  
  > "At any location in a model disk where the temperature was less than 20 K, we assumed the CO was frozen onto dust grains and had an abundance of zero" (Expected CO Fluxes)
   - assumption: gas-to-dust 100, CO/H2 7e-5, shared temperature structure  
  > "with a gas-to-dust ratio of 100 and a CO to H$_2$ ratio of $7\times10^{-5}$ by number" (Expected CO Fluxes)
   - fitting: _not stated_
   - validation: Compared to observed fluxes from Paper I  
  > "For the sources not detected in CO, the model fluxes were consistent with observational upper limits." (Expected CO Fluxes)
4. **Compare sizes and surface densities with younger regions**: Compute effective radii (68%, 95% mass) and Sigma0 for matched spectral type/mass ranges and compare with Tripathi2017 and Tazzari2017  
  > "we can define an effective radius for our sample as containing 68% of the total dust mass" (Dust Disk Sizes)
   - parameter: S/N >= 15 threshold for well-constrained R_dust  
  > "to constrain the dust outer radius ($R_{dust}$) to better than a factor of 2 required a signal-to-noise of at least 15." (Dust Disk Sizes)
   - assumption: Optically thin dust, constant midplane temperature in outer disk; opacity 4.94 cm2/g at 890 um  
  > "our assumed dust opacity of $4.94$ cm$^{2}$ g$^{-1}$" (Implications for Disk Evolution)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADMC-3D** : dust temperature, model images, CO line fluxes  
  > "The Monte Carlo radiative transfer code RADMC-3D (cite: Dullemond2012) was used to determine the temperature throughout the model dust disk due to stellar irradiation." (Continuum Modeling)
- **emcee** : MCMC parameter fitting  
  > "The Markov chain Monte Carlo implementation *emcee* (cite: Foreman-Mackey2013) was used" (Continuum Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Median dust outer radius, 25 disks with S/N>=15 | 21 | not stated | au | 1 | The 25 disks that meet this threshold have dust outer radii ranging from 8 to 65 au, with a median of 21 au. |
| Dust radii range, all fitted disks | 4 to 173 | not stated | au | 1 | The dust disks range from 4 to 173 au in radius, although 82% of the disks have radii less than 50 au. |
| Median CO outer radius, 9 well-constrained disks | 54 | not stated | au | 2 | we measured radii ranging from 12 to 169 au, with a median of 54 au |
| Median effective radius (68%), K9-M5, Upper Sco | 14 | not stated | au | 4 | range from 5 au to 44 au, with a median of 14 au. |
| Median 95% radius, Upper Sco | 20 | not stated | au | 4 | we find a range of 7 au to 62 au, with a median of 20 au. |
| Mean log Sigma0, Upper Sco | -1.65 | std dev 0.42 | dex g cm^-2 | 4 | Upper Sco has a mean $\log\Sigma_0$ of $-1.65$, with a standard deviation of $0.42$. |

## Qualitative findings

- Dust disks in Upper Sco are ~3 times smaller than in Taurus, Ophiuchus and Lupus (not a uniform analysis)  
  > "these results suggest that the disks in Upper Sco are smaller than those found in Taurus, Ophiuchus, and Lupus by a factor of $\sim$3." (Dust Disk Sizes)

## Claim tuples

- H: Upper Sco dust disks are compact | E: Visibility fitting of R^-1 dust models | R: Median R_dust 21 au for 25 high S/N disks | F: Disks are extremely compact | **supported**
- H: Small sizes explain the CO non-detections | E: Predicted CO fluxes from dust models with shared gas and dust distribution | R: Model fluxes consistent with upper limits | F: CO depletion not required | **supported**
- H: CO is more extended than dust | E: Compared R_CO and R_dust for 7 disks | R: 4 of 7 have larger CO radii | F: Possibly due to CO optical depth | **partially**
- H: Upper Sco disks are smaller than younger disks | E: Compared effective radii with Tripathi2017 and Tazzari2017 | R: Factor ~3 smaller | F: Tentative size decrease with age | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Low S/N prevents fitting slope and radius together, so a fixed R^-1 single power law was adopted  
  > "The continuum signal-to-noise ratio for the majority of our sample is too low to simultaneously constrain the dust outer radius and the slope of the surface density power law." (Continuum Modeling)
- Alternative: Self-similar viscous profile and broken power law rejected given evolutionary state and low S/N  
  > "given the evolutionary state of the Upper Sco disks, it is not clear that this description is appropriate." (Continuum Modeling)
- How they decided it was enough: _not stated_
- Limitation (authors): Single-wavelength data cannot constrain dust opacity; CO likely optically thick so gas mass unconstrained  
  > "there is no way to constrain the dust opacity based on our single-wavelength data." (Continuum Modeling)
- Caveat (inferred, ours): Radii depend on assumed R^-1 profile and unresolved low-S/N fits
- Caveat (inferred, ours): Comparison with other regions uses different methods
- Caveat (inferred, ours): Uniform opacity and temperature assumptions

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Paper I calibration and imaging
- Missing: Own fitting code not released
- Missing: MCMC settings
- Data volume (inferred): ~100-200 GB raw for two ALMA projects
- Score (inferred): 3/5, Models and methods are described, but calibration is in Paper I, no code is released and MCMC settings are missing.
- Rediscovery candidate: no, Needs Paper I products and custom visibility-fitting code with unstated settings.

## Links

- Method: (cite: Dullemond2012) (RADMC-3D)
- Method: (cite: Foreman-Mackey2013) (emcee)
- Companion: Paper I (Barenfeld et al. 2016) (Source survey, observations and data reduction)
- Related: Lupus ALMA survey
- Related: Taurus/Ophiuchus disk sizes (Tripathi2017)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2011.0.00966.S"
 ],
 "obscore_codes_not_in_card": [
  "2011.0.00526.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 35,
  "rate": 0.479
 },
 "evidence_ok": true
}
```
