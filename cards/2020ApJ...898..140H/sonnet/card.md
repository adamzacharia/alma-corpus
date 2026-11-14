# Large-scale CO Spiral Arms and Complex Kinematics Associated with the T Tauri Star RU Lup

`2020ApJ...898..140H` | The Astrophysical Journal 2020 | first author: Huang, Jane | arXiv: 2007.02974 | DOI: 10.3847/1538-4357/aba1e1

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type observational_alma_primary

## Science

- Fields: protoplanetary_disks
- Question: What are the distribution and kinematics of the large-scale CO gas around the T Tauri star RU Lup, and what could explain its morphology?  
  > "We comment on potential explanations for RU Lup’s peculiar gas morphology, including gravitational instability, accretion of material onto the disk, or perturbation by another star." (abstract)
- Target **RU Lup**: coordinates ICRS 15h56m42.311s, -37d49m15.473s  
  > "RU Lup (ICRS 15$^\text{h}$56$^\text{m}$42$^\text{s}$.311, $-37^\circ$49$'$15.473$''$), a $0.5\substack{+0.8\\-0.3}$ Myr old K7 star located $158.9\pm0.7$ pc away in the Lupus II cloud" (Introduction); z/distance 158.9±0.7 pc  
  > "RU Lup (ICRS 15$^\text{h}$56$^\text{m}$42$^\text{s}$.311, $-37^\circ$49$'$15.473$''$), a $0.5\substack{+0.8\\-0.3}$ Myr old K7 star located $158.9\pm0.7$ pc away in the Lupus II cloud" (Introduction); distance from Gaia DR2 / Bailer-Jones et al. 2018 (cite: 2018AJ....156...58B)  
  > "RU Lup (ICRS 15$^\text{h}$56$^\text{m}$42$^\text{s}$.311, $-37^\circ$49$'$15.473$''$), a $0.5\substack{+0.8\\-0.3}$ Myr old K7 star located $158.9\pm0.7$ pc away in the Lupus II cloud" (Introduction)

## Data provenance

- ALMA projects: _none stated_
- bands: Band 6  
  > "ALMA Band 6 observations of RU Lup were taken using the Morita Array/Atacama Compact Array (ACA) and two configurations with the 12-meter antennas (C43-2 and C43-5)." (2 Observations and Data Reduction)
- frequencies and spectral setup: 12CO, 13CO, C18O J=2-1, DCO+ J=3-2, SiO J=5-4; channel width 61.035 kHz; continuum window at 232.7 GHz, 2000 MHz  
  > "Continuum window | 232.7 | 2000 | 2000 | 15625" (Table 2)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: ACA, C43-2, C43-5  
  > "the Morita Array/Atacama Compact Array (ACA) and two configurations with the 12-meter antennas (C43-2 and C43-5)" (2 Observations and Data Reduction)
- baselines: ACA 9-49 m; C43-2 15-500 m; C43-5 15-1398 m  
  > "2018 November 10 | C43-5 (12-m antennas) | 45 | $15-1398$ | 33" (Table 1)
- angular resolution: ~0.3" (~50 au)  
  > "at a resolution of $\sim0.3\ensuremath{''}$ ($\sim50$ au)" (abstract)
- max recoverable scale: 20" (shortest baseline); 7" (5th percentile baseline)  
  > "is $20''$ and the more conservative MRS defined by the 5th percentile of the baselines" (3.1 Overview)
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: 2018 Oct 2 to 2019 Jan 9  
  > "2019 January 9 | C43-2 (12-m antennas) | 44 | $15-314$ | 16" (Table 1)
- pi or archival as stated: _not stated_
- Line: 12CO J=2-1 (230.5380000 GHz)
- Line: 13CO J=2-1 (220.3986842 GHz)
- Line: C18O J=2-1 (219.5603541 GHz)
- Line: DCO+ J=3-2 (216.1125822 GHz)
- Line: SiO J=5-4 (217.1049800 GHz)
- Other facility **VLT-SPHERE**: H-band Qphi scattered light image for comparison  
  > "the VLT-SPHERE $H$-band $Q_\phi$ image from the DARTTS-S survey" (4 Comparison)
- Other facility **DSHARP (ALMA)**: high-resolution mm continuum image for comparison  
  > "high-resolution millimeter continuum image from the DSHARP survey" (4 Comparison)
- External data: Disk inclination 18.8 deg and position angle 121 deg used for deprojection  
  > "Using the inclination ($18.8\ensuremath{^\circ}$) and position angle (121$^\circ$) measured for RU Lup in (cite: 2018ApJ...869L..43H)" (3.3 Spiral arms) [from (cite: 2018ApJ...869L..43H)]
- External data: DSHARP dust opacities  
  > "We adopt the DSHARP dust opacities from (cite: 2018ApJ...869L..45B)" (Column density) [from (cite: 2018ApJ...869L..45B)]
