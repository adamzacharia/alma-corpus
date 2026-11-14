# Binary-induced spiral arms inside the disc cavity of AB Aurigae

`2020MNRAS.496.2362P` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Poblete, Pedro P. | arXiv: 2005.10722 | DOI: 10.1093/mnras/staa1655

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: Can a binary companion orbiting inside the dust cavity of AB Aur produce the inner 12CO (2-1) spiral structure observed with ALMA?  
  > "In this work we demonstrate that the inner spiral structure observed in AB Aurigae can be created by a binary star orbiting inside the dust cavity." (abstract)
- Target **AB Aurigae**: coordinates _not stated_; z/distance 163 pc  
  > "and a source distance of 163 pc (cite: Gaia2018)" (2.2 Radiative Transfer Calculations); "AB Aur is one of the closest Herbig Ae stars" (1 Introduction); distance from Gaia (cite: Gaia2018)  
  > "and a source distance of 163 pc (cite: Gaia2018)" (2.2 Radiative Transfer Calculations); "AB Aur is one of the closest Herbig Ae stars" (1 Introduction)

## Data provenance

- ALMA projects: 2015.1.00889.S
- bands: Band 6; 12CO (2-1) line and 1.3 mm continuum  
  > "These observations were taken in band 6, and include" (2.3 Observational Data); "(2-1) and continuum data at 1.3 mm" (2.3 Observational Data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: restoring beam of 0.12"x0.09" for the 12CO cube  
  > "The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width." (2.3 Observational Data)
- max recoverable scale: _not stated_
- sensitivity: RMS of 3.5 mJy/beam for a 150 m/s channel width  
  > "The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width." (2.3 Observational Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Archival: data of (cite: Tang+2017) retrieved from the ALMA archive  
  > "we retrieved the data used in (cite: Tang+2017) from the ALMA archive (project 2015.1.00889.S)" (2.3 Observational Data)
- Line: 12CO 2-1 (not stated)
- Other facility **Gaia**: Source distance of 163 pc  
  > "and a source distance of 163 pc (cite: Gaia2018)" (2.2 Radiative Transfer Calculations)
- External data: Disc inclination 26 deg and position angle -36 deg used in the radiative transfer  
  > "We assume an inclination of $i = 26^{\circ}$, a position angle PA$=-36^{\circ}$ (cite: Tang+2017; Riviere-Marichalar+2019)" (2.2 Radiative Transfer Calculations) [from (cite: Tang+2017; Riviere-Marichalar+2019)]
- External data: Primary star temperature of 10,000 K  
  > "The temperature of the central star is set to 10,000 K (cite: Ancker+1998)" (2.2 Radiative Transfer Calculations) [from (cite: Ancker+1998)]
- External data: Secondary star temperature 3800 K, radius 1.32 Rsun, luminosity about 0.19 Lsun  
  > "where we assume a temperature of 3800 K and radius of 1.32 $R_\odot$, giving a blackbody luminosity of approximately 0.19 $L_\odot$ (cite: Siess+2000)" (2.2 Radiative Transfer Calculations) [from (cite: Siess+2000)]
- External data: Analytical logarithmic-spiral fits to the eastern and western 12CO spirals, used as the reference for rotating the simulation  
  > "The authors provide the following analytical functions to each spiral (as logarithmic spirals)" (3.3 Integrated CO Emission) [from (cite: Tang+2017)]
- External data: Observed accretion rate of AB Aur of 1.3e-7 Msun/yr  
  > "AB Aur shows an accretion rate of $1.3 \cdot 10^{-7}\ M_{\odot}\ \rm yr^{-1}$; which is considered high for a star of its kind (cite: Garcia-Lopez+2006; Salyk+2013)" (4.2 Observational Signatures) [from (cite: Garcia-Lopez+2006; Salyk+2013)]
- Simulation/model as data: Phantom 3D SPH gas simulation of a circumbinary disc (q=0.25, a=40 au, e=0.5, i=90 deg), compared with the ALMA 12CO data  
  > "We use the same setup as the ‘e50–i90’ case in (cite: Poblete+2019) for both disc and binary" (2.1 SPH simulations)
- Simulation/model as data: mcfost radiative transfer of the SPH output, converted to synthetic ALMA observations with CASA simutil at the observed uv-coverage  
  > "We then simulate the ALMA synthetic observations using the `simutil` tools in casa (v. 5.5.0) and the same $uv$-coverage as the observations." (2.2 Radiative Transfer Calculations)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Three rounds of phase self-calibration on the continuum; continuum peak SNR 38 to 76  
  > "We performed three rounds of phase self-calibration using the continuum observations, which improved the continuum peak SNR from 38 to 76." (2.3 Observational Data)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "we imaged the $^{12}$CO (2-1) emission using natural weighting" (2.3 Observational Data)
- uv taper: 0.08 arcsec; baselines shorter than 160 klambda removed  
  > "a $uv$-tapering of 0.08", and removing baselines shorter than 160 k$\lambda$, since their poor sampling produced substantial artefacts" (2.3 Observational Data)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.12"x0.09"  
  > "The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width." (2.3 Observational Data)
- final rms: 3.5 mJy/beam per 150 m/s channel  
  > "The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width." (2.3 Observational Data)

### Inherited from earlier work

- Archival ALMA data and the spiral analytic functions taken from the earlier work  
  > "we retrieved the data used in (cite: Tang+2017) from the ALMA archive (project 2015.1.00889.S)" (2.3 Observational Data) [from (cite: Tang+2017)]
- Disc and binary setup of the SPH simulation  
  > "We use the same setup as the ‘e50–i90’ case in (cite: Poblete+2019) for both disc and binary" (2.1 SPH simulations) [from (cite: Poblete+2019)]
- Inclination and position angle used for ray-tracing  
  > "We assume an inclination of $i = 26^{\circ}$, a position angle PA$=-36^{\circ}$ (cite: Tang+2017; Riviere-Marichalar+2019)" (2.2 Radiative Transfer Calculations) [from (cite: Tang+2017; Riviere-Marichalar+2019)]

### Not stated but needed to reproduce (our reading)

- Self-calibration solution intervals, reference antenna and which spectral windows or execution blocks were used
- Whether imaging used tclean or another task, image size, cell size, deconvolver, masks and cleaning threshold
- Continuum subtraction method and line-free channels
- Rest frequency and velocity range used for the 12CO moment maps and channel maps
- bettermoments options beyond the 3 rms clip
- Number of SPH particles and snapshot output times beyond the quoted time fractions, and the exact time zero of the binary orbit phase
- mcfost parameter files (grid, wavelength sampling, line broadening) and the simutil observing parameters
- Amount of flux or uv range retained after removing baselines shorter than 160 klambda in the synthetic data
- How the PA of about 100 deg rotation and the snapshot t about 0.7 Tb were chosen quantitatively (only visual comparison is described)

## Analysis recipe

1. **Run 3D SPH simulation of a misaligned eccentric circumbinary disc**: Phantom SPH simulation with both stars as sink particles, disc evolved for about 30 binary orbits  
  > "We model both stars as sink particles (cite: Bate+1995) with an accretion radius of 1 au." (2.1 SPH simulations); "Figure [1](#fig:simulation) shows the gas surface density after approximately 30 binary orbits." (3 Results)
   - software: Phantom
   - parameter: q=0.25 (M1=2 Msun, M2=0.5 Msun)  
  > "The binary is initialised with a mass ratio of $q=M_2/M_1=0.25$ with $M_1=2\,M_{\odot}$ and $M_2=0.5\,M_{\odot}$." (2.1 SPH simulations)
   - parameter: semi-major axis 40 au, eccentricity 0.5, period about 160 yr  
  > "The companion is placed on an orbit with a semi-major axis of $40$ au, and an eccentricity $e_{\rm B}=0.5$, giving a period of $\sim$160 yrs." (2.1 SPH simulations)
   - parameter: 5e6 SPH particles, total gas mass 0.01 Msun  
  > "The gas disc in our simulation is initialised with $5\times 10^6$ SPH particles in Keplerian rotation with a total gas mass of $0.01\ M_{\odot}$." (2.1 SPH simulations)
   - parameter: Sigma proportional to R^-1, T proportional to R^-0.3, H/R = 0.06 at R_in and 0.1 at R_out  
  > "The surface density profile is given by a power law, $\Sigma \propto R^{-1}$." (2.1 SPH simulations); "giving a scale height of $H/R = 0.06$ at $R_{\rm in}$ and $H/R = 0.1$ at $R_{\rm out}$" (2.1 SPH simulations)
   - assumption: No dust grains in the simulation; binary inclined 90 deg to the disc mid-plane, omega = Omega = 0 deg  
  > "We did not include dust grains in our simulation." (2.1 SPH simulations); "The initial argument of periapsis ($\omega$) and the line of nodes ($\Omega$) are both set to $0\degree$." (2.1 SPH simulations)
   - assumption: Vertically isothermal disc with SPH alpha_AV about 0.3, giving alpha_SS about 5e-3  
  > "The disc is vertically isothermal" (2.1 SPH simulations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer of the SPH output to predict 12CO (2-1) emission**: Monte Carlo radiative transfer with mcfost, with a dust model built from the SPH gas distribution  
  > "Since we do not include dust grains in our simulation, we construct a dust model using the gas distribution in our SPH simulation" (2.2 Radiative Transfer Calculations)
   - software: mcfost
   - parameter: 1e8 Monte Carlo photon packets; i = 26 deg, PA = -36 deg, distance 163 pc  
  > "We used $10^8$ Monte Carlo photon packets to compute the temperature and specific intensities." (2.2 Radiative Transfer Calculations); "and a source distance of 163 pc (cite: Gaia2018)" (2.2 Radiative Transfer Calculations)
   - parameter: Dust grain sizes 0.01 micron to 1 mm with m=3.5, giving kappa = 15 cm2/g at 1 mm  
  > "This gives an opacity of $\kappa = 15\ $cm$^2$g$^{-1}$ at a wavelength of 1 mm." (2.2 Radiative Transfer Calculations)
   - assumption: Gas-to-dust ratio 100  
  > "The total dust mass is calculated assuming the typical gas-to-dust ratio value of 100, where the gas mass is taken directly from our simulation." (2.2 Radiative Transfer Calculations)
   - assumption: 12CO-to-H2 abundance 1e-4  
  > "We assume an abundance ratio of $^{12}$CO-to-H$_2$ of $10^{-4}$ when computing the $^{12}$CO (2-1) line emission intensity." (2.2 Radiative Transfer Calculations)
   - assumption: Primary 10,000 K, 2.5 Rsun, luminosity 52 Lsun; passively heated disc with dust and gas in thermal equilibrium  
  > "The disc is passively heated and we assume that the dust and gas are in thermal equilibrium." (2.2 Radiative Transfer Calculations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Make synthetic ALMA observations of the model**: CASA simutil with the same uv-coverage as the observations, imaged with the same procedure as the data  
  > "Finally, images were obtained using the same procedure as with the observations" (2.2 Radiative Transfer Calculations)
   - software: CASA
   - parameter: CASA v. 5.5.0  
  > "tools in casa (v. 5.5.0) and the same $uv$-coverage as the observations" (2.2 Radiative Transfer Calculations)
   - fitting: _not stated_
   - validation: Checked that perturbed iso-velocity curves are also present with perfect uv-coverage  
  > "These features in our model are not a product of the sparse $uv$-coverage, as they are also evident when we assume perfect $uv$-coverage." (3.5 CO Kinematics)
4. **Reprocess archival ALMA 12CO (2-1) data and make moment maps**: Phase self-calibration on continuum, imaging with natural weighting, uv-taper and baseline cut, moments 0 and 1 with sigma clipping  
  > "We performed three rounds of phase self-calibration using the continuum observations, which improved the continuum peak SNR from 38 to 76." (2.3 Observational Data); "Finally, the corresponding moments 0 and 1 were produced using the" (2.3 Observational Data)
   - software: bettermoments
   - parameter: natural weighting, uv-taper 0.08 arcsec, baselines shorter than 160 klambda removed  
  > "a $uv$-tapering of 0.08", and removing baselines shorter than 160 k$\lambda$, since their poor sampling produced substantial artefacts" (2.3 Observational Data)
   - parameter: sigma-clipping at 3 rms for the moments  
  > "using $\sigma$-clipping at the 3 rms level" (2.3 Observational Data)
   - fitting: _not stated_
   - validation: _not stated_
5. **Compare model and observations to select orientation and orbital phase**: Rotate the simulation so the binary eccentricity vector points at PA about 100 deg, then compare spiral positions, moment 0, moment 1 and channel maps with Tang+2017 logarithmic spirals; best match at t about 0.7 Tb  
  > "We use these functions as a reference to rotate our simulation when conducting the radiative transfer modelling." (3.3 Integrated CO Emission); "In Figure [2](#fig:spiral_evolution), our closest match to the spiral arms occurs when $t \sim 0.7 \ T_\mathrm{b}$." (4.2 Observational Signatures)
   - parameter: Eccentricity vector at PA about 100 deg  
  > "Rotating our model such that the eccentricity vector of the binary companion points at a $\textrm{PA} \sim 100 \degree$ provides a close match to the spiral structure." (3.3 Integrated CO Emission)
   - fitting: No formal fit; visual comparison only  
  > "Our model matches relatively well the location of the spiral arms, and apart from the hot-spot at the south side, the intensity also matches." (3.3 Integrated CO Emission)
   - validation: Excess model CO near the primary tested with a gas-to-dust ratio of 10; companion parameter space not searched exhaustively  
  > "With this setup, the models resemble the observed CO emission of the inner regions more closely." (Appendix: CO maps for a gas-to-dust ratio of 10); "In this work we have not conducted an exhaustive search of this parameter space to rule out other possible configurations." (4.1 Binary Orbital Parameters)
6. **Derive companion location, motion and inclination range as predictions**: Read companion position and proper motion from the best-match snapshot; combine with the dust morphology of Poblete+2019 to bound the binary inclination  
  > "In our model the companion is currently located at roughly $r \sim 0.18\ensuremath{''}$ from the central source, with a $\rm PA\sim 100\degree$ and is moving away from the primary star at a rate of roughly 6 mas/yr." (4 Discussion)
   - assumption: Results are model dependent  
  > "These quantities are model-dependent;" (4 Discussion)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Phantom** : 3D SPH hydrodynamical simulation of the circumbinary disc  
  > "using the Phantom smoothed particle hydrodynamics (SPH) code" (2.1 SPH simulations)
- **mcfost** : Monte Carlo radiative transfer to create synthetic observations of the SPH output  
  > "using the Monte Carlo radiative transfer code mcfost (cite: Pinte+2006; Pinte+2009)" (2.2 Radiative Transfer Calculations)
- **CASA (simutil)** 5.5.0: Simulating ALMA synthetic observations with the real uv-coverage  
  > "tools in casa (v. 5.5.0) and the same $uv$-coverage as the observations" (2.2 Radiative Transfer Calculations)
- **bettermoments** : Producing moment 0 and moment 1 maps of observations and simulations  
  > "Finally, the corresponding moments 0 and 1 were produced using the" (2.3 Observational Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Predicted companion separation from the primary | 0.18 | not stated | arcsec | 6 | our model predicts the location of the companion at $r \sim 0.18\ensuremath{''}$ from the central source, with a $\rm PA\sim 100\degree$. |
| Predicted companion position angle | about 100 | not stated | deg | 6 | our model predicts the location of the companion at $r \sim 0.18\ensuremath{''}$ from the central source, with a $\rm PA\sim 100\degree$. |
| Predicted companion radial motion away from the primary | 6 | model dependent | mas/yr | 6 | Our model suggest a motion of 6 mas/yr away from the primary star, but this value is model dependent. |
| Binary inclination range relative to the circumbinary disc | 60 to 90 | not stated | deg | 6 | we constrain the inclination of the binary with respect to the circumbinary disc to range between $60\degree$ and $90\degree$ |
| Orbital phase of best match to spirals | t about 0.7 Tb | not stated | dimensionless | 5 | In Figure [2](#fig:spiral_evolution), our closest match to the spiral arms occurs when $t \sim 0.7 \ T_\mathrm{b}$. |
| Continuum peak SNR before and after self-calibration | 38 to 76 | not stated | dimensionless | 4 | which improved the continuum peak SNR from 38 to 76 |
| 12CO cube restoring beam | 0.12 x 0.09 | not stated | arcsec | 4 | The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width. |
| 12CO cube RMS per 150 m/s channel | 3.5 | not stated | mJy/beam | 4 | The resulting cube has a restoring beam of 0.12"x0.09" and an RMS of 3.5 mJy/beam for a 150 m/s channel width. |
| Simulated primary accretion rate for most of the orbit | about 1.5e-8 | not stated | Msun/yr | 1 | we see that during most of the binary orbit, the accretion rate of the primary remains at roughly $\sim 1.5\cdot 10^{-8}\ M_{\odot}\ \rm yr^{-1}$ |
| Simulated primary accretion rate spike | about 7e-8 at t = 0.2 Tb | varies between orbits by up to a factor of a few | Msun/yr | 1 | However there is a portion of the binary orbit where the accretion rate spikes close to $\sim 7~\cdot 10^{-8}\ M_{\odot}\ \rm yr^{-1}$. |

## Qualitative findings

- The eccentric, inclined companion yields two prominent inner spiral arms that change markedly over the binary orbit rather than co-rotating with the companion  
  > "It is clearly seen that the spiral pattern and the gas distribution change markedly over the binary orbit" (3.2 Orbital Dependence of the Inner Structures)
- The model overpredicts CO near the primary; a gas-to-dust ratio of 10 reduces the discrepancy  
  > "The model shows an excess of CO emission near the primary star with respect to the observation." (3.3 Integrated CO Emission); "This suggests that in the inner regions the gas-to-dust ratio could reach values as low as 10." (Appendix: CO maps for a gas-to-dust ratio of 10)
- Inner kinematics are strongly perturbed and consistent with a misaligned inner disc in the model  
  > "This is in agreement with our model, as material inside the cavity becomes misaligned with respect to the outer disc due to the orbit of the companion" (3.5 CO Kinematics)

## Claim tuples

- H: An inclined, eccentric stellar binary inside the cavity can produce the inner double-spiral seen in 12CO (2-1) of AB Aur | E: Phantom SPH simulation plus mcfost radiative transfer and CASA simutil, compared with reprocessed archival ALMA 12CO moment and channel maps | R: Model spiral locations and intensities match the observed spirals, except a south hot-spot and excess CO near the primary | F: The inner spirals can be explained by a q=0.25, e=0.5, a=40 au binary inclined 90 deg | **supported**
- H: The binary inclination relative to the circumbinary disc can be constrained | E: Compare the 90 deg gas spirals with the 60 deg dust clump morphology of Poblete+2019 | R: 90 deg matches the CO spirals, 60 deg the 1.3 mm dust morphology | F: Inclination between 60 and 90 deg, but other configurations were not ruled out | **partially**
- H: The inner spiral structure changes with time instead of co-rotating with the companion | E: Plot surface density at ten time steps of the binary orbit | R: Spiral pattern and gas distribution change markedly over the orbit | F: Spirals should vary in time and not simply co-rotate with the companion | **supported**
- H: A lower gas-to-dust ratio in the inner disc explains the excess model CO emission | E: Repeat the radiative transfer with gas-to-dust ratio 10 | R: Models resemble the observed inner CO emission more closely | F: Inner gas-to-dust ratio could be as low as 10 | **partially**
- H: The binary scenario explains the high observed accretion rate of AB Aur | E: Measure SPH particles entering the 1 au accretion radius of the primary over one orbit | R: About 1.5e-8 Msun/yr most of the orbit with a spike near 7e-8 Msun/yr at a phase other than the best spiral match | F: Binary could help explain the accretion rate, but a phase discrepancy remains | **partially**

## Reasoning

- Why this data: Archival ALMA 12CO (2-1) data from the earlier work were used to confront the simulation  
  > "To confront our simulations with observations, we retrieved the data used in (cite: Tang+2017) from the ALMA archive (project 2015.1.00889.S)." (2.3 Observational Data)
- Why this method: A dust model is built from the gas because the SPH run contains no dust  
  > "Since we do not include dust grains in our simulation, we construct a dust model using the gas distribution in our SPH simulation" (2.2 Radiative Transfer Calculations)
- Alternative: A companion on the stable polar alignment did not produce the double spiral inside the cavity  
  > "We found that placing a companion on the stable polar alignment does not produce a double spiral arm feature inside the cavity of AB Aur." (4.1 Binary Orbital Parameters)
- Alternative: Co-planar stellar companions do not make quasi-symmetric double spirals inside the cavity like those in AB Aur  
  > "Co-planar stellar companions do not appear to make quasi-symmetric double spiral arms inside the cavity like the ones seen in AB Aur" (4.1 Binary Orbital Parameters)
- How they decided it was enough: _not stated_
- Limitation (authors): Parameter space not searched exhaustively; other binary configurations could match  
  > "However, once again we caution that other binary configurations may produce a similar double spiral morphology with the companion at a different location in the cavity." (4.1 Binary Orbital Parameters)
- Limitation (authors): Model overpredicts CO near the primary; no MHD, winds or photoevaporation  
  > "However, we note that our simulations do not include mechanisms such as magneto-hydrodynamical effects, stellar winds, or photoevaporation" (3.3 Integrated CO Emission)
- Limitation (authors): Accretion rate measured only as SPH particles entering the 1 au accretion radius  
  > "our accretion rate simply measures the flux of SPH particles that enter the accretion radius of 1 au for our primary star" (4.2 Observational Signatures)
- Limitation (authors): Predicted companion location and motion are model dependent  
  > "These quantities are model-dependent;" (4 Discussion)
- Limitation (authors): The configuration used is not stable for long-term evolution  
  > "Even though this configuration is not stable for long-term evolution" (4.1 Binary Orbital Parameters)
- Caveat (inferred, ours): Match to the observed spirals is judged by eye; no quantitative goodness-of-fit or parameter uncertainties are given
- Caveat (inferred, ours): Single simulation; orientation (PA about 100 deg) and phase (t about 0.7 Tb) were tuned to the observations, so the companion location prediction has no error bar
- Caveat (inferred, ours): Archival 12CO imaging uses a uv-taper and a 160 klambda baseline cut, so the diffuse emission and spiral contrast are affected
- Caveat (inferred, ours): Model CO excess near the primary suggests the thermal and abundance assumptions (gas-to-dust 100, CO/H2 1e-4) are not validated

## Reproducibility

- Data public (paper): ALMA archive project 2015.1.00889.S  
  > "we retrieved the data used in (cite: Tang+2017) from the ALMA archive (project 2015.1.00889.S)" (2.3 Observational Data)
- Products in archive: _not stated_
- Missing: Self-calibration and imaging task settings (solints, image size, cell, mask, threshold, line-free channels)
- Missing: mcfost and simutil parameter files and the SPH snapshot
- Missing: Quantitative criterion for choosing PA and orbital phase
- Missing: Phantom setup files beyond those inherited from Poblete+2019
- Data volume (inferred): One ALMA Band 6 project (2015.1.00889.S), likely tens of GB of raw data for the 12CO and continuum observations; simulation compute is separate
- Score (inferred): 3/5, Data are public and the simulation parameters are largely given, but calibration and imaging settings are incomplete, the SPH setup is partly inherited, code and snapshots are not released, and the main result is a visual match.
- Rediscovery candidate: no, The main results are a qualitative visual match plus model-dependent predictions, and the simulation and imaging recipe is not complete enough to redo.

## Links

- Method: (cite: Poblete+2019) (Source of the e50-i90 disc and binary setup)
- Method: (cite: Pinte+2006; Pinte+2009) (mcfost radiative transfer code)
- Method: (cite: PricePH+2018b) (Phantom SPH code)
- Companion: (cite: Tang+2017) (Source of the ALMA 12CO (2-1) data and the spiral analytic functions)
- Companion: (cite: Riviere-Marichalar+2019) (HCO+ kinematics and disc orientation of AB Aur)
- Companion: (cite: Boccaletti+2020) (SPHERE observations interpreted as a planetary-mass companion, noted in the proof addendum)
- Related: 2015.1.00889.S

## Checks

```json
{
 "quotes": 95,
 "quotes_ok": 95,
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
  "facts": 102,
  "stated": 65,
  "rate": 0.637
 },
 "evidence_ok": true
}
```
