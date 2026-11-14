# Signatures of Young Star Formation Activity within Two Parsecs of Sgr A*

`2015ApJ...808...97Y` | The Astrophysical Journal 2015 | first author: Yusef-Zadeh, F. | arXiv: 1505.05177 | DOI: 10.1088/0004-637X/808/1/97

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: milky_way_ism, star_formation
- Question: Is there on-going star formation within ~2 pc of Sgr A*, as indicated by water masers, YSO SED fits, SiO clumps, ionized jet kinematics and radio dark clouds?  
  > "We present radio and infrared observations indicating on-going star formation activity inside the $\sim2-5$ pc circumnuclear ring at the Galactic center." (abstract)
- Target **Sgr A* circumnuclear molecular ring**: coordinates _not stated_; z/distance 8.5 kpc  
  > "the distance to the Galactic center of 8.5 kpc $\pm$10%" (Results and Discussion); distance from assumed Galactic center distance  
  > "the distance to the Galactic center of 8.5 kpc $\pm$10%" (Results and Discussion)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: SiO (5-4) ALMA data of the ring interior only referenced from Yusef-Zadeh et al. 2013; SMA 3.6''x2.4'' used here  
  > "with a spatial and spectral resolution of $3.6''\times2.4''$ and 2 km s$^{-1}$  respectively" (Published Data)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: SiO 5-4 (not stated)
- Line: H2O maser (22.23419 GHz)
- Other facility **VLA**: 22 GHz water maser observations, B-configuration, 2012 Feb 2  
  > "Water maser observations were carried out with the Karl G. Jansky Very Large Array (VLA)[^1] in its B-configuration on February 2, 2012." (Present Data)
- Other facility **CARMA**: SiO (2-1) mosaic  
  > "The SiO (2-1) line data were taken with the Combined Array for Research in Millimeter-wave Astronomy (CARMA)" (Published Data)
- Other facility **SMA**: SiO (5-4) mapping of ring  
  > "We also used the SiO (5-4) line data taken with the Sub-Millimeter Array (SMA)." (Published Data)
- Other facility **VLT**: 1.6-19.5 micron photometry for SED fitting  
  > "We used the published data obtained with the Very Large Telescope (VLT) at wavelengths ranging between 1.6 and 19.5 $\mu$m (Viehmann et al. 2006)." (Mid-IR data)
- Other facility **TEXES/IRTF**: [Ne II] 12.8 micron kinematics  
  > "Sgr A West was observed in the \[Ne II\] (12.8$\mu$m) line with the high-resolution mid-infrared spectrograph TEXES on the NASA IRTF" ([Ne ii] Line)
- External data: ALMA SiO (5-4) detection of 11 clumps in ring interior  
  > "ALMA observations of the interior of the molecular ring detected SiO (5-4) emission from 11 clumps (Yusef-Zadeh et al. 2013)." (Introduction) [from Yusef-Zadeh et al. 2013 (cite: zadeh13)]
- External data: VLT photometry for SED fitting  
  > "The data points for Spectral Energy Distribution (SED) fitting (see $\S3.2$) are taken from Table 1 of Viehmann et al. (2006)" (Mid-IR data) [from Viehmann et al. 2006 (cite: viehmann06)]
