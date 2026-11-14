# Laboratory rotational spectroscopy of isotopic acetone, CH<SUB>3</SUB><SUP>13</SUP>C(O)CH<SUB>3</SUB> and <SUP>13</SUP>CH<SUB>3</SUB>C(O)CH<SUB>3</SUB>, and astronomical search in Sagittarius B2(N2)

`2019A&A...629A..72O` | Astronomy and Astrophysics 2019 | first author: Ordu, Matthias H. | arXiv: 1907.08073 | DOI: 10.1051/0004-6361/201935887

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Measure the rotational spectra of 13C isotopologs of acetone in the laboratory and search for them, and for torsionally excited main-species acetone, in the EMoCA ALMA survey of Sgr B2(N2).  
  > "We want to study the rotational spectra of CH$_3^{13}$C(O)CH$_3$ and $^{13}$CH$_3$C(O)CH$_3$ and search for them in Sagittarius B2(N2)." (abstract)
- Target **Sgr B2(N2)**: coordinates J2000 17h47m19.86s, -28d22m13.4s  
  > "In this work we focus on the peak position of the hot molecular core Sgr B2(N2) with J2000 equatorial coordinates ($17^{\rm h}47^{\rm m}19.86^{\rm s}$, $-28^\circ22\ensuremath{'}13.4\ensuremath{''}$)." (4.2 Radioastronomical observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, 488.3 kHz resolution (1.7-1.3 km/s), five tunings S1-S5  
  > "the survey covers the frequency range from 84.1 GHz to 114.4 GHz with a spectral resolution of 488.3 kHz (1.7 to 1.3 km s$^{-1}$). It was performed with five frequency tunings called S1 to S5." (4.2 Radioastronomical observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6 arcsec  
  > "The median angular resolution is 1.6$\ensuremath{''}$." (4.2 Radioastronomical observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Laboratory submillimeter spectrometers (MIDAS-COINS and setup 2)**: Room-temperature absorption spectra 36-910 GHz of acetone isotopologs  
  > "We investigated the laboratory rotational spectrum of isotopically enriched CH$_3^{13}$C(O)CH$_3$ between 40 GHz and 910 GHz and of acetone between 36 GHz and 910 GHz" (abstract)
- External data: Earlier acetone ground-state line list and ERHAM fit  
  > "studied the main isotopolog quite extensively." (4.1.3 The main isotopic species in its ground vibrational state) [from (cite: acetone-12C_groner_2002)]
- External data: FTMW data of 13C acetone isotopologs (10-25 GHz)  
  > "determined 44 transition frequencies of 11 different rotational transitions with $J \le 4$ in the region of 10$-$25 GHz." (4.1.1 CH3 13C(O)CH3 ground state) [from (cite: mono-13C-acetone)]

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

- Observation details, data reduction and line identification/column density method of the EMoCA survey  
  > "Details about the observations, data reduction, and the method used to identify the detected lines and derive column densities can be found in (cite: 2x13C-MeCN_det_2016)." (4.2 Radioastronomical observations) [from (cite: 2x13C-MeCN_det_2016)]

### Not stated but needed to reproduce (our reading)

- Calibration, imaging and rms details of the EMoCA data (only by reference)
- Spectral extraction details (pixel/beam) for Sgr B2(N2)
- Line-by-line catalog files for the new predictions (promised for CDMS)
- Source systemic velocity

## Analysis recipe

1. **Fit laboratory spectra**: Assign lines with AABS and fit an effective Hamiltonian with extended ERHAM, iterating until weighted standard deviation near 1  
  > "we carried out new fits with ERHAM under systematic variations of parameters to reach a weighted standard deviation close to 1.0" (3.2 Spectroscopic analysis)
   - software: AABS, ERHAM
   - fitting: _not stated_
   - validation: Weighted standard deviation of fits; comparison with ALMA spectrum  
  > "to reach a weighted standard deviation close to 1.0, which means that the experimental data were fit within their uncertainties on average." (Spectroscopic analysis)
2. **Model main isotopolog in EMoCA spectrum**: LTE modeling with Weeds with five free parameters, population diagram for temperature  
  > "we proceeded in an iterative way using Weeds (cite: Maret11) under the local thermodynamic equilibrium (LTE) approximation." (4.2.1 CH3C(O)CH3)
   - software: Weeds
   - parameter: Tfit 152 +/- 4 K, adopted 140 K; size 1.2 arcsec; N = 4e17 cm-2  
  > "A fit to this diagram yields a rotational temperature of $152 \pm 4$ K." (4.2.1 CH3C(O)CH3)
   - assumption: LTE  
  > "we proceeded in an iterative way using Weeds (cite: Maret11) under the local thermodynamic equilibrium (LTE) approximation." (CH$_3$C(O)CH$_3$)
   - fitting: Population diagram fit; weighted  
  > "A fit to this diagram yields a rotational temperature of $152 \pm 4$ K." (CH$_3$C(O)CH$_3$)
   - validation: Compared with JPL predictions  
  > "The new spectroscopic predictions produced over the course of this work yield much better agreement with the ALMA spectrum than what could previously be achieved with the predictions available in the JPL catalog" (Radioastronomical observations (Discussion))
3. **Search for 13C isotopologs**: Synthetic spectra with main isotopolog parameters and scaled column density  
  > "We used the parameters derived for the main isotopolog of acetone to search for transitions of the $^{13}$C-substituted isotopologs" (4.2.2 13C isotopologs)
   - software: Weeds
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Weeds** : LTE synthetic spectra of Sgr B2(N2)  
  > "we proceeded in an iterative way using Weeds (cite: Maret11) under the local thermodynamic equilibrium (LTE) approximation." (4.2.1 CH3C(O)CH3)
- **ERHAM** : Modeling rotational spectra  
  > "We employed an extended version of the “Effective Rotational HAMiltonian program for molecules with up to two periodic large-amplitude motions” (ERHAM)" (3.2 Spectroscopic analysis)
- **AABS** : Assigning laboratory spectra  
  > "We used the software package Assignment and Analysis of Broadband Spectra (AABS)" (3.2 Spectroscopic analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Rotational temperature of acetone | 152 | 4 | K | 2 | A fit to this diagram yields a rotational temperature of $152 \pm 4$ K. |
| Acetone column density (v=0) | 4.0e17 | not stated | cm-2 | 2 | CH$_3$C(O)CH$_3$, $\varv=0$$^\star$ / d / 122 / 1.2 / 140 / 4.0 (17) |
| 13CH3C(O)CH3 column density | 3.0e16 | not stated | cm-2 | 3 | computed with a column density of $3.0 \times 10^{16}$ cm$^{-2}$ |
| 12C/13C ratio | 27 | not stated | dimensionless | 3 | this yields a $^{12}$C/$^{13}$C isotopic ratio of 27 for acetone |

## Qualitative findings


## Claim tuples

- H: Is 13CH3C(O)CH3 present in Sgr B2(N2)? | E: Compare synthetic LTE spectrum with EMoCA data | R: One clear line at 110.131 GHz, N = 3.0e16 cm-2 | F: Tentative detection with 12C/13C of 27 | **partially**
- H: Do the new predictions improve agreement with ALMA? | E: Compare with JPL predictions | R: Discrepancies disappear | F: New ground-state predictions more reliable at 3 mm | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Torsionally excited state models only marginally improved; 13CH3 species needs enriched sample  
  > "We find that models of the torsionally excited states $\varv _{12} = 1$ and $\varv _{17} = 1$ of CH$_3$C(O)CH$_3$ improve only marginally." (abstract)
- Caveat (inferred, ours): Tentative detection rests on one clean line
- Caveat (inferred, ours): Temperature uncertainty likely underestimated

## Reproducibility

- Data public (paper): Interferometric data in ALMA archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: EMoCA reduction details
- Missing: Released line lists (CDMS)
- Data volume (inferred): Large (EMoCA survey, hundreds of GB)
- Score (inferred): 3/5, Lab part is thorough, ALMA part relies on a previous paper.
- Rediscovery candidate: no, ALMA recipe is inherited and the main result is mostly laboratory.

## Links

- Method: (cite: 2x13C-MeCN_det_2016) (EMoCA data reduction and analysis method)
- Related: EMoCA

## Checks

```json
{
 "quotes": 30,
 "quotes_ok": 30,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 62,
  "stated": 21,
  "rate": 0.339
 },
 "evidence_ok": true
}
```
