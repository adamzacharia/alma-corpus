# Complex organic molecules in low-mass protostars on Solar System scales. I. Oxygen-bearing species

`2020A&A...639A..87V` | Astronomy and Astrophysics 2020 | first author: van Gelder, M. L. | arXiv: 2005.06784 | DOI: 10.1051/0004-6361/202037758

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: What are the abundance ratios of O-bearing COMs relative to CH3OH on ~100 AU scales in Class 0 protostars, and how do they compare to other low-mass protostars, cold vs hot components, and methanol D/H?  
  > "The aim is to determine the abundance ratios of oxygen-bearing COMs in Class 0 protostellar systems on scales of ∼100 AU radius." (abstract)
- Target **B1-c**: coordinates 03:33:17.88 +31:09:31.8 (J2000)  
  > "B1-c Perseus 03:33:17.88 31:09:31.8 320" (Table 1); z/distance 320 pc  
  > "B1-c Perseus 03:33:17.88 31:09:31.8 320" (Table 1); distance from Ortiz-León et al. (2018)  
  > "B1-c Perseus 03:33:17.88 31:09:31.8 320" (Table 1)
- Target **S68N**: coordinates 18:29:48.09 +01:16:43.3 (J2000)  
  > "S68N Serpens 18:29:48.09 01:16:43.3 436" (Table 1); z/distance 436 pc  
  > "S68N Serpens 18:29:48.09 01:16:43.3 436" (Table 1); distance from Ortiz-León et al. (2017)  
  > "S68N Serpens 18:29:48.09 01:16:43.3 436" (Table 1)
- Target **B1-bS**: coordinates 03:33:21.36 +31:07:26.3 (J2000)  
  > "B1-bS Perseus 03:33:21.36 31:07:26.3 320" (Table 1); z/distance 320 pc  
  > "B1-bS Perseus 03:33:21.36 31:07:26.3 320" (Table 1); distance from Ortiz-León et al. (2018)  
  > "B1-bS Perseus 03:33:21.36 31:07:26.3 320" (Table 1)
- Target **B1-b, B1-bN, Ser-emb 8 (N), SMM3**: coordinates see Table 1 (e.g. SMM3 18:29:57.75 +01:14:06.7)  
  > "SMM3 Serpens 18:29:57.75 01:14:06.7 436" (Table 1); z/distance 320 pc (Perseus), 436 pc (Serpens)  
  > "SMM3 Serpens 18:29:57.75 01:14:06.7 436" (Table 1); distance from Ortiz-León et al. (2017, 2018)  
  > "SMM3 Serpens 18:29:57.75 01:14:06.7 436" (Table 1)

## Data provenance

- ALMA projects: 2017.1.01174.S, 2017.1.01350.S
- bands: Band 3 (3 mm) and Band 6 (1 mm)  
  > "were taken in Band 3 (3 mm) and Band 6 (1 mm)." (2. Observations)
- frequencies and spectral setup: resolution ~0.2 km/s for most windows, 0.3-0.4 in a few Band 3 windows  
  > "The spectral resolution was ∼0.2 km s −1 for most spectral windows" (2. Observations)
- continuum bandwidth: _not stated_
- arrays: 12m array  
  > "All data were taken using the 12m array" (2. Observations)
- configurations: C43-2 & C43-3 (Band 3), C43-4 (Band 6)  
  > "C43-2 & C43-3 configuration) and ∼0.45" (∼100-200 AU; C43-4 configuration)" (2. Observations)
