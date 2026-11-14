# Detection of Rydberg Lines from the Atmosphere of Betelgeuse

`2024ApJ...966L..13D` | The Astrophysical Journal Letters 2024 | first author: Dent, W. R. F. | arXiv: 2404.06501 | DOI: 10.3847/2041-8213/ad3afa

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars, stellar_physics
- Question: Are the emission lines near 232 GHz toward Betelgeuse Rydberg transition lines (H30alpha and a combined X30alpha of heavier elements), and what do they reveal about the extended atmosphere?  
  > "Emission lines from Rydberg transitions are detected for the first time from a region close to the surface of Betelgeuse." (abstract); "To examine whether the putative 232 GHz Rydberg transitions are consistent with atmospheric conditions surrounding Betelgeuse we computed" (Models and Discussion)
- Target **Betelgeuse**: coordinates ICRS 05:55:10.3435 +07:24:25.640 (measured stellar centre)  
  > "At a distance of 222 pc (cite: Harper2017b), Betelgeuse is the second-closest RSG after Antares" (Introduction); "We measure the stellar centre as ICRS 05:55:10.3435 +07:24:25.640 with" (Results); z/distance 222 pc  
  > "At a distance of 222 pc (cite: Harper2017b), Betelgeuse is the second-closest RSG after Antares" (Introduction); "We measure the stellar centre as ICRS 05:55:10.3435 +07:24:25.640 with" (Results); distance from Harper et al. 2017 (cite: Harper2017b)  
  > "At a distance of 222 pc (cite: Harper2017b), Betelgeuse is the second-closest RSG after Antares" (Introduction); "We measure the stellar centre as ICRS 05:55:10.3435 +07:24:25.640 with" (Results)

## Data provenance

- ALMA projects: 2022.A.00026.S
- bands: 1.40-1.29 mm (spectral windows 214.769 to 231.966 GHz)  
  > "four spectral windows centred at 214.769, 217.073, 220.266 and 231.966 GHz (1.40–1.29 mm)" (Observations)
- frequencies and spectral setup: Four spectral windows centred at 214.769, 217.073, 220.266 and 231.966 GHz; channel spacing 0.976 MHz; effective resolution 2.6 km/s at 232 GHz after Hanning smoothing  
  > "four spectral windows centred at 214.769, 217.073, 220.266 and 231.966 GHz (1.40–1.29 mm) with a spectral channel spacing of 0.976 MHz and an effective spectral resolution of 2.6" (Observations); "after Hanning smoothing." (Observations)
- continuum bandwidth: Total bandwidth 7.5 GHz in four spectral windows  
  > "We used a total bandwidth of 7.5 GHz in four spectral windows" (Observations)
- arrays: _not stated_
- configurations: Most extended configuration  
  > "Betelgeuse was observed using ALMA in its most extended configuration giving a maximum baseline of 15 km" (Observations)
- baselines: Maximum baseline 15 km  
  > "giving a maximum baseline of 15 km, in two executions on Aug 3 and Aug 27 2023." (Observations)
- angular resolution: Restoring beam (28.8x20.6) mas FWHM at PA 50 deg around 232 GHz; continuum beam (27x19) mas at PA 51 deg  
  > "The restoring beam at around 232 GHz is ($28.8\times20.6$) mas FWHM at PA $50^{\circ}$" (Observations); "using a restoring beam of ($27\times19$) mas FWHM at PA $51^{\circ}$" (Observations)
- max recoverable scale: 0.35 arcsec  
  > "The maximum recoverable scale is 0.35" (Observations)
- sensitivity: Continuum off-source noise 0.024 mJy/beam; 0.9 mJy/beam per spectral channel  
  > "achieving an off-source continuum noise level of 0.024 mJy beam" (Observations); "the noise level per spectral channel is $\sigma_{\mathrm {rms}} =0.9$ mJy beam$^{-1}$" (Observations)
- time on source: _not stated_
- observing dates: Aug 3 and Aug 27 2023 (two executions)  
  > "in two executions on Aug 3 and Aug 27 2023." (Observations)
