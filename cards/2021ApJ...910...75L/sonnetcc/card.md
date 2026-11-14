# What Produces Dust Polarization in the HH 212 Protostellar Disk at 878 μm: Dust Self-scattering or Dichroic Extinction?

`2021ApJ...910...75L` | The Astrophysical Journal 2021 | first author: Lee, Chin-Fei | arXiv: 2102.11481 | DOI: 10.3847/1538-4357/abe53a

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation
- Question: Is the 878 um dust polarization in the HH 212 protostellar disk produced by dust self-scattering or by dichroic extinction by magnetically aligned grains?  
  > "in order to further determine the contributions of dichroic extinction and dust self-scattering" (Introduction)
- Target **HH 212 disk**: coordinates _not stated_; z/distance ~400 pc  
  > "in the Class 0 phase in Orion at a distance of $\sim$ 400 pc" (Introduction); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00044.S
- bands: Band 7 (878 um), Cycle 5  
  > "were obtained with ALMA in Band 7 in Cycle 5 (Project ID: 2017.1.00044.S)" (Observations)
- frequencies and spectral setup: 4 spectral windows centered at 334.7, 336.5, 346.6, 348.4 GHz  
  > "The correlator was set up to have 4 spectral windows (centered at 334.7, 336.5, 346.6, and 348.4 GHz, respectively)" (Observations)
- continuum bandwidth: ~8 GHz total, centered at ~341.5 GHz (878 um)  
  > "with a total bandwidth of $\sim$ 8 GHz centered at $\sim$ 341.5 GHz (or 878 $\mu$m correspondingly)" (Observations)
- arrays: 47 antennas, single pointing, primary beam ~17 arcsec  
  > "A single pointing was used to map the disk with a primary beam of $\sim$ $17''$. 47 antennas were used in the observations" (Observations)
- configurations: _not stated_
- baselines: projected baselines ~60-8500 m  
  > "47 antennas were used in the observations, with projected baselines of $\sim$ 60$-$8500 m" (Observations)
- angular resolution: ~0.035 arcsec (14 au) in continuum  
  > "obtained with ALMA at $\sim$ $0^{\prime\prime}_{^\textrm{.}}035$ (14 au) resolution in continuum" (abstract)
- max recoverable scale: ~0.4 arcsec  
  > "The maximum recoverable size scale was $\sim$ $0^{\prime\prime}_{^\textrm{.}}4$, enough to map the disk without any significant missing flux." (Observations)
- sensitivity: Stokes I rms ~25 uJy/beam (0.233 K); Stokes Q and U rms ~19 uJy/beam (0.177 K)  
  > "In Stokes *I* map, the noise level is $\sigma \sim$ 25 $\mu$Jy beam$^{-1}$ (or 0.233 K)." (Observations); "In Stokes *Q* and *U* maps, the noise level is $\sigma_p \sim$ 19 $\mu$Jy beam$^{-1}$ (or 0.177 K)." (Observations)
- time on source: ~98 minutes on target in three observations  
  > "Three observations were taken on 2017 November 27, with a total time of $\sim$ 98 minutes on the target." (Observations)
- observing dates: 2017 November 27  
  > "Three observations were taken on 2017 November 27" (Observations)
- pi or archival as stated: _not stated_
- External data: Toomre Q values of 1-2.5 for the disk, from 0.87 and 9 mm continuum  
  > "has found that the disk has Toomre Q values of 1$-$2.5" (A Flared Dusty Disk Model) [from Tobin2020 (cite: Tobin2020)]
- External data: Absorption opacity kappa_abs ~1.9 Q cm^2 per gram of dust at ~852 um from multi-wavelength modeling; adopted with Q~1 as 1.9 cm^2/g at 878 um  
  > "Thus here in our model, adopting $Q \sim 1$, we assume $\kappa_\textrm{\scriptsize abs} \sim 1.9$ cm$^2$ per gram of dust at the observed wavelength of 878 $\mu$m." (A Flared Dusty Disk Model) [from Lin2021 (cite: Lin2021)]
- External data: Inclination of ~87 deg for the nearly edge-on disk  
  > "The disk is assumed to be nearly edge-on with an inclination of $\sim$ 87$^\circ$" (A Flared Dusty Disk Model) [from Lee2021Dwind (cite: Lee2021Dwind)]
