# Evidence for auroral influence on Jupiter's nitrogen and oxygen chemistry revealed by ALMA

`2023NatAs...7.1048C` | Nature Astronomy 2023 | first author: Cavalié, T. | arXiv: 2407.07385 | DOI: 10.1038/s41550-023-02016-7

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: solar_system
- Question: How are CO and HCN, long-lived species deposited by comet Shoemaker-Levy 9, distributed in latitude and altitude in Jupiter's stratosphere in March 2017, and what does this imply for jovian chemistry and dynamics (notably in the auroral regions)?  
  > "the spatial distributions of CO and HCN, two of these long-lived species, had never been jointly observed at high latitudinal resolution." (abstract); "We used ALMA and Gemini/TEXES observations (21-23) to retrieve the spatial distribution of HCN and CO in Jupiter’s stratosphere to better understand their temporal evolution." (Observations)
- Target **Jupiter**: coordinates _not stated_; z/distance not stated (geocentric distance taken from JPL Horizons ephemeris; angular size 43.82 arcsec)  
  > "The planet was mapped with 42 antennas using 39-point mosaic (see Supplementary Figure 1), because of its 43.82” angular size." (Methods - Observations); "We take the ephemeris from JPL Horizons Solar System Dynamics ephemerides (https://ssd.jpl.nasa.gov/horizons/) to have the planet geometrical data at the time of the observations." (Methods - Radiative transfer); distance from JPL Horizons ephemerides  
  > "The planet was mapped with 42 antennas using 39-point mosaic (see Supplementary Figure 1), because of its 43.82” angular size." (Methods - Observations); "We take the ephemeris from JPL Horizons Solar System Dynamics ephemerides (https://ssd.jpl.nasa.gov/horizons/) to have the planet geometrical data at the time of the observations." (Methods - Radiative transfer)

## Data provenance

- ALMA projects: 2016.1.01235.S
- bands: _not stated_
- frequencies and spectral setup: HCN (4-3) at 354.505 GHz and CO (3-2) at 345.796 GHz; spectral resolutions 122 and 488 kHz  
  > "The spectral setup simultaneously covered the HCN (4-3) and CO (3-2) lines at 354.505 and 345.796 GHz, respectively, with spectral resolutions of 122 and 488 kHz, respectively." (Methods - Observations)
- continuum bandwidth: _not stated_
- arrays: 42 antennas, 39-point mosaic  
  > "The planet was mapped with 42 antennas using 39-point mosaic (see Supplementary Figure 1), because of its 43.82” angular size." (Methods - Observations)
- configurations: C-1 compact configuration  
  > "With the C-1 compact antenna configuration, the resulting elliptical synthetic beam was 1.2” (East-West) $\times$ 1” (North-South)" (Methods - Observations)
- baselines: _not stated_
- angular resolution: Synthetic beam 1.2 arcsec (East-West) x 1 arcsec (North-South); latitudinal resolution 2 deg at low latitudes, up to 8 deg at highest latitudes along the limb  
  > "With the C-1 compact antenna configuration, the resulting elliptical synthetic beam was 1.2” (East-West) $\times$ 1” (North-South)" (Methods - Observations); "with a latitudinal resolution of 2$^\circ$ at low latitudes and increasing to 8$^\circ$ at the highest latitudes along the limb." (Methods - Observations)
- max recoverable scale: ~8 arcsec  
  > "the Maximum recoverable Scale was $\sim$8”." (Methods - Observations)
- sensitivity: Noise at the level of 3-4%  
  > "The noise in the observations is at the level of 3-4%." (Methods - Observations)
- time on source: 24 minutes integration  
  > "The rather short integration time of 24 minutes limits the longitudinal smearing to 15$^\circ$." (Methods - Observations)
- observing dates: 22 March 2017  
  > "were recorded on March 22nd, 2017." (Observations)
- pi or archival as stated: Project 2016.1.01235.S; data previously used for stratospheric wind mapping by ref. (21); data obtainable from the ALMA archive  
  > "as part of the 2016.1.01235.S project, which have enabled mapping the winds in Jupiter’s stratosphere (21)." (Methods - Observations); "Observation data can be obtained from the ALMA archive." (Data availability)
