# High-speed molecular cloudlets around the Galactic center's supermassive black hole

`2018A&A...618A..35G` | Astronomy and Astrophysics 2018 | first author: Goicoechea, Javier R. | arXiv: 1806.01748 | DOI: 10.1051/0004-6361/201833558

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism
- Question: Does molecular gas exist inside the central cavity around Sgr A*, and how does its kinematics compare with the CND and ionized streamers?  
  > "High-angular resolution, velocity-resolved observations with ALMA provide new avenues to probe and characterize the molecular gas component in the vicinity of a SMBH." (Introduction)
- Target **Sgr A* and southern lobe of the circumnuclear disk**: coordinates RA(J2000)=17h45m40.036s, Dec=-29d00m28.17s  
  > "Observations toward Sgr A$^*$ (R.A. (J2000)=17h 45 m 40.036s; DEC. (J2000)=-29$^{\circ}$00$'$28.17$''$)" (2 Observations); "We adopt a distance of 8300 pc to Sgr A$^*$ (cite: Genzel10)." (4.1 CND kinematics); z/distance 8300 pc  
  > "Observations toward Sgr A$^*$ (R.A. (J2000)=17h 45 m 40.036s; DEC. (J2000)=-29$^{\circ}$00$'$28.17$''$)" (2 Observations); "We adopt a distance of 8300 pc to Sgr A$^*$ (cite: Genzel10)." (4.1 CND kinematics); distance from Genzel10  
  > "Observations toward Sgr A$^*$ (R.A. (J2000)=17h 45 m 40.036s; DEC. (J2000)=-29$^{\circ}$00$'$28.17$''$)" (2 Observations); "We adopt a distance of 8300 pc to Sgr A$^*$ (cite: Genzel10)." (4.1 CND kinematics)

## Data provenance

- ALMA projects: 2013.1.01058.S
- bands: _not stated_
- frequencies and spectral setup: 975 kHz (~0.8 km/s) resolution over 1875 MHz bandwidth; CO 3-2, H13CN 4-3, SO in the same spectrum; 39-pointing mosaic, 60''x60'' field  
  > "We employed a correlator providing a resolution of 975 kHz ($\simeq$0.8 km s$^{-1}$) over an 1875 MHz bandwidth ($\simeq$1600 km s$^{-1}$)" (2 Observations); "The observations consisted of a 39-pointing mosaic" (2 Observations)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m array, 28 antennas, plus single-dish total power from three 12-m antennas  
  > "were carried out using 28 12 m-array antennas as part of project 2013.1.01058.S" (2 Observations); "a deep, fully-sampled single-dish map taken with 3 different 12-m antennas providing a beam full-width at half-maximum (FWHM) of about 18$''$" (2 Observations)
- configurations: _not stated_
- baselines: 12 to about 350 m  
  > "Baseline configurations from 12 to about 350 m were measured." (2 Observations)
- angular resolution: 1.1''x0.7'' synthesized beam  
  > "using the final synthesized beam-size of 1.1$''$$\times$0.7$''$" (2 Observations)
- max recoverable scale: _not stated_
- sensitivity: ~200 mK per 2 km/s channel in final cube; TP map ~7 mK per 2 km/s  
  > "The rms noise in the final cube is $\sim$200 mK per resolution channel." (2 Observations)
- time on source: ~3 h ALMA 12m; TP map 17.4 h on-source  
  > "The observation time with the ALMA 12 m-array was $\simeq$3 h." (2 Observations); "The total on-source time of these single-dish ‘total power’ (TP) map was 17.4 h." (2 Observations)
- observing dates: _not stated_
- pi or archival as stated: PI J. R. Goicoechea  
  > "project 2013.1.01058.S (PI. J. R. Goicoechea)" (2 Observations)
- Line: 12CO J=3-2 (345.796 GHz)
- Line: H13CN J=4-3 (345.339 GHz)
- Line: SO 8_9-7_8 (346.528 GHz)
- Other facility **Herschel/PACS 70 um (Hi-GAL)**: 70 um dust emission map for comparison  
  > "the 70 $\mu$m dust thermal emission (cite: Molinari11)" (4.4 FUV attenuation)
- Other facility **[Ne II] 12.8 um cube**: ionized gas kinematics from Irons12  
  > "of the \[Ne ii\]12.8 $\mu$m line[^1] (green) from ionized gas inside the cavity (cite: Irons12)" (3 Results)
