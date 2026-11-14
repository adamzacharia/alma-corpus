# ALMA hints at the existence of an unseen reservoir of diffuse molecular gas in the Galactic bulge

`2017A&A...600A..48G` | Astronomy and Astrophysics 2017 | first author: Gerin, M. | arXiv: 1702.03331 | DOI: 10.1051/0004-6361/201730400

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, astrochemistry
- Question: Why is mm-wave molecular absorption seen at -200 to -140 km/s toward B1741-312, away from bulge regions with prominent CO emission, and does it trace an unseen reservoir of molecular gas in the bulge?  
  > "We aim to understand the unexpected presence of mm-wave molecular absorption at -200 km s [−][1] < v < −140 km s [−][1] in a" (abstract)
- Target **B1741-312**: coordinates l = -2.1366 deg, b = -0.9968 deg  
  > "The blazar background source B1741-312 at l = −2.1366 [o], b = −0.9968 [o] was observed in nine spectral line windows" (2.1 ALMA absorption measurements); z/distance Galactic bulge gas placed at R_gal 320-1500 pc; R0 = 8.5 kpc  
  > "The blazar background source B1741-312 at l = −2.1366 [o], b = −0.9968 [o] was observed in nine spectral line windows" (2.1 ALMA absorption measurements); distance from kinematic placement with flat rotation curve and non-circular bar velocity field (Burton & Liszt 1978)  
  > "The blazar background source B1741-312 at l = −2.1366 [o], b = −0.9968 [o] was observed in nine spectral line windows" (2.1 ALMA absorption measurements)

## Data provenance

- ALMA projects: 2013.1.01194.S
- bands: near 89 GHz (Cycle 2)  
  > "We observed HCO [+], HCN, and HNC in absorption near 89 GHz in ALMA Cycle 2 project 2013.1.01194.S" (2.1 ALMA absorption measurements)
- frequencies and spectral setup: nine spectral line windows; HCN, HCO+, HNC J=1-0 at 88.631, 89.188, 90.663 GHz; 244 kHz channels (~0.8 km/s), resolution twice as coarse  
  > "The channel spacing of the ALMA data presented here is 244 kHz, or approximately 0.8 km s [−][1], and the resolution is twice as high." (2.1 ALMA absorption measurements)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: channel-channel rms optical depth 0.0062  
  > "channel-channel rms optical depth fluctuations of 0.0062 at zero optical depth" (2.1 ALMA absorption measurements)
- time on source: 720 s  
  > "the source was observed for 720s, leading to channel-channel rms optical depth fluctuations of 0.0062 at zero optical depth" (2.1 ALMA absorption measurements)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: HCN J=1-0 (88.631 GHz)
- Line: HCO+ J=1-0 (89.188 GHz)
- Line: HNC J=1-0 (90.663 GHz)
- Other facility **Southern Mini-Telescope CO survey**: CO J=1-0 emission profiles and maps, 8' resolution  
  > "We present CO J=1-0 emission profiles from the Southern MiniTelescope CO survey of Bitran et al. (1997) at 8 [′] spatial resolution on a 1/8 [o] grid" (2.2 Other data: H I and CO emission)
- Other facility **SGPS**: H I emission, 145'' resolution  
  > "H I emission from the Southern Galactic Plane Survey (SGPS) survey data of McClure-Griffiths et al. (2005) at 145 [′′] spatial resolution" (2.2 Other data: H I and CO emission)
- External data: H I absorption line profile used with SGPS emission to derive N(HI)  
  > "which we used in conjunction with the H I absorption line profile of Dickey et al. (1983)" (2.2 Other data: H I and CO emission) [from Dickey et al. (1983)]
- External data: 3D IR extinction map E(J-K) along line of sight, 6' resolution  
  > "We also use data at 6 [′] resolution from the 3D IR extinction map of the bulge of Schultheis et al. (2014)" (2.3 Extinction) [from Schultheis et al. (2014)]
