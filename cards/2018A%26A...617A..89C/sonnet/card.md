# Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). I. Indication for a centrifugal barrier in the environment of a single high-mass envelope

`2018A&A...617A..89C` | Astronomy and Astrophysics 2018 | first author: Csengeri, T. | arXiv: 1804.06482 | DOI: 10.1051/0004-6361/201832753

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: star_formation, astrochemistry
- Question: What is the structure and kinematics of a single high-mass protostellar envelope, and do the CH3OH and HC3N emission indicate a centrifugal barrier and accretion disk?  
  > "To assess the physical conditions of high-mass protostars in their main accretion phase, here we present a case study of a young massive clump selected from the ATLASGAL survey" (abstract)
- Target **G328.2551-0.5321**: coordinates phase center (J2000) 15h58m00.05s, -53d57m57.8s; continuum peak 15h57m59.802s, -53d58m00.51s  
  > "the phase center was (α, δ) J2000 = (15 h 58 m 00.05 s, −53 ◦ 57 ′ 57. ′′ 8)" (2. Observations and data reduction); "our target is embedded in the MSXDC G328.25-00.51 dark cloud (Csengeri et al. 2017a)" (2. Observations and data reduction); z/distance 2.5 (+0.5/-0.7?) kpc (text garbled: 2.5 +1.0/-0.75 kpc)  
  > "the phase center was (α, δ) J2000 = (15 h 58 m 00.05 s, −53 ◦ 57 ′ 57. ′′ 8)" (2. Observations and data reduction); "our target is embedded in the MSXDC G328.25-00.51 dark cloud (Csengeri et al. 2017a)" (2. Observations and data reduction); distance from _not stated_

## Data provenance

- ALMA projects: 2013.1.00960.S
- bands: Band 7  
  > "the signal was correlated in lowresolution wide-band mode in Band 7, yielding 4 × 1.75 GHz effective bandwidth" (2. Observations and data reduction)
- frequencies and spectral setup: 4 basebands centred on 347.331, 345.796, 337.061, 333.900 GHz; 0.977 MHz (~0.9 km/s) resolution  
  > "The four basebands were centred on 347.331, 345.796, 337.061, and 333.900GHz, respectively." (2. Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ALMA 12 m (34-35 antennas) and 7 m (11 antennas)  
  > "We used 11 of the 7 m antennas on the 2014 July 8 and 16, as well as 34 and 35 of the 12 m antennas on 2015 May 3, and 2015 September 1, respectively." (2. Observations and data reduction)
- configurations: _not stated_
- baselines: 12 m: 15 m (17 kλ) to 1574 m (1809 kλ)  
  > "the baseline range is 15 m (17 kλ) to 1574 m (1809kλ)" (2. Observations and data reduction)
- angular resolution: continuum 0.17'' (7m+12m, robust -2); lines 0.26'' (robust 0.5)  
  > "with a geometric mean of 0.17 ′′ for the continuum maps" (2. Observations and data reduction)
- max recoverable scale: ~7'' for 12 m array  
  > "the largest angular scales of ∼ 7 ′′, where the sensitivity of our 12 m array observations drops" (2. Observations and data reduction)
- sensitivity: continuum rms ~1.3 mJy/beam  
  > "We measure an rms noise level in the final continuum image of ∼ 1.3 mJy/beam" (2. Observations and data reduction)
- time on source: 7.4 minutes (12 m)  
  > "The total time on source was 7.4 minutes" (2. Observations and data reduction)
- observing dates: 7 m: 2014 July 8 and 16; 12 m: 2015 May 3 and September 1  
  > "on the 2014 July 8 and 16, as well as 34 and 35 of the 12 m antennas on 2015 May 3, and 2015 September 1" (2. Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: CH3OH-E vt=1 3_0-2_1 (334.42656 GHz)
- Line: SO2 8_2,6-7_1,7 (334.67335 GHz)
- Line: HC3N v7=1e 38-37 (346.45573 GHz)
- Line: CO 3-2 (345.79599 GHz)
- Other facility **ATLASGAL/APEX**: 870 µm single-dish clump flux  
  > "the total flux density from the single dish observations from ATLASGAL" (3.1.3 The mass reservoir for accretion)
- Other facility **Herschel/Hi-GAL**: far-IR photometry for SED  
  > "we perform aperture photometry on the PACS 70 µm, and 160 µm maps" (Appendix A)
- External data: ALMA 7 m array MDC parameters (Table 1)  
  > "The listed parameters are from the ALMA 7 m array from Csengeri et al. (2017b)." (Table 1) [from Csengeri et al. 2017b]
- External data: Clump parameters from ATLASGAL catalog  
  > "The corresponding parameters are extracted from the catalog of Csengeri et al. (2014) based on the ATLASGAL data." (Table 1) [from Csengeri et al. (2014)]
- External data: Protostellar evolution tracks to estimate mass from luminosity  
  > "we use evolutionary diagrams (Fig. 10) based on protostellar evolution models (Hosokawa & Omukai 2009)" (4.1 The most massive envelope of a young protostar) [from Hosokawa & Omukai 2009; Hosokawa et al. 2010]

## Processing

### Calibration

- pipeline or manual: CASA pipeline  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34044)." (2. Observations and data reduction)
- casa version: CASA 4.3.1  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34044)." (2. Observations and data reduction)
- pipeline version: 34044  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34044)." (2. Observations and data reduction)
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: _not stated_
- deconvolver: CLEAN  
  > "used the CLEAN algorithm for deconvolution" (2. Observations and data reduction)
