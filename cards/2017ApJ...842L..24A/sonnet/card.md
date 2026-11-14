# Very Deep inside the SN 1987A Core Ejecta: Molecular Structures Seen in 3D

`2017ApJ...842L..24A` | The Astrophysical Journal Letters 2017 | first author: Abellán, F. J. | arXiv: 1706.04675 | DOI: 10.3847/2041-8213/aa784c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: stellar_physics, astrochemistry
- Question: What is the 3D morphology of CO and SiO emission in the inner ejecta of SN 1987A, and how do clump size scales compare with 3D neutrino-driven explosion models?  
  > "The size scales of the clumpy distribution are compared quantitatively to models, demonstrating how progenitor and explosion physics can be constrained." (abstract)
- Target **SN 1987A**: coordinates _not stated_; z/distance 50 kpc (LMC)  
  > "we converted velocity into angular size on the sky by assuming the distance to the LMC to be 50 kpc." (Observations and data reduction); distance from assumed distance to the LMC  
  > "we converted velocity into angular size on the sky by assuming the distance to the LMC to be 50 kpc." (Observations and data reduction)

## Data provenance

- ALMA projects: 2013.1.00280.S, 2015.1.00631.S
- bands: Band 6 (1.3 mm, 211-275 GHz)  
  > "ALMA observations of SN 1987A at 1.3 mm (Band 6, $211-275$ GHz) were performed in two different epochs" (Observations and data reduction)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: 34 m (25 kλ) to 16,196 m (12,600 kλ), cycles 2+3 combined  
  > "Combining the cycle 2 and 3 data sets results in baselines between 34 m (25 k$\lambda$) and 16,196 m (12,600 k$\lambda$)." (Observations and data reduction)
- angular resolution: cube at 50 mas  
  > "process the interferometric data into a cube with 50 mas angular resolution and 100 km s$^{-1}$ spectral bins" (Observations and data reduction)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: Cycle 2: 2 September 2014; Cycle 3: 1-15 November 2015  
  > "cycle 2 low angular resolution images were made in September 2, 2014 (A001/X10e/X140), and cycle 3 high angular resolution images were obtained from November 1 to 15, 2015" (Observations and data reduction)
- pi or archival as stated: _not stated_
- Line: 12C16O J=2-1 (230.538 GHz)
- Line: 28Si16O J=5-4 (217.105 GHz)
- Line: SiO J=6-5 (260.518 GHz)
- External data: Kinetic temperature ~50 K, collider density and total CO and SiO masses from lower-resolution ALMA data  
  > "From lower angular resolution ALMA observations, the total CO and SiO masses are a few $\times 10^{-2}$ $M_{\odot}$ and a few $\times 10^{-4}$ $M_{\odot}$, respectively" (Comparison with hydrodynamical models) [from (cite: Matsuura17)]
- External data: Expected C and Si yields  
  > "These masses account for $<20\%$ and $<0.1\%$ of the expected C and Si yields (cite: Woosley95)." (Comparison with hydrodynamical models) [from (cite: Woosley95)]
- Simulation/model as data: 3D PROMETHEUS neutrino-driven explosion models W15, L15, N20, B15 with 56Ni heating, scaled homologously from 150 days to 29 years and convolved to the observed resolution  
  > "We study four different non-rotating, non-magnetic progenitors: two 15 $M_\odot$ red supergiants (RSGs), model W15 (cite: Woosley95) and model L15 (cite: Limongi00)" (Comparison with hydrodynamical models)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: J0519-4546 (cycle 2 and 3); J0334-4008 for part of SiO 6-5  
  > "For the cycle 2 data set J0519–4546 (05:19:49.72, -45:46:43.85; 0.75 Jy at 234 GHz) was the absolute flux calibrator" (Observations and data reduction)
- flux scale uncertainty: _not stated_
- self calibration: _not stated_

### Imaging

- task: CASA tclean  
  > "For imaging and deconvolution we used the task `tclean` with different `multiscale` scales depending on the resulting beam sizes." (Observations and data reduction)
