# The debris disc of HD 131488: bringing together thermal emission and scattered light

`2024MNRAS.527.3559P` | Monthly Notices of the Royal Astronomical Society 2024 | first author: Pawellek, Nicole | arXiv: 2311.03272 | DOI: 10.1093/mnras/stad3455

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: debris_disks
- Question: Can scattered light (SPHERE) and thermal emission (SED) of the CO-rich debris disc HD 131488 be fitted self-consistently with a semi-dynamical N-body model, and what does this imply for gas drag, porosity and size distribution  
  > "To further explore gas-dust interactions in an optically thin environment, in this paper we present the first spatially resolved scattered light images of the gaseous debris disc around HD 131488 obtained with the SPHERE instrument." (1 Introduction); "We use N-body simulations to model both the scattered light images and the SED of the disc in a self-consistent way." (abstract)
- Target **HD 131488**: coordinates _not stated_; z/distance 154.0 +/- 2.5 pc  
  > "HD 131488 is an A1-type star at a distance of 154.0$\pm$2.5 pc" (1 Introduction); "after updating the distance of HD 131488 by Gaia data" (4.3.3 DDA model / Mie model); distance from Gaia (cite: gaia-collaboration-et-al-2016; lindegren-et-al-2018; bailer-jones-et-al-2018)  
  > "HD 131488 is an A1-type star at a distance of 154.0$\pm$2.5 pc" (1 Introduction); "after updating the distance of HD 131488 by Gaia data" (4.3.3 DDA model / Mie model)

## Data provenance