- External data: E(B-V)=6.3 mag dust reddening toward B1741  
  > "E B−V = 6.3 mag (Schlafly & Finkbeiner, 2011)" (3.6 Another estimate of the total atomic gas deficit) [from Schlafly & Finkbeiner (2011)]

## Processing

### Calibration

- pipeline or manual: standard ALMA pipeline, run January and February 2016 after delivery  
  > "The spectra were reduced using the standard ALMA pipeline in January and February 2016 after the data had been delivered." (2.1 ALMA absorption measurements)
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
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Non-circular bar velocity field inside R_gal=1.5 kpc  
  > "using approximately equal circular and radial motions 170-180 km s [−][1] to explain the geometry and gas motions in the inner galaxy" (3.1 Placement of kinematic features) [from Burton & Liszt (1978)]
- H I/H2 transition analytical framework  
  > "Using the analytical framework for the H I/H 2 transition developed by Sternberg et al. (2014) and Bialy & Sternberg (2016)" (3.4 High H2-fractions in the bulge gas) [from Sternberg et al. (2014); Bialy & Sternberg (2016)]
- N(HCO+)/N(H2)=3e-9 local abundance  
  > "with N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9], the local value for solar metallicity as a benchmark for H 2" (3.2 Derived results) [from local value (no citation given)]

### Not stated but needed to reproduce (our reading)

- Pipeline/CASA version and calibrators
- Imaging parameters (weighting, cell, beam) of the cubes
- Continuum normalization and baseline fitting for optical depth
- Velocity ranges and integration details beyond Table 1
- Excitation/hyperfine treatment for HCN
- Derivation details of n_100 I_UV values
- Exact procedure for inverting E(J-K) vs distance modulus

## Analysis recipe

1. **Extract ALMA absorption spectra**: Spectra extracted from pipeline cubes at the pixel of peak continuum flux  
  > "Spectra were extracted from the final data cubes at the pixel of peak continuum flux." (2.1 ALMA absorption measurements)
   - software: ALMA pipeline
   - fitting: _not stated_
   - validation: _not stated_
2. **Place gas kinematically in disk/bulge**: Compare LSR velocities with flat rotation curve and non-circular bar field  
  > "for pure circular motion with a flat rotation curve with R 0 = 8.5 kpc, Θ = 220 km s [−][1]" (3.1 Placement of kinematic features)
   - assumption: R0 = 8.5 kpc, Theta = 220 km/s  
  > "flat rotation curve with R 0 = 8.5 kpc, Θ = 220 km s [−][1]" (3.1 Placement of kinematic features)
   - fitting: _not stated_
   - validation: _not stated_
3. **Derive N(HI), N(HCO+), N(H2)**: Optical-depth corrected N(HI) from emission+absorption; N(H2) from HCO+ with fixed abundance; Tex=2.729 K  
  > "column densities (units of cm [−][2] ) calculated using Eq. 1 for H I, T ex = 2.729 K for HCO [+]" (3.2 Derived results)
   - assumption: N(HCO+)/N(H2)=3e-9  
  > "with N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9], the local value for solar metallicity" (3.2 Derived results)
   - fitting: _not stated_
   - validation: Implied X_CO compared with canonical 2e20  
  > "the assumed HCO [+] abundance yields a canonical value 2×10 [20] H 2 cm [−][2] (K-km s [−][1] ) [−][1] for the CO-H 2 conversion factor" (3.2 Derived results)
