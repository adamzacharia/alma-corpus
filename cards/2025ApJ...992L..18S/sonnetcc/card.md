# The First Radio-bright Off-nuclear Tidal Disruption Event AT 2024tvd Reveals the Fastest-evolving Double-peaked Radio Emission

`2025ApJ...992L..18S` | The Astrophysical Journal Letters 2025 | first author: Sfaradi, Itai | arXiv: 2508.03807 | DOI: 10.3847/2041-8213/ae0a26

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: How does the radio emission of the off-nuclear TDE AT 2024tvd evolve, and are its two radio flares explained by prompt or delayed, relativistic or non-relativistic outflow(s)?  
  > "The off-nuclear TDE 2024tvd exhibits double-peaked radio light curves and the fastest evolving radio emission observed from a TDE to date." (abstract); "We find that a single prompt outflow cannot easily explain these observations" (abstract)
- Target **AT 2024tvd**: coordinates _not stated_; z/distance z = 0.04494; luminosity distance 200 Mpc  
  > "The reported redshift of AT 2024tvd is $z=0.04494$, and we adopt a luminosity distance of $200$ Mpc based on a standard $\Lambda$CDM cosmology" (Introduction); distance from reported redshift with a standard LCDM cosmology (Omega_M = 0.3, Omega_Lambda = 0.7, H0 = 70 km/s/Mpc)  
  > "The reported redshift of AT 2024tvd is $z=0.04494$, and we adopt a luminosity distance of $200$ Mpc based on a standard $\Lambda$CDM cosmology" (Introduction)

## Data provenance

- ALMA projects: 2024.A.00024.T, 2024.A.00034.T
- bands: Band 3 and Band 5  
  > "We used ALMA Bands 3 and 5 with the central frequencies of $97.5$ and $203$ GHz, respectively" (Atacama Large Millimeter/submillimeter Array)
- frequencies and spectral setup: central frequencies 97.5 GHz (Band 3) and 203 GHz (Band 5)  
  > "We used ALMA Bands 3 and 5 with the central frequencies of $97.5$ and $203$ GHz, respectively" (Atacama Large Millimeter/submillimeter Array)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: four epochs (individual dates not given in the text)  
  > "Following our first detection with the VLA we obtained mm-band observations with ALMA in four epochs under two DDT programs (2024.A.00024.T; 2024.A.00034.T; PI: Sfaradi)." (Atacama Large Millimeter/submillimeter Array)
