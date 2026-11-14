# Planet migration, resonant locking, and accretion streams in PDS 70: comparing models and data

`2020MNRAS.499.2015T` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Toci, Claudia | arXiv: 2009.11893 | DOI: 10.1093/mnras/staa2933

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks, exoplanets
- Question: Can 3D SPH dust+gas simulations of PDS 70 with two migrating, accreting embedded planets reach a stable resonant configuration and reproduce the observed ALMA mm continuum, 12CO and SPHERE scattered-light features?  
  > "In this work we present new 3D smoothed particle hydrodynamics (SPH) simulations of the PDS 70 disc assuming two embedded giant planets." (Introduction); "We model both dust and gas, aiming to understand the physical origin of features observed in mm and scattered light images." (Introduction)
- Target **PDS 70**: coordinates _not stated_; z/distance 113.4 +/- 0.5 pc (113 pc adopted in the models)  
  > "located at a distance of 113.4 $\pm$ 0.5 pc (cite: Gaia2018)" (Introduction); "we fixed the values of the source distance $d=113$ pc (cite: Gaia2018)" (2.4 Radiative transfer); distance from Gaia (cite: Gaia2018)  
  > "located at a distance of 113.4 $\pm$ 0.5 pc (cite: Gaia2018)" (Introduction); "we fixed the values of the source distance $d=113$ pc (cite: Gaia2018)" (2.4 Radiative transfer)

## Data provenance

- ALMA projects: 2013.1.00592.S
- bands: _not stated_
- frequencies and spectral setup: 855 um continuum and 12CO J = 3-2 (observations from Keppler2019, used only for comparison)  
  > "We produced 855 $\mu$m continuum images" (2.4 Radiative transfer); "synthetic emission in $^{12}$CO J = 3 - 2 of our three models (last three panels) compared to the observations (left panel)" (CO maps and mass accretion rate)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 74 x 57 mas beam at 855 um (observed beam used to convolve the models)  
  > "74 $\times$ 57 mas for the 855 $\mu$m image from (cite: Keppler2019" (2.4 Radiative transfer)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMA data ADS/JAO.ALMA 2013.1.00592.S acknowledged; comparison images are taken from published work (Keppler2019, Isella2019)  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA 2013.1.00592.S." (Acknowledgements)
- Line: 12CO J = 3-2 (not stated)
- Other facility **VLT/SPHERE (IRDIS)**: 2018-02-24 IRDIS dataset (Muller2018) re-reduced by the authors for scattered-light comparison  
  > "we have both reduced the 2018-02-24 SPHERE/IRDIS dataset presented in (cite: Muller2018)" (2.5 Post-processing of IR synthetic images)
- Other facility **Gaia**: Distance to PDS 70  
  > "located at a distance of 113.4 $\pm$ 0.5 pc (cite: Gaia2018)" (Introduction)
- External data: Distance to PDS 70 (113 pc)  
  > "we fixed the values of the source distance $d=113$ pc (cite: Gaia2018)" (2.4 Radiative transfer) [from (cite: Gaia2018)]
- External data: ALMA 855 um continuum image and beam (74 x 57 mas) used for comparison  
  > "74 $\times$ 57 mas for the 855 $\mu$m image from (cite: Keppler2019" (2.4 Radiative transfer) [from (cite: Keppler2019)]
- External data: 12CO moment 0 observations used for comparison  
  > "In order to test whether our models are compatible with CO observations of (cite: Keppler2019) we also produced synthetic CO moment zero maps." (CO maps and mass accretion rate) [from (cite: Keppler2019)]
- External data: Planet-to-star contrasts used to inject planet flux in the IR images  
  > "using the contrast with respect to the star measured in (cite: Muller2018; Mesa2019)" (2.5 Post-processing of IR synthetic images) [from (cite: Muller2018; Mesa2019)]
- External data: Stellar Teff = 4090 K and R = 1.57 Rsun from stellar evolution models for 0.8 Msun at 5 Myr  
  > "as derived from stellar evolution models for a 0.8 M$_\odot$ at 5Myr (cite: Siess2000)" (2.4 Radiative transfer) [from (cite: Siess2000)]
- External data: DIANA standard dust composition  
  > "as the DIANA standard dust composition (cite: Woitke2016)" (2.4 Radiative transfer) [from (cite: Woitke2016)]
