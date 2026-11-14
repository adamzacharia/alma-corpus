# A Multiline Study of a High-mass Young Stellar Object in the Small Magellanic Cloud with ALMA: The Detection of Methanol Gas at 0.2 Solar Metallicity

`2018ApJ...862..102S` | The Astrophysical Journal 2018 | first author: Shimonishi, Takashi | arXiv: 1806.07120 | DOI: 10.3847/1538-4357/aacd0c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What are the physical and chemical properties of dense cores around a high-mass YSO in the SMC, and is CH3OH gas present at 0.2 solar metallicity?  
  > "The first detection of CH$_3$OH in the SMC has a strong impact on our understanding of the formation of complex organic molecules in metal-poor environments." (abstract)
- Target **IRAS 01042-7215 (SMC high-mass YSO)**: coordinates RA 01h05m49.32s, Dec -71d59m48.4s (J2000)  
  > "The telescopes were pointed to RA = 01$^\mathrm{h}$05$^\mathrm{m}$49$s$32 and Dec = -71$^\circ$59$\ensuremath{'}$48$\ensuremath{''}$4 (J2000)" (2.2 Observations); "which corresponds to 0.11 pc $\times$ 0.07 pc at the distance of the SMC (62.1 kpc)" (2.3 Data reduction); z/distance 62.1 kpc  
  > "The telescopes were pointed to RA = 01$^\mathrm{h}$05$^\mathrm{m}$49$s$32 and Dec = -71$^\circ$59$\ensuremath{'}$48$\ensuremath{''}$4 (J2000)" (2.2 Observations); "which corresponds to 0.11 pc $\times$ 0.07 pc at the distance of the SMC (62.1 kpc)" (2.3 Data reduction); distance from assumed SMC distance (Graczyk et al. 2014 is cited for the SMC generally; the paper does not tie the 62.1 kpc value to it)  
  > "The telescopes were pointed to RA = 01$^\mathrm{h}$05$^\mathrm{m}$49$s$32 and Dec = -71$^\circ$59$\ensuremath{'}$48$\ensuremath{''}$4 (J2000)" (2.2 Observations); "which corresponds to 0.11 pc $\times$ 0.07 pc at the distance of the SMC (62.1 kpc)" (2.3 Data reduction)

## Data provenance

- ALMA projects: 2016.1.00394.S
- bands: Band 6  
  > "The target was observed in Band 6 with four spectral windows" (2.2 Observations)
