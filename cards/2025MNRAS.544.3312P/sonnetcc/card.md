# Sculpting protoplanetary discs ─ modelling circumbinary cavities at observable scales with radiation hydrodynamics

`2025MNRAS.544.3312P` | Monthly Notices of the Royal Astronomical Society 2025 | first author: Penzlin, Anna B. T. | arXiv: 2510.25010 | DOI: 10.1093/mnras/staf1876

Card schema 1.0 | model claude-sonnet-5-5-claude-code | depth light | type theory_or_simulation_compared_to_alma

## Science

- Fields: protoplanetary_disks
- Question: How do radiative heating and cooling processes, which vary with disc size scale, set the shape and size of circumbinary cavities, and can this explain observed cavities such as Cs Cha and GG Tau?  
  > "To fully understand what determines the properties of observed cavities, it is therefore necessary to capture the effect of radiative processes in modelling." (abstract); "We then establish connections to observed circumbinary systems to test our findings and the applicability of our model." (1 Introduction)
- Target **Cs Cha**: coordinates _not stated_; z/distance 169 pc  
  > "a distance to the source of 169 pc" (6 Synthetic observations); "a disc inclination of 17.86 deg, and PA of 263.1 deg" (6 Synthetic observations); distance from system parameters as presented in Kurtovic et al. 2022 (cite: 2022Kurtovic)  
  > "a distance to the source of 169 pc" (6 Synthetic observations); "a disc inclination of 17.86 deg, and PA of 263.1 deg" (6 Synthetic observations)
- Target **GG Tau A**: coordinates _not stated_; z/distance _not stated_; distance from _not stated_

## Data provenance

- ALMA projects: 2017.1.00969.S, 2018.1.00532.S
- bands: _not stated_
- frequencies and spectral setup: _not stated_
- continuum bandwidth: _not stated_
- arrays: _not stated_
- configurations: _not stated_
- baselines: _not stated_
- angular resolution: _not stated_
- max recoverable scale: _not stated_
- sensitivity: _not stated_
- time on source: _not stated_
- observing dates: _not stated_
- pi or archival as stated: _not stated_
- Line: 12CO J=3-2 (not stated (synthetic cubes centred at ~345.796 GHz))
- Other facility **ALMA (12CO(3-2) observation of Cs Cha, taken from the literature)**: 12CO(3-2) ALMA observation of Cs Cha, compared with the synthetic CO cube  
  > "the comparison to the $\rm ^{12}CO(3-2)$ ALMA observation (cite: 2022Kurtovic)" (6 Synthetic observations)
- Other facility **Scattered-light imaging of GG Tau (instrument not named for this comparison)**: Scattered-light observation of GG Tau compared with the simulated scattered-light image  
  > "We compare also the scattered light observation of the GG Tau system (cite: 2020Keppler) with our simulation" (6 Synthetic observations)
- External data: Cs Cha binary and disc parameters (distance, total mass, inclination, position angle) and the 12CO(3-2) observation used for comparison  
  > "a disc inclination of 17.86 deg, and PA of 263.1 deg" (6 Synthetic observations); "the comparison to the $\rm ^{12}CO(3-2)$ ALMA observation (cite: 2022Kurtovic)" (6 Synthetic observations) [from (cite: 2022Kurtovic)]
- External data: GG Tau A binary parameters (Table 2)  
  > "For the system parameters we used the measurement in (cite: 2022Kurtovic) for CsCha and (cite: 2020Keppler) and (cite: 2011Koehler) for GG Tau" (6 Synthetic observations) [from (cite: 2020Keppler); (cite: 2011Koehler)]
- External data: GG Tau millimetre continuum observation compared with the simulated continuum  
  > "the left two panels compare the continuum emission between observation (cite: 2024Rota) and simulation" (6 Synthetic observations) [from (cite: 2024Rota)]
- External data: GG Tau scattered-light observation  
  > "We compare also the scattered light observation of the GG Tau system (cite: 2020Keppler)" (6 Synthetic observations) [from (cite: 2020Keppler)]
- External data: Disjoint power-law opacity model  
  > "We use the disjoint power-law opacity model of (cite: 1985Lin) (cite: 2012Muller)" (2.4 Radiative cooling) [from (cite: 1985Lin); (cite: 2012Muller)]
