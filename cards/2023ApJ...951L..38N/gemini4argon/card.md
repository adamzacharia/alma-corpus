# Evidence for Ubiquitous Carbon Grain Destruction in Hot Protostellar Envelopes

`2023ApJ...951L..38N` | The Astrophysical Journal Letters 2023 | first author: Nazari, Pooneh | arXiv: 2306.11778 | DOI: 10.3847/2041-8213/acdde4

Card schema 1.0 | model gemini-4-argon | depth full | type large_program_or_survey

## Science

- Fields: astrochemistry, star_formation
- Question: Search for signatures of carbon grain (refractory organics) destruction in hot protostellar envelopes by comparing hot and warm gas components of oxygen-rich and oxygen-poor organic molecules across 37 high-mass protostars.  
  > "In this work we use one such molecular surveys with the Atacama Large Millimeter/submillimeter Array (ALMA) to search for the signatures of destruction of carbon grains through a two-component temperature fit to oxygen-rich and oxygen-poor organics." (Introduction); "We then compare the ratios of the hot number of molecules to warm number of molecules for species with and without oxygen in a sample of 37 protostellar systems." (Introduction)
- Target **37 high-mass protostars from the ALMAGAL sample**: coordinates _not stated_; z/distance 2-3 kpc  
  > "Using observations of $37$ high-mass protostars with ALMA" (Abstract); "The angular resolution for high-mass sources located at distances of $2-3$ kpc correspond to radii of between ${\sim}500$ au and ${\sim}2500$ au." (Data); distance from _not stated_

## Data provenance

- ALMA projects: 2019.1.00195.L
- bands: _not stated_
- frequencies and spectral setup: 217.00-218.87 GHz and ~219.07-220.95 GHz; spectral resolution ~0.7 km s^-1  
  > "The frequency ranges covered for the selected sample are $217.00-218.87$ GHz and ${\sim}219.07-220.95$ GHz." (Data); "The spectral resolution is around $0.7$ km s$^{-1}$ which results in spectrally resolved molecular lines toward the protostellar systems." (Data)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.5'' to ~1.5''  
  > "All data used here have an angular resolution between ${\sim} 0.5\ensuremath{''}$ and ${\sim} 1.5\ensuremath{''}$." (Data)
- max recoverable scale: _not stated_
- sensitivity: line rms ~0.2 K  
  > "The line rms is ${\sim}0.2$ K for the spectra." (Data)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ALMAGAL large program (PIs: S. Molinari, P. Schilke, C. Battersby, P. Ho), publicly available  
  > "We use data from the large program ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy (ALMAGAL, PIs: S. Molinari, P. Schilke, C. Battersby, P. Ho)" (Introduction); "In this work we use the publicly available ALMA data from the ALMAGAL large program (project ID: 2019.1.00195.L)." (Data)
- Line: CH3CN 12_4-11_4 and lines with E_up = 419 K, 526 K, 782 K, 931 K (not stated)
- Line: CH3OH lines with E_up = 508 K, 746 K, 776 K, 802 K, and 1181 K (220.887 GHz (for ~1200 K line))
- Line: HNCO lines with E_up = 448 K, 750 K, 1050 K, 1450 K (not stated)
- Line: C2H3CN line with E_up ~ 435.0 K (not stated)
- External data: Warm column densities and emitting areas for CH3OH, CH3CN, HNCO, and C2H3CN (measured from 13C or 18O isotopologues)  
  > "We take the warm column densities for the above species from (cite: Nazari2022ALMAGAL), who measure them from the $^{13}$C or $^{18}$O isotopologues of the targeted molecules" (Introduction); "We use the CASSIS spectral analysis tool ((cite: Vastel2015)) to fit the spectra assuming the same emitting area that was used in (cite: Nazari2022ALMAGAL) for the warm component." (Spectral fitting) [from (cite: Nazari2022ALMAGAL)]
