# A Millimeter Rebrightening in GRB 210702A

`2024ApJ...974..279D` | The Astrophysical Journal 2024 | first author: de Wet, Simon | arXiv: 2408.14641 | DOI: 10.3847/1538-4357/ad77bb

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: transients
- Question: Why does the ALMA 97.5 GHz afterglow light curve of GRB 210702A rebrighten, and can a standard forward shock model explain the multi-wavelength data?  
  > "We investigate possible explanations for the millimeter rebrightening and find that energy injection or a reverse shock from a late-time shell collision are plausible causes." (abstract); "A standard forward shock model in a stellar wind circumburst medium can explain most of our X-ray, optical and millimeter observations prior to the rebrightening" (abstract)
- Target **GRB 210702A**: coordinates RA 11h14m18.70s, Dec -36d44m50.0s (J2000), optical afterglow position from UVOT  
  > "identified at coordinates $\alpha=11^\mathrm{h}14^\mathrm{m}18.70^\mathrm{s}$, $\delta = -36^\circ 44^{\prime}50.0^{\prime\prime}$ (J2000) with an uncertainty of $0.42^{\prime\prime}$" (2.2 UV/Optical); "The burst redshift of $z=1.160$ (cite: 30357) corresponds to a luminosity distance of $D_L=2.53\times10^{28}$ cm" (2.1 Prompt emission); z/distance z = 1.160; D_L = 2.53e28 cm  
  > "identified at coordinates $\alpha=11^\mathrm{h}14^\mathrm{m}18.70^\mathrm{s}$, $\delta = -36^\circ 44^{\prime}50.0^{\prime\prime}$ (J2000) with an uncertainty of $0.42^{\prime\prime}$" (2.2 UV/Optical); "The burst redshift of $z=1.160$ (cite: 30357) corresponds to a luminosity distance of $D_L=2.53\times10^{28}$ cm" (2.1 Prompt emission); distance from Redshift from GCN Circular (cite: 30357); luminosity distance computed with Planck2020 cosmology  
  > "identified at coordinates $\alpha=11^\mathrm{h}14^\mathrm{m}18.70^\mathrm{s}$, $\delta = -36^\circ 44^{\prime}50.0^{\prime\prime}$ (J2000) with an uncertainty of $0.42^{\prime\prime}$" (2.2 UV/Optical); "The burst redshift of $z=1.160$ (cite: 30357) corresponds to a luminosity distance of $D_L=2.53\times10^{28}$ cm" (2.1 Prompt emission)

## Data provenance

- ALMA projects: 2019.1.01484.T, 2019.1.01032.T
- bands: Band 3 (97.5 GHz): nine epochs; Band 7 (343.5 GHz): three epochs  
  > "We obtained nine epochs of observations with the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 3 (97.5 GHz) and three epochs of observations in Band 7 (343.5 GHz)" (2.4.1 ALMA)