- External data: Estimated binary separation of Cs Cha used to choose a_bin = 5 au  
  > "The middle value is the estimated separation of the binary stars in Cs Cha (cite: 2007Guenther)" (3.2 Physical conditions) [from (cite: 2007Guenther)]
- Simulation/model as data: 27 two-dimensional PLUTO simulations of circumbinary discs (a_bin = 1, 5, 25 au; e_bin = 0.01, 0.15, 0.3; locally isothermal, radiative, radiative with in-plane cooling)  
  > "we run 27 simulations of circumbinary discs in 2D using the PLUTO code" (abstract); "We varied the binary eccentricity, investigated three size scales $a_\mathrm{bin}=[1,5,25]$ au, and compared three different thermodynamical models" (8 Conclusion)
- Simulation/model as data: Synthetic 12CO(3-2) cubes, 0.9 mm continuum and 1 micron scattered-light images from RADMC-3D ray tracing of the PLUTO models  
  > "We use radmc3d (cite: radmc) to created synthetic observation based on the models which include in-plane cooling." (6 Synthetic observations)

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
- continuum subtraction: _not stated_
- line free channels: _not stated_
- primary beam correction: _not stated_
- array combination: _not stated_
- smoothing: symmetric Gaussian convolution of 30 mas applied to the synthetic image  
  > "A symmetric Gaussian convolution filter of 30 milliarcsecs is applied to the image." (6 Synthetic observations)
- final beam: _not stated_
- final rms: _not stated_

### Inherited from earlier work

- 2D vertically integrated co-planar setup  
  > "We will build on the vertically integrated, two-dimensional (2D) models presented in (cite: 2019Kley)" (2 Hydro- and thermodynamics in accretion discs) [from (cite: 2019Kley)]
- Binary orbit integration with an N-body scheme  
  > "The orbital evolution of the binary is integrated in time using the N-body scheme detailed in (cite: 2017Thun)." (3.1 Numerical setup) [from (cite: 2017Thun)]
- Cavity size fit (ellipse from apocentre and pericentre density maxima)  
  > "dashed ellipses mark a simple fit to the cavity size following (cite: 2022Sudarshan)" (5 Cavity shapes and sizes at different radial scales) [from (cite: 2022Sudarshan)]
- Procedure for synthetic 12CO(3-2) data cubes  
  > "we followed the procedure presented in (cite: 2024Barraza) (see further details and references therein)" (6 Synthetic observations) [from (cite: 2024Barraza)]
- Cooling time and relaxation prescription for in-plane cooling  
  > "relaxing the temperature to its initial profile over a cooling timescale" (2.5 In-plane cooling) [from (cite: 2017Flock); (cite: 2001Gammie)]
- Pressureless dust fluid in PLUTO  
  > "which includes support for dust as a pressureless fluid (cite: 2024dust)" (6 Synthetic observations) [from (cite: 2024dust)]
- Mixing-settling equilibrium for the vertical dust structure  
  > "assuming a mixing–settling equilibrium for the vertical direction with $\alpha=10^{-4}$ following (cite: fromang-nelson-2009)" (6 Synthetic observations) [from (cite: fromang-nelson-2009)]
- Boundary conditions and radial extent  
  > "This combination of boundary conditions with the radial extent of the domain is motivated by the analysis in (cite: 2022Penzlin)" (3.1 Numerical setup) [from (cite: 2022Penzlin)]

### Not stated but needed to reproduce (our reading)

- Reduction, calibration and imaging details of the ALMA 12CO(3-2) Cs Cha cube and the GG Tau continuum used for comparison (beam, rms, robust, channel width); the paper only cites Kurtovic et al. 2022 and Rota et al. 2024.
- Which of the two printed ALMA projects (2017.1.00969.S, 2018.1.00532.S) corresponds to which compared observation.
- Number of grid cells in R and phi, and the PLUTO and RADMC-3D versions.
- The exact numeric opacity table (disjoint power-law coefficients) and the gas temperature or opacity inputs passed to RADMC-3D.
- Gas-phase CO abundance, CO freeze-out or photodissociation treatment and microturbulence beyond the stated broadening for the synthetic CO cubes.
- How simulations were aligned and rotated to observations (orientation, sky position) and the time snapshot chosen for each comparison.
- Full thermal-model parameters for the GG Tau run beyond Table 2 (stellar luminosities, surface density and h0 for the 39.9 au case).
- Disc surface density normalisation used for the 5 au Cs Cha and 39.9 au GG Tau comparison runs.

