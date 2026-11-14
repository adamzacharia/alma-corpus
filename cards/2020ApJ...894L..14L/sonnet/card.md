# ALMA Observations of Massive Clouds in the Central Molecular Zone: Jeans Fragmentation and Cluster Formation

`2020ApJ...894L..14L` | The Astrophysical Journal Letters 2020 | first author: Lu, Xing | arXiv: 2004.09532 | DOI: 10.3847/2041-8213/ab8b65

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: milky_way_ism, star_formation
- Question: Do massive CMZ clouds contain hidden early-phase fragmentation into cores, and is it consistent with thermal Jeans fragmentation and with forming Arches/Quintuplet-like clusters?  
  > "Could there exist a population of very early phase star formation that is still deeply embedded in the four clouds, but has been missed previously?" (1 Introduction)
- Target **20 km/s cloud, 50 km/s cloud, Sgr B1-off, Sgr C (CMZ)**: coordinates _not stated_; z/distance 8.178 kpc  
  > "Throughout this Letter we adopt a distance of 8.178 kpc to the CMZ (cite: gravity2019)." (1 Introduction); distance from GRAVITY Collaboration 2019  
  > "Throughout this Letter we adopt a distance of 8.178 kpc to the CMZ (cite: gravity2019)." (1 Introduction)

## Data provenance

- ALMA projects: 2016.1.00243.S
- bands: Band 6, continuum centred at 226 GHz  
  > "ALMA) Band 6 continuum observations of 2000 AU resolution" (abstract)