- frequencies and spectral setup: Two 4 GHz base-bands centred on 91.5 and 103.5 GHz (Band 3) and 337.5 and 349.5 GHz (Band 7)  
  > "The Band 3 and Band 7 observations both employed two 4 GHz base-bands centred on 91.5 and 103.5 GHz, and 337.5 and 349.5 GHz, respectively." (2.4.1 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: First ALMA detections at 1.17 days (97.5 GHz) and 1.06 days (343.5 GHz) post-trigger; 97.5 GHz rebrightening begins 8.2 days, peaks 18.1 days  
  > "At the time of the first ALMA 97.5 GHz detection at 1.17 days, we measure" (3.3 Stellar wind medium); "to the time of the first 343.5 GHz detection at 1.06 days" (3.3 Stellar wind medium)
- pi or archival as stated: Programs with PI Laskar (2019.1.01484.T) and PI Perley (2019.1.01032.T); pipeline images downloaded from the ALMA archive  
  > "through programs 2019.1.01484.T (PI Laskar) and 2019.1.01032.T (PI Perley)" (2.4.1 ALMA); "We downloaded the pipeline-generated images from the ALMA archive" (2.4.1 ALMA)
- Other facility **Swift/BAT**: Trigger, T90 and prompt gamma-ray light curve  
  > "Refined BAT analysis indicated that the $\gamma$-ray mask-weighted light curve showed a single-peaked fast rise exponential decay-like structure" (2.1 Prompt emission)
- Other facility **Swift/XRT**: X-ray light curve and spectra (WT and PC modes)  
  > "We downloaded the X-ray count-rate light curve and time-averaged WT and PC spectra from the online" (2.2 X-ray)
- Other facility **Swift/UVOT**: UV/optical photometry out to 8.08 days  
  > "Observations continued intermittently in all filters until 8.08 days post-trigger." (2.3 UV/Optical)
- Other facility **MeerLICHT**: Early optical photometry in q, u, g, r, i, z filters  
  > "Observations consisted of 60 s exposures in six optical filters following the filter sequence" (2.3 UV/Optical)
- Other facility **ATCA**: Seven epochs at 5.5, 9, 16.7, 21.2, 33 and 35 GHz  
  > "We observed GRB 210702A at seven epochs with the Australia Telescope Compact Array (ATCA) beginning at 3.50 days post-trigger." (2.4.2 ATCA)
- Other facility **MeerKAT**: L band (1.28 GHz), five epochs, 0.65 hr on source per epoch  
  > "We observed the radio afterglow with the MeerKAT radio telescope in the L band (1.28 GHz) at five epochs" (2.4.3 MeerKAT)
- Other facility **GMRT**: Band 4 (700 MHz), five epochs from 8.6 days  
  > "Observations were carried out in Band 4 (700 MHz) with a 400 MHz bandwidth" (2.4.4 GMRT)
- External data: Early ATCA radio fluxes at t<1 day (average of 3 sigma fluxes per band from Table A1) used as one flux per band at about 0.53 days  
  > "we take the average of the $3\sigma$ fluxes per observing band from their Table A1" (2.4.2 ATCA) [from Anderson2023 (cite: Anderson2023)]
- External data: Saturated UVOT u-band AB magnitude u=12.34+-0.18 mag  
  > "we adopt the AB magnitude measurement of $u=12.34\pm0.18$ mag calculated by (cite: Zhou2023)" (2.3 UV/Optical) [from Zhou2023 (cite: Zhou2023)]
- External data: Burst redshift z=1.160  
  > "The burst redshift of $z=1.160$ (cite: 30357)" (2.1 Prompt emission) [from GCN Circular (cite: 30357)]
- External data: Galactic hydrogen column density 1.19e21 cm^-2  
  > "The Galactic column density was fixed at $N_\mathrm{H,Gal}=1.19\times10^{21}$ cm$^{-2}$ (cite: Willingale2013)" (2.2 X-ray) [from Willingale2013 (cite: Willingale2013)]
- External data: Optical photometry from GCN Circulars (VLT/X-Shooter at 0.18 d, Chilescope at 0.19 d)  
  > "We additionally make use of optical photometry made public through Gamma-Ray Coordinates Network (GCN) Circulars" (2.3 UV/Optical) [from (cite: 30357); (cite: 30365)]
- External data: Galactic extinction A_V=0.3271 mag along the line of sight  
  > "for a Galactic extinction of $A_V=0.3271$ mag along the line of sight (cite: SF2011)" (3.3 Stellar wind medium) [from SF2011 (cite: SF2011)]
- External data: ISS transition frequency 7.66 GHz and scattering measure 1.06e-3 kpc m^-20/3  
  > "Using the ISS transition frequency ($\nu_0=7.66$ GHz)" (6.2 Failure of forward shock model) [from Anderson2023 (cite: Anderson2023), derived using RISS19 (cite: Goodman1997; Hancock2019)]
- Simulation/model as data: ScaleFit afterglow models (based on BoxFit hydrodynamic simulations) fitted to the data  
  > "which is based on the `BoxFit` set of high-resolution hydrodynamic simulations of GRB explosions" (4 Afterglow modelling with ScaleFit)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALMA pipeline-generated images downloaded from the archive; fluxes measured with CASA imfit  
  > "We downloaded the pipeline-generated images from the ALMA archive" (2.4.1 ALMA)
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

- MCMC implementation with emcee  
  > "following the implementation described in detail in (cite: deWet2023b)" (4 Afterglow modelling with ScaleFit) [from (cite: deWet2023b)]
- Equations for spectral break locations and flux densities in a wind medium  
  > "(see Table 2 in (cite: Granot2002))" (4 Afterglow modelling with ScaleFit) [from (cite: Granot2002)]
- Closure relations for energy injection in the q-formalism  
  > "making use of the closure relations for energy injection within the $q$-formalism from (cite: Zhang2006)" (5.5 Energy injection) [from (cite: Zhang2006)]
- Synchrotron forward shock model description  
  > "The synchrotron forward shock model is described in detail in (cite: Sari1998) and (cite: Granot2002)." (3 Multi-wavelength modelling) [from (cite: Sari1998); (cite: Granot2002)]
- Light curve fitting form of the smoothly broken power law  
  > "we fit the light curve with a smoothly broken power-law following Equation" (3.2 X-ray and UV/optical temporal evolution) [from Equation (BPL) in this paper]

### Not stated but needed to reproduce (our reading)

- ALMA flux calibrator, calibration pipeline/CASA version and imaging parameters (the images are archive products, but their CASA pipeline version and weighting are not given)
- Region or fit settings used with CASA imfit for the ALMA point-source flux (box, initial guess, fixed beam)
- Per-epoch ALMA flux values: the main flux table is only partly printed, the full table is machine-readable only
- Priors, likelihood, walker number and burn-in for the emcee/ScaleFit MCMC
- Initial guesses and fitting method for the PL+BPL light curve fit (software, fit range)
- Which data points entered the ScaleFit fit besides those listed as excluded, and how upper limits were treated
- ALMA flux scale uncertainty adopted
- Exact times (days post-trigger) and durations of each ALMA epoch

## Analysis recipe

1. **measure ALMA fluxes**: Download pipeline-generated archive images and fit a source model in the image plane  
  > "We downloaded the pipeline-generated images from the ALMA archive and measured the source flux using the Common Astronomy Software Application" (2.4.1 ALMA)
   - software: CASA
   - parameter: imfit task used for flux  
  > "measured the source flux using the Common Astronomy Software Application (cite: McMullin2007) `imfit` task" (2.4.1 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **fit the 97.5 GHz light curve**: Fit a sum of a power law and a smoothly broken power law to the ALMA 97.5 GHz light curve; fit rise and decay segments directly  
  > "we fit a model comprising the sum of a power-law (PL) and a smoothly broken power-law (BPL)" (3.1 The millimeter rebrightening)
   - parameter: smoothness omega = 1 gives a better fit than sharper breaks  
  > "For the broken power-law component we find that a smoother break with $\omega=1$ results in a better fit than sharper breaks." (3.1 The millimeter rebrightening)
   - fitting: _not stated_
   - validation: Compared with direct fits to the rising and decaying segments  
  > "direct fits to the rising and decaying segments (Figure [1](#fig:ALMA_LC)) result in" (3.1 The millimeter rebrightening)
3. **measure X-ray and optical temporal and spectral indices**: Power-law fits to MeerLICHT, UVOT and XRT light curves, smoothly broken power-law to a composite b-band light curve, X-ray spectral fits  
  > "Fitting the MeerLICHT and *Swift* UV/optical data separately with power-laws in time" (3.2 X-ray and UV/optical temporal evolution)
   - software: Xspec
   - parameter: composite b-band light curve built with spectral index beta=-1.44  
  > "using a spectral index of $\beta=-1.44$, the average spectral index from our spectral fits to the MeerLICHT and UVOT data" (3.2 X-ray and UV/optical temporal evolution)
   - assumption: Galactic and host absorption with fixed Galactic NH and z=1.160 in the X-ray spectral fits  
  > "taking into account Galactic and host galaxy absorption" (2.2 X-ray)
   - fitting: _not stated_
   - validation: Residuals from the MeerLICHT power-law fit checked against the fitted break time  
  > "which is consistent with the evidence for a break seen in our residuals from the power-law fit to the MeerLICHT data" (3.2 X-ray and UV/optical temporal evolution)
4. **test forward shock regimes with closure relations**: Compare observed temporal and spectral indices with predicted closure relations for ISM and wind media to derive p and select the medium  
  > "For the stellar wind case we derive $p=2.24\pm0.01$ from our observed light curve evolution" (3.3 Stellar wind medium)
   - assumption: Slow cooling regime with nu_m < nu_c  
  > "During slow-cooling ($\nu_m<\nu_c$) there are two spectral regimes to consider" (3.3 Stellar wind medium)
   - fitting: _not stated_
   - validation: Predicted optical spectral index compared with measured beta_O = -0.63+-0.08; ISM ruled out via peak flux argument  
  > "which is more than an order of magnitude larger than our constraint on the peak flux from our millimeter data at 1.17 days and therefore clearly rules out an ISM medium" (3.3 Stellar wind medium)
5. **build radio SEDs and constrain self-absorption**: Extract SEDs at seven epochs, interpolating early ATCA light curves with power laws, and measure spectral indices to constrain nu_a  
  > "We have extracted SEDs at seven epochs indicated by the vertical grey regions" (3.4 Radio evolution)
   - assumption: The rebrightening does not significantly affect light curves and SEDs before 8.2 days  
  > "Prior to the start of the rebrightening at 8.2 days we assume that the rebrightening does not have a significant effect on the light curves nor SEDs." (3.4 Radio evolution)
   - fitting: _not stated_
   - validation: _not stated_
6. **fit forward shock model to multi-wavelength data**: MCMC exploration of ScaleFit parameter space with data excluded where the model is not expected to apply  
  > "We conduct a Markov Chain Monte Carlo (MCMC) exploration of our `ScaleFit` parameter space using the `emcee` Python package" (4 Afterglow modelling with ScaleFit)
   - software: ScaleFit, emcee
   - parameter: z fixed to 1.160 and d_L = 2.52e28 cm  
  > "We fix the burst redshift to $z=1.160$ and the luminosity distance to the value computed using our adopted cosmology, $d_L=2.52\times10^{28}$ cm." (4 Afterglow modelling with ScaleFit)
   - parameter: Excluded: uvw2 data, radio data after 8.2 days, X-ray t<0.01 d, first ATCA epoch, radio <16.7 GHz at 6.6 d  
  > "We therefore exclude these data from our modelling, along with the radio observations following the start of the 97.5 GHz rebrightening at 8.2 days." (4 Afterglow modelling with ScaleFit)
   - assumption: theta_obs = 0 and xi_N = 1  
  > "We assume that the observer is looking directly down the axis of the jet ($\theta_\mathrm{obs}=0$) and that the fraction of shock-accelerated electrons is unity" (4 Afterglow modelling with ScaleFit)
   - assumption: Spherical jet (theta = pi/2)  
  > "We assume a spherical jet ($\theta=\pi/2$) since our observations show no clear evidence for a jet break." (4 Afterglow modelling with ScaleFit)
   - assumption: Milky Way extinction (Fitzpatrick 1999, R_V=3.1, A_V=0.3271) and SMC host extinction curve (Pei 1992) with free A_V,host  
  > "we adopt the Small Magellanic Cloud (SMC) extinction curve from (cite: Pei1992) to account for possible host galaxy extinction, which is a free parameter in our modelling" (4 Afterglow modelling with ScaleFit)
   - assumption: LCDM cosmology Omega_m=0.315, H0=67.4  
  > "We adopt a $\Lambda$CDM cosmology with $\Omega_m=0.315$ and $H_0=67.4$ km s$^{-1}$ Mpc$^{-1}$ (cite: Planck2020)." (1 Introduction)
   - fitting: emcee MCMC; priors and likelihood not stated  
  > "following the implementation described in detail in (cite: deWet2023b)" (4 Afterglow modelling with ScaleFit)
   - validation: Highest-likelihood model compared with optical, X-ray and radio SEDs; radio SEDs found incompatible with the model  
  > "As we expected, the optically thick spectra observed in the Epoch 1 and 3 radio SEDs are incompatible with our highest-likelihood model" (4 Afterglow modelling with ScaleFit)
7. **derive jet opening angle lower limit and efficiency**: Invert Chevalier and Li (2000) Equation 5 with no jet break before 8.2 days to get a lower limit on theta_j, then beaming correction and radiative efficiency  
  > "we can place a lower limit on the opening angle using the inverted form of Equation 5 from (cite: Chevalier2000)" (4 Afterglow modelling with ScaleFit)
   - assumption: Wind medium with E_K,iso from the ScaleFit model; jet break time t_j >= 8.2 days  
  > "No jet break is seen in our data prior to the start of the millimeter rebrightening at 8.2 days" (4 Afterglow modelling with ScaleFit)
   - fitting: _not stated_
   - validation: Compared with sample range of theta_j from Wang et al. 2015  
  > "which is consistent with the sample range of $\theta_j=2.5\pm1.5$ degrees found by (cite: Wang2015)" (4 Afterglow modelling with ScaleFit)
8. **test explanations for the rebrightening**: Test energy injection (closure relation for q, kinetic energy rising as t^(1-q) between 8.2 and 18.1 days) and a reverse shock from a shell collision against higher frequency radio data; rule out other scenarios by argument  
  > "we introduce a period of energy injection in which the kinetic energy of the blast wave increases as $t^{1-q}$ between 8.2 and 18.1 days" (5.5 Energy injection)
   - parameter: Other forward shock parameters kept fixed; lower frequency radio bands excluded  
  > "We keep all other forward shock parameters the same." (5.5 Energy injection)
   - assumption: For the shell collision, collision time = start of rise (8.2 d), deceleration time = peak (18.1 d)  
  > "We choose to associate the collision time with the beginning of the rise in the 97.5 GHz light curve at 8.2 days, and the deceleration time with the peak in the light curve at 18.1 days." (5.6 Reverse shock)
   - fitting: _not stated_
   - validation: Models compared by eye with higher frequency radio bands; neither captures the other radio bands  
  > "The model can adequately capture the 97.5 GHz rebrightening, but does not fully capture the behaviour in the higher frequency bands" (5.5 Energy injection)

## Software

- **CASA** : ALMA flux measurement with imfit; ATCA imaging (tclean) and UV-fitting (uvmodelfit); GMRT calibration; MeerKAT flux with imfit  
  > "measured the source flux using the Common Astronomy Software Application (cite: McMullin2007) `imfit` task" (2.4.1 ALMA); "UV-fitting the calibrated measurement sets with a point source model with the CASA `uvmodelfit` task" (2.4.2 ATCA)
- **MIRIAD** : ATCA calibration  
  > "We used the `MIRIAD` software package" (2.4.2 ATCA)
- **Xspec** 12.13.0: X-ray spectral fits with an absorbed power law  
  > "We fitted the WT and PC mode spectra in Xspec version 12.13.0 with a photoelectrically absorbed power-law model" (2.2 X-ray)
- **HEASoft (uvotproduct)** 6.31.1: UVOT magnitude extraction  
  > "FTOOLS software package, version 6.31.1" (2.3 UV/Optical)
- **oxkat** : MeerKAT flagging, calibration and imaging  
  > "We flagged, calibrated and imaged the data using the `oxkat` pipeline" (2.4.3 MeerKAT)
- **processMeerKAT** : GMRT imaging and self-calibration  
  > "to perform imaging and two rounds of phase self-calibration followed by one round of amplitude and phase self-calibration" (2.4.4 GMRT)
- **ScaleFit** : Forward shock afterglow spectra and light curves for theoretical modelling  
  > "We perform theoretical modelling using the `ScaleFit` software package" (4 Afterglow modelling with ScaleFit)
- **emcee** : MCMC exploration of ScaleFit parameter space  
  > "using the `emcee` Python package" (4 Afterglow modelling with ScaleFit)
- **RISS19** : ISS transition frequency and scattering measure (used by Anderson et al. 2023)  
  > "derived using RISS19" (6.2 Failure of forward shock model)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 97.5 GHz power-law decay index | -1.03 | 0.02 | dimensionless | 2 | the power-law component decays with $\alpha_\mathrm{97.5~GHz}=-1.03\pm0.02$ |
| BPL rising index alpha_1 | 3.04 | 0.78 | dimensionless | 2 | The rising and decaying indices for this component are $\alpha_1=3.04\pm0.78$ and $\alpha_2=-3.41\pm1.60$ |
| BPL decaying index alpha_2 | -3.41 | 1.60 | dimensionless | 2 | The rising and decaying indices for this component are $\alpha_1=3.04\pm0.78$ and $\alpha_2=-3.41\pm1.60$ |
| BPL break time t_b | 19.5 | 4.3 | days | 2 | with a break time of $t_b=19.5\pm4.3$ days |
| 97.5 GHz rise index (direct fit) | 0.95 | not stated | dimensionless | 2 | result in $\alpha_\mathrm{97.5GHz,rise}=0.95$ and $\alpha_\mathrm{97.5GHz,decay}=-1.67\pm0.17$ |
| 97.5 GHz decay index (direct fit) | -1.67 | 0.17 | dimensionless | 2 | result in $\alpha_\mathrm{97.5GHz,rise}=0.95$ and $\alpha_\mathrm{97.5GHz,decay}=-1.67\pm0.17$ |
| 343.5 GHz decay index | -1.31 | not stated | dimensionless | 2 | while the 343.5 GHz light curve decays with $\alpha=-1.31$ |
| Electron index p from wind-medium closure relations | 2.24 | 0.01 | dimensionless | 4 | For the stellar wind case we derive $p=2.24\pm0.01$ from our observed light curve evolution |
| Spectral index 5.5 to 97.5 GHz at Epoch 1 | 0.93 | 0.06 | dimensionless | 5 | with a spectral index of $\beta_\mathrm{5.5-97.5GHz}=0.93\pm0.06$ |
| ScaleFit MCMC electron index p | 2.28 | +0.01/-0.01 | dimensionless | 6 | $2.28^{+0.01}_{-0.01}$ |
| Isotropic kinetic energy E_K,iso | 30.7 | +4.5/-3.1 | 1e53 erg | 6 | $30.7^{+4.5}_{-3.1}$ |
| Wind density parameter A_star | 4.7e-3 | +1.6/-2.1 (e-3) | dimensionless | 6 | $4.7^{+1.6}_{-2.1}\times10^{-3}$ |
| epsilon_e | 8.7e-3 | +1.3/-2.1 (e-3) | dimensionless | 6 | $8.7^{+1.3}_{-2.1}\times10^{-3}$ |
| epsilon_B | 2.4e-1 | +3.7/-1.0 (e-1) | dimensionless | 6 | $2.4^{+3.7}_{-1.0}\times10^{-1}$ |
| Host extinction A_V,host | 0.011 | +0.010/-0.007 | mag | 6 | $0.011^{+0.010}_{-0.007}$ |
| Jet opening angle lower limit | >~1.1 | not stated | deg | 7 | We calculate a lower limit of $\theta_j\gtrsim1.1$ deg |
| Radiative efficiency | 24.6 | not stated | percent | 7 | find $\eta_\gamma = 24.6$% |
| Isotropic gamma-ray energy | 9.3e53 | 0.7e53 | erg | 0 | from which we calculate a burst isotropic $\gamma$-ray energy of $E_{\gamma,\mathrm{iso}}=(9.3\pm0.7)\times10^{53}$ erg |
| Energy injection index q | -1.88 | not stated | dimensionless | 8 | we calculate a value of $q=-1.88$ |
| Blast wave energy increase during the rebrightening | about 10 | not stated | dimensionless | 8 | We find that the blast wave energy increases by a factor of $\approx10$ over the course of the rebrightening. |
| ISS modulation index at 97.5 GHz | <~2.5 | not stated | percent | 0 | $m\lesssim2.5\%$ at 97.5 GHz |

## Qualitative findings

- The 97.5 GHz light curve rebrightens by a factor of about 2, the first such rebrightening seen in a millimeter afterglow light curve  
  > "is, to our knowledge, the first such rebrightening seen in a millimeter afterglow light curve" (3.1 The millimeter rebrightening)
- The radio SEDs show self-absorbed emission that no standard forward shock model can reconcile  
  > "demonstrates that the optically-thick radio data cannot be reconciled within any standard forward shock model" (3.4 Radio evolution)
- Radio light curves do not evolve achromatically with the millimeter rebrightening  
  > "Throughout the millimeter rebrightening, our radio light curves do not show obviously achromatic behaviour." (3.4 Radio evolution)

## Claim tuples

- H: Does the ALMA millimeter afterglow show a rebrightening that is intrinsic to the source? | E: Nine ALMA Band 3 epochs fitted with power law plus smoothly broken power law; ISS modulation index estimated | R: Rebrightening by a factor of about 2 from 8.2 to a peak at 18.1 days; ISS modulation m<~2.5% at 97.5 GHz | F: The millimeter rebrightening is real and intrinsic, not scintillation | **supported**
- H: Can a standard forward shock model in a wind medium explain the X-ray, optical and early millimeter data? | E: Closure relations plus ScaleFit MCMC fit with excluded data | R: Wind medium with p about 2.27 fits optical, late X-ray and pre-rebrightening millimeter data; early X-ray and low-frequency radio are not fit | F: A standard wind-medium forward shock explains most data except early X-ray and optically thick low-frequency radio | **partially**
- H: Do low-frequency radio self-absorption constraints agree with a standard forward shock? | E: Radio SEDs at seven epochs and ScaleFit prediction of nu_a | R: Observed nu_a about 97.5 GHz at 1.17 days and about 16.7 GHz at 6.6 days versus model nu_a about 110 MHz at 6.6 days; solving break equations gives epsilon_e > 1 | F: No standard forward shock model accommodates the observed self-absorption frequencies | **refuted**
- H: What causes the millimeter rebrightening? | E: Tested supernova, counter jet, density enhancement, ISS, two-component jet, energy injection and reverse shock | R: Energy injection and a late-time shell-collision reverse shock both fit the 97.5 GHz rebrightening but not all other radio bands; the others are disfavoured | F: Energy injection or a reverse shock from a shell collision are plausible but not conclusively distinguished | **partially**

## Reasoning

- Why this data: Millimeter observations are mostly free of scintillation so features must be intrinsic to the source  
  > "millimeter observations are usually not subject to scintillation and therefore any observed light curve feature must be intrinsic to the source" (1 Introduction)
- Why this method: Forward shock model ScaleFit chosen to test standard afterglow physics and derive blast wave parameters  
  > "may also be used to test whether a standard forward shock model is compatible with our data" (4 Afterglow modelling with ScaleFit)
- Alternative: Supernova emission ruled out (peak decades after explosion; mm luminosities far fainter)  
  > "We therefore rule out supernova emission as a possible cause for the rebrightening in GRB 210702A." (5.1 Supernova emission)
- Alternative: Counter jet ruled out (no jet break observed)  
  > "The lack of a jet break observed in our data therefore rules out a counter jet as a viable explanation." (5.2 Counter jet)
- Alternative: Interstellar scintillation ruled out at millimeter  
  > "We rule out ISS as a viable explanation for the millimeter rebrightening." (5.4 Interstellar scintillation)
- Alternative: Standard reverse shock ruled out (would outshine optical emission at 0.004 days)  
  > "ruling out a standard RS scenario" (5.6 Reverse shock)
- Alternative: Two-component jet disfavoured (no jet break in X-ray light curve)  
  > "No jet break is seen in our X-ray light curve, so this model appears to be disfavoured." (5.5 Two-component jet)
- Alternative: ISM circumburst medium ruled out in favour of a wind medium  
  > "therefore clearly rules out an ISM medium" (3.3 Stellar wind medium)
- How they decided it was enough: _not stated_
- Limitation (authors): Higher-frequency ATCA data at epoch three were dropped, losing temporal information  
  > "leads to a loss of possibly valuable temporal information" (3.4 Radio evolution)
- Limitation (authors): Possible unaccounted systematic uncertainties in ATCA calibration prevent excluding energy injection  
  > "possible unaccounted-for systematic uncertainties from the calibration of our ATCA data prevents us from completely excluding this scenario" (5.5 Energy injection)
- Limitation (authors): Reverse shock model is not unique; two break frequencies unconstrained  
  > "this is not a unique model since two of the break frequencies" (5.6 Reverse shock)
- Caveat (inferred, ours): ALMA processing (pipeline version, imfit settings, flux scale) is not documented, so the key mm light curve cannot be regenerated exactly from the text
- Caveat (inferred, ours): Rebrightening interpretation rests on only nine Band 3 epochs and an ad hoc PL+BPL fit with large uncertainties on the broken power-law indices
- Caveat (inferred, ours): No priors or likelihood given for the MCMC; forward shock fit excludes data that disagree, so the failure of the model is partly built in
- Caveat (inferred, ours): Energy injection and reverse shock models are not fitted jointly with the lower frequency radio data and neither is statistically compared

## Reproducibility

- Data public (paper): ALMA pipeline images downloaded from the archive; Swift data from public archives; full flux table machine-readable  
  > "We downloaded the pipeline-generated images from the ALMA archive" (2.4.1 ALMA); "is published in its entirety in the machine-readable format" (Table 3 notes)
- Products in archive: ALMA pipeline-generated images  
  > "We downloaded the pipeline-generated images from the ALMA archive" (2.4.1 ALMA)
- Missing: ALMA flux values per epoch beyond the printed excerpt (machine-readable table only)
- Missing: imfit regions and settings
- Missing: MCMC priors, likelihood and sampler configuration
- Missing: ScaleFit version and access
- Data volume (inferred): Small: pipeline-generated ALMA images for 12 epochs (a few GB or less) plus public Swift and radio data
- Score (inferred): 3/5, ALMA data come from public archive pipeline images and key numbers are given, but ALMA flux extraction details, MCMC priors and the data selection for ScaleFit are incompletely specified.
- Rediscovery candidate: no, ALMA part is simple but the main results depend on multi-facility data and modelling choices (ScaleFit, priors) not fully specified.

## Links

- Method: deWet2023b (cite: deWet2023b) (emcee implementation used for MCMC)
- Method: Aksulu2022 (cite: Aksulu2022); Ryan2015 (cite: Ryan2015) (ScaleFit afterglow modelling code)
- Method: Heywood2020 (cite: Heywood2020) (oxkat MeerKAT pipeline)
- Companion: Anderson2023 (cite: Anderson2023) (Early ATCA radio observations and ISS analysis of the same burst)
- Companion: Schroeder2023 (cite: Schroeder2023) (Similar radio rebrightening in GRB 210726A)
- Related: 2019.1.01484.T
- Related: 2019.1.01032.T

## Checks

```json
{
 "quotes": 122,
 "quotes_ok": 122,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 21,
 "numeric_problems": 0,
 "fill": {
  "facts": 123,
  "stated": 84,
  "rate": 0.683
 },
 "evidence_ok": true
}
```
