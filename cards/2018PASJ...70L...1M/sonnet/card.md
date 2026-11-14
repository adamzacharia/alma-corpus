# ALMA [C I] observations toward the central region of Seyfert galaxy NGC 613

`2018PASJ...70L...1M` | Publications of the Astronomical Society of Japan 2018 | first author: Miyamoto, Yusuke | arXiv: 1802.00486 | DOI: 10.1093/pasj/psy016

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: nearby_galaxies, agn_and_quasars, astrochemistry
- Question: What does [CI] trace relative to CO lines in the CND and star-forming ring of NGC 613, and is there a [CI] molecular outflow driven by the AGN jets?  
  > "Comparisons between \[C\] and CO lines in the energetic activities could provide clues to understanding what \[C\] traces." (Introduction)
- Target **NGC 613**: coordinates _not stated_; z/distance 17.5 Mpc  
  > "at the distance of the galaxy (17.5 Mpc; (cite: tully1988))" (2 Observations); distance from Tully 1988  
  > "at the distance of the galaxy (17.5 Mpc; (cite: tully1988))" (2 Observations)

## Data provenance

- ALMA projects: 2015.1.01487.S
- bands: Band 3 and Band 8  
  > "NGC 613 was observed with the Atacama Large Millimeter/submillimeter Array (ALMA) using Bands 3 and 8 receivers." (2 Observations)
- frequencies and spectral setup: Band 3: three SPWs in USB (13CO, C18O 1-0); Band 8: one SPW in USB for [CI]  
  > "The correlators for Band 8 were configured to set one spectral window in the upper sideband" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: Band 8: 12-m array, ACA and TP; Band 3: 12-m  
  > "For Band 8, the Atacama compact array (ACA) and total power array (TP) were used in addition to the 12-m array." (2 Observations)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 3 0.42"x0.35"; Band 8 0.26"x0.23"  
  > "The synthesized beams at Bands 3 and 8 were $0.42\ensuremath{''}\times0.35\ensuremath{''}$" (2 Observations)
- max recoverable scale: Band 3 ~22"  
  > "The maximum recoverable scale for Band 3 is $\sim \timeform{22''}$." (2 Observations)
- sensitivity: [CI] 6 mJy/beam (~0.5 K); 13CO and C18O 0.2 mJy/beam (~0.1 K) per 10 km/s channel  
  > "are 6 mJy beam$^{-1}$ ($\sim0.5$ K), 0.2 mJy beam$^{-1}$ ($\sim0.1$ K), and 0.2 mJy beam$^{-1}$ ($\sim0.1$ K), respectively, in channels of 10 km s$^{-1}$ width." (2 Observations)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: [CI] 3P1-3P0 (492.160651 GHz)
- Line: 13CO J=1-0 (110.201354 GHz)
- Line: C18O J=1-0 (109.782176 GHz)
- External data: CO(3-2) intensity map, rotational temperatures and kinetic temperatures  
  > "where the O intensity map is from (cite: miyamoto) and the beam size of \[C\] is convolved with those of the CO." (3.1) [from Miyamoto et al. 2017 (cite: miyamoto)]
