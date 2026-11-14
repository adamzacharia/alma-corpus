# Molecular analysis of a high-mass prestellar core candidate in W43-MM1

`2019A&A...626A.132M` | Astronomy and Astrophysics 2019 | first author: Molet, J. | arXiv: 1905.12463 | DOI: 10.1051/0004-6361/201935497

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the chemical composition and temperature of the high-mass prestellar core candidate W43-MM1 core #6, compared with the protostellar core #3 and other sources?  
  > "We aim to characterise the chemistry in this high-mass prestellar core candidate, referred to as W43-MM1 core #6, and its environment." (abstract)
- Target **W43-MM1 core #6**: coordinates RA 18h47m46.16s, Dec -1d54m33.30s (J2000)  
  > "6 18 [h] 47 [m] 46 [s] .16 -1 [◦] 54 [′] 33 [′′] . 30 0.55×0.45 1300 56±9 6.6±0.1 23±2" (Table 2); "located at the end of the Galactic bar at a distance of 5.5 kpc from the Sun (Nguyen Luong et al. 2011; Zhang et al. 2014)" (1. Introduction); z/distance 5.5 kpc  
  > "6 18 [h] 47 [m] 46 [s] .16 -1 [◦] 54 [′] 33 [′′] . 30 0.55×0.45 1300 56±9 6.6±0.1 23±2" (Table 2); "located at the end of the Galactic bar at a distance of 5.5 kpc from the Sun (Nguyen Luong et al. 2011; Zhang et al. 2014)" (1. Introduction); distance from Nguyen Luong et al. 2011; Zhang et al. 2014  
  > "6 18 [h] 47 [m] 46 [s] .16 -1 [◦] 54 [′] 33 [′′] . 30 0.55×0.45 1300 56±9 6.6±0.1 23±2" (Table 2); "located at the end of the Galactic bar at a distance of 5.5 kpc from the Sun (Nguyen Luong et al. 2011; Zhang et al. 2014)" (1. Introduction)
- Target **W43-MM1 core #3**: coordinates RA 18h47m46.37s, Dec -1d54m33.41s (J2000)  
  > "3 18 [h] 47 [m] 46 [s] .37 -1 [◦] 54 [′] 33 [′′] . 41 0.52×0.47 1200 59±2 7.6±0.3 45±1" (Table 2); z/distance 5.5 kpc  
  > "3 18 [h] 47 [m] 46 [s] .37 -1 [◦] 54 [′] 33 [′′] . 41 0.52×0.47 1200 59±2 7.6±0.3 45±1" (Table 2); distance from Nguyen Luong et al. 2011; Zhang et al. 2014  
  > "3 18 [h] 47 [m] 46 [s] .37 -1 [◦] 54 [′] 33 [′′] . 41 0.52×0.47 1200 59±2 7.6±0.3 45±1" (Table 2)

## Data provenance

- ALMA projects: 2013.1.01365.S, 2015.1.01273.S
- bands: Band 6 (216-234 GHz)  
  > "W43-MM1 was imaged in band 6 (between 216 and 234 GHz)" (2.1 Data set)
- frequencies and spectral setup: 4.8 GHz total: two continuum bands and seven narrow bands, 122-976 kHz resolution  
  > "The total bandwidth is 4.8 GHz made of two continuum bands and seven narrow bands centred on lines of interest, with a spectral resolution ranging from 122 to 976 kHz" (2.1 Data set)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m and ACA 7 m; 33 mosaic fields (12 m), 11 fields (ACA)  
  > "with a 78"×53" (2.1 pc×1.4 pc) mosaic composed of 33 fields with the 12 m array and 11 fields with ACA" (2.1 Data set)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~0.44" (~2400 au); continuum band at 232.4 GHz ~0.57" (~3200 au)  
  > "a spatial resolution of ∼0.44" (∼2400 au) (see Table 1)" (2.1 Data set)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (217.105 GHz)
- Line: CO 2-1 (230.538 GHz)
- External data: Core properties (positions, sizes, masses, densities, dust temperatures) of cores #3, #6, #9, #18  
  > "Characteristics of the cores located at the tip of the main filament (from Motte et al. 2018b)." (Table 2) [from Motte et al. 2018b]
