# The circumstellar envelope around the S-type AGB star W Aql. Effects of an eccentric binary orbit

`2017A&A...605A.126R` | Astronomy and Astrophysics 2017 | first author: Ramstedt, S. | arXiv: 1709.07327 | DOI: 10.1051/0004-6361/201730934

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the wind properties (average mass-loss rate) of W Aql and how has the known companion shaped the CSE, compared with 3D SPH binary interaction models with e=0.2 and 0.6?  
  > "The aim of this paper is to investigate the wind properties of the AGB star and to analyse how the known companion has shaped the CSE." (abstract)
- Target **W Aql**: coordinates 19:15:23.379 -07:02:50.38 (J2000.0)  
  > "W Aql has a known companion at a separation of $a$ = 0.46$''$ (cite: ramsetal11) or $\approx$180 AU, and the distance to the system is estimated to 395 pc (cite: danietal14)." (Introduction); "| W Aql  | 19:15:23.379 | -07:02:50.38 | 29$\pm$3 mJy |" (Table 1); z/distance 395 pc  
  > "W Aql has a known companion at a separation of $a$ = 0.46$''$ (cite: ramsetal11) or $\approx$180 AU, and the distance to the system is estimated to 395 pc (cite: danietal14)." (Introduction); "| W Aql  | 19:15:23.379 | -07:02:50.38 | 29$\pm$3 mJy |" (Table 1); distance from Danilovich et al. 2014 (cite: danietal14)  
  > "W Aql has a known companion at a separation of $a$ = 0.46$''$ (cite: ramsetal11) or $\approx$180 AU, and the distance to the system is estimated to 395 pc (cite: danietal14)." (Introduction); "| W Aql  | 19:15:23.379 | -07:02:50.38 | 29$\pm$3 mJy |" (Table 1)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: four ~2 GHz spectral windows centred on 331, 333, 343, 345 GHz covering 12CO and 13CO J=3-2  
  > "The correlator was set up with four spectral windows $\sim$2 GHz in width centred on 331, 333, 343, and 345 GHz to cover the $^{12}$CO and $^{13}$CO $J$ = 3 $\rightarrow$ 2 lines in the same setting." (2.1 Observations)
- continuum bandwidth: _not stated_
- arrays: 12 m main array (33 and 34 antennas), ACA 7 m (10 antennas), Total Power (3 antennas)  
  > "W Aql was observed with ten Atacama Compact Array (ACA) 7 m antennas on 6 March 2014. It was also observed on 20 March 2014 with 33, and on 14 April 2014 with 34 main array 12 m antennas." (2.1 Observations)
- configurations: _not stated_
- baselines: 15-558 m main array; 9-49 m ACA  
  > "Baseline lengths range from 15 to 558 m for the main array, and from 9 to 49 m for the ACA." (2.1 Observations)
- angular resolution: 0.47''x0.41'', PA 65.3 deg (final images)  
  > "The beam of the final images has a full width at half maximum of 0.47$''$$\times$0.41$''$, and a position angle of 65.3$^{\circ}$." (2.1 Observations)
- max recoverable scale: ~7'' main array, ~12'' ACA  
  > "This results in a maximum recoverable scale of $\sim$7$''$ for the main array and $\sim$12$''$ for the ACA." (2.1 Observations)
- sensitivity: 15 mJy/beam rms in emission-free channels (2 km/s resolution)  
  > "The rms noise level in the emission-free channels reaches 15 mJy/beam." (2.1 Observations)
- time on source: 23 min ACA; 7.25 and 7.3 min 12m; 67 min TP  
  > "The total observing time was 23 mins for the ACA, and 7.25 mins and 7.3 mins for the 12m array on the first and second run, respectively, and 67 mins total time for the TP array." (2.1 Observations)
- observing dates: ACA 6 Mar 2014; 12m 20 Mar and 14 Apr 2014; TP 12 Jun 2015  
  > "Finally, it was observed with three 12 m antennas of the Total Power (TP) array on the 12 June 2015." (2.1 Observations)
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **APEX**: previous 12CO 3-2 single-dish peak intensity ~145 Jy, used to check flux recovery  
  > "Previous $^{12}$CO $J$ = 3 $\rightarrow$ 2 line emission observations with APEX (cite: ramsetal09) measured a peak intensity of $\sim$145 Jy" (2.1 Observations)
- External data: Single-dish CO rotational line model of W Aql (Mdot=4e-6, abundances) used as base 1D model  
  > "The model by (cite: danietal14) is further constrained here by the brightness distribution derived from the CO($J$ = 3$\rightarrow$2) map from ALMA." (3.1 Determining the average mass-loss rate) [from (cite: danietal14)]
