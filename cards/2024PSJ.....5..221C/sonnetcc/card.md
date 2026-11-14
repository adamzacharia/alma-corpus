# Evidence for Surprising Heavy Nitrogen Isotopic Enrichment in Comet 46P/Wirtanen's Hydrogen Cyanide

`2024PSJ.....5..221C` | The Planetary Science Journal 2024 | first author: Cordiner, M. A. | arXiv: 2409.05711 | DOI: 10.3847/PSJ/ad7829

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: Derive the 12C/13C and 14N/15N ratios in HCN in the coma of Jupiter-family comet 46P/Wirtanen from ACA observations of HCN, H13CN and HC15N, using non-LTE radiative transfer modeling  
  > "The data were analyzed using the SUBLIME non-LTE radiative transfer code to derive $^{12}$C/$^{13}$C and $^{14}$N/$^{15}$N ratios." (abstract)
- Target **Comet 46P/Wirtanen**: coordinates _not stated_; z/distance around 0.1 au from Earth (0.09-0.12 au geocentric, by date); 1.06-1.07 au from the Sun  
  > "when the comet was around 0.1 au from Earth and 1.06–1.07 au from the Sun" (Observations); distance from _not stated_

## Data provenance

- ALMA projects: 2018.1.01114.S
- bands: Band 6 and 7  
  > "using the Band 6 and 7 receivers" (Observations)
- frequencies and spectral setup: HCN J=4-3 at 354.505477 GHz (Band 7); HC15N J=3-2 at 258.156996 GHz and H13CN J=3-2 at 259.011798 GHz plus CH3OH 5_K-4_K band at 241.7-241.9 GHz (Band 6); spectral resolution 122 kHz (HCN), 977 kHz (HC15N, H13CN), 244 kHz (CH3OH)  
  > "Multiple lines of the CH$_3$OH $J_K=5_K-4_K$ band were observed in the range 241–242 GHz in order to derive the coma kinetic temperature." (Observations); "354.505477" (Table 1); "258.156996" (Table 1)
- continuum bandwidth: _not stated_
- arrays: Atacama Compact Array (ACA), 12 x 7 m antennas  
  > "This study focuses on the Atacama Compact Array (ACA) data, which incorporated $12\times7$ m antennas covering baselines in the range 9-50 m." (Observations)
- configurations: _not stated_
- baselines: 9-50 m  
  > "which incorporated $12\times7$ m antennas covering baselines in the range 9-50 m" (Observations)
- angular resolution: 4.5'' x 2.8'' at 354 GHz (HCN); 7.6'' x 4.1'' for HC15N and H13CN; 7.0'' x 4.2'' for CH3OH  
  > "the resulting synthesized beam size (angular resolution) was $\theta_B=4.5''\times2.8''$ at 354 GHz" (Observations)
- max recoverable scale: Structures less than lambda/D, with D = 9 m minimum antenna separation (no angular value given)  
  > "the interferometer is only sensitive to structures less than $\lambda/D$ in spatial extent, where $\lambda$ is the observed wavelength and $D$ is the minimum antenna separation (9 m in this case)" (Results)
- sensitivity: sigma = 4.7 mJy per channel for HC15N; integrated-line statistical errors derived from the noise inside a +-90 km/s region adjacent to each line  
  > "the four spectral channels that make up the line peak are all at a significance of greater than $3\sigma$ (where $\sigma=4.7$ mJy)" (Results); "with $\pm1\sigma$ statistical errors derived from the actual noise level inside a $\pm90$ km s$^{-1}$ region adjacent to each spectral line" (Observations)
- time on source: _not stated_
- observing dates: 2018 December 2-7 (HCN 2018-12-02; HC15N, H13CN, CH3OH 2018-12-07)  
  > "Observations of comet 46P/Wirtanen were conducted using ALMA during 2018 December 2-7" (Observations)
- pi or archival as stated: Data observed and previously presented by Cordiner et al. 2023 (cite: cor23); this paper analyses the ACA part  
  > "which was observed by (cite: cor23) using the Atacama Large Millimeter/submillimeter Array (ALMA) during its exceptional 2018 apparition" (Introduction)
