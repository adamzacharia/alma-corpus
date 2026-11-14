# The ALMA-PILS survey: First tentative detection of 3-hydroxypropenal (HOCHCHCHO) in the interstellar medium and chemical modeling of the C<SUB>3</SUB>H<SUB>4</SUB>O<SUB>2</SUB> isomers

`2022A&A...660L...6C` | Astronomy and Astrophysics 2022 | first author: Coutens, A. | arXiv: 2203.14119 | DOI: 10.1051/0004-6361/202243038

Card schema 1.0 | model gemini-4-argon | depth full | type large_program_or_survey

## Science

- Fields: star_formation, astrochemistry
- Question: Can 3-hydroxypropenal (HOCHCHCHO) and its C3H4O2 isomers be detected in the solar-type protostar IRAS 16293-2422, and how are they formed chemically?  
  > "In this work, we analyzed the Atacama Large Millimeter/submillimeter Array (ALMA) data of the Protostellar Interferometric Line Survey (PILS), an unbiased spectral survey of the solar-type protostar IRAS 16293–2422, and we tentatively detected 3-hydroxypropenal (HOCHCHCHO)" (abstract); "We included HOCHCHCHO and five of its isomers in the chemical network presented in (cite: Manigand2021) and we predicted their chemical evolution with the Nautilus code." (abstract)
- Target **IRAS 16293–2422 B**: coordinates 16h32m22.58s, -24d28m32.8s (J2000)  
  > "The applied spectrum corresponds to the component B of IRAS16293 at a position offset by 0.5$\ensuremath{''}$ (one beam) with respect to the continuum peak position in the south-west direction ($\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22.58s, $\delta_{\rm J2000}$=-24$\ensuremath{^\circ}$28$\ensuremath{'}$32.8$\ensuremath{''}$)." (Analysis and results); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S, 2012.1.00712.S
- bands: Band 7, Band 6, Band 3  
  > "In summary, these observations obtained with both the 12m array and the Atacama Compact Array (ACA) cover the entire range between 329.1 and 362.9 GHz (Band 7) with a resolution of 0.244 MHz ($\sim$0.2 km s$^{-1}$)." (Observations and spectroscopy); "Besides the Band 7 observations, small spectral windows were also covered in Bands 3 and 6." (Observations and spectroscopy)
- frequencies and spectral setup: 329.1 to 362.9 GHz with 0.244 MHz (~0.2 km s^-1) resolution  
  > "In summary, these observations obtained with both the 12m array and the Atacama Compact Array (ACA) cover the entire range between 329.1 and 362.9 GHz (Band 7) with a resolution of 0.244 MHz ($\sim$0.2 km s$^{-1}$)." (Observations and spectroscopy)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "In summary, these observations obtained with both the 12m array and the Atacama Compact Array (ACA) cover the entire range between 329.1 and 362.9 GHz (Band 7) with a resolution of 0.244 MHz ($\sim$0.2 km s$^{-1}$)." (Observations and spectroscopy)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.4 to 0.7 arcsec, restored with a circular beam of 0.5 arcsec  
  > "The beam sizes vary between 0.4 and 0.7$\ensuremath{''}$ and the observations were restored with a circular beam of 0.5$\ensuremath{''}$." (Observations and spectroscopy)
- max recoverable scale: _not stated_
- sensitivity: 4-5 mJy beam^-1 km s^-1  
  > "The sensitivity of the combined 12m array and ACA observations is about 4-5 mJy beam$^{-1}$ km s$^{-1}$." (Observations and spectroscopy)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HOCHCHCHO rotational and rotation-tunneling transitions in Band 7 and Band 6 (329184.3 to 362238.2 MHz (Band 7), 239460.6 to 250459.9 MHz (Band 6))
- Line: C2H3OCHO rotational transition (355.2462 GHz)
- Line: C2H3COOH s-cis and s-trans conformers (not stated)
- Line: CH2OHCH2CH2OH conformer a'GG'g (not stated)
- External data: Spectroscopic data for HOCHCHCHO, C2H3OCHO, C2H3COOH, and CH2OHCH2CH2OH from CDMS  
  > "The spectroscopic data of HOCHCHCHO come from the Cologne Database for Molecular Spectroscopy (CDMS, (cite: Muller2001; Muller2005))." (Observations and spectroscopy); "Only C$_2$H$_3$OCHO (vinyl formate) and the s-cis and s-trans conformers of C$_2$H$_3$COOH (propenoic acid) are available in CDMS." (Analysis and results) [from CDMS (cite: Muller2001; Muller2005)]