## Analysis recipe

1. **Run radiative models to quasi-equilibrium**: 2D PLUTO runs with viscous heating, stellar irradiation and radiative surface cooling, to reach quasi-equilibrium and set temperature profiles  
  > "Radiative models with viscous heating, stellar irradiation and radiative cooling" (3.2 Physical conditions); "to allow the disc to reach a quasi-equilibrium state and compute realistic surface temperature estimates." (3.2 Physical conditions)
   - software: PLUTO
   - parameter: alpha = 1e-4  
  > "In this study, we use a low but non-zero turbulent viscosity with $\alpha=10^{-4}$" (3.2 Physical conditions)
   - parameter: All models run for 30 000 binary orbits  
  > "All models are run for 30 000 binary orbits in total." (3.2 Physical conditions)
   - assumption: Binary of equal-mass stars of 0.95 Msun total 1.9 Msun, 0.745 Lsun each; binary orbit receives no feedback from the disc  
  > "The binary stars are of equal mass with a luminosity of $0.745~L_\odot$ each and the orbits of the binary do not receive any feedback from the disc." (3.2 Physical conditions)
   - fitting: _not stated_
   - validation: _not stated_
2. **Run matched locally isothermal models**: Locally isothermal runs using power-law approximations of the temperature profiles from the radiative models, run in parallel for comparison  
  > "Corresponding locally isothermal models using the above temperature profiles (approximated as power-laws) are executed in parallel for comparison." (3.2 Physical conditions)
   - software: PLUTO
   - fitting: _not stated_
   - validation: _not stated_
3. **Add in-plane cooling**: Beta-cooling relaxation to the earlier temperature profile T0 added to the radiative models and continued  
  > "after 10 000 binary orbits" (3.2 Physical conditions); "simulations are continued for 30 000 orbits." (3.2 Physical conditions)
   - software: PLUTO
   - parameter: relaxation source term with a factor of 4 in front  
  > "with the factor of 4 motivated by linear analysis in order to match calculations with a self-consistent treatment of radiative terms" (2.5 In-plane cooling)
   - assumption: Rosseland and Planck mean opacities equal  
  > "further assume that the Rosseland and Planck mean opacities are equal" (2.4 Radiative cooling)
   - fitting: _not stated_
   - validation: Cooling timescale profile compared with 2D local cooling from the simulations  
  > "We can compare the 1D prediction for the cooling time to the local cooling in 2D disc models" (5 Cavity shapes and sizes at different radial scales)
4. **Measure cavity size and eccentricity**: Elliptical cavity fit: apocentre at the highest density, pericentre from the opposite density maximum, cavity edge where density falls to 10% of the maximum  
  > "From these points we define the cavity as the radial position where the density drops to $\leq10\%$ of the maximium density in peri- and apocentre." (5 Cavity shapes and sizes at different radial scales)
   - fitting: _not stated_
   - validation: _not stated_
5. **Evolve dust in the PLUTO models**: Continue simulations with a pressureless dust fluid and dust back-reaction enabled  
  > "which includes support for dust as a pressureless fluid (cite: 2024dust)" (6 Synthetic observations); "Dust back-reaction on the gas was enabled as well" (6 Synthetic observations)
   - software: PLUTO
   - parameter: grain size 1 mm, bulk density 2.08 g/cm3  
  > "grains with a bulk density of $\tilde{\rho} = 2.08\,\text{g}/\text{cm}^3$ and a grain size of 1 mm" (6 Synthetic observations)
   - parameter: initial dust-to-gas 0.01 outside the pressure maximum, 1e-6 elsewhere  
  > "$\Sigma_\text{d}=0.01\,\Sigma_\text{g}$ exterior to the pressure maximum at the cavity edge, and $\Sigma_\text{d}=10^{-6}\,\Sigma_\text{g}$ otherwise" (6 Synthetic observations)
   - fitting: _not stated_
   - validation: _not stated_
