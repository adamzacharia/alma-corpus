# Characterizing the radio continuum nature of sources in the massive star-forming region W75N (B)

`2020MNRAS.496.3128R` | Monthly Notices of the Royal Astronomical Society 2020 | first author: Rodríguez-Kamenetzky, A. | arXiv: 2006.08566 | DOI: 10.1093/mnras/staa1742

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: What is the nature of the radio continuum sources (VLA 1, VLA 3, VLA 4, Bc and new weak sources) in the massive star-forming region W75N (B)?  
  > "which allowed us to study the morphology and the nature of the emission of the different radio continuum sources." (abstract)
- Target **W75N (B)**: coordinates RA(J2000) = 20:38:37.0, Dec(J2000) = +42:37:51.0 (ALMA phase center)  
  > "W75N (B), located in the Cygnus X complex at a distance of 1.3 kpc (cite: rygl2012)" (1 Introduction); "The phase center for the W75N (B) observations was RA(J2000) = 20:38:37.0 and Dec(J2000) = +42:37:51.0" (2.2 ALMA); z/distance 1.3 kpc  
  > "W75N (B), located in the Cygnus X complex at a distance of 1.3 kpc (cite: rygl2012)" (1 Introduction); "The phase center for the W75N (B) observations was RA(J2000) = 20:38:37.0 and Dec(J2000) = +42:37:51.0" (2.2 ALMA); distance from Rygl et al. 2012  
  > "W75N (B), located in the Cygnus X complex at a distance of 1.3 kpc (cite: rygl2012)" (1 Introduction); "The phase center for the W75N (B) observations was RA(J2000) = 20:38:37.0 and Dec(J2000) = +42:37:51.0" (2.2 ALMA)

## Data provenance

- ALMA projects: 2017.1.01593.S
- bands: 1.3 mm  
  > "W75N (B) was observed with ALMA at 1.3 mm during three sessions" (2.2 ALMA)
- frequencies and spectral setup: 4 spws: two 1.875 GHz wide at 217.117 and 230.552 GHz; two 117.188 MHz wide at 216.124 and 231.334 GHz; 1920 channels each  
  > "Two spws had 1.875 GHz bandwidth and were centered on $217.117$ and $230.552$ GHz." (2.2 ALMA); "All spws had 1920 spectral channels after hanning smoothing." (2.2 ALMA)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 500 m, 46 antennas  
  > "46 ALMA telescopes participated, with a minimum baseline length of 15 m and a maximum baseline length of 500 m." (2.2 ALMA)
- angular resolution: 1.73" x 0.86", PA -4 deg  
  > "yielding a synthesized beam size for the 1.3 mm continuum observations of $1.73\ensuremath{''}\times0.86\ensuremath{''}$ with a position angle of $-4^\circ$" (2.2 ALMA)
- max recoverable scale: ~7 arcsec  
  > "This resulted in a maximum recoverable scale of $\sim$7 arcsec." (2.2 ALMA)
- sensitivity: _not stated_
- time on source: ~16 minutes  
  > "In total, approximately 16 minutes were spent on source." (2.2 ALMA)
- observing dates: May 6, 7 and 11, 2018  
  > "on May 6th, 7th, and 11th 2018" (2.2 ALMA)
- pi or archival as stated: archive ALMA data  
  > "(archive ALMA data, project code: 2017.1.01593.S)" (2.2 ALMA)
- Line: CH3OH 5(1,4)-4(2,2) (216.94552 GHz)
- Line: SO2 22(2,20)-22(1,21) (216.64330 GHz)
- Line: SiO v=0 (5-4) (217.10498 GHz)
- Other facility **VLA**: 4-48 GHz A-configuration continuum (project 14A-007) plus archive multi-epoch data; main dataset of the paper  
  > "in its A-configuration at C (6 cm), Ku (2 cm), K (1.3 cm), and Q (7 mm) bands (project code 14A-007)" (2.1 VLA)
- External data: Archive multi-epoch VLA data (1992, 2001, 2006) reanalyzed for proper motions  
  > "we also reanalyzed previously reported, multi-epoch VLA archive data (cite: carrasco2010)" (2.1 VLA) [from (cite: carrasco2010)]
