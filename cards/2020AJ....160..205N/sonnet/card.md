# Detection of Cyclopropenylidene on Titan with ALMA

`2020AJ....160..205N` | The Astronomical Journal 2020 | first author: Nixon, Conor A. | arXiv: 2010.12743 | DOI: 10.3847/1538-3881/abb679

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: solar_system, astrochemistry
- Question: Can cyclopropenylidene (c-C3H2), pyridine and pyrimidine be detected in Titan's atmosphere with ALMA, and what are their abundances or upper limits?  
  > "In 2016 and 2017 we conducted high sensitivity observations with ALMA, with the goal of searching for new molecules in Titan’s atmosphere" (1. INTRODUCTION)
- Target **Titan**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00423.S, 2016.A.00014.S, 2015.1.00512.S
- bands: Band 6 (2016, ~251 GHz) and Band 7 (2017, ~352 GHz); CO J=2-1 dataset near 230 GHz  
  > "∼ 251 GHz in 2016 (Band 6) and ∼ 352 GHz" (abstract)
- frequencies and spectral setup: Spw channel spacing 0.244 MHz (0.977 MHz for Spw 5); 1920 or 3840 channels; spectral resolution twice the channel spacing  
  > "6 351281-352219 0.244 3840 C 2 H 3 CN — multiple" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Beams 0.87"×0.72" (2016 Band 6), 0.92"×0.81" (CO), 0.18"×0.15" and 0.28"×0.19" (2017)  
  > "08-May-2017 08:49 09:07 18 -19.28 22.24 0.18 ′′ × 0.15 ′′" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 43 min ×3 (2015.1.00423.S); 2 min (2015.1.00512.S); 18 and 98 min (2016.A.00014.S)  
  > "16-May-2017 05:34 07:12 98 -13.61 15.97" (Table 1)
- observing dates: 2–4 March 2016 (Band 6); 8 and 16 May 2017 (Band 7); 1 April 2016 (CO)  
  > "Observations of Titan were completed during March 2–4 2016 in Band 6" (2. OBSERVATIONS)
- pi or archival as stated: _not stated_
- Line: c-C3H2 7(0,7)-6(1,6)/7(1,7)-6(0,6) blend; 6(2,5)-5(1,4) (251314.3 and 251527.3 MHz)
- Line: c-C3H2 10(1,10)-9(0,9)/10(0,10)-9(1,9) blend; 9(1,8)-8(2,7)/9(2,8)-8(1,7) blend (351781.6 and 351965.9 MHz)
- Line: CO J=2-1; J=3-2 (230538 MHz; 345796 MHz)
- Other facility **Cassini INMS**: Ion abundances used as a priori for gradient model  
  > "in line with the INMS ion measurements (Vuitton et al. 2007)" (4.2)
- External data: CO mixing fraction of 49.6 ppm held fixed in temperature retrieval  
  > "CO was fixed at a constant mixing fraction of 49.6 ppm as determined by Serigano et al. (2016)" (3.1) [from Serigano et al. (2016)]
- External data: A priori temperature profile from HASI and Cassini radio science below 100 km, ALMA 2015 retrieval above  
  > "disk-averaged retrieval results from 2015 ALMA observations of Titan (Thelen et al. 2018) were used at altitudes > 100 km" (3.1) [from Fulchignoni et al. 2005; Schinder et al. 2012; Thelen et al. 2018]
- External data: Spectral line data from CDMS and JPL catalogs  
  > "Spectral line data for most molecules were taken from the CDMS catalog" (3. MODELING) [from Müller et al. 2001, 2005; Pickett et al. 1998]

## Processing

### Calibration

- pipeline or manual: 2015.1.00423.S delivered calibrated; 2015.1.00512.S reduced with ALMA pipeline script without hifa_fluxcalflag  
  > "using the ALMA pipeline script prepared by the Joint ALMA Observatory staff, with the exception of the removal of the hifa fluxcalflag task" (2. OBSERVATIONS)
- casa version: CASA 4.7.2-REL (2015.1.00423.S); CASA 5.6.1-8 (2015.1.00512.S)  
  > "the data were reduced in CASA Version 5.6.1-8" (2. OBSERVATIONS)
- pipeline version: _not stated_
- archive products used as is: 2015.1.00423.S provided calibrated, then post-processed  
  > "the data were provided in calibrated form (bandpass, phase and flux calibrated)" (2. OBSERVATIONS)
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA clean; cvel and fixplanets for rest-velocity and ephemeris  
  > "to provide rest-velocity correction ( cvel ) and ephemeris update ( fixplanets )" (2. OBSERVATIONS)