- Line: HCN 4-3 (354.505 GHz)
- Line: CO 3-2 (345.796 GHz)
- Other facility **Gemini/TEXES**: CH4 7.8 micron band spectra used to retrieve the stratospheric temperature field (1 microbar to 50 mbar) needed for the HCN and CO retrievals  
  > "These were used to retrieve the temperature field between 1 $\mu$bar and 50 mbar with uncertainties $<$ 2 K." (Observations); "Fortunately, Jupiter’s stratospheric temperatures have been retrieved from Gemini/TEXES observations of the CH$_4$ band at 7.8 $\mu$m a few days before our observations." (Methods - Temperature field)
- Other facility **JPL Horizons**: Ephemeris/geometry of Jupiter at the time of observation  
  > "We take the ephemeris from JPL Horizons Solar System Dynamics ephemerides (https://ssd.jpl.nasa.gov/horizons/) to have the planet geometrical data at the time of the observations." (Methods - Radiative transfer)
- External data: Gemini/TEXES temperature maps for low-to-mid latitudes (14, 16, 20 March 2017)  
  > "The spectral maps of the equatorial zone up to the mid-latitudes were obtained on March 14, 16 and 20, 2017 by (22)" (Methods - Temperature field) [from (22) Cosentino et al., JGR Planets 122, 2719]
- External data: Gemini/TEXES temperature maps for high latitudes (17-19 March 2017)  
  > "and for the high latitudes on March 17–19, 2017, by (23)." (Methods - Temperature field) [from (23) Sinclair et al., Planet. Sci. J. 4, 76 (2023)]
- External data: Statistical average of the UV auroral emission used for comparison with the HCN column density  
  > "we compare the column density on the limb with the statistical average of the UV emission of the auroras (24) at the time of our observations" (HCN at high latitudes) [from (24) Clarke et al., JGR 114, A05210 (2009)]
- External data: HCN pressure broadening coefficient 0.145 cm-1 atm-1 and temperature exponent 0.75  
  > "We adopted a pressure broadening coefficient $\gamma$ of 0.145 cm$^{-1}$.atm$^{-1}$ and a temperature dependence exponent $n$ of 0.75 for the HCN line according to (43)." (Methods - Radiative transfer) [from (43) Rohart et al. 1987]
- External data: CO pressure broadening coefficient 0.067 cm-1 atm-1 and temperature exponent 0.60  
  > "For the CO line, we took $\gamma$=0.067 cm$^{-1}$.atm$^{-1}$ and $n$=0.60, according to (44)." (Methods - Radiative transfer) [from (44) Dick et al. 2009]
- External data: Collision-induced absorption of H2-He-CH4 for the continuum  
  > "The continuum is formed from the collision-induced absorption of H$_2$–He–CH$_4$ (45-47)" (Methods - Radiative transfer) [from (45-47) Borysow et al. 1985, Borysow and Frommhold 1986, Borysow et al. 1988]
- External data: Spectroscopic data for both lines from the JPL catalog  
  > "The spectroscopic data for both lines come from the JPL catalog." (Methods - Radiative transfer) [from JPL catalog (no reference given)]
- External data: Earlier HCN and CO measurements used for loss-factor comparisons (1995-1998 maps; 2000 Cassini value)  
  > "This corresponds to a loss factor of 50$\pm$30 when compared with the 1995-1998 period (15)" (The spatial distribution of CO and HCN); "or 120$\pm$35 when compared with the value derived in 2000 from the Cassini flyby data (18)." (The spatial distribution of CO and HCN) [from (15) Moreno et al. 2003; (18) Lellouch et al. 2006]