- pi or archival as stated: two DDT programs, PI: Sfaradi (the authors' own proposals)  
  > "Following our first detection with the VLA we obtained mm-band observations with ALMA in four epochs under two DDT programs (2024.A.00024.T; 2024.A.00034.T; PI: Sfaradi)." (Atacama Large Millimeter/submillimeter Array)
- Other facility **VLA**: Cm-band monitoring (S to Ku bands) under program VLA 24A-386 (PI: Alexander) and DDT VLA 25A-483 (PI: Sfaradi)  
  > "We observed the field of AT 2024tvd with the VLA under our dedicated TDE program (VLA 24A-386; PI: Alexander), and a DDT (VLA 25A-483; PI: Sfaradi)." (Karl G. Jansky Very Large Array)
- Other facility **AMI-LA**: 15.5 GHz high-cadence light curve of the second flare, from 2025 January 12  
  > "It observes with a $5$ GHz bandwidth around a central frequency of $15.5$ GHz." (Arcminute Micro-Kelvin Imaging - Large Array)
- Other facility **ATA**: 1.5, 3, 5 and 8 GHz observations under program P062 (PI: Sfaradi), from 2025 March 20  
  > "We observed the field of AT 2024tvd with the ATA under our program (P062; PI: Sfaradi) starting on 2025 March 20" (Allen Telescope Array)
- Other facility **SMA**: mm-band observations from 2025 April 21 under the POETS Large-Scale program 2022B-S046 (PI: E. Berger)  
  > "several observations of AT 2024tvd were conducted with the SMA, as part of the Pursuit of Extragalactic Transients with the SMA (POETS) Large-Scale SMA program (2022B-S046; PI: E. Berger)" (Submillimeter Array)
- Other facility **Zwicky Transient Facility**: Optical discovery of AT 2024tvd (g band, 2024 August 25), which defines the reference time for Delta t  
  > "AT 2024tvd was discovered in the Zwicky Transient Facility" (Introduction)
- External data: Off-nuclear position, black hole mass estimate of 1e5-1e7 Msun and 0.8 kpc offset from the host nucleus; also X-ray spectral analysis and host nucleus coordinates  
  > "a MBH mass of $10^{5} -10^{7} \, M_{\odot}$ at an offset of $0.8$ kpc from the host nucleus was then estimated by (cite: Yao_2025)" (Introduction) [from Yao et al. 2025b (cite: Yao_2025)]
- External data: Thermal optical/UV bolometric luminosity of the TDE used for the inverse-Compton cooling frequency  
  > "we use the thermal optical/UV luminosity during the time of the first radio flare" (Prompt sub-relativistic outflow fit) [from Yao et al., in prep.]
- External data: Relation between star formation rate and 1.4 GHz luminosity  
  > "Adopting the relation between the star formation rate (SFR) and the $1.4$ GHz luminosity from (cite: davies_2017)" (Emission from the host galaxy nucleus) [from Davies et al. 2017 (cite: davies_2017)]
- External data: SFR upper limit of 0.1 Msun/yr for the host from stellar population synthesis  
  > "derived from stellar population synthesis analysis (cite: maraston_2009)" (Emission from the host galaxy nucleus) [from Maraston et al. 2009 (cite: maraston_2009)]
- External data: Flux model for Vesta used for SMA flux calibration  
  > "Flux calibration uses the Butler–JPL–Horizons 2012 (cite: butler_2012) model for Vesta." (Submillimeter Array) [from Butler 2012 (cite: butler_2012)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Yes, the standard NRAO calibrated images were used  
  > "We used the standard National Radio Astronomy Observatory (NRAO) calibrated images" (Atacama Large Millimeter/submillimeter Array)
- flux calibrator: J1550+0527 (absolute flux and bandpass); J1753+2848 (phase)  
  > "J1550+0527 as an absolute flux and bandpass calibrator, and J1753+2848 as a phase calibrator" (Atacama Large Millimeter/submillimeter Array)
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

- ALMA calibration and imaging taken from the standard NRAO calibrated images (no re-imaging)  
  > "We used the standard National Radio Astronomy Observatory (NRAO) calibrated images" (Atacama Large Millimeter/submillimeter Array) [from standard NRAO calibrated images]
- Newtonian equipartition formalism for radius and magnetic field  
  > "Here we use the Newtonian formalism introduced in (cite: chevalier_1998) since the inferred velocities in the spherical outflow scenario are sub-relativistic" (Analysis and modeling of individual SEDs) [from (cite: chevalier_1998)]
- Broken power-law SED function and smoothing parameter  
  > "To obtain the peak flux density and its frequency we adopt here a broken power-law function (see Eq. 1 in (cite: granot_2002))" (Analysis and modeling of individual SEDs) [from (cite: granot_2002)]
- Free-free absorption optical depth  
  > "We also calculate the free-free absorption optical depth as in (cite: Rybicki_lightman) (see also (cite: Nayana_2024))" (Multi-epoch time-dependent modeling of the first radio flare) [from (cite: Rybicki_lightman); see also (cite: Nayana_2024)]
- Off-axis jet derivation procedure  
  > "To derive the physical parameters of an off-axis jet we follow the same procedure outlined in (cite: Matsumoto_2024) and (cite: Christy_2024)." (Relativistic jets observed off-axis) [from (cite: Matsumoto_2024); (cite: Christy_2024)]

### Not stated but needed to reproduce (our reading)

- Individual ALMA execution dates, array configurations and baselines for all four epochs (only Delta t of two epochs is given in the text)
- ALMA spectral setup details: continuum bandwidth, channelisation, integration time and sensitivity per epoch
- ALMA project code to epoch mapping (which epochs belong to 2024.A.00024.T vs 2024.A.00034.T)
- Archive product identifiers and CASA/pipeline version of the NRAO calibrated images used
- IMFIT setup for ALMA: image weighting, beam, fit region, how the source position was fixed, and the ALMA flux-scale uncertainty added to the error
- How the 203 GHz upper limit was defined (sigma level)
- Full machine-readable flux table is online only (not in the text)
- emcee initialisation and convergence tests for the SED and time-dependent fits
- Treatment of host nucleus contamination for the ALMA data
- Electron temperature and Gaunt factor sensitivity checks for the time-dependent model are not shown

## Analysis recipe

1. **measure ALMA flux densities of AT 2024tvd**: Use standard NRAO calibrated images, fit the point source with imfit, and obtain image rms with imstat  
  > "We used the standard National Radio Astronomy Observatory (NRAO) calibrated images, and fitted the point source with CASA task `IMFIT`, and used CASA task `IMSTAT` to obtain the image rms." (Atacama Large Millimeter/submillimeter Array)
   - software: CASA
   - parameter: Band 3 at 97.5 GHz and Band 5 at 203 GHz  
  > "We used ALMA Bands 3 and 5 with the central frequencies of $97.5$ and $203$ GHz, respectively" (Atacama Large Millimeter/submillimeter Array)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit broken power laws to broadband SEDs**: Broken power-law function with smoothing parameter s fixed to 1.25 - 0.18p; electron index p fitted from combined VLA+ALMA SEDs separated by 2-3 days and applied to the neighbouring epochs  
  > "we combine VLA and ALMA observations separated by $2-3$ days" (Analysis and modeling of individual SEDs); "the smoothing parameter, $s$, to $1.25 - 0.18p$" (Analysis and modeling of individual SEDs)
   - software: emcee
   - parameter: 200 walkers, 5,000 steps per chain, first 100 steps discarded  
  > "We use 200 walkers with 5,000 steps for each chain and discard the first 100 steps for burn-in." (Analysis and modeling of individual SEDs)
   - fitting: emcee MCMC with flat priors  
  > "We use `emcee` (cite: foreman_mackey_2013) to determine the best-fit parameters and infer their posterior distributions using flat priors." (Analysis and modeling of individual SEDs)
   - validation: _not stated_
3. **equipartition radius, field, density and energy for a prompt non-relativistic outflow**: Chevalier (1998) Newtonian equipartition applied to each SED peak; velocity from R over Delta t  
  > "First, we assume that (1) the outflow was launched around the time of optical discovery, (2) equipartition ($\epsilon_{\rm e} = \epsilon_{\rm B} = 0.1$), and (3) an emission filling factor, $f=0.5$" (A prompt, non-relativistic outflow)
   - parameter: epsilon_e = epsilon_B = 0.1, filling factor f = 0.5  
  > "(2) equipartition ($\epsilon_{\rm e} = \epsilon_{\rm B} = 0.1$), and (3) an emission filling factor, $f=0.5$" (A prompt, non-relativistic outflow)
   - assumption: Fully ionized hydrogen, mu_e = 1  
  > "throughout our analysis we assume a fully ionized hydrogen composition, i.e., $\mu_{\rm e} = 1$" (Analysis and modeling of individual SEDs)
   - assumption: Luminosity distance 200 Mpc  
  > "we adopt a luminosity distance of $200$ Mpc based on a standard" (Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **estimate outflow launch time**: Fit the equipartition radius with a constant-velocity linear function of time since launch, with the radius at Delta t_0 and t_launch free  
  > "To estimate the outflow launch time we fit the equipartition radius with a function of the form" (Delayed, non-relativistic outflows); "which assumes a constant outflow expansion velocity" (Delayed, non-relativistic outflows)
   - software: emcee
   - parameter: Delta t_0 = 131 days (first flare) and 247 days (second flare)  
  > "We set $\Delta t_{\rm 0} \equiv 131$ and $247$ days for the first and second flare, respectively." (Delayed, non-relativistic outflows)
   - fitting: emcee posteriors  
  > "`emcee` is used to estimate the posteriors of the best-fitting parameters." (Delayed, non-relativistic outflows)
   - validation: _not stated_
5. **off-axis relativistic jet equipartition**: Generalise the Matsumoto and Piran (2023) off-axis equipartition formalism to electrons radiating at nu_m and general p, solved numerically for several viewing angles with a requirement nu_m below 1.5 GHz  
  > "We explore the possibility of an off-axis jet model by generalizing the method devised by (cite: Matsumoto_2023)." (Relativistic jets observed off-axis); "Our observations imply $\nu_{\rm m} \lesssim 1.5 \, {\rm GHz} < \nu_{\rm sa}$" (Relativistic jets observed off-axis)
   - parameter: f_A = f_V = 1  
  > "We assume $f_{\rm A} = f_{\rm V} = 1$, which accounts only for energy within $1/\Gamma$ from our line of sight." (Relativistic jets observed off-axis)
   - assumption: epsilon_e = epsilon_B (equipartition)  
  > "Finally, we also assume equipartition, $\epsilon_{\rm e} = \epsilon_{\rm B}$." (Relativistic jets observed off-axis)
   - fitting: _not stated_
   - validation: _not stated_
6. **time-dependent SSA + FFA + IC model of the first flare**: Constant-velocity shock in a single power-law density profile; synchrotron break frequencies computed self-consistently, broken power-law SED, FFA absorption, IC cooling checked against the cooling frequency; fitted to all first-flare radio data up to Delta t = 173 days with t_launch = 84 days  
  > "We fit this model to all of the radio data from the first flare (up to $\Delta t \leq 173$ days) assuming $t_{\rm launch} = 84$ days[^4]." (Multi-epoch time-dependent modeling of the first radio flare)
   - software: emcee
   - parameter: Free parameters beta_0, n_0, k, p, epsilon_B  
  > "The free parameters are $\beta_{\rm 0}$, $n_{\rm 0}$, $k$, $p$, and $\epsilon_{\rm B}$." (Multi-epoch time-dependent modeling of the first radio flare)
   - parameter: Flat priors 0.005 < beta_0 < 0.9, 1 < log10(n_0) < 11, 1 < k < 9  
  > "We use the following flat priors $0.005 < \beta_{\rm 0} < 0.9$, $1 < \log_{10}\left(n_{\rm 0} / \left[ \rm{cm^{-3}} \right]\right) < 11$, $1 < k < 9$," (Multi-epoch time-dependent modeling of the first radio flare)
   - parameter: 200 walkers, 30,000 steps, first 1,000 discarded  
  > "We use $200$ walkers with $30,000$ steps for each chain and discard the first $1,000$ steps for burn-in." (Multi-epoch time-dependent modeling of the first radio flare)
   - assumption: T_e = 1e5 K, f_A = 1, f = 0.5  
  > "We further assume that the temperature of the electrons in the surrounding medium is $T_{\rm e} = 10^5 \, \rm K$, and filling factors of $f_A = 1$, and $f=0.5$." (Multi-epoch time-dependent modeling of the first radio flare)
   - assumption: epsilon_e = 0.001 fixed because of the epsilon_e and epsilon_B degeneracy  
  > "We also assume $\epsilon_{\rm e} = 0.001$ (which is needed for $\epsilon_{\rm B} \leq 0.1$) since there is a degeneracy between $\epsilon_{\rm e}$ and $\epsilon_{\rm B}$." (Multi-epoch time-dependent modeling of the first radio flare)
   - assumption: Gaunt factor 5, Z = 1, fully ionized medium  
  > "we use a Gaunt factor $g_{\rm ff} = 5$, a charge of $Z=1$, and assume full ionization of the medium" (Multi-epoch time-dependent modeling of the first radio flare)
   - fitting: emcee with flat priors  
  > "We use `emcee` to determine the best-fitting parameters and infer their posterior distribution." (Multi-epoch time-dependent modeling of the first radio flare)
   - validation: Fitted synchrotron cooling frequency checked for consistency with the IC cooling frequency from the optical/UV luminosity  
  > "Therefore, we conclude that our model is self-consistent with the location of the IC cooling frequency even though we are not explicitly accounting for it in our fitting process." (Multi-epoch time-dependent modeling of the first radio flare)
7. **model host nucleus emission and subtract it from compact-configuration VLA data**: Fit a power law to VLA A-configuration flux densities of the host nucleus (X band at 88 days, S, C and Ku bands at 160 days) and subtract it from C- and D-configuration TDE fluxes  
  > "We construct an SED of the host galaxy nucleus by taking flux measurements at two different epochs from VLA observations taken in A-configuration" (Emission from the host galaxy nucleus)
   - fitting: _not stated_
   - validation: Correction is below 10% of the flux measurements  
  > "However, we note that this is a minor correction of less than $10\%$ of the flux measurements for these observations." (Emission from the host galaxy nucleus)

## Software

- **CASA** : imfit/imstat flux and rms measurement of ALMA images; tclean imaging and calibration of VLA, AMI-LA and ATA data  
  > "We used the standard National Radio Astronomy Observatory (NRAO) calibrated images, and fitted the point source with CASA task `IMFIT`, and used CASA task `IMSTAT` to obtain the image rms." (Atacama Large Millimeter/submillimeter Array); "We used the CASA task `TCLEAN` to produce clean images of the field of AT 2024tvd." (Karl G. Jansky Very Large Array)
- **emcee** : MCMC fits of SEDs, launch time and the time-dependent model  
  > "We use `emcee` (cite: foreman_mackey_2013) to determine the best-fit parameters and infer their posterior distributions using flat priors." (Analysis and modeling of individual SEDs)
- **astropy** : _not stated_
- **reduce_dc** : Reduction, flagging and calibration of AMI-LA data  
  > "We reduced, flagged, and calibrated our observations using `reduce_dc`, a customized AMI-LA data reduction software package (cite: perrott_2013)." (Arcminute Micro-Kelvin Imaging - Large Array)
- **ATARI pipeline** : Customised CASA-based ATA data reduction  
  > "We used a customized pipeline (<https://github.com/joesbright/ATARI/>) utilizing CASA to reduce the observations" (Allen Telescope Array)
- **SMA COMPASS pipeline** : Calibration and flagging of SMA data  
  > "Analysis of the data was performed using the SMA COMPASS pipeline (G. K. Keating et al, in prep)" (Submillimeter Array)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| First flare rise index F_nu ~ t^alpha at Delta t = 88-131 days | faster than t^9 | lower limit | dimensionless | 0 | the first radio flare rises faster than $F_{\rm \nu} \sim t^{9}$ at $\Delta t = 88-131$ days |
| First flare peak flux and peak frequency decline indices | F_p ~ t^-6 and nu_p ~ t^-5 | not stated | dimensionless | 2 | the radio spectral peak declines as $F_{\rm p} \sim t^{-6}$, and the peak frequency also declines quickly, $\nu_{\rm p} \sim t^{-5}$ |
| Second flare initial rise and optically thin decline indices | F_nu ~ t^18 rise; F_nu ~ t^-12 decline | not stated | dimensionless | 0 | The emergence of a second radio flare is observed at $\Delta t \approx 194$ days with an initial fast rise of $F_{\rm \nu} \sim t^{18}$, and an optically thin decline of $F_{\rm \nu} \sim t ^{-12}$. |
| ALMA first-epoch optically thin spectral slope (Delta t = 139-141 days) | steeper than nu^-1.2 | limit (97.5 GHz detection, 203 GHz upper limit) | dimensionless | 1 | showed an optically thin spectral slope higher than $F_{\rm \nu} \sim \nu^{-1.2}$ (based on the detection at $97.5$ GHz and the upper limit at $203$ GHz) |
| Electron power-law index p | about 2.15 for both flares | not stated | dimensionless | 2 | we observe $p \simeq 2.15$ for both flares |
| Equipartition energy of the first flare at Delta t = 131 days (prompt, non-relativistic) | ~4e48 | not stated | erg | 3 | The initial equipartition energy of the first flare is $\sim 4 \times 10^{48} \, \rm erg$ at $\Delta t = 131$ days |
| Equipartition energy of the second flare at Delta t = 284 days | ~6e49 | not stated | erg | 3 | reaching $\sim 6 \times 10^{49} \, \rm erg$ at $\Delta t = 284$ days |
| Prompt-outflow shock velocity | ~0.06-0.085c | not stated | c | 3 | The shock velocities we infer in this case are $\sim 0.06-0.085c$ |
| Launch time of the first outflow | 84 | +6/-25 | days after optical discovery | 4 | For the first flare the outflow launching time is $t_{\rm launch} = 84^{+6} _{-25}$ days |
| Radius at Delta t_0 = 131 days (first flare) | 2.1e16 | 0.1e16 | cm | 4 | the radius at $\Delta t_{\rm 0} = 131$ days is $\tilde{R} = \left( 2.1 \pm 0.1\right) \times 10^{16} \, \rm cm$ |
| Launch time of the second outflow | 170 | 10 | days after optical discovery | 4 | for the second flare $t_{\rm launch} = 170 \pm 10$ days |
| Minimum off-axis jet launch times | first flare >~ 80 days, second flare >~ 190 days | limit | days | 5 | This approach results in $t_{\rm launch} \gtrsim 80$ days for the first flare, and $t_{\rm launch} \gtrsim 190$ days for the second flare. |
| Density power-law slope of the first-flare time-dependent fit | -3.8 (n proportional to (r/r_0)^-3.8) | 0.1 | dimensionless | 6 | $n \left( r \right) = n_{\rm 0} \left( r/r_{\rm 0} \right)^{-3.8 \pm 0.1}$ |
| Density normalisation n_0 at r_0 | 10^5.2 at r_0 ~ 2.1e16 cm | 0.2 dex | cm^-3 | 6 | We also find $n_{\rm 0} = 10^{5.2 \pm 0.2} \rm \, cm^{-3}$ at $r_{\rm 0} \simeq 2.1 \times 10^{16} \, \rm cm$. |
| log10 epsilon_B (for epsilon_e = 0.001) | -1.9 | 0.3 | dimensionless | 6 | We find $\log_{10} \left( {\epsilon_{\rm B}} \right) = -1.9 \pm 0.3$, implying deviation from equipartition. |
| Synchrotron cooling frequency evolution | from ~50 GHz to >~100 GHz | not stated | GHz | 6 | the synchrotron cooling frequency evolving from $\sim 50$ GHz to $\nu_{\rm c} \gtrsim 100$ GHz at later times |
| Host nucleus SED normalisation and index | A = 64 uJy at 5 GHz, beta = 0.53 | A: 4 uJy; beta: 0.12 | uJy; dimensionless | 7 | with $A = 64 \pm 4\, \rm \mu Jy$, and $\beta = 0.53 \pm 0.12$ |
| Host nucleus star formation rate from 1.4 GHz luminosity | 0.51 | 0.06 | Msun/yr | 7 | we infer an SFR of $0.51 \pm 0.06 \, \rm M_{\rm \odot} \, yr^{-1}$ |

## Qualitative findings

- AT 2024tvd is the first optically selected off-nuclear TDE and the first off-nuclear TDE with bright radio emission  
  > "This paper discusses AT 2024tvd, the first off-nuclear TDE selected from optical sky surveys, which is also the first bonafide off-nuclear TDE with bright radio emission." (Introduction)
- The radio source at the host centre is a low-luminosity AGN, not star formation  
  > "the radio source at the center of the galaxy must be powered by a low-luminosity AGN with a steep radio spectrum, possibly associated with a jet" (Emission from the host galaxy nucleus)

## Claim tuples

- H: Can a prompt outflow launched near optical discovery explain the first radio flare? | E: Equipartition analysis and the time-dependent SSA+FFA+IC model with t_launch = 0 | R: A prompt model needs a post-shock energy of a few 1e52 erg and a very steep density profile n_e ~ r^-6, and the prompt model gives an accelerating shock | F: A prompt non-relativistic outflow is disfavoured; a delayed outflow launched at about 80 days is preferred | **supported**
- H: What is the origin of the second radio flare and is it the same outflow as the first? | E: Equipartition analysis of the second-flare SEDs for non-relativistic and off-axis jet scenarios with different launch times | R: The second flare needs either a density break for the same outflow or a second outflow at 170-190 days; a time-dependent fit was not possible | F: Two scenarios remain: one delayed outflow in a complex density profile, or a second distinct outflow | **partially**
- H: Is the radio evolution of AT 2024tvd faster than that of other radio-bright TDEs? | E: Compare 10 GHz light curves and temporal power-law indices with other TDEs | R: Indices reach t^9 and t^18 on the rise and t^-6 and t^-12 on the decline | F: AT 2024tvd shows the fastest radio evolution seen in a TDE | **supported**
- H: Is the radio outflow launch connected to the X-ray accretion state? | E: Compare the inferred launch time with the onset of a Comptonization component in X-ray spectra from earlier work | R: The Comptonization onset at about 80 days coincides with the inferred launch time | F: The first flare may come from an accretion-driven outflow; this is speculative | **partially**
- H: Is the unusual radio evolution related to the off-nuclear position of the black hole? | E: Qualitative discussion of density-profile breaks, stagnation radius and IMBH scenarios | R: No test is performed; both a connection and no connection are allowed | F: A link is raised as a possibility only | **partially**

## Reasoning

- Why this data: Radio detection with the VLA triggered a broadband multi-epoch campaign; mm-band data are needed to constrain the launch date and the cooling break  
  > "Following this detection, we initiated a broadband, multi-epoch campaign, using the VLA, Atacama Large Millimeter/submillimeter Array (ALMA)," (Radio observations); "early observations in the mm-bands are sometimes the only way to constrain the outflow launch date as an absorbed emission is expected to first peak in those bands." (Summary and conclusions)
- Why this method: Individual-SED equipartition analysis is complemented by a time-dependent model because the former ignores outflow dynamics  
  > "it does not take into account the dynamics of the outflow" (Detailed modeling of the radio emission)
- Alternative: Prompt non-relativistic outflow rejected for the first flare because of extreme energy and density  
  > "Based on this analysis, we conclude that the origin of the first flare is unlikely to be related to a prompt, non-relativistic outflow." (Prompt sub-relativistic outflow fit)
- Alternative: Prompt off-axis jet rejected  
  > "Therefore, we find that a prompt off-axis jet is an unlikely scenario." (The nature of the first radio flare); "Therefore, we conclude that an off-axis relativistic jet launched around the time of optical discovery is disfavored." (Relativistic jets observed off-axis)
- How they decided it was enough: Time-dependent modelling of the second flare was not done because more epochs are needed  
  > "However, more epochs of observations are needed to constrain the evolution of the optically thin regime." (Multi-epoch time-dependent modeling of the first radio flare)
- Limitation (authors): Second flare is not modelled beyond equipartition  
  > "We leave the modeling of the second radio flare beyond equipartition for future work." (Multi-epoch time-dependent modeling of the first radio flare)
- Limitation (authors): ALMA flux at Delta t = 227 days is too high relative to low-GHz data and cannot be accounted for  
  > "We note that the high-GHz emission observed with ALMA at $\Delta t = 227$ days is too high compared to the emission in low-GHz, and we cannot account for it in our equipartition analysis." (The nature of the second radio flare)
- Limitation (authors): ATA fluxes are contaminated by background due to the large beam  
  > "The flux density measured by the ATA is contaminated by the background due to the large beam of the ATA." (Allen Telescope Array)
- Limitation (authors): Model degeneracies between relativistic and non-relativistic outflows remain  
  > "In order to break some of the model degeneracies and determine if the radio emitting outflows are relativistic or non-relativistic, high-resolution, Very Long Baseline Interferometry (VLBI) observations are required" (Summary and conclusions)
- Caveat (inferred, ours): ALMA plays a small role: only a few flux densities are extracted from NRAO calibrated images, with no stated flux-scale error or imaging parameters
- Caveat (inferred, ours): Key conclusions rest on fits to SEDs with few points; p is fixed in most epochs
- Caveat (inferred, ours): Launch time depends on a constant-velocity assumption while the density slope k > 3 implies acceleration (admitted in a footnote)
- Caveat (inferred, ours): epsilon_e is fixed at 0.001 because of a degeneracy, so epsilon_B and energetics depend on that choice
- Caveat (inferred, ours): Optical/UV luminosity for the IC cooling comes from an unpublished paper

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: Standard NRAO calibrated images were used, implying archive-standard products  
  > "We used the standard National Radio Astronomy Observatory (NRAO) calibrated images" (Atacama Large Millimeter/submillimeter Array)
- Code: Code to calculate synchrotron SEDs is released on GitHub (Itaisfa/full_synchrotron_SED)  
  > "we provide the code used to calculate the synchrotron SEDs based on this method at <https://github.com/Itaisfa/full_synchrotron_SED/tree/main>" (Synchrotron self-absorption frequency in the slow-cooling regime)
- Code: ATA reduction pipeline ATARI is public on GitHub  
  > "We used a customized pipeline (<https://github.com/joesbright/ATARI/>) utilizing CASA to reduce the observations" (Allen Telescope Array)
- Missing: Machine-readable full flux table is online only; the text table lists a subset
- Missing: ALMA epoch dates, configurations, imfit settings and flux errors are not given
- Missing: Multi-facility data (VLA, ATA, AMI-LA, SMA) need separate reduction and are partly unpublished pipelines
- Missing: Optical/UV luminosity from an unpublished paper
- Missing: emcee seeds and convergence criteria not given; time-dependent code not clearly released
- Data volume (inferred): Small for the ALMA part (four Band 3/5 DDT epochs, likely a few GB of products); the full reproduction also needs VLA, ATA, AMI-LA and SMA data
- Score (inferred): 2/5, ALMA measurements are a few flux densities from standard NRAO products, but the modelling needs other facilities' data, a table available only online, and unpublished inputs
- Rediscovery candidate: no, ALMA is a minor part, the public status of the DDT data is not stated, and the modelling relies on multi-facility data and unpublished inputs

## Links

- Method: Chevalier 1998 (cite: chevalier_1998) (Newtonian equipartition formalism for radius and magnetic field)
- Method: Granot & Sari 2002 (cite: granot_2002) (Broken power-law spectral shapes and smoothing parameter)
- Method: Matsumoto & Piran 2023 (cite: Matsumoto_2023) (Off-axis equipartition formalism generalised here)
- Method: Barniol Duran, Nakar & Piran 2013 (cite: BDNP13) (Relativistic equipartition analysis)
- Method: Nayana et al. 2025 (cite: Nayana_2024) (FFA and IC cooling treatment)
- Companion: Yao et al. 2025b (cite: Yao_2025) (Optical, UV and X-ray analysis and off-nuclear position of AT 2024tvd)
- Companion: Sfaradi et al. 2024 (cite: Sfaradi_2024) (Off-axis jet interpretation of AT 2018hyz radio evolution)
- Related: VLA 24A-386
- Related: VLA 25A-483
- Related: ATA P062
- Related: SMA POETS 2022B-S046

## Checks

```json
{
 "quotes": 103,
 "quotes_ok": 103,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 18,
 "numeric_problems": 0,
 "fill": {
  "facts": 109,
  "stated": 69,
  "rate": 0.633
 },
 "evidence_ok": true
}
```
