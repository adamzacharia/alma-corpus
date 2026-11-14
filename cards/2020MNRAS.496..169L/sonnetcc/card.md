# Validating scattering-induced (sub)millimetre disc polarization through the spectral index, wavelength-dependent polarization pattern, and polarization spectrum: the case of HD 163296

`2020MNRAS.496..169L` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Lin, Zhe-Yu Daniel | arXiv: 1912.10012 | DOI: 10.1093/mnras/staa1499

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can dust scattering simultaneously reproduce both the (sub)mm polarization fraction and the low spectral index observed in the HD 163296 disk?  
  > "can scattering simultaneously reproduce both the polarization fraction and the spectral index in a particular object quantitatively?" (Introduction)
- Target **HD 163296**: coordinates _not stated_; z/distance 101 pc  
  > "It is a Class II source at a distance of 101 pc (cite: Gaia2018)." (Introduction); "We fix the inclination angle to $46.7^{\circ}$, which was measured by fitting ellipses to the continuum annular substructures (cite: Isella2018)." (2.3 Using the 1D Slab Model to Estimate Parameters); distance from Gaia (cite: Gaia2018)  
  > "It is a Class II source at a distance of 101 pc (cite: Gaia2018)." (Introduction); "We fix the inclination angle to $46.7^{\circ}$, which was measured by fitting ellipses to the continuum annular substructures (cite: Isella2018)." (2.3 Using the 1D Slab Model to Estimate Parameters)

## Data provenance

- ALMA projects: 2013.1.00226.S, 2013.1.00601.S, 2015.1.00616.S, 2016.1.00484.L, 2016.1.00712.S, 2019.1.00035.S
- bands: Band 6 (1.25 mm, DSHARP) and Band 7 (0.87 mm, polarization and spectral index from Dent et al. 2019)  
  > "the high-angular resolution observations at Band 6 ($\lambda$ = 1.25mm) from DSHARP" (2 Model Setup); "the polarization fraction at Band 7 ($\lambda$ = 0.87mm)" (2 Model Setup)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6 beam 0.038'' x 0.048''; Band 7 polarization beam 0.21'' x 0.19''; spectral index beam 0.18'' x 0.17''  
  > "with a synthesized beam FWHM of 0.038$''$ $\times$ 0.048$''$, the polarization fraction at Band 7 ($\lambda$ = 0.87mm) with a FWHM of $0.21\ensuremath{''} \times 0.19\ensuremath{''}$, and the spectral index with a FWHM of $0.18\ensuremath{''} \times 0.17\ensuremath{''}$" (2 Model Setup)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Band 6 from the DSHARP large program (public images and radial profiles); Band 7 profiles provided by W.R.F. Dent from Dent et al. 2019  
  > "We express our gratitude to W.R.F. Dent for providing the Band 7 Stokes $I$, polarization, and spectral index profiles of HD 163296" (Acknowledgements); "the DSHARP group for making the radial profiles and images of their data publicly available" (Acknowledgements)
- Other facility **DSHARP (Disk Substructures at High Angular Resolution Project)**: High-resolution Band 6 continuum (Stokes I) of HD 163296 used as a modelling constraint  
  > "the high-angular resolution observations at Band 6 ($\lambda$ = 1.25mm) from DSHARP" (2 Model Setup)
- Other facility **ALMA Band 7 polarization data (Dent et al. 2019)**: Band 7 polarization fraction and spectral index profiles used as modelling constraints  
  > "the polarization fraction at Band 7 ($\lambda$ = 0.87mm)" (2 Model Setup)
- External data: Band 7 polarization fraction, orientation and spectral index (Band 7 to Band 6) of HD 163296, including major-axis polarization cuts  
  > "The polarization data is taken from Fig. 2a of (cite: Dent2019) where the polarization along the major axis is separated into the Northwest and Southeast directions." (3.2 Profiles along the Major Axis) [from (cite: Dent2019)]
