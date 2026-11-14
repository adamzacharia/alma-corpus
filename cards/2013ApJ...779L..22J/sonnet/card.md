# A Recent Accretion Burst in the Low-mass Protostar IRAS 15398-3359: ALMA Imaging of Its Related Chemistry

`2013ApJ...779L..22J` | The Astrophysical Journal Letters 2013 | first author: Jørgensen, Jes K. | arXiv: 1312.0724 | DOI: 10.1088/2041-8205/779/2/L22

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: Can the chemical emission signatures (HCO+ ring, central CO and CH3OH) be related to the physical structure and evolution, e.g. a recent accretion burst, of IRAS 15398-3359?  
  > "The main aim of this paper is to relate the observed chemical emission signatures to the physical structure and evolution of the protostar." (1 Introduction)
- Target **IRAS 15398-3359**: coordinates 15h43m02.16s -34d09m06.80s (J2000, phase center)  
  > "located in the Lupus I molecular cloud (B228) (cite: heyer89; chapman07) at a distance of 155 pc (cite: lombardi08)" (1 Introduction); "The phase center was taken to be $\alpha$=15$^{\rm h}$43$^{\rm m}$02.16s; $\delta$=$-$34$^\circ$09$'$06.80$''$ \[J2000\]." (2 Observations); z/distance 155 pc  
  > "located in the Lupus I molecular cloud (B228) (cite: heyer89; chapman07) at a distance of 155 pc (cite: lombardi08)" (1 Introduction); "The phase center was taken to be $\alpha$=15$^{\rm h}$43$^{\rm m}$02.16s; $\delta$=$-$34$^\circ$09$'$06.80$''$ \[J2000\]." (2 Observations); distance from Lombardi et al. 2008  
  > "located in the Lupus I molecular cloud (B228) (cite: heyer89; chapman07) at a distance of 155 pc (cite: lombardi08)" (1 Introduction); "The phase center was taken to be $\alpha$=15$^{\rm h}$43$^{\rm m}$02.16s; $\delta$=$-$34$^\circ$09$'$06.80$''$ \[J2000\]." (2 Observations)

## Data provenance

- ALMA projects: 2011.0.00628.S, 2011.0.00777.S
- bands: Band 7 (0.87 mm)  
  > "at 0.87 mm (ALMA band 7)" (2 Observations)
- frequencies and spectral setup: 4 spectral windows, 3840 channels, 122 kHz (0.11 km/s); 336.95–337.45, 338.30–338.80, 349.35–349.85, 346.90–347.40 GHz  
  > "The spectral setup was chosen to cover 336.95–337.45 GHz, 338.30–338.80 GHz, 349.35–349.85 GHz and 346.90–347.40 GHz." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: extended configuration, 15–16 antennae  
  > "At the time of observations 15–16 antennae were present in the array in an extended configuration" (2 Observations)
- baselines: 20–392 m (≈23–445 kλ)  
  > "providing baselines ranging from 20–392 m ($\approx$ 23–445 k$\lambda$)" (2 Observations)
- angular resolution: 0.55″×0.37″ (PA = −82°)  
  > "beam size of about 0.55$''$$\times$0.37$''$ (PA = $-$82$^\circ$)" (2 Observations)
- max recoverable scale: emission smooth on scales much larger than 9″ (1400 AU) unreliable  
  > "emission that is smooth on scales much larger than 9$''$ (1400 AU) or present on scales larger than 16$''$ (2500 AU) will be unreliable" (3 Results)
- sensitivity: 13 mJy/beam/channel; continuum RMS ~0.28 mJy/beam  
  > "an RMS level of 13 mJy beam$^{-1}$ channel$^{-1}$" (2 Observations); "with a resulting RMS level of about 0.28 mJy beam$^{-1}$" (2 Observations)
- time on source: about three hours (plus 1 hour for 2011.0.00777.S)  
  > "with a total on-source integration time of about three hours" (2 Observations)
- observing dates: 2012 March 29 to April 11, four occasions  
  > "observed on four occasions between 2012 March 29 and 2012 April 11" (2 Observations)
- pi or archival as stated: _not stated_
- Line: C17O J=3-2 (not stated)
- Line: H13CO+ J=4-3 (not stated)
- Line: CH3OH 7k-6k (338.3–338.7 GHz)
- Line: C34S J=7-6 (not stated)
- Line: C2H N=4-3, J=7/2-5/2 (not stated)
- Other facility **JCMT/SCUBA**: 850 µm image from SCUBA legacy archive, total flux 3.9 Jy  
  > "shows the core on larger scales with a total integrated flux of 3.9 Jy at 850 $\mu$m" (3 Results)