- External data: List of previously identified species in IRAS 16293 B and additional molecules for spectral overlay  
  > "We added HONO (cite: Coutens2019), CH$_3$OCH$_2$OH, CH$_2$DCHO, t-C$_2$H$_5$OCH$_3$ (cite: Manigand2020), C$_2$H$_3$CHO, C$_3$H$_6$ (cite: Manigand2021), and CH$_3$OCHD$_2$ (cite: Richard2021) to the list presented in Appendix A of (cite: Coutens2019)." (Analysis and results) [from (cite: Coutens2019; Manigand2020; Manigand2021; Richard2021)]
- External data: Initial abundances and physical model for chemical modeling  
  > "the initial abundances listed in Table 3 of (cite: Manigand2021), and a duration of 10$^6$ years; and ii) the collapse phase described in (cite: Manigand2021)." (Chemical modeling and discussion) [from (cite: Manigand2021)]
- Simulation/model as data: Three-phase gas, grain surface, and grain mantle time-dependent chemical model using the Nautilus code  
  > "To better understand the chemistry of HOCHCHCHO and its isomers, we used the Nautilus code (cite: Ruaud2016), a three-phase gas, grain surface, and grain mantle time-dependent chemical model." (Chemical modeling and discussion)

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
- continuum subtraction: performed as described in Jorgensen et al. 2016  
  > "More information about the data reduction, the continuum subtraction, and these additional data can be found in (cite: Jorgensen2016)." (Observations and spectroscopy)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 12m array and ACA combined  
  > "The sensitivity of the combined 12m array and ACA observations is about 4-5 mJy beam$^{-1}$ km s$^{-1}$." (Observations and spectroscopy)
- smoothing: _not stated_
- final beam: 0.5 arcsec circular beam  
  > "The beam sizes vary between 0.4 and 0.7$\ensuremath{''}$ and the observations were restored with a circular beam of 0.5$\ensuremath{''}$." (Observations and spectroscopy)
- final rms: 4-5 mJy beam^-1 km s^-1  
  > "The sensitivity of the combined 12m array and ACA observations is about 4-5 mJy beam$^{-1}$ km s$^{-1}$." (Observations and spectroscopy)

### Inherited from earlier work

- ALMA PILS survey observations, data reduction, and continuum subtraction  
  > "The ALMA/PILS survey is fully described in (cite: Jorgensen2016)." (Observations and spectroscopy); "More information about the data reduction, the continuum subtraction, and these additional data can be found in (cite: Jorgensen2016)." (Observations and spectroscopy) [from (cite: Jorgensen2016)]
- LTE synthetic spectrum analysis and chi-square fitting methodology  
  > "Our analysis is similar to those presented in earlier studies (cite: Coutens2016; Coutens2019; Lykke2017; Ligterink2017)." (Analysis and results) [from (cite: Coutens2016; Coutens2019; Lykke2017; Ligterink2017)]
- Chemical network, initial abundances, and two-stage physical model of protostellar collapse  
  > "We updated the chemical network described in (cite: Manigand2021) by including the reactions producing and consuming the C$_3$H$_4$O$_2$ isomers" (Chemical modeling and discussion); "For the physical model of the formation of a low-mass protostar, we considered two successive stages, similarly to (cite: Manigand2021)" (Chemical modeling and discussion) [from (cite: Manigand2021)]

### Not stated but needed to reproduce (our reading)

- Source size (beam filling factor) assumed in the CASSIS LTE synthetic spectrum modeling
- Assumed methanol (CH3OH) column density in IRAS 16293 B used to convert column densities into abundances relative to CH3OH
- Exact coarse grid range and step sizes for the first LTE chi-square grid search
- Line width (FWHM) and systemic velocity (v_LSR) fixed or varied during the CASSIS LTE grid fitting

## Analysis recipe