- External data: Band 6 DSHARP continuum images and radial profiles  
  > "the high-angular resolution observations at Band 6 ($\lambda$ = 1.25mm) from DSHARP" (2 Model Setup) [from (cite: Andrews2018; Huang2018; Isella2018)]
- External data: Observed Band 7 flux, Band 6 flux and spectral index at 20, 67 and 100 au used for the 1D slab estimation (Table 1)  
  > "| 20 | 78.1 | 2.08 | 1.4 |" (Table 1) [from (cite: Dent2019) and DSHARP]
- External data: Dust model: composition, mass fractions and refractive indices (DSHARP dust model)  
  > "We follow the DSHARP dust model prescribed in (cite: Birnstiel2018)." (2.1 Dust Opacity); "The respective refractive indices of the different components are taken from (cite: Warren2008), (cite: Draine2003), and, for the latter two, (cite: Henning1996)." (2.1 Dust Opacity) [from (cite: Birnstiel2018); (cite: Warren2008); (cite: Draine2003); (cite: Henning1996)]
- External data: Disk inclination of 46.7 deg  
  > "We fix the inclination angle to $46.7^{\circ}$, which was measured by fitting ellipses to the continuum annular substructures (cite: Isella2018)." (2.3 Using the 1D Slab Model to Estimate Parameters) [from (cite: Isella2018)]
- External data: Distance of 101 pc  
  > "It is a Class II source at a distance of 101 pc (cite: Gaia2018)." (Introduction) [from (cite: Gaia2018)]
- External data: Gas density structure used for the dust scale height estimate (H_g = 8.7 au, gas surface density 3.9 g cm^-2 at 100 au)  
  > "We estimate the gas density structure from the multi-line fitting results in (cite: Flaherty2015) scaled to our adopted distance of 101pc." (4.1.3 Dust Scale Height) [from (cite: Flaherty2015)]
- External data: Literature midplane temperature profiles from CO lines used for comparison (and Flaherty 2015 profile for the warmer model)  
  > "$19 (R/128 \text{au})^{-0.3}$K (cite: Rosenfeld2013), $22.5 (R/124 \text{au})^{-0.3}$K (cite: Flaherty2015)" (4.1.2 Temperature) [from (cite: Rosenfeld2013; Flaherty2015; Dullemond2020)]
- Simulation/model as data: RADMC-3D Monte Carlo radiative transfer disk models (with scattering polarization) of HD 163296, compared with ALMA Band 6/7 data  
  > "we model the ALMA dust continuum and polarization data of HD 163296 using RADMC-3D" (abstract)
- Simulation/model as data: 1D plane-parallel isothermal slab model with scattering used to estimate surface density and temperature  
  > "we consider a 1D isothermal slab with scattering where the observed intensity at a given wavelength can be computed analytically for different optical depths and temperatures." (2.3 Using the 1D Slab Model to Estimate Parameters)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% of Stokes I assumed for absolute flux calibration; 0.3 uncertainty on spectral index (Dent et al. 2019 used 7%)  
  > "We overlay the range that encloses $10\%$ of the measured Stokes $I$ at Bands 7 and 6 to account for the absolute flux calibration uncertainty of ALMA observations" (2.3 Using the 1D Slab Model to Estimate Parameters); "an uncertainty of 0.3 for the measured spectral index ((cite: Dent2019); which used a $7\%$ calibration uncertainty)" (2.3 Using the 1D Slab Model to Estimate Parameters)
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
- smoothing: Model images convolved with circular Gaussian beams: 0.043'' (Band 6 Stokes I), 0.2'' (Band 7 Q and U), 0.175'' (Bands 6 and 7 Stokes I for spectral index)  
  > "the Stokes $I$ images are convolved by a Gaussian beam with a circular FWHM of 0.043$''$ for Band 6" (3.1 Polarization Image); "after the Stokes $Q$ and $U$ images are first convolved individually with a circular FWHM of 0.2$''$" (3.1 Polarization Image); "The spectral index is calculated after Band 7 and Band 6 Stokes $I$ are each convolved by a Gaussian beam with a circular FWHM of 0.175$''$" (3.1 Polarization Image)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Dust opacity model (composition, Mie theory, power-law size distribution) follows DSHARP  
  > "We follow the DSHARP dust model prescribed in (cite: Birnstiel2018)." (2.1 Dust Opacity) [from (cite: Birnstiel2018)]