- deconvolver: _not stated_
- weighting robust: _not stated_
- uv taper: _not stated_
- cell size: 6 mas  
  > "In both cases, we used a 6 mas pixel size." (Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: [0,7,21] for CO 2-1 and SiO 5-4; [0,5,15] for SiO 6-5  
  > "For CO $2-1$ and SiO $5-4$ images, we adopted $scales=[0,7,21]$, and for the SiO $6-5$ image we adopted $scales=[0,5,15]$." (Observations and data reduction)
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: cycle 2 and cycle 3 data combined  
  > "Combining data from both cycles improves the image quality." (Observations and data reduction)
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Not stated but needed to reproduce (our reading)

- tclean weighting and robust value
- CASA version and whether the pipeline or manual calibration was used
- continuum subtraction and line-free channels
- masks, thresholds and iteration limits
- cycle 2 and 3 combination method and flux scale checks
- cprops/clumpfind parameters
- model cube preparation, convolution and scaling details
- final beam and rms

## Analysis recipe

1. **Image the line cubes**: CASA tclean multiscale imaging into a cube with 50 mas resolution and 100 km/s bins  
  > "We used the Common Astronomy Software Application (casa.nrao.edu) to process the interferometric data into a cube with 50 mas angular resolution and 100 km s$^{-1}$ spectral bins" (Observations and data reduction)
   - software: CASA, tclean
   - parameter: scales [0,7,21] or [0,5,15]; 6 mas pixel  
  > "For CO $2-1$ and SiO $5-4$ images, we adopted $scales=[0,7,21]$, and for the SiO $6-5$ image we adopted $scales=[0,5,15]$." (Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Convert velocity to 3D position**: Map velocity to sky-plane size assuming spherical free expansion  
  > "We adopted a spherical free expansion, and for the age of the supernova we took the time elapsed since the supernova explosion and the date of the observations ($\sim28.7$ years)." (Observations and data reduction)
   - assumption: Distance 50 kpc; age ~28.7 yr; free expansion  
  > "we converted velocity into angular size on the sky by assuming the distance to the LMC to be 50 kpc." (Observations and data reduction)
   - fitting: _not stated_
   - validation: FWZI ~4000 km/s and ~480 mas size give 28.5 yr since explosion, so free expansion holds  
  > "we obtain a time of $28.5$ years since the explosion. There is no evidence of deceleration of the supernova ejecta" (Observations and data reduction)
3. **Compare with explosion models**: Compare observed cubes with sqrt(12C x 16O) and sqrt(28Si x 16O) model densities, with and without density ceilings. Measure clump sizes (cprops, clumpfind), the radially averaged 3D Fourier transform, and pair-distance distributions at 50-90% thresholds.  
  > "Segmenting the cube into clumps using *cprops* (cite: Rosolowsky06) and *clumpfind* (cite: Williams94) algorithms reveals the clump size distribution." (Comparison with hydrodynamical models)
   - software: cprops, clumpfind
   - parameter: thresholds 50%-90% of peak emission  
  > "thresholds between $50\%$ and $90\%$ of peak of emission were considered" (Comparison with hydrodynamical models)
   - assumption: Excitation dominated by 44Ti decay; kinetic temperature ~50 K; LVG optical depth cutoffs  
  > "it is reasonable to assume that excitation and heating are predominantly due to $^{44}$Ti decay." (Comparison with hydrodynamical models)
   - fitting: _not stated_
   - validation: Results robust to different thresholds and segmentation parameters  
  > "The results obtained for the clump sizes and distributions are robust to the different approaches." (Comparison with hydrodynamical models)

## Software

- **CASA** : Processing the interferometric data into cubes  
  > "We used the Common Astronomy Software Application (casa.nrao.edu) to process the interferometric data into a cube" (Observations and data reduction)
- **tclean** : Imaging and multiscale deconvolution  
  > "For imaging and deconvolution we used the task `tclean` with different `multiscale` scales" (Observations and data reduction)
- **cprops** : Clump segmentation  
  > "Segmenting the cube into clumps using *cprops* (cite: Rosolowsky06)" (Comparison with hydrodynamical models)
- **clumpfind** : Clump segmentation  
  > "*clumpfind* (cite: Williams94) algorithms reveals the clump size distribution" (Comparison with hydrodynamical models)
- **PROMETHEUS** : 3D hydrodynamic explosion models compared with the data  
  > "finite-volume Eulerian multifluid hydrodynamics code PROMETHEUS (cite: Utrobin15; Wongwathanarat15)" (Comparison with hydrodynamical models)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Time since explosion from free-expansion check | 28.5 | not stated | years | 2 | we obtain a time of $28.5$ years since the explosion. |
| CO maximum extension | ±1700 (±1.53e17 cm) | not stated | km/s | 0 | $\pm1700$ km s$^{-1}$ vs. $\pm1300$ km s$^{-1}$; or $\pm1.53\times10^{17}$ cm vs. $\pm1.17\times10^{17}$ cm, approximately |
| SiO maximum extension | ±1300 (±1.17e17 cm) | not stated | km/s | 0 | $\pm1700$ km s$^{-1}$ vs. $\pm1300$ km s$^{-1}$; or $\pm1.53\times10^{17}$ cm vs. $\pm1.17\times10^{17}$ cm, approximately |
| CO clump separation peak | ~0.25 | not stated | arcsec | 3 | The clump separation of CO shows a clear peak at $\sim0.25\ensuremath{''}$ |
| SiO clump separation minor peak | ~0.30 | not stated | arcsec | 3 | the distribution of SiO shows a minor peak at $\sim0.30\ensuremath{''}$ |
| Radial directions where SiO extends beyond CO (emission >30% of peak) | 25 | not stated | percent | 0 | SiO has a greater extent than CO in $25\%$ of radial directions |

## Qualitative findings

- CO forms a torus perpendicular to the equatorial ring, while SiO is clumpier in a broken shell; both have a central deficit.  
  > "the CO emission forms a torus-like shape perpendicular to the equatorial ring" (Observational Results)
- No model reproduces both lines in all structural metrics; the BSG models give clumps that are too small.  
  > "none of the models fit both emission lines in all structural metrics" (Comparison with hydrodynamical models)

## Claim tuples

- H: Is the molecular ejecta structure clumpy, asymmetric and centrally deficient? | E: 3D CO and SiO cubes from combined ALMA cycle 2 and 3 data | R: CO torus and SiO broken shell with central holes; SiO extends beyond CO in some directions | F: Evidence of non-spherical instabilities and possible nickel heating | **supported**
- H: Do 3D neutrino-driven models reproduce the observed clump size scales? | E: Compare clump sizes and separations of data and four models W15, L15, N20, B15 | R: RSG models match CO clump sizes; BSG clumps are too small; none fits both lines | F: No model is fully consistent, but the comparison constrains progenitor and explosion physics | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Peak brightness cannot be converted to density without non-LTE excitation modelling, which needs more than one line.  
  > "requires modeling the non-LTE excitation of each clump, which we cannot do with only one emission line" (Observational Results)
- Limitation (authors): Models are non-rotating and omit chemistry, so SASI signatures cannot be assessed.  
  > "The models compared here are non-rotating, and thus we cannot say how different the signatures of SASI would be." (Conclusions)
- Caveat (inferred, ours): Models lack molecule formation and excitation physics, so the comparison uses atomic densities as proxies.
- Caveat (inferred, ours): Optical depth for SiO may be significant, which would affect clump sizes.
- Caveat (inferred, ours): Clump metrics depend on segmentation choices that are not fully given.

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: Calibration details and CASA version
- Missing: Weighting and cleaning parameters
- Missing: Model data cubes and clump-finding settings
- Data volume (inferred): Hundreds of GB raw for two long-baseline ALMA Band 6 projects
- Score (inferred): 3/5, The data codes and main imaging settings are given, but calibration, weighting and the model comparison details are missing, and the model data are not public.
- Rediscovery candidate: no, The recipe is incomplete and the model comparison needs unreleased simulation data.

## Links

- Method: (cite: Rosolowsky06) (cprops clump segmentation)
- Method: (cite: Williams94) (clumpfind algorithm)
- Companion: (cite: Matsuura17) (Lower-resolution ALMA analysis of SN 1987A molecules, temperature and masses)
- Companion: (cite: Kamenetzky13) (Earlier ALMA detection of CO and SiO)

## Checks

```json
{
 "quotes": 47,
 "quotes_ok": 47,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 33,
  "rate": 0.485
 },
 "evidence_ok": true
}
```