6. **Make synthetic 12CO(3-2) cube for the 5 au model and compare to Cs Cha**: Extend the 2D gas model to 3D with a Gaussian vertical density and an assumed vertical temperature law, then ray-trace with RADMC-3D using the simulation gas temperature  
  > "we followed the procedure presented in (cite: 2024Barraza) (see further details and references therein). However, we used directly the simulation gas temperature as input into radmc3d." (6 Synthetic observations)
   - software: RADMC-3D
   - parameter: channels cover +-8.875 km/s with 0.25 km/s resolution  
  > "channels covering $\rm \pm 8.875 \,km \,s^{-1}$ and a velocity resolution of $\rm 0.25 \,km \,s^{-1}$" (6 Synthetic observations)
   - parameter: Cs Cha: distance 169 pc, inclination 17.86 deg, PA 263.1 deg, total mass 1.9 Msun  
  > "a disc inclination of 17.86 deg, and PA of 263.1 deg" (6 Synthetic observations)
   - assumption: Vertical temperature structure is an approximation that likely underestimates the true temperature but suffices to make an optical surface  
  > "it is sufficient to create a optical surface necessary for the synthetic CO maps." (6 Synthetic observations)
   - fitting: _not stated_
   - validation: Qualitative comparison of the synthetic gas shape with the Cs Cha 12CO(3-2) ALMA observation  
  > "we can recover the shape of the CsCha observation gas" (6 Synthetic observations)
7. **Make synthetic continuum and scattered-light images and compare to GG Tau**: RADMC-3D thermal Monte Carlo with 1e9 photons, dust opacities from OpTool for 0.1 micron and 1 mm grains, images at 0.9 mm and 1 micron; gas Sigma scaled by 0.01 for small grains  
  > "We computed the thermal structure of the disc using the mctherm command of RADMC-3D with $10^9$ photons" (6 Synthetic observations); "to generate images of thermal continuum emission at 0.9 mm and scattered light emission at $1\,\mu$m" (6 Synthetic observations)
   - software: RADMC-3D, OpTool
   - parameter: small grains 0.1 micron from 0.01 x gas surface density  
  > "the gas component was translated to a population of small grains by multiplying $\Sigma_\text{g}$ by 0.01 and assigning a grain size of 0.1 $\mu$m" (6 Synthetic observations)
   - parameter: GG Tau scattered light: settled dust of grain size 870 micron  
  > "assuming vertically settled dust following the gas surface density with a grain size of $870~\mu$m" (6 Synthetic observations)
   - assumption: Anisotropic scattering with Henyey-Greenstein, anisotropy from OpTool; DIANA opacity standard  
  > "assuming anisotropic scattering using the approach of (cite: henyey-greenstein-1941) with the anisotropy factor computed via" (6 Synthetic observations)
   - fitting: _not stated_
   - validation: Qualitative comparison with GG Tau continuum and scattered-light images  
  > "We recover a dynamic behaviour in our model that matches the structures in GG Tau." (6 Synthetic observations)
8. **Compute dynamic eccentricity of the GG Tau model**: Cell-by-cell eccentric Keplerian orbit fit from the velocity vectors around the centre of mass  
  > "The dynamic eccentricity uses the velocities vector in for each cell to calculate the orbital parameters of an eccentric Keplerian orbit around the centre of mass" (Appendix: Dynamic eccentricity in GG Tau)
   - fitting: _not stated_
   - validation: _not stated_

## Software

- **PLUTO** : GPU-parallelised 2D hydrodynamic simulations including dust fluid  
  > "We use the PLUTO astrophysical code (cite: 2007Pluto) in a vertically integrated, cylindrical polar geometry" (3.1 Numerical setup)
- **RADMC-3D** : Synthetic CO cubes, continuum and scattered-light images  
  > "We use radmc3d (cite: radmc) to created synthetic observation based on the models which include in-plane cooling." (6 Synthetic observations)
- **OpTool** : Dust opacities for 0.1 micron and 1 mm grains with the DIANA standard  
  > "grains using OpTool (cite: optool) following the DIANA standard (cite: woitke-etal-2016)" (6 Synthetic observations)

## Numeric results

