# A detailed view on the circumstellar environment of the M-type AGB star EP Aquarii. I. High-resolution ALMA and SPHERE observations

`2020A&A...642A..93H` | Astronomy and Astrophysics 2020 | first author: Homan, Ward | arXiv: 2008.08394 | DOI: 10.1051/0004-6361/202038255

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What do new high-resolution (0.025") ALMA band 6 and SPHERE/ZIMPOL data reveal about the companion-shaped circumstellar wind of EP Aqr, the SiO emission void, and the inner dust distribution?  
  > "The new ALMA data better resolve the inner wind and reveal that its morphology as observed in CO is consistent with hydrodynamical companion-induced perturbations." (abstract)
- Target **EP Aquarii**: coordinates RA 21:46:31.88046, Dec -02:12:45.5471  
  > "Hipparcos measured its distance to the Earth to be approximately 135 parsec" (1 Introduction); "EP Aqr was observed at R.A. 21:46:31.88046, Dec. –02:12:45.5471." (2.1 Observations); z/distance 135 pc (Gaia: 124 pc)  
  > "Hipparcos measured its distance to the Earth to be approximately 135 parsec" (1 Introduction); "EP Aqr was observed at R.A. 21:46:31.88046, Dec. –02:12:45.5471." (2.1 Observations); distance from Hipparcos (Lebzelter2002)  
  > "Hipparcos measured its distance to the Earth to be approximately 135 parsec" (1 Introduction); "EP Aqr was observed at R.A. 21:46:31.88046, Dec. –02:12:45.5471." (2.1 Observations)

## Data provenance

- ALMA projects: 2018.1.00750.S, 2011.0.00277.S
- bands: Band 6  
  > "EP Aquarii was observed by ALMA in Band 6 for project code 2018.1.00750.S" (2.1 Observations)
- frequencies and spectral setup: 4 spws centred 217.128, 220.422, 230.562, 235.176 GHz; 0.468692 GHz wide, 1920 channels, ~0.32 km/s  
  > "Each spw has a width of 0.468692 GHz, divided into 1920 channels, resulting in a velocity channel width of $\sim0.32$ km s$^{-1}$" (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10 (TM0) extended, plus 2016 ACA, TM2, TM1 data  
  > "using the extended configuration C43-10, hereafter referred to as TM0." (2.1 Observations)
- baselines: 83 to 16196 m, 46 antennae  
  > "covered baseline lengths between 83 and 16196 m, which are sensitive to angular scales up to 0.48”." (2.1 Observations)
- angular resolution: ~0.025" (TM0 beam ~21-26 mas; combined 23x22 mas continuum)  
  > "2019 | All | 16.32 | 20.95 | 0.02" (Table 2)
- max recoverable scale: 0.48" (TM0)  
  > "covered baseline lengths between 83 and 16196 m, which are sensitive to angular scales up to 0.48”." (2.1 Observations)
- sensitivity: _not stated_
- time on source: 99 min on target (TM0)  
  > "for a total of 99 minutes on target" (2.1 Observations)
- observing dates: 2019-06-05 (TM0); 2016-10-08, 2016-12-13 earlier  
  > "2019-06-05 | TM0 (12m) | 16.10 | 21.35 | 0.03" (Table 2)
- pi or archival as stated: 2018.1.00750.S PI W. Homan; 2016 data from Homan2018b  
  > "project code 2018.1.00750.S (PI W. Homan)" (2.1 Observations)
- Line: 12CO J=2-1 (230.55 GHz)
- Line: SiO J=5-4 (217.12 GHz)
- Line: SO2 4(2,2)-3(1,3) (235.15 GHz)
- Line: 13CO J=2-1 (220.399 GHz)
- Other facility **VLT/SPHERE/ZIMPOL**: Polarimetric visible images of inner wind in CntHα and BHα filters (V and Cnt748 saturated)  
  > "in four filters, V, CntH$\alpha$, BH$\alpha$ and Cnt748, on August 17th 2018" (3 SPHERE data acquisition and reduction)
- External data: 2016 ACA+TM2+TM1 ALMA data (Cycle 4) combined with new data  
  > "The combination of the lower-resolution data is described in (cite: Homan2018b)." (2.3 Combination of multi-array data) [from (cite: Homan2018b)]
- External data: Photodissociation cross-sections of SiO  
  > "we have made use of the cross-sections made available via the Leiden database for photodissociation" (6.2 The nature of the companion) [from (cite: Heays2017)]
- External data: Dust opacity 7 cm2/g  
  > "values of $\kappa_d$=7cm$^2$/g (cite: Demyk2017)" (6.2 The nature of the companion) [from (cite: Demyk2017)]
- External data: WD cooling curves  
  > "We used the WD cooling curves given by (cite: Renedo2010) to obtain the cooling time for different WD masses." (6.2 The nature of the companion) [from (cite: Renedo2010)]
- External data: WD initial-final-mass relation  
  > "combining this with the WD initial-final-mass relation (cite: Cummings2018)" (6.2 The nature of the companion) [from (cite: Cummings2018)]

## Processing

### Calibration

- pipeline or manual: ALMA pipeline  
  > "The data were calibrated using the ALMA pipeline." (2.2 Data reduction and imaging)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: 7%  
  > "This is consistent with the ALMA flux scale accuracy of 7%." (2.3 Combination of multi-array data)
- self calibration: Continuum phase then amplitude self-cal, applied also to line data  
  > "We then used this image as a starting model for self-calibration of phase and then amplitude." (2.2 Data reduction and imaging)

### Imaging

- task: _not stated_
- deconvolver: multi-scale clean  
  > "we imaged the channels around the SiO and CO lines using multi-scale clean" (2.3 Combination of multi-array data)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 0.003" (TM0 alone); 5 mas (combined)  
  > "used a pixel size of 0”.003 and a total image size of 6”." (2.2 Data reduction and imaging)
- image size: 6" (TM0)  
  > "used a pixel size of 0”.003 and a total image size of 6”." (2.2 Data reduction and imaging)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Line-free channels selected from visibility spectra  
  > "Scanning the visibility spectra, we selected the line-free channels and used these to image the continuum" (2.2 Data reduction and imaging)
- line free channels: _not stated_
- primary beam correction: applied  
  > "the primary beam correction was applied" (2.3 Combination of multi-array data)
- array combination: TM0 weight 0.2 relative to combined 2016 data; continuum equal weight per dataset  
  > "The TM0 data were given a weight of 0.2 relative to the combined 2016 data" (2.3 Combination of multi-array data)
- smoothing: _not stated_
- final beam: 23x22 mas continuum, PA -15; CO 87x79 mas combined  
  > "2019 | All | 16.32 | 20.95 | 0.02" (Table 2)
- final rms: Continuum 0.02 mJy/beam; CO 0.6 mJy, SiO 0.7 mJy (combined)  
  > "SiO | J=5-4 | 217.12 | 0.7" (Table 3)

### Inherited from earlier work

- Data reduction aspects common to all observations  
  > "aspects of data reduction common to all observations are described there." (2.1 Observations) [from (cite: Homan2018b)]
- Multi-array combination procedure  
  > "We followed the same procedure to add the extended-configuration data to the combined dataset." (2.3 Combination of multi-array data) [from (cite: Homan2018b)]
- Distance of 135 pc adopted for consistency  
  > "we adopt a distance of 135 pc (cite: Lebzelter2002) in order to retain consistency with the work by (cite: Homan2018b)" (1 Introduction) [from (cite: Lebzelter2002); (cite: Homan2018b)]

### Not stated but needed to reproduce (our reading)

- CASA version and pipeline version for ALMA data
- robust/weighting, clean thresholds, multiscale scales and masks
- which line-free channels were used and self-cal solution intervals
- flux calibrator for TM0
- details of 2016 data calibration (in Homan2018b)
- SPHERE reduction parameters beyond pipeline version
- method for DoLP vs PA profile and radial bump extraction
- how density contrast and dynamic times were computed in detail

## Analysis recipe

1. **Calibrate and self-calibrate ALMA data**: Pipeline calibration, continuum from line-free channels, phase then amplitude self-cal applied to lines  
  > "The corrections from the continuum self-calibration were applied also to the line data." (2.2 Data reduction and imaging)
   - software: ALMA pipeline
   - fitting: _not stated_
   - validation: Check source position offset ~4 mas  
  > "the check source’s apparent position was displaced by $\sim$4 mas" (2.3 Combination of multi-array data)
2. **Combine 2016 and 2019 data and image lines**: Align on earliest phase centre, weight TM0 0.2, multiscale clean, PB correction  
  > "we did not adjust the positions, but combined the data aligned with the phase centre of the earliest observation." (2.3 Combination of multi-array data)
   - parameter: pixel 5 mas  
  > "With a pixel size of 5 mas, we imaged the channels around the SiO and CO lines" (2.3 Combination of multi-array data)
   - assumption: Line flux scales not modified for variability  
  > "We therefore did not attempt to modify the line flux density scales." (2.3 Combination of multi-array data)
   - fitting: _not stated_
   - validation: _not stated_
3. **Characterise continuum with 2-D Gaussian**: 2-D Gaussian fit to continuum at each epoch and combined  
  > "Fitting it with a 2-D Gaussian results in a measured size of 14.0 $\pm$ 0.6 mas $\times$ 11.5 $\pm$ 0.7 mas" (4.1 ALMA continuum emission)
   - fitting: _not stated_
   - validation: _not stated_
4. **Analyse CO and SiO morphology and profiles**: Channel maps, moment 1, PVD, radial SiO profile along E-W axis with power-law fits  
  > "The emission in the inner portion of the wind can be approximated by a power-law with a slope of -0.77." (5.2 28SiO J=5-4 emission)
   - fitting: _not stated_
   - validation: _not stated_
5. **Derive companion properties from SiO void**: Equate SiO UV photodissociation timescale (blackbody, geometric dilution, dust extinction) with void crossing time; WD cooling and IFMR for mass  
  > "Setting this photodissociation time scale equal to the dynamical void crossing time scale produces a space of solutions for black body temperature and radius combinations." (6.2 The nature of the companion)
   - parameter: wind speed 11 km/s; crossing time ~5.8 yr; blackbody T 5000-15000 K  
  > "half of the void’s width ($\sim$27 AU/2) divided by the wind speed ($\sim$11$\, {\rm km}\, {\rm s}^{-1}$) corresponds to approximately 5.8 years." (6.2 The nature of the companion)
   - assumption: kappa_d=7 cm2/g, dust-to-gas 200, constant  
  > "and $\rho_d$ equal to the gas density $\rho_g$ times an assumed dust-to-gas mass ratio of 200." (6.2 The nature of the companion)
   - fitting: _not stated_
   - validation: Order-of-magnitude; wind speed varied by 90%  
  > "The shaded zone in Fig. [10](#pd) represents the shift of the solution curve under a 90% increase and decrease in the assumed wind speed." (6.2 The nature of the companion)
6. **Analyse SPHERE polarised signal**: Reduce with ESO reflex; compute I, polarised flux, DoLP; DoLP vs PA to find symmetry axis and inclination  
  > "The raw data was reduced using the ESO reflex data pipeline v0.24.0" (3 SPHERE data acquisition and reduction)
   - software: ESO Reflex
   - assumption: Dust in flat cylindrical EDE, Rayleigh scattering  
  > "Assuming the dust is confined to a cylindrical and flat EDE, then back-of-the-envelope Rayleigh scattering theory" (6.3 Shape of the polarised light from SPHERE)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** : Calibration  
  > "The data were calibrated using the ALMA pipeline." (2.2 Data reduction and imaging)
- **ESO Reflex** v0.24.0: SPHERE data reduction  
  > "The raw data was reduced using the ESO reflex data pipeline v0.24.0" (3 SPHERE data acquisition and reduction)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak (combined 2019) | 16.32 | not stated | mJy/beam | 3 | The continuum peak is 16.32 mJy/beam |
| Continuum Gaussian size | 14.0 x 11.5 mas, PA 54 | ±0.6, ±0.7 mas; ±8 deg | mas | 3 | a measured size of 14.0 $\pm$ 0.6 mas $\times$ 11.5 $\pm$ 0.7 mas, with a PA of 54 $\pm$ 8 degrees |
| SiO void offset from CBP | 0.4 (~55 AU at 135 pc) | not stated | arcsec | 4 | located approximately 0.4” directly west of the continuum peak position |
| SiO radial power-law slopes | -0.77 inner, -2.6 outer (break ~1.8") | not stated | dimensionless | 4 | can be approximated by a power-law with a slope of -2.6 |
| SiO bumps spacing | 0.45 (4 bumps) | not stated | arcsec | 4 | 4 small consecutive bumps that occur roughly every 0.45” |
| CO rotation axis PA | ~145 | not stated | deg | 4 | has a PA of $\sim$145$^\circ$ |
| Red-shifted CO shells | 6 (7 total in receding outflow) | not stated | count | 4 | These contours reveal 6 distinct shells for the red-shifted line wing |
| Companion WD mass | 0.65-0.8 | not stated | Msun | 5 | the space of solutions is only consistent for WD masses between $\sim$0.65 - 0.8$\,{\rm M}_\odot$ |
| DoLP symmetry axis PA | 138.5 | not stated | deg | 6 | which is at a PA of 138.5$^\circ$ |
| Inclination from DoLP | ~35-45 | crude | deg | 6 | predicts scattering angles between $\sim$35 degrees and $\sim$45 degrees |

## Qualitative findings

- CO inner wind morphology consistent with L1/L3 wake and reflex spiral flows from a companion at 0.4" west of CBP  
  > "In particular, the flow along the L1 and L3 Lagrange points can be identified" (7 Summary)

## Claim tuples

- H: Is the SiO void caused by a photodissociating companion, and what is it? | E: Equate SiO photodissociation and void crossing times for blackbody; WD cooling and IFMR | R: Solutions consistent with WD 6000-8000 K, mass 0.65-0.8 Msun | F: Most probable companion is a white dwarf; solar-like not excluded | **partially**
- H: Does a closer tertiary companion exist? | E: Radial SiO profile and CO arcs | R: 4 bumps spaced 0.45" implying ~25 yr period | F: Tentatively a companion at ~10 AU | **partially**
- H: What is the inner dust distribution? | E: SPHERE DoLP maps | R: Ring of ~0.1" radius, decreased DoLP along PA 138 deg | F: Dust confined to inclined ring-like structure | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Hot accretion disc around companion and main-sequence M dwarf rejected as photodissociation source  
  > "the space of solutions does not appear to be consistent with the presence of a hot accretion disc around the companion" (6.2 The nature of the companion)
- How they decided it was enough: _not stated_
- Limitation (authors): Photodissociation calculation is back-of-the-envelope, order-of-magnitude  
  > "the results in Fig. [10](#pd) should be interpreted within an order of magnitude margin" (6.2 The nature of the companion)
- Caveat (inferred, ours): No quantitative uncertainties on most measured features
- Caveat (inferred, ours): Void interpretation assumes photodissociation and constant wind speed
- Caveat (inferred, ours): Continuum variability of ~20% between epochs complicates combined data
- Caveat (inferred, ours): Many claims qualitative and by eye

## Reproducibility

- Data public (paper): ALMA projects cited in acknowledgements; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2011.0.00277.S and ADS/JAO.ALMA#2018.1.00750.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA/pipeline versions and imaging parameters
- Missing: 2016 data combination details deferred to Homan2018b
- Missing: Exact measurement procedures for profiles and DoLP
- Data volume (inferred): ~200-500 GB raw for extended-configuration plus earlier data
- Score (inferred): 3/5, Data identifiable and public likely, but imaging parameters and combination details largely deferred or unstated; results largely qualitative.
- Rediscovery candidate: no, Recipe incomplete and main results mostly morphological rather than numeric.

## Links

- Method: (cite: Homan2018b) (Describes data reduction and multi-array combination for 2016 data)
- Companion: (cite: Homan2018b) (Earlier lower-resolution ALMA analysis of EP Aqr)
- Companion: (cite: TuanAnh2019) (CSE gas properties from Cycle 4 ALMA data)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 75,
 "quotes_ok": 75,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 80,
  "stated": 52,
  "rate": 0.65
 },
 "evidence_ok": true
}
```