- External data: Stellar mass range 0.2-0.5 Msun (kinematics), 0.6-1.2 Msun (evolutionary models)  
  > "Mass estimates for RU Lup have ranged from $0.2-0.5$ $M_\odot$ based on analyses of line kinematics" (Clumps) [from (cite: 2018AA...616A.100Y); (cite: 2017AA...600A..20A); (cite: 2018ApJ...865..157A)]

## Processing

### Calibration

- pipeline or manual: ALMA staff pipeline calibration, then self-calibration by authors  
  > "The raw data were first calibrated by ALMA staff with the `CASA v.5.4.0` pipeline" (2 Observations and Data Reduction)
- casa version: CASA 5.4.0  
  > "The same `CASA` version was used for subsequent processing and imaging following data delivery from ALMA." (2 Observations and Data Reduction)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: ~10%  
  > "Given ALMA’s systematic flux calibration uncertainty of $\sim10\%$" (2 Observations and Data Reduction)
- self calibration: ACA and C43-2: two phase rounds (60 s,15 s ACA; 15 s,10 s C43-2) + one amplitude; C43-5: three phase rounds (15,6,6 s) + one amplitude  
  > "while the C43-5 continuum underwent three rounds of phase self-calibration (intervals of 15 s, 6 s, and 6 s) and one round of amplitude self-calibration" (2 Observations and Data Reduction)

### Imaging

- task: tclean (Clark for ACA/C43-2 continuum, multi-scale for C43-5 continuum)  
  > "imaged with the `tclean` task, using the Clark CLEAN algorithm for the ACA and C43-2 data" (2 Observations and Data Reduction)
- deconvolver: multi-scale CLEAN for 12CO  
  > "We produced a preliminary $^{12}$CO image with multi-scale CLEAN by manually masking the visible emission." (2 Observations and Data Reduction)
- weighting robust: Briggs 0.5 for CO lines; 2.0 for DCO+  
  > "DCO$^+$ $J=3-2$ | 2.0 | $0.50\times0.48$ $(69.1)$" (Table 3)
- uv taper: Gaussian taper for DCO+ (and SiO); taper value not given  
  > "The weaker DCO$^+$ emission was imaged with a Gaussian taper to improve sensitivity." (2 Observations and Data Reduction)
- cell size: _not stated_
- image size: _not stated_
- masking: 12CO: ellipses around >5 sigma emission, expanded for adjacent-channel emission; thresholds 15 then 5 mJy/beam; 13CO/C18O circular 2" masks; DCO+ 3" mask  
  > "We began constructing a new CLEAN mask by specifying ellipses that encompassed emission exceeding $5\times$ the rms level" (2 Observations and Data Reduction)
- multiscale scales: _not stated_
- continuum subtraction: uvcontsub in uv plane  
  > "Using the `uvcontsub` task, the continuum was subtracted from the spectral line observations in the $uv$ plane." (2 Observations and Data Reduction)
- line free channels: _not stated_
- primary beam correction: applied in CASA to all images  
  > "A primary beam correction was applied in `CASA` to this and all subsequent images." (2 Observations and Data Reduction)
- array combination: all configurations CLEANed together  
  > "before combining all the configurations to produce a final continuum image" (2 Observations and Data Reduction)
- smoothing: _not stated_
- final beam: 12CO 0.32x0.31"; 13CO 0.32x0.32"; C18O 0.33x0.32"; DCO+ 0.50x0.48"  
  > "$^{12}$CO $J=2-1$ | 0.5 | $0.32\times0.31$ $(-57.5)$" (Table 3)
- final rms: 12CO 2.5 (1.7) mJy/beam; 13CO 2.0; C18O 1.6; DCO+ 1.3 (dv=0.25 km/s)  
  > "$^{13}$CO $J=2-1$ | 0.5 | $0.32\times0.32$ $(-56.6)$ | 93 | 2.0$^{b}$" (Table 3)

### Inherited from earlier work

- Disk inclination and position angle  
  > "measured for RU Lup in (cite: 2018ApJ...869L..43H)" (3.3 Spiral arms) [from (cite: 2018ApJ...869L..43H)]
- Median-stacking of channelization-shifted cubes for peak maps  
  > "The median-stacking procedure is necessary to mitigate the artifacts that arise from channelization (cite: 2014ApJ...785L..12C)." (3.3 Spiral arms) [from (cite: 2014ApJ...785L..12C)]
- Virial velocity dispersion formula  
  > "Following (cite: 1992ApJ...384..523F), we compute the velocity dispersion with" (Column density) [from (cite: 1992ApJ...384..523F)]

### Not stated but needed to reproduce (our reading)