- frequencies and spectral setup: 4 spectral windows: 241.48–243.36, 243.84–245.71, 256.99–258.87, 258.85–260.72 GHz; 977 kHz resolution before averaging  
  > "covering 241.48–243.36, 243.84-245.71, 256.99–258.87, and 258.85–260.72 GHz in the rest-frame frequency. The frequency resolution is 977 kHz before channel averaging." (2.2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 19 m to 1.1 km, 43 antennas  
  > "In total 43 antennas are used for the observations with the minimum and maximum baseline length of 19 m and 1.1 km." (2.2 Observations)
- angular resolution: 0.35–0.37″ × 0.22–0.23″, PA -25 deg  
  > "The synthesized beam size is 0.35–0.37$\ensuremath{''}$ $\times$ 0.22–0.23$\ensuremath{''}$ with a position angle of -25 degree" (2.3 Data reduction)
- max recoverable scale: about 3″  
  > "the maximum recoverable angular scale is about 3$\ensuremath{''}$" (2.3 Data reduction)
- sensitivity: _not stated_
- time on source: 39 minutes  
  > "The total on-source integration time is 39 minutes." (2.2 Observations)
- observing dates: November 2016  
  > "Observations were carried out with ALMA in November 2016" (2.2 Observations)
- pi or archival as stated: Cycle 4 program, PI T. Shimonishi  
  > "Cycle 4 program 2016.1.00394.S (PI T. Shimonishi)" (2.2 Observations)
- Line: CS 5–4 (244.93556 GHz)
- Line: SO 6_6–5_5 (258.25583 GHz)
- Line: CH3OH 5_0–4_0 A+ (241.79143 GHz)
- Line: H13CO+ 3–2 (260.25533 GHz)
- Line: HDS (tentative) 1_0,1–0_0,0 (244.55558 GHz)
- Other facility **Gemini South T-ReCS**: mid-infrared N-band imaging  
  > "high spatial resolution mid-infrared imaging data obtained with T-ReCS at the Gemini South telescope" (2.4 Complementary infrared data)
- Other facility **AKARI IRC**: 2–5 micron spectrum for ice absorption  
  > "a near-infrared 2–5 $\mu$m spectrum obtained with the Infrared Camera (IRC) on board *AKARI*" (2.4 Complementary infrared data)
- External data: Dust mass absorption coefficient for grains with thin ice mantles  
  > "is the mass absorption coefficient of dust grains coated by thin ice mantles as taken from (cite: Oss94)" (3.3.2) [from (cite: Oss94)]
- External data: 32S/33S = 40 from 33SO2 in an LMC hot core  
  > "We here assume $^{32}$S/$^{33}$S = 40, based on the $^{33}$SO$_2$ observations towards a hot core in the LMC (cite: ST16b)." (3.3.3) [from (cite: ST16b)]
- External data: 12C/13C = 50 from SMC N27  
  > "We here assume $^{12}$C/$^{13}$C = 50 according to HCO$^+$/H$^{13}$CO$^+$ observations of the N27 region in the SMC (cite: Hei99)." (3.3.3) [from (cite: Hei99)]
- External data: NH/E(B-V) = 4.6e22 cm-2 mag-1 for SMC  
  > "(cite: Mar89) reported $N_{\mathrm{H}}$/$E(B-V)$ = 4.6 $\times$ 10$^{22}$ cm$^{-2}$ mag$^{-1}$ for the SMC." (3.3.2) [from (cite: Mar89)]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: calibration with CASA 4.7.0  
  > "The calibration is done with CASA 4.7.0 and the imaging is with CASA 4.7.2." (2.3 Data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J2357-5311 (flux), J2056-4714 (bandpass), J0102-7546 (gain)  
  > "We use J2357-5311, J2056-4714, and J0102-7546 as a flux, bandpass, and gain calibrator, respectively." (2.2 Observations)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA 4.7.2 imaging  
  > "The calibration is done with CASA 4.7.0 and the imaging is with CASA 4.7.2." (2.3 Data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in CASA  
  > "The continuum emission is subtracted from the spectral data using the uvcontsub task in CASA." (2.3 Data reduction)
- line free channels: _not stated_
- primary beam correction: impbcor in CASA  
  > "The primary beam correction is done by using the impbcor task in CASA." (2.3 Data reduction)
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.35–0.37″ × 0.22–0.23″, PA -25 deg  
  > "The synthesized beam size is 0.35–0.37$\ensuremath{''}$ $\times$ 0.22–0.23$\ensuremath{''}$ with a position angle of -25 degree" (2.3 Data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Optically thin dust emission treatment for N(H2)  
  > "based on the standard treatment of optically thin dust emission (cite: ST16b)" (3.3.2) [from (cite: ST16b)]
- Standard rotation diagram formulae  
  > "We use the following formulae based on the standard treatment of the rotation diagram analysis (cite: Sut95; Gol99)" (3.3.1) [from (cite: Sut95; Gol99)]
- Ice column density derivation from AKARI spectrum  
  > "ice column densities are estimated to be $N$(H$_2$O ice) = (17 $\pm$ 5) $\times$ 10$^{17}$ cm$^{-2}$" (4.2) [from (cite: ST16)]

### Not stated but needed to reproduce (our reading)

- CLEAN/tclean parameters: weighting, robust, deconvolver, threshold, masks, cell and image size
- Line-free channels used for uvcontsub and the continuum bandwidth
- Whether the CASA pipeline or manual scripts were used, and flux calibrator flux values
- Velocity ranges for moment maps and polynomial order of baseline fits
- Rest frequency/velocity reference for channel maps and how rotation diagram uncertainties were derived (fitting method)
- Method and parameters used for the ice column density and SED integration
- Continuum frequency/bandwidth used for the 1200 micron photometry

## Analysis recipe

1. **Extract spectra and continuum at three positions**: Spectra and continuum flux extracted from 0.34″ diameter regions at P1, P2, P3 after uvcontsub  
  > "The spectra and continuum flux are extracted from the 0.34$\ensuremath{''}$ (0.10 pc) diameter region centered at the three positions" (2.3 Data reduction)
   - software: CASA
   - parameter: velocity resolution 1.5 km/s  
  > "The velocity resolution of the extracted spectra is 1.5 km s$^{-1}$." (2.3 Data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Measure line parameters**: Single Gaussian fits with optional polynomial local baseline; direct integration for two narrow CH3OH lines; 3 sigma detection criterion  
  > "Line parameters are measured by fitting a single Gaussian profile to observed lines." (3.1 Spectra); "The detection criteria adopted here are the 3$\sigma$ significance level" (3.1 Spectra)
   - fitting: _not stated_
   - validation: Velocity coincidence with systemic velocity of nearby clouds  
  > "the velocity coincidence with the systemic velocity of nearby clouds (cite: Isr93)" (3.1 Spectra)
3. **CH3OH rotation diagram**: Rotation diagram under optically thin LTE, straight-line fit, spectroscopy from CDMS  
  > "An optically thin condition and the local thermodynamic equilibrium (LTE) are assumed here." (3.3.1)
   - parameter: Blended 241.90416 GHz line intensity divided by two  
  > "the measured intensity of the CH$_3$OH line at 241.90416 GHz is divided by two" (3.3.1)
   - assumption: Optically thin, LTE  
  > "An optically thin condition and the local thermodynamic equilibrium (LTE) are assumed here." (3.3.1)
   - fitting: Straight-line fit in the rotation diagram; marginal detections and upper limits included  
  > "the data points for two marginal CH$_3$OH detections (5$_{0}$–4$_{0}$ E and 5$_{\pm2}$–4$_{\pm2}$ E, $Eu$ = 48 K and 61 K) are included in the straight-line fit for P2." (3.3.1)
   - validation: Compared fits excluding marginal detections/upper limits; these gave higher T and were incompatible with upper limits  
  > "However, these fits are incompatible with upper limits, and the fitted line deviates upward from the points." (3.3.1)
4. **H2 column density and mass from dust continuum**: Optically thin dust emission with Ossenkopf & Henning opacity, dust-to-gas ratio 1/5 of 0.008  
  > "We assume that the dust-to-gas mass ratio in the SMC is lower than the typical Galactic value of 0.008 by a factor of five according to the metallicity." (3.3.2)
   - parameter: Td 12 K (P2), 13 K (P3), 10–20 K (P1)  
  > "The dust temperature at P2 and P3 is assumed to be 12 K and 13 K according to the rotation temperatures of CH$_3$OH" (3.3.2)
   - assumption: Dust temperature equals CH3OH rotation temperature at P2/P3  
  > "The dust temperature at P2 and P3 is assumed to be 12 K and 13 K according to the rotation temperatures of CH$_3$OH" (3.3.2)
   - fitting: _not stated_
   - validation: AV estimates compared with Ward et al. 2017 value of 16±8 mag  
  > "(cite: War17) estimate $A_{V}$ = 16 $\pm$ 8 mag for the YSO at P1" (3.3.2)
5. **Column densities and abundances of other molecules**: Solve rotation-diagram equation for N at assumed T; isotopologues for optically thick lines  
  > "Column densities of molecular species other than CH$_3$OH and H$_2$ are estimated by solving Equation [\[Eq_rd2\]](#Eq_rd2) for $N$." (3.3.3)
   - assumption: 32S/33S = 40; 12C/13C = 50  
  > "We here assume $^{32}$S/$^{33}$S = 40" (3.3.3)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **CASA** 4.7.0 (calibration), 4.7.2 (imaging): calibration, imaging, impbcor, uvcontsub  
  > "The calibration is done with CASA 4.7.0 and the imaging is with CASA 4.7.2." (2.3 Data reduction)
- **CDMS** : line identification and spectroscopic parameters  
  > "Spectral lines are identified with the aid of the Cologne Database for Molecular Spectroscopy" (3.1 Spectra)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| CH3OH N at P2 | 3.0e14 | +5.1/-1.9 e14 (2σ) | cm-2 | 3 | $N$ = (3.0 $^{+5.1}_{-1.9}$) $\times$ 10$^{14}$ cm$^{-2}$ and $T_{\mathrm{rot}}$ = 12.3 $^{+5.3}_{-2.9}$ K for Position 2 |
| CH3OH Trot at P2 | 12.3 | +5.3/-2.9 (2σ) | K | 3 | $T_{\mathrm{rot}}$ = 12.3 $^{+5.3}_{-2.9}$ K for Position 2 |
| CH3OH N at P3 | 3.2e14 | +4.5/-1.9 e14 (2σ) | cm-2 | 3 | $N$ = (3.2 $^{+4.5}_{-1.9}$) $\times$ 10$^{14}$ cm$^{-2}$ and $T_{\mathrm{rot}}$ = 13.1 $^{+4.9}_{-2.8}$ K for Position 3 |
| CH3OH Trot at P3 | 13.1 | +4.9/-2.8 (2σ) | K | 3 | $T_{\mathrm{rot}}$ = 13.1 $^{+4.9}_{-2.8}$ K for Position 3 |
| CH3OH fractional abundance P2 | 4.7e-9 | +8.0/-3.0 e-9 | dimensionless | 5 | (4.7 $^{+8.0}_{-3.0}$) $\times$ 10$^{-9}$ at P2 |
| CH3OH fractional abundance P3 | 1.5e-8 | +2.2/-0.9 e-8 | dimensionless | 5 | 1.5$^{+2.2}_{-0.9}$ $\times$ 10$^{-8}$ at P3 |
| N(H2) at P2 | 6.3e22 | not stated | cm-2 | 4 | 6.3 $\times$ 10$^{22}$ |
| Continuum brightness P1, P2, P3 | 0.30, 0.16, 0.06 | not stated | mJy/beam | 1 | The measured continuum brightnesses are 0.30 mJy/beam for P1, 0.16 mJy/beam for P2, and 0.06 mJy/beam for P3. |
| Gas mass YSO core / East core | ~80 / ~50 | not stated | Msun | 4 | about 80 M$_{\ensuremath{\odot}}$ for the YSO core and about 50 M$_{\ensuremath{\odot}}$ for the East core |
| YSO bolometric luminosity | 2e4 | not stated | Lsun | 0 | The bolometric luminosity of the YSO is estimated to be 2 $\times$ 10$^4$ L$_{\ensuremath{\odot}}$ by integrating the SED from 1 $\mu$m to 1200 $\mu$m. |
| N(HDS) at P2 (tentative) | 5e13 | 1.3e13 | cm-2 | 5 | $N$(HDS) = (5 $\pm$ 1.3) $\times$ 10$^{13}$ cm$^{-2}$ |

## Qualitative findings

- CH3OH, SO2, H2CS, C33S and H13CN detected for the first time in the SMC  
  > "CH$_3$OH, SO$_2$, H$_2$CS, C$^{33}$S, and H$^{13}$CN are for the first time detected in the SMC." (3.1 Spectra)

## Claim tuples

- H: Is CH3OH gas present in a low-metallicity SMC dense core, and at what temperature? | E: Band 6 ALMA lines with CH3OH rotation diagram | R: Multiple CH3OH lines detected at P2, P3 with Trot ~12–13 K | F: CH3OH gas detected in SMC; cold gas ~10 K | **supported**
- H: Is CH3OH gas abundance reduced at 0.2 solar metallicity? | E: Compare East core abundances with Galactic cold sources | R: (0.5–1.5)e-8, comparable or marginally higher | F: No metallicity-scaled depletion of CH3OH in East core | **supported**
- H: Are the YSO core and East core chemically distinct? | E: Compare abundances at P1, P2, P3 | R: CS, H2CS, SiO underabundant at P1; P2 and P3 correlated (r=0.89) | F: Chemical differentiation between the cores | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Warm gas components (>=50 K) cannot be ruled out given limited frequency coverage  
  > "the presence of warm gas components ($\gtrsim$50 K) within the core can not be ruled out from the limited frequency coverage of the present observations." (3.3.1)
- Limitation (authors): Abundances carry systematic uncertainty from assumed dust temperature  
  > "derived molecular abundances entail the systematic uncertainty depending on the assumption of dust temperatures" (3.3.2)
- Caveat (inferred, ours): Dust temperature set equal to CH3OH Trot; abundance depends strongly on it
- Caveat (inferred, ours): Rotation diagram with few lines, marginal detections and large uncertainties
- Caveat (inferred, ours): Single source, so generality to SMC is unclear
- Caveat (inferred, ours): LTE and optically thin assumptions untested

## Reproducibility

- Data public (paper): Project code given; archive data  
  > "ADS/JAO.ALMA$\#$2016.1.00394.S" (Acknowledgments)
- Products in archive: _not stated_
- Missing: tclean parameters and masks
- Missing: line-free channels for continuum subtraction
- Missing: fitting method for rotation diagram uncertainties
- Missing: ice column density method details
- Data volume (inferred): ~5–20 GB raw for one Band 6 execution block set
- Score (inferred): 3/5, Public data and clear analysis equations, but imaging parameters and fitting details are missing.
- Rediscovery candidate: yes, Public archive data, simple analysis (Gaussian fits, rotation diagram) with numeric results.

## Links

- Method: (cite: ST16b) (Dust-continuum N(H2) treatment and isotope ratio)
- Method: (cite: Sut95; Gol99) (Rotation diagram formalism)
- Companion: (cite: Oli13) (Previous infrared study of the YSO)
- Companion: (cite: War17) (Near-infrared study of the source)
- Related: AKARI IRC
- Related: Gemini T-ReCS

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 78,
  "stated": 48,
  "rate": 0.615
 },
 "evidence_ok": true
}
```
