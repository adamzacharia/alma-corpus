# The extended molecular envelope of the asymptotic giant branch star π<SUP>1</SUP> Gruis as seen by ALMA. II. The spiral-outflow observed at high-angular resolution

`2020A&A...633A..13D` | Astronomy and Astrophysics 2020 | first author: Doan, L. | arXiv: 1911.10756 | DOI: 10.1051/0004-6361/201935245

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: evolved_stars
- Question: What are the morphology and kinematics of the circumstellar envelope of the AGB star pi1 Gru at high angular resolution, and what do they imply about an undetected close companion and a mass-loss eruption?  
  > "The improved spatial resolution allows for the investigation of the complex circumstellar morphology and the search for imprints on the CSE of the third component." (abstract)
- Target **pi1 Gruis**: coordinates _not stated_; z/distance 163 pc  
  > "at a distance of 163 pc (cite: vanL07)" (4.1 The morphology interpretation); distance from van Leeuwen 2007  
  > "at a distance of 163 pc (cite: vanL07)" (4.1 The morphology interpretation)

## Data provenance

- ALMA projects: 2012.1.00524.S
- bands: _not stated_
- frequencies and spectral setup: four 2 GHz spectral windows centred on 331, 333, 343 and 345 GHz  
  > "The observations were done with four spectral windows that have a width of 2 GHz each, centered on 331, 333, 343, and 345 GHz." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: ACA (7-m), 12-m main array and total power  
  > "We have observed $\pi^{1}$ Gruis using both the compact array, ACA, and the 12-m main array." (2 Observations and data reduction)
- configurations: _not stated_
- baselines: ACA 11-49 m; 12-m 15-438 m and 15-348 m  
  > "| ALMA 12-m |     7.06     |    31     |  15-438  |" (Table 1)