- External data: Isotopic ratios 12C/13C=45±13, 32S/33S=90±30, 18O/16O=327±32  
  > "12 C/ 13 C = 45±13 (Milam et al. 2005), 32 S/ 33 S = 90±30 (Chin et al. 1996), and [18] O/ [16] O = 327±32 (Wilson & Rood 1994)" (3.2 Critical density and opacity) [from Milam et al. 2005; Chin et al. 1996; Wilson & Rood 1994]
- External data: Abundances of comparison sources (Table 4)  
  > "List of sources used for comparison with cores #3 and #6." (Table 4) [from Ohishi et al. 1992; Marcelino et al. 2018; Allen et al. 2017; Fechtenbaum 2015; and others in Table 4]

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

- task: CASA 4.7.2 cleaning, multiscale  
  > "Data reduction was made with CASA 4.7.2. (McMullin et al. 2007)." (2.1 Data set)
- deconvolver: _not stated_
- weighting robust: Briggs robustness 0.5  
  > "The cleaning was performed with a 0.5 Briggs robustness weighting, using the multiscale option" (2.1 Data set)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: threshold ~1σ, region excluding mosaic borders  
  > "with a threshold of ∼1σ cropped on a region excluding the borders of the mosaic to avoid problems of divergence." (2.1 Data set)
