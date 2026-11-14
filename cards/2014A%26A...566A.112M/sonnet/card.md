# An ALMA Early Science survey of molecular absorption lines toward PKS 1830-211. Analysis of the absorption profiles

`2014A&A...566A.112M` | Astronomy and Astrophysics 2014 | first author: Muller, S. | arXiv: 1404.7667 | DOI: 10.1051/0004-6361/201423646

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry, nearby_galaxies
- Question: What is the structure, velocity-component content, chemical inventory and time variability of molecular absorption along the NE and SW lines of sight of the z=0.89 absorber toward PKS 1830-211?  
  > "resolve the structure of the absorption, locate the different velocity components, and obtain high signal-to-noise ratio line profiles;" (1 Introduction)
- Target **PKS 1830-211 (z=0.89 absorber)**: coordinates _not stated_; z/distance z=0.88582 (absorber); blazar z=2.5  
  > "heliocentric frame and with $z$=0.88582, toward the SW and NE images, respectively" (1 Introduction); distance from Wiklind & Combes 1996 (absorber), Lidman et al. 1999 (blazar)  
  > "heliocentric frame and with $z$=0.88582, toward the SW and NE images, respectively" (1 Introduction)

## Data provenance

- ALMA projects: 2011.0.00405.S
- bands: B3 (100 GHz), B6 (250 GHz), B7 (290 and 300 GHz)  
  > "Four tunings were observed in spectral mode, at 100 GHz (B3), 250 GHz (B6), and 290 and 300 GHz (B7)" (2 Observations and data reduction)
