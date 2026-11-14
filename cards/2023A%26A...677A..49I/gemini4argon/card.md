# Investigation of the rotational spectrum of CD<SUB>3</SUB>OD and an astronomical search toward IRAS 16293-2422

`2023A&A...677A..49I` | Astronomy and Astrophysics 2023 | first author: Ilyushin, V. V. | arXiv: 2307.07801 | DOI: 10.1051/0004-6361/202347105

Card schema 1.0 | model gemini-4-argon | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Develop an accurate spectroscopic model of CD3OD in low-lying torsional states up to 1.1 THz and search for CD3OD toward the protostellar system IRAS 16293-2422 using ALMA PILS data.  
  > "The goal of our present investigation is to develop a spectroscopic model of the CD$_3$OD isotopolog in low-lying torsional states which is sufficiently accurate to provide reliable calculations of line positions and linestrengths for astronomical searches" (Introduction); "We generated a line list that was based on our present results, which we applied in a search for CD$_3$OD in the Atacama Large Millimeter/submillimeter Array (ALMA) data of the Protostellar Interferometric Line Survey" (Introduction)
- Target **IRAS 16293-2422**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: _not stated_
- frequencies and spectral setup: 329 to 363 GHz, spectral resolution ~0.2 km s^-1  
  > "PILS represents an unbiased spectral survey of the Class 0 protostellar system IRAS 16293$-$2422 using the Atacama Large Millimeter/submillimeter Array covering the frequency range from 329 to 363 GHz." (Astronomical search for CD$_3$OD); "show abundant lines of complex organic molecules at an angular resolution of $\sim$0.5$''$ and a spectral resolution of $\sim$0.2 km s$^{-1}$." (Astronomical search for CD$_3$OD)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5''  
  > "show abundant lines of complex organic molecules at an angular resolution of $\sim$0.5$''$ and a spectral resolution of $\sim$0.2 km s$^{-1}$." (Astronomical search for CD$_3$OD)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS survey data  
  > "The new spectroscopic calculations were used to search for CD$_3$OD in data from the Protostellar Interferometric Line Survey (PILS; (cite: PILS_2016))." (Astronomical search for CD$_3$OD)
- Line: CD3OD rotational transitions in ground and first excited torsional states (v_t = 0, 1) (329 to 363 GHz (16 strongest lines including 348.988 GHz))
- Other facility **Institute of Radio Astronomy (IRA) of NASU millimeter wave spectrometer**: Laboratory rotational spectra of CD3OD in the frequency ranges 34.5-184 GHz and 234-420 GHz  
  > "The measurements of the CD$_3$OD spectrum at the Institute of Radio Astronomy (IRA) of NASU were performed in the frequency ranges of 34.5$-$184 GHz and 234$-$420 GHz using an automated synthesizer based millimeter wave spectrometer (cite: Alekseev2012)." (Rotational spectra at IRA NASU)
- Other facility **Universität zu Köln spectrometer**: Laboratory rotational spectra of CD3OD between 370 and 1095 GHz  
  > "We utilized three VDI frequency multipliers driven by Rohde & Schwarz SMF 100A synthesizers as sources and a closed cycle liquid He-cooled InSb bolometer (QMC Instruments Ltd) as detector to cover frequencies between 370 and 1095 GHz" (Rotational spectra at the Universität zu Köln)
- External data: 488 v_t = 0 and 182 v_t = 1 microwave transitions of CD3OD up to J_max = 25 and K_max = 14  
  > "We started our analysis from the results of (cite: CD3OD_rot-K_2006), where the dataset, consisting of 488 $\varv_{\rm t} = 0$ and 182 $\varv_{\rm t} = 1$ microwave transitions, ranging up to $J_{\rm max} = 25$ and $K_{\rm max} = 14$" (Spectroscopic results) [from (cite: CD3OD_rot-K_2006)]
- External data: Far-infrared (FIR) data of CD3OD  
  > "Finally, at an advanced stage of our analysis, the FIR data from (cite: CD3OD_rot_etc-IM_2021) were added to the fit." (Spectroscopic results) [from (cite: CD3OD_rot_etc-IM_2021)]
- External data: Dipole moment function of CH3OH  
  > "The dipole moment function of (cite: MEKHTIEV1999171) was employed in our calculations" (Spectroscopic results) [from (cite: MEKHTIEV1999171)]
