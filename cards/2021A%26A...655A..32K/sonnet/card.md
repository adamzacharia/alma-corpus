# V838 Monocerotis as seen by ALMA: A remnant of a binary merger in a triple system

`2021A&A...655A..32K` | Astronomy and Astrophysics 2021 | first author: Kamiński, Tomek | arXiv: 2106.07427 | DOI: 10.1051/0004-6361/202141526

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, astrochemistry
- Question: What is the architecture of the V838 Mon merger remnant ~17 yr after the 2002 eruption, including the position of the B-type companion and the mass and distribution of gas and dust?  
  > "We wish to characterize the merger remnant $\sim$17 yr after the eruption to learn more about the remaining system, the progenitor, and merger physics." (abstract)
- Target **V838 Monocerotis**: coordinates RA=07:04:04.821535, Dec=-03:50:50.629426 (ICRS, component M)  
  > "in the far outer Galaxy, at a distance of 5.9 kpc (cite: sparks; Ortiz-Leon)" (Introduction); "RA=07:04:04.821535($\pm$0.000012) and Dec=$-03$:50:50.629426($\pm$0.000177) (J2000.0)" (4 ALMA results: continuum); z/distance 5.9 kpc  
  > "in the far outer Galaxy, at a distance of 5.9 kpc (cite: sparks; Ortiz-Leon)" (Introduction); "RA=07:04:04.821535($\pm$0.000012) and Dec=$-03$:50:50.629426($\pm$0.000177) (J2000.0)" (4 ALMA results: continuum); distance from Sparks et al. 2008; Ortiz-León et al. 2020  
  > "in the far outer Galaxy, at a distance of 5.9 kpc (cite: sparks; Ortiz-Leon)" (Introduction); "RA=07:04:04.821535($\pm$0.000012) and Dec=$-03$:50:50.629426($\pm$0.000177) (J2000.0)" (4 ALMA results: continuum)

## Data provenance

- ALMA projects: 2018.1.00336.S
- bands: Band 6  
  > "The observations were executed in band 6 and covered frequencies 215.56–217.44, 219.06–220.94, 230.11–231.99, and 232.06–233.94 GHz" (2 ALMA observations)
- frequencies and spectral setup: four spectral ranges, native resolution 1.3–2.5 km/s  
  > "at a native resolution of 1.3–2.5 km s$^{-1}$" (2 ALMA observations)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: 43 antennas, most extended configuration, baselines 83.1–15 238.4 m  
  > "The array with 43 antennas was in its most extended configuration with baselines of 83.1–15 238.4 m." (2 ALMA observations)
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: 9.8 uJy/beam continuum, beam 28x25 mas, natural weighting  
  > "The continuum sensitivity of the ALMA data is 9.8 $\mu$Jy per beam at a beam full width at half-maximum (FWHM) of 28$\times$25 mas and at natural weighting of visibilities." (2 ALMA observations)
- time on source: _not stated_
- observing dates: 20 June 2019, three execution blocks  
  > "The ALMA observations were acquired on 20 June 2019 in three consecutive execution blocks." (2 ALMA observations)
- pi or archival as stated: _not stated_
- Line: CO 2-1 (230.538 GHz)
- Line: SiO 5-4 (217.1049 GHz)
- Line: SO 5_6-4_5 (219.9494 GHz)
- Line: AlOH 7-6 (220.3344 GHz)
- Other facility **VLT X-SHOOTER**: 2012 optical/NIR spectrum used for spectral typing  
  > "We used the X-SHOOTER spectrograph on the Very Large Telescope (VLT) to obtain spectra of V838 Mon." (Optical spectra)
- Other facility **SALT HRS**: 2020 high-resolution optical spectrum  
  > "The observations were taken on 23 December 2020 with the High Resolution Spectrograph" (Optical spectra)
- Other facility **SOFIA HAWC+, Subaru COMICS, Mount Abu NICS, WISE**: IR photometry for the SED  
  > "The data used in our SED reconstruction are listed in Table [2](#tab-sed)." (SED data sources)
- External data: UBVRI photometry used in the SED  
  > "The $UBVR_CI_C$ photometry was taken from (cite: Barsukova) through the website of V. Goranskij" (SED data sources) [from (cite: Barsukova)]
- External data: Systemic LSR velocity 53 km/s  
  > "LSR) systemic velocity of the star of 53 km s$^{-1}$ (cite: KamiSubmm)" (5 Optical spectroscopy) [from (cite: KamiSubmm)]

## Processing

### Calibration

