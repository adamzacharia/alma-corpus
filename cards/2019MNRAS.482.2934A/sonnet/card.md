# PKS B1740-517: an ALMA view of the cold gas feeding a distant interacting young radio galaxy

`2019MNRAS.482.2934A` | Monthly Notices of the Royal Astronomical Society 2019 | first author: Allison, J. R. | arXiv: 1810.08507 | DOI: 10.1093/mnras/sty2852

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: agn_and_quasars, nearby_galaxies
- Question: Is there cold molecular gas (12CO 2-1) in absorption or emission in the young radio galaxy PKS B1740-517, and how does it relate to the HI absorption, the interaction with a companion, and the source age?  
  > "Here we have used ALMA to search for [12] CO (2-1) emission and absorption, tracing the cold molecular component of the neutral gas" (1 INTRODUCTION)
- Target **PKS B1740-517**: coordinates RA 17h44m25.450s, Dec -51d44m43.79s (J2000)  
  > "RA(J2000) 17 [h] 44 [m] 25 [s] _._ 450 Fey et al. (2009)" (Table 1); "_z_ 0.4413 A15" (Table 1); z/distance z = 0.4413 (rest frame at z = 0.44185 from broad HI/CO absorption)  
  > "RA(J2000) 17 [h] 44 [m] 25 [s] _._ 450 Fey et al. (2009)" (Table 1); "_z_ 0.4413 A15" (Table 1); distance from 21-cm absorption, confirmed by optical spectrum (A15)  
  > "RA(J2000) 17 [h] 44 [m] 25 [s] _._ 450 Fey et al. (2009)" (Table 1); "_z_ 0.4413 A15" (Table 1)

## Data provenance

- ALMA projects: 2015.1.00808.S
- bands: ~150-160 GHz (Band 4); one baseband on CO(2-1) at 159.9 GHz, three continuum basebands  
  > "We centred one baseband on the expected frequency of 12 159.9 GHz for the redshifted CO (2-1) line" (3.1 The Atacama Large Millimetre Array)
- frequencies and spectral setup: Line baseband: 3840 x 0.488 MHz channels (~0.9 km/s); continuum basebands at 146, 148, 158 GHz with 128 channels each  
  > "These were centred at sky frequencies of 146, 148, and 158 GHz, each with 128 channels spanning a bandwidth of 1875 MHz." (3.1 The Atacama Large Millimetre Array)
- continuum bandwidth: 3 x 1875 MHz basebands  
  > "each with 128 channels spanning a bandwidth of 1875 MHz" (3.1 The Atacama Large Millimetre Array)
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 1.1 km  
  > "spanning baseline lengths between approximately 15.1 m and 1.1 km" (3.1 The Atacama Large Millimetre Array)
- angular resolution: 0.33x0.76 arcsec (uniform, continuum); 0.5x1.1 arcsec (natural, CO)  
  > "giving a resolution of 0 _._ 33 _×_ 0 _._ 76 arcsec at 152 GHz" (3.1 The Atacama Large Millimetre Array)
- max recoverable scale: sensitive to angular scales ~0.35 to 26 arcsec  
  > "is sensitive to angular scales between about 0.35 and 26 arcsec" (3.1 The Atacama Large Millimetre Array)
- sensitivity: _not stated_
- time on source: 23 min on target in three scans  
  > "PKS B1740 _−_ 517 was observed for a total of 23 mins, in three scans" (3.1 The Atacama Large Millimetre Array)
- observing dates: 2016 July 20  
  > "were carried using ALMA on 2016 July 20" (3.1 The Atacama Large Millimetre Array)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (absorption and emission) (not stated (observed 159.9 GHz at z=0.44))
- Other facility **ASKAP (BETA and ASKAP-12)**: HI 21-cm absorption spectra, 11 epochs  
  > "Further 21-cm observations of PKS B1740 _−_ 517 were undertaken as part of ASKAP commissioning and early science verification." (3.2 The Australian SKA Pathfinder)
- Other facility **Gemini-South**: optical imaging and spectra (from A15)  
  > "constructed from _g_ _[′]_ _r_ _[′]_ _i_ _[′]_ -band observations with the 8-m Gemini-South telescope by A15" (2 PKS B1740-517)
