# exoALMA. X. Channel Maps Reveal Complex <SUP>12</SUP>CO Abundance Distributions and a Variety of Kinematic Structures with Evidence for Embedded Planets

`2025ApJ...984L..15P` | The Astrophysical Journal Letters 2025 | first author: Pinte, Christophe | arXiv: 2504.18717 | DOI: 10.3847/2041-8213/adc433

Card schema 1.0 | model claude-sonnet-5-5 | depth full | type large_program_or_survey

## Science

- Fields: protoplanetary_disks, astrochemistry, exoplanets
- Question: What kinematic substructures and CO abundance distributions appear in individual 12CO J=3-2 channel maps of the 15 exoALMA disks, and are they consistent with embedded planets?  
  > "In this paper, we extend the analysis to individual channel maps, which provide a complementary approach by isolating specific velocity channels across the emission line profiles." (Introduction)
- Target **15 exoALMA disks (MWC 758, HD 135344B, CQ Tau, J1604, AA Tau, SY Cha, J1842, J1615, LkCa 15, HD 143006, J1852, DM Tau, HD 34282, V4046 Sgr, PDS 66)**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2021.1.01123.L
- bands: _not stated_
- frequencies and spectral setup: 12CO J=3-2 cubes; velocity resolution ≈26 m/s; binned 28 to 200 m/s  
  > "With a velocity resolution of $\approx 26\mathrm{m\,s}^{-1}$ and spatial resolution of $\approx 0.1\ensuremath{''}$" (Introduction)
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: ≈0.1'' native; inspected 0.1'' to 0.3''; 0.25'' for faint emission  
  > "We inspected the $^{12}$CO $J=3-2$ exoALMA data cubes at various spatial ($0.1\ensuremath{''}$ to $0.3\ensuremath{''}$) and spectral (28 to 200 m/s) resolutions" (Observations and Imaging)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated)
- External data: Gardner et al. higher-resolution LkCa 15 imaging with extra velocity kink  
  > "(cite: Gardner_exoALMA) detected an additional velocity kink at the systemic velocity at a separation of $\lesssim 0.1\ensuremath{''}$" (Comparison with Data) [from (cite: Gardner_exoALMA)]
- Simulation/model as data: phantom SPH + mcfost models with a planet of 1, 2, 5 or 10 MJup per disk  
  > "we embedded a single planet at the projected location of the detected primary kinks with an initial mass of 1, 2, 5, or 10 M$_\mathrm{Jup}$" (Modeling)

## Processing

### Calibration

- pipeline or manual: _not stated_
- casa version: _not stated_
- pipeline version: _not stated_
- archive products used as is: _not stated_
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
- continuum subtraction: Cubes imaged without continuum subtraction; checked that kinematic deviations also appear in continuum-subtracted maps  
  > "we imaged all the channel maps without continuum subtraction, and checked that the detected kinematic deviations are also present in the corresponding continuum-subtracted maps." (Observations and Imaging)
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: _not stated_
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- Standard exoALMA imaging procedure, with additional weighting schemes and spectral binning  
  > "we also reimaged the visibilities using the standard exoALMA imaging procedure (cite: Loomis_exoALMA)" (Observations and Imaging) [from (cite: Loomis_exoALMA)]
- Regularized maximum likelihood reimaging for selected disks  
  > "reimaged using regularized maximum likelihood imaging instead of CLEAN (cite: Zawadzki_exoALMA)" (Observations and Imaging) [from (cite: Zawadzki_exoALMA)]
- CO abundance prescription for freeze-out, photodissociation and photodesorption  
  > "We set the CO abundance following the prescription in Appendix B of (cite: Pinte2018a)" (Modeling) [from (cite: Pinte2018a)]

### Not stated but needed to reproduce (our reading)

- Weighting schemes (robust, taper) and exact channel binning for each disk's reimaged cubes
- Which channels are shown for each disk
- Exact dynamite fitting setup and uncertainties
- Criteria for the visual classification
- Beam and noise for the Figure 6 cubes
- Planet-wake projection details
- Specific depletion factor grid values
- Number of mcfost photons and grid setup

## Analysis recipe

1. **Reimage cubes and inspect channel maps**: Reimaged exoALMA visibilities at several resolutions and binnings without continuum subtraction, and checked against continuum-subtracted maps and regularized maximum likelihood imaging  
  > "we imaged all the channel maps without continuum subtraction, and checked that the detected kinematic deviations are also present in the corresponding continuum-subtracted maps." (Observations and Imaging)
   - software: CASA
   - fitting: _not stated_
   - validation: Compared CLEAN, continuum-subtracted and regularized maximum likelihood images  
  > "confirming that the detections presented here are not artifacts of the imaging process." (Observations and Imaging)
