# The ALMA-PILS survey: detection of CH<SUB>3</SUB>NCO towards the low-mass protostar IRAS 16293-2422 and laboratory constraints on its formation

`2017MNRAS.469.2219L` | Monthly Notices of the Royal Astronomical Society 2017 | first author: Ligterink, N. F. W. | arXiv: 1703.03252 | DOI: 10.1093/mnras/stx890

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Is CH3NCO present toward the low-mass protostellar binary IRAS 16293-2422, how does its abundance compare with other sources, and can it form in the solid state via CH3 + HNCO?  
  > "unambiguously identify CH$_{3}$NCO through the detection of 43 unblended transitions in the ALMA Protostellar Interferometric Line Survey (PILS) of the low mass solar-type protostellar binary IRAS 16293-2422." (abstract)
- Target **IRAS 16293-2422 source B (one beam SW offset position)**: coordinates α=16h32m22.58s, δ=-24d28m32.8s (J2000)  
  > "The first position is offset by one beam diameter ($\sim$0.5$\ensuremath{''}$) from the continuum peak of source B in the south west direction" (2.1 The ALMA PILS survey); "IRAS16293 (d = 120 pc) is considered as a protostellar template for low-mass sources" (1 Introduction); z/distance d = 120 pc  
  > "The first position is offset by one beam diameter ($\sim$0.5$\ensuremath{''}$) from the continuum peak of source B in the south west direction" (2.1 The ALMA PILS survey); "IRAS16293 (d = 120 pc) is considered as a protostellar template for low-mass sources" (1 Introduction); distance from _not stated_
- Target **IRAS 16293-2422 source A (0.3 arcsec offset position)**: coordinates α=16h32m22.90s, δ=-24d28m36.2s (J2000)  
  > "the position $\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22$s$90, $\delta_{\rm J2000}$=$-24 \ensuremath{^\circ} 28 \ensuremath{'} 36.2 \ensuremath{''}$ appears to be one of the best positions to search for new species toward source A (0.3$''$ offset)" (2.1 The ALMA PILS survey); z/distance d = 120 pc  
  > "the position $\alpha_{\rm J2000}$=16$^{\rm h}$32$^{\rm m}$22$s$90, $\delta_{\rm J2000}$=$-24 \ensuremath{^\circ} 28 \ensuremath{'} 36.2 \ensuremath{''}$ appears to be one of the best positions to search for new species toward source A (0.3$''$ offset)" (2.1 The ALMA PILS survey); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00278.S
- bands: _not stated_
- frequencies and spectral setup: 329.147 to 362.896 GHz; spectral resolution 0.2 km/s  
  > "this survey covers a spectral range from 329.147 to 362.896 GHz and was obtained with both the 12m array and the Atacama Compact Array (ACA)." (2.1 The ALMA PILS survey)
- continuum bandwidth: _not stated_
- arrays: 12m array and ACA  
  > "was obtained with both the 12m array and the Atacama Compact Array (ACA)" (2.1 The ALMA PILS survey)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.4-0.7 arcsec native; circular 0.5 arcsec restoring beam used  
  > "The beam size ranges between $\sim$0.4$\ensuremath{''}$ and 0.7$\ensuremath{''}$ depending on the configuration at the time of the observations." (2.1 The ALMA PILS survey)
- max recoverable scale: _not stated_
- sensitivity: rms 7-10 mJy/beam/channel (~4-5 mJy/beam km/s)  
  > "The rms of the combined data sets is about 7–10 mJy beam$^{-1}$ channel$^{-1}$, i.e., approximately 4–5 mJy beam$^{-1}$ km s$^{-1}$." (2.1 The ALMA PILS survey)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: CH3NCO (vb=0) 43 unblended transitions, e.g. 39(0,39,0)-38(0,38,0) (336339.9 MHz (example))
- Other facility **CryoPAD2 (Sackler Laboratory for Astrophysics)**: VUV irradiation experiments on CH4:HNCO ices with RAIRS and TPD  
  > "The Cryogenic Photoproduct Analysis Device 2 (CryoPAD2) in the Sackler Laboratory for Astrophysics is used to perform the measurements" (3 Laboratory experiments)
- External data: Spectroscopic data for CH3NCO from CDMS, taken from Cernicharo et al. and Koput  
  > "The identification is based on spectroscopic data from the Cologne Database for Molecular Spectroscopy (CDMS, (cite: muller2001; muller2005)), taken from (cite: cernicharo2016) as well as from (cite: koput1986)." (2.2 Results) [from (cite: muller2001; muller2005; cernicharo2016; koput1986)]
- External data: 12C/13C ratio of 68 for HNCO column density  
  > "assuming a $^{12}$C/$^{13}$C ratio of 68 (cite: milam2005)" (2.2 Results) [from (cite: milam2005)]
