# The complexity of Orion: an ALMA view. II. gGg'-ethylene glycol and acetic acid

`2017A&A...604L...2F` | Astronomy and Astrophysics 2017 | first author: Favre, C. | arXiv: 1707.01741 | DOI: 10.1051/0004-6361/201731327

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Are acetic acid and gGg'-ethylene glycol detected in Orion-KL, how are they distributed, and how do their abundance ratios compare with the low-mass protostar IRAS 16293-2422?  
  > "In this Letter, we focus on acetic acid (CH$_3$COOH) and the gGg$^{\prime}$ conformer of ethylene glycol (gGg$^{\prime}$(CH$_2$OH)$_2$) and report their first detection in Orion-KL." (Introduction)
- Target **Orion-KL**: coordinates phase centers 05h35m14.16s and 05h35m13.477s (J2000)  
  > "The two following phase-tracking centers were used to perform the observations: $\alpha_{J2000}$ = 05$^{h}$35$^{m}$14.16s" (2 Observations and data reduction); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00533.S
- bands: Band 6, ~1.3 mm, Cycle 2  
  > "The observations were carried out at $\sim$1.3mm with ALMA during the Cycle 2." (abstract)
- frequencies and spectral setup: 215.15-252.04 GHz, ~16 GHz effective bandwidth, ~0.7 km/s resolution  
  > "The observations lie in the frequency range 215.15 GHz to 252.04 GHz in band 6 and cover about 16 GHz of effective bandwidth with spectral resolution of about 0.7 km s$^{-1}$." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 1.8'' x 1.1'' (P.A. 84 deg)  
  > "The resulting synthesized beam is typically 1.8$\ensuremath{''}$ $\times$ 1.1$\ensuremath{''}$ (P.A. of 84$\ensuremath{^\circ}$)." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2014 Dec 29 (37 antennas) and Dec 30 (39 antennas)  
  > "were observed with 37 antennas on 2014 December 29 and 39 antennas on 2014 December 30." (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CH3COOH 15 transitions, Eup 70-318 K (5 unblended) (not stated)
- Line: aGg'(CH2OH)2 50 transitions, Eup 111-266 K (19 unblended) (not stated)
- Line: gGg'(CH2OH)2 22 transitions, Eup 102-216 K (5 unblended) (not stated)
- External data: Acetic acid spectroscopy (Ilyushin et al.)  
  > "We used the spectroscopic data parameters from (cite: Ilyushin:2008) and (cite: Ilyushin:2013) for acetic acid" (3.1) [from (cite: Ilyushin:2008); (cite: Ilyushin:2013)]
- External data: Ethylene glycol spectroscopy from CDMS  
  > "we used the spectroscopic data parameters from (cite: Christen:2003) and (cite: Muller:2004) that are available from the Cologne Database for Molecular Spectroscopy catalog" (3.1) [from (cite: Christen:2003); (cite: Muller:2004); (cite: Muller:2005)]
- External data: Acetic acid partition function  
  > "we adopt the complete rotational-torsional-vibrational partition function given by Calcutt, Woods, Carvajal et al. (to be submitted to MNRAS)." (3.1) [from Calcutt, Woods, Carvajal et al. (to be submitted)]
- External data: IRAS 16293-2422 abundance ratios for comparison  
  > "along with the ones derived towards the low-mass protostar IRAS 16293–2422 by (cite: Jorgensen:2016)" (4 Discussion) [from (cite: Jorgensen:2016)]
- External data: HC3N molecular ring map overlaid  
  > "show the HC$_3$N ring-like structure emission (cite: Wright:2017)" (Appendix HC3N) [from (cite: Wright:2017)]

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
- deconvolver: line cleaning with GILDAS  
  > "The cleaning of the spectral lines was performed using the GILDAS software" (2 Observations and data reduction)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: performed in CASA  
  > "Data reduction and continuum subtraction were performed through the Common Astronomy Software Applications (CASA) software (cite: McMullin:2007)." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.8'' x 1.1'', P.A. 84 deg  
  > "The resulting synthesized beam is typically 1.8$\ensuremath{''}$ $\times$ 1.1$\ensuremath{''}$ (P.A. of 84$\ensuremath{^\circ}$)." (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Observations, data reduction and other-species model emission  
  > "For further details, see Paper I." (2 Observations and data reduction) [from Paper I (cite: Pagani:2017)]
- Initial LTE model parameters for aGg' ethylene glycol  
  > "We used the values derived for aGg$^{\prime}$(CH$_2$OH)$_2$ by BD15 as input parameter to initialize our models." (3.2 LTE Modeling) [from BD15 (Brouillet et al. 2015)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Weighting, robust, cell size, image size, masks
- Line-free channels for continuum subtraction
- Extraction region/pixel for EGP spectra
- Model emission of other species from Paper I
- Rest frequencies used for line integration maps and velocity ranges
- Rotational temperature was fixed (140 K) without stated fitting procedure

## Analysis recipe

1. **Select spectroscopic lines**: Choose transitions by Aij and Eup limits from catalogs  
  > "Einstein spontaneous emission coefficient A$_\mathrm{ij}$ $\ge$ 5$\times$10$^{-5}$ s$^{-1}$ and upper level energy E$_\mathrm{up}$ $\le$ 400 K." (3.1)
   - software: CDMS
   - parameter: Ethylene glycol: Eup up to ~400 K, Aij >= 1e-4 s-1  
  > "we searched for transitions up to E$_\mathrm{up}$ $\simeq$ 400 K, and A$_\mathrm{ij}$ $\ge$ 1$\times$10$^{-4}$ s$^{-1}$." (3.1)
   - fitting: _not stated_
   - validation: _not stated_
2. **Map integrated emission**: Emission maps integrated over line profile with restricted vLSR interval  
  > "although we use a restricted $v_\mathrm{LSR}$ interval to produce the maps, confusion still dominate the region (Paper I)." (3.3 Emission map)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Contamination by U-line identified in acetic acid map  
  > "the northwest extension seen in the acetic acid emission map is due to contamination by a U-line" (3.3 Emission map)
3. **LTE modeling of spectra at EGP**: By-eye WEEDS fits with two velocity components, optically thin  
  > "our best "by eye" WEEDS fits together with the sum of the modeled emission from all the other species in the region (Paper I) are also overlaid" (3.4 Spectra)
   - software: WEEDS, CLASS
   - parameter: Source size 3'' for each component  
  > "assuming a source size of 3$\ensuremath{''}$ for each velocity component." (3.5)
   - assumption: LTE, same Trot and source size for all species, optically thin  
  > "we assume that all the species emit at the same rotational temperature within the same source size." (3.2 LTE Modeling)
   - fitting: By-eye fit, uncertainty 30-40%  
  > "In the present analysis we assume an overall uncertainty in the range 30$\%$–40$\%$." (3.4 Spectra)
   - validation: aGg' result consistent with BD15 within uncertainties  
  > "is consistent within the uncertainties ($\sim$30$\%$-40$\%$) with the value reported by BD15." (3.5)
4. **Derive abundance ratios and compare**: Ratios of column densities per velocity component, compared with IRAS 16293-2422  
  > "Table 1 lists the relative abundance ratios for acetic acid and ethylene glycol derived from our best model results" (3.5)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data reduction and continuum subtraction  
  > "Data reduction and continuum subtraction were performed through the Common Astronomy Software Applications (CASA) software" (2)
- **GILDAS** : Cleaning of spectral lines  
  > "The cleaning of the spectral lines was performed using the GILDAS software" (2)
- **WEEDS (CLASS extension)** : LTE modeling of emission  
  > "We use the CLASS extension WEEDS (cite: Maret:2011) to model the acetic acid and ethylene glycol" (3.2 LTE Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3COOH column density, 8 km/s component | 12e15 | 30-40% | cm-2 | 3 | / CH$_3$COOH                   / 7.9             / 2.5                             / 140              / 12                      / 5.1             / 2.3                             / 140              / 3.3                     / |
| CH3COOH column density, 5 km/s component | 3.3e15 | 30-40% | cm-2 | 3 | / CH$_3$COOH                   / 7.9             / 2.5                             / 140              / 12                      / 5.1             / 2.3                             / 140              / 3.3                     / |
| aGg' column densities (8 and 5 km/s) | 6.8e15 and 1.5e15 | 30-40% | cm-2 | 3 | / aGg$^{\prime}$(CH$_2$OH)$_2$ / 7.8             / 2.1                             / 140              / 6.8                     / 5.1             / 2.1                             / 140              / 1.5                     / |
| gGg' column densities (8 and 5 km/s) | 2.7e15 and 0.66e15 | 30-40% | cm-2 | 3 | / gGg$^{\prime}$(CH$_2$OH)$_2$ / 7.8             / 2.1                             / 140              / 2.7                     / 5.1             / 2.1                             / 140              / 0.66                    / |
| Rotational temperature | 140 | not stated | K | 3 | / CH$_3$COOH                   / 7.9             / 2.5                             / 140              / 12                      / 5.1             / 2.3                             / 140              / 3.3                     / |
| CH3COOH/gGg' ratio (8 and 5 km/s) | 4.4 and 5.0 | 40-50% | dimensionless | 4 | / 8 km s$^{-1}$ / 1.8 / 4.4 / 2.5 /; / 5 km s$^{-1}$ / 2.4 / 5.0 / 2.3 / |
| CH3COOH/aGg' ratio (8 and 5 km/s) | 1.8 and 2.4 | 40-50% | dimensionless | 4 | / 8 km s$^{-1}$ / 1.8 / 4.4 / 2.5 / |

## Qualitative findings

- Acetic acid and ethylene glycol peak ~2'' southwest of the hot core, unlike the V-shaped O-bearing species  
  > "that of acetic acid and ethylene glycol mainly peaks at about 2$^{\ensuremath{''}}$ southwest from the hot core region (near sources I and n)." (abstract)

## Claim tuples

- H: Do acetic acid and ethylene glycol trace the same morphology as other O-bearing COMs? | E: Integrated emission maps compared with methyl formate | R: Compact peak ~2'' SW of hot core (EGP) | F: Distribution differs from typical O-bearing species | **supported**
- H: Do CH3COOH:(CH2OH)2 ratios in Orion-KL match the low-mass protostar IRAS 16293-2422? | E: LTE-derived ratios compared with Jorgensen et al. 2016 | R: Ratios larger by over an order of magnitude | F: Orion-KL is overabundant in CH3COOH, requiring an extra mechanism | **supported**
- H: Were the COMs released by a bullet from the explosive event? | E: Comparison with HC3N ring and blue wing line profiles | R: Emission co-spatial with ring; blue-shifted wing | F: Grain-formed species released by impact (best hypothesis) | **partially**

## Reasoning

- Why this data: ALMA resolution and sensitivity needed for weak COM lines  
  > "High resolution and sensitivity, as offered by ALMA, are thus mandatory to search for weak lines associated with COMs." (Introduction)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas-phase formation routes cannot be ruled out  
  > "although gas-phase formation routes cannot be ruled out" (4 Discussion)
- Caveat (inferred, ours): By-eye LTE fits with fixed Trot give no formal uncertainties
- Caveat (inferred, ours): Single 3'' source size assumed; beam dilution and optical depth untested
- Caveat (inferred, ours): Shock/bullet scenario is speculative
- Caveat (inferred, ours): Many lines blended

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Paper I calibration and imaging details
- Missing: Model of other species
- Missing: CASA version and imaging parameters
- Missing: Acetic acid partition function (unpublished)
- Data volume (inferred): ~100s GB
- Score (inferred): 2/5, Data reduction deferred to Paper I; by-eye fits with limited documented settings.
- Rediscovery candidate: no, Recipe incomplete; by-eye fitting and reliance on Paper I.

## Links

- Method: Pagani et al. 2017 (Paper I) (ALMA data and reduction details)
- Method: Brouillet et al. 2015 (BD15) (aGg' ethylene glycol starting parameters)
- Companion: (cite: Pagani:2017) (Paper I: ALMA Cycle 2 data and first results)
- Related: HEXOS Herschel/HIFI survey

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.00533.S"
 ],
 "obscore_codes_not_in_card": [
  "2013.1.00553.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 70,
  "stated": 32,
  "rate": 0.457
 },
 "evidence_ok": true
}
```
