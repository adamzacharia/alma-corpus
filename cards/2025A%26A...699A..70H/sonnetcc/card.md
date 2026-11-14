# Investigating the chemical link between H<SUB>2</SUB>CO and CH<SUB>3</SUB>OH within the central molecular zone of NGC 253

`2025A&A...699A..70H` | Astronomy and Astrophysics 2025 | first author: Huang, K.-Y. | arXiv: 2505.16255 | DOI: 10.1051/0004-6361/202554156

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type large_program_or_survey

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Investigate the physical and chemical properties traced by CH3OH and H2CO in NGC 253 and whether the two species are chemically linked  
  > "The aim of the current study is to investigate both the physical and chemical properties traced by and in the nearby starburst galaxy, NGC 253, and investigate whether the two species are chemically linked." (Introduction)
- Target **NGC 253 CMZ (eight GMCs: 1a, 2b, 3, 4, 6, 7, 8a, 9a; GMC 5 and 10 excluded)**: coordinates phase center ICRS 00h47m33.26s, -25d17m17.7s; GMC positions in Table 1  
  > "The nominal phase center of the observations is $\alpha(\rm ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(\rm ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$." (2 Observations and data analysis); "beam-sized ($1.^{\prime\prime}$6 or 28 pc) structures" (4 Non-LTE radiative transfer modeling analysis); z/distance not stated (1.6 arcsec corresponds to 28 pc)  
  > "The nominal phase center of the observations is $\alpha(\rm ICRS)$ = 00$^h$47$^m$33$^s$.26, $\delta(\rm ICRS)$ = $-25^\circ$17$^\prime$17$^{\prime\prime}.7$." (2 Observations and data analysis); "beam-sized ($1.^{\prime\prime}$6 or 28 pc) structures" (4 Non-LTE radiative transfer modeling analysis); distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: ALCHEMI covers Bands 3, 4, 5, 6 and 7 (84.2 to 373.2 GHz rest frequency)  
  > "with rest-frequency coverage from 84.2 to 373.2 GHz, corresponding to the ALMA frequency Bands 3, 4, 5, 6, and 7" (2 Observations and data analysis)
- frequencies and spectral setup: Spectral scan 84.2-373.2 GHz; cube spectral resolution ~10 km/s; common mapped area 50 x 20 arcsec (850 x 340 pc) at PA 65 deg  
  > "A common rectangular area with a size of $50^{\prime\prime} \times 20^{\prime\prime}$ ($850\times340$ pc) at a position angle of $65^\circ$ was imaged to cover the central nuclear region in NGC 253." (2 Observations and data analysis); "The angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ (cite: ALCHEMI_main_2021) and $\sim10$ km s$^{-1}$, respectively." (2 Observations and data analysis)