- multiscale scales: _not stated_
- continuum subtraction: Per-pixel EMG fit of intensity distribution  
  > "We developed a method similar to the one presented in Jørgensen et al. (2016), using the density distribution of the channel intensities on each pixel." (2.2 Continuum subtraction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Core nomenclature, sizes and shapes  
  > "we follow the same nomenclature" (3 Results and analysis) [from Nony et al. 2018; Motte et al. 2018b]
- Continuum subtraction method similar to density distribution method  
  > "We developed a method similar to the one presented in Jørgensen et al. (2016)" (2.2 Continuum subtraction) [from Jørgensen et al. (2016)]

### Not stated but needed to reproduce (our reading)

- Calibration pipeline/manual details and calibrators
- Array combination (12m+ACA) procedure and primary-beam correction
- Cell and image size
- Multiscale scales
- Initial-guess and fitting details of the EMG fit
- Line-free/stacking details and how spectra were extracted and smoothed
- Details of CASSIS rotational-diagram fitting settings and the filling-factor correction

## Analysis recipe

1. **Subtract continuum per pixel**: Fit exponentially modified Gaussian to the intensity distribution of channels on each pixel  
  > "we use the exponentially modified Gaussian (EMG) function (Grushka 1972), which is the convolution between a Gaussian and an exponential decay" (2.2 Continuum subtraction)
   - software: STATCONT
   - fitting: _not stated_
   - validation: Compared with cSCM of STATCONT on synthetic spectra: error ±2% vs ±5%, ~20 times faster  
  > "we estimated a relative error on the continuum of ±2% with the EMG method fit versus ±5% for the cSCM" (2.2 Continuum subtraction)
2. **Identify molecules and map distributions**: Identify lines in core #3, then core #6; integrate maps; Gaussian fits for sizes  
  > "We used a Gaussian fit to derive a deconvolved size of the molecular emission" (3.1 Molecular content of cores #3 and #6)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive Tex and Ntot**: Rotational diagrams in LTE optically thin; otherwise Eq. 3 with Tex=190 K assumed for core #3  
  > "When it was not possible to use a rotational diagram, we assumed an excitation temperature of 190K for core #3 to derive a column density with Eq. (3)." (3.3 Temperatures and abundances)
   - software: CASSIS
   - assumption: Filling factor equal to 1; LTE since critical densities 1e4-1e7 below nH2 ~1e9 cm-3  
  > "We assume here that the filling factor is equal to 1." (3.3 Temperatures and abundances)
   - fitting: _not stated_
   - validation: Synthetic spectra and residuals; isotopologue ratios consistent with elemental ratios  
  > "Residuals show that only a few lines are unidentified towards core #3." (3.3 Temperatures and abundances)
4. **Compute abundances and compare with other sources**: Divide by NH2 from core densities for source sizes 2400, 1000, 500 au and Tex 10-200 K; compare with Table 4 sources  
  > "The molecular column densities are corrected by the filling factor assuming a r−2 density model for n H 2." (4.2 Unresolved cores)
   - assumption: Depth along line of sight equals core size  
  > "We consider that the depth of the molecular distribution along the line of sight is equal to the size of the continuum cores" (3.3 Temperatures and abundances)
   - fitting: _not stated_
   - validation: Optical depth check excludes sizes <500 au  
  > "When considering core sizes smaller than 500 au, all lines become optically thick in our temperature range" (4.2 Unresolved cores)

## Software

- **CASA** 4.7.2: Data reduction and cleaning  
  > "Data reduction was made with CASA 4.7.2." (2.1 Data set)
- **STATCONT** : Comparison of cSCM continuum method  
  > "the corrected sigma-clipping method (cSCM) seems to be the most effective using their STATCONT algorithm" (2.2 Continuum subtraction)
- **CASSIS** : Rotational diagrams  
  > "The rotational diagrams were performed using the CASSIS" (3.3. Temperatures and abundances)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Tex core #3 (hot core) | ~190 | not stated | K | 3 | core #3 appears to contain a hot core with a temperature of about 190 K |
| Tex range core #6 from rotational diagrams | 20-90 (abstract); 15-90 (text) | not stated | K | 3 | core #6 seems to have a lower temperature in the range from 20 K to 90 K from a rotational diagram analysis |
| Mean line width core #6 vs core #3 | 3.2±0.1 vs 5.2±0.2 | as given | km/s | 2 | with a mean line width of 3.2±0.1 km/s against 5.2±0.2 km/s |
| Number of molecules identified in core #3 / core #6 | 25 / 17 | not stated | dimensionless | 2 | The 25 molecules that we identified in this core, including isotopologues, are listed in Table 3. Out of these molecules, 17 are identified in core #6. |
| CH3OH Ntot core #6 (beam size) | 4.2e17 | ±4.0e17 | cm-2 | 3 | CH 3 OH 97.1±0.1 5.9±0.3 4.7±0.4(17) 320±80 0.55×0.35 95.8±0.2 3.3±0.4 4.2±4.0(17) 55±35 |

## Qualitative findings

- Ten molecules are centred on core #6; the others trace shocks from outflows/filament.  
  > "ten are directly associated to core #6 and the others can be associated to the interaction between its envelope and the lowvelocity shock of the ridge" (5 Conclusion)

## Claim tuples

- H: Core #6 is a high-mass prestellar core rather than protostellar | E: Molecular abundances and temperatures compared with core #3 and other sources for several source sizes | R: Abundances compatible with 1000 au core at 20-90 K or 500 au core at ~80 K; non-detection of N2D+ | F: Core #6 remains a good prestellar candidate though it may be at the very start of the protostellar phase | **partially**
- H: Core #3 is a hot core | E: Rotational diagrams | R: Tex ~190 K | F: Core #3 contains a hot core | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Source sizes <500 au rejected because lines would be optically thick  
  > "the source size is not less than 500 au because the lines would be optically thick, which is not observed." (5 Conclusion)
- How they decided it was enough: _not stated_
- Limitation (authors): Huge uncertainty on temperature from rotational diagrams due to low S/N  
  > "Because of the low signal-to-noise ratio and the range of upper energy levels, there is a huge uncertainty on the temperature (15-90 K)" (5 Conclusion)
- Caveat (inferred, ours): Conclusions depend strongly on assumed source size
- Caveat (inferred, ours): Only three molecules give rotational diagrams for core #6
- Caveat (inferred, ours): Comparison abundances from literature are at different sizes, not filling-factor corrected

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration and imaging parameters
- Missing: Fit details of EMG continuum method
- Missing: CASSIS fit settings
- Data volume (inferred): ~100-300 GB for 12m+ACA mosaic Band 6 raw data
- Score (inferred): 3/5, Project codes given and CASA/robust stated, but calibration, extraction and fitting details lacking.
- Rediscovery candidate: no, Recipe incomplete (spectra extraction, line identification, fitting settings).

## Links

- Method: Sanchez-Monge et al. 2017 (STATCONT) (Continuum determination methods)
- Method: Jørgensen et al. 2016 (Density-distribution continuum subtraction)
- Companion: Nony et al. 2018 (Identified cores #3 and #6 and the prestellar candidate)
- Companion: Motte et al. 2018b (Core catalogue and continuum maps)
- Related: ALMA-IMF-precursor W43-MM1 mosaic

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 35,
  "rate": 0.493
 },
 "evidence_ok": true
}
```