1. **Predict molecular presence with a convolutional neural network**: Apply a convolutional neural network (CNN) trained on multi-species LTE synthetic spectra to the PILS spectrum at the 0.5 arcsec offset position of IRAS 16293 B  
  > "Using a dedicated convolutional neural network (CNN) on a large set of multi-species synthetic spectra assuming local thermodynamic equilibrium (LTE, (cite: Boulanger2022)), we predicted the presence of HOCHCHCHO in the PILS data with a probability greater than 50%." (Analysis and results)
   - parameter: Offset position: alpha_J2000 = 16h32m22.58s, delta_J2000 = -24d28m32.8s (0.5 arcsec SW of continuum peak)  
  > "The applied spectrum corresponds to the component B of IRAS16293 at a position offset by 0.5$\ensuremath{''}$ (one beam) with respect to the continuum peak position in the south-west direction ($\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22.58s, $\delta_{\rm J2000}$=-24$\ensuremath{^\circ}$28$\ensuremath{'}$32.8$\ensuremath{''}$)." (Analysis and results)
   - assumption: Local thermodynamic equilibrium (LTE)  
  > "Using a dedicated convolutional neural network (CNN) on a large set of multi-species synthetic spectra assuming local thermodynamic equilibrium (LTE, (cite: Boulanger2022)), we predicted the presence of HOCHCHCHO in the PILS data with a probability greater than 50%." (Analysis and results)
   - fitting: _not stated_
   - validation: Confirmed line identifications with classical analysis using CASSIS  
  > "We confirm that several lines can be identified as HOCHCHCHO with a classical analysis using the CASSIS software." (Analysis and results)
2. **Identify unblended transitions and fit Gaussian line profiles**: Overlay synthetic spectra of previously identified molecules to exclude blended lines, lines with large spectroscopic uncertainties, and lines affected by absorption; fit Gaussians to detected HOCHCHCHO transitions  
  > "To ensure that the lines are not blended with other species, we overlaid the model including the species previously identified in this source." (Analysis and results); "Table [\[List_line_parameters\]](#List_line_parameters) lists the observational parameters of the detected HOCHCHCHO lines obtained after Gaussian fitting." (Additional tables and figures)
   - software: CASSIS
   - parameter: 11 detected lines >= 20 mJy beam^-1 in Band 7, plus 5 undetected lines with small uncertainties  
  > "In total, we found 11 lines ($\gtrsim$ 20 mJy\,beam$^{-1}$) that could be associated to HOCHCHCHO towards IRAS16293 B" (Analysis and results); "To avoid overestimating the column density, we also included five undetected lines presenting small uncertainties in the $\chi^2$ analysis" (Analysis and results)
   - fitting: Single or double Gaussian profile fitting  
  > "Table [\[List_line_parameters\]](#List_line_parameters) lists the observational parameters of the detected HOCHCHCHO lines obtained after Gaussian fitting." (Additional tables and figures); "$\ddagger$ A double Gaussian is used to fit the observations." (Table 2)
   - validation: _not stated_