- External data: CH3OH column density from CH3 18OH, and CH3CN column densities (in prep.)  
  > "CH$_3$CN was analysed by Calcutt et al. (in prep.) toward both source A ($\sim$ 8 $\times$ 10$^{16}$ cm$^{-2}$) and source B ($\sim$ 3 $\times$ 10$^{16}$ cm$^{-2}$)." (2.2 Results) [from Jørgensen et al. (in prep.); Calcutt et al. (in prep.)]

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
- final beam: circular 0.5 arcsec restoring beam at 0.2 km/s resolution  
  > "the combined data set used in this paper was produced with a circular restoring beam of 0.5$\ensuremath{''}$ at a spectral resolution of 0.2 km s$^{-1}$." (2.1 The ALMA PILS survey)
- final rms: 7-10 mJy/beam/channel  
  > "The rms of the combined data sets is about 7–10 mJy beam$^{-1}$ channel$^{-1}$" (2.1 The ALMA PILS survey)

### Inherited from earlier work

- Full description and data reduction of the PILS survey  
  > "A full description and data reduction of the survey is presented in (cite: jorgensen2016)." (2.1 The ALMA PILS survey) [from (cite: jorgensen2016)]
- Source size of 0.5 arcsec assumed for column densities  
  > "assuming the same source size of 0.5$\ensuremath{''}$ as used in previous PILS studies (cite: coutens2016; jorgensen2016; lykke2017)" (2.2 Results) [from (cite: coutens2016; jorgensen2016; lykke2017)]

### Not stated but needed to reproduce (our reading)

- Calibration, self-calibration and imaging details (in Jørgensen et al. 2016)
- Line widths, vLSR and fitting procedure used in CASSIS LTE models
- Spectral extraction details (single pixel or beam average) at the offset positions
- CASSIS version
- Chi-square or other criteria for choosing Tex and N
- CH3OH and CH3CN column densities are from unpublished work
- Details of IR band integration ranges and baselines
- Gas-grain model parameters

## Analysis recipe

1. **Identify CH3NCO lines and fit LTE models**: Identified unblended CH3NCO lines at two offset positions and compared LTE models for Tex=100 and 300 K  
  > "Using the CASSIS software, we have been able to identify 43 unblended lines of CH$_3$NCO in the bending ground state ($\nu_b$ = 0)" (2.2 Results)
   - software: CASSIS
   - parameter: Source size 0.5 arcsec; Tex 100 and 300 K  
  > "the CH$_{3}$NCO column density is found to be about 3 $\times$ 10$^{15}$ cm$^{-2}$ and 4 $\times$ 10$^{15}$ cm$^{-2}$ for $T_{\rm ex}$ = 300 and 100 K, respectively." (2.2 Results)
   - assumption: LTE, optically thin lines  
  > "All lines are optically thin." (2.2 Results)
   - fitting: _not stated_
   - validation: Column densities accurate to better than 30%  
  > "It is expected that for the same assumptions all column densities toward source B are accurate to better than 30%." (2.2 Results)
