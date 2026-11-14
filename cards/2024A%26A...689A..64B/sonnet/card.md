# An ALCHEMI inspection of sulphur-bearing species towards the central molecular zone of NGC 253

`2024A&A...689A..64B` | Astronomy and Astrophysics 2024 | first author: Bouvier, M. | arXiv: 2405.08408 | DOI: 10.1051/0004-6361/202449186

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, astrochemistry
- Question: Which type of gas regions are probed by sulphur-bearing species in the NGC 253 CMZ, and which process(es) dominate the release of sulphur into the gas phase?  
  > "We intend to understand which type of regions are probed by sulphur-bearing species and which process(es) dominate(s) the release of sulphur into the gas phase." (abstract)
- Target **NGC 253 CMZ**: coordinates RA(ICRS)=00h47m33.26s, Dec(ICRS)=-25d17m17.7s (field centre)  
  > "NGC 253 is a nearby starburst galaxy located at a distance of 3.5 Mpc (cite: rekola_distance_2005) with an inclination of 76$^\circ$ (cite: mccormick_2013)." (2 The structure of the central molecular zone of NGC 253); "were centred at the position $\alpha$(ICRS)$=00^h47^m33.26^s$ and $\delta$(ICRS)$=-25^\circ 17'17.7''$" (3 Observations, Data Processing and Line Selection); z/distance 3.5 Mpc  
  > "NGC 253 is a nearby starburst galaxy located at a distance of 3.5 Mpc (cite: rekola_distance_2005) with an inclination of 76$^\circ$ (cite: mccormick_2013)." (2 The structure of the central molecular zone of NGC 253); "were centred at the position $\alpha$(ICRS)$=00^h47^m33.26^s$ and $\delta$(ICRS)$=-25^\circ 17'17.7''$" (3 Observations, Data Processing and Line Selection); distance from Rekola et al. 2005  
  > "NGC 253 is a nearby starburst galaxy located at a distance of 3.5 Mpc (cite: rekola_distance_2005) with an inclination of 76$^\circ$ (cite: mccormick_2013)." (2 The structure of the central molecular zone of NGC 253); "were centred at the position $\alpha$(ICRS)$=00^h47^m33.26^s$ and $\delta$(ICRS)$=-25^\circ 17'17.7''$" (3 Observations, Data Processing and Line Selection)

## Data provenance

- ALMA projects: 2017.1.00161.L, 2018.1.00162.S
- bands: Bands 3 through 7, 84.2-373.2 GHz  
  > "The observations covered Bands 3 through 7, with a frequency ranging between 84.2 and 373.2 GHz" (3 Observations, Data Processing and Line Selection)
- frequencies and spectral setup: spectral resolution ~10 km/s  
  > "The spectral resolution is $\sim 10$ km.s$^{-1}$." (3 Observations, Data Processing and Line Selection)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: common beam 1.6" x 1.6" (~27 pc)  
  > "All the data cubes have a common beam size of $1.6\ensuremath{''}\times 1.6\ensuremath{''}$ ($\sim 27$ pc)" (3 Observations, Data Processing and Line Selection)
- max recoverable scale: >=15" (>=255 pc)  
  > "a maximum recovered scale of $\geq 15''$ ($\geq 255$ pc)" (3 Observations, Data Processing and Line Selection)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycles 5 and 6  
  > "The observations were performed during Cycles 5 and 6" (3 Observations, Data Processing and Line Selection)
- pi or archival as stated: ALCHEMI Large Program (co-PIs S. Martin, N. Harada, J. Mangum)  
  > "The observations used in this work are part of the ALCHEMI Large Program (co-PIs.: S. Martín, N. Harada, and J. Mangum)." (3 Observations, Data Processing and Line Selection)
