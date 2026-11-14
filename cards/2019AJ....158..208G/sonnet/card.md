# First Detection of CS Masers around a High-mass Young Stellar Object, W51 e2e

`2019AJ....158..208G` | The Astronomical Journal 2019 | first author: Ginsburg, Adam | arXiv: 1909.11089 | DOI: 10.3847/1538-3881/ab4790

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry, milky_way_ism
- Question: Do the CS J=1-0 and J=2-1 rotational transitions show maser emission toward high-mass protostars in W51 A, and where do they arise?  
  > "We report here the first detection of maser emission from CS $v=0$ in both the J=1-0 and J=2-1 transitions in W51 e2e and nondetections in the other two hot cores." (Introduction)
- Target **W51 e2e**: coordinates RA 290.9331982, Dec 14.5095852 deg (ICRS, CS J=2-1 peak)  
  > "The W51 A high-mass star-forming region (at a distance of 5.4 kpc - (cite: Sato2010a))" (Introduction); z/distance 5.4 kpc  
  > "The W51 A high-mass star-forming region (at a distance of 5.4 kpc - (cite: Sato2010a))" (Introduction); distance from Sato et al. 2010  
  > "The W51 A high-mass star-forming region (at a distance of 5.4 kpc - (cite: Sato2010a))" (Introduction)
