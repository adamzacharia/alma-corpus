# Rotational spectrum of methoxyamine up to 480 GHz: a laboratory study and astronomical search

`2018A&A...609A..24K` | Astronomy and Astrophysics 2018 | first author: Kolesniková, L. | arXiv: - | DOI: 10.1051/0004-6361/201730744

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: astrochemistry, star_formation
- Question: Provide laboratory rotational frequencies of methoxyamine (75-480 GHz) and search for it in Orion KL, Sgr B2, B1-b and TMC-1  
  > "The aim of this work is to provide direct experimental frequencies of its ground-vibrational state in the millimeterand submillimeter-wave regions to achieve its detection in the interstellar medium." (abstract)
- Target **Orion KL**: coordinates ALMA SV hot core: 05h35m14.5s, -05d22m32.5s (Table 2)  
  > "Orion KL (Turner 1991; Motiyenko et al. 2012; Cernicharo et al. 2016), the nearest hot core at 414 ± 7 pc (Menten et al. 2007)." (4. Radioastronomical observations); z/distance 414 ± 7 pc  
  > "Orion KL (Turner 1991; Motiyenko et al. 2012; Cernicharo et al. 2016), the nearest hot core at 414 ± 7 pc (Menten et al. 2007)." (4. Radioastronomical observations); distance from Menten et al. 2007  
  > "Orion KL (Turner 1991; Motiyenko et al. 2012; Cernicharo et al. 2016), the nearest hot core at 414 ± 7 pc (Menten et al. 2007)." (4. Radioastronomical observations)

## Data provenance

- ALMA projects: 2011.0.00009.SV
- bands: _not stated_
- frequencies and spectral setup: 213.7-246.6 GHz (ALMA SV)  
  > "ALMA Science Verification (SV) data that cover frequencies between 213.7 and 246.6 GHz." (4. Radioastronomical observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~1.9 x 1.4 arcsec synthetic beam  
  > "∼1.9 × 1.4" (Table 2)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **IRAM 30 m**: Orion KL survey 80-306 GHz; Sgr B2 3 mm data; B1-b and TMC-1 data  
  > "we explored the wide frequency band (80−306 GHz) of the IRAM 30 m survey of Orion KL" (4. Radioastronomical observations)
- Other facility **GBT PRIMOS**: Sgr B2 survey 7-50 GHz  
  > "We did not find this species above the detection limit of the data, either in the PRIMOS survey" (4. Radioastronomical observations)
- External data: Physical parameters for formamide in Sgr B2(N) adopted for the upper limit  
  > "we adopted the physical parameters derived by Belloche et al. (2013) for formamide (see Table 2)." (4. Radioastronomical observations) [from Belloche et al. 2013]
- External data: Orion KL source-averaged N(H2) = 4.2e23 cm-2  
  > "Tercero et al. (2010) obtained a source-averaged N(H2) of 4.2 × 10 [23] cm [−][2] for the hot core of Orion KL" (5. Discussion) [from Tercero et al. 2010]

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

- Positions A and B and physical parameters for Orion KL  
  > "These positions are described in Cernicharo et al. (2016) as positions A and B." (4. Radioastronomical observations) [from Cernicharo et al. (2016)]

### Not stated but needed to reproduce (our reading)

- ALMA SV calibration and imaging details (CASA version, weighting, cell size)
- Detection limit / noise rms of the ALMA SV cubes
- Line list or frequencies used for the methylamine maps
- How upper limits were derived from synthetic spectra

## Analysis recipe

1. **Map methylamine to choose positions**: Maps of CH3NH2 from two unblended lines in ALMA SV band  
  > "we created maps of the spatial distribution of methylamine using two lines that were free of blending that arise in the ALMA SV band" (4. Radioastronomical observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Derive upper limits to column density**: Synthetic spectrum compared with data at Table 2 parameters  
  > "We used MADEX (Cernicharo 2012) to implement the spectroscopy of CH3ONH2 provided in the Col. 4 of Table 1 and to derive the synthetic spectrum" (4. Radioastronomical observations)
   - software: MADEX
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **MADEX** : synthetic spectra and upper limits  
  > "We used MADEX (Cernicharo 2012) to implement the spectroscopy of CH3ONH2" (4. Radioastronomical observations)
- **SPFIT/SPCAT** : fits of A and E species  
  > "A and E transitions were analyzed separately using the SPFIT/SPCAT programs (Pickett 1991)." (3. Rotational spectra analysis)
- **ERHAM** : global A+E fit  
  > "another fit using the ERHAM program (Groner 1997), which allows proper weighting of blended transitions, was performed" (3. Rotational spectra analysis)
- **XIAM** : barrier V3 fit  
  > "fitted using the XIAM program (Hartwig & Dreizler 1996) in order to obtain the barrier to the internal rotation V3" (3. Rotational spectra analysis)
- **Gaussian09** : MP2/aug-cc-pVTZ ab initio calculations  
  > "Supporting ab initio calculations were performed at the beginning of the analysis using the Gaussian09 package" (3. Rotational spectra analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| N(CH3ONH2) upper limit, Orion KL hot core (ALMA SV) | ≤3.0e15 | ±1.0e15 | cm-2 | 2 | ≤(3.0 ± 1.0) |
| Upper limit abundance, Orion KL (IRAM 30 m) | 2e-9 | factor of at least 2 | dimensionless | 2 | We derived an upper limit to the CH3ONH2 abundance of 2 × 10 [−][9] |
| Number of newly assigned lines | >400 | not stated | lines | 0 | Over 400 lines were newly assigned for the most stable conformer of methoxyamine |

## Qualitative findings

- Methoxyamine not detected; upper limits consistent with Garrod et al. 2008 model  
  > "the upper limits to the methoxyamine abundance in these regions agree with the CH3ONH2 abundances derived in chemical models." (6. Conclusion)

## Claim tuples

- H: Methoxyamine is detectable in hot cores | E: Search in ALMA SV, IRAM 30 m, PRIMOS data | R: No lines above detection limit; upper limits derived | F: Not detected, upper limits consistent with chemical models | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Most CH3ONH2 lines are fully blended in the 30 m data  
  > "this is not a strong constraint because most of the CH3ONH2 lines are fully blended with more abundant species in these data." (4. Radioastronomical observations)
- Caveat (inferred, ours): ALMA analysis is minimally described
- Caveat (inferred, ours): Upper limits lack stated noise levels

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA SV reduction details
- Missing: Detection thresholds
- Data volume (inferred): tens of GB
- Score (inferred): 2/5, ALMA part is brief; recipe incomplete.
- Rediscovery candidate: no, ALMA analysis details missing; results are upper limits.

## Links

- Companion: Cernicharo et al. 2016 (ALMA SV Orion KL maps and positions)
- Related: ALMA Science Verification Orion KL
- Related: PRIMOS

## Checks

```json
{
 "quotes": 26,
 "quotes_ok": 26,
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
  "facts": 61,
  "stated": 20,
  "rate": 0.328
 },
 "evidence_ok": true
}
```