| quantity | value | uncertainty | units | step | quote |
|---|---|---|---|---|---|
| Radius range of long cooling time (viscous heating dominated), peak location | between 3 and 7 au, peaking at ~5 au | not stated | au | 1 | The long cooling time between 3 and 7 au, peaking at $\sim5$ au |
| Speed-up of cooling from in-plane diffusion relative to surface cooling alone | ~5x faster | not stated | dimensionless | 3 | leads to $\sim5\times$ faster cooling compared to models with surface cooling alone |
| Cooling time beta at a_bin = 25 au with in-plane cooling | <0.3 | not stated | dimensionless | 3 | the overall cooling time in the disc drops significantly to $\beta<0.3$. |
| Cavity eccentricity, a_bin = 1 au models | 0.1 to 0.35 | not stated | dimensionless | 4 | with a cavity size between 3.5 and 5 and an eccentricity between 0.1 and 0.35 |
| Cavity eccentricity e_cav of locally isothermal discs at a_bin = 5 au | >0.25 | not stated | dimensionless | 4 | While the locally isothermal discs grow in cavity size and eccentricity to $a_\mathrm{cav}>4$ and $e_\mathrm{cav}>0.25$ |
| Span of cooling timescale across models | 4 orders of magnitude | not stated | dimensionless | 1 | Given that the cooling timescale spans 4 orders of magnitude in our models |
| GG Tau model gas eccentricity at the cavity edge | ~0.1 | not stated | dimensionless | 8 | The eccentricity at the cavity edge reaches $\sim0.1$. |
| GG Tau model eccentricity around the inner edge of the dust density | ~0.05 | not stated | dimensionless | 8 | drops to values $\sim0.05$ around the inner edge of the dust density |

## Qualitative findings

- At a_bin = 5 au the thermally evolving discs stay small and circular, with no significant eccentricity growth in 30k binary orbits  
  > "Fig. [6](#fig:evo5) shows that the there is no growth of significant eccentricity through the whole non-isothermal simulations of 30k" (5.2 Binaries with intermediate separations)
- At a_bin = 25 au the model without in-plane cooling stays small and circular, while with in-plane cooling it re-excites to a large eccentric cavity  
  > "Fig. [7](#fig:evo25) shows that the system without in-plane cooling is never able to reach any significant excitation within the simulation time." (5.3 Wide binary discs)

## Claim tuples

- H: The diverse observed cavity shapes result from a radially varying cooling timescale | E: 27 2D PLUTO runs over three binary separations, three eccentricities and three thermodynamic treatments | R: Cavities are large and eccentric for 1 au and for 25 au with in-plane cooling, but small and circular near the orbital cooling time | F: Cavity shape follows the cooling regime set by disc scale | **supported**
- H: Cooling comparable to the orbital time at the cavity edge circularises cavities | E: Compared isothermal and radiative models at a_bin = 5 au | R: Radiative models stay circular with small cavities and damp any excitation within 10k binary orbits; isothermal models become eccentric | F: Wave damping at beta ~ 1 yields circular cavities | **supported**
- H: Thermal wave damping alone can explain the circular cavity of Cs Cha without a planet | E: Synthetic 12CO(3-2) from the 5 au in-plane cooling model compared with the ALMA observation | R: Shape recovered but size not matched perfectly given the binary orbital elements | F: Thermodynamic damping can circularise the disc, but the planet scenario cannot be excluded | **partially**
- H: One physical model explains the eccentricity levels of both Cs Cha and GG Tau | E: Synthetic continuum and scattered light for a 39.9 au binary compared with GG Tau observations | R: Circular mm dust ring and off-centre eccentric scattered light with spirals, but infalling streams not captured by the planar model | F: Model matches GG Tau structures and reduces the eccentricity found in isothermal models | **partially**

## Reasoning

- Why this data: Cs Cha stellar properties chosen to put an intermediate-sized disc at the centre of the study; observations compared because the models are gas only  
  > "To put an intermediate-sized disc at the centre of the investigation, we base the stellar properties on the case of Cs Cha" (3.2 Physical conditions); "Since our simulations are only gas, they are best to compare to scattered-light and CO observation of systems." (6 Synthetic observations)
- Why this method: _not stated_
- Alternative: Circularisation by an embedded planet or by dust back-reaction is discussed as an alternative; the dust-to-gas ratio used makes dust circularisation minuscule  
  > "While the circularization can be caused by the thermodynamic interaction it can also be caused and maintained by planets (cite: 2021Penzlin)." (7.2 Other methods for circularisation); "although we note that for the dust-to-gas ratio we employed this circularisation effect should be minuscule" (6 Synthetic observations)