- External data: Line lists, frequencies, quantum numbers, E_up, and A_ij of considered lines  
  > "The line lists are taken from the Cologne Database for Molecular Spectroscopy (CDMS; (cite: Muller2001); (cite: Muller2005))." (Spectral fitting); "Frequencies, quantum numbers, $E_{\rm up}$ and $A_{\rm ij}$ of the considered lines are given in Tables B.1 and E.7 of (cite: vanGelder2022) and (cite: Nazari2022ALMAGAL)." (Spectral fitting) [from CDMS ((cite: Muller2001); (cite: Muller2005)), (cite: vanGelder2022), (cite: Nazari2022ALMAGAL)]
- External data: Isotope ratio relations as a function of Galactic center distance  
  > "The isotope ratios in that work were calculated from the relations given in (cite: Wilson1994) and (cite: Milam2005) and the distances of the objects from the Galactic center." (Spectral fitting) [from (cite: Wilson1994), (cite: Milam2005)]

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
- final beam: ~0.5'' to ~1.5''  
  > "All data used here have an angular resolution between ${\sim} 0.5\ensuremath{''}$ and ${\sim} 1.5\ensuremath{''}$." (Data)
- final rms: ~0.2 K  
  > "The line rms is ${\sim}0.2$ K for the spectra." (Data)

### Inherited from earlier work

- Observational data details, extracted peak-pixel spectra from CH3CN 12_4-11_4 moment zero map, warm component column densities, emitting areas, and fit-by-eye spectral fitting method  
  > "The works mentioned above present the full details of the data, here we only give a summary of the observational parameters." (Data); "The spectra are the same as those used in (cite: Nazari2022ALMAGAL) which were extracted from the peak pixel of the CH$_3$CN 12$_4$–11$_4$ moment zero map." (Data); "For all sources the column density of the hot component is found using the same fit-by-eye method used in (cite: Nazari2022ALMAGAL) (also see (cite: Chen2023))." (Spectral fitting) [from (cite: Nazari2022ALMAGAL), (cite: vanGelder2022), (cite: vanGelder2022Deuteration), (cite: Chen2023)]
- Analytical power-law formulation for number of molecules in a spherical envelope  
  > "the number of molecules for species $i$ in the hot (or warm) gas can be written as (see Appendix B of (cite: Nazari2021))" (Envelope-only analytical model) [from (cite: Nazari2021)]

### Not stated but needed to reproduce (our reading)

- Full CASA calibration and imaging parameters (handled in Nazari et al. 2022b / van Gelder et al. 2022a)
- Exact source coordinates, systemic velocities, line widths (FWHM), and assumed emitting areas for each of the 37 protostars
- Exact numerical values of the warm column densities for each of the 37 sources (taken from Nazari et al. 2022b)
- Objective criteria/grid ranges used in the fit-by-eye method in CASSIS to determine best-fit values and uncertainties

## Analysis recipe

