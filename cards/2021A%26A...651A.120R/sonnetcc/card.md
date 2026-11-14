# Torsional-rotational spectrum of doubly deuterated dimethyl ether (CH<SUB>3</SUB>OCHD<SUB>2</SUB>). First ALMA detection in the interstellar medium

`2021A&A...651A.120R` | Astronomy and Astrophysics 2021 | first author: Richard, C. | arXiv: 2106.07983 | DOI: 10.1051/0004-6361/202141282

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Measure and fit the 0.15-1.5 THz ground-state rotational spectrum of both conformers of doubly-deuterated dimethyl ether (CH3OCHD2), then use the predictions to detect it toward IRAS 16293-2422 B in ALMA PILS data  
  > "This paper presents the first analysis of the 2D-DME from 0.15 to 1.5 THz (or 150 to 1500 GHz) and reports its detection toward the B component toward IRAS 16293-2422." (Introduction)
- Target **IRAS 16293-2422 B (position offset 0.5 arcsec to the southwest)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7  
  > "PILS covers a continuous frequency range from 329.1 to 362.9 GHz of the main atmospheric window in ALMA’s Band 7." (Astronomical search for CH3OCHD2)
- frequencies and spectral setup: continuous coverage 329.1 to 362.9 GHz; spectral resolution ~0.2 km/s  
  > "PILS covers a continuous frequency range from 329.1 to 362.9 GHz" (Astronomical search for CH3OCHD2); "The spectral resolution over this full range is $\approx$ 0.2 km s$^{-1}$" (Astronomical search for CH3OCHD2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.5 arcsec  
  > "with an angular resolution of 0.5$''$" (Astronomical search for CH3OCHD2)
- max recoverable scale: _not stated_
- sensitivity: ~5 mJy beam^-1 km s^-1  
  > "the sensitivity $\approx$ 5 mJy beam$^{-1}$ km s$^{-1}$" (Astronomical search for CH3OCHD2)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PILS program, PI Jes Jørgensen  
  > "(project id: 2013.1.00278.S; PI: Jes Jørgensen)" (Astronomical search for CH3OCHD2)
- Line: CH3OCHD2, asymmetric conformer not stated (24 strongest predicted lines shown, about 20 well fitted) (not stated)
- Line: CH3OCHD2, symmetric conformer not stated (24 strongest predicted lines shown, about 20 well fitted) (not stated)
- Other facility **Lille submillimeter spectrometer (laboratory)**: Laboratory absorption spectra of CH3OCHD2 between 150 and 1500 GHz  
  > "The absorption spectra were measured between 150 and 1500 GHz using the Lille spectrometer (cite: zakharenko2015)." (Lille THz spectrometer)
- External data: D/H ratio of about 3% for mono-deuterated dimethyl ether toward IRAS 16293B from ALMA PILS data  
  > "Through ALMA observations (cite: jorgensen18) determined the D/H ratio for these conformers (corrected for the number of equivalent hydrogen atoms) of about 3% toward one component in this source" (Introduction) [from (cite: jorgensen18)]
- External data: D/H ratios inferred from singly-to-non deuterated dimethyl ether, used as the comparison for the doubly-deuterated enhancement  
  > "These imply D/H ratios that are about a factor of 5 higher than those inferred from the singly-to-non deuterated variants once corrected for the number of equivalent hydrogen atoms (cite: manigand19)." (Astronomical search for CH3OCHD2) [from (cite: manigand19)]
- Simulation/model as data: LTE synthetic spectra with Gaussian line profiles used to identify CH3OCHD2 lines and fit column densities  
  > "We consequently used synthetic spectra calculated under this assumption to identify the lines of" (Astronomical search for CH3OCHD2); "Under the LTE assumption the line profiles are calculated assuming Gaussian line-profiles with constant LSR velocity offsets and line widths." (Astronomical search for CH3OCHD2)

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

- ALMA PILS observations, calibration and imaging taken from the PILS survey paper, not described here  
  > "in Atacama Large Millimeter/submillimeter Array (ALMA) observations from the Protostellar Interferometric Line Survey, PILS (cite: jorgensen16)" (Astronomical search for CH3OCHD2) [from (cite: jorgensen16)]
- LSR velocity 2.6 km/s, line width (FWHM) 1 km/s and source size 0.5 arcsec (Gaussian) adopted as for the single-deuterated variants and most other PILS species  
  > "For these parameters we adopt the same values as for the single-deuterated variants and most other species in the PILS range" (Astronomical search for CH3OCHD2); "a LSR velocity of 2.6 km s$^{-1}$, a line width (FWHM) of 1 km s$^{-1}$ and source size of 0.5$''$ (assumed as a Gaussian distribution)" (Astronomical search for CH3OCHD2) [from the single-deuterated variants and most other species in the PILS range (no citation given in this sentence)]
- Excitation temperature of 125 K adopted from non- and singly-deuterated dimethyl ether  
  > "For the latter we adopt a temperature of 125 K of the non- and singly-deuterated variants of dimethylether" (Astronomical search for CH3OCHD2) [from non- and singly-deuterated dimethyl ether analyses (no citation given in this sentence)]
- Angle alpha fixed to 0 for the asymmetric conformer, following the mono-deuterated analysis  
  > "we have decided to fix the parameter to 0 for the same reasons as discussed in the Section 4 of the mono-deuterated analysis (cite: richard2013)" (Spectral analysis) [from (cite: richard2013)]
- Synthesis of the deuterated ester precursor prepared as previously reported for the trideutero derivative  
  > "This latter was prepared as previously reported for the trideutero derivative but using methan-*d*$_2$-ol as alcohol (cite: yamamoto2016)." (Preparation of the doubly-deuterated DME) [from (cite: yamamoto2016)]

### Not stated but needed to reproduce (our reading)

- ALMA calibration, self-calibration, continuum subtraction and imaging of the PILS data (only a pointer to the PILS survey paper)
- Exact coordinates of the offset position southwest of IRAS16293B and how the spectrum was extracted (aperture or single pixel)
- Which lines were 'reasonably isolated' and used in the chi-squared fit, with their rest frequencies and quantum numbers
- Chi-squared noise model, fit code and column density grid, and any uncertainties on N
- Column density of mono-deuterated dimethyl ether used to form the 15-20% ratio
- Line-free channels or baseline treatment for the synthetic-spectrum comparison
- Distance to IRAS 16293-2422 (not needed for the column density but needed for any physical scaling)

## Analysis recipe

1. **Record laboratory rotational spectrum**: Absorption spectroscopy 150-1500 GHz with the Lille spectrometer, 2f demodulation preferred, InSb bolometer detector  
  > "The absorption spectra were measured between 150 and 1500 GHz using the Lille spectrometer (cite: zakharenko2015)." (Lille THz spectrometer); "Absorption signals were detected by an InSb liquid He-cooled bolometer (QMC Instruments Ltd.)." (Lille THz spectrometer)
   - parameter: Typical pressures 35-60 Pa at room temperature; 220 cm long, 6 cm diameter cell  
  > "The measurements were performed at typical pressures of 35-60 Pa at room temperature." (Lille THz spectrometer)
   - parameter: Line frequency uncertainties 30, 50 and 100 kHz depending on S/N and frequency range  
  > "Estimated uncertainties for measured line frequencies are 30 kHz, 50 kHz, and 100 kHz depending on the observed S/N ratio and the frequency range." (Lille THz spectrometer)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit effective Hamiltonian to the laboratory lines**: Weighted least-squares fit with the ERHAM code (combined axes method) for each conformer; 15 pure rotational and 5 torsion-rotation parameters; congested high-Ka bQ series removed and only isolated lines kept  
  > "To treat the internal rotation, we used the ERHAM code (cite: groner1997; groner2012)." (Spectral analysis); "For each conformer, a set of 15 pure rotational and 5 torsional-rotation parameters of the effective Hamiltonian implemented in the ERHAM code was needed to fit the observed molecular lines." (Spectral analysis); "we decided to remove these congested lines from the final fit and to include only the lines from such series that could be considered as isolated ones." (Spectral analysis)
   - software: ERHAM
   - parameter: ISCD = -1 and alpha = 0 for the symmetric conformer; ISCD = +1 and alpha fixed to 0 for the asymmetric conformer  
  > "Therefore, in the ERHAM code, the symmetry parameters ISCD is set to $-1$ and $\alpha$, the angle between the rho vector and $ab$ principal axes plane, is set to $0$." (Spectral analysis); "Consequently, for the asymmetric conformation, ISCD=$+1$ and after various attempts to set a value to $\alpha$, we have decided to fix the parameter to 0" (Spectral analysis)
   - assumption: The two conformers are treated as two independent asymmetric tops each with one methyl internal rotor; tunneling between configurations ignored  
  > "In this study, the two conformations of 2D-DME were considered as two independent asymmetric top molecules each with a single unsubstituted CH$_3$ internal rotor." (Introduction)
   - fitting: Weights equal to the reciprocal of the squared measurement accuracy  
  > "In the weighted least-squares fit implemented in the ERHAM code, the weight of each frequency is calculated as reciprocal of the measurement accuracy squared." (Spectral analysis)
   - validation: Weighted rms deviations close to 1 and absence of extra splittings support the independent treatment  
  > "the weighted rms deviations of the fits close to 1 support our initial strategy to treat the two conformations independently" (Discussion)
3. **Estimate the internal rotation barrier V3**: BARRIER program combining the A-E ground-state splitting with the internal rotation constant F  
  > "we used the program BARRIER which is derived from the program ASTOR described in (cite: groner1986) that determines the potential barrier for a single simple internal rotor from torsional transitions or splittings." (Discussion)
   - software: BARRIER, ERHAM
   - assumption: Relative error of V3 taken equal to the relative errors of the A-E energy difference and of the tunneling coefficient epsilon_10  
  > "The estimated error of the $V_3$ barriers is derived with the assumption that the relative error of $V_3$ is the same as the relative errors of the $\Delta  E(E-A)$ energy difference and the tunneling coefficient $\varepsilon_{10}$." (Discussion)
   - fitting: _not stated_
   - validation: Barrier heights compared with the mono-deuterated and parent dimethyl ether studies  
  > "The determined barrier heights agree well with the results of the study of monodeuterated DME (cite: richard2013)" (Discussion)
4. **Compute line predictions and partition functions**: ERHAM V16g-R3 predictions in JPL catalog format up to 1.5 THz; partition functions at 9 temperatures from ERHAM output, compared with a rigid-rotor approximation  
  > "using the ERHAM software in its “ERHAM V16g-R3” version (downloaded on the PROSPE website (cite: kisiel2001)), we calculated predictions in the JPL catalog format (cite: pickett1991) up to 1.5 THz" (Predictions); "Numerical values of overall partition functions were computed at 9 different temperatures using the ERHAM output" (Predictions)
   - software: ERHAM
   - parameter: Degeneracy factor g_n = 1 for symmetric and 2 for asymmetric conformer in the rigid-rotor approximation  
  > "the degeneracy factor $g_n$ is equal to 1 for the symmetric conformation and 2 for the asymmetric one" (Predictions)
   - fitting: _not stated_
   - validation: Rigid-rotor partition function agrees with the fit-based values to a ratio of 1.002-1.058; only the fit-based values were used for column densities  
  > "However, only the results from the fit, highlighted in bold, were used to derive column densities." (Predictions)
5. **Fit LTE synthetic spectra to the PILS spectrum**: Compare LTE synthetic spectra to the ALMA spectrum toward the offset position and chi-squared fit column densities of each conformer separately using reasonably isolated lines  
  > "We then perform $\chi^2$-fitting to the reasonably isolated lines to constrain the column densities of the symmetic and asymmetric conformers separately." (Astronomical search for CH3OCHD2)
   - parameter: LSR velocity 2.6 km/s, FWHM 1 km/s, source size 0.5 arcsec (Gaussian), kept fixed  
  > "a LSR velocity of 2.6 km s$^{-1}$, a line width (FWHM) of 1 km s$^{-1}$ and source size of 0.5$''$ (assumed as a Gaussian distribution)" (Astronomical search for CH3OCHD2)
   - parameter: Excitation temperature fixed to 125 K  
  > "For the latter we adopt a temperature of 125 K of the non- and singly-deuterated variants of dimethylether" (Astronomical search for CH3OCHD2)
   - assumption: LTE excitation  
  > "At the targeted scales, the densities should be high enough for the excitation of the molecules to occur under Local Thermodynamic Equilibrium (LTE) conditions." (Astronomical search for CH3OCHD2)
   - assumption: Doubly-deuterated variants are present in the same gas as the non- and singly-deuterated variants  
  > "again under the assumption that the doubly-deuterated variants are present in the same gas" (Astronomical search for CH3OCHD2)
   - fitting: Chi-squared fit of column density with all other parameters fixed; priors and uncertainties not stated  
  > "With these choices of fixed parameters what remains to be fitted are the column densities of the species and their excitation temperature." (Astronomical search for CH3OCHD2)
   - validation: Fitted column density ratio of the two conformers (factor 2.3) compared with the expected factor 2  
  > "The factor 2.3 we derive when fitting the two conformers independently is consequently an additional verification of the assignment of the two conformers." (Astronomical search for CH3OCHD2)
6. **Derive doubly-to-mono deuterated ratio and compare D/H**: Ratio of fitted column densities N(CH3OCHD2)/N(CH3OCH2D) compared with D/H from singly-to-non deuterated variants corrected for equivalent hydrogen atoms  
  > "Taken together the derived column densities imply a ratio between the column densities of the doubly-to-mono deuterated forms, $N$(CH$_3$OCHD$_2$)/$N$(CH$_3$OCH$_2$D) of 15–20% for the two conformers." (Astronomical search for CH3OCHD2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ERHAM** ERHAM V16g-R3: Fitting the effective Hamiltonian to laboratory lines and computing predictions and partition functions  
  > "using the ERHAM software in its “ERHAM V16g-R3” version (downloaded on the PROSPE website (cite: kisiel2001))" (Predictions); "New sets of spectroscopic parameters have been determined by a least squares fit with the ERHAM code" (Abstract)
- **BARRIER** : Estimating the potential barrier V3 for internal rotation  
  > "we used the program BARRIER which is derived from the program ASTOR described in (cite: groner1986)" (Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Assigned lines, symmetric conformer / asymmetric conformer | 1451 / 2080 | not stated | lines | 2 | A total of 1451 lines with $J_{max}=71$, $K_{a,max}=27$ and 2080 lines with $J_{max}=72$, $K_{a,max}=25$ were assigned respectively for symmetric and asymmetric conformers. |
| Standard deviation of the fit to laboratory frequencies | better than 80 | not stated | kHz | 2 | allowed us to reproduce measurements with a standard deviation better than 80 kHz |
| Internal rotation constant F, symmetric / asymmetric conformer | 6.223 / 6.338 | not stated | cm^-1 | 3 | The $F$ values determined in this study are 6.223 and $6.338$ cm$^{-1}$, respectively, for symmetric and asymmetric conformers. |
| Uncertainty of V3 barrier, symmetric / asymmetric conformer | 3 / 1.5 | not stated | cm^-1 | 3 | We found respectively an uncertainty of 3 and 1.5 cm$^{-1}$ for the symmetric and asymmetric conformers. |
| Rigid-rotor partition function coefficient, symmetric / asymmetric conformer (multiplying T^3/2) | 27.53433 / 54.48133 | not stated | dimensionless (T in K) | 4 | We thus obtain 27.53433$T^{3/2}$ for the symmetric conformer and 54.48133$T^{3/2}$ for the asymmetric one. |
| Column density of asymmetric CH3OCHD2 | 6.1e15 | not stated | cm^-2 | 5 | The derived column densities are $6.1\times 10^{15}$ cm$^{-2}$ for the asymmetric and $2.7\times 10^{15}$ cm$^{-2}$ for the symmetric conformers. |
| Column density of symmetric CH3OCHD2 | 2.7e15 | not stated | cm^-2 | 5 | The derived column densities are $6.1\times 10^{15}$ cm$^{-2}$ for the asymmetric and $2.7\times 10^{15}$ cm$^{-2}$ for the symmetric conformers. |
| Column density ratio asymmetric/symmetric conformer | 2.3 | not stated | dimensionless | 5 | The factor 2.3 we derive when fitting the two conformers independently |
| N(CH3OCHD2)/N(CH3OCH2D) for the two conformers | 15-20% | not stated | percent | 6 | of 15–20% for the two conformers |
| Doubly-deuterated D/H relative to D/H from singly-to-non deuterated variants | about a factor of 5 higher | not stated | dimensionless | 6 | These imply D/H ratios that are about a factor of 5 higher than those inferred from the singly-to-non deuterated variants |

## Qualitative findings

- Both conformers of CH3OCHD2 are detected near IRAS 16293-2422 B; about 20 transitions per conformer are well fitted  
  > "both conformers have been detected near the “B” component of the protostellar system IRAS 16293-2422" (Conclusion); "For the two species good fits can be seen for about 20 transitions" (Astronomical search for CH3OCHD2)
- No additional tunneling splittings seen in the asymmetric conformer at Doppler-limited resolution  
  > "Under Doppler limited spectral resolution, we didn’t observe any additional splittings in the ground state rotational lines of the asymmetric conformation" (Discussion)

## Claim tuples

- H: The ground-state rotational spectra of both CH3OCHD2 conformers can be fitted with an effective Hamiltonian with one internal rotor each | E: Laboratory spectra 150-1500 GHz fitted with ERHAM for each conformer separately | R: 1451 (symmetric) and 2080 (asymmetric) lines fitted to better than 80 kHz standard deviation | F: An accurate set of spectroscopic parameters and predictions up to 1.5 THz was obtained | **supported**
- H: CH3OCHD2 is present toward IRAS 16293-2422 B and can be identified with the new predictions | E: LTE synthetic spectra compared with the PILS ALMA Band 7 spectrum at an offset position | R: About 20 good fits for each conformer among the 24 strongest predicted lines | F: First detection of both conformers in the ISM | **supported**
- H: The asymmetric/symmetric column density ratio should be about 2 from symmetry | E: Independent chi-squared fits of the two conformers | R: 6.1e15 and 2.7e15 cm^-2, factor 2.3 | F: The ratio is an additional verification of the assignment of the two conformers | **supported**
- H: Doubly-deuterated dimethyl ether is enhanced relative to the D/H inferred from the singly-deuterated species, as for other organics | E: Ratio of fitted N(CH3OCHD2) to N(CH3OCH2D) compared with D/H from singly-to-non deuterated variants | R: Ratio 15-20%, implying D/H about a factor of 5 higher | F: Strong enhancement of multi-deuterated variants also holds for dimethyl ether | **supported**

## Reasoning

- Why this data: IRAS 16293-2422 shows high D/H ratios and narrow lines at the offset position, which eases line assignment  
  > "The advantage of looking for the deuterated species toward IRAS 16293-2422 is that it shows high D/H ratios for many organic molecules" (Astronomical search for CH3OCHD2); "This enables easy assignments of individual transitions without problems with line overlaps and absorption." (Astronomical search for CH3OCHD2)
- Why this method: Synthetic spectra preferred over rotation diagrams because they test matches and non-detections at predicted frequencies  
  > "The synthetic spectrum method is preferred over, e.g., classical rotation diagrams, as it immediately makes it possible both to search for good matches in the data" (Astronomical search for CH3OCHD2)
- Alternative: Classical rotation diagrams not used in favour of synthetic spectra  
  > "The synthetic spectrum method is preferred over, e.g., classical rotation diagrams" (Astronomical search for CH3OCHD2)
- Alternative: Various values of alpha were tried for the asymmetric conformer before fixing it to 0  
  > "after various attempts to set a value to $\alpha$, we have decided to fix the parameter to 0 for the same reasons" (Spectral analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Tunneling between equivalent configurations and between conformers is ignored in the spectroscopic model  
  > "The independence in the treatment of their rotational spectra consisted in ignoring the possible effects of tunneling between two equivalent configurations of the asymmetric conformation or between symmetric and asymmetric conformations." (Introduction)
- Limitation (authors): The assumed source size affects results mainly for optically thick lines  
  > "The assumed source size mainly affects the results when optically thick lines are considered" (Astronomical search for CH3OCHD2)
- Caveat (inferred, ours): No uncertainties are given on the column densities or on the 15-20% ratio
- Caveat (inferred, ours): Excitation temperature, line width, LSR velocity and source size are fixed and untested for this species; only chi-squared on unnamed 'reasonably isolated' lines
- Caveat (inferred, ours): The ALMA analysis is shown only as spectra and two numbers; no residuals, line list or blending assessment in the text
- Caveat (inferred, ours): The mono-deuterated column density behind the ratio is not given here
- Caveat (inferred, ours): A single offset position is used, so spatial dependence is not tested

## Reproducibility

- Data public (paper): Laboratory measurements and predictions are available at the CDS; public status of the ALMA PILS data is not stated  
  > "are available in their entirety in electronic form at the Centre de Données astronomiques de Strasbourg (CDS)" (Discussion); "The complete tables are available through the CDS in the catalog format." (Predictions)
- Products in archive: _not stated_
- Code: ERHAM V16g-R3 downloaded from the PROSPE website; no new code released  
  > "using the ERHAM software in its “ERHAM V16g-R3” version (downloaded on the PROSPE website (cite: kisiel2001))" (Predictions)
- Missing: Calibrated PILS cubes or the imaging recipe (in the PILS survey paper)
- Missing: Spectrum extraction position and aperture
- Missing: List of lines used in the chi-squared fit
- Missing: Fit code, noise model and uncertainties
- Missing: Mono-deuterated dimethyl ether column density for the ratio
- Data volume (inferred): Full PILS Band 7 cubes cover 33.8 GHz at 0.2 km/s, likely hundreds of GB; the lab line list from CDS is small
- Score (inferred): 3/5, The lab fit is reproducible from CDS data and ERHAM with numeric parameters, and the LTE parameters are given, but ALMA processing, extraction position and line selection are not stated and no uncertainties are given.
- Rediscovery candidate: no, Public status of the ALMA data is not stated in the paper and the line selection and extraction recipe are incomplete.

## Links

- Method: (cite: jorgensen16) (PILS survey description: data, calibration and imaging)
- Method: (cite: richard2013) (Mono-deuterated dimethyl ether analysis whose ERHAM treatment is followed)
- Method: (cite: zakharenko2015) (Lille spectrometer)
- Method: (cite: groner1997; groner2012) (ERHAM code)
- Companion: (cite: jorgensen18) (PILS D/H of mono-deuterated dimethyl ether toward IRAS 16293B)
- Companion: (cite: manigand19) (D/H ratios used for comparison; multiply-deuterated species in PILS)
- Related: PILS (Protostellar Interferometric Line Survey), project 2013.1.00278.S

## Checks

```json
{
 "quotes": 80,
 "quotes_ok": 80,
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
  "facts": 89,
  "stated": 49,
  "rate": 0.551
 },
 "evidence_ok": true
}
```
