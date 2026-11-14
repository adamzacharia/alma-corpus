# ALMA Detection of Interstellar Methoxymethanol (CH<SUB>3</SUB>OCH<SUB>2</SUB>OH)

`2017ApJ...851L..46M` | The Astrophysical Journal Letters 2017 | first author: McGuire, Brett A. | arXiv: 1712.03256 | DOI: 10.3847/2041-8213/aaa0c3

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: astrochemistry, star_formation
- Question: Is methoxymethanol (CH3OCH2OH) present in the ISM toward NGC 6334I MM1, at what abundance, and what does it imply for formation routes?  
  > "We report the detection of interstellar methoxymethanol () in ALMA Bands 6 and 7 toward the MM1 core in the high-mass star-forming region NGC 6334I" (abstract)
- Target **NGC 6334I MM1**: coordinates analysis position J2000 17:20:53.373, -35:46:58.14  
  > "at a distance of 1.3 kpc (cite: Reid:2014km)" (Introduction); "The position chosen for analysis (J2000 17:20:53.373, $-35$:46:58.14)" (4 Results and Analysis); z/distance 1.3 kpc  
  > "at a distance of 1.3 kpc (cite: Reid:2014km)" (Introduction); "The position chosen for analysis (J2000 17:20:53.373, $-35$:46:58.14)" (4 Results and Analysis); distance from Reid et al. 2014 (cite: Reid:2014km)  
  > "at a distance of 1.3 kpc (cite: Reid:2014km)" (Introduction); "The position chosen for analysis (J2000 17:20:53.373, $-35$:46:58.14)" (4 Results and Analysis)

## Data provenance

- ALMA projects: 2016.1.00383.S, 2015.A.00022.T, 2015.1.00150.S
- bands: Band 6 (249 GHz) and Band 7 (287, 303, 344 GHz)  
  > "Band | Band 6 | Band 7 | Band 7 | Band 7" (Table 1)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 4: C40-7; Cycle 3: C36-4, C36-5, C36-2  
  > "Cycle: configuration(s) | 4: C40-7 | 3: C36-4, C36-5 | 3: C36-2 | 3: C36-4, C36-5" (Table 1)
- baselines: _not stated_
- angular resolution: 0.11x0.08'' (249 GHz), 0.25x0.19'' (287), 0.87x0.64'' (303), 0.22x0.17'' (344)  
  > "$0.11\times 0.08$ ($+76$) | $0.25\times 0.19$ ($-82$) | $0.87\times 0.64$ ($+74$) | $0.22\times 0.17$ ($-76$)" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: rms per channel 1.1, 2.0, 20.0, 3.3 mJy/beam (2.5, 0.62, 0.48, 0.91 K)  
  > "1.1 (2.5) | 2.0 (0.62) | 20.0 (0.48) | 3.3 (0.91)" (Table 1)
- time on source: 37+37, 26+26, 27, 27+27 min  
  > "Time on Source (min) | 37, 37 | 26, 26 | 27 | 27, 27" (Table 1)
- observing dates: 2016 Jan to Aug (Cycle 3); 2017 Aug 18, 19 (Cycle 4)  
  > "2017 Aug 18, 19 | 2016 Jul 18, 2016 Aug 02 | 2016 Jan 17" (Table 1)
- pi or archival as stated: _not stated_
- Line: CH3OCH2OH (conformer I) more than two dozen unblended transitions (e.g. 281024.6590 MHz)
- External data: Laboratory rotational spectrum of CH3OCH2OH conformers (150-450 GHz) and dipole moments  
  > "were recently published by (cite: Motiyenko:2017dwa) between 150 and 450 GHz." (Spectroscopy) [from Motiyenko et al. 2017 (cite: Motiyenko:2017dwa)]
- External data: 12CH3OH/13CH3OH ratio of 68  
  > "by scaling by a / ratio of 68 (cite: Milam:2005gt)" (Appendix Column Density) [from Milam et al. 2005 (cite: Milam:2005gt)]
- Simulation/model as data: MAGICKAL three-phase chemical model with warm-up timescales (fast/intermediate/slow) for gas-phase CH3OCH2OH abundance  
  > "was included in the three-phase chemical kinetics model *MAGICKAL* of (cite: Garrod:2013id)." (4.2 Chemical Modeling)

## Processing

### Calibration

- pipeline or manual: ALMA pipeline; self-calibration on line-free continuum channels  
  > "used to construct an initial continuum image model that was then used to iteratively self-calibrate the data." (2 Observations)