4. **Compare gas N(H) with extinction-derived N(H)**: N(H)=1.171e22 E(J-K) from 3D extinction cube versus N(HI)+2N(H2), cumulative with R_gal  
  > "N(H) = 1.171 × 10 [22] cm [−][2] E(J-K), where N(H) is the total column density of H-nuclei in atomic and molecular form" (2.3 Extinction)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **ALMA pipeline** : data reduction  
  > "The spectra were reduced using the standard ALMA pipeline" (2.1 ALMA absorption measurements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum flux of B1741-312 | 0.59 | not stated | Jy | 1 | The continuum flux was 0.59 Jy |
| N(H2) at -164 to -135 km/s | 1.21e21 | not stated | cm^-2 | 3 | N(H 2 ) [ cm [−][2] ] 2.86 × 10 [20] 1.21 × 10 [21] |
| N(HI) at -196 to -180 km/s | 1.51e20 | 0.06e20 | cm^-2 | 3 | 1.51(0.06) × 10 [20] 6.13(0.71) × 10 [19] |
| H2 fraction of -190 and -150 km/s components | ~0.8 and ~0.95 | not stated | dimensionless | 4 | ∼ 0.8 and ∼ 0.95 for the -190 and -150 km s [−][1] velocity components, respectively |
| n100*I_UV for the two bulge clouds | ~0.5 and ~0.2 | not stated | dimensionless | 4 | We find n [I] [UV] 100 [∼] [0][.][5] |
| N(H) from E(B-V) | 5.0e22 | not stated | H-nuclei cm^-2 | 4 | N(H) = 6.3 × 8 × 10 [21] = 5.0 × 10 [22] H-nuclei cm [−][2] |

## Qualitative findings

- Bulge gas at R_gal<1.5 kpc has HI contributing under 10% of the E(J-K)-inferred material; molecular absorption is needed to explain the extinction.  
  > "Within the Galactic bulge at R gal < 1.5 kpc, H I contributes less than 10% of the material inferred from E(J-K)" (abstract)

## Claim tuples

- H: Does the bulge molecular absorption represent gas needed to account for the extinction? | E: Compare N(H) from HI plus HCO+-derived H2 with N(H) from E(J-K) vs R_gal | R: HI accounts for only a small portion of the column inside R_gal<1.5 kpc; HCO+ absorption can fill the gap | F: Unseen diffuse molecular gas exists in the bulge, poorly traced by CO | **supported**
- H: Is the bulge gas weakly irradiated? | E: Apply the HI/H2 transition theory | R: n100*I_UV ~0.5 and ~0.2 | F: Low FUV field; H2 is mainly self-shielded | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Gas along -190 to -150 km/s cannot be precisely located along the line of sight; metallicity variations affect results.  
  > "cannot be precisely located along the line of sight owing to imprecise knowledge of the bar-like inner-galaxy velocity field" (4 Summary)
- Caveat (inferred, ours): Single sightline
- Caveat (inferred, ours): Constant HCO+ abundance and gas-to-reddening ratio assumed in bulge
- Caveat (inferred, ours): No uncertainties on N(H2) or extinction N(H)
- Caveat (inferred, ours): Distance placement is model dependent

## Reproducibility

- Data public (paper): Archive data cited via ADS/JAO.ALMA#2013.1.01194.S  
  > "ADS/JAO.ALMA#2013.1.01194.S" (Acknowledgements)
- Products in archive: _not stated_
- Missing: Reduction details and imaging parameters
- Missing: Extracted spectra
- Missing: Extinction-cube inversion procedure
- Data volume (inferred): a few GB for a short 720 s single-source observation, plus survey data
- Score (inferred): 3/5, Public ALMA data and simple analysis, but many procedural details missing.
- Rediscovery candidate: no, Key steps (extinction inversion, kinematic placement, line windows) are insufficiently specified.

## Links

- Method: Bialy & Sternberg (2016); Sternberg et al. (2014) (HI/H2 transition theory)
- Companion: forthcoming paper on HOC+, CF+, C3H+, c-C3H (Other species from same ALMA project)
- Related: Southern Mini-Telescope CO survey
- Related: SGPS
- Related: Schultheis et al. 2014 3D extinction map

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
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
  "facts": 68,
  "stated": 28,
  "rate": 0.412
 },
 "evidence_ok": true
}
```