- Naming of disk substructures (e.g. B100, D48) follows DSHARP notation  
  > "We follow the DSHARP notation in (cite: Huang2018) to describe the substructures of HD 163296." (2.2 Disk Model) [from (cite: Huang2018)]
- 1D isothermal slab with scattering follows earlier analytic work  
  > "Following (cite: Birnstiel2018) and (cite: Zhu2019), we consider a 1D isothermal slab with scattering" (2.3 Using the 1D Slab Model to Estimate Parameters) [from (cite: Birnstiel2018); (cite: Zhu2019)]
- Convolution beam for the spectral index chosen to match the Band 7 spectral index map of Dent et al. 2019  
  > "first to match that from (cite: Dent2019)" (3.1 Polarization Image) [from (cite: Dent2019)]

### Not stated but needed to reproduce (our reading)

- The Band 7 Stokes I, polarization and spectral index profiles were supplied by W.R.F. Dent; the processing (imaging, calibration, uv coverage, flux scale) is not given and must be taken from Dent et al. 2019
- How the DSHARP Band 6 radial and major-axis profiles were extracted (azimuthal averaging or cut width, deprojection, position angle)
- RADMC-3D version, grid (radial/theta/phi resolution), number of photon packages, scattering mode (polarised scattering, number of angles) and wavelengths used
- Stellar parameters (luminosity, temperature, mass) and whether any stellar heating is used, given that the dust temperature is prescribed
- Position angle, image pixel scale, and viewing geometry used for the synthetic images
- How the parameters in Table 2 were chosen: no goodness-of-fit metric, tolerance or parameter uncertainties are given, only a hand-tuned set
- The full Table 1 procedure for reading off observed values at 20, 67 and 100 au (radial range, averaging)
- Gas-to-dust ratio and dust mass are not used; no conversion from dust surface density to total mass is given

## Analysis recipe

1. **Compute dust opacity and choose maximum grain size**: Mie theory opacity for DSHARP composition with a power-law size distribution; a_max chosen where the product of single-scattering polarization P and effective albedo peaks at Band 7  
  > "The product, $P \omega^{\text{eff}}_{\nu}$, gives the grain size that contributes most to the polarization at the observing wavelength." (2.1 Dust Opacity); "Opacity is calculated using Mie Theory which assumes compact (non-porous) spherical grains and requires as input parameters the grain size and refractive indices." (2.1 Dust Opacity)
   - software: RADMC-3D Mie code (python version)
   - parameter: Size distribution a^-3.5, minimum size 0.01 micron, a_max free then fixed at 90 micron  
  > "The minimum grain size is fixed at $0.01\mu$m, while the maximum grain size $a_{\text{max}}$ is left as a free parameter." (2.1 Dust Opacity); "We will therefore hold $a_{\text{max}}$ fixed at this value for our models and assume the same dust population throughout the whole disk" (2.1 Dust Opacity)
   - assumption: Compact spherical grains; same dust population throughout the whole disk; mass fractions of ice, silicates, troilite and organics ~0.2, 0.33, 0.07, 0.4  
  > "with mass fractions of $\sim 0.2$, $0.33$, $0.07$, and $0.4$, respectively" (2.1 Dust Opacity)
   - fitting: _not stated_
   - validation: _not stated_