2. **Overlay Keplerian isovelocity curves and classify structures**: Used dynamite to extract geometry, stellar mass and emission-layer height, then visually classified deviations  
  > "We used the code dynamite (cite: Pinte2018a) to extract the disk’s geometric parameters (outer radius, inclination, position angle (PA), and systemic velocity, and stellar masses)" (A Variety of Kinematic Substructures)
   - software: dynamite
   - assumption: Keplerian rotation  
  > "assuming the disks are in Keplerian rotation" (A Variety of Kinematic Substructures)
   - fitting: _not stated_
   - validation: Parameters consistent with discminer values and emission surfaces from Galloway et al.  
  > "We verified that all those parameters are consistent with the values derived with discminer by (cite: Izquierdo_exoALMA)" (A Variety of Kinematic Substructures)
3. **Hydrodynamical planet simulations**: 3D gas-only SPH with phantom, 10^6 particles, 20 orbits, then each particle split into 13 and evolved 2 more orbits  
  > "We used $10^6$ particles and evolved the system for 20 planet orbits" (Modeling)
   - software: phantom
   - parameter: alpha_av = 0.2; inner radius 5 au; H/R=0.1 at 50 au; gamma=0.8; accretion radius 0.125 Hill radius  
  > "we set the shock viscosity to $\alpha_{\rm av} = 0.2$" (Modeling)
   - assumption: Vertically isothermal; self-gravity neglected; disk mass 5e-3 Msun  
  > "We neglect self-gravity and use a disk mass of $5 \times 10^{-3} \, \mathrm{M}_\odot$ for all disks" (Modeling)
   - fitting: No formal fit; restricted grid of planet masses  
  > "Our aim is not to develop a detailed model for each source; instead, we test, through a restricted exploration of the parameter space, whether a single planet can reasonably explain the observed channel maps." (Modeling)
   - validation: phantom+mcfost benchmarked by Bae et al.  
  > "The combination of phantom and mcfost was benchmarked and validated by (cite: Bae_exoALMA)." (Modeling)
4. **Radiative transfer synthetic CO channel maps**: mcfost for dust temperature and CO maps with Voronoi cells matched to SPH particles; Tgas=Tdust, LTE  
  > "We postprocessed the models with the radiative transfer code mcfost (cite: Pinte2006; Pinte2009) to compute the dust temperature structure and CO maps" (Modeling)
   - software: mcfost, pymcfost
   - parameter: 12CO abundance 1e-4 relative to H in warm layer; depleted below 20 K by a variable factor  
  > "Below 20 K, we deplete this abundance by a factor that we allow to vary" (Modeling)
   - assumption: Astrosilicate grains, dn ∝ a^-3.5 da, 0.03-1000 micron, gas-to-dust 100; zero turbulent velocity; 1 Myr isochrones  
  > "a uniform gas-to-dust ratio of 100" (Modeling)
   - fitting: _not stated_
   - validation: Visual comparison of kink shape and amplitude with data  
  > "The planet model matches the observations well for LkCa 15, J1615, and J1842, in terms of both shape and amplitude of the kink." (Comparison with Data)
5. **Compare models to data and constrain planet mass and CO depletion**: Visual comparison of the channel with the most visible kink; compared depletion factors in Fig. 8  
  > "For each source, we compare the channel where the velocity kink is most visible to our synthetic models." (Comparison with Data)
   - fitting: No formal fit  
  > "We do not attempt to precisely match the brightness of the emitting upper and lower surfaces or the midplane." (Comparison with Data)
   - validation: Depletion varied for a single hydrodynamical model only; range indicative  
  > "We note that this range is only indicative, as we varied the freeze-out fraction for a single hydrodynamical model" (Comparison with Data)

## Software

- **CASA** : listed in software section; imaging  
  > "casa (cite: casa)" (Software)
- **casa_cube** : listed in software section  
  > "casa_cube (cite: casa_cube)" (Software)
- **dynamite** : geometry and emission surface extraction  
  > "We used the code dynamite (cite: Pinte2018a)" (A Variety of Kinematic Substructures)
- **phantom** : SPH hydrodynamical simulations  
  > "We performed 3D gas-only simulations with the Smoothed Particle Hydrodynamics (SPH) code phantom (cite: Price2018)." (Modeling)
- **mcfost** : radiative transfer  
  > "We postprocessed the models with the radiative transfer code mcfost" (Modeling)
- **pymcfost** : listed in software section  
  > "pymcfost (cite: pymcfost)" (Software)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Disks with velocity deviations in channel maps | 13 of 15 | not stated | disks | 2 | We visually detect velocity deviations in $^{12}$CO channel maps in 13 of the 15 exoALMA objects. |