1. **Extract single-pixel spectra toward 37 protostars**: Use pre-extracted spectra from the peak pixel of the CH3CN 12_4-11_4 moment zero map as prepared in earlier work.  
  > "The spectra are the same as those used in (cite: Nazari2022ALMAGAL) which were extracted from the peak pixel of the CH$_3$CN 12$_4$–11$_4$ moment zero map." (Data)
   - parameter: CH3CN 12_4-11_4 moment zero peak pixel  
  > "The spectra are the same as those used in (cite: Nazari2022ALMAGAL) which were extracted from the peak pixel of the CH$_3$CN 12$_4$–11$_4$ moment zero map." (Data)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit hot gas column densities and excitation temperatures**: Fit optically thin high-excitation lines (E_up >= 400 K) of main isotopologues of CH3CN, CH3OH, HNCO, and C2H3CN using a fit-by-eye LTE spectral model in CASSIS while ignoring E_up < 400 K lines.  
  > "Here we attempt to find the column densities of the relevant molecules in the hot regions closer to the protostars by only fitting the optically thin lines of the main isotopologues with $E_{\rm up} \gtrsim 400$ K." (Spectral fitting); "We use the CASSIS spectral analysis tool ((cite: Vastel2015)) to fit the spectra assuming the same emitting area that was used in (cite: Nazari2022ALMAGAL) for the warm component." (Spectral fitting); "For all sources the column density of the hot component is found using the same fit-by-eye method used in (cite: Nazari2022ALMAGAL) (also see (cite: Chen2023))." (Spectral fitting)
   - software: CASSIS
   - parameter: E_up > 400 K lines only (CH3CN: 419, 526, 782, 931 K; CH3OH: 746, 776, 802, 1181 K, ignoring 508 K; HNCO: 448, 750, 1050, 1450 K; C2H3CN: ~435.0 K)  
  > "Methyl cyanide (CH$_3$CN) in the chosen sample normally has three unblended detected lines with $E_{\rm up} > 400$ K (419 K, 526 K and 782 K)" (Spectral fitting); "These lines have $E_{\rm up}$ of 508 K, 746 K, 776 K, 802 K, and 1181 K. The line with $E_{\rm up} = 508$ K for the most line-rich sources becomes optically thick. Therefore, we ignore this line for all sources" (Spectral fitting); "Isocyanic acid (HNCO) in the chosen sample normally has two detected lines with $E_{\rm up} > 400$ K, at $E_{\rm up} = 448$ K and $E_{\rm up} = 750$ K." (Spectral fitting)
   - parameter: Fixed T_ex = 300 K when highest-E_up temperature-sensitive lines are not detected (and for all C2H3CN fits); omit hot N if T_ex upper limit <= 200 K  
  > "However, when the 782 K line is not detected the temperature is fixed to 300 K." (Spectral fitting); "Hence, we fix the temperature to 300 K and only fit the line with $E_{\rm up} \sim 435.0$ K to find an approximation for the hot column densities of C$_2$H$_3$CN." (Measurement of hot column densities of C2H3CN); "For all our molecules if the upper limit on the excitation temperature of the hot gas is $\leq 200$ K, the hot column density is not measured to avoid potential contribution from the warm gas in the calculations." (Additional tables and plots)
   - assumption: Thermal excitation conditions (LTE) and optically thin emission for E_up > 400 K lines  
  > "Assuming only thermal excitation conditions, we interpret these results as a signature of destruction of refractory organics, consistent with the cometary composition." (Abstract); "Here we attempt to find the column densities of the relevant molecules in the hot regions closer to the protostars by only fitting the optically thin lines of the main isotopologues with $E_{\rm up} \gtrsim 400$ K." (Spectral fitting)
   - assumption: Same emitting area as the warm component in Nazari et al. (2022b)  
  > "We use the CASSIS spectral analysis tool ((cite: Vastel2015)) to fit the spectra assuming the same emitting area that was used in (cite: Nazari2022ALMAGAL) for the warm component." (Spectral fitting)
   - fitting: Fit-by-eye method in CASSIS  
  > "For all sources the column density of the hot component is found using the same fit-by-eye method used in (cite: Nazari2022ALMAGAL) (also see (cite: Chen2023))." (Spectral fitting)
   - validation: Varied T_ex from 200 K to 500 K for a few sources and confirmed column densities change by a factor of <= 2.  
  > "To test whether this assumption is valid, we varied the excitation temperature from 200 K to as high as 500 K for a few sources and found that the column densities could only change by a factor of $\lesssim2$." (Spectral fitting)
