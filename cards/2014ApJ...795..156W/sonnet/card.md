# ALMA Observations of the Antennae Galaxies. I. A New Window on a Prototypical Merger

`2014ApJ...795..156W` | The Astrophysical Journal 2014 | first author: Whitmore, Bradley C. | arXiv: 1410.4473 | DOI: 10.1088/0004-637X/795/2/156

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, star_formation
- Question: What is the CO (3-2) morphology and kinematics of the Antennae overlap region at 0.5'' resolution, and how do CO knots compare with radio and HST clusters in an evolutionary classification of cluster formation?  
  > "The goal of this paper is to present the data and to briefly examine both large- and small-scale features in the Cycle 0 ALMA CO (3-2) observations." (1 Introduction)
- Target **Antennae galaxies (NGC 4038/39) overlap region**: coordinates _not stated_; z/distance 22 Mpc (distance modulus 31.71 mag); 1'' = 107 pc  
  > "In this paper we adopt a distance modulus of 31.71 mag for the Antennae, as found by Schweizer et al. (2008) based on the Type Ia supernova 2007SR." (1 Introduction); distance from Schweizer et al. (2008), SN Ia 2007sr  
  > "In this paper we adopt a distance modulus of 31.71 mag for the Antennae, as found by Schweizer et al. (2008) based on the Type Ia supernova 2007SR." (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00876.S
- bands: Band 7 (345 GHz)  
  > "Using the “Band 7" (345 GHz) receiver, observations of CO (3-2), HCO$^+$ (4-3), HCN (4-3), and the $\sim$850 $\mu$m dust continuum emission were made simultaneously." (2.1 Data and Reductions)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, max baseline ~400 m, 13-point mosaic  
  > "The array was used in its extended (maximum baseline $\sim$400 m) configuration to obtain a 13-point mosaic" (2.1 Data and Reductions)
- baselines: _not stated_
- angular resolution: 0.56''x0.43'' synthesized beam  
  > "The CO (3-2) data cube has 5 km s$^{-1}$ channels and a synthesized beam $0.56\ensuremath{''}\times0.43\ensuremath{''}$." (2.1 Data and Reductions)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: ten mosaic executions April-October 2012, 14-22 antennas  
  > "The entire mosaic was observed by ALMA ten times between April and October 2012, with between 14 and 22 antennae operational." (2.1 Data and Reductions)
- pi or archival as stated: _not stated_
- Line: CO 3-2 (not stated)
- Other facility **HST**: BVIJH, Halpha, Pabeta images and cluster ages/extinctions (Whitmore et al. 2010)  
  > "in particular broad- (*BVIJH*) and narrow-band data (H$_{\alpha}$ and Pa$_{\beta}$) taken with *HST*" (abstract)
- Other facility **VLA**: 3.6 cm radio continuum, archival project AN079, ~15 microJy/beam  
  > "The VLA data was taken from archival project AN079, and has roughly 15 microJy/beam sensitivity." (6 Small-Scale Structure)
- External data: Cluster ages, extinctions, I-band magnitudes  
  > "The cluster properties were taken from Whitmore et al. (2010)." (Table 1) [from Whitmore et al. 2010]
- External data: Preliminary CO knot catalog (positions, peaks, velocities)  
  > "Based on preliminary catalog from Leroy et al. 2014 (i.e., Paper 2)." (Table 1) [from Leroy et al. 2014]

## Processing

### Calibration

- pipeline or manual: CASA standard Cycle 0 procedures  
  > "We reduced and calibrated the data using CASA (Common Astronomy Software Applications)[^3] following the standard procedures for Cycle 0 data reduction." (2.1 Data and Reductions)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan; phase calibrators J1215-175 or J1159-224  
  > "Titan was observed in each track and used to set the overall flux scale of the observations." (2.1 Data and Reductions)
- flux scale uncertainty: ~10%  
  > "The accuracy of ALMA’s flux calibration at 345 GHz is estimated to be $\approx$10%." (2.1 Data and Reductions)
- self calibration: CO averaged over 500 km/s into one plane, cleaned, model used with 10 min solution interval  
  > "the data were iteratively self-calibrated by averaging the CO line emission across a 500 km s$^{-1}$ channel into a single plane image" (2.1 Data and Reductions)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The data were imaged using Briggs weighting with the robustness parameter set to 0.5." (2.1 Data and Reductions)
- uv taper: _not stated_
- cell size: 0.08''  
  > "The final calibrated data were imaged on a $600\times1000$ pixel grid of $0.08\ensuremath{''}$ pixels." (2.1 Data and Reductions)
- image size: 600x1000 pixels  
  > "The final calibrated data were imaged on a $600\times1000$ pixel grid of $0.08\ensuremath{''}$ pixels." (2.1 Data and Reductions)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.56''x0.43'', 5 km/s channels  
  > "The CO (3-2) data cube has 5 km s$^{-1}$ channels and a synthesized beam $0.56\ensuremath{''}\times0.43\ensuremath{''}$." (2.1 Data and Reductions)
- final rms: _not stated_

### Inherited from earlier work

- Continuum and HCN/HCO+ analysis deferred to Paper 3; CO cloud catalog from Paper 2  
  > "Brogan et al. (2014; Paper 3) will describe the ALMA 850 $\mu$m continuum maps and the dense gas tracers HCN (4-3) and HCO$^{+}$ (4-3)." (2.1 Data and Reductions) [from Brogan et al. 2014 (Paper 3); Leroy et al. 2014 (Paper 2)]
- Standard Cycle 0 CASA reduction  
  > "following the standard procedures for Cycle 0 data reduction" (2.1 Data and Reductions) [from standard Cycle 0 procedures]

### Not stated but needed to reproduce (our reading)

- CASA version
- clean threshold, masking and number of iterations
- Which of the ten executions/calibrators were used and flagging
- Continuum subtraction and line-free channels
- Primary-beam correction details
- Rest frequency and velocity convention
- RMS noise of the cube
- Final catalog of Leroy et al. (preliminary, unpublished)
- Radio image reduction and astrometric alignment details
- Rules for assigning evolutionary stages

## Analysis recipe

1. **Calibrate, self-calibrate and image CO (3-2) cube**: CASA standard reduction, Briggs imaging, self-calibration on 500 km/s collapsed CO image  
  > "After initial imaging, the data were iteratively self-calibrated by averaging the CO line emission across a 500 km s$^{-1}$ channel into a single plane image" (2.1 Data and Reductions)
   - software: CASA
   - parameter: robust 0.5; 0.08'' pixels; 5 km/s channels; 10 min solint  
  > "the resulting model was used to carry out an additional calibration using a 10 minute solution interval." (2.1 Data and Reductions)
   - fitting: _not stated_
   - validation: RMS and peak constant within ~10% before and after self-calibration  
  > "The RMS in signal-free regions and the peak intensity remained approximately constant (within $\approx$10%) before and after the self-calibration." (2.1 Data and Reductions)
2. **Make moment maps and identify filaments/knots**: Moment 0, 1, 2 maps; CPROPS for CO peaks and velocities  
  > "The CO peak value and velocities were measured with the CPROPS program (Rosolowsky & Leroy 2006)." (6 Small-Scale Structure)
   - software: CPROPS
   - fitting: _not stated_
   - validation: _not stated_
3. **Align HST and VLA to ALMA and compare cluster properties**: Match Pabeta emission to 3.6 cm and HST; clusters brighter than I=24 within 1.2''x1.2'' box  
  > "We estimate relative astrometric precision between the three systems is better than $\approx$0.1$''$." (6 Small-Scale Structure)
   - parameter: 24x24 pixel box (1.2'', 130 pc), twice beam size  
  > "This box size was chosen in order to roughly match a value of twice the $0.56''\times0.43''$ synthesized beam size." (6 Small-Scale Structure)
   - assumption: distance 22 Mpc  
  > "This modulus corresponds to a distance of 22 Mpc, hence 1$''$ is equivalent to 107 pc." (1 Introduction)
   - fitting: _not stated_
   - validation: _not stated_
4. **Assign evolutionary stages and estimate timescales/age spread**: Classify by presence of CO, radio, optical continuum and line emission; compare stage counts with timescale-predicted fractions assuming constant formation rate  
  > "assuming a roughly constant cluster formation rate, we can determine whether our expected time scales are reasonable by simply counting the number of objects in each of the six stages." (7.2 Quick Census)
   - assumption: roughly constant cluster formation rate  
  > "assuming a roughly constant cluster formation rate" (7.2 Quick Census)
   - fitting: _not stated_
   - validation: Compared with Kawamura et al. 2009 and Miura et al. 2012  
  > "Kawamura et al. (2009) estimate a 20–30 Myr lifetime for GMCs in regions with recent star formation for their LMC data set" (7.3 Age Spread)

## Software

- **CASA** : calibration and imaging  
  > "We reduced and calibrated the data using CASA (Common Astronomy Software Applications)" (2.1 Data and Reductions)
- **CPROPS** : CO peak and velocity of knots  
  > "The CO peak value and velocities were measured with the CPROPS program (Rosolowsky & Leroy 2006)." (6 Small-Scale Structure)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| L-T Filament length | 3 | not stated | kpc | 2 | The L-T Filament is approximately 3 kpc long and has a width of $\approx$100 pc (i.e., an aspect ratio of $30/1$). |
| L-T Filament ensemble velocity dispersion | 11 (7 without southernmost knot) | not stated | km/s | 2 | i.e., 11 km s$^{-1}$ if all the knots are included or 7 km s$^{-1}$ if the most southerly knot |
| SGMC2 velocity range of knots | 1388-1631 | not stated | km/s | 2 | we find 12 CO knots in this region, with a range of velocities between 1388 and 1631 km s$^{-1}$ |
| W10-3 ensemble velocity dispersion | 25 | not stated | km/s | 2 | This region has an ensemble velocity dispersion = 25 km s$^{-1}$ |
| Observed stage fractions 1/2/3 (1? as 1) | 23%/23%/55% | not stated | dimensionless | 4 | \[N/sample size = 5/22, 5/22, 12/22\] = \[23%, 23%, 55%\] |
| Maximum cluster age spread in complex | ~10 | not stated | Myr | 4 | our current estimate for an upper limit for the age spread in typical cluster complexes is $\approx$10 Myr |

## Qualitative findings

- Discovery of a long thin low-dispersion CO filament that breaks into knots  
  > "We report on the discovery of a long (3 kpc), thin (aspect ratio 30/1), filament of CO gas which breaks up into roughly ten individual knots." (abstract)

## Claim tuples

- H: Do Antennae CO structures differ in kinematics across regions? | E: Moment maps and CPROPS knot velocities for L-T Filament and SGMC2 | R: L-T knots ~10 km/s dispersion; SGMC2 10-80 km/s | F: Filament is kinematically cold, SGMC2 is the opposite extreme | **supported**
- H: CO, radio and HST emission trace an evolutionary sequence of cluster formation | E: Visual multiwavelength comparison of 26 regions, stage classification | R: Regions fit stages 0-5 well except crowded SGMC2 | F: Classification is a useful framework | **supported**
- H: Stage timescales match counted stage populations | E: Count of 22 regions vs timescale-predicted fractions | R: Agreement only if '1?' regions are reclassified as stage 2 | F: Reasonable agreement, uncertain | **partially**
- H: GMC destruction timescale in cluster complexes | E: Age spread of coexisting stages | R: Stages 0-4 coexist, no stage 5 associated | F: ~10 Myr within ~200 pc | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Small sample, selection effects, superposition and low-number statistics  
  > "These include selection and completeness effects; the possibility that many of the clusters may be destroyed with time" (7.2)
- Caveat (inferred, ours): Stage assignment is visual and subjective, radio strengths estimated by eye
- Caveat (inferred, ours): Sample is CO-selected, so older stages are truncated
- Caveat (inferred, ours): Constant formation rate assumption and small N
- Caveat (inferred, ours): Relies on unpublished preliminary catalog

## Reproducibility

- Data public (paper): Cycle 0 ALMA data cited by project code; VLA archival AN079  
  > "This paper also used archival VLA data from project AN079." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Final CO cloud catalog (Paper 2)
- Missing: CASA version and clean parameters
- Missing: Stage assignment criteria beyond qualitative description
- Missing: Whitmore et al. 2010 cluster catalog access
- Data volume (inferred): ~50-200 GB raw for ten executions of 13-field mosaic
- Score (inferred): 4/5, Imaging recipe partly given but main results are largely qualitative/visual classification and depend on unpublished catalog.
- Rediscovery candidate: no, Main results are qualitative classification relying on unpublished catalogs.

## Links

- Method: Rosolowsky & Leroy 2006 (CPROPS cloud properties)
- Companion: Leroy et al. 2014 (Paper 2) (CO cloud survey and scaling laws)
- Companion: Brogan et al. 2014 (Paper 3) (850 um continuum, HCN and HCO+)
- Companion: Johnson et al. 2014 (Paper 4) (Firecracker proto super star cluster)
- Companion: Whitmore et al. 2015 (Paper 5) (Evolutionary classification system)
- Related: HST Antennae cluster catalog (Whitmore et al. 2010)

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 36,
  "rate": 0.522
 },
 "evidence_ok": true
}
```
