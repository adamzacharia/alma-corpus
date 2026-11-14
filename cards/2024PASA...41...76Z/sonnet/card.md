# Hierarchical hub-filament structures and gas inflows on galaxy-cloud scales

`2024PASA...41...76Z` | Publications of the Astronomical Society of Australia 2024 | first author: Zhou, Jian-Wen | arXiv: 2404.15862 | DOI: 10.1017/pasa.2024.47

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type archival_reuse

## Science

- Fields: nearby_galaxies, milky_way_ism
- Question: Do gas structures on galaxy-cloud scales in NGC5236 and NGC4321 show hierarchical hub-filament structures, gas inflows and gravitational collapse like cloud-clump and clump-core scales?  
  > "We investigated the kinematics and dynamics of gas structures on galaxy-cloud scales in two spiral galaxies NGC5236 (M83) and NGC4321 (M100) using CO (2$-$1) line." (abstract)
- Target **NGC5236 (M83)**: coordinates _not stated_; z/distance 4.89 Mpc  
  > "corresponding to linear resolutions $\sim$51 pc and $\sim$123 pc for NGC5236 and NGC4321 at the distances 4.89 Mpc and 15.21 Mpc" (Data and target); distance from Leroy2021-257; Anand2021-501  
  > "corresponding to linear resolutions $\sim$51 pc and $\sim$123 pc for NGC5236 and NGC4321 at the distances 4.89 Mpc and 15.21 Mpc" (Data and target)
- Target **NGC4321 (M100)**: coordinates _not stated_; z/distance 15.21 Mpc  
  > "corresponding to linear resolutions $\sim$51 pc and $\sim$123 pc for NGC5236 and NGC4321 at the distances 4.89 Mpc and 15.21 Mpc" (Data and target); distance from Leroy2021-257; Anand2021-501  
  > "corresponding to linear resolutions $\sim$51 pc and $\sim$123 pc for NGC5236 and NGC4321 at the distances 4.89 Mpc and 15.21 Mpc" (Data and target)

## Data provenance

- ALMA projects: 2013.1.01161.S, 2015.1.00121.S, 2015.1.00956.S, 2016.1.00386.S, 2017.1.00886.L
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: 12m+7m+TP combined  
  > "We use the combined 12m+7m+TP PHANGS-ALMA CO (2$-$1) data cubes" (Data and target)
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ~2.1'' (NGC5236), ~1.7'' (NGC4321); spectral resolution 2.5 km/s  
  > "which have a spectral resolution of 2.5 km s$^{-1}$ and angular resolutions $\sim$2.1 $''$ and $\sim$1.7 $''$" (Data and target)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: PHANGS-ALMA survey products  
  > "We select two face-on spiral galaxies NGC5236 (M83) and NGC4321 (M100) from the PHANGS-ALMA survey." (Data and target)
- Line: CO J=2-1 (not stated)
- External data: PHANGS-ALMA CO(2-1) cubes and moment maps  
  > "The PHANGS-ALMA CO (2$-$1) data cubes and other data products (such as Moment maps) are available from the PHANGS team website" (Data and target) [from Leroy2021-257; Leroy2021-255]
- External data: alpha_CO(2-1) ≈ 6.7 Msun pc^-2 (K km/s)^-1  
  > "here $\alpha^{2-1}_{\rm CO} \approx 6.7 \rm M_{\odot} \rm pc^{-2} (\rm K*km s^{-1})^{-1}$ (cite: Leroy2022-927)" (Scaling relations) [from Leroy2022-927]
- External data: Inclinations 24 deg (NGC5236) and 38.5 deg (NGC4321)  
  > "The inclination angles of NGC5236 and NGC4321 are 24$^{\rm o}$ and 38.5$^{\rm o}$ (cite: Lang2020-897), respectively." (Data and target) [from Lang2020-897]

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: PHANGS-ALMA calibrated, imaged data products used; calibration described in Leroy2021-255  
  > "A detailed description of data calibration, imaging, and product creation procedures is presented in (cite: Leroy2021-255)." (Data and target)
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

- GAUSSPY+ parameter settings follow earlier work  
  > "The parameter settings for the decomposition align with those employed by (cite: Zhou2023-676)." (Velocity component) [from (cite: Zhou2023-676)]
- Dendrogram structure identification and screening follow earlier works  
  > "we employed the same approach as outlined in (cite: Zhou2024-682-128) and (cite: Zhou2024-682-173) to identify dense gas structures." (Dendrogram) [from (cite: Zhou2024-682-128); (cite: Zhou2024-682-173)]
