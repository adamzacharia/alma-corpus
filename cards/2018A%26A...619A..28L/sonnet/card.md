# The ALMA-PILS survey: Stringent limits on small amines and nitrogen-oxides towards IRAS 16293-2422B

`2018A&A...619A..28L` | Astronomy and Astrophysics 2018 | first author: Ligterink, N. F. W. | arXiv: 1808.00251 | DOI: 10.1051/0004-6361/201731980

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: astrochemistry, star_formation
- Question: Are NH2OH, CH3NH2 and their potential precursors NO, N2O and CH2NH present towards the low-mass protostar IRAS 16293B, and what do their abundances imply for formation routes?  
  > "We aim to detect both amines and their potential precursor molecules NO, N$_{2}$O and CH$_{2}$NH towards the low-mass protostellar binary IRAS 16293–2422" (abstract)
- Target **IRAS 16293-2422 source B**: coordinates RA 16h32m22.58s, Dec -24d28m32.8s (J2000), one-beam offset position  
  > "at a position offset by one beam diameter (0.5$''$) from the continuum peak position in the south west direction ($\alpha_{J2000}$=16$^{\rm h}$32$^{\rm m}$22.58s" (Observations and data analysis); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: Band 7, 329.147-362.896 GHz  
  > "The survey covers a spectral range of 329.147 to 362.896 GHz in Band 7, obtained with the 12 m array and the Atacama Compact Array (ACA)." (Observations and data analysis)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12 m array and ACA  
  > "obtained with the 12 m array and the Atacama Compact Array (ACA)" (Observations and data analysis)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: circular restoring beam 0.5"  
  > "produced with a circular restoring beam of 0.5$''$" (Observations and data analysis)
- max recoverable scale: 13"  
  > "The maximum recoverable scale is 13$^{\ensuremath{''}}$." (Observations and data analysis)
- sensitivity: RMS 7-10 mJy/beam/channel at 0.2 km/s resolution  
  > "A spectral resolution of 0.2 km s$^{-1}$ and a root mean square (RMS) noise level of about 7–10 mJy beam$^{-1}$ channel$^{-1}$" (Observations and data analysis)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH2NH hyperfine features at 332.575, 340.354, 351.455, 360.294 GHz (332-360 GHz)
- Line: N2O J=14-13 (351.667 GHz)
- Line: NO 4-3 hyperfine, Eup=36 K (350.69-351.05 GHz)
- Line: CH3NH2 6_1 -> 5_0 (upper limit) (357.440 GHz)
- Line: NH2OH 7_0-6_0 (upper limit) (352.522 GHz)
- Other facility **JCMT TIMASSS survey**: single-dish data used to confirm N2O and check CH2NH  
  > "Publicly available data of the single dish TIMASSS survey towards IRAS 16293 (cite: Caux2011) were analysed for CH$_{2}$NH spectral features" (Results)
- External data: Reference column densities NH2CHO=1e16, CH3OH=1e19, H2>1.2e25 cm-2 at B offset position  
  > "NH$_{2}$CHO = 1$\times$10$^{16}$, CH$_{3}$OH = 1$\times$10$^{19}$ and H$_{2}$ $>$1.2 $\times$10$^{25}$ cm$^{-2}$" (Astrochemical implications) [from (cite: Coutens2016; jorgensen2016)]
