# Sulphur monoxide exposes a potential molecular disk wind from the planet-hosting disk around HD 100546

`2018A&A...611A..16B` | Astronomy and Astrophysics 2018 | first author: Booth, Alice S. | arXiv: 1712.05992 | DOI: 10.1051/0004-6361/201731347

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, astrochemistry
- Question: Is SO detectable in the planet-hosting transition disk HD 100546, where is it located, and does it trace a disk wind?  
  > "We present the first detection of SO in the planet-hosting disk around HD 100546 from ALMA Cycle 0 observations gaining insight into the molecular content and structure of transition disks." (Introduction)
- Target **HD 100546**: coordinates _not stated_; z/distance 109 (+4/-3) pc  
  > "HD 100546 is a $2.4~M_\odot$ Herbig Be star (cite: Ancker1998) at a distance of $109^{+~4}_{-~3}$ $pc$ (cite: Gaia1; Gaia2)" (2 HD 100546); distance from Gaia (Gaia Collaboration 2016a,b)  
  > "HD 100546 is a $2.4~M_\odot$ Herbig Be star (cite: Ancker1998) at a distance of $109^{+~4}_{-~3}$ $pc$ (cite: Gaia1; Gaia2)" (2 HD 100546)
- Target **HD 97048**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2011.0.00863.S
- bands: Band 7 (SO lines at 301-346 GHz)  
  > "Rest frequency (GHz) | 301.286 | 304.078 | 344.311 | 345.704" (Table 1)
