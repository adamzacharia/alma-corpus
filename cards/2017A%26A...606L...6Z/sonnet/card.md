# Detection of a new methanol maser line with ALMA

`2017A&A...606L...6Z` | Astronomy and Astrophysics 2017 | first author: Zinchenko, I. | arXiv: 1709.08889 | DOI: 10.1051/0004-6361/201731752

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Identify a very bright, apparently non-thermal line at ~349.1 GHz toward S255IR-SMA1, determine its nature (maser), location, kinematics and variability  
  > "In our ALMA data we noticed a very bright, apparently non-thermal line toward this object." (Introduction)
- Target **S255IR (SMA1 clump, YSO S255 NIRS3)**: coordinates _not stated_; z/distance 1.78 (+0.12/-0.11) kpc  
  > "located at the distance of $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)" (Introduction); distance from Burns16  
  > "located at the distance of $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.00500.S
- bands: Band 7 (0.8 mm), two epochs in Cycle 4  
  > "Observations of the S255 IR region were carried out with ALMA in Band 7 at two epochs during Cycle 4" (2 Observations)
- frequencies and spectral setup: 4 FDM spws centred ~335.4, 337.3, 349.0, 346.6 GHz; bandwidths 1875.0, 234.4, 937.5, 1875.0 MHz; maser in the 349.0 GHz spw; 0.244 MHz channels, 0.42 km/s with Hanning smoothing  
  > "Four Frequency Division Mode (FDM) spectral windows centered at around 335.4 GHz, 337.3 GHz, 349.0 GHz, and 346.6 GHz, with bandwidths of 1875.0 MHz, 234.4 MHz, 937.5 MHz, and 1875.0 MHz, respectively" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Epoch 1: C36-2/3 (2016 Apr 21); Epoch 2: C40-6 (2016 Sep 9)  
  > "The first observing epoch on 2016 April 21, carried out with the 12-meter array in its C36-2/3 configuration" (2 Observations)
- baselines: 15-612 m (epoch 1); 15-3143 m (epoch 2)  
  > "baselines ranging between 15 and 3143 m" (2 Observations)
- angular resolution: 0.10" x 0.15"  
  > "The resulting images achieve an angular resolution of $0{\ensuremath{''}}10\times 0{\ensuremath{''}}15$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016 April 21 and 2016 September 9  
  > "The second epoch of observations on 2016 September 9" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CH3OH 14_1 - 14_0 A-+ (maser) (349.1070 GHz)
- Line: CH3OH 16_1 - 15_2 A- (thermal comparison) (345.90397 GHz)
- Other facility **JVLA and EVN (6.7 GHz masers, Moscadelli17)**: 6.7 GHz methanol maser and 5 GHz continuum positions for comparison  
  > "reported several clusters of the 6.7 GHz maser spots observed with the JVLA and EVN" (3 Results)
- Other facility **SMA**: 2010 detection of CH3OH 13_1-13_0 A-+ in quasi-thermal emission (Zin15)  
  > "in our SMA data obtained in December 2010, the CH$_3$OH $13_{1} - 13_{0}$ A$^{- +}$ line at 342.729796 GHz was detected in quasi-thermal emission" (4 Discussion)
- External data: 6.7 GHz maser cluster and 5 GHz continuum positions  
  > "the position of their 5 GHz radio continuum as well as those of the dominating pre-/post-burst 6.7 GHz methanol maser clusters labeled as P and A" (3 Results) [from Moscadelli17]
- External data: Spectral line catalogs used for line identification (CDMS, JPL)  
  > "An inspection of the major catalogs of spectral lines (Cologne Database for Molecular Spectroscopy, CDMS" (3 Results) [from Mueller01; Mueller05; Pickett98]

## Processing

### Calibration

