# Interstellar glycolamide: A comprehensive rotational study and an astronomical search in Sgr B2(N)

`2020A&A...639A.135S` | Astronomy and Astrophysics 2020 | first author: Sanz-Novo, M. | arXiv: 2006.13634 | DOI: 10.1051/0004-6361/202038149

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation, milky_way_ism
- Question: Measure the rotational spectrum of glycolamide in the lab and use it to search for the molecule toward Sgr B2(N2) (ALMA EMoCA) and Sgr B2(N) (Effelsberg), then compare with a chemical model  
  > "the aim of our work is to provide direct experimental frequencies of the ground vibrational state of glycolamide in the centimeter-, millimeter- and submillimeter-wavelength regions in order to enable its identification in the interstellar medium." (abstract)
- Target **Sgr B2(N2)**: coordinates RA 17h47m19.86s, Dec -28d22m13.4s (J2000), per text  
  > "Here we analyze the spectrum at the peak position of Sgr B2(N2) located at" (4.1 Observations); "located in the galactic center region at a distance of 8.2 kpc (Reid et al. 2019)" (1. Introduction); z/distance 8.2 kpc  
  > "Here we analyze the spectrum at the peak position of Sgr B2(N2) located at" (4.1 Observations); "located in the galactic center region at a distance of 8.2 kpc (Reid et al. 2019)" (1. Introduction); distance from Reid et al. 2019  
  > "Here we analyze the spectrum at the peak position of Sgr B2(N2) located at" (4.1 Observations); "located in the galactic center region at a distance of 8.2 kpc (Reid et al. 2019)" (1. Introduction)

## Data provenance