3. **Compute and compare hot-to-warm total molecule number ratios**: Calculate total number of molecules (N_tot = A * N) in the hot and warm components for CH3OH, HNCO, CH3CN, and C2H3CN, and compute the weighted mean and scatter of N_hot / N_warm across the sample.  
  > "However, we stress that the relevant quantity for our study is the total number of molecules ($\mathcal{N} = A N$, where $A$ and $N$ are the emitting area and column density)" (Spectral fitting); "Therefore, after the derivation of column densities we compare the total numbers of hot and warm molecules with each other (see Section 3)." (Spectral fitting)
   - assumption: Lines are optically thin so N_tot = A * N is independent of the assumed emitting area.  
  > "the total number of molecules ($\mathcal{N} = A N$, where $A$ and $N$ are the emitting area and column density) which does not change if a different emitting area is used as long as the lines are optically thin." (Spectral fitting)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare observed ratios with an analytical spherical envelope model**: Derive analytical expectation for N_hot / N_warm in a power-law spherical protostellar envelope assuming pure ice sublimation at T_sub without additional hot gas-phase chemistry, and compare with observed ratios.  
  > "Here we explain what is expected for the hot and warm number of molecules from a simple analytical model." (Envelope-only analytical model); "The total number of molecules of species $i$ in the hot gas and in the warm gas can then be compared as $$\begin{equation} \frac{\mathcal{N}_{i, \rm hot}}{\mathcal{N}_{i, \rm warm}} = \frac{X_{i,\rm hot}}{X_{i,\rm warm}} \left(\frac{T_{i,\rm{hot}}}{T_{i,\rm{warm}}}\right)^{-3.75}. \label{eq:ratio} \end{equation}$$" (Envelope-only analytical model)
   - parameter: Density power-law index p = -1.5, temperature power-law index q = -0.4, T_hot = 300 K, T_warm = 150 K  
  > "Assuming a spherical model with a power-law density and temperature as a function of radius with powers $p=-1.5$ and $q=-0.4$ based on observations and radiative transfer models" (Envelope-only analytical model); "Assuming $T_{\rm hot} = 300$ K and $T_{\rm warm} = 150$ K consistent with the average excitation temperatures of the hot and warm gas for the studied molecules (see Appendix 9), $(T_{i,\rm{hot}}/T_{i,\rm{warm}})^{-3.75} =0.07$." (Envelope-only analytical model)
   - assumption: Spherical envelope with power-law density and temperature profiles, sublimation temperatures <= 100-150 K, and constant abundance X_hot / X_warm = 1 if no hot gas chemistry occurs.  
  > "Therefore, if there is no additional gas phase chemistry in the hot gas (i.e., $X_{i,\rm hot}/X_{i,\rm warm} = 1$), $$\begin{equation} \frac{\mathcal{N}_{i, \rm hot}}{\mathcal{N}_{i, \rm warm}} \sim 0.1. \end{equation}$$" (Envelope-only analytical model); "It is worth noting that this result is valid for molecules with sublimation temperatures of $\lesssim 100-150$ K so that there exists a warm component in the gas." (Envelope-only analytical model)
   - fitting: _not stated_
   - validation: Checked sensitivity to optically thick steeper temperature profile (q = -0.5), which changes the power from -3.75 to -3.0 and N_hot / N_warm from 0.07 to 0.13.  
  > "To check how this assumption changes the calculations we take a steeper temperature profile with $q=-0.5$ for the optically thick regime (see (cite: Adams1985) for low-mass and (cite: Nazari2023Highmass) for high-mass sources). This will change the power of -3.75 to -3.0 and the value of $\mathcal{N}_{i, \rm hot}/\mathcal{N}_{i, \rm warm}$ from 0.07 to 0.13." (Envelope-only analytical model)

## Software

- **CASSIS** : Spectral analysis and LTE fitting of hot gas molecular column densities and excitation temperatures  
  > "We use the CASSIS spectral analysis tool ((cite: Vastel2015)) to fit the spectra assuming the same emitting area that was used in (cite: Nazari2022ALMAGAL) for the warm component." (Spectral fitting)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Weighted mean hot-to-warm molecule number ratio for CH3OH | 0.12 | factor 1.78 spread around the mean | dimensionless | 3 | The hot to warm ratios of methanol have a weighted mean of 0.12 while that for methyl cyanide is 0.48.; The spread around the mean is tight for the two molecules with only a spread of a factor 1.78 and 1.33 around the mean for methanol and methyl cyanide, respectively. |
