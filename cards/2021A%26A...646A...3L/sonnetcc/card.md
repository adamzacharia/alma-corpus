# Chemically tracing the water snowline in protoplanetary disks with HCO<SUP>+</SUP>

`2021A&A...646A...3L` | Astronomy and Astrophysics 2021 | first author: Leemker, M. | arXiv: 2011.12319 | DOI: 10.1051/0004-6361/202039387

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Whether HCO+ and H13CO+ can trace the water snowline in protoplanetary disks (Herbig Ae disk models and the outbursting source V883 Ori), and what sensitivity and resolution are needed  
  > "the aim of this research is to investigate the validity of HCO$^+$ and the optically thin isotopologue, H$^{13}$CO$^+$, as tracers of the water snowline in protoplanetary disks" (abstract)
- Target **V883 Ori**: coordinates _not stated_; z/distance ~400 pc  
  > "at a distance of $\sim$400 pc; (cite: Kounkel2017)" (H$^{13}$CO$^+$ observations); distance from Kounkel et al. 2017 (cite: Kounkel2017)  
  > "at a distance of $\sim$400 pc; (cite: Kounkel2017)" (H$^{13}$CO$^+$ observations)

## Data provenance

- ALMA projects: 2017.1.01066.T, 2018.1.01131.S
- bands: Band 7 (2017.1.01066.T, H13CO+ J=4-3); Band 6 (2018.1.01131.S, HCO+ J=3-2)  
  > "A promising dataset to locate the water snowline in V883 Ori is the band 7 observation by (cite: Lee2019)" (H$^{13}$CO$^+$ observations); "a recent band 6 dataset (project code 2018.1.01131.S" (HCO$^+$ observations)
