# Tentative detection of cyanoformamide NCCONH<SUB>2</SUB> in space

`2024PASJ...76...54L` | Publications of the Astronomical Society of Japan 2024 | first author: Li, Juan | arXiv: 2311.01721 | DOI: 10.1093/pasj/psad079

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: Is cyanoformamide (NCCONH2) present toward Sgr B2(N1E) in archival ReMoCA 3 mm data, and how do peptide-like molecule abundances there compare with Sgr B2(N1S)?  
  > "we present a tentative detection of NCCONH$_2$ in the interstellar medium (ISM) with the Atacama Large Millimeter/submillimeter Array (ALMA) archive data." (abstract); "We also searched for other peptide-like molecules toward Sgr B2(N1E)." (abstract)
- Target **Sgr B2(N1E)**: coordinates about 1.5'' east of Sgr B2(N1); absolute coordinates of N1E not stated (observation phase center given for Sgr B2(N))  
  > "which is about 1.5$''$ to the east of the hot core Sgr B2(N1)" (Identification of NCCONH$_2$); "which locates half way between the two main hot molecular hot cores Sgr B2(N1) and N2." (OBSERVATIONS AND DATA REDUCTION); z/distance _not stated_; distance from _not stated_
- Target **Sgr B2(N1S)**: coordinates about 1'' south of Sgr B2(N1); used as comparison position with values from Belloche19  
  > "Sgr B2(N1S) is a position that is about 1$''$ to the south of Sgr B2(N1)" (Comparison of Sgr B2(N1E) and Sgr B2(N1S)); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00243.S