- continuum bandwidth: _not stated_
- arrays: 12 m Array and Atacama Compact Array (ACA), combined  
  > "after combining the 12 m Array and Atacama Compact Array (ACA) measurements at all frequencies" (2 Observations and data analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.6 arcsec (~28 pc)  
  > "The angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ (cite: ALCHEMI_main_2021) and $\sim10$ km s$^{-1}$, respectively." (2 Observations and data analysis)
- max recoverable scale: 15 arcsec (common to all frequencies)  
  > "A common maximum recoverable angular scale of $15^{\prime\prime}$ was achieved after combining the 12 m Array and Atacama Compact Array (ACA) measurements at all frequencies." (2 Observations and data analysis)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3OH (E- and A-) 39 transitions in several groups (e.g. near 96.74, 157.26, 165.07 GHz); see paper table (96.739360 to 358.605800 GHz (from paper table))
- Line: H2CO (o- and p-) 10 transitions, e.g. 2_12 - 1_11 (140.839500 GHz for 2_12 - 1_11; the 10 transitions span 140.8 to 365.4 GHz (from paper table))
- External data: CH3OH collisional excitation rates (Dagdigian 2023) from EMAA  
  > "The collisional excitation rates used for are from (cite: Dagdigian_2023) while the rates are from (cite: H2CO_mole_data)." (4 Non-LTE radiative transfer modeling analysis) [from (cite: Dagdigian_2023)]
- External data: H2CO collisional excitation rates from LAMDA  
  > "The collisional excitation rates used for are from (cite: Dagdigian_2023) while the rates are from (cite: H2CO_mole_data)." (4 Non-LTE radiative transfer modeling analysis) [from (cite: H2CO_mole_data)]
- External data: CH3OH frequencies and spectroscopic parameters from the JPL catalogue  
  > "Frequencies and spectroscopic parameters have been extracted from the JPL catalogue (cite: Pickett+1998)." (Table notes (CH3OH transitions)) [from (cite: Pickett+1998)]
- External data: H2CO frequencies and spectroscopic parameters from CDMS  
  > "Frequencies and spectroscopic parameters have been extracted from CDMS (cite: Muller+2005; Endres+2016)." (Table notes (H2CO transitions)) [from (cite: Muller+2005; Endres+2016)]
- External data: H2 column densities for GMC 3 to 7 from the 220 GHz continuum, rescaled by 0.63 to the 1.6 arcsec beam  
  > "To derive the methanol and formaldehyde abundances, we used the H$_2$ column densities from (cite: Mangum+2019)." (4.4 Derivation of H2CO and CH3OH abundances); "This resulted in multiplying their $N_{H2}$ by a factor of 0.63." (4.4 Derivation of H2CO and CH3OH abundances) [from (cite: Mangum+2019)]
- External data: N_H2 = (3-10)e22 cm^-2 for GMC 1a, 2b, 8a, 9a (not rescaled)  
  > "For these regions, we used $N_{H2}=(3-10)\times10^{22}$ cm$^{-2}$ (see their Figure 4c)." (4.4 Derivation of H2CO and CH3OH abundances) [from (cite: Harada+2022)]
- External data: HNCO and SiO column densities and filling factors used for comparison abundances  
  > "we used the column densities of HNCO and SiO from (cite: Huang+2023) and of the S-bearing species from (cite: Bouvier+2024)" (Appendix Abundances) [from (cite: Huang+2023)]
- External data: S-bearing species (OCS, H2CS, H2S, CS) column densities and filling factors used for comparison abundances  
  > "we used the column densities of HNCO and SiO from (cite: Huang+2023) and of the S-bearing species from (cite: Bouvier+2024)" (Appendix Abundances) [from (cite: Bouvier+2024)]

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
- masking: Moment images masked below 3 sigma (channel-based) via CubeLineMoment spectral and spatial masks  
  > "images masked below a $3\sigma$ threshold (channel-based)" (2 Observations and data analysis)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12 m Array and ACA combined  
  > "after combining the 12 m Array and Atacama Compact Array (ACA) measurements at all frequencies" (2 Observations and data analysis)
- smoothing: _not stated_
- final beam: 1.6 arcsec (circular 1.6 x 1.6 arcsec used in abundance step)  
  > "The angular and spectral resolution of the image cubes generated from these measurements were $1.^{\prime\prime}6$ (cite: ALCHEMI_main_2021) and $\sim10$ km s$^{-1}$, respectively." (2 Observations and data analysis); "versus $1.6'' \times 1.6''$" (4.4 Derivation of H2CO and CH3OH abundances)
- final rms: _not stated_

### Inherited from earlier work

- Data acquisition, calibration and imaging of the ALCHEMI cubes  
  > "Full details regarding the data acquisition, calibration, and imaging are described in (cite: ALCHEMI_main_2021)." (2 Observations and data analysis) [from (cite: ALCHEMI_main_2021)]
- Cube resolution of 1.6 arcsec  
  > "$1.^{\prime\prime}6$ (cite: ALCHEMI_main_2021)" (2 Observations and data analysis) [from (cite: ALCHEMI_main_2021)]
- CubeLineMoment tool for extracting integrated line intensities  
  > "(cite: Mangum+2019) to extract integrated spectral-line intensities from our data cubes" (2 Observations and data analysis) [from (cite: Mangum+2019)]
- Beam filling factors for HNCO, SiO and S-bearing species taken from earlier non-LTE analyses  
  > "we applied the beam filling factor derived for each region and each species from the non-LTE analyses performed in (cite: Huang+2023) and (cite: Bouvier+2024)" (Appendix Abundances) [from (cite: Huang+2023); (cite: Bouvier+2024)]

### Not stated but needed to reproduce (our reading)

- ALCHEMI imaging and calibration details (CASA version, robust, cell size, deconvolver, continuum subtraction, line-free channels, primary-beam correction) are only in the ALCHEMI main paper
- Which ALCHEMI spectral-window cubes contain each of the 39 CH3OH and 10 H2CO transitions and how they were smoothed to a common 1.6 arcsec beam
- Aperture used to extract integrated intensities at each GMC (white circles in Fig. 1): size and exact extraction method
- CubeLineMoment settings: which bright line was the velocity tracer per cube, spatial mask settings, velocity integration limits
- How the 3 sigma per-channel noise and the intensity uncertainties used in the chi-squared were computed (including any flux-calibration error term)
- RADEX settings: line width, background temperature, treatment of opacity and how line widths were set from the data
- Nautilus settings: number of live points, stopping criterion, number of posterior samples, and how best-fit values and uncertainties were summarised (median, percentiles)
- Numerical N_H2 values per GMC from Mangum+2019 Table 5 and how X range was bounded from the N_H2 range
- How the source size theta_S in the beam filling factor relates to the fitted eta_ff

## Analysis recipe

1. **extract integrated line intensities at GMC positions**: CubeLineMoment spectral and spatial masks give moment 0, 1, 2 maps masked below 3 sigma; transitions selected by SNR and contamination criteria  
  > "to extract integrated spectral-line intensities from our data cubes" (2 Observations and data analysis); "(1) the transition needs to be bright enough, specifically with signal-to-noise ratio (SNR) greater than 3; and (2) no significant contamination from other molecule(s) involved." (2 Observations and data analysis)
   - software: CubeLineMoment
   - parameter: Moment images masked below 3 sigma (channel-based)  
  > "images masked below a $3\sigma$ threshold (channel-based)" (2 Observations and data analysis)
   - parameter: GMC 5 (absorption) and GMC 10 (non-detections) excluded; 8 GMCs kept  
  > "As a result, we do not discuss these two regions (GMCs 5 and 10) any further." (3 Molecular line emission)
   - assumption: Blended lines modelled separately and summed to compare with the measured blended intensity of each group  
  > "for each blending group, we model the integrated intensities of the transitions that make up the blending group separately, sum up the emission from each of these lines" (4 Non-LTE radiative transfer modeling analysis)
   - fitting: _not stated_
   - validation: Tested impact of contaminating lines (SO2, NH2OH, NH2CN) on derived parameters: unchanged within uncertainties  
  > "We have tested the impact of these contaminants on our derivation of physical parameters performed in Section 4 and found that the derived physical parameters are unchanged within the uncertainties in each parameter fit." (2 Observations and data analysis)
2. **convert integrated intensities to K km/s**: I(K) = 13.59 (300 GHz / nu)^2 / (theta_max theta_min) I(Jy), with Gaussian beam axes  
  > "We convert the integrated emission from Jy beam$^{-1}$ km s$^{-1}$ to K km s$^{-1}$ using the following expression" (3 Molecular line emission); "$\theta_{max}$ and $\theta_{min}$ are the major and minor axes, respectively, of our Gaussian beam" (3 Molecular line emission)
   - fitting: _not stated_
   - validation: _not stated_
3. **non-LTE radiative transfer fit of physical conditions**: RADEX via SpectralRadex coupled with Nautilus sampler; fit n_H2, T_kin, column densities of both spin isomers and beam filling factor per GMC  
  > "for Bayesian posterior and evidence estimation." (4 Non-LTE radiative transfer modeling analysis); "The collisional excitation rates used for are from (cite: Dagdigian_2023) while the rates are from (cite: H2CO_mole_data)." (4 Non-LTE radiative transfer modeling analysis)
   - software: RADEX, SpectralRadex, Nautilus
   - parameter: Priors (Table 2): n_H2 1e2-1e8 cm^-3 log-uniform; T_kin 10-800 K uniform; column densities 1e12-1e18 cm^-2 log-uniform; eta_ff 0-1 uniform  
  > "$10^{2}-10^{8}$" (Table 2); "$10-800$" (Table 2); "Prior ranges adopted for our parameter space explored in the" (Table 2 caption)
   - parameter: T_kin outside the collisional-rate grid (3-250 K CH3OH, 10-300 K H2CO) is clamped to the nearest grid temperature  
  > "uses the minimum or maximum kinetic temperature at which collisional excitation rates are provided" (4 Non-LTE radiative transfer modeling analysis)
   - assumption: Gaussian intensity uncertainties  
  > "We also assume that the uncertainty on our measured intensities is Gaussian" (4 Non-LTE radiative transfer modeling analysis)
   - assumption: Beam filling factor eta_ff = theta_S^2 / (theta_MB^2 + theta_S^2)  
  > "the beam filling factor ($\eta_{ff}=\frac{\theta^{2}_{S}}{\theta^{2}_{MB}+\theta^{2}_{S}}$)" (4 Non-LTE radiative transfer modeling analysis)
   - fitting: Nautilus sampler; uniform or log-uniform priors; likelihood exp(-chi^2/2)  
  > "We assume priors of uniform or log-uniform distribution within the determined ranges" (4 Non-LTE radiative transfer modeling analysis); "our likelihood is given by $P(\theta | d) \sim \exp(-\frac{1}{2}\chi^2),$" (4 Non-LTE radiative transfer modeling analysis)
   - validation: Compared old (Rabli and Flower 2010) and new (Dagdigian 2023) CH3OH rates: the E/A ratio range changes from 0.85-2.84 to 0.25-1.26; Nautilus gave results indistinguishable from UltraNest  
  > "With the (cite: CH3OH_mol_data_2010) rates, the average range for the best EAR was 0.85–2.84 whilst with the (cite: Dagdigian_2023) rates, the range is 0.25–1.26." (4 Non-LTE radiative transfer modeling analysis); "while providing indistinguishable results." (Footnote 6)
4. **check for sub-thermal excitation**: Compare collisional and radiative excitation rates using fitted opacity, density and temperature in each GMC  
  > "we compared the collisional and radiative excitation rate (cite: Goldsmith+2012) based on the on-the-spot measurements of opacity, gas density, and gas temperature in each GMC." (4.1 Properties of the gas as traced by CH3OH and H2CO)
   - fitting: _not stated_
   - validation: _not stated_
5. **derive CH3OH and H2CO abundances**: Divide column densities by H2 column densities from Mangum+2019 (rescaled by 0.63; GMC 1a, 2b, 8a, 9a from Harada+2022), both scaled by the fitted beam filling factor; E- and A- (or o- and p-) combined  
  > "we rescaled their H$_2$ column densities to match our angular resolution" (4.4 Derivation of H2CO and CH3OH abundances); "we applied a beam filling factor to the scaled H$_2$ column densities for each region" (4.4 Derivation of H2CO and CH3OH abundances)
   - parameter: Rescaling factor 0.63 for Mangum+2019 N_H2  
  > "This resulted in multiplying their $N_{H2}$ by a factor of 0.63." (4.4 Derivation of H2CO and CH3OH abundances)
   - assumption: E- and A- (and o- and p-) column densities are equal within uncertainties so abundances are derived for both forms together  
  > "we derived X$_{\rm{CH3OH}}$ for both forms together" (4.4 Derivation of H2CO and CH3OH abundances)
   - fitting: _not stated_
   - validation: _not stated_
6. **compare with shock tracers and interpret E/A ratio**: Compare n_H2, T_kin and abundances with HNCO, SiO and S-bearing species from earlier ALCHEMI fits; interpret E-/A- column density ratio (EAR) as a probe of formation temperature  
  > "we compare the gas characteristics as traced by these two molecules with our and results" (5.1 Do methanol and formaldehyde trace the same gas as SiO and HNCO?)
   - assumption: EAR is fixed at the time of methanol formation; in thermal equilibrium EAR is set by the spin temperature  
  > "Hence the ratio of these two isomers should be fixed at the time of the formation of methanol" (5.4 The E/A Ratio in NGC 253 as a probe of methanol formation and destruction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CubeLineMoment** : Extract integrated intensities and moment 0/1/2 maps with spectral and spatial masks  
  > "to extract integrated spectral-line intensities from our data cubes" (2 Observations and data analysis)
- **RADEX** : Non-LTE radiative transfer code  
  > "We use the radiative transfer code" (4 Non-LTE radiative transfer modeling analysis)
- **SpectralRadex** : Python package used to run RADEX  
  > "via the Python package" (4 Non-LTE radiative transfer modeling analysis)
- **Nautilus** : Sampler for Bayesian posterior and evidence estimation  
  > "for Bayesian posterior and evidence estimation." (4 Non-LTE radiative transfer modeling analysis)
- **UltraNest** : Sampler used in earlier ALCHEMI studies; compared with Nautilus  
  > "while providing indistinguishable results." (Footnote 6)
- **JPL catalogue** : CH3OH frequencies and spectroscopic parameters  
  > "Frequencies and spectroscopic parameters have been extracted from the JPL catalogue (cite: Pickett+1998)." (Table notes (CH3OH transitions))
- **CDMS** : H2CO frequencies and spectroscopic parameters  
  > "Frequencies and spectroscopic parameters have been extracted from CDMS (cite: Muller+2005; Endres+2016)." (Table notes (H2CO transitions))
- **EMAA database** : CH3OH collisional excitation rates  
  > "These rates were obtained from the Excitation of Molecules and Atoms for Astrophysics" (4 Non-LTE radiative transfer modeling analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH T_kin range across GMCs | 10.59-87.5 | not stated | K | 3 | $10.59-87.5$ |
| CH3OH T_kin, GMC 1a | 76.06 | +11.44/-9.69 | K | 3 | $76.06^{+11.44}_{-9.69}$ |
| CH3OH T_kin, GMC 2b | 11.14 | +0.57/-0.55 | K | 3 | $11.14^{+0.57}_{-0.55}$ |
| CH3OH log n_H2 range across GMCs | 4.11-7.11 | not stated | log(cm^-3) | 3 | $4.11-7.11$ |
| CH3OH beam filling factor range | 0.07-0.92 | not stated | dimensionless | 3 | $0.07-0.92$ |
| CH3OH E-/A- column density ratio (best) range across GMCs | 0.25-1.26 | not stated | dimensionless | 3 | $0.25-1.26$ |
| H2CO T_kin, GMC 4 | 266.73 | +316.23/-122.64 | K | 3 | $266.73^{+316.23}_{-122.64}$ |
| H2CO T_kin, GMC 3 | 129.71 | +49.30/-32.99 | K | 3 | $129.71^{+49.30}_{-32.99}$ |
| H2CO T_kin, all GMCs lower bound | >=67.23 | not stated | K | 3 | $\geq67.23$ |
| H2CO beam filling factor range | 0.04-0.67 | not stated | dimensionless | 3 | $0.04-0.67$ |
| CH3OH abundance range X(CH3OH) | 4.0e-10 to 1.4e-7 | not stated | dimensionless | 5 | Overall, we derive X$_{\rm{CH3OH}}$ in the range $4.0\times 10^{-10} - 1.4 \times 10^{-7}$ |
| H2CO abundance range X(H2CO) | 1.4e-10 to 1.4e-6 | not stated | dimensionless | 5 | For X$_{\rm{H2CO}}$, the range is $1.4\times 10^{-10} - 1.4\times10^{-6}$. |
| Rescaling factor applied to Mangum+2019 N_H2 | 0.63 | not stated | dimensionless | 5 | This resulted in multiplying their $N_{H2}$ by a factor of 0.63. |

## Qualitative findings

- CH3OH and H2CO trace distinct environments: H2CO low density and high T_kin, CH3OH high density and low T_kin  
  > "H$_2$CO traces low volume density and high kinetic temperatures, while CH$_3$OH traces high volume density and low kinetic temperatures." (abstract)
- CH3OH abundance shows a radial gradient; H2CO abundance is constant but poorly constrained  
  > "while the CH$_3$OH abundance shows a radial gradient from low to high values within the NGC 253 CMZ" (abstract)
- Only about half of CH3OH transitions are sub-thermally excited; most H2CO transitions are sub-thermal  
  > "We find that overall only about half of the transitions may be undergoing sub-thermal excitation conditions." (4.1 Properties of the gas as traced by CH3OH and H2CO); "Surprisingly the majority of transitions possess sub-thermal excitation conditions." (4.1 Properties of the gas as traced by CH3OH and H2CO)
- Derived column densities are 1-2 orders of magnitude above earlier LTE values that assumed a filling factor of 1  
  > "This discrepancy can be explained by the fact that their LTE analysis assumed a filling factor of 1." (4.2 Comparison with existing measurements)

## Claim tuples

- H: CH3OH and H2CO trace the same physical gas and are chemically linked | E: Non-LTE RADEX plus Nautilus fits of 39 CH3OH and 10 H2CO ALCHEMI transitions in eight GMCs | R: CH3OH: T_kin about 11-30 K (76 K in GMC 1a) and high density; H2CO: T_kin >~100 K and n_H2 ~1e4 cm^-3 | F: The two molecules trace distinct physical environments and are not directly chemically linked | **supported**
- H: CH3OH and H2CO trace the same gas as the shock tracers SiO and HNCO | E: Compare n_H2, T_kin and abundances with ALCHEMI SiO, HNCO and S-bearing species fits | R: CH3OH is 2-3 orders of magnitude denser than SiO and colder than HNCO; CH3OH resembles H2CS and OCS | F: CH3OH is not a fast-shock tracer; it may trace slow shocks or post-shock gas | **partially**
- H: H2CO forms on ices together with CH3OH | E: Compare gas conditions and non-thermal desorption scenario for H2CO and CH3OH | R: H2CO is absent from the cold component traced by CH3OH and its abundance stays constant across GMCs | F: H2CO is mainly formed in the gas phase | **partially**
- H: CH3OH abundance varies with position in the CMZ | E: Derive abundances from fitted column densities and published N_H2 | R: Distinct abundance gap between inner GMCs 3, 4, 6 and outer GMCs with outer regions richer in methanol | F: Inner GMCs may be at a younger evolutionary stage | **partially**
- H: The CH3OH E/A ratio records its formation history | E: Compare fitted E-/A- column density ratios per GMC with thermal-equilibrium expectations | R: EAR below 1 in most GMCs and above 1 in GMCs 3, 4 and 6 | F: Most CH3OH formed on cold ices; inner GMCs may have gas-phase formation at higher temperature, or EAR may be reset by proton exchange | **partially**

## Reasoning

- Why this data: ALCHEMI gives a wide spectral scan of the CMZ with many transitions per species  
  > "With wide and thorough spectral scanning across the CMZ of NGC 253, ALCHEMI provides a comprehensive molecular view of its nucleus." (2 Observations and data analysis)
- Why this method: Many transitions over a wide range of excitation energy allow non-LTE modelling to constrain the gas  
  > "Given the plethora of transitions we have measured for both species, spanning a wide range in excitation energy, radiative transfer analysis can be used to properly constrain the gas physical characteristics." (4 Non-LTE radiative transfer modeling analysis)
- Alternative: Older CH3OH collisional rates (Rabli and Flower 2010) gave a higher EAR range (0.85-2.84) and lower T_kin in GMC 1a (~36 K); the Dagdigian 2023 rates were adopted  
  > "With the (cite: CH3OH_mol_data_2010) rates, the average range for the best EAR was 0.85–2.84 whilst with the (cite: Dagdigian_2023) rates, the range is 0.25–1.26." (4 Non-LTE radiative transfer modeling analysis)
- Alternative: GMC 5 (absorption, needs background-continuum radiative transfer) and GMC 10 (few detections) excluded  
  > "Such a modeling effort is beyond the scope of the present study." (3 Molecular line emission)
- How they decided it was enough: _not stated_
- Limitation (authors): H2CO abundances and parameters are poorly constrained  
  > "The H$_2$CO abundances are constant, though poorly constrained" (abstract)
- Limitation (authors): Derived EAR depends on the choice of CH3OH collisional rates  
  > "The choice of the rates used for thus seem more critical if one aims to derive the EAR." (4 Non-LTE radiative transfer modeling analysis)
- Limitation (authors): Very high H2CO temperatures in GMC 4 and 6 are not well constrained  
  > "although not very well constrained" (5.1 Do methanol and formaldehyde trace the same gas as SiO and HNCO?)
- Caveat (inferred, ours): Beam filling factor, column density and density are degenerate; uncertainty on eta_ff propagates into the abundances, which are given only as wide ranges
- Caveat (inferred, ours): N_H2 comes from two different studies with different resolution; the 0.63 rescaling and the unscaled (3-10)e22 range add systematic error
- Caveat (inferred, ours): Intensity uncertainties and the line-width treatment in RADEX are not described
- Caveat (inferred, ours): H2CO T_kin in GMC 4 and 6 sits against the prior or grid edge, so 'high temperature' there is weakly constrained
- Caveat (inferred, ours): Low T_kin from CH3OH sub-thermal excitation could bias the density-temperature degeneracy
- Caveat (inferred, ours): Single-component models for each GMC may blend several velocity or temperature components

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Code: CubeLineMoment is available on GitHub (keflavich/cube-line-extractor)  
  > "https://github.com/keflavich/cube-line-extractor" (Footnote 3)
- Code: Integrated intensity tables for all transitions toward the GMCs released on Zenodo  
  > "are available as a machine-readable table" (Table notes (CH3OH transitions))
- Missing: ALCHEMI calibration and imaging recipe (only in the ALCHEMI main paper)
- Missing: GMC extraction aperture size, CubeLineMoment settings and per-channel noise values
- Missing: Nautilus and RADEX run settings (live points, line width, background temperature)
- Missing: Numerical N_H2 values used for each GMC
- Missing: Posterior summary statistic definition
- Data volume (inferred): ALCHEMI cubes covering Bands 3-7 for the needed transitions: roughly tens to hundreds of GB; the released Zenodo intensity table alone is small (MB)
- Score (inferred): 3/5, ALCHEMI data are the public large program and the Zenodo intensity table plus stated priors, likelihood, collisional rates and sampler allow rerunning the RADEX fits; but the cube processing, aperture, sampler settings and N_H2 values are not fully given.
- Rediscovery candidate: yes, The paper's integrated intensities are released, the RADEX plus Nautilus recipe is mostly specified, and the main results are numeric (T_kin, n_H2, column densities, EAR, abundances); full reproduction from cubes would need the ALCHEMI paper.

## Links

- Method: (cite: ALCHEMI_main_2021) (Describes ALCHEMI data acquisition, calibration and imaging)
- Method: (cite: Mangum+2019) (CubeLineMoment and the source of the H2 column densities)
- Method: (cite: Holdship+2021_SpectralRadex) (SpectralRadex package)
- Method: (cite: Dagdigian_2023) (CH3OH collisional excitation rates)
- Companion: (cite: Huang+2023) (HNCO and SiO non-LTE analysis in the same ALCHEMI data, used for comparison)
- Companion: (cite: Bouvier+2024) (S-bearing species analysis used for comparison)
- Companion: (cite: Humire+2022) (LTE analysis of CH3OH in NGC 253 with maser candidates, compared with)
- Companion: (cite: Harada+2022) (N_H2 values for outer GMCs)
- Related: ALCHEMI (ALMA Comprehensive High-resolution Extragalactic Molecular Inventory), 2017.1.00161.L and 2018.1.00162.S

## Checks

```json
{
 "quotes": 101,
 "quotes_ok": 101,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 102,
  "stated": 63,
  "rate": 0.618
 },
 "evidence_ok": true
}
```
