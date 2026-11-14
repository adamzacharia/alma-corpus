# Hidden molecular outflow in the LIRG Zw 049.057

`2018A&A...609A..75F` | Astronomy and Astrophysics 2018 | first author: Falstad, N. | arXiv: 1711.05321 | DOI: 10.1051/0004-6361/201732088

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: nearby_galaxies
- Question: Investigate the molecular gas distribution and kinematics in the nucleus of Zw 049.057 to confirm and locate the molecular outflow.  
  > "We aim to investigate the molecular gas distribution and kinematics in the nucleus of Zw 049.057 in order to confirm and locate the molecular outflow" (abstract)
- Target **Zw 049.057**: coordinates CO 6-5 690 GHz continuum peak R.A.=15h13m13.092s, decl.=+07d13m31.84s (J2000)  
  > "at a distance of $56$ Mpc (linear scale: ${\sim}270$ pc/arcsec)" (1.1 A highly obscured nucleus in Zw 049.057); "We adopt a redshift of $z=0.012999$, corresponding to a velocity of $3897$ km s$^{-1}$, determined in the ESO nearby Abell cluster survey (cite: kat98)" (1.1 A highly obscured nucleus in Zw 049.057); z/distance z=0.012999; 56 Mpc  
  > "at a distance of $56$ Mpc (linear scale: ${\sim}270$ pc/arcsec)" (1.1 A highly obscured nucleus in Zw 049.057); "We adopt a redshift of $z=0.012999$, corresponding to a velocity of $3897$ km s$^{-1}$, determined in the ESO nearby Abell cluster survey (cite: kat98)" (1.1 A highly obscured nucleus in Zw 049.057); distance from redshift from ESO nearby Abell cluster survey (Katgert et al. 1998)  
  > "at a distance of $56$ Mpc (linear scale: ${\sim}270$ pc/arcsec)" (1.1 A highly obscured nucleus in Zw 049.057); "We adopt a redshift of $z=0.012999$, corresponding to a velocity of $3897$ km s$^{-1}$, determined in the ESO nearby Abell cluster survey (cite: kat98)" (1.1 A highly obscured nucleus in Zw 049.057)

## Data provenance