3. **Constrain column density and excitation temperature via LTE grid fitting**: Generate LTE synthetic spectra over two grids (coarse then fine) of column density N and excitation temperature T_ex, and compute chi-square on unblended and selected undetected lines; also derive upper limits for isomers and 1,3-propanediol  
  > "Synthetic spectra are produced assuming LTE for various values of column densities, $N,$ and excitation temperatures, $T_{\rm ex}$. A $\chi^2$ method is then used on the unblended lines to derive the best fit parameters." (Analysis and results); "To constrain the best-fit parameters, we ran two grids: one with large steps followed by another one around the best model with smaller steps ($\Delta N$ = 2 $\times$ 10$^{14}$ cm$^{-2}$, $\Delta T$ = 25 K)." (Analysis and results)
   - software: CASSIS
   - parameter: Fine grid: N from 2 x 10^14 to 3 x 10^15 cm^-2 (step 2 x 10^14 cm^-2), T_ex from 50 to 350 K (step 25 K)  
  > "To constrain the best-fit parameters, we ran two grids: one with large steps followed by another one around the best model with smaller steps ($\Delta N$ = 2 $\times$ 10$^{14}$ cm$^{-2}$, $\Delta T$ = 25 K)." (Analysis and results); "For this second grid, the column density ranged from 2 $\times$ 10$^{14}$ to 3 $\times$ 10$^{15}$ cm$^{-2}$, while the excitation temperature was between 50 and 350 K." (Analysis and results)
   - parameter: Fixed T_ex tests at 125 K and 300 K  
  > "If we assume excitation temperatures of 125 and 300 K, we obtain column densities of 3-hydroxypropenal of 1.0 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0) and 1.8 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0), respectively." (Analysis and results)
   - assumption: Local thermodynamic equilibrium (LTE)  
  > "Synthetic spectra are produced assuming LTE for various values of column densities, $N,$ and excitation temperatures, $T_{\rm ex}$." (Analysis and results)
   - fitting: Chi-square minimization over N and T_ex grid  
  > "A $\chi^2$ method is then used on the unblended lines to derive the best fit parameters." (Analysis and results)
   - validation: Checked consistency across Band 6 and Band 3 spectral windows and verified that no predicted lines are missing  
  > "We carefully checked that no HOCHCHCHO line is missing with this model in other parts of the PILS survey. In Band 6, two faint lines are detected at 247.5312 and 250.4599 GHz and are in agreement with the model." (Analysis and results)
4. **Produce moment 0 maps of HOCHCHCHO transitions**: Create integrated intensity (moment 0) maps for three transitions of HOCHCHCHO  
  > "The moment 0 maps of the transitions at 329.1843, 330.8262, and 335.3758 GHz are presented in Fig. [7](#fig_map)." (Analysis and results)
   - parameter: Transitions at 329.1843, 330.8262, and 335.3758 GHz  
  > "The moment 0 maps of the transitions at 329.1843, 330.8262, and 335.3758 GHz are presented in Fig. [7](#fig_map)." (Analysis and results)
   - fitting: _not stated_
   - validation: Compared spatial morphology to other COMs detected in IRAS 16293 B  
  > "The emission is compact and similar to the other COMs detected in this source (see e.g., (cite: Lykke2017; Jorgensen2018; Calcutt2018))." (Analysis and results)
5. **Model chemical evolution of C3H4O2 isomers**: Run a three-phase time-dependent astrochemical model using Nautilus with an updated network including six C3H4O2 isomers and DFT-calculated reaction barriers  
  > "To better understand the chemistry of HOCHCHCHO and its isomers, we used the Nautilus code (cite: Ruaud2016), a three-phase gas, grain surface, and grain mantle time-dependent chemical model." (Chemical modeling and discussion); "The barriers were calculated using the DFT method associated with the M06-2X functional." (Chemical modeling and discussion)
   - software: Nautilus
   - parameter: Pre-stellar stage: density = 5 x 10^4 cm^-3, T_gas = T_dust = 10 K, A_V = 4.5 mag, cosmic-ray ionization rate = 1.3 x 10^-17 s^-1, UV field = 1 G0, duration = 10^6 years; followed by protostellar collapse stage  
  > "i) a uniform and constant stage, corresponding to the pre-stellar phase, with a density of 5 $\times$ 10$^4$ cm$^{-3}$, a temperature of 10\,K for both gas and dust, a visual extinction of 4.5 mag, a cosmic-ray ionization rate of 1.3 $\times$ 10$^{-17}$ s$^{-1}$, a standard external UV field of 1 G$_0$" (Chemical modeling and discussion); "the initial abundances listed in Table 3 of (cite: Manigand2021), and a duration of 10$^6$ years; and ii) the collapse phase described in (cite: Manigand2021)." (Chemical modeling and discussion)
   - assumption: Isomeric ratio approximated by ratio of rovibrational densities of states at the isomerization barrier; barriers and imaginary frequencies calculated at M06-2X/AVTZ DFT level  
  > "In our network, we consider that the ratio between the isomeric forms is then approximated by the ratio of the rovibrational densities of states of the isomers at the barrier to isomerization." (Chemical modeling of 3-hydroxypropenal (HOCHCHCHO) and its isomers); "The barriers were calculated using the DFT method associated with the M06-2X functional." (Chemical modeling and discussion)
   - fitting: _not stated_
   - validation: Compared predicted abundances relative to CH3OH against observed values and upper limits  
  > "HOCHCHCHO has a predicted abundance with respect to CH$_3$OH of 4.6\,$\times$\,10$^{-4}$ in agreement with the observations (1\,$\times$\,10$^{-4}$)" (Chemical modeling and discussion)