2. **Estimate surface density and temperature with 1D slab model**: Search a grid of slab temperature and surface density, computing Band 6 and 7 intensities and spectral index, and keep ranges that match observed values at 20, 67 and 100 au within uncertainty  
  > "we search through a parameter space of temperature and surface density of the slab and calculate the expected intensities at ALMA Bands 6 and 7 and the spectral index between the two." (2.3 Using the 1D Slab Model to Estimate Parameters)
   - parameter: Inclination 46.7 deg; tolerance 10% on Stokes I and 0.3 on spectral index  
  > "We fix the inclination angle to $46.7^{\circ}$" (2.3 Using the 1D Slab Model to Estimate Parameters); "an uncertainty of 0.3 for the measured spectral index" (2.3 Using the 1D Slab Model to Estimate Parameters)
   - assumption: Isothermal plane-parallel slab with scattering  
  > "we consider a 1D isothermal slab with scattering" (2.3 Using the 1D Slab Model to Estimate Parameters)
   - fitting: Grid search over slab temperature and surface density; no formal likelihood stated  
  > "we search through a parameter space of temperature and surface density of the slab" (2.3 Using the 1D Slab Model to Estimate Parameters)
   - validation: Used as a consistency check and starting point for the Monte Carlo models  
  > "These constrained ranges serve as a consistency check and provide a starting point for exploring the parameter space using Monte Carlo radiation transfer calculations" (2.3 Using the 1D Slab Model to Estimate Parameters)
3. **Run polarized Monte Carlo radiative transfer for the full disk model**: RADMC-3D radiative transfer with scattering polarization for a ring and gap surface density (power-law-like plus Gaussian-like components) and power-law temperature, then beam convolution and comparison with Band 6 Stokes I, Band 7 polarization and spectral index  
  > "we performed a set of RADMC-3D-based radiative transfer calculations including polarization from scattering" (3 Numerical Results); "we adopt a composite surface density distribution $\Sigma_{d}$ that is composed of two different types of profiles: power-law-like profiles and Gaussian-like profiles." (2.2 Disk Model)
   - software: RADMC-3D
   - parameter: Temperature T = T_t (R/R_t)^-q with R_t = 100 au, T_t = 12.5 K, q = 0.65; dust scale height H_t = 3 au  
  > "$T_{t}$ \[K\] | 12.5" (Table 2); "$H_{t}$ \[au\] | 3" (Table 2)
   - assumption: Dust and temperature distributions prescribed, not computed self-consistently  
  > "Ideally, both the dust and temperature distributions should be computed self-consistently, but doing so is numerically costly" (2.2 Disk Model)
   - fitting: Hand-chosen parameter set guided by 1D slab estimates; no sampler, priors or likelihood stated  
  > "Guided by the analytical estimates in Section" (3 Numerical Results)
   - validation: Qualitative and major-axis profile comparison with observed Stokes I, polarization fraction and spectral index  
  > "we take a cut along the major axis and compare the beam-convolved model images to observations" (3.2 Profiles along the Major Axis)
4. **Quantify beam averaging of rings and gaps**: Compare intrinsic (unconvolved) and beam-convolved model spectral index along the major axis  
  > "To identify the effects of convolution, we also plot the intrinsic model images without convolution." (3.2 Profiles along the Major Axis)
   - fitting: _not stated_
   - validation: _not stated_
5. **Test a warmer midplane temperature**: Re-fit surface density parameters to Band 6 Stokes I using the Flaherty et al. 2015 temperature profile and compare spectral index  
  > "we adopt the temperature profile of (cite: Flaherty2015) (see Fig. [5](#fig:obsmaj)e) and vary the surface density parameters to fit the Band 6 Stokes $I$ high resolution image." (An Illustrative Model of A Warmer Disk)
   - software: RADMC-3D
   - parameter: T = 22.5 K at R_t = 124 au, q = 0.3  
  > "$T_{t}$ \[K\] | 22.5" (Table 3)
   - fitting: _not stated_
   - validation: Warmer model fails to reproduce spectral index at the 100 au ring  
  > "The higher temperature model does not fit the spectral index, especially at the outer, 100 au ring." (4.1.2 Temperature)