- pipeline or manual: Default observatory calibration scripts  
  > "Visibilities were calibrated with default calibration scripts delivered by the observatory" (2 ALMA observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Attempted, unsatisfactory; original calibration used  
  > "An attempt to improve data quality by a self-calibration procedure was unsatisfactory and visibilities with the original calibration were used." (2 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: natural, uniform, and Briggs robust = 0.5 (beam 22 mas)  
  > "An example map with Briggs weighting and the robust parameter of $R$=0.5 (resulting in a beam of a FWHM of 22 mas)" (3 ALMA results: continuum)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Polynomial fit to calibrated visibilities; continuum images from line-free channels  
  > "Continuum images include only line-free channels and cubes with line emission had continuum removed by a polynomial fit to calibrated visibilities." (2 ALMA observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Systemic velocity and earlier LTE multi-line models of SMA data revised with new filling factors  
  > "we revised the multi-line models by implementing updated beam filling factors." (4 ALMA results: spectral lines) [from (cite: KamiSubmm)]
- Interstellar extinction E(B-V)=0.85, R_V=3.1  
  > "all data were corrected for interstellar extinction with $E_{B_V}$=0.85 mag and $R_V$=3.1, following (cite: TylendaProgenitor)." (SED data sources) [from (cite: TylendaProgenitor)]

### Not stated but needed to reproduce (our reading)

- CASA version and tclean parameters (cell, image size, masks, deconvolver)
- Line-free channel selection and polynomial order
- Flux calibrator and flux scale uncertainty
- Spectral resolution/channel width of cubes used for moments, moment clipping thresholds
- Full RADMC-3D model input files and how models were compared to data (no fit statistic)
- LTE excitation model parameters and CO-to-H2 conversion for 0.1 Msun
- Dust mass derivation details

## Analysis recipe

1. **Measure continuum components**: Gaussian fits to components M and B in Briggs R=0.5 continuum map; remainder is external cloud  
  > "A Gaussian fit to this compact source (at Briggs’ $R$=0.5) gives a size (corrected for the beam-size) of (17.6$\pm$0.8)$\times$(7.6$\pm$1.4) mas" (3 ALMA results: continuum)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Map molecular lines and moments**: Zeroth, first and second moment maps of CO, SiO, SO etc.  
  > "The maps of velocity-integrated emission (zeroth moment) are shown in Fig. [3](#fig-line-maps)." (4 ALMA results: spectral lines)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
3. **Estimate molecular excitation and mass**: LTE multi-line models with updated beam filling factors; CO 2-1 optical depth, column density, H2 mass  
  > "they yield an overall mass of H$_2$ of 0.1 M$_{\ensuremath{\odot}}$ that is consistent with the old data." (4 ALMA results: spectral lines)
   - assumption: CO as proxy of H2 distribution; beam filling factor of one  
  > "We assume that CO is the most representative probe of the entire molecular remnant, that is, it can be used as a proxy of the H$_2$ distribution." (4 ALMA results: spectral lines)
   - fitting: _not stated_
   - validation: consistent with earlier SMA-based mass  
  > "they yield an overall mass of H$_2$ of 0.1 M$_{\ensuremath{\odot}}$ that is consistent with the old data." (ALMA results: spectral lines)
4. **3D dust radiative transfer model of continuum and SED**: RADMC-3D models with two stars, disk/torus, shells and Gaussian clouds, compared to SED and maps after thousands of simulations  
  > "After running thousands of simulations, we arrived at a model described below and shown in Fig. [8](#fig-model3D)." (6.1 Dust)
   - software: RADMC-3D
   - parameter: V838 Mon blackbody 3300 K, R=3.25e13 cm; B star 18 kK, 230 au away; M disk inclined 26 deg, 60–95 au  
  > "V838 Mon was represented by a black body of a fixed temperature of 3300 K" (6.1 Dust)
   - assumption: Mg-rich amorphous pyroxene silicates, single grain size 0.1 um, grain density 3 g/cm3  
  > "Grain density was set to 3 g cm$^{-3}$." (6.1 Dust)
   - fitting: manual exploratory fitting, no formal fit  
  > "the model we attempted to match to the observations was rather exploratory." (6.1 Dust)
   - validation: Compared simulated and observed images and SED  
  > "A comparison between observed and simulated images and SEDs are shown in Figs. [9](#fig-compare) and [10](#fig-sed)." (6.1 Dust)
5. **Model SiO and CO gas structure**: RADMC-3D shell for CO; Shape software two-shell model with linear velocity law for SiO  
  > "The velocity gradient is steeper for the outer structure ($k$=1.9) than for the inner one ($k$=1.7)." (6.2 Molecular gas)
   - software: RADMC-3D, Shape
   - fitting: _not stated_
   - validation: Reproduces channel maps and PV diagrams qualitatively  
  > "Our simple model satisfactorily reproduces structures in channel maps, shown in Appendix [11](#appendix-SiO), and position-velocity diagrams" (3D reconstruction of the remnant, Molecular gas)

## Software

- **CASA** : calibration and imaging  
  > "data were processed, including imaging, with the Common Astronomy Software Applications (cite: casa)" (2 ALMA observations)
- **RADMC-3D** : 3D dust and gas radiative transfer  
  > "We attempted a reconstruction of dust distribution in the remnant of V838 Mon using RADMC-3D" (6.1 Dust)
- **Shape** : 3D morpho-kinematic SiO model  
  > "we used the Shape software[^2] (cite: shape1)" (6.2 Molecular gas)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Component M size | 17.6 x 7.6, PA 132 deg | ±0.8 x ±1.4 mas; ±4 deg | mas | 1 | (17.6$\pm$0.8)$\times$(7.6$\pm$1.4) mas with the major axis at a position angle (PA) of 132$^\circ$$\pm$4$^\circ$ |
| Component M flux | 588 | 14 | uJy | 1 | Its flux of 588$\pm$14 $\mu$Jy constitutes 28% of the total continuum flux in the map. |
| Component B flux | 510 | 48 | uJy | 1 | a flux of 510$\pm$48 $\mu$Jy (24.4% of the total flux in the map) |
| M–B separation | 38.2 mas (225.4 au) at PA -58.5 deg | not stated | mas | 1 | 38.2 mas or 225.4 au at a PA of –58.5$^\circ$ |
| Molecular mass (H2) | 0.1 | not stated | Msun | 3 | the estimate of the remnant’s mass is currently $M_{\rm H2}$=0.1 M$_{\ensuremath{\odot}}$ |
| Dust mass | 8.3e-3 | uncertain | Msun | 4 | Our independent but uncertain estimate of the mass of dust only is 8.3$\cdot$10$^{-3}$ M$_{\ensuremath{\odot}}$. |
| CO 5-sigma extent radius | 115 | ±5 mas | mas | 2 | the 5$\sigma$ contour extends up to a radius of 115$\pm$5 mas or 679$\pm$30 au |
| CO 2-1 maximal radial velocity | 230 | ±20 km/s | km/s | 2 | indicates maximal radial velocities of 230$\pm$20 km s$^{-1}$ |

## Qualitative findings

- B component identifies the companion position, consistent with ~250 au separation  
  > "Its projected distance to V838 Mon of 225 au (at the 5.9 kpc distance) is close to the separation $a\approx$250 au" (3 ALMA results: continuum)
- Gas and dust distributions differ; SiO void and chemical changes near the B star suggest shocks  
  > "we find it more likely that this turbulent region hosts shocks that strongly influence gas molecular composition." (7.1 Molecular gas)

## Claim tuples

- H: Can the B-type companion be located relative to V838 Mon? | E: Band 6 continuum imaging at ~25 mas | R: Secondary continuum source 38.2 mas (225 au) from M | F: Component B is material around the B star, consistent with orbit ~230–250 au | **supported**
- H: Is there a disk around the merger remnant? | E: Gaussian fit of M and RADMC-3D modeling | R: Elongated 17.6x7.6 mas source; inclined torus fits | F: Interpreted as a disk at moderate inclination, not firm | **partially**
- H: The merger ejecta interacts with the B star | E: Molecular maps and moments, analytic radiation pressure/wind estimates | R: Turbulent, redshifted region and SiO void near B | F: Interaction with B star alters kinematics and chemistry | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Spherical dusty cloud for M rejected: too much extinction toward central star  
  > "However, such a configuration results in a higher extinction towards the central star than observed." (6.1 Dust)
- How they decided it was enough: _not stated_
- Limitation (authors): Models have many free parameters and are non-unique  
  > "They cannot be uniquely constrained by our observations" (6.1 Dust)
- Caveat (inferred, ours): Dust and gas models are manually tuned with no uncertainty estimates
- Caveat (inferred, ours): Disk interpretation rests on a barely resolved source
- Caveat (inferred, ours): Dust mass depends on assumed single-size silicate opacity

## Reproducibility

- Data public (paper): ALMA project code given; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2018.1.00336.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CASA version and imaging parameters
- Missing: RADMC-3D model files
- Missing: Line-free channel ranges
- Data volume (inferred): ~100–300 GB raw for long-baseline Band 6 data
- Score (inferred): 3/5, Data identifiable and key fluxes numeric, but imaging and model details are sparse.
- Rediscovery candidate: no, Imaging parameters and models are incompletely specified; model results not uniquely reproducible.

## Links

- Method: (cite: radmc3d) (dust radiative transfer code)
- Method: (cite: shape1) (Shape modeling software)
- Companion: (cite: Ortiz-Leon) (briefly presented part of the same ALMA dataset)
- Companion: (cite: KamiSubmm) (earlier SMA observations of V838 Mon)

## Checks

```json
{
 "quotes": 60,
 "quotes_ok": 60,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 40,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
