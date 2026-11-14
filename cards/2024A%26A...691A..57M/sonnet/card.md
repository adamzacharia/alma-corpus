# SPH modelling of AGB wind morphology in hierarchical triple systems and a comparison to observation of R Aql

`2024A&A...691A..57M` | Astronomy and Astrophysics 2024 | first author: Malfait, J. | arXiv: 2408.16565 | DOI: 10.1051/0004-6361/202450844

Card schema 1.0 | model claude-sonnet-5-5 | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: evolved_stars
- Question: How do coplanar hierarchical triple systems shape AGB outflows, and could R Aql's complex wind be shaped by such a system?  
  > "We investigate how triple systems can shape the outflow of Asymptotic Giant Branch (AGB) stars, and characterise the different wind structures that form." (abstract)
- Target **R Aql**: coordinates _not stated_; z/distance 230 pc  
  > "R Aql is an O-rich AGB star that is located at a distance of $230\, {\rm pc}$ from Earth." (5.1 ALMA observation); distance from Decin et al. 2020 (cite: Decin2020)  
  > "R Aql is an O-rich AGB star that is located at a distance of $230\, {\rm pc}$ from Earth." (5.1 ALMA observation)

## Data provenance

- ALMA projects: _none stated_
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: compact, mid and extended; baselines 15-500, 15-1398, 111-13894 m  
  > "three different ALMA antenna array configurations: compact, mid and extended (with baseline ranges of $15-500, 15-1398,$ and $111-13894 \, {\rm m}$ respectively)" (5.1 ALMA observation)
- baselines: _not stated_
- angular resolution: restoring beams 40.7x36.0 mas (continuum), 58.3x49.3 mas (CO cube)  
  > "of ($40.7, 36.0, 22.38$) and ($58.3, 49.3, 25.12$) for the continuum and CO cube, respectively" (5.1 ALMA observation)
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: ATOMIUM ALMA large programme  
  > "R Aql was observed as part of the ATOMIUM ALMA large programme" (5.1 ALMA observation)
- Line: 12CO J=2-1 (not stated)
- External data: R Aql stellar mass (1.6 Msun), mass-loss rate (~1.1e-6 Msun/yr), distance  
  > "Its mass is estimated to $1.6 \, M_\odot$ and its mass-loss rate is $\sim \dot{M} = 1.1 \times 10^{-6} \, {\rm{M_\odot\,yr^{-1}}}$ (cite: Decin2020)." (5.1 ALMA observation) [from (cite: Decin2020)]
- External data: ATOMIUM combined ALMA data of R Aql  
  > "We refer to (cite: Gottlieb2022) for more details on the observations and data processing." (5.1 ALMA observation) [from (cite: Gottlieb2022)]
- Simulation/model as data: PHANTOM SPH grid of 8 triple and 4 binary AGB wind models; model v08m06 post-processed with MAGRITTE  
  > "We model a grid of hierarchical triple systems including a wind-launching AGB star, with the smoothed-particle-hydrodynamic PHANTOM code." (abstract)

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
- uv taper: FWHM 0.04 arcsec, combining three configurations  
  > "a combination is made of the data from these three configurations (with a $uv$ taper of FWHM $0.04 "$" (5.1 ALMA observation)
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

- Numerical input physics of the SPH model  
  > "We use the same numerical input physics as described in (cite: Malfait2024), where more details can be found." (2.1 Input physics SPH model) [from (cite: Malfait2024)]
- ALMA observations and data processing  
  > "We refer to (cite: Gottlieb2022) for more details on the observations and data processing." (5.1 ALMA observation) [from (cite: Gottlieb2022)]
- Epsilon classification parameter  
  > "a classification parameter $\varepsilon$, as proposed by (cite: Maes2021), and applied by (cite: Malfait2021)" (2.4 Classification parameter and flattening ratio) [from (cite: Maes2021)]

### Not stated but needed to reproduce (our reading)

- ALMA project code and CASA/pipeline versions for the ATOMIUM R Aql data
- SPH particle number and resolution
- MAGRITTE grid/mesh settings, image resolution and velocity channel setup
- Procedure used to measure arc spacing in observed channel maps
- Why the simulated model was not convolved with the ALMA beam

