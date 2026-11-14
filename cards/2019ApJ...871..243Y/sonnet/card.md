# JCMT POL-2 and ALMA Polarimetric Observations of 6000-100 au Scales in the Protostar B335: Linking Magnetic Field and Gas Kinematics in Observations and MHD Simulations

`2019ApJ...871..243Y` | The Astrophysical Journal 2019 | first author: Yen, Hsi-Wei | arXiv: 1901.00242 | DOI: 10.3847/1538-4357/aafb6c

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type multi_facility_alma_minor

## Science

- Fields: star_formation
- Question: How do magnetic field strength and field-matter coupling in the Class 0 protostar B335, inferred from JCMT/ALMA polarimetry compared with MHD simulations, relate to the observed gas kinematics?  
  > "Therefore, linking observational results of magnetic field structures and gas kinematics could shed light on the role of the magnetic field in the dynamics of collapsing cores." (Introduction)
- Target **B335**: coordinates _not stated_; z/distance 100 pc  
  > "B335 is an isolated Bok globule with an embedded Class 0 protostar at a distance of 100 pc" (Introduction); distance from Keene80; Keene83; Stutz08; Olofsson09  
  > "B335 is an isolated Bok globule with an embedded Class 0 protostar at a distance of 100 pc" (Introduction)

## Data provenance

- ALMA projects: 2013.1.01380.S
- bands: ALMA 1.3 mm polarimetry; JCMT POL-2 850 um (450 um not used)  
  > "The ALMA polarimetric data at 1.3 mm analyzed here were retrieved from the archive" (2.2 ALMA observations)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ALMA 0.67'' x 0.47'' (~70 x 50 au); JCMT 14'' at 850 um  
  > "The achieved angular resolution is 0.67$''$ $\times$ 0.47$''$ ($\sim$70 au $\times$ 50 au)." (2.2 ALMA observations); "The angular resolution of JCMT at 850 $\mu$m is 14$\ensuremath{''}$." (2.1 JCMT POL-2 observations)
- max recoverable scale: _not stated_
- sensitivity: ALMA: 50 uJy Stokes I, 15 uJy Q and U; JCMT: 1.6 mJy/beam I, 1.5 mJy/beam Ip at 12'' pixels  
  > "The achieved noise level is 50 $\mu$Jy in Stokes *I* and 15 $\mu$Jy in both Stokes *Q* and *U*." (2.2 ALMA observations); "The achieved noise level is 1.6 mJy Beam$^{-1}$ in Stokes *I* and 1.5 mJy Beam$^{-1}$ in the polarized intensity" (2.1 JCMT POL-2 observations)
- time on source: JCMT 6.8 hours on source  
  > "The total on-source observing time was 6.8 hours." (2.1 JCMT POL-2 observations)
- observing dates: JCMT: 18 April, 5 and 12 May 2017  
  > "The observations with the JCMT were conducted on April 18 and May 5 and 12 in 2017." (2.1 JCMT POL-2 observations)
- pi or archival as stated: ALMA archival; JCMT new observations (M17AP067)  
  > "The JCMT data were obtained under program ID M17AP067." (Acknowledgements)
- Other facility **JCMT POL-2/SCUBA-2**: 850 um polarimetric maps of 6000 au scale field  
  > "Polarized continuum emission was observed at 850 $\mu$m and 450 $\mu$m simultaneously with the polarimeter POL-2" (2.1 JCMT POL-2 observations)
- External data: Gas kinematics (rotation and infall velocities, disk radius upper limit 10 au) from SMA/ALMA used to compare with simulations  
  > "put an upper limit of the disk radius of 10 au in B335" (5.2) [from (cite: Yen15b)]
- External data: Core rotation angular speed 4e-14 s^-1 from single-dish velocity gradients  
  > "The angular speed of its solid-body rotation is adopted to be $4\times10^{-14}$ s$^{-1}$" (3.1 Simulation setup) [from (cite: Saito99; Yen11; Kurono13)]
- External data: Magnetic field strength 10-40 uG on 0.1 pc scale  
  > "observational estimate of 10–40 $\mu$G on a 0.1 pc scale in B335" (3.1 Simulation setup) [from (cite: Bertrang14)]