- External data: SFR in CND 0.02 Msun/yr  
  > "$0.02~{\rm \MO~yr^{-1}}$ (cite: falcon)" (3.2) [from (cite: falcon)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Band 3: J2357-5311, J0334-4008; Band 8: J0006-0623, Uranus  
  > "The flux density at the Band 3 was calibrated by J2357-5311 and J0334-4008, and at Band 8 by J0006-0623 and Uranus." (2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN in CASA  
  > "The imaging was performed using the CLEAN-algorithm in CASA." (2 Observations)
- deconvolver: _not stated_
- weighting robust: Briggs robust 0.5 for Band 3; natural for Band 8  
  > "Briggs weighting mode on the data with robustness of 0.5 for Band 3 and the natural weighting mode for Band 8." (2 Observations)
- uv taper: _not stated_
- cell size: 0.05" Band 3; 0.02" Band 8  
  > "$0.05\ensuremath{''}$ per pixel and $0.02\ensuremath{''}$ per pixel for Band 3 and 8, respectively." (2 Observations)
- image size: 1500x1500 pixels  
  > "The resultant maps were $1500\times1500$ pixels" (2 Observations)
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum determined from line-free channels and subtracted  
  > "Each line data was then combined after subtracting continuum emission determined at the channels that are free from spectral line emission." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: TP combined with 12-m+ACA using Feather in CASA (Band 8)  
  > "By using the Feather algorithm in CASA, the low-resolution image obtained through the TP and high-resolution image obtained through the 12-m and ACA" (2 Observations)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Phase reference center adopted  
  > "The phase reference center of $(\alpha_{\rm J2000.0}$, $\delta_{\rm J2000.0})=$ (, ) was adopted (Miyamoto et al. 2017)." (2 Observations) [from Miyamoto et al. 2017]
- Optical depth and column density calculation  
  > "According to (cite: ikeda2002), we calculated the optical depths of \[C\], O(1–0) and C(1–0) under LTE assumption" (3.1) [from (cite: ikeda2002)]

### Not stated but needed to reproduce (our reading)

- CASA version and whether pipeline or manual calibration
- Line-free channel ranges and clean thresholds/masks
- Band 8 beam-matching details and feather parameters
- Self-calibration
- Exact component integration regions for A, B, C and spot positions
- Phase center coordinates (blank in text)

## Analysis recipe

1. **Image cubes and combine arrays**: CLEAN in CASA at 10 km/s; continuum subtracted; Band 8 12m+ACA feathered with TP  
  > "The imaging was performed using the CLEAN-algorithm in CASA." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: Band 8 shifted so continuum peak matches center  
  > "We, therefore, shifted the position in Band 8 data so that the continuum position coincides with the center." (2 Observations)
2. **Moment maps and line ratios**: Mask <3 sigma in smoothed cube; integrated intensity maps; [CI] convolved to CO beam; ratios R_CI/CO  
  > "pixel values $<3~\sigma$ in each velocity channel of the cube smoothed with twice the size of the beam-width were masked" (3.1)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Optical depths under LTE**: LTE optical depth following Ikeda et al. 2002  
  > "we adopted the rotational temperatures of $T_{\rm rot}\sim 18$ K in the CND and $T_{\rm rot}\sim 12$ K in the ring as the excitation temperatures" (3.1)
   - assumption: Tex = Trot 18 K (CND), 12 K (ring)  
  > "$T_{\rm rot}\sim 18$ K in the CND and $T_{\rm rot}\sim 12$ K in the ring" (3.1)
   - fitting: _not stated_
   - validation: _not stated_
4. **Outflow mass, rate and energetics**: PV diagram along minor axis; column densities and masses of components; expansion velocity and time; kinetic luminosity vs jet power  
  > "the expanding time is $t_{\rm exp}\sim2.4~{\rm Myr}$" (3.2)
   - assumption: [C]/[H2]~1.5e-3; [12CO]/[13CO]=60; spherical expansion  
  > "adopting typical value of \[C\]/\[H\]$\sim1.5\times10^{-3}$" (3.2)
   - fitting: _not stated_
   - validation: Outflow described as tentative  
  > "although the \[C\] outflow is tentative" (3.2)

## Software

- **CASA** : Data processing, CLEAN imaging, Feather combination  
  > "The data were processed using the Common Astronomy Software Application (CASA; (cite: mcmullin2007))." (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| [CI] optical depth in CND | 0.6 | 0.3 | dimensionless | 3 | $\tau_{\rm  C\emissiontype{I}}= 0.6\pm0.3$ |
| R_CI/CO range | 0.1–0.3 | not stated | dimensionless | 2 | is in a range of 0.1–0.3 in both the CND and star-forming ring |
| Expansion time | 2.4 | not stated | Myr | 4 | $t_{\rm exp}\sim2.4~{\rm Myr}$ |
| Mass outflow rate (component C) | 0.04 | not stated | Msun/yr | 4 | $dM_{\rm H_2}/dt\sim 0.04$ |
| Jet power | 1.5e42 | not stated | erg/s | 4 | $P_{\rm jet}=1.5\times10^{42}~{\rm erg~s^{-1}}$ |

## Qualitative findings

- [CI] distribution in the ring resembles CO, but [CI] is prominent in the CND where CO isotopes are weak  
  > "although \[C\] is prominent in the CND." (abstract)

## Claim tuples

- H: Does [CI] trace different gas than CO? | E: Compared ratio maps and spectra at ring spots | R: [CI] profiles differ from CO at high R_CI/CO spots | F: [CI] traces different gas there, possibly dark CO | **partially**
- H: Is there an AGN-jet-driven molecular outflow? | E: [CI] PV diagram along minor axis | R: Outflow rate 0.04 Msun/yr exceeds CND SFR 0.02 | F: Bubbly outflow likely boosted by jets, tentative | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Outflow is tentative; more sensitive observations needed  
  > "In order to confirm the outflow, more sensitive \[C\] observations are needed." (3.2)
- Caveat (inferred, ours): Outflow rate from a single component with lower-limit velocity
- Caveat (inferred, ours): Low velocity resolution (10 km/s) and low S/N
- Caveat (inferred, ours): Assumed Tex and abundances drive masses

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: CASA version
- Missing: clean parameters
- Missing: component regions
- Missing: phase center coordinates
- Data volume (inferred): ~50-100 GB
- Score (inferred): 3/5, Data public project code given but processing details sparse.
- Rediscovery candidate: no, Recipe incomplete.

## Links

- Method: Ikeda et al. 2002 ([CI] optical depth and column density)
- Companion: Miyamoto et al. 2017 (CO(3-2) data and CND properties)

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
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 64,
  "stated": 31,
  "rate": 0.484
 },
 "evidence_ok": true
}
```
