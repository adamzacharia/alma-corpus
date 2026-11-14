# G-0.02-0.07, the compact H II region complex nearest to the galactic center with ALMA

`2019PASJ...71..128T` | Publications of the Astronomical Society of Japan 2019 | first author: Tsuboi, Masato | arXiv: 1909.13405 | DOI: 10.1093/pasj/psz116

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: How do the ionized gas of the G-0.02-0.07 H II regions and the surrounding molecular gas in the 50MC relate, and what do they say about the massive star formation history?  
  > "the structure and kinematics of the ionized gas of the G-0.02-0.07 H$_{\mathrm{II}}$ region complex and the surrounding molecular gas may trace the history of the massive star formation." (1 Introduction)
- Target **G-0.02-0.07 H II region complex (HII-A to HII-D)**: coordinates _not stated_; z/distance 8 kpc (1" = 0.04 pc)  
  > "Throughout this paper, we adopt 8 kpc as the distance to the Galactic center (e.g. (cite: Boehle))." (1 Introduction); distance from Galactic center distance (cite: Boehle)  
  > "Throughout this paper, we adopt 8 kpc as the distance to the Galactic center (e.g. (cite: Boehle))." (1 Introduction)

## Data provenance

- ALMA projects: 2012.1.00080.S
- bands: _not stated_
- frequencies and spectral setup: channel width 244 kHz; velocity resolution 1.7 km/s (488 kHz)  
  > "The frequency channel width is 244 kHz. The velocity resolution is $1.7$ km s$^{-1}$(488 kHz)." (2 Observation and Data Reduction)
- continuum bandwidth: _not stated_
- arrays: 12-m array 137-pointing mosaic plus 7-m array (ACA) 52-pointing mosaic, 330"x330"  
  > "The entire ALMA observation consists of a 137 pointing mosaic of the 12-m array and a 52 pointing mosaic of the 7-m array (ACA)" (2 Observation and Data Reduction)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: natural: 2.5"x1.9" (PA=-31°) at 86 GHz, 2.2"x1.7" at 98 GHz; Briggs R=0.5: 2.0"x1.4", 1.9"x1.3"  
  > "The angular resolutions using “natural weighting" as *u-v* sampling at 86 and 98 GHz are $2.5\ensuremath{''} \times 1.9\ensuremath{''}, PA=-31^\circ$ and $2.2\ensuremath{''} \times 1.7\ensuremath{''}$" (2 Observation and Data Reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: time span of one year and seven months  
  > "Because the observation has a large time span of one year and seven months" (2 Observation and Data Reduction)
- pi or archival as stated: ALMA Cy.1, PI M. Tsuboi  
  > "ALMA Cy.1 observation (2012.1.00080.S. PI M.Tsuboi)" (2 Observation and Data Reduction)
- Line: H42alpha recombination line (85.6884 GHz)
- Line: H13CO+ J=1-0 (86.754288 GHz)
- Line: SiO v=0 J=2-1 (86.846995 GHz)
- Line: CS J=2-1 (97.980953 GHz)
- Other facility **Nobeyama 45-m telescope**: previous SiO/H13CO+ ratio map of the 50MC  
  > "using the Nobeyama 45-m telescope ((cite: Tsuboi2011), (cite: Tsuboi2015))" (4.5 Origin of the Massive Young Stars)
- External data: Continuum flux densities at 1.5, 5.0 GHz  
  > "$^1$ (cite: Ekers1983)." (Table 1) [from (cite: Ekers1983)]
- External data: Continuum flux densities at 8.4 GHz  
  > "$^2$ (cite: Mills)." (Table 1) [from (cite: Mills)]
- External data: Continuum flux densities at 14.7 GHz  
  > "$^3$ (cite: Goss1985)." (Table 1) [from (cite: Goss1985)]
- Simulation/model as data: RADEX non-LTE CS J=2-1 brightness temperatures vs n0 (Table 3)  
  > "The values are based on the non-LTE calculation, RADEX ((cite: VanderTak))." (Table 3)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Titan, Neptune and Mars  
  > "The flux density scale was determined using Titan, Neptune and Mars." (2 Observation and Data Reduction)
- flux scale uncertainty: as large as 15 %  
  > "the absolute flux density uncertainty may be as large as 15 %" (2 Observation and Data Reduction)
- self calibration: _not stated_

### Imaging

- task: CASA  
  > "The calibration and imaging of the data were done by CASA (cite: McMullin)." (2 Observation and Data Reduction)
- deconvolver: _not stated_
- weighting robust: natural weighting and Briggs R=0.5  
  > "briggs weighting ($R=0.5$)" at 86 and 98 GHz are $2.0\ensuremath{''} \times 1.4\ensuremath{''}$" (2 Observation and Data Reduction)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: UVCONTSUB fitorder=1  
  > "The continuum emission was subtracted from the spectral data using the CASA task UVCONTSUB ($fitorder=1$)." (2 Observation and Data Reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: FEATHER with Total Power data for molecular lines  
  > "We performed it using the CASA task "FEATHER"." (2 Observation and Data Reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Detailed single-dish feathering procedure and full molecular results  
  > "We presented the detailed description of the procedure and the full results in another paper (cite: Uehara)." (2 Observation and Data Reduction) [from (cite: Uehara)]

### Not stated but needed to reproduce (our reading)

- CASA version
- pipeline vs manual calibration and bandpass/gain calibrators
- line-free channels for UVCONTSUB
- cell size, image size, cleaning threshold and masks
- which dates/execution blocks and configurations
- exact integration circles for each HII region
- primary-beam correction
- how the sampling positions a-j were chosen
- rms noise of maps
- He+/H+ ratio origin and a(nu,T) adopted value

## Analysis recipe

1. **Measure continuum flux, size and brightness temperature**: Integrate 85.7 GHz continuum within circles; mean radius from 5 sigma contour area  
  > "The area is within the 5 $\sigma$ contour." (3.1)
   - software: CASA
   - assumption: Distance 8 kpc  
  > "we adopt 8 kpc as the distance to the Galactic center" (1 Introduction)
   - fitting: _not stated_
   - validation: Compared with lower-frequency fluxes, optically thin S ∝ nu^-0.1  
  > "our derived values are on the whole consistent with previous values at lower frequencies" (3.1)
2. **Measure H42alpha line parameters**: Gaussian fits to line profiles for centre velocity, FWHM; integrated intensity over 7.5-77.5 km/s  
  > "The LSR center velocities by Gaussian fit of HII-A, HII-B, HII-C, and HII-D are" (3.4)
   - software: CASA
   - fitting: _not stated_
   - validation: Consistent with previous observations  
  > "These derived velocities are consistent with those of previous observations" (3.4)
3. **Derive LTE electron temperature and density**: Te from line-to-continuum ratio; ne from Altenhoff formula with spherical path length L=4R/3  
  > "is estimated from the ratio between the integrated recombination line intensity, $\int S_{\mathrm{line}}(\mathrm{H}42\alpha)dV$, and the continuum flux density" (4.2.1)
   - parameter: N(He+)/N(H+)=0.09  
  > "We assume that the number ratio of He$^+$ to H$^+$ is $\frac{N(\mathrm{He^+})}{N(\mathrm{H^+})}=0.09$" (4.2.1)
   - assumption: Optically thin line and continuum  
  > "assuming that the line and continuum emissions are optically thin" (4.2.1)
   - fitting: _not stated_
   - validation: Line brightness much lower than Te, supporting optically thin; ~10% uncertainty  
  > "These indicate that the optically thin assumption is valid in the compact H$_{\mathrm{II}}$ regions." (4.2.1)
4. **Ambient density and expansion age, spectral type**: RADEX CS J=2-1 for n0; Vexp from FWHM and sound speed; Stromgren radius, age and Q0; compare with Martins2005 calibration  
  > "Then the mean expanding velocities of HII-A, HII-B, HII-C, and HII-D are $V_{\mathrm{exp}}=16.7, 11.6, 11.1$, and $12.1$ km s$^{-1}$, respectively." (4.4)
   - software: RADEX
   - parameter: X(CS)=1e-8, TK=150 K, dV=15 km/s, path 3 pc, TB~6 K  
  > "The fractional abundance and gas kinetic temperature of CS molecule are assumed to be $X{\mathrm{(CS)}}=1\times 10^{-8}$" (4.4)
   - assumption: Spherical HII region in uniform ambient gas; Maxwell distribution; single main-sequence stars  
  > "Here the Maxwell distribution is assumed for convenience." (4.4)
   - fitting: _not stated_
   - validation: Compared with previous radio and IR spectral types  
  > "These derived spectral types are roughly consistent with the previous radio estimation" (4.4)

## Software

- **CASA** : calibration, imaging, UVCONTSUB, FEATHER  
  > "The calibration and imaging of the data were done by CASA (cite: McMullin)." (2 Observation and Data Reduction)
- **RADEX** : non-LTE CS J=2-1 brightness temperature to derive n0  
  > "We would derive the gas density of the ambient molecular gas, $n_0$, using the non-LTE calculation, RADEX" (4.4)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| 85.7 GHz flux density HII-A | 426 | 10 | mJy | 1 | $S_\nu$(85.7 GHz) \[mJy\] / $426\pm10$ |
| H42alpha FWHM HII-A | 36.2 | 1.6 | km/s | 2 | $\Delta V_{\mathrm{FWHM}}=36.2\pm1.6$ |
| Electron temperature range | 5150-5920 | ~10% | K | 3 | $T_{\mathrm{e}}=5150-5920$ K |
| Electron density range | 950-2340 | ~10% | cm^-3 | 3 | $n_{\mathrm{e}}=950-2340$ cm$^{-3}$ |
| Ambient gas density n0 | 1.5e4 | ±50% | cm^-3 | 4 | the gas density is estimated to be $n_0\sim 1.5\times10^4$ cm$^{-3}$. The uncertainty is guessed to be as large as $\pm50$ %. |
| Expansion velocities A-D | 16.7, 11.6, 11.1, 12.1 | not stated | km/s | 4 | $V_{\mathrm{exp}}=16.7$, $11.6$, $11.1$, and $12.1$ km s$^{-1}$ |
| Ages A-D | 1.4e4, 1.7e4, 2.0e4, 0.7e4 | ~30% | yr | 4 | the typical uncertainty of the age is as large as $30~\%$ |

## Qualitative findings

- HII-A,B,C lie on the near side of the 50MC, HII-D on the far side  
  > "HII-A, B and C are located on the near side of the 50 km s$^{-1}$ Molecular Cloud (50MC) but HII-D is located on the far side." (abstract)

## Claim tuples

- H: Where are the HII regions along the line of sight relative to the 50MC? | E: Compare absorption dips in CS and H13CO+ against continuum brightness | R: H13CO+ dip toward HII-D (~0.3 K), none deeper than 0.02 K toward A and C | F: A-C on near side, D on far side | **supported**
- H: Are bright/dark halves due to bow shocks? | E: Compare Te, ne, pressure and velocities of halves | R: Bright halves have lower Te, higher ne; no shocked gas in front | F: No evidence for bow shock | **supported**
- H: Did a cloud-cloud collision shock trigger the star formation? | E: Compare SiO enhancement, Class I masers and HII positions | R: HII regions lie on concave side of SiO feature, masers on its edge | F: Shock propagated from HII-C to HII-A, triggering star formation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Bow-shock origin of asymmetric brightness rejected  
  > "Therefore there is no observational evidence supporting the bow shock picture." (4.5)
- How they decided it was enough: _not stated_
- Limitation (authors): Simple assumptions (spherical, uniform density) add ambiguity; HII-D not resolved  
  > "The ambiguity of our estimation would be caused by our simple assumptions" (4.4)
- Caveat (inferred, ours): Te depends on assumed He+/H+ and optically thin assumption
- Caveat (inferred, ours): Single n0 adopted for all regions
- Caveat (inferred, ours): Age from simple expansion model, no error propagation
- Caveat (inferred, ours): No pressure/Hii-region distance independent check

## Reproducibility

- Data public (paper): ALMA data acknowledged by project code; no explicit public statement  
  > "This paper makes use of the following ALMA data:ADS/JAO.ALMA#2012.1.00080.S." (Summary)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: feather details (in Uehara 2019a)
- Missing: integration region definitions
- Data volume (inferred): Large mosaic (137+52 pointings); likely hundreds of GB raw, tens of GB products
- Score (inferred): 3/5, Analysis equations and values given, but processing parameters largely missing.
- Rediscovery candidate: no, Imaging recipe is incomplete (version, masks, regions) though numbers are quantitative.

## Links

- Method: (cite: Uehara) (feathering procedure and full molecular results)
- Companion: (cite: Uehara) (companion ALMA analysis of 50MC molecular gas)
- Related: ALMA large-scale mosaic of Sgr A complex

## Checks

```json
{
 "quotes": 55,
 "quotes_ok": 55,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 7,
 "numeric_problems": 0,
 "fill": {
  "facts": 71,
  "stated": 39,
  "rate": 0.549
 },
 "evidence_ok": true
}
```