## Software

- **CASSIS** : Classical spectral line identification and LTE synthetic spectrum modeling  
  > "We confirm that several lines can be identified as HOCHCHCHO with a classical analysis using the CASSIS software." (Analysis and results)
- **Nautilus** : Three-phase gas, grain surface, and grain mantle time-dependent astrochemical modeling  
  > "To better understand the chemistry of HOCHCHCHO and its isomers, we used the Nautilus code (cite: Ruaud2016), a three-phase gas, grain surface, and grain mantle time-dependent chemical model." (Chemical modeling and discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HOCHCHCHO column density (best-fit at T_ex = 350 K) | 2.2e15 | not stated | cm^-2 | 3 | The best-fit model was obtained for a column density $N$ of 2.2 $\times$ 10$^{15}$ cm$^{-2}$ and an excitation temperature $T_{\rm ex}$ of 350 K ($\chi^2_{\rm red}$ $\sim$ 2.0). |
| HOCHCHCHO column density (assuming T_ex = 125 K) | 1.0e15 | not stated | cm^-2 | 3 | If we assume excitation temperatures of 125 and 300 K, we obtain column densities of 3-hydroxypropenal of 1.0 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0) and 1.8 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0), respectively. |
| HOCHCHCHO column density (assuming T_ex = 300 K) | 1.8e15 | not stated | cm^-2 | 3 | If we assume excitation temperatures of 125 and 300 K, we obtain column densities of 3-hydroxypropenal of 1.0 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0) and 1.8 $\times$ 10$^{15}$ cm$^{-2}$ ($\chi^2_{\rm red}$ $\sim$ 2.0), respectively. |
| HOCHCHCHO excitation temperature range | 75-350 | 3 sigma | K | 3 | Our $\chi^2$ analysis shows that various models with excitation temperatures in the 75–350 K range can properly reproduce the lines included in the calculation (3$\sigma$ uncertainty). |
| Observed HOCHCHCHO abundance relative to CH3OH | 1.0e-4 | not stated | dimensionless | 3 | Based on the observed line intensities and assuming local thermodynamic equilibrium, its column density is constrained to be $\sim$10$^{15}$ cm$^{-2}$, corresponding to an abundance of 10$^{-4}$ relative to methanol, CH$_3$OH.; / 3-Hydroxypropenal / HOCHCHCHO / 1.4 $\times$ 10$^{-8}$ / 4.6 $\times$ 10$^{-4}$ / 1.0 $\times$ 10$^{-4}$ / |
| C2H3OCHO (vinyl formate) column density upper limit | < 4e15 | not stated | cm^-2 | 3 | C$_2$H$_3$OCHO is not detected with an upper limit of 4\,$\times$\,10$^{15}$ cm$^{-2}$ based on the undetected transition at 355.2462 GHz. |
| s-cis C2H3COOH (propenoic acid) column density upper limit | < 1e15 | not stated | cm^-2 | 3 | Upper limits of 1\,$\times$\,10$^{15}$ cm$^{-2}$ and 4\,$\times$\,10$^{15}$ cm$^{-2}$ are also derived for the s-cis and s-trans conformers of C$_2$H$_3$COOH, respectively. |
| s-trans C2H3COOH (propenoic acid) column density upper limit | < 4e15 | not stated | cm^-2 | 3 | Upper limits of 1\,$\times$\,10$^{15}$ cm$^{-2}$ and 4\,$\times$\,10$^{15}$ cm$^{-2}$ are also derived for the s-cis and s-trans conformers of C$_2$H$_3$COOH, respectively. |
| CH2OHCH2CH2OH (1,3-propanediol, conformer a'GG'g) column density upper limit | < 1e15 | not stated | cm^-2 | 3 | The lower energy conformer a’GG’g present in the CDMS database was searched for and an upper limit of 1\,$\times$\,10$^{15}$ cm$^{-2}$ was derived. |
| Predicted HOCHCHCHO abundance relative to CH3OH | 4.6e-4 | factor of 10 | dimensionless | 5 | / 3-Hydroxypropenal / HOCHCHCHO / 1.4 $\times$ 10$^{-8}$ / 4.6 $\times$ 10$^{-4}$ / 1.0 $\times$ 10$^{-4}$ /; Table notes: The total uncertainty on the predicted abundances is about a factor 10. |
| Predicted CH3COCHO (methyl glyoxal) abundance relative to CH3OH | 2.4e-3 | factor of 10 | dimensionless | 5 | / Methyl glyoxal / CH$_3$COCHO / 7.4 $\times$ 10$^{-8}$ / 2.4 $\times$ 10$^{-3}$ / /; Table notes: The total uncertainty on the predicted abundances is about a factor 10. |
| Predicted CH2COHCHO (2-hydroxypropenal) abundance relative to CH3OH | 6.6e-4 | factor of 10 | dimensionless | 5 | / 2-Hydroxypropenal / CH$_2$COHCHO / 2.0 $\times$ 10$^{-8}$ / 6.6 $\times$ 10$^{-4}$ / /; Table notes: The total uncertainty on the predicted abundances is about a factor 10. |
| Predicted HCOCH2CHO (propanedial) abundance relative to CH3OH | 9.9e-5 | factor of 10 | dimensionless | 5 | / Propanedial / HCOCH$_2$CHO / 3.0 $\times$ 10$^{-9}$ / 9.9 $\times$ 10$^{-5}$ / /; Table notes: The total uncertainty on the predicted abundances is about a factor 10. |

