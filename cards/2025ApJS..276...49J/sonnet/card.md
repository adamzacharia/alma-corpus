# ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). II. Freshly Sublimated Complex Organic Molecules in the Keplerian Disk

`2025ApJS..276...49J` | The Astrophysical Journal Supplement Series 2025 | first author: Jeong, Jae-Hong | arXiv: 2411.03826 | DOI: 10.3847/1538-4365/ad9450

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry, star_formation
- Question: What is the COM inventory and composition of the freshly sublimated ices in the Keplerian disk of the eruptive star V883 Ori, and how does it compare with hot corinos, hot cores and comet 67P?  
  > "In this paper, we report the results of our COMs analyses with the V883 Ori spectral survey data, focusing on oxygen- and nitrogen-bearing species." (Introduction)
- Target **V883 Ori**: coordinates _not stated_; z/distance 388 pc  
  > "V883 Ori is an eruptive young stellar object in transition between Class I and Class II, located within the Orion Molecular Cloud at a distance of 388 pc (cite: jelee19)." (Introduction); "Its disk inclination is 38.3$^{\circ}$, and the mass of the protostar is 1.2 M$_{\odot}$ (cite: cieza_2016; jelee19)." (Introduction); distance from Lee et al. 2019 (jelee19)  
  > "V883 Ori is an eruptive young stellar object in transition between Class I and Class II, located within the Orion Molecular Cloud at a distance of 388 pc (cite: jelee19)." (Introduction); "Its disk inclination is 38.3$^{\circ}$, and the mass of the protostar is 1.2 M$_{\odot}$ (cite: cieza_2016; jelee19)." (Introduction)

## Data provenance