6. **Estimate dust scale height and viscosity parameter**: Compare model dust scale height with a settling-turbulence balance H_d/H_g ~ sqrt(alpha_v/(Omega tau_f)) using gas density from Flaherty et al. 2015  
  > "Using our prescribed dust scale height, the $\alpha_{v} \sim 1.7 \times 10^{-3}$." (4.1.3 Dust Scale Height)
   - parameter: H_g = 8.7 au, gas surface density 3.9 g cm^-2, rho_g = 1.2e-14 g cm^-3 at 100 au; rho_s ~ 1.7 g cm^-3; grain size 90 micron  
  > "At a radius of 100 au, $H_{g} = 8.7$au, gas surface density is 3.9 g cm$^{-2}$ and $\rho_{g} = 1.2 \times 10^{-14}$ g cm$^{-3}$." (4.1.3 Dust Scale Height)
   - fitting: _not stated_
   - validation: Compared with the upper limit alpha_v <~ 1e-3 from Flaherty et al. 2015  
  > "The upper limit on the viscosity parameter was found to be $\alpha _{v} \lesssim 1 \times 10^{-3}$ (cite: Flaherty2015) which is broadly consistent with our model result." (4.1.3 Dust Scale Height)
7. **Predict polarization in Bands 7 to 3**: Synthetic polarization fraction maps and spectra for Bands 7, 6, 5, 4 and 3 without telescope resolution effects, at selected major-axis locations  
  > "Here we will make predictions for all other bands where polarization observations are currently possible with ALMA, including Bands 6, 5, 4 and 3" (4.3 Polarization Spectrum as a Test of Scattering-Induced Polarization)
   - software: RADMC-3D
   - fitting: _not stated_
   - validation: No data at other bands; predictions left for future observations  
  > "These can be checked against future observations." (4.3 Polarization Spectrum as a Test of Scattering-Induced Polarization)

## Software

- **RADMC-3D** : Monte Carlo radiative transfer including scattering polarization to produce model images  
  > "we will use the Monte Carlo radiative transfer code RADMC-3D" (2 Model Setup)
- **Mie code (python version in RADMC-3D)** : Mie opacity calculation for the dust model  
  > "Mie opacity calculation is implemented using the python version of the Mie code available in RADMC-3D." (2.1 Dust Opacity)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optimal maximum grain size for Band 7 polarization | 90 | not stated | micron | 1 | the optimal maximum grain size for producing polarization at $\lambda$ = 0.87mm is $90 \mu$m |