- External data: Permanent dipole moment components for CD3OD (mu_a = 0.867 D and mu_b = 1.430 D)  
  > "replaced by appropriate ones for CD$_3$OD $\mu_a = 0.867$ D and $\mu_b = 1.430$ D taken from (cite: MUKHOPADHYAY19981307)." (Spectroscopic results) [from (cite: MUKHOPADHYAY19981307)]
- External data: CH3OH main isotopolog column density constrained by CH3^18OH  
  > "The quoted column density would correspond to an CD$_3$OD abundance of 0.02% relative to the main isotopolog CH$_3$OH (the column density of that constrained by observations of optically thin transitions of CH$_3^{18}$OH)." (Astronomical search for CD$_3$OD) [from (cite: deuteration_16293_2018)]

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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- PILS survey data and LTE synthetic spectrum modeling approach  
  > "The new spectroscopic calculations were used to search for CD$_3$OD in data from the Protostellar Interferometric Line Survey (PILS; (cite: PILS_2016))." (Astronomical search for CD$_3$OD); "The search for CD$_3$OD was conducted following the approach applied in other papers from PILS: synthetic spectra are calculated assuming that the excitation of the molecule is characterized by local thermodynamical equilibrium" (Astronomical search for CD$_3$OD) [from (cite: PILS_2016)]
- Excitation temperature of 225 K taken similar to that of CD3OH  
  > "For the search we assume a temperature of 225 K similar to that of CD$_3$OH (cite: CD3OH_rot_2022)." (Astronomical search for CD$_3$OD) [from (cite: CD3OH_rot_2022)]
- Two-step diagonalization procedure in the rho-axis-method  
  > "The RAM36 code uses the two-step diagonalization procedure of (cite: Herbst:1984) and in the current study, we keep 31 torsional basis functions at the first diagonalization step and 11 torsional basis functions at the second diagonalization step." (Spectroscopic properties of CD$_3$OD and our theoretical approach) [from (cite: Herbst:1984)]
- K-labeling scheme for torsion-rotation energy levels  
  > "The details of this approach to $K$-labeling for torsion–rotation energy levels in low-barrier molecules can be found in (cite: ILYUSHIN2004)." (Spectroscopic properties of CD$_3$OD and our theoretical approach) [from (cite: ILYUSHIN2004)]
- Ordering scheme for Hamiltonian terms  
  > "when applying the ordering scheme of (cite: Nakagawa:1987)." (Spectroscopic results) [from (cite: Nakagawa:1987)]

### Not stated but needed to reproduce (our reading)

- Exact sky coordinates of the extracted spectrum offset position near IRAS 16293-2422 B
- Software or code used to compute the LTE synthetic spectra for the ALMA PILS comparison
- Assumed source size / beam filling factor for the LTE synthetic spectrum calculation
- Exact value of the CH3OH reference column density used to compute the 0.02% relative abundance

## Analysis recipe

1. **Fit laboratory and literature torsion-rotation spectra of CD3OD using a RAM Hamiltonian**: Bootstrap least-squares fitting of 4337 FIR and 10001 microwave line frequencies using the rho-axis-method (RAM) Hamiltonian with a two-step diagonalization procedure.  
  > "We employed the RAM36 code (cite: Ilyushin:2010; Ilyushin:2013)" (Spectroscopic properties of CD$_3$OD and our theoretical approach); "Our final CD$_3$OD dataset for the purposes of this paper involves 4337 FIR and 10001 microwave line frequencies that correspond, due to blending, to 16259 transitions with $J_{\rm max} = 51$." (Spectroscopic results); "A Hamiltonian model consisting of 117 parameters provided a fit with a weighted root mean square (RMS) deviation of 0.71 which was selected as our "best fit" for this paper." (Spectroscopic results)
   - software: RAM36
   - parameter: 117 Hamiltonian parameters; 31 torsional basis functions at first step, 11 at second step; J_max = 51  
  > "in the current study, we keep 31 torsional basis functions at the first diagonalization step and 11 torsional basis functions at the second diagonalization step." (Spectroscopic properties of CD$_3$OD and our theoretical approach); "A Hamiltonian model consisting of 117 parameters provided a fit with a weighted root mean square (RMS) deviation of 0.71 which was selected as our "best fit" for this paper." (Spectroscopic results)
   - fitting: Weighted least-squares fit achieving weighted RMS deviation of 0.71  
  > "A Hamiltonian model consisting of 117 parameters provided a fit with a weighted root mean square (RMS) deviation of 0.71 which was selected as our "best fit" for this paper." (Spectroscopic results)
   - validation: Checked convergence criteria, agreement of duplicate measurements between Kharkiv and Cologne (370-420 GHz), and verified all data groups fit within experimental uncertainties.  
  > "A rather good agreement within the experimental uncertainties was observed for this limited set of duplicate new measurements." (Spectroscopic results); "The final set of the parameters converged perfectly in all three senses: (i) the relative change in the weighted RMS deviation of the fit at the last iteration was about $\sim$10$^{-7}$" (Spectroscopic results)
