# Spectroscopic study and astronomical detection of doubly <SUP>13</SUP>C-substituted ethyl cyanide

`2016A&A...590A..93M` | Astronomy and Astrophysics 2016 | first author: Margulès, L. | arXiv: 1604.03256 | DOI: 10.1051/0004-6361/201628309

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Can the three doubly 13C-substituted isotopologues of ethyl cyanide be characterised in the laboratory and detected in the EMoCA ALMA spectrum of Sgr B2(N2)?  
  > "We want to determine the spectroscopic parameters of all three doubly $^{13}$C-substituted isotopologues of ethyl cyanide to search for them in our ALMA data." (abstract)
- Target **Sagittarius B2(N2)**: coordinates RA 17h47m19.86s, Dec -28d22m13.4s (J2000)  
  > "at the equatorial position ($\alpha, \delta$)$_{\rm J2000}$ = ($17^{\rm h}47^{\rm m}19.86^{\rm s}, -28^\circ22'13.4''$)" (2.3 Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz survey, spectral resolution 488.3 kHz (1.7 to 1.3 km/s)  
  > "the survey covers the frequency range 84.1 – 114.4 GHz with a spectral resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$)." (2.3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.4'' to 2.1''  
  > "The angular resolution ranges from 1.4$\ensuremath{''}$ to 2.1$\ensuremath{''}$." (2.3 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Lille submillimeter spectrometer**: Laboratory rotational spectra of the three isotopologues, 150-990 GHz  
  > "The measurements in the frequency range under investigation (150$-$990 GHz) were performed using the Lille spectrometer" (2.2 Lille - submillimeter spectra)
- External data: Spectroscopic parameters of parent C2H5CN (to 1.6 THz) used in the parameter table  
  > "together with values for the parent isotopologue from (cite: EtCN_rot_2009)" (3.1 Laboratory spectroscopy) [from (cite: EtCN_rot_2009)]
- External data: Rotational temperatures and column densities of C2H5CN, singly 13C and 15N isotopologues  
  > "Those for C$_2$H$_5$CN, the three singly $^{13}$C-substituted isotopologues, and the $^{15}$N isotopologue were already reported in (cite: Belloche16)." (3.2 Detection toward Sgr B2(N2)) [from (cite: Belloche16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 15% calibration uncertainty per setup (Belloche et al. 2016)  
  > "(cite: Belloche16) estimated a calibration uncertainty of 15% for the individual setups of the EMoCA survey." (3.2 Detection toward Sgr B2(N2))
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

- Observations, reduction and analysis method of the full EMoCA dataset  
  > "A detailed account of the observations, reduction, and analysis method of the full dataset is reported in (cite: Belloche16)." (2.3 Observations) [from (cite: Belloche16)]
- Rotational temperature of 150 K adopted from C2H5CN and singly 13C isotopologues  
  > "the value of 150 K that we adopted based on C$_2$H$_5$CN and the three singly $^{13}$C-substituted isotopologues (cite: Belloche16)" (3.2 Detection toward Sgr B2(N2)) [from (cite: Belloche16)]

### Not stated but needed to reproduce (our reading)

- Calibration, imaging and continuum-subtraction details (all in Belloche et al. 2016)
- LTE modelling software not named
- Full-survey line identification list needed for blending
- Spectroscopic catalog entries needed before the LTE model can be run

## Analysis recipe

1. **Fit laboratory rotational spectra**: Assign transitions and fit with Watson S-reduction, Ir representation  
  > "Predictions of the spectra were carried out with SPCAT (cite: spfit_1991), ASFIT (cite: Kisiel2001) was employed for fitting." (3.1 Laboratory spectroscopy)
   - software: SPCAT, ASFIT
   - fitting: _not stated_
   - validation: _not stated_
2. **Build LTE model and population diagrams of EMoCA spectrum**: Full LTE model for all identified species; population diagrams for rotational temperatures  
  > "we can account for this contamination thanks to our full LTE model that contains all species identified so far." (3.2 Detection toward Sgr B2(N2))
   - parameter: Source size 1.2'', Trot 150 K, linewidth 5.0 km/s, velocity offset -0.8 km/s, Vlsr 74 km/s  
  > "the model assumes a source size of 1.20$\ensuremath{''}$, a rotational temperature of 150 K, a linewidth of 5.0 km s$^{-1}$" (Table 3)
   - assumption: Same source size and temperature as more abundant isotopologues  
  > "Therefore we assume the same source size of 1.2$\ensuremath{''}$ as for the more abundant isotopologues." (3.2 Detection toward Sgr B2(N2))
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SPCAT** : Spectral predictions  
  > "Predictions of the spectra were carried out with SPCAT (cite: spfit_1991)" (3.1 Laboratory spectroscopy)
- **ASFIT** : Fitting laboratory spectra  
  > "ASFIT (cite: Kisiel2001) was employed for fitting." (3.1 Laboratory spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Column density of each doubly 13C isotopologue | 7.6e15 | not larger than ~15% | cm^-2 | 2 | / $^{13}$CH$_3$$^{13}$CH$_2$CN / 8 / 7.6 (15) / 1.38 / 818 / |
| 12C12C/12C13C column density ratio | ~32 | not stated | dimensionless | 2 | imply a $^{12}$C$^{12}$C/$^{12}$C$^{13}$C ratio of $\sim$32 and a $^{12}$C$^{13}$C/$^{13}$C$^{13}$C ratio of $\sim$25 |
| 12C13C/13C13C column density ratio | ~25 | not stated | dimensionless | 2 | imply a $^{12}$C$^{12}$C/$^{12}$C$^{13}$C ratio of $\sim$32 and a $^{12}$C$^{13}$C/$^{13}$C$^{13}$C ratio of $\sim$25 |

## Qualitative findings


## Claim tuples

- H: Doubly 13C ethyl cyanide isotopologues are detectable in EMoCA data | E: Lab spectroscopy then LTE modelling of the ALMA spectrum of Sgr B2(N2) | R: About 8, 7 and 8 clean lines detected for the three species | F: All three are unambiguously detected | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Rotational temperatures of the doubly 13C species are poorly constrained, and uniform source structure assumed  
  > "Their rotational temperatures are thus poorly constrained" (3.2 Detection toward Sgr B2(N2))
- Caveat (inferred, ours): The 32 vs 25 ratio difference may be a modelling bias

## Reproducibility

- Data public (paper): Interferometric data available in the ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging recipe from Belloche et al. 2016
- Missing: LTE modelling code
- Data volume (inferred): Large (full EMoCA survey, hundreds of GB)
- Score (inferred): 2/5, ALMA part inherited from a companion paper; recipe for the LTE modelling is thin.
- Rediscovery candidate: no, ALMA processing and LTE details are not given here.

## Links

- Method: (cite: Belloche16) (EMoCA observations, reduction and LTE analysis method)
- Companion: (cite: Belloche14) (Earlier EMoCA results)
- Related: EMoCA

## Checks

```json
{
 "quotes": 25,
 "quotes_ok": 25,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 59,
  "stated": 18,
  "rate": 0.305
 },
 "evidence_ok": true
}
```