- frequencies and spectral setup: 4 SPWs per tuning, 1.875 GHz wide, 3840 channels of 0.488 MHz; 1-3 km/s resolution after Hanning smoothing  
  > "four different 1.875 GHz-wide spectral windows were set, each counting 3840 channels separated by 0.488 MHz, providing a velocity resolution of 1–3 km s$^{-1}$ after Hanning smoothing." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: Cycle 0 extended configuration  
  > "we required the Cycle 0 extended configuration." (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: ~0.5'' in B6 and B7, ~2'' in B3  
  > "This array configuration results in a synthesized beam of $\sim$$0.5''$ in B6 and B7, and $\sim$$2''$ in B3." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2012 April to June  
  > "between 2012 early April and mid-June" (2 Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: H2O 1_10-1_01 (ortho) (556.936 GHz)
- Line: HCO+ 2-1 (178.375 GHz)
- Line: CO 4-3 (461.041 GHz)
- Other facility **ATCA**: Earlier 7 mm and 3 mm spectra for comparison of absorption profiles  
  > "we compare the ALMA B3-100 GHz (2012) spectra with past ATCA-3 mm data taken on 2011 July 27" (4.5 Time variations)
- External data: H I absorption spectrum from WSRT  
  > "The H I absorption spectrum obtained with the Westerbork Synthesis Radio Telescope in October 1998" (4.1 Velocity components) [from (cite: koo05)]
- External data: [CH]/[H2]=3.5e-8 abundance  
  > "Further assuming a fractional abundance \[CH\]/\[H$_2$\]=3.5$\times$10$^{-8}$ ((cite: she08))" (4.2.2 Line wings) [from (cite: she08)]

## Processing

### Calibration

- pipeline or manual: CASA, standard procedure  
  > "The data calibration was done within the CASA [^2] package following a standard procedure." (2 Observations and data reduction)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune or Titan  
  > "Either Neptune or Titan were used for flux calibration" (2 Observations and data reduction)
- flux scale uncertainty: ~10% in B3, ~20% in B6 and B7  
  > "We expect an absolute flux accuracy of $\sim$10% in B3 and $\sim$20% in B6 and B7." (2 Observations and data reduction)
- self calibration: Phase self-cal with two-point-source model, one solution per 30 s; S/N improved ~2  
  > "The visibility phases were then self-calibrated using this best-fit model, with one gain solution every 30 seconds." (2 Observations and data reduction)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: No imaging for spectra; spectra extracted from visibilities with two point-source fit; residual spectral index removed by first-order polynomial  
  > "This was removed by a first order polynomial." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Relative positions of NE and SW point sources fixed from VLBI  
  > "with well known relative positions from VLBI observations" (2 Observations and data reduction) [from VLBI observations (no specific citation)]
- Physical conditions of SW gas (n_H2~1000-2000 cm-3, Tkin~80 K)  
  > "$T_\mathrm{kin}$$\sim$80 K, (cite: hen08; hen09; mul13)" (4 Analysis) [from (cite: hen08; hen09; mul13)]

### Not stated but needed to reproduce (our reading)

- Exact VLBI relative positions of NE and SW components
- RADEX input parameters used to derive alpha for CO and C I
- Self-bandpass channel selection (line-free channels)
- CASA version
- Hanning smoothing details and time-averaging weights for combined spectra
- Method for Gaussian fit and hfs deconvolution of CH

## Analysis recipe

1. **Extract NE and SW spectra**: Fit two point-like sources to visibilities with uvmultifit per channel; solve NE flux and SW/NE ratio ('self-bandpass'); apply cvel Doppler correction  
  > "solved, on a spectral channel basis, for the flux density of the NE image and for the flux ratio SW/NE." (2 Observations and data reduction)
   - software: CASA, uvmultifit
   - fitting: _not stated_
   - validation: Epochs' spectra averaged after checking profiles unaffected by variations  
  > "we averaged the extracted spectra instead, after checking that the absorption profiles were not significantly affected by time variations" (2 Observations and data reduction)
2. **Derive covering factors and column densities**: Saturation level in -2 to +3 km/s gives f_c; integrated opacity times alpha gives column density; abundances scaled to CH (SW) or H2O (NE)  
  > "We measure the saturation level by averaging the absorption intensity for channels in the range $v$=$-$2 km s$^{-1}$ to +3 km s$^{-1}$." (4.2.1)
   - software: RADEX
   - assumption: Trot=TCMB=5.14 K for polar species; [H2O]/[H2]=5e-8, [HCO+]/[H2]=6e-9  
  > "Their rotation temperatures are $T_\mathrm{rot}$$\sim$$T_\mathrm{CMB}$=5.14 K" (4 Analysis)
   - fitting: Gaussian fits (two CH components with same centroid)  
  > "The fitting exercise, with two Gaussian CH components set at the same centroid velocity" (4.2.2 Line wings)
   - validation: _not stated_

## Software

- **CASA** : Calibration and Doppler correction (cvel)  
  > "The data calibration was done within the CASA" (2 Observations)
- **uvmultifit** : Spectra extraction from visibilities  
  > "We use the Python-based task uvmultifit ((cite: mar14)) to extract the spectra" (2 Observations)
- **RADEX** : Non-LTE alpha coefficients for CO and C I; opacity predictions vs redshift  
  > "We can use the non-LTE radiative transfer code RADEX ((cite: vdtak07)) to estimate their $\alpha$ coefficients." (4 Analysis)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of species toward SW | 42 (plus 14 rare isotopologues) | not stated | count | 0 | now giving a total of 42 different species |
| Species toward NE | 14 | not stated | count | 0 | the number of detected species now reaches a total of 14 |
| SW saturation level (covering factor) | ~95% (H2O) to ~91% (HCO+/HCN) | not stated | % of continuum | 2 | the saturation level ranges between $\sim$95% of the continuum intensity for the water line, and $\sim$91% for the HCO$^+$/HCN (2-1) lines |
| H2 column density SW | 2.2e22 | not stated | cm^-2 | 2 | we derive a total (narrow+broad component) H$_2$ column density of 2.2$\times$10$^{22}$ cm$^{-2}$ along the SW line-of-sight |
| H2O 1_10-1_01 +170 km/s integrated opacity | 0.187 | 0.019 | km/s | 2 | / H$_2$O $1_{10}$-$1_{01}$ / 173.5 (0.2) / 4.8 (0.6) / 0.187 (0.019) / |
| CH narrow component FWHM | 17 | not stated | km/s | 2 | results in a narrow component of FWHM=17 km s$^{-1}$ with an opacity of $\tau$$\sim$1.1 |

## Qualitative findings

- The +170 km/s component lies along the SW line of sight and is mostly molecular; the -300 km/s component is not confirmed.  
  > "The ALMA spectra do not confirm this component and it remains unidentified." (4.1)

## Claim tuples

- H: Where do the additional velocity components lie? | E: Resolve NE and SW images and extract spectra | R: +170 km/s in H2O, HCO+, HCN toward SW; -224 km/s toward NE | F: +170 km/s component located on SW line of sight and mostly molecular | **supported**
- H: Are absorber abundances like Galactic diffuse gas? | E: Scaled relative abundances from integrated opacities | R: Abundances in SW wings and NE within a factor of a few of each other | F: Comparable to Galactic diffuse ISM | **supported**
- H: Do absorption profiles vary with time? | E: Compare ALMA 2012 to ATCA 2011 and within ALMA epochs | R: Factor ~2 changes yearly; minor changes in wings during ALMA observations | F: Absorption depths can change by at least a factor of two within a year | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Wide velocity spread may arise from disk inclination, extraplanar gas, thick molecular disk, or a merger; not discriminated  
  > "What could be the causes for the broad absorption profiles seen in the molecular gas? Possible interpretations include:" (5.1)
- How they decided it was enough: _not stated_
- Limitation (authors): CO and C I column densities highly uncertain in SW wings and NE  
  > "The derived column densities and abundances of CO and C I are highly uncertain in the wings of the SW absorption and toward the NE image" (4.4)
- Caveat (inferred, ours): Point-source model assumes unresolved blazar structure
- Caveat (inferred, ours): Abundance scaling relies on assumed Galactic H2O and CH abundances
- Caveat (inferred, ours): Only two sightlines, limiting disk interpretation

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: VLBI positions
- Missing: CASA version and scripts
- Missing: RADEX parameters for alpha
- Data volume (inferred): ~100-300 GB raw for 13 Cycle 0 execution blocks
- Score (inferred): 3/5, Data public, method outlined, but many parameters not stated.
- Rediscovery candidate: no, Recipe lacks key details (positions, RADEX settings, line-free channels).

## Links

- Method: (cite: mar14) (uvmultifit task)
- Companion: (cite: mul14) (H2Cl+ detection and 35Cl/37Cl ratio)
- Companion: (cite: mar13) (Chromatic flux ratio variability during flare)
- Related: ATCA 7 mm spectral scan (Muller et al. 2011)

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
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 61,
  "stated": 29,
  "rate": 0.475
 },
 "evidence_ok": true
}
```
