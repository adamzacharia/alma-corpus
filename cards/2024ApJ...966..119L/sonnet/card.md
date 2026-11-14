# ALMA Spectral Survey of an Eruptive Young Star, V883 Ori (ASSAY). I. What Triggered the Current Episode of Eruption?

`2024ApJ...966..119L` | The Astrophysical Journal 2024 | first author: Lee, Jeong-Eun | arXiv: 2403.03436 | DOI: 10.3847/1538-4357/ad3106

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks, star_formation, astrochemistry
- Question: What triggered the current eruption of V883 Ori, as seen in the morphology and kinematics of molecular lines from the envelope and disk?  
  > "Together, these features suggest that the current episode of eruption in V883 Ori may be triggered by the infall from the envelope to the outer disk" (abstract)
- Target **V883 Ori**: coordinates _not stated_; z/distance 388 pc  
  > "It has a bolometric luminosity of $\sim$220 L$_\odot$ (cite: Furlan2016) at a distance of 388 pc (cite: jelee19)." (Introduction); distance from Lee et al. 2019 (jelee19)  
  > "It has a bolometric luminosity of $\sim$220 L$_\odot$ (cite: Furlan2016) at a distance of 388 pc (cite: jelee19)." (Introduction)

## Data provenance

- ALMA projects: 2019.1.00377.S
- bands: Band 6, ~221-275 GHz  
  > "The spectral survey covers from $\sim$221 to $\sim$275 GHz with three Science Goals (SGs)" (2 Observation)
- frequencies and spectral setup: 3 SGs x 5 tunings x 4 SPWs = 60 SPWs, 933.5 MHz each, 488.281 kHz resolution  
  > "resulting in 60 SPWs in total. Each SPW covers a bandwidth of 933.5 MHz and a spectral resolution of 488.281 kHz" (2 Observation)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 15.1 m to 3.6 km across executions  
  > "SG3 & 256.70 – 274.86 & 2021/11/15 & 41.4 m – 3.6 km & 52 & 50.6" (Observation log table)
- angular resolution: 0.15'' - 0.2''  
  > "Our spatial resolutions (0.15$''$ $\sim$ 0.2$''$) are high enough to resolve the water sublimation radius" (Introduction)
- max recoverable scale: 1.6'' to 3.7''  
  > "the maximum recoverable sizes (1.6$''$ to 3.7$''$ equivalent with 600 au to 1500 au)" (Introduction)
- sensitivity: RMS about 1.8-3.5 mJy/beam per SPW (per-SPW table)  
  > "& 17 & 235.20 – 236.14 & 0.17 & 0.12 & -75.9 & 3.5" (Table of beams and RMS)
- time on source: SG1 37.9 min, SG2 22.7 min, SG3 50.6 min per execution  
  > "SG3 & 256.70 – 274.86 & 2021/11/15 & 41.4 m – 3.6 km & 52 & 50.6" (Observation log table)
- observing dates: 2021 May to November  
  > "SG1 & & 2021/05/10 & 15.1 m – 2.5 km & 44 & 37.9" (Observation log table)
- pi or archival as stated: New Cycle 7 observations, PI Jeong-Eun Lee  
  > "carried out in band 6 during Cycle 7 (2019.1.00377.S, PI: Jeong-Eun Lee)" (2 Observation)
- Line: HDO 3(1,2)-2(2,1) (225.89672 GHz)
- Line: CO 2-1 (230.53800 GHz)
- Line: HCO+ 3-2 (267.55763 GHz)
- Line: HCN 3-2 (265.88643 GHz)
- Line: HNC 3-2 (271.98114 GHz)
- Line: C17O 2-1 (224.71419 GHz)
- Line: SO 7(6)-6(5) (261.84372 GHz)
- External data: Systemic velocity 4.3 km/s  
  > "The systematic velocity of V883 ori is 4.3 km s$^{-1}$ (cite: cieza16)." (3 Spatial Distribution) [from cieza16]
- External data: Inclination 38.3 +/- 1 deg  
  > "is 38.3 $\pm$ 1 $^\circ$ (cite: cieza16)" (3 Spatial Distribution) [from cieza16]
- External data: Central mass 1.2 Msun from C18O/C17O Keplerian rotation  
  > "the central mass is 1.2 M$_\odot$, estimated using the Keplerian rotation traced by the C$^{18}$O and C$^{17}$O lines (cite: cieza16; jelee19)" (3 Spatial Distribution) [from cieza16; jelee19]
- External data: Disk surface density profile used for Toomre Q  
  > "with the surface density profile of (cite: Cieza2018) and the *current* temperature profile (cite: jelee19)" (4.1) [from Cieza2018; jelee19]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The calibration was performed using the CASA pipeline (6.2.1.7)" (2 Observation)
- casa version: 6.2.1.7  
  > "The calibration was performed using the CASA pipeline (6.2.1.7)" (2 Observation)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0423-0120 (bandpass and flux); J0529-0159 phase  
  > "with a quasar, J0423-0120, as the bandpass and flux calibrators and a quasar, J0529-0159, as the phase calibrator" (2 Observation)
