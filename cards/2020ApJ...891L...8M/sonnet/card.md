# The Formation Height of Millimeter-wavelength Emission in the Solar Chromosphere

`2020ApJ...891L...8M` | The Astrophysical Journal Letters 2020 | first author: Martínez-Sykora, Juan | arXiv: 2001.10645 | DOI: 10.3847/2041-8213/ab75ac

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: sun
- Question: Where in the solar atmosphere do ALMA band 3 and band 6 emission form in rMHD models with ambipolar diffusion and non-equilibrium ionization, and how well does brightness temperature trace gas temperature?  
  > "Key for the interpretation of solar ALMA observations is understanding where in the solar atmosphere the ALMA emission originates." (abstract)
- Target **Plage/network region in 2.5D Bifrost simulations (gol_lte, gol_nei); observed chromospheric hole region (ALMA band 3, 2017/04/27)**: coordinates heliocentric 170'', -210''  
  > "The IRIS observing program was centered at heliocentric coordinates of 170$''$, -210$''$" (Alternative observational interpretations); z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2016.1.00202.S
- bands: Band 3 (3 mm, 100 GHz) observation  
  > "he ALMA interferometric data were acquired on 2017/04/27 in Band 3 (at 3mm, i.e., 100 GHz) in configuration C40-3" (Alternative observational interpretations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C40-3  
  > "in configuration C40-3" (Alternative observational interpretations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: 10.5 minute scans, 2 s integration, 37 min total within 16:00-16:45 UT  
  > "ALMA obtained 10.5 minute scans separated by 2min calibration scans, with 2s integration time, for a total of 37min within 16:00-16:45 UT (45 minutes)." (Alternative observational interpretations)
- observing dates: 2017/04/27  
  > "he ALMA interferometric data were acquired on 2017/04/27 in Band 3" (Alternative observational interpretations)
- pi or archival as stated: _not stated_
- Other facility **IRIS**: Mg II k 2796 Å spectroheliogram and SJI of same region  
  > "Both ALMA and IRIS observed the same region through a coordinated ALMA/IRIS campaign" (Alternative observational interpretations)
- Other facility **SDO/AIA and HMI**: 171 Å images and magnetograms  
  > "The SDO/HMI magnetograms (panel B and green contours) confirm that these fibrils do indeed connect to a strong magnetic field region" (Alternative observational interpretations)
- External data: ALMA band 3 observations and analysis of chromospheric holes  
  > "Further details of the ALMA observational analysis can be found in (cite: Loukitcheva:2019ApJ...877L..26L)." (Alternative observational interpretations) [from (cite: Loukitcheva:2019ApJ...877L..26L)]
- External data: Mean Tb difference between ALMA bands of 1400 K over whole Sun  
  > "This is similar to the difference in mean brightness temperature between the two ALMA bands of 1400 K in the veraged over the whole Sun (cite: White:2017SoPh..292...88W)." (Conclusions and discussion) [from (cite: White:2017SoPh..292...88W)]
- Simulation/model as data: Bifrost 2.5D rMHD simulations gol_lte and gol_nei, 90 Mm wide, 14 km horizontal grid, -3 to 40 Mm height, ~190 G mean field plage  
  > "The horizontal resolution is uniform with a $14$ km grid spacing" (Numerical simulations)

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

- Simulation setup and analysis  
  > "Further details on the setup and analysis of these two simulations can be found in (cite: Martinez-Sykora:2019hhegol)" (Numerical simulations) [from (cite: Martinez-Sykora:2019hhegol)]
- ALMA observation reduction and analysis  
  > "Further details of the ALMA observational analysis can be found in (cite: Loukitcheva:2019ApJ...877L..26L)." (Alternative observational interpretations) [from (cite: Loukitcheva:2019ApJ...877L..26L)]

### Not stated but needed to reproduce (our reading)

- Simulation snapshot data and Bifrost output access
- STiC version and exact frequency/opacity settings
- Definition of the formation height and tau=1 computation details
- ALMA calibration and imaging details for the observation
- Snapshot selection and time sampling for statistics

## Analysis recipe

1. **Synthesize ALMA intensities**: LTE module of STiC computes continuum opacity and emergent intensity at 1.2 and 3 mm from simulation electron density and gas pressure  
  > "STiC utilizes the electron densities and gas pressure stratifications from the simulations to compute the partial densities of all species that are involved in the calculations." (Synthesis of ALMA observations)
   - software: STiC
   - assumption: Free-free hydrogen absorption main opacity source  
  > "which include the main opacity source at mm wavelengths (free-free hydrogen absorption" (Synthesis of ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Compute tau=1 formation heights and compare Tb with gas temperature**: Optical depth at 1.2 and 3 mm, tau=1 heights averaged over 12 minutes, JPDFs of Tb vs T, contribution and source functions, comparison with VAL-C  
  > "we computed the optical depth ($\tau$) at 1.2 and 3mm wavelengths (ALMA bands 6 and 3, respectively)." (Formation height of ALMA observations)
   - software: IDL
   - fitting: _not stated_
   - validation: Compared with VAL-C atmosphere  
  > "For comparison we add, for both ALMA wavelengths, the height at which the optical depth is unity for a VAL-C (cite: Vernazza:1981yq) atmosphere" (Formation height of ALMA observations)

## Software

- **STiC** : Synthetic ALMA intensities in LTE module  
  > "we used the LTE module in the tockholm inversion code (STiC) code" (Synthesis of ALMA observations)
- **Bifrost** : rMHD simulations  
  > "These simulations have been calculated with the 3D rMHD *Bifrost* code" (Numerical simulations)
- **IDL** : Data analysis  
  > "To analyze the data we have used IDL." (Acknowledgments)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean formation height 1.2 mm, LTE | 0.9 | std 0.7 Mm | Mm | 2 | the average formation height at wavelengths of 1.2mm is 0.9 Mm (with a standard deviation of 0.7 Mm) |
| Mean formation height 3 mm, LTE | 1.8 | std 1 Mm | Mm | 2 | the average formation height at 3mm is 1.8 Mm (standard deviation of 1 Mm) |
| Mean formation height 1.2 mm, NEI | 2.67 | ±1.08 | Mm | 2 | n average the 1.2mm emission is formed at a height of $2.67\pm1.08$ Mm |
| Mean formation height 3 mm, NEI | 2.78 | ±1.09 | Mm | 2 | the 3mm emission is formed at a mean height of $2.78\pm1.09$ Mm |
| Mean Tb difference 3 mm vs 1.2 mm, NEI | 1280 | not stated | K | 2 | The mean brightness temperature difference between the two wavelengths is $1280$ K. |

## Qualitative findings

- In NEI both bands form at similar heights in the upper chromosphere, mostly in spicules and fibrils along canopy fields  
  > "In our NEI model, the formation height of ALMA at both wavelengths occurs at greater heights than in LTE models." (Conclusions and discussion)

## Claim tuples

- H: Do bands 3 and 6 form at significantly different heights? | E: tau=1 heights from LTE and NEI rMHD simulations | R: LTE difference 0.92 Mm; NEI 0.11±0.3 Mm | F: With NEI both bands form at similar upper-chromospheric heights | **supported**
- H: Can chromospheric holes be explained by cool low-lying loops? | E: Compare simulations with ALMA, IRIS, SDO observations | R: Fibril-like features in all three; simulated loops reach 3500-4500 K | F: Holes may be cool sub-threads in low-lying loops | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Model is 2D and may limit LOS superposition  
  > "We note that our model is limited to two dimensions, and it is crucial to expand this model into 3D." (Conclusions and discussion)
- Caveat (inferred, ours): Observational interpretation is qualitative, no forward-modelled comparison to the ALMA data
- Caveat (inferred, ours): 2.5D models only
- Caveat (inferred, ours): Formation height definition and snapshot statistics unclear

## Reproducibility

- Data public (paper): ALMA data public  
  > "We used the publicly available data ADS/JAO.ALMA#2016.1.00202.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Simulation outputs (gol_lte, gol_nei)
- Missing: STiC settings
- Data volume (inferred): small for ALMA; simulations large and external
- Score (inferred): 2/5, Main results depend on simulations not provided; ALMA only used for a qualitative comparison.
- Rediscovery candidate: no, Main results come from unreleased simulations, not ALMA data.

## Links

- Method: (cite: delaCruzRodriguez:2019A&A...623A..74D) (STiC code)
- Companion: (cite: Martinez-Sykora:2019hhegol) (Describes the simulations)
- Companion: (cite: Loukitcheva:2019ApJ...877L..26L) (ALMA chromospheric holes observation)
- Related: IRIS
- Related: SDO

## Checks

```json
{
 "quotes": 32,
 "quotes_ok": 32,
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
  "facts": 62,
  "stated": 23,
  "rate": 0.371
 },
 "evidence_ok": true
}
```