- External data: Albedo as a function of maximum grain size (10, 25, 50, 75, 100 um gives ~0, 0.036, 0.23, 0.50, 0.70 at 870 um)  
  > "estimated an albedo of $\sim$ 0, 0.036 0.23, 0.50, 0.70, respectively, at the observed wavelength of 870 $\mu$m" (Dust Self-Scattering by Submillimeter-Sized Grains) [from Kataoka2015 (cite: Kataoka2015)]
- External data: Optical constants of amorphous pyroxene (70 percent magnesium, 30 percent iron) used for the Mie scattering matrix  
  > "using the optical constants of an amorphous silicate (amorphous pyroxene with 70 percent magnesium and 30 percent iron)" (Dust Self-Scattering by Submillimeter-Sized Grains) [from Jaeger1994; Dorschner1995 (cite: Jaeger1994; Dorschner1995)]
- External data: Material density 1.675 g cm^-3 for the grains  
  > "a grain size of 100 $\mu$m, and material density of 1.675 g cm$^{-3}$" (Dust Self-Scattering by Submillimeter-Sized Grains) [from Birnstiel2018 (cite: Birnstiel2018)]
- External data: Protostellar mass ~0.25 Msun used in the viscous heating estimate  
  > "In HH 212, with $M \sim 0.25$ $M_\odot$" (Discussion) [from Codella2014; Lee2014; Lee2017COMs (cite: Codella2014; Lee2014; Lee2017COMs)]
- External data: Accretion rate ~5e-6 Msun/yr used in the viscous heating estimate  
  > "$\dot{M} \sim 5\times10^{-6}$ $M_\odot$ yr$^{-1}$" (Discussion) [from Lee2014 (cite: Lee2014)]
- External data: Instrumental error on polarization fraction expected to be <~0.2% for a source much smaller than 1/3 of the primary beam  
  > "According to ALMA Technical Handbook in Cycle 5, the instrumental error on $P$ is expected to be $\lesssim$ 0.2% for the disk" (Observations) [from ALMA Technical Handbook, Cycle 5]
- Simulation/model as data: Parametrized flared dusty disk model, with dichroic extinction and dust self-scattering variants, compared with the observed polarization  
  > "Following up on that, we first introduce a simple parametrized disk model and then explore these two possible mechanisms in more details." (Polarization Models)

## Processing

### Calibration

