# Substructures in the Keplerian disc around the O-type (proto-)star G17.64+0.16

`2019A&A...627L...6M` | Astronomy and Astrophysics 2019 | first author: Maud, L. T. | arXiv: 1906.06548 | DOI: 10.1051/0004-6361/201935633

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, protoplanetary_disks
- Question: Does the disc around the O-type (proto)star G17.64+0.16 show substructure, Keplerian rotation, and gravitational stability when resolved at ~20 mas (~40 au)?  
  > "we now fully resolve the dust and molecular line emission and for the first time uncover clear enhanced substructures in the disc around this massive forming O-star." (Introduction)
- Target **G17.64+0.16 (AFGL 2136)**: coordinates J2000 18h22m26.3862s -13d30m11.9717s (peak emission)  
  > "Located at 2.2 kpc and with a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$[^3] (cite: Lumsden2013)" (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.3862$^{\rm s}$ $-$13$^{\circ}$30$'$11.9717$''$" (2 Observations); z/distance 2.2 kpc  
  > "Located at 2.2 kpc and with a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$[^3] (cite: Lumsden2013)" (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.3862$^{\rm s}$ $-$13$^{\circ}$30$'$11.9717$''$" (2 Observations); distance from Lumsden2013 (RMS survey)  
  > "Located at 2.2 kpc and with a bolometric luminosity of 1$\times$10$^5$ L$_{\odot}$[^3] (cite: Lumsden2013)" (Introduction); "J2000 18$^{\rm h}$22$^{\rm m}$26.3862$^{\rm s}$ $-$13$^{\circ}$30$'$11.9717$''$" (2 Observations)

## Data provenance

- ALMA projects: 2017.1.00098.S
- bands: Band 6  
  > "observations of G17.64 using the ALMA long-baselines at Band 6" (Introduction)
- frequencies and spectral setup: 4 SPWs of 1.875 GHz: 216.746-218.621, 218.854-220.746, 230.938-232.812, 233.048-234.94 GHz; ~1.3 km/s resolution (0.8 km/s for SiO)  
  > "SPW0: 216.746-218.621 GHz, SPW1: 218.854-220.746 GHz, SPW2: 230.938-232.812 GHz, SPW3: 233.048-234.94 GHz." (Other Lines); "all four spectral-windows (SPWs) were configured with the widest bandwidth of 1.875 GHz" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-10, 43 antennas, one execution block  
  > "in configuration C43-10, with 43 antennas" (2 Observations)
- baselines: _not stated_
- angular resolution: 20x15 mas (44x33 au), PA -88.4 deg, continuum robust 0.0  
  > "The maximal angular resolution of 20$\times$15 mas at a position-angle (PA) of -88.4$^{\circ}$ in the continuum was achieved using a robust parameter of 0.0" (2 Observations)
- max recoverable scale: at least 0.64 arcsec  
  > "we note our maximal recoverable scale is at least 0.64$''$, much larger than the dust disc." (3.1 Continuum emission)
- sensitivity: continuum 40.4 uJy/beam; H2O 0.76 mJy/beam/channel  
  > "The final continuum noise level achieved was 40.4 $\mu$Jy beam$^{-1}$." (2 Observations)
- time on source: 30.6 minutes  
  > "The on-source time was 30.6 minutes." (2 Observations)
- observing dates: 4 October 2017 (Cycle 5)  
  > "conducted during Cycle 5 on 4 October 2017" (2 Observations)
- pi or archival as stated: _not stated_
- Line: H2O 5(5,0)-6(4,3) v2=1 (232.68670 GHz)
- Line: SiO 5-4 (not stated)
- Line: H30alpha radio recombination line (not stated)
- External data: Radio-to-mm free-free extrapolation: 3.57 to 29.5 mJy at mm wavelengths  
  > "we reported that the radio wavelength emission accounts for between 3.57 mJy and 29.5 mJy when extrapolated to the mm regime." (3.1 Continuum emission) [from Maud2018]
- External data: Point-source size 29 mas at 43 GHz  
  > "A point source assumption is consistent with the size (29 mas at 43 GHz) found by (cite: Menten2004)" (3.1 Continuum emission) [from Menten2004]
- External data: Dust opacity kappa = 1.0 cm2/g at 1.3 mm  
  > "we use $\kappa_\nu$ = 1.0 cm$^2$ g$^{-1}$ as suggested for dust with thin ice mantles" (Disc Mass) [from Ossenkopf1994]
- External data: Stellar parameters of a 45 Msun O star (R0~9.3 Rsun, L~1.9e5 Lsun, T~60000 K)  
  > "temperature of a 45 M$_{\odot}$ main-sequence O-star from (cite: Hosokawa2009)" (4.2 Disc stability) [from Hosokawa2009]

## Processing

### Calibration

- pipeline or manual: CASA pipeline for calibration  
  > "Data calibration used the casa pipeline, version 5.1.1" (2 Observations)
- casa version: 5.1.1 calibration; 5.4.0 imaging and self-cal  
  > "while subsequent imaging and self-calibration used version 5.4.0" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: down to 6 s phase, 54 s amplitude; dynamic range 405 to 640  
  > "Self-calibration was possible down to a solution time of 6 s in phase and 54 s for amplitude, improving the dynamic range from 405 to 640." (2 Observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: continuum and H30a robust 0.0; H2O robust 1.5; SiO robust 1.5  
  > "For the H$_2$O images a robust value of 1.5 was used to boost surface brightness sensitivity." (2 Observations)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: in the uv domain  
  > "continuum subtraction was undertaken in the *u*,v domain" (2 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: continuum 20x15 mas; H2O 28x23 mas PA 65.8; SiO 30x24 mas; H30a 20x18 mas  
  > "The resulting resolution was 28$\times$23 mas at a PA of 65.8$^{\circ}$" (2 Observations)
- final rms: 40.4 uJy/beam continuum  
  > "The final continuum noise level achieved was 40.4 $\mu$Jy beam$^{-1}$." (2 Observations)

### Inherited from earlier work

- Spectral setup covers the frequency range of earlier observations  
  > "The spectral setup covered the frequency range of our previous observations (cite: Cesaroni2017)." (2 Observations) [from Cesaroni2017]
- Disc-only PV model and by-eye fitting of contour levels  
  > "Following (cite: Maud2018), fitting is made by-eye matching equivalent contour levels (cite: Ilee2018)." (4.1 Stellar mass) [from Maud2018; Ilee2018]
- Toomre Q methodology  
  > "We follow the methods outlined in (cite: Beuther2017a) and (cite: Ahmadi2018)." (4.2 Disc stability) [from Beuther2017a; Ahmadi2018]
- Disc mass via optically thin formula  
  > "following (cite: Hildebrand1983)" (3.1 Continuum emission) [from Hildebrand1983]

### Not stated but needed to reproduce (our reading)

- CLEAN threshold, masks, cell and image sizes, deconvolver
- Line-free channels used for continuum subtraction
- Exact point-source flux subtracted in the visibility domain for the min/max free-free cases
- Model parameters of the PV disc model (velocity/density laws, line width) and code
- Column density map details and conversion to Sigma
- Flux calibrator and flux-scale uncertainty

## Analysis recipe

1. **Image continuum and measure disc size, inclination**: Fit ellipse to the 50 sigma contour; inclination from axis ratio assuming a circular thin disc  
  > "Fitting an ellipse to the 50$\sigma$ contour level ($\sim$2.0 mJy beam$^{-1}$) we find that the disc measures 93$\times$71 mas." (3.1 Continuum emission)
   - software: least-squares ellipse fitting (Hammel)
   - assumption: Circular thin disc with settled mm grains  
  > "Assuming a circular thin-disc where the mm-sized dust grains have settled to the mid-plane" (3.1 Continuum emission)
   - fitting: _not stated_
   - validation: Uncertainty from fitting at 30 and 70 sigma contours  
  > "The uncertainty propagates from fitting the disc size at the 30$\sigma$ and 70$\sigma$ contours" (3.1 Continuum emission)
2. **Subtract free-free point source and estimate disc mass**: Point-source subtraction in visibilities at the upper-limit free-free flux; optically thin mass with Hildebrand formula, Td = 50, 100, 150 K  
  > "resulting lower limit optically thin disc mass ranges from 0.6 to 2.6 M$_{\odot}$ following (cite: Hildebrand1983)" (3.1 Continuum emission)
   - software: CASA
   - assumption: gas-to-dust 100, kappa=1.0 cm2/g at 1.3 mm, Td 50-150 K, d=2.2 kpc  
  > "g is the gas-to-dust ratio = 100" (Disc Mass)
   - fitting: _not stated_
   - validation: Imaging done with and without phase-centre shift to rule out sidelobe artefacts  
  > "no notable differences were seen in any of our images." (2 Observations)
3. **H2O moment maps and PV diagram**: Moment 0/1 maps; PV cut at PA 25.9 deg, 5 pixel width, PA from Gaussian centres of blue and red moment-0 maps  
  > "The cut for the PV diagram was taken at a position angle of 25.9$^{\circ}$ using a width of 5 pixels" (3.2 H2O)
   - fitting: _not stated_
   - validation: _not stated_
4. **Estimate central stellar mass**: Disc-only Keplerian PV model matched by eye to contours, outer radius 120 au, inclination 40 deg, inner radius 25-30 au  
  > "fix the disc outer radius to 120 au as per the dust and H$_2$O maps and also revise the inclination angle to 40$\pm$5$^{\circ}$" (4.1 Stellar mass)
   - fitting: by-eye matching of contour levels  
  > "fitting is made by-eye matching equivalent contour levels" (4.1 Stellar mass)
   - validation: _not stated_
5. **Toomre Q map**: Q = c_s kappa/(pi G Sigma); Sigma from column density times mu m_H, mu=2.3; T(R) propto R^-0.4 anchored to a 45 Msun O star  
  > "The temperature of the disc is calculated using $T(R)\propto (R/R_0)^{-0.4}$ (cite: Whitney2003)" (4.2 Disc stability)
   - assumption: Optically thin; steeper T profile or optical depth would lower Q  
  > "If we use a steeper temperature profile (cite: Brinch2010) the temperature in the disc is below 150 K" (4.2 Disc stability)
   - fitting: _not stated_
   - validation: Computed for minimal and maximal free-free removal  
  > "Toomre Q maps for G17.64 where the minimal and maximal free-free contamination is removed" (4.2 Disc stability)

## Software

- **CASA** 5.1.1 (calibration), 5.4.0 (imaging/self-cal): Calibration pipeline, imaging, self-calibration  
  > "Data calibration used the casa pipeline, version 5.1.1" (2 Observations)
- **least-squares-ellipse-fitting** : Ellipse fitting to continuum contours  
  > "This paper makes use of the least-squares fitting by (cite: HammelLS)." (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Continuum peak flux | 25.12 | not stated | mJy/beam | 1 | The peak flux is 25.12 mJy beam$^{-1}$ |
| Integrated flux (60 mas radius) | 79.14 | not stated | mJy | 1 | We recover an integrated flux of 79.14 mJy (within a 60 mas radius circle) |
| Disc inclination | 40 | 4 | deg | 1 | we estimate the disc inclination as $\sim$40$\pm$4$^{\circ}$ |
| Disc mass (optically thin, lower limit) | 0.6 to 2.6 | not stated | Msun | 2 | resulting lower limit optically thin disc mass ranges from 0.6 to 2.6 M$_{\odot}$ |
| Central stellar mass | 45 | 10 | Msun | 4 | the modelled central mass must be increased to 45$\pm$10 M$_{\odot}$ |
| Toomre Q in ring (65-97 au) | 2 to 4 | not stated | dimensionless | 5 | has the lowest Toomre Q values, between 2 and 4 |

## Qualitative findings

- Dust disc shows a ring-like enhancement at 65-97 au, possibly an underlying spiral  
  > "the continuum emission has a significant enhancement of dust emission in a ring-like, or possibly underlying spiral structure" (Conclusions)

## Claim tuples

- H: Does the disc around G17.64 have substructure? | E: Band 6 long-baseline continuum imaging at 20 mas | R: Ring-like enhancement at 65-97 au; arcs peak at 3-4 mJy/beam | F: First substructure seen in a disc around an O-type protostar | **supported**
- H: Is the H2O emission tracing a Keplerian disc and what is the central mass? | E: PV diagram and by-eye disc model | R: Keplerian pattern; 45 +/- 10 Msun | F: Keplerian rotation about a ~45 Msun star | **supported**
- H: Is the disc gravitationally unstable? | E: Toomre Q maps | R: Q 2-4 in the ring for T>150 K | F: Locally stable in the optically thin, hot case | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Extreme excitation H2O line chosen to trace the inner disc  
  > "The extreme excitation energy of this line makes it particularly suited for tracing very inner regions of a molecular disc" (3.2 H2O)
- Alternative: Binary companion or earlier spiral instabilities considered as causes of the ring  
  > "it is plausible that a binary companion is the cause of the ring-like enhancements" (4.3 Disc enhancements)
- How they decided it was enough: _not stated_
- Limitation (authors): Free-free contamination is uncertain so the inner ring is speculative  
  > "Although speculative, because the free-free contamination is uncertain, we tentatively reveal an enhanced inner ring" (3.1 Continuum emission)
- Caveat (inferred, ours): Stellar mass fit is by eye with no formal uncertainty or degeneracy exploration
- Caveat (inferred, ours): Single-band continuum cannot separate optical depth and temperature effects
- Caveat (inferred, ours): Substructure could be partly imaging or self-calibration artefacts at a dynamic range of 640

## Reproducibility

- Data public (paper): Project ID given; CDS data mentioned  
  > "project ID: 2017.1.00098.S - PI: Maud" (2 Observations)
- Products in archive: _not stated_
- Missing: Imaging parameters beyond robust
- Missing: PV model code and parameters
- Missing: Free-free subtraction flux values
- Data volume (inferred): ~20-50 GB
- Score (inferred): 5/5, Single public dataset with clear weighting and calibration, but the model and imaging details are sparse.
- Rediscovery candidate: yes, Public data and numeric results (continuum fluxes, inclination, disc mass), though the PV mass fit is by eye.

## Links

- Method: Maud2018 (Earlier disc PV model and free-free estimates)
- Method: Beuther2017a; Ahmadi2018 (Toomre Q method)
- Companion: Cesaroni2017 (Original ALMA survey of O-type protostars)
- Companion: Maud2018 (Lower-resolution ALMA study of G17.64)
- Related: Red MSX Survey (RMS)

## Checks

```json
{
 "quotes": 64,
 "quotes_ok": 64,
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
  "facts": 74,
  "stated": 46,
  "rate": 0.622
 },
 "evidence_ok": true
}
```
