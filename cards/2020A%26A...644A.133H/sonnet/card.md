# APEX-SEPIA660 Early Science: gas at densities above 10<SUP>7</SUP> cm<SUP>-3</SUP> towards OMC-1

`2020A&A...644A.133H` | Astronomy and Astrophysics 2020 | first author: Hacar, A. | arXiv: 2009.12549 | DOI: 10.1051/0004-6361/202038138

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type multi_facility_alma_minor

## Science

- Fields: star_formation, milky_way_ism
- Question: What are the densities of the star-forming gas in OMC-1 near the Orion Nebula Cluster, probed by N2H+ (7-6) at 652 GHz with APEX-SEPIA660 and compared with ALMA N2H+ (1-0)?  
  > "We investigated the density properties of the star-forming gas in the OMC-1 region located in the vicinity of the Orion Nebula Cluster (ONC)." (abstract)
- Target **OMC-1 (Orion BN/KL, OMC-1 Ridge, OMC-1 South)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2015.1.00669.S
- bands: _not stated_
- frequencies and spectral setup: N2H+ (7-6) 652095.865 MHz and C18O (6-5) 658553.278 MHz, 240 kHz (0.11 km/s) native resolution, 8 GHz bandwidth, XFFTS backend (APEX SEPIA660)  
  > "observed simultaneously with a native spectral resolution of 240 kHz (or 0.11 km s$^{-1}$) thanks to the large instantaneous bandwidth (8 GHz) of the new SEPIA660 receiver connected to an XFFTS backend" (2 New SEPIA660 observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: 10 arcsec (convolved SEPIA660 maps)  
  > "We convolved our N$_2$H$^+$ (7–6) and C$^{18}$O (6–5) datasets into a uniform Nyquist sampled grid with a final resolution of 10 arcsec." (2 New SEPIA660 observations)
- max recoverable scale: _not stated_
- sensitivity: rms ~0.65 K  
  > "well above the noise level our our data with $<rms> \sim 0.65$ K" (4 Gas at densities)
- time on source: _not stated_
- observing dates: August 2019, PWV <= 0.5 mm  
  > "Our observations were carried out in August 2019 under excellent weather conditions with a Precipitable Water Vapor (PWV) of PWV$\le$ 0.5 mm" (2 New SEPIA660 observations)
- pi or archival as stated: _not stated_
- Line: N2H+ J=7-6 (652095.865 MHz)
- Line: C18O J=6-5 (658553.278 MHz)
- Other facility **APEX-12m SEPIA660**: N2H+ (7-6) and C18O (6-5) OTF maps of OMC-1  
  > "We combine four on-the-fly (OTF) maps covering a total area of $\sim 450 \times 200$ arcsec$^2$" (2 New SEPIA660 observations)
- External data: ALMA N2H+ (1-0) maps and N(N2H+)=5e13 from hyperfine opacity analysis  
  > "derived from detailed analysis of the hyperfine opacities obtained in our previous N$_2$H$^+$ (1–0) observations (cite: HAC18)" (4 Gas at densities) [from (cite: HAC18)]
- External data: Gas temperature estimates for OMC-1 (Ridge ~25 K, South ~35 K)  
  > "slightly warmer conditions found towards OMC-1 South ($T_\mathrm{K}\sim$ 35 K) compared to the OMC-1 Ridge ($T_\mathrm{K}\sim$ 25 K) (cite: HAC19)" (4 Gas at densities) [from (cite: HAC19)]

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
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: convolved to Nyquist-sampled grid, 10 arcsec  
  > "We convolved our N$_2$H$^+$ (7–6) and C$^{18}$O (6–5) datasets into a uniform Nyquist sampled grid with a final resolution of 10 arcsec." (2 New SEPIA660 observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- N2H+ (1-0) ALMA data and hyperfine-derived column density  
  > "obtained in our previous N$_2$H$^+$ (1–0) observations (cite: HAC18)" (4 Gas at densities) [from (cite: HAC18)]

### Not stated but needed to reproduce (our reading)

- How the ALMA N2H+ (1-0) data were reduced and matched to the SEPIA 10 arcsec grid
- Baseline polynomial order and line-free windows
- Method for the 30 Msun mass estimate (column density to mass conversion)
- Kinetic temperature map used per position
- Distance to Orion adopted
- Total integration time

## Analysis recipe

1. **Reduce and map SEPIA660 data**: Extract, reduce and combine OTF maps in GILDAS/CLASS, convolve to 10 arcsec, baseline subtract, convert to Tmb with eta_mb=0.4  
  > "Each molecular species was extracted, reduced, and combined independently using the software GILDAS/CLASS." (2 New SEPIA660 observations)
   - software: GILDAS/CLASS
   - parameter: eta_mb = 0.4  
  > "assuming a typical main-beam efficiency of $\eta_{mb}=0.4$ measured in Uranus" (2 New SEPIA660 observations)
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit line spectra**: Single Gaussian fit to each N2H+ (7-6) spectrum  
  > "We fitted all our N$_2$H$^+$ (7–6) spectra using a single Gaussian velocity component." (4 Gas at densities)
   - fitting: single Gaussian  
  > "We fitted all our N$_2$H$^+$ (7–6) spectra using a single Gaussian velocity component." (Gas at densities $>10^7$ cm$^{-3}$ in OMC-1)
   - validation: Gaussian peak temperatures agree with full-hyperfine predictions within <=15%  
  > "our gaussian fits accurately reproduce the line peak temperatures of the observed N$_2$H$^+$ (1–0) and (7–6) spectra within $\le$ 15%" (4 Gas at densities)
3. **Constrain density with RADEX**: RADEX grid in density 1e5-1e8 cm^-3 for TK=15, 25, 35 K, compared with observed Tmb(7-6) and the 7-6/1-0 ratio  
  > "Our models include three representative gas kinetic temperatures, namely, $T_\mathrm{K}=$ 15 K, 25 K, and 35 K" (4 Gas at densities)
   - software: RADEX
   - parameter: N(N2H+)=5e13; LAMDA collisional coefficients; single line without hyperfine structure  
  > "Our calculations assume the latest collisional coefficients and energy levels provided by the Leiden Molecular Database (cite: LAMDA) without hyperfine structure." (4 Gas at densities)
   - assumption: LAMDA rates extrapolated from HCO+; factor 3-5 density uncertainty  
  > "The difference between the two approximately introduces an uncertainty of a factor of 3-5 in our density estimates (cite: LIQ15)." (4 Gas at densities)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **GILDAS/CLASS** : reduction and combination of SEPIA660 data  
  > "Each molecular species was extracted, reduced, and combined independently using the software GILDAS/CLASS." (2 New SEPIA660 observations)
- **RADEX** : radiative transfer modelling of N2H+ lines  
  > "We used the radiative transfer calculations provided by RADEX (cite: RADEX)" (4 Gas at densities)
- **APLpy** : plotting  
  > "This research made use of APLpy, an open-source plotting package for Python (cite: Astropy)." (Acknowledgements)
- **TOPCAT** : _not stated_

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of independent beams with N2H+ (7-6) S/N>3 | 384 | not stated | beams | 2 | 384 independent beams in our maps show N$_2$H$^+$ (7–6) spectra with signal-to-noise (S/N) larger than 3. |
| Mean N2H+ (7-6) Tmb | ~4 | not stated | K | 2 | mean values of $T_\mathrm{mb}$(N$_2$H$^+$ (7–6)) $\sim$ 4 K |
| N2H+ (7-6) linewidth | ~1.3 | not stated | km/s | 2 | linewidths $\Delta V$(N$_2$H$^+$ (7–6)) $\sim$ 1.3 km s$^{-1}$ |
| Gas mass at n(H2)>1e7 cm^-3 | >=30 | lower limit | Msun | 3 | we estimate a minimum of 30 M$_\odot$ at densities n(H$_2$) $>10^7$ cm$^{-3}$ within our maps. |
| Tmb(7-6)/Tmb(1-0) at OMC-1 Ridge | ~0.5 | not stated | dimensionless | 2 | At the OMC-1 ridge, comparisons between our SEPIA660 and ALMA data show values with |

## Qualitative findings

- N2H+ (7-6) emission is extended, avoids hot BN/KL, and is anticorrelated with C18O (6-5), which traces warm low-column gas  
  > "we find no significant N$_2$H$^+$ (7–6) emission at the position of the hot Orion BN/KL region" (3 Dense gas exposed to the ONC)

## Claim tuples

- H: Does OMC-1 contain parsec-scale gas at n(H2)>1e7 cm^-3? | E: Mapped N2H+ (7-6) with SEPIA660 and compared with ALMA (1-0) using RADEX models | R: Observed Tmb and the 7-6/1-0 ratio are reproduced only by n(H2)>5e7 cm^-3 | F: Large reservoirs of gas at n>1e7 cm^-3 exist near the ONC | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Single-component RADEX without hyperfine structure, extrapolated collisional rates, factor 3-5 density uncertainty; first-order estimate only  
  > "Our analysis focuses on a simplified description of the N$_2$H$^+$ (1–0) and (7–6) peak temperatures ($T_\mathrm{mb}$) meant to obtain a first order approximation" (4 Gas at densities)
- Caveat (inferred, ours): Densities rest on a single-component, one-column-density RADEX model with no uncertainty propagation
- Caveat (inferred, ours): Beam filling and the 10 arcsec versus ALMA resolution matching are not discussed
- Caveat (inferred, ours): Mass estimate method is not described

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Mass calculation recipe
- Missing: ALMA (1-0) data processing
- Missing: Baseline fitting details
- Data volume (inferred): small (<1 GB) for SEPIA data; ALMA N2H+ (1-0) cubes several GB
- Score (inferred): 3/5, APEX data and RADEX setup are described but the ALMA part is inherited and the mass estimate is vague.
- Rediscovery candidate: no, The main data are APEX SEPIA660 observations, and the ALMA role is a comparison with previously published data.

## Links

- Method: (cite: RADEX) (radiative transfer code)
- Companion: (cite: HAC18) (ALMA N2H+ (1-0) observations of OMC-1)
- Companion: (cite: TEN20) (N2H+ (3-2) in OMC-1)
- Related: ORION-4D

## Checks

```json
{
 "quotes": 34,
 "quotes_ok": 34,
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
  "facts": 65,
  "stated": 23,
  "rate": 0.354
 },
 "evidence_ok": true
}
```
