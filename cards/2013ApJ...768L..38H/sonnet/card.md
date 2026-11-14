# Submillimeter H<SUB>2</SUB>O Maser in Circinus Galaxy—a New Probe for the Circumnuclear Region of Active Galactic Nuclei

`2013ApJ...768L..38H` | The Astrophysical Journal Letters 2013 | first author: Hagiwara, Yoshiaki | arXiv: 1305.0076 | DOI: 10.1088/2041-8205/768/2/L38

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: Is there 321 GHz H2O maser emission in the Circinus galaxy, and how does it compare with the known 22 GHz maser?  
  > "In this work, we present the observation of the 321 GHz H$_{2}$O$\;$maser emission in Circinus galaxy, obtained using Atacama Large Millimeter/submillimeter Array (ALMA) in the Cycle 0 program." (INTRODUCTION)
- Target **Circinus galaxy**: coordinates RA(J2000)=14h13m09.906s, Dec=-65d20m20.468s (tracking center)  
  > "The tracking center of the galaxy was $\alpha$(J2000) = 14$^{\rm h}$13$^{\rm m}$09$^{\rm s}$.906" (2 OBSERVATIONS AND DATA REDUCTION); "at a distance of 4.2 $\pm$ 0.8 Mpc is a nearby spiral lying behind the Galactic plane(cite: free77)" (INTRODUCTION); z/distance 4.2 ± 0.8 Mpc; systemic velocity 433 km/s  
  > "The tracking center of the galaxy was $\alpha$(J2000) = 14$^{\rm h}$13$^{\rm m}$09$^{\rm s}$.906" (2 OBSERVATIONS AND DATA REDUCTION); "at a distance of 4.2 $\pm$ 0.8 Mpc is a nearby spiral lying behind the Galactic plane(cite: free77)" (INTRODUCTION); distance from Freeman et al. 1977 (cite: free77)  
  > "The tracking center of the galaxy was $\alpha$(J2000) = 14$^{\rm h}$13$^{\rm m}$09$^{\rm s}$.906" (2 OBSERVATIONS AND DATA REDUCTION); "at a distance of 4.2 $\pm$ 0.8 Mpc is a nearby spiral lying behind the Galactic plane(cite: free77)" (INTRODUCTION)

## Data provenance

- ALMA projects: 2011.0.00121.S
- bands: Band 7 (321 GHz line)  
  > "based on the capabilities of Cycle 0 observations in Band 7." (2 OBSERVATIONS AND DATA REDUCTION)
- frequencies and spectral setup: One dual-polarization spectral window, 1.875 GHz bandwidth, 3840 channels, 488.3 kHz (0.458 km/s) resolution at 319.4 GHz, ~1760 km/s coverage  
  > "single dual polarization spectral window (1.875 GHz bandwidth), divided into 3840 spectral channels, yielding spectral resolutions of 488.3 kHz or 0.458 km s$^{-1}\;$at the observed frequency of 319.4 GHz." (2 OBSERVATIONS AND DATA REDUCTION)
- continuum bandwidth: _not stated_
- arrays: 18 antennas  
  > "Observations lasted for 49 minutes (approximately 25 minutes on-source) with 18 antennas." (2 OBSERVATIONS AND DATA REDUCTION)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 0.66 x 0.51 arcsec, PA -17 deg  
  > "the synthesized beam size was 0$\ensuremath{''}.66 \times 0\ensuremath{''}$.51 (P.A.= –17$\ensuremath{^\circ}$)" (2 OBSERVATIONS AND DATA REDUCTION)
- max recoverable scale: _not stated_
- sensitivity: line rms ~9–11 mJy/beam per channel; continuum rms ~0.8 mJy/beam  
  > "The rms noise level of spectral line maps in natural weight was $\sim$9–11 mJy beam$^{-1}$  per spectral channel" (2 OBSERVATIONS AND DATA REDUCTION)
- time on source: 49 min total, ~25 min on-source  
  > "Observations lasted for 49 minutes (approximately 25 minutes on-source) with 18 antennas." (2 OBSERVATIONS AND DATA REDUCTION)
- observing dates: 2012 June 3  
  > "on 2012 June 3 using the ALMA" (2 OBSERVATIONS AND DATA REDUCTION)