- ALMA projects: 2019.1.00377.S
- bands: Band 6 (220.703-274.861 GHz)  
  > "The frequency range covered by the spectral survey is 220.703 GHz to 274.861 GHz with a spectral resolution of 488.281 kHz (0.66$-$0.53 km s$^{-1}$)." (2 Observation and Spectral Extraction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.15''-0.2'' (~60-80 au)  
  > "with an angular resolution of 0.15$\ensuremath{''}$$-$0.2$\ensuremath{''}$, corresponding to $\sim$60 to 80 au at a distance of 388 pc" (2 Observation and Spectral Extraction)
- max recoverable scale: _not stated_
- sensitivity: continuum 0.01 mJy/beam; line 0.4-0.6 mJy/beam  
  > "The continuum sensitivity is 0.01 mJy beam$^{-1}$, and the line sensitivity is 0.4$-$0.6 mJy beam$^{-1}$." (2 Observation and Spectral Extraction)
- time on source: 194.5 minutes  
  > "The on-source integration time is 194.5 minutes." (2 Observation and Spectral Extraction)
- observing dates: May 2021 - November 2021  
  > "The observations were conducted between May 2021 and November 2021." (2 Observation and Spectral Extraction)
- pi or archival as stated: Cycle 7 program, PI Jeong-Eun Lee  
  > "In the ALMA Cycle 7 program 2019.1.00377.S (PI: Jeong-Eun Lee)" (2 Observation and Spectral Extraction)
- External data: Dust mass opacity kappa=2.2 cm2/g at 230 GHz and beta=1  
  > "We adopt $\kappa_{\rm ref}= 2.2$ cm$^{2}$ g$^{-1}$ (at $\nu_{\rm ref}$= 230 GHz) and $\beta$=1 from (cite: Cieza2018)." (3.1 Dust attenuation of line intensities) [from (cite: Cieza2018)]
- External data: Disk model average temperature 120 K within 0.3'' used as T_rot  
  > "$T_{\rm rot}$ was set to 120 K, which is the average temperature within 0.3$\ensuremath{''}$ radius of the disk model of V883 Ori (cite: jelee19)." (3.2 Molecular line identification) [from (cite: jelee19)]
- External data: HDO:H2O ratio 2.26e-3 used to derive water column  
  > "The water column density was calculated from our estimated HDO column density (6.68$\times$10$^{16}$ cm$^{-2}$) and the disk-averaged HDO:H$_{2}$O ratio (2.26$\times$10$^{-3}$) reported by (cite: Tobin2023)." (6.2.1) [from (cite: Tobin2023)]
- External data: IRAS 16293-2422B (PILS) column densities for comparison  
  > "For this comparison, we used the results of IRAS 16293-2422B in the IRAS 16293-2422 binary system." (6.1.1) [from (cite: PILS2) and PILS papers]
- External data: Comet 67P/C-G abundances  
  > "Through the mission, various organic compounds were discovered, and their abundances were determined (cite: Schuhmann2019; Rubin2019)." (6.1.1) [from (cite: Schuhmann2019; Rubin2019; PILS19)]

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
- continuum subtraction: image-space subtraction, continuum level measured with STATCONT  
  > "The continuum emission was subtracted in the image space, and the continuum level is automatically measured using `STATCONT` (cite: Sanchez-Monge2018)." (2 Observation and Spectral Extraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation and data reduction details  
  > "The details of observation and data reduction can be found in (cite: jelee2024)." (2 Observation and Spectral Extraction) [from (cite: jelee2024) Paper I]
- PC1 filtering for spectral extraction  
  > "For more information, please refer to (cite: yun2023pca)." (2 Observation and Spectral Extraction) [from (cite: yun2023pca)]

### Not stated but needed to reproduce (our reading)

- Imaging parameters (robust, cell, tclean settings, beam of final cubes) are deferred to Paper I
- CASA/pipeline version and calibrators not stated
- Which strong isolated lines were used to build the PC1
- XCLASS version and MAGIX genetic algorithm/MCMC settings
- Exact criteria for isolated lines and line-matching tolerance in f_N,X
- Spectral extraction aperture details beyond ~0.3''

## Analysis recipe

1. **Extract disk-averaged spectra**: PC1 filtering of the data cube over the COM emission region  
  > "We extracted averaged spectra over the entire COMs emission region in the disk ($\sim$0.3$''$) using a newly-developed filtering technique: first principal component (PC1) filtering method" (2 Observation and Spectral Extraction)
   - software: STATCONT
   - fitting: _not stated_
   - validation: _not stated_
2. **Correct dust attenuation**: Fit continuum vs spectral window weighted by PC1 moment 0 to get N_H2 and eta; divide line intensity by exp(-tau_dust)  
  > "To get $N_{\rm H_{2}}$ and $\eta$, we fitted the continuum intensities as a function of spectral windows, weighted by the moment 0 map of the PC1" (3.1 Dust attenuation of line intensities)
   - parameter: SG2 and SG3 spectra scaled up by 5% and 2%  
  > "we scaled up the SG2 and SG3 spectra by 5% and 2%, respectively." (3.1 Dust attenuation of line intensities)
   - assumption: Dust and gas coupled, gas in LTE; kappa=2.2 cm2/g at 230 GHz, beta=1  
  > "We assume that dust and gas are well coupled and that the gas is in LTE." (3.1 Dust attenuation of line intensities)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify molecular lines**: XCLASS model spectra for ~1500 species at 35 column density steps; f_N,X = matched/modeled lines; keep species reaching 100%, then visual inspection  
  > "for every possible species (about 1,500), we constructed model spectra with 35 column density steps (from 5$\times$10$^{12}$ cm$^{-2}$ to 5$\times$10$^{18}$ cm$^{-2}$)." (3.2 Molecular line identification)
   - software: XCLASS, CDMS, JPL
   - parameter: v_width = 3 km/s, T_rot = 120 K, eta = 0.384, N free  
  > "We fixed $v_{\rm width}$ at 3 km s$^{-1}$, which is obtained from the PC1-filtered spectrum." (3.2 Molecular line identification)
   - assumption: LTE  
  > "Assuming local thermodynamic equilibrium (LTE), `XCLASS` can model the spectra of each molecular species" (3.2 Molecular line identification)
   - fitting: _not stated_
   - validation: Visual inspection of selected species  
  > "Finally, we performed a visual inspection to confirm the detection of those molecules selected by this procedure." (3.2 Molecular line identification)
4. **Derive column densities by iterative LTE fitting**: Fit N only with MAGIX, iteratively keeping isolated lines with tau<0.7 and width<4 km/s until convergence  
  > "The optical depth criterion is set to $\tau_{\rm \nu,line}=0.7$, meaning that only lines with their modeled $\tau_{\rm \nu,line}$ lower than 0.7 are considered in the fitting process." (4.1)
   - software: XCLASS, MAGIX
   - parameter: tau criterion 0.7; exclude line width >4 km/s  
  > "we removed observed lines with large line width ($>$ 4 km s$^{-1}$), which may be due to blending with unidentified lines." (4.1)
   - assumption: T_rot fixed 120 K, eta fixed 0.384  
  > "the column density ($N$) was the only free parameter in the analysis, while the other parameters were fixed to the aforementioned values." (4.1)
   - fitting: Genetic algorithm for best fit; MCMC for uncertainties  
  > "The genetic algorithm was used to derive the best-fit values of the parameters, and the Markov chain Monte Carlo (MCMC) method was used to calculate the uncertainties." (4.1)
   - validation: Rotation diagram comparison: scatter 0.28 dex, offset 0.03 dex  
  > "the difference in column densities obtained from the two methods has a scatter of 0.28 dex with only a slight offset of 0.03 dex." (4.1)
5. **Upper limits and comparison with other sources**: 3 sigma upper limits for nondetections; abundances relative to CH3OH compared with IRAS 16293B, comet 67P and other sources; 12C/13C ratios  
  > "The column density producing the strongest line corresponding to the 3$\sigma$ level of the observation is considered the upper limit." (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **XCLASS** : Line identification and LTE modeling  
  > "We used the eXtended CASA Line Analysis Software Suite (cite: Moller17) for the line identification." (3.2 Molecular line identification)
- **MAGIX** : Column density fitting (genetic algorithm, MCMC)  
  > "We operated a fitting tool of `XCLASS`: the Modeling and Analysis Generic Interface for eXternal numerical codes (`MAGIX`) (cite: Moller13)." (4.1)
- **STATCONT** : Continuum level measurement  
  > "the continuum level is automatically measured using `STATCONT` (cite: Sanchez-Monge2018)" (2 Observation and Spectral Extraction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of COM species detected | 23 | not stated | species | 3 | a total of 23 complex organic molecular species have been found in V883 Ori, based on about 3,700 lines above 3$\sigma$. |
| Beam-filling factor eta | 0.384 | not stated | dimensionless | 2 | Finally, the fitted $\eta$ is 0.384, and the fitted $N_{\rm H_{2}}$ is $1.24\times10^{25}$ cm$^{-2}$ with uncertainty of 2$\%$. |
| N_H2 | 1.24e25 | 2% | cm^-2 | 2 | Finally, the fitted $\eta$ is 0.384, and the fitted $N_{\rm H_{2}}$ is $1.24\times10^{25}$ cm$^{-2}$ with uncertainty of 2$\%$. |
| CH3OH column density | 2.35e18 | +0.65/-0.14 e18 | cm^-2 | 4 | $2.35_{-0.14}^{+0.65}\times10^{18}$ |
| CH3OCHO column density | 1.05e18 | +0.04/-0.17 e18 | cm^-2 | 4 | $1.05_{-0.17}^{+0.04}\times10^{18}$ |
| Lower limit CH3OCHO/CH2OHCHO | >647 | not stated | dimensionless | 5 | a lower limit of the ratio between two isomers of C$_{2}$H$_{4}$O$_{2}$, CH$_{3}$OCHO/CH$_{2}$OHCHO is 647 for V883 Ori, while the average ratio of the other sources in Figure [10](#fig:abund_comp) is 15.9. |
| Average 12C/13C of COMs | 24.4 (range 9.6-38.5) | not stated | dimensionless | 5 | the COMs have the $^{12}$C/$^{13}$C ratio of 24.4 on average (from minimum 9.6 to maximum 38.5) |
| H2O/CH3OH ratio | ~13 | not stated | dimensionless | 5 | the H$_{2}$O/CH$_{3}$OH ratio ($\sim$13) is about an order of magnitude lower compared to IRAS 16293-2422 (330) and Comet 67P (476) |

## Qualitative findings

- Only CH3CN among nitrogen-bearing COMs is detected; CH2OH-bearing COMs are missing while O-bearing COMs are abundant  
  > "nitrogen-bearing COMs other than CH$_{3}$CN are missing, whereas various oxygen-bearing COMs, except for the CH$_2$OH-bearing molecules, are detected." (abstract)

## Claim tuples

- H: Does including optically thick lines bias COM column densities? | E: Iterative LTE fitting with tau<0.7 versus fitting all lines | R: All-line fits underestimate N for CH3OH, CH3OCHO, CH3CHO by up to nearly an order of magnitude | F: Using only optically thin lines over a wide frequency range is critical | **supported**
- H: Is the V883 Ori COM inventory like hot corinos? | E: Compare abundances relative to CH3OH with IRAS 16293B and 67P | R: Abundances higher than hot corino, comparable to comet; CH2OH- and N-bearing COMs missing | F: Possible in-disk chemical evolution and water-rich ice formation | **partially**
- H: Do COMs show carbon isotope fractionation? | E: 12C/13C from detected isotopologues | R: Average 24.4 | F: Lower than local ISM and comet 67P | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Wide unbiased coverage allows selecting isolated optically thin lines  
  > "This approach using only optically thin, isolated lines is possible because we identified as many molecular lines as possible during the line identification process" (4.1)
- Alternative: T_rot of 200 K and 300 K rejected; 120 K fits most species best  
  > "Above all, the spectra of most species are best fitted by 120 K." (9.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Fixed beam-filling factor makes column densities likely lower limits (factor ~2-3)  
  > "the accurate beam-filling factors of less abundant molecules can increase the column densities by a factor of $\sim2-3$, so the current values can be considered lower limits." (11)
- Limitation (authors): ~20% of lines unidentified  
  > "Most observed lines have been identified, but $\sim$20$\%$ of the lines remain unidentified." (5.1)
- Caveat (inferred, ours): Single T_rot and eta for all species despite different emitting regions
- Caveat (inferred, ours): Disk-averaged spectra ignore radial temperature structure
- Caveat (inferred, ours): Dust correction assumes a single averaged tau
- Caveat (inferred, ours): Nitrogen interpretation of ammonium salts is speculative

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00377.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibrated and imaged cubes (Paper I) details
- Missing: PC1 filtering implementation parameters
- Missing: XCLASS/MAGIX configuration
- Data volume (inferred): Large: ~55 GHz Band 6 spectral survey, hundreds of GB raw
- Score (inferred): 3/5, Public data and clear algorithm, but imaging and PC1 details are deferred to other papers.
- Rediscovery candidate: no, Reduction and PC1 filtering are inherited from other papers, so the recipe is incomplete.

## Links

- Method: (cite: yun2023pca) (PC1 filtering method)
- Method: (cite: Moller17) (XCLASS)
- Method: (cite: Sanchez-Monge2018) (STATCONT)
- Companion: (cite: jelee2024) (Paper I: observations and data reduction)
- Companion: (cite: jelee19) (Earlier Band 7 V883 Ori COM study)
- Related: PILS
- Related: EMoCA
- Related: CALYPSO
- Related: ALMASOP
- Related: PEACHES
- Related: CoCCoA

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 40,
  "rate": 0.513
 },
 "evidence_ok": true
}
```