| Absorption opacity, effective albedo and forward-scattering parameter at 0.87 mm | kappa_abs = 0.97 cm^2 g^-1 (per gram of dust), effective albedo 0.64, g = 0.15 | not stated | cm^2 g^-1 (kappa_abs); dimensionless | 1 | $\kappa_{\text{abs}}=0.97$ cm$^{2}$ g$^{-1}$ per gram of dust, $\omega_{\nu}^{\text{eff}} = 0.64$, and $g_{\nu} = 0.15$ at $\lambda$ = 0.87mm |
| Absorption opacity, effective albedo and forward-scattering parameter at 1.25 mm | kappa_abs = 0.46 cm^2 g^-1, effective albedo 0.47, g = 0.044 | not stated | cm^2 g^-1 (kappa_abs); dimensionless | 1 | whereas at $\lambda=$1.25mm, $\kappa_{\text{abs}} = 0.46$ cm$^{2}$ g$^{-1}$, $\omega_{\nu}^{\text{eff}} = 0.47$, and $g_{\nu} = 0.044$ |
| Dust opacity index beta_dust between Band 7 and Band 6 | 2.06 | not stated | dimensionless | 1 | The opacity index $\beta_{\text{dust}}$ index between the two wavelengths is 2.06. |
| Midplane dust temperature parameters of best model | T = 12.5 K at 100 au, power-law index q = 0.65 | not stated | K (T_t); dimensionless (q) | 3 | $T_{t}$ \[K\] / 12.5; $q$ / 0.65 |
| Optical depth of inner disk (R <~ 30 au) at Band 6 | ~10 (higher at Band 7) | not stated | dimensionless | 3 | we find that optical depths of $\sim10$ at Band 6 and higher for Band 7 are needed to produce the low spectral index observed there |
| Optical depth at centres of the 67 and 100 au rings at Band 6 | ~3 | not stated | dimensionless | 3 | For the dust rings at 67 and 100 au, we find optical depths of $\sim 3$ at their centers in Band 6. |
| Model spectral index and polarization fraction in the inner disk | alpha ~ 1.5; polarization fraction ~ 1% | not stated | dimensionless; percent | 3 | Note that the low spectral index values of $\sim 1.5$ and the polarization fraction of $\sim 1 \%$ in the inner disk are well reproduced. |
| Model polarization orientation scatter about the disk minor axis | within ~ +-10 deg | not stated | deg | 3 | The polarization orientations are mainly in the disk minor axis direction, within $\sim\pm 10^{\circ}$ across the image. |
| Intrinsic spectral index in optically thin gaps | ~ 4 | not stated | dimensionless | 4 | In the gap regions, the intrinsic spectral index approaches $\alpha \sim 4$ |
| Intrinsic spectral index in optically thick rings | ~ 1.5 | not stated | dimensionless | 4 | In the optically thick rings, the spectral indices are intrinsically low ($\sim 1.5$) because of preferential scattering at shorter wavelengths |
| Beam-convolved spectral index in rings and gaps | rings alpha ~ 2; gaps alpha ~ 2.5 | not stated | dimensionless | 4 | Convolution with the telescope beam brings the spectral index in the rings up, to $\alpha\sim 2$, and that in the gaps down, to $\alpha\sim 2.5$ |
| Inferred opacity index beta in gaps and rings, intrinsic and after convolution | intrinsic beta ~ 2 (gaps), ~ -0.5 (rings); after convolution ~ 0.5 (gaps), ~ 0 (rings) | not stated | dimensionless | 4 | we have $\beta\sim 2$ in the optically thin gaps and $\beta \sim -0.5$ in the optically thick rings; After convolution with the telescope beam, the former is brought down to $\beta\sim 0.5$, and the latter up to $\beta \sim 0$. |
| Viscosity parameter implied by the model dust scale height at 100 au | ~ 1.7e-3 | not stated | dimensionless | 6 | Using our prescribed dust scale height, the $\alpha_{v} \sim 1.7 \times 10^{-3}$. |
| Maximum polarization fraction color scale, Band 7 and Band 3 (no beam) | ~ 6% (Band 7) to ~ 0.35% (Band 3) | not stated | percent | 7 | starting at $\sim 6\%$ for the shortest-wavelength Band 7 and decreasing to $\sim 0.35\%$ for the longest-wavelength Band 3 |
| Predicted polarization spectrum slope in the inner disk | p proportional to lambda^-0.85 | not stated | dimensionless | 7 | approximately as $\lambda^{-0.85}$ |
| Predicted polarization spectrum slope in the gap (Rayleigh limit) | p proportional to lambda^-3 | not stated | dimensionless | 7 | approaches the steep power-law $\lambda^{-3}$ for Rayleigh scattering toward the longest wavelength bands with the lowest optical depths |

## Qualitative findings

- The tension between grain sizes inferred from polarization and from the spectral index disappears because the low alpha values do not require large mm-sized grains  
  > "The tension between the grain sizes inferred from polarization and spectral index disappears because the low $\alpha$ values do not require large mm-sized grains." (abstract)
- The model midplane temperature is lower than CO-based estimates, so those likely probe warmer gas down to the CO snow surface  
  > "Our inferred midplane temperature is lower than that inferred from optically thick CO lines." (5 Conclusions)
- In optically thick rings the polarization spectrum is flattened or inverted, unlike the steep decline in gaps  
  > "which becomes flattened or even inverted towards short wavelengths in the optically thick rings" (abstract)

## Claim tuples