## Analysis recipe

1. **Run SPH simulations of triple and binary AGB winds**: PHANTOM SPH with sink particles and wind injection; free-wind approximation; H I cooling  
  > "We perform hydrodynamic simulations of an AGB outflow in a hierarchical triple system with the smoothed-particle hydrodynamics (SPH) code PHANTOM (cite: phantom)." (2.1 Input physics SPH model)
   - software: PHANTOM, REBOUND
   - parameter: M1=1.6, M2=0.4 Msun, ai=5 au, ao=35 au, Mdot=1.1e-6 Msun/yr, T1=2800 K, v_ini 8 or 15 km/s, M3=0.1/0.6/1.2 Msun  
  > "$a_{\rm{o}}$       | \[au\]                        |         $35$         |" (Table 1)
   - assumption: gamma = 1.2, mu = 2.38  
  > "We adopt constant values of the polytropic index $\gamma = 1.2$ and the mean molecular weight $\mu = 2.38$" (2.1 Input physics SPH model)
   - fitting: _not stated_
   - validation: Mardling & Aarseth stability criterion and REBOUND N-body integration over 1000 outer periods  
  > "the orbit of all systems is integrated with the REBOUND N-body code (cite: rebound) over $1000$ outer orbital periods $P_{\rm o}$, to confirm the stability of the orbits." (2.2 Grid setup triples)
2. **Radiative transfer of model v08m06 to synthetic 12CO(2-1) channel maps**: MAGRITTE ray-tracer, NLTE, first 40 rotational levels, LAMDA data, viewed at 230 pc and inclination 30 deg  
  > "calculations are done in non local thermodynamical equilibrium (NLTE), taking into account the first $40$ rotational transitions." (5.2 Comparison to synthetic observation)
   - software: MAGRITTE
   - parameter: micro-turbulence 0.5 km/s; CMB outer boundary  
  > "The micro-turbulence is set to $0.5 \, {\rm km \, s^{-1}}$ (cite: Ramstedt2008)" (5.2 Comparison to synthetic observation)
   - assumption: All mass in H2; [CO/H2] = 3e-4  
  > "we assume that all mass is in H$_2$, and the fractional abundance of CO is \[CO$/$H$_2$\]$= 3\times 10^{-4}$" (5.2 Comparison to synthetic observation)
   - fitting: _not stated_
   - validation: Qualitative visual comparison with ATOMIUM channel maps; no ALMA simulator applied  
  > "A detailed one-to-one comparison is, however, not feasible, due to the large uncertainty on the selected parameters of the model and the inclination" (5.2 Comparison to synthetic observation)

## Software

- **PHANTOM** : SPH hydrodynamic simulations  
  > "smoothed-particle hydrodynamics (SPH) code PHANTOM (cite: phantom)" (2.1 Input physics SPH model)
- **REBOUND** : N-body orbit stability test  
  > "integrated with the REBOUND N-body code (cite: rebound)" (2.2 Grid setup triples)
- **MAGRITTE** : NLTE radiative transfer post-processing  
  > "we post-process the PHANTOM output of model v08m06 with the MAGRITTE[^1] radiative transfer code" (5.2 Comparison to synthetic observation)
- **SPLASH** : visualisation  
  > "made using the visualisation tools PLONS[^2] and SPLASH (cite: splash)" (Acknowledgements)
- **PLONS** : visualisation  
  > "made using the visualisation tools PLONS[^2] and SPLASH (cite: splash)" (Acknowledgements)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Inner binary orbital period | 7.91 | not stated | yr | 1 | The orbital period of the inner binary $M_{\rm 1}$–$M_{\rm 2}$ is $P_{\rm i} = 7.91 \, {\rm yrs}$ |