- flux scale uncertainty: within 5% calibration uncertainty  
  > "remains within the calibration uncertainty of 5% (cite: francis20)" (2 Observation)
- self calibration: Three phase and one amplitude rounds per SG, using continuum from line-free channels  
  > "Three phases and one amplitude self-calibrations were carried out for each SG." (2 Observation)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs robust = 0.5 for SG1, SG2; Natural for SG3  
  > "cleaned using the Briggs weighting (robust = 0.5) for SGs 1 and 2 and the Natural weighting for SG 3" (2 Observation)
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Image-space subtraction, level measured with STATCONT  
  > "The continuum was subtracted in the image space, and the continuum level is automatically measured using STATCONT" (2 Observation)
- line free channels: Identified by strong extended emission (CO, HCN, HCO+) or a 3 sigma threshold in the averaged spectrum within a 0.3'' aperture (COMs)  
  > "a signal higher than the 3 $\sigma$ RMS level in the averaged spectra within an aperture of 0.3$''$" (2 Observation)
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: For consistency checks only, all SPWs convolved to 0.25'' x 0.15'' (-77 deg)  
  > "all SPWs were convolved into a beam of 0.25$''$ $\times$ 0.15$''$ (-77$^\circ$)" (2 Observation)
- final beam: 0.13-0.24'' major, 0.11-0.13'' minor, per SPW  
  > "& 13 & 249.58 – 250.52 & 0.24 & 0.12 & -77.3 & 3.3" (Table of beams and RMS)
- final rms: about 1.8-3.5 mJy/beam per SPW  
  > "& 2 & 257.61 – 258.55 & 0.13 & 0.11 & -64.4 & 1.8" (Table of beams and RMS)

### Inherited from earlier work

- PC1-filtering (PCA) method for extracting COM spectra and PV contours  
  > "extracted by the PC1-filtering method developed using the Principle Component Analysis (PCA) applied to the cube data of isolated strong COMs lines (cite: Yun2023)" (3) [from Yun2023]
- Spiral fitting analysis (logarithmic and Archimedean)  
  > "we follow the analysis presented by (cite: cflee2020) to fit the peak intensity positions of HCN along the spiral arms" (4.1) [from cflee2020]
- HDO line same as Tobin et al. 2023  
  > "the HDO line adopted in this figure is the same as (cite: Tobin2023) used" (3.1) [from Tobin2023]

### Not stated but needed to reproduce (our reading)

- tclean parameters: cell size, image size, masks, deconvolver, threshold, niter
- Channel width/velocity regridding for moment maps
- Which channels were line-free per SPW
- Self-calibration solution intervals
- Disk geometry for the PV cuts and the spiral-arm peak positions
- Temperature profile and surface density details for Q curves
- How the 1'' aperture spectra were extracted and corrected
- Details of the PCA implementation

## Analysis recipe

1. **Calibrate and self-calibrate**: CASA pipeline calibration; continuum self-calibration (3 phase + 1 amplitude) per SG  
  > "Three phases and one amplitude self-calibrations were carried out for each SG." (2 Observation)
   - software: CASA
   - fitting: _not stated_
   - validation: Continuum consistent across 60 SPWs, within 5% flux uncertainty  
  > "The continuum images using the STATCONT show consistent values within individual SPWs" (2 Observation)
2. **Image cubes and subtract continuum**: Clean with Briggs robust 0.5 (SG1, SG2) or natural (SG3); image-space continuum subtraction with STATCONT  
  > "The continuum was subtracted in the image space, and the continuum level is automatically measured using STATCONT" (2 Observation)
   - software: CASA, STATCONT
   - fitting: _not stated_
   - validation: _not stated_
3. **Moment maps and spectra**: Moments 0, 1, 8, 9 after clipping below 4 sigma; PC1 filtering for COM spectra  
  > "We create the moment maps of each molecule by clipping out values below 4$\sigma$." (3)
   - software: PCA
   - fitting: _not stated_
   - validation: Compared a SG2-beam-convolved CH3OH image with the original to check beam artifacts  
  > "Figure [5](#fig:beam) shows the comparison between the original CH$_3$OH image and the image convolved with the elongated beam obtained by SG2" (3.2)
4. **Kinematics: PV diagrams and model velocity comparison**: PV diagrams along the disk semi-major axis compared with Keplerian rotation; model moment 9 maps convolved to observed resolution  
  > "All three PV diagrams follow well the Keplerian rotation velocity profile, with a central mass of 1.2 M$_\odot$." (4.2)
   - assumption: Distance 388 pc, M*=1.2 Msun, inclination 38.3 deg, PA ~120 deg  
  > "The inclination inferred from the ratio between the disk semi-major and semi-minor axes is 38.3 $\pm$ 1 $^\circ$ (cite: cieza16)" (3)
   - fitting: _not stated_
   - validation: C17O consistent with the Keplerian model  
  > "The C$^{17}$O moment 9 map, which is the best tracer of the Keplerian disk, is consistent with the model." (4.1)