- External data: Disc inclination 180-49 deg  
  > "disc inclination $i=180 - 49^{\circ}$ ( following (cite: Muller2018)" (2.4 Radiative transfer) [from (cite: Muller2018)]
- Simulation/model as data: Three 3D dust+gas SPH simulations (Sim 1-3) with PHANTOM, 10^6 SPH particles, two migrating and accreting sink-particle planets, evolved at least 500 outer-planet orbits (~0.18 Myr)  
  > "We perform a set of three dust and gas hydrodynamics simulations in 3D using PHANTOM, a smoothed particle hydrodynamics (SPH) code (cite: Price2018)." (2 Methods); "All of our calculations have been evolved for at least 500 outer planet orbits, about $\sim$ 0.18 Myr." (2.1 Simulation set)
- Simulation/model as data: MCFOST radiative transfer post-processing of the t = 500 Torb snapshots: 855 um continuum, 2.11 and 2.25 um scattered light, 12CO moment 0  
  > "We produced 855 $\mu$m continuum images and both 2.11$\mu$m and 2.25 $\mu$m scattered light images of the t = 500 T$_{\rm orb}$ ($\sim$ 0.18 Myr) snapshot for all three simulations." (2.4 Radiative transfer)

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
- final beam: Gaussian beam 74 x 57 mas applied to synthetic 855 um images  
  > "we convolved the sub-mm images with a Gaussian beam to match the beam size of the observations" (2.4 Radiative transfer)
- final rms: _not stated_

### Inherited from earlier work

- Initial gas surface density profile  
  > "We set up an initial surface density profile for the disc as in (cite: LodatoPrice2010)" (2.2 Gas and dust) [from (cite: LodatoPrice2010)]
- alpha_SPH viscosity set to give alpha_SS = 0.005  
  > "In all our simulations we set the value of $\alpha_{\rm SPH}$ viscosity as in (cite: LodatoPrice2010)" (2.2 Gas and dust) [from (cite: LodatoPrice2010)]
- Surface density slope p = 1  
  > "we choose $p=1$, consistent with (cite: Bae2019)" (2.2 Gas and dust) [from (cite: Bae2019)]
- Sound speed index q = 0.5  
  > "where $q=0.5$ (again, following (cite: Bae2019))" (2.2 Gas and dust) [from (cite: Bae2019)]
- Initial planet masses chosen so the outer planet can migrate inward  
  > "This choice is motivated by our previous study on discs with two embedded giant planets (cite: Toci2020)" (2.3 Properties of the embedded planets) [from (cite: Toci2020)]
- CO line modelling assumptions (LTE, constant abundance, photo-dissociation)  
  > "following (cite: Pinte2018) and (cite: Pinte2019), we assumed local thermal equilibrium (LTE)" (2.4 Radiative transfer) [from (cite: Pinte2018) and (cite: Pinte2019)]
- Median-ADI processing of the IRDIS cube  
  > "We then processed the calibrated IRDIS cube using the median-ADI algorithm (cite: Marois2006) as in (cite: Muller2018)." (2.5 Post-processing of IR synthetic images) [from (cite: Muller2018)]
- Details of IR post-processing steps (ii) to (vi)  
  > "More details on steps (ii) to (vi) can be found in (cite: Calcino2020)" (2.5 Post-processing of IR synthetic images) [from (cite: Calcino2020)]

### Not stated but needed to reproduce (our reading)

- PHANTOM version, input parameter files, SPH smoothing/viscosity settings and random seeds
- Planet accretion (sink) details for the star beyond its 2 au sink radius, and softening choices
- MCFOST version, grid/Voronoi cell settings and the composition fraction of the remaining 25 percent of grain volume
- The planet contrast values actually used for flux injection in the IR images
- Position angle and orientation of the 74 x 57 mas beam, and how the ALMA continuum and CO images were obtained and flux-compared (no CASA or archive reduction is described)
- CO moment 0 velocity range, channel width and the observed flux values used for the comparison
- Number of PCA components for the final sPCA images and the noise level injected
- Snapshot data and processing scripts are not provided

## Analysis recipe

