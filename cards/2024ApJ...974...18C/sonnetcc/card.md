# The Peculiar Radio Evolution of the Tidal Disruption Event ASASSN-19bt

`2024ApJ...974...18C` | The Astrophysical Journal 2024 | first author: Christy, Collin T. | arXiv: 2404.12431 | DOI: 10.3847/1538-4357/ad675b

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: transients
- Question: Radio evolution of the TDE ASASSN-19bt, tested against an off-axis relativistic jet or a spherical non-relativistic outflow  
  > "In this work, we present the radio evolution of ASASSN-19bt and consider two possible models: an off-axis relativistic jet or a spherical non-relativistic outflow." (Introduction)
- Target **ASASSN-19bt / AT2019ahk (host 2MASX J07001137-6602251)**: coordinates _not stated_; z/distance z = 0.0262; distance 115.2 Mpc (assumed)  
  > "ASASSN-19bt ($z = 0.0262$) was discovered by the All-Sky Automated Survey for SuperNovae" (Introduction); "We assume a distance of 115.2 Mpc for ASASSN-19bt." (2 Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01766.T
- bands: Band 3, mean frequency 97.5 GHz (four observations)  
  > "We also obtained four Band 3 observations using the Atacama Large Millimeter/submillimeter Array (ALMA) with a mean frequency of 97.5 GHz under program 2018.1.01766.T (PI: K. Alexander)." (2.1 Radio/Millimeter)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: ALMA, observations labelled C43-1, C43-2, C43-3 and C43-9/10 in the data table  
  > "C43-1" (Table 1 (radio data)); "C43-2" (Table 1 (radio data)); "C43-3" (Table 1 (radio data)); "C43-9/10" (Table 1 (radio data))
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2019-03-03, 2019-03-24, 2019-04-13, 2019-06-20  
  > "2019-03-03" (Table 1 (radio data)); "2019-03-24" (Table 1 (radio data)); "2019-04-13" (Table 1 (radio data)); "2019-06-20" (Table 1 (radio data))
- pi or archival as stated: PI: K. Alexander (program 2018.1.01766.T)  
  > "under program 2018.1.01766.T (PI: K. Alexander)" (2.1 Radio/Millimeter)
- Other facility **ATCA**: Radio flux densities 2-19 GHz in 6A, 6D, 1.5B and 750C configurations (programs C3325, CX432, C3148; archival C1473, C3101)  
  > "We collected radio observations of ASASSN-19bt using the Australia Telescope Compact Array (ATCA) in the 6A, 6D, 1.5B, 750C configurations with a frequency range 2-19 GHz" (2.1 Radio/Millimeter)
- Other facility **MeerKAT**: 0.82 GHz (UHF) and 1.28 GHz (L-band) flux densities, program SCI-20210212-YC-01  
  > "Finally, we obtained observations with MeerKAT at 0.82 GHz" (2.1 Radio/Millimeter)
- Other facility **Chandra X-ray Observatory**: Two deep ACIS epochs (Obs IDs 22182, 22183), 9.98 ks each, 2019-04-17 and 2019-06-09  
  > "We obtained two epochs of deep X-ray observations of ASASSN-19bt with the Chandra X-ray Observatory (CXO) on 2019-04-17 and 2019-06-09" (2.3 X-rays: Chandra X-ray Observatory)
- Other facility **Swift-XRT**: X-ray light curve, 0.3-10 keV, delta t = 9-1666 days  
  > "between 2019-01-31 and 2023-08-15" (2.4 X-rays: Swift-XRT); "We analyzed all available" (2.4 X-rays: Swift-XRT)
- Other facility **XMM-Newton**: X-ray luminosities taken from Holoien et al. 2019  
  > "X-ray luminosity measurements are from grouped EPIC-PN, EPIC-MOS1, and EPIC-MOS2 data, exact values are obtained from (cite: holoien_2019)" (Table (X-ray data))
- External data: Optical discovery data, TESS onset date (2019 January 21.6) and earlier-published data used as the time origin and in comparisons  
  > "In addition, we also use archival X-ray and radio data and data first published in (cite: holoien_2019)." (2 Observations); "the date where the TESS light curve indicates that the transient began to brighten (cite: holoien_2019)" (2 Observations) [from (cite: holoien_2019)]
- External data: SMBH masses of comparison TDE hosts, used to scale radii in the density-profile comparison  
  > "We use the SMBH masses from Alexander et al. 2024 (in prep.) and references therein" (5.2 Circumnuclear Density) [from Alexander et al. 2024 (in prep.) and references therein; (cite: Yao_2024)]
- External data: Radio-to-star-formation-rate conversion used for the host-galaxy radio detection  
  > "Extrapolating the quiescent component to 1.4 GHz, the observed radio luminosity requires the formation rate of stars more massive than 5" (2.2 Archival Radio Observations) [from (cite: Condon_2002)]

## Processing

### Calibration

- pipeline or manual: ALMA data pipeline  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B using J0519-4546 as the flux calibrator and J0700-6610 as the phase calibrator." (2.1 Radio/Millimeter)
- casa version: CASA 6.2.1.7 (used for imaging and imfit)  
  > "We imaged the data using the Common Astronomy Software Applications (CASA; version 6.2.1.7) software package" (2.1 Radio/Millimeter)
- pipeline version: Pipeline-CASA54-P1-B  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B" (2.1 Radio/Millimeter)
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (flux); J0700-6610 (phase)  
  > "using J0519-4546 as the flux calibrator and J0700-6610 as the phase calibrator." (2.1 Radio/Millimeter)
- flux scale uncertainty: additional 5% of the source flux density, for ATCA, ALMA and MeerKAT  
  > "When modelling we include an additional uncertainty of 5% of the source flux density to account for the known absolute flux density scale calibration accuracy of ATCA, ALMA, and MeerKAT." (2.1 Radio/Millimeter)
- self calibration: _not stated_

### Imaging

- task: CASA imfit used to fit an elliptical Gaussian fixed to the synthesized beam; the imaging (clean) task is not named  
  > "wherein we fit the flux densities and associated uncertainties by fitting an elliptical Gaussian fixed to the size of the synthesized beam using the CASA task" (2.1 Radio/Millimeter)
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

- Host-galaxy radio component modelled as a single power law, following the earlier procedure  
  > "we follow the same procedure outlined in (cite: alexander_2016), and assume that the host component of the radio emission follows a single power law" (2.2 Archival Radio Observations) [from (cite: alexander_2016)]
- Analytic synchrotron SED shape (broken power law with sharpness s) taken from the GRB afterglow model  
  > "Although we use the analytic SED shape from the (cite: Granot_2002) model for synchrotron emission from gamma-ray burst (GRB) afterglows for the regime where" (3 Synchrotron Emission Modeling) [from (cite: Granot_2002)]
- Smoothing parameter s = 10 for the cooling-break SED adopted from the AT2019dsg analysis  
  > "Instead, we adopt the smoothing parameter used in (cite: at2019dsg) for the TDE AT2019dsg" (footnote 4) [from (cite: at2019dsg)]
- Equipartition radius/energy/B/Ne procedure for the non-relativistic outflow  
  > "we can determine the physical properties of the outflow using the procedures outlined in (cite: Barniol_Duran_2013)" (4.1 Non-Relativistic Outflow) [from (cite: Barniol_Duran_2013)]
- Off-axis relativistic jet model and the launch-time constraint  
  > "We examined the possibility of a relativistic jet in ASASSN-19bt by employing the model outlined in (cite: matsumoto)." (4.2 Relativistic Jet from an Arbitrary Viewing Angle); "We obtain this constraint by making an assumption about the outflow launch time, following (cite: matsumoto)." (4.2 Relativistic Jet from an Arbitrary Viewing Angle) [from (cite: matsumoto)]
- epsilon_e = 0.1 typical value  
  > "we adopt the typical value of $\epsilon_e=0.1$ (cite: Panaitescu_2002)" (4.1 Non-Relativistic Outflow) [from (cite: Panaitescu_2002)]
- Peeling technique to improve ATCA calibration near a bright source  
  > "see e.g., (cite: peeling)" (2.1 Radio/Millimeter) [from (cite: peeling)]
- Swift-XRT light curve extraction with custom scripts  
  > "and custom scripts (cite: Margutti13)" (2.4 X-rays: Swift-XRT) [from (cite: Margutti13)]

### Not stated but needed to reproduce (our reading)

- ALMA imaging recipe: clean task, weighting/robust, cell size, image size, masking, uv range, spectral windows and bandwidth used for the continuum
- ALMA beam sizes, image rms and integration time per execution block, and how the upper limit on 2019 June 20 was defined (sigma level)
- Whether the pipeline products were used as delivered or manually re-flagged, and the flux density assumed for J0519-4546
- Miriad imaging parameters (weighting, cell, clean depth) and peeling source model for the ATCA data
- How individual SEDs were grouped into the 7 epochs beyond the dates listed, and walker initialisation for emcee
- Numerical recipe for solving Gamma and the radius in the off-axis jet model in each epoch
- Public availability of the ALMA data and whether the DDT/T project is accessible in the archive

## Analysis recipe

1. **Calibrate and image ALMA Band 3 data, measure flux densities**: ALMA pipeline calibration, imaging in CASA, point-source flux by fitting an elliptical Gaussian fixed to the synthesized beam with imfit  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B using J0519-4546 as the flux calibrator and J0700-6610 as the phase calibrator." (2.1 Radio/Millimeter); "wherein we fit the flux densities and associated uncertainties by fitting an elliptical Gaussian fixed to the size of the synthesized beam using the CASA task" (2.1 Radio/Millimeter)
   - software: CASA, ALMA pipeline
   - parameter: Mean frequency 97.5 GHz; first three observations detected, 2019 June 20 an upper limit  
  > "We detected ASASSN-19bt in the first three observations, while the 2019 June 20 observation yielded an upper limit." (2.1 Radio/Millimeter)
   - assumption: 5% of source flux density added as absolute flux scale uncertainty  
  > "When modelling we include an additional uncertainty of 5% of the source flux density to account for the known absolute flux density scale calibration accuracy of ATCA, ALMA, and MeerKAT." (2.1 Radio/Millimeter)
   - fitting: _not stated_
   - validation: _not stated_
2. **Reduce ATCA and MeerKAT data and measure flux densities**: ATCA reduced with Miriad (B1934-638 flux calibrator, J0700-6610 phase calibrator, peeling), imaged with mfclean/restor, point-source fit; MeerKAT from SARAO SDP calibrated images fitted with CASA imfit  
  > "For calibration, we employed B1934-638 as the primary flux calibrator for all observations and frequencies." (2.1 Radio/Millimeter); "Flux densities and their associated uncertainties were determined by fitting a point source model (gaussian with the width of the point-spread-function) using the" (2.1 Radio/Millimeter); "We used the calibrated images obtained via the South African Radio Astronomy Observatory Science Data Processor (SDP)" (2.1 Radio/Millimeter)
   - software: Miriad, CASA
   - parameter: Bright-target ATCA data split into 2 subbands of 1024 MHz for imaging  
  > "In observations where the target was sufficiently bright, we split the data into 2 subbands of 1024 MHz for imaging." (2.1 Radio/Millimeter)
   - parameter: Peeling: direction-dependent gains applied to a limited part of the image to remove artifacts from a nearby bright source  
  > "This is a procedure for applying direction dependent gains to a limited portion of an image to reduce the artifacts due to a nearby bright source." (2.1 Radio/Millimeter)
   - fitting: _not stated_
   - validation: _not stated_
3. **Model and subtract the constant host-galaxy radio component**: Host component taken as a single power law normalised to the weighted average of two archival 2.1 GHz ATCA detections, assumed constant in time  
  > "we follow the same procedure outlined in (cite: alexander_2016), and assume that the host component of the radio emission follows a single power law" (2.2 Archival Radio Observations); "We thus conclude it is reasonable to assume that the host galaxy emission component is constant in time." (2.2 Archival Radio Observations)
   - software: Miriad
   - parameter: F_nu = 439 uJy (nu / 2.1 GHz)^-1  
  > "$F_\nu\approx(439\ \rm{\mu Jy}) (\nu/2.1 \rm GHz)^{-1}$" (2.2 Archival Radio Observations)
   - assumption: Host emission constant in time  
  > "We thus conclude it is reasonable to assume that the host galaxy emission component is constant in time." (2.2 Archival Radio Observations)
   - fitting: _not stated_
   - validation: Archival detection found consistent with star formation in the host (radio SFR about 0.22 Msun/yr vs 0.17 from the archival spectrum)  
  > "We find that the archival detection is consistent with radio emission from ongoing star formation in the host galaxy." (2.2 Archival Radio Observations)
4. **Fit the transient radio SED in 7 epochs**: Singly broken power law with peak at the self-absorption frequency, Granot & Sari shape, each SED fit independently; p fixed after an initial free fit  
  > "We group our radio observations into 7 epochs, subtract our model for the quiescent host emission" (3 Synchrotron Emission Modeling); "we fit each SED independently, without requiring any specific dynamic evolution of the emission." (3 Synchrotron Emission Modeling)
   - software: emcee
   - parameter: Free parameters F_nu,ext and nu_a; p fixed to 2.80 (transient) or 2.75 (total flux)  
  > "we adopted a weighted average of $p = 2.80 \pm 0.02$ for the transient component" (3 Synchrotron Emission Modeling)
   - parameter: 100 MCMC chains, 2,000 steps each, first 1,000 discarded  
  > "we ran each chain for 2,000 steps and discarded the initial 1,000 steps." (3 Synchrotron Emission Modeling)
   - parameter: Sharpness s = 1.25 - 0.18p, appropriate for rho proportional to r^-2  
  > "$s=1.25 - 0.18p$ describes the sharpness of the peak" (3 Synchrotron Emission Modeling)
   - assumption: Break frequencies ordered nu_m < nu_a < nu_c; SED peak is nu_a  
  > "We therefore initially fit our data with a singly broken power law" (3 Synchrotron Emission Modeling)
   - fitting: emcee EnsembleSampler, Gaussian likelihood, uniform priors p in [2,4], log(F_nu,ext/mJy) in [-4,2], log(nu_a/Hz) in [6,11]  
  > "to determine the optimal model parameters, assuming a Gaussian likelihood for all the parameters." (3 Synchrotron Emission Modeling); "We adopt uniform priors on the model parameters $p$, $F_{\nu,\rm ext}$, and $\nu_a$, where $p \in [2,4]$, log($F_{\nu,\rm ext}/ \rm{mJy}$) $\in [-4,2]$, and log($\nu_a/\rm{Hz}$) $\in [6,11]$." (3 Synchrotron Emission Modeling)
   - validation: Convergence ensured by long chains with burn-in; fits to total flux density done as a check and found not to alter conclusions  
  > "To ensure the convergence of the samples" (3 Synchrotron Emission Modeling)
5. **Test for a synchrotron cooling break using the 97.5 GHz limit**: Single-break SED plus a cooling break (Granot & Sari form) fitted to day-132 data and the 2019 June 20 ALMA upper limit; nu_c used to infer epsilon_B  
  > "we obtained an upper limit on the flux density at 97.5 GHz that is inconsistent with our single-break synchrotron SED model fit" (3.1 Synchrotron Cooling)
   - parameter: beta_3 = -p/2 above the cooling break, smoothing s = 10  
  > "$\beta_3 = {-p/2}$ is the spectral slope above the cooling break, and $s=10$ describes the smoothing" (3.1 Synchrotron Cooling)
   - assumption: Outflow launched at delta t = 0 days  
  > "We conservatively assume that the radio outflow was launched at $\delta t=0$ days." (3.1 Synchrotron Cooling)
   - fitting: _not stated_
   - validation: _not stated_
6. **Derive outflow properties for a non-relativistic spherical outflow**: Equipartition formulae for R, E, B, Ne and n_ext using F_p and nu_p of each epoch, with nu_p identified with nu_a  
  > "In our analysis, we associate $\nu_p$ with $\nu_a$ and assume $\nu_m < \nu_a$." (4.1 Non-Relativistic Outflow); "we can determine the physical properties of the outflow using the procedures outlined in (cite: Barniol_Duran_2013)" (4.1 Non-Relativistic Outflow)
   - parameter: Emitting volume in a shell of radius 0.1R: f_A = 1, f_V = 0.36  
  > "we assume that the emitting volume of the outflow is confined to a spherically-symmetric shell of radius $0.1R$, implying $f_A = 1$ and $f_V = \frac{4}{3}(1-0.9^3) \approx 0.36$." (4.1 Non-Relativistic Outflow)
   - parameter: gamma_m = 2, p = 2.8  
  > "In our analysis we set the minimum Lorentz factor $\gamma_m=2$" (4.1 Non-Relativistic Outflow); "With $p=2.8$, the expressions for the radius and energy are given by (cite: Barniol_Duran_2013)" (4.1 Non-Relativistic Outflow)
   - parameter: epsilon_e = 0.1, epsilon_B = 0.2  
  > "we adopt the typical value of $\epsilon_e=0.1$ (cite: Panaitescu_2002) and fix $\epsilon_B = 0.2$, which is motivated by the observed location of the cooling break at 132 days" (4.1 Non-Relativistic Outflow)
   - assumption: Kinetic energy dominated by hot protons, correction xi = 1 + 1/epsilon_e  
  > "we thus incorporate the extra energy carried by the hot protons using the correction factor $\xi =1+\epsilon_e^{-1}$ to the total energy" (4.1 Non-Relativistic Outflow)
   - fitting: _not stated_
   - validation: _not stated_
7. **Derive outflow properties for an off-axis relativistic jet**: Generalised equipartition model of Matsumoto & Piran, with equations updated for non-equipartition epsilon_B and hot protons, solved per epoch for Gamma at fixed viewing angles  
  > "We examined the possibility of a relativistic jet in ASASSN-19bt by employing the model outlined in (cite: matsumoto)." (4.2 Relativistic Jet from an Arbitrary Viewing Angle); "We solve for $\Gamma$ in each epoch using the same procedure outlined (cite: matsumoto)." (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
   - parameter: Viewing angles 0.1, 0.26, 0.52, 0.79, 1.05, 1.57 rad  
  > "$\theta_\text{obs} = 0.1,0.26,0.52,0.79,1.05,1.57$" (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
   - parameter: f_A = f_V = 1 (theta_j = 1/Gamma); alternative fixed opening angle theta_j = 10 deg with energy multiplied by 4 Gamma^2 (1 - cos theta_j)  
  > "We initially set the jet area and volume filling factors to be $f_A=f_V=1$." (4.2 Relativistic Jet from an Arbitrary Viewing Angle); "we impose an intermediate jet opening angle of $\theta_{j} = 10^\circ$" (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
   - parameter: epsilon_B from the cooling break between 3e-4 and 0.005 depending on viewing angle  
  > "the observed location of the cooling break implies $3\times 10^{-4} < \epsilon_B < 0.005$ depending on the viewing angle" (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
   - assumption: Launch time delta t = 0 days  
  > "As in §[3.1](#sec:cool), we take the launch time to be $\delta t=0$ days." (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
   - fitting: _not stated_
   - validation: _not stated_
8. **Fit evolution laws, estimate launch dates and circumnuclear density profiles**: Linear fit of radius versus time extrapolated to R = 0 for the launch date; power-law fits to R, E, B, n and Gamma versus time; compare with other TDEs  
  > "then we can apply a linear fit to the radius evolution and extrapolate to $R = 0$." (5.3 Multiple Outflows?); "In the relativistic model, we estimate the density of the unshocked ambient medium at radius $R$ as $n_\text{ext} = n_e/4\Gamma^2$" (5.2 Circumnuclear Density)
   - assumption: Constant outflow velocity for the linear-radius launch-date estimate  
  > "if the outflow is assumed to be moving at a constant velocity" (5.3 Multiple Outflows?)
   - fitting: _not stated_
   - validation: Launch dates compared against the first detection at delta t = 40 days  
  > "which is inconsistent with our initial radio detection at $\delta t = 40$ days." (5.3 Multiple Outflows?)
9. **Measure X-ray fluxes and spectra (Chandra, Swift-XRT)**: CIAO reduction of Chandra data, wavdetect and specextract, absorbed power-law spectral fit in Xspec; Swift-XRT light curve from the online tools, count-to-flux conversion using the joint Chandra fit  
  > "software package (v4.15) applying standard ACIS data filtering." (2.3 X-rays: Chandra X-ray Observatory); "We extracted a 0.3-10 keV count-rate light-curve using the online automated tools released by the Swift-XRT team" (2.4 X-rays: Swift-XRT)
   - software: CIAO, Xspec, HEASoft
   - parameter: Adopted spectral parameters from the joint CXO fit for Swift count-to-flux conversion  
  > "For the count-to-flux calibration we adopt the best-fitting spectral parameters derived from the joint fit of the two CXO epochs of" (2.4 X-rays: Swift-XRT)
   - fitting: Absorbed simple power law (tbabs*ztbabs*pow); joint fit of two epochs  
  > "Adopting an absorbed simple power-law model" (2.3 X-rays: Chandra X-ray Observatory)
   - validation: Spectral parameters consistent with XMM constraints from Holoien et al. 2019  
  > "These spectral parameters are consistent with those constrained from XMM observations in (cite: holoien_2019)." (2.3 X-rays: Chandra X-ray Observatory)

## Software

- **CASA** 6.2.1.7: Imaging ALMA data and imfit flux fits for ALMA and MeerKAT  
  > "We imaged the data using the Common Astronomy Software Applications (CASA; version 6.2.1.7) software package" (2.1 Radio/Millimeter)
- **ALMA data pipeline** Pipeline-CASA54-P1-B: Calibration of the ALMA data  
  > "The data were calibrated with the ALMA data pipeline version Pipeline-CASA54-P1-B" (2.1 Radio/Millimeter)
- **Miriad** : Reduction, imaging and flux fitting of ATCA data  
  > "To process the data, we applied standard data reduction techniques using the package" (2.1 Radio/Millimeter); "Flux densities and their associated uncertainties were determined by fitting a point source model (gaussian with the width of the point-spread-function) using the" (2.1 Radio/Millimeter)
- **emcee** : MCMC fits of the radio SEDs  
  > "We employed the Markov Chain Monte Carlo (MCMC) module" (3 Synchrotron Emission Modeling); "with 100 MCMC chains using the sampler EnsembleSampler from" (3 Synchrotron Emission Modeling)
- **CIAO** v4.15: Reduction of Chandra ACIS data, including wavdetect and specextract  
  > "software package (v4.15) applying standard ACIS data filtering." (2.3 X-rays: Chandra X-ray Observatory)
- **Xspec** : Absorbed power-law fit to Chandra spectra  
  > "Adopting an absorbed simple power-law model" (2.3 X-rays: Chandra X-ray Observatory)
- **HEASoft** v.6.32.1: Analysis of Swift-XRT data  
  > "using HEASoft v.6.32.1 and corresponding calibration files" (2.4 X-rays: Swift-XRT)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA 97.5 GHz flux density, delta t = 40 d | 143 | 21 (stat) and 7 (sys) | uJy | 1 | 143 $\pm$ 21 $\pm$ 7 |
| ALMA 97.5 GHz flux density, delta t = 61 d | 89 | 16 (stat) and 4 (sys) | uJy | 1 | 89 $\pm$ 16 $\pm$ 4 |
| ALMA 97.5 GHz flux density, delta t = 81 d | 60 | 14 (stat) and 3 (sys) | uJy | 1 | 60 $\pm$ 14 $\pm$ 3 |
| ALMA 97.5 GHz flux density upper limit, delta t = 149 d | <31 | not stated | uJy | 1 | $<$31 |
| Electron index p (transient component) | 2.80 | 0.02 | dimensionless | 4 | we adopted a weighted average of $p = 2.80 \pm 0.02$ for the transient component |
| Peak frequency nu_p, delta t = 49 d | 28.56 | 3.34 | GHz | 4 | 28.56 $\pm$ 3.34 |
| Peak frequency nu_p, delta t = 88 d | 7.79 | 1.22 | GHz | 4 | 7.79 $\pm$ 1.22 |
| Peak frequency nu_p, delta t = 132 d | 4.27 | 0.64 | GHz | 4 | 4.27 $\pm$ 0.64 |
| Peak frequency nu_p, delta t = 186 d | 2.53 | 0.41 | GHz | 4 | 2.53 $\pm$ 0.41 |
| Peak frequency nu_p, delta t = 457 d | 4.03 | 0.12 | GHz | 4 | 4.03 $\pm$ 0.12 |
| Peak frequency nu_p, delta t = 800 d | 1.95 | 0.09 | GHz | 4 | 1.95 $\pm$ 0.09 |
| Peak frequency nu_p, delta t = 1377 d | 1.06 | 0.05 | GHz | 4 | 1.06 $\pm$ 0.05 |
| Peak flux density F_p, delta t = 49 d | 0.20 | 0.02 | mJy | 4 | 0.20 $\pm$ 0.02 |
| Peak flux density F_p, delta t = 88 d | 0.25 | 0.02 | mJy | 4 | 0.25 $\pm$ 0.02 |
| Peak flux density F_p, delta t = 132 d | 0.53 | 0.06 | mJy | 4 | 0.53 $\pm$ 0.06 |
| Peak flux density F_p, delta t = 186 d | 0.79 | 0.11 | mJy | 4 | 0.79 $\pm$ 0.11 |
| Peak flux density F_p, delta t = 457 d | 4.96 | 0.14 | mJy | 4 | 4.96 $\pm$ 0.14 |
| Peak flux density F_p, delta t = 800 d | 4.46 | 0.15 | mJy | 4 | 4.46 $\pm$ 0.15 |
| Peak flux density F_p, delta t = 1377 d | 5.78 | 0.20 | mJy | 4 | 5.78 $\pm$ 0.20 |
| Peak flux density growth between 186 and 457 d | F_p proportional to t^2.1 | not stated | dimensionless | 4 | with the peak flux density evolving as $t^{2.1}$ |
| Cooling break frequency nu_c | approximately 19 | not stated | GHz | 5 | Our best-fit synchrotron cooling model suggests that $\nu_c \approx 19 \ \rm GHz$. |
| epsilon_B implied for spherical non-relativistic outflow | approximately 0.2 | not stated | dimensionless | 5 | The observed $\nu_c$ is consistent with $\epsilon_B \approx 0.2$ under the assumption that the outflow is spherical and non-relativistic. |
| log R (non-relativistic), delta t = 49 d | 15.30 | +0.05/-0.04 | log cm | 6 | 15.30 $^{+ 0.05 }_{- 0.04 }$ |
| log R (non-relativistic), delta t = 1377 d | 17.42 | +0.03/-0.02 | log cm | 6 | 17.42 $^{+ 0.03 }_{- 0.02 }$ |
| log E (non-relativistic), delta t = 49 d | 46.40 | +0.05/-0.04 | log erg | 6 | 46.40 $^{+ 0.05 }_{- 0.04 }$ |
| log E (non-relativistic), delta t = 1377 d | 49.57 | +0.04/-0.03 | log erg | 6 | 49.57 $^{+ 0.04 }_{- 0.03 }$ |
| beta (non-relativistic), delta t = 49 d | 0.016 | +0.002/-0.001 | dimensionless | 6 | 0.016 $^{+ 0.002 }_{- 0.001 }$ |
| beta (non-relativistic), delta t = 1377 d | 0.074 | +0.006/-0.004 | dimensionless | 6 | 0.074 $^{+ 0.006 }_{- 0.004 }$ |
| Radius growth law, all epochs | R proportional to t^1.3 | not stated | dimensionless | 6 | Including all epochs, the radius expands at a rate of $R\propto t^{1.3}$ |
| Radius growth law, 2019 epochs (delta t = 49-186) | R proportional to t^2.3 | not stated | dimensionless | 6 | follow a much steeper trend of $R\propto t^{2.3}$ |
| Energy growth law (non-relativistic) | E proportional to t^2.2 | not stated | dimensionless | 6 | increasing more than three orders of magnitude as $E\propto t^{2.2}$ over the full four years of observation |
| Magnetic field radial profile (non-relativistic) | B(r) proportional to r^-0.8 early, r^-1 late | not stated | dimensionless | 6 | We find that the magnetic field decays with increasing distance as $B(r)\propto r^{-0.8}$ at early times and as $B(r)\propto r^{-1}$ at late times. |
| Jet Lorentz factor Gamma, theta_obs = 1.57, delta t = 49 d | 25.7 | +1.6/-1.9 | dimensionless | 7 | 25.7 $^{+ 1.6 }_{- 1.9 }$ |
| Jet Lorentz factor Gamma, theta_obs = 1.57, delta t = 1377 d | 8.3 | +0.4/-0.4 | dimensionless | 7 | 8.3 $^{+ 0.4 }_{- 0.4 }$ |
| Jet log E, theta_obs = 1.57, delta t = 1377 d | 51.91 | +0.02/-0.03 | log erg | 7 | 51.91 $^{+ 0.02 }_{- 0.03 }$ |
| Jet log E_wide, theta_obs = 1.57, delta t = 1377 d | 52.05 | +0.06/-0.07 | log erg | 7 | 52.05 $^{+ 0.06 }_{- 0.07 }$ |
| Jet Lorentz factor for most off-axis viewing angles | 10-20 | not stated | dimensionless | 7 | All viewing angles yield a solution where the jet propagates at nearly light speed with $\Gamma\sim10-20$ for the most off-axis viewing angles. |
| Jet Lorentz factor deceleration | Gamma proportional to t^-1 before re-brightening; t^-0.2 after | not stated | dimensionless | 7 | We find that the jet slows as $\Gamma\propto t^{-1}$. After the radio re-brightening, we find that $\Gamma$ exhibits a weaker decay where $\Gamma\propto t^{-0.2}$. |
| Late-time energy for theta_j = 10 deg jet | approximately 1e52 | not stated | erg | 7 | then remains constant at $E\sim 10^{52} \ \text{erg}$ at later times. |
| epsilon_B range for off-axis jet | 3e-4 to 0.005 depending on viewing angle | not stated | dimensionless | 5 | We find $\epsilon_B$ ranges from $\sim 3 \times10^{-4}$ to $\sim 0.005$ depending on the viewing angle |
| Launch date from linear fit to all radius data | 46 | not stated | days (delta t) | 8 | applying a linear fit to all of the data implies a launch date of $\delta t \approx46$ days |
| Launch date from linear fit to later epochs | approximately 210 | not stated | days (delta t) | 8 | would imply a launch date of $\delta t \approx 210$ days |
| Density profile slope, off-axis jet model | n(r) proportional to r^-4.3 early, r^-2.6 late | not stated | dimensionless | 8 | the constructed density profile decays as $n(r)\propto r^{-4.3}$ at early times and as $n(r)\propto r^{-2.6}$ at late times |
| Chandra photon index (joint fit of two epochs) | 1.64 | +0.57/-0.50 (1 sigma) | dimensionless | 9 | $\Gamma= 1.64^{+0.57}_{-0.50}$ |

## Qualitative findings

- Radio emission is detected shortly after optical discovery and keeps rising for years, with the peak flux density plateauing after about 1 year  
  > "Radio emission was first detected shortly after the optical discovery and continued to rise for years afterward" (6 Conclusions)
- The non-relativistic energy increase is the largest seen in any TDE  
  > "This is by far the largest energy increase ever seen in any TDE." (5.1 Energy and Velocity)
- Early X-ray emission is among the faintest of any optically selected TDE and no X-rays are detected after about 225 days  
  > "its early X-ray emission was among the least luminous of any optically-selected TDE and no X-rays have been detected since approximately 225 days post-discovery." (6 Conclusions)

## Claim tuples

- H: Does ASASSN-19bt show radio evolution like other TDEs? | E: ATCA, ALMA and MeerKAT monitoring from 40 to 1464 days, SED fits in 7 epochs | R: Peak flux density rises rapidly until 457 days then plateaus | F: ASASSN-19bt has unusual radio evolution among TDEs | **supported**
- H: A non-relativistic spherical outflow explains the radio emission | E: Equipartition analysis of each epoch with f_A = 1, f_V = 0.36 | R: Energy rises from about 1e46 to 1e49 erg with beta about 0.05 and outflow acceleration in the first 186 days | F: Model does not explain the observed acceleration and large energy rise | **partially**
- H: An off-axis relativistic jet explains the radio emission | E: Generalised equipartition model at six viewing angles, jet opening angles 1/Gamma and 10 deg | R: Energy of about 1e50 to 1e52 erg with Gamma of about 10 persisting to late times in the most off-axis cases | F: Reduces the energy increase but has implausible features such as the energy budget and persistent high Gamma | **partially**
- H: Either simple model gives a holistic explanation | E: Comparison of the two limiting geometries against the SED evolution and other TDEs | R: Neither model matches all observed behaviour | F: More complex models, possibly multiple outflows, are needed | **supported**
- H: The 97.5 GHz upper limit reveals a synchrotron cooling break | E: Single-break plus cooling-break SED fit to day-132 data and the ALMA limit | R: nu_c about 19 GHz, so the radio synchrotron under-predicts the X-rays | F: The X-ray emission is not synchrotron in origin | **supported**

## Reasoning

- Why this data: Radio observations constrain the disruption geometry and outflow characteristics  
  > "Radio observations may illuminate the nature of this emission by constraining the disruption geometry and the characteristics of any resulting outflows." (Introduction)
- Why this method: Emitting-volume shell geometry chosen to compare with previously studied TDEs  
  > "To compare to previously studied TDEs from the literature (cite: alexander_2016; at2019dsg; AT2018hyz), we assume that the emitting volume of the outflow is confined to a spherically-symmetric shell of radius $0.1R$" (4.1 Non-Relativistic Outflow)
- Alternative: Narrow jet geometries (theta_j < 1/Gamma) not included because the implied opening angle was nonphysical  
  > "We did not include any narrow jet geometries ($\theta_j < 1/\Gamma$) as the implied jet opening angle became nonphysical due to large bulk $\Gamma$s." (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
- Alternative: Small viewing angles give extreme, unphysical solutions  
  > "We find that the solutions become exceedingly extreme for small viewing angles." (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
- How they decided it was enough: _not stated_
- Limitation (authors): Chandra spectra have too few counts to constrain the spectral shape  
  > "Due to the low-number statistics, we cannot statistically constrain the spectral shape and both thermal and non-thermal models are statistically acceptable." (2.3 X-rays: Chandra X-ray Observatory)
- Limitation (authors): Inferred Gamma depends on the assumed jet launch date  
  > "We note that $\Gamma$ is dependent on the inferred launch date of the jet" (4.2 Relativistic Jet from an Arbitrary Viewing Angle)
- Caveat (inferred, ours): The ALMA data are only four Band 3 epochs and the imaging and flux-measurement settings are barely described, so the ALMA flux densities cannot be reproduced from the text alone
- Caveat (inferred, ours): Results depend on assumed epsilon_e = 0.1, epsilon_B from the single cooling-break constraint, and launch time delta t = 0
- Caveat (inferred, ours): Host subtraction assumes a constant host power law with index -1 normalised at 2.1 GHz
- Caveat (inferred, ours): Seven epochs are fit with only two free parameters each, with p fixed, so parameter uncertainties may be underestimated

## Reproducibility

- Data public (paper): Swift data stated as public; public status of the ALMA data not stated  
  > "We acknowledge the use of public data from the Swift data archive." (Acknowledgements)
- Products in archive: _not stated_
- Missing: ALMA imaging parameters and flux calibrator flux value
- Missing: Miriad imaging settings and peeling model for ATCA
- Missing: Exact numerical solver details for the off-axis jet Gamma and R per epoch
- Missing: Epoch grouping and emcee initialisation details
- Data volume (inferred): small for the ALMA part (four short Band 3 observations, likely a few GB raw); ATCA and MeerKAT data would add more
- Score (inferred): 3/5, Flux densities for all epochs are tabulated and the equipartition and SED-fit recipes, priors and parameters are given, so the modelling can be redone from the table; the ALMA reduction and imaging settings are not given and public status of the ALMA data is not stated.
- Rediscovery candidate: no, Public availability of the ALMA data is not stated and the ALMA imaging recipe is incomplete, even though the tabulated fluxes allow the modelling to be repeated.

## Links

- Method: (cite: Barniol_Duran_2013) (Equipartition formulae for radius, energy, B and Ne)
- Method: (cite: matsumoto) (Off-axis relativistic jet equipartition model and launch-time constraint)
- Method: (cite: Granot_2002) (Synchrotron SED shape and cooling-break form)
- Method: (cite: alexander_2016) (Host-component subtraction procedure)
- Companion: (cite: holoien_2019) (Discovery paper with optical/UV and XMM data used here)
- Companion: (cite: yvette_2023) (Delayed radio emission in TDEs)
- Companion: (cite: AT2018hyz) (Comparison TDE with late rising radio emission)
- Related: ATCA programs C3325, CX432, C3148, C1473, C3101
- Related: MeerKAT program SCI-20210212-YC-01
- Related: Chandra DDT-20708675
- Related: TESS Continuous Viewing Zone light curve

## Checks

```json
{
 "quotes": 157,
 "quotes_ok": 157,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 44,
 "numeric_problems": 0,
 "fill": {
  "facts": 122,
  "stated": 82,
  "rate": 0.672
 },
 "evidence_ok": true
}
```
