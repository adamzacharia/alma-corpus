# Exploring the dust grain size and polarization mechanism in the hot and massive Class 0 disk IRAS 16293-2422 B

`2024A&A...682A..56Z` | Astronomy and Astrophysics 2024 | first author: Zamponi, Joaquin | arXiv: 2311.02521 | DOI: 10.1051/0004-6361/202244628

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: star_formation, protoplanetary_disks
- Question: How do different maximum grain sizes and carbon sublimation change the continuum and self-scattering polarization of a hot, massive Class 0 disk model, and can they reproduce IRAS 16293 B observations?  
  > "We aim to investigate the effects of changing the maximum grain sizes in the resultant continuum and continuum polarization fractions from self-scattering for a hot and massive Class 0 disk" (abstract)
- Target **IRAS 16293-2422 B**: coordinates _not stated_; z/distance 141 pc  
  > "it is one of the closest and brightest protostars at a distance of 141 pc (cite: Dzib2018)" (Introduction); distance from Dzib2018  
  > "it is one of the closest and brightest protostars at a distance of 141 pc (cite: Dzib2018)" (Introduction)

## Data provenance

- ALMA projects: 2015.1.01112.S, 2017.1.01247.S, 2016.1.00457.S
- bands: ALMA Band 6 (1.3 mm), Band 3 (3 mm), JVLA Q (7 mm), Ka (9 mm), Ku (18 mm)  
  > "1.3 mm (ALMA Band 6), 3 mm (ALMA Band 3) and 7 mm (JVLA Band Q)" (2.1 ALMA & VLA archival data)
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: Band 6 Stokes I 0.114"x0.069"; polarization 0.18"x0.09"; Band 3 0.048"x0.046"  
  > "with a beam size of 0.048"$\times$0.046" and a noise level of 17$\,\mu$Jy beam$^{-1}$ (0.95 K)" (2.1 ALMA & VLA archival data)
- max recoverable scale: _not stated_
- sensitivity: Band 6 Stokes I 104 uJy/beam; Band 3 17 uJy/beam; Ka 16 uJy/beam; Ku 47 uJy/beam  
  > "a noise level of 104$\,\mu$Jy beam$^{-1}$ (0.3 K" (2.1 ALMA & VLA archival data)
- time on source: _not stated_
- observing dates: Ka: 7 March 2022; Ku: 2, 4, 5 January 2021  
  > "Band Ka observations were carried out on March 7, 2022 (project code: 22A-322, PI: Zamponi)." (2.2 VLA Band Ka & Ku observations)
- pi or archival as stated: _not stated_
- Other facility **JVLA**: Ka (9 mm) and Ku (18 mm) continuum, Q-band 7 mm polarization  
  > "We present JVLA standard continuum mode observations at Ka (9 mm) and Ku band (18 mm) toward IRAS 16293-2422 B" (2.2 VLA Band Ka & Ku observations)
- External data: Public Band 6 Stokes I, Q, U polarization images  
  > "we used publicly available Stokes I, Q and U images by (cite: Sadavoy2018)" (2.1 ALMA & VLA archival data) [from Sadavoy2018]
- External data: Optical constants of astronomical silicate and graphite  
  > "The optical constants[^3] for both materials were obtained from (cite: Draine2003a) and (cite: Draine2003b), respectively." (3.4 Composition) [from Draine2003a; Draine2003b]
- External data: Refractory organics (CHON) optical constants  
  > "we use the optical constants from amorphous carbon (CHON) from (cite: Henning1996)" (4.2) [from Henning1996]
- Simulation/model as data: SPH radiation-hydrodynamic core collapse snapshot at 18.2 kyr (disk ~0.3 Msun) from sphNG, from Zamponi2021  
  > "The disk is obtained from a simulation snapshot at a stage 18.2 kyr after the collapse of a 1 M$_{\odot}$ spherical and isothermal cloud" (3.1 Protostellar disk model)

## Processing

### Calibration

- pipeline or manual: Ka: standard VLA Pipeline; Ku: manual standard calibration  
  > "We calibrated the data using the standard VLA Pipeline (v2021.2.0.128)" (2.2 VLA Band Ka & Ku observations)
- casa version: Ka: CASA 6.2.1.7; Ku: CASA 5.6.2  
  > "We manually followed the standard data calibration strategy using CASA (release 5.6.2)." (2.2 VLA Band Ka & Ku observations)
- pipeline version: _not stated_
- archive products used as is: _not stated_
- flux calibrator: _not stated_
- flux scale uncertainty: _not stated_
- self calibration: Ka: iterative phase-only self-calibration  
  > "We performed phase-only self-calibration iteratively in CASA." (2.2 VLA Band Ka & Ku observations)

### Imaging

- task: _not stated_
- deconvolver: Ka: mtmfs, scales 0, 1, 3 beams; Ku: nterm=1  
  > "the cleaning was done with the deconvolver `mtmfs`, a robust parameter of 0.5 and scales 0, 1 and 3 beams" (2.2 VLA Band Ka & Ku observations)