1. **Run 3D dust+gas SPH simulations of two embedded migrating planets**: PHANTOM SPH with one-fluid dust, 1 mm grains, planets and star as sink particles that accrete and migrate, three runs with different initial planet masses and positions  
  > "We perform a set of three dust and gas hydrodynamics simulations in 3D using PHANTOM, a smoothed particle hydrodynamics (SPH) code (cite: Price2018)." (2 Methods); "The planets and the central star are included in the code as sink particles, characterized by an initial mass, position and sink radius." (2.3 Properties of the embedded planets)
   - software: PHANTOM
   - parameter: 10^6 SPH particles; M_star = 0.8 Msun; R_out = 120 au; R_in = 5 au (Sim 1) or 2 au (Sim 2, 3); R_0 = 100 au; Sigma_0 = 1.07 g cm^-2; H/R = 0.05 at R_0; alpha_SS = 0.005; dust 1 mm, dust-to-gas 0.01  
  > "representing the disc with $10^6$ SPH particles" (2.2 Gas and dust); "The outer radius is fixed in all the simulations, $R_{\rm out}=120$ au." (2.2 Gas and dust); "in order to have a value for the effective (cite: SS1973) viscosity of $\alpha_{\rm SS}=0.005$" (2.2 Gas and dust)
   - parameter: Initial planet masses and positions, and sink radii as fractions of the Hill radius, listed per simulation in Table 1  
  > "Initial conditions for the three simulations, called sim 1, sim 2, sim 3." (Table 1)
   - assumption: Locally isothermal equation of state  
  > "We assume a locally isothermal equation of state with a sound speed profile" (2.2 Gas and dust)
   - assumption: Dust initially coupled to gas (Stokes number below unity), justifying the one-fluid mode  
  > "This implies that dust and the gas are initially coupled in the disc." (2.2 Gas and dust)
   - fitting: _not stated_
   - validation: Dependence of results on the sink radius was checked by varying it between simulations  
  > "The value of the sink radius may affect the planetary accretion rate and thus their final mass, so we decided to check the dependence of our results on this parameter." (2.3 Properties of the embedded planets)
2. **Radiative transfer of the snapshots into synthetic continuum and scattered-light images**: MCFOST Monte Carlo radiative transfer on the SPH snapshot at t = 500 Torb, ray-traced images at 855 um, 2.11 and 2.25 um, then convolution with the observed ALMA beam  
  > "we post-processed our simulation using the Monte Carlo radiative transfer code MCFOST (cite: Pinte2006; Pinte2009)." (2.4 Radiative transfer); "We then compute the source function by ray-tracing to produce the output images at the desired wavelengths." (2.4 Radiative transfer)
   - software: MCFOST
   - parameter: 1.3e8 photon packets; d = 113 pc; i = 180-49 deg; PA = 159 deg  
  > "We use $1.3\times 10^8$ photon packets in the Monte Carlo simulation to compute the temperature and specific intensities of our models." (2.4 Radiative transfer); "position angle PA=$159^{\circ}$" (2.4 Radiative transfer)
   - parameter: Grain size distribution dn/da ~ a^-3.5, a_min = 0.03 um, a_max = 2500 um; porosity 10 percent; Mie theory  
  > "We assume a power-law grain size dust distribution $dn/da \propto a^{-3.5}$ (integrating over the whole disc)" (2.4 Radiative transfer); "and a porosity of 10$\%$" (2.4 Radiative transfer)
   - parameter: Stellar blackbody Teff = 4090 K, R = 1.57 Rsun  
  > "effective temperature T$_{\rm e}$ = 4090 K and a radius of R$_\star$= 1.57 Solar radii" (2.4 Radiative transfer)
   - assumption: Grains smaller than 1 um follow the gas; grains larger than 1 mm follow the 1 mm grains; gas-to-dust ratio of the SPH simulation is 100  
  > "the total dust mass is derived from the gas to ratio of the SPH simulation, which is 100" (2.4 Radiative transfer); "Grains larger than 1 mm are assumed to follow the distribution of the 1 mm grains." (2.4 Radiative transfer)
   - fitting: _not stated_
   - validation: _not stated_