- frequencies and spectral setup: 217–221 GHz and 231–235 GHz, 1.129 MHz (1.5 km/s) resolution  
  > "The correlators were set to cover frequencies between 217–221 GHz and 231–235 GHz, with a uniform spectral resolution of 1.129 MHz (1.5 km s$^{-1}$)." (2 Observations and data reduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: C43-5 and C43-3  
  > "The data were taken in the C43-5 and C43-3 configurations" (2 Observations and data reduction)
- baselines: _not stated_
- angular resolution: 0.25"x0.17" (2000 AU x 1400 AU)  
  > "The resulting synthesized beam is 0$''$25$\times$0$''$17 (equivalent to 2000 AU$\times$1400 AU)." (2 Observations and data reduction)
- max recoverable scale: 7" (~0.3 pc)  
  > "the data are not sensitive to structures larger than 7$''$ ($\sim$0.3 pc)" (2 Observations and data reduction)
- sensitivity: 40 uJy/beam rms (~60 near brightest Sgr C peak)  
  > "The image rms measured in emission-free regions without primary-beam corrections is 40 $\mu$Jy beam$^{-1}$" (2 Observations and data reduction)
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Other facility **Herschel**: Dust temperature of 20 K at >=0.5 pc (via cited work)  
  > "The dust temperature at $\gtrsim$0.5 pc in these clouds is measured to be 20 K based on *Herschel* observations (cite: kauffmann2017a)." (3.2 Physical Properties of the Cores)
- External data: Dust opacity 0.899 cm2/g  
  > "We assumed $R$=100 and $\kappa_\nu$=0.899 cm$^2$ g$^{-1}$ (cite: ossenkopf1994)." (3.2 Physical Properties of the Cores) [from Ossenkopf & Henning 1994 (cite: ossenkopf1994)]
- External data: Parent 0.2 pc core gas temperature 50–200 K and density 1e6 cm-3  
  > "we adopt the characteristic gas temperature 50–200 K and gas density $10^6$ cm$^{-3}$ from those works." (4.1 Thermal Jeans Fragmentation) [from Lu et al. 2017; Lu et al. 2019a]
- External data: H2O maser and UC HII region associations  
  > "About 30 cores are spatially associated with H$_2$O masers ([1](#fig:cont)) or UC H ii regions (cite: lu2019a)" (3.2 Physical Properties of the Cores) [from Lu et al. 2019a (cite: lu2019a)]

## Processing

### Calibration

- pipeline or manual: Standard pipeline; configurations calibrated separately  
  > "The calibration was done using the standard pipeline implemented in CASA 4.7.2." (2 Observations and data reduction)
- casa version: CASA 4.7.2 (calibration); CASA 5.4.0 (imaging)  
  > "The imaging was done using CASA 5.4.0." (2 Observations and data reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Sgr B1-off: 2 phase-only iterations; Sgr C: 2 phase-only + 1 phase&amplitude; solint 2.048 s  
  > "The time interval used for solving self-calibration solutions is the shortest integration duration (2.048 s)." (2 Observations and data reduction)

### Imaging

- task: tclean, CASA 5.4.0, both configurations imaged together  
  > "We used the *tclean* task in CASA, with Briggs weighting and a robust parameter of 0.5" (2 Observations and data reduction)
- deconvolver: multiscale, scales [0, 5, 15, 50, 150]  
  > "a multiscale algorithm with scales of \[0, 5, 15, 50, 150\]" (2 Observations and data reduction)
- weighting robust: Briggs, robust = 0.5  
  > "with Briggs weighting and a robust parameter of 0.5" (2 Observations and data reduction)
- uv taper: _not stated_
- cell size: 0.04"  
  > "a pixel size of 0$''$04" (2 Observations and data reduction)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: Continuum built from line-free channels (channels not listed)  
  > "Continuum emission was reconstructed from line-free channels, with a central frequency at 226 GHz." (2 Observations and data reduction)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.25"x0.17"  
  > "The resulting synthesized beam is 0$''$25$\times$0$''$17" (2 Observations and data reduction)
- final rms: 40 uJy/beam (~60 near brightest Sgr C peak)  
  > "except around the brightest peak in Sgr C where it is $\sim$60 $\mu$Jy beam$^{-1}$ after self-calibration." (2 Observations and data reduction)

### Inherited from earlier work

- Continuum at this frequency dominated by cold dust emission  
  > "we concluded that the continuum at this frequency is dominated by cold dust emission" (3.1 Identification of Cores) [from Lu et al. 2019a (cite: lu2019a)]
- Projection correction factor 2/pi for separations  
  > "we divide the edge lengths by a factor of 2/$\pi$ to get the deprojected separations (cite: sanhueza2019)" (4.1 Thermal Jeans Fragmentation) [from Sanhueza et al. 2019 (cite: sanhueza2019)]
- Temperature-flux power-law scheme for alternative dust temperatures  
  > "interpolate assuming a power-law dependence of dust temperatures on core fluxes, following (cite: sadaghiani2020)" (Appendix: Impact of Varying Dust Temperatures) [from Sadaghiani et al. 2020]
- Completeness-limit method with artificial cores  
  > "we used the method in (cite: cheng2018) to estimate the completeness limit of the core sample" (Appendix: Lower Bound) [from Cheng et al. 2018]

### Not stated but needed to reproduce (our reading)

- Image size and phase centres per field
- Line-free channel selection
- Which execution blocks and calibrators were used; flux calibrator and flux uncertainty
- Cleaning threshold, niter and masks
- Exact astrodendro call details beyond min_value/min_delta/min_npix
- Modifications made to FragMent
- KDE settings for separation distributions
- Primary beam correction details and mosaic pointing layout

## Analysis recipe

1. **Image continuum**: tclean with Briggs weighting, multiscale clean, self-calibration on Sgr B1-off and Sgr C  
  > "We used the *tclean* task in CASA, with Briggs weighting and a robust parameter of 0.5" (2 Observations and data reduction)
   - software: CASA
   - parameter: robust 0.5; scales [0,5,15,50,150]; 0.04" pixel  
  > "a multiscale algorithm with scales of \[0, 5, 15, 50, 150\] and a pixel size of 0$''$04" (2 Observations and data reduction)
   - fitting: _not stated_
   - validation: _not stated_
2. **Identify cores**: astrodendro dendrogram on non-PB-corrected images; leaves are cores; fluxes from PB-corrected images; drop leaves outside 30% PB response  
  > "We set the minimum flux density to 4$\sigma$, the minimum significance for structures to 1$\sigma$, and the minimum area to the size of the synthesized beam." (3.1 Identification of Cores)
   - software: astrodendro
   - parameter: min flux 4 sigma, min significance 1 sigma, min area = beam  
  > "We set the minimum flux density to 4$\sigma$, the minimum significance for structures to 1$\sigma$, and the minimum area to the size of the synthesized beam." (3.1 Identification of Cores)
   - fitting: _not stated_
   - validation: Varied dendrogram parameters (3 sigma flux, 2 sigma significance) and found conclusions unchanged  
  > "we explore the impact of varying the dendrogram parameters upon the following analyses (e.g., changing the minimum significance to 2$\sigma$) and find that it does not affect our conclusions." (3.1 Identification of Cores)
3. **Derive core masses, radii, densities**: Optically thin dust: M = R S d^2/(B(T) kappa); r=(A/pi)^0.5; n(H2)=M/(4 pi r^3/3)/(2.8 mH)  
  > "The effective core radius $r_\text{c}$ is derived as $(A/\pi)^{1/2}$, where $A$ is the area of the core reported by *astrodendro*." (3.2 Physical Properties of the Cores)
   - parameter: T_dust = 20 K, R = 100, kappa = 0.899 cm2/g, d = 8.178 kpc  
  > "we assumed a constant $T_\text{dust}$ of 20 K as a fiducial case" (3.2 Physical Properties of the Cores)
   - assumption: Optically thin dust, constant 20 K, gas-to-dust 100  
  > "Assuming optically thin dust emission, the core masses were derived as" (3.2 Physical Properties of the Cores)
   - fitting: _not stated_
   - validation: Tested 50 K, flux-dependent and random T_dust in appendix  
  > "If we adopt a dust temperature of 50 K, the core masses would decrease by a factor of 3." (Appendix: Impact of Varying Dust Temperatures)
4. **Fit CMF high-mass power law**: MLE power-law fit of dN/dlogM with simultaneous lower bound (KS minimisation), plfit  
  > "using the maximum likelihood estimation (MLE) method in (cite: clauset2009) implemented with the *plfit* package" (3.2 Physical Properties of the Cores)
   - software: plfit
   - fitting: MLE of Clauset et al. 2009; lower bound by KS distance  
  > "It is chosen by minimizing the distance (represented by a Kolmogorov–Smirnov statistic) between the probability distribution of the measured data and the best-fit power-law model" (Appendix: Lower Bound)
   - validation: Completeness estimated by injecting artificial cores  
  > "by generating artificial cores of certain masses, randomly putting them in the original image, and using *astrodendro* to check whether they can be picked out" (Appendix: Lower Bound)
5. **Core separations and Jeans comparison**: MST of core positions, deprojected by 2/pi; compare with Jeans length and mass  
  > "The MST algorithm is implemented with a modified version of the FragMent package (cite: clarke2019)." (4.1 Thermal Jeans Fragmentation)
   - software: FragMent
   - parameter: Jeans: T 50–200 K, n = 1e6 cm-3, rho = n(H2) x 2.37 mH  
  > "we adopt the characteristic gas temperature 50–200 K and gas density $10^6$ cm$^{-3}$ from those works." (4.1 Thermal Jeans Fragmentation)
   - fitting: _not stated_
   - validation: Varied dendrogram parameters; separations vary by up to 50%  
  > "the characteristic spatial separations between cores derived from the MST analysis could vary by up to 50%" (Appendix: Dendrogram Parameters)

## Software

- **CASA** 4.7.2 (calibration), 5.4.0 (imaging): Calibration, tclean imaging, self-calibration  
  > "The calibration was done using the standard pipeline implemented in CASA 4.7.2." (2 Observations and data reduction)
- **astrodendro** : Core identification  
  > "We used the dendrogram algorithm (cite: rosolowsky2008dendro) implemented with *astrodendro*" (3.1 Identification of Cores)
- **plfit** : Power-law MLE fit of CMF  
  > "implemented with the *plfit* package" (3.2 Physical Properties of the Cores)
- **FragMent** modified version: MST calculation  
  > "The MST algorithm is implemented with a modified version of the FragMent package (cite: clarke2019)." (4.1 Thermal Jeans Fragmentation)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Number of cores, 20 km/s cloud | 471 | not stated | cores | 2 | / 20 km s$^{-1}$ / 471 / |
| Number of cores, Sgr B1-off | 89 | not stated | cores | 2 | / Sgr B1-off     / 89        / |
| Number of cores, Sgr C | 275 | not stated | cores | 2 | / Sgr C          / 275       / |
| 5 sigma mass sensitivity | 0.3 | not stated | Msun per beam | 3 | the 5$\sigma$ mass sensitivity is 0.3 $M_\odot$ per beam given a $T_\text{dust}$ of 20 K |
| CMF power-law index alpha (three clouds) | 1.00–1.07 | not stated | dimensionless | 4 | The other three fittings reach similar values of $\alpha$ in the range of 1.00–1.07. |
| CMF lower bound | ~5 | not stated | Msun | 4 | The lower bound of all fittings is found to be around 5 $M_\odot$ |
| Most frequent core separation | ~1e4 | (0.8–1.5)e4 under varied parameters | AU | 5 | In the three clouds, the most frequent separation is $\sim$$10^4$ AU. |
| Jeans length | (1.0–1.9)e4 | not stated | AU | 5 | The derived Jeans length is (1.0–1.9)$\times$$10^4$ AU. |
| Jeans mass | 3–25 | not stated | Msun | 5 | This is generally consistent with the Jeans mass of 3–25 $M_\odot$. |
| 90% completeness limit, 20 km/s cloud | ~2 (30% PB); ~5 (above 5 sigma) | not stated | Msun | 4 | the 90% completeness limit is estimated to be $\sim$2 $M_\odot$ for the 20 km s$^{-1}$ cloud |
| CMF index, flux-dependent T_dust, fixed lower bound 1 Msun | 1.40 | 0.10 | dimensionless | 4 | fit a power-law index of $1.40\pm0.10$ |

## Qualitative findings

- Clouds differ in fragmentation: 20 km/s cloud and Sgr C most fragmented, 50 km/s cloud little  
  > "The 20 km s$^{-1}$ cloud and Sgr C have the most fragmented substructures." (3.1 Identification of Cores)

## Claim tuples

- H: CMF shape differs from the IMF | E: Power-law MLE fits to CMFs assuming 20 K | R: alpha ~1.00–1.07, shallower than 1.3 | F: Slightly top-heavy CMF, but highly uncertain, especially in dust temperature | **partially**
- H: Fragmentation at sub-0.1 pc is thermal Jeans | E: MST separations and core masses vs Jeans length/mass | R: ~1e4 AU separations vs 1.0–1.9e4 AU; masses 1–7 vs 3–25 Msun | F: Consistent with thermal Jeans fragmentation | **supported**
- H: These clouds can form Arches/Quintuplet-like clusters | E: Count cores above ~20 Msun | R: 5–20 massive cores per cloud | F: Only OB associations currently; massive clusters need further accretion | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: Dendrogram leaves with one criteria set on uniform-noise images  
  > "allowing us to apply a single set of criteria to the whole image" (3.1 Identification of Cores)
- Alternative: Dust temperature 50 K, flux-dependent 20–150 K, and random 20–150 K; all steepen the CMF  
  > "the power law in the CMFs significantly steepens and is no longer top-heavy as compared to the IMF" (Appendix: Impact of Varying Dust Temperatures)
- How they decided it was enough: _not stated_
- Limitation (authors): Dust temperature at 2000 AU unknown, strongly affects masses  
  > "$T_\text{dust}$ at 2000 AU scales is unclear." (3.2 Physical Properties of the Cores)
- Limitation (authors): Cannot tell whether cores are prestellar or protostellar  
  > "with the current data we cannot determine whether the cores have collapsed and are mostly protostellar" (3.2 Physical Properties of the Cores)
- Caveat (inferred, ours): Constant 20 K dust temperature makes masses and CMF slope highly uncertain
- Caveat (inferred, ours): Leaves of a dendrogram in crowded regions are sensitive to parameters and confusion
- Caveat (inferred, ours): Jeans comparison uses gas parameters from 0.2 pc scale, not measured at core scale
- Caveat (inferred, ours): Single-band continuum with no spectral index to check free-free contamination

## Reproducibility

- Data public (paper): Project code cited; the ALMA data are archival-type, but public status is not explicitly stated  
  > "This paper makes use of the following ALMA data: ADS/JAO.ALMA#2016.1.00243.S." (Acknowledgments)
- Products in archive: _not stated_
- Missing: Image size and field centres
- Missing: Line-free channel list
- Missing: Exact mask/threshold for cleaning
- Missing: Full details of FragMent modifications
- Data volume (inferred): ~100–500 GB raw for several fields in two configurations
- Score (inferred): 3/5, Imaging and dendrogram parameters are given and the catalog is online, but several imaging details and the full pipeline scripts are missing.
- Rediscovery candidate: yes, The project code is given, the recipe is mostly specified, and the results are numeric (core counts, alpha, separations).

## Links

- Method: Rosolowsky et al. 2008 (cite: rosolowsky2008dendro) (dendrogram algorithm)
- Method: Clauset et al. 2009 (cite: clauset2009) (power-law MLE fitting)
- Method: Clarke et al. 2019 (cite: clarke2019) (FragMent MST package)
- Method: Cheng et al. 2018 (cite: cheng2018) (completeness estimate method)
- Companion: Lu et al. 2019a (cite: lu2019a) (earlier 3'' study of the same clouds with masers and UC HII regions)
- Companion: Lu et al. 2019b (cite: lu2019b) (UC HII region and maser survey in the CMZ)

## Checks

```json
{
 "quotes": 68,
 "quotes_ok": 68,
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
  "facts": 79,
  "stated": 52,
  "rate": 0.658
 },
 "evidence_ok": true
}
```