- pi or archival as stated: _not stated_
- Line: H 30alpha (Rydberg) (231.9009 GHz)
- Line: X (combined Mg, Si, Fe and perhaps O, S) 30alpha (Rydberg cluster) (232.0232 GHz (abundance-weighted combined centre))
- Line: He 30alpha (Rydberg), not detected (231.9954 GHz)
- Other facility **VLA**: Radio continuum visibilities used to build the semi-empirical atmosphere model  
  > "derived from the VLA radio continuum visibilities from (cite: Lim1998)" (Models and Discussion)
- Other facility **Hubble Space Telescope**: Ultraviolet fluxes used to build the semi-empirical atmosphere model  
  > "ultraviolet (UV) fluxes (cite: 1994ApJ...428..329C)" (Models and Discussion)
- External data: Distance to Betelgeuse of 222 pc  
  > "At a distance of 222 pc (cite: Harper2017b)" (Introduction) [from Harper et al. 2017 (cite: Harper2017b)]
- External data: K-band angular diameter of 42.5 mas  
  > "spectro-interferometric angular diameter of 42.5 mas (cite: 2011A&A...529A.163O)" (Introduction) [from Ohnaka et al. 2011 (cite: 2011A&A...529A.163O)]
- External data: Rydberg-formula rest frequencies of 30alpha lines  
  > "Rest frequency from Rydberg formula (cite: Towle1996)" (Table 1) [from Towle et al. 1996 (cite: Towle1996)]