- pipeline or manual: ALMA manual or pipeline calibration (not specified which)  
  > "Data were first calibrated through the ALMA manual or pipeline calibration process." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Epoch 1: J0750+1231 (flux), J0854+2006 (bandpass); epoch 2: J0510+1800 for both  
  > "For the second epoch, J0510+1800 was used for both bandpass and flux calibration purposes." (2 Observations)
- flux scale uncertainty: ~5% for Band 7 (ALMA Cycle 4 Technical Handbook)  
  > "the absolute flux calibration for band 7 is at a level of about 5% based on the ALMA Cycle 4 Technical Handbook" (3 Results)
- self calibration: Phase-only, two iterations (240 s, 60 s) on continuum from the 335.4 GHz spw; applied to all spws; 30% dynamic range improvement  
  > "Two iterations of self-calibration with solution intervals set to 240s and 60s were than performed for deriving refined phase gains." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting with a robust parameter of 0.5" (2 Observations)
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
- final beam: 0.10" x 0.15"  
  > "The resulting images achieve an angular resolution of $0{\ensuremath{''}}10\times 0{\ensuremath{''}}15$" (2 Observations)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version
- Whether manual or pipeline calibration was used for each execution block
- Which channels/spw were excluded as contaminated for the continuum image
- Self-calibration details (cell size, image size, masks, number of clean iterations, SNR thresholds)
- Cell and image size, deconvolver, cleaning thresholds and masks for line cubes
- Continuum subtraction method for line cubes
- Whether epochs were combined for the images in the figures
- Rest frequency/velocity reference (LSRK) and systemic velocity
- Rms noise of the cubes
- How the 3900 K brightness temperature was computed (beam, Rayleigh-Jeans)

## Analysis recipe

1. **Calibrate and self-calibrate**: ALMA calibration, then phase self-calibration from the wide continuum spw, solutions applied to all spws  
  > "The self-calibration gain solutions were then applied to all spectral windows for further imaging processes." (2 Observations)
   - software: CASA
   - parameter: solution intervals 240 s and 60 s  
  > "solution intervals set to 240s and 60s" (2 Observations)
   - fitting: _not stated_
   - validation: 30% improvement in continuum dynamic range  
  > "The final continuum image has a 30% improvement in the dynamic range as compared to the first image." (2 Observations)
2. **Image line cubes and identify line**: Briggs-weighted imaging; line identified by checking CDMS and JPL catalogs  
  > "shows that the most probable identification is the CH$_3$OH $14_{1} - 14_{0}$ A$^{- +}$ line at 349.1070 GHz" (3 Results)
   - software: CASA
   - parameter: robust = 0.5  
  > "Briggs weighting with a robust parameter of 0.5" (2 Observations)
   - assumption: Rest frequency of the CH3OH 14_1-14_0 A-+ line assumed for channel maps  
  > "by assuming that the rest frequency equals to that of the CH$_3$OH $14_{1} - 14_{0}$ A$^{- +}$ line" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