- Line: CS J=2-1 to 7-6 (97980-342883 MHz)
- Line: H2S (and H2-34S) 1_10-1_01, 2_20-2_11, 3_30-3_21 (168762, 216710, 300505 MHz)
- Line: OCS J=7-6 to 29-28 (85139-352599 MHz)
- Line: H2CS many ortho/para lines (101477-371847 MHz)
- Line: SO and 34SO many lines (84410-344310 MHz)
- Line: SO2 many lines (104029-371172 MHz)
- Line: CCS many lines (86181-336722 MHz)
- External data: Collisional excitation rates for LVG (BASECOL/LAMDA)  
  > "The collision excitation rates were taken from the BASECOL database, except for H$_2$CS and SO$_2$ for which the rates were taken from the LAMDA database." (5.2.2 Methodology of the LVG analysis) [from (cite: dubernet_basecol_2013); (cite: schoier_lamda_2005)]
- External data: 32S/34S ratio of 10  
  > "We assumed a value of 10 for the $^{32}$S/$^{34}$S ratio, as derived in Martin et al. 2021." (12 LVG modeling and results) [from Martin et al. 2021 (cite: martin_alchemi_2021)]
- External data: Physical conditions of other species (C2H, H3O+/SO, HCN/HNC, HNCO, SiO) in the CMZ  
  > "Previous ALCHEMI studies derived physical conditions of the gas emitting C$_2$H (cite: holdship_distribution_2021), H$_3$O$^+$ and SO (cite: holdship_energizing_2022)" (6.1 Comparison with previous ALCHEMI studies) [from Holdship 2021, 2022; Behrens 2022; Huang 2023]