- Other facility **Herschel-PACS**: water detection associated with the outflow (Karska et al.)  
  > "Water is detected toward IRAS15398 with Herschel-PACS and found to be associated with the outflow (cite: karska13)" (6 Discussion)
- External data: Envelope luminosity, Tbol and mass from SED/submm reanalysis; Lbol=1.8 Lsun, Tbol=44 K, Menv≈1.2 Msun  
  > "From a reanalysis of its SED and submillimeter continuum maps, its luminosity $L_{\rm bol}$=1.8 $L_\odot$" (1 Introduction) [from not given explicitly]
- External data: Median compact-continuum mass for Class 0 protostars, 0.089 Msun  
  > "compared to the median 0.089 $M_\odot$ for the Class 0 protostars" (6 Discussion) [from (cite: evolpaper)]
- Simulation/model as data: 1D Transphere envelope model with power-law density, p=1.5–2, (1–3)e7 cm-3 and 30 K at 175–200 AU  
  > "The IRAS15398 envelope is well-fit with a power-law density profile decreasing toward larger radii as" (6 Discussion)

## Processing

### Calibration

- pipeline or manual: standard recipes in CASA  
  > "The reduction followed standard recipes in CASA[^1] (cite: mcmullin07)" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Neptune and Titan (gain J1517-243, passband J1325-430)  
  > "calibration of the complex gains through observations of the quasar J1517-243, passband calibration on J1325-430 and flux calibration on Neptune and Titan" (2 Observations)
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
- continuum subtraction: continuum built by averaging channels reasonably free of line emission  
  > "The continuum was constructed by averaging the channels across the four spectral bands that appear reasonably free of line emission" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: 2011.0.00777.S combined for CH3OH and continuum  
  > "For those CH$_3$OH transitions as well as the continuum we combine the datasets for a slight improvement in signal-to-noise." (2 Observations)
- smoothing: _not stated_
- final beam: 0.55″×0.37″ (PA −82°)  
  > "beam size of about 0.55$''$$\times$0.37$''$ (PA = $-$82$^\circ$)" (2 Observations)
- final rms: _not stated_

### Inherited from earlier work

- Radiative transfer approach (abundances constant in temperature-separated regions, fit to brightness profiles)  
  > "following the same approach as in, e.g., (cite: l483art)" (6 Discussion) [from (cite: l483art)]