- deconvolver: Högbom  
  > "deconvolved (‘cleaned’) in CASA using the H¨ogbom algorithm, with a cell size of 0.1" (2. OBSERVATIONS)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.1" (2016 Band 6); 0.2" (CO)  
  > "where pixels were set to 0.2 ′′ × 0.2 ′′" (2. OBSERVATIONS)
- image size: 128 × 128 pixels (CO dataset)  
  > "image size = 128 × 128 pixels" (2. OBSERVATIONS)
- masking: Disk-averaged spectra from circular mask containing 90% of Titan continuum flux  
  > "a circular pixel mask set to contain 90% of Titan’s continuum flux, as in Lai et al. (2017)" (2. OBSERVATIONS)
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.87"×0.72" (Band 6)  
  > "a final restoring beam size of 0.87 ′′ × 0.72 ′′" (2. OBSERVATIONS)
- final rms: _not stated_

### Inherited from earlier work

- Data reduction of the 2017 data (2016.A.00014.S)  
  > "The data reduction of the 2017 data (2016.A.00014.S) has already been described in Cordiner et al. (2019)." (2. OBSERVATIONS) [from Cordiner et al. (2019)]
- Disk-averaged spectrum extraction mask  
  > "as in Lai et al. (2017)" (2. OBSERVATIONS) [from Lai et al. (2017)]
- Disk-model emission angles weighting  
  > "as described in Teanby et al. (2013), Appendix A" (3. MODELING) [from Teanby et al. (2013)]
- Delta chi-square upper-limit method  
  > "the 1, 2 and 3- σ upper limits are indicated at the trial abundances where the ∆ χ [2] reaches +1, +4, and +9 respectively (Nixon et al. 2012)" (4.3) [from Nixon et al. (2012)]

### Not stated but needed to reproduce (our reading)

- Mapping of CASA pipeline processing for 2016.A.00014.S (in Cordiner et al. 2019)
- Noise estimates σν used in chi-square
- Fixed temperature profile values and NEMESIS input files
- Line-free channels and continuum treatment
- Flux scale uncertainty
- Exact time/epoch-dependent Titan ephemeris details
- Which Spw/windows of 2015.1.00423.S used for the 2016 temperature retrieval

## Analysis recipe

1. **Reduce and extract disk-averaged spectra**: CASA calibration, cvel/fixplanets, Högbom clean, extract spectra from mask enclosing 90% of continuum  
  > "Disk-averaged spectra from all observations were extracted from an integrated region defined by a circular pixel mask" (2. OBSERVATIONS)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Retrieve temperature profile from CO lines**: NEMESIS fit of CO 2-1 (2016) and 3-2 (2017) with continuous temperature variation 100–500 km, CO fixed at 49.6 ppm  
  > "allowed continuous variation of the temperature profile between 100–500 km" (3.1)
   - software: NEMESIS
   - parameter: a priori temperature error 5 K in all layers (0–1200 km)  
  > "Temperature a priori errors were set to 5 K in all atmospheric layers (0–1200 km)" (3.1)
   - fitting: Bayesian optimal estimation with Marquardt-Levenberg minimization; convergence when solution changes <0.1%  
  > "Marquart-Levenberg minimization is used to descend a downhill trajectory of the cost function until satisfactory convergence is reached (solution changing by < 0.1%)" (3. MODELING)
   - validation: _not stated_
3. **Fit known nitriles and search for new species**: Step-function profiles for C2H5CN (250 km) and C2H3CN (300 km); add trial species and test fit improvement; c-C3H2 introduced with step at 300 km or higher  
  > "we found a significant improvement to the model fit after introducing the gas c-C 3 H 2" (3.2)
   - software: NEMESIS
   - fitting: _not stated_
   - validation: Delta chi-square curve with 350 km step model  
  > "we calculated a ∆ χ [2] curve for different amounts of the gas in a forward model, using a step function at 350 km" (3.2)
4. **Retrieve c-C3H2 abundances**: Step models at 300/350/400 km and four-parameter gradient model with a priori at 1100 km and 300 km  
  > "a four-parameter gradient model" (4.2)
   - software: NEMESIS
   - parameter: p_u=(5.0±2.0)e-11 bar, q_u=(3.4±1.0)e-6, p_l=(1.0±0.5)e-4 bar, q_l=(2.0±1.9)e-9  
  > "p l = (1 . 0 ± 0 . 5) × 10 − 4 bar, q l = (2 . 0 ± 1 . 9) × 10 − 9" (4.2)
   - fitting: Optimal estimation; errors per Irwin et al. 2008 and Nixon et al. 2008, with factor 1.291 for Hanning apodization  
  > "the final error bars are increased by a factor √ 2 / 1 . 095 = 1 . 291" (4.1)
   - validation: Delta chi-square significance  
  > "The combined significance of the detection is 6.3" (3.2. Spectral windows 1 and 6: Discovery of Cyclopropenylidene)