- frequencies and spectral setup: Band 7 data: spectral resolution 0.25 km/s  
  > "and the spectral resolution is 0.25 km s$^{-1}$" (H$^{13}$CO$^+$ observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 7: 0.2'' synthesized beam; Band 6: ~0.5''  
  > "The synthesized beam of these observations is $0.2\ensuremath{''}$ (40 AU radius, 80 AU diameter at a distance of $\sim$400 pc;" (H$^{13}$CO$^+$ observations); "The spatial resolution of $\sim0.5\ensuremath{''}$ is insufficient to resolve the water snowline" (HCO$^+$ observations)
- max recoverable scale: _not stated_
- sensitivity: ~15 mJy per spectral bin in the velocity-stacked band 7 spectrum  
  > "The noise level of $\sim$15 mJy per spectral bin is determined using an empty region in the stacked image." (H$^{13}$CO$^+$ observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival ALMA data (PI Jeong-Eun Lee for 2017.1.01066.T)  
  > "Our analysis of recent archival ALMA band 6 observations of the $J=3-2$ transition of HCO$^+$" (abstract); "(project code: 2017.1.01066.T, PI: Jeong-Eun Lee)" (H$^{13}$CO$^+$ observations)
- Line: H13CO+ J=4-3 (observed, band 7) (not stated)
- Line: HCO+ J=3-2 (observed, band 6) (not stated)
- Line: HCO+ J=2-1 (modelled) (178.375 GHz)
- Line: H13CO+ J=2-1 (modelled) (173.507 GHz)
- Other facility **VANDAM survey**: 9.1 mm continuum flux used to estimate the V883 Ori disk mass  
  > "The disk mass is estimated using the 9.1 mm continuum observations of the VANDAM survey (cite: Tobin2020)" (Model HCO$^+$ images: locating the snowline)
- External data: Collisional rate coefficients for HCO+ and H13CO+ from the LAMDA database  
  > "we used the collisional rate coefficients in the LAMDA database (cite: Botschwina1993; Flower1999; Schoier2005)" (Radiative transfer) [from (cite: Botschwina1993; Flower1999; Schoier2005)]
- External data: Gas-phase reaction rate coefficients (alpha, beta, gamma) from the rate12 UMIST database  
  > "are taken from the rate12 UMIST database (cite: McElroy2013)" (Table 2 notes) [from (cite: McElroy2013)]
- External data: Stellar spectrum of HD 100546 used for the Herbig Ae model  
  > "Spectrum of HD 100546 (cite: Kama2016)" (Table 1 notes) [from (cite: Kama2016)]
- External data: V883 Ori stellar mass 1.3 Msun, inclination 38 deg, position angle 32 deg  
  > "using a stellar mass, $M_{\star}$ = 1.3 M$_{\odot}$, an inclination of 38$\degree$, and a position angle of 32$\degree$ (cite: Cieza2016)" (H$^{13}$CO$^+$ observations) [from (cite: Cieza2016)]
- External data: V883 Ori distance of ~400 pc  
  > "at a distance of $\sim$400 pc; (cite: Kounkel2017)" (H$^{13}$CO$^+$ observations) [from (cite: Kounkel2017)]
- External data: Dust opacity of 0.28 cm2/g at 9.1 mm for the disk mass estimate  
  > "Following (cite: Tychoniec2020), a dust opacity of 0.28 cm$^2$g$^{-1}$ at a wavelength of 9.1 mm is used (cite: Woitke2016)." (Model HCO$^+$ images: locating the snowline) [from (cite: Tychoniec2020); (cite: Woitke2016)]
- External data: Radial extent of V883 Ori C18O J=2-1 emission used to set the characteristic radius  
  > "to match the radial extent of emission from the $J=2-1$ transition of C$^{18}$O presented by (cite: vantHoff2018methanol)" (Model HCO$^+$ images: locating the snowline) [from (cite: vantHoff2018methanol)]
- External data: 12C/13C isotope ratio of 70  
  > "corresponding to the typical $^{12}$C/$^{13}$C isotope ratio (cite: Milam2005)" (Chemical models) [from (cite: Milam2005)]
- External data: Rest frequencies of acetaldehyde lines near H13CO+ J=4-3 from the JPL molecular database  
  > "(Jet Propulsion Laboratory (JPL) molecular database; (cite: Pickett1998))" (H$^{13}$CO$^+$ observations) [from (cite: Pickett1998)]
- Simulation/model as data: DALI thermochemical model of a typical Herbig Ae disk (L = 36 Lsun) providing density and temperature structure  
  > "a disk around a typical Herbig Ae star with a luminosity of 36 L$_{\odot}$" (Introduction)
- Simulation/model as data: Two small time-dependent chemical networks (no water, NW; with water, W) giving HCO+ abundances  
  > "The first network, network *no water* (NW), is shown in the dashed box in Fig." (Chemical models)
- Simulation/model as data: Representative DALI model of V883 Ori with three luminosities placing the snowline at 47, 76 and 119 AU  
  > "which put the snowline at 47, 76, and 119 AU, respectively" (Model HCO$^+$ images: locating the snowline)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Band 6 HCO+ J=3-2: azimuthal average made from the archive product data  
  > "a normalized, deprojected azimuthal average of the observed emission from the product data of the $J=3-2$ transition of HCO$^+$" (HCO$^+$ observations)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 5.1.1 tclean (band 7 line images)  
  > "Using the CASA 5.1.1" (H$^{13}$CO$^+$ observations)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with a Briggs weighting of 0.5, line images are made" (H$^{13}$CO$^+$ observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: mask of about 2" diameter centered on the continuum peak  
  > "line images are made with a mask of about 2" in diameter centered on the peak of the continuum" (H$^{13}$CO$^+$ observations)
- multiscale scales: _not stated_
- continuum subtraction: Continuum from all line-free channels, subtracted from line data  
  > "The line data are continuum subtracted using these continuum solutions." (H$^{13}$CO$^+$ observations)
- line free channels: all line-free channels, carefully selected (ranges not listed)  
  > "The continuum is created using all line-free channels, which are carefully selected to exclude any line emission." (H$^{13}$CO$^+$ observations)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.2'' (band 7); ~0.5'' (band 6)  
  > "The synthesized beam of these observations is $0.2\ensuremath{''}$ (40 AU radius, 80 AU diameter at a distance of $\sim$400 pc;" (H$^{13}$CO$^+$ observations)
- final rms: ~15 mJy per spectral bin (stacked spectrum)  
  > "The noise level of $\sim$15 mJy per spectral bin is determined using an empty region in the stacked image." (H$^{13}$CO$^+$ observations)

### Inherited from earlier work

- Velocity stacking of the band 7 line data using Keplerian rotation  
  > "Following the approach of (cite: Lee2019), the line observations are velocity-stacked using a stellar mass" (H$^{13}$CO$^+$ observations) [from Lee et al. 2019 (cite: Lee2019); also (cite: Yen2016; Yen2018)]
- Acetaldehyde line widths fixed to 2 km/s in the Gaussian fit  
  > "the widths of the lines are fixed to 2 km s$^{-1}$ following (cite: Lee2019)" (H$^{13}$CO$^+$ observations) [from (cite: Lee2019)]
- Disk density structure approach for the DALI model  
  > "following the approach of (cite: Andrews2011)" (Disk structure) [from (cite: Andrews2011)]
- Two-population dust vertical structure  
  > "using two populations of dust grains following the approach of (cite: DAlessio2006)" (Disk structure) [from (cite: DAlessio2006)]
- Band 6 HCO+ image and observational details deferred to a companion paper  
  > "An image of the HCO$^+$ emission will be presented in" (HCO$^+$ observations) [from Ruiz-Rodriguez et al. (in prep.)]
- Dust opacity for the disk mass estimate  
  > "Following (cite: Tychoniec2020), a dust opacity of 0.28 cm$^2$g$^{-1}$ at a wavelength of 9.1 mm is used" (Model HCO$^+$ images: locating the snowline) [from (cite: Tychoniec2020)]

### Not stated but needed to reproduce (our reading)

- DALI version and access (code availability, configuration and chemistry settings are not described)
- Calibration of the band 7 and band 6 data: pipeline vs manual, CASA version, flux calibrator, self-calibration
- Which spectral windows, channel ranges and line-free channels were used for the band 7 continuum and line cubes
- Band 6 data: beam, noise level, imaging parameters and the deprojection geometry used for the azimuthal average
- Normalisation used in the azimuthal profiles and how models were convolved and matched to the observations
- Rest frequencies of HCO+ J=3-2 and H13CO+ J=4-3 as used
- Choice of radial bins and error treatment for the observed profiles; no quantitative goodness-of-fit is reported

## Analysis recipe

1. **Model disk density and temperature structure**: Parametric disk with exponentially tapered power-law gas surface density, Gaussian vertical structure, two dust populations; gas temperature solved iteratively with chemistry and heating/cooling, dust temperature from Monte Carlo radiative transfer  
  > "This approach is based on the self-similar solution for a viscously evolving disk, where the gas surface density of the disk outside the dust sublimation radius follows a power law with an exponential taper" (Disk structure); "The dust temperature is computed using Monte Carlo continuum radiative transfer." (Disk structure)
   - software: DALI
   - parameter: Full parameter set (R_c, Sigma_c, M_disk, gamma, h_c, psi, chi, f_ls, L, M_star, i, d) listed in Table 1  
  > "An overview of all parameters used for the density and temperature structure can be found in Table" (Disk structure)
   - parameter: R_subl = 0.05 AU  
  > "A sublimation radius of $R_{\mathrm{subl}} = 0.05$ AU is assumed." (Disk structure)
   - parameter: Gas-to-dust mass ratio 100  
  > "which is set to the ISM value of 100" (Disk structure)
   - parameter: Grain size distribution proportional to a^-3.5 (MRN)  
  > "the size distribution of both grain populations is assumed to be proportional to $a^{-3.5}$" (Disk structure)
   - assumption: Typical Herbig Ae star luminosity 36 Lsun  
  > "a typical Herbig Ae star with a luminosity of 36 L$_{\odot}$" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute HCO+ abundance with small chemical networks**: Time-dependent small networks (NW without water, W with water) solved up to 1 Myr on the DALI density and temperature structure  
  > "which is solved time-dependently up to 1 Myr with the python function" (Chemical models)
   - software: scipy odeint (LSODA)
   - parameter: Initial x(CO) = 1e-4 in both networks; x(H2O) = 3.8e-7 in network W; others 0  
  > "Initially, the abundance of all gas- and ice-phase species are set to 0 except for the abundance of gas-phase CO, which is set to $10^{-4}$ both in network NW and W" (Chemical models); "and the abundance of gas-phase water in network W, which is set to $3.8\times 10^{-7}$" (Chemical models)
   - parameter: Grain number density 1e-12 x n(H2), grain size 0.1 um; H13CO+ abundance a factor 70 below HCO+  
  > "we assume in chemical network NW and W a typical grain number density of 10$^{-12}\times n(\mathrm{H_2})$ and a grain size of 0.1 $\mu$m" (Chemical models); "the H$^{13}$CO$^+$ abundance is taken to be a factor 70 smaller than the abundance of HCO$^+$" (Chemical models)
   - assumption: Single grain size for the chemistry is an approximation  
  > "Assuming a single grains size for the chemistry is an approximation" (Chemical models)
   - fitting: _not stated_
   - validation: Compared with full chemical networks and tested against different initial CO, H2O and cosmic-ray ionization rate conditions  
  > "Our small network is thus suited to study HCO$^+$ as a tracer of the water snowline." (Chemistry); "Therefore, the results in the following sections do not depend critically on the choice of initial conditions." (Effect of the CO, H$_2$O abundance, and cosmic ray ionization rate on the HCO$^+$ abundance)
3. **Predict HCO+ and H13CO+ emission profiles**: Non-LTE ray tracing with continuum and line optical depth, radial profiles along the semi-major axis, convolved with a 0.05'' beam  
  > "The line radiative transfer does not assume LTE." (Radiative transfer); "To mimic high resolution ALMA observations, the emission is convolved with a $0.05\ensuremath{''}$ beam, unless denoted otherwise." (Radiative transfer)
   - software: DALI
   - parameter: Distance 100 pc, inclination 38 deg  
  > "the disk is assumed to be located at a distance of 100 pc and the inclination is taken to be 38$\degree$" (Radiative transfer)
   - assumption: Radial emission profiles taken along the semi-major axis  
  > "The radial emission profiles are taken to be along the semi-major axis of the disk." (Radiative transfer)
   - fitting: _not stated_
   - validation: _not stated_
4. **Quantify the snowline effect and disentangle ring origins**: Compare NW and W emission; define maximum relative difference; rerun with dust opacities divided by 1e10; inspect J-level populations  
  > "This maximum relative difference is defined as the maximum difference between the flux predicted by network NW and W compared to the maximum flux predicted by network W" (HCO$^+$ and H$^{13}$CO$^+$ emission); "the dust opacities (dust mass absorption coefficients $\kappa_{\nu}$) are divided by a factor of $10^{10}$" (Continuum optical depth)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_
5. **Test line profiles as a snowline diagnostic**: Subtract the network W line profile from the network NW profile for J=2-1 of HCO+ and H13CO+  
  > "To show the difference between the models we subtracted the spectrum associated with network W from the spectrum associated with network NW." (Line profiles)
   - software: DALI
   - fitting: _not stated_
   - validation: _not stated_
6. **Detect H13CO+ J=4-3 in V883 Ori (band 7)**: Continuum-subtract, make tclean line cubes, velocity-stack with Keplerian model, fit two Gaussians to acetaldehyde lines excluding +-1 km/s around H13CO+, subtract fit  
  > "This Doppler shift is then used to shift the spectrum of each pixel to the velocity of the star, before adding the spectra of all pixels." (H$^{13}$CO$^+$ observations); "In addition, emission within 1 km s$^{-1}$ from the rest frequency of the $J=4-3$ transition of H$^{13}$CO$^+$ is excluded from the fit." (H$^{13}$CO$^+$ observations)
   - software: CASA 5.1.1 tclean, scipy curve_fit
   - parameter: Stacking with M_star = 1.3 Msun, i = 38 deg, PA = 32 deg; acetaldehyde line frequencies fixed, widths fixed to 2 km/s  
  > "To reduce the number of free parameters in the fit, the line frequencies are fixed to their respective rest frequencies listed above and the widths of the lines are fixed to 2 km s$^{-1}$ following (cite: Lee2019)." (H$^{13}$CO$^+$ observations)
   - fitting: Two Gaussian profiles fitted to acetaldehyde emission with curve_fit; no priors or sampler  
  > "To quantify this excess emission, two Gaussian profiles are fitted with" (H$^{13}$CO$^+$ observations)
   - validation: Detection judged at >5 sigma after subtracting the acetaldehyde fit  
  > "Therefore we conclude that H$^{13}$CO$^+$ is detected at $>$5$\sigma$" (H$^{13}$CO$^+$ observations)
7. **Locate the water snowline in V883 Ori with HCO+ J=3-2**: Build DALI model of V883 Ori for three luminosities, convolve to the observed resolution, compare deprojected normalized azimuthal averages of model and observed HCO+ J=3-2  
  > "The model results are convolved to the same spatial resolution as the observations before calculating the deprojected azimuthal average." (Model HCO$^+$ images: locating the snowline); "The observed peak location and gap depth in the center best match with a snowline between 76 and 119 AU." (Model HCO$^+$ images: locating the snowline)
   - software: DALI
   - parameter: Luminosities 2e3, 6e3, 1.4e4 Lsun giving snowlines at 47, 76, 119 AU  
  > "We therefore use three luminosities of $2\times 10^3$, $6\times 10^3$ and $1.4\times 10^4$ L$_{\odot}$ in our models, which put the snowline at 47, 76, and 119 AU, respectively." (Model HCO$^+$ images: locating the snowline)
   - parameter: Characteristic radius 75 AU; disk mass 0.25 Msun  
  > "The characteristic disk radius is set to 75 AU" (Model HCO$^+$ images: locating the snowline); "This gives an estimated disk mass of 0.25 M$_{\odot}$." (Model HCO$^+$ images: locating the snowline)
   - parameter: Predictions for future observations convolved with a 0.1'' beam  
  > "The results in this section are convolved with a small $0.1\ensuremath{''}$ beam" (Model HCO$^+$ images: locating the snowline)
   - assumption: Dust temperature 50 K for the disk mass estimate  
  > "As V883 Ori is an outbursting source, a dust temperature of 50 K is assumed." (Model HCO$^+$ images: locating the snowline)
   - fitting: Visual comparison of peak location and central gap depth; no quantitative fit  
  > "The observed peak location and gap depth in the center best match with a snowline between 76 and 119 AU." (Model HCO$^+$ images: locating the snowline)
   - validation: Continuum becomes optically thin well within 100 AU in all models; complex organic molecules peak inside the HCO+ ring  
  > "Furthermore, the continuum becomes optically thin well within 100 AU in all three of our models" (Model HCO$^+$ images: locating the snowline)

## Software

- **DALI** : Thermochemical disk model (temperature) and ray tracing of line emission  
  > "Predictions for multiple transitions of HCO$^+$ and H$^{13}$CO$^+$ were made using the ray tracer in" (Radiative transfer)
- **CASA** 5.1.1: tclean imaging of band 7 line data  
  > "Using the CASA 5.1.1" (H$^{13}$CO$^+$ observations)
- **scipy odeint (LSODA)** : Time-dependent solution of the chemical networks  
  > "part of the Scipy package in python and uses the LSODA routine from the ODEPACK library in FORTRAN" (Footnote 1)
- **scipy curve_fit** : Gaussian fits to acetaldehyde emission  
  > "function is part of the Scipy package in python." (Footnote 2)
- **LAMDA database** : Collisional rate coefficients for line radiative transfer  
  > "we used the collisional rate coefficients in the LAMDA database" (Radiative transfer)
- **UMIST rate12 database** rate12: Gas-phase reaction rate coefficients  
  > "are taken from the rate12 UMIST database (cite: McElroy2013)" (Table 2 notes)
- **JPL molecular database** : Rest frequencies of acetaldehyde lines  
  > "(Jet Propulsion Laboratory (JPL) molecular database; (cite: Pickett1998))" (H$^{13}$CO$^+$ observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Water snowline radius, typical Herbig Ae model | 4.5 | not stated | AU | 2 | the water snowline, the midplane location where water freezes-out, is located at 4.5 AU |
| HCO+ abundance jump outside the water snowline | two orders of magnitude over 2 AU | not stated | dimensionless | 2 | The HCO$^+$ abundance jumps by two orders of magnitude over a radial range of 2 AU outside the water snowline |
| HCO+ column density jump outside the snowline (network W) | ~230 over 3 AU | not stated | dimensionless | 3 | the total HCO$^+$ column density jumps by a factor $\sim230$ over a radial range of 3 AU outside the water snowline in network W |
| Maximum relative emission difference NW vs W, HCO+ J=2-1 | 24 | not stated | % | 4 | translates into a relative maximum difference of only 24% between the radial emission profiles of the $J=2-1$ transition of HCO$^+$ |
| Maximum relative emission difference NW vs W, H13CO+ J=2-1 | 13 | not stated | % | 4 | The relative maximum difference between chemical network NW and W is 13% for H$^{13}$CO$^+$ |
| H13CO+ flux relative to HCO+ (J=2-1) | about 39 times lower | not stated | dimensionless | 3 | Though the expected flux is about 39 times lower for H$^{13}$CO$^+$ than for HCO$^+$. |
| Radius out to which dust is optically thick, Herbig Ae model | ~14 | not stated | AU | 4 | the dust in the typical Herbig Ae disk model is optically thick out to $\sim$14 AU |
| Line-wing flux difference NW minus W | 1.75 mJy (HCO+), 28 uJy (H13CO+); 0.6% and 0.3% of emission | not stated | mJy / uJy | 5 | this difference is only 1.75 mJy for HCO$^+$ and 28 $\mu$Jy for H$^{13}$CO$^+$ i.e. 0.6% and 0.3% of emission |
| Noise in stacked V883 Ori band 7 spectrum | ~15 | not stated | mJy per spectral bin | 6 | The noise level of $\sim$15 mJy per spectral bin is determined using an empty region in the stacked image. |
| H13CO+ J=4-3 detection significance in V883 Ori | >5 | not stated | sigma | 6 | H$^{13}$CO$^+$ is detected at $>$5$\sigma$ |
| V883 Ori disk mass estimate | 0.25 | not stated | Msun | 7 | This gives an estimated disk mass of 0.25 M$_{\odot}$. |
| Model snowline radii for the three V883 Ori luminosities | 47, 76, 119 | not stated | AU | 7 | which put the snowline at 47, 76, and 119 AU, respectively |
| V883 Ori water snowline radius inferred from HCO+ J=3-2 | ~75-120 | not stated | AU | 7 | our analysis is consistent with a water snowline at $\sim$75-120 AU in V883 Ori |

## Qualitative findings

- Emission of HCO+ and H13CO+ is ring-shaped due to gas-phase water destruction, continuum optical depth and molecular excitation, so locating the snowline in Herbig Ae disks is difficult  
  > "We find that the emission of H$^{13}$CO$^+$ and HCO$^+$ is ring-shaped due to three effects: destruction of HCO$^+$ by gas-phase water, continuum optical depth, and molecular excitation effects." (abstract)
- Observed HCO+ J=3-2 is ring-shaped while complex organic molecules peak inside the ring, so the HCO+ central hole is not only due to continuum optical depth  
  > "This azimuthal average shows that the HCO$^+$ emission is ring shaped." (HCO$^+$ observations)

## Claim tuples

- H: Gas-phase water destruction of HCO+ makes HCO+ abundance trace the water snowline | E: Two small chemical networks (NW without water, W with water) on a DALI Herbig Ae disk | R: HCO+ abundance jumps by two orders of magnitude over 2 AU outside the snowline at 4.5 AU | F: HCO+ abundance is a good chemical tracer of the water snowline | **supported**
- H: The snowline signature is observable in HCO+ and H13CO+ J=2-1 emission of Herbig Ae disks | E: Ray-traced J=2-1 emission for networks NW and W convolved with a 0.05'' beam | R: Water causes only an additional ~13% (H13CO+) and 24% (HCO+) drop in the disk center | F: Locating the snowline with HCO+ in Herbig Ae disks is very difficult | **partially**
- H: Outbursting sources such as V883 Ori make HCO+ a usable snowline tracer | E: DALI models of V883 Ori with three luminosities | R: Dust and excitation effects do not limit HCO+ as a tracer if the snowline lies beyond ~40 AU | F: HCO+ can trace the snowline in V883 Ori-like disks | **supported**
- H: The water snowline of V883 Ori is at ~42 AU as estimated from the continuum intensity break | E: Compare archival ALMA band 6 HCO+ J=3-2 azimuthal average with models of snowline at 47, 76, 119 AU | R: Observed peak location and central gap best match a snowline between 76 and 119 AU | F: Snowline is around 100 AU, outside the continuum opacity change at 42 AU | **partially**

## Reasoning

- Why this data: Archival V883 Ori data were the only H13CO+ dataset with sufficient resolution and sensitivity, and a band 6 HCO+ dataset was available  
  > "To date, these observations are the only H$^{13}$CO$^+$ observations in a protoplanetary disk, to our knowledge, at sufficient spatial and spectral resolution with sufficient sensitivity to potentially resolve the water snowline." (H$^{13}$CO$^+$ observations)
- Why this method: J=2-1 chosen for the best balance between line brightness and continuum optical depth  
  > "because this transition provides the best balance between the brightness of the line and the effects of the continuum optical depth" (Radiative transfer)
- Alternative: H13CO+ J=4-3 rejected for snowline imaging because it is blended with acetaldehyde  
  > "The line blending of H$^{13}$CO$^+$ $J=4-3$ with acetaldehyde prevents us from using the only available dataset" (H$^{13}$CO$^+$ observations)
- How they decided it was enough: _not stated_
- Limitation (authors): Band 6 beam (~0.5'') cannot resolve a snowline inside ~90 AU  
  > "The spatial resolution of $\sim0.5\ensuremath{''}$ is insufficient to resolve the water snowline" (HCO$^+$ observations)
- Limitation (authors): Viscous heating and self-absorption in outbursting sources are not modelled  
  > "One effect that needs to be taken into account in outbursting sources like V883 Ori is viscous heating." (Model HCO$^+$ images: locating the snowline)
- Caveat (inferred, ours): Snowline location in V883 Ori rests on a visual match of model and observed azimuthal profiles at a beam larger than the snowline radius, with no fit statistic or uncertainty
- Caveat (inferred, ours): Models use a small chemical network and fixed parameters; model luminosity values are artificially raised to move the snowline
- Caveat (inferred, ours): Band 6 data details are deferred to an in-prep paper

## Reproducibility

- Data public (paper): Archival ALMA data with project codes given  
  > "Models are then compared with archival ALMA data." (abstract)
- Products in archive: Band 6 HCO+ J=3-2 product data used  
  > "the observed emission from the product data of the $J=3-2$ transition of HCO$^+$" (HCO$^+$ observations)
- Missing: DALI configuration and code access
- Missing: Calibration, spectral windows and channel selections for both ALMA datasets
- Missing: Band 6 imaging parameters and deprojection geometry
- Missing: Numerical model profiles needed to reproduce the figure comparison
- Data volume (inferred): Tens of GB for the two archival projects (rough estimate, sizes not stated)
- Score (inferred): 2/5, Model parameters are tabulated and the chemical network is fully specified, but DALI setup, ALMA calibration and imaging choices are mostly not given and the observational comparison is qualitative.
- Rediscovery candidate: no, Main results are model predictions plus a qualitative comparison with ALMA data; the observational recipe is incomplete and the key code setup is unstated.

## Links

- Method: Lee et al. 2019 (cite: Lee2019) (Band 7 V883 Ori observations and velocity stacking approach followed)
- Method: Bruderer et al. 2009, 2012; Bruderer 2013 (cite: Bruderer2009; Bruderer2012; Bruderer2013) (DALI thermochemical code)
- Method: Andrews et al. 2011 (cite: Andrews2011) (Disk density structure approach)
- Companion: van 't Hoff et al. 2018b (cite: vantHoff2018methanol) (Methanol and C18O observations of V883 Ori; snowline near 100 AU)
- Companion: Cieza et al. 2016 (cite: Cieza2016) (Previous snowline estimate at 42 AU from continuum)
- Companion: Ruiz-Rodriguez et al. in prep. (Presents the band 6 HCO+ data)
- Related: VANDAM survey

## Checks

```json
{
 "quotes": 115,
 "quotes_ok": 115,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 110,
  "stated": 78,
  "rate": 0.709
 },
 "evidence_ok": true
}
```
