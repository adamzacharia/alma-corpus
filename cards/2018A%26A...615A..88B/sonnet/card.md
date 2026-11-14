# Low levels of methanol deuteration in the high-mass star-forming region NGC 6334I

`2018A&A...615A..88B` | Astronomy and Astrophysics 2018 | first author: Bøgelund, Eva G. | arXiv: 1804.01090 | DOI: 10.1051/0004-6361/201832757

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the methanol deuteration fractions (CH2DOH/CH3OH, CH3OD/CH3OH) at several locations in NGC 6334I, and what do they say about formation conditions and the cause of low deuteration in the Galactic Centre?  
  > "We derive methanol deuteration fractions at a number of locations towards the high-mass star-forming region NGC 6334, located at a mean distance of 1.3 kpc, and discuss how these can shed light on the conditions prevailing during its formation." (abstract)
- Target **NGC 6334I (MM1, MM2, MM3)**: coordinates MM1 region at 17:20:53.437 -35:46:57.902 (J2000); nine extraction positions across MM1, MM2, MM3  
  > "Here we will assume a mean distance of 1.3 kpc, corresponding to a galactocentric distance, D$_{\textrm{GC}}$, of $\sim$7.02 kpc." (1 Introduction); "MM1 | 17:20:53.437 | -35:46:57.902" (Table 1); z/distance 1.3 kpc (mean)  
  > "Here we will assume a mean distance of 1.3 kpc, corresponding to a galactocentric distance, D$_{\textrm{GC}}$, of $\sim$7.02 kpc." (1 Introduction); "MM1 | 17:20:53.437 | -35:46:57.902" (Table 1); distance from mean of maser parallax distances of Reid2014 (1.34 kpc) and Chibueze2014 (1.26 kpc)  
  > "Here we will assume a mean distance of 1.3 kpc, corresponding to a galactocentric distance, D$_{\textrm{GC}}$, of $\sim$7.02 kpc." (1 Introduction); "MM1 | 17:20:53.437 | -35:46:57.902" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00150.S, 2015.A.00022.T
- bands: _not stated_
- frequencies and spectral setup: Primary: centred 302 GHz, ~3 GHz bandwidth (301.180–304.165 GHz); secondary: windows near 281, 293, 338, 350 GHz, each ~3.75 GHz wide  
  > "centered on 302 GHz, and covering $\sim$3 GHz of total bandwidth with an rms noise of $\sim$500 mK." (2.1 Observations); "centered around four frequency windows at approximately 281, 293, 338, and 350 GHz each $\sim$3.75 GHz wide" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Primary ~1" (1.00"x0.74" beam, ~1300 AU); secondary ~0.2" (260 AU)  
  > "With a synthesised beam of the observations of 1$\overset{\second}{.}$00$\times$0$\overset{\second}{.}$74, this allows us to probe NGC 6334 at scales of $\sim$1300 AU." (1 Introduction)