| Weighted mean hot-to-warm molecule number ratio for CH3CN | 0.48 | factor 1.33 spread around the mean | dimensionless | 3 | The hot to warm ratios of methanol have a weighted mean of 0.12 while that for methyl cyanide is 0.48.; The spread around the mean is tight for the two molecules with only a spread of a factor 1.78 and 1.33 around the mean for methanol and methyl cyanide, respectively. |
| Spread around the mean hot-to-warm ratio for HNCO | 1.77 | not stated | dimensionless | 3 | Figure 3 shows that HNCO has a similar mean and a similar standard deviation to methanol (factor of 1.77 around the mean). |
| Mean hot-to-warm molecule number ratio for C2H3CN | 1.47 | factor of 1.44 scatter around the mean | dimensionless | 3 | Moreover, the number of hot to the number of warm vinyl cyanide molecules are more similar to those of methyl cyanide with a mean of 1.47 and a factor of 1.44 scatter around the mean. |
| Enhancement factor of hot-to-warm ratio for oxygen-poor vs oxygen-rich molecules | ~5 (~0.7 dex) | not stated | dimensionless | 3 | In contrast, nitrogen-containing, oxygen-poor molecules (CH$_3$CN and C$_2$H$_3$CN) systematically show an enhancement of a factor ${\sim} 5$ in their hot component; This results in two distinct population of molecules, with at least a ${\sim}0.7$ dex (factor of ${\sim}$5) difference between the mean of the ratios. |
| Analytical model expectation for N_hot / N_warm without hot gas chemistry (q = -0.4) | 0.07 (~0.1) | 0.07 to 0.13 for q = -0.4 to -0.5 | dimensionless | 4 | Assuming $T_{\rm hot} = 300$ K and $T_{\rm warm} = 150$ K consistent with the average excitation temperatures of the hot and warm gas for the studied molecules (see Appendix 9), $(T_{i,\rm{hot}}/T_{i,\rm{warm}})^{-3.75} =0.07$.; Therefore, if there is no additional gas phase chemistry in the hot gas (i.e., $X_{i,\rm hot}/X_{i,\rm warm} = 1$), $$\begin{equation} \frac{\mathcal{N}_{i, \rm hot}}{\mathcal{N}_{i, \rm warm}} \sim 0.1. \end{equation}$$; This will change the power of -3.75 to -3.0 and the value of $\mathcal{N}_{i, \rm hot}/\mathcal{N}_{i, \rm warm}$ from 0.07 to 0.13. |
| Hot-to-warm abundance enhancement (X_hot / X_warm) for oxygen-poor molecules | >=5 | not stated | dimensionless | 4 | This means an enhancement of oxygen-poor species in the hot gas and $X_{i,\rm hot}/X_{i,\rm warm}$ of ${\gtrsim}5$ for these molecules |

## Qualitative findings

- Oxygen-rich molecules (CH3OH and HNCO) systematically show no enhancement in their hot component relative to analytical expectations of simple ice sublimation.  
  > "Using observations of $37$ high-mass protostars with ALMA, we find that oxygen-containing molecules (CH$_3$OH and HNCO) systematically show no enhancement in their hot component." (Abstract); "Our findings in Section 3 show that the mean of hot number of molecules to warm number of molecules for oxygen-rich species agrees well with the expected ratio of ${\sim} 0.1$ from the simple analytical model in Section 4." (Discussion and conclusions)
- Nitrogen-containing oxygen-poor molecules (CH3CN and C2H3CN) show a systematic enhancement of a factor of ~5 in their hot component, indicating additional gas-phase formation in the hot gas triggered by destruction of refractory organics.  
  > "In contrast, nitrogen-containing, oxygen-poor molecules (CH$_3$CN and C$_2$H$_3$CN) systematically show an enhancement of a factor ${\sim} 5$ in their hot component, pointing to additional production of these molecules in the hot gas." (Abstract); "We attribute the enhancement of oxygen-poor molecules, CH$_3$CN and C$_2$H$_3$CN, in the hot gas to destruction of refractory organics and find it to be common in high-mass protostellar systems." (Discussion and conclusions)
- Destruction of refractory organics implies higher C/O and N/O elemental ratios in the hot gas than in the warm gas.  
  > "This destruction implies a higher C/O and N/O in the hot gas than the warm gas, while, the exact values of these ratios depend on the fraction of grains that are effectively destroyed." (Abstract)

## Claim tuples