- weighting robust: robust = -2 for continuum; robust = 0.5 for line cubes  
  > "we used Briggs weighting with a robust parameter of −2, corresponding to uniform weighting" (2. Observations and data reduction); "we used here a robust parameter of 0.5 for the imaging" (2. Observations and data reduction)
- uv taper: SiO (8-7) cube tapered; beam 0.69''x0.59''  
  > "For the SiO (8–7) datacube we lowered the weight on the longest baselines with a tapering function to gain in signal to noise." (2. Observations and data reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from emission-free channels around each line  
  > "we subtracted the continuum determined in emission free channels around the selected line" (2. Observations and data reduction)
- line free channels: channels with line emission above 3σ rms excluded, iteratively  
  > "We created line-free continuum maps by excluding channels with line emission above 3σ rms per channel" (2. Observations and data reduction)
- primary beam correction: final continuum rms measured on image corrected for primary beam attenuation  
  > "on the image corrected for primary beam attenuation" (2. Observations and data reduction)
- array combination: 12 m + 7 m joint deconvolution for continuum and CO(3-2)  
  > "we therefore combine the 12 m array data with the data taken in the same setup with the 7 m array" (2. Observations and data reduction)
- smoothing: _not stated_
- final beam: continuum 0.23x0.12'' PA 86 deg (7m+12m)  
  > "The resulting beam is 0.23 × 0.12 ′′ with 86 ◦ position angle" (2. Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- 7 m array observations and MDC properties  
  > "The 7 m array observations are discussed in detail in Csengeri et al. (2017b)." (2. Observations and data reduction) [from Csengeri et al. (2017b)]
- Dust opacity and mass equation for MDC mass  
  > "We used Eq. 2 from Csengeri et al. (2017a) with the same parameters for the dust" (3.1.3 The mass reservoir for accretion) [from Csengeri et al. (2017a)]
- vlsr of dense gas  
  > "We adopt the v lsr of the dense gas seen on the clump/core scale used in Csengeri et al. (2017a)." (3.2.1 Torsionally excited methanol) [from Csengeri et al. (2017a)]
- Toy model for pv diagrams  
  > "a simple toy model adapted from Ohashi et al. (1997)" (4.3 Indirect evidence for a Keplerian disk) [from Ohashi et al. (1997)]

### Not stated but needed to reproduce (our reading)

- Line-free channel ranges used for continuum
- Clean threshold, masks, cell and image size
- Self-calibration use
- Exact distance uncertainties and source
- Details of uv-domain fit functions and parameters
- Rotational diagram partition function and line fit details
- Model grid parameters of toy pv model beyond those given
- Flux calibrators and flux scale uncertainty

## Analysis recipe

1. **Image continuum and line cubes**: CASA CLEAN imaging, 12 m only and 12 m+7 m joint deconvolution; continuum from line-free channels  
  > "we used Briggs weighting with a robust parameter of −2" (2. Observations and data reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: _not stated_
2. **Fit continuum envelope and compact component**: 2D Gaussian fits in image plane; envelope removed to reveal residual compact source; visibility fits (power law plus disk) in uv-domain  
  > "we use here a 2D Gaussian fit in the image plane as a first approach." (3.1.1); "we also perform a fitting procedure in the uvdomain." (3.1.2)
   - fitting: _not stated_
   - validation: compare image-plane and uv-plane flux and size  
  > "our analysis in the image plane attributes a somewhat larger flux density to this compact component, but finds a similar spatial extent." (3.1.2)
3. **Derive bolometric luminosity, dust temperature and MDC mass**: SED from mid-IR to 870 µm; two-component greybody fit 70-870 µm; mass from dust emission  
  > "we use a two component greybody to model the SED" (Appendix A)
   - assumption: κ345GHz = 0.0185 g cm-2 (incl. gas-to-dust 100), β = 2, Td = 22 K for MDC  
  > "We use κ 345 GHz = 0.0185g cm [−][2] and an emissivity index of β = 2" (Appendix A)
   - fitting: two-component greybody  
  > "we use a two component greybody to model the SED, which reveals the temperature corresponding to the cold gas component dominating the bulk of the emission" (Appendix A)
   - validation: Lbol compared with Dunham et al. 2008 70 µm relation: 1.2e4 Lsun  
  > "and obtain 1.2 × 10 [4] L bol" (Appendix A)
4. **Estimate protostellar mass**: Hosokawa protostellar evolution tracks with accretion rates 1-30e-3 Msun/yr at Lbol  
  > "we find a central mass around 11 M ⊙ for L bol = 1.3 × 10 [4] L ⊙" (4.1)
   - fitting: _not stated_
   - validation: _not stated_
5. **Methanol physical conditions**: rotational diagram of CH3OH and 13CH3OH lines (isotopic ratio 60), and LTE grid modelling of full spectrum  
  > "We include the 13 CH 3 OH lines with an isotopic ratio of 60" (3.3.1); "We created a grid of models for the CH 3 OH column density" (3.3.2)
   - software: WEEDs
   - parameter: N 1e17-1e20 cm-2, Tkin 50-300 K, 25 linear steps each; source size fixed 0.4''  
  > "We sampled by 25 linearly spaced values both parameter ranges, and then visually assessed the results." (3.3.2)
   - assumption: LTE; optically thin for lines used in rotational diagram  
  > "For the rest of the transitions we assume optically thin emission." (3.3.1)
   - fitting: visual assessment of grid  
  > "We sampled by 25 linearly spaced values both parameter ranges, and then visually assessed the results." (3.3.2. LTE modelling with WEEDs)
   - validation: consistency between rotational diagram and LTE modelling  
  > "our results are consistent with the estimates of column density and rotational temperature obtained from the rotational diagram analysis" (3.3.2)
6. **Outflow dynamical age**: projected SiO bow-shock distance and CO line-wing velocity, corrected for inclination 56 deg  
  > "we obtain a dynamical age estimate of t dyn ∼ 3.5 × 10 [3] yr for the protostar" (3.4.1)
   - assumption: inclination from envelope axis ratio assuming circular envelope  
  > "This is obtained from the axis ratio of the measured envelope size from the dust emission assuming that it has a circular morphology" (3.4.1)
   - fitting: _not stated_
   - validation: inclination range 15-75 deg gives 6.3e2-8.8e3 yr  
  > "An inclination angle range between 15 [◦] and 75 [◦] would result in t dyn = 6.3× 10 [2] − 8.8× 10 [3] yr." (3.4.1 (footnote 7))
7. **Toy kinematic models and specific angular momentum**: pv-diagram models of ring (vrot~r^-1) and Keplerian disk, 15 Msun; Keplerian velocity curves; j/m = R×vrot  
  > "a central protostellar mass of 15 M ⊙ (see Sect 4.1)" (4.3)
   - parameter: grid 2x2500 au, 0.7 km/s velocity resolution, n∝r^-1.5, ring 300-900 au, vrot=4.5 km/s at 300 au; Keplerian disk up to 600 au  
  > "We use an x,y grid size of 2 × 2500 au, and a velocity axis with 0.7 km s [−][1] resolution" (4.3)
   - fitting: _not stated_
   - validation: visual comparison with observed moment 0 / pv  
  > "The observed spots of CH 3 OH corresponding to the highest column densities are reasonably well reproduced with these models" (4.3. Indirect evidence for a Keplerian disk)

## Software

- **CASA** 4.3.1: calibration (pipeline) and imaging  
  > "The data have been calibrated in CASA 4.3.1 with the pipeline (version 34044)." (2. Observations and data reduction)
- **WEEDs** : LTE modelling of the full spectrum  
  > "we modelled the entire spectrum using the WEEDs package (Maret et al. 2011) assuming LTE conditions" (3.3.2)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Bolometric luminosity | 1.3e4 | not stated | Lsun | 3 | The source exhibits a bolometric luminosity of 1.3 × 10 [4] L ⊙ |
| Protostellar mass | 11-16 | not stated | Msun | 4 | lies in the range between 11 and 16 M ⊙ |
| MDC mass | 120 | not stated | Msun | 3 | Adopting therefore, T d =22 K for the MDC we obtain M MDC = 120 M ⊙ |
| Inner envelope FWHM | 0.96x0.56 at PA 74 deg | not stated | arcsec | 2 | gives a full-width at half-maximum (FWHM) of 0.96 ′′ ×0.56 ′′ with a position angle of 74 ◦ |
| Inner envelope radius R90% | 1500 | not stated | au | 2 | This gives a radius, R env 90% , of 0.59 ′′ corresponding to 1500 au. |
| Compact disk component flux density (uv fit) | 43 | not stated | mJy | 2 | consistent with a disk component with a flux density of 43 mJy, and a 0.2 ′′ major axis FWHM |
| Dust cold/warm temperature | 22 / 48 | not stated | K | 3 | We obtain a cold gas component at 22 K, and a warm gas component at 48 K |
| CH3OH N and Tkin (LTE grid) | N=1.2-2e19 cm-2; Tkin 160-200 K | not stated | cm-2; K | 5 | Our results give column densities on the order of 1.2– 2×10 [19] cm [−][2], and a kinetic temperature around 160–200K for the two positions. |
| Rotational diagram Trot and N | Trot=160-175 K; N~8e18 cm-2 | ~10% line fit errors | K; cm-2 | 5 | T rot = 160 − 175 K, and N(CH 3 OH)=∼ 8 × 10 [18] cm [−][2] |
| Outflow dynamical age | 3.5e3 | range 6.3e2-8.8e3 for i 15-75 deg | yr | 6 | we obtain a dynamical age estimate of t dyn ∼ 3.5 × 10 [3] yr for the protostar |
| Specific angular momentum | 4.5e21 | 52% | cm2 s-1 | 7 | j/m = R × v rot = 4.5 × 10 [21] cm [2] s [−][1] |
| Disk radius range | 255-817 | not stated | au | 7 | giving a disk radius between 255 and 817 au |

## Qualitative findings

- Torsionally excited CH3OH shows two spots offset ±4.5 km/s from vlsr, offset from the continuum peak; HC3N v7=1 is compact  
  > "This shows two bright peaks of emission spatially offset from the dust continuum peak" (abstract)

## Claim tuples

- H: The CH3OH vt=1 peaks trace accretion shocks at a centrifugal barrier around a disk | E: Map vt=1 and vt=0 lines, rotational diagram and LTE modelling, pv diagrams, toy ring/Keplerian models | R: Velocity offsets ±4.5 km/s match Keplerian velocity for ~15 Msun at 300-800 au; T~160-200 K, N~1-2e19 | F: CH3OH peaks trace shocks at the centrifugal barrier; indirect evidence for disk | **partially**
- H: The target is a single high-mass protostellar envelope | E: Continuum at 0.17'' | R: single source to ~400 au with compact component and azimuthal elongations | F: Single massive envelope, ~120 Msun | **supported**
- H: Specific angular momentum is larger in high-mass than low-mass protostars | E: Compare j/m with literature | R: j/m=4.5e21 cm2/s | F: several times larger; consistent with global collapse | **partially**
- H: Vibrationally excited HC3N is a tracer of compact accretion disks | E: Compare HC3N v7=1 with CH3OH and dust | R: compact emission peaked on compact dust component | F: proposed potential tracer | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: 7 m data combined because continuum and CO are more extended than 12 m largest scales  
  > "The interferometric filtering has, however, a significant impact on both the continuum and the CO (3–2) emission" (2. Observations and data reduction)
- Alternative: Optical depth effects and outflow shocks rejected as origin of CH3OH peaks  
  > "This leads us to conclude that the two prominent spots traced by the � t = 1 state CH 3 OH line cannot be a result of a large optical depth" (3.2.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Direct evidence for disk hindered by angular and spectral resolution; parameters uncertain within a factor of few  
  > "Direct evidence for the presence of the disk is hindered by the angular and spectral resolution of our dataset" (4.3)
- Caveat (inferred, ours): Disk interpretation is indirect; only a marginally resolved source
- Caveat (inferred, ours): Distance uncertainty large, affecting mass and sizes
- Caveat (inferred, ours): Toy models without inclination correction and no formal fit
- Caveat (inferred, ours): Single source, LTE assumptions

## Reproducibility

- Data public (paper): ALMA project 2013.1.00960.S acknowledged  
  > "This paper makes use of the ALMA data: ADS/JAO.ALMA 2013.1.00960.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters (cell, size, masks, thresholds)
- Missing: Line-free channels
- Missing: uv-fit functional forms
- Missing: Toy model code
- Data volume (inferred): ~50-100 GB raw (12 m and 7 m, Band 7)
- Score (inferred): 5/5, Public data and many numbers stated, but imaging details and toy model/fit specifics missing.
- Rediscovery candidate: no, Several key results depend on unstated parameters and non-fitted toy models.

## Links

- Method: Maret et al. 2011 (WEEDs) (LTE modelling)
- Method: Ohashi et al. 1997 (toy pv model)
- Companion: Csengeri et al. 2017b (7 m array observations of this source)
- Companion: Csengeri et al. 2017a (ATLASGAL clump/core properties)
- Related: SPARKS
- Related: ATLASGAL

## Checks

```json
{
 "quotes": 86,
 "quotes_ok": 86,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 1,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 12,
 "numeric_problems": 0,
 "fill": {
  "facts": 83,
  "stated": 58,
  "rate": 0.699
 },
 "evidence_ok": true
}
```