- External data: HST/PolCor dust scattered-light image used for comparison  
  > "Figure [5](#polcor) shows the CO emission contours from Fig. [1](#lineandimage) overlayed on the PolCor image." (5.1 Comparison to previous resolved observations of the CSE around W Aql) [from (cite: ramsetal11)]
- Simulation/model as data: 3D ESI-Gadget SPH models of W Aql binary (e=0.2, 0.6), 6e6 particles, gridded to 512^3, post-processed with LIME and the ALMA simulator  
  > "After $\approx$ 11 800 years of evolution, 6$\times 10^6$ particles had been injected." (3.2 Hydrodynamical modelling)

## Processing

### Calibration

- pipeline or manual: standard procedure (details not given)  
  > "Calibration was carried out following standard procedure." (2.1 Observations)
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: Ceres, Titan, J1924-292  
  > "Ceres, Titan, and quasar J1924-292 were used as flux calibrators." (2.1 Observations)
- flux scale uncertainty: _not stated_
- self calibration: not possible; continuum too weak  
  > "the continuum was too weak to be used for self-calibration of the offset mosaic pointings" (2.1 Observations)

### Imaging

- task: _not stated_
- deconvolver: careful iterative multiscale cleaning (details not given)  
  > "without the careful, iterative, multiscale cleaning used when imaging the real data" (4.3 Binary interaction model results)
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: _not stated_
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: continuum from emission-free channels subtracted; spectral resolution averaged to 2 km/s  
  > "Final imaging was done after subtracting the continuum and averaging to reach a spectral resolution of 2 km s$^{-1}$." (2.1 Observations)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: main array + ACA (ACA weight 0.25) combined, then with TP via SD2VIS  
  > "The combined main array+ACA visibilities were finally combined with the TP visibility data using the CASA task SD2VIS" (2.1 Observations)
- smoothing: cube smoothed to 0.6'' with imsmooth for brightness profile  
  > "derived by smoothing the full image cube to a resolution of 0.6$''$ using imsmooth in CASA" (3.1 Determining the average mass-loss rate)
- final beam: 0.47''x0.41'', PA 65.3 deg  
  > "The beam of the final images has a full width at half maximum of 0.47$''$$\times$0.41$''$, and a position angle of 65.3$^{\circ}$." (2.1 Observations)
- final rms: 15 mJy/beam  
  > "The rms noise level in the emission-free channels reaches 15 mJy/beam." (2.1 Observations)

### Inherited from earlier work

- 1D non-LTE CO radiative transfer model of W Aql, assumptions and code  
  > "For a further description on the assumptions made for the W Aql model in particular and the code in general see (cite: danietal14) and (cite: schoolof01), respectively." (3.1 Determining the average mass-loss rate) [from (cite: danietal14); (cite: schoolof01)]
- CO envelope size previously from photodissociation models  
  > "The CO envelope size was previously based on the photodissociation models by (cite: mamoetal88; stanetal95)." (3.1 Determining the average mass-loss rate) [from (cite: mamoetal88; stanetal95)]
- Collisional rates, energy levels and transition probabilities from LAMDA  
  > "Collisional rate coefficients, as well as energy levels and radiative transition probabilities, are taken from (cite: schoetal05)" (3.3 Post-processing radiative transfer) [from (cite: schoetal05)]

### Not stated but needed to reproduce (our reading)

- Pipeline/CASA versions and manual calibration details
- Robust weighting, cell size, image size, clean masks, multiscale scales
- Line-free channels for continuum
- Flux scale uncertainty
- Specific ALMA simulator settings (simobserve/simanalyze parameters)
- Numerical radial profiles and abundance/temperature/velocity law in the 1D model
- How arc separations were measured and the PV slit details beyond 9 pixels

## Analysis recipe

1. **Combine and image ALMA data**: Combine main array and ACA (weight 0.25), image, add TP via SD2VIS, subtract continuum, average to 2 km/s  
  > "The main array data was combined with the ACA data, which was weighted by a factor of 0.25 to account for the lower sensitivity of the 7m antennas, and the combined data was imaged." (2.1 Observations)
   - software: CASA, SD2VIS
   - fitting: _not stated_
   - validation: Peak flux compared with APEX ~145 Jy  
  > "showing that the same amount of flux was recovered by the combined ALMA observations" (2.1 Observations)
