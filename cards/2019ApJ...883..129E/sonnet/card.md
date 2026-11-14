# Interstellar Glycolaldehyde, Methyl Formate, and Acetic Acid. I. A Bimodal Abundance Pattern in Star-forming Regions

`2019ApJ...883..129E` | The Astrophysical Journal 2019 | first author: El-Abd, Samer J. | arXiv: 1907.13551 | DOI: 10.3847/1538-4357/ab3646

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: How do the relative column densities of methyl formate, glycolaldehyde and acetic acid vary across NGC 6334I MM1/MM2 and 13 other star-forming regions from the literature?  
  > "The relative column densities of the structural isomers methyl formate, glycolaldehyde, and acetic acid are derived for a dozen positions towards the massive star-forming regions MM1 and MM2 in the NGC 6334I complex" (abstract)
- Target **NGC 6334I (MM1, MM2)**: coordinates 17:20:53.36, -35:47:00.0 (J2000, pointing center)  
  > "The observations were centered at $\alpha$(J2000) = 17:20:53.36, $\delta$(J2000) = -35:47:00.0" (Observations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.A.00022.T
- bands: _not stated_
- frequencies and spectral setup: two tunings, 4 spws each, 1.87 GHz per window; centered 280.1, 282.0, 292.1, 294.0 and 337.1, 339.0, 349.1, 351.0 GHz; 1.1 km/s resolution  
  > "The observations consisted of two tunings, each with four spectral windows, with a bandwidth of 1.87 GHz per window." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.24''x0.17'' (-83 deg) nominal  
  > "had a nominal resolution of $0.24''\times 0.17''$ ($-83^\circ$)" (Observations)
- max recoverable scale: _not stated_
- sensitivity: 2.0 mJy/beam (0.62 K) rms per channel  
  > "a rms per channel of 2.0 mJy beam$^{-1}$ (0.62 K)" (Observations)
- time on source: _not stated_
- observing dates: Cycle 3, 2016  
  > "The ALMA data toward NGC 6334I were observed during Cycle 3 in 2016" (Observations)
- pi or archival as stated: _not stated_
- External data: Column densities of methyl formate, glycolaldehyde, acetic acid for 13 other star-forming regions  
  > "Values for the column densities of methyl formate, acetic acid, and glycolaldehyde in the literature are presented here unchanged from the original analysis with few exceptions" (Literature Sources) [from Table refs: Favre:2011fg; Belloche:2013eba; Lykke:2015ig; Remijan:2002tv; Remijan:2003wf; Rivilla:2017vg; Calcutt:2014ug; Fuente:2014je; Jorgensen:2016cq; Lefloch:2017jd; Taquet:2015en]
- External data: Spectroscopic line properties from CDMS and JPL  
  > "The spectral line properties for all of the simulated molecules were obtained from the CDMS (cite: Muller:2005ii) and JPL (cite: Pickett:1998cp) databases" (Methods) [from Muller:2005ii; Pickett:1998cp]

## Processing

### Calibration

- pipeline or manual: ALMA Cycle 4 pipeline  
  > "The data were calibrated using the ALMA Cycle 4 pipeline (CASA 4.7.2)." (Observations)
- casa version: CASA 4.7.2  
  > "The data were calibrated using the ALMA Cycle 4 pipeline (CASA 4.7.2)." (Observations)
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
- continuum subtraction: following Brogan et al. 2018  
  > "Measurement and subtraction of the background continuum from the observations were done following the methods of (cite: Brogan:2018wb)." (Methods)
- line free channels: _not stated_
- primary beam correction: applied to images  
  > "Primary beam corrections were applied to the images" (Observations)
- array combination: _not stated_
- smoothing: cubes smoothed to 0.26''x0.26''  
  > "the cubes were smoothed to a resolution of $0.26''\times 0.26''$ before analysis" (Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Observation/imaging details  
  > "Further details are given in (cite: McGuire:2017gy), (cite: Hunter:2017th), and (cite: Brogan:2018wb)." (Observations) [from McGuire:2017gy; Hunter:2017th; Brogan:2018wb]
- Continuum measurement and subtraction  
  > "Measurement and subtraction of the background continuum from the observations were done following the methods of (cite: Brogan:2018wb)." (Methods) [from Brogan:2018wb]
- Column density formalism  
  > "the column density (cm$^{-2}$) can be determined using the formalisms outlined in (cite: Hollis:2004uh)" (Methods) [from Hollis:2004uh]

### Not stated but needed to reproduce (our reading)

- Line-free channels and continuum fitting details
- Beam efficiency value eta_B used
- Exact imaging parameters (robust, cell size)
- Spectrum extraction aperture/pixel for each position
- Least-squares fitting code and whether Tex, dV, vlsr were fixed
- Distance to NGC 6334I
- Fit details of which lines used per position beyond the example table
- Flux calibrator and flux uncertainty

## Analysis recipe

1. **Extract spectra**: Spectra extracted from 9 positions around MM1 and 3 around MM2  
  > "we extracted spectra from 9 positions around MM1 and 3 positions around MM2" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
2. **By-eye LTE model to identify unblended lines**: Simulated spectra at fixed Tex, dV, vlsr; column density varied until visual match; at least 50 species  
  > "we performed a zeroth-order, by-eye fit to the data for a number of different interstellar molecules by generating simulated spectra at fixed values of $T_{ex}$, $\Delta V$, and $v_{lsr}$." (Methods)
   - software: Splatalogue (CDMS, JPL)
   - assumption: single Tex, LTE  
  > "We assumed a single excitation temperature and that the molecules were in local thermodynamic equilibrium (LTE)." (Methods)
   - fitting: _not stated_
   - validation: Tex checked with optically thick lines via Turner 1991 formalism  
  > "To verify the accuracy of the assumed $T_{ex}$, we use the formalism of (cite: Turner:1991um)" (Methods)
3. **Fit column densities of three isomers**: Least-squares optimization of column densities using unblended, optically thin lines  
  > "a least-squares optimization of the column densities of methyl formate, glycolaldehyde, and acetic acid was performed using only those lines that were identified as likely unblended" (Methods)
   - assumption: all molecules in beam share same Tex; molecules co-spatial  
  > "This analysis assumes that all molecules within the $0.26''\times 0.26''$ beam share the same value of $T_{ex}$" (Methods)
   - fitting: _not stated_
   - validation: _not stated_
4. **Compare MF/GA and MF/AA with literature sample**: Compile literature column densities, plot MF vs GA and AA, classify MF/GA as small or large  
  > "we plotted the column density of methyl formate as a function of the acetic acid and glycolaldehyde column densities." (Results & Discussion)
   - assumption: 30% uncertainty when literature gave none  
  > "When they were not, a 30% uncertainty was assumed." (Literature Sources)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2: pipeline calibration  
  > "The data were calibrated using the ALMA Cycle 4 pipeline (CASA 4.7.2)." (Observations)
- **Astropy** : acknowledged use  
  > "Astropy, a community-developed core Python package for Astronomy" (Acknowledgments)
- **APLpy** : plotting  
  > "APLpy, an open-source plotting package for Python" (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex range in MM1 | 135-285 | not stated | K | 2 | Excitation temperatures in MM1, for instance, were found to vary between 135-285 K |
| Tex range in MM2 | 152-200 | not stated | K | 2 | the excitation temperatures in MM2 varied from 152-200 K |
| MM1-i methyl formate column density | 1.7e18 | 0.3e18 | cm^-2 | 3 | NGC 6334I MM1-i / $1.7 (3) \times 10^{18}$ / $1.2 (3) \times 10^{17}$ |
| MM1-i MF/GA | 15 | 5 | dimensionless | 3 | NGC 6334I MM1-i |
| MM2-i MF/GA | >=158.3 | not stated | dimensionless | 3 | NGC 6334I MM2-i |

## Qualitative findings

- MF and acetic acid column densities correlate; MF vs glycolaldehyde is bimodal  
  > "there is a clear bi-modal distribution in the glycolaldehyde column densities" (Results & Discussion)

## Claim tuples

- H: Do isomer relative abundances show a single trend across sources? | E: Compare MF vs GA and AA column densities for 15 regions | R: MF-AA single trend; MF-GA two groups (small and large MF/GA) | F: Another parameter besides mass affects glycolaldehyde formation | **supported**
- H: Do MM1 and MM2 share the same MF/GA trend? | E: Spectra at 12 positions | R: MM1 small, MM2 large MF/GA, across all positions | F: Chemical differentiation despite ~4000 AU separation | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Literature column densities are inhomogeneous, different facilities and resolutions  
  > "the techniques used to measure the column densities are not self-consistent" (Results & Discussion)
- Caveat (inferred, ours): Heterogeneous literature sample with differing beams and methods may produce the bimodality
- Caveat (inferred, ours): No formal statistical test of bimodality
- Caveat (inferred, ours): Single Tex and fixed linewidth per position; optically thick lines poorly modelled
- Caveat (inferred, ours): Many MM2 GA values are upper limits

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Extraction apertures, fit code and beam efficiency
- Missing: Imaging parameters
- Data volume (inferred): ~100-300 GB raw for the 8 spectral windows
- Score (inferred): 4/5, Data project code given but fitting details and extraction specifics are sparse.
- Rediscovery candidate: no, Fitting recipe incomplete (by-eye selections, unstated extraction details).

## Links

- Method: Hollis:2004uh (column density formalism)
- Method: Turner:1991um (Tex verification formalism)
- Companion: Brogan:2018wb (data and continuum methods)
- Companion: McGuire:2017gy (observation details)

## Checks

```json
{
 "quotes": 38,
 "quotes_ok": 38,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 29,
  "rate": 0.426
 },
 "evidence_ok": true
}
```