- H: Destruction of carbon- and nitrogen-rich refractory organic grains in hot protostellar gas (>=300 K) leads to top-down gas-phase production and enhancement of nitrogen-bearing, oxygen-poor organic molecules relative to oxygen-rich molecules. | E: Fit high-upper-energy (E_up > 400 K) optically thin lines in ALMAGAL spectra of 37 high-mass protostars using CASSIS to measure hot gas molecule numbers of CH3OH, HNCO, CH3CN, and C2H3CN, and compare hot-to-warm molecule ratios against a spherical power-law envelope analytical model. | R: Oxygen-rich species (CH3OH, HNCO) have mean hot-to-warm ratios of ~0.12 matching the no-chemistry analytical prediction (~0.1), whereas oxygen-poor species (CH3CN, C2H3CN) have mean ratios of 0.48 and 1.47, showing a systematic ~0.7 dex (factor of ~5) enhancement. | F: Ubiquitous destruction of refractory organics occurs in hot protostellar envelopes, enhancing oxygen-poor nitrogen-bearing molecules and raising the C/O and N/O ratios in the hot gas. | **supported**

## Reasoning

- Why this data: The ALMAGAL survey provides high sensitivity across a large sample of 37 sources to detect both optically thin minor isotopologues (probing warm gas) and weak high-E_up (>400-500 K) lines of main isotopologues (probing hot gas).  
  > "We use data from the large program ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy (ALMAGAL, PIs: S. Molinari, P. Schilke, C. Battersby, P. Ho) because of its high sensitivity to detect both optically thin minor isotopologues of the most abundant molecules such as methanol to probe the warm gas and the optically thin weak lines of the major isotopologues with $E_{\rm up} > 400-500$ K to probe the hot gas." (Introduction)
- Why this method: Fitting only E_up > 400 K lines of main isotopologues avoids optically thick low-E_up lines and isolates the hot gas component, while comparing total numbers of molecules (N_tot = A * N) eliminates dependence on the assumed emitting area.  
  > "When fitting these high-$E_{\rm up}$ lines, the lines with $E_{\rm up} < 400$ K are ignored as they are usually (marginally) optically thick and even if they were not optically thick, their emission would be dominated by the warm component." (Spectral fitting); "However, we stress that the relevant quantity for our study is the total number of molecules ($\mathcal{N} = A N$, where $A$ and $N$ are the emitting area and column density) which does not change if a different emitting area is used as long as the lines are optically thin." (Spectral fitting)
- Alternative: Variations in envelope temperature power-law index (q = -0.5 instead of -0.4) or assumed fixed excitation temperature (200-500 K) were tested and rejected as explanations for the factor of ~5 difference because they alter ratios by less than a factor of 2.  
  > "To test whether this assumption is valid, we varied the excitation temperature from 200 K to as high as 500 K for a few sources and found that the column densities could only change by a factor of $\lesssim2$." (Spectral fitting); "This will change the power of -3.75 to -3.0 and the value of $\mathcal{N}_{i, \rm hot}/\mathcal{N}_{i, \rm warm}$ from 0.07 to 0.13." (Envelope-only analytical model)
- How they decided it was enough: _not stated_
- Limitation (authors): Isotope ratios derived from Galactic center distance relations could introduce uncertainty if an object is an outlier.  
  > "If an object is an outlier with respect to those relations, the calculated column densities from isotope ratios could have an additional uncertainty." (Spectral fitting)
- Limitation (authors): HNCO excitation temperatures are uncertain due to the lack of detected lines spanning a wide range of E_up.  
  > "However, we note that these excitation temperatures are uncertain given the lack of detected lines with a large range of $E_{\rm up}$, while column densities can be measured accurately." (Spectral fitting)
- Limitation (authors): C2H3CN hot column densities are approximate and lack error bars because only one unblended line with E_up ~ 435.0 K is available and T_ex is fixed to 300 K.  
  > "Hence, we fix the temperature to 300 K and only fit the line with $E_{\rm up} \sim 435.0$ K to find an approximation for the hot column densities of C$_2$H$_3$CN. We do not measure the error bars as it is not possible to firmly measure them." (Measurement of hot column densities of C2H3CN)