5. **Spiral fitting and Toomre Q**: Fit HCN peak positions with logarithmic and Archimedean spirals; compute Q for current and pre-burst temperature  
  > "the logarithmic spiral with $R=R_0 e^{a\theta}$, developed by the gravitational instability and the Archimedean spiral with $R=R_0 + b\theta$" (4.1)
   - assumption: Pre-burst snowline at 4 au  
  > "If the snowline was located at 4 au, then $Q < 2$ at $r < 100$ au and $Q \sim 3.5$ at 200 au" (4.1)
   - fitting: _not stated_
   - validation: Southern arm well fit, northern not; shape ambiguous  
  > "The northern arm does not reveal a spiral profile, while the southern arm is well-fit." (4.1)

## Software

- **CASA** 6.2.1.7: Pipeline calibration, self-calibration and cleaning  
  > "The calibration was performed using the CASA pipeline (6.2.1.7)" (2 Observation)
- **STATCONT** : Continuum level measurement for subtraction  
  > "the continuum level is automatically measured using STATCONT" (2 Observation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| HDO emission boundary radius (water sublimation radius in disk surface) | ~0.3'' (~120 au) | not stated | arcsec / au | 3 | The largest water sublimation radius, as traced by HDO, is about 120 au ($\sim$0.3$''$). |
| Outer gas disk radius | ~0.8 | not stated | arcsec | 3 | The outer boundary of the gas disk is at r$\sim$0.8$''$. |
| Toomre Q (current) | >2 at all radii, ~7 at 200 au | not stated | dimensionless | 5 | it is greater than 2 at all radii and $\sim$7 at 200 au |
| Toomre Q (pre-burst, snowline at 4 au) | <2 at r<100 au, ~3.5 at 200 au | not stated | dimensionless | 5 | then $Q < 2$ at $r < 100$ au and $Q \sim 3.5$ at 200 au |
| Infall absorption velocity | ~1.5 | not stated | km/s | 3 | The clear absorption negative dips are seen around 1.5 km s$^{-1}$. |
| Number of detected lines | ~4600 | not stated | lines | 3 | Our ALMA observations detect about 4600 lines |

## Qualitative findings

- HDO, COMs, HDCO, HNCO and OCS emission is confined within the water sublimation radius, and HCO+ has a hole due to destruction by water  
  > "Molecular emission from complex organic molecules (COMs) is confined within the HDO emission boundary, and HCO$^+$ has an emission hole" (abstract)

## Claim tuples

- H: The current eruption was triggered by infall from the envelope onto the outer disk | E: Mapped many molecular lines and inspected morphology and kinematics | R: Arm-like structures in HCO+ and SO, red-shifted absorption, tentative spirals in HCN and H2CO | F: Infall may have induced a spiral wave that propagated inward and triggered the burst | **partially**
- H: HDO traces the water sublimation region, and COMs sublimate with it | E: Moment maps of HDO and COMs | R: HDO emission radius ~0.3''; COMs lie within it | F: COMs are co-located with water sublimation | **supported**
- H: Spiral structure is consistent with gravitational instability | E: Toomre Q computed for current and pre-burst temperatures | R: Q>2 now; Q<2 inside 100 au if the pre-burst snowline was at 4 au | F: Spirals could have developed before the burst; the disk is now stable | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: Moments 8 and 9 are used where line blending or hyperfine structure contaminates moments 0 and 1  
  > "moment 8 and 9 maps better present the distribution of the dominating line emission" (3)
- How they decided it was enough: _not stated_
- Limitation (authors): Velocity resolution and S/N are too low to robustly examine arm kinematics and spirals  
  > "the velocity resolution of our data is not high enough to robustly examine the kinematics of the large arm-like structures beyond the disk." (4.1)
- Caveat (inferred, ours): Spiral and streamer features are tentative and qualitative
- Caveat (inferred, ours): Trigger scenario is inferred, with no quantitative modelling
- Caveat (inferred, ours): Pre-burst temperature assumption (snowline at 4 au) is unconstrained
- Caveat (inferred, ours): Optically thick lines are partially filtered out in the absorption channel

## Reproducibility

- Data public (paper): Acknowledges ALMA data 2019.1.00377.S; public status not stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2019.1.00377.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Full tclean parameters and masks
- Missing: Line-free channel lists
- Missing: Spiral fit and Q calculation details
- Missing: PCA code details
- Data volume (inferred): Large: 60 SPW cubes over 7 executions, probably several hundred GB to ~1 TB
- Score (inferred): 3/5, Calibration and weighting are given, but imaging parameters and the qualitative analysis are underspecified.
- Rediscovery candidate: no, Results are mostly qualitative morphology with few numeric answer keys, and the imaging recipe is incomplete.

## Links

- Method: Yun2023 (PC1 filtering method)
- Method: Sanchez-Monge2018 (cite: Sanchez-Monge2018) (STATCONT continuum estimation)
- Method: cflee2020 (Spiral fitting analysis)
- Companion: Jeong et al. submitted (COM spectra analysis)
- Companion: ruiz2022 (Lower-resolution ALMA observations of V883 Ori)
- Related: ASSAY

## Checks

```json
{
 "quotes": 65,
 "quotes_ok": 65,
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
  "facts": 71,
  "stated": 47,
  "rate": 0.662
 },
 "evidence_ok": true
}
```
