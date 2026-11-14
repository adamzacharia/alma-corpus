# Ordered magnetic fields around the 3C 84 central black hole

`2024A&A...682L...3P` | Astronomy and Astrophysics 2024 | first author: Paraschos, G. F. | arXiv: 2402.00927 | DOI: 10.1051/0004-6361/202348308

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type multi_facility_alma_minor

## Science

- Fields: agn_and_quasars
- Question: Detect compact structures with 228 GHz EHT VLBI in 3C 84 and constrain the physical conditions (magnetic field, polarisation, jet-launching model) of its compact region  
  > "we aim to perform a direct detection of compact structures and understand the physical conditions in the compact region of 3C 84." (abstract)
- Target **3C 84 (NGC 1275)**: coordinates _not stated_; z/distance D_L = 78.9 +/- 2.4 Mpc, z = 0.0176, 0.36 pc/mas  
  > "The radio source 3C 84 (NGC 1275; $D_\textrm{L} = 78.9\pm2.4\,\textrm{Mpc}$, $z = 0.0176$, (cite: Strauss92), corresponding to a conversion factor $\uppsi=0.36$ pc/mas" (Introduction); "We used $H_0=69.6$ and ${\Omega_\textrm{M} = 0.286}$ in a flat cosmology (cite: Bennet14), yielding a length scale of $\uppsi=0.36$ pc/mas." (Data description and analysis); distance from Strauss92 (D_L, z); H0 = 69.6, Omega_M = 0.286 flat cosmology from Bennet14 for the length scale  
  > "The radio source 3C 84 (NGC 1275; $D_\textrm{L} = 78.9\pm2.4\,\textrm{Mpc}$, $z = 0.0176$, (cite: Strauss92), corresponding to a conversion factor $\uppsi=0.36$ pc/mas" (Introduction); "We used $H_0=69.6$ and ${\Omega_\textrm{M} = 0.286}$ in a flat cosmology (cite: Bennet14), yielding a length scale of $\uppsi=0.36$ pc/mas." (Data description and analysis)

## Data provenance

- ALMA projects: 2016.1.01154.V
- bands: EHT 228 GHz (1.3 mm) VLBI  
  > "at 228 GHz on April 7 between 18:30 and 19:40 UTC, with six scans each around 5 mins in length." (Data description and analysis)
- frequencies and spectral setup: Two 2 GHz bands centred at 227.1 GHz (LO) and 229.1 GHz (HI); both combined, averaged over 2 GHz and 120 s  
  > "The frequency setup of the EHT in 2017 consisted of two bands, each of 2 GHz in width, centred at 227.1 GHz (LO band) and 229.1 GHz (HI band)" (Additional methodology comments); "we combined data sets from both bands, using data points averaged over 2 GHz in frequency and for 120 s in time." (Additional methodology comments)