- External data: Relative TiO2 line intensities used to rule out TiO2 contribution  
  > "based on the relative CDMS/JPL intensities listed in" (Results) [from CDMS/JPL via Splatalogue (https://splatalogue.online/)]
- External data: Fe and C abundances for the line model  
  > "We adopt the Fe and C abundances from (cite: 2000ApJ...530..307C)" (Models and Discussion) [from Carr et al. 2000 (cite: 2000ApJ...530..307C)]
- External data: Isotopic ratio 12C/13C = 6  
  > "from (cite: 1984ApJ...284..223L)" (Models and Discussion) [from Lambert et al. 1984 (cite: 1984ApJ...284..223L)]
- External data: Si abundance and isotopic ratios  
  > "the Si abundance and isotopic ratios given in (cite: 2014A&A...561A..47O)" (Models and Discussion) [from Ohnaka 2014 (cite: 2014A&A...561A..47O)]
- External data: Solar abundances for Mg and S  
  > "Solar abundances (cite: Asplund2021) were adopted for Mg and S" (Models and Discussion) [from Asplund et al. 2021 (cite: Asplund2021)]
- External data: Non-thermal motion widths constrained by far-UV emission lines  
  > "consistent with the observed widths of narrow (low opacity) far-ultraviolet emission lines (cite: 2018ApJ...869..157C)" (Models and Discussion) [from Carpenter et al. 2018 (cite: 2018ApJ...869..157C)]
- External data: Mean electron density about 2e8 cm^-3 from C II] 2325 A emission  
  > "The mean electron density measured from the" (Models and Discussion) [from Judge & Carpenter 1998 (cite: Judge1998)]
- Simulation/model as data: Semi-empirical 1D thermodynamic atmosphere model of Betelgeuse (update of Harper et al. 2001) giving nH, ne, Te versus radius, used to compute 232 GHz continuum and H30alpha/X30alpha profiles  
  > "We have used an update of the model of (cite: 2001ApJ...551.1073H), to include the revised distance and photospheric Rosseland angular diameter." (Models and Discussion)
- Simulation/model as data: Spherical MARCS photospheric model (Teff = 3650, log g = -0.5) for the inner region  
  > "a spherical MARCS photospheric model with" (Models and Discussion)

## Processing

### Calibration

- pipeline or manual: Standard ALMA CASA pipeline calibrated measurement sets, then phase self-calibration  
  > "The standard calibrated measurement sets (visibility data) from the ALMA" (Observations); "were concatenated, and the line-free channels used to made a continuum image to provide a model for phase self-calibration in" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Standard pipeline-calibrated measurement sets were concatenated before self-calibration  
  > "The standard calibrated measurement sets (visibility data) from the ALMA" (Observations)
- flux calibrator: _not stated_
- flux scale uncertainty: ~7% flux scale accuracy; ~3 mas astrometric accuracy  
  > "The flux scale is accurate to $\sim7\%$ and the astrometric accuracy is $\sim$3 mas." (Observations)
- self calibration: Phase self-calibration using a continuum model from the line-free channels; calibration applied to all channels  
  > "to provide a model for phase self-calibration in" (Observations); "The calibration was applied to all spectral channels" (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Spectral cubes made before and after continuum subtraction  
  > "we made spectral image cubes before and after continuum subtraction" (Observations)
- line free channels: Line-free channels used for the continuum image (channel ranges not given)  
  > "the line-free channels used to made a continuum image" (Observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: Continuum restoring beam (27x19) mas at PA 51 deg; cube beam (28.8x20.6) mas at PA 50 deg  
  > "using a restoring beam of ($27\times19$) mas FWHM at PA $51^{\circ}$" (Observations); "The restoring beam at around 232 GHz is ($28.8\times20.6$) mas FWHM at PA $50^{\circ}$" (Observations)
- final rms: 0.024 mJy/beam (continuum, off-source); 0.9 mJy/beam per channel  
  > "achieving an off-source continuum noise level of 0.024 mJy beam" (Observations); "the noise level per spectral channel is $\sigma_{\mathrm {rms}} =0.9$ mJy beam$^{-1}$" (Observations)

### Inherited from earlier work

- Atmosphere model is an update of the Harper, Brown & Lim 2001 semi-empirical model; full details of the revision not given here  
  > "We have used an update of the model of (cite: 2001ApJ...551.1073H), to include the revised distance and photospheric Rosseland angular diameter." (Models and Discussion); "Full details of the revised semi-empirical model will be published elsewhere" (Models and Discussion) [from (cite: 2001ApJ...551.1073H)]
- Outer model scaled to the new distance following earlier work  
  > "The outer reaches of the 2001 model were scaled to the new distance as described in (cite: Harper2009)" (Models and Discussion) [from (cite: Harper2009)]
- Collisional (electron) broadening estimate uses an approximation from Brocklehurst & Seaton 1972, Eq. 4.8  
  > "Assuming the approximation from (cite: Brocklehurst1972) (Eq. 4.8) is applicable to" (Models and Discussion) [from (cite: Brocklehurst1972)]
- Full results (molecular lines, SiO and CO) of the same ALMA program deferred to a separate paper  
  > "Full results will be presented in a separate paper." (Introduction) [from separate later paper (not cited)]

### Not stated but needed to reproduce (our reading)

- CASA version used for calibration, self-calibration and imaging
- Pipeline version and whether the archive pipeline products were used unchanged
- tclean parameters: weighting and robust value, deconvolver, cell and image size, masks, number of iterations, threshold
- Line-free channel ranges used for the continuum and for continuum subtraction (and the method of subtraction)
- Self-calibration solution interval, number of rounds and solution mode
- Flux calibrator identity
- How the Voigt fits were done (fitting code, priors, fit range, error treatment)
- Aperture and annulus definitions for the radial profiles and azimuthal averaging
- Radiative transfer code and the revised atmosphere model tables (nH, ne, Te versus radius), which are not published in the paper
- Time on source per execution and PI of the program

## Analysis recipe

1. **Calibrate and self-calibrate, make continuum image**: Concatenate pipeline-calibrated measurement sets, image line-free channels as continuum, use it as the model for phase self-calibration, then solve for the stellar spectral index in the final continuum image  
  > "were concatenated, and the line-free channels used to made a continuum image to provide a model for phase self-calibration in" (Observations); "The final continuum image was made solving for the stellar spectral index" (Observations)
   - software: CASA
   - parameter: Phase calibrator J0552+0313, cycled every 80-90 seconds; bandpass calibrator J0510+1800  
  > "cycling to the phase calibrator J0552+0313" (Observations); "The bandpass was calibrated using J0510+1800." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make spectral cubes**: Apply the self-calibration to all spectral channels and image cubes before and after continuum subtraction  
  > "The calibration was applied to all spectral channels and we made spectral image cubes before and after continuum subtraction." (Observations)
   - software: CASA
   - parameter: Cube noise 0.9 mJy/beam per channel; beam (28.8x20.6) mas at PA 50 deg  
  > "the noise level per spectral channel is $\sigma_{\mathrm {rms}} =0.9$ mJy beam$^{-1}$" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Measure continuum size, stellar centre and flux**: Fit a 2D Gaussian to the 214-233 GHz continuum; measure the centre; sum flux in an image-plane aperture of radius 65 mas that encloses all emission  
  > "a 2D Gaussian component fitted to the 214–233 GHz continuum has a radius at FWHM (after deconvolution from the beam) of" (Results); "we found that an aperture of radius 65 mas ($R_{65}$) enclosed all the emission, both line and continuum" (Results)
   - fitting: 2D Gaussian component (details not given)  
  > "a 2D Gaussian component fitted to the 214–233 GHz continuum" (Results)
   - validation: _not stated_
4. **Extract and fit line spectra**: Extract continuum-subtracted integrated spectra in R65 (and central R11) in the stellar rest frame and fit Gaussian and Voigt profiles  
  > "shows the continuum-subtracted integrated spectrum taken within" (Results); "were better fitted by Voigt rather than Gaussian profiles." (Results)
   - parameter: Stellar rest frame with V* = V_helio = 20.9 km/s (V_lsr 4.9 km/s)  
  > "Fitted centre frequency in target frame adjusted to" (Table 1)
   - assumption: Line identification by Rydberg formula rest frequencies; TiO2 excluded using relative CDMS/JPL intensities  
  > "we conclude that there is no evidence of significant contribution from this species" (Results)
   - fitting: Voigt profiles (Gaussian + Lorentzian components) for H30alpha and X30alpha; sampler, priors and likelihood not stated  
  > "Combined FWHM, fitted using a Voigt profile" (Table 1)
   - validation: Voigt fit compared against Gaussian fit in the integrated spectra  
  > "were better fitted by Voigt rather than Gaussian profiles." (Results)
5. **Map the line emission and radial structure**: Make integrated line maps of H30alpha and X30alpha and azimuthally averaged projected radial profiles, find ring radii and azimuthal contrast  
  > "compares the angular distribution of the two RTLs and 1.3 mm stellar continuum emission across Betelgeuse" (Results); "lies in ring-like structures of radii 1.4 and 0.9" (Results)
   - parameter: Radius of peak emission is azimuthally averaged projected radius  
  > "Projected radius of peak emission, azimuthally-averaged." (Table 1)
   - fitting: _not stated_
   - validation: Datacubes checked for velocity differences between clumps; profiles checked for symmetry (masering test)  
  > "Closer examination of both datacubes show no significant velocity differences between the emission clumps" (Results)
6. **Compute model continuum and line profiles**: Solve spherical radiative transfer (LTE line and level populations with non-LTE ionization balance) in the semi-empirical atmosphere for the continuum and H30alpha/X30alpha, with Saha-Boltzmann level populations from nH and ne  
  > "The absolute level populations are derived from the Saha-Boltzmann equation from the atmospheric hydrogen and electron densities." (Models and Discussion); "was solved for the line and continuum." (Models and Discussion)
   - software: MARCS model atmosphere (inner region)
   - parameter: Species included: 12C, 13C, 23Na, 24Mg, 25Mg, 26Mg, 28Si, 29Si, 30Si, 32S, 56Fe plus H  
  > "We computed the X30" (Models and Discussion)
   - parameter: Continuum opacities: H free-free, H- free-free and metal- free-free  
  > "The continuum opacity sources included were H free-free" (Models and Discussion)
   - assumption: Upper and lower levels hydrogenic and populated in Boltzmann ratios  
  > "it was assumed the upper and lower levels are hydrogenic and populated in their Boltzmann ratios" (Models and Discussion)
   - assumption: Isotropic non-thermal motions ramping outward with radius (11 km/s at 1.3 R* to 23 km/s at 2.0 R*, FWHM)  
  > "we assume isotropic non-thermal motions ramping from 11" (Models and Discussion)
   - assumption: Mg, Fe, Si ionized gives ne = 1e-4 nH; C and S also fully ionized gives ne = 3e-4 nH  
  > "if Mg, Fe, Si are ionized then" (Models and Discussion)
   - assumption: A small H ionization fraction (1e-4) arbitrarily added to produce H30alpha emission  
  > "In the simulation we arbitrarily added a small H ionization fraction in the model to create the emission shown in the blue spectrum." (Models and Discussion)
   - fitting: No fitting; forward model compared to observed spectra  
  > "A comparison of the observed and model spectra is shown in Fig." (Models and Discussion)
   - validation: Model 232 GHz continuum flux density and disk size (convolved with ALMA beam) compared with observed values  
  > "The 232 GHz stellar continuum flux density was computed to be" (Models and Discussion)
7. **Estimate electron density from Lorentzian broadening**: Apply the Brocklehurst & Seaton (1972) Eq. 4.8 approximation to the Lorentzian component of H30alpha  
  > "Assuming the approximation from (cite: Brocklehurst1972) (Eq. 4.8) is applicable to" (Models and Discussion)
   - parameter: Te = 3000 K in emitting region from the model  
  > "using T$_e$ = 3000K in the emitting region from the model" (Models and Discussion)
   - assumption: Collisional broadening with electrons accounts for the Lorentzian component  
  > "one possibility is collisional broadening - with electrons, ions or neutrals." (Models and Discussion)
   - fitting: _not stated_
   - validation: Compared with chromospheric ne of about 2e8 cm^-3 (C II] 2325 A) and local densities that may reach 1e9  
  > "and (cite: Harper2006) show that the local density may reach" (Models and Discussion)

## Software

- **CASA** : Pipeline calibration, phase self-calibration and imaging  
  > "were concatenated, and the line-free channels used to made a continuum image to provide a model for phase self-calibration in" (Observations)
- **Splatalogue** : Looking up CDMS/JPL line intensities to test the TiO2 contribution  
  > "https://splatalogue.online/" (Footnote 1); "based on the relative CDMS/JPL intensities listed in" (Results)
- **MARCS** : Spherical photospheric model (Teff 3650, log g -0.5) for the inner part of the atmosphere model  
  > "a spherical MARCS photospheric model with" (Models and Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux density around 232 GHz in R65 | 297 | 20 | mJy | 3 | the continuum flux density around 232 GHz is 297$\pm$20 mJy |
| Disc-average continuum spectral index 214-233 GHz | approximately 1.7 | not stated | dimensionless | 3 | The disc-average spectral index between 214–233 GHz ($\alpha$) is approximately 1.7 |
| Continuum radius at FWHM at 232 GHz (deconvolved) | 30 | not stated | mas | 3 | has a radius at FWHM (after deconvolution from the beam) of $R_{\mathrm {232GHz}}$ = 30 mas. |
| Stellar centre (ICRS) | 05:55:10.3435 +07:24:25.640 | ~3 mas stochastic | sexagesimal | 3 | We measure the stellar centre as ICRS 05:55:10.3435 +07:24:25.640 with |
| H30alpha measured frequency | 231.9055 | 0.0004 (formal fit error) | GHz | 4 | 231.9055 |
| X30alpha measured frequency | 232.0255 | 0.0002 (formal fit error) | GHz | 4 | 232.0255 |
| H30alpha Voigt FWHM (Gaussian, Lorentzian components in brackets) | 42.6 (31.0, 19.4) | not stated | km/s | 4 | 42.6 (31.0,19.4) |
| X30alpha Voigt FWHM (Gaussian, Lorentzian components in brackets) | 21.5 (15.3, 10.2) | not stated | km/s | 4 | 21.5 (15.3,10.2) |
| H30alpha peak line flux (130 mas diameter aperture) | 50.6 | not stated | mJy | 4 | 50.6 |
| X30alpha peak line flux (130 mas diameter aperture) | 80.8 | not stated | mJy | 4 | 80.8 |
| H30alpha total intensity | 4.5e-19 | not stated | W m^-2 | 4 | $4.5\times10^{-19}$ |
| X30alpha total intensity | 5.7e-19 | not stated | W m^-2 | 4 | 5.7$\times10^{-19}$ |
| He30alpha peak line flux upper limit | <5 | not stated | mJy | 4 | $<$5 |
| Radii of peak emission for H30alpha and X30alpha | 1.4 R* (H30alpha), 0.9 R* (X30alpha); Table: 28 mas and 18 mas | not stated | R* / mas | 5 | lies in ring-like structures of radii 1.4 and 0.9 |
| Azimuthal variation in the X30alpha map | ~10% | not stated | percent | 5 | azimuthal variations of $\sim10\%$ are found in the X30$\alpha$ map |
| Observed blueshift of H30alpha and X30alpha peaks relative to V* | -5.9 (H30alpha), -3.0 (X30alpha) | not stated | km/s | 4 | appear to be blue-shifted relative to $V_{\star}$, by $-5.9$ and $-3.0$ |
| Model 232 GHz continuum flux density | ~300 | not stated | mJy | 6 | The 232 GHz stellar continuum flux density was computed to be $\simeq 300$ mJy in good agreement with the observed value. |
| Radius of continuum optical depth unity at 232 GHz in the model | ~1.3 R* | not stated | R* | 6 | the predicted surface of continuum optical depth unity at 232 GHz occurs at $\sim1.3R_\star$, in good agreement with observations. |
| Electron density implied by H30alpha Lorentzian component | ~3e8 | not stated | cm^-3 | 7 | would indicate an electron density of $\sim3\times 10^8\>{\rm cm}^{-3}$ |

## Qualitative findings

- X30alpha emission is smoother and more symmetric than H30alpha, indicating a different origin region  
  > "has more symmetric, less clumpy structure than either" (Results)
- No evidence of strong masering; weak amplification of the continuum may still occur  
  > "These characteristics suggest that the RTLs are not strongly masering" (Results)
- Both observed lines are blue-shifted relative to the model spectra by about 3 km/s (X30alpha) and 6 km/s (H30alpha)  
  > "lines appear blue-shifted with respect to the model spectra, by 3 and 6" (Models and Discussion)

## Claim tuples

- H: The emission lines near 232 GHz toward Betelgeuse are Rydberg transition lines (H30alpha and an X30alpha blend of heavier elements) | E: Compared observed line frequencies with Rydberg-formula rest frequencies, ruled out TiO2, and computed model line profiles from a semi-empirical atmosphere | R: Observed lines lie near the H30alpha and X30alpha cluster frequencies and the model reproduces the X30alpha emission on and off the disk | F: The lines are identified as H30alpha and X30alpha | **supported**
- H: Line wings are better described by Voigt than Gaussian profiles, with electron collisional broadening contributing | E: Fitted Voigt and Gaussian profiles to integrated spectra and applied a collisional broadening approximation to the H30alpha Lorentzian | R: Voigt fits are better; the Lorentzian component implies ne of about 3e8 cm^-3 | F: Electron densities in the hotter chromosphere are consistent with collisional broadening | **partially**
- H: H30alpha and X30alpha arise from different regions of the atmosphere | E: Imaged the lines and measured azimuthally averaged radial profiles | R: X30alpha is in a smooth ring near 0.9 R*; H30alpha is clumpy and peaks near 1.4 R* | F: X30alpha emission does not arise from the same region as H30alpha | **supported**
- H: A semi-empirical thermodynamic atmosphere reproduces the 232 GHz continuum and places the line emission appropriately | E: Computed continuum and line profiles with Saha-Boltzmann level populations from the model nH, ne and Te | R: Continuum flux of about 300 mJy and optical depth unity near 1.3 R*; X30alpha emitted where temperature and turbulence increase outward; line wings and velocity shifts not matched | F: Good agreement with continuum and line observations given simple assumptions; velocity differences remain unexplained | **partially**

## Reasoning

- Why this data: Observations came from a multi-band high-resolution program to study Betelgeuse after the Great Dimming  
  > "These observations were obtained as part of a multi-band high-resolution program to study this star after the Great Dimming event" (Introduction)
- Why this method: A semi-empirical atmosphere model was used to test whether the putative Rydberg lines are consistent with atmospheric conditions  
  > "To examine whether the putative 232 GHz Rydberg transitions are consistent with atmospheric conditions surrounding Betelgeuse we computed" (Models and Discussion)
- Alternative: TiO2 rejected as the origin of the lines  
  > "we conclude that there is no evidence of significant contribution from this species" (Results)
- Alternative: Zeeman broadening rejected as insufficient  
  > "which is insufficient to induce significant Zeeman broadening" (Models and Discussion)
- Alternative: Strong masering disfavoured  
  > "These characteristics suggest that the RTLs are not strongly masering" (Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Model ignores non-LTE level populations, so computed line fluxes are not over-interpreted  
  > "We choose not to over-interpret the computed line fluxes because we have ignored non-LTE level population effects that are likely to change opacities and source functions and alter the distribution of the emission." (Models and Discussion)
- Limitation (authors): Model is a mean 1D lukewarm chromosphere, without hot small-filling-factor plasma or cold molecular pockets  
  > "This model represents the mean 1D dominant lukewarm chromosphere and not the small filling factor of hot chromospheric plasma that gives rise to the rich UV spectrum." (Models and Discussion); "It also does not include pockets of cold molecular material." (Models and Discussion)
- Limitation (authors): H30alpha emission in the model requires an arbitrarily added hydrogen ionization fraction  
  > "In the simulation we arbitrarily added a small H ionization fraction in the model to create the emission shown in the blue spectrum." (Models and Discussion)
- Caveat (inferred, ours): X30alpha identification rests on a blend of unresolved lines with an abundance-weighted rest frequency, so velocity shifts of 3 km/s are degenerate with rest-frequency uncertainty
- Caveat (inferred, ours): Voigt fits report only formal errors and no fitting procedure or sampler is described
- Caveat (inferred, ours): Atmosphere model is only summarised and its revised version is unpublished, so the model comparison cannot be redone from this paper
- Caveat (inferred, ours): Imaging parameters (weighting, masks, line-free channels, self-cal solints) are absent, so the maps and fluxes cannot be rebuilt exactly

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Used standard ALMA CASA pipeline calibrated measurement sets (project 2022.A.00026.S)  
  > "The standard calibrated measurement sets (visibility data) from the ALMA" (Observations); "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2022.A.00026.S." (Acknowledgements)
- Missing: CASA version, tclean settings, masks and self-calibration parameters
- Missing: Line-free channel selections
- Missing: Fitting procedure for the Voigt profiles and aperture definitions for radial profiles
- Missing: Revised semi-empirical atmosphere model tables and the radiative transfer code
- Missing: Observing time on source
- Data volume (inferred): Large (tens to hundreds of GB for two long-baseline executions with four spectral windows at 0.976 MHz channels); not stated in the paper
- Score (inferred): 2/5, The ALMA project is identified and key numbers are tabulated, but imaging and calibration settings are missing and the atmosphere model used for the comparison is unpublished.
- Rediscovery candidate: no, The line measurements are numeric and the data are archival, but the imaging recipe is incomplete and the model comparison depends on an unpublished atmosphere model.

## Links

- Method: CASA Team et al. 2022 (cite: 2022PASP..134k4501C) (Reference for CASA used in self-calibration)
- Method: Towle et al. 1996 (cite: Towle1996) (Rydberg formula rest frequencies)
- Method: Olofsson et al. 2021 (cite: Olofsson2021) (Earlier identification of the X30alpha line cluster in HD101584)
- Companion: Kervella et al. 2018 (cite: Kervella2018) (ALMA SiO and CO study of the Betelgeuse molecular shell used for comparison)
- Companion: Harper, Brown & Lim 2001 (cite: 2001ApJ...551.1073H) (Base semi-empirical atmosphere model of Betelgeuse)
- Related: 2022.A.00026.S (multi-band high-resolution Betelgeuse program after the Great Dimming)

## Checks

```json
{
 "quotes": 137,
 "quotes_ok": 137,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 19,
 "numeric_problems": 0,
 "fill": {
  "facts": 107,
  "stated": 81,
  "rate": 0.757
 },
 "evidence_ok": true
}
```