5. **Upper limits for pyridine and pyrimidine**: Delta chi-square at +1, +4, +9 for 1,2,3 sigma using constant profile above 300 km  
  > "the 1, 2 and 3- σ upper limits are indicated at the trial abundances where the ∆ χ [2] reaches +1, +4, and +9 respectively" (4.3)
   - software: NEMESIS
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.2-REL; 5.6.1-8: Calibration post-processing, cvel, fixplanets, clean  
  > "post-processed using the Common Astronomy Software Applications (CASA) package Version 4.7.2-REL" (2. OBSERVATIONS)
- **NEMESIS** : Radiative transfer retrieval of spectra  
  > "Modeling was accomplished using the NEMESIS program (Irwin et al. 2008)" (3. MODELING)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| c-C3H2 VMR, 350 km step, 2016 (Band 6) | 0.50 | ±0.14 | ppb | 4 | we obtained a VMR of 0.50 ± 0.14 ppb and column abundance of 3.5 × 10 [12] cm − 2 in 2016 |
| c-C3H2 VMR, 350 km step, 2017 (Band 7) | 0.28 | ±0.08 | ppb | 4 | somewhat lower VMR (0.28 ± 0.08) |
| Mean c-C3H2 VMR (350 km step) | 0.33 | ±0.07 | ppb | 4 | a mean value of 0.33 ± 0.07 ppb for the 350 km step profile |
| Detection significance combined | 6.3 | not stated | sigma | 3 | The combined significance of the detection is 6.3 σ . |
| pyridine 2-sigma upper limit | 1.153 | not stated | ppb | 5 | c-C 5 H 5 N 0.020 263331 0.29 1.046 1.153 1.356 |
| pyrimidine 2-sigma upper limit | 0.854 | not stated | ppb | 5 | c-C 4 H 4 N 2 0.020 262143 0.34 0.663 0.854 1.042 |
| C2H5CN abundance, 250 km step | 5.040 | ±0.095 | ppb | 3 | C 2 H 5 CN 250 km step 1.002 5.040 ± 0.095 2.2378 × 10 [14] |

## Qualitative findings

- First detection of c-C3H2 in a planetary atmosphere; column ~1e12 cm-2 similar to photochemical models  
  > "first time this molecule has been detected in a planetary atmosphere" (abstract)

## Claim tuples

- H: Cyclopropenylidene is present in Titan's atmosphere | E: Delta chi-square tests on ALMA Band 6 and 7 spectra | R: 4.6σ (Band 6), 4.3σ (Band 7), combined 6.3σ | F: First detection of c-C3H2 on Titan | **supported**
- H: Pyridine and pyrimidine are detectable | E: Delta chi-square upper limits in Spw 2 and 3 | R: 2σ limits 1.15 and 0.85 ppb | F: Non-detections | **refuted**
- H: c-C3H2 abundance changed between 2016 and 2017 | E: Compare retrievals | R: 0.50±0.14 vs 0.28±0.08 ppb | F: Either a decrease or consistent mean | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Little constraint on vertical profile shape; results weakly sensitive to step altitude  
  > "we have very little constraint on this at present" (5.1)
- Caveat (inferred, ours): Detection significance depends on noise estimate and apodization correction
- Caveat (inferred, ours): Single step altitude assumption drives abundance
- Caveat (inferred, ours): Possible line blends with unmodeled species not excluded
- Caveat (inferred, ours): Pyridine shallow minimum unexplained

## Reproducibility

- Data public (paper): ALMA project codes cited; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00423.S," (ACKNOWLEDGMENTS)
- Products in archive: _not stated_
- Missing: Pipeline/imaging details for 2017 data
- Missing: NEMESIS setup and noise estimates
- Missing: Final temperature profiles numerically
- Data volume (inferred): ~50-200 GB raw for three projects
- Score (inferred): 5/5, Data identified and retrieval method described, but key inputs rely on prior papers and unreleased NEMESIS configuration.
- Rediscovery candidate: no, Requires NEMESIS configuration and inherited reduction details not given.

## Links

- Method: Irwin et al. 2008 (NEMESIS retrieval code)
- Method: Cordiner et al. (2019) (2017 data reduction)
- Method: Teanby et al. 2009 (Delta chi-square method)
- Companion: Lai et al. (2017) (Disk-averaged spectra extraction)

## Checks

```json
{
 "quotes": 56,
 "quotes_ok": 56,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 72,
  "stated": 39,
  "rate": 0.542
 },
 "evidence_ok": true
}
```