- casa version: CASA 4.7.2 (Cycle 3 data), CASA 5.1.1 (Cycle 4 data)  
  > "calibrated by the ALMA Cycle 4 pipeline (CASA 4.7.2)" (2 Observations); "calibrated by the ALMA Cycle 5 pipeline (CASA 5.1.1)" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: iterative self-cal using continuum model from line-free channels; solint not given  
  > "used to iteratively self-calibrate the data" (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uv-plane subtraction using relatively line-free channels  
  > "The same channels were also used to subtract the continuum emission in the uv-plane before the spectral cubes were imaged." (2 Observations)
- line free channels: _not stated_
- primary beam correction: applied  
  > "The data presented here have been corrected for primary beam attenuation." (2 Observations)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Cycle 3 calibration procedure  
  > "as described in (cite: Hunter:2017th)" (2 Observations) [from Hunter et al. 2017 (cite: Hunter:2017th)]
- Column density formalism for single-excitation model  
  > "following the formalism established in (cite: Hollis:2004uh)" (4 Results and Analysis) [from Hollis et al. 2004 (cite: Hollis:2004uh)]
- Optical depth correction  
  > "a correction was applied using the formalisms of (cite: Goldsmith:1999vg) and (cite: Turner:1991um)" (4 Results and Analysis) [from Goldsmith & Langer 1999; Turner 1991]
- Two-stage chemical modeling approach  
  > "The chemical modeling was performed using the two-stage approach described in (cite: Garrod:2013id)." (4.2 Chemical Modeling) [from Garrod 2013 (cite: Garrod:2013id)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for continuum and self-calibration
- Self-cal solution intervals and number of iterations
- Imaging task, weighting/robust, cell and image size, deconvolver
- Spectral resolution handling and exact beam-to-K conversion details
- Full list of the >two dozen transitions (only in Supplementary Information)
- Chemical network and reaction rates for the MAGICKAL runs
- Which transitions were used in the column density fit
- Line list/catalog for the other simulated species

## Analysis recipe

1. **Extract spectra and convert to K**: Spectra extracted at an offset position from the continuum peak; Jy/beam converted to K using the beam sizes  
  > "The spectra were converted from Jy/beam to K intensity scale in each spectral window using the beam sizes listed in Table [1](#obs)." (4 Results and Analysis)
   - parameter: position 17:20:53.373, -35:46:58.14, ~400 au west of MM1b  
  > "lies $\sim$400 au west of the brightest continuum peak" (4 Results and Analysis)
   - fitting: _not stated_
   - validation: _not stated_
2. **Column density by spectral simulation**: Single-excitation model fit of convolved spectra; N varied to minimize RMS error over unblended lines; optical depth correction  
  > "The excitation temperature was fixed to 200 K, and the column density was varied to minimize the RMS intensity error for unblended transitions." (4 Results and Analysis)
   - parameter: Tex = 200 K, linewidth 2.4 km/s, Tbg ~53 K (287 GHz), ~66 K (344 GHz)  
  > "and with a 2.4 km s$^{-1}$ linewidth (red)" (4 Results and Analysis)
   - parameter: detection threshold: >=10 sigma and not substantially blended  
  > "only features at least 10$\sigma$ above the RMS, and not substantially blended with another spectral feature, were considered significant" (4 Results and Analysis)
   - assumption: Source fills the beam; beam efficiency unity  
  > "We assume that the source fills the beam." (4 Results and Analysis)
   - fitting: Manual minimization of RMS intensity error; rotation diagram not used  
  > "made it difficult to extract physically-meaningful quantitative results from a rotation diagram analysis" (4 Results and Analysis)
   - validation: Simulations compared to Band 6 and 1'' Band 7 data  
  > "Because these profiles show remarkably good agreement even at twice the spatial resolution" (4 Results and Analysis)
3. **Partition function**: Rotational Q by direct summation; vibrational correction from Gaussian 09 B3LYP/6-311++G(d,p) frequencies  
  > "a geometry optimization and frequency analysis was performed using Gaussian 09 (cite: gaussian09B1) at the B3LYP/6-311++G(d,p) level" (Appendix Vibrational Partition Function)
   - software: Gaussian 09
   - fitting: _not stated_
   - validation: _not stated_
4. **Methanol column density for ratio**: Optically thin 13CH3OH vt=1 line at 282383 MHz, Tex=150 K, scaled by 12C/13C = 68  
  > "A column density of $N_T$ = $1.4\times10^{20}$ cm$^{-2}$ was then inferred by scaling by a / ratio of 68" (Appendix Column Density)
   - parameter: Tbg = 53 K, linewidth 2.8 km/s  
  > "A linewidth of 2.8 km s$^{-1}$ was fit to the lines." (Appendix Column Density)
   - fitting: _not stated_
   - validation: Viewed as an estimate and lower limit  
  > "this value should be viewed as an estimate and as a lower limit." (Appendix Column Density)
5. **Chemical modeling**: MAGICKAL with back-diffusion correction and Belloche et al. network; cold collapse then warm-up at three timescales  
  > "Phase 1 is a cold collapse to a maximum density of 2 x 10$^8$ cm$^{-3}$ and a dust grain temperature of 8 K." (4.2 Chemical Modeling)
   - software: MAGICKAL
   - fitting: _not stated_
   - validation: Compared with observed ratio  
  > "The observed ratio of : is estimated to be 1:34" (4.2 Chemical Modeling)

## Software

- **CASA** 4.7.2 and 5.1.1: Pipeline calibration  
  > "calibrated by the ALMA Cycle 4 pipeline (CASA 4.7.2)" (2 Observations)
- **Gaussian 09** Revision B.01: Vibrational frequencies for Qvib  
  > "performed using Gaussian 09 (cite: gaussian09B1)" (Appendix Vibrational Partition Function)
- **MAGICKAL** : Gas-grain chemical kinetics modeling  
  > "three-phase chemical kinetics model *MAGICKAL*" (4.2 Chemical Modeling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OCH2OH column density (Tex=200 K) | 4(2)e18 | ~60% | cm^-2 | 2 | The final derived value is $N_T$ = 4(2)$\times$10$^{18}$ cm$^{-2}$ at $T_{ex}$ = 200 K. |
| Abundance ratio to CH3OH | 1:34 | not stated | dimensionless | 4 | The observed ratio of : is estimated to be 1:34 |
| 13CH3OH column density | 1.95e18 | not stated | cm^-2 | 4 | The resulting column density was $N_T$ = $1.95\times10^{18}$ cm$^{-2}$. |
| CH3OH column density | 1.4e20 | lower limit | cm^-2 | 4 | A column density of $N_T$ = $1.4\times10^{20}$ cm$^{-2}$ was then inferred |
| Modeled peak CH3OCH2OH abundance (fast warm-up) | ~1e-12 | not stated | relative to H | 5 | with a maximum fractional abundance of $\sim$10$^{-12}$ with respect to total hydrogen |
| Qvib(300 K) | 5.33 | not stated | dimensionless | 3 | $Q_{vib}$\[300 K\] = 5.33 |

## Qualitative findings

- CH3OCH2OH spatial distribution is nearly identical across transitions, similar to but slightly more compact than CH3OH vt=1, and differs from g'Gg-ethylene glycol  
  > "Notably, the distribution of appears to be similar to, but slightly more compact than, that of  $v_t$=1." (4.1 Spatial Distributions)

## Claim tuples

- H: CH3OCH2OH is detectable in NGC 6334I MM1 | E: Spectral simulation against Band 6/7 ALMA data | R: More than two dozen unblended transitions above 10 sigma | F: First interstellar detection of methoxymethanol | **supported**
- H: Current models reproduce the observed abundance | E: MAGICKAL runs with three warm-up timescales | R: Model peak ~1e-12 vs observed ratio 1:34 to CH3OH | F: Models significantly underproduce CH3OCH2OH | **supported**
- H: CH3OCH2OH chemistry is tied to CH3OH | E: Integrated intensity maps | R: Similar distribution to CH3OH, different from other COMs | F: Suggestive of CH3O + CH2OH formation; not definitive | **partially**

## Reasoning

- Why this data: Band 7 0.2'' data had the most unblended features  
  > "This Band 7 data contained the largest number of unblended features" (4 Results and Analysis)
- Why this method: Spectral simulation used because methyl-rotor line profiles are non-Gaussian, preventing rotation diagrams  
  > "Instead, the convolved spectra were simulated using a single-excitation model" (4 Results and Analysis)
- Alternative: Rotation diagram analysis rejected due to non-Gaussian line profiles  
  > "made it difficult to extract physically-meaningful quantitative results from a rotation diagram analysis" (4 Results and Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Uncertainty from continuum subtraction due to lack of line-free channels; Tex assumed; abundance uncertain  
  > "the somewhat significant uncertainty introduced by the continuum subtraction due to the lack of line-free channels" (4 Results and Analysis)
- Caveat (inferred, ours): Tex fixed at 200 K, not fitted
- Caveat (inferred, ours): Source assumed to fill the beam while MM1 is structured
- Caveat (inferred, ours): Methanol column from optically thin 13CH3OH with assumed Tex and 12C/13C
- Caveat (inferred, ours): Fits by-eye/RMS minimization without formal errors
- Caveat (inferred, ours): Chemical model network not detailed

## Reproducibility

- Data public (paper): ALMA project codes acknowledged, but public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.A.00022.T," (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: Line-free channel selection
- Missing: Full transition list (Supplementary)
- Missing: Chemical network files
- Data volume (inferred): ~200-500 GB for four datasets (raw); less for calibrated products
- Score (inferred): 3/5, Data and column-density formalism are described, but imaging and calibration details and line list are incomplete.
- Rediscovery candidate: no, Imaging and channel selection details are missing, and the analysis was done by hand-tuned spectral simulation.

## Links

- Method: Hollis et al. 2004 (cite: Hollis:2004uh) (Column density formalism)
- Method: Hunter et al. 2017 (cite: Hunter:2017th) (Calibration of Cycle 3 data)
- Companion: Brogan et al. 2016 (cite: Brogan:2016cy) (NGC 6334I ALMA continuum and MM1/MM2 description)
- Companion: Motiyenko et al. 2017 (cite: Motiyenko:2017dwa) (Laboratory spectroscopy)

## Checks

```json
{
 "quotes": 63,
 "quotes_ok": 63,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 76,
  "stated": 45,
  "rate": 0.592
 },
 "evidence_ok": true
}
```