- External data: Radio SED flux densities from many surveys (Figure 7 references)  
  > "compiled using our data and those in the literature." (Figure 7 caption) [from Hurley-Walker et al. (2017), Mauch et al. (2003), Van Kempen et al. (2014), etc.]
- External data: VLBI 2.3 GHz component separation 52 mas and flux ratio  
  > "resolved by very long baseline interferometry (VLBI; King 1994) into two compact (≲ 10 mas) components separated by 52 mas" (2 PKS B1740-517) [from King (1994)]
- External data: Optical spectrum, X-ray N_H and spin temperature limit, ASKAP-BETA HI data epochs  
  > "A15 compared the total hydrogen column density from the X-ray spectrum and the total integrated H I 21-cm optical depth from the ASKAP spectrum" (4.1.1) [from Allison et al. (2015) (A15)]

## Processing

### Calibration

- pipeline or manual: CASA with standard ALMA science pipeline tools  
  > "Data importing, flagging and calibration were carried out using version 4.5.3 of the CASA [3] package (McMullin et al. 2007) and the standard ALMA science pipeline tools [4]" (3.1 The Atacama Large Millimetre Array)
- casa version: 4.5.3  
  > "version 4.5.3 of the CASA [3] package" (3.1 The Atacama Large Millimetre Array)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J1924-2914 (flux scale and bandpass)  
  > "A further 5 min observation of J1924-2914 was used for calibration of the flux scale and spectral bandpass." (3.1 The Atacama Large Millimetre Array)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Uniform for continuum; natural for CO absorption and emission cubes  
  > "two-term Taylor multi-frequency synthesis image with Uniform weighting" (3.1 The Atacama Large Millimetre Array); "we used natural weighting (with a resolution of 0 _._ 5 _×_ 1 _._ 1 arcsec)" (3.1 The Atacama Large Millimetre Array)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Emission: UVSUB of imaged continuum then first-order UVCONTSUB; absorption: 1st-order polynomial fit to continuum in spectrum  
  > "first imaged and subtracted the continuum directly from the visibilities using UVSUB, followed by a first-order polynomial using UVCONTSUB3" (3.1 The Atacama Large Millimetre Array)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing; cubes at 2 km/s (absorption) and 10 km/s (emission)  
  > "we imaged the visibilities at the full 2 km s _[−]_ [1] velocity resolution" (3.1 The Atacama Large Millimetre Array)
- final beam: _not stated_
- final rms: CO absorption 3.1 per cent per 2 km/s; 1.98 mJy/beam per 2 km/s; emission 2.10 mJy per 10 km/s  
  > "RMS noise level of 1.98 mJy beam _[−]_ [1] per 2 km s _[−]_ [1]" (3.1 The Atacama Large Millimetre Array)

### Inherited from earlier work

- ASKAP data reduction (self-calibration, continuum subtraction, imaging in MIRIAD) and HI line width fitting method  
  > "et al. 1995) as described by A15, but using a higher 1 MHz resolution to form the coarse-channel data" (3.2 The Australian SKA Pathfinder) [from Allison et al. (2015) (A15)]
- Narrow HI line width modelling as two Gaussians convolved with fine filter bank response  
  > "we repeat the method described by A15, jointly modeling the narrower H I component as the superposition of two Gaussians" (4.1.2) [from A15]

### Not stated but needed to reproduce (our reading)

- Continuum line-free channel ranges and polynomial fit region for the CO spectrum
- Taylor-term, clean threshold, cell and image size for ALMA imaging
- Pipeline version and flux calibrator flux density used
- Which ALMA execution blocks/MOUS to use
- Fitting details (priors, errors) of SED least-squares fit
- Equipartition assumptions detail for B~3.4 mG

## Analysis recipe

