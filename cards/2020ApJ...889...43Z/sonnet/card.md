# Dense Cores, Filaments, and Outflows in the S255IR Region of High-mass Star Formation

`2020ApJ...889...43Z` | The Astrophysical Journal 2020 | first author: Zinchenko, Igor I. | arXiv: 1911.11447 | DOI: 10.3847/1538-4357/ab5c18

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What are the spatial and kinematic structure of the high-mass star-forming region S255IR (dense cores, filaments, outflows) at ~0.1 arcsec resolution?  
  > "We investigate at a high angular resolution the spatial and kinematic structure of the high mass star-forming region, which demonstrated recently the first disk-mediated accretion burst in the massive young stellar object." (abstract)
- Target **S255IR region (SMA1, SMA2, SMA3, SMM1, SMM2)**: coordinates SMA1 circle centre R.A.(J2000)=06h12m54.008s, Dec.(J2000)=17d59m23.12s  
  > "The distance to the source derived from the annual parallax measurements of water masers is $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction); z/distance 1.78 (+0.12/-0.11) kpc  
  > "The distance to the source derived from the annual parallax measurements of water masers is $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction); distance from water maser parallax (Burns16)  
  > "The distance to the source derived from the annual parallax measurements of water masers is $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction)

## Data provenance

- ALMA projects: 2015.1.00500.S
- bands: Band 7  
  > "The observations were performed with ALMA in Band 7 during several observing sessions in 2016–2017" (2 Observations)
- frequencies and spectral setup: 4 spectral windows at ~335.4, 337.3, 349.0, 346.6 GHz; bandwidths 1875.0, 234.4, 937.5, 1875.0 MHz; channel 244 kHz (C34S, CCH), 977 kHz (CO, SiO); Hanning smoothing  
  > "four spectral windows were observed, centered at around 335.4 GHz, 337.3 GHz, 349.0 GHz, and 346.6 GHz, with bandwidths of 1875.0 MHz, 234.4 MHz, 937.5 MHz, and 1875.0 MHz." (2 Observations); "The spectral resolution was twice of these values with Hanning-smoothing applied." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15 m to 3.0 km  
  > "The projected array baselines for all sessions range between 15 m and 3.0 km." (2 Observations)
- angular resolution: ~0.11x0.15 arcsec (~180 AU)  
  > "The resulting images achieve an angular resolution of $0{\ensuremath{''}}11\times 0{\ensuremath{''}}14$ (PA = –6.9$^\circ$) for C$^{34}$S" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2016–2017  
  > "during several observing sessions in 2016–2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: CO J=3-2 (345.8 GHz)
- Line: C34S J=7-6 (337.4 GHz)
- Line: SiO J=8-7 (347.3 GHz)
- Line: CCH N=4-3 (349.4 GHz)
- External data: CCH line strengths from CDMS  
  > "the ratio of the line strengths of these lines is $\approx 29.2$ (CDMS – (cite: Mueller05; Endres16))" (3 Results) [from (cite: Mueller05; Endres16)]
- External data: Dust opacity 1.8 cm2/g at this wavelength  
  > "Assuming the dust opacity at this wavelength of 1.8 cm$^2$ g$^{-1}$ according to (cite: Ossenkopf94)" (4.1 General structure) [from (cite: Ossenkopf94)]