- ALMA projects: 2013.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: Four spectral windows of 2 GHz each, 15.6 MHz frequency resolution  
  > "Four spectral windows each covered a bandwidth of $2$ GHz (${\sim}750$ km s$^{-1}$ at the frequency of CO $J=6-5$), with a frequency resolution of $15.6$ MHz." (Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: 12 m array, 37 antennas  
  > "with a total of 37 antennas in the $12$ m array" (Observations and data reduction)
- configurations: _not stated_
- baselines: 17.5 to 555.5 m  
  > "with baselines between $17.5$ and $555.5$ m" (Observations and data reduction)
- angular resolution: 0.23" x 0.21" (PA ~15 deg)  
  > "The resulting beam size is $0.23\ensuremath{''}\,\times\,0.21\ensuremath{''}$ (PA ${\sim}15\ensuremath{^\circ}$)." (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: 15 mJy/beam per 20 km/s channel  
  > "the final sensitivity achieved was $15$ mJy beam$^{-1}$ per $20$ km s$^{-1}$ (${\sim}46$ MHz) channel" (Observations and data reduction)
- time on source: 272 s  
  > "The total on-source time for the observations was $272$ s" (Observations and data reduction)
- observing dates: 2015 May 19  
  > "The data were taken on 2015 May 19" (Observations and data reduction)
- pi or archival as stated: Archival, PI N. Lu  
  > "obtained from the ALMA archive (project 2013.1.00524.S, PI N. Lu)" (Observations and data reduction)
- Line: CO J=6-5 (not stated)
- Other facility **VLA**: 4.65 and 6.0 GHz continuum and OH absorption lines  
  > "to observe the $\Lambda$-doublet transitions in the first two rotationally excited states of OH, as well as the radio continuum" (1.1 A highly obscured nucleus in Zw 049.057)
- Other facility **SMA**: CO J=2-1 and 230 GHz continuum  
  > "to observe the $J=2-1$ transition of CO" (1.1 A highly obscured nucleus in Zw 049.057)
- Other facility **HST**: NICMOS/WFC3 images of the jet-like dust feature  
  > "seen in *Hubble* Space Telescope (HST) NICMOS (cite: sco00) and WFC3 (Gallagher, priv. comm.) images" (4.4 Is the outflowing molecular gas entrained by a radio jet?)
- External data: Herschel far-IR OH, H2O and [O I] results for comparison  
  > "in their *Herschel* far-infrared and submillimeter observations of Zw 049.057, (cite: fal15) found evidence of a highly obscured nucleus" (1.1 A highly obscured nucleus in Zw 049.057) [from (cite: fal15)]
- External data: 1.4 GHz total flux density 51 mJy used for jet power  
  > "the flux density of the total source at $1.4$ GHz is $51$ mJy" (4.4 Is the outflowing molecular gas entrained by a radio jet?) [from (cite: baa06)]

## Processing

### Calibration

- pipeline or manual: Pipeline calibration, no major effort to improve flux calibration  
  > "we made no major effort to improve the flux calibration with respect to the results from the pipeline" (2.3 ALMA)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: uncertain to a factor of about 2  
  > "Thus, the flux calibration is uncertain to a factor of about 2." (2.3 ALMA)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robustness 0.5  
  > "For the imaging we used briggs weighting with a robustness factor of 0.5." (2.3 ALMA)
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
- final beam: 0.23" x 0.21", PA ~15 deg  
  > "The resulting beam size is $0.23\ensuremath{''}\,\times\,0.21\ensuremath{''}$ (PA ${\sim}15\ensuremath{^\circ}$)." (2.3 ALMA)
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- Calibrator names for ALMA data (blank in text)
- CASA version
- Continuum-subtraction method and line-free channels for CO 6-5
- Cell and image size, deconvolution threshold, masking
- Integration ranges and systemic velocity definition for wing maps
- Spectrum extraction region

## Analysis recipe

1. **Image CO 6-5 and 690 GHz continuum**: Calibrate and image archival data in CASA with Briggs weighting  
  > "The CASA package was used for calibration and imaging of the data set." (2.3 ALMA)
   - software: CASA
   - parameter: robust 0.5  
  > "For the imaging we used briggs weighting with a robustness factor of 0.5." (2.3 ALMA)
   - fitting: _not stated_
   - validation: Astrometry checked via calibrator peak positions vs catalogue, <0.05"  
  > "The astrometric accuracy was estimated by comparing the peak positions of the calibrators to their catalog positions and turned out to be $<0.05\ensuremath{''}$." (2.3 ALMA)
2. **Extract line wings and map their emission**: Integrated spectrum over emitting region; integrated intensity maps over line wings (200-350 km/s beyond systemic)  
  > "The bottom panel shows the integrated intensity maps taken over the line wings ($200-350$ km s$^{-1}$ beyond the systemic velocity)" (3.3 CO J=6-5 line and 690 GHz continuum emission)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration and imaging of ALMA, SMA and VLA data  
  > "The CASA package was used for calibration and imaging of the data set." (2.3 ALMA)
- **GILDAS** : Acknowledged as used in the research  
  > "This research has made use of NASA’s Astrophysics Data System (ADS) and of GILDAS software" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CO 6-5 line wings extent beyond systemic | at least 350 | not stated | km/s | 2 | There are clear line wings extending at least $350$ km s$^{-1}$ beyond the systemic velocity |
| 690 GHz continuum peak position | R.A.=15h13m13.092s, decl.=+07d13m31.84s | not stated | J2000 | 2 | which peaks at $\mathrm{R.A.}=15^{\mathrm{h}}13^{\mathrm{m}}13^{\mathrm{s}}.092$, $\mathrm{decl.}=+07\ensuremath{^\circ}13\ensuremath{'}31\ensuremath{''}.84$ |
| CO 6-5 outflow position angle | ~105 | not stated | deg | 2 | the nuclear CO $J=6-5$ outflow (PA ${\sim}105\ensuremath{^\circ}$) does not have the same position angle as the radio feature (PA ${\sim}130\ensuremath{^\circ}$) |

## Qualitative findings

- CO 6-5 wing emission is oriented roughly perpendicular to the overall rotation, supporting an outflow.  
  > "The wing emission is oriented along an axis that is approximately perpendicular to the overall rotation of the CO $J=6-5$ and $J=2-1$ emission." (3.3 CO J=6-5 line and 690 GHz continuum emission)

## Claim tuples

- H: Do the CO line wings trace a nuclear molecular outflow? | E: Compare SMA CO 2-1, ALMA CO 6-5 and VLA OH absorption line profiles and morphology | R: CO wings to ±300 km/s; ALMA wings spatially separated perpendicular to rotation; OH blue wings to -300 km/s | F: Wings are signatures of a nuclear molecular outflow | **supported**
- H: Is the outflow related to the minor-axis radio feature? | E: Compare CO 6-5 wing PA with radio feature PA | R: PA ~105 vs ~130 deg | F: Association possible but unconfirmed | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wings could be rapidly rotating gas rather than an outflow; outflow favoured due to OH blue wings at similar velocity.  
  > "Although this could also be interpreted as a signature of rapidly rotating gas in the center of the the nucleus" (4.3 A nuclear outflow)
- How they decided it was enough: _not stated_
- Limitation (authors): Large resolution difference between CO 6-5 and 2-1 precludes detailed excitation analysis.  
  > "the large difference in angular resolution between the CO $J=6-5$ and $J=2-1$ observations complicates the matter, precluding a detailed analysis" (4.3 A nuclear outflow)
- Caveat (inferred, ours): ALMA flux calibration uncertain by factor 2 and only 272 s on source
- Caveat (inferred, ours): Blue wing reaches the band edge, so wing extent is a lower limit
- Caveat (inferred, ours): Outflow interpretation is qualitative; no mass or rate estimated

## Reproducibility

- Data public (paper): ALMA data obtained from the archive  
  > "The CO $J = 6-5$ data set was obtained from the ALMA archive" (2.3 ALMA)
- Products in archive: _not stated_
- Missing: Calibrator names
- Missing: CASA version
- Missing: Wing velocity integration limits relative to defined systemic velocity
- Missing: Imaging parameters beyond robust
- Data volume (inferred): ~5-20 GB
- Score (inferred): 3/5, Public data and robust given, but ALMA processing is thinly described and results are mostly qualitative.
- Rediscovery candidate: no, ALMA recipe is incomplete and results largely qualitative.

## Links

- Companion: (cite: fal15) (Herschel far-IR study of Zw 049.057)

## Checks

```json
{
 "quotes": 43,
 "quotes_ok": 43,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 3,
 "numeric_problems": 0,
 "fill": {
  "facts": 60,
  "stated": 31,
  "rate": 0.517
 },
 "evidence_ok": true
}
```