- Line: HCN J=4-3 (354.505477 GHz (strongest hyperfine component))
- Line: H13CN J=3-2 (259.011798 GHz (strongest hyperfine component))
- Line: HC15N J=3-2 (258.156996 GHz (strongest hyperfine component))
- Line: CH3OH J_K = 5_K-4_K band (14 detected transitions) (241.7-241.9 GHz)
- Other facility **SOHO (Ly-alpha water production rates)**: H2O production rates at the observation times, via cubic spline interpolation of measurements by Combi et al. 2020  
  > "H$_2$O production rates for comet 46P ($Q({\rm H_2O})$) were obtained for our observation times from cubic spline interpolation of the SOHO Ly-$\alpha$-derived measurements by (cite: com20)" (Results)
- Other facility **IRAM 30-m**: Comparison tentative HC15N detection in 46P giving HCN/HC15N of 77+-26 (Biver et al. 2021)  
  > "A tentative ($3\sigma$) detection of HC$^{15}$N was also obtained in comet 46P by (cite: biv21) using the IRAM 30-m telescope" (Discussion)
- Other facility **VLT (ultraviolet spectroscopy)**: Comparison CN/C15N ratio of 150+-30 one day after the HC15N observation (Moulane et al. 2023)  
  > "(cite: mou23) measured a nominal CN/C$^{15}$N ratio of $150\pm30$ using VLT ultraviolet spectroscopy" (Discussion)
- External data: Spectral line frequencies from the CDMS database  
  > "Spectral line frequencies were obtained from the CDMS database (cite: end16)." (Table 1) [from (cite: end16)]
- External data: HCN-H2O collision rates, assumed to apply to all three HCN isotopologues  
  > "HCN–H$_2$O collision rates are from (cite: dub19), and were assumed to apply equally for all three HCN isotopologues." (Results) [from (cite: dub19)]
- External data: CH3OH-H2O collision rates assumed equal to CH3OH-H2 rates  
  > "collision rates between CH$_3$OH and H$_2$O were assumed to be the same as CH$_3$OH with H$_2$ (cite: rab10)" (Results) [from (cite: rab10)]
- External data: Molecular data for rovibrational solar pumping of HCN and CH3OH (HITRAN and Planetary Spectrum Generator databases)  
  > "Rovibrational pumping due to the solar radiation field was calculated using molecular data for HCN and CH$_3$OH from the HITRAN and Planetary Spectrum Generator databases (cite: cor23; vil18)." (Results) [from (cite: cor23; vil18)]
- External data: H2O production rates Q(H2O) of comet 46P at the observation times (SOHO Ly-alpha derived)  
  > "H$_2$O production rates for comet 46P ($Q({\rm H_2O})$) were obtained for our observation times from cubic spline interpolation of the SOHO Ly-$\alpha$-derived measurements by (cite: com20)" (Results) [from (cite: com20)]
- External data: Q(HCN)/Q(H2O) = 0.0020+-0.0001 from six infrared measurements, used to argue the HCN/H2O ratio was constant  
  > "the error-weighted mean was $Q({\rm HCN})$/$Q({\rm H_2O})$ = $0.0020\pm0.0001$" (Discussion) [from (cite: bon21; kha23)]
- External data: Expected HCN/H13CN ratio of about 90 from 12C/13C in diverse Solar System bodies, used for the conservative HCN abundance  
  > "the expected HCN/H$^{13}$CN ratio ($\approx90$; based on measurements of $^{12}$C/$^{13}$C ratios in a diverse range of comets and other solar system bodies; (cite: nom23))" (Discussion) [from (cite: nom23)]
- External data: Error-weighted average HCN/HC15N of 146+-11 in four previous comets  
  > "the (error-weighted) average of prior HCN/HC$^{15}$N measurements in four previous comets is $146\pm11$ (cite: boc08; biv16)" (Discussion) [from (cite: boc08; biv16)]
- External data: Weighted average 14N/15N of 144+-3 from HCN, CN and NH2 in 31 comets  
  > "The weighted average $^{14}$N/$^{15}$N ratio for HCN, CN and NH$_2$ in a sample of 31 comets is $144\pm3$ (cite: hil17)" (Discussion) [from (cite: hil17)]