3. **Synthesise 12CO J=3-2 moment 0 maps**: MCFOST line radiative transfer in LTE with T_gas = T_dust and CO photo-dissociation where log(chi/n) > -6, compared with Keppler2019 observations  
  > "we assumed local thermal equilibrium (LTE), $T_{\rm gas} = T_{\rm dust}$ and a constant $^{12}$CO abundance of $10^{-4}$." (2.4 Radiative transfer); "the condition for the photo-dissociation of the CO is $\log(\chi/n) > -6$" (2.4 Radiative transfer)
   - software: MCFOST
   - parameter: Constant 12CO abundance 1e-4; local unresolved turbulent velocity 50 m/s  
  > "We added a local spatially unresolved turbulent velocity of 50 m s$^{-1}$" (2.4 Radiative transfer)
   - assumption: LTE, T_gas = T_dust  
  > "we assumed local thermal equilibrium (LTE), $T_{\rm gas} = T_{\rm dust}$" (2.4 Radiative transfer)
   - fitting: _not stated_
   - validation: Compared by eye and by azimuthally averaged flux profile with the Keppler2019 observations  
  > "Figure [5](#fig:fig_azim) presents the azimuthally averaged CO deprojected flux density of our models." (CO maps and mass accretion rate)
4. **Mimic high-contrast IR observing biases and reduce the SPHERE data**: Reduce 2018-02-24 IRDIS data with a custom python pipeline plus VIP median-ADI; apply to the synthetic 2.11 and 2.25 um images a nine-step chain (planet injection, PSF convolution, coronagraph transmission, resampling to 12.25 mas/pixel, shot noise, synthetic ADI cube, field-rotation smearing, median-ADI, averaging of K1 and K2)  
  > "We calibrated the IRDIS data with a custom-made python pipeline which performs dark subtraction, flat-fielding, bad pixel correction, sky subtraction, star centering based on satellite spots" (2.5 Post-processing of IR synthetic images); "Resampling of the RT images to the same pixel scale as the observations (12.25mas/pixel) using a fourth-order Lanczos interpolation;" (2.5 Post-processing of IR synthetic images)
   - software: VIP (Vortex Image Processing), custom python pipeline
   - parameter: Observed PSF FWHM about 63 mas (K1) and 66 mas (K2); 96 s exposures smeared by field rotation  
  > "which has a FWHM of $\sim$63mas and $\sim$66mas in K1 and K2, respectively;" (2.5 Post-processing of IR synthetic images)
   - fitting: _not stated_
   - validation: Features checked against a snapshot with planet c at +180 deg true anomaly, with and without ADI  
  > "we also processed a snapshot of the simulation corresponding to planet c located at the opposite point of its orbit (+180 degrees true anomaly) compared to the observations." (3.1 Synthetic Images)
5. **Compare dynamics, images and accretion rates with observations**: Track planet masses, positions, period ratio and accretion rates versus time, and compare synthetic 855 um, CO and scattered-light images with published ALMA and SPHERE data  
  > "to check whether or not they settle into a mean motion resonance, as a function of the normalized time." (3.2 Overall dynamics)
   - assumption: Accretion rate is the mass entering the sink radius, so computed planet accretion rates are upper limits  
  > "so that our computed accretion rates may be considered as upper limits." (3.3 CO maps and mass accretion rate)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PHANTOM** : 3D SPH dust and gas simulations with sink-particle planets  
  > "We perform a set of three dust and gas hydrodynamics simulations in 3D using PHANTOM, a smoothed particle hydrodynamics (SPH) code (cite: Price2018)." (2 Methods)
- **MCFOST** : Monte Carlo radiative transfer, synthetic continuum, scattered-light and CO images  
  > "we post-processed our simulation using the Monte Carlo radiative transfer code MCFOST (cite: Pinte2006; Pinte2009)." (2.4 Radiative transfer)
- **VIP (Vortex Image Processing)** : Routines for IRDIS calibration and ADI/sPCA processing  
  > "The pipeline uses routines of the Vortex Image Processing package (cite: GomezGonzalez2017), an open-source compilation of python routines used in high-contrast imaging." (2.5 Post-processing of IR synthetic images)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Planet b and c masses at t = 500 Torb, Sim 3 | Mb = 5.3, Mc = 3.9 | not stated | M_J | 1 | Masses and positions of the two planets, gas and dust disc masses for our set of simulations at t=500 T$_{\rm orb}$. |