- FILFINDER filament identification follows earlier method  
  > "Following the method described in (cite: Zhou2022-514) and (cite: Zhou2023-676), we used the Moment 0 maps of CO (2$-$1) emission" (Identification of filaments) [from (cite: Zhou2022-514); (cite: Zhou2023-676)]

### Not stated but needed to reproduce (our reading)

- FILFINDER parameters
- GAUSSPY+ parameter values (only referenced to previous paper)
- Moment map masking details
- KinMS model parameters (rotation curve form, fitting procedure)
- Segment definitions and peak selection for velocity gradient fits
- Dendrogram implementation, e.g. astrodendro and min_value settings
- Linear fit method and uncertainties for the gradient-scale relation

## Analysis recipe

1. **Decompose spectra into Gaussian components**: GAUSSPY+ fit of CO(2-1) cubes  
  > "We utilized the fully automated Gaussian decomposer `GAUSSPY+`" (Velocity component)
   - software: GAUSSPY+
   - fitting: _not stated_
   - validation: reduced chi^2 around 1  
  > "The reduced $\chi^{2}$ values output in the fitting of NGC4321 and NGC5236 are around 1" (Velocity component)
2. **Identify structures and derive scaling relations**: Dendrogram on Moment 0 maps, average spectra per structure after subtracting KinMS rotation model; compute R_eff, mass, sigma, N  
  > "We conducted a direct identification of hierarchical (sub-)structures based on the 2D integrated intensity (Moment 0) map of CO (2$-$1) emission." (Dendrogram)
   - software: dendrogram
   - parameter: minimum area larger than 1 beam, no other parameters  
  > "we therefore only require the smallest area of the identified structure larger than 1 beam and do not set other parameters in the algorithm" (Dendrogram)
   - assumption: alpha_CO(2-1) = 6.7 Msun pc^-2 (K km/s)^-1  
  > "here $\alpha^{2-1}_{\rm CO} \approx 6.7 \rm M_{\odot} \rm pc^{-2} (\rm K*km s^{-1})^{-1}$ (cite: Leroy2022-927)" (Scaling relations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Identify filaments**: FILFINDER on Moment 0 maps; main filaments along spiral arms  
  > "The FILFINDER algorithm (cite: Koch2015) was used to identify and characterize filaments in the galaxy." (Identification of filaments)
   - software: FILFINDER
   - fitting: _not stated_
   - validation: _not stated_
4. **Remove galactic rotation and fit local velocity gradients**: Linear baseline per filament segment, and alternatively KinMS dynamical model subtracted from Moment 1; gradients fitted around intensity peaks  
  > "Here, we eliminated the large-scale velocity gradient by employing a simple linear function for modeling." (Linear fitting)
   - software: KinMS
   - assumption: projection effect ignored for face-on galaxies  
  > "Given that NGC4321 and NGC5236 are good face-on galaxies, here we ignored the projection effect in velocity gradient fitting." (Linear fitting)
   - fitting: _not stated_
   - validation: two methods give consistent results  
  > "As shown in Fig.[7](#compare), two methods give consistent fitting results." (Statistical analysis of the fitted velocity gradients)
5. **Compare gradients with free-fall model**: Fit gradient vs scale and compare with free-fall nabla v ∝ R^-1.5; infer central masses  
  > "the linear fitting in Fig.[7](#compare)(a) gives $\nabla v \propto R^{-0.8}$" (Deviation of the free-fall model)
   - assumption: free-fall gradient sqrt(GM/2R^3)  
  > "Assuming free-fall, $$\begin{equation}
\nabla v = -\frac{d}{dR}\sqrt{\frac{2GM}{R}}
=\sqrt{\frac{GM}{2R^3}}," (Deviation of the free-fall model)
   - fitting: linear fit in log space (implied)  
  > "In equation.[\[e-free\]](#e-free), $\nabla v \propto R^{-1.5}$, however, the linear fitting in Fig.[7](#compare)(a) gives $\nabla v \propto R^{-0.8}$" (Deviation of the free-fall model)
   - validation: _not stated_

## Software

- **GAUSSPY+** : Gaussian decomposition of CO spectra  
  > "We utilized the fully automated Gaussian decomposer `GAUSSPY+`" (Velocity component)
- **FILFINDER** : filament identification  
  > "The FILFINDER algorithm (cite: Koch2015) was used to identify and characterize filaments in the galaxy." (Identification of filaments)
- **KinMS** : gas dynamical model of galaxy rotation  
  > "using the Kinematic Molecular Simulation (KinMS) package of (cite: Davis2013-429)" (Gas dynamical model)
- **dendrogram algorithm** : hierarchical structure identification  
  > "Dendrogram algorithm decomposes the intensity data (Moment 0 map) into hierarchical structures." (Dendrogram)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Retained structures NGC4321 | 853 | not stated | count | 2 | there are 853 and 2581 retained structures for NGC4321 and NGC5236, respectively |
| Retained structures NGC5236 | 2581 | not stated | count | 2 | there are 853 and 2581 retained structures for NGC4321 and NGC5236, respectively |
| Observed gradient-scale slope | -0.8 | not stated | dimensionless | 5 | the linear fitting in Fig.[7](#compare)(a) gives $\nabla v \propto R^{-0.8}$ |
| Central masses implied by free-fall (small/large scales) | ~10^5–10^6.5 and ~10^6–10^7.5 | not stated | Msun | 5 | with central masses of $\sim$ 10$^{5}$–10$^{6.5}$  M$_\odot$ and $\sim$ 10$^{6}$–10$^{7.5}$  M$_\odot$ |
| Single-component spectra fraction NGC4321 / NGC5236 | 98% / 87% | not stated | percent | 1 | 98% spectra are single component, 2% spectra have two velocity components. |

## Qualitative findings

- sigma-N*R slopes are shallower than 0.5, indicating slower-than-free-fall collapse  
  > "the slopes of the $\sigma-N*R$ relations are notably shallower than 0.5" (Scaling relations)

## Claim tuples

- H: Hierarchical hub-filament structures and inflows extend to galaxy-cloud scales | E: Velocity gradients along FILFINDER filaments fitted around intensity peaks | R: Gradients increase from large to small scales; boundary ~500 pc; implied masses 10^5-10^7.5 Msun | F: Clouds/complexes act as hubs in spiral galaxies | **supported**
- H: Collapse is pure free-fall | E: sigma-N*R and gradient-R scaling | R: Slopes shallower than free-fall (R^-0.8 vs R^-1.5) | F: Collapse is slower than free-fall | **refuted**

## Reasoning

- Why this data: Face-on galaxies with strong CO(2-1) emission and continuous spiral arms  
  > "They have strong CO (2$-$1) emission, presenting large-scale continuous structures (strong spiral arms)" (Data and target)
- Why this method: _not stated_
- How they decided it was enough: _not stated_
- Limitation (authors): Only line-of-sight velocity and CO traced mass are measured, so acceleration and central mass are underestimated  
  > "We only measured the projection of the realistic velocity vector and hence acceleration, thus tends to underestimate the observed acceleration." (Discussion)
- Caveat (inferred, ours): Gradients depend on filament identification and segmentation choices that are not specified
- Caveat (inferred, ours): Resolution differs between galaxies (51 vs 123 pc), possibly biasing scale trends
- Caveat (inferred, ours): Constant alpha_CO assumed
- Caveat (inferred, ours): Free-fall interpretation is degenerate with galactic rotation, shear and magnetic support
- Caveat (inferred, ours): No uncertainties on fitted slopes

## Reproducibility

- Data public (paper): PHANGS-ALMA cubes and moment maps available from PHANGS website  
  > "The PHANGS-ALMA CO (2$-$1) data cubes and other data products (such as moment maps) are available from the PHANGS team website" (Data Availability)
- Products in archive: _not stated_
- Missing: FILFINDER and GAUSSPY+ parameters
- Missing: KinMS model details
- Missing: Segment and peak selection for gradient fitting
- Missing: Dendrogram software settings
- Data volume (inferred): ~10-20 GB (two PHANGS CO(2-1) cubes and moment maps)
- Score (inferred): 3/5, Public data and standard tools, but key parameters are deferred to earlier papers or unstated, and the gradient measurements are partly manual.
- Rediscovery candidate: no, Data are public but the gradient fitting recipe is incomplete and partly subjective.

## Links

- Method: Leroy2021-255 (PHANGS-ALMA calibration and imaging)
- Method: Zhou2024-682-128 (Dendrogram structure identification and screening)
- Method: Zhou2023-676 (Velocity-gradient and hub-filament methodology)
- Companion: Zhou2022-514 (Hub-filament systems on clump-core scales (ATOMS))
- Companion: Zhou2024-682-173 (Related kinematic analysis)
- Related: PHANGS-ALMA
- Related: ATOMS

## Checks

```json
{
 "quotes": 49,
 "quotes_ok": 49,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 5,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 5,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 35,
  "rate": 0.455
 },
 "evidence_ok": true
}
```
