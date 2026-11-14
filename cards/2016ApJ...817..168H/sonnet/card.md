# ALMA Observation of the 658 GHz Vibrationally Excited H2O Maser in Orion KL Source I

`2016ApJ...817..168H` | The Astrophysical Journal 2016 | first author: Hirota, Tomoya | arXiv: 1512.04148 | DOI: 10.3847/0004-637X/817/2/168

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: star_formation, astrochemistry
- Question: Is the 658 GHz vibrationally excited H2O line detected toward Orion KL Source I, what are its spatial and velocity structure, and does it arise from maser action at the base of the outflow/disk?  
  > "This line is clearly detected at the position of the massive protostar candidate, the Source I." (abstract)
- Target **Orion KL Source I**: coordinates Source I ~ RA 05h35m14s.518, Dec -05d22'30".54 (band 9 continuum)  
  > "The Orion Kleinmann-Low (cite: kleinmann1967) region is known as the nearest site of active massive-star formation at a distance of 420 pc (cite: menten2007; kim2008)." (Introduction); "05h35m14s.5182(4)" (Table 1); z/distance 420 pc  
  > "The Orion Kleinmann-Low (cite: kleinmann1967) region is known as the nearest site of active massive-star formation at a distance of 420 pc (cite: menten2007; kim2008)." (Introduction); "05h35m14s.5182(4)" (Table 1); distance from Menten et al. 2007; Kim et al. 2008  
  > "The Orion Kleinmann-Low (cite: kleinmann1967) region is known as the nearest site of active massive-star formation at a distance of 420 pc (cite: menten2007; kim2008)." (Introduction); "05h35m14s.5182(4)" (Table 1)

## Data provenance

- ALMA projects: 2011.0.00199.S
- bands: Band 9, Cycle 0  
  > "Observations with ALMA at band 9 were carried out during Cycle 0 at five epochs" (Observations)