- H: Dust scattering by small grains can simultaneously reproduce the Band 7 polarization and the low Band 7 to 6 spectral index of HD 163296 | E: RADMC-3D disk model with a_max = 90 micron grains compared with Band 6 Stokes I, Band 7 polarization and spectral index | R: The model broadly reproduces Stokes I, the post-convolution spectral index (alpha ~ 1.5 in the inner disk) and the polarization | F: Scattering by ~100 micron grains explains both polarization and low spectral index, supporting the scattering interpretation | **supported**
- H: Low apparent spectral index in the gaps does not require mm-sized grains | E: Compare intrinsic and beam-convolved model spectral index across rings and gaps | R: Intrinsic gap alpha ~ 4 and ring alpha < 2 are averaged by the beam to gap alpha ~ 2.5 and ring alpha ~ 2 | F: Beam averaging of rings and gaps can mimic large grains, so the grain-size tension may be illusory | **supported**
- H: The disk midplane is as warm as inferred from optically thick CO lines | E: Refit the model with the Flaherty et al. 2015 temperature profile and compare spectral index | R: The warmer model requires less dust, makes the B67 and B100 rings optically thin and pushes alpha above the observed constraint | F: The midplane is colder than CO-based temperatures; CO lines likely trace warmer gas near the CO snow surface | **supported**
- H: Scattering-induced polarization has distinctive wavelength-dependent patterns in rings versus gaps that can serve as further tests | E: Predict polarization fraction maps and spectra in ALMA Bands 7 to 3 for the best model | R: Gap polarization falls roughly as lambda^-3, ring polarization can invert, and the inner disk falls as ~lambda^-0.85 | F: Resolved multi-wavelength polarization should test the scattering interpretation | **partially**
- H: The model reproduces the observed polarization fraction along the major axis | E: Compare beam-convolved model polarization fraction with Dent et al. 2019 cuts | R: Matches within the first gap but is somewhat lower than observed at outer radii | F: Reasonable agreement in the inner disk, with a shortfall at large radii | **partially**

## Reasoning

- Why this data: HD 163296 has both polarization and spectral index measurements and well-resolved substructure  
  > "The disk is a particularly suitable source to study polarization and the spectral index since both measurements are available (cite: Dent2019)." (Introduction)
- Why this method: Polarization radiative transfer is expensive, so parameters are first estimated with a 1D analytic slab model before Monte Carlo runs  
  > "polarization radiative transfer calculations are computationally expensive; thus we choose to first estimate the parameters needed to fit the Bands 6 and 7 data observed in HD 163296" (2.3 Using the 1D Slab Model to Estimate Parameters)
- Alternative: Grid search or MCMC parameter fitting was not used because of the computational cost of polarized radiative transfer  
  > "To constrain model parameters, one can implement a grid-based search or other parameter fitting methods, e.g., Markov-Chain Monte Carlo." (2.3 Using the 1D Slab Model to Estimate Parameters)
- Alternative: Warmer disk using the Flaherty et al. 2015 temperature profile rejected because it does not fit the spectral index at the 100 au ring  
  > "The higher temperature model does not fit the spectral index, especially at the outer, 100 au ring." (4.1.2 Temperature)
- How they decided it was enough: Judged by a broad visual match of major-axis profiles; no formal fit statistic is stated  
  > "broadly reproduces the total intensity (Stokes $I$) observed at $1.25$ mm" (5 Conclusions)
- Limitation (authors): Polarization fraction may be affected by differential filtering of Stokes I versus Q and U by the interferometer, not quantified here  
  > "the polarization fraction may be significantly affected by the differential filtering of Stokes $I$ vs. $Q$ and $U$ by interferometers such as ALMA." (3.2 Profiles along the Major Axis)
- Limitation (authors): Simple power-law temperature breaks down at small radii and ignores rings and gaps  
  > "indicating that the simple power-law temperature profile breaks down at small radii." (4.1.2 Temperature)