## Qualitative findings

- Tentative first detection of 3-hydroxypropenal (HOCHCHCHO) in the interstellar medium towards IRAS 16293-2422 B  
  > "we tentatively detected 3-hydroxypropenal (HOCHCHCHO) for the first time in the interstellar medium towards source B." (abstract)
- HOCHCHCHO is mainly formed via the grain surface reaction CH2CHO + HCO -> HCOCH2CHO followed by tautomerization into HOCHCHCHO  
  > "This species is mainly formed through the grain surface reaction CH$_2$CHO + HCO $\rightarrow$ HCOCH$_2$CHO, followed by the tautomerization of HCOCH$_2$CHO into HOCHCHCHO." (abstract)
- Two isomers, CH3COCHO (methyl glyoxal) and CH2COHCHO (2-hydroxypropenal), are predicted to be more abundant than HOCHCHCHO  
  > "Two isomers, CH$_3$COCHO and CH$_2$COHCHO, are predicted to be even more abundant than HOCHCHCHO." (abstract)

## Claim tuples

- H: 3-hydroxypropenal (HOCHCHCHO) is present and detectable in the solar-type protostar IRAS 16293-2422 B | E: Applied a CNN to the ALMA-PILS spectrum of IRAS 16293 B and performed a classical LTE synthetic spectrum and chi-square analysis with CASSIS across Band 7 and Band 6 | R: 11 lines in Band 7 (7 fully reproduced, 4 partially blended) and 2 faint lines in Band 6 match HOCHCHCHO, yielding N ~ 1.0 x 10^15 cm^-2 (at T_ex = 125 K) and an abundance of 10^-4 relative to CH3OH | F: 3-hydroxypropenal is tentatively detected for the first time in the interstellar medium towards IRAS 16293 B | **partially**
- H: Grain-surface radical association reactions and keto-enol tautomerization can account for the observed abundance of HOCHCHCHO in IRAS 16293 B | E: Updated the Nautilus three-phase chemical network with six C3H4O2 isomers and DFT-calculated reaction barriers, and simulated the pre-stellar and protostellar collapse phases | R: The model predicts an HOCHCHCHO abundance relative to CH3OH of 4.6 x 10^-4 (within a factor of 10 uncertainty), consistent with the observed 1.0 x 10^-4, mainly via CH2CHO + HCO -> HCOCH2CHO followed by tautomerization | F: The chemical model reproduces the observed abundance of HOCHCHCHO within uncertainties through grain-surface radical association and tautomerization | **supported**
- H: Other C3H4O2 isomers are also abundant and potentially detectable in IRAS 16293 B | E: Predicted abundances of five other C3H4O2 isomers with the Nautilus code and searched for spectroscopically available isomers (C2H3OCHO and C2H3COOH) in PILS data | R: C2H3OCHO and C2H3COOH are not detected (upper limits <= 4 x 10^-4 and <= 5 x 10^-4 relative to CH3OH, consistent with low predicted abundances of 2.8 x 10^-5 and 7.3 x 10^-9), whereas CH3COCHO and CH2COHCHO are predicted at 2.4 x 10^-3 and 6.6 x 10^-4 relative to CH3OH but lack spectroscopic catalog data | F: CH3COCHO and CH2COHCHO are predicted to be more abundant than HOCHCHCHO and potentially detectable once spectroscopic studies become available | **supported**