- bands: 3 mm (84.1-114.4 GHz)  
  > "with the ALMA archive data at 3-mm wavelength." (CONCLUSIONS); "This is a compete spectral line survey toward Sgr B2(N) covering from 84.1 to 114.4 GHz." (OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: ReMoCA spectral line survey, 84.1 to 114.4 GHz, five spectral setups, spectral resolution 0.488 MHz (1.3-1.7 km/s)  
  > "Five spectral setups were used in total." (OBSERVATIONS AND DATA REDUCTION); "The spectral resolution is 0.488 MHz, which corresponds to a velocity resolution of 1.3-1.7 km s$^{-1}$ across the observing band." (OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: imaging rms of 0.4 ~ 1 mJy/beam  
  > "We did not perform self-calibration, but still achieved a sufficiently high imaging rms of 0.4 $\sim$ 1 mJy beam$^{-1}$" (OBSERVATIONS AND DATA REDUCTION)
- time on source: 47 to 50 minutes per frequency window  
  > "The on-source time for each frequency windows range from 47 to 50 minutes." (OBSERVATIONS AND DATA REDUCTION)
- observing dates: ALMA Cycle 4, between 2016 and 2017  
  > "The ReMoCA survey was conducted with ALMA during Cycle 4 between 2016 and 2017." (OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: archival data from the ReMoCA survey (Belloche et al. 2019), reduced by the authors  
  > "The data used for this study were acquired from the ALMA Science archive of the ReMoCA survey (Re-exploring Molecular Complexity with ALMA) (cite: Belloche19)." (OBSERVATIONS AND DATA REDUCTION); "Detailed description about the observations is presented in (cite: Belloche19)." (OBSERVATIONS AND DATA REDUCTION)
- Line: NCCONH2 (cyanoformamide) 10 unblended and 21 partially blended a-/b-type transitions, e.g. 20(5,16)-20(4,17) (unblended lines 86036.2567 to 108734.3241 MHz (Table 1))
- Line: CH3NCO v=0 nine relatively clean and strong transitions (not stated)
- Line: CH3NHCHO v=0 thirteen relatively clean and strong transitions (not stated)
- Line: NH2CONH2 (urea) v=0 four clean and strong transitions, all seriously blended (not stated)
- External data: H2 column density of 3.5e24 cm^-2 toward Sgr B2(N1E), derived with C18O  
  > "By adopting the H$_2$ column density of 3.5$\times 10^{24}$ cm$^{-2}$ derived with C$^{18}$O (cite: Li21)" (Column densities of NCCONH$_2$ and related molecules) [from (cite: Li21)]
- External data: Column densities toward Sgr B2(N1S) used for comparison  
  > "$^{**}$: cited from (cite: Belloche19)." (Table 2) [from (cite: Belloche19)]
- External data: HCONH2 and CH3CONH2 column densities toward Sgr B2(N1E) taken from earlier work  
  > "$^*$: cited from (cite: Li21)." (Table 2) [from (cite: Li21)]
- External data: Rotational spectrum of NCCONH2 used for line modelling  
  > "The microwave and millimeter-wave spectrum of NCCONH$_2$ was reported by (cite: Christiansen05) and (cite: Winnewisser05)." (Identification of NCCONH$_2$) [from (cite: Christiansen05); (cite: Winnewisser05)]
- External data: Desorption peak temperatures (NH2CONH2 ~265 K, NH2CHO ~210 K, CH3CONH2 ~219 K) from laboratory studies  
  > "According to laboratory studies in (cite: Ligterink18), the desorption peak of NH$_2$CONH$_2$ is $\sim$265 K" (Comparison of Sgr B2(N1E) and Sgr B2(N1S)) [from (cite: Ligterink18)]
- External data: Upper limit on NCCONH2/formamide of 0.05 in G31.41+0.31, used for comparison  
  > "They found that the abundance ratio of NCCONH$_2$ to formamide was lower than 0.05 in G31.41+0.31." (Column densities of NCCONH$_2$ and related molecules) [from (cite: Colzi21)]

## Processing

### Calibration

- pipeline or manual: standard ALMA data calibration pipeline with CASA  
  > "The data was calibrated using the standard ALMA data calibration pipeline with the Common Astronomy Software Applications package (CASA)." (OBSERVATIONS AND DATA REDUCTION)
- casa version: CASA 4.7.0-1 (first setup) and 4.7.2 (other four setups) for calibration; CASA 5.6.1-8 for imaging  
  > "CASA version 4.7.0-1 was used for the first spectral setup, while CASA version 4.7.2 was used for the other four spectral setups." (OBSERVATIONS AND DATA REDUCTION); "The CASA version 5.6.1-8 was used to image the calibrated data." (OBSERVATIONS AND DATA REDUCTION)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 or J1733-1304  
  > "Quasars J1924-2914 or J1733-1304 were used to derive the absolute flux density scale." (OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: _not stated_
- self calibration: not performed  
  > "We did not perform self-calibration" (OBSERVATIONS AND DATA REDUCTION)

### Imaging

- task: TCLEAN in CASA 5.6.1-8  
  > "The TCLEAN deconvolution algorithm in CASA was used to produce the images." (OBSERVATIONS AND DATA REDUCTION)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum level set in the spectra from several groups of lowest values after masking absorption lines (compared with HII region spectra)  
  > "We first compared with spectra toward HII regions to mask absorption lines, then we chose several groups of lowest values to determine the continuum levels." (OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: 0.4 ~ 1 mJy/beam  
  > "but still achieved a sufficiently high imaging rms of 0.4 $\sim$ 1 mJy beam$^{-1}$" (OBSERVATIONS AND DATA REDUCTION)

### Inherited from earlier work

- Data reduction procedure  
  > "Our data reduction procedure has been introduced in (cite: Li21)." (OBSERVATIONS AND DATA REDUCTION) [from (cite: Li21)]
- Observation details of the ReMoCA survey  
  > "Detailed description about the observations is presented in (cite: Belloche19)." (OBSERVATIONS AND DATA REDUCTION) [from (cite: Belloche19)]
- Excitation temperature of 150 K, close to that obtained for molecules toward Sgr B2(N1S)  
  > "an assumption of excitation temperature of 150 K (which is very close to what was obtained for molecules toward Sgr B2(N1S) by (cite: Belloche19)" (Column densities of NCCONH$_2$ and related molecules) [from (cite: Belloche19)]
- Choice of CH3NCO and CH3NHCHO transitions and urea transitions to search, based on earlier observing results  
  > "Based on observing results of (cite: Belloche19), we searched for nine relatively clean and strong transitions of CH$_3$NCO v=0 toward Sgr B2(N1E)." (Search of related molecules toward Sgr B2(N1E)) [from (cite: Belloche19)]
- Continuum level determination guided by simulated-spectra tests  
  > "We could see from Figure 1(b) in (cite: sanchez2018) that the continuum level of the spectra could be better determined with several groups of lowest values in the spectra after masking absorption lines." (OBSERVATIONS AND DATA REDUCTION) [from (cite: sanchez2018)]

### Not stated but needed to reproduce (our reading)

- tclean parameters: weighting and robust value, cell size, image size, niter, threshold, masks, deconvolver, primary-beam correction
- which execution blocks and spectral windows were imaged and the synthesized beam per spectral window
- array configurations and baseline range of the ReMoCA data
- how the 0.4-1 mJy/beam rms varies per spectral window and the exact rms adopted per window
- which spectral windows/channels were taken as line-free for the continuum level, and the exact lowest-value grouping
- how HII-region absorption masking was done and the continuum values adopted
- extraction position/aperture for the Sgr B2(N1E) spectrum and its exact coordinates
- line-by-line goodness of fit, uncertainties on the column densities and velocity offsets, and the criterion for eye-fit acceptance
- how the 2.3'' source size was chosen relative to the beam
- rate-coefficient (modified Arrhenius) parameters and transition-state energies for the DFT reaction study

## Analysis recipe

1. **calibrate and image archival ReMoCA data**: Standard ALMA pipeline calibration in CASA, then tclean imaging without self-calibration  
  > "The data was calibrated using the standard ALMA data calibration pipeline with the Common Astronomy Software Applications package (CASA)." (OBSERVATIONS AND DATA REDUCTION); "The TCLEAN deconvolution algorithm in CASA was used to produce the images." (OBSERVATIONS AND DATA REDUCTION)
   - software: CASA, tclean
   - parameter: CASA 4.7.0-1 / 4.7.2 for calibration, 5.6.1-8 for imaging  
  > "The CASA version 5.6.1-8 was used to image the calibrated data." (OBSERVATIONS AND DATA REDUCTION)
   - parameter: imaging rms 0.4 ~ 1 mJy/beam  
  > "but still achieved a sufficiently high imaging rms of 0.4 $\sim$ 1 mJy beam$^{-1}$" (OBSERVATIONS AND DATA REDUCTION)
   - assumption: Self-calibration would introduce artifacts for the complicated Sgr B2(N) substructure, so it was skipped  
  > "therefore, self-calibration will likely introduce artifacts into images, which may affect spectral line identification, especially for the weak lines in our case." (OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: rms compared with that of Belloche19  
  > "which is not much higher than that in (cite: Belloche19)." (OBSERVATIONS AND DATA REDUCTION)
2. **set continuum level and rms noise of spectra**: Mask absorption lines using HII region spectra, take groups of lowest values as continuum level; rms from median of channel maps  
  > "We first compared with spectra toward HII regions to mask absorption lines, then we chose several groups of lowest values to determine the continuum levels." (OBSERVATIONS AND DATA REDUCTION); "The rms noise levels for the spectra window were determined using the median values of channel maps." (OBSERVATIONS AND DATA REDUCTION)
   - parameter: median of rms levels adopted, from regions without continuum or lines, and checked in regions with strong continuum  
  > "The median values of rms noise levels were adopted in this paper." (OBSERVATIONS AND DATA REDUCTION)
   - assumption: Broad frequency coverage gives enough line-free intervals; at least 1 GHz bandwidth needed  
  > "They think that a bandwidth of at least 1 GHz is needed." (OBSERVATIONS AND DATA REDUCTION)
   - fitting: _not stated_
   - validation: _not stated_
3. **identify NCCONH2 lines with LTE modelling**: LTE model with five parameters per spectral window in Weeds (GILDAS), using JPL and CDMS catalogs  
  > "Weeds in Gildas package was used for line identification and spectral modeling." (Identification of NCCONH$_2$); "The 3-mm emission of NCCONH$_2$ is modeled assuming LTE conditions with five parameters: column density, temperature, source size, velocity offset, and linewidth." (Identification of NCCONH$_2$)
   - software: Weeds, GILDAS
   - parameter: each spectral window of each setup modelled separately with the same parameter set  
  > "Each spectral window of each observed setup was modeled separately to account for the varying angular resolution, but with a same set of parameters." (Identification of NCCONH$_2$)
   - parameter: about 120 lines expected; 10 unblended and 21 partially blended possibly seen at about 3 sigma  
  > "Approximately 120 NCCONH$_2$ lines were expected to be seen in the observed frequency ranges." (Identification of NCCONH$_2$)
   - assumption: LTE  
  > "is modeled assuming LTE conditions" (Identification of NCCONH$_2$)
   - fitting: _not stated_
   - validation: Signal-to-noise about 3 sigma so detection is not secure; remaining blended lines do not contradict expected intensities  
  > "it is not possible to claim secure detection of NCCONH$_2$ with these data." (Identification of NCCONH$_2$); "the observed results do not contradict with the expected intensities." (Identification of NCCONH$_2$)
4. **derive column density and abundance of NCCONH2**: Eye-fitting spectra in Weeds, varying column density and centroid velocity at fixed size, linewidth and Tex; abundance relative to H2  
  > "The column densities of NCCONH$_2$ and related molecules are obtained by eye-fitting the spectra in Weeds." (Column densities of NCCONH$_2$ and related molecules); "the column density and centroid velocity are varied to fit the detected transitions." (Column densities of NCCONH$_2$ and related molecules)
   - software: Weeds, GILDAS
   - parameter: source size 2.3'', linewidth 3.0 km/s, Trot 150 K, velocity offset -1 km/s  
  > "Velocity offset with respect to the assumed systemic velocity of Sgr B2(N1), $V_{sys}=64$ km s$^{-1}$" (Table 2); "With a linewidth measurement of 3.0 km s$^{-1}$, and an assumption of excitation temperature of 150 K" (Column densities of NCCONH$_2$ and related molecules)
   - assumption: emitting size 2.3'', beam filling factor about 1  
  > "The emitting size was assumed to be 2.3$''$" (Column densities of NCCONH$_2$ and related molecules)
   - assumption: H2 column density 3.5e24 cm^-2 from C18O (Li21)  
  > "By adopting the H$_2$ column density of 3.5$\times 10^{24}$ cm$^{-2}$ derived with C$^{18}$O (cite: Li21)" (Column densities of NCCONH$_2$ and related molecules)
   - fitting: Eye-fit, no sampler, priors or likelihood  
  > "obtained by eye-fitting the spectra in Weeds." (Column densities of NCCONH$_2$ and related molecules)
   - validation: NCCONH2/formamide ratio about 0.01 consistent with Colzi21 upper limit of 0.05 in G31.41+0.31  
  > "This value is consistent with result in (cite: Colzi21)." (Column densities of NCCONH$_2$ and related molecules)
5. **search related peptide-like molecules and compare N1E with N1S**: Search selected clean transitions of CH3NCO, CH3NHCHO and urea toward N1E, model with the same size and Tex, compare column densities and abundances with Sgr B2(N1S) values from Belloche19  
  > "We also modeled the emission of CH$_3$NCO and CH$_3$NHCHO toward Sgr B2(N1E) with the same size and excitation temperature" (Column densities of NCCONH$_2$ and related molecules); "We compared these results with those of Sgr B2(N1S) presented in (cite: Belloche19)." (Comparison of Sgr B2(N1E) and Sgr B2(N1S))
   - software: Weeds, GILDAS, CDMS, Lille Spectroscopic Database
   - parameter: nine CH3NCO lines and thirteen CH3NHCHO lines detected; four urea lines all blended  
  > "Nine clean lines were detected." (Search of related molecules toward Sgr B2(N1E)); "All of these lines were detected." (Search of related molecules toward Sgr B2(N1E))
   - assumption: Same size (2.3'') and Trot (150 K) as for NCCONH2  
  > "Parameters of LTE model of NCCONH$_2$ and related molecules toward Sgr B2(N1E)." (Table 2)
   - fitting: Eye-fit of column density, as for NCCONH2  
  > "The column densities of NCCONH$_2$ and related molecules are obtained by eye-fitting the spectra in Weeds." (Column densities of NCCONH$_2$ and related molecules)
   - validation: _not stated_
6. **evaluate gas-phase formation routes of NCCONH2 with quantum chemistry**: DFT M06-2X/6-311+G(d,p) geometry optimisations, M06-2X/aug-cc-pVTZ single-point energies, rate coefficients from the modified Arrhenius equation  
  > "High-performance single point energies were also calculated at the M06-2X/aug-cc-pVTZ (cite: dunning89) level using the M06-2X structures." (Possible formation mechanism for interstellar cyanoformamide); "We have calculated the rate coefficients of Reaction (1) by the modified Arrhenius equation." (Possible formation mechanism for interstellar cyanoformamide)
   - software: Gaussian 16
   - parameter: barrier of reaction (1) 9.7 kJ/mol; rate coefficients at 150 and 200 K  
  > "which is 9.7 kJ/mol (=1,167 K)" (Possible formation mechanism for interstellar cyanoformamide)
   - assumption: gas-phase reaction CN + NH2CHO -> NCCONH2 + H (Winnewisser05); alternative grain-surface CN + NH2CO proposed  
  > "we propose another possible reaction route of NCCONH$_2$, where it might be formed upon recombination of two free radicals on the grain surface at low temperature" (Possible formation mechanism for interstellar cyanoformamide)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0-1 and 4.7.2 (calibration), 5.6.1-8 (imaging): pipeline calibration and imaging of ReMoCA data  
  > "The CASA version 5.6.1-8 was used to image the calibrated data." (OBSERVATIONS AND DATA REDUCTION); "CASA version 4.7.0-1 was used for the first spectral setup, while CASA version 4.7.2 was used for the other four spectral setups." (OBSERVATIONS AND DATA REDUCTION)
- **tclean** : deconvolution and image production  
  > "The TCLEAN deconvolution algorithm in CASA was used to produce the images." (OBSERVATIONS AND DATA REDUCTION)
- **Weeds (GILDAS)** : line identification and LTE spectral modelling, column density eye-fitting  
  > "Weeds in Gildas package was used for line identification and spectral modeling." (Identification of NCCONH$_2$)
- **JPL molecular spectroscopy catalog** : line frequencies for identification  
  > "The Jet Population Laboratory (JPL) (cite: Pickett98) and the Cologne Database for Molecular Spectroscopy (CDMS) (cite: CDMS2; Endres16) databases were used." (Identification of NCCONH$_2$)
- **CDMS** : line frequencies for identification, including CH3NCO  
  > "The CDMS database is used for the identification." (Search of related molecules toward Sgr B2(N1E))
- **Lille Spectroscopic Database** : identification of CH3NHCHO lines  
  > "The Lille Spectrascopic Database (https://lsd.univ-lille.fr/) is used for the identification." (Search of related molecules toward Sgr B2(N1E))
- **Gaussian 16** 16 (Revision A.03 in reference list): quantum chemical calculations of formation reactions  
  > "All quantum chemical calculations were run with the Gaussian 16 (cite: frisch16)." (Possible formation mechanism for interstellar cyanoformamide)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| NCCONH2 column density toward Sgr B2(N1E) | 2.4e15 | not stated | cm^-2 | 4 | a column density of $2.4\times10^{15}$ cm$^{-2}$ was obtained for cyanoformamide |
| NCCONH2 abundance relative to H2 | 6.9e-10 | not stated | dimensionless | 4 | the abundance relative to H$_2$ was estimated to be $6.9\times10^{-10}$ for NCCONH$_2$. |
| NCCONH2 to NH2CHO abundance ratio | ~0.01 | not stated | dimensionless | 4 | the abundance ratio between NCCONH$_2$ and formamide is found to be $\sim$0.01. |
| number of unblended NCCONH2 transitions (about 3 sigma) | 10 | not stated | lines | 3 | Ten unblended lines of NCCONH$_2$ were seen around 3$\sigma$ noise levels toward Sagittarius B2(N1E) |
| number of partially blended NCCONH2 transitions | 21 | not stated | lines | 3 | Ten unblended transitions, and 21 partially blended transitions of NCCONH$_2$ were possibly seen toward Sgr B2(N1E) |
| CH3NCO column density toward Sgr B2(N1E) | 2.4e16 | not stated | cm^-2 | 5 | A column density of 2.4$\times 10^{16}$ cm$^{-2}$ was obtained for CH$_3$NCO. |
| CH3NHCHO column density toward Sgr B2(N1E) | 2.1e16 | not stated | cm^-2 | 5 | A column density of $2.1\times10^{16}$ cm$^{-2}$ was obtained for CH$_3$NHCHO. |
| CH3NCO to NH2CHO abundance ratio toward Sgr B2(N1E) | 0.086 | not stated | dimensionless | 5 | The abundance ratio of CH$_3$NCO to NH$_2$CHO, was 0.086 toward Sgr B2(N1E) |
| barrier energy of reaction CN + NH2CHO -> NCCONH2 + H | 9.7 | not stated | kJ/mol | 6 | which is 9.7 kJ/mol (=1,167 K) |
| rate coefficients of reaction (1) at 150 K and 200 K | 2.4e-13 (150 K) and 1.94e-12 (200 K) | not stated | cm^3 s^-1 | 6 | The rate coefficients are $2.4 \times 10^{-13}$ and $1.94 \times 10^{-12}$ cm$^3$ s$^{-1}$ at T = 150 and 200 K, respectively. |

## Qualitative findings

- Abundances of NH2CHO, CH3NCO and CH3NHCHO toward N1E are about one tenth of those toward N1S, while CH3CONH2 is about one twentieth  
  > "while the abundances of CH$_3$CONH$_2$ was only one twentieth of that toward Sgr B2(N1S)." (abstract)
- NCCONH2 could not be searched toward other positions in Sgr B2(N1) because of line blending, so its spatial distribution is unknown  
  > "Thus we could not get the spatial distribution of NCCONH$_2$ in Sgr B2(N1)." (Identification of NCCONH$_2$)
- Gas-phase CN + NH2CHO is slow; reactions (2) and (3) have high barriers; grain-surface CN + NH2CO proposed  
  > "This means that the exothermic formation reaction (1) is slow in the gas-phase." (Possible formation mechanism for interstellar cyanoformamide)

## Claim tuples

- H: NCCONH2 is present in Sgr B2(N1E) | E: LTE modelling of ReMoCA 3 mm archival spectra toward N1E in Weeds | R: 10 unblended and 21 partially blended lines seen at about 3 sigma | F: tentative detection of NCCONH2, not a secure one | **partially**
- H: What are the abundance of NCCONH2 and its ratio to formamide toward N1E | E: Eye-fit LTE model with 2.3'' size, 150 K, 3 km/s; H2 column from C18O | R: N = 2.4e15 cm^-2, abundance 6.9e-10, NCCONH2/NH2CHO about 0.01 | F: Ratio consistent with the Colzi21 upper limit in G31.41+0.31 | **supported**
- H: Peptide-like molecule abundances at N1E differ from those at N1S | E: Search and model NH2CHO, CH3NCO, CH3NHCHO, CH3CONH2 and urea toward N1E; compare with Belloche19 N1S values | R: NH2CHO, CH3NCO, CH3NHCHO about one tenth of N1S; CH3CONH2 about one twentieth; urea not detected because of blending | F: Lower CH3CONH2 and urea non-detection may reflect higher desorption energies | **partially**
- H: NCCONH2 forms from CN + NH2CHO in the gas phase | E: DFT M06-2X potential energy surface and rate coefficients for reactions (1)-(3) | R: Reaction (1) barrier 9.7 kJ/mol, rate coefficients 2.4e-13 and 1.94e-12 cm3/s at 150 and 200 K; reactions (2) and (3) endothermic with barriers above 55 kJ/mol | F: Gas-phase route is slow; a grain-surface CN + NH2CO route is proposed | **partially**

## Reasoning

- Why this data: Complete 3 mm spectral line survey of Sgr B2(N) in the ALMA archive (ReMoCA)  
  > "This is a compete spectral line survey toward Sgr B2(N) covering from 84.1 to 114.4 GHz." (OBSERVATIONS AND DATA REDUCTION)
- Why this method: No self-calibration because of complicated Sgr B2(N) structure and weak lines; lowest-value continuum determination chosen for line-dominated spectra  
  > "Therefore, we believe that this strategy is suitable for our purpose of identification of weak lines." (OBSERVATIONS AND DATA REDUCTION); "This could properly determine the continuum levels for spectra dominated by emission lines." (OBSERVATIONS AND DATA REDUCTION)
- Alternative: Self-calibration rejected to avoid artifacts  
  > "We did not perform self-calibration" (OBSERVATIONS AND DATA REDUCTION)
- Alternative: Gas-phase reactions (2) and (3) between CN and NH2CHO considered and found endothermic with high barriers  
  > "both reactions (2) and (3) are endothermic with high barriers ($>$55 kJ/mol)" (Possible formation mechanism for interstellar cyanoformamide)
- How they decided it was enough: Nine lines considered enough to detect and model a molecule in Sgr B2  
  > "As nine lines are enough for the detection and modelling of molecule in Sgr B2, we did not search for all the CH$_3$NCO v=0 toward Sgr B2(N1E)." (Search of related molecules toward Sgr B2(N1E))
- Limitation (authors): Detection is only at about 3 sigma, not secure  
  > "it is not possible to claim secure detection of NCCONH$_2$ with these data." (Identification of NCCONH$_2$)
- Limitation (authors): Line blending toward other directions prevents mapping and detection elsewhere  
  > "However, serious line-blending prevents detection of this molecule toward other directions." (Identification of NCCONH$_2$)
- Limitation (authors): Emission size hard to determine because morphology is not Gaussian  
  > "The physical size of the emission region is hard to determine" (Column densities of NCCONH$_2$ and related molecules)
- Limitation (authors): Confirmation observations needed  
  > "It is highly desirable to conduct confirmation observations on the existence of NCCONH$_2$ in space." (CONCLUSIONS)
- Caveat (inferred, ours): Detection rests on eye-fit LTE models at about 3 sigma with no quantified goodness of fit, uncertainties or false-positive test
- Caveat (inferred, ours): Fixed Tex of 150 K, size of 2.3'' and 3 km/s width are assumed, not fitted; column density has no error bar
- Caveat (inferred, ours): Abundance uses an H2 column from a previous paper (Li21) and the N1E position is offset from the continuum peak
- Caveat (inferred, ours): Of about 120 expected lines only 10 are unblended; the 90 contaminated lines are only said to be not contradictory

## Reproducibility

- Data public (paper): Data come from the ALMA science archive (ReMoCA, project 2016.1.00243.S)  
  > "The data used for this study were acquired from the ALMA Science archive of the ReMoCA survey (Re-exploring Molecular Complexity with ALMA) (cite: Belloche19)." (OBSERVATIONS AND DATA REDUCTION)
- Products in archive: _not stated_
- Missing: tclean imaging parameters (weighting, robust, cell, image size, masks, thresholds)
- Missing: exact spectrum extraction position and aperture for Sgr B2(N1E)
- Missing: continuum levels adopted and line-free channel selection
- Missing: fit uncertainties and model-comparison criteria; the fit is an eye-fit
- Missing: details of the DFT rate-coefficient calculation
- Data volume (inferred): Large: five spectral setups of a 84-114 GHz survey with several execution blocks each, likely hundreds of GB raw and imaged cubes of tens of GB
- Score (inferred): 2/5, Public ALMA archive data and CASA/Weeds tools are named, but imaging parameters, extraction position and continuum levels are not given and the column density is an eye-fit without uncertainties.
- Rediscovery candidate: no, Data are public but the recipe is not complete (imaging settings, extraction position, continuum levels, eye-fit) and the 3 sigma detection is tentative.

## Links

- Method: (cite: Belloche19) (Describes the ReMoCA observations and the N1S comparison values)
- Method: (cite: Li21) (Data reduction procedure, H2 column density and earlier N1E results)
- Method: (cite: sanchez2018) (Continuum level determination in line-rich spectra)
- Companion: (cite: Li21) (Tentative propionamide detection toward Sgr B2(N1E))
- Companion: (cite: Colzi21) (Earlier NCCONH2 search toward G31.41+0.31 with a negative result)
- Related: ReMoCA survey (Re-exploring Molecular Complexity with ALMA), project 2016.1.00243.S

## Checks

```json
{
 "quotes": 116,
 "quotes_ok": 116,
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
  "facts": 106,
  "stated": 73,
  "rate": 0.689
 },
 "evidence_ok": true
}
```