- External data: Abundance ratios in Sgr B2, Orion KL and hot core models for comparison  
  > "Sgr B2(M) | 31 | 3.2 | 0.008 | (cite: Belloche2013)" (Table 2) [from (cite: Belloche2013; Turner1991; Halfen2013; Neill2014; Garrod2013; Crockett2014)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 5-10% calibration uncertainty (10% used)  
  > "The dataset has a calibration uncertainty of 5–10%." (Observations and data analysis)
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
- final beam: 0.5" circular  
  > "produced with a circular restoring beam of 0.5$''$" (Observations and data analysis)
- final rms: 7-10 mJy/beam/channel  
  > "RMS) noise level of about 7–10 mJy beam$^{-1}$ channel$^{-1}$" (Observations and data analysis)

### Inherited from earlier work

- PILS data reduction and survey setup  
  > "The observations were taken as part of the Protostellar Interferometric Line Survey (PILS), an unbiased spectral survey using the Atacama Large Millimeter Array (ALMA, (cite: jorgensen2016))." (Observations and data analysis) [from (cite: jorgensen2016)]
- Upper limit column density formalism  
  > "For the non-detected species the formalism in (cite: Ligterink2015) is used to derive upper limit column densities" (Observations and data analysis) [from (cite: Ligterink2015)]

### Not stated but needed to reproduce (our reading)

- Calibration and imaging details (CASA version, weighting, continuum subtraction) are only in the PILS paper
- Exact grid step sizes and chi2 definition for the LTE fits
- Line-free ranges used for RMS of upper limits
- Adopted source size treatment for N2O in the PILS fit and the T_bg derivation
- TIMASSS line list and rotation diagram details

## Analysis recipe

1. **Fit LTE synthetic spectra to detected species**: Grid of LTE models fitted to lines at one-beam offset position, chi2 minimisation plus by-eye acceptance  
  > "From this model grid, we obtain the best-fit model solutions through $\chi^2$ minimisation." (Observations and data analysis)
   - software: CASSIS
   - parameter: CH2NH: N=1e14-5e15 cm-2, Tex=25-300 K; NO and N2O: N=1e15-1e17, Tex=25-400 K; Vpeak 2.5-2.9 km/s; FWHM=1 km/s  
  > "For CH$_{2}$NH, $N$ was varied between 1$\times$10$^{14}$ – 5$\times$10$^{15}$ cm$^{-2}$ and $T_\mathrm{ex}$ between 25 – 300 K" (Observations and data analysis)
   - assumption: LTE, source size 0.5", Tbg=21 K due to dust  
  > "For the one beam offset position at source B $T_{\rm bg}$ = 21 K" (Observations and data analysis)
   - fitting: chi2 minimisation over grid  
  > "we obtain the best-fit model solutions through $\chi^2$ minimisation" (Observations and data analysis)
   - validation: Non-detected higher-Eup lines constrain Tex; fits at other Tex show anti-coincidences  
  > "otherwise anti-coincidences with the $E_{\rm up}$ = 209 K lines in the synthetic spectrum show up" (Results)
2. **Derive 3 sigma upper limits for non-detections**: 1 sigma = 1.1*sqrt(dv*FWHM)*RMS on strongest transitions in line-free ranges, converted to N versus Tex  
  > "The 1$\sigma$ limit is given by 1.1$\cdot \sqrt{\delta\nu \cdot FWHM} \cdot$RMS" (Observations and data analysis)
   - software: CASSIS
   - parameter: Tex=100 K for quoted limits; 3 sigma 23 mJy km/s (CH3NH2), 27/21/27 (NH2OH)  
  > "resulting in a 3$\sigma$ of 27, 21 and 27 mJy km s$^{-1}$, respectively" (Results)
   - fitting: _not stated_
   - validation: Uncertainty of factor ~2 over reasonable Tex range  
  > "The typical uncertainty of the column densities of these upper limits for a reasonable range of excitation temperatures is a factor of $\sim$2" (Results)
3. **Confirm N2O with TIMASSS and estimate emitting size**: Gaussian fits and rotation diagram of four unblended TIMASSS lines; compare line fluxes to get emitting area  
  > "the emitting area in the TIMASSS data is found to be around 1.6$''$" (Results)
   - fitting: Gaussian profiles; rotational temperature diagram  
  > "From the fits a rotational temperature diagram is created" (N2O fit of TIMASSS data set)
   - validation: _not stated_
4. **Compute abundance ratios and compare with Sgr B2, Orion KL and models**: Ratios to NH2CHO, CH3OH and H2 compared with literature  
  > "the column density ratios between the molecules studied here and formamide (NH$_{2}$CHO), methanol (CH$_{3}$OH) and molecular hydrogen (H$_{2}$) are computed and compared with other sources" (Astrochemical implications)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASSIS** : line identification and LTE synthetic spectra  
  > "The spectra are analysed with the CASSIS software" (Observations and data analysis)
- **JPL and CDMS catalogs** : line lists  
  > "linelists from the Jet Propulsion Laboratory (JPL[^2]) catalog for molecular spectroscopy" (Observations and data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(CH2NH) | (6.0-10.0)e14 | range | cm-2 | 1 | Methanimine / CH$_2$NH / (6.0 – 10.0)$\times$10$^{14}$ / 70 – 120 |
| N(NO) | (1.5-2.5)e16 | range | cm-2 | 1 | Nitric oxide / NO / (1.5 – 2.5)$\times$10$^{16}$ / 40 – 150 |
| N(N2O) | >=4.0e16 | lower limit | cm-2 | 1 | $\geq$4.0$\times$10$^{16,\ddagger}$ |
| N(NH2OH) 3 sigma upper limit at 100 K | <=3.7e14 | not stated | cm-2 | 2 | upper limit column density of NH$_{2}$OH of $\leq$3.7$\times$10$^{14}$ cm$^{-2}$ at $T_{\rm ex}$ = 100 K |
| N(CH3NH2) 3 sigma upper limit at 100 K | <=5.3e14 | factor ~2 | cm-2 | 2 | the upper limit column density is $\leq$5.3$\times$10$^{14}$ cm$^{-2}$ |
| N2O Tex and N from TIMASSS | 68 K; 1.7e16 cm-2 | N ±25% | K; cm-2 | 3 | The best fit to the optically thin lines in the TIMASSS data is found for $T_{\rm ex}$ = 68 K and $N$ = 1.7$\times$10$^{16}$ cm$^{-2}$ |
| N(NH2OH)/N(H2) | <=3.1e-11 | not stated | dimensionless | 4 | $N$(NH$_{2}$OH)/$N$(H$_{2}$) $\leq$3.1$\times$10$^{-11}$ |
| N(NO)/N(N2O) | <=0.5 | not stated | dimensionless | 4 | The $N$(NO)/$N$(N$_{2}$O) $\leq$ 0.5 ratio |

## Qualitative findings

- CH2NH and N2O detected for the first time towards a low-mass protostar; NO also detected  
  > "CH$_2$NH and N$_{2}$O are detected for the first time towards a low-mass source" (abstract)

## Claim tuples

- H: Are CH3NH2 and NH2OH present towards IRAS 16293B? | E: Search PILS spectra and derive 3 sigma upper limits | R: Not detected; N<=5.3e14 and <=3.7e14 cm-2 | F: Limits importance of amino acid routes via these species | **supported**
- H: Are CH2NH, NO and N2O detectable? | E: LTE fits to PILS and TIMASSS data | R: CH2NH, NO detected; N2O tentative in PILS, supported by TIMASSS | F: Amino acid routes via CH2NH remain plausible | **supported**
- H: Do low- and high-mass sources differ in amine chemistry? | E: Compare abundance ratios with Sgr B2 and models | R: CH2NH and CH3NH2 ratios lower than Sgr B2 and models | F: Formation is less efficient in IRAS 16293B and overpredicted by models | **partially**

## Reasoning

- Why this data: IRAS 16293 is well studied, rich in complex organics, and PILS is unbiased with high resolution  
  > "Its physics and chemistry are well studied and it is abundant in complex organic molecules" (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Comparison with single-dish Sgr B2/Orion data may reflect beam dilution rather than chemistry  
  > "differences in abundance ratios do not necessarily reflect chemical differences" (Astrochemical implications)
- Caveat (inferred, ours): N2O detection in PILS is a single line, tentative
- Caveat (inferred, ours): Fit acceptance partly by eye; no formal uncertainties
- Caveat (inferred, ours): H2 is only a lower limit so abundances are limits
- Caveat (inferred, ours): Source size for N2O is uncertain

## Reproducibility

- Data public (paper): PILS data from project 2013.1.00278.S; TIMASSS publicly available  
  > "Publicly available data of the single dish TIMASSS survey towards IRAS 16293" (Results)
- Products in archive: _not stated_
- Missing: Calibrated PILS cubes processing details
- Missing: CASSIS fit grid steps
- Data volume (inferred): Large: full Band 7 survey cubes, hundreds of GB; subset spectra small
- Score (inferred): 3/5, Public data and clear LTE recipe, but PILS reduction is in other papers and fits are partly by eye.
- Rediscovery candidate: yes, Public data, simple LTE fit and upper-limit recipe with numeric results, though dependent on PILS cubes.

## Links

- Method: (cite: jorgensen2016) (PILS survey description and data reduction)
- Method: (cite: Ligterink2015) (upper limit formalism)
- Companion: (cite: Coutens2016) (PILS formamide and reference column densities)
- Companion: (cite: Lykke2017) (PILS analysis at same position)
- Related: PILS
- Related: TIMASSS

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 67,
  "stated": 32,
  "rate": 0.478
 },
 "evidence_ok": true
}
```