- frequencies and spectral setup: native spectral resolution 0.24 km/s (Hanning smoothed), imaged also at 1 km/s  
  > "The individual lines were each imaged at the spectral resolution of the observations (0.24 km s$^{-1}$, applying Hanning smoothing) and then at a coarser resolution of 1 km s$^{-1}$." (3 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21 - 375 m  
  > "Baselines | 21 - 375 m" (Table 1)
- angular resolution: 1.1'' x 0.6'' (stacked beam)  
  > "Synthesised beam | 1.1$''$ $\times$ 0.6$''$" (Table 1)
- max recoverable scale: _not stated_
- sensitivity: stacked rms 4.2 mJy/beam/channel at 1 km/s  
  > "r.m.s noise (channel$^{-1}$ mJy beam$^{-1}$) | 10.9 | 9.9 | 17.4 | 16.2 | 4.2" (Table 1)
- time on source: _not stated_
- observing dates: 18th November 2012  
  > "Date observed | 18th November 2012" (Table 1)
- pi or archival as stated: _not stated_
- Line: SO 7_7-6_6 (301.286 GHz)
- Line: SO 7_8-6_7 (304.078 GHz)
- Line: SO 8_8-7_7 (344.311 GHz)
- Line: SO 3_2-1_2 (345.704 GHz)
- External data: Disk position angle 146 deg and inclination 44 deg for HD 100546  
  > "host to a bright disk with a position angle of $146^{\circ}$ and an inclination of $44^{\circ}$ (cite: Walsh2014)" (2 HD 100546) [from (cite: Walsh2014)]
- External data: CO J=3-2 source velocity 5.7 km/s and CO image used for comparison and as matched filter  
  > "The source velocity of the emission, as inferred from the CO $J=3-2$ emission (cite: Walsh2014; walsh2017), is 5.7 km s$^{-1}$." (4.1 Detected SO emission) [from (cite: Walsh2014; walsh2017)]
- External data: SO line frequencies and Einstein A coefficients from CDMS and LAMDA; collisional rates  
  > "The values for the line frequencies and Einstein A coefficients are from the Cologne Database for Molecular Spectroscopy (cite: 2001A&A...370L..49M) and the Leiden Atomic and Molecular Database (cite: 2005A&A...432..369S)." (3 Observations) [from (cite: 2001A&A...370L..49M; 2005A&A...432..369S; 2006A&A...450..399L)]
- Simulation/model as data: HD 100546 physical disk structure used as input to LIME (from earlier work)  
  > "simulated emission generated using a HD 100456 physical disk structure (Figure 6) and LIME version 1.5 (cite: 2010A&A...523A..25B)" (5 Modelling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Uses self-calibrated, phase-corrected, continuum-subtracted measurement sets from Walsh et al. 2014  
  > "this work uses the self-calibrated, phase-corrected and continuum subtracted measurements sets." (3 Observations)

### Imaging

- task: CASA 4.6.0 CLEAN; lines stacked in uv plane via regridspw and concat  
  > "The line emission was imaged at a velocity resolution of $1~km~s^{-1}$ using the CLEAN algorithm with natural weighting" (3 Observations)
- deconvolver: _not stated_
- weighting robust: natural  
  > "Weighting | natural" (Table 1)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: channel-by-channel mask guided by the CO J=3-2 emission (3 sigma)  
  > "a channel by channel mask guided by the spatial extent of the CO $J=3-2$ emission (3$\sigma$)" (3 Observations)
- multiscale scales: _not stated_
- continuum subtraction: Data already continuum subtracted  
  > "this work uses the self-calibrated, phase-corrected and continuum subtracted measurements sets." (3 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing; 1 km/s channels  
  > "(0.24 km s$^{-1}$, applying Hanning smoothing)" (3 Observations)
- final beam: 1.1'' x 0.6'', PA 24 deg (stacked)  
  > "Synthesised beam | 1.1$''$ $\times$ 0.6$''$" (Table 1)
- final rms: 4.2 mJy/beam/channel (stacked)  
  > "The emission reaches a peak S/N of 6 with an r.m.s. noise of 4.2 mJy beam$^{-1}$ channel$^{-1}$." (4.1 Detected SO emission)

### Inherited from earlier work

- Continuum and CO data calibration/self-calibration from earlier analysis  
  > "The continuum and CO line emission from this data have already been analysed (cite: Walsh2014)" (3 Observations) [from (cite: Walsh2014)]
- Matched filter method for uv-plane line detection  
  > "We use a matched filter code[^1] developed for interferometric data sets to confirm the detection of the two SO lines" (4.2 Matched filter) [from (cite: loomis2017)]

### Not stated but needed to reproduce (our reading)

- Cell size, image size, and channel-mask details for imaging
- CASA calibration and self-calibration details (inherited from Walsh 2014)
- Flux calibrator and flux uncertainty
- Matched filter implementation parameters and noise normalization
- LIME model grid, number of photons/points, disk structure details (gas density and temperature profiles)
- How the wedge angular range was chosen beyond 'by eye'
- Inner/outer SO radii adopted in the LIME model beyond 20-100 au
- Observed line-ratio uncertainty derivation

## Analysis recipe

1. **Image SO lines and stack**: Image each line, shift spw to SO line frequency with regridspw, concat in uv plane, CLEAN natural weighting at 1 km/s  
  > "These measurement sets were then concatenated using the CASA task `concat`." (3 Observations)
   - software: CASA
   - parameter: Only 7_7-6_6 and 7_8-6_7 stacked; 8_8-7_7 excluded since it increased noise  
  > "Including the $J=8_8-7_7$ transition in the stacking increased the noise level in the channel maps thus degrading the S/N in the resulting images." (3 Observations)
   - fitting: _not stated_
   - validation: Checked velocity frame, line frequencies, removal of 5-10% of baselines, and image-plane stacking; double-peaked profile persists  
  > "we checked the removal of 5% to 10% of the longer and shorter baselines and the double-peaked line profile persists." (4.1 Detected SO emission)
2. **Moment maps of disk and wind components**: Moment zero maps over -7.5 to -2.5 km/s (wind) and -2.5 to 4.5 km/s (disk)  
  > "Figure 4 shows the integrated intensity maps from -7.5 km s$^{-1}$ to -2.5 km s$^{-1}$ and from -2.5 km s$^{-1}$ to 4.5 km s$^{-1}$." (4.1 Detected SO emission)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Matched filter detection and relative line intensities**: Cross-correlate uv visibilities with CO image (scaled to 1/4) and best-fit LIME model as filters  
  > "We use the CLEAN image of the CO line ($J=3-2$) and the best fit LIME model (see Section 5 for details) as filters." (4.2 Matched filter)
   - software: vis_sample, matched filter code
   - parameter: CO filter compression factors 1/2, 1/3, 1/4 tested  
  > "We tested different CO filters with different compression factors of 1/2, 1/3 and 1/4." (4.2 Matched filter)
   - fitting: _not stated_
   - validation: Compared different filters; response consistent for 7_8-6_7  
  > "We found that the $J=7_8-6_7$ transition is picked up in all the filters but the higher excitation lines have an improved response with the more compact filters." (4.2 Matched filter)
4. **Constrain density and temperature from line ratios**: RADEX grid of line ratios over temperature and density compared to matched filter ratios  
  > "The line ratios of the three lines were calculated over a grid of temperatures and densities and the results are shown in Figure 7." (5 Modelling)
   - software: RADEX
   - parameter: SO column density 1e14 cm^-2  
  > "assuming an SO column density of 10$^{14}$ cm$^{-2}$ motivated by full chemical models" (5 Modelling)
   - assumption: Isothermal homogeneous medium, no velocity gradient; matched filter response proportional to intensity  
  > "assuming an isothermal, homogeneous medium with no significant velocity gradient" (5 Modelling)
   - fitting: Visual comparison of grids; no formal fit  
  > "These model line ratios were compared to the observed line ratios taken from the matched filter responses." (Modelling the SO disk emission using LIME)
   - validation: _not stated_
5. **Derive SO abundance with LIME**: LIME LTE ray-tracing with full-disk and 45 deg wedge models; vary SO abundance to match peak integrated intensities  
  > "A set of models were run varying the fractional abundance of SO with respect to H$_2$." (5 Modelling)
   - software: LIME
   - parameter: Distance, inclination, PA of source; SO in 20-100 au layer above midplane  
  > "These conditions result in the SO being distributed in a ring from 20 to 100 au in a layer above the mid-plane" (5 Modelling)
   - assumption: LTE (critical density 6e6 cm^-3 at 100 K for 7_7-6_6); only near surface of disk modelled  
  > "The critical density for the SO $J=7_{7}-6_{6}$ transition was determined to be $6~\times~10^{6}$ cm$^{-3}$ at 100 K" (5 Modelling)
   - fitting: Manual abundance adjustment; wedge position picked by eye from residuals  
  > "the optimal position picked by eye from the residual maps" (5 Modelling)
   - validation: Residual maps and model vs observed line profiles  
  > "The residual maps of the observed integrated intensity minus the model integrated intensity for the two lines are shown in Figure 8." (5 Modelling)

## Software

- **CASA** 4.6.0: Imaging, regridspw, concat  
  > "Imaging of the data was done using Common Astronomy Software Application (CASA) version 4.6.0." (3 Observations)
- **LIME** 1.5: Radiative transfer modelling of SO emission  
  > "LIME version 1.5 (cite: 2010A&A...523A..25B)" (5 Modelling)
- **RADEX** : Model line ratios over temperature/density grid  
  > "Model line ratios were calculated from line intensities determined using the RADEX radiative transfer code" (5 Modelling)
- **vis_sample** : Matched filter code sampling model in uv plane  
  > "vis_sample is publicly available at: <https://github.com/AstroChem/vis_sample>" (4.2 Matched filter)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak S/N of integrated intensity, 7_7-6_6 and 7_8-6_7 | 7 and 11 | not stated | dimensionless | 1 | detected with a peak S/N of 7 and 11 respectively in the integrated intensity |
| Stacked channel map peak emission | 24.7 | rms 4.2 | mJy/beam | 1 | Peak emission (mJy beam$^{-1}$) / \- / \- / \- / \- / 24.7 |
| Matched filter peak responses with CO filter (7_8-6_7, 7_7-6_6, 8_8-7_7) | 6.8, 4.2, 4.0 | not stated | sigma | 3 | They have a peak response of 6.8, 4.2 and 4.0 respectively. |
| Observed line ratios (7_8-6_7/7_7-6_6, 7_8-6_7/8_7-7_6, 7_7-6_6/8_7-7_6) | 1.5, 1.6, 1.1 | ±0.4 each | dimensionless | 3 | 1.5$\pm$0.4 / 1.6$\pm$0.4 / 1.1$\pm$0.4 |
| Best-fit H2 density and gas temperature | 1e8-1e10 cm^-3; 50-100 K | not stated | cm^-3; K | 4 | a H$_2$ density between 10$^8$ to 10$^{10}$ cm$^{-3}$ and a gas temperature between 50 and 100 K |
| SO fractional abundance, full disk model | 3.5e-7 | not stated | wrt H2 | 5 | A model for a full disk was calculated with a fractional abundance of 3.5$\times$ $10^{-7}$ with respect to H$_2$ |
| SO fractional abundance, 45 deg wedge model | 5.0e-6 | not stated | wrt H2 | 5 | A fractional abundance of 5.0$\times$ $10^{-6}$ with respect to H$_2$ resulted in a peak intensity |
| HD 97048 stacked rms (non-detection) | 6 | not stated | mJy/beam | 1 | reaches an r.m.s. noise of 6 mJy beam$^{-1}$ |

## Qualitative findings

- SO emission is more compact than CO and has an excess blue-shifted component not consistent with Keplerian disk emission, attributed to a disk wind  
  > "The blue-shifted emission peaks off source spectrally and spatially and it is attributed to a disk wind" (4.1 Detected SO emission)
- Disk SO emission is asymmetric, peaking north-east, coincident with CO hot-spot and possible warp  
  > "This is coincident with a ‘hot-spot’ observed in CO emission relating to a possible disk warp (cite: walsh2017)." (6.1 Location and abundance)

## Claim tuples

- H: Is SO detectable in the HD 100546 disk? | E: Imaging, uv stacking and matched filtering of Cycle 0 Band 7 data | R: Two lines detected in image plane; three detected with matched filter | F: First detection of SO in HD 100546 disk | **supported**
- H: Does SO trace a molecular disk wind? | E: Line profile and moment map analysis, comparison with CO | R: Blue-shifted off-source component at about -5 km/s | F: SO may trace a molecular disk wind | **partially**
- H: What SO abundance is required? | E: LIME models of full disk and wedge | R: 5e-6 wrt H2 for wedge, above dark cloud value ~1e-8 | F: Energetic processes may release refractory sulphur | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Accretion shock from a circumplanetary disk as alternative explanation  
  > "An alternative explanation for the SO emission is that it is the result of an accretion shock due to a circumplanetary disk." (6.3 What is the SO tracing?)
- How they decided it was enough: _not stated_
- Limitation (authors): Emission is the same size as the beam so disk and wind components cannot be disentangled; model kinematics mismatch  
  > "Further refinement of the disk emission component requires better data as the emission is the same size scale as the beam." (5 Modelling)
- Caveat (inferred, ours): Detections are low S/N (5-7 sigma) near beam size, so wind interpretation is tentative
- Caveat (inferred, ours): Wedge position chosen by eye and abundance degenerate with density
- Caveat (inferred, ours): Matched-filter ratios used as intensities with large errors
- Caveat (inferred, ours): Blue-shift could have other explanations, e.g. warp

## Reproducibility

- Data public (paper): ALMA Cycle 0 archive data acknowledged  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00863.S" (Acknowledgements)
- Products in archive: _not stated_
- Code: vis_sample matched filter code publicly available on GitHub  
  > "vis_sample is publicly available at: <https://github.com/AstroChem/vis_sample>" (footnote)
- Missing: LIME disk structure and model setup
- Missing: Self-calibrated measurement sets from Walsh 2014
- Missing: Matched filter parameters
- Data volume (inferred): ~10-50 GB (Cycle 0 Band 7 single EB)
- Score (inferred): 3/5, Data public and steps described, but LIME model and imaging details are underspecified.
- Rediscovery candidate: no, Disk model and manual choices (wedge by eye, matched filter) are not fully specified.

## Links

- Method: (cite: loomis2017) (Matched filter technique)
- Method: (cite: 2010A&A...523A..25B) (LIME)
- Companion: (cite: Walsh2014) (Original analysis of continuum and CO from the same data)
- Companion: (cite: walsh2017) (CO kinematics and possible warp)
- Companion: (cite: 2016Walsh) (HD 97048 Cycle 0 data)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 82,
  "stated": 49,
  "rate": 0.598
 },
 "evidence_ok": true
}
```