2. **Generate astronomical line list and partition function for CD3OD**: Calculate transition frequencies, uncertainties, lower state energies, and transition strengths up to 1.33 THz from the best-fit RAM Hamiltonian, and compute torsion-rotation partition function via direct summation.  
  > "Using the parameters of our final fit we calculated a list of CD$_3$OD transitions in the ground and first excited torsional states for astronomical observations." (Spectroscopic results); "We provide additionally the torsion-rotation part of the partition function $Q_{\rm rt}$(T) of CD$_3$OD calculated from first principles, that is, via direct summation over the torsion-rotational states." (Spectroscopic results)
   - software: RAM36
   - parameter: v_t <= 1, J <= 55, |K_a| <= 25, frequency <= 1.33 THz, uncertainty < 0.1 MHz; partition function up to J = 90 and n_vt = 11  
  > "we limited our predictions by $\varv_{\rm t} \leq 1$, $J \leq 55$ and $|K_{a}| \leq 25$." (Spectroscopic results); "The calculations were done up to 1.33 THz. Additionally, we limit our calculations to transitions for which calculated uncertainties are less than 0.1 MHz." (Spectroscopic results); "The maximum $J$ value is 90 and $n_{\varv_{\rm t}} = 11$ torsional states were taken into account." (Spectroscopic results)
   - assumption: Permanent dipole moment components mu_a = 0.867 D and mu_b = 1.430 D  
  > "where the values for the permanent dipole moment components of CH$_3$OH were replaced by appropriate ones for CD$_3$OD $\mu_a = 0.867$ D and $\mu_b = 1.430$ D taken from (cite: MUKHOPADHYAY19981307)." (Spectroscopic results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Search for CD3OD and derive upper column density limit in IRAS 16293-2422 B**: Calculate LTE synthetic spectra and compare the 16 strongest predicted lines of CD3OD against the ALMA PILS spectrum at the offset position near IRAS 16293-2422 B.  
  > "synthetic spectra are calculated assuming that the excitation of the molecule is characterized by local thermodynamical equilibrium, which is reasonable at the densities on the scales probed by PILS (cite: PILS_2016)." (Astronomical search for CD$_3$OD); "Figure 3 shows the 16 lines predicted to be strongest for this temperature: the column density is taken to be the maximum possible without overproducing lines compared to the RMS noise level of the data" (Astronomical search for CD$_3$OD)
   - parameter: v_LSR = 2.6 km s^-1, FWHM = 1 km s^-1, T_ex = 225 K  
  > "The source velocity offset relative to the local standard of rest is assumed to be 2.6 km s$^{-1}$ and the line full width at half maximum (FWHM) is taken as 1 km s$^{-1}$." (Astronomical search for CD$_3$OD); "For the search we assume a temperature of 225 K similar to that of CD$_3$OH (cite: CD3OH_rot_2022)." (Astronomical search for CD$_3$OD)
   - assumption: Local thermodynamical equilibrium (LTE), T = 225 K, v_LSR = 2.6 km s^-1, FWHM = 1 km s^-1  
  > "synthetic spectra are calculated assuming that the excitation of the molecule is characterized by local thermodynamical equilibrium" (Astronomical search for CD$_3$OD); "The source velocity offset relative to the local standard of rest is assumed to be 2.6 km s$^{-1}$ and the line full width at half maximum (FWHM) is taken as 1 km s$^{-1}$." (Astronomical search for CD$_3$OD); "For the search we assume a temperature of 225 K similar to that of CD$_3$OH (cite: CD3OH_rot_2022)." (Astronomical search for CD$_3$OD)
   - fitting: Column density set to maximum possible without overproducing lines compared to RMS noise level  
  > "the column density is taken to be the maximum possible without overproducing lines compared to the RMS noise level of the data with a value of 2$\times 10^{15}$ cm$^{-2}$." (Astronomical search for CD$_3$OD)
   - validation: _not stated_

## Software

- **RAM36** : Fitting the torsion-rotation RAM Hamiltonian to the CD3OD spectroscopic dataset and generating predictions  
  > "We employed the RAM36 code (cite: Ilyushin:2010; Ilyushin:2013) that was successfully used in the past for a number of near prolate tops" (Spectroscopic properties of CD$_3$OD and our theoretical approach); "Since the BELGI code (cite: Kleiner:2010) was used in the previous study (cite: CD3OD_rot-K_2006), we refit the available dataset with the RAM36 program (cite: Ilyushin:2010; Ilyushin:2013) as the first step." (Spectroscopic results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Weighted RMS deviation of best-fit RAM Hamiltonian model | 0.71 | not stated | dimensionless | 1 | A Hamiltonian model consisting of 117 parameters provided a fit with a weighted root mean square (RMS) deviation of 0.71 which was selected as our "best fit" for this paper. |
| CD3OD parameter (1/2)V_3 | 181.1021642 | 0.0000055 | cm^-1 | 1 | $2_{2,0}$ / $(1-\cos 3\alpha)$ / $(1/2)V_3$ / $181.1021642(55)$ |
| CD3OD parameter F | 14.75939375 | 0.00000090 | cm^-1 | 1 | $2_{2,0}$ / $p_\alpha^2$ / $F$ / $14.75939375(90)$ |
| CD3OD parameter rho | 0.8219648943 | 0.0000000019 | dimensionless | 1 | $2_{1,1}$ / $P_ap_\alpha$ / $\rho$ / $0.8219648943(19)$ |
| CD3OD rotational parameter A | 2.1693625 | 0.0000090 | cm^-1 | 1 | $2_{0,2}$ / $P_a^2$ / $A$ / $2.1693625(90)$ |
| CD3OD rotational parameter B | 0.63055239 | 0.00000026 | cm^-1 | 1 | $2_{0,2}$ / $P_b^2$ / $B$ / $0.63055239(26)$ |
| CD3OD rotational parameter C | 0.59843413 | 0.00000022 | cm^-1 | 1 | $2_{0,2}$ / $P_c^2$ / $C$ / $0.59843413(22)$ |
| CD3OD upper column density limit toward IRAS 16293-2422 B | 2e15 | upper limit | cm^-2 | 3 | the column density is taken to be the maximum possible without overproducing lines compared to the RMS noise level of the data with a value of 2$\times 10^{15}$ cm$^{-2}$.; The upper column density limit of 2$\times 10^{15}$ cm$^{-2}$ for CD$_3$OD was derived based on the assumption of an excitation temperature of 225 K |
| CD3OD/CH3OH abundance ratio upper limit | 0.02 | upper limit | % | 3 | The quoted column density would correspond to an CD$_3$OD abundance of 0.02% relative to the main isotopolog CH$_3$OH; Comparison with the CH$_3$OH main isotopolog (for which the column density is deduced from optically thin lines of CH$_3^{18}$OH) yields a CD$_3$OD/CH$_3$OH ratio as high as $\sim$0.02% |
| Implied D/H ratio from CD3OD upper limit | 12 | not stated | % | 3 | If all D/H substitutions would be considered equally probable, this in turn would imply a D/H ratio of about 12% |

## Qualitative findings

- CD3OD is not confidently detected toward IRAS 16293-2422 in the PILS dataset, though three to four transitions match observed features at or slightly above the 3 sigma level.  
  > "As we can see, three to four lines match the observed spectral features at or slightly above the 3$\sigma$ level in the data." (Astronomical search for CD$_3$OD); "While this makes the assignments of the three to four transitions plausible it is not possible to claim a solid detection based on so few lines." (Astronomical search for CD$_3$OD)
- The second excited torsional state (v_t = 2) of CD3OD exhibits perturbations likely caused by intervibrational interactions from low-lying small-amplitude vibrations.  
  > "After revealing perturbations in the second excited torsional state of CD$_3$OD, presumably caused by the intervibrational interactions arising from low-lying small-amplitude vibrations in this molecule, we concentrated our efforts on refining the theoretical model" (Conclusion)

## Claim tuples

- H: A 117-parameter RAM Hamiltonian model can fit the torsion-rotation spectrum of CD3OD in its ground and first excited torsional states up to 1.1 THz within experimental error. | E: Measured laboratory spectra from 34.5 GHz to 1.095 THz, combined with FIR data, and fitted 14338 line frequencies (15135 unique transitions up to J=51) using the RAM36 code. | R: Achieved an overall weighted RMS deviation of 0.71, with all data groups fitting within experimental uncertainties. | F: The RAM Hamiltonian model accurately reproduces line positions and intensities for the ground and first excited torsional states of CD3OD. | **supported**
- H: Fully deuterated methanol (CD3OD) is detectable in the ALMA PILS spectral survey of IRAS 16293-2422 at abundances consistent with enhanced D/H ratios seen in other multiply deuterated molecules. | E: Generated a CD3OD line list from the new spectroscopic model and compared LTE synthetic spectra (at T=225 K) against the ALMA PILS data (329-363 GHz) toward the offset position near IRAS 16293-2422 B. | R: Three to four predicted lines match observed features at or slightly above the 3 sigma level, yielding an upper column density limit of 2x10^15 cm^-2 (CD3OD/CH3OH <= 0.02%, implied D/H ~ 12%). | F: A solid detection of CD3OD cannot be claimed due to too few lines, but the upper limit is consistent with enhanced D/H ratios in multiply deuterated species and suggests detection is within reach of deeper ALMA observations at lower frequencies. | **partially**

## Reasoning

- Why this data: The ALMA PILS survey toward the offset position of IRAS 16293-2422 B exhibits intrinsically narrow lines and abundant complex organic molecules, including other deuterated methanol isotopologs (CH2DOH, CH3OD, CHD2OH, CD3OH).  
  > "Toward a position slightly offset from the “B” component of the system, the lines are intrinsically narrow, making it an ideal hunting ground for new species and several complex organic molecules and their isotopologs have been identified there" (Astronomical search for CD$_3$OD)
- Why this method: The rho-axis-method (RAM) is the most effective approach for treating torsional large amplitude motions in methanol-like molecules, and LTE is reasonable at the high densities on the spatial scales probed by PILS.  
  > "we employ the so-called rho-axis-method (RAM), which has proven to be the most effective approach so far in treating torsional large amplitude motions in methanol-like molecules." (Spectroscopic properties of CD$_3$OD and our theoretical approach); "synthetic spectra are calculated assuming that the excitation of the molecule is characterized by local thermodynamical equilibrium, which is reasonable at the densities on the scales probed by PILS (cite: PILS_2016)." (Astronomical search for CD$_3$OD)
- Alternative: Dominant eigenvector component labeling alone was insufficient starting at J ~ 25 due to basis-set mixing, so a combined labeling scheme using eigenvector composition similarity with adjacent J states was adopted.  
  > "In CD$_3$OD, however, the angle between the RAM $a$-axis and PAM $a$-axis is 0.68$^{\circ}$ and $\kappa \approx -0.959$, and it appeared that starting from $J \approx 25$, some eigenvectors do not have a dominant eigenvector component that would allow for unambiguous labeling." (Spectroscopic properties of CD$_3$OD and our theoretical approach); "Therefore, we have employed a combined labeling scheme." (Spectroscopic properties of CD$_3$OD and our theoretical approach)
- Alternative: Fitting full v_t = 2 torsional state transitions and including data from Mukhopadhyay (2022) was rejected for the present fit due to perturbations from intervibrational interactions; only the lowest three K series in v_t = 2 were retained.  
  > "Thus, at the final stage of model refinement, we limited our fitting attempts mainly to the ground and first excited torsional states of CD$_3$OD. Only the lowest three $K$ series for the A and E species in $\varv_{\rm t}=2$ were retained in the fits" (Spectroscopic results); "Taking into account that our efforts are essentially concentrated on the ground and first excited torsional states of CD$_3$OD, we decided not to include any data from (cite: CD3OD_rot_etc-IM_2022) in the present analysis" (Spectroscopic results)
- How they decided it was enough: _not stated_
- Limitation (authors): The v_t = 2 torsional state is perturbed by intervibrational interactions from low-lying small-amplitude vibrations, limiting the model predictions to v_t <= 1.  
  > "it finally became evident that the $\varv_{\rm t}=2$ torsional state poses some problems with fitting. The strong influence of intervibrational interactions arising from low lying small amplitude vibrations in CD$_3$OD, which then propagate down through numerous intertorsional interactions, is a possible explanation" (Spectroscopic results)
- Limitation (authors): Line confusion and the small number of matching transitions (three to four at ~3 sigma) prevent claiming a solid detection of CD3OD in the ALMA PILS data.  
  > "While this makes the assignments of the three to four transitions plausible it is not possible to claim a solid detection based on so few lines." (Astronomical search for CD$_3$OD); "by targeting IRAS 16293-2422 through deep observations at lower frequencies where line confusion may be less problematic." (Astronomical search for CD$_3$OD)
- Caveat (inferred, ours): The upper limit on CD3OD column density is determined visually/heuristically against the RMS noise rather than via a formal statistical fit across all line-free/blended channels.
- Caveat (inferred, ours): The excitation temperature (225 K) is fixed to that of CD3OH rather than varied to test sensitivity of the upper limit.

## Reproducibility

- Data public (paper): Spectroscopic line lists, quantum numbers, uncertainties, residuals, and partition function are publicly available at CDS and CDMS; ALMA project code 2013.1.00278.S is stated.  
  > "The calculations, as well as the experimental line list from the present work, can be found in the online Supplementary material with this article and will also be available in the Cologne Database for Molecular Spectroscopy, (cite: Endres2016)." (Spectroscopic results); "This paper makes use of the following ALMA data: ADS/JAO.ALMA \# 2013.1.00278.S." (Acknowledgements); "The data are available at Centre de Données astronomiques de Strasbourg (CDS) via anonymous ftp to cdsarc.u-strasbg.fr (130.79.128.5) or via http://cdsweb.u-strasbg.fr/cgi-bin/qcat?J/A+A/" (Footnote 1)
- Products in archive: _not stated_
- Missing: Exact sky coordinates of the 0.5'' offset position near IRAS 16293-2422 B used to extract the PILS spectrum
- Missing: Assumed source size (beam filling factor) and continuum background temperature used in the LTE radiative transfer calculation
- Missing: Local RMS noise value adopted in the 329-363 GHz spectral windows to set the 3 sigma threshold
- Data volume (inferred): ~100 MB for the extracted 1D PILS spectrum and spectroscopic tables (several hundred GB if re-imaging the full PILS survey cubes)
- Score (inferred): 7/5, The spectroscopic dataset, Hamiltonian parameters, and calculated line list/partition function are fully published at CDS/CDMS, and the ALMA PILS data are public, though a few LTE modeling parameters (exact offset coordinates, source size) require consulting earlier PILS papers.
- Rediscovery candidate: yes, Both the CD3OD spectroscopic catalog (at CDS/CDMS) and the ALMA PILS dataset (2013.1.00278.S) are public, and the main astronomical result is a numeric upper limit on the column density derived from standard LTE synthetic spectra.

## Links

- Method: (cite: Ilyushin:2010) (Describes the RAM36 code used to fit the torsion-rotation Hamiltonian)
- Method: (cite: Ilyushin:2013) (Further describes the RAM36 program for rho-axis-method spectroscopic fitting)
- Method: (cite: ILYUSHIN2004) (Describes the K-labeling scheme based on eigenvector composition similarity)
- Method: (cite: Nakagawa:1987) (Defines the ordering scheme for symmetry-allowed torsion-rotation Hamiltonian terms)
- Method: (cite: PILS_2016) (Describes the ALMA PILS survey observations, data reduction, and LTE spectral modeling methodology)
- Companion: (cite: CD3OH_rot_2022) (Previous study by the same team on the rotational spectrum and PILS analysis of the CD3OH isotopolog)
- Companion: (cite: CHD2OH_catalog_2022) (Related PILS study on the doubly deuterated methanol isotopolog CHD2OH)
- Companion: (cite: deuteration_16293_2018) (PILS study of singly deuterated methanol (CH2DOH, CH3OD) and CH3^18OH reference column density toward IRAS 16293-2422)
- Related: Protostellar Interferometric Line Survey (PILS)
- Related: Cologne Database for Molecular Spectroscopy (CDMS)

## Checks

```json
{
 "quotes": 81,
 "quotes_ok": 81,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 4,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 37,
  "rate": 0.487
 },
 "evidence_ok": true
}
```