- angular resolution: 0.84'' x 0.56'' at PA -81 deg  
  > "The synthesized beam size is $0.84\ensuremath{''}\times0.56\ensuremath{''}$ at a position angle (PA) of $-$81$^{\circ}$." (2 Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: rms 0.022 Jy/beam (2 km/s channels, -40 to 16 km/s); 0.006 and 0.005 Jy/beam (4 km/s channels outside)  
  > "| $\left[ -40, 16 \right]$ | 2 | 0.022 |" (Table 2)
- time on source: ACA 23.7 min; 12-m 7.06 min per configuration; TP 67.1 min  
  > "| ALMA-ACA  |     23.7     |     7     |  11-49   |" (Table 1)
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- Other facility **APEX**: 2005 flux used as a check on recovered flux  
  > "The combined data recovers $\sim$90% of the flux observed by APEX in 2005." (2 Observations and data reduction)
- External data: Gas temperature law T(r)=190 (r/1e15 cm)^-0.85, density and velocity laws, inclination 40 deg and best-fit parameters from the Paper I model  
  > "The gas temperature distribution is adapted from Paper I, $T(r) = 190 (r/ 10^{15} \rm{cm})^{-0.85}$ and used for the whole structure." (4.1 Density and temperature distribution) [from Doan et al. 2017 (cite: doan17) (Paper I)]
- External data: CO abundance 6.5e-4  
  > "The CO abundance relative to H$_{2}$ is 6.5$\times10^{-4}$ (cite: knap99)." (4.1 Radiative transfer) [from (cite: knap99)]
- External data: Collisional rates, energy levels, transition probabilities  
  > "The collisional rate coefficients, energy levels and radiative transition probabilities, are taken from (cite: scho05)." (4.1 Radiative transfer) [from (cite: scho05)]
- External data: Excitation temperature 15 K  
  > "The excitation temperature $T_{ex} = 15$ K, which is also about the average kinetic temperature for a major part of the CSE, is adopted from (cite: buja97)." (4.2 The mass-loss eruption) [from (cite: buja97)]
- Simulation/model as data: SPH simulation with ESI-GADGET: 1 Msun AGB star plus 0.6 Msun companion, separation 10 AU, e=0.0 and 0.8, mdot 2e-6 Msun/yr, wind 11 km/s  
  > "The binary separation is 10 AU and the AGB star has mass-loss rate of $2 \times 10^{-6}$ M$_{\odot}$yr$^{-1}$, and wind velocity of 11 km s$^{-1}$" (4.3 Eccentric orbit of the undetected companion)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: CASA 4.3.0  
  > "The data reduction was done using the Common Astronomy Software Application (CASA 4.3.0)." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CLEAN with iterative decreasing threshold  
  > "using the *CLEAN* package using an iterative procedure with a decreasing threshold parameter" (2 Observations and data reduction)
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
- array combination: ACA and 12-m calibrated and combined, then combined with TP; ACA/12-m weight ratio scaled to 0.18  
  > "The ratio between the ACA (7-m) array and the main (12-m) array weights was scaled to be 0.18." (2 Observations and data reduction)
- smoothing: 0.5 km/s channels binned to 2 and 4 km/s  
  > "The initial spectral resolution of 0.5 km s$^{-1}$ has been binned to 2 and 4 km s$^{-1}$ for the low- and high-velocity channels" (2 Observations and data reduction)
- final beam: 0.84'' x 0.56'', PA -81 deg  
  > "The synthesized beam size is $0.84\ensuremath{''}\times0.56\ensuremath{''}$ at a position angle (PA) of $-$81$^{\circ}$." (2 Observations and data reduction)
- final rms: _not stated_

### Inherited from earlier work

- Low-angular-resolution data already discussed in Paper I  
  > "The low-angular resolution data used in this study has already been discussed in Paper I." (1 Introduction) [from Paper I (cite: doan17)]
- Inclination of 40 deg  
  > "The inclination angle between the line of sight and the equatorial plane is 40$^{\circ}$ as was determined in Paper I." (4.1 Morphology) [from Paper I (cite: doan17)]
- Mass estimate method  
  > "We applied the equation and procedure that was described by (cite: olof94), and also used by (cite: chiu06) for the $J$=2-1 emission" (4.2 The mass-loss eruption) [from (cite: olof94); (cite: chiu06)]

### Not stated but needed to reproduce (our reading)

- CLEAN parameters: weighting, robust, cell size, image size, masks, thresholds
- Calibrators and calibration approach (manual or pipeline)
- Observing dates and execution blocks
- Line-free channels and continuum subtraction
- TP combination method (feather or other)
- Exact SHAPE/LIME model files and parameters (arm width, flaring, R1, opening angle details)
- SIMALMA settings
- Spiral line fit parameters
- SPH setup details

## Analysis recipe

1. **Combine and image data**: Calibrate and combine ACA and 12-m, add TP, image with CLEAN  
  > "The interferometric data was first calibrated and combined separately, then combined with the TP data." (2 Observations and data reduction)
   - software: CASA
   - parameter: ACA/12-m weight ratio 0.18  
  > "The ratio between the ACA (7-m) array and the main (12-m) array weights was scaled to be 0.18." (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: Recovers ~90% of APEX flux  
  > "The combined data recovers $\sim$90% of the flux observed by APEX in 2005." (2 Observations and data reduction)
2. **Characterise spiral geometry from the data**: Collapse max-intensity image over -4 to -20 km/s, fit peak points in radius-angle plane with a line; PV diagrams with 1-pixel slits  
  > "The peak intensity points of the region $\pm$2$''$ from a radius of 5$''$ have been fitted with a line in the radial distance-position angle plane" (3.1 Images)
   - software: CASA
   - fitting: Linear fit of r versus theta  
  > "The peak intensity points of the region $\pm$2$''$ from a radius of 5$''$ have been fitted with a line in the radial distance-position angle plane" (3.1 Images)
   - validation: _not stated_
3. **Build and run 3D radiative transfer model**: SHAPE morphology with spiral R~theta^n and bipolar bubbles; LIME non-LTE; SIMALMA to simulate observations  
  > "The radiative transfer was performed using the non-LTE, non-local 3D radiative transfer code LIME (cite: brin10)." (4.1 Radiative transfer)
   - software: SHAPE, LIME, CASA simalma
   - parameter: A_s=1.8e8 cm-3, B=1e7 cm-3, spiral velocity 8+5r/R1, bipolar outflow 60 km/s, opening angle ~40 deg, n=2  
  > "$A_{s} = 1.8\times10^{8}$ cm$^{-3}$ and $B = 1\times10^{7}$ cm$^{-3}$, respectively." (4.2 Modelling results)
   - parameter: domain radius 2700 AU, 100000 grid points, levels up to J=41  
  > "The computational domain is a volume with radius of 2700 AU gridded in 100000 points." (4.1 Radiative transfer)
   - assumption: H2 ortho-to-para 3, CO/H2 6.5e-4, equatorial plane reflection symmetry  
  > "considers an ortho-to-para ratio of 3" (4.1 Radiative transfer)
   - fitting: No formal fit; best model chosen by eye  
  > "the model that could best reproduce the different features and structures seen in the channel maps and PV-diagrams was chosen by eye, but no formal fitting procedure has been performed." (4.2 Modelling results)
   - validation: Compare model PV diagrams and channel maps to observations  
  > "It generally matches the observational PV diagram except for the outermost arc in the blue-shifted part" (4.2 Modelling results)
4. **Estimate lower limit of density contrast**: Vary A_i with A_s fixed, simulate observations, compare rms in inter-arm box to max in arm box (>90% means barely discernible)  
  > "If the root-mean-square intensity within the red rectangle is close to (\>90%) or higher than the maximum pixel intensity within the green rectangle" (Appendix A)
   - software: CASA, LIME, CASA IRING
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate eruption mass and mass-loss rate**: Optically thin CO mass formula of Olofsson & Nyman, integrated intensity over high-velocity range times 2  
  > "The integrated intensity $I$ was first calculated over the high velocity range of the bipolar outflow, and then multiplied by a factor of 2." (4.2 The mass-loss eruption)
   - parameter: D=160 pc, f=6.5e-4, eta=0.76, Tex=15 K  
  > "the distance $D = 160$ pc, the effective area $A_{e}=\eta A_{g}$ with the aperture efficiency $\eta = 0.76$" (4.2 The mass-loss eruption)
   - assumption: Optically thin CO 3-2, thermalised  
  > "by assuming that the $J$=3-2 CO line emission is optically thin" (4.2 The mass-loss eruption)
   - fitting: _not stated_
   - validation: Optical depth about unity, so mass is a lower limit  
  > "the actual mass is probably underestimated and would be somewhat higher than the given value." (4.2 The mass-loss eruption)
6. **Compare spiral branching with SPH models**: ESI-GADGET SPH simulations with e=0 and 0.8, post-processed with LIME  
  > "The simulation uses the Evolved Stellar Interactions with GADGET in 3D that is a modified version of the GADGET2 code (cite: spri05; rams17)." (4.3 Eccentric orbit of the undetected companion)
   - software: GADGET2, LIME
   - fitting: _not stated_
   - validation: Visual comparison of branching feature  
  > "The branching feature seen in the observations is produced with an eccentric orbit ($e$=0.8) model." (4.3 Eccentric orbit of the undetected companion)

## Software

- **CASA** 4.3.0: data reduction, imaging, SIMALMA  
  > "The data reduction was done using the Common Astronomy Software Application (CASA 4.3.0)." (2 Observations and data reduction)
- **SHAPE** : 3D morpho-kinematical model  
  > "using the 3D modelling tool for complex structures, SHAPE (cite: stefetal11; santetal15)" (4.1 Radiative transfer)
- **LIME** : non-LTE 3D radiative transfer  
  > "the non-LTE, non-local 3D radiative transfer code LIME (cite: brin10)" (4.1 Radiative transfer)
- **GADGET2 (ESI-GADGET)** : SPH simulation of eccentric binary  
  > "a modified version of the GADGET2 code" (4.3 Eccentric orbit of the undetected companion)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Largest spiral arm separation | 5.5 | not stated | arcsec | 3 | The largest separation between two successive windings is $\sim$5.5$''$  measured at the outermost windings. |
| Orbital period | 330 | not stated | yr | 0 | the corresponding orbital period, $T=\Delta r/v$, is 330 yrs. |
| Companion separation | about 70 | not stated | AU | 0 | the mean separation between the AGB star and the companion shaping the envelope should be about 70 AU. |
| Minimum density contrast | 2 | not stated | dimensionless | 4 | $\beta_{min} \simeq 2$ |
| Eruption gas mass | 4.3e-5 | not stated | Msun | 5 | The estimated mass, $M$, is approximately $4.3 \times 10^{-5}$ M$_{\odot}$. |
| Eruption mass-loss rate | 3.3e-6 | not stated | Msun/yr | 5 | The corresponding mass-loss rate is $3.3 \times 10^{-6}$ M$_{\odot}$yr$^{-1}$ |
| Eruption time and duration | 100 yr ago, lasted ~13 yr | not stated | yr | 0 | we estimate that the eruption occurred 100 years ago, and that the increased mass-loss rate lasted for approximately 13 years. |
| Maximum bipolar outflow velocity | 60 | not stated | km/s | 0 | the highest estimated velocity of the fast outflow is about 60 km s$^{-1}$ relative to the systemic velocity. |

## Qualitative findings

- Spiral with branching windings in the equatorial torus plus a fast bipolar outflow perpendicular to it  
  > "both a faster bipolar outflow and a spiral pattern along the orbital plane can be seen in the gas envelope." (abstract)

## Claim tuples

- H: A close undetected companion shapes the spiral | E: Measure spiral arm spacing in ALMA CO 3-2 and model with 3D radiative transfer | R: Arm spacing 5.5'' gives period ~330 yr and separation ~70 AU | F: A closer undetected companion, not the known 400 AU one, shapes the envelope | **supported**
- H: The bipolar outflow arises from a recent mass-loss eruption | E: Kinematic model of thin bubbles and optically thin mass estimate | R: Mass 4.3e-5 Msun, rate 3.3e-6 Msun/yr, at least 5 times the earlier rate | F: Eruption ~100 yr ago lasting ~13 yr | **supported**
- H: An eccentric orbit explains the branching windings | E: SPH models with e=0 and 0.8 | R: Branching appears only for e=0.8 | F: Eccentric orbit is a good explanation | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Gravity of the known 400 AU companion cannot shape the envelope  
  > "We find that the gravitation of the known companion is not strong enough to shape the envelope." (5 Summary)
- How they decided it was enough: _not stated_
- Limitation (authors): Model not formally fit; chosen by eye  
  > "no formal fitting procedure has been performed" (4.2 Modelling results)
- Limitation (authors): Mass-loss rate is a lower limit as optical depth is about unity  
  > "the estimated mass-loss rate should be considered as a lower limit." (4.2 The mass-loss eruption)
- Caveat (inferred, ours): Period from arm spacing assumes spacing/expansion velocity equals orbital period in a projected image
- Caveat (inferred, ours): No uncertainties on derived quantities
- Caveat (inferred, ours): Eyeball model selection is not reproducible
- Caveat (inferred, ours): SPH models use a different separation (10 AU) than the 70 AU inferred

## Reproducibility

- Data public (paper): Project code cited in acknowledgements; public status not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2012.1.00524.S." (Acknowledgements)
- Products in archive: _not stated_
- Missing: CLEAN parameters
- Missing: SHAPE model files
- Missing: Many Paper I parameters needed
- Data volume (inferred): tens of GB (ACA, 12-m and TP raw data)
- Score (inferred): 3/5, Data identified and the model laws given, but imaging parameters and model details are missing and the model was tuned by eye.
- Rediscovery candidate: no, Imaging recipe is incomplete and the main results come from by-eye modelling.

## Links

- Method: Olofsson & Nyman (cite: olof94) (mass estimate equation)
- Method: Brinch & Hogerheijde 2010 (cite: brin10) (LIME code)
- Companion: Doan et al. 2017 (cite: doan17) (Paper I, low-resolution ACA analysis and model)
- Related: ALMA project on binary AGB systems: R Aqr, Mira, W Aql, pi1 Gru

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
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 84,
  "stated": 50,
  "rate": 0.595
 },
 "evidence_ok": true
}
```