- Simulation/model as data: Forward radiative transfer model of Jupiter's limb emission with NH3 and PH3 vertical profiles q = q0 (p/p0)^((1-f)/f) (NH3: q0 2e-4, p0 800 mbar, f 0.15; PH3: q0 6e-7, p0 500 mbar, f 0.2)  
  > "with deep mole fractions $q_0$ of 2$\times$10$^{-4}$ and 6$\times$10$^{-7}$, cut-off pressures $p_0$ of 800 and 500 mbar, and fractional scale heights f of 0.15 and 0.2, for NH$_3$ and for PH$_3$, respectively." (Methods - Radiative transfer)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.7.2 (data reduced by ref. 21)  
  > "reduced the data using CASA 4.7.2 and applied bandpass, amplitude and phase calibration using the following sources, respectively: J1256-0547 (3C279), Ganymede and J1312-0424." (Methods - Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ganymede (amplitude); bandpass J1256-0547 (3C279); phase J1312-0424  
  > "applied bandpass, amplitude and phase calibration using the following sources, respectively: J1256-0547 (3C279), Ganymede and J1312-0424." (Methods - Observations)
- flux scale uncertainty: ~5%  
  > "The calibration uncertainties are $\sim$5%." (Methods - Observations)
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
- continuum subtraction: Subtraction in the uv-plane using a uniform (disk) continuum model, leaving continuum residuals  
  > "The continuum is then subtracted in the uv-plane to enable imaging the spectral line. It is done using a uniform continuum model." (Methods - Observations); "This results in an imperfect continuum subtraction, which leaves some continuum residuals." (Methods - Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.2 arcsec (East-West) x 1 arcsec (North-South)  
  > "the resulting elliptical synthetic beam was 1.2” (East-West) $\times$ 1” (North-South)" (Methods - Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction and calibration (CASA 4.7.2, calibrators) done in the earlier wind-mapping paper  
  > "reduced the data using CASA 4.7.2 and applied bandpass, amplitude and phase calibration using the following sources" (Methods - Observations) [from (21) Cavalié et al. 2021, A&A 647, L8]
- Radiative transfer model adapted to Jupiter  
  > "We used the radiative transfer model described in (42) adapted to Jupiter’s atmosphere." (Methods - Radiative transfer) [from (42) Cavalié et al. 2019, A&A 630, A87]
- Temperature field from TEXES maps of other authors  
  > "The spectral maps of the equatorial zone up to the mid-latitudes were obtained on March 14, 16 and 20, 2017 by (22)" (Methods - Temperature field) [from (22) Cosentino et al. 2017; (23) Sinclair et al. 2023]

### Not stated but needed to reproduce (our reading)

- tclean/imaging parameters (weighting, robust, cell size, image size, deconvolver, cleaning masks) used to make the HCN and CO cubes
- Channel ranges used for the uniform-disk continuum model and uv-plane subtraction, and the disk model parameters
- Calibration flux model for Ganymede and any flux-scale corrections
- How the 557 HCN and 540 CO limb spectra were extracted (positions, limb definition, bilinear interpolation details); text says 'they extracted', not clear who
- Value of the regularization parameter alpha and the initial parameter guesses
- Noise values (S_e) assigned per spectrum
- The retrieval code itself (available only on request) and the TEXES-derived 3D temperature cubes beyond what is on Zenodo
- Exact JPL catalog line list entries and versions

## Analysis recipe

1. **Calibrate ALMA data**: Data reduced with CASA 4.7.2 in the earlier paper (21), with bandpass, amplitude and phase calibrators  
  > "reduced the data using CASA 4.7.2 and applied bandpass, amplitude and phase calibration using the following sources, respectively: J1256-0547 (3C279), Ganymede and J1312-0424." (Methods - Observations)
   - software: CASA
   - parameter: Calibration uncertainty ~5%  
  > "The calibration uncertainties are $\sim$5%." (Methods - Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Subtract continuum and image the lines**: uv-plane continuum subtraction with a uniform disk model, then spectral line cubes  
  > "The continuum is then subtracted in the uv-plane to enable imaging the spectral line. It is done using a uniform continuum model." (Methods - Observations)
   - assumption: Uniform disk continuum, which misses Jupiter's zone/belt structure and alters the line-to-continuum ratio by up to 30%  
  > "This subtraction is performed using a uniform disk model which does not perfectly fit the zone/belt structure of Jupiter’s continuum." (The spatial distribution of CO and HCN)
   - fitting: _not stated_
   - validation: Variability in column densities attributed to the continuum subtraction was identified as an artefact (also for CO)  
  > "We find a similar structure in the variability of the CO column density profile in this latitudinal range and it is thus also not a real feature." (The spatial distribution of CO and HCN)
3. **Extract limb spectra**: Spectra extracted along the limb at the 1-bar level from the data cube by bilinear interpolation of spatial pixels; beam oversampled by a factor of four to five  
  > "We took the 557 HCN spectra and 540 CO spectra they extracted from the limb (at the 1-bar level) to carry out our analyses." (Methods - Observations); "The beam was oversampled by a factor of four to five and the spectra were obtained from a bilinear interpolation of the spatial pixels of the data cube." (Methods - Observations)
   - parameter: 557 HCN spectra, 540 CO spectra  
  > "We took the 557 HCN spectra and 540 CO spectra they extracted from the limb (at the 1-bar level)" (Methods - Observations)
   - fitting: _not stated_
   - validation: _not stated_
4. **Build the temperature field**: 3D temperature field reconstructed from Gemini/TEXES retrievals, gaps filled by linear interpolation; 2D latitude/pressure maps extracted at 350W and 170W for each limb  
  > "We reconstructed a full 3D temperature field from the combined retrieved temperature maps, and filled the latitudinal and longitudinal gaps by interpolating linearly between the data points." (Methods - Temperature field); "We extracted these 2D thermal maps from the 3D field at 350W (eastern limb) and 170W (western limb)." (Methods - Temperature field)
   - assumption: Temperatures at other longitudes ignored; 2D fields per limb  
  > "we do not consider the temperatures at other longitudes in our radiative transfer calculations and essentially work with 2D fields (pressure-latitude) for each limb." (Methods - Temperature field)
   - fitting: _not stated_
   - validation: Forward calculations through the full 3D temperature field compared with 2D maps; the 3D field was needed for <5% of HCN spectra, which were re-run  
  > "These cases represent less than 5% of the HCN spectra" (Methods - Retrieval model)
5. **Retrieve HCN and CO vertical profiles per limb spectrum**: Forward radiative transfer plus iterative damped least-squares (Twomey-Tikhonov) retrieval of a three-parameter tanh vertical profile for each limb spectrum  
  > "We solved the inverse problem with an iterative damped least-squares method, also known as Twomey–Tikhonov in Earth atmospheric science literature (50)." (Methods - Retrieval model); "The mixing ratio as a function of height in km above the 1 bar level, f(z), is parameterized with three independent numbers, $a_1$, $a_2$, $a_3$ as follows:" (Methods - Retrieval model)
   - software: radiative transfer model of Cavalie et al. 2019, JPL catalog, JPL Horizons
   - parameter: Convergence when reduced chi-squared improves by less than 0.5%  
  > "The iterative process continues while the current reduced $\chi_i^2$ is smaller than the one from previous iteration within a threshold of 0.5%." (Methods - Retrieval model)
   - parameter: Regularization parameter alpha fixed for all retrievals after trial and error with synthetic inversions  
  > "The regularization parameter, $\alpha$, was estimated by trial and error with synthetic inversions and then fixed for all subsequent iterations of all retrievals." (Methods - Retrieval model)
   - assumption: Lines not optically thick (tau 0.2 for CO, 0.4 for HCN at high latitudes, 1.6 for HCN at low-to-mid latitudes)  
  > "because the lines are not optically thick (i.e., $\tau$$=$ 0.2 for CO, 0.4 for HCN at high latitudes, and 1.6 for HCN in the low-to-mid latitudes)." (Observations)
   - assumption: Pressure broadening and NH3/PH3 profiles as given  
  > "We adopted a pressure broadening coefficient $\gamma$ of 0.145 cm$^{-1}$.atm$^{-1}$ and a temperature dependence exponent $n$ of 0.75 for the HCN line according to (43)." (Methods - Radiative transfer)
   - fitting: Damped least squares with numerical Jacobian held constant over iterations; initial guess from the previously inverted limb point (first point set manually); uncertainties from the solution covariance matrix  
  > "This matrix remains constant during iterations." (Methods - Retrieval model); "For subsequent points on the map, they were however taken from the previously inverted measurement before running the first retrieval iteration." (Methods - Retrieval model)
   - validation: Parameters are independent per Jacobian study; about 95% of HCN and 98% of CO retrievals converge automatically; uncertainties generally <3% on a1, <1% on a2, 5-10% on a3  
  > "About 95% of HCN retrievals converge automatically to the set criteria, and about 98% in case of CO which is more optically thin." (Methods - Retrieval model); "We studied the forward radiance Jacobians (as used in inverse problems) and found that the three parameters can be estimated with a high-degree of independence." (Methods - Retrieval model)
6. **Derive column densities, masses and loss factors and compare with auroras**: Retrieved profiles integrated to column density versus latitude; column density profile integrated to total mass; compared with UV auroral emission statistical average  
  > "The whole set of retrieved profiles is shown in Fig. 8 and we took these profiles to compute the column density as a function of latitude." (The spatial distribution of CO and HCN); "Integrating the HCN column density meridional profile, we find a total mass of 5.0$\pm$0.1 $\times$ 10$^{11}$ g." (The spatial distribution of CO and HCN)
   - assumption: Meridional mixing lower limit estimated as Kyy ~ L^2/Delta t with L from 44S to the north pole and Delta t = 22.5 years  
  > "For CO to populate all latitudes starting from the impact latitude in maximum $\Delta$t$=$ 22.5 years" (The spatial distribution of CO and HCN)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: Data reduction and calibration (done by ref. 21)  
  > "reduced the data using CASA 4.7.2 and applied bandpass, amplitude and phase calibration" (Methods - Observations)
- **JPL Horizons** : Planet geometry ephemerides at the time of observation  
  > "We take the ephemeris from JPL Horizons Solar System Dynamics ephemerides (https://ssd.jpl.nasa.gov/horizons/) to have the planet geometrical data at the time of the observations." (Methods - Radiative transfer)
- **JPL catalog** : Spectroscopic data for the HCN and CO lines  
  > "The spectroscopic data for both lines come from the JPL catalog." (Methods - Radiative transfer)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO cut-off pressure (meridionally uniform) | 3 | 1 | mbar | 5 | we find a CO mole fraction of 41$\pm$12 ppb (1-$\sigma$ uncertainty) at pressures lower than an average cut-off of 3$\pm$1 mbar. |
| CO mole fraction above cut-off | 41 | 12 (1-sigma) | ppb | 5 | we find a CO mole fraction of 41$\pm$12 ppb (1-$\sigma$ uncertainty) |
| CO column density (meridionally uniform) | 1.86e15 | 0.52e15 | cm^-2 | 6 | The resulting meridionally uniform CO column density is 1.86$\pm$0.52 $\times$ 10$^{15}$ cm$^{-2}$. |
| Total mass of SL9-derived CO | 5.47e13 | 0.26e13 | g | 6 | The total mass of SL9-derived CO is then 5.47$\pm$0.26 $\times$ 10$^{13}$ g |
| CO loss factor since 1995-1998 | 9 | 3 | dimensionless | 6 | which corresponds to a loss factor of 9$\pm$3 since 1995-1998 (15). |
| Lower limit on meridional eddy mixing Kyy | >=3.7e11 | not stated | cm^2 s^-1 | 6 | it requires $K_{yy}\sim\frac{L^{2}}{\Delta t}\geq3.7 \times 10^{11}$ cm$^2$.s$^{-1}$ around mbar pressures |
| HCN column density, ~55S to ~40N | 22.6e12 | 5.7e12 | cm^-2 | 6 | with a value of 22.6$\pm$5.7 $\times$ 10$^{12}$ cm$^{-2}$ |
| HCN mole fraction in low-to-mid latitudes | 0.9 | 0.5 (1-sigma) | ppb | 5 | we find an HCN mole fraction of 0.9$\pm$0.5 ppb (1-$\sigma$ uncertainty) |
| HCN cut-off pressure in low-to-mid latitudes | 2 | +2/-1 | mbar | 5 | at pressures lower than an average cut-off of 2$_{-1}^{+2}$ mbar. |
| HCN cut-off pressure in the auroral regions | 0.04 | +0.07/-0.03 | mbar | 5 | the HCN profile is cut-off at a pressure higher than 0.04$_{-0.03}^{+0.07}$ mbar in these regions |
| HCN column density drop at high latitudes | 25-100 | not stated | dimensionless (factor) | 6 | the HCN column density drops by a factor of 25–100 with respect to the low-to-mid latitudes. |
| Total mass of HCN | 5.0e11 | 0.1e11 | g | 6 | we find a total mass of 5.0$\pm$0.1 $\times$ 10$^{11}$ g. |
| HCN loss factor vs 1995-1998 | 50 | 30 | dimensionless | 6 | This corresponds to a loss factor of 50$\pm$30 when compared with the 1995-1998 period (15) |
| HCN loss factor vs 2000 Cassini value | 120 | 35 | dimensionless | 6 | or 120$\pm$35 when compared with the value derived in 2000 from the Cassini flyby data (18). |
| HCN abundance interior of southern auroral oval vs surrounding polar region (sub-mbar) | ~10 times higher | not stated | dimensionless | 5 | There is thus a $\sim$10 times higher abundance of HCN at sub-mbar pressures interior of the southern aurora compared to the surrounding polar region. |
| Uncertainty on column densities from continuum subtraction | about 30% | not stated | percent | 2 | The resulting uncertainty on the column densities is about 30% and is the biggest source of uncertainty in this study. |

## Qualitative findings

- CO is meridionally uniform in Jupiter's stratosphere and confined to pressures lower than ~3 mbar  
  > "CO was meridionally uniform and restricted to pressures lower than 3$\pm$1 mbar." (abstract)
- HCN is depleted at pressures between ~2 and 0.04 mbar in the aurora and surrounding regions, with a two-orders-of-magnitude drop in column density  
  > "resulting in a drop by two orders of magnitude in column density." (abstract)
- Proposed explanation: heterogeneous chemistry bonding HCN on large aurora-produced aerosols  
  > "We propose that heterogeneous chemistry bonds HCN on large aurora-produced aerosols at these pressures in the jovian auroral regions causing the observed depletion." (abstract)

## Claim tuples

- H: Is CO, a long-lived SL9 species, uniformly distributed in latitude in Jupiter's stratosphere? | E: Retrieval of CO vertical profiles from ALMA CO (3-2) limb spectra along the planetary limb | R: CO mole fraction of 41+/-12 ppb below an average cut-off of 3+/-1 mbar at all latitudes; column density 1.86+/-0.52e15 cm^-2 | F: CO is meridionally uniform, which sets a lower limit on meridional mixing | **supported**
- H: Does HCN share the CO distribution at all latitudes? | E: Retrieval of HCN vertical profiles from ALMA HCN (4-3) limb spectra | R: HCN similar to CO at low-to-mid latitudes but its column density drops by a factor of 25-100 poleward, with cut-off at 0.04 mbar | F: HCN is depleted in the auroral and surrounding regions | **supported**
- H: Is the HCN depletion caused by a dynamical barrier or by HCN-specific chemical loss in the auroras? | E: Compared CO and HCN distributions and HCN depletion with the UV auroral emission | R: CO is not depleted where HCN is, and the depletion matches auroral locations | F: Efficient HCN-specific chemical loss, proposed to be uptake onto aurora-produced organic aerosols, rather than a dynamical barrier | **partially**
- H: Why is there an HCN excess interior of the southern auroral oval? | E: Tested whether higher sub-mbar temperatures could explain the excess emission | R: Increasing sub-mbar temperatures from 170 K to 210 K decreases the sub-mbar HCN mole fraction only by ~20% and still fails to fit the line | F: A change in the HCN vertical profile is needed; HCN may be formed from N2 ionised by magnetospheric electrons in the auroras | **partially**

## Reasoning

- Why this data: High-S/N, high spectral resolution ALMA maps resolve the line shapes and thus the vertical profile  
  > "Such a high spectral resolution enables fully resolving the lineshape of the HCN and CO lines" (Methods - Observations)
- Why this method: A three-parameter vertical profile was chosen because the HCN line shape implies a cut-off altitude needing two parameters  
  > "We thus opted for a three-parameter parametrization of the vertical profiles, because the HCN line profile clearly implies a cut-off altitude which has to be described by two parameters" (Methods - Retrieval model)
- Alternative: Destruction of HCN by magnetospheric energetic electrons rejected because they do not penetrate to mbar pressures  
  > "However, we dismiss this possibility because magnetospheric electrons do not penetrate down to mbar pressures in the auroras (25, 26)." (HCN at high latitudes)
- Alternative: Dynamical barrier explanation rejected because CO is not depleted  
  > "The fact that HCN is clearly depleted in the auroral regions between 0.04 and 3 mbar while CO is not can therefore not be caused by a dynamical barrier" (HCN at high latitudes)
- Alternative: Higher auroral temperatures alone rejected as explanation for HCN excess in southern oval  
  > "However, there is no profile with increased temperatures in the sub-mbar region that enables the reproduction of the observations without invoking a change in the HCN vertical profile." (HCN interior of the southern auroral oval)
- How they decided it was enough: _not stated_
- Limitation (authors): Uniform-disk continuum subtraction leaves residuals, giving about 30% uncertainty on column densities, the largest uncertainty  
  > "The resulting uncertainty on the column densities is about 30% and is the biggest source of uncertainty in this study." (Methods - Observations)
- Limitation (authors): Temperature model limited by interpolation in gaps of TEXES coverage of auroral regions  
  > "Since our temperature model is inherently limited by the interpolation that we apply in the few gaps in the coverage of the auroral regions the Gemini/TEXES data have" (HCN interior of the southern auroral oval)
- Limitation (authors): Northern aurora geometry less favorable at the time of observations  
  > "Although the geometry was less favorable at the time of the observations with the northern auroral oval just rising over the 170W limb" (HCN at high latitudes)
- Limitation (authors): Only northernmost latitudes unobserved; 2D temperature maps per limb ignore other longitudes  
  > "The sub-observer latitude of -3$^\circ$ ensures that only the northernmost latitudes were unobserved." (Methods - Observations)
- Caveat (inferred, ours): Only one epoch (single 24-minute ALMA observation) so no temporal evolution is shown despite the stated aim
- Caveat (inferred, ours): Aerosol-uptake explanation is not tested with a chemistry or microphysics model, and the aerosols are not observed
- Caveat (inferred, ours): Retrieval relies on an interpolated TEXES temperature field from observations on different dates than the ALMA data
- Caveat (inferred, ours): The tanh three-parameter profile shape is assumed; alternative shapes and the effect of regularization are not shown
- Caveat (inferred, ours): Retrieval code is not public

## Reproducibility

- Data public (paper): Observation data obtainable from the ALMA archive  
  > "Observation data can be obtained from the ALMA archive." (Data availability)
- Products in archive: Temperature profiles, HCN and CO limb spectra and retrieved vertical profiles on Zenodo (10.5281/zenodo.7928701)  
  > "Temperature profiles, HCN and CO limb spectra and retrieved vertical profiles can be obtained on the following Zenodo repository: https://doi.org/10.5281/zenodo.7928701" (Data availability)
- Code: Retrieval software available upon request  
  > "Software used for the retrievals is available upon request by contacting the corresponding author." (Code availability)
- Missing: Imaging recipe and continuum/line-free channel choices used to make the cubes
- Missing: Retrieval code and regularization parameter
- Missing: How limb spectra were extracted in detail
- Missing: Calibration details are only in ref. 21
- Data volume (inferred): Small to moderate: one 24-minute C-1 mosaic of 39 pointings, a few tens of GB raw; the Zenodo spectra are small
- Score (inferred): 3/5, Data are public in the ALMA archive and the limb spectra, temperature profiles and retrieved profiles are on Zenodo, and the retrieval equations and numeric results are given; but imaging settings are inherited from ref. 21 and not stated, and the retrieval code is only on request.
- Rediscovery candidate: no, The retrieval code is not public and imaging/continuum-subtraction settings are not given, so the pipeline from archive data to the profiles cannot be redone from the paper alone, although the Zenodo spectra allow a partial check.

## Links

- Method: (21) Cavalié et al. 2021, A&A 647, L8 (Earlier paper on the same ALMA data; data reduction with CASA 4.7.2 and calibration)
- Method: (42) Cavalié et al. 2019, A&A 630, A87 (Describes the radiative transfer model adapted to Jupiter)
- Companion: (22) Cosentino et al. 2017, JGR Planets 122, 2719 (TEXES temperature maps for low-to-mid latitudes)
- Companion: (23) Sinclair et al. 2023, Planet. Sci. J. 4, 76 (TEXES temperature maps for high latitudes)
- Related: ALMA project 2016.1.01235.S
- Related: Gemini/TEXES observations of March 2017

## Checks

```json
{
 "quotes": 109,
 "quotes_ok": 109,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 16,
 "numeric_problems": 0,
 "fill": {
  "facts": 98,
  "stated": 68,
  "rate": 0.694
 },
 "evidence_ok": true
}
```