3. **Map morphology and kinematics**: Channel maps, peak spectrum, moment 0 and 1 maps compared with thermal methanol line and continuum  
  > "This gradient, best demonstrated by the 1st moment map of the emission in Fig. [3](#fig:maps)c" (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
4. **Test variability between epochs**: Compare visibility amplitude vs baseline length of the peak channel (~4 km/s) for the three execution blocks  
  > "We instead compare the visibility amplitudes of the maser emission observed at different epochs." (3 Results)
   - assumption: Band 7 absolute flux accuracy ~5%  
  > "the absolute flux calibration for band 7 is at a level of about 5%" (3 Results)
   - fitting: _not stated_
   - validation: Checked that amplitude branches arise from different uv sampling  
  > "We verify that it is because these visibilities from the two epochs are sampling different parts (direction) of the $uv$ domain." (3 Results)

## Software

- **CASA** : All data calibration and reduction  
  > "All data calibration and reduction were carried out with the Common Astronomy Software Applications (cite: McMullin07)." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak brightness of maser line | 5.9 | not stated | Jy/beam | 3 | The brightness reaches about 5.9 Jy/beam, which corresponds to about 3900 K |
| Brightness temperature at peak | ~3900 | not stated | K | 3 | The brightness reaches about 5.9 Jy/beam, which corresponds to about 3900 K |
| Width of brightest maser feature | ~2.5 | not stated | km/s | 3 | The width of the brightest maser feature is about 2.5 km s$^{-1}$. |
| Peak flux density integrated over ~1" circle | ~25 | not stated | Jy | 3 | The peak flux density integrated over a circle of about 1$^{\prime\prime}$ in size is about 25 Jy |
| Single-channel emission size at peak velocity (~2.34 km/s) | 0.17" x 0.08" (~300 x 140 AU) | not stated | arcsec | 3 | it is about $0.17\ensuremath{''}\times 0.08\ensuremath{''}$ ($\sim 300\times 140$ AU) |

## Qualitative findings

- Maser emission spans about -1 to 8 km/s with the peak moving toward north-north-west; velocity gradient in the same sense as disk rotation  
  > "strong line emission emerges at about -1 km s$^{-1}$ spanning to $\sim 8$ km s$^{-1}$ and its peak location gradually moves toward north-north-west direction" (Results)

## Claim tuples

- H: The very bright 349.1 GHz line toward S255IR-SMA1 is a maser of methanol | E: Line identification with CDMS/JPL; brightness temperature estimate | R: Peak 5.9 Jy/beam (~3900 K), >10x brighter than other lines; best match CH3OH 14_1-14_0 A-+ | F: Newly discovered, previously unpredicted methanol maser line | **supported**
- H: The new maser belongs to Class II | E: Qualitative arguments from level populations and comparison with the 6.7 GHz maser | R: Same velocity range and position-velocity dependence as 6.7 GHz maser | F: Classified as Class II methanol maser | **partially**
- H: The maser is variable on a months timescale | E: Compare visibility amplitudes across epochs | R: Consistent amplitudes on baselines <180 m; consistent in overlapping uv regions | F: No variation above ~5% in total flux density over several months | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Nearby lines of acetone, vinyl cyanide, aminoacetonitrile, dimethyl ether rejected because they have never been reported to show strong maser emission  
  > "which have never been reported to manifest strong maser emission" (3 Results)
- How they decided it was enough: _not stated_
- Limitation (authors): No long-baseline sampling in April, so variability at scales <0.4" cannot be tested; further modeling and monitoring needed  
  > "We have no sampling at long baselines in April to differentiate or identify any flux density variation at angular scales significantly less than $0{\ensuremath{''}}4$." (3 Results)
- Caveat (inferred, ours): Line identification rests on catalog match without independent confirmation from other transitions in the series
- Caveat (inferred, ours): Class II assignment is qualitative, with no maser modeling
- Caveat (inferred, ours): Rest frequency/velocity scale is assumed from the identification
- Caveat (inferred, ours): Brightness temperature depends on the beam and is not documented

## Reproducibility

- Data public (paper): Data from ALMA project 2015.1.00500.S; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00500.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version
- Missing: Line cube imaging parameters
- Missing: Self-calibration imaging details
- Missing: Moment map thresholds and method
- Data volume (inferred): ~100-300 GB raw (three execution blocks, Band 7)
- Score (inferred): 5/5, Data are identifiable and the basic recipe is given, but key CASA parameters are missing and the results are mostly qualitative.
- Rediscovery candidate: no, Main results are partly qualitative and imaging parameters are incomplete, although data are likely public.

## Links

- Method: McMullin07 (CASA)
- Companion: Moscadelli17 (6.7 GHz methanol maser clusters in S255IR NIRS3 for comparison)
- Companion: Zin15 (Earlier SMA study of S255IR-SMA1)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
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
  "facts": 67,
  "stated": 34,
  "rate": 0.507
 },
 "evidence_ok": true
}
```