- External data: Terrestrial and solar 14N/15N reference values of 273 and 459  
  > "compared to the bulk terrestrial and Solar values of 273 and 459, respectively (cite: nie50; mar11)" (Discussion) [from (cite: nie50; mar11)]
- Simulation/model as data: Initial best-fit SUBLIME model image cubes, spectrally integrated and processed with CASA simobserve, used to derive interferometric flux loss factors  
  > "These were derived based on initial best-fit SUBLIME model image cubes" (Results)

## Processing

### Calibration

- pipeline or manual: Flagging and calibration as described by Cordiner et al. 2023 (details not given here)  
  > "Data flagging, calibration and continuum subtraction were performed as described by (cite: cor23)." (Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 10% uncertainty on Q(HCN) and Q(HC15N) for possible absolute ACA flux scale inaccuracies  
  > "combined with a further 10% uncertainty on $Q({\rm HCN})$ and $Q({\rm HC^{15}N})$ to account for possible inaccuracies in the absolute ACA flux scale" (Discussion)
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations)
- deconvolver: Hogbom  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations)
- weighting robust: natural weighting  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations)
- uv taper: _not stated_
- cell size: 0.5''  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations)
- image size: _not stated_
- masking: 30''-diameter circular mask centered on the comet; flux threshold of twice the RMS noise  
  > "Deconvolution was carried out within a $30''$-diameter circular mask centered on the comet, with a flux threshold of twice the RMS noise level ($\sigma$)." (Observations)