- max recoverable scale: _not stated_
- sensitivity: rms ~500 mK (primary); ~620 mK and ~900 mK in lower and higher frequency ranges (secondary)  
  > "with an rms noise of $\sim$620 mK and $\sim$900 mK in the lower and higher frequency ranges, respectively" (2.1 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 13CH3OH 8 transitions, e.g. 10(0,10)-9(1,8) (301.238–303.865 GHz)
- Line: CH3(18)OH 4 transitions (301.279–303.856 GHz)
- Line: CH2DOH 12(2,11)-12(1,12) b-type (301.514 GHz)
- Line: CH3OD 7(2,+)-7(1,-) (fit) and 7(4,-)-8(3,-) (303.296 GHz and 303.904 GHz)
- External data: OCS column density 1.2e18 cm-2 (source size 2.5", Tex=100 K), used to estimate O13CS blend  
  > "the column density for OCS derived by (cite: Zernickel2012) of 1.2$\times$10$^{18}$ cm$^{-2}$ (assuming a source size of 2.5${^{\second}}$) at $T_{\textrm{ex}}$ = 100 K" (3.2 CH3(18)OH) [from (cite: Zernickel2012)]
- External data: Updated CH2DOH line intensity log10 = -3.84±0.2 nm2 MHz at 300 K for the 301.514 GHz transition  
  > "an updated value for the base 10 logarithm of the integrated line intensity at 300 K for this transition of -3.84$\pm$0.2 nm$^2$ MHz (John Pearson, private communication)" (2.2 Analysis method) [from John Pearson, private communication]
- External data: 12C/13C = 62 and 16O/18O = 450 from galactocentric relations  
  > "a $^{12}$C/$^{13}$C ratio of 62 and a $^{16}$O/$^{18}$O ratio of 450 is adopted, both derived assuming D$_{\textrm{GC}}$ $\sim$7.02 kpc" (2.2 Analysis method) [from (cite: Milam2005), (cite: Wilson1999)]
- External data: CH3OD spectroscopy: frequencies summary and line strengths  
  > "we use the summary of CH$_3$OD frequencies reported by (cite: Walsh2000), the line strengths reported by (cite: Anderson1988) and (cite: Anderson1993)" (2.2 Analysis method) [from (cite: Walsh2000); (cite: Anderson1988); (cite: Anderson1993)]
- External data: Comparison deuteration ratios for Sgr B2, Orion KL, HH212, IRAS 16293  
  > "They report a tentative detection of CH$_2$DOH and derive a deuteration fraction for CH$_2$DOH/CH$_3$OH of 0.12%." (4.2 Comparison with other sources) [from (cite: Belloche2016); (cite: Neill2013); (cite: Peng2012); (cite: Bianchi2017); (cite: Jorgensen2017)]
- Simulation/model as data: GRAINOBLE gas-ice astrochemical model runs at constant T and nH = 1e4, 1e5, 1e6 cm-3 to relate CH2DOH/CH3OH to formation temperature  
  > "Models are shown for three different densities, $n_{\rm H}$ = 10$^4$, 10$^5$ and 10$^6$ cm$^{-3}$, with respective ages of 2$\times$10$^7$, 2$\times$10$^6$, and 2$\times$10$^5$ years." (4.4 Comparison with models)

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
- continuum subtraction: most line-free continuum channels selected and used for self calibration and continuum subtraction  
  > "the most line-free continuum channels were selected and used for both self calibration and continuum subtraction" (2.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.00" x 0.74"  
  > "Each spectrum represents the average of a 1$\overset{\second}{.}$00$\times$0$\overset{\second}{.}$74 region, equivalent to the area of the synthesised beam." (2.2 Analysis method)
- final rms: _not stated_

### Inherited from earlier work

- Observations, reduction and analysis procedures taken from earlier papers  
  > "The observations have been described in detail in (cite: McGuire2017), while the analysis and reduction procedures are described in detail in (cite: Brogan2016) and (cite: Hunter2017)" (2.1 Observations) [from (cite: McGuire2017); (cite: Brogan2016); (cite: Hunter2017)]
- GRAINOBLE model description  
  > "This code has been described in detail in previous studies (cite: Taquet2012; Taquet2013; Taquet2014)" (4.4 Comparison with models) [from (cite: Taquet2012; Taquet2013; Taquet2014)]

### Not stated but needed to reproduce (our reading)

- CASA version, calibrators and flux scale; calibration deferred to earlier papers
- Self-calibration parameters and which channels are line-free
- Imaging parameters (weighting, robust, cell, deconvolver, masks)
- Whether spectra are primary-beam corrected and whether Jy-to-K conversion was applied
- CASSIS fitting details (chi2 definition, noise, channel ranges used, line width fixing)
- Exact source size/beam filling treatment for LTE models
- Partition function details for CH3OD and handling of A/E methanol species
- Values of vLSR and FWHM fit procedure per region

## Analysis recipe

1. **Extract spectra**: Nine spectra averaged over a synthesised-beam-sized region from the data cube at positions sampling MM1, MM2, MM3  
  > "Nine spectra are extracted from the data cube. Each spectrum represents the average of a 1$\overset{\second}{.}$00$\times$0$\overset{\second}{.}$74 region, equivalent to the area of the synthesised beam." (2.2 Analysis method)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify lines and check blends**: Match isotopologue transitions using JPL/CDMS; exclude blending species by non-detection in space, Aij and Eup; check other transitions and parent species  
  > "In the first step, all species which have not previously been detected in space are excluded. Secondly, species are excluded based on Einstein $A_{ij}$ coefficient and upper state energy." (2.2 Analysis method)
   - software: CASSIS
   - fitting: _not stated_
   - validation: Second dataset (0.2") used to confirm presence of isotopologues  
  > "Based on transitions in these data the presence of the less abundant CH$_3$OH-isotopologues is confirmed." (2.2 Analysis method)
3. **Fit 13CH3OH Tex and N**: LTE optically thin synthetic spectra over a grid of Tex and N; minimum chi2 best fit, all 13CH3OH lines simultaneously  
  > "creating a grid of models, with $T_{\textrm{ex}}$ ranging between 50 and 350 K and $N$ ranging between 5$\times$10$^{16}$ and 5$\times$10$^{19}$ cm$^{-2}$, and selecting the model with the minimal $\chi^2$ as the best fit" (2.2 Analysis method)
   - software: CASSIS
   - parameter: Tex 50–350 K; N 5e16–5e19 cm-2  
  > "$T_{\textrm{ex}}$ ranging between 50 and 350 K and $N$ ranging between 5$\times$10$^{16}$ and 5$\times$10$^{19}$ cm$^{-2}$" (2.2 Analysis method)
   - assumption: LTE, optically thin, emitting size equal to the synthesised beam  
  > "angular size of the emitting region (which is assumed to be equal to the area of the synthesised beam)" (2.2 Analysis method)
   - fitting: Grid chi2 minimisation; no sampler  
  > "by creating a grid of models, with $T_{\textrm{ex}}$ ranging between 50 and 350 K and $N$ ranging between 5$\times$10$^{16}$ and 5$\times$10$^{19}$ cm$^{-2}$, and selecting the model with the minimal $\chi^2$ as the best fit" (Analysis method)
   - validation: Compared model with data; tested fitting only 302.166 and 303.865 GHz lines giving 5–10x higher N, saturating other lines  
  > "the column densities need to be higher by factors of 5–10, as compared to the best-fit column density when fitting to all lines" (3.1 13CH3OH)
4. **Fit other isotopologue columns**: Optimise N of CH3(18)OH, CH2DOH, CH3OD with Tex fixed to the 13CH3OH best-fit; model blends (CH3OCHO, O13CS, CH3NC) separately; fits with and without blend give ranges  
  > "the column densities of the remaining methanol isotopologues are optimised keeping the excitation temperature fixed at the value of the best-fit $^{13}$C-methanol model" (2.2 Analysis method)
   - software: CASSIS
   - assumption: CH2DOH vibrational correction factor 1.25; line strength uncertainty included  
  > "a vibrational correction factor of 1.25 has been applied to all listed values (Holger Müller, private communication)" (2.2 Analysis method)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive deuteration ratios**: Scale 13C and 18O methanol columns to CH3OH with 12C/13C=62 and 16O/18O=450; compute CH2DOH/CH3OH, CH3OD/CH3OH, CH2DOH/CH3OD  
  > "to estimate the $^{12}$CH$_3^{16}$OH column density used to calculate the deuterium fraction for each spectral region, a $^{12}$C/$^{13}$C ratio of 62 and a $^{16}$O/$^{18}$O ratio of 450 is adopted" (2.2 Analysis method)
   - assumption: Isotope ratios at DGC ~7.02 kpc  
  > "both derived assuming D$_{\textrm{GC}}$ $\sim$7.02 kpc" (2.2 Analysis method)
   - fitting: _not stated_
   - validation: Varied Tex: ratios within factor 2 of the 200 K value; 13C vs 18O ratios agree within ~2  
  > "the spread in CH$_2$DOH/CH$_3$OH and CH$_3$OD/CH$_3$OH ascribed to different excitation temperatures (over all regions) is within a factor 2 of the value derived for $T_{\textrm{ex}}$= 200 K" (4.1 NGC 6334)
6. **Compare with GRAINOBLE model**: Pseudo-time dependent constant T and density simulations of ice methanol deuteration compared to observed ratios to infer formation temperature  
  > "Based on the model predictions, our inferred deuterium fractionation of methanol in the NGC 6334 regions, indicate a temperature during formation around 30 K." (4.4 Comparison with models)
   - software: GRAINOBLE
   - assumption: Dust and gas temperatures equal; gas phase composition around hot cores reflects pre-stellar ices  
  > "the analysis is implicitly based on the assumption that the gas phase composition around the hot cores reflects the composition of the ices in the pre-stellar phase" (4.4 Comparison with models)
   - fitting: _not stated_
   - validation: Consistent with Herschel dust temperature 25–35 K of Russeil2013  
  > "show that the area is dominated by temperatures $\sim$25–35 K" (4.4 Comparison with models)

## Software

- **CASSIS** : Line identification and LTE synthetic spectrum modelling/fitting  
  > "For our line analysis, the software package CASSIS[^1] is used." (2.2 Analysis method)
- **JPL and CDMS databases** : Spectroscopic line data  
  > "For line input the Jet Propulsion Laboratory (JPL[^2]) and Cologne Database for Molecular Spectroscopy (CDMS[^3]) databases are used." (2.2 Analysis method)
- **GRAINOBLE** : Gas-ice astrochemical model of methanol deuteration  
  > "among these the GRAINOBLE model." (4.4 Comparison with models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Excitation temperature range | ~120–330 | not stated | K | 3 | The excitation temperatures of the best-fit models range between $\sim$120 and 330 K |
| 13CH3OH column density range | 0.8–8.3e17 | not stated | cm-2 | 3 | (0.8–8.3)$\times$10$^{17}$ cm$^{-2}$ for $^{13}$CH$_3$OH |
| CH2DOH column density range | 0.03–1.63e17 | not stated | cm-2 | 4 | (0.03–1.63)$\times$10$^{17}$ cm$^{-2}$ for CH$_2$DOH |
| CH3OD column density range | 0.15–5.5e17 | not stated | cm-2 | 4 | (0.15–5.5)$\times$10$^{17}$ cm$^{-2}$ for CH$_3$OD |
| CH2DOH/CH3OH (13C standard) | 0.03–0.34 | not stated | % | 5 | These values range from 0.03% to 0.34% for CH$_2$DOH and from 0.27% to 1.07% for CH$_3$OD |
| CH3OD/CH3OH (13C standard) | 0.27–1.07 | not stated | % | 5 | from 0.27% to 1.07% for CH$_3$OD if we use the $^{13}$C isotope of methanol as a standard |
| Mean CH2DOH/CH3OH (13C) | 0.13 | ±0.06 | % | 5 | 0.13$\%$$\pm$0.06$\%$ and 0.53$\%$$\pm$0.27$\%$ based on the $^{13}$C isotopologue |
| Mean CH3OD/CH3OH (13C) | 0.53 | ±0.27 | % | 5 | 0.13$\%$$\pm$0.06$\%$ and 0.53$\%$$\pm$0.27$\%$ based on the $^{13}$C isotopologue |
| CH2DOH/CH3OD column density ratio | 0.10–0.50 | not stated | dimensionless | 5 | These range from 0.10–0.50, the highest value associated with the region MM2 |
| Inferred grain temperature at formation | ~30 | not stated | K | 6 | indicate a dust temperature at the time of the systems formation $\sim$30 K |

## Qualitative findings

- CH3OD column densities are consistently higher than CH2DOH in all regions, giving CH2DOH/CH3OD far below the statistical value of 3  
  > "the column densities of CH$_3$OD are consistently higher than those of CH$_2$DOH throughout the region by factors of 2–15" (abstract)
- Homogeneous low CH2DOH/CH3OH suggests cores formed from the same precursor cloud  
  > "This homogeneity of the CH$_2$DOH/CH$_3$OH ratios derived for the different cores indicate that they formed from the same precursor cloud." (5 Summary and conclusion)

## Claim tuples

- H: Methanol deuteration in NGC 6334I is low compared with low-mass protostars and similar to Orion/Sgr B2 | E: LTE fits of methanol isotopologue lines at nine positions, ratios compared with literature | R: CH2DOH/CH3OH 0.03–0.34% and CH3OD/CH3OH 0.27–1.07% (13C standard) | F: Levels are much lower than in IRAS 16293 and HH212 and similar to or slightly below Sgr B2 and Orion | **supported**
- H: Astration explains low deuteration in the Galactic Centre | E: Compare NGC 6334I ratios (not near the GC) with Sgr B2 and model predictions | R: Similar low ratios, model implies ~30 K formation | F: Astration is not required; high temperature is the likely cause | **partially**
- H: CH2DOH and CH3OD form with statistical ratio 3 | E: Derived CH2DOH/CH3OD column density ratios | R: ~0.3 (0.10–0.50) | F: Ratio far below statistical, unexplained by models or experiments | **refuted**

## Reasoning

- Why this data: _not stated_
- Why this method: Optically thin, weak isotopologue lines are needed because main-isotopologue lines are thick; 13C and 18O methanol used as standards  
  > "Because CH$_3$OH is a very abundant species in star-forming regions, the lines of the primary $^{12}$C-isotope are optically thick and cannot be used to derive column densities and excitation temperatures." (2.2 Analysis method)
- Alternative: Gas-phase destruction processes rejected as cause of low CH2DOH/CH3OD since timescales exceed 1e5 yr  
  > "However the timescale needed to significantly alter the CH$_2$DOH/CH$_3$OD ratio through these reactions is likely too long, i.e., more than 10$^5$ years" (4.1 NGC 6334)
- How they decided it was enough: _not stated_
- Limitation (authors): CH2DOH spectroscopy poorly understood (b-type line), so CH2DOH/CH3OD may be higher  
  > "because the spectroscopy of CH$_2$DOH is not well understood, the CH$_2$DOH/CH$_3$OD ratios derived may be higher" (4.1 NGC 6334)
- Limitation (authors): 13CH3OH lines may be partially optically thick; single-Tex single-N models used, columns possibly underestimated  
  > "the $^{13}$CH$_3$OH lines, which are assumed to be optically thin, are in fact partially optically thick, and therefore the derived column densities may be slightly underestimated" (3.2 CH3(18)OH)
- Caveat (inferred, ours): Only one CH2DOH b-type line and heavy blending give large systematic uncertainty
- Caveat (inferred, ours): Single-Tex, beam-filling LTE model ignores gradients; no formal uncertainties on columns
- Caveat (inferred, ours): Model comparison assumes gas deuteration reflects pre-stellar ices
- Caveat (inferred, ours): Isotope ratios 12C/13C and 16O/18O adopted, not measured

## Reproducibility

- Data public (paper): Data cited by ALMA project codes in acknowledgements  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00150.S and #2015.A.00022.T." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details (deferred to Brogan2016, Hunter2017, McGuire2017)
- Missing: Exact CASSIS fit setup and line-free channels
- Missing: Private-communication spectroscopic corrections
- Missing: GRAINOBLE code not released
- Data volume (inferred): ~50-200 GB for the two projects' raw data; calibrated cubes smaller
- Score (inferred): 3/5, Data public and analysis is simple LTE fitting with listed lines, but processing is deferred to other papers and key fit details and spectroscopic corrections are unavailable.
- Rediscovery candidate: no, Calibration/imaging recipes and private spectroscopic corrections are missing, so the numeric results cannot be redone from the paper alone.

## Links

- Method: (cite: Brogan2016) (Data reduction and analysis procedures)
- Method: (cite: Hunter2017) (Data reduction procedures)
- Method: (cite: Taquet2014) (GRAINOBLE chemical model)
- Companion: (cite: McGuire2017) (Detailed description of the observations)
- Related: ALMA-PILS (IRAS 16293)

## Checks

```json
{
 "quotes": 67,
 "quotes_ok": 67,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 43,
  "rate": 0.524
 },
 "evidence_ok": true
}
```