1. **Measure 152 GHz continuum**: Two-term Taylor MFS image of continuum basebands, uniform weighting  
  > "we generated a two-term Taylor multi-frequency synthesis image with Uniform weighting" (3.1 The Atacama Large Millimetre Array)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Extract CO(2-1) absorption spectrum**: Natural-weighted cube, spectrum at peak continuum, divided by 1st-order polynomial continuum fit to give percentage absorption  
  > "extracted the spectrum from the cube at the position of peak continuum flux density. We fitted a 1st-order polynomial to the continuum" (3.1 The Atacama Large Millimetre Array)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared with ASKAP HI spectrum  
  > "We show the spectrum in Figure 2, overlaid with the H I absorption detected with ASKAP." (3.1 The Atacama Large Millimetre Array)
3. **Search for CO(2-1) emission**: Subtract continuum, 10 km/s cube, sum pixels within 1.75 arcsec (10 kpc)  
  > "We extracted the flux density spectrum by summing pixels per spatial resolution element within 1.75 arcsec" (3.1 The Atacama Large Millimetre Array)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive column densities and gas masses**: Integrated optical depths converted to N(HI) and N(CO), then N(H2) with CO/H2 abundance; emission limit via X_CO; masses for disc with h~150 pc, radius 2 kpc  
  > "Assuming that the atomic gas has a scale height _h_ _∼_ 150 pc (so that the disc obscures both source components) and a radial extent _∼_ 2 kpc from the AGN" (4.1.1)
   - assumption: Tspin 100-2000 K; Tex >= 10 K for CO; Z_CO ~1e-4; Milky Way X_CO = 2e20; 400 km/s line width  
  > "We therefore consider spin temperatures in the range 100 to 2000 K" (4.1.1)
   - fitting: _not stated_
   - validation: CO absorption H2 lower limit compared with emission upper limit  
  > "which gives _N_ H 2 ≲ 1 _×_ 10 [22] cm _[−]_ [2], consistent with the lower limit estimated from the absorption line." (4.1.1)
5. **Fit radio SED and estimate spectral age**: Least squares fit of peaked spectrum with continuous-injection break, then t_syn from equipartition B  
  > "Least squares fitting gives _v_ p = 786 MHz, _v_ br = 16 GHz, _α_ tk = 1 _._ 4, _α_ tn = _−_ 0 _._ 71, and _S_ p = 8 _._ 1 Jy." (4.2)
   - assumption: Equipartition, equal electron and proton energy, component sizes ~10 mas  
  > "Assuming equipartition of the cosmic ray and magnetic field energy densities, equal energy densities of electrons and protons, and source component sizes of ∆ _θ_ _∼_ 10 mas" (4.2)
   - fitting: Least squares  
  > "Least squares fitting gives _v_ p = 786 MHz, _v_ br = 16 GHz," (4.2 Evidence for a young radio AGN)
   - validation: Compared expansion speed with literature  
  > "implies an expansion velocity of _v_ exp _∼_ 0 _._ 3 c, which is consistent with the distribution of directly measured velocities in the literature" (4.2)

## Software

- **CASA** 4.5.3: ALMA import, flagging, calibration, imaging, UVSUB, UVCONTSUB  
  > "version 4.5.3 of the CASA [3] package (McMullin et al. 2007)" (3.1 The Atacama Large Millimetre Array)
- **MIRIAD** : ASKAP self-calibration, continuum subtraction, imaging  
  > "were carried out using the MIRIAD [5] package" (3.2 The Australian SKA Pathfinder)
- **Astropy** : general analysis  
  > "We have made use of A STROPY, a community-developed core P YTHON package for astronomy" (ACKNOWLEDGEMENTS)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 152 GHz continuum flux density | 72.5 | 0.3 | mJy | 1 | has a total flux density of 72 _._ 5 _±_ 0 _._ 3 mJy at 152 GHz |