- External data: Galactic S-species abundance ratios for L1157-B1, Orion KL, PDRs, dark clouds, GC clouds  
  > "we selected the prototypical L1157-B1 bow shock, a well-known shocked region within the protostellar outflow of L1157-mm" (6.2 Comparison with Galactic environments) [from various, e.g. (cite: esplugues_line_2013), (cite: vastel_sulphur_2018)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: ALCHEMI-provided continuum-subtracted cubes  
  > "We used the continuum-subtracted FITS image cubes provided by ALCHEMI" (3 Observations, Data Processing and Line Selection)
- flux calibrator: _not stated_
- flux scale uncertainty: 15%  
  > "following (cite: martin_alchemi_2021), we adopted a flux calibration error of 15%." (3 Observations, Data Processing and Line Selection)
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
- continuum subtraction: provided already subtracted by ALCHEMI  
  > "We used the continuum-subtracted FITS image cubes provided by ALCHEMI" (3 Observations, Data Processing and Line Selection)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: all cubes at common 1.6" beam  
  > "All the data cubes have a common beam size of $1.6\ensuremath{''}\times 1.6\ensuremath{''}$" (3 Observations, Data Processing and Line Selection)
- final beam: _not stated_
- final rms: measured per spectrum by 0th-order polynomial fit to line-free channels  
  > "we fit a $0^{\rm{th}}$ order polynomial to the line-free channels from the continuum-subtracted data cubes to retrieve the information about the spectral root-mean-square (rms)." (3 Observations, Data Processing and Line Selection)

### Inherited from earlier work

- Data acquisition, calibration and imaging  
  > "The full details of the data acquisition, calibration and imaging are described by (cite: martin_alchemi_2021)." (3 Observations, Data Processing and Line Selection) [from (cite: martin_alchemi_2021)]
- Flux calibration error of 15%  
  > "following (cite: martin_alchemi_2021), we adopted a flux calibration error of 15%." (3 Observations, Data Processing and Line Selection) [from (cite: martin_alchemi_2021)]
- Line identification used to assess contamination  
  > "we used the existing line identification ((cite: martin_alchemi_2021) and priv. comm.)" (3 Observations, Data Processing and Line Selection) [from (cite: martin_alchemi_2021)]
- Region definitions (GMCs, proto-SSCs)  
  > "Regions GMC10, GMC7, and GMC6 correspond to the Giant Molecular Clouds 10, 7, and 6, respectively, as previously defined by (cite: leroy_alma_2015)." (4 Emission Distribution and Targeted Regions) [from (cite: leroy_alma_2015); (cite: huang_reconstructing_2023); (cite: leroy_forming_2018)]

### Not stated but needed to reproduce (our reading)

- Private-communication line identifications used for contamination checks
- Exact line-free channel ranges for rms and baseline fitting
- grelvg grid sampling steps and chi-square definition/minimisation details
- How blended-line multi-Gaussian fits were initialised
- Exact velocity windows for direct integration of each line
- Exact ALCHEMI data release/version of the cubes
- Rotation-diagram fitting code and how upper limits were treated

## Analysis recipe

1. **Extract spectra and line parameters**: Velocity-integrated maps and beam-sized (1.6") spectra from ALCHEMI cubes; direct integration for non-blended lines, Gaussian fits for FWHM and Vlsr, two-Gaussian fits for blended lines; flux converted to brightness temperature  
  > "In the case of non-blended lines, we measured the direct integration of the channel intensities." (5.1 Gaussian Fit and Spectra); "we performed a multi-Gaussian fit (with two Gaussian components)" (5.1 Gaussian Fit and Spectra)
   - software: GILDAS MAPPING, GILDAS CLASS, WEEDS
   - parameter: 3 sigma detection threshold; lines >15% contaminated rejected  
  > "the threshold for line detection was set to 3$\sigma$ for the integrated intensity." (3 Observations, Data Processing and Line Selection)
   - parameter: Spectra from circular region of one beam (1.6") at coordinates in Table 1  
  > "We extracted each spectrum from a circular region of a beam size (1.6$"$) centred at the coordinates given in Tab. [1](#tab:regions)." (5.1 Gaussian Fit and Spectra)
   - fitting: _not stated_
   - validation: _not stated_
2. **Rotation diagram LTE analysis**: Rotation diagrams without beam correction, one to three rotation temperature components, chi-square minimisation including 15% calibration error and rms  
  > "we performed rotation diagrams (RDs) without beam correction." (5.2 Derivation of physical parameters); "The best-fit was calculated by minimizing the reduced chi-square, $\chi^2_r$." (5.2.1 LTE analysis: OCS, CCS, and SO2)
   - assumption: LTE, optically thin lines, beam filling factor 1  
  > "The beam filling factor was set to 1 as (1) we do not know the size of emission of the species" (5.2.1 LTE analysis: OCS, CCS, and SO2)
   - fitting: reduced chi-square minimisation  
  > "The best-fit was calculated by minimizing the reduced chi-square, $\chi^2_r$." (5.2.1 LTE analysis: OCS, CCS, and SO2)
   - validation: _not stated_
3. **Non-LTE LVG modelling**: Grid (>=10,000 models) over column density, gas density and gas temperature, with source size free when >=4 lines; fit each rotation-temperature component separately; slab geometry  
  > "For each region and species, we ran a large grid of models ($\geq 10,000$) varying the column density of the species, the gas density and the gas temperature." (5.2.2 Methodology of the LVG analysis)
   - software: grelvg
   - parameter: N 5e12-1e18 cm-2; n 1e3-1e8 cm-3; T limited to collisional-rate range; source size 0.1"-150"  
  > "In *grelvg* the sizes can vary between 0.1$\ensuremath{''}$ and 150$\ensuremath{''}$." (5.2.2 Methodology of the LVG analysis)
   - assumption: Semi-infinite slab geometry, CBR 2.7 K, H2 OPR=3, line widths from measured averages, 15% calibration error  
  > "we assumed the geometry to be a semi-infinite slab" (5.2.2 Methodology of the LVG analysis); "The ortho-to-para ratio (OPR) for H$_2$ is assumed to be set to the statistical value of 3." (5.2.2 Methodology of the LVG analysis)
   - fitting: best chi-square over grid; uncertainty ranges from chi-square  
  > "For each region and species, we ran a large grid of models ($\geq 10,000$) varying the column density of the species, the gas density and the gas temperature." (5.2.2 Methodology of the LVG analysis)
   - validation: Uniform-sphere geometry gave similar results (not shown)  
  > "We nonetheless performed some modelling using the geometry of a uniform sphere which led to similar results (not shown)." (5.2.2 Methodology of the LVG analysis)
4. **Compare with ALCHEMI studies and Galactic regions**: Compare derived T and n with other ALCHEMI tracers; compare abundance ratios of S-bearing species with Galactic shocks, hot cores, PDRs, clouds  
  > "we compare various S-bearing abundance ratios." (6.2 Comparison with Galactic environments)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS (MAPPING, CLASS)** : Velocity-integrated maps, spectra extraction, Gaussian fitting  
  > "We processed the FITS image cubes using the packages MAPPING and CLASS from GILDAS" (3 Observations, Data Processing and Line Selection)
- **WEEDS** : Checking line contamination using JPL and CDMS  
  > "performed an additional check using the CLASS extension WEEDS" (3 Observations, Data Processing and Line Selection)
- **grelvg** : Non-LTE LVG modelling  
  > "we performed a non-LTE analysis using the large velocity gradient (LVG) code *grelvg*" (5.2.2 Methodology of the LVG analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| OCS first-component Trot range | 10 to 65 | not stated | K | 2 | ranges from $T_{\text{rot}}=10$ K in GMC10 to $T_{\text{rot}}=65$ K in SSC5 |
| OCS second-component Trot range | 124-312 | not stated | K | 2 | The range of the second temperature component is $T_{\text{rot}}=124-312$ K. |
| SO2 Trot components | 55-79 and 115-298 | not stated | K | 2 | The first and second components have $T_{\text{rot}}= (55-79)$ K and $(115-298)$ K, respectively. |
| H2S gas temperature (inner CMZ and GMC10) | 30-159 | not stated | K | 3 | $T_{\text{gas}}=30-159$ K and $n_{\text{gas}}\geq 10^7$cm$^{-3}$ |
| H2S emission size | 0.17-0.5 | not stated | arcsec | 3 | values ranging between 0.17 and 0.5$\ensuremath{''}$ ($\sim 3-8$ pc) |
| CS low-Eu component gas temperature | 5-14 | not stated | K | 3 | values between $T_{\text{gas}}=5-14$ K, and between $T_{\text{gas}}=15-110$ K for the first and second components |
| OCS low-Eu LVG column density | 2e15-5e17 | not stated | cm^-2 | 3 | The total column densities derived range between $2\times10^{15}$ and $5\times10^{17}$ cm$^{-2}$. |
| Best H2S OPR | 1 | not stated | dimensionless | 3 | We found that the best OPR reproducing the observations in all the regions is 1. |

## Qualitative findings

- H2S and parts of OCS, H2CS, SO emission trace shocks; part of SO and CS emission trace dense molecular gas  
  > "strong evidence indicates that H$_2$S and part of the emission of OCS, H$_2$CS, and SO, are tracing shocks whilst part of SO and CS emission rather trace the dense molecular gas." (abstract)
- Shocks are mild/low-velocity, not strong SiO-type shocks  
  > "none of these S-bearing species are probing fast and, thus, strong shocks since they do not trace the same gas as SiO" (6.3.1 Primary shock tracers)

## Claim tuples

- H: Most S-bearing species in the CMZ trace shocks tied to star formation | E: LTE and LVG analysis plus comparison with ALCHEMI tracers and Galactic abundance ratios | R: H2S, low-Eu OCS and H2CS, high-Eu SO show shock-like conditions and ratios | F: Emission is likely dominated by shocks associated with ongoing star formation | **supported**
- H: Shocks vs thermal evaporation in the inner CMZ with proto-SSCs | E: Compared temperatures with desorption temperatures and shock tracers | R: Hot components of H2CS, OCS, SO2 consistent with thermal desorption but shocks not excluded | F: Cannot distinguish the two processes in the inner CMZ | **partially**
- H: Low-Eu SO and CS trace dense molecular gas | E: Compared LVG conditions with HCN/HNC and GMC properties | R: Warm moderately dense SO and cold dense CS on GMC scales | F: These components trace dense GMC gas | **partially**

## Reasoning

- Why this data: ALCHEMI offers high resolution and many transitions per species  
  > "giving us access to both high angular resolution ($1.6\ensuremath{''}$ or $\sim 27$ pc) and a large number of transitions for many molecular species" (1 Introduction)
- Why this method: Multiple transitions over wide Eu range allow RDs to identify components, then LVG for non-LTE conditions  
  > "As we cover a large range of $E_{\text{u}}$ for most of the species, it can allow us to identify whether different components with different excitation conditions" (5.2 Derivation of physical parameters)
- Alternative: Fitting all transitions with one LVG component was tried but failed to reproduce low and high Eu lines together  
  > "we could not find models reproducing simultaneously the low- and high-upper-level energy transitions." (5.2.2 Methodology of the LVG analysis)
- Alternative: Uniform sphere geometry tested, similar results  
  > "We nonetheless performed some modelling using the geometry of a uniform sphere which led to similar results (not shown)." (5.2.2 Methodology of the LVG analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): CS results poorly constrained, source size fixed at 1.6"  
  > "Overall, due to the low number of transitions available for each of the component, the results for CS are among the less constrained and should be taken with caution." (5.2.3 Results of the LVG analysis)
- Limitation (authors): No non-LTE analysis possible for CCS, SO2, OCS second component  
  > "We could not perform the non-LTE analysis for CCS, SO$_2$, and OCS." (5.2 Derivation of physical parameters)
- Limitation (authors): Comparing GMC-scale NGC 253 with parsec scale Galactic regions  
  > "We would like to raise a word of caution as we are comparing GMC-size scales in NGC 253 with parsec and sub-parsec scales in the various Galactic environments." (6.2 Comparison with Galactic environments)
- Caveat (inferred, ours): Two-component assumption and fixed source sizes make LVG solutions degenerate
- Caveat (inferred, ours): Beam of 27 pc blends multiple proto-SSCs and mixes components
- Caveat (inferred, ours): Shock vs. hot core assignment relies on qualitative ratio comparison without chemical modelling
- Caveat (inferred, ours): Collisional rate discrepancies between LAMDA and BASECOL for OCS

## Reproducibility

- Data public (paper): ALMA data identified by project codes; ALCHEMI cubes used  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.00161.L and ADS/JAO.ALMA#2018.1.00162.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Private-communication line identifications
- Missing: grelvg code version and grid settings
- Missing: Exact integration windows and fit initialisation
- Data volume (inferred): Large: ALCHEMI Bands 3-7 spectral-scan cubes, hundreds of GB; selected cubes tens of GB
- Score (inferred): 3/5, Public ALCHEMI cubes and clear workflow, but LVG details, private line IDs and some choices are missing.
- Rediscovery candidate: no, Recipe is only partly complete (private line IDs, grelvg grid details) and several results are ranges and interpretive.

## Links

- Method: (cite: martin_alchemi_2021) (ALCHEMI data acquisition, calibration, imaging and line identification)
- Method: (cite: ceccarelli_2003) (Origin of the grelvg LVG code)
- Companion: (cite: huang_reconstructing_2023) (HNCO and SiO shock analysis in the same CMZ)
- Companion: (cite: holdship_energizing_2022) (SO and H3O+ analysis in NGC 253)
- Companion: (cite: behrens_tracing_2022) (HCN/HNC analysis in NGC 253)
- Related: ALCHEMI

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