- continuum bandwidth: _not stated_
- arrays: EHT 2017: ALMA, APEX, SMT, JCMT, SMA (five telescopes, three sites)  
  > "Five telescopes at three geographical sites participated in the observation:" (Data description and analysis); "and the Atacama Pathfinder Experiment (APEX) telescope in Chile;" (Data description and analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: six scans of about 5 min each  
  > "with six scans each around 5 mins in length." (Data description and analysis)
- observing dates: 2017 April 7, 18:30-19:40 UTC (EHT 2017 campaign)  
  > "at 228 GHz on April 7 between 18:30 and 19:40 UTC" (Data description and analysis)
- pi or archival as stated: EHT collaboration data; lower-frequency VLBA epochs used as published by monitoring programs  
  > "As both monitoring programs publish fully calibrated and imaged data sets, we opted to use them as provided." (Data description and analysis)
- Other facility **VLBA 15 GHz (April 22, 2017)**: Quasi-simultaneous 15 GHz VLBI epoch (Lister18)  
  > "we used the publicly available Very Long Baseline Array (VLBA) epochs from April 22, 2017 at 15 GHz (cite: Lister18)" (Data description and analysis)
- Other facility **VLBA 43 GHz (April 16, 2017)**: Quasi-simultaneous 43 GHz VLBI epoch (Jorstad17)  
  > "and April 16, 2017 at 43 GHz (cite: Jorstad17)" (Data description and analysis)
- Other facility **GMVA 86 GHz (March 30, 2017)**: Quasi-simultaneous 86 GHz VLBI epoch (Paraschos22); D-terms with polsolve, imaged with CLEAN  
  > "At 86 GHz, we used the Global Millimeter VLBI Array (GMVA) epoch from March 30, 2017 (cite: Paraschos22)." (Data description and analysis)
- Other facility **POLAMI (IRAM 30m)**: Single-dish 86 and 228 GHz flux densities and polarisation (April 4, 2017)  
  > "The single-dish data used in this paper were observed by the POLAMI (cite: Thum08; Agudo18a) and QUIVER (cite: Myserlis18; Kraus03) programmes on April 4 and April 8, 2017, respectively." (Data description and analysis); "POLAMI (IRAM 30m Telescope)" (Additional methodology comments)
- Other facility **QUIVER (Effelsberg 100m)**: Single-dish 8 GHz flux density (April 8, 2017)  
  > "QUIVER (Effelsberg 100m Telescope)" (Additional methodology comments)
- External data: VLBA 15 GHz epoch images (April 22, 2017), used as provided  
  > "we used the publicly available Very Long Baseline Array (VLBA) epochs from April 22, 2017 at 15 GHz (cite: Lister18)" (Data description and analysis) [from Lister18]
- External data: VLBA 43 GHz epoch images (April 16, 2017), used as provided  
  > "and April 16, 2017 at 43 GHz (cite: Jorstad17)" (Data description and analysis) [from Jorstad17]
- External data: GMVA 86 GHz epoch (March 30, 2017)  
  > "At 86 GHz, we used the Global Millimeter VLBI Array (GMVA) epoch from March 30, 2017 (cite: Paraschos22)." (Data description and analysis) [from Paraschos22]
- External data: Thermal electron density n_e = 3e4 cm^-3 (for RM-based field estimate); BH mass 8e8 Msun  
  > "Here, $n_\textrm{e}$ is the number density of the thermal electrons, which we set to $n_\textrm{e}=3\times10^4\,\textrm{cm}^{-3}$ (cite: Scharwaechter13)." (Magnetic field estimate) [from Scharwaechter13]
- External data: alpha_thick = 0.51 +/- 0.10  
  > "Following (cite: Kim19), we set $\upalpha_\textrm{thick}=0.51\pm0.10$." (Magnetic field estimate) [from Kim19]
- External data: alpha_thin = -0.5  
  > "The optically thin spectral index is $\upalpha_\textrm{thin}=-0.5$ (cite: Kim19)." (Magnetic field estimate) [from Kim19]
- External data: Synchrotron peak flux density S_m = 9.0 +/- 0.5 Jy, extrapolated from the optically thin flux density  
  > "the synchrotron peak flux density as $S_{\rm m}=9.0\pm 0.5\,\textrm{Jy}$ at the frequency $\upnu_{\rm m}$, extrapolated from the optically thin flux density (cite: Chamani21)" (Magnetic field estimate) [from Chamani21]
- External data: Total jet luminosity P_jet = 1.5e44 erg/s  
  > "Finally, the total luminosity of the jet in 3C 84 (cite: Rafferty06) is $P_\textrm{jet}=1.5\times 10^{44}\,\textrm{erg\,s}^{-1}$." (Dimensionless magnetic flux) [from Rafferty06]

## Processing

### Calibration

- pipeline or manual: Standard EHT data reduction path incl. EHT-HOPS fringe-fitting and post-processing pipeline  
  > "Following the correlation, observations were subjected to the standard EHT data reduction path" (Data description and analysis); "including the `EHT-HOPS` fringe-fitting and post-processing pipeline (cite: Blackburn19)." (Data description and analysis)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: VLBA 15 and 43 GHz data used as provided by the monitoring programs (not ALMA archive products)  
  > "As both monitoring programs publish fully calibrated and imaged data sets, we opted to use them as provided." (Data description and analysis)
- flux calibrator: _not stated_
- flux scale uncertainty: 20% at 15 GHz, 30% at 43 GHz, 50% at 86 GHz, 15% at 228 GHz  
  > "The uncertainties of the flux density measurements are of the order of $20\%$ at 15 GHz, $30\%$ at 43 GHz, $50\%$ at 86 GHz, and $15\%$ at 228 GHz" (Additional methodology comments)
- self calibration: _not stated_

### Imaging

- task: CLEAN algorithm for the 86 GHz GMVA data (D-terms with polsolve)  
  > "the data were imaged using the `CLEAN` algorithm (cite: Shepherd94; Shepherd95)." (Data description and analysis)
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

- Standard EHT data reduction path (2017 campaign)  
  > "Following the correlation, observations were subjected to the standard EHT data reduction path" (Data description and analysis) [from EHT19b; EHT19c; EHT22b (cite keys as written)]
- EHT-HOPS fringe-fitting and post-processing pipeline  
  > "including the `EHT-HOPS` fringe-fitting and post-processing pipeline (cite: Blackburn19)." (Data description and analysis) [from Blackburn19]
- Polarimetric calibration referenced to ALMA (absolute EVPA, complex polarimetric gains)  
  > "the polarimetric calibration relies on the calibration of ALMA (cite: Goddi19), which provides the absolute EVPA" (Additional methodology comments) [from Goddi19; EHT21a]
- D-term magnitudes of the EHT array taken from previous EHT publications  
  > "We assumed the magnitude of the complex EHT array D-terms estimated and verified in previous EHT publications (cite: EHT21a; Issaoun22; Jorstad2023)" (Additional methodology comments) [from EHT21a; Issaoun22; Jorstad2023]
- 86 GHz GMVA epoch and its processing  
  > "At 86 GHz, we used the Global Millimeter VLBI Array (GMVA) epoch from March 30, 2017 (cite: Paraschos22)." (Data description and analysis) [from Paraschos22]
- Template-matching technique for lower-frequency component fluxes  
  > "This is made possible by using the template-matching technique (cite: Savolainen08; Kovalev08)" (Multi-frequency template matching) [from Savolainen08; Kovalev08]
- Resolution limit restricted to about one-fifth of the beam size  
  > "We therefore adopted the more conservative approach of restricting the resolution limit to the typical value of approximately one-fifth of the beam size (cite: Oh22)." (Multi-frequency template matching) [from Oh22]
- RM from the EVPA gradient versus wavelength squared  
  > "by determining the gradient of the EVPAs as a function of the wavelength squared (cite: Kim19)" (Model interpretation) [from Kim19]
- n-pi ambiguity resolution of EVPAs  
  > "The $n\uppi$ ambiguity was resolved beforehand, as described in (cite: Hovatta12)." (Model interpretation) [from Hovatta12]
- Doppler factor 1.1 +/- 0.1 adopted from earlier observations  
  > "We assumed $\updelta=1.1\pm0.1$ for the Doppler factor based on observations presented in (cite: Kim19; Punsly21; Paraschos21)" (Magnetic field estimate) [from Kim19; Punsly21; Paraschos21]

### Not stated but needed to reproduce (our reading)

- Where the calibrated EHT 2017 3C 84 visibility data (April 7 scans) can be obtained and whether they are public
- Exact SciPy optimiser, error-function definition, weights between amplitudes, closure phases and fractional polarisation, starting guesses, parameter bounds and number of restarts
- Station amplitude-gain parametrisation and priors used in the fit
- Treatment (shape, size, flux) of the ~5000 microarcsecond extended component beyond the stated approximate values
- How component flux and position uncertainties were derived beyond the quoted percentages
- Which data points and weights were used in the turnover-frequency fit (S_0, nu_m), and whether single-dish points were included
- How fluxes and polarisation of the three components were measured in the 15, 43 and 86 GHz images (beams, template-matching software, fit settings)
- Which scan(s), baselines and gain solutions supplied the ALMA-based EVPA calibration
- The single-dish EVPA and polarised-flux values used for the RM fit (only total fluxes are tabulated)
- Random seed and procedure of the ten D-term phase realisations
- Details of the Faraday-screen geometry (path length psi*theta, viewing angle, r_in, r_out) choices beyond the single values given

## Analysis recipe

1. **Reduce and prepare the EHT 228 GHz data**: Standard EHT reduction with EHT-HOPS fringe fitting; both bands combined and averaged to 2 GHz and 120 s; ALMA-based polarimetric calibration only for the single scan where ALMA was present  
  > "Following the correlation, observations were subjected to the standard EHT data reduction path" (Data description and analysis); "As ALMA was present in only one-sixth of the observing scans of 3C 84, we only obtained the ALMA-based calibration for the single scan." (Additional methodology comments)
   - software: EHT-HOPS
   - parameter: Both bands combined, points averaged over 2 GHz in frequency and 120 s in time  
  > "we combined data sets from both bands, using data points averaged over 2 GHz in frequency and for 120 s in time." (Additional methodology comments)
   - assumption: Absolute EVPA not reliably constrained, so only absolute values of fractional polarisation are fitted  
  > "we made a choice to only fit the absolute values of the fractional Fourier polarisation" (Additional methodology comments)
   - fitting: _not stated_
   - validation: _not stated_
2. **Model-fit the compact region with circular Gaussians (amplitudes, closure phases, fractional polarisation)**: Forward modelling with circular Gaussian components (3g chosen over 2g), simultaneous fit of visibility amplitudes, closure phases and absolute fractional Fourier linear polarisation; net polarisation from the three components  
  > "We modelled the EHT data with circular Gaussian components, because the $(u,v)$ coverage is too sparse to reconstruct an image from it." (Modelling the EHT data); "different data products used for the simultaneous fitting: visibility amplitudes, closure phases, and fractional Fourier linear polarisation" (Additional methodology comments)
   - software: eht-imaging, SciPy
   - parameter: 3g model adds six degrees of freedom over the 2g compact model  
  > "The latter adds six degrees of freedom to the compact emission part." (Modelling the EHT data)
   - parameter: Fit data: 86 visibility amplitudes, 14 non-trivial closure phases, 80 absolute fractional polarisations  
  > "there are 86 visibility amplitudes, 14 non-trivial closure phases" (Modelling the EHT data)
   - parameter: Net polarisation: image-domain Stokes sum over the whole field of view  
  > "and performed the pixel-wise summation over the whole field of view." (Results)
   - assumption: Circular rather than elliptical Gaussians to reduce degrees of freedom; circular polarisation V neglected  
  > "Circular instead of elliptical Gaussian components were preferred in order to reduce the number of degrees of freedom." (Modelling the EHT data); "circular polarisation $V$ is consequently neglected in the studies of total intensity I and linear polarisation P." (Additional methodology comments)
   - fitting: Heuristic optimisation in SciPy minimising an error function; no sampler or priors stated  
  > "to search for the best-fit solution in terms of a minimum of an error function." (Modelling the EHT data)
   - validation: Reduced chi^2 per data product; closure phases of the APEX-SMT-JCMT triangle compared with 2g and 3g models; ten random D-term phase realisations refitted to gauge polarimetric leakage  
  > "The high quality of the fit is quantified with the reduced $\chi^2$" (Additional methodology comments); "generated ten random realisations of D-term phases, subsequently refitting the polarimetric source model to data sets with different leakage calibration variants." (Additional methodology comments)
3. **Cross-identify the components at 15, 43 and 86 GHz by template matching**: Template matching using the 228 GHz structure as prior, with component FWHM and positions fixed  
  > "This is made possible by using the template-matching technique (cite: Savolainen08; Kovalev08)" (Multi-frequency template matching); "The FWHM and positions of the 43, 86, and 228 GHz components have been fixed in the multi-frequency template-matching framework." (Additional methodology comments)
   - parameter: S/N ~550 at 43 GHz and ~375 at 86 GHz; resolution limit restricted to ~1/5 of beam (beams ~100 and ~50 microarcsec)  
  > "For our observations, $S/N\sim550$ at 43 GHz and $S/N\sim375$ at 86 GHz" (Multi-frequency template matching)
   - assumption: Core shift between frequencies neglected (few tens of microarcsec)  
  > "We also disregarded the core shift effects (cite: Paraschos21; Oh22; Paraschos23) between the images at different frequencies" (Multi-frequency template matching)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit the synchrotron spectrum to get the turnover frequency**: Fit of homogeneous cylindrical synchrotron spectrum (Condon16 form) with S_0 free, alpha_thick fixed, p = 2; nu_m from the peak of the fitted spectrum  
  > "We estimated the magnetic field strength in the core via synchrotron turnover frequency fitting." (Magnetic field estimate); "Subsequently, $\upnu_\textrm{m}$ is calculated by determining the peak of the fitted spectrum." (Magnetic field estimate)
   - parameter: p = 2; alpha_thick = 0.51 +/- 0.10  
  > "The parameter $p$ is the power-law slope of the electron energy distribution function and is set to $p=2$ (cite: Condon16)." (Magnetic field estimate)
   - parameter: Component sizes fixed at all frequencies to mitigate differing (u,v) coverage  
  > "We also fixed the sizes of the components for all the frequencies in order to mitigate the effects of the different $(u, v)$ coverages" (Insights from the synchrotron spectrum)
   - assumption: Homogeneous, cylindrical source  
  > "for a homogeneous and cylindrical source" (Magnetic field estimate)
   - fitting: Least-squares-type spectral fit not specified; S_0 = 5.7 +/- 0.3 Jy from the fit  
  > "$S_0=5.7\pm 0.3\,\textrm{Jy}$ is a multiplication constant, determined from the fit" (Magnetic field estimate)
   - validation: _not stated_
5. **Derive brightness temperature and magnetic fields (B_SSA, B_eq)**: B_SSA from Eq. 2 of Marscher83; B_eq from the Pacholczyk70 prescription; T_B from nu_m assuming size equal to that at 228 GHz; equipartition Doppler factor from B_SSA = B_eq  
  > "We computed a core brightness temperature of $T_\textrm{B}=(3.6\pm 1.5)\times 10^{11}\,\textrm{K}$ from $\upnu_\textrm{m}$" (Insights from the synchrotron spectrum); "We used two different prescriptions for the magnetic field strength." (Magnetic field estimate)
   - parameter: k_u = 0 and f = 1 (electron-positron pair plasma, volume filling)  
  > "Under the assumption of an electron-positron pair plasma (cite: Paraschos23), which is volume filling, $k_\textrm{u} = 0$ and $f = 1$." (Magnetic field estimate)
   - parameter: nu_min = 1e7 Hz, nu_max = 3e14 Hz  
  > "We used $\upnu_\textrm{min} = 10^7\,\textrm{Hz}$ (lowest possible frequency for synchrotron emission) and $\upnu_\textrm{max} = 3\times10^{14}\,\textrm{Hz}$ (cite: Biermann87)." (Magnetic field estimate)
   - parameter: theta = 144 +/- 18 microarcsec; delta = 1.1 +/- 0.1; S_m = 9.0 +/- 0.5 Jy; b(alpha_thin) = 3.2  
  > "and used $\uptheta=(144\pm 18)\,\upmu\textrm{as}$ (this value already includes the geometric correction discussed in (cite: Marscher83))" (Magnetic field estimate); "Our choice of $\upalpha_\textrm{thin}=-0.5$ results in $b(\upalpha_\textrm{thin})=3.2$." (Magnetic field estimate)
   - assumption: Equipartition between cosmic-ray and magnetic energy density; alpha_thin = 0.5 (exponent 2/7)  
  > "We note that the exponent $2/7$ only holds for $\upalpha_\textrm{thin} = 0.5$ (cite: Beck05)." (Magnetic field estimate)
   - fitting: _not stated_
   - validation: Uncertainties by standard error propagation; B_SSA and B_eq agree within errors; B_SSA very sensitive to nu_m  
  > "The uncertainties were calculated through standard error propagation." (Insights from the synchrotron spectrum); "An increase or decrease of a few GHz would vary the value of $B_\textrm{SSA}$ by two orders of magnitude." (Magnetic field estimate)
6. **Estimate rotation measure and coherent field lower limit**: RM from the gradient of single-dish EVPA versus wavelength squared; lower limit on ordered field from RM = 8.1e5 integral n_e B dl with path length psi x theta  
  > "by determining the gradient of the EVPAs as a function of the wavelength squared (cite: Kim19)" (Model interpretation); "The path length of integration through the plasma is $\textrm{d}l$ and can be approximated by $\uppsi\times\uptheta$." (Magnetic field estimate)
   - parameter: n_e = 3e4 cm^-3 (Scharwaechter13)  
  > "which we set to $n_\textrm{e}=3\times10^4\,\textrm{cm}^{-3}$ (cite: Scharwaechter13)" (Magnetic field estimate)
   - assumption: Faraday rotation external to the emitting region  
  > "This computation rests on the assumption that the Faraday screen is external." (Dimensionless magnetic flux)
   - fitting: _not stated_
   - validation: Field lower limit consistent with B_eq and B_SSA  
  > "which is consistent as a lower limit to our calculations of $B_\textrm{eq}$ and $B_\textrm{SSA}$." (Magnetic field estimate)
7. **Compute mass-accretion rate and dimensionless magnetic flux to test the MAD state**: Mdot from RM via Marrone06 Eq. 9 for CDAF (beta=0.5) and ADAF (beta=1.5); phi from jet power relation of Tchekhovskoy10 with a* = 1; compared with phi_max = 50  
  > "To determine the mass-accretion rate, we use Eq. 9 from (cite: Marrone06)" (Dimensionless magnetic flux); "Values above the saturation value $\upphi_\textrm{max} = 50$ indicate that the jet is in a magnetically arrested state" (Physical consequences)
   - parameter: L_Edd ~ 1e47 erg/s, epsilon = 0.1, r_out ~ 1e5 R_s, r_in ~ 90 R_s, RM = 6.06e6 rad/m^2  
  > "Using $L_\textrm{Edd} \sim 10^{47}\,\textrm{erg\,s}^{-1}$ (cite: Plambeck14), $\epsilon=0.1$, $r_\textrm{out}\sim10^5\,R_\textrm{s}$ (cite: Nagai17)" (Dimensionless magnetic flux)
   - parameter: kappa = 0.05; P_jet = 1.5e44 erg/s; a* = 1  
  > "$\upkappa=0.05$ is a constant depending on the initial field geometry." (Dimensionless magnetic flux); "Thus, setting $a_*=1$, we computed a range of $\upphi=41-93$." (Dimensionless magnetic flux)
   - assumption: Accretion flow dominates the Faraday rotation; viewing angle ~40 deg  
  > "Our analysis described in Appendix [9](#sec:AppMagFieldM) is based on the assumption that the accretion flow is dominant." (Physical consequences)
   - fitting: _not stated_
   - validation: RM would have to be underestimated by more than an order of magnitude for phi to equal the MAD saturation value  
  > "We note here that the RM would need to be underestimated by more than an order of magnitude" (Dimensionless magnetic flux)

## Software

- **EHT-HOPS** : Fringe fitting and post-processing of EHT data  
  > "including the `EHT-HOPS` fringe-fitting and post-processing pipeline (cite: Blackburn19)." (Data description and analysis)
- **polsolve** : Antenna D-term calibration of the 86 GHz GMVA data  
  > "The antenna instrumental polarisation calibration (D-terms) was performed using the software `polsolve` (cite: MartiVidal21)" (Data description and analysis)
- **CLEAN** : Imaging of the 86 GHz GMVA data  
  > "the data were imaged using the `CLEAN` algorithm (cite: Shepherd94; Shepherd95)." (Data description and analysis)
- **eht-imaging** : Forward modelling of the EHT data with Gaussian components  
  > "We used the forward modelling `eht-imaging` software (cite: Chael16)" (Modelling the EHT data)
- **SciPy** : Heuristic optimisation for the best-fit model  
  > "leveraged heuristic optimisation tools implemented in `SciPy` (cite: 2020SciPy-NMeth)" (Modelling the EHT data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Net linear fractional polarisation of compact region (m_net) | 17.0 | +/-3.9 | % | 2 | we determined the net linear fractional polarisation in the compact region to be $m_\textrm{net}=(17.0\pm 3.9)\%$. |
| Number of circular Gaussian components in compact region | 3 (core C, east E, west W) | not stated | dimensionless | 2 | This region is best fitted by three circular Gaussian components |
| Turnover frequency nu_m | 113 | +/-4 | GHz | 4 | $\upnu_\textrm{m} = (113\pm 4)\,\textrm{GHz}$ (cite: Tuerler00) |
| Fitted spectrum multiplication constant S_0 | 5.7 | +/-0.3 | Jy | 4 | $S_0=5.7\pm 0.3\,\textrm{Jy}$ is a multiplication constant, determined from the fit |
| Core brightness temperature T_B | 3.6e11 | +/-1.5e11 | K | 5 | We computed a core brightness temperature of $T_\textrm{B}=(3.6\pm 1.5)\times 10^{11}\,\textrm{K}$ |
| Synchrotron self-absorption magnetic field B_SSA | 2.9 | +/-1.6 | G | 5 | we computed $B_\textrm{SSA} = (2.9\pm 1.6)\,\textrm{G}$ using Eq. 2 from (cite: Marscher83) |
| Equipartition magnetic field B_eq | 5.2 | +/-0.6 | G | 5 | We also calculated an equipartition magnetic field strength of $B_\textrm{eq} = (5.2\pm 0.6)\,\textrm{G}$. |
| Equipartition Doppler factor | 1.5 | +/-0.4 | dimensionless | 5 | The equipartition Doppler factor is $\updelta_\textrm{eq} = 1.5\pm 0.4$ |
| Rotation measure (single-dish, quasi-simultaneous) | 6.06e6 | +/-0.01e6 | rad/m^2 | 6 | We find that $\textrm{RM} = (6.06\pm 0.01)\times 10^6\,\textrm{rad/m}^2$ by determining the gradient of the EVPAs as a function of the wavelength squared |
| Lower limit of ordered field from RM, B_parallel | 4.7 | +/-0.6 | mG | 6 | Using these values, $B^\textrm{tot}_\parallel = 4.7\pm 0.6\,\textrm{mG}$ |
| Mass-accretion rate (CDAF, beta = 0.5 / ADAF, beta = 1.5) | 0.3e-3 / ~1.1e-3 | not stated | Msun/yr | 7 | yields $\dot{M}=0.3\times10^{-3}M_\odot\,\textrm{yr}^{-1}$ for $\upbeta=0.5$ and $\dot{M}\sim1.1\times10^{-3}M_\odot\,\textrm{yr}^{-1}$ $\upbeta=1.5$. |
| Accretion rate in Eddington units | ~1e-5 to 1e-4 | not stated | Mdot_Edd | 7 | corresponds to $\dot{M} \sim 10^{-5}-10^{-4}\dot{M}_\textrm{Edd}$ |
| Dimensionless magnetic flux phi | 41-93 | not stated | dimensionless | 7 | we find that the dimensionless magnetic flux $\upphi = 41-93$ |

## Qualitative findings

- The east-west elongated core structure persists at 1.3 mm and at lower frequencies  
  > "also persists at 1.3 mm, and in lower frequencies" (Insights from the synchrotron spectrum)
- Fractional polarisation increases markedly at 228 GHz, indicating a transition to the optically thin regime  
  > "it is evident that there is a significant increase at 228 GHz, indicating a transition in the accretion flow to the optically thin regime." (Results)
- Steeply negative spectral slope at 228 GHz  
  > "We report a steeply negative slope of the spectrum at 228 GHz." (abstract)
- Components E and W are highly polarised, pointing to Case I (double rail) rather than jet and counter-jet, but this is speculative  
  > "are highly linearly polarised (20-80%)" (Model interpretation); "However, we note that this interpretation remains speculative, given the uncertainties." (Model interpretation)

## Claim tuples

- H: Does the compact region of 3C 84 host an ordered magnetic field detectable in 228 GHz polarimetry? | E: Gaussian model fit of EHT 228 GHz amplitudes, closure phases and fractional polarisation | R: Three components resolved; net fractional polarisation 17.0 +/- 3.9 % | F: Highly ordered, strong magnetic field around the central black hole | **supported**
- H: Is the compact region in equipartition, and what are its turnover frequency and magnetic field? | E: Turnover-frequency fit to multi-frequency component fluxes, then B_SSA and B_eq from standard prescriptions | R: nu_m = 113 +/- 4 GHz, B_SSA = 2.9 +/- 1.6 G, B_eq = 5.2 +/- 0.6 G, T_B = 3.6e11 K | F: The system is consistent with equipartition | **supported**
- H: Is jet launching in 3C 84 consistent with a MAD ADAF around a rapidly rotating black hole? | E: Dimensionless magnetic flux phi from RM-derived accretion rate and jet power, compared with phi_max = 50 | R: phi = 41-93 for a* = 1; high spin and beta = 1.5 give values near phi_max | F: Preference for high spin and ADAF in a magnetically arrested state | **partially**
- H: Do the 228 GHz component positions match lower-frequency VLBI structure? | E: Template matching of the 228 GHz model to 15, 43 and 86 GHz data | R: Structure recovered at 86 and 43 GHz, blended at 15 GHz | F: Component positions are compatible with those seen in low-frequency VLBI since 2017-2018 | **supported**

## Reasoning

- Why this data: Studying the central engine needs VLBI above 86 GHz  
  > "A detailed investigation of the central engine region necessitates the use of very-long-baseline interferometry (VLBI) above the hitherto available maximum frequency of 86 GHz." (abstract)
- Why this method: Geometric Gaussian model fitting because the (u,v) coverage is too sparse for imaging  
  > "We modelled the EHT data with circular Gaussian components, because the $(u,v)$ coverage is too sparse to reconstruct an image from it." (Modelling the EHT data)
- Alternative: Two-component (2g) model rejected because it cannot reproduce closure phases in a joint fit  
  > "it is not capable of reproducing the closure phase measurements in a joint fit to all data products" (Modelling the EHT data)
- Alternative: Elliptical Gaussians not used, to reduce degrees of freedom  
  > "Circular instead of elliptical Gaussian components were preferred in order to reduce the number of degrees of freedom." (Modelling the EHT data)
- How they decided it was enough: _not stated_
- Limitation (authors): Sparse (u,v) coverage leaves large possibly unaccounted model uncertainties  
  > "Moreover, our models still contain large uncertainties due to the sparsity of the $(u, v)$ coverage, which may not be fully accounted for." (Insights from the synchrotron spectrum)
- Limitation (authors): No polarimetric leakage calibration; absolute EVPA calibration challenging  
  > "The dominant systematic uncertainty in the linear polarisation analysis results comes from the lack of the polarimetric leakage calibration" (Additional methodology comments); "the absolute EVPA calibration was found to be challenging and dependent on additional assumptions" (Additional methodology comments)
- Limitation (authors): B_SSA very sensitive to nu_m  
  > "We point out that the $B_\textrm{SSA}$ calculation is strongly impacted by the value of $\upnu_\textrm{m}$." (Magnetic field estimate)
- Caveat (inferred, ours): Only five stations and one night with an asymmetric (u,v) plane; component number and positions are model dependent (3g chosen despite mild over-fitting)
- Caveat (inferred, ours): Polarisation uses only fractional amplitudes, no EVPA or leakage calibration, so the ordered-field inference rests on |m| alone
- Caveat (inferred, ours): Template matching joins epochs up to about three weeks apart for a variable source
- Caveat (inferred, ours): B_SSA depends on nu_m to a high power, so a few GHz shifts change it by orders of magnitude
- Caveat (inferred, ours): MAD conclusion needs RM from single-dish applied to the compact region and an external Faraday screen assumption

## Reproducibility

- Data public (paper): VLBA 15 and 43 GHz epochs described as publicly available; public status of the EHT 2017 3C 84 data not stated  
  > "we used the publicly available Very Long Baseline Array (VLBA) epochs from April 22, 2017 at 15 GHz (cite: Lister18)" (Data description and analysis)
- Products in archive: _not stated_
- Missing: EHT 2017 calibrated 3C 84 visibilities (location and version)
- Missing: Optimiser choice, error function, starting points and bounds of the Gaussian fits
- Missing: Image-domain measurements of component flux and polarisation at 15, 43 and 86 GHz
- Missing: Single-dish EVPA values per wavelength for the RM fit
- Missing: Exact data selection and weights in the turnover-frequency fit
- Data volume (inferred): Calibrated EHT visibilities for one ~70 min track are small (well under 1 GB); raw VLBI data are TB-scale; ALMA is only a phased station, no standalone ALMA cubes involved
- Score (inferred): 2/5, Scale 1-5. Recipe is described but the key EHT visibilities are not stated as public, the fit setup is under-specified, and results depend on a specialised VLBI pipeline.
- Rediscovery candidate: no, EHT data availability is not stated, the fitting setup is incomplete, and the data are VLBI rather than standard ALMA products.

## Links

- Method: EHT19b (EHTC et al. 2019b) (EHT 2017 frequency setup and standard data reduction)
- Method: EHT19c (EHTC et al. 2019c) (Data reduction path and flux density uncertainties)
- Method: Blackburn19 (EHT-HOPS fringe-fitting pipeline)
- Method: Goddi19 (ALMA-based polarimetric calibration)
- Method: EHT21a (EHTC et al. 2021a) (Polarimetric modelling notation, polarimetric gain calibration and D-terms)
- Method: Chael16 (eht-imaging forward modelling)
- Method: Savolainen08 (Template-matching technique)
- Method: MartiVidal21 (polsolve D-term calibration of 86 GHz data)
- Companion: Paraschos22 (86 GHz GMVA epoch used)
- Companion: Kim19 (Spectral indices and RM method adopted)
- Companion: Oh22 (Resolution limit and viewing angle)
- Companion: Paraschos21 (Core shift and magnetic field comparison)
- Companion: Punsly21 (Lower-frequency component structure motivating the 3g model)
- Companion: Giovannini18 (RadioAstron broad core structure)
- Companion: EHT22a (EHTC et al. 2022a) (EHT 2017 campaign reference)
- Related: EHT 2017 campaign
- Related: POLAMI
- Related: QUIVER
- Related: VLBA-BU-BLAZAR monitoring program
- Related: GMVA

## Checks

```json
{
 "quotes": 130,
 "quotes_ok": 130,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 121,
  "stated": 86,
  "rate": 0.711
 },
 "evidence_ok": true
}
```