## Reasoning

- Why this data: The ALMA-PILS survey is an unbiased spectral survey of IRAS 16293-2422, ideal for identifying complex organic molecules, and the 0.5 arcsec offset position towards component B exhibits narrow (FWHM ~ 1 km s^-1), bright lines free of strong absorption  
  > "The Protostellar Interferometric Line Survey (PILS, (cite: Jorgensen2016)), carried out with the Atacama Large Millimeter/submillimeter Array (ALMA), has contributed significantly to the characterization of the chemical content in this source." (Introduction); "This position is regularly used in the PILS studies to search for molecules and isotopologues, as the lines are relatively narrow ($FWHM$ $\sim$ 1 km s$^{-1}$) and bright without being affected by absorption features (cite: Coutens2016; Lykke2017)." (Analysis and results)
- Why this method: A CNN was used to rapidly screen the multi-species spectrum for candidate molecules, followed by standard CASSIS LTE synthetic spectrum fitting on unblended lines and Nautilus three-phase chemical modeling to understand formation pathways  
  > "Using a dedicated convolutional neural network (CNN) on a large set of multi-species synthetic spectra assuming local thermodynamic equilibrium (LTE, (cite: Boulanger2022)), we predicted the presence of HOCHCHCHO in the PILS data with a probability greater than 50%." (Analysis and results); "To better understand the chemistry of HOCHCHCHO and its isomers, we used the Nautilus code (cite: Ruaud2016), a three-phase gas, grain surface, and grain mantle time-dependent chemical model." (Chemical modeling and discussion)
- Alternative: Searching for HOCHCHCHO towards IRAS 16293 A was rejected because broader lines prevent identification of isolated transitions  
  > "As the lines are broader towards IRAS16293 A, it is not possible to identify isolated transitions of 3-hydroxypropenal toward that source." (Analysis and results)
- Alternative: High excitation temperature (>= 300 K) for HOCHCHCHO was disfavored because transitions at 343.4656, 349.9189, and 350.0168 GHz are not detected within their spectroscopic uncertainties  
  > "However, there are a few exceptions for the transitions at 343.4656, 349.9189, and 350.0168 GHz that do not show lines within their uncertainties, which suggests that the excitation temperature could be lower than 300 K." (Analysis and results)
- Alternative: Formation of C3H4O2 isomers via O or OH reactions with unsaturated C3HxO species on grains was found to be inefficient compared to HCO + C2H3O radical associations  
  > "However, O mainly reacts with the abundant radicals on the grains (HCO, CH$_2$OH, and CH$_3$O) and the production of C$_3$H$_4$O$_2$ isomers from the reactions of O is limited." (Chemical modeling of 3-hydroxypropenal (HOCHCHCHO) and its isomers); "In contrast to the O + C$_3$H$_x$O reactions, the reactions with HCO are much more efficient because HCO is abundant and relatively mobile on the grains (cite: Wakelam2017; Minissale2016)." (Chemical modeling of 3-hydroxypropenal (HOCHCHCHO) and its isomers)
- How they decided it was enough: _not stated_
- Limitation (authors): Excitation temperature of HOCHCHCHO is poorly constrained (75-350 K) because detected unblended lines span a small range of E_up and high-J, low-K_a transitions have large spectroscopic uncertainties  
  > "However, the excitation temperature was not well constrained. Our $\chi^2$ analysis shows that various models with excitation temperatures in the 75–350 K range can properly reproduce the lines included in the calculation (3$\sigma$ uncertainty)." (Analysis and results); "It is due to the $E_{\rm up}$ values of the detected lines that only span a small range" (Analysis and results)