- Steady-state HCO+ chemistry calculation based on more detailed models  
  > "a steady state calculation based on the more detailed models of (cite: visser12)" (6 Discussion) [from (cite: visser12)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, CLEAN settings
- CASA version
- Line-free channels used for continuum
- Flux scale uncertainty and any self-calibration
- How profile brightness fits were done and compared (radial profile extraction)
- Transphere inputs (SED, luminosity, dust opacities) and RATRAN grid setup
- Cosmic-ray rate printed as 5e17 (likely typo) and chemical network initial abundances

## Analysis recipe

1. **Calibrate and image**: Standard CASA reduction; continuum from line-free channels; datasets combined for CH3OH and continuum  
  > "The reduction followed standard recipes in CASA[^1] (cite: mcmullin07)" (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Model envelope physical structure**: 1D power-law density envelope with self-consistent temperature from Transphere, constrained by SED and submm images  
  > "we adopted a 1D model for the IRAS15398 envelope with a power-law density profile, constrained by the spectral energy distribution and submillimeter continuum images" (6 Discussion)
   - software: Transphere
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive C17O and H13CO+ abundance profiles**: RATRAN line radiative transfer with abundances constant in temperature zones, adjusted to match observed brightness profiles  
  > "the abundances of the two species were taken to be constant in regions separated at specific temperatures and adjusted to match the observed brightness profiles" (6 Discussion)
   - software: RATRAN
   - assumption: CO abundance 1e-4 relative to H2 in warm inner region  
  > "with an abundance of 5$\times 10^{-8}$ (a CO abundance of 1$\times 10^{-4}$)" (6 Discussion)
   - fitting: manual adjustment, no sampler  
  > "the abundances of the two species were taken to be constant in regions separated at specific temperatures and adjusted to match the observed brightness profiles" (Discussion)
   - validation: comparison with observed brightness profiles (Fig. 3)  
  > "adjusted to match the observed brightness profiles (Fig. [3](#chemfits))" (6 Discussion)
4. **Test HCO+ destruction by water**: Steady-state gas-phase chemistry calculation of HCO+ vs H2O and C2H abundance with UDfA12 network  
  > "utilizing the UDfA12 gas-phase chemical network (cite: mcelroy13)" (6 Discussion)
   - parameter: density 1e7 cm-3, T=30 K  
  > "at a density of $10^7$ cm$^{-3}$, temperature of 30 K" (6 Discussion)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate CH3OH abundance**: Radex estimate matching C17O 3-2 and CH3OH 7_0-6_0 line strengths  
  > "A simple estimate using *Radex* (cite: vandertak07radex) shows that the C$^{17}$O 3–2 and CH$_3$OH $7_0-6_0$ are similar in strength" (6 Discussion)
   - software: Radex
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : data reduction  
  > "The reduction followed standard recipes in CASA[^1] (cite: mcmullin07)" (2 Observations)
- **Transphere** : envelope temperature structure  
  > "temperature distribution calculated self-consistently using the Transphere code[^2] (cite: dullemond02)" (6 Discussion)
- **RATRAN** : 1D line radiative transfer  
  > "the line radiative transfer was performed for C$^{17}$O and H$^{13}$CO$^+$ using the one-dimensional RATRAN code" (6 Discussion)
- **Radex** : CH3OH/CO abundance ratio estimate  
  > "A simple estimate using *Radex* (cite: vandertak07radex)" (6 Discussion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 19 | not stated | mJy/beam | 1 | with a peak flux of 19 mJy beam$^{-1}$ and integrated flux of 28 mJy |
| Continuum integrated flux | 28 | not stated | mJy | 1 | with a peak flux of 19 mJy beam$^{-1}$ and integrated flux of 28 mJy |
| C17O abundance inside 30 K (175 AU) | 5e-8 | not stated | relative to H2 | 3 | with an abundance of 5$\times 10^{-8}$ (a CO abundance of 1$\times 10^{-4}$) in the inner regions of the envelope with temperatures above 30 K (175 AU) |
| H13CO+ abundance in 20–30 K region | 7e-11 | drop of at least a factor 20 inside and outside | relative to H2 | 3 | an abundance of 7$\times 10^{-11}$ (HCO$^+$ abundance of 5$\times 10^{-9}$) in the region of the envelope where the temperature is between 20 K and 30 K |
| Required luminosity increase and burst timescale | factor ~100; 100–1000 yr | not stated | dimensionless; yr | 4 | during the last 100–1000 years increasing the luminosity of IRAS 15398–3359 by a factor of 100 above its current luminosity |
| CH3OH abundance in inner region | ~1e-8 | not stated | relative to H2 | 5 | this translates into a CH$_3$OH abundance with respect to H$_2$ of $\sim
10^{-8}$ in this inner region |

## Qualitative findings

- H13CO+ emits only in a ring of radius ~1–1.5″ (150–200 AU) while C17O, C34S and CH3OH are centrally condensed  
  > "emission from H$^{13}$CO$^+$ is only present in a ring-like structure with a radius of about 1–1.5$''$ (150–200 AU)" (abstract)

## Claim tuples

- H: Is the HCO+ hole caused by destruction by water vapor from a recent accretion burst? | E: ALMA imaging, RATRAN abundance fits, and a steady-state chemistry calculation | R: H2O abundance of 1e-6 reduces HCO+ by two orders of magnitude; luminosity ~100x higher needed to sublimate water at 175 AU | F: A burst in the last 100–1000 yr is proposed, which also explains CH3OH, extended warm carbon-chain chemistry and weak compact continuum | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Outflow-shock water and H2CO or carbon-chain destroyers considered less likely  
  > "the ring-like structure of H$^{13}$CO$^+$ and relatively narrow lines of CH$_3$OH (another molecule that could be produced by ice sputtering) speak against this being the reason" (6 Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): No direct imaging of water vapor; kinematics of H13CO+ not addressable at current sensitivity  
  > "Unfortunately no direct imaging of the water vapor in IRAS15398 exists" (6 Discussion)
- Caveat (inferred, ours): Burst scenario is not unique; the interpretation rests on simple 1D models and a steady-state calculation
- Caveat (inferred, ours): H13CO+ velocity offset unexplained
- Caveat (inferred, ours): Imaging parameters not given

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Imaging parameters and CASA version
- Missing: Model input files for Transphere/RATRAN
- Data volume (inferred): tens of GB raw (Cycle 0 Band 7, 4 spectral windows, ~4 hours)
- Score (inferred): 3/5, Project codes given and data are Cycle 0 archive data, but imaging and modeling details are sparse.
- Rediscovery candidate: no, Imaging recipe is incomplete and the results rest on bespoke modeling.

## Links

- Method: Hogerheijde & van der Tak 2000 (RATRAN) (line radiative transfer code)
- Companion: Lindberg et al. 2013, submitted (R CrA-IRS7B observed with similar setup)
- Companion: Y. Oya et al., in prep. (extended C2H emission related to the outflow)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 74,
  "stated": 41,
  "rate": 0.554
 },
 "evidence_ok": true
}
```