| Planet b and c orbital radii at t = 500 Torb, Sim 3 | Rb = 19.1, Rc = 36.1 | not stated | au | 1 | Masses and positions of the two planets, gas and dust disc masses for our set of simulations at t=500 T$_{\rm orb}$. |
| Planet b mass reached after about 100 Torb | 4.5 - 5 | not stated | M_J | 5 | reaching the value of 4.5 - 5 M$_{\rm J}$, depending on the initial conditions |
| Planet c mass at end of simulation | ~5 | not stated | M_J | 5 | reaching $\sim$ 5 M$_{\rm J}$ mass at the end of the simulation |
| Planet locations matching 2:1 resonance and ALMA 855 um flux | Planet b ~17-22 au, Planet c ~34-39 au | not stated | au | 5 | Planet b should be located at $\sim$17–22 au and Planet c at $\sim$34–39 au. |
| Orbital eccentricity of planets | < ~0.1 (Planet c), ~0.15 (Planet b) | not stated | dimensionless | 5 | the orbital eccentricity of the planets remains relatively small, less than about 0.1 for Planet c (with an exact value dependent on the planet mass) and $\sim$ 0.15 for Planet b |
| Dust ring location | ~65-90 au (Sim 1); ~50-75 au (Sim 2, 3) | not stated | au | 2 | the position of the dust ring (that appears at $\sim$ 65–90 au for Sim 1 and at $\sim$ 50–75 au in the other cases) |
| Gas cavity width in CO model | ~40 | not stated | au | 3 | The two planets open a $\sim 40$ au wide cavity |
| Peak of azimuthally averaged CO emission, models vs observation | models ~0.3, observed ~0.4 | not stated | arcsec | 3 | the observed CO images peaks at about 0.4 arcsec while the models show the peak at about 0.3 arcsec |
| Stellar mass accretion rate in simulations | ~5e-10 | not stated | Msun/yr | 5 | the accretion rate on the star is $\sim 5 \times 10^{-10}$ M$_\odot$ yr$^{-1}$, an order of magnitude higher than the observed value. |
| Planet c and Planet b accretion rates | c ~1e-8; b <= 1e-10 | not stated | Msun/yr | 5 | the outer Planet c has a higher accretion rate ($\sim 10^{-8}$ M$_\odot$ yr$^{-1}$) with respect to the inner Planet b, ($\leq 10^{-10}$ M$_\odot$ yr$^{-1}$) |

## Qualitative findings

- An accretion stream connects planet c with the gas rim of the disc  
  > "an accretion stream connects Planet c with the gas rim of the disc, highlighting that the planet is actively interacting with the disc" (3 Results)
- Circumplanetary discs form around all planets but are accreted onto the sinks within about 50-100 Torb  
  > "a circumplanetary disc is created around all the planets and quickly (in about 50-100 T$_{\rm orb}$) accreted." (3 Results)
- The mm dust spur near planet c is reproduced and is not a numerical artefact  
  > "confirming that this is not a numerical feature but is due to the presence of dust surrounding Planet c" (3.1 Synthetic Images)

## Claim tuples

- H: Planets that start lighter and farther out, free to migrate and accrete, can reach the observed mass, position and resonance of PDS 70 b and c | E: Three 3D SPH runs with different initial planet masses and positions | R: Planets lock into resonance; Sim 3 gives Planet b at ~18-20 au and Planet c at ~35-40 au | F: Planet migration and resonant locking produce a configuration compatible with observations | **supported**
- H: Observed mm and scattered-light features are explained by the accretion stream onto planet c without a circumplanetary disc | E: MCFOST synthetic 855 um and ADI-processed 2.11/2.25 um images compared with ALMA and SPHERE data, plus a +180 deg control snapshot | R: The mm spur and most intra-cavity IR features are reproduced; the dusty feature near planet b is absent | F: Planet-disc interactions alone explain most features, though the spur origin (CPD vs wake) stays unclear | **partially**
- H: The simulated 12CO emission matches the observed cavity and flux | E: Synthetic 12CO J=3-2 moment 0 maps and azimuthal profiles versus Keppler2019 | R: Flux compatible, but the compact inner ring is not reproduced and the ring peak lies at 0.3 arcsec instead of 0.4 | F: Models have too much gas in the cavity | **partially**
- H: Simulated planetary accretion rates match the observed values | E: Sink accretion rates versus time for each simulation | R: Planet b rate consistent with observed; planet c rate strongly overestimated; outer planet accretes faster than the inner one | F: Absolute accretion rates cannot be constrained, only the relative ordering | **partially**
- H: Whether a dust ring forms between the two planets | E: Tracking dust between the orbits in the three runs | R: An inter-planetary ring forms in the first ~100 orbits but is accreted within ~100-150 orbits later | F: No long-lived dust ring between the planets, consistent with the observations | **supported**