- pipeline or manual: Manual calibration in CASA by the ALMA QA2 team; J5010+1800 passband and flux calibrator, J0541-0211 gain calibrator, J0522-3627 polarization calibrator  
  > "The Common Astronomy Software Applications (CASA) package was used to calibrate the $uv$ data manually by the ALMA QA2 team" (Observations); "and quasar J0541-0211 as a gain calibrator, and quasar J0522-3627 as a polarization calibrator" (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J5010+1800  
  > "with quasar J5010+1800 as a passband and flux calibrator" (Observations)
- flux scale uncertainty: _not stated_
- self calibration: Phase-only self-calibration using the Stokes I continuum map  
  > "We also performed a phase-only self-calibration using the continuum intensity (Stokes-I) map to improve the map fidelity." (Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: super-uniform weighting, robust = 0.5, npixels=0  
  > "We adopted a super-uniform weighting with a robust factor of 0.5 (with npixels=0) for the $uv$ data to generate the continuum map" (Observations)
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
- final beam: ~0.036 x 0.032 arcsec at ~341.5 GHz  
  > "with a synthesized beam (resolution) of $\sim$ $0^{\prime\prime}_{^\textrm{.}}036$$\times$$0^{\prime\prime}_{^\textrm{.}}032$" (Observations)
- final rms: Stokes I ~25 uJy/beam; Stokes Q and U ~19 uJy/beam  
  > "In Stokes *I* map, the noise level is $\sigma \sim$ 25 $\mu$Jy beam$^{-1}$ (or 0.233 K)." (Observations); "In Stokes *Q* and *U* maps, the noise level is $\sigma_p \sim$ 19 $\mu$Jy beam$^{-1}$ (or 0.177 K)." (Observations)

### Inherited from earlier work

- Radial power-law indices of the disk density and temperature (p=2, q=0.75)  
  > "As in (cite: Lee2017Disk), we assume that $p=2$ and $q=0.75$." (A Flared Dusty Disk Model) [from (cite: Lee2017Disk)]
- Radiative transfer code used for the thermal dust emission model  
  > "Radiative transfer assuming LTE is used to calculate the dust emission from the model, using our radiative transfer code in (cite: Lee2017Disk)." (A Flared Dusty Disk Model) [from (cite: Lee2017Disk)]
- Tapering of the disk total height beyond R_t to match the outer edge  
  > "as discussed in (cite: Lee2017Disk), since the continuum emission of the disk becomes geometrically thinner near the outer edge, the total height of the disk is revised to" (A Flared Dusty Disk Model) [from (cite: Lee2017Disk)]
- Polarized radiative transfer equations in Stokes I, Q, U  
  > "the radiative transfer in Stokes $I$, $Q$, and $U$ parameters can be given by the following (cite: Reissl2016)" (Dichroic Extinction by Magnetically Aligned Grains) [from (cite: Reissl2016)]
- Extinction and polarization cross sections per gram  
  > "The extinction cross section per gram (i.e., extinction opacity) and polarization cross section per gram (i.e., polarization opacity) can be given by (cite: Lee1985)" (Dichroic Extinction by Magnetically Aligned Grains) [from (cite: Lee1985)]

### Not stated but needed to reproduce (our reading)

- CASA version used for calibration and imaging
- Imaging task, deconvolver, clean mask, threshold, cell size and image size for the Stokes I, Q and U maps
- Self-calibration solution interval, number of iterations and reference image
- How polarization was calibrated and imaged (leakage and position-angle calibration details, Stokes cube construction)
- Whether the maps are primary-beam corrected and the flux scale uncertainty
- Source code and exact implementation of the authors' own radiative transfer code (only referenced to Lee et al. 2017)
- Grid, photon count and dust size distribution settings for the RADMC-3D scattering runs
- Fitting procedure for the disk parameters (matched by comparison, no sampler or goodness-of-fit stated)
- Disk geometry details of the rotation applied to the maps and the position-angle of the nearside tilt used in the model
- Whether archival or other ALMA project data were used beyond 2017.1.00044.S (none stated)

## Analysis recipe

1. **Image continuum Stokes I, Q, U**: Manual CASA calibration by the ALMA QA2 team, then continuum imaging at ~341.5 GHz with super-uniform weighting and phase-only self-calibration  
  > "We adopted a super-uniform weighting with a robust factor of 0.5 (with npixels=0) for the $uv$ data to generate the continuum map" (Observations); "We also performed a phase-only self-calibration using the continuum intensity (Stokes-I) map to improve the map fidelity." (Observations)
   - software: CASA
   - parameter: robust = 0.5, npixels=0, super-uniform weighting  
  > "We adopted a super-uniform weighting with a robust factor of 0.5 (with npixels=0)" (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive polarized intensity, fraction and orientation**: Bias-corrected polarized intensity from Q and U, fraction P = Pi/I, orientations from E vectors  
  > "Linear polarized intensity is defined as $P_i=\sqrt{Q^2+U^2-\sigma_p^2}$ and thus bias-corrected." (Observations); "Polarization orientations are defined by the $E$ vectors." (Observations)
   - software: CASA
   - parameter: sigma_p ~19 uJy/beam used for bias correction  
  > "In Stokes *Q* and *U* maps, the noise level is $\sigma_p \sim$ 19 $\mu$Jy beam$^{-1}$ (or 0.177 K)." (Observations)
   - fitting: _not stated_
   - validation: Instrumental error on P expected to be <~0.2% for a source much smaller than 1/3 of the primary beam  
  > "According to ALMA Technical Handbook in Cycle 5, the instrumental error on $P$ is expected to be $\lesssim$ 0.2% for the disk" (Observations)
3. **Model the thermal dust emission with a flared disk**: Parametrized flared disk in vertical hydrostatic equilibrium; LTE radiative transfer with the authors' code; parameters matched to the observed continuum structure  
  > "The disk is composed of dust and gas in vertical hydrostatic equilibrium with a scale height of $h_\mathrm{s}$." (A Flared Dusty Disk Model); "By matching the observed structure of the continuum emission assuming pure dust thermal emission" (A Flared Dusty Disk Model)
   - software: custom radiative transfer code of Lee et al. 2017
   - parameter: R_t ~34+-5 au, R_o ~68+-10 au, h_s ~12+-2 au  
  > "we find that $R_\mathrm{t}\sim$ 34$\pm5$ au" (A Flared Dusty Disk Model); "$R_\mathrm{o}\sim 68\pm10$ au" (A Flared Dusty Disk Model); "$h_\mathrm{s}\sim$ 12$\pm2$ au" (A Flared Dusty Disk Model)
   - parameter: rho_t ~3.0+-0.4e-15 g cm^-3, T_t ~65+-10 K  
  > "$\rho_\mathrm{t}\sim 3.0\pm0.4 \times 10^{-15}$ g cm$^{-3}$" (A Flared Dusty Disk Model); "$T_\mathrm{t}\sim 65\pm10$ K" (A Flared Dusty Disk Model)
   - assumption: Gas to dust mass ratio of 100, gas of molecular hydrogen and atomic helium  
  > "Assuming a gas to dust mass ratio of $100$ and a gas composed of molecular hydrogen and atomic helium" (A Flared Dusty Disk Model)
   - assumption: Absorption opacity 1.9 cm^2 per gram of dust at 878 um (Q~1)  
  > "adopting $Q \sim 1$, we assume $\kappa_\textrm{\scriptsize abs} \sim 1.9$ cm$^2$ per gram of dust at the observed wavelength of 878 $\mu$m." (A Flared Dusty Disk Model)
   - assumption: Inclination ~87 deg, nearside tilted slightly to the south  
  > "The disk is assumed to be nearly edge-on with an inclination of $\sim$ 87$^\circ$" (A Flared Dusty Disk Model)
   - assumption: LTE radiative transfer  
  > "Radiative transfer assuming LTE is used to calculate the dust emission from the model" (A Flared Dusty Disk Model)
   - fitting: Parameters matched to the observed continuum structure; no sampler, priors or likelihood stated  
  > "By matching the observed structure of the continuum emission assuming pure dust thermal emission" (A Flared Dusty Disk Model)
   - validation: Compared with parameters from the earlier disk model; mass compared with a literature estimate  
  > "This mass is also consistent with that found by (cite: Galvan2018)" (A Flared Dusty Disk Model)
4. **Model polarization by dichroic extinction of aligned grains**: Uniform vertical poloidal field aligning grains with long axis perpendicular to the field; polarized radiative transfer in Stokes I, Q, U, with polarization efficiency set to match the observed fraction; model convolved with the observed beam  
  > "In this scenario, we assume that the disk is threaded with uniform (vertical) poloidal magnetic fields and the dust grains are aligned by the magnetic fields" (Dichroic Extinction by Magnetically Aligned Grains); "shows the model results convolved to the observed beam to be compared with the observations." (Dichroic Extinction by Magnetically Aligned Grains)
   - software: custom radiative transfer code of Lee et al. 2017
   - parameter: polarization efficiency alpha ~0.075  
  > "we find that a value of $\alpha \sim 0.075$ is required in the model" (Dichroic Extinction by Magnetically Aligned Grains)
   - assumption: Constant polarization efficiency and thus constant grain alignment efficiency  
  > "Our dichroic extinction model assumes a constant polarization efficiency and thus grain alignment efficiency." (Discussion)
   - fitting: alpha set by matching the observed central polarization fraction of ~0.03  
  > "By matching the polarization fraction of $\sim$ 0.03 observed in the optically thick central region of the disk" (Dichroic Extinction by Magnetically Aligned Grains)
   - validation: Qualitative comparison of convolved model maps with observed polarized intensity, fraction and orientations  
  > "Both the polarized intensity and polarization degree of the beam convolved model peak at the center and decrease outward, also roughly similar to the observed trends." (Dichroic Extinction by Magnetically Aligned Grains)
5. **Model polarization by dust self-scattering**: Mie scattering matrix for 100 um amorphous silicate grains scaled to an albedo of 0.5; polarization maps from RADMC-3D; temperature raised to match brightness; albedo 0.25 also tried; model convolved with the observed beam  
  > "we adopt an albedo of 0.5, or equivalently assume a scattering opacity the same as the absorption opacity, to study the dust self-scattering effect." (Dust Self-Scattering by Submillimeter-Sized Grains); "Then we use the RADMC-3D[^1] code (cite: Dullemond2012) to produce the polarization maps." (Dust Self-Scattering by Submillimeter-Sized Grains)
   - software: RADMC-3D
   - parameter: albedo 0.5 (also 0.25 tried); T_t ~95+-14 K required  
  > "$T_\mathrm{t}\sim 95\pm14$ K, which is about 50% higher than that without dust scattering" (Dust Self-Scattering by Submillimeter-Sized Grains); "We have tried with a smaller albedo of 0.25." (Dust Self-Scattering by Submillimeter-Sized Grains)
   - assumption: 100 um amorphous pyroxene grains, material density 1.675 g cm^-3, scattering opacity scaled to equal absorption opacity  
  > "a grain size of 100 $\mu$m, and material density of 1.675 g cm$^{-3}$" (Dust Self-Scattering by Submillimeter-Sized Grains); "then scale it down to have a scattering opacity the same as that of the absorption opacity" (Dust Self-Scattering by Submillimeter-Sized Grains)
   - fitting: Temperature raised to roughly match the observed brightness temperature; no formal fit  
  > "is required to roughly match the observed brightness temperature" (Dust Self-Scattering by Submillimeter-Sized Grains)
   - validation: Qualitative comparison of convolved model with observed polarization morphology and intensity profiles  
  > "In addition, unlike those seen in the observations, the polarized intensity and polarization degree in the model increase toward the edges along the major axis and drop rapidly at the edges." (Dust Self-Scattering by Submillimeter-Sized Grains)
6. **Check midplane temperature against viscous heating**: Estimate of midplane temperature from viscous heating with accretion rate, protostellar mass, Rosseland opacity and dust surface density  
  > "We can estimate whether the midplane temperature inferred from our modeling can be produced by viscous heating due to disk accretion." (Discussion)
   - parameter: M ~0.25 Msun, Mdot ~5e-6 Msun/yr, Sigma ~1.14 g cm^-2 at R_t  
  > "$\dot{M} \sim 5\times10^{-6}$ $M_\odot$ yr$^{-1}$" (Discussion); "In our model, the dust surface density $\Sigma \sim 1.14$ g cm$^{-2}$ at $R_\mathrm{t}$." (Discussion)
   - assumption: Maximum grain size of 100 um to bound the Rosseland mean opacity (kappa_R < 200 cm^2/g) read from a literature figure  
  > "Then, assuming a maximum grain size of 100 $\mu$m and judging from Figure 1 in (cite: Kataoka2015) that shows the dust opacity versus wavelength" (Discussion)
   - fitting: _not stated_
   - validation: Compared the viscous-heating limit with the model midplane temperatures of 65 K and 95 K  
  > "Thus, the midplane temperature in the disk should be less than 65 K at $R_\mathrm{t}$." (Discussion)

## Software

- **CASA** : Manual calibration of the uv data (by the ALMA QA2 team) and continuum imaging  
  > "The Common Astronomy Software Applications (CASA) package was used to calibrate the $uv$ data manually by the ALMA QA2 team" (Observations)
- **RADMC-3D** : Polarization maps of the dust self-scattering model  
  > "Then we use the RADMC-3D[^1] code (cite: Dullemond2012) to produce the polarization maps." (Dust Self-Scattering by Submillimeter-Sized Grains)
- **Custom radiative transfer code (Lee et al. 2017)** : LTE thermal and dichroic extinction polarization radiative transfer for the flared disk model  
  > "using our radiative transfer code in (cite: Lee2017Disk)" (A Flared Dusty Disk Model); "Our radiative transfer code can be expanded to calculate the polarization maps." (Dichroic Extinction by Magnetically Aligned Grains)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Stokes I noise level | 25 | not stated | uJy/beam | 1 | In Stokes *I* map, the noise level is $\sigma \sim$ 25 $\mu$Jy beam$^{-1}$ (or 0.233 K). |
| Stokes Q and U noise level | 19 | not stated | uJy/beam | 1 | In Stokes *Q* and *U* maps, the noise level is $\sigma_p \sim$ 19 $\mu$Jy beam$^{-1}$ (or 0.177 K). |
| Synthesized beam | 0.036 x 0.032 | not stated | arcsec | 1 | with a synthesized beam (resolution) of $\sim$ $0^{\prime\prime}_{^\textrm{.}}036$$\times$$0^{\prime\prime}_{^\textrm{.}}032$ |
| Peak polarization degree near the center | ~3-4 | not stated | percent | 2 | The polarization degree peaks at $\sim$ 3-4% near the center at the two polarized intensity peaks |
| Polarization degree at disk edges and surfaces | ~1.5 | not stated | percent | 2 | decreases outwards along the major and minor axes to $\sim$ 1.5% at the edges and surfaces of the disk |
| Distance of the two polarized intensity peaks from the central source | ~0.02 (8 au) | not stated | arcsec | 2 | the polarized intensity shows two peaks in the midplane near the central source on either side at a distance of $\sim$ 0.02 (8 au) |
| Disk radius R_t (model) | 34 | +-5 | au | 3 | we find that $R_\mathrm{t}\sim$ 34$\pm5$ au |
| Disk outer radius R_o (model) | 68 | +-10 | au | 3 | $R_\mathrm{o}\sim 68\pm10$ au |
| Scale height h_s at R_t | 12 | +-2 | au | 3 | $h_\mathrm{s}\sim$ 12$\pm2$ au |
| Midplane dust mass density at R_t | 3.0e-15 | +-0.4e-15 | g cm^-3 | 3 | $\rho_\mathrm{t}\sim 3.0\pm0.4 \times 10^{-15}$ g cm$^{-3}$ |
| Molecular hydrogen number density at R_t | 6.5e10 | +-1.0e10 | cm^-3 | 3 | $n_\mathrm{t}\sim 6.5\pm1.0\times10^{10}$ cm$^{-3}$ |
| Midplane temperature at R_t (no scattering) | 65 | +-10 | K | 3 | $T_\mathrm{t}\sim 65\pm10$ K |
| Total (gas plus dust) disk mass | 0.14 | +-0.02 | Msun | 3 | Thus, the disk has a total (gas plus dust) mass of $\sim 0.14\pm0.02$ $M_\odot$ |
| Polarization efficiency alpha | 0.075 | not stated | dimensionless | 4 | we find that a value of $\alpha \sim 0.075$ is required in the model |
| Midplane temperature at R_t with dust self-scattering (albedo 0.5) | 95 | +-14 | K | 5 | $T_\mathrm{t}\sim 95\pm14$ K, which is about 50% higher than that without dust scattering |
| Maximum midplane temperature at R_t from viscous heating | <65 | not stated | K | 6 | Thus, the midplane temperature in the disk should be less than 65 K at $R_\mathrm{t}$. |
| Maximum grain size allowing scattering opacity comparable to or below absorption opacity | 50-75 | not stated | um | 5 | the grains can have a maximum size of 50$-$75 $\mu$m |

## Qualitative findings

- Polarized emission forms V-shaped structures opening to the east and probably west, with arm structures further out that may be spiral arms  
  > "The polarized emission forms V-shaped structures opening to the east and probably west arising from the disk surfaces" (abstract)
- Polarization orientations are mainly parallel to the disk minor axis, with a slight concave tilt in the west  
  > "The polarization orientations are mainly parallel to the minor axis of the disk" (abstract)
- The dichroic extinction model predicts a polarization gap and a flip of orientation in the outer disk that are not detected  
  > "However, such an increase in polarized intensity and a flip of polarization orientation in the outer disk are not detected here." (Dichroic Extinction by Magnetically Aligned Grains)

## Claim tuples

- H: Is the HH 212 disk dust polarization produced by dichroic extinction or by dust self-scattering? | E: Compared simple dichroic extinction and dust self-scattering models, convolved to the observed beam, with the polarization morphology, intensity and degree | R: Neither model alone reproduces all observed features | F: Neither mechanism alone fully accounts for the observations | **supported**
- H: Does the tilt of polarization orientations point to dust self-scattering? | E: Self-scattering model with albedo 0.5 compared with observed orientations | R: The self-scattering model produces the concave tilt of orientations seen in the west | F: The tilt is expected from self-scattering, e.g. by 50-75 um grains | **supported**
- H: Does dichroic extinction by poloidal-field-aligned grains explain the radial decrease of polarized intensity and degree? | E: Dichroic extinction model with polarization efficiency alpha ~0.075 compared with observations | R: The model reproduces the decrease of polarized intensity and fraction toward the edges but not the central dip | F: The decreases are expected from dichroic extinction by grains aligned by poloidal fields | **partially**
- H: Are both mechanisms needed to explain the polarization? | E: Qualitative combination of the two model comparisons | R: Each model reproduces different observed features | F: Both grain growth and poloidal fields may be present in the disk; combined modeling deferred | **partially**

## Reasoning

- Why this data: Higher resolution polarization data (3 times higher than previous) are needed to separate dichroic extinction from dust self-scattering  
  > "at 3 times higher resolution than previous observations, in order to further determine the contributions of dichroic extinction and dust self-scattering" (Introduction)
- Why this method: A flared disk model of the kind already used for this disk's thermal dust emission is adopted as the base for polarization models  
  > "Similar flared disk models have been used to produce the thermal dust emission in this disk" (A Flared Dusty Disk Model)
- Alternative: A smaller albedo of 0.25 was tried in the self-scattering model but polarized intensity still peaked at the edges and fell below 3 sigma  
  > "We have tried with a smaller albedo of 0.25." (Dust Self-Scattering by Submillimeter-Sized Grains)
- How they decided it was enough: _not stated_
- Limitation (authors): RADMC-3D cannot treat scattering by aligned non-spherical grains, so the combined model is deferred  
  > "Since RADMC-3D cannot treat scattering by aligned (non-spherical) grains at the present time, we will defer the combined modeling to a future publication." (Discussion)
- Limitation (authors): Dust absorption opacity is a major model uncertainty  
  > "A major uncertainty in the model is the dust absorption opacity." (A Flared Dusty Disk Model)
- Limitation (authors): Existence of the predicted polarization gap needs deeper observations  
  > "but deeper observations are needed to check them" (Dichroic Extinction by Magnetically Aligned Grains)
- Caveat (inferred, ours): Model-to-data comparison is qualitative; no goodness-of-fit or parameter uncertainty from a formal fit for the polarization models
- Caveat (inferred, ours): Single albedo and single grain-size population assumed across the disk
- Caveat (inferred, ours): Disk thermal parameters depend on the adopted absorption opacity and on Q~1
- Caveat (inferred, ours): Polarization calibration and instrumental polarization handling are not described beyond the Technical Handbook error

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: RADMC-3D is publicly available; release of the authors' own radiative transfer code is not stated  
  > "RADMC-3D is a publicly available code for radiative calculations" (Footnotes)
- Missing: CASA version and exact tclean or equivalent parameters for Stokes I, Q, U imaging
- Missing: Self-calibration details
- Missing: The authors' own radiative transfer code and the exact grid and numerical settings
- Missing: The polarization calibration recipe
- Data volume (inferred): Tens of GB of raw visibilities for three Band 7 execution blocks (~98 min on target)
- Score (inferred): 3/5, Observation and basic data reduction choices are given, but imaging parameters, CASA version and the model code are missing; main results are model-based and compared qualitatively (scale 1-5).
- Rediscovery candidate: no, The paper does not state that the data are public, imaging parameters are incomplete and the key models use an unreleased in-house radiative transfer code.

## Links

- Method: Lee, C.-F., Li, Z.-Y., Ho, P. T. P., et al. 2017a, Science Advances, 3, e1602935 (cite: Lee2017Disk) (Source of the flared disk model, radiative transfer code and fixed power-law indices)
- Method: Reissl, S., Wolf, S., & Brauer, R. 2016, A&A, 593, A87 (cite: Reissl2016) (Polarized radiative transfer equations in Stokes I, Q, U)
- Method: Kataoka, A., Muto, T., Momose, M., et al. 2015, ApJ, 809, 78 (cite: Kataoka2015) (Albedo as a function of maximum grain size)
- Companion: Lee, C.-F., Li, Z.-Y., Ching, T.-C., et al. 2018a, ApJ, 854, 56 (cite: Lee2018BDisk) (Earlier lower-resolution polarization detection in the same disk)
- Companion: Lin, Z.-Y. D., Lee, C.-F., Li, Z.-Y., et al. 2021, MNRAS, 501, 1316 (cite: Lin2021) (Multi-wavelength continuum modeling giving the adopted absorption opacity)
- Companion: Tobin, J. J., Sheehan, P. D., Megeath, S. T., et al. 2020, ApJ, 890, 130 (cite: Tobin2020) (Toomre Q and gravitational instability of the disk)
- Related: ALMA Cycle 5 project 2017.1.00044.S

## Checks

```json
{
 "quotes": 112,
 "quotes_ok": 112,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 17,
 "numeric_problems": 0,
 "fill": {
  "facts": 101,
  "stated": 74,
  "rate": 0.733
 },
 "evidence_ok": true
}
```