- pi or archival as stated: _not stated_
- Line: H2O 10(2,9)–9(3,6) (321.226 GHz)
- Other facility **DSN Tidbinbilla 70 m**: 22 GHz H2O maser spectrum on 2012 September 7 for comparison  
  > "22 GHz spectra obtained on 2012 September 7 using the Deep Space Network 70 m antenna at Tidbinbilla" (3 RESULTS)
- External data: Enclosed mass 1.7e6 Msun and Keplerian disk model for 22 GHz maser  
  > "by calculation based on a Keplerian ($v$ $\propto$ $r^{-0.5}$) rotation disk model in Greenhill et al. (2003a, 2003b)" (4.3 Possible Detection of High-velocity Gas) [from Greenhill et al. 2003a, 2003b (cite: linc03a; linc03b)]
- External data: Optical nucleus position from NED  
  > "(primary from NED)" (3 RESULTS) [from NED]

## Processing

### Calibration

- pipeline or manual: CASA calibration; Titan amplitude, 3C 279 bandpass, J1329-5608 phase reference  
  > "Amplitude calibration was performed using observations of Titan, and the bandpass correction was made with 3C 279." (2 OBSERVATIONS AND DATA REDUCTION)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan  
  > "Amplitude calibration was performed using observations of Titan" (2 OBSERVATIONS AND DATA REDUCTION)
- flux scale uncertainty: 10%  
  > "Flux-density errors of 10 % are conservatively adopted" (2 OBSERVATIONS AND DATA REDUCTION)
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural weighting  
  > "Imaging was performed using CASA in natural weighting" (2 OBSERVATIONS AND DATA REDUCTION)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum subtracted from visibilities using line-free channels before imaging  
  > "the 321 GHz continuum emission of the Circinus was subtracted from the spectral line visibilities using line-free channels prior to the imaging and CLEAN deconvolution of line emission." (2 OBSERVATIONS AND DATA REDUCTION)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.66 x 0.51 arcsec, PA -17 deg  
  > "the synthesized beam size was 0$\ensuremath{''}.66 \times 0\ensuremath{''}$.51 (P.A.= –17$\ensuremath{^\circ}$)" (2 OBSERVATIONS AND DATA REDUCTION)
- final rms: line ~9–11 mJy/beam per channel; continuum ~0.8 mJy/beam  
  > "The rms of the continuum map was $\sim$0.8 mJy beam$^{-1}$." (2 OBSERVATIONS AND DATA REDUCTION)

### Inherited from earlier work

- Relative positional error formula (beam/(2×S/N))  
  > "represented by the synthesized beam size divided by 2 $\times$ S/N (cite: hagi03b)" (3 RESULTS) [from (cite: hagi03b)]
- Positional accuracy ~10% of beam from Cycle 0 capabilities  
  > "According to the ALMA Cycle 0 Capabilities, the positional errors are $\sim$ 10% of the synthesize beam" (3 RESULTS) [from ALMA Cycle 0 Capabilities]

### Not stated but needed to reproduce (our reading)

- CASA version
- Line-free channel ranges
- Clean threshold, cell and image size, masking
- Flux density of Titan model and phase-reference solutions
- Which antennas/baselines and any flagging
- Number of channels averaged or velocity resolution of images
- Details of Gaussian fits

## Analysis recipe

1. **Calibrate and image**: CASA calibration, continuum subtraction in uv, natural-weighted CLEAN cube  
  > "Imaging was performed using CASA in natural weighting" (2 OBSERVATIONS AND DATA REDUCTION)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Search for line emission and measure spectra and positions**: Searched within 18 arcsec field over VLSR -430 to +1290 km/s; Gaussian-fitted peak positions  
  > "was searched within the nominal field of view of 18$''$, centered on the phase-tracking center of the galaxy and in the velocity range of $V$$_{\rm LSR}$=$-$430 to $+$1290 km s$^{-1}$" (3 RESULTS)
   - software: CASA, AIPS
   - fitting: Gaussian fit to positions  
  > "The Gaussian-fitted position (relative to the phase-referencing source) of the redshifted peak emission" (3 RESULTS)
   - validation: Compared with 22 GHz Tidbinbilla spectrum  
  > "we made a comparison of the 321 GHz H$_{2}$O$\;$spectra with 22 GHz spectra obtained on 2012 September 7" (3 RESULTS)