- ALMA projects: 2015.1.01243.S
- bands: 1.3 mm (ALMA continuum and CO J=2-1, from the earlier study)  
  > "Using the ALMA interferometer at 1.3 mm, recently the disc was successfully resolved in continuum and in $J=2-1$ rotational transitions of" (1 Introduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (not stated)
- Other facility **VLT/SPHERE (IRDIS and IFS)**: New near-IR scattered light images: IRDIS H23 dual-band and IFS Y-J, ESO programme 0101.C-0753(B), 7 April 2018  
  > "We observed the disc around HD 131488 in the programme 0101.C-0753(B) (PI: A. Moór) on the night of 7$^\text{th}$ April 2018 for one hour with the SPHERE instrument of the VLT" (2 Observations and data reduction)
- Other facility **Archival photometry (Tycho, APASS, Gaia, DENIS, 2MASS, WISE, AKARI, Herschel/PACS, ATCA)**: Continuum photometry used to constrain the SED / thermal emission model (Table 1)  
  > "The photometric data of the dust continuum used to constrain the thermal emission model are given in Tab." (4.4.1 Model set-up)
- Other facility **Gaia**: Stellar distance and photometry  
  > "after updating the distance of HD 131488 by Gaia data" (4.3.3 DDA model / Mie model)
- External data: ALMA Gaussian ring parameters: maximum of surface brightness at 88 +/- 3 au, total disc width 46 +/- 12 au  
  > "That study finds the maximum of the surface brightness at a distance of $(88\pm3)$ au, and a total disc width of ($46\pm12$) au." (2.1 Radial profiles) [from (cite: moor-et-al-2017)]
- External data: ALMA CO gas mass of 9e-2 Earth masses  
  > "The study estimated a gas mass of $9\times10^{-2}$ $M_\oplus$" (3.5.3 Influence of gas on the size distribution) [from (cite: moor-et-al-2017)]
- External data: Stellar temperature, metallicity and surface gravity used for the ATLAS9 photosphere  
  > "Here, the stellar temperature, metallicity, and surface gravity provided by" (4.1 Stellar photosphere and dust composition) [from (cite: rebollido-et-al-2018)]
- External data: ALMA 1.3 mm flux density (2.91 mJy), ATCA 8.75 mm and other photometry in Table 1 taken from the listed references  
  > "The photometric data of the dust continuum used to constrain the thermal emission model are given in Tab." (4.4.1 Model set-up) [from (cite: moor-et-al-2017; norfolk-et-al-2021; marton-et-al-2017; wright-et-al-2010; cutri-et-al-2003)]
- External data: Stellar mass of 1.8 Msun for the CO position-velocity diagram  
  > "and a stellar mass of 1.8 $M_{\odot}$" (Appendix 12CO position-velocity diagram) [from (cite: matra-et-al-2018)]
- Simulation/model as data: ACE collisional simulation of a planetesimal belt between 88 and 118 au to estimate Poynting-Robertson-drag dust  
  > "for a planetesimal belt between 88 and 118 au and bodies up to 40 km in radius." (5.2.2 Inward transport - PR-drag); "We collisionally evolve the belt for several Myr and infer the surface density of the dust as function of radius." (5.2.2 Inward transport - PR-drag)

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

- ALMA visibilities fitted with a Gaussian ring model; ALMA data reduction and ring fit taken from the earlier ALMA paper  
  > "By fitting the measured ALMA visibilities using a Gaussian ring model" (2.1 Radial profiles) [from (cite: moor-et-al-2017)]
- SPHERE radial surface-brightness profile extraction method  
  > "We extracted the radial profile of the surface brightness using the same method as described in" (2.1 Radial profiles) [from (cite: choquet-et-al-2017)]
- SED calculation approach (SONATA), extended with radiation pressure  
  > "The SED is calculated by the same approach as the SONATA code" (4.4.1 Model set-up) [from (cite: pawellek-et-al-2014; pawellek-krivov-2015; pawellek-et-al-2021)]
- Collisional model for production of sub-blowout grains  
  > "Sub-blowout grains are produced following the collisional model of" (4.3.2 Mie model) [from (cite: wyatt-et-al-2007b)]
- Porous grain model used for DDA  
  > "we will use the porous grain model of" (3.3 Dust composition) [from (cite: kirchschlager-wolf-2013)]
- Gas-drag dust migration treatment (stability distance)  
  > "We use the classical approach of" (5.2.3 Inward transport - gas drag) [from (cite: takeuchi-artymowicz-2001)]

### Not stated but needed to reproduce (our reading)

- How the 1.65 mm (1652 micron) ALMA flux density marked 'This work' in Table 1 was measured, from which data, and with what imaging/aperture
- ALMA array configuration, spectral setup, imaging parameters and calibration of the data used for the CO position-velocity diagram
- How the CO position-velocity diagram was extracted (task, aperture width, channel range, beam)
- MODERATO code and its input grids (size bins, number of particles, optical-constant files for astrosilicate) are not provided
- DDA code and settings (number of dipoles, void placement realisation) not named
- SONATA SED fit settings (priors, free parameters of the second belt, fit statistic)
- Per-pixel noise image construction details beyond derotation in the opposite direction, and the pixel mask used in chi2
- Stellar flux density, luminosity and mass sources for the models beyond ATLAS9 inputs

## Analysis recipe

1. **Reduce SPHERE IRDIS/IFS data and extract the disc**: HC-DC pre-processing, then classical ADI (median coronagraphic model subtracted, de-rotate, stack) and a PCA reduction  
  > "which consisted of building a model of the coronagraphic image from the median of all pupil-stabilised images, which was then subtracted from each frame before de-rotating and stacking the images." (2 Observations and data reduction)
   - software: HC-DC, ESO Data Reduction and Handling software, ANDROMEDA
   - parameter: PCA retaining two principal components  
  > "retaining two principal components, a value found to maximise the signal-to-noise (SNR) of the disk." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Both ADI and PCA reductions compared; ANDROMEDA used to look for point sources  
  > "Both reduction methods lead to similar results." (2.1 Radial profiles)
2. **Fit Henyey-Greenstein geometric model to get PA, inclination, g, r0**: Forward modelling of the scattered light with a two-part power-law radial profile and HG phase function  
  > "We use a simple geometric model with the free parameters PA, inclination, $g$, central radius $r_0$, and flux density." (4.3.1 Henyey-Greenstein model)
   - parameter: Radial power-law slopes fixed to alpha1=12 and alpha2=-12  
  > "The slopes of the power law were fixed to $\alpha_1=12$ and $\alpha_2=-12$ so that the disc is narrow" (4.3.1 Henyey-Greenstein model)
   - assumption: Zero disc eccentricity  
  > "We assume a zero disc eccentricity." (4.3.1 Henyey-Greenstein model)
   - fitting: chi2 minimisation on the residual image  
  > "To find the best fit model, we use a $\chi^2$-minimisation assuming that an ideal residual image should only contain white noise in each pixel." (4.2 Fitting approach)
   - validation: _not stated_
3. **Constrain CO gas extent and gas surface density from ALMA 12CO**: Position-velocity diagram of 12CO J=2-1 with two Keplerian orbital radii bracketing the emission  
  > "By varying the two orbital radii such that the white wedges enclose most of the CO emission, we find that the CO gas is mostly contained between 30 and 130 au." (Appendix 12CO position-velocity diagram)
   - parameter: Inclination and PA from scattered light, stellar mass 1.8 Msun  
  > "obtained assuming the inclination and position angle derived from the scattered light images, and a stellar mass of 1.8 $M_{\odot}$" (Appendix 12CO position-velocity diagram)
   - assumption: Keplerian rotation  
  > "and assuming Keplerian rotation." (Appendix 12CO position-velocity diagram)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit scattered light with semi-dynamical radiation-pressure models (Mie and DDA)**: MODERATO dust-orbit models with free disc width, dust mass, size index q and porosity P, compared with IRDIS image by chi2  
  > "We use the following free parameters: disc width $\Delta r$, dust mass $M_\text{d}$, size distribution index $q$, and dust porosity $P$." (4.3.2 Mie model); "In order to analyse the scattered light and thermal emission data of HD 131488, we make use of the MODERATO code" (3 Theoretical Background)
   - software: MODERATO
   - parameter: PA and i fixed to the HG values  
  > "We fix PA and $i$ to the values inferred from the HG approach to keep the fitting process fast." (4.3.2 Mie model)
   - parameter: Maximum grain size 1e4 micron, minimum 0.1 micron  
  > "To account for most of the cases we will assume a maximum size of $10^4\mu$m" (3.5.2 Maximum grain size and size distribution index); "we will not fix our size distribution to the blowout limit but to a size of 0.1 $\mu$m to account for the presence of those sub-blowout grains" (3.5.1 Minimum size)
   - parameter: Porosity grid 0.0 to 0.8 in steps of 0.2  
  > "($0.0 \leq P \leq 0.8$ in steps of 0.2)" (4.3.2 Mie model)
   - assumption: Pure astronomical silicate, bulk density 3.3 g/cm3, porosity via Bruggeman EMT (Mie) or vacuum voids of 1/100 grain diameter (DDA)  
  > "We assume a dust composition of pure astronomical silicate with a bulk density of 3.3 g/cm$^{3}$" (4.1 Stellar photosphere and dust composition); "We assume the diameter of the vacuum inclusions (“voids”) to be as large as 1/100 of the grain diameter" (3.3 Dust composition)
   - assumption: Proper eccentricity of colliding planetesimals 0.1  
  > "we assume a proper eccentricity $\langle e\rangle$ of the colliding planetesimals of 0.1" (3.5.1 Minimum size)
   - fitting: chi2 minimisation; parameter uncertainties from varying each parameter until chi2 exceeds the critical value  
  > "Based on the best-fit parameter values we change each free parameter individually until the final $\chi^2$ gets larger than the critical value." (4.2 Fitting approach)
   - validation: Reduced chi2 <= 1.05 as 95 per cent confidence criterion  
  > "In terms of a reduced $\chi^2$ this means a value of $\leq 1.05$ in our case." (4.2 Fitting approach)
5. **Fit the SED / thermal emission to get the dust mass**: SONATA two-component fit, then MODERATO with radiation pressure for the outer belt  
  > "In a first approach we use the SONATA code to fit a two component model to the observational data" (4.4.2 Results); "In a second approach we use the MODERATO code which now includes the effects of radiation pressure." (4.4.2 Results)
   - software: SONATA, MODERATO, ATLAS9
   - parameter: Scattered-light best-fit parameters applied: P=0.6, q=3.0, r0=88 au, Delta r=30 au; dust mass then fitted to 1 Mearth  
  > "we find that the observational data can be fitted when using a dust mass of $1\,M_\oplus$ instead of $5\,M_\oplus$" (4.4.2 Results)
   - assumption: Only the outer Kuiper-belt analogue modelled; inner warm belt not modelled with MODERATO  
  > "Hence, we do not model a possible Asteroid belt analogue with MODERATO but only the outer Kuiper belt analogue" (4.4.2 Results)
   - fitting: _not stated_
   - validation: _not stated_
6. **Add gas drag to reconcile scattered-light and SED dust masses and derive gas surface density**: Vary gas surface density; grains with Stokes number St<=1 retained by setting beta to zero  
  > "In a simple approach we vary the gas surface density and assume that particles for which the Stokes number is" (4.5 Combining SED and scattered light results); "are retained within the disc by setting the $\beta$ parameter to zero." (4.5 Combining SED and scattered light results)
   - software: MODERATO
   - parameter: q=3.0, dust mass fixed to 1 Mearth in both scattered light and SED  
  > "we need a surface density of $\Sigma = (2.0\pm0.1)\times 10^{-5}\,M_\oplus/$au$^2$ to fit both the SED and the scattered light data." (4.5 Combining SED and scattered light results)
   - assumption: beta itself is unchanged by gas; only the grain orbits are  
  > "We note that in reality $\beta$ is not changed by the presence of gas, but the grains’ orbits are." (4.5 Combining SED and scattered light results)
   - fitting: _not stated_
   - validation: Compared with ALMA-based gas surface density estimate (rough, no uncertainty)  
  > "this value is in agreement with expectations/estimates from ALMA observations." (4.5 Combining SED and scattered light results)

## Software

- **HC-DC (High Contrast Data Centre)** : Pre-processing of raw SPHERE IRDIS and IFS data  
  > "The raw IRDIS and IFS data were pre-processed by the High Contrast Data Centre (HC-DC)" (2 Observations and data reduction)
- **ESO Data Reduction and Handling software** : Native recipes within the SPHERE pre-processing  
  > "It uses native recipes from the ESO Data Reduction and Handling software" (2 Observations and data reduction)
- **ANDROMEDA** : Search for point-like sources (planets) in the SPHERE data  
  > "we made use of the ANgular Differential OptiMal Exoplanet Detection Algorithm" (2.2 Presence of planets)
- **MODERATO** : Semi-dynamical dust disc models: orbits, scattered light and thermal images  
  > "In order to analyse the scattered light and thermal emission data of HD 131488, we make use of the MODERATO code" (3 Theoretical Background)
- **SONATA** : Two-component SED fit without radiation pressure  
  > "In a first approach we use the SONATA code to fit a two component model to the observational data" (4.4.2 Results)
- **ACE** : Collisional evolution of the planetesimal belt to estimate PR-drag dust  
  > "To do so we use the collisional code ACE" (5.2.2 Inward transport - PR-drag)
- **ATLAS9** : Stellar photosphere model  
  > "we apply an ATLAS9 model" (4.1 Stellar photosphere and dust composition)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disc position angle (H23, forward model) | 97 | +/- 2 | deg | 2 | We found the PA of the disc in H23-band to be $(97\pm 2)^\circ$ and the inclination to be $(84^{+1.5}_{-2.0})^\circ$. |
| Disc inclination (H23, forward model) | 84 | +1.5/-2.0 | deg | 2 | We found the PA of the disc in H23-band to be $(97\pm 2)^\circ$ and the inclination to be $(84^{+1.5}_{-2.0})^\circ$. |
| HG asymmetry parameter g | 0.67 | +/- 0.07 | dimensionless | 2 | We included an adhoc phase function and find a best fitting value for the asymmetry parameter $g = \langle\cos(\vartheta)\rangle$ of ($0.67\pm0.07$) |
| HG central radius r0 | 110 | +/- 25 | au | 2 | The best fit value for $r_0$ is then found for ($110\pm25$) au but remains rather uncertain. |
| Average disc SNR with ADI between 22 and 80 au | 4 | not stated | dimensionless | 1 | Our observations reach an average disc signal-to-noise (SNR) level of 4 using an ADI reduction between 22 and 80 au. |
| CO gas radial extent | 30-130 | not stated | au | 3 | we find that the CO gas is mostly contained between 30 and 130 au. |
| Average CO gas surface density from ALMA | 2e-6 | not stated | Mearth au^-2 | 3 | These translate to an average gas surface density of $2\times10^{-6}$ $M_\oplus$ au$^{-2}$. |
| Mie model size distribution index q | 3.0 | +/- 0.1 | dimensionless | 4 | The best-fitting size distribution index is $q=3.0\pm 0.1$. |
| Mie model dust mass (radiation pressure only) | 4.5 | +/- 0.8 | Mearth | 4 | we need a dust mass of $\sim4.5\pm0.8\,M_\oplus$ to fit the scattering flux density observed |
| Best-fitting porosity (Mie) | 0.6 | 0.0-0.4 not excluded | dimensionless | 4 | We find a best fitting porosity of 0.6. |
| Parent belt width (asymmetric Gaussian, Mie) | 30 | +/- 3 | au | 4 | With this approach we find a best fitting disc width of ($30\pm3$) au |
| DDA model size distribution index q and dust mass | q=3.0; M=4.4 | q +/- 0.2; M +/- 0.7 | q dimensionless; Mearth | 4 | The size distribution index is found as $q=3.0\pm 0.2$, and the dust mass as $M_\text{dust} \approx 4.4\pm0.7~M_\oplus$. |
| Blowout size, compact grains to P=0.8 (Mie) | 2.9 (compact) to ~11 (P=0.8) | not stated | micron | 4 | the blowout sizes vary between $2.9\,\mu\hbox{m}$ for compact grains and $\sim11\,\mu\hbox{m}$ for particles with a porosity of 0.8 |
| Dust mass from SED | 1.0 | +/- 0.2 | Mearth | 5 | We find a best-fitting model for a dust mass of $1.0\pm0.2~M_\oplus$ |
| Gas surface density needed to fit SED and scattered light | 2.0e-5 | +/- 0.1e-5 | Mearth au^-2 | 6 | we need a surface density of $\Sigma = (2.0\pm0.1)\times 10^{-5}\,M_\oplus/$au$^2$ to fit both the SED and the scattered light data. |

## Qualitative findings

- No point source above the 5 sigma contrast threshold in the SPHERE data  
  > "there is no point source above the $5\,\sigma$ contrast threshold shown in Fig." (2.2 Presence of planets)
- Large particles contribute significantly to the scattered light because of the shallow size distribution  
  > "We also show that the shallow size distribution of the dust leads to a significant contribution of large particles to the overall amount of scattered light." (abstract)
- Scattered-light models predict little dust inside 88 au  
  > "HG, DDA, and Mie predict that within 88 au the amount of dust material has to be small in order to fit the scattered light data" (5.2.1 ALMA vs SPHERE)

## Claim tuples

- H: Can one dust model fit both scattered light and thermal emission of HD 131488 | E: Radiation-pressure-only MODERATO fits to SPHERE image and SED, then added gas drag by retaining sub-blowout grains | R: Radiation pressure alone needs ~4.4 Mearth in scattered light versus 1.0 Mearth from the SED; with gas drag both are fitted with 1 Mearth and Sigma = (2.0+/-0.1)e-5 Mearth/au^2 | F: Only with gas drag can scattered light and thermal emission be fitted consistently; the implied gas density agrees roughly with ALMA-based estimates | **supported**
- H: Does DDA improve on Mie theory for modelling this disc's scattered light | E: Mie plus EMT versus DDA with small vacuum voids, same fitting | R: Similar chi2 and parameters (P=0.6, q=3.0) | F: DDA and Mie give similar results for spherical grains with small voids; Mie is adequate for this disc | **supported**
- H: What is the porosity of the dust | E: Phase-function comparison with HG g=0.67 and fit quality versus porosity | R: Best fit P=0.6, lower values not excluded, P=0.8 excluded | F: Porosity about 0.2 to 0.6, consistent with a pebble pile scenario | **supported**
- H: Is the scattered-light radial profile consistent with the ALMA ring | E: Compared HG, Mie and DDA radial profiles with the ALMA Gaussian ring | R: Scattered light prefers little dust inside 88 au, unlike the ALMA Gaussian (width 46 au versus 30 au for an asymmetric profile) | F: The profiles deviate inside 88 au, possibly due to the low ALMA resolution; the outer regions agree | **partially**
- H: Does the disc show a blue scattered-light colour | E: Reflectance at five wavelengths from IFS and IRDIS compared with models | R: Weak decrease of reflectance with wavelength with large uncertainties | F: Slightly blue colour suggested but not constraining | **partially**

## Reasoning

- Why this data: HD 131488 has an outstandingly high CO mass, making it ideal for studying gas-dust interaction  
  > "The outstandingly high CO mass makes HD 131488 an ideal choice for a detailed study of the gas-dust interaction." (1 Introduction)
- Why this method: Semi-dynamical model gives self-consistent scattered light and thermal emission  
  > "This approach guarantees that the models for thermal emission and scattered light are self-consistent." (4.4.1 Model set-up)
- Alternative: Varying void size and orientation in DDA was not done because of the extra parameters and computing time  
  > "We decided against a variation of the voids for our scattered light models of the debris disc around HD 131488 as this would open several dimensions in parameter space" (3.3 Dust composition)
- Alternative: High proper eccentricity (0.9) pure radiation-pressure model rejected: poor chi2 and too short a collisional timescale  
  > "a proper eccentricity of 0.9 leads to a very short collisional timescale for the planetesimals." (5.5 Combining scattered light and SED models)
- How they decided it was enough: _not stated_
- Limitation (authors): Gas surface density is a rough estimate without uncertainties  
  > "We note that this is a rough estimate without uncertainties as we do not have enough data on gas species present in the disc." (4.5 Combining SED and scattered light results)
- Limitation (authors): Disc extent beyond 90 au uncertain because of low SNR  
  > "However, in this region the SNR is low so that the actual extent beyond 90 au remains uncertain." (2.1 Radial profiles)
- Limitation (authors): Inner disc poorly constrained by the low-resolution, nearly edge-on ALMA data  
  > "Due to the low spatial resolution of the ALMA data and the nearly edge-on orientation of the disc, the region within 88 au is not well constrained at long wavelengths." (5.2.1 ALMA vs SPHERE)
- Caveat (inferred, ours): Gas drag is implemented by setting beta to zero for grains with St<=1, a crude treatment, so the derived gas density depends on that assumption
- Caveat (inferred, ours): Gas density and eccentricity are degenerate (e=0.5 also fits with half the gas)
- Caveat (inferred, ours): Scattered-light SNR is only 3 to 4, so chi2 constraints are weak
- Caveat (inferred, ours): ALMA role is limited to literature results and a 12CO position-velocity reanalysis with unspecified details

## Reproducibility

- Data public (paper): ALMA and VLT/SPHERE data are public; other data on request  
  > "The ALMA and VLT/SPHERE data are publicly available and can be queried and downloaded directly from the ALMA archive" (Data Availability); "The data underlying this article will be shared on request to the corresponding author." (Data Availability)
- Products in archive: _not stated_
- Missing: MODERATO and SONATA code and settings (not released as stated)
- Missing: Details of the ALMA CO reanalysis and the new 1.65 mm flux measurement
- Missing: SPHERE reduction parameters beyond ADI/PCA with two components
- Data volume (inferred): SPHERE IRDIS/IFS raw cubes a few GB; ALMA Band 6 data for 2015.1.01243.S likely tens of GB if reprocessed
- Score (inferred): 2/5, Data are public but the central models rely on the unreleased MODERATO code and the ALMA analysis details are not given, though numeric results are tabulated
- Rediscovery candidate: no, The main results come from an unreleased semi-dynamical code and SPHERE modelling; ALMA plays a minor supporting role

## Links

- Method: (cite: pawellek-et-al-2019b) (MODERATO code and Mie scattered-light disc modelling)
- Method: (cite: wyatt-et-al-2007b) (Collisional model for sub-blowout grain production)
- Method: (cite: choquet-et-al-2017) (Radial profile extraction method)
- Method: (cite: kirchschlager-wolf-2013) (Porous DDA grain model)
- Method: (cite: takeuchi-artymowicz-2001) (Gas-drag dust migration)
- Companion: (cite: moor-et-al-2017) (ALMA 1.3 mm continuum and CO observations of HD 131488)
- Companion: (cite: melis-et-al-2013) (Discovery of the infrared excess of HD 131488)
- Related: ESO programme 0101.C-0753(B) (SPHERE)
- Related: ALMA 2015.1.01243.S

## Checks

```json
{
 "quotes": 97,
 "quotes_ok": 97,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 15,
 "numeric_problems": 0,
 "fill": {
  "facts": 105,
  "stated": 62,
  "rate": 0.59
 },
 "evidence_ok": true
}
```