- Simulation/model as data: 3D ZeusTW (non-)ideal MHD collapse models of a 1 Msun uniform rotating core, lambda = 2.4, 4.8, 9.6, MRN/tr-MRN, CR1/CR5/CR10, plus 15 deg misaligned runs; synthetic polarization with SPARX  
  > "we carried out three-dimensional (3D) non-ideal MHD simulations using ZeusTW code (cite: Krasnopolsky10) to model the collapse of a magnetized non-turbulent dense core" (3 MHD simulations)

## Processing

### Calibration

- pipeline or manual: Archive calibration script, plus phase self-calibration  
  > "We reduced the data with the calibration script provided in the archive using the software Common Astronomy Software Applications (cite: McMullin07) of version 4.7.0, and we further performed self calibration on the phase." (2.2 ALMA observations)
- casa version: CASA 4.7.0  
  > "of version 4.7.0" (2.2 ALMA observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: phase self-calibration (details not stated)  
  > "we further performed self calibration on the phase" (2.2 ALMA observations)

### Imaging

- task: _not stated_
- deconvolver: _not stated_
- weighting robust: Briggs, robust = 0.5  
  > "The images were generated with Briggs weighting with a robust parameter of 0.5." (2.2 ALMA observations)
- uv taper: _not stated_
- cell size: Q/U binned to 0.35'' pixels (ALMA); JCMT binned 4'' to 12''  
  > "We binned up the Stokes *Q* and *U* maps to have a pixel size of 0.35$''$" (2.2 ALMA observations)
- image size: _not stated_
- masking: _not stated_
- multiscale scales: _not stated_
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: 0.67'' x 0.47''  
  > "The achieved angular resolution is 0.67$''$ $\times$ 0.47$''$" (2.2 ALMA observations)
- final rms: 50 uJy (I), 15 uJy (Q,U)  
  > "The achieved noise level is 50 $\mu$Jy in Stokes *I* and 15 $\mu$Jy in both Stokes *Q* and *U*." (2.2 ALMA observations)

### Inherited from earlier work

- Details of the ALMA observations  
  > "The details of the ALMA observations were described in (cite: Maury18)." (2.2 ALMA observations) [from (cite: Maury18)]
- Radiative transfer dust properties and Stokes formulation in SPARX  
  > "SPARX adopts the properties of dust grains and formulization in (cite: Lee85) to compute Stokes parameters and generate synthetic images." (4 Comparison between simulations and observations) [from (cite: Lee85)]
- Ambipolar diffusivity computed with equilibrium chemical network  
  > "computed at run-time using the equilibrium chemical network from (cite: Zhao16)" (3.1 Simulation setup) [from (cite: Zhao16)]

### Not stated but needed to reproduce (our reading)

- ALMA execution block / array configuration details and observing dates (deferred to Maury18)
- Self-calibration solution intervals and number of iterations
- Spectral windows used for the continuum image, clean threshold, masking, image size
- Exact criteria/code for extracting polarization segments and comparing PA distributions
- Simulation numerical resolution, sink prescription, and ZeusTW/SPARX configuration files
- How beta_rot was reduced in the lower-beta_rot simulations
- POL-2 pol2map parameter files and masks

## Analysis recipe

1. **Reduce JCMT POL-2 data to Stokes IQU and detect polarization**: Starlink pol2map with makemap then skyloop; debiased Ip; binned to 12'' pixels  
  > "Then, the final Stokes *IQU* maps were generated with the procedure *skyloop*, and the polarized intensity was debiased in this process." (2.1 JCMT POL-2 observations)
   - software: Starlink, pol2map
   - parameter: Detection criteria Ip/dIp > 3 and Stokes I S/N > 5  
  > "$I_{\rm p}/\Delta I_{\rm p} >3$, and the S/N in Stokes *I* larger than 5" (2.1 JCMT POL-2 observations)
   - fitting: _not stated_
   - validation: Compared with SCUPOL results and outflow direction  
  > "The mean orientation of the magnetic field is consistent with the direction of the outflow having a PA of 90$\ensuremath{^\circ}$–99$\ensuremath{^\circ}$" (2.3 Observational results)
2. **Image ALMA archival polarization data**: Archive script calibration in CASA 4.7.0, phase self-cal, Briggs robust 0.5 imaging, debiased Ip, binned Q/U to 0.35''  
  > "We debiased $I_{\rm p}$ with $I_{\rm p} = \sqrt{Q^2 + U^2 - {\sigma_{Q,U}}^2}$" (2.2 ALMA observations)
   - software: CASA
   - parameter: Detection: Stokes I S/N > 3 and Ip/dIp > 3  
  > "Our detection criteria of the polarized emission are S/N higher than 3 in Stokes *I* and $I_{\rm p}/\Delta I_{\rm p} > 3$." (2.2 ALMA observations)
   - fitting: _not stated_
   - validation: _not stated_
3. **Run MHD collapse simulations**: ZeusTW 3D ambipolar-diffusion and ideal MHD of a 1 Msun, 1e17 cm uniform core, rotating at 4e-14 s^-1; vary lambda, grain size, CR rate; snapshots at M*+disk 0.04/0.1 (ideal: 0.02) Msun  
  > "the initial core was set to have a total mass of 1.0 $M_{\ensuremath{\odot}}$ and an outer radius of $10^{17}$ cm (6684 au)" (3.1 Simulation setup)
   - software: ZeusTW
   - parameter: B0 = 42.5, 21.3, 10.2 uG giving lambda = 2.4, 4.8, 9.6  
  > "This gives a dimensionless mass-to-flux ratio $\lambda$" (3.1 Simulation setup)
   - assumption: Non-turbulent, axisymmetric initial condition; only ambipolar diffusion considered  
  > "we only consider ambipolar diffusion (AD)" (3.1 Simulation setup)
   - fitting: _not stated_
   - validation: _not stated_
4. **Generate synthetic polarization maps and compare orientations**: SPARX Stokes IQU at 850 um and 1.3 mm, convolved with JCMT/ALMA beams, regridded, model PAs extracted at observed detection positions; compared PA distributions  
  > "We convolved the model Stokes *IQU* maps at 850 $\mu$m and 1.3 mm with the beams of the JCMT and ALMA observations, respectively." (4 Comparison between simulations and observations)
   - software: SPARX, CASA simulator
   - assumption: Constant polarization efficiency; no dust scattering; only orientations compared  
  > "the polarization efficiency is assumed to be constant, and we do not consider polarization due to dust scattering" (4 Comparison between simulations and observations)
   - fitting: _not stated_
   - validation: CASA imaging simulations on most/least pinched models show no significant difference in regions with detections  
  > "there is no significant difference between the polarization orientations extracted from the simulated and convolved model maps in the regions where there are ALMA polarization detections" (4 Comparison between simulations and observations)
5. **Compare simulated and observed kinematics**: Compare radial infall and rotation velocity profiles along midplane in simulations to observational estimates  
  > "we compare the radial profiles of the infalling and rotational velocities along the midplane in the simulations and the observational estimates" (5.2)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Starlink** : JCMT POL-2 data reduction  
  > "The data were reduced with the software *Starlink* (cite: Currie14) and the task *pol2map*." (2.1 JCMT POL-2 observations)
- **CASA** 4.7.0: ALMA calibration, self-cal, imaging; imaging simulations  
  > "of version 4.7.0" (2.2 ALMA observations)
- **ZeusTW** : 3D non-ideal MHD simulations  
  > "using ZeusTW code (cite: Krasnopolsky10)" (3 MHD simulations)
- **SPARX** : synthetic Stokes IQU maps  
  > "using the radiative transfer code, Simulation Package for Astronomical Radiative Xfer (SPARX" (4 Comparison between simulations and observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Mean B-field orientation, JCMT (all segments) | 99 | std 20 | deg | 1 | The mean orientation of the magnetic field segments is 99$\ensuremath{^\circ}$ with a standard deviation of 20$\ensuremath{^\circ}$. |
| Mean B-field orientation, JCMT excluding NW segment | 92 | std 12 | deg | 1 | the mean orientation becomes 92$\ensuremath{^\circ}$ with a standard deviation of 12$\ensuremath{^\circ}$ |
| JCMT polarization percentage near center | 0.7 | not stated | % | 1 | The polarization precentage close to the center is 0.7%. |
| Number of JCMT polarization detections | 7 | not stated | dimensionless | 1 | This leads to seven detections |
| Initial rotational-to-gravitational energy beta_rot | 0.4 | not stated | % | 3 | The corresponding ratio of rotational-to-gravitational energy $\beta_{\rm rot}$ is around 0.4%. |
| Disk radius in 9.6tr-MRN-CR1 at M=0.1 Msun | 20-50 | not stated | au | 3 | /  / 9.6 / 1 / 0.1 / 20–50 au / |
| Simulated rotational velocity vs observed, weak field with high CR | factor 4-10 higher | not stated | dimensionless | 5 | higher than those estimated from the observations by a factor of four to ten |

## Qualitative findings

- Persistent disks form only in tr-MRN (a_min=0.1 um) models  
  > "persistent disks only form in the tr-MRN ($a_{\rm min}=0.1~\mu$m) cases" (3.2.1 Disk formation)
- Field pinches more with weaker field, longer evolution, lower diffusion  
  > "the magnetic field lines pinch more severely in a collapsing dense core with weaker magnetic field, longer time evolution, and lower magnetic diffusion" (3.2.2 Pinched magnetic field)

## Claim tuples

- H: Is the 6000 au field in B335 aligned with the outflow and pinched? | E: JCMT POL-2 850 um compared to synthetic maps | R: Mean PA 92 deg (std 12) vs outflow PA 90-99; all models fit equally | F: Field on 6000 au scale is pinched and aligned with outflow; JCMT cannot discriminate field strength | **supported**
- H: What field strength do the ALMA polarization data favor? | E: Compare PA distributions with MHD models | R: Central segments parallel to midplane only in lambda=9.6 at 0.1 Msun | F: Weak field lambda = 9.6 favored by polarimetry | **supported**
- H: Do gas kinematics agree with the weak field? | E: Compare simulated rotation velocities and disk sizes with observations | R: Weak-field models over-rotate and form larger disks | F: Kinematics favor lambda < 4.8; tension with polarimetry, possibly from overestimated beta_rot or scattering | **partially**

## Reasoning

- Why this data: Archival ALMA polarimetry used to study fields from core to inner envelope  
  > "We additionally obtained the ALMA polarimetric data at millimeter wavelength from the public archive" (Introduction)
- Why this method: _not stated_
- Alternative: 15 deg field-rotation misalignment cannot explain NW and SE orientations  
  > "incorporating the misalignment still cannot explain the observed magnetic field orientations in the northwest and the southeast" (4.2)
- How they decided it was enough: _not stated_
- Limitation (authors): Northern and northwestern ALMA patches not reproduced by axisymmetric models  
  > "there are two patches of the magnetic field orientations observed in the north and the northwest that cannot be explained with our MHD simulations" (4.2)
- Limitation (authors): Polarization percentage not compared; no dust scattering in models  
  > "we only compare the polarization orientations from the observations and the synthetic images, and we do not compare the polarization percentage" (4 Comparison between simulations and observations)
- Caveat (inferred, ours): Only qualitative visual comparison of PA distributions; no quantitative fit statistic
- Caveat (inferred, ours): Coarse parameter grid; initial conditions not tuned, degeneracies with beta_rot
- Caveat (inferred, ours): Scattering could bias ALMA polarization near center
- Caveat (inferred, ours): Non-turbulent axisymmetric models vs asymmetric observed source

## Reproducibility

- Data public (paper): ALMA data from public archive; JCMT program M17AP067  
  > "retrieved from the archive (project code: 2013.1.01380.S)" (2.2 ALMA observations)
- Products in archive: _not stated_
- Missing: Simulation outputs and ZeusTW/SPARX setup
- Missing: Detailed self-calibration and polarization extraction parameters
- Data volume (inferred): ~10-50 GB for ALMA polarimetry, plus JCMT raw data
- Score (inferred): 3/5, ALMA and JCMT reductions are reproducible in outline, but the MHD simulations and comparison are hard to repeat without code and parameters.
- Rediscovery candidate: no, Main results depend on custom MHD simulations and qualitative comparison, not purely numeric outputs from public data.

## Links

- Method: (cite: Zhao16) (Non-ideal MHD diffusivity prescription)
- Method: (cite: Krasnopolsky10) (ZeusTW code)
- Companion: (cite: Maury18) (Original ALMA polarimetry of B335)
- Companion: (cite: Yen15b) (B335 gas kinematics used for comparison)

## Checks

```json
{
 "quotes": 61,
 "quotes_ok": 61,
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
  "facts": 80,
  "stated": 47,
  "rate": 0.588
 },
 "evidence_ok": true
}
```