- External data: Distance 1.78 kpc  
  > "The distance to the source derived from the annual parallax measurements of water masers is $1.78^{+0.12}_{-0.11}$ kpc (cite: Burns16)." (Introduction) [from (cite: Burns16)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "for continuum with Briggs weighting with a robust parameter of 0.5." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: Hanning smoothing  
  > "The spectral resolution was twice of these values with Hanning-smoothing applied." (2 Observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Details of 2016 observations  
  > "Details of the observations in 2016 are given in (cite: Zin17)." (2 Observations) [from (cite: Zin17)]
- Details of 2017 observations  
  > "Details of the observations in 2017 are given in (cite: Liu18)." (2 Observations) [from (cite: Liu18)]

### Not stated but needed to reproduce (our reading)

- CASA version and calibration/pipeline details
- Flux, bandpass, phase calibrators and flux scale uncertainty
- Self-calibration and combination of 2016 and 2017 sessions (SMA1 variable)
- Continuum-subtraction line-free channels
- Cell/image size, masking, deconvolver, cleaning thresholds
- Final rms per image
- Velocity ranges for CO wing integration
- Method for RADEX fits (grid, fitting criterion)
- Dust-to-gas and CO abundance used for H2 conversion

## Analysis recipe

1. **Measure continuum sources and filament**: 2D Gaussian fits to compact sources; filament flux from total minus cores; intensity cuts for width  
  > "The estimates of the fluxes and sizes of the continuum sources obtained from 2D Gaussian fit are given in Table [1](#table:cont-mm)." (3 Results)
   - fitting: _not stated_
   - validation: _not stated_
2. **CCH excitation and optical depth**: Hyperfine line ratio with equal Tex, plus RADEX modelling  
  > "We modeled the CCH excitation with RADEX (cite: vdTak07)." (3 Results)
   - software: RADEX
   - assumption: Same excitation temperature for all transitions; beam filling factor unity  
  > "under the assumption of the same excitation temperature for all transitions" (3 Results)
   - fitting: _not stated_
   - validation: Compared RADEX with line ratios  
  > "At lower densities the excitation of different components becomes significantly different and the intensity ratios for the stronger components are inconsistent with the observations." (3 Results)
3. **Filament mass and density from dust continuum**: Optically thin dust emission with Td=50 K, opacity 1.8 cm2/g, mu=2.8  
  > "we obtain the dust column density $\sim 0.03$ g cm$^{-2}$ and assuming the mean molecular weight per hydrogen molecule of 2.8 (cite: Kauffmann08)" (4.1 General structure)
   - assumption: Dust temperature equal to gas temperature, 50 K; thickness equal to width  
  > "We assume the kinetic temperature in the continuum filament to be 50 K." (4.1 General structure)
   - fitting: _not stated_
   - validation: _not stated_
4. **C34S column density and abundance**: RADEX with CS 7-6 as proxy  
  > "for the CS $J=7-6$ transition (C$^{34}$S is absent in the RADEX database)" (4.1 General structure)
   - software: RADEX
   - fitting: _not stated_
   - validation: _not stated_
5. **Outflow properties and SiO abundance**: CO(3-2) wings under LTE, low optical depth; outflow timescale; SiO/CO intensity ratio  
  > "under the assumptions of the LTE conditions and low optical depth, which translates into $N(\mathrm{H_2})\ensuremath{\gtrsim} 1.3\times 10^{22}$ cm$^{-2}$." (4.2 Outflow from SMA1)
   - software: RADEX
   - assumption: Inclination ~80 deg for SMA1  
  > "most probably it is rather large, about 80$^\circ$" (4.2 Outflow from SMA1)
   - fitting: _not stated_
   - validation: RADEX shows optical depths <~1  
  > "the optical depth for both SiO and CO transitions is moderate ($\ensuremath{\lesssim} 1$)" (4.2 Outflow from SMA1)
6. **SMA2 rotation and masses**: C34S position-velocity diagram for Keplerian-like rotation; disk mass from continuum  
  > "The data are consistent with the assumption of a Keplerian-like rotation of the core." (4.3 SMA2)
   - assumption: Td=50 K, gas-to-dust ratio 100  
  > "assuming the dust temperature of 50 K and a normal gas-to-dust mass ratio of 100" (4.3 SMA2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **RADEX** : Non-LTE modelling of CCH, CS/C34S, SiO and CO excitation  
  > "We modeled the CCH excitation with RADEX (cite: vdTak07)." (3 Results)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Total continuum flux density at 0.9 mm | 6.6 | not stated | Jy | 1 | The total flux density in continuum is approximately 6.6 Jy. |
| Filament flux density | 5.4 | not stated | Jy | 1 | arrive at an estimate for the filament flux density of 5.4 Jy |
| Filament width (FWHM) | 0.6-1 arcsec (1000-1800 AU) | not stated | arcsec | 1 | the filament width at the half intensity level is $\sim 0.6-1$ arcsecond, which corresponds to $\sim 1000-1800$ AU |
| CCH excitation temperature | ~50 | not stated | K | 2 | we obtain the excitation temperature $T_{ex}\approx 50$ K. |
| Filament mass | ~35 | not stated | Msun | 3 | The total mass of the filamentary structure seen in continuum is about 35 M$_\odot$ |
| Filament mean H density | ~3e7 | not stated | cm-3 | 3 | we obtain the mean hydrogen volume density $n\sim 3\times 10^7$ cm$^{-3}$ |
| SMA1 outflow dynamical time | ~700 | not stated | yr | 5 | we obtain the outflow dynamic time scale about 700 years |
| SMA1 high-velocity gas mass | >=0.3 | not stated | Msun | 5 | is $\ensuremath{\gtrsim} 0.3$ M$_\odot$ (assuming a low optical depth) |
| Mass loss rate | >=4e-4 | not stated | Msun/yr | 5 | $\dot{M}\ensuremath{\gtrsim} 4\times 10^{-4}$ M$_\odot$ year$^{-1}$ |
| SiO abundance relative to H | ~1e-8 | not stated | dimensionless | 5 | This implies the SiO abundance relative to hydrogen $X(\mathrm{SiO}\sim 10^{-8}$ |
| SMA2 dynamical mass | M sin^2 i ~2 | not stated | Msun | 6 | the dynamical central mass obtained from the rotation velocity is much higher, $M \sin^2 i \sim 2$ M$_\odot$ |
| SMA2 disk mass | ~0.4 | not stated | Msun | 6 | The continuum flux gives an estimate of the disk mass $\sim 0.4$ M$_\odot$ |
| SMM1 flux density | 15 | not stated | mJy | 1 | / SMM1 / 06:12:53.884 / 17.59.24.99 / 15 / 0.20 / 0.14 / 17 / |
| SMM1/SMM2 masses | ~0.3 and ~0.2 | not stated | Msun | 3 | These values correspond to masses of $\sim 0.3$ M$_\odot$ and $\sim 0.2$ M$_\odot$, respectively (assuming the dust temperature of 20 K). |

## Qualitative findings

- Dense warm walls around the SMA1 wide-angle outflow seen in C34S and CCH  
  > "We detected warm and dense walls around this wide-angle molecular outflow." (5 Conclusions)

## Claim tuples

- H: Do C34S/CCH filaments trace outflow cavity walls? | E: Compare C34S, CCH with CO and SiO maps | R: C34S surrounds the red lobe; SiO at the interface | F: Walls of dense warm gas around the SMA1 wide-angle outflow, thickness ~1000-2000 AU | **supported**
- H: Is SMA2 driving a separate outflow, from a binary? | E: CO and SiO channel maps, C34S PV | R: Bent outflow with chain of knots 350-500 AU apart; Keplerian-like rotation | F: Possible formation of a binary of low/intermediate-mass stars | **partially**
- H: Are SMM1 and SMM2 new cores prestellar? | E: Continuum detection, no line emission or IR source | R: Masses ~0.2-0.3 Msun | F: May be low-mass prestellar cores | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Reduced dust-to-gas ratio (dust destruction/sweeping) rejected to explain C34S emission without continuum  
  > "Therefore we conclude that this alternative explanation can be rejected." (4.1 General structure)
- How they decided it was enough: _not stated_
- Limitation (authors): Wall temperature >=100 K cannot be confirmed by the data  
  > "Unfortunately the assumption of such high temperature cannot be confirmed by the available observational data." (4.1 General structure)
- Limitation (authors): Resolution insufficient for firm disk conclusion in SMA2  
  > "although the achieved spatial resolution is not sufficient for a firm conclusion" (4.3 SMA2)
- Caveat (inferred, ours): Many estimates assume LTE, unit filling factor and low optical depth with no uncertainties
- Caveat (inferred, ours): Temperature assumptions drive masses and densities
- Caveat (inferred, ours): No formal fits or error propagation

## Reproducibility

- Data public (paper): Project code cited, data used under ALMA project 2015.1.00500.S  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00500.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Calibration and imaging details
- Missing: Exact integration ranges and masks
- Missing: RADEX input grids
- Data volume (inferred): ~100-300 GB raw for several Band 7 sessions
- Score (inferred): 3/5, Data public and main imaging parameters partly given, but calibration, masking and many analysis choices are unstated, and the results are estimates.
- Rediscovery candidate: no, Recipe incomplete (calibration, combination of epochs, integration ranges unstated) and many results are assumption-driven.

## Links

- Method: (cite: Zin17) (2016 observation details)
- Method: (cite: Liu18) (2017 observation details)
- Companion: (cite: Zin18-raa) (Earlier ALMA results on S255IR outflows and filament)

## Checks

```json
{
 "quotes": 58,
 "quotes_ok": 58,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 14,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 34,
  "rate": 0.453
 },
 "evidence_ok": true
}
```