- External data: Physical parameters of mm cores taken from SMA study  
  > "we are not able to derive with accuracy their physical parameters with the present data. For those estimates we refer to (cite: minh2010)." (3.2 ALMA) [from (cite: minh2010)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline, then two rounds of phase self-calibration on continuum  
  > "The observations were initially calibrated using the ALMA pipeline of CASA 5.1.1 (cite: mullin2007)." (2.2 ALMA); "we performed two interactions of phase self-calibration on the continuum emission by using CASA 5.1.1." (2.2 ALMA)
- casa version: CASA 5.1.1  
  > "The observations were initially calibrated using the ALMA pipeline of CASA 5.1.1" (2.2 ALMA)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: two phase-only iterations; S/N improved by factor of three  
  > "This improved the continuum signal-to-noise ratio by a factor of three." (2.2 ALMA)

### Imaging

- task: TCLEAN, centered on VLA 2  
  > "the data were imaged and cleaned (task TCLEAN) centered on VLA 2" (2.2 ALMA)
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "using Briggs weighting with a robust parameter of $0.5$" (2.2 ALMA)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: line channels excluded for continuum  
  > "after excluding the channels showing line emissions" (2.2 ALMA)
- line free channels: _not stated_
- primary beam correction: not applied to ALMA images  
  > "The ALMA images presented in this paper (Section [3.2](#alma-sources)) have not been corrected by primary beam" (2.2 ALMA)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 1.73" x 0.86", PA -4 deg  
  > "$1.73\ensuremath{''}\times0.86\ensuremath{''}$ with a position angle of $-4^\circ$" (2.2 ALMA)
- final rms: _not stated_

### Inherited from earlier work

- VLA observation and calibration details  
  > "A detailed description of the observations and calibration procedures can be found in (cite: carrasco2015)." (2.1 VLA) [from (cite: carrasco2015)]
- Mass-loss rate formula  
  > "we follow Equation (3) from (cite: beltran2001) based on the model from (cite: reynolds1986)" (4.1 VLA 1) [from (cite: beltran2001); (cite: reynolds1986)]

### Not stated but needed to reproduce (our reading)

- Channels excluded as line-emitting for ALMA continuum and self-cal solution intervals
- ALMA image size, cell size, cleaning threshold, masks and final rms
- Moment-map channel ranges and clipping thresholds for CH3OH, SO2, SiO
- Method for locating ALMA cores (positions, fluxes of MM1-MM[N])
- Exact fit procedures/uncertainties for the VLA SED and proper motions

## Analysis recipe

1. **calibrate and image ALMA 1.3 mm continuum**: Pipeline calibration, line-free phase self-cal, tclean with Briggs weighting  
  > "using Briggs weighting with a robust parameter of $0.5$" (2.2 ALMA)
   - software: CASA
   - parameter: robust = 0.5  
  > "using Briggs weighting with a robust parameter of $0.5$" (2.2 ALMA)
   - fitting: _not stated_
   - validation: _not stated_
2. **identify mm cores and associate with VLA sources; map lines**: Compare ALMA continuum cores with VLA positions; integrated intensity and first-moment maps of CH3OH, SO2, SiO  
  > "we also show the images of the integrated intensity and velocity field (first order momentum) of the molecular lines" (3.2 ALMA)
   - fitting: _not stated_
   - validation: Compared with SMA results of Minh et al. 2010  
  > "which is fully consistent with the velocity gradient reported by (cite: minh2010)" (3.2 ALMA)

## Software

- **CASA** 5.1.1 (ALMA); 4.1.0 (VLA): ALMA pipeline calibration, self-calibration, tclean imaging; VLA CLEAN imaging  
  > "The observations were initially calibrated using the ALMA pipeline of CASA 5.1.1" (2.2 ALMA)
- **AIPS** : calibration of archive VLA data  
  > "using the Astronomical Image Processing System (AIPS[^4]) data reduction package" (2.1 VLA)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| ALMA continuum synthesized beam | 1.73 x 0.86, PA -4 | not stated | arcsec, deg | 1 | $1.73\ensuremath{''}\times0.86\ensuremath{''}$ with a position angle of $-4^\circ$ |
| Velocity gradient of CH3OH/SO2 core | ~5 | not stated | km/s | 2 | exhibits a velocity gradient of $\sim$5 km/s along the northwest–southeast direction |
| VLA upper limit toward MM[N] | ~30 | not stated | microJy (4 sigma) | 0 | with an upper limit of $\sim$30 $\mu$Jy (4$\sigma$ in the combination of C+Ku+K+Q bands |
| VLA 1 high-resolution Q-band spectral index | +0.5 | 0.4 | dimensionless | 0 | we obtain a spectral index $\alpha= +0.5\pm0.4$ |

## Qualitative findings

- ALMA 1.3 mm shows four cores (MM1, MM2, MM3, new MM[N]); VLA 1-3 sit in MM1; VLA[SW] and VLA[NE] coincide with MM2 and MM3  
  > "The ALMA continuum observations at 1.3 mm show four cores in a region of $\sim$14 arcsec (MM1, MM2, MM3, MM\[N\]; Fig. [3](#figualma))." (3.2 ALMA)

## Claim tuples

- H: Are the new weak VLA sources embedded YSOs? | E: Compare VLA positions with ALMA 1.3 mm cores | R: VLA[SW] and VLA[NE] coincide with MM2 and MM3 | F: They are likely embedded YSOs | **supported**
- H: Are Bc and VLA 4 protostars? | E: Check association with mm cores plus VLA spectral index and proper motions | R: No mm core association, flat spectra, proper motions ~112-118 km/s | F: They are shock-excited obscured HH objects driven by VLA 3 | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Cores lie at the edge of the ALMA primary beam, single band, limited resolution; physical parameters not derived  
  > "Because these millimeter continuum cores are found at the edge of the ALMA primary beam and they were only observed at a single frequency band" (3.2 ALMA)
- Caveat (inferred, ours): ALMA images not primary-beam corrected so fluxes unreliable
- Caveat (inferred, ours): Resolution too coarse to separate VLA 1-3 in mm

## Reproducibility

- Data public (paper): Archive ALMA data; data availability cites public archives  
  > "The datasets underlying this article were derived from sources in the public domain" (Data availability)
- Products in archive: _not stated_
- Missing: ALMA clean parameters and line-free channels
- Missing: Core flux measurements
- Data volume (inferred): ~10-50 GB for ALMA raw data
- Score (inferred): 3/5, ALMA part is minor and thinly described, though project code, robust and CASA version are given.
- Rediscovery candidate: no, ALMA analysis is qualitative with few numbers; main results are VLA-based.

## Links

- Companion: (cite: carrasco2015) (Earlier publication of part of the same VLA data (VLA 2))
- Companion: (cite: minh2010) (SMA study of the same mm cores)

## Checks

```json
{
 "quotes": 50,
 "quotes_ok": 50,
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
  "facts": 59,
  "stated": 34,
  "rate": 0.576
 },
 "evidence_ok": true
}
```
