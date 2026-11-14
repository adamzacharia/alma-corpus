# Revised spectroscopic parameters of SH<SUP>+</SUP> from ALMA and IRAM 30 m observations

`2014A&A...569L...5M` | Astronomy and Astrophysics 2014 | first author: Müller, Holger S. P. | arXiv: 1409.1807 | DOI: 10.1051/0004-6361/201424756

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, milky_way_ism
- Question: Are the SH+ N_J=1_0-0_1 lines near 346 GHz at the previously reported frequencies, and what are the correct line frequencies and spectroscopic parameters?  
  > "We show that the previously reported SH$^+$ $N_J=1_0-0_1$ line frequencies at $\sim$346 GHz are not correct and use the frequencies derived from our observations to compute improved SH$^+$ spectroscopic parameters and line frequencies." (Introduction)
- Target **Orion Bar dissociation front (CO+ peak)**: coordinates IRAM: 05h35m20.8s, -05d25'17.0" (J2000); ALMA mosaic center 05h35m20.6s, -05d25'20.0"  
  > "The target position is at $\mathrm{\alpha_{2000}=05^{h}\,35^{m}\,20.8^{s}\,}$, $\mathrm{\delta_{2000}=-\,05^{\circ}25'17.0''}$, close to the so-called CO$^{+}$ peak (cite: Sto95)." (2.1 Single-dish IRAM 30 m observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2012.1.00352.S
- bands: Band 7 (~346 GHz)  
  > "Observations were carried out with the band 7 receiver near 346 GHz" (2.2 Interferometric ALMA and ACA observations)
- frequencies and spectral setup: 488.3 kHz (~0.4 km/s) resolution, 937.5 MHz total bandwidth  
  > "at a spectral resolution of 488.3 kHz ($\sim$0.4 km s$^{-1}$) over a total bandwidth of 937.5 MHz" (2.2 Interferometric ALMA and ACA observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m (27 antennas) plus ACA (nine 7 m antennas)  
  > "The ALMA array observations used twenty-seven 12 m antennas." (2.2 Interferometric ALMA and ACA observations)
- configurations: C32-2; 27-pointing mosaic (ALMA), 10-pointing mosaic (ACA)  
  > "The field of view was observed as a mosaic of 27 Nyquist-sampled pointings in the C32-2 configuration" (2.2 Interferometric ALMA and ACA observations)
- baselines: _not stated_
- angular resolution: ~1" (ALMA), ~3.6" (ACA)  
  > "The ACA mosaic contained ten pointings Nyquist-sampled fields and provided a typical resolution of $\sim$3.6$''$." (2.2 Interferometric ALMA and ACA observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: about 6.5 h (ACA) and 2.2 h (ALMA)  
  > "The total observing time was about 6.5 h and 2.2 h for ACA and ALMA observations respectively." (2.2 Interferometric ALMA and ACA observations)
- observing dates: 2013 and 2014, Cycle 1  
  > "observations of the Orion Bar were carried out in 2013 and 2014 during ALMA *Cycle 1* observations" (2.2 Interferometric ALMA and ACA observations)
- pi or archival as stated: Project 2012.1.00352.S, PI J.R. Goicoechea  
  > "They belong to the 2012.1.00352.S project “The fundamental structure of molecular cloud edges: from clumps to photoevaporation” (P.I.: J.R. Goicoechea)." (2.2 Interferometric ALMA and ACA observations)
- Line: SH+ N_J=1_2-0_1 FS component, F=1.5-0.5 and 0.5-0.5 HFS (searched as 1_0-0_1) (345944.35 MHz and 345858.27 MHz (derived))
- Other facility **IRAM 30 m**: EMIR330/FFTS spectrum of the SH+ lines toward the Orion Bar, 2 h integration  
  > "IRAM 30 m telescope observations were taken in 2013 using the EMIR330 receiver and the FFTS backend" (2.1 Single-dish IRAM 30 m observations)
- External data: Previous laboratory SH+ frequency near 346 GHz and 526 GHz lines  
  > "(cite: Sav04) employed source- and velocity-modulation to determine accurate rest frequencies of all three HFS components near 526 GHz" (4 New SH+ spectroscopic parameters) [from Savage et al. 2004 (cite: Sav04)]
- External data: LMR rotational data, extrapolated to zero field, and rovibrational data used in the fit  
  > "The LMR transition frequencies extrapolated to zero field by (cite: SH+\_parameters_2009) were fit together with the field-free rotational data (cite: Sav04)" (4 New SH+ spectroscopic parameters) [from (cite: SH+\_parameters_2009); (cite: SH+\_LMR_1987); (cite: SH+\_IR_1986); (cite: SH+\_IR_1989)]

## Processing

### Calibration

- pipeline or manual: CASA, standard algorithms  
  > "The data were calibrated within the CASA software package using the standard algorithms." (2.2 Interferometric ALMA and ACA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: Exported calibrated uv tables to GILDAS; ACA and ALMA deconvolved separately  
  > "The calibrated uv tables were then exported to GILDAS[^3], where the data were deconvolved using the Högbom CLEAN algorithm." (2.2 Interferometric ALMA and ACA observations)
- deconvolver: Högbom CLEAN  
  > "the data were deconvolved using the Högbom CLEAN algorithm" (2.2 Interferometric ALMA and ACA observations)
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

- Full ALMA data reduction and data set to be presented elsewhere  
  > "All technical details on the data reduction and the complete data set will be presented elsewhere." (2.2 Interferometric ALMA and ACA observations) [from not stated]
- IRAM 30 m Orion Bar line survey  
  > "They are part of a complete millimeter line survey toward the Orion Bar dissociation front (cite: Cua14)" (2.1 Single-dish IRAM 30 m observations) [from (cite: Cua14)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibrators
- Weighting, cell size, image size, CLEAN threshold and masks
- Spectral extraction region for ACA/ALMA spectra
- Baseline order for IRAM subtraction
- Line-fit procedure details beyond Gaussians
- Full list of lab lines and weights used in the Dunham fit

## Analysis recipe

1. **Detect lines and measure frequencies**: Gaussian fits to the two emission lines in IRAM 30 m, ACA and ALMA spectra; average of three; 0.2 MHz systematic uncertainty added  
  > "Table [\[table:1\]](#table:1) shows results from Gaussian fits to the two lines, which were detected with up to 12 $\sigma$ and 7 $\sigma$ significance levels." (3 Observational results)
   - software: GILDAS
   - parameter: v_LSR = 10.50 km/s from HCO+ J=4-3  
  > "using a local standard of rest velocity (v$_{\rm LSR}$) of 10.50 km s$^{-1}$" (3 Observational results)
   - fitting: _not stated_
   - validation: Same lines in three independent instruments, 1:2 intensity ratio and spacing  
  > "the two emission lines, each observed $\sim$15 MHz higher, had the expected 1 : 2 intensity ratio and spacing" (4 New SH+ spectroscopic parameters)
2. **Refit SH+ spectroscopic parameters**: Dunham-type fit with SPFIT of lab, rovibrational and new astronomical frequencies, replacing the 346 GHz lab line  
  > "Hence, we used averages over the three independent observations given in section [3](#obs-res) to redetermine the SH$^+$ spectroscopic parameters." (4 New SH+ spectroscopic parameters)
   - software: SPFIT
   - fitting: Least squares; Y03 fixed to Brown & Müller value  
  > "Kept fixed to the value derived by (cite: SH+\_parameters_2009)." (Table 1)
   - validation: Fit rms error improved from 0.898 to 0.826 when omitting the lab line; final 0.820  
  > "The rms error of this fit is 0.820, demonstrating that our transition frequencies are more compatible" (4 New SH+ spectroscopic parameters)

## Software

- **CASA** : Calibration of ALMA/ACA data  
  > "The data were calibrated within the CASA software package using the standard algorithms." (2.2 Interferometric ALMA and ACA observations)
- **GILDAS** : Deconvolution of ALMA and ACA visibilities  
  > "where the data were deconvolved using the Högbom CLEAN algorithm" (2.2 Interferometric ALMA and ACA observations)
- **SPFIT** : Spectroscopic parameter fitting  
  > "because the SPFIT program (cite: spfit_1991) does not permit the use of field-dependent data" (4 New SH+ spectroscopic parameters)
- **MADEX** : HCO+ line frequencies and line catalog checks  
  > "were used to compute HCO$^+$ line frequencies with MADEX (cite: Cer12)" (Footnote 4)
- **ATM** : Atmospheric calibration of IRAM 30 m data  
  > "Atmospheric calibration of the IRAM 30 m data was carried out with the ATM program (cite: Pardo01)." (2.1 Single-dish IRAM 30 m observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| SH+ line rest frequency (F=1.5-0.5) | 345944.35 | 0.2 MHz (systematic) | MHz | 1 | we obtain 345944.35 MHz and 345858.27 MHz for the two lines |
| SH+ line rest frequency (F=0.5-0.5) | 345858.27 | 0.2 MHz (systematic) | MHz | 1 | we obtain 345944.35 MHz and 345858.27 MHz for the two lines |
| Fit rms error with new data | 0.820 | not stated | dimensionless | 2 | The rms error of this fit is 0.820 |

## Qualitative findings

- The 345929.8 MHz lab line is not SH+; the lines near 345944 and 345858 MHz arise from the Orion Bar edge.  
  > "Here we demonstrate that the 345929.8 MHz line is not SH$^+$" (4 New SH+ spectroscopic parameters)

## Claim tuples

- H: The lab SH+ 346 GHz frequencies are correct | E: Search Orion Bar with IRAM 30 m, ACA and ALMA at the lab frequencies | R: No emission at lab frequencies; two lines ~15 MHz higher with 1:2 ratio in all three | F: Previous 346 GHz frequencies are incorrect; new lines are SH+ | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Lines checked against other carriers in MADEX, CDMS and JPL catalogs; none found  
  > "which could not be assigned to other carriers in the MADEX, CDMS (cite: CDMS_2001; CDMS_2005), and JPL (cite: JPL-catalog_1998) spectroscopic catalogs" (3 Observational results)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainty in v_LSR due to complex Orion kinematics  
  > "Given the complex gas kinematics in Orion, implying an uncertainty in v$_{\rm LSR}$, we adopted a 1 $\sigma$ systematic uncertainty of 0.2 MHz" (3 Observational results)
- Caveat (inferred, ours): Lab confirmation is lacking; assignment rests on astronomical lines
- Caveat (inferred, ours): Blend possibility near CO 3-2 not tested quantitatively

## Reproducibility

- Data public (paper): ALMA project code given; public status not stated  
  > "They belong to the 2012.1.00352.S project “The fundamental structure of molecular cloud edges: from clumps to photoevaporation” (P.I.: J.R. Goicoechea)." (Interferometric ALMA and ACA observations)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Spectral extraction region
- Missing: Complete laboratory line list for the fit
- Data volume (inferred): ~10-50 GB for ALMA+ACA band 7 mosaics
- Score (inferred): 3/5, Frequency measurement is simple but ALMA processing is sparsely documented and the fit needs external lab data.
- Rediscovery candidate: no, Processing details are incomplete and the main result relies on a spectroscopic fit with external laboratory data.

## Links

- Companion: Cuadrado et al. 2014 (cite: Cua14) (Orion Bar IRAM 30 m line survey)

## Checks

```json
{
 "quotes": 40,
 "quotes_ok": 40,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 33,
  "rate": 0.524
 },
 "evidence_ok": true
}
```