2. **Estimate average mass-loss rate via 1D radiative transfer**: Measure brightness distribution of CO(3-2) at 0.6'' beam in four directions, average, and fit model brightness distribution with CO envelope size free  
  > "The corresponding brightness distribution (using the same beam size and radii) is calculated from the radiative transfer modelling results and compared to the observed values until a fit is found" (3.1 Determining the average mass-loss rate)
   - software: CASA imsmooth, Schöier & Olofsson 2001 Monte Carlo code
   - parameter: distance 395 pc; flux error 10%  
  > "The error in the measured line flux is assumed to be 10% with the variation across the different directions taken into account." (3.1 Determining the average mass-loss rate)
   - assumption: spherically symmetric CSE with constant mass-loss rate  
  > "The radiative transfer code assumes a spherically symmetric CSE created by a constant mass-loss rate." (3.1 Determining the average mass-loss rate)
   - fitting: fit by eye/until a fit is found; no sampler stated  
  > "The corresponding brightness distribution (using the same beam size and radii) is calculated from the radiative transfer modelling results and compared to the observed values until a fit is found" (Analysis, Determining the average mass-loss rate)
   - validation: Consistent with earlier single-dish results and photodissociation model size  
  > "This agrees well with previous estimates of the average mass-loss rate during the creation of the CSE around W Aql." (4.1 Wind properties)
3. **Run SPH binary interaction models**: 3D ESI-Gadget SPH with W Aql parameters, e=0.2 and 0.6, gridded to 512^3  
  > "The output from these high-resolution models was then gridded using the SPH cubic spline kernel to a 512$^3$ grid" (3.2 Hydrodynamical modelling)
   - software: 3D ESI-Gadget, GADGET2
   - parameter: M_AGB 2 Msun, M_comp 1 Msun, Mdot 3e-6 Msun/yr, v_inf 16.5 km/s, a=180 AU, Porb 1395 yr  
  > "| $\dot{M}_{\rm AGB}$   | 3$\times10^{-6}\, {\rm M}_{\odot}$ yr$^{-1}$ |" (Table 2)
   - assumption: stars as point masses; companion accretion boundary 1 AU  
  > "the stars are treated as point masses, and two different eccentricities for the binary orbit were assumed" (3.2 Hydrodynamical modelling)
   - fitting: _not stated_
   - validation: _not stated_
4. **Radiative transfer of SPH model and interferometer simulation**: LIME 3D non-LTE CO; image at 0.2'', 1 km/s, 100 channels; pass through ALMA simulator with Cycle 1 configs; simanalyze  
  > "Finally, the uv-coverage of the combined ALMA arrays is taken into account by running this image through the ALMA simulator" (3.3 Post-processing radiative transfer)
   - software: LIME, CASA simanalyze
   - parameter: 100000 grid points, radius 15000 AU, CO/H2 = 6.0e-4, 41 rotational transitions  
  > "A constant CO/H$_{2}$ fractional abundance of 6.0$\times$10$^{-4}$ is assumed for the S-type star." (3.3 Post-processing radiative transfer)
   - assumption: ortho-to-para H2 ratio 3; amorphous silicate dust  
  > "Collisions with H$_{2}$ are included assuming an ortho-to-para ratio of 3." (3.3 Post-processing radiative transfer)
   - fitting: _not stated_
   - validation: Compared model arc separation and contrast to observed PV diagrams  
  > "the contrast between the smooth component and the arcs is very weak (about a factor of 2, in agreement with the $e$=0.2 model)" (Discussion, Comparison to the binary interaction models)
5. **Characterise observed arcs**: Channel maps, central-channel image, PV diagrams along PA 0, 90, 35 deg with 9-pixel slit  
  > "Figure [3](#pv90) shows position–velocity (PV) diagrams generated over a narrow slit (9 pixels) across the north-south and east-west directions" (4.2 Circumstellar morphology)
   - software: CASA
   - fitting: _not stated_
   - validation: Structures beyond ~12'' judged unreliable  
  > "structures beyond $\sim$12$''$ are less reliable, due to the rapidly declining image quality when moving away from the image centre" (4.2 Circumstellar morphology)

## Software

- **CASA** : imaging, imsmooth, simanalyze, SD2VIS  
  > "using imsmooth in CASA" (3.1 Determining the average mass-loss rate)
- **LIME** : 3D non-LTE CO radiative transfer on SPH output  
  > "The non-LTE, non-local 3D radiative transfer code LIME (cite: brinhoge10) is used to calculate the CO level populations" (3.3 Post-processing radiative transfer)