- weighting robust: Ka robust 0.5; Ku robust 0  
  > "The Briggs Robust$=$0 weighted image achieved a noise level of 47 $\mu$Jy beam$^{-1}$" (2.2 VLA Band Ka & Ku observations)
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
- final beam: Ka 0.12"x0.05"; Ku 0.23"x0.094"  
  > "The final image has a resolution of 0$''$.12$\times$0$''$.05 (P.A.$=$-23.11$^{\circ}$)" (2.2 VLA Band Ka & Ku observations)
- final rms: _not stated_

### Inherited from earlier work

- ALMA Band 6 and 3 observations, calibration and imaging  
  > "We refer the reader to (cite: Zamponi2021) for more information about the high-resolution ALMA observations at bands 6 and 3 as well as their calibration and imaging." (2.1 ALMA & VLA archival data) [from Zamponi2021]
- JVLA Q-band polarization observations, calibration and imaging  
  > "we refer to (cite: Liu2018b) for the details on the observations, calibration and imaging of the polarized data at the JVLA band Q" (2.1 ALMA & VLA archival data) [from Liu2018b]

### Not stated but needed to reproduce (our reading)

- Grain size distribution power-law slope q
- Synthetic observation array configurations, integration times and tclean parameters
- Disk inclination and orientation used in radiative transfer
- Number of RADMC3D grid cells and grid extent
- Calibration and imaging details of Band 6/3 ALMA data are only in Zamponi2021
- Mass-loss factor details for sublimated dust-to-gas ratio

## Analysis recipe

1. **Build dust opacity tables**: BHMIE Mie opacities per material, integrated over a power-law size distribution, summed weighted by mass fractions (DustMixer)  
  > "we calculated opacities per material and combined them as a sum weighted by their mass fractions" (The DustMixer)
   - software: Synthesizer, DustMixer
   - parameter: a_min = 0.1 um; a_max = 10, 100, 1000 um; 62.5% silicate + 37.5% graphite  
  > "corresponding to spherical grains with a minimum size of 0.1 $\mu$m" (3.3 Grain sizes)
   - assumption: Spherical grains; gas-to-dust ratio 100; dust temperature equals gas temperature  
  > "We assume a homogeneous gas to dust density ratio of 100." (3.1 Protostellar disk model)
   - fitting: _not stated_
   - validation: _not stated_
2. **Radiative transfer of the SPH disk**: Interpolate SPH particles to Cartesian grid, run RADMC3D with full Mie scattering in all four Stokes  
  > "We have performed radiative transfer calculations in all four Stokes components (I, Q, U, V) using the radiative transfer code RADMC3D" (3.5)
   - software: RADMC-3D, Synthesizer
   - parameter: Carbon sublimation at 300 K (also 500 K) with 50% and 80% organics tested  
  > "set a sublimation temperature of 300 K" (4.2)
   - fitting: _not stated_
   - validation: Convergence of scattering Monte Carlo reached at about 1e10 photons  
  > "The convergence was reached at about 10$^{10}$ photons." (3.5)
3. **Synthetic observations**: CASA simobserve and tclean using the setups of real observations, with thermal noise; PI debiased  
  > "Synthesizer uses the CASA (v5.6.2) software and its SIMOBSERVE and TCLEAN tasks to produce a synthetic image from a model image" (3.6 Synthetic observations)
   - software: CASA, Synthesizer
   - parameter: Vectors masked where I/sigma_I<3 and PI/sigma_PI<3  
  > "we mask out the vectors at locations where $\mathrm{I}/\sigma_{\rm I}<3$ and $PI/\sigma_{\rm PI}<3$" (3.6 Synthetic observations)
   - fitting: _not stated_
   - validation: Model noise levels comparable to real observations  
  > "lead to noise levels comparable to the real observations" (3.6 Synthetic observations)
4. **Compare models to observations**: Compare east-west brightness temperature cuts, spectral index maps, and polarization fractions between models and data (visual comparison)  
  > "We extracted a cut of the brightness temperature maps along the east-west axis and plotted it as a function of physical offset from the peak" (4.1)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **Synthesizer** : New tool to automate gridding, RADMC3D, and CASA synthetic observations  
  > "we have developed a new tool called SYNTHESIZER, which we have made publicly available" (3.2)
- **RADMC-3D** : Monte Carlo radiative transfer incl. polarized scattering  
  > "We have used the RADMC3D radiative transfer code (cite: radmc3d)" (3.1 Protostellar disk model)
- **CASA** 5.6.2 (synthetic obs); 6.2.1.7 (Ka); 5.6.2 (Ku): VLA calibration/imaging and synthetic observations  
  > "Synthesizer uses the CASA (v5.6.2) software and its SIMOBSERVE and TCLEAN tasks" (3.6 Synthetic observations)