- How they decided it was enough: _not stated_
- Limitation (authors): 2D vertically integrated models; 3D effects and vertical radiative transfer not included  
  > "Another effect that would require the full 3D model would be the radiative transfer in the disc, as we consider only vertically integrated approximation." (7.3 Viscosity and instability in the disc)
- Limitation (authors): Binary orbit does not evolve with the disc  
  > "The binary in our model is not included in the domain and does not evolve its orbit due to the gravitational or accretion interaction with the disc." (7.1 Evolution of disc and binary)
- Limitation (authors): Gas disc is an upper limit on eccentricity because dust and 3D effects are neglected  
  > "Hence, our gas disc represents an upper limit on the expected eccentricity of the disc." (7.2 Other methods for circularisation)
- Limitation (authors): Synthetic Cs Cha image size does not match the observation perfectly because of uncertain binary orbital elements  
  > "the size of the synthetic observations does not match the AMLA images perfectly due to our specific choice of binary orbital elements" (6 Synthetic observations)
- Limitation (authors): Radiative diffusion is not captured, only relaxation cooling  
  > "we do not capture the effects of radiative diffusion" (7.4 Effects of radiative diffusion)
- Caveat (inferred, ours): Comparison with Cs Cha and GG Tau is by eye; no quantitative fit statistic or uncertainty on cavity size.
- Caveat (inferred, ours): Cs Cha model uses e_bin = 0.3 although Table 2 lists 0.40 for the literature value.
- Caveat (inferred, ours): Results depend on the assumed opacity law, disc mass and alpha = 1e-4, which are not varied.
- Caveat (inferred, ours): ALMA data enter only through earlier papers, so the ALMA contribution cannot be checked from this paper alone.

## Reproducibility

- Data public (paper): Observations publicly available through ALMA and ESO archives; simulation data on request  
  > "The observations are publicly available through ALMA and ESO archives." (Data Availability); "The data underlying this article will be shared on reasonable request to the corresponding author." (Data Availability)
- Products in archive: _not stated_
- Missing: Grid resolution and PLUTO/RADMC-3D versions
- Missing: Opacity coefficients and CO abundance treatment for the synthetic observations
- Missing: ALMA data reduction details for the compared observations (given only in cited papers)
- Missing: Simulation outputs and setup files only on request
- Data volume (inferred): Simulations: GPU runs of 30 000 binary orbits for 27 models; ALMA comparison data: tens of GB of archive data if re-reduced (inferred, not stated).
- Score (inferred): 2/5, ALMA data are only compared with cited published results; the simulations use PLUTO with many setup details and opacity inputs inherited or unstated, and outputs are only on request.
- Rediscovery candidate: no, ALMA data are secondary and the main results come from simulations whose full setup and outputs are not public.

## Links

- Method: (cite: 2019Kley) (2D circumbinary disc setup the models build on)
- Method: (cite: 2022Sudarshan) (Radiative damping of circumbinary cavities and cavity-fit method)
- Method: (cite: 2024Barraza) (Procedure for synthetic 12CO(3-2) cubes)
- Method: (cite: 2017Thun) (PLUTO binary N-body scheme)
- Method: (cite: 2020Miranda_II) (Cooling timescale formulation)
- Companion: (cite: 2022Kurtovic) (Source of the Cs Cha ALMA 12CO(3-2) observation and system parameters)
- Companion: (cite: 2020Keppler) (GG Tau scattered-light observation and parameters)
- Companion: (cite: 2024Rota) (GG Tau continuum observation)
- Companion: (cite: 2024Penzlin) (Earlier locally isothermal circumbinary models and dynamic eccentricity)

## Checks

```json
{
 "quotes": 91,
 "quotes_ok": 91,
 "quote_pass_rate": 1.0,
 "quotes_too_long": 0,
 "unsupported_facts": 0,
 "project_codes": 2,
 "codes_not_in_text": [],
 "codes_not_in_obscore": [],
 "obscore_codes_not_in_card": [],
 "codes_printed_but_missing": [],
 "numeric_results": 8,
 "numeric_problems": 0,
 "fill": {
  "facts": 112,
  "stated": 59,
  "rate": 0.527
 },
 "evidence_ok": true
}
```