- frequencies and spectral setup: 4 spws, 938 MHz bandwidth; line spws at 658.2 and 646.8 GHz, continuum spws at 640.6 and 662.2 GHz; 244 kHz, 3840 channels, 0.11 km/s  
  > "We observed four spectral windows (spw) in band 9 with bandwidths of 938 MHz for both of the linear polarizations." (Observations); "The spectral resolution and number of spectral channels were 244 kHz and 3840 channels, respectively." (Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 21-385 m (45-845 kλ)  
  > "Because the baseline length ranged from 21-385 m (45-845 k$\lambda$), extended structures of $>$5$''$  are resolved out." (Data analysis)
- angular resolution: 0.28"x0.25", PA -64 deg (natural weighting)  
  > "The synthesized beam size was 0.28$''$$\times$0.25$''$  at a position angle of -64 degrees using natural weighting." (Data analysis)
- max recoverable scale: structures >5" resolved out  
  > "extended structures of $>$5$''$  are resolved out." (Data analysis)
- sensitivity: 1.2 Jy/beam per line-free channel (1σ)  
  > "The resultant rms noise level for each line-free channel was 1.2 Jy beam$^{-1}$ (1$\sigma$) at 658 GHz" (Data analysis)
- time on source: 350 s  
  > "Total on-source time was 350 seconds" (Observations)
- observing dates: 2012 Aug 25 (one of five epochs)  
  > "we selected the Aug. 25, 2012 observation for analysis in the present paper" (Observations)
- pi or archival as stated: _not stated_
- Line: H2O v2=1, 1(1,0)-1(0,1) (658.006550 GHz)
- Line: H2O 9(7,3)-8(8,0) (645.766010 GHz)
- Line: H2O 9(7,2)-8(8,1) (645.950620 GHz)
- Other facility **CSO 10.4 m**: Single-dish 658 GHz line flux (300 Jy) for comparison  
  > "corresponding to the total flux denity of 300 Jy" (Spectral profile)
- External data: VLA 43 GHz continuum position of Source I, corrected for proper motion  
  > "the absolute position is calculated from that in 2009 January 12 and corrected for the measured proper motion to the epoch of the ALMA data" (Table 1) [from (cite: goddi2011)]
- External data: Rest frequencies and lower-state energies of H2O lines  
  > "at a rest frequency of 658.006550 GHz (cite: chen2000)" (Observations) [from (cite: chen2000)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: Calibrated visibilities delivered by EA-ARC  
  > "We used the calibrated visibility data delivered by the East Asia ALMA Regional Center (EA-ARC) to make synthesized images." (Data analysis)
- flux calibrator: Callisto (flux); J0423-013 bandpass; J0607-085 gain  
  > "Bandpass, flux, and gain calibrators were J0423-013, Callisto, and J0607-085, respectively." (Observations)
- flux scale uncertainty: ~50% total; J0607-085 flux fixed to 0.64 Jy, 658 GHz spw scaled by 0.42  
  > "In summary, the total flux calibration uncertainty is $\sim$50% for both of the 658 GHz H$_{2}$O line and continuum data" (Flux density scale)
- self calibration: On peak channel (13.0 km/s): phase-only 5 s, then phase+amp 30/72 s; applied to all channels/spws  
  > "First we solved only for phase solutions, with a short integration time of 5 seconds." (Data analysis)

### Imaging

- task: CASA clean  
  > "with the CASA task `clean` and `gaincal`" (Data analysis)
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "using natural weighting" (Data analysis)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: CASA uvcontsub3 after cvel Doppler tracking  
  > "subtracted the continuum emission from the calibrated visibility data using the CASA task `uvcontsub3`" (Data analysis)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: channel map made by integrating 9 channels (~1 km/s)  
  > "we also made a lower-resolution channel map by integrating 9 velocity channels ($\sim$1 km s$^{-1}$)" (Data analysis)
- final beam: 0.28"x0.25", PA -64 deg  
  > "Convolved with a synthesized beam of 0.28$''$$\times$0.25$''$  with a position angle of -64 deg." (Table 1)
- final rms: 1.2 Jy/beam (1.6 in emission channels)  
  > "although it increases to 1.6 Jy beam$^{-1}$ (1$\sigma$) at the channels with significant emission" (Data analysis)

### Inherited from earlier work

- Primary beam pointing error 0.6" taken from ALMA Cycle 0 Technical Handbook  
  > "If we consider a possible pointing error of 0.6$''$  as described in the ALMA Cycle 0 Technical Handbook" (Flux density scale) [from ALMA Cycle 0 Technical Handbook]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges for uvcontsub3
- Clean masks, iterations, threshold, cell and image size
- Polynomial order of continuum fit
- Moment-map clipping thresholds
- Exact brightness-temperature calculation and beam used
- Which flux scaling was applied before reported flux densities

## Analysis recipe

1. **Doppler tracking and continuum subtraction**: cvel to rest frequency, then uvcontsub3 on line-free channels  
  > "We first conducted Doppler tracking with the CASA task `cvel`, setting the rest frequency to 658.006550 GHz." (Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Self-calibration**: Solve on peak channel, phase then amp+phase, apply to all  
  > "These phase and amplitude solutions were applied to rest of the spectral channels, including other spws for continuum data by using the CASA task `applycal`." (Data analysis)
   - software: CASA
   - parameter: solint 5 s then 30/72 s  
  > "We then self-calibrated the data with longer integration times (30 or 72 seconds)" (Data analysis)
   - fitting: _not stated_
   - validation: _not stated_
3. **Image cube, moment maps, continuum**: clean cube at 0.11 km/s; immoments for moment 0/1; continuum from line-free channels  
  > "The moment 0 and 1 maps were made using the CASA task `immoments`" (Data analysis)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Measure positions and sizes**: Single Gaussian fits with imfit to continuum and moment 0; AIPS SAD per channel for centroids  
  > "we performed a two dimensional Gaussian fit to determine peak positions using the AIPS task SAD" (Absolute and relative positional accuracy)
   - software: CASA, AIPS
   - fitting: Single 2D Gaussian  
  > "The source size of the 658 GHz H$_{2}$O channel map at 13.0 km s$^{-1}$ is derived to be 0.42$''$$\times$0.31$''$  by the two-dimensional Gaussian fitting of the image." (Results and discussion, Spectral profile)
   - validation: Compared with VLA 43 GHz position: offsets 40 and 20 mas  
  > "We find that the position offset of the band 9 continuum relative to the VLA 43 GHz data are 40 mas and 20 mas in right ascension and declination" (Absolute and relative positional accuracy)
5. **Flux scale correction and brightness temperature**: Primary beam correction 8.6; spw flux rescaled by 0.64/1.51; Tb from peak flux and fitted source size  
  > "The brightness temperature of the 658 GHz H$_{2}$O line is calculated to be 2$\times$10$^{4}$ K or higher, as the emission region is unresolved with the ALMA beam." (Spectral profile)
   - assumption: J0607-085 flux density 0.64 Jy  
  > "In this paper, we employ the absolute flux density of J0607-085 to be 0.64 Jy." (Flux density scale)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Synthesis imaging, self-calibration, cvel, uvcontsub3, imfit, immoments  
  > "Synthesis imaging and self-calibration were done using the Common Astronomy Software Applications (CASA) package in a standard manner." (Data analysis)
- **AIPS** : Plotting, image analysis, SAD Gaussian fits per channel  
  > "Part of the data plotting and image analysis were made by using the Astronomical Image Processing System (AIPS) package." (Data analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak flux density of 658 GHz line | 940 | ~50% | Jy | 5 | The peak flux density is 940 Jy at the LSR velocity of 13.0 km s$^{-1}$. |
| Brightness temperature lower limit | >2e4 | not stated | K | 5 | The brightness temperature of the 658 GHz H$_{2}$O line is calculated to be 2$\times$10$^{4}$ K or higher |
| Moment 0 size (FWHM) | 0.525x0.384 | 0.010, 0.009 | arcsec | 4 | 0.525(10)$\times$0.384(9) |
| Moment 0 position angle | 44.6 | 1.2 | deg | 4 | 44.6$\pm$1.2 degrees |
| Band 9 continuum flux density of Source I (observed) | 1.04 | 0.04 | Jy | 4 | 1.04$\pm$0.04 Jy and 0.77$\pm$0.03 Jy beam$^{-1}$ |
| Primary-beam-corrected continuum flux density | 8.9 | 50% | Jy | 5 | the absolute flux density is calculated to be 8.9 Jy, with an uncertainty of 50% |
| Absolute position uncertainty | ~50 | not stated | mas | 4 | the absolute position uncertainty of Source I in the present ALMA band 9 continuum observations is $\sim$50 mas |

## Qualitative findings

- Line is not related to the 22 GHz supermaser; no emission at the Compact Ridge  
  > "Thus, the 658 GHz H$_{2}$O line is not related to the 22 GHz supermaser phenomenon" (Relationship between the 22 GHz H$_{2}$O supermaser)
- The 646 GHz lines are not detected  
  > "but they are not detected in Orion KL" (abstract)

## Claim tuples

- H: Is the 658 GHz H2O line a maser from the base of the Source I outflow/disk? | E: Imaging at 0.26" and measuring Tb, morphology, and velocity gradient | R: Compact ~100 AU, elongated NE-SW, perpendicular velocity gradient, Tb>2e4 K | F: Maser emission from the base of the outflow in a rotating, expanding disk | **supported**
- H: Is the ALMA flux different from the CSO flux? | E: Compare ALMA flux with CSO 300 Jy | R: ALMA is a factor of 3 higher | F: May indicate variability; monitoring needed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Source I is outside the primary beam, giving ~50% flux uncertainty; limited resolution  
  > "Due to the large ($\sim$50%) flux uncertainty of Source I (which is outside the primary beam)" (Continuum emission at ALMA band 9)
- Caveat (inferred, ours): Primary beam correction of 8.6 at the beam edge is very uncertain
- Caveat (inferred, ours): Possible flux calibration problem at 658 GHz in this epoch
- Caveat (inferred, ours): Centroid structure may be a resolution artifact

## Reproducibility

- Data public (paper): Cycle 0 project data cited; archive-delivered calibrated data used  
  > "We used the calibrated visibility data delivered by the East Asia ALMA Regional Center (EA-ARC) to make synthesized images." (Data analysis)
- Products in archive: _not stated_
- Missing: Line-free channel ranges
- Missing: Clean parameters and masks
- Missing: CASA version
- Data volume (inferred): ~10-50 GB for the single epoch
- Score (inferred): 3/5, Data are public and the recipe is outlined, but many imaging parameters and the flux treatment are unspecified.
- Rediscovery candidate: no, Many imaging parameters are missing and the flux scale is ambiguous, though the data are public.

## Links

- Companion: Hirota et al. 2014a (cite: hirota2014a) (321 and 336 GHz H2O lines in Source I with ALMA)

## Checks

```json
{
 "quotes": 59,
 "quotes_ok": 59,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 41,
  "rate": 0.594
 },
 "evidence_ok": true
}
```