- Self-calibration source-model details and SNR thresholds
- uv taper value for DCO+ and SiO imaging
- Cell size and image size
- Multi-scale scales used
- Line-free channel ranges for continuum
- Exact masks for 12CO (only shown in figures)
- Flux values of calibrators and gencal scaling factors
- Project codes not printed in text
- Spiral fit procedure is manual; no objective criteria

## Analysis recipe

1. **Self-calibrate and combine continuum**: Align EBs with fixvis/fixplanets, rescale flux with gencal to C43-5, phase and amplitude self-cal, apply solutions to line data  
  > "The `fixvis` and `fixplanets` tasks were used to shift the continuum peaks to the phase center" (2 Observations and Data Reduction)
   - software: CASA
   - fitting: _not stated_
   - validation: EB visibility amplitudes consistent at overlapping spatial frequencies  
  > "the visibility amplitudes from different EBs were consistent with one another at overlapping spatial frequencies" (2 Observations and Data Reduction)
2. **Image line cubes and make moment maps**: uvcontsub, tclean with masks; moment maps with clipped pixels (1 sigma for 12CO integrated, 5 sigma for velocity)  
  > "pixels in the image cube that fall below the 1$\sigma$ level are also excluded when calculating the integrated intensity map" (3.1 Overview)
   - software: CASA
   - fitting: _not stated_
   - validation: ACA and 12-m imaged separately; fluxes agree within ~10% in non-cloud channels  
  > "found that the CO fluxes were comparable (within $\sim10\%$) in the non-cloud-contaminated channels" (3.3 Spiral arms)
3. **Characterize spiral arms**: Peak brightness temperature map, deprojected, with manually adjusted logarithmic spirals R=R0 exp(b theta)  
  > "the parameters for the proposed spirals were adjusted manually in order to identify a reasonable approximation to the spiral morphology" (3.3 Spiral arms)
   - assumption: Spirals lie in the disk plane (i=18.8 deg, PA=121 deg)  
  > "the spiral geometries are computed under the assumption that they lie in the same plane as RU Lup’s disk" (3.3 Spiral arms)
   - fitting: _not stated_
   - validation: _not stated_
4. **Fit clump spectra and sizes**: Gaussian line fit with MCMC (40 walkers, 2000 steps, 1000 burn-in), uniform priors; 2D Gaussian imfit for sizes/fluxes  
  > "with 40 walkers evolved over 2000 steps for each clump. The first 1000 steps are discarded as burn-in." (3.4 Clumps)
   - software: emcee, CASA
   - parameter: Priors 0<Ipeak<1 Jy/beam, 0.05<sigma_v<3 km/s  
  > "Broad uniform priors are specified: $0<I_\text{peak}<1$ Jy beam$^{-1}$, $0.05<\sigma_v<3$ km s$^{-1}$" (3.4 Clumps)
   - assumption: Gaussian likelihood, independent channels  
  > "The likelihood function is taken to be Gaussian, and the noise in each channel is assumed to be independent." (3.4 Clumps)
   - fitting: _not stated_
   - validation: _not stated_
5. **Estimate column densities and masses**: Optically thin LTE 13CO for envelope; 12CO with tau=3 for clumps; dust upper limits from continuum non-detection  
  > "Assuming a lower bound of $\tau=3$, the clump-averaged CO column density lower bound would be $N_\text{tot}\sim 8\times 10^{15}$ cm$^{-2}$." (3.5 Column density)
   - software: dsharp_opac
   - assumption: Trot 35 K (envelope), 10 K (clumps); 12CO:H2=1e-4; 12C:13C=69; gas-to-dust 100; kappa(1.3mm)=0.4 cm2/g  
  > "we take our lower bound on $\kappa_\text{abs}$ at $\lambda=1.3$ mm to be 0.4 cm$^2$ g$^{-1}$" (3.5 Column density)
   - fitting: _not stated_
   - validation: Compared with disk mass 0.03 Msun and HI column density  
  > "the total mass of the RU Lup disk is 0.03 $M_\odot$" (3.5 Column density)

## Software

- **CASA** 5.4.0: pipeline, self-calibration, imaging, imfit, uvcontsub  
  > "The same `CASA` version was used for subsequent processing and imaging" (2 Observations and Data Reduction)
- **emcee** : MCMC fit of clump spectra  
  > "affine invariant MCMC sampler implemented in `emcee`" (3.4 Clumps)
- **dsharp_opac** : dust opacities  
  > "`dsharp_opac` (cite: 2018ApJ...869L..45B)" (Software)
- **analysisUtils** : listed as used  
  > "`analysisUtils` (<https://casaguides.nrao.edu/index.php/Analysis_Utilities>)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Keplerian disk radius | ~120 | not stated | au | 2 | A Keplerian disk extending to a radius of $\sim120$ au. |