- External data: [Ne II] 12.8 um data cube of ionized gas  
  > "of the \[Ne ii\]12.8 $\mu$m line[^1] (green) from ionized gas inside the cavity (cite: Irons12)" (3 Results) [from Irons12]
- External data: 19.7/31.7 um color temperatures: ~145 K in cavity, ~85 K at CND-S inner edge  
  > "peaks at $T_{\rm d}$$\approx$145 K inside the cavity, and is $\approx$85 K at the inner edge of the CND-S lobe (cite: Lau13)" (4.4 FUV attenuation) [from Lau13]
- External data: Rotation temperature of H12CN = 43+-6 K  
  > "$T_{\rm rot}$(H$^{12}$CN)=43$\pm$6 K from H$^{12}$CN $J$=6-5 to 8-7 line observations (cite: Goicoechea18)" (4.3 Molecular gas densities) [from Goicoechea18]
- External data: H12CN abundance ~5e-9  
  > "The H$^{12}$CN abundance is well constrained by chemical models to $x$(H$^{12}$CN)$\approx$5$\cdot$10$^{-9}$ (cite: Boger05)." (4.3 Molecular gas densities) [from Boger05]
- Simulation/model as data: Ellipse (three Keplerian orbit families) and spiral models of ionized streamers compared with molecular data  
  > "We start by confronting the spiral and the ellipse models of the orbiting ionized streamers." (4.2 Plausible cloudlet motions)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.6.0  
  > "ALMA executing blocks were first calibrated in CASA 4.6.0 software and then exported to GILDAS software" (2 Observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: Högbom CLEAN in GILDAS  
  > "The dirty image was deconvolved using the Högbom CLEAN algorithm." (2 Observations)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Linear baseline fit in uv plane to line-free velocity windows, on a 800-channel x 2 km/s axis  
  > "we made a linear fit to velocity windows devoid of molecular line emission." (2 Observations)
- line free channels: Excluded [-800,-300] and [-250,+560] km/s  
  > "we excluded the $[-800,-300]$ and $[-250,+560]$ km s$^{-1}$ velocity ranges" (2 Observations)
- primary beam correction: _not stated_
- array combination: Zero-spacing pseudo-visibilities from TP map created with GILDAS/MAPPING and merged in the uv plane  
  > "These pseudo-visibilities were merged with the interferometric (alone) observations in the UV plane." (2 Observations)
- smoothing: Smoothed to 2 km/s velocity resolution by integrating rectangles  
  > "smoothed by integrating rectangles, to a velocity resolution of 2 km s$^{-1}$" (2 Observations)
- final beam: 1.1''x0.7''  
  > "using the final synthesized beam-size of 1.1$''$$\times$0.7$''$" (2 Observations)
- final rms: ~200 mK per resolution channel  
  > "The rms noise in the final cube is $\sim$200 mK per resolution channel." (2 Observations)

### Inherited from earlier work

- Ellipse model of three Keplerian orbit families for ionized streamers  
  > "the standard model (cite: Zhao09)" (4.2.2 The ellipse model) [from Zhao09]
- Spiral model and simplified stellar mass distribution M*(r)=m* r^1.2  
  > "Here we follow (cite: Irons12) and use a simplified mass distribution $M_{\star}(r) \simeq m_{\star}\cdot r^{1.2}$" (4.1 CND kinematics) [from Irons12]
- Zero-spacing visibility creation with GILDAS/MAPPING  
  > "The GILDAS/MAPPING software was used to create the zero-spacing visibilities (cite: Pety10) not sampled by the ALMA array." (2 Observations) [from Pety10]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters (threshold, mask, iterations), weighting, cell and image size
- Flux calibrator and calibration details; flux scale uncertainty
- How the TP map was calibrated and scaled when merged
- Cloudlet identification criteria and Gaussian fitting procedure
- Model orbit parameters of the ellipse model used for overplots
- Path/area definitions for integrated column densities and masses
- Self-calibration usage

## Analysis recipe

1. **Calibrate and image ALMA+TP cubes**: CASA calibration, GILDAS uv-plane baseline subtraction, TP zero-spacing merge, mosaic, Högbom CLEAN, smooth to 2 km/s  
  > "Each mosaic field was then imaged and a dirty mosaic was built." (2 Observations)
   - software: CASA, GILDAS
   - fitting: _not stated_
   - validation: Compared ALMA-alone and ALMA+TP channel maps  
  > "Figures [5](#fig:h13cn_so_appendix) and [6](#fig:co_alma-tp_appendix) show the final channel maps after adding the zero-spacing data" (Appendix)
2. **Model CND kinematics with circular orbits**: Synthetic rotation curves vLSR=v_phi sin(i) cos(phi) with beta scaling, overplotted on H13CN mean velocity vs position angle  
  > "In order to improve the fit, we allowed an ad hoc parameter $\beta$, from 0 to 1, so that the actual circular velocity is v$_{\phi} \cdot \beta$." (4.1 CND kinematics)
   - parameter: theta~30 deg, i 65-75 deg, beta~0.8-0.9  
  > "the required circular velocity is v$_{\phi}$=100-110 km s$^{-1}$ ($\beta$$\simeq$0.8-0.9)" (4.1 CND kinematics)
   - assumption: Distance 8300 pc; systemic velocity 0 km/s  
  > "We adopt a distance of 8300 pc to Sgr A$^*$ (cite: Genzel10)." (4.1 CND kinematics)
   - fitting: Visual bracketing by models, not formal fit  
  > "Most of the bright H$^{13}$CN ($J$=4-3) emission can be bracketed by models of circular orbits" (4.1 CND kinematics)
   - validation: _not stated_
3. **Compare cloudlet kinematics with spiral and ellipse models**: Overplot spiral model (Irons12 parameters) and Keplerian ellipse models (standard and 3x enclosed mass) on channel maps  
  > "we increase the enclosed mass ($M$ in Eq. 2) by a factor of 3" (4.2.2 The ellipse model)
   - fitting: _not stated_
   - validation: _not stated_
4. **Derive column densities, masses and extinction**: Single Trot Boltzmann optically thin column density with opacity correction; AV=NH/1.9e21  
  > "We assume a single rotational temperature ($T_{\rm rot}$) and a Boltzmann distribution of rotational levels." (4.3 Molecular gas densities)
   - parameter: H13CN Trot 20-100 K; CO Trot=100 K  
  > "We assume a uniform CO abundance of $x$($^{12}$CO)=2$\cdot$10$^{-5}$ and $T_{\rm rot}$=100 K." (4.3 Molecular gas densities)
   - assumption: x(H13CN)=1e-8/25; x(12CO)=2e-5; 12C/13C=25  
  > "Here we take $x$(H$^{13}$CN)=10$^{-8}$/25" (4.3 Molecular gas densities)
   - fitting: _not stated_
   - validation: Compared to LVG results of Mills13 and Smith14  
  > "roughly agree, actually they are up to a factor ten lower, with those derived from local LVG models" (4.3 Molecular gas densities)
5. **Estimate FUV field and photodissociation timescales**: G0=(Td/12.2)^5 from dust color temperatures; attenuation to AV; CO photodissociation rates  
  > "We use $G_0$$\simeq$($T_{\rm d}$/12.2)$^5$ (cite: Hollenbach91)" (4.4 FUV attenuation)
   - assumption: Td(big grains)=Tcol  
  > "we adopt $T_{\rm d}$ (big grains) $\simeq$ $T_{\rm col}$" (4.4 FUV attenuation)
   - fitting: _not stated_
   - validation: _not stated_
6. **Fit foreground CO absorption toward Sgr A***: Multi-Gaussian fit to 1'' ALMA-only spectrum; N(CO) from optical depth integral with Trot=5 K; N(H2) with N(CO)/N(H2)=4e-5  
  > "where we have assumed $T_{\rm rot}$=5 K." (4.5 Absorption spectrum)
   - fitting: multigaussian fit  
  > "From a multigaussian fit to the 1$''$-resolution spectrum toward Sgr A$^*$." (Table 2)
   - validation: Checked for line contamination, e.g. SH+  
  > "We checked that no line from a molecule different than CO could be responsible of the observed spectral features." (Appendix footnote)

## Software

- **CASA** 4.6.0: Calibration of execution blocks  
  > "ALMA executing blocks were first calibrated in CASA 4.6.0 software" (2 Observations)
- **GILDAS** : Imaging, deconvolution and analysis  
  > "then exported to GILDAS software for imaging, deconvolution, and analysis" (2 Observations)
- **GILDAS/MAPPING** : Creating zero-spacing visibilities from TP map  
  > "The GILDAS/MAPPING software was used to create the zero-spacing visibilities" (2 Observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| H2 mass in CND-S lobe | 700-1100 | not stated | Msun | 4 | we determine an H$_2$ mass of 700-1100 $M_{\odot}$ in the CND-S lobe |
| EPVG cloudlet H2 mass (+200 to +300 km/s) | 6-12 | not stated | Msun | 4 | a total H$_2$ mass of 6-12 $M_{\odot}$ |
| HPVG H2 mass (+150 to +200 km/s) | 45-90 | not stated | Msun | 4 | The estimated H$_2$ mass in this velocity interval is 45-90 $M_{\odot}$ |
| G0 in cavity and CND inner edge | 10^5.3 and 10^4.2 | not stated | Habing | 5 | $G_{\rm 0,Cavity}$$\approx$10$^{5.3}$ to $G_{\rm 0,CND}$$\approx$10$^{4.2}$ |
| Circular velocity in CND | 100-110 | not stated | km/s | 2 | the required circular velocity is v$_{\phi}$=100-110 km s$^{-1}$ |
| Infall rates for HPVG and EPVG cloudlets | 1e-2 and 1e-3 | not stated | Msun/yr | 0 | we estimate infall rates of 10$^{-2}$ and 10$^{-3}$ $M_{\odot}$ yr$^{-1}$ respectively |
| CO absorption at -73 km/s N(CO) | 2.09e17 | not stated | cm^-2 | 6 | -73$\pm$1 / 5$\pm$1 / 0.842 / 2.09$\cdot$10$^{17}$ |

## Qualitative findings

- Extreme negative-velocity CO absorption features at -264 and ~-310 km/s newly reported  
  > "two additional weak features at more extreme negative-velocities (v$_{\rm LSR}$=$-$264 and $-$310 km s$^{-1}$) that have not been reported before" (4.5)

## Claim tuples

- H: Does molecular gas exist inside the central cavity? | E: ALMA+TP 12CO(3-2) images at |vLSR|>150 km/s | R: Collection of small high and extreme positive-velocity cloudlets | F: Cavity is not fully cleared of molecular gas | **supported**
- H: Do cloudlets follow ionized streamer kinematics? | E: Compared with spiral and ellipse models | R: Only structures A and B match | F: Most cloudlets do not fit | **supported**
- H: Are CND cores stable? | E: H13CN column density and density estimates vs Roche density | R: Densities ~two orders below Roche density | F: Cores are tidally unstable and transient | **supported**

## Reasoning

- Why this data: Higher resolution and zero-spacing data needed since previous interferometry missed extended gas  
  > "previous interferometric observations were not sensitive to the presence of extended gas emission in the field" (Introduction)
- Why this method: _not stated_
- Alternative: Spiral model rejected for extreme velocities as it only predicts them near Sgr A*  
  > "the spiral model cannot fit the kinematics of the $^{12}$CO cloudlets at extreme velocities" (4.2.1)
- How they decided it was enough: _not stated_
- Limitation (authors): 12CO emission between -100 and +100 km/s may be contaminated by the reference position, so only |vLSR|>130 km/s discussed  
  > "Thus, in this work we only discuss the $^{12}$CO emission in the $|$v$_{\rm LSR}$$|$$>$130 km s$^{-1}$ range." (2 Observations)
- Caveat (inferred, ours): Masses depend strongly on assumed CO abundance and Trot
- Caveat (inferred, ours): Cloudlet distances from Sgr A* are unknown, so cavity membership relies on velocity
- Caveat (inferred, ours): Models compared by eye without formal fits

## Reproducibility

- Data public (paper): Project code given; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.01058.S." (Footnote)
- Products in archive: _not stated_
- Missing: CLEAN settings
- Missing: TP calibration details
- Missing: Cloudlet selection and fitting procedure
- Data volume (inferred): ~100-300 GB raw for 39-pointing mosaic plus TP
- Score (inferred): 4/5, Data identified and main steps described, but imaging parameters and cloudlet extraction are underspecified.
- Rediscovery candidate: no, Imaging and TP merge details are missing and key results depend on assumptions and visual model comparison.

## Links

- Method: Pety10 (GILDAS zero-spacing visibility creation)
- Method: Irons12 (Spiral model and mass distribution)
- Method: Zhao09 (Ellipse (tidally stretched cloud) model)
- Companion: Goicoechea18 (Herschel/mid-J CO detection of hot high-velocity gas toward Sgr A*)
- Companion: Moser17 (Earlier ALMA detection of high-velocity clumps)

## Checks

```json
{
 "quotes": 74,
 "quotes_ok": 74,
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
  "facts": 82,
  "stated": 53,
  "rate": 0.646
 },
 "evidence_ok": true
}
```