3. **Estimate radius of high-velocity feature**: Keplerian v∝r^-0.5 scaling from the Greenhill disk model  
  > "it is located at a radius of $\sim$ 0.018 pc" (4.3 Possible Detection of High-velocity Gas)
   - assumption: Black hole mass 1.7e6 Msun; Keplerian rotation  
  > "for a 1.7 $\times$ 10$^6$ $M_{\ensuremath{\odot}}\;$black hole" (4.3 Possible Detection of High-velocity Gas)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Calibration, imaging, image analysis  
  > "The image analysis was performed using both the CASA and the Astronomical Image Processing Software." (2 OBSERVATIONS AND DATA REDUCTION)
- **AIPS** : Image analysis  
  > "The image analysis was performed using both the CASA and the Astronomical Image Processing Software." (2 OBSERVATIONS AND DATA REDUCTION)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Peak line flux density | 131 | not stated | mJy/beam | 2 | peak flux density of which is 131 mJy beam$^{-1}$  at $V$$_{\rm LSR}$=531.1 km s$^{-1}$ |
| Integrated intensity | ~14 | not stated | Jy km/s | 2 | The total integrated intensity estimated from all the detected H$_{2}$O$\;$emission is $\sim$14 Jy km s$^{-1}$. |
| Continuum total flux density | 55 | not stated | mJy | 2 | The detected nuclear continuum with the total flux density of 55 mJy |
| Radius of high-velocity feature | ~0.018 | not stated | pc | 3 | it is located at a radius of $\sim$ 0.018 pc |

## Qualitative findings

- 321 GHz H2O emission is likely maser, unresolved at 0.66 arcsec, coincident with continuum peak  
  > "The detected maser features remain unresolved at the synthesized beam of $\sim$ $0\ensuremath{''}$.66 ($\sim$15 pc) and coincide with the 321 GHz continuum peak within small uncertainties." (abstract)

## Claim tuples

- H: Circinus hosts 321 GHz H2O maser | E: ALMA Cycle 0 Band 7 spectral line observation | R: Peak 131 mJy/beam, S/N>10, features at 255–275 and 470–670 km/s | F: First extragalactic 321 GHz H2O maser detected, in region similar to 22 GHz maser | **supported**
- H: A high-velocity feature probes the innermost gas | E: 3 sigma feature at 1069 km/s interpreted with Keplerian disk | R: Radius ~0.018 pc | F: Tentative highest velocity feature | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal origin cannot be excluded by brightness temperature; maser favoured from small size and narrow lines  
  > "it is most likely that the H$_{2}$O$\;$emission detected in the Circinus galaxy is due to maser amplification." (4.1 Origin)
- How they decided it was enough: _not stated_
- Limitation (authors): Beam too large to measure brightness temperature or resolve kinematics  
  > "The synthesized beam size of our observation was too large to determine if the detected 321 GHz H$_{2}$O$\;$emission is thermal emission or maser" (4.1 Origin)
- Caveat (inferred, ours): High-velocity feature is only ~3 sigma
- Caveat (inferred, ours): 22 GHz and 321 GHz observed months apart with strong variability
- Caveat (inferred, ours): Processing details sparse

## Reproducibility

- Data public (paper): ALMA project code given; Cycle 0 data  
  > "This Letter makes use of the following ALMA data: 2011.0.00121.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: CASA version and scripts
- Missing: line-free channels
- Missing: imaging parameters
- Data volume (inferred): ~1-5 GB
- Score (inferred): 3/5, Single public dataset and simple analysis, but sparse processing details.
- Rediscovery candidate: yes, Public Cycle 0 data, simple recipe, numeric line and continuum results.

## Links

- Companion: Greenhill et al. 2003a, 2003b (cite: linc03a; linc03b) (22 GHz maser VLBI disk model used for Keplerian radius)

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
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 63,
  "stated": 35,
  "rate": 0.556
 },
 "evidence_ok": true
}
```