- ALMA projects: 2011.0.00017.S, 2012.1.00012.S
- bands: _not stated_
- frequencies and spectral setup: 84.1-114.4 GHz, spectral resolution 488 kHz (1.7 to 1.3 km/s)  
  > "the survey covers the frequency range from 84.1 GHz to 114.4 GHz with a spectral resolution of 488 kHz (1.7 to 1.3 km s" (4.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: median 1.6"  
  > "a median angular resolution of 1.6" (4.1 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Effelsberg 100 m**: 4-8 and 12-17 GHz spectra toward Sgr B2(N) for glycolamide search  
  > "We performed measurements (project id: 08-20) toward Sgr B2(N) with the S45mm and S20mm receivers of the 100 m radio telescope at Effelsberg" (5.1 Observations)
- External data: Acetamide LTE parameters (size 0.9", T 180 K, linewidth 5 km/s, N=1.4e17) in Sgr B2(N2)  
  > "we assumed the same parameters as those derived by Belloche et al. (2017) for acetamide" (4.2 Nondetection of glycolamide) [from Belloche et al. 2017]
- External data: MAGICKAL warm-up model results originally published  
  > "Selected model results were originally published by Garrod et al. (2017)" (6. Astrochemical modeling) [from Garrod et al. 2017]
- Simulation/model as data: MAGICKAL gas-grain chemical kinetics model, medium-timescale warm-up (8-400 K) for Sgr B2(N2)  
  > "the astrochemical kinetics model MAGICKAL relating to the cold collapse and gradual warm up (8–400 K) of a hot core" (6. Astrochemical modeling)

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

- EMoCA observational setup and data reduction  
  > "A detailed account of the observational setup and data reduction of the EMoCA survey can be found in Belloche et al. (2016)." (4.1 Observations) [from Belloche et al. (2016)]
- Weeds LTE modelling with five parameters per species  
  > "As described in Belloche et al. (2016), the spectrum was modeled with the software Weeds" (4.1 Observations) [from Belloche et al. (2016); Maret et al. 2011]
- Population diagram method with optical depth and contamination correction  
  > "Following the method described in Belloche et al. (2016), we corrected the diagrams for optical depth" (4.3 Comparison to other molecules) [from Belloche et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Calibration details (pipeline/CASA versions, flux calibrator) are only in Belloche et al. 2016
- Exact criteria for the upper limit (how the 2.4e16 cm-2 was chosen beyond visual comparison with 3 sigma)
- Rms noise of EMoCA spectrum at glycolamide frequencies
- Partition function used for glycolamide in the LTE model

## Analysis recipe

1. **Fit laboratory rotational spectrum**: Least-squares fit of Watson A-reduced Hamiltonian plus quadrupole term to measured lines  
  > "The fits and predictions were made in terms of Watson’s A-reduced Hamiltonian in I r -representation with the Pickett’s SPFIT/SPCAT program suite (Pickett 1991)." (3.2 Millimeter and submillimeter wave spectra)
   - software: SPFIT/SPCAT
   - fitting: _not stated_
   - validation: _not stated_
2. **Model glycolamide upper limit toward Sgr B2(N2)**: LTE synthetic spectrum with acetamide parameters, column density adjusted until not exceeding the ALMA spectrum  
  > "The red spectrum shown in Fig. 4 was computed with a glycolamide column density of 2.4 × 10 16 cm −2 (see Table 5)." (4.2 Nondetection of glycolamide)
   - software: Weeds
   - parameter: size 0.9", T 180 K, linewidth 5 km/s, Voff 0  
  > "an emission size of 0.9 [JJ], a temperature of 180 K, a linewidth of 5 km s [−] [1], and no velocity o ff set with respect to the systemic velocity" (4.2 Nondetection of glycolamide)
   - assumption: LTE; Vsys = 74 km/s  
  > "velocity offset with respect to the assumed systemic velocity of the source (74 km s" (4.1 Observations)
   - fitting: _not stated_
   - validation: Compared to 3 sigma noise level; lines at 103875 MHz leave no room  
  > "there is no room left for glycolamide emission at 103875 MHz" (4.2 Nondetection of glycolamide)
3. **Derive comparison molecules' column densities**: Population diagrams and LTE fits for acetaldehyde and glycolaldehyde  
  > "A fit to the corrected population diagrams yields temperatures of 166 ± 17 K and 164 ± 6 K for acetaldehyde and glycolaldehyde, respectively" (4.3 Comparison to other molecules)
   - software: Weeds
   - assumption: 12C/13C = 20-25  
  > "assuming a 12 C/ 13 C isotopic ratio in the range 20–25" (4.3 Comparison to other molecules)
   - fitting: _not stated_
   - validation: _not stated_
4. **Effelsberg upper limit**: Baseline subtraction (5th order) and Weeds synthetic spectra, beam filling 1, Trot 8 K, FWHM 10 km/s, Vsys 64 km/s  
  > "we obtained a column density upper limit of 1.2 × 10 14 cm −2 for glycolamide at the 4–5σ level for extended emission" (5.2 Nondetection of glycolamide)
   - software: Weeds, GILDAS/CLASS
   - assumption: Trot 8 K as in Hollis et al. 2006  
  > "a systemic velocity of 64 km s −1 and a rotational temperature of 8 K" (5.2 Nondetection of glycolamide)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **SPFIT/SPCAT** : Spectroscopic fits and predictions, partition functions  
  > "with the Pickett’s SPFIT/SPCAT program suite (Pickett 1991)" (3.2)
- **Weeds** : LTE synthetic spectra  
  > "the spectrum was modeled with the software Weeds" (4.1 Observations)
- **GILDAS/CLASS** : Effelsberg data reduction  
  > "The data reduction was performed using the GILDAS/CLASS software" (5.1 Observations)
- **MAGICKAL** : Gas-grain chemical modelling  
  > "We used the gas-grain chemical kinetics model MAGICKAL to interpret the results of the astronomical observations." (abstract)
- **AABS** : Line frequency measurement in lab spectra  
  > "employing a Gaussian profile function with the AABS package (Kisiel et al. 2005)" (2.3 MMW spectroscopy)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Glycolamide column density upper limit, Sgr B2(N2) | 2.4e16 | not stated | cm-2 | 2 | < 2.4 (16) |
| Glycolamide column density upper limit, Effelsberg | 1.2e14 | not stated | cm-2 | 4 | column density upper limit of 1.2 × 10 14 cm −2 |
| Acetamide/glycolamide ratio | >5.8 | not stated | dimensionless | 3 | [CH 3 C(O)NH 2 ]/[CH 2 (OH)C(O)NH 2 ] > 5.8 |
| Glycolaldehyde/glycolamide ratio | >4.6 | not stated | dimensionless | 3 | [CH 2 (OH)CHO]/[CH 2 (OH)C(O)NH 2 ] > 4.6 |
| Acetaldehyde rotational temperature | 166 | 17 | K | 3 | 166 (17) |
| Glycolaldehyde rotational temperature | 163.8 | 6.1 | K | 3 | 163.8 (6.1) |

## Qualitative findings

- Glycolamide not detected in Sgr B2(N2) or the Sgr B2(N) envelope  
  > "We report the nondetection of glycolamide toward this source" (abstract)

## Claim tuples

- H: Is glycolamide detectable in Sgr B2(N2) with EMoCA? | E: LTE modelling with lab predictions | R: Only one ~5σ matching line; others overpredicted; upper limit 2.4e16 cm-2 | F: Not detected; at least 6x less abundant than acetamide | **supported**
- H: Is glycolamide present in the extended envelope? | E: Effelsberg 4-8 and 12-17 GHz search | R: No lines; N < 1.2e14 cm-2 | F: Non-detection, limit similar to GBT acetamide and glycolaldehyde | **supported**
- H: Does the chemical model explain the observed ratios? | E: MAGICKAL comparison | R: Model glycolamide/glycolaldehyde 0.21 vs observed limit 0.22; glycolamide/acetamide discrepant by ~26 | F: Glycolamide may lie just below the upper limit | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Rotational temperature of 100 K for envelope would raise the limit by factor 43 to 5.3e15 cm-2  
  > "the upper limit based on the cm data would increase by a factor of 43 to 5.3 × 10 15 cm −2" (5.3)
- How they decided it was enough: _not stated_
- Limitation (authors): Envelope limit depends on questionable LTE assumption at 8 K  
  > "the questionable assumption of LTE with a rotation temperature of 8 K" (5.3 Discussion of the Effelsberg nondetection)
- Caveat (inferred, ours): Upper limit relies on acetamide parameters assumed for glycolamide
- Caveat (inferred, ours): No formal statistical definition of the upper limit

## Reproducibility

- Data public (paper): ALMA data in the archive  
  > "The interferometric data are available in the ALMA archive at https://almascience.eso.org/aq/." (Acknowledgements)
- Products in archive: _not stated_
- Missing: EMoCA calibration and imaging details (Belloche et al. 2016)
- Missing: Full Weeds model of all other species in Sgr B2(N2)
- Data volume (inferred): large (full EMoCA survey, hundreds of GB)
- Score (inferred): 3/5, Public ALMA data and clear LTE parameters, but depends on the heavy EMoCA full-source model and earlier papers.
- Rediscovery candidate: no, Result is an upper limit depending on a complete multi-species model not reproducible from this paper alone.

## Links

- Method: Belloche et al. 2016 (cite: Belloche2016) (EMoCA setup, reduction, LTE modelling)
- Companion: Belloche et al. 2017 (Acetamide parameters in Sgr B2(N2))
- Related: EMoCA

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 31,
  "rate": 0.419
 },
 "evidence_ok": true
}
```