- Limitation (authors): Four of the 11 detected Band 7 lines are only partially reproduced by the best-fit model, likely due to partial blending with unknown species  
  > "The lines at 333.1546, 341.8653, 356.3017, and 362.2382 GHz are only partially reproduced, which could mean that they are partially blended with unknown species." (Analysis and results)
- Limitation (authors): Three C3H4O2 isomers (HCOCH2CHO, CH3COCHO, CH2COHCHO) lack spectroscopic entries in CDMS and JPL and could not be searched for in the data  
  > "HCOCH$_2$CHO (propanedial), CH$_3$COCHO (methylglyoxal), and CH$_2$COHCHO (2-hydroxypropenal) are not in the spectroscopic databases CDMS and JPL (cite: Pickett1998)." (Analysis and results)
- Limitation (authors): Predicted chemical abundances have a total uncertainty of about a factor of 10 due to uncertain branching ratios (factor of 2) and H-atom destruction tunneling barriers (factor of 5), and grain isomerization of CH3COCHO into CH2COHCHO may be less favorable than modeled  
  > "For CH$_2$COHCHO, it is more ambiguous because one of the main pathways of formation is the isomerization of CH$_3$COCHO, which could be very less favorable on grains that the result given by the methodology used here." (Chemical modeling and discussion); "Thus, the total uncertainty on the predicted abundances of the C$_3$H$_4$O$_2$ isomers is about a factor of 10." (Chemical modeling and discussion)
- Caveat (inferred, ours): The detection is only tentative, relying on 7 unblended lines in a highly line-rich spectrum where confusion and partial blending (seen in 4 additional lines) are pervasive.
- Caveat (inferred, ours): The source size (beam filling factor) assumed in the CASSIS LTE modeling and the exact reference CH3OH column density are not explicitly stated in this Letter, requiring consultation of earlier PILS papers.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Assumed source angular size (beam filling factor) for CASSIS LTE synthetic spectrum calculation
- Missing: Reference CH3OH column density used to compute relative abundances
- Missing: Full updated Nautilus chemical network files (only C3H4O2 and C2H3O subset is tabulated in Table E.1)
- Missing: Trained CNN model weights and configuration from Boulanger et al. 2022
- Data volume (inferred): ~100 MB for the extracted 1D PILS spectrum at the offset position; ~100 GB if re-imaging the full PILS Band 7 cubes
- Score (inferred): 7/5, The PILS dataset is public, the extraction coordinates, line lists, spectroscopic parameters (CDMS), LTE grid parameters, and new chemical reactions are thoroughly tabulated, though a few inherited parameters (source size, CH3OH reference column density, full Nautilus network file) require consulting companion papers.
- Rediscovery candidate: yes, Public ALMA-PILS archival data with exact extraction coordinates, complete line tables, and clear numeric column density targets reproducible via standard LTE spectral fitting (CASSIS).

## Links

- Method: (cite: Boulanger2022) (Convolutional neural network (CNN) method used to predict the presence of HOCHCHCHO in the PILS spectrum)
- Method: (cite: Ruaud2016) (Nautilus three-phase astrochemical modeling code)
- Method: (cite: Vastel2015) (CASSIS spectral analysis software used for LTE modeling and line identification)
- Companion: (cite: Jorgensen2016) (ALMA-PILS survey overview, observations, data reduction, and continuum subtraction)
- Companion: (cite: Coutens2019) (Baseline list of previously identified species in IRAS 16293 B used for spectral overlay)
- Companion: (cite: Manigand2021) (Three-carbon molecule study in IRAS 16293 B providing the base chemical network, initial abundances, and two-stage physical collapse model)
- Related: ALMA-PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 104,
 "quotes_ok": 104,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 1,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 13,
 "numeric_problems": 0,
 "fill": {
  "facts": 86,
  "stated": 52,
  "rate": 0.605
 },
 "evidence_ok": true
}
```