| Outer orbital period for M3=0.6 Msun | 128.5 | not stated | yr | 1 | $P_{\rm o} = 143.0, 128.5 \, {\rm and}\, 115.8 \, {\rm yrs}$ |
| Measured flattening ratio, triple v08 models | ~0.5 | not stated | dimensionless | 1 | This measured $R_{\rm f}$ is approximately $0.5$ for all masses of $M_3$. |
| R Aql continuum peak intensity | 18.9 | not stated | mJy/beam | 0 | It consists of one centrally condensed patch of emission with a specific intensity peak of $18.9 \, {\rm mJy \, beam^{-1}}$. |
| Mean radial spacing of observed arcs/spirals in R Aql | ~1.15 | large (not quantified) | arcsec | 0 | is $\sim 1.15 \, {\rm arcsec}$, indicating that these wind structures travel about $\sim 265 \, {\rm au}$ during one orbital period. |
| Implied orbital period from arc spacing (v~10 km/s) | ~126 | not stated | yr | 0 | the time between two structures (corresponding to the orbital period), is $\sim 126 \, {\rm yrs}$. |

## Qualitative findings

- Triples produce a large two-edged spiral wake from the outer companion with a waved outer edge, over a snail-shell inner spiral.  
  > "A large two-edged spiral wake results behind the outer companion star." (abstract)

## Claim tuples

- H: How does adding a hierarchical outer companion change binary wind morphology? | E: Grid of PHANTOM triple models compared with binary subsystems | R: Large-scale gravity wake with waved outer edge, inner spiral deformed to snail-shell | F: Triple nature produces distinctive wind structures | **supported**
- H: Could R Aql be shaped by a triple system? | E: MAGRITTE 12CO(2-1) synthetic maps of model v08m06 compared with ATOMIUM data | R: Similar global morphology; triple signatures not resolved in channel maps | F: Possible but not demonstrated | **partially**

## Reasoning

- Why this data: _not stated_
- Why this method: _not stated_
- Alternative: Test with mu = 1.26 for v08m12 showed no material accumulation, but changed wind velocity strongly  
  > "We performed a test simulation of this model with $\mu = 1.26$, which is more suited for atomic gas, and find no accumulation of material." (4.2 Impact of different wind velocity)
- How they decided it was enough: _not stated_
- Limitation (authors): Parameter space degenerate; no ALMA simulator applied; pulsations missing  
  > "the SPH models lack some physics such as the impact of the stellar pulsations, that may affect the wind morphology" (5.2 Comparison to synthetic observation)
- Caveat (inferred, ours): R Aql comparison is purely qualitative with a single hand-picked model
- Caveat (inferred, ours): Only coplanar circular/limited eccentric orbits, one inclination
- Caveat (inferred, ours): No convolution with ALMA beam or noise
- Caveat (inferred, ours): Simplified equation of state

## Reproducibility

- Data public (paper): Simulation inputs and outputs on Zenodo  
  > "The input files and output dumps to reproduce the Phantom simulations and figures in this paper are available online (<https://zenodo.org/records/12795466>)." (2.1 Input physics SPH model)
- Products in archive: _not stated_
- Code: MAGRITTE open source on GitHub; plons on GitHub  
  > "Open source & available online: <https://github.com/Magritte-code/Magritte>." (footnote)
- Missing: ALMA project code and reduced ATOMIUM cubes
- Missing: MAGRITTE imaging settings
- Data volume (inferred): Simulations: large (HPC); ALMA data: tens of GB if reprocessed
- Score (inferred): 3/5, Simulation inputs are public, but the ALMA comparison is qualitative and details are deferred to other papers.
- Rediscovery candidate: no, The ALMA part is qualitative and the main results are simulation morphologies, not numeric.

## Links

- Method: Malfait et al. 2024 (cite: Malfait2024) (SPH input physics)
- Method: Gottlieb et al. 2022 (cite: Gottlieb2022) (ATOMIUM data processing)
- Method: Maes et al. 2021 (cite: Maes2021) (epsilon parameter)
- Companion: Decin et al. 2020 (cite: Decin2020) (ATOMIUM programme and R Aql)
- Related: ATOMIUM

## Checks

```json
{
 "quotes": 41,
 "quotes_ok": 41,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 0,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [
  "2018.1.00659.L"
 ],
 "codes_printed_but_missing": [],
 "numeric_results": 6,
 "numeric_problems": 0,
 "fill": {
  "facts": 68,
  "stated": 31,
  "rate": 0.456
 },
 "evidence_ok": true
}
```