- **sphNG** : SPH simulation of core collapse (from earlier work)  
  > "simulated using the smoothed-particle-hydrodynamics (SPH) code `sphNG` (cite: Bate1995)" (3.1 Protostellar disk model)
- **APLpy** : Plotting  
  > "This research made use of APLpy, an open-source plotting package for Python" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Optical depth range 1.3 to 18 mm | 130 to 2 | not stated | dimensionless | 2 | Optical depths are in the range of 130 to 2 from 1.3 to 18 mm, respectively. |
| Max polarization fraction from self-scattering at 1.3 mm (a_max=100 um) | ~0.1 | not stated | percent | 2 | The polarization fraction produced by self-scattering reaches a maximum of $\sim$0.1% at 1.3 mm for a maximum grain size of 100 $\mu$m |
| Flux difference with vs without sublimation | <10 | not stated | percent | 2 | The difference in the fluxes with and without sublimation are small ($<10$%). |
| Proper motion of IRAS 16293 B | RA -11.8, DEC -19.7 | 0.3, 1.3 | mas/yr | 0 | The applied correction is RA: $-11.8 \pm 0.3$ mas/yr and DEC: $-19.7 \pm 1.3$ mas/yr. |

## Qualitative findings

- Models with a_max 100-1000 um match observed Stokes I central fluxes within a factor of 2; grain growth in the inner sootline improves match  
  > "the observed Class 0 disk fluxes lie between the models with $a_{\rm max}=100\,\mu$m and 1000 $\mu$m, with differences between the observations and models within a factor of up to 2" (4.1)

## Claim tuples

- H: Significant grain growth is present in IRAS 16293 B | E: Synthetic Stokes I observations at 1.3-18 mm for a_max 10, 100, 1000 um vs. data | R: Observed central fluxes lie between a_max=100 and 1000 um models | F: Significant grain growth could be present, esp. in the inner hot region | **supported**
- H: Self-scattering explains the observed 2-4% polarization at 1.3 and 7 mm | E: Full Mie RADMC3D polarization models and synthetic observations | R: Model fractions <~0.1-0.5%, Q and U undetectable in synthetic observations | F: Self-scattering is too weak; other mechanisms needed | **refuted**
- H: Carbon sublimation in the sootline alters continuum fluxes | E: Models with refractory organics removed at T>=300 K | R: Small flux differences (<10%) | F: Hard to detect sublimation with continuum alone | **supported**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Dichroic extinction, polarization reversal by elongated grains, and grain alignment (RAT/MET) remain untested alternatives  
  > "effects like dichroic extinction or polarization reversal of elongated aligned grains remain other possible but untested scenarios" (abstract)
- How they decided it was enough: _not stated_
- Limitation (authors): Disk model lacks the east-west asymmetry of the observed source, so outskirts are overpredicted  
  > "This east-west difference is because our disk model does not have such a marked east-west asymmetry as the one observed in IRAS 16293 B" (4.1)
- Caveat (inferred, ours): Single simulation snapshot, not fitted to the source; comparison is qualitative
- Caveat (inferred, ours): Only spherical compact grains and one power-law size distribution
- Caveat (inferred, ours): Degeneracy between temperature structure and grain size not quantified
- Caveat (inferred, ours): No uncertainty estimates for model-observation comparisons

## Reproducibility

- Data public (paper): Band 6 polarization images stated publicly available; Synthesizer code public  
  > "we used publicly available Stokes I, Q and U images by (cite: Sadavoy2018)" (2.1 ALMA & VLA archival data)
- Products in archive: _not stated_
- Code: Synthesizer released at github.com/jzamponi/synthesizer and PyPI astro-synthesizer  
  > "we have developed a new tool called SYNTHESIZER, which we have made publicly available" (3.2)
- Missing: SPH simulation snapshot (from Zamponi2021) availability not stated
- Missing: Details of ALMA Band 6/3 processing deferred to Zamponi2021
- Missing: Synthetic observing parameters only in repository scripts
- Data volume (inferred): Tens of GB for ALMA and VLA visibilities; simulation data additional
- Score (inferred): 3/5, Code is public but the simulation input and key observing/imaging details are deferred to other papers; results are largely qualitative comparisons.
- Rediscovery candidate: no, Depends on a simulation snapshot and inherited processing; main results are comparisons, not mostly numeric.

## Links

- Method: Zamponi2021 (Disk model, ALMA Band 6/3 observations, calibration and imaging)
- Method: Liu2018b (VLA Q-band polarization data processing)
- Companion: Sadavoy2018 (Source of the 1.3 mm polarization data)

## Checks

```json
{
 "quotes": 51,
 "quotes_ok": 51,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 3,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 4,
 "numeric_problems": 0,
 "fill": {
  "facts": 75,
  "stated": 40,
  "rate": 0.533
 },
 "evidence_ok": true
}
```