- Target **W51 IRS2/North**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_
- Target **W51 e8**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.01596.S, 2017.1.00293.S
- bands: ALMA Band 6 (1 mm) and Band 3 (3 mm); VLA Q-band (7 mm)  
  > "2017.1.00293.S observed Band 3 (3 mm, CS J=2-1), and the Karl G. Jansky Very Large Array (VLA) program VLA 16B-202 observed Q-band (7 mm, CS J=1-0)." (2 Observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ALMA long-baseline configurations; VLA A configuration  
  > "The ALMA data were taken in long-baseline configurations, and the VLA data were taken in the most extended configuration (A)." (2 Observations)
- baselines: _not stated_
- angular resolution: CS 2-1 beam 0.067"x0.043"; CS 1-0 beam 0.043"x0.037"  
  > "resulting in a beam $0.067\arcsec\times0.043\arcsec$, PA=$-44.5^\circ$, and sensitivity $\sigma_{rms} = 0.59$ mJy $\textrm{beam}^{-1}$(26 K)." (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: CS 2-1 0.59 mJy/beam (3 km/s channels); CS 1-0 1.3 mJy/beam (6 km/s)  
  > "beam $0.043\arcsec\times0.037\arcsec$, PA=$-64.8^\circ$ and sensitivity 1.3 mJy $\textrm{beam}^{-1}$(420 K)." (2 Observations)
- time on source: _not stated_
- observing dates: VLA: 2016-10-02, 2016-12-26, 2016-12-30, 2017-01-07  
  > "across four observing epochs (2016-10-02, 2016-12-26, 2016-12-30, 2017-01-07;" (Variability check)
- pi or archival as stated: _not stated_
- Line: CS J=2-1 (97.980953 GHz)
- Line: CS J=1-0 (48.990955 GHz)
- Line: SiO J=5-4 (not stated)
- Other facility **VLA**: Q-band CS J=1-0 data (program VLA 16B-202)  
  > "the Karl G. Jansky Very Large Array (VLA) program VLA 16B-202 observed Q-band (7 mm, CS J=1-0)" (2 Observations)
- External data: Positions of OH, water and CH3OH masers for comparison  
  > "The closest OH and water masers (cite: Fish2007a; Sato2010a) are separated by $>0.2\arcsec$ ($>1000$ AU)." (5 Analysis) [from Fish2007a; Sato2010a; Etoka2012a; Surcis2012a]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline-calibrated data; VLA EVLA pipeline with RFI flagging and Hanning smoothing disabled  
  > "The VLA data were calibrated with the EVLA pipeline[^1] with radio frequency interference (RFI) flagging and Hanning smoothing disabled to avoid flagging bright lines." (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Band 6 continuum: nine iterations of phase-only self-cal, applied to continuum only  
  > "using nine iterations of phase-only self-calibration; the solutions were only used for the continuum data." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: CS 2-1 robust 0.5; CS 1-0 robust 0; SiO and 1 mm continuum robust 0.5  
  > "we imaged it with robust 0 weighting" (2 Observations)
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
- final rms: 0.59 mJy/beam (CS 2-1); 1.3 mJy/beam (CS 1-0)  
  > "sensitivity 1.3 mJy $\textrm{beam}^{-1}$(420 K)." (2 Observations)

### Inherited from earlier work

- Band 6 continuum self-calibration procedure  
  > "The Band 6 (1 mm) continuum data were self-calibrated as described in (cite: Goddi2018a)" (2 Observations) [from Goddi2018a]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, masks, niter, deconvolver)
- Continuum subtraction and line-free channels
- Whether the VLA continuum band used for CS 1-0 was continuum-subtracted
- ALMA configurations, baselines, and integration times
- Details of the FK5-to-ICRS correction procedure
- Gaussian fit method details for the line profiles

## Analysis recipe

1. **Image CS lines**: Imaged CS J=2-1 (3 km/s channels, robust 0.5) and CS J=1-0 (6 km/s, robust 0) from calibrated data  
  > "We imaged the CS J=2-1 line at 97.980953 GHz with robust 0.5 weighting with 3 km s$^{-1}$ channels" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Velocity check for the VLA data; variability check across epochs  
  > "found no evidence for variability across four observing epochs" (Variability check)
2. **Fit line and position**: Gaussian fits to line profiles and peak intensity images  
  > "We report Gaussian fit parameters to the line profiles and to the peak intensity images" (4 Results)
   - software: pyspeckit
   - fitting: Gaussian fit; errors assume no parameter correlation  
  > "the errors reported in the table are fit errors assuming no correlation between the parameters" (4 Results)
   - validation: _not stated_
3. **Infer enclosed mass from maser separation**: Assume masers at opposite ends of an orbiting disk, v_orb=15 km/s, R=95 AU  
  > "assuming the masers come from opposite ends of a disk such that $v_{orb}=15\pm1$ km s$^{-1}$ and $R_{disk}=95\pm30$ AU" (5 Analysis)
   - assumption: Masers trace orbiting material; invalid if from outflow  
  > "In that case, the orbital analysis is not valid." (5 Analysis)
   - fitting: _not stated_
   - validation: Compared with luminosity-based mass estimates from earlier work  
  > "This mass is comparable to that suggested by (cite: Ginsburg2017a) and (cite: Goddi2018a) based on luminosity estimates." (5 Analysis)

## Software

- **CASA** : data reduction and imaging  
  > "This paper used `astropy` (cite: Astropy-Collaboration2013a; Astropy-Collaboration2018a), `pyspeckit` (cite: Ginsburg2011c), and CASA (cite: McMullin2007a)." (Acknowledgements)
- **pyspeckit** : line fitting (inferred from listing)  
  > "`pyspeckit` (cite: Ginsburg2011c)" (Acknowledgements)
- **astropy** : general analysis  
  > "This paper used `astropy` (cite: Astropy-Collaboration2013a; Astropy-Collaboration2018a)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CS J=2-1 maser v_LSR | 34.50 | 0.07 | km/s | 2 | $34.50 \pm       0.07$ |
| CS J=1-0 v_LSR | 64 | 6 | km/s | 2 | $64 \pm        6$ |
| CS J=2-1 amplitude (brightness temperature) | 6700 | 200 | K | 2 | $6700 \pm        200$ |
| Offset between CS 1-0 and 2-1 masers | 190 | 60 | AU | 2 | ($190\pm60$ AU) |
| Implied enclosed mass | 24 | +12/-10 | Msun | 3 | the implied contained mass is $M=24_{-10}^{+12}$ $\mathrm{M}_{\odot}$ |
| CS 2-1 flux limit toward IRS2/North and e8 | 15 | not stated | mJy/beam | 1 | peak CS 2-1 flux limit ${S_{98
\mathrm{GHz}} \leq 15 \mathrm{mJy~\ensuremath{\textrm{beam}^{-1}}}}$ |

## Qualitative findings

- CS 1-0 and 2-1 masers are spatially and spectrally offset; both near the base of the blueshifted outflow  
  > "but both appear to come from the base of the blueshifted outflow from this source" (abstract)

## Claim tuples

- H: CS rotational lines in W51 e2e are masers | E: Imaged CS 1-0 (VLA) and 2-1 (ALMA) and measured brightness temperatures and velocities | R: Peak brightness ~7000 K, lines at different velocities and positions | F: First detection of CS masers | **supported**
- H: Other W51 HMYSOs also host CS masers | E: Searched IRS2/North and e8 in same data | R: No compact bright CS, limit 15 mJy/beam | F: W51 e2e is unique | **supported**
- H: Masers trace a disk around a central mass | E: Orbital mass from velocity and spatial separation | R: M=24 Msun | F: Possible but outflow origin not excluded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Thermal origin rejected because of different velocities of the peaks and high brightness temperature  
  > "This velocity difference rules out a thermal origin for either transition" (5 Analysis)
- How they decided it was enough: _not stated_
- Limitation (authors): Spectral resolution too coarse to identify lines narrower than thermal width  
  > "our observations have too coarse resolution to identify such narrow widths if they are present." (5 Analysis)
- Limitation (authors): Systematic pointing error ~0.003" (16 AU)  
  > "so our systematic pointing error is approximately 0.003(16 AU)." (2 Observations)
- Caveat (inferred, ours): Offset uncertainty of 0.12 arcsec in text looks inconsistent with 190±60 AU
- Caveat (inferred, ours): Quoted CS 1-0 v_LSR differs between sections (64±6 vs 65.5±0.7 km/s)
- Caveat (inferred, ours): Mass estimate depends on unproven disk geometry
- Caveat (inferred, ours): Maser classification relies on brightness temperature, not on line width

## Reproducibility

- Data public (paper): ALMA projects cited; ALMA data are archival  
  > "This paper makes use of the following ALMA data sets: ADS/JAO.ALMA#2013.1.01596.S and 2017.1.00293.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and tclean parameters
- Missing: Continuum subtraction details
- Missing: Exact fitting procedure
- Missing: Positional correction procedure
- Data volume (inferred): ~100-500 GB for ALMA long-baseline Band 3 and Band 6 plus VLA Q-band
- Score (inferred): 3/5, Public data and key imaging weights are given, but CASA version and many imaging parameters are missing; the results are few.
- Rediscovery candidate: yes, Data are public, imaging choices (robust, channel width) are stated, and the results are numeric line parameters.

## Links

- Companion: Goddi2018a (Source of Band 6 data, self-calibration and SiO outflow)
- Companion: Ginsburg2017a (W51 hot core and mass estimates)
- Related: VLA 16B-202

## Checks

```json
{
 "quotes": 46,
 "quotes_ok": 46,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [
  "2013.1.01596.S"
 ],
 "obscore_codes_not_in_card": [
  "2015.1.01596.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 69,
  "stated": 31,
  "rate": 0.449
 },
 "evidence_ok": true
}
```