| Integrated CO optical depth (lower limit) | 4.78 | 0.47 | km/s | 4 | � _τ_ CO d _v_ ≳ 4 _._ 78 _±_ 0 _._ 47 km s _[−]_ [1] |
| Integrated HI optical depth | 0.549 | 0.019 | km/s | 4 | � _τ_ HI d _v_ _≈_ 0 _._ 549 _±_ 0 _._ 019 km s _[−]_ [1] |
| CO column density lower limit | 1.5e16 | not stated | cm^-2 | 4 | We estimate a lower limit to the average CO column density in front of the source of 1 _._ 5 _×_ 10 [16] cm _[−]_ [2] |
| CO(2-1) emission upper limit | <579 | not stated | mJy km/s | 3 | giving an upper limit for undetected emission of � _S_ CO d _v_ _<_ 579 mJy km s _[−]_ [1] |
| Cold H2 mass | 0.9-60e7 | not stated | Msun | 4 | _M_ H 2 _∼_ 0 _._ 9 _−_ 60 _×_ 10 [7] M _⊙_ |
| Narrow HI FWHM | 4.77 | +0.07/-0.07 | km/s | 0 | ∆ _v_ FHWM = 4 _._ 77 _−_ [+0] 0 _[.]_ _._ [07] 07 [km s] _[−]_ [1] |
| Spectral age | ~1600 | order of magnitude | yr | 5 | This gives an approximate spectral age for the source of _t_ syn _∼_ 1600 yr. |
| SED break frequency | 16 | not stated | GHz | 5 | _v_ p = 786 MHz, _v_ br = 16 GHz |
| SFR upper limit from [OII] | <=0.66 | not stated | Msun/yr | 0 | giving a total SFR ≲ 0 _._ 66 M _⊙_ yr _[−]_ [1] |

## Qualitative findings

- CO(2-1) absorption coincides with the broad HI component; no CO absorption at the narrow HI component; no CO emission within 10 kpc.  
  > "rather strikingly has no associated CO absorption" (4.1.2)

## Claim tuples

- H: Cold molecular gas is present in PKS B1740-517 and traces the same reservoir as HI | E: ALMA CO(2-1) spectrum compared with ASKAP HI | R: CO absorption detected with similar width to broad HI | F: Gas reservoir ~1e7-1e8 Msun in a disc or ring within a few kpc | **supported**
- H: The narrow HI component is a cold cloud with no CO | E: Line width fit and covering-fraction / metallicity arguments | R: FWHM 4.77 km/s, no CO | F: Cloud <100 pc along sightline and/or low-metallicity tidal gas | **partially**
- H: The radio source is young | E: SED fit with ALMA 150 GHz point | R: break at 16 GHz | F: Age ~1600 yr, delayed relative to ~50 Myr interaction | **supported**

## Reasoning

- Why this data: ALMA to search CO and constrain high-frequency continuum and spectral age  
  > "to provide a stronger constraint on the high frequency continuum and hence spectral age of the source" (1 INTRODUCTION)
- Why this method: _not stated_
- Alternative: Narrow HI line as jet-driven outflow rejected because of its low velocity dispersion  
  > "is inconsistent with jet-driven gas outflows that are typically associated with young radio sources" (4.1.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Source age is an order-of-magnitude estimate relying on several assumptions  
  > "should therefore be considered a useful order of magnitude measurement of the source age" (4.2)
- Caveat (inferred, ours): Single short ALMA observation; CO absorption lower limits depend on unknown covering fraction
- Caveat (inferred, ours): Gas masses depend on assumed Tspin, Tex, X_CO and disc geometry
- Caveat (inferred, ours): Spectral age depends on equipartition and a fit to non-simultaneous data

## Reproducibility

- Data public (paper): ALMA data cited by project code; archive implied  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00808.S." (ACKNOWLEDGEMENTS)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, clean settings)
- Missing: Line-free channel selection
- Missing: ASKAP data access
- Data volume (inferred): ~5-20 GB
- Score (inferred): 5/5, Simple short observation and analytic equations given, but imaging details missing and ASKAP data needed for context.
- Rediscovery candidate: yes, Public single-dataset ALMA data; CO absorption spectrum and continuum flux are numeric and reproducible.

## Links

- Method: Allison et al. (2015) (cite: A15) (ASKAP HI reduction and line fitting method)
- Companion: Allison et al. (2015) (First HI detection and optical data for PKS B1740-517)
- Related: ASKAP FLASH
- Related: MeerKAT MALS
- Related: MIGHTEE
- Related: Apertif SHARP

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 10,
 "numeric_problems": 0,
 "fill": {
  "facts": 73,
  "stated": 45,
  "rate": 0.616
 },
 "evidence_ok": true
}
```