- Limitation (authors): Dust and temperature structures are not computed self-consistently  
  > "Ideally, both the dust and temperature distributions should be computed self-consistently, but doing so is numerically costly" (2.2 Disk Model)
- Limitation (authors): Model polarization fraction is somewhat lower than observed at outer radii  
  > "is somewhat lower than the observed values at outer radii given by (cite: Dent2019)" (3.2 Profiles along the Major Axis)
- Caveat (inferred, ours): Parameters in Table 2 are hand-tuned with no goodness-of-fit, no uncertainties and no degeneracy exploration, so the uniqueness of the solution (a_max, temperature, optical depth) is untested
- Caveat (inferred, ours): a_max is fixed at 90 micron from the Band 7 polarization peak before fitting, so alternative grain sizes (and porous or non-spherical grains) are not tested against the spectral index
- Caveat (inferred, ours): Band 6 and Band 7 flux scales and filtering of extended emission are not modelled; the Band 7 data are provided by a co-author source rather than reprocessed
- Caveat (inferred, ours): Temperature conclusion depends on the optically thick ring assumption and on the chosen dust model; the CO-based temperature comparison is qualitative
- Caveat (inferred, ours): Polarization predictions for Bands 6 to 3 are untested against data

## Reproducibility

- Data public (paper): DSHARP radial profiles and images are public; Band 7 profiles were provided by W.R.F. Dent (not stated as public in the paper)  
  > "the DSHARP group for making the radial profiles and images of their data publicly available" (Acknowledgements); "We express our gratitude to W.R.F. Dent for providing the Band 7 Stokes $I$, polarization, and spectral index profiles of HD 163296" (Acknowledgements)
- Products in archive: DSHARP data hosted at bulk.cv.nrao.edu/almadata/lp/DSHARP/  
  > "https://bulk.cv.nrao.edu/almadata/lp/DSHARP/" (footnote 3)
- Code: RADMC-3D is publicly available; the authors' own model scripts are not stated as released  
  > "We also thank C.P. Dullemond for making RADMC-3D publicly available." (Acknowledgements)
- Missing: Dent et al. 2019 Band 7 polarization, Stokes I and spectral index profiles (supplied privately)
- Missing: RADMC-3D setup details (grid, photon counts, scattering mode, stellar parameters, position angle)
- Missing: Rule for selecting the final Table 2 parameters and the radial-cut definition used for the observed profiles
- Data volume (inferred): Small (well under 1 GB) if the DSHARP continuum images and published profiles are used; raw ALMA visibilities are not needed
- Score (inferred): 3/5, Full parameter tables, public DSHARP data and a public RADMC-3D code are given, but Band 7 inputs came privately, RADMC-3D settings are missing, and the fit is hand-tuned with only qualitative agreement criteria.
- Rediscovery candidate: no, The main results are model comparisons judged by eye with unstated RADMC-3D settings and a privately supplied Band 7 dataset, so there is no complete numeric recipe to redo.

## Links

- Method: (cite: Birnstiel2018) (DSHARP dust opacity model and scattering effects followed here)
- Method: (cite: Zhu2019) (1D slab model with scattering used for parameter estimation)
- Method: (cite: Huang2018) (DSHARP substructure notation)
- Companion: (cite: Dent2019) (Source of Band 7 polarization and spectral index data and earlier scattering model)
- Companion: (cite: Ohashi2019) (Independent polarization modelling of HD 163296 used for comparison)
- Companion: (cite: Isella2018) (DSHARP HD 163296 data paper; inclination and optical depth constraints)
- Companion: (cite: Andrews2018) (DSHARP overview)
- Related: DSHARP (Disk Substructures at High Angular Resolution Project)
- Related: ALMA project 2019.1.00035.S (IM Lup Band 6 polarization, PI C. Hull)

## Checks

```json
{
 "quotes": 108,
 "quotes_ok": 108,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 6,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2019.1.00035.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00694.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 100,
  "stated": 63,
  "rate": 0.63
 },
 "evidence_ok": true
}
```