2. **Upper limits for isomers and HOCN, and HNCO column density**: 3 sigma upper limits for CH3CNO, CH3OCN, HOCN; HN13CO re-analysed with 12C/13C=68 to get HNCO  
  > "From this non-detection $3\sigma$ upper limits of 5 $\times$ 10$^{13}$ cm$^{-2}$ and 5 $\times$ 10$^{14}$ cm$^{-2}$ are derived, respectively (assuming an excitation temperature of 100 K)." (2.2 Results)
   - assumption: 12C/13C = 68  
  > "assuming a $^{12}$C/$^{13}$C ratio of 68 (cite: milam2005)" (2.2 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Laboratory test of CH3 + HNCO formation**: VUV irradiation of 13CH4/CH4:HNCO 5:1 ices at 20 K, monitored by RAIRS and TPD (m/z 57, 56)  
  > "mixtures of $^{13}$CH$_{4}$/CH$_{4}$:HNCO at 5:1 ratio are prepared." (3.1 Set-up and method)
   - parameter: Fluence ~3.3e17 photons; 1 cm-1 IR resolution  
  > "irradiated with a total fluence of $\sim$3.3$\times$10$^{17}$ photons" (3.1 Set-up and method)
   - assumption: CH3NCO NCO stretch band strength equals that of HNCO  
  > "making the assumption that the bandstrength of the NCO antisymmetric stretch vibration of methyl isocyanate equals that of the corresponding vibration of HNCO" (3.2 Results – IR Spectra)
   - fitting: _not stated_
   - validation: 13C isotope red shift of ~10 cm-1; controls with pure HNCO and CH4  
  > "a clear red shift of about 10 cm$^{-1}$ of the two features is seen between the sample of $^{12}$CH$_{4}$ and $^{13}$CH$_{4}$" (3.2 Results – IR Spectra)

## Software

- **CASSIS** : Line identification and LTE modelling  
  > "Using the CASSIS software[^3], we have been able to identify 43 unblended lines" (2.2 Results)
- **MAGICKAL** : Gas-grain model by Belloche et al. 2017 used for comparison  
  > "have incorporated reactions [\[eq.belloche1\]](#eq.belloche1) and [\[eq.belloche2\]](#eq.belloche2) (see Section [1](#sec.int)) into the large gas-grain model MAGICKAL" (Linking observations and laboratory data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(CH3NCO) source B | 3e15 (Tex=300 K); 4e15 (Tex=100 K) | ~30% | cm^-2 | 1 | the CH$_{3}$NCO column density is found to be about 3 $\times$ 10$^{15}$ cm$^{-2}$ and 4 $\times$ 10$^{15}$ cm$^{-2}$ for $T_{\rm ex}$ = 300 and 100 K, respectively. |
| N(CH3NCO) source A | 6e15 (300 K); 9e15 (100 K) | ~30% | cm^-2 | 1 | A column density of $\sim$ 6 $\times$ 10$^{15}$ cm$^{-2}$ and $\sim$ 9 $\times$ 10$^{15}$ cm$^{-2}$ (assuming a source size of 0.5$\ensuremath{''}$) |
| N(HNCO) source B | 3.7e16 | within 30% | cm^-2 | 2 | obtained a HNCO column density of 3.7 $\times$ 10$^{16}$ cm$^{-2}$ |
| HNCO/CH3NCO source B | 12 | less than a factor 2 | dimensionless | 2 | The resulting HNCO/CH$_3$NCO abundance ratio is about 12 toward source B with an uncertainty of less than a factor 2. |
| HNCO/CH3NCO source A | 4 | factor of 3 | dimensionless | 2 | The corresponding HNCO/CH$_3$NCO ratio is consequently about 4 toward this component, with a somewhat larger uncertainty of a factor of 3 |
| HOCN upper limit source B | <3e13 (3 sigma) | not stated | cm^-2 | 2 | a $3\sigma$ upper limit of 3 $\times$ 10$^{13}$ cm$^{-2}$ is derived toward source B |
| Lab N(HNCO)/N(CH3NCO) | 100-200 | not stated | dimensionless | 3 | A ratio of $N$(HNCO)/$N$(CH$_{3}$NCO) = 100 – 200 is found |
| CH3NCO TPD desorption peak | 145 | not stated | K | 3 | show the combined release of the primary and secondary masses of methyl isocyanate $m$=57 and 56 at 145 K |

## Qualitative findings

- CH3NCO emission is compact (~60 AU radius) with little difference between A and B  
  > "the emission is quite compact with a size of $\sim$60 AU radius and centred near the two sources" (2.2 Results)

## Claim tuples

- H: CH3NCO is present in a low-mass protostar | E: Line search in PILS data toward A and B | R: 43 unblended lines toward B, 11 toward A; N ~3-9e15 cm-2 | F: First detection toward a low-mass protostar, both components | **supported**
- H: Gas-phase HOCN route is significant | E: HOCN search | R: No HOCN, N(HOCN)/N(HNCO) > 1000 | F: HOCN route insignificant | **supported**
- H: CH3NCO forms in ices through CH3 + HNCO | E: VUV irradiation of CH4:HNCO at 20 K with RAIRS and TPD | R: New IR features near 2300 cm-1 shifting with 13C and m/z 57/56 desorption at 145 K | F: Solid-state formation plausible | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Isomers CH3CNO and CH3OCN not detected  
  > "the corresponding transitions were not found in the PILS data set" (2.2 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): Pure CH3NCO could not be used for lab calibration due to toxicity; m/z 57/56 ratio differs from NIST  
  > "methyl isocyanate is severely toxic and specialised laboratories and equipment are needed to work with this substance." (3.1 Set-up and method)
- Limitation (authors): Data insensitive to cold CH3NCO since low Eup lines are missing  
  > "Our data are not sensitive to any cold CH$_3$NCO component since lines with low $E_{\rm up}$ values are missing in the spectral range of the PILS survey." (2.2 Results)
- Caveat (inferred, ours): Tex not constrained (100 vs 300 K both fit)
- Caveat (inferred, ours): Lab and astronomical ratios differ by an order of magnitude
- Caveat (inferred, ours): Band strength assumption for CH3NCO is uncertain
- Caveat (inferred, ours): Source A line blending

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: PILS reduction details are in Jørgensen et al. 2016
- Missing: CASSIS model settings
- Missing: CH3OH and CH3CN columns from unpublished work
- Data volume (inferred): Several hundred GB (PILS full-band 12m+ACA data)
- Score (inferred): 3/5, The ALMA data are PILS-based with a stated project code, but the calibration and imaging are inherited and the LTE fit settings are sparse.
- Rediscovery candidate: no, The reduction recipe is inherited from another paper and the fitting details are incomplete; lab work is not reproducible from archive data.

## Links

- Method: (cite: jorgensen2016) (PILS survey description and data reduction)
- Companion: (cite: coutens2016) (PILS HNCO and formamide analysis)
- Companion: (cite: lykke2017) (PILS acetone, propanal and ethylene oxide)
- Companion: (cite: martin-domenech2017) (Independent detection toward source B)
- Related: PILS (Protostellar Interferometric Line Survey)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
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
  "facts": 72,
  "stated": 33,
  "rate": 0.458
 },
 "evidence_ok": true
}
```