| Planet orbital radii | 80-310 | not stated | au | 5 | suggests planets with orbital radii between 80 and 310 au and masses between 1 and 5 M$_\mathrm{Jup}$. |
| Planet masses (AA Tau, J1615, LkCa 15 / SY Cha / J1842) | 2 / 5 / 1 | not stated | MJup | 5 | best reproduced with a planet mass of 2 M$_\mathrm{Jup}$ for LkCa 15, AA Tau, and J1615, 5 M$_\mathrm{Jup}$ for SY Cha, and 1 M$_\mathrm{Jup}$ for J1842. |
| Midplane 12CO depletion factor | 1e-3 to 1e-2 | indicative range | dimensionless | 5 | with a depletion factor of $\approx 10^{-3}$ – $10^{-2}$ compared to the warm molecular layer. |
| Lower limit on planet mass detectable by kinematics | ≈1 | not stated | MJup | 5 | currently sets the lower limit for the kinematic detection of planets to $\approx$ 1 M$_\mathrm{Jup}$. |

## Qualitative findings

- Midplane 12CO emission is detected between surfaces in 7 disks with favorable inclination, and CO desorption is seen in outer regions  
  > "The vertical CO snowline is clearly detected in seven disks where the upper and lower emission surfaces are well separated." (Conclusions)

## Claim tuples

- H: Kinematic kinks in exoALMA disks are caused by embedded planets | E: phantom+mcfost single-planet models compared to channel maps | R: Planets of 1-5 MJup at 80-310 au reproduce the kinks in several disks; 10 MJup too strong | F: Six disks show signatures consistent with planet wakes, though models are imperfect | **partially**
- H: CO is not fully frozen out in the midplane | E: Examined emission between upper and lower surfaces and compared with models of varied depletion | R: Non-zero midplane emission; depletion 1e-3 to 1e-2 fits better than full or no freeze-out | F: Partial freeze-out and outer-disk desorption | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Alternatives to planets (MRI, GI, VSI, buoyancy spirals, vertical thermal structure) are discussed but not tested  
  > "Other physical processes can also produce deviations from Keplerian rotation, including magneto-rotational instability (MRI), GI, and vertical shear instability" (Discussion)
- How they decided it was enough: _not stated_
- Limitation (authors): Classification is subjective and inclination-biased  
  > "Our classification is subjective, and some sources clearly exhibit multiple types of substructures." (A Variety of Kinematic Substructures)
- Limitation (authors): Vertically isothermal assumption is a major limitation  
  > "One major limitation of our models is the assumption of a vertically isothermal profile in phantom." (Discussion)
- Caveat (inferred, ours): Planet detection is by visual comparison with no quantitative fit or uncertainty
- Caveat (inferred, ours): Planet masses degenerate with other kinematic structures and a single-planet model
- Caveat (inferred, ours): Depletion constraint from a single hydrodynamical model
- Caveat (inferred, ours): Disk masses rescaled ad hoc

## Reproducibility

- Data public (paper): Models are public; ALMA data are from an ALMA Large Program  
  > "The phantom and mcfost models are available in (cite: DVN/H5QUQT_2025)." (Modeling)
- Products in archive: _not stated_
- Code: phantom and mcfost models in Harvard Dataverse  
  > "The phantom and mcfost models are available in (cite: DVN/H5QUQT_2025)." (Modeling)
- Missing: Imaging parameters for each reimaged cube
- Missing: Visual classification criteria
- Missing: Full simulation inputs beyond the released models
- Data volume (inferred): Hundreds of GB for 15 disks' calibrated exoALMA cubes; simulations are additional compute
- Score (inferred): 3/5, Data and models are available, but classification and model comparison are qualitative and imaging details are inherited.
- Rediscovery candidate: no, Main results are qualitative visual classifications and a restricted model comparison, not a numeric recipe.

## Links

- Method: (cite: Loomis_exoALMA) (standard exoALMA imaging)
- Method: (cite: Pinte2018a) (dynamite and CO abundance prescription)
- Method: (cite: Bae_exoALMA) (phantom+mcfost benchmark)
- Companion: (cite: Teague_exoALMA) (exoALMA overview)
- Companion: (cite: Izquierdo_exoALMA) (integrated maps and discminer parameters)
- Companion: (cite: Galloway_exoALMA) (emission surfaces)
- Related: exoALMA Large Program

## Checks

```json
{
 "quotes": 48,
 "quotes_ok": 48,
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
  "facts": 79,
  "stated": 38,
  "rate": 0.481
 },
 "evidence_ok": true
}
```