- Simulation/model as data: Robitaille et al. (2006) grid of pre-computed YSO model SEDs  
  > "We compare the sources’ SEDs to the Robitaille et al. (2006) large grid of pre-computed YSO model SEDs" (Results and Discussion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: 3C286 primary flux calibrator (VLA); NRAO530 gain and bandpass  
  > "3C286 was used as a primary flux calibrator and NRAO530 as the complex gain and bandpass calibrator." (Present Data)
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
- continuum subtraction: UVLSF in AIPS in the visibility plane  
  > "Continuum subtraction in the visibility plane was carried out using the UVLSF task of AIPS" (Present Data)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 2.17''x0.81'' (PA=-10.9 deg) for VLA masers  
  > "2.17$''\times0.81''$ (PA=$-10.9^{\circ}$)" (Present Data)
- final rms: about 2.8 mJy/beam per channel (VLA)  
  > "The rms noise in each channel map is about 2.8 mJy beam$^{-1}$." (Present Data)

### Inherited from earlier work

- SED fitting technique  
  > "We used the same technique that identified a population of YSO candidates toward the inner few hundred parsecs of the Galaxy" (Results and Discussion) [from Yusef-Zadeh et al. 2009 (cite: zadeh09)]
- SMA SiO observations similar to earlier paper  
  > "Details of these observations are very similar to the data presented in Martin et al. (2012)" (Published Data) [from Martin et al. (2012)]

### Not stated but needed to reproduce (our reading)

- ALMA data reduction details and project code (only referenced from Yusef-Zadeh et al. 2013)
- CARMA and SMA calibration details
- LVG code name
- Kroupa IMF scaling procedure details

## Analysis recipe

1. **SED fit YSO candidates**: Fit VLT SEDs to Robitaille YSO model grid with linear regression fitter; well-fit if chi2/pt<3  
  > "We identify well-fit models as those with a normalized $\chi^2$ per data point ($\chi^2/pt$) less than 3." (Results and Discussion)
   - software: Robitaille et al. 2007 SED fitting tool
   - parameter: A_V 25-30 mag; distance 7.65-9.35 kpc; sources with >=4 fluxes  
  > "We consider models with interstellar extinction ($A_{V}$) between 25 and 30 mag, and distance between 7.65 and 9.35 kpc" (Results and Discussion)
   - fitting: Parameters averaged over models with chi2/pt within chi2min+2  
  > "averaging parameters of all YSO models that fit the source’s SED with $\chi^2/pt$ in a range between the $\chi^2/pt$ for the best-fitting model" (Results and Discussion)
   - validation: Visual examination of fits  
  > "The visual examination of the fits showed that the YSO model fits" (Results and Discussion)
2. **Estimate SFR**: Scale Kroupa IMF to Stage I YSO mass distribution, integrate 0.08-50 Msun, divide by lifetime  
  > "scale the Kroupa (2001) initial mass function (IMF; $dN/dm \propto m^{-\alpha}$, m – a stellar mass) to match the peak of the distribution" (Results and Discussion)
   - assumption: Stage I lifetime 1e5 yr  
  > "Assuming a typical lifetime of the Stage I YSO of 10$^{5}$ years" (Results and Discussion)
   - fitting: _not stated_
   - validation: _not stated_
3. **LVG analysis of SiO**: Convolve CARMA and SMA to common resolution, Gaussian fit, uniform slab LVG with 5-4/2-1 ratio  
  > "we first convolved the CARMA and SMA data to an identical resolution of $6.85''\times3.73''$ and then performed Gaussian fits to the sources" (LVG Analysis of SiO Lines)
   - parameter: dust temperature 75 K, A_V 30, Tkin 50 and 150 K, FWHM 30 km/s  
  > "a dust temperature of 75 K, 30 magnitudes of visual extinction and a dust extinction curve following Draine & Lee (1984)" (LVG Analysis of SiO Lines)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **AIPS** : VLA calibration and UVLSF continuum subtraction  
  > "The data were calibrated in the usual manner using Astronomical Image Processing System (AIPS)." (Present Data)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Water masers detected | 13 | not stated | count | 0 | We detect 13 water masers concentrated toward the inner edge of the molecular ring. |
| Well-fit YSO sources | 19 of 52 | not stated | count | 1 | only 19 out of 52 sources are well-fit by YSO models |
| SFR within 1 pc | ~1e-2 | order of magnitude | Msun/yr | 2 | the SFR within 1 pc of Sgr A\* is estimated to be $\sim$1$\times10^{-2}$ M$_{\odot}$ yr$^{-1}$ |
| Ionized outflow mass loss rate (f=0.1) | ~5e-5 | not stated | Msun/yr | 0 | the total mass and the mass loss rate are $\sim0.5$   and $\sim5\times10^{-5}$   yr$^{-1}$, respectively |

## Qualitative findings


## Claim tuples

- H: Star formation is on-going within 2 pc of Sgr A* | E: Water masers, SED fitting, SiO clumps, [Ne II] kinematics, radio dark clouds | R: 13 masers, 19 YSO-fit sources, 26 SiO clumps, SiO bipolar outflow candidate, jet-like ionized ridge | F: Multiple lines of evidence support disk-based on-going star formation near Sgr A* | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): SFR is only an order of magnitude estimate  
  > "This is only an order magnitude estimate because of the small number statistics" (Results and Discussion)
- Caveat (inferred, ours): Water masers with multiple components may be OH/IR stars
- Caveat (inferred, ours): YSO SED classification not definitive
- Caveat (inferred, ours): ALMA data only inherited, not reanalysed

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA data processing not described
- Missing: LVG code unspecified
- Data volume (inferred): small to moderate (~tens of GB across VLA, CARMA, SMA)
- Score (inferred): 3/5, ALMA role minor; many inputs from prior papers.
- Rediscovery candidate: no, ALMA minor and recipe incomplete.

## Links

- Method: Robitaille et al. 2007 (cite: robitaille07) (SED fitting tool)
- Companion: Yusef-Zadeh et al. 2013 (cite: zadeh13) (ALMA SiO (5-4) detection)

## Checks

```json
{
 "quotes": 36,
 "quotes_ok": 36,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2011.0.00005.SV"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 67,
  "stated": 28,
  "rate": 0.418
 },
 "evidence_ok": true
}
```