- Limitation (authors): Higher vibrational states in the CDMS partition function for CH3CN above 300 K and CH3OH above 300 K are not included.  
  > "The higher vibrational states each contribute to less than 1% at 300 K and hence are ignored here." (Spectroscopic information); "The vibrational levels included in the partition function are sufficient for temperatures up to 300 K." (Spectroscopic information)
- Limitation (authors): The exact fraction of refractory organics destroyed and whether the trend extends to other COMs or low-mass protostars remain unknown.  
  > "It is yet to be confirmed whether the trend seen in Fig. 3 holds for other oxygen-poor (e.g., C$_2$H$_5$CN) and oxygen-rich species (e.g., CH$_3$OCH$_3$)." (Discussion and conclusions); "However, the exact values of these ratios depend on the fraction of refractory organics that are destroyed in these high-temperature regions which is not known." (Discussion and conclusions)
- Caveat (inferred, ours): Spectral fitting is performed using a subjective 'fit-by-eye' method rather than an automated statistical sampler (e.g., MCMC).
- Caveat (inferred, ours): Spatially unresolved hot core observations blend disk and envelope components together.
- Caveat (inferred, ours): Non-LTE or radiative pumping (infrared pumping of vibrational states at high temperatures) is not modeled; purely thermal excitation is assumed.
- Caveat (inferred, ours): Warm C2H3CN column densities in the companion paper were derived from the main isotopologue rather than 13C isotopologues, risking optical depth effects in the warm component.

## Reproducibility

- Data public (paper): Publicly available ALMA data from the ALMAGAL large program (2019.1.00195.L)  
  > "In this work we use the publicly available ALMA data from the ALMAGAL large program (project ID: 2019.1.00195.L)." (Data)
- Products in archive: _not stated_
- Missing: Extracted peak-pixel spectral files for the 37 sources
- Missing: Table of warm column densities and emitting areas from Nazari et al. (2022b)
- Missing: Exact line widths, systemic velocities, and continuum subtraction details used in CASSIS fits
- Missing: Quantitative fitting criteria for the fit-by-eye procedure
- Data volume (inferred): Tens of MB for the 37 extracted 1D spectra; several TB if re-imaging the raw ALMAGAL visibility data for 37 fields
- Score (inferred): 65/5, ALMA project code is public, spectral fitting software (CASSIS) and molecular line databases (CDMS) are public, and full per-source hot column densities and temperatures are tabulated. However, data reduction, spectra extraction, warm column densities, and exact line lists are inherited from companion papers, and the fitting relies on a subjective fit-by-eye method.
- Rediscovery candidate: yes, The ALMAGAL data are public, the 37 targets and targeted molecular transitions are well-defined (with full details in Nazari et al. 2022b), and the main results are concrete numeric column densities, excitation temperatures, and hot-to-warm ratios.

## Links

- Method: (cite: Vastel2015) (CASSIS spectral analysis tool used for LTE line fitting)
- Method: (cite: Muller2001); (cite: Muller2005) (CDMS database for molecular spectroscopy line lists and partition functions)
- Method: (cite: Nazari2021) (Derivation of the analytical power-law envelope model for molecule numbers)
- Companion: (cite: Nazari2022ALMAGAL) (Provides the extracted ALMAGAL spectra, line lists, emitting areas, fit-by-eye methodology, and warm gas column densities for the 37 sources)
- Companion: (cite: vanGelder2022) (Provides ALMAGAL data details, methanol analysis, and spectroscopic line tables)
- Companion: (cite: vanGelder2022Deuteration) (Companion ALMAGAL study on methanol deuteration in the same sample)
- Companion: (cite: Nazari2023) (Companion radiative transfer modeling paper on temperature structure effects on number of molecules)
- Related: ALMAGAL (ALMA Evolutionary study of High Mass Protocluster Formation in the Galaxy)

## Checks

```json
{
 "quotes": 93,
 "quotes_ok": 93,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 5,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 41,
  "rate": 0.526
 },
 "evidence_ok": true
}
```
