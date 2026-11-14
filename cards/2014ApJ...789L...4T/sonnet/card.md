# ALMA Observations of a High-density Core in Taurus: Dynamical Gas Interaction at the Possible Site of a Multiple Star Formation

`2014ApJ...789L...4T` | The Astrophysical Journal Letters 2014 | first author: Tokuda, Kazuki | arXiv: 1405.7574 | DOI: 10.1088/2041-8205/789/1/L4

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation
- Question: What is the dense-gas structure, outflow and dynamics at the center of MC27/L1521F, a core close to the first protostellar core phase, and does it indicate multiple star formation?  
  > "We found a few starless high-density cores, one of which has a very high density of $\sim$10$^{7}$cm$^{-3}$" (abstract)
- Target **MC27/L1521F**: coordinates 04h28m38.92s, +26d51m36.2s (J2000)  
  > "toward MC27/L1521F with the center position of ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (4$^{\rm h}$28$^{\rm m}$38.92s, +26$^\circ$51$''$36.2$''$)" (2 Observations); "the distance of the source (140 pc (cite: Elias1978))" (3.1 High-density Dust Cores); z/distance 140 pc  
  > "toward MC27/L1521F with the center position of ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (4$^{\rm h}$28$^{\rm m}$38.92s, +26$^\circ$51$''$36.2$''$)" (2 Observations); "the distance of the source (140 pc (cite: Elias1978))" (3.1 High-density Dust Cores); distance from Elias 1978  
  > "toward MC27/L1521F with the center position of ($\alpha_{J2000.0}$, $\delta_{J2000.0}$) = (4$^{\rm h}$28$^{\rm m}$38.92s, +26$^\circ$51$''$36.2$''$)" (2 Observations); "the distance of the source (140 pc (cite: Elias1978))" (3.1 High-density Dust Cores)

## Data provenance

- ALMA projects: 2011.0.00611.S
- bands: Band 6 (211–275 GHz), Cycle 0  
  > "We carried out ALMA Band 6 (211–275 GHz) observations toward MC27/L1521F" (2 Observations)