- **3D ESI-Gadget** : SPH binary interaction simulation  
  > "W Aql was modelled using the Evolved Stellar Interactions with GADGET in 3D ($^{\rm{3D}}$ESI-Gadget code)" (3.2 Hydrodynamical modelling)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| average mass-loss rate | 3.0e-6 | not stated | Msun/yr | 2 | $\dot{M}$ = 3.0$\times$10$^{-6}$ M$_{\odot}$ yr$^{-1}$ |
| terminal expansion velocity | 16.5 | not stated | km/s | 2 | reaches the terminal expansion velocity of $v_{\rm{e}}$ = 16.5 km s$^{-1}$ at r $\sim$ 2$\times$10$^{16}$ cm |
| continuum flux density at 338 GHz | 29 | 3 | mJy | 1 | / W Aql  / 19:15:23.379 / -07:02:50.38 / 29$\pm$3 mJy / |
| model arc separation | 10-12 | not stated | arcsec | 4 | the arc separation will be 10–12$''$ |
| observed inner arc separation | 2-3 | not stated | arcsec | 5 | where the arcs are separated by 2-3$''$ |

## Qualitative findings

- CO emission dominated by smooth component with two weak arc patterns; larger pattern likely due to known companion  
  > "The CO($J$ = 3$\rightarrow$2) emission is dominated by a smooth component overlayed with two weak arc patterns with different separations." (abstract)

## Claim tuples

- H: What is the average mass-loss rate of W Aql? | E: 1D radiative transfer constrained by ALMA brightness distribution and single-dish lines | R: Mdot = 3.0e-6 Msun/yr | F: Agrees with previous single-dish results; CO size consistent with photodissociation | **supported**
- H: Does the known companion produce the large arc pattern? | E: SPH+LIME+ALMA simulator for e=0.2, 0.6 compared with observed PV | R: ~10'' arcs in model; weak hint in data with contrast ~2 | F: Likely due to companion, consistent with low eccentricity | **partially**
- H: Origin of the 2-3'' arcs | E: Compared observed arcs with models and known processes | R: ~200 yr timescale, asymmetric, coincident with dust | F: Not explained by any known process of the system | **partially**

## Reasoning

- Why this data: Observe CO around known binary AGB stars to constrain 3D hydrodynamical models  
  > "we have designed a project for ALMA to observe the CO gas distribution and kinematics around known binary AGB stars" (Introduction)
- Why this method: _not stated_
- Alternative: Pulsation/convection and episodic dust-formation stalling rejected as cause of inner arcs  
  > "The pulsation/convection timescale is much shorter than the arc-formation timescale, and therefore is probably not the cause of the arcs at smaller separations." (5.3 Circumstellar gas envelope of W Aql)
- How they decided it was enough: _not stated_
- Limitation (authors): Weak arc contrast and unreliable image beyond ~12'' limit eccentricity constraints  
  > "a deeper and larger image would be necessary in order to draw firm conclusions about the orbit eccentricity of the known companion" (5.2 Comparison to the binary interaction models)
- Caveat (inferred, ours): Mass-loss rate fit has no stated uncertainty or formal fitting
- Caveat (inferred, ours): Arc detection is qualitative and prone to imaging artefacts
- Caveat (inferred, ours): Model orientation unknown; only two eccentricities tested
- Caveat (inferred, ours): Simulated ALMA imaging did not use the same cleaning as the real data

## Reproducibility

- Data public (paper): ALMA project 2012.1.00524.S acknowledged; no explicit public statement  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: Imaging parameters and clean settings
- Missing: Full 1D model input profiles
- Missing: SPH code availability and simulator settings
- Data volume (inferred): ~100 GB (12m+ACA+TP, four spectral windows)
- Score (inferred): 3/5, Data are archival and the models are described, but the imaging and 1D fitting details are sparse.
- Rediscovery candidate: no, Recipe incomplete; key results rely on qualitative arc identification and custom codes.

## Links

- Method: (cite: danietal14) (1D CO model of W Aql)
- Method: (cite: schoolof01) (Monte Carlo radiative transfer code)
- Method: (cite: brinhoge10) (LIME)
- Companion: (cite: ramsetal14); (cite: ramsetal15); (cite: doanetal17) (Other stars in the same ALMA binary AGB project)
- Related: ALMA binary AGB project (R Aqr, o Cet, W Aql, pi1 Gru)

## Checks

```json
{
 "quotes": 66,
 "quotes_ok": 66,
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
  "facts": 77,
  "stated": 52,
  "rate": 0.675
 },
 "evidence_ok": true
}
```