- multiscale scales: _not stated_
- continuum subtraction: Performed as described by Cordiner et al. 2023 (details not given here)  
  > "Data flagging, calibration and continuum subtraction were performed as described by (cite: cor23)." (Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 4.5'' x 2.8'' at 354 GHz (HCN)  
  > "the resulting synthesized beam size (angular resolution) was $\theta_B=4.5''\times2.8''$ at 354 GHz" (Observations)
- final rms: _not stated_

### Inherited from earlier work

- Data flagging, calibration and continuum subtraction  
  > "Data flagging, calibration and continuum subtraction were performed as described by (cite: cor23)." (Observations) [from Cordiner et al. 2023 (cite: cor23)]
- RMS noise on each spectrum multiplied by 1.29 to account for correlation between adjacent channels from the ACA correlator  
  > "the RMS noise measurement on each spectrum was multiplied by a factor of 1.29, following (cite: nix20)" (Results) [from Nixon et al. 2020 (cite: nix20)]
- SUBLIME non-LTE coma radiative transfer code (1D version)  
  > "Spectral modeling was performed using the spherically symmetric (1D) version of SUBLIME: a time-dependent, non-LTE radiative transfer code for cometary comae (cite: cor22)" (Results) [from Cordiner et al. 2022 (cite: cor22)]
- Molecular data for solar rovibrational pumping of HCN and CH3OH  
  > "Rovibrational pumping due to the solar radiation field was calculated using molecular data for HCN and CH$_3$OH from the HITRAN and Planetary Spectrum Generator databases (cite: cor23; vil18)." (Results) [from (cite: cor23; vil18)]

### Not stated but needed to reproduce (our reading)

- Flux, bandpass and phase calibrators and the calibration route (manual or pipeline) and CASA version: all deferred to Cordiner et al. 2023
- How the comet ephemeris tracking and the continuum subtraction (line-free channels, order) were done
- tclean details: number of iterations, absolute threshold in mJy, channel width and velocity regridding of the cubes, execution blocks combined
- SUBLIME input setup: gas temperature and outflow velocity profiles, parent photodissociation rates, grid, H2O collision-partner treatment, hyperfine line list, and exact sky position and time used for each line
- Settings of the CASA simobserve runs used to derive the 0.79 and 0.73 flux loss factors (antenna configuration, integration times, number of iterations to the initial best-fit model)
- How the quoted uncertainty of 67+-17 (Conclusion) versus 67+-16 and 67+-20 (Discussion) was computed, and the origin of the (9.27+-2.88)e-3 HCN abundance given in the Discussion (the Table gives 9.17e-4)
- Position-extraction aperture: spectra are taken from the (0,0) pixel of each map, without aperture size stated
- Whether and how primary-beam correction was applied

## Analysis recipe

1. **Image ACA cubes of the targeted lines**: CASA tclean (Hogbom) with natural weighting after flagging, calibration and continuum subtraction as in Cordiner et al. 2023  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations); "Data flagging, calibration and continuum subtraction were performed as described by (cite: cor23)." (Observations)
   - software: CASA tclean
   - parameter: pixel size 0.5''; 30''-diameter circular mask; threshold 2 x RMS  
  > "Deconvolution was carried out within a $30''$-diameter circular mask centered on the comet, with a flux threshold of twice the RMS noise level ($\sigma$)." (Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Make integrated flux maps and extract spectra**: Integrate over +-1.2 km/s about each line rest velocity (ranges for weak lines set from the HCN line width); extract spectra at the (0,0) position of each map, with the origin at the HCN peak for HCN and the CH3OH peak for HC15N and H13CN  
  > "integrated over velocity ranges $\pm1.2$ km s$^{-1}$ with respect to the line rest velocities" (Results); "Spectra were extracted from the (0,0) position in each map" (Results)
   - parameter: For the weaker lines the integration ranges follow the velocity width of the HCN line  
  > "For the weaker (HC$^{15}$N and H$^{13}$CN) lines, the spectral integration ranges were determined based on the velocity width of the stronger (HCN) line." (Results)
   - fitting: _not stated_
   - validation: Detections judged against the 3 sigma criterion for a source of known position; HC15N peak coincides with the CH3OH-derived nucleus position and line profile matches the HCN rest velocity and FWHM  
  > "a detection can be considered real if appears above the $3\sigma$ level for a source with a known location" (Results); "the HC$^{15}$N emission peak coincides with the known location of the comet’s nucleus" (Results)
3. **Correct for interferometric flux loss**: Initial best-fit SUBLIME model cubes were spectrally integrated, run through CASA simobserve for each line's sky position and observation time, and cleaned and deconvolved as the data; the resulting loss factors were applied to the measured spectra  
  > "These were derived based on initial best-fit SUBLIME model image cubes" (Results); "the measured ACA spectra were corrected for interferometric flux loss factors of 0.79 for HCN and 0.73 for HC$^{15}$N and H$^{13}$CN" (Results)
   - software: SUBLIME, CASA simobserve
   - parameter: flux loss factors 0.79 (HCN) and 0.73 (HC15N, H13CN)  
  > "the measured ACA spectra were corrected for interferometric flux loss factors of 0.79 for HCN and 0.73 for HC$^{15}$N and H$^{13}$CN" (Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive coma kinetic temperature from CH3OH**: Least-squares fit of SUBLIME model to the CH3OH 5_K-4_K spectrum  
  > "$T_{kin}=93\pm3$ K was derived using a least-squares fit to the CH$_3$OH spectrum" (Results)
   - software: SUBLIME
   - assumption: CH3OH-H2O collision rates taken equal to CH3OH-H2 rates  
  > "collision rates between CH$_3$OH and H$_2$O were assumed to be the same as CH$_3$OH with H$_2$ (cite: rab10)" (Results)
   - assumption: Spherically symmetric (1D) coma  
  > "the 1D version of the model was found to provide a sufficiently good fit to these ACA data" (Results)
   - fitting: Least-squares fit  
  > "$T_{kin}=93\pm3$ K was derived using a least-squares fit to the CH$_3$OH spectrum" (Results)
   - validation: _not stated_
5. **Fit HCN line profile for coma outflow velocity and Doppler shift**: Fit the well-resolved HCN J=4-3 profile; resulting values fixed in later fits to the isotopologue lines  
  > "these values were used in subsequent fits to the spectrally less well resolved (and lower signal-to-noise) HCN isotopologue lines" (Results)
   - software: SUBLIME
   - parameter: outflow velocity 0.53+-0.01 km/s; Doppler shift -0.097+-0.006 km/s  
  > "a coma outflow velocity of $0.53\pm0.01$ km s$^{-1}$, and Doppler shift of $-0.097\pm0.006$ km s$^{-1}$ was derived" (Results)
   - assumption: HCN-H2O collision rates identical for all three isotopologues; hyperfine components in equilibrium line-strength ratios  
  > "Hyperfine structure was included in the model spectra for all three HCN isotopologues, assuming equilibrium line-strength ratios among the hyperfine components in a given $J$ state." (Results)
   - fitting: _not stated_
   - validation: Optical depth check: line largely optically thin (max 0.2 at peak, mean 0.04 in beam), hyperfine satellites too weak to be detected  
  > "The maximum optical depth of our radiative transfer model at the HCN central peak is 0.2" (Results); "the mean optical depth inside the ACA beam is only 0.04" (Results)
6. **Fit production rates and abundances of HCN, HC15N and H13CN**: Least-squares fit of SUBLIME 1D model spectra to the flux-loss-corrected spectra; abundances relative to H2O using Q(H2O) from SOHO Ly-alpha  
  > "Best fitting production rates and abundances (relative to H$_2$O) for the three HCN isotopologues are given in Table [\[tab:results\]](#tab:results)." (Results); "Formal ($1\sigma$) uncertainties were derived from the diagonal elements of the covariance matrix of the least-squares fit." (Results)
   - software: SUBLIME
   - parameter: RMS noise multiplied by 1.29 for adjacent-channel correlation  
  > "the RMS noise measurement on each spectrum was multiplied by a factor of 1.29, following (cite: nix20)" (Results)
   - assumption: Q(H2O) from cubic spline interpolation of SOHO Ly-alpha measurements, taken as applicable at the ACA spatial resolution  
  > "implies that the SOHO water production rates should be applicable at the spatial resolution of our ACA data" (Results)
   - fitting: Least-squares; 1 sigma errors from the diagonal of the covariance matrix  
  > "Formal ($1\sigma$) uncertainties were derived from the diagonal elements of the covariance matrix of the least-squares fit." (Results)
   - validation: Q(H2O) cross-checked against SOFIA (8e27 s-1) and IRTF (7e27 s-1) values from other dates  
  > "These $Q({\rm H_2O})$ values are consistent with the average water production rate of $8\times10^{27}$ s$^{-1}$ measured by (cite: lis19) using the SOFIA telescope" (Results)
7. **Derive isotopic ratios and propagate uncertainties**: Ratios of production rates; uncertainties extended with 10% Q(H2O) scatter and 10% flux scale error added in quadrature; conservative alternative using H13CN abundance and an assumed HCN/H13CN of 90; delta15N relative to the terrestrial standard  
  > "gives a value of HCN/HC$^{15}$N = $67\pm20$." (Discussion); "This leads to a more conservative HCN/HC$^{15}$N ratio (and uncertainty) of $68\pm27$." (Discussion)
   - parameter: Q(H2O) RMS scatter 7.6e26 s-1 (~10%) about the linear trend between 2018-11-28 and 2018-12-11  
  > "which amount to an RMS of $7.6\times10^{26}$ s$^{-1}$ ($\sim10$%) with respect to the best-fitting linear trend in $Q({\rm H_2O})$ between 2018-11-28 and 2018-12-11" (Discussion)
   - assumption: HCN/H2O abundance constant between observations (std of Q(HCN)/Q(H2O) is 6%), so its variation is negligible  
  > "It is therefore reasonable to assume that variations in the comet’s HCN/H$_2$O ratio contribute a negligible source of uncertainty to our result." (Discussion)
   - assumption: Expected HCN/H13CN of about 90 in the conservative estimate  
  > "the expected HCN/H$^{13}$CN ratio ($\approx90$" (Discussion)
   - fitting: _not stated_
   - validation: Compared with IRAM 30-m HCN/HC15N of 77+-26 in 46P and with the 144+-3 average of 31 comets  
  > "leading to an HCN/HC$^{15}$N ratio of $77\pm26$" (Discussion); "is $2.8\sigma$ less than the weighted average of 144" (Discussion)

## Software

- **CASA** : tclean imaging and simobserve simulated observations for flux loss  
  > "Imaging was performed using the CASA `tclean` (Högbom) algorithm with natural weighting and a pixel size of $0.5''$." (Observations); "processed using CASA `simobserve` according to the particular sky position and observation time of each line" (Results)
- **SUBLIME** 1D (spherically symmetric) version: Time-dependent non-LTE radiative transfer modeling of cometary comae to fit spectra and derive production rates, abundances and Tkin  
  > "Spectral modeling was performed using the spherically symmetric (1D) version of SUBLIME: a time-dependent, non-LTE radiative transfer code for cometary comae (cite: cor22)" (Results)
- **Planetary Spectrum Generator** : Source of molecular data for solar rovibrational pumping (with HITRAN)  
  > "from the HITRAN and Planetary Spectrum Generator databases (cite: cor23; vil18)" (Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HCN J=4-3 integrated line intensity | 2,806 | +-37 | mJy km/s | 2 | $2,806\pm37$ |
| HC15N J=3-2 integrated line intensity | 41 | +-9 | mJy km/s | 2 | $41\pm9$ |
| H13CN J=3-2 integrated line intensity | 32 | +-10 | mJy km/s | 2 | $32\pm10$ |
| CH3OH 5_K-4_K summed integrated line intensity | 3,472 | +-68 | mJy km/s | 2 | $3,472\pm68$ |
| Detection significance of HCN, HC15N, H13CN | 76 sigma, 4.6 sigma, 3.2 sigma | not stated | dimensionless | 2 | HCN is detected at a high significance ($76\sigma$), while HC$^{15}$N and H$^{13}$CN are detected at $4.6\sigma$ and $3.2\sigma$, respectively. |
| Interferometric flux loss factor, HCN | 0.79 | not stated | dimensionless | 3 | interferometric flux loss factors of 0.79 for HCN and 0.73 for HC$^{15}$N and H$^{13}$CN |
| Interferometric flux loss factor, HC15N and H13CN | 0.73 | not stated | dimensionless | 3 | interferometric flux loss factors of 0.79 for HCN and 0.73 for HC$^{15}$N and H$^{13}$CN |
| Gas kinetic temperature (beam-averaged) | 93 | +-3 | K | 4 | $T_{kin}=93\pm3$ K was derived using a least-squares fit to the CH$_3$OH spectrum |
| Coma outflow velocity | 0.53 | +-0.01 | km/s | 5 | a coma outflow velocity of $0.53\pm0.01$ km s$^{-1}$ |
| Doppler shift of the HCN line | -0.097 | +-0.006 | km/s | 5 | Doppler shift of $-0.097\pm0.006$ km s$^{-1}$ was derived |
| HCN production rate (2018-12-02) | 5.20e24 | +-0.09e24 | s-1 | 6 | $(5.20\pm0.09)\times10^{24}$ |
| HC15N production rate (2018-12-07) | 1.03e23 | +-0.25e23 | s-1 | 6 | $(1.03\pm0.25)\times10^{23}$ |
| H13CN production rate (2018-12-07) | 7.70e22 | +-2.49e22 | s-1 | 6 | $(7.70\pm2.49)\times10^{22}$ |
| HCN abundance relative to H2O | 9.17e-4 | +-0.16e-4 | dimensionless | 6 | $(9.17\pm0.16)\times10^{-4}$ |
| HC15N abundance relative to H2O | 1.36e-5 | +-0.33e-5 | dimensionless | 6 | $(1.36\pm0.33)\times10^{-5}$ |
| H13CN abundance relative to H2O | 1.03e-5 | +-0.32e-5 | dimensionless | 6 | $(1.03\pm0.32)\times10^{-5}$ |
| HCN/HC15N production rate ratio (statistical errors only) | 67 | +-16 | dimensionless | 7 | the HCN/HC$^{15}$N production rate ratio in comet 46P is $67\pm16$ |
| HCN/H13CN production rate ratio (statistical errors only) | 90 | +-28 | dimensionless | 7 | and the HCN/H$^{13}$CN ratio is $90\pm28$ |
| HCN/HC15N including Q(H2O) scatter and 10% flux-scale error | 67 | +-20 | dimensionless | 7 | gives a value of HCN/HC$^{15}$N = $67\pm20$. |
| HCN/HC15N conservative value (from H13CN abundance and assumed HCN/H13CN of 90) | 68 | +-27 | dimensionless | 7 | This leads to a more conservative HCN/HC$^{15}$N ratio (and uncertainty) of $68\pm27$. |
| HCN/HC15N production rate ratio quoted in the Conclusion | 67 | +-17 | dimensionless | 7 | we derived a HCN/HC$^{15}$N production rate ratio of $67\pm17$ |
| delta15N relative to the terrestrial standard | 3015 | +-1200 | per mil | 7 | = ($3015\pm1200$) (per mil) |
| Significance of 14N/15N below the 144 cometary weighted average | 2.8 | not stated | sigma | 7 | is $2.8\sigma$ less than the weighted average of 144 |
| HCN optical depth: maximum at peak and mean in ACA beam | 0.2 (peak), 0.04 (mean) | not stated | dimensionless | 5 | The maximum optical depth of our radiative transfer model at the HCN central peak is 0.2; the mean optical depth inside the ACA beam is only 0.04 |

## Qualitative findings

- The HCN/H13CN ratio is consistent with a lack of significant 13C fractionation in cometary HCN  
  > "The HCN/H$^{13}$CN ratio is found to be consistent with a lack of significant $^{13}$C fractionation" (abstract)
- HC15N mapped for the first time in a comet; 46P HCN is strongly enriched in 15N compared with solar and terrestrial values, similar to meteoritic hotspots  
  > "allowing HC$^{15}$N to be mapped for the first time in a comet" (Conclusion); "reaching a value similar to those found in the most $^{15}$N-enriched “hotspots” in spatially isolated meteoritic samples" (Conclusion)

## Claim tuples

- H: Is the 14N/15N ratio in HCN of Jupiter-family comet 46P consistent with the roughly 140 found in previous comets? | E: ACA HCN and HC15N observations of 46P modeled with SUBLIME, comparing HCN/HC15N with prior comet measurements | R: HCN/HC15N = 68+-27 (conservative); 2.8 sigma below the 144 cometary average; 67+-20 with Q(H2O) and flux-scale errors | F: 46P HCN is strongly enriched in 15N relative to solar, terrestrial and prior cometary values | **supported**
- H: Does cometary HCN show carbon isotopic fractionation in 46P? | E: H13CN and HCN production rates from SUBLIME fits to ACA data | R: HCN/H13CN = 90+-28 | F: No strong 13C fractionation in cometary HCN, consistent with earlier comets and Solar System values | **supported**
- H: Can Jupiter-family comets reach larger nitrogen isotopic enrichment than previously thought, possibly via isotopically heterogeneous nucleus material? | E: Comparison of the ACA value with IRAM, VLT CN/C15N and meteoritic hotspot values, plus an estimate of the volatile mass within the ACA beam | R: ACA HCN/HC15N is similar to meteoritic hotspots (65+-14) but a VLT CN/C15N of 150+-30 one day later is higher | F: Heterogeneity or a spatially isolated 15N enhancement is proposed as plausible but speculative | **partially**
- H: Is a spherically symmetric optically thin coma model adequate for the ACA HCN data? | E: 1D SUBLIME fits and optical depth evaluation | R: Maximum optical depth 0.2 at the HCN peak and 0.04 mean in the beam | F: HCN J=4-3 is largely optically thin and the 1D model is sufficient | **supported**

## Reasoning

- Why this data: The exceptionally close Earth-comet distance allowed detection of weak lines not normally detectable in Jupiter-family comets; the ACA's short baselines are sensitive to extended coma emission  
  > "The unusually close Earth-comet distance allowed the detection of weak spectral lines not typically detectable in Jupiter family comets from the ground" (Introduction); "The shorter baselines of the ACA compared with the main (12 m) ALMA array make it more sensitive to extended coma emission" (Observations)
- Why this method: A 1D spherically symmetric non-LTE model suffices since cometary HCN data are typically well reproduced by such models  
  > "Considering the cometary HCN data are typically well reproduced by a spherically-symmetric coma model" (Results)
- Alternative: A more conservative HCN abundance and HCN/HC15N from H13CN and an assumed HCN/H13CN of about 90, in case Q(H2O) or HCN/H2O varies strongly with time  
  > "The possibility of more extreme temporal variability in $Q({\rm H_2O})$ (or greater variability in HCN/H$_2$O) as a function of time cannot be ruled out however." (Discussion)
- How they decided it was enough: Detection criterion of 3 sigma for a source with known location, met by HC15N and H13CN  
  > "a detection can be considered real if appears above the $3\sigma$ level for a source with a known location" (Results)
- Limitation (authors): Raw statistical significance of the HC15N and H13CN detections is low  
  > "The raw statistical significance of our HC$^{15}$N and H$^{13}$CN detections is less than optimal" (Results)
- Limitation (authors): HCN and isotopologues were observed on different dates, so variations in Q(H2O) and HCN/H2O enter the uncertainty  
  > "Because HCN and its minor isotopologues were observed in comet 46P on different dates (almost 6 days apart)" (Discussion)
- Limitation (authors): CN may have an additional source beyond HCN photolysis, so CN/C15N need not equal HCN/HC15N  
  > "it should be noted that CN in cometary comae often has an additional source that cannot be explained by HCN photolysis alone" (Discussion)
- Caveat (inferred, ours): HC15N and H13CN detected at only 4.6 sigma and 3.2 sigma, so the headline ratio rests on a few channels
- Caveat (inferred, ours): HCN and the isotopologues are measured on different days with different beams, so the ratio depends on Q(H2O) from SOHO and on flux-loss corrections of 0.79 and 0.73 derived from the same model
- Caveat (inferred, ours): The tabulated HCN abundance (9.17e-4) differs by a factor of 10 from the conservative abundance quoted in the text ((9.27+-2.88)e-3), and the Conclusion quotes 67+-17 against 67+-16 or 67+-20 in the Discussion
- Caveat (inferred, ours): Spherical-symmetry assumption applies although a solar-facing jet is invoked elsewhere for this comet
- Caveat (inferred, ours): Nominal 2.8 sigma deviation from the comet average is modest for a claimed outlier

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging details deferred to Cordiner et al. 2023
- Missing: SUBLIME input model parameters and fitting configuration
- Missing: Flux-loss simulation setup
- Missing: Q(H2O) values are taken from Combi et al. 2020 and must be obtained separately
- Data volume (inferred): ACA execution blocks for one project (2018.1.01114.S), likely a few GB of raw data
- Score (inferred): 3/5, ALMA project code and most imaging choices are given and key numbers are tabulated, but calibration is deferred to a prior paper and the SUBLIME model setup and flux-loss simulations are not fully specified.
- Rediscovery candidate: no, Calibration is deferred to another paper and the non-LTE model configuration and simobserve settings are not given, so the main ratios cannot be redone from this text alone.

## Links

- Method: Cordiner et al. 2023 (cite: cor23) (Describes the flagging, calibration and continuum subtraction and the earlier analysis of the same data)
- Method: Cordiner et al. 2022 (cite: cor22) (Describes the SUBLIME radiative transfer code)
- Method: Nixon et al. 2020 (cite: nix20) (Source of the 1.29 noise correction factor for ACA channel correlation)
- Companion: Cordiner et al. 2023 (cite: cor23) (Earlier presentation of the same ALMA observations of 46P)
- Companion: Biver et al. 2021 (cite: biv21) (IRAM 30-m tentative HC15N detection in 46P)
- Companion: Moulane et al. 2023 (cite: mou23) (VLT CN/C15N measurement in 46P one day after the ACA HC15N observation)
- Related: 2018.1.01114.S

## Checks

```json
{
 "quotes": 132,
 "quotes_ok": 132,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 24,
 "numeric_problems": 0,
 "fill": {
  "facts": 103,
  "stated": 75,
  "rate": 0.728
 },
 "evidence_ok": true
}
```