## Reasoning

- Why this data: PDS 70 has two directly imaged embedded giant planets, making it a laboratory for planet-disc interaction  
  > "The disc surrounding PDS 70, with two directly imaged embedded giant planets, is an ideal laboratory to study planet-disc interaction." (abstract)
- Why this method: SPH suits accretion flows and asymmetric planet-disc interactions because it has no preferred geometry  
  > "is particularly suitable for the study of accretion flows and asymmetric interactions between planets and the disc, because there is no preferred geometry" (2 Methods)
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample; a wider parameter study is needed to test robustness  
  > "However, a more detailed study of the parameter space is needed to understand the robustness of the model" (Discussion)
- Limitation (authors): Radiative feedback from the planets is neglected  
  > "We also neglect any radiative feedback from the planets." (3.3 CO maps and mass accretion rate)
- Limitation (authors): Star sink radius (2 au) far larger than the real stellar radius may inflate the stellar accretion rate  
  > "The fact that our sink radius for the star (2 au) is far larger than the actual radius for the star can be the reason for this overestimate." (3.3 CO maps and mass accretion rate)
- Limitation (authors): Computed planet accretion rates are upper limits because unresolved circumplanetary discs are not modelled  
  > "so that our computed accretion rates may be considered as upper limits." (3.3 CO maps and mass accretion rate)
- Caveat (inferred, ours): Only three simulations with one disc setup, one grain size (1 mm) and a locally isothermal gas; resonance and ring positions may depend on these choices
- Caveat (inferred, ours): The ALMA data are only used as published images; no quantitative fit statistic between models and data is given
- Caveat (inferred, ours): Agreement is judged qualitatively by eye for the continuum and scattered-light features

## Reproducibility

- Data public (paper): Data underlying the article shared on reasonable request  
  > "The data underlying this article will be shared on reasonable request to the corresponding author." (Data availability)
- Products in archive: _not stated_
- Missing: Simulation input files and PHANTOM and MCFOST versions or settings
- Missing: How the ALMA images from the cited papers were obtained and compared
- Missing: Planet contrasts and noise level used in the IR post-processing
- Data volume (inferred): Small for the ALMA part (published images only); simulations need HPC (10^6 particles, hundreds of orbits)
- Score (inferred): 2/5, Initial conditions and RT parameters are well listed, but no code versions, input files or numerical comparison with ALMA data are given, and data are only on request.
- Rediscovery candidate: no, The ALMA data are not reduced in this paper, and the results are largely qualitative image comparisons from long hydrodynamic runs.

## Links

- Method: (cite: Price2018) (PHANTOM SPH code)
- Method: (cite: Pinte2006; Pinte2009) (MCFOST radiative transfer code)
- Method: (cite: Calcino2020) (Details of IR synthetic image post-processing steps)
- Method: (cite: GomezGonzalez2017) (VIP high-contrast imaging package)
- Method: (cite: LodatoPrice2010) (Initial surface density and viscosity setup)
- Companion: (cite: Keppler2019) (ALMA 855 um continuum and 12CO observations compared with)
- Companion: (cite: Isella2019) (ALMA sub-mm observations of the spur near planet c)
- Companion: (cite: Bae2019) (Previous 2D simulations of PDS 70)
- Companion: (cite: Muller2018) (SPHERE/IRDIS data and planet contrasts)
- Companion: (cite: Toci2020) (Earlier two-planet disc simulations motivating the setup)
- Related: ALMA 2013.1.00592.S

## Checks

```json
{
 "quotes": 96,
 "quotes_ok": 96,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 99,
  "stated": 59,
  "rate": 0.596
 },
 "evidence_ok": true
}
```