- baselines: _not stated_
- angular resolution: ~1.5-2.5" (Band 3), ~0.45" (Band 6)  
  > "a synthesized beam of ∼1.5–2.5" (500-1000 AU at the distances of our sources; C43-2" (2. Observations)
- max recoverable scale: ~20" (Band 3), ~6" (Band 6)  
  > "The largest recoverable scales (LAS) were ∼20" (∼6000–9000 AU) and ∼6"" (2. Observations)
- sensitivity: line sensitivity ~0.1 K  
  > "The line sensitivity is ∼0.1 K." (2. Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: Own program PI van Dishoeck; SMM3 Band 6 archival (PI Tychoniec)  
  > "project 2017.1.01174.S; PI: E.F. van Dishoeck" (2. Observations)
- Line: CH3OH and isotopologues, CH2DOH, CH3CH2OH, CH3CHO, CH3OCHO, CH3OCH3, CH3COCH3, (CH2OH)2, CH2OHCHO, H2CCO, t-HCOOH many; see Tables E.2 and E.3 (~109.5-113.2 GHz (Band 3), ~260-263.8 GHz (Band 6))
- External data: Source distances, Lbol, Tbol, Menv  
  > "(1) Ortiz-León et al. (2018). (2) Enoch et al. (2009)." (Table 1) [from Ortiz-León et al. 2017, 2018; Enoch et al. 2009, 2011; Karska et al. 2018; Hirano & Liu 2014]
- External data: Local ISM isotope ratios 12C/13C~70, 16O/18O~560  
  > "12 C/ 13 C = 70 and 16 O/ 18 O = 560, respectively." (Table 2 notes) [from Milam et al. 2005; Wilson & Rood 1994]
- External data: Comparison abundances for IRAS 16293B, HH 212, IRAS 2A/4A, IRAS 16293A  
  > "The HH 212 abundances are from Lee et al. (2019a)." (Figure 7 caption) [from Jørgensen et al. 2018; Lee et al. 2019a; Taquet et al. 2015, 2019; Manigand et al. 2020]
- External data: Spectroscopic line lists  
  > "The line lists of each molecule were taken from the CDMS" (3.1 Methodology) [from CDMS (Müller et al. 2001, 2005; Endres et al. 2016); JPL (Pickett et al. 1998)]

## Processing

### Calibration

- pipeline or manual: pipeline product data used  
  > "From the pipeline product data, it was clear that all COM emission (except CH 3 OH) was unresolved" (2. Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ≤15% absolute flux calibration  
  > "The absolute uncertainty on the flux calibration is ≤15% for all observations." (2. Observations)
- self calibration: _not stated_

### Imaging

- task: CASA 5.1.1 tclean  
  > "with the CASA 5.1.1 tclean task using a Briggs weighting of 0.5." (2. Observations)
- deconvolver: _not stated_
- weighting robust: Briggs 0.5  
  > "with the CASA 5.1.1 tclean task using a Briggs weighting of 0.5." (2. Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: mask a few times the synthesized beam  
  > "line images were made using a mask size of a few times the size of the synthesized beam" (2. Observations)
- multiscale scales: _not stated_
- continuum subtraction: continuum from line-free channels, subtracted from line data  
  > "Using the continuum solutions, all line data were continuum subtracted." (2. Observations)
- line free channels: _not stated_
- primary beam correction: applied; factors ~1 to ~4  
  > "The images were primary beam corrected, with factors of ∼1 for sources in the center of the images" (2. Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 100 K radius relation for hot cores  
  > "Using the relation of Bisschop et al. (2007) for the 100 K radius in hot cores:" (4.1 Occurrence of COMs in young protostars) [from Bisschop et al. (2007)]
- D/H to formation temperature via GRAINOBLE model results  
  > "In order to compare our methanol D/H ratios to their model results, our gasphase CH 2 DOH abundances have to be corrected for statistical weights" (4.6 Temperature dependence of deuterated methanol) [from Bøgelund et al. (2018); Taquet et al. (2012)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum
- Image size and cell size
- Mask details and clean threshold/iterations
- Self-calibration usage
- Flux calibrator and pipeline version
- Which lines were excluded as blended per source
- Exact CASSIS version and chi2 definition/noise estimate
- Vlsr values per source
- Spectral extraction aperture details

## Analysis recipe

1. **Image continuum and line cubes**: Continuum from line-free channels, continuum subtraction, tclean line images with masks; spectra extracted from central beam  
  > "Spectra were extracted from the central beam of the sources." (2. Observations)
   - software: CASA
   - parameter: Briggs 0.5  
  > "using a Briggs weighting of 0.5." (2. Observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit LTE models to get column densities and Tex**: Grid of N, Tex, FWHM per species; minimum reduced chi2; Band 3 and 6 modeled separately; optically thick and blended lines excluded  
  > "the χ 2 is computed for each grid point, after which the best fitting model is determined by the minimum reduced χ 2 ." (3.1 Methodology)
   - software: CASSIS
   - parameter: N grid 1e13-1e17 cm-2 (step 0.05 dex), Tex 50-550 K (10 K), FWHM 0.5-9.0 km/s (0.1)  
  > "The total parameter space probed is 10 13 –10 17 cm −2, 50–550 K, and 0.5–9.0 km s −1, respectively" (3.1 Methodology)
   - parameter: Tex fixed to 200 K for species with few lines; Band 3 Tex set to Band 6; B1-bS FWHM fixed to 1 km/s  
  > "the excitation temperature was fixed to T ex = 200 K, and only the column density and FWHM were varied." (3.1 Methodology)
   - assumption: Source size 0.45" for all sources; single Tex; Gaussian line profiles; column densities are lower limits  
  > "A source size of 0.45" (equal to the Band 6 beam) is used for all sources." (3.1 Methodology)
   - fitting: Grid chi2 minimization; 2σ uncertainties from grid  
  > "The 2σ uncertainty on the column density, excitation temperature, and FWHM is computed from the grid." (3.1 Methodology)
   - validation: Tested Tex=100 K and -30 K for Band 3; excluded low-Eup lines in Band 6  
  > "When the Band 3 excitation temperature of all species for which T ex was fixed is decreased by 30 K, no significant changes in the column densities and abundances arise." (3.2 Column densities and excitation temperatures)
3. **Derive CH3OH column density and abundance ratios**: CH3OH scaled from 13CH3OH (Band 3) and CH3 18OH (Band 6); abundances relative to CH3OH  
  > "the column density of CH 3 OH is determined by scaling it from 13 CH 3 OH for Band 3 and CH 18 3 OH for Band 6" (3.2 Column densities and excitation temperatures)
   - software: CASSIS
   - parameter: 12C/13C = 70, 16O/18O = 560  
  > "using 12 C/ 13 C = 70 and 16 O/ 18 O = 560, respectively." (Table 2)
   - assumption: CH3OH used as reference because CO traces more extended regions  
  > "Because the usual tracer of H 2, CO, comes from more extended regions, CH 3 OH is chosen as the reference species." (3.3 Relative abundances)
   - fitting: _not stated_
   - validation: Source-size scaling test with optical depth tau<0.1  
  > "For B1-c and S68N, the resulting column densities still give optically thin (τ < 0.1) lines for all species except CH 3 OH." (4.2 Dependence on source size)
4. **Fit cold extended component in Band 3**: Two-component model: Band 6 best fit kept fixed as warm/hot; cold component Tex=60 K, N fitted, source size 2.0"  
  > "Here, an excitation temperature of 60 K was assumed and only the column density was fitted for." (4.3.1 Multi-component model)
   - software: CASSIS
   - parameter: Only B1-c and S68N  
  > "This is only done for B1-c and S68N since the S/N of B1-bS in Band 3 is insufficient to carry out such analysis." (4.3.1 Multi-component model)
   - fitting: _not stated_
   - validation: _not stated_
5. **Methanol D/H and formation temperature**: CH2DOH/CH3OH corrected by statistical weight factor 3, compared to GRAINOBLE model  
  > "a D atom has a 3 times higher probability to stick into the CH 3 group than into the OH group." (4.6 Temperature dependence of deuterated methanol)
   - parameter: nH = 1e5-6 cm-3  
  > "where a density of n H = 10 5−6 cm −3 was assumed" (4.6 Temperature dependence of deuterated methanol)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 5.1.1: tclean imaging of lines  
  > "with the CASA 5.1.1 tclean task using a Briggs weighting of 0.5." (2. Observations)
- **CASSIS** : LTE modelling of column densities and Tex  
  > "was used to determine column densities and excitation temperatures of detected species." (3.1. Methodology)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH column density B1-c, Band 6 | 1.9e18 | ±0.6e18 | cm-2 | 3 | CH 3 OH CDMS – (1.8 ± 0.4) × 10 18 ≡ 100 – (1.9 ± 0.6) × 10 18 ≡ 100 |
| CH3OH column density S68N, Band 6 | 1.4e18 | ±0.6e18 | cm-2 | 3 | CH 3 OH CDMS – (3.6 ± 0.8) × 10 17 ≡ 100 – (1.4 ± 0.6) × 10 18 ≡ 100 |
| CH3OCHO/CH3OH B1-c Band 6 | 1.0 | ±0.3 | % | 3 | CH 3 OCHO Methyl formate 2.3 ± 1.0 1.0 ± 0.3 0.29 ± 0.07 1.1 ± 0.5 6.1 ± 1.8 0.75 ± 0.10 |
| CH3OCH3/CH3OH B1-c Band 6 | 1.3 | ±0.4 | % | 3 | CH 3 OCH 3 Dimethyl ether 1.0 ± 0.2 1.3 ± 0.4 1.8 ± 0.4 0.9 ± 0.4 4.3 ± 1.2 1.3 ± 0.2 |
| Methanol D/H B1-c Band 6 | 2.7 | ±0.9 | % | 5 | In Band 6, this is 2.7 ± 0.9%, 1.4 ± 0.6%, and < 1.6%. |
| Methanol D/H B1-c Band 3 | 1.9 | ±0.7 | % | 5 | In Band 3, this gives a D/H ratio of 1.9±0.7%, < 4.3%, and < 3.3% for B1-c, S68N, and B1-bS respectively. |
| Methanol formation temperature | ~15 | not stated | K | 5 | These deuteration fractions correspond to a temperature during the formation of methanol of ∼ 15 K |
| Band 3 minus Band 6 average Tex | ~-30 | not stated | K | 2 | the average excitation temperature in Band 3 is ∼ 30 K lower than in Band 6. |
| Average FWHM B1-c Band 6 | 3.3 | ±0.2 | km/s | 2 | The average FWHM for B1-c and S68N in Band 6 is 3.3±0.2 and 5.0±0.2 km s −1, respectively |
| R(T=100K) B1-c | 37.4 | not stated | AU | 0 | implies an R T =100K of 37.4 AU, 35.8 AU, and 11.6 AU for B1-c, S68N, and B1-bS, respectively. |

## Qualitative findings

- COM emission in 3 of 7 sources (B1-c, S68N, B1-bS), no clear correlation with luminosity  
  > "No clear correlation seems to exist between the occurrence of COMs and source luminosity." (abstract)
- Cold (Tex~60 K) extended COM component in B1-c with few % of warm column density  
  > "B1-c hosts a cold ( T ex ≈ 60 K), more extended component of COM emission" (abstract)

## Claim tuples

- H: Does COM occurrence correlate with luminosity? | E: Detection of COMs in seven Class 0 sources vs Lbol | R: 3 of 7 detect COMs; most luminous SMM3 none, low-luminosity B1-bS detected | F: No clear correlation | **supported**
- H: Are COM abundances similar across protostars? | E: Compare Band 6 abundances to IRAS 16293B, HH 212 etc. | R: CH2DOH, CH3OCHO, CH3OCH3, CH3COCH3 within a factor of a few; CH3CHO, CH3CH2OH, CH2OHCHO lower up to an order of magnitude | F: Many ratios fixed early; others depend on local conditions | **supported**
- H: Is there a cold extended COM component? | E: Two-component fit to Band 3 with Tex=60 K | R: Detected in B1-c with a few % of warm column; less evident in S68N | F: Cold component present in B1-c | **partially**
- H: What temperature does methanol D/H imply? | E: Statistical-weight corrected CH2DOH/CH3OH vs GRAINOBLE | R: D/H 1-3% | F: Formation at ~15 K | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: CH3OH chosen as reference since CO traces extended regions  
  > "Because the usual tracer of H 2, CO, comes from more extended regions, CH 3 OH is chosen as the reference species." (3.3 Relative abundances)
- How they decided it was enough: _not stated_
- Limitation (authors): Source size assumed 0.45"; column densities are lower limits; B1-bS abundances to be used with care  
  > "In reality, the size of the emitting region is smaller than the assumed 0.45" and any derived column densities are thus lower limits." (3.1 Methodology)
- Limitation (authors): CH3OH lines optically thick, so CH3OH column derived from isotopologues, possibly underestimated  
  > "This hints at the possibility that even 13 CH 3 OH is optically thick for these sources." (3.3 Relative abundances)
- Caveat (inferred, ours): LTE with single Tex and fixed Tex=200 K for many species adds uncertainty
- Caveat (inferred, ours): Small sample (three COM-rich sources)
- Caveat (inferred, ours): Assumed source size affects column densities and optical depth
- Caveat (inferred, ours): Beam dilution differs a lot between bands, complicating cold/hot comparison

## Reproducibility

- Data public (paper): ALMA data acknowledged; SMM3 from archival program  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2017.1.01174.S and ADS/JAO.ALMA#2017.1.01350.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Line-free channels and imaging parameters
- Missing: Which lines were excluded as blended
- Missing: Vlsr values
- Missing: CASSIS version
- Data volume (inferred): ~100-300 GB raw for two programs
- Score (inferred): 3/5, Public data and CASSIS fitting grid are well described with line tables, but imaging details, calibration and exact line selections are missing.
- Rediscovery candidate: yes, Data public, LTE grid fitting recipe described with parameter ranges, and results are numeric tables.

## Links

- Method: Bisschop et al. (2007) (100 K radius relation)
- Method: Bøgelund et al. (2018) (D/H vs formation temperature models)
- Companion: Jørgensen et al. (2018) (IRAS 16293B COM abundances for comparison)
- Companion: Lee et al. (2019a) (HH 212 abundances)
- Related: PILS
- Related: JWST/MIRI GTO program 1290
- Related: VANDAM

## Checks

```json
{
 "quotes": 76,
 "quotes_ok": 76,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [
  "2017.1.01774.S"
 ],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 87,
  "stated": 58,
  "rate": 0.667
 },
 "evidence_ok": true
}
```