- frequencies and spectral setup: Bandwidth 234.4 MHz (61.04 kHz x 3840 channels), frequency domain mode  
  > "The correlator was used in the frequency domain mode with a bandwidth of 234.4 MHz (61.04 kHz $\times$ 3840 channels)." (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: January: 16 antennas compact; November: 24 antennas compact+extended  
  > "The January observations were carried out by using 16 antennas with a compact configuration, and the November observations by 24 antennas with a compact+extended configuration." (2 Observations)
- baselines: 26.5 m to 381.8 m (12.2 to 211 kλ)  
  > "The baselines range from 26.5 m to 381.8 m, corresponding to *uv* distances from 12.2 to 211 k$\lambda$." (2 Observations)
- angular resolution: ~1.0" x 0.8" for HCO+ (3-2); continuum ~1.1" x 0.8"  
  > "The synthesized beam is $\sim$1.0$''$ $\times$ 0.8$''$ = 140 AU $\times$ 110 AU for HCO$^+$ ($J$ = 3–2)" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: line rms ~8 mJy/beam at ~0.14 km/s; continuum rms 0.12 mJy/beam  
  > "The (1$\sigma$) rms of molecular lines are $\sim$8 mJy beam$^{-1}$ with a velocity resolution of $\sim$0.14 km s$^{-1}$." (2 Observations)
- time on source: _not stated_
- observing dates: 2012 Jan 11, Nov 5 and 6  
  > "on 2012 January 11 and on 2012 November 5 and 6" (2 Observations)
- pi or archival as stated: _not stated_
- Line: HCO+ J=3-2 (267.55763 GHz)
- Line: HCN J=3-2 (265.88643 GHz)
- Line: H13CO+ J=3-2 (260.25534 GHz)
- Line: CS J=5-4 (244.93556 GHz)
- Line: SiO J=6-5 (260.51802 GHz)
- Other facility **Spitzer**: Detection of the very low-luminosity protostar (Spitzer source)  
  > "around a very low-luminosity protostar detected by *Spitzer*" (abstract)
- External data: Distance 140 pc  
  > "the distance of the source (140 pc (cite: Elias1978))" (3.1 High-density Dust Cores) [from (cite: Elias1978)]
- External data: Inclination 20-40 deg  
  > "is $20$$\ensuremath{^\circ}$–$40$$\ensuremath{^\circ}$ (cite: Terebey2009)" (3.2 Very Compact Outflow) [from (cite: Terebey2009)]
- External data: H13CO+ abundance 1.0e-9  
  > "$X_{\rm H^{13}CO^{+}}$ = 1.0 $\times$ 10$^{-9}$ (cite: But1995)" (3.1 High-density Dust Cores) [from (cite: But1995)]

## Processing

### Calibration

- pipeline or manual: CASA used for processing; details not given  
  > "The data were processed in the Common Astronomy Software Applications package" (2 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0538-440, Callisto, Ganymede (Butler-JPL-Horizons 2012 model)  
  > "flux calibration on J0538–440, Callisto and Ganymede." (2 Observations)
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
- continuum subtraction: Continuum made by integrating all frequency ranges except line frequencies  
  > "The dust continuum emission was extracted by integrating all the frequency ranges except for the line frequencies." (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum ~1.1" x 0.8"  
  > "The synthesized beam and rms for the continuum map are $\sim$1.1$''$ $\times$ 0.8$''$" (2 Observations)
- final rms: continuum 0.12 mJy/beam  
  > "0.12 mJy beam$^{-1}$, respectively." (2 Observations)

### Inherited from earlier work

- Dust opacity 0.01 cm2/g at 231 GHz and beta=1  
  > "We assumed $T_d$ = 10 K and $\beta$ = 1 (cite: Kau2008)." (3.1 High-density Dust Cores) [from (cite: Oss1994; Kau2008)]

### Not stated but needed to reproduce (our reading)

- Imaging task, weighting/robust, cell and image size, deconvolution and masks
- CASA version
- Line-free channels used for continuum
- Mosaic combination of the two epochs and configurations
- Gain/flux calibration details and flux uncertainty
- How outflow peak positions and maximum velocities were measured
- Gas-to-dust ratio / mean molecular weight value

## Analysis recipe

1. **Image continuum and lines**: CASA processing and imaging; continuum from line-free frequency ranges  
  > "The data were processed in the Common Astronomy Software Applications package (http://casa.nrao.edu), and visibilities imaged." (2 Observations)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Core masses and column densities from dust**: Optically thin dust emission, M = F d^2 / (kappa B(Td))  
  > "We calculated the mass from the dust emission assuming optically thin emission and constant dust temperature" (3.1 High-density Dust Cores)
   - assumption: Td = 10 K, beta = 1, kappa231GHz = 0.01 cm2/g, d = 140 pc  
  > "We assumed $T_d$ = 10 K and $\beta$ = 1 (cite: Kau2008)." (3.1 High-density Dust Cores)
   - fitting: _not stated_
   - validation: Compared with H13CO+ derived values  
  > "we also estimated the mass and column density from the H$^{13}$CO$^+$ ($J$ = 3–2) data." (3.1 High-density Dust Cores)
3. **Mass and column density from H13CO+**: LTE, optically thin line emission  
  > "Under the assumption of the local thermodynamical equilibrium condition and optically thin molecular line emission" (3.1 High-density Dust Cores)
   - assumption: Tex = 10 K; X(H13CO+) = 1.0e-9  
  > "The excitation temperature is adopted as 10 K." (3.1 High-density Dust Cores)
   - fitting: Single Gaussian fit to H13CO+ line width  
  > "by fitting the profile with a single Gaussian profile" (Table 1)
   - validation: _not stated_
4. **Outflow size, velocity and dynamical timescale**: R_obs=R_flow cos i, V_obs=V_flow sin i; t=R_flow/V_flow  
  > "$R_{\rm obs} = R_{\rm flow} {\rm cos}i$, $V_{\rm obs} = V_{\rm flow} {\rm sin}i$" (3.2 Very Compact Outflow)
   - assumption: inclination 20-40 deg (0 = plane of the sky)  
  > "is $20$$\ensuremath{^\circ}$–$40$$\ensuremath{^\circ}$ (cite: Terebey2009)" (3.2 Very Compact Outflow)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** : Data processing and imaging  
  > "The data were processed in the Common Astronomy Software Applications package" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| MMS-2 density | ~10^7 | not stated | cm^-3 | 2 | is calculated to be $\sim$10$^7$ cm$^{-3}$ |
| MMS-2 dust mass | 3.5e-3 | not stated | Msun | 2 | 3.5 $\times$ 10$^{-3}$ |
| Outflow dynamical timescale, blue | 60-140 | not stated | yr | 4 | (blue = $60$–$140$ yr, red =$90$–$210$ yr) |
| Outflow dynamical timescale, red | 90-210 | not stated | yr | 4 | (blue = $60$–$140$ yr, red =$90$–$210$ yr) |
| MMS-1 flux | 1.7 | not stated | mJy | 1 | / MMS-1 / 4$^{\rm h}$28$^{\rm m}$38.96s / +26$^\circ$51$''$35.0$''$ / 1.7 / 200 / 2.0 / |
| MMS-2 flux | 4.4 | not stated | mJy | 1 | / MMS-2 / 4$^{\rm h}$28$^{\rm m}$38.89s / +26$^\circ$51$''$33.9$''$ / 4.4 / 380 / |
| Arc-like structure length | ~2000 | not stated | AU | 0 | The length of the arc-like structure is $\sim$2000 AU |

## Qualitative findings

- No SiO (6-5) emission detected, consistent with a very young source without strong shocks  
  > "We note that no SiO ($J$ = 6–5) emission was detected" (3.2 Very Compact Outflow)

## Claim tuples

- H: Are there starless high-density cores near the Spitzer source? | E: Band 6 dust continuum plus H13CO+ mass and density estimates | R: MMS-2 density ~1e7 cm^-3, MMS-3 1e6-1e7 | F: Very dense starless cores, candidates for first protostellar core | **supported**
- H: Does the Spitzer source drive a very compact outflow? | E: HCO+ (3-2) velocity maps and kinematics | R: Dynamical timescale 60-210 yr | F: Very young compact bipolar outflow interacting with surrounding gas | **supported**
- H: Does the gas show dynamical interaction? | E: HCO+ channel maps | R: ~2000 AU arc-like structure at ~7 km/s | F: Initial conditions are highly dynamical, possibly turbulent fragmentation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): H13CO+ nearly optically thick (~7 K peak), so rarer species are needed  
  > "which means that the line gets almost optically thick and that we need observations in more rare species to look into the central part." (3.1 High-density Dust Cores)
- Caveat (inferred, ours): Fixed Td=10 K and beta=1 make masses and densities uncertain, and no uncertainties are given
- Caveat (inferred, ours): Arc interpretation as turbulent interaction is qualitative
- Caveat (inferred, ours): Flux filtering by the interferometer limits the interpretation of the missing systemic emission
- Caveat (inferred, ours): MMS-2 'starless' status is not independently established

## Reproducibility

- Data public (paper): Project code given in the acknowledgments; public status not explicitly stated  
  > "This Letter makes use of the following ALMA data: ADS/JAO.ALMA$\#$2011.0.00611.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Imaging parameters
- Missing: CASA version
- Missing: Calibration details
- Missing: Outflow measurement procedure
- Data volume (inferred): ~10-50 GB
- Score (inferred): 3/5, Cycle 0 data with a project code and simple analysis, but imaging and calibration details are missing.
- Rediscovery candidate: no, Imaging recipe incomplete, though the numeric results are modest and the analysis is simple.

## Links

- Companion: Takahashi et al. 2013 (cite: Takahashi2013) (12CO(2-1) compact outflow toward the same source)

## Checks

```json
{
 "quotes": 54,
 "quotes_ok": 54,
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
  "facts": 66,
  "stated": 34,
  "rate": 0.515
 },
 "evidence_ok": true
}
```