| Envelope-like structure radius | ~260 | not stated | au | 2 | extending from the Keplerian disk to a radius of $\sim260$ au |
| 13CO integrated flux | 1.2 | 0.2 | Jy km/s | 2 | $1.2\pm0.2$ |
| C18O integrated flux | 0.34 | 0.03 | Jy km/s | 2 | $0.34\pm0.03$ |
| DCO+ integrated flux | 0.054 | 0.016 | Jy km/s | 2 | $0.054\pm 0.016$ |
| Spiral pitch angles | 15-31 | not stated | degrees | 3 | S5  /  850  / 0.6  /     31 |
| Envelope 13CO column density | ~3e14 | order of magnitude | cm^-2 | 5 | The resulting $^{13}$CO column density is estimated to be $\sim3\times10^{14}$ cm$^{-2}$. |
| Envelope mass | ~2e-5 | not stated | Msun | 5 | we estimate the overall mass of the envelope-like structure to be $\sim2\times10^{-5}$ $M_\odot$ |
| Infall rate at 120 au | 3e-8 to 5e-8 | not stated | Msun/yr | 5 | $\dot M_\text{infall}\sim3\times10^{-8}-5\times10^{-8}$ $M_\odot$ yr$^{-1}$ |
| Clump mass lower bound | ~0.1 | not stated | Earth masses | 5 | this H$_2$ column density corresponds to a clump mass lower bound of $5\times10^{26}$ g, or $\sim0.1$ $M_\ensuremath{\oplus}$ |
| Clump C1 velocity | 2.23 | 0.02 | km/s | 4 | $2.23\pm0.02$ |

## Qualitative findings

- Spiral arms are mostly blueshifted, clumpy, with inner tips ending at a ~260 au clumpy ring  
  > "Their inward termination point appears to be at a clumpy CO emission ring that is $\sim260$ au from RU Lup." (Summary)

## Claim tuples

- H: Is the CO around RU Lup a simple Keplerian disk? | E: Deep multi-configuration ALMA imaging of 12CO, 13CO, C18O | R: Four components: Keplerian disk, envelope-like structure, at least five spiral arms, 11 clumps | F: RU Lup has complex, extended non-Keplerian gas | **supported**
- H: Are the clumps bound to RU Lup? | E: Compared clump velocity offsets with escape velocity at 840 au | R: Escape velocity ~1.6 km/s for 1.2 Msun | F: Most clumps appear unbound; some depend on stellar mass | **partially**
- H: What origin explains the gas morphology? | E: Compared with models of GI, infall, winds, companions, flybys | R: No single model fully matches | F: May be scaled-down FU Ori-like behavior; origin unresolved | **partially**

## Reasoning

- Why this data: Previous observations were not designed to recover large-scale emission  
  > "Because previous ALMA observations of RU Lup were not designed to recover large-scale emission" (Introduction)
- Why this method: _not stated_
- Alternative: Envelope-like structure as foreground cloud emission considered unlikely  
  > "We consider the latter scenario unlikely for a couple reasons." (3.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Cloud contamination and spatial filtering affect 12CO fluxes and masses  
  > "is reported for completeness but should be treated with caution" (3.1 Overview)
- Caveat (inferred, ours): Spiral parameters fit by eye, no uncertainties
- Caveat (inferred, ours): Mass estimates depend on assumed Trot, abundance, linewidth, tau
- Caveat (inferred, ours): Envelope-cloud separation ambiguous at cloud velocities

## Reproducibility

- Data public (paper): _not stated_
- Products in archive: _not stated_
- Missing: ALMA project codes not printed
- Missing: Cell/image size, multiscale scales
- Missing: Final CLEAN masks and self-cal details
- Missing: Spiral parameters selection
- Data volume (inferred): ~100-300 GB raw for 7 EBs (ACA+12m, high spectral resolution)
- Score (inferred): 3/5, Data likely public and recipe mostly described, but masks, imaging params and project codes are not fully given.
- Rediscovery candidate: no, Project codes not stated in paper and manual mask construction and spiral fitting limit exact redo.

## Links

- Method: (cite: 2014ApJ...785L..12C) (median-stacking of peak maps)
- Method: (cite: 2016ApJ...831...16L) (ALMA spectral response)
- Companion: (cite: 2018ApJ...859...21A) (earlier ALMA Lupus survey)
- Companion: (cite: 2018ApJ...869L..41A) (DSHARP)
- Related: DSHARP
- Related: DARTTS-S
- Related: ALMA Lupus survey

## Checks

```json
{
 "quotes": 73,
 "quotes_ok": 73,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2016.1.00484.L",
  "2018.1.01201.S"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 11,
 "numeric_problems": 0,
 "fill": {
  "facts": 77,
  "stated": 53,
  "rate": 0.688
 },
 "evidence_ok": true
}
```
